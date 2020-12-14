---
title: 자산 오프로딩 우수 사례
description: AEM Assets에서 자산 수집 및 복제 워크플로우를 오프로드하기 위한 권장 사용 사례 및 모범 사례
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---


# 자산 오프로딩 우수 사례 {#assets-offloading-best-practices}

>[!WARNING]
>
>이 기능은 AEM 6.4부터 사용되지 않으며 AEM 6.5에서 제거됩니다. 그에 따라 계획하십시오.

AEM(Adobe Experience Manager)에서 대용량 파일 및 실행 워크플로우를 처리하는 자산은 상당한 CPU, 메모리 및 I/O 리소스를 사용할 수 있습니다. 특히 자산 크기, 워크플로우, 사용자 수 및 자산 수집의 빈도는 전체 시스템 성능에 영향을 줄 수 있습니다. 가장 많은 리소스를 필요로 하는 작업에는 AEM 자산 수집 및 복제 워크플로우가 포함됩니다. 단일 AEM 저작 인스턴스에서 이러한 워크플로우를 과도하게 사용하면 저작 효율성이 저하될 수 있습니다.

이러한 작업을 전용 작업자 인스턴스로 업로드하면 CPU, 메모리 및 IO 오버헤드가 줄어듭니다. 일반적으로, 오프로딩 작업의 이면은 많은 CPU/메모리/IO 리소스를 사용하는 작업을 전용 작업자 인스턴스에 분배하는 것입니다. 다음 섹션에는 자산 오프로딩에 대한 권장 사용 사례가 포함됩니다.

## AEM Assets 오프로딩 중 {#aem-assets-offloading}

AEM Assets은 오프로드를 위한 기본 에셋 특정 워크플로우 확장을 구현합니다. 오프로딩 프레임워크가 제공하는 일반 워크플로우 확장을 기반으로 구축되지만 구현에 추가 자산별 기능이 포함됩니다. 자산 오프로딩의 목표는 업로드된 자산에서 DAM 자산 업데이트 워크플로우를 효율적으로 실행하는 것입니다. 자산 오프로드를 통해 통합 워크플로우를 보다 완벽하게 제어할 수 있습니다.

## AEM Assets 구성 요소 오프로딩 중 {#aem-assets-offloading-components}

다음 다이어그램은 자산 오프로딩 프로세스의 기본 구성 요소를 보여 줍니다.

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM 자산 업데이트 오프로딩 워크플로 {#dam-update-asset-offloading-workflow}

DAM 자산 오프로드 워크플로우는 사용자가 자산을 업로드하는 기본(작성자) 서버에서 실행됩니다. 이 워크플로우는 일반 워크플로우 실행 프로그램에 의해 트리거됩니다. 업로드된 에셋을 처리하는 대신 이 오프로딩 작업 과정은 *com/adobe/granite/workflow/offloading* 항목을 사용하여 새 작업을 만듭니다. 오프로딩 워크플로우는 대상 워크플로우의 이름을 추가합니다. 이 경우 DAM 자산 업데이트 워크플로우이며 자산의 경로를 작업 페이로드에 추가합니다. 오프로딩 작업을 만든 후 기본 인스턴스의 오프로딩 작업 과정은 오프로딩 작업이 실행되기 전까지 대기합니다.

### 작업 관리자 {#job-manager}

작업 관리자는 근로자 인스턴스에 새 작업을 배포합니다. 배포 메커니즘을 디자인할 때는 주제 활성화를 고려해야 합니다. 작업의 항목이 활성화된 인스턴스에만 작업을 지정할 수 있습니다. 기본 항목에서 `com/adobe/granite/workflow/offloading` 항목을 비활성화하고 작업자가 작업을 작업자에게 할당했는지 확인하려면 워커에서 활성화합니다.

### AEM 오프로딩 중 {#aem-offloading}

오프로딩 프레임워크는 작업자 인스턴스에 할당된 작업 로드 작업 흐름을 식별하며, 페이로드(예: 인제스트할 이미지)를 작업자에게 물리적으로 전송하기 위해 복제를 사용합니다.

### 작업 소비자 로드 워크플로 {#workflow-offloading-job-consumer}

작업자가 작업물에 대해 작성되면 작업 관리자는 *com/adobe/granite/workflow/offloading* 항목을 담당하는 작업 소비자를 호출합니다. 그런 다음 작업 소비자는 자산에서 DAM 자산 업데이트 워크플로우를 실행합니다.

## Sling 토폴로지 {#sling-topology}

Sling 토폴로지는 AEM 인스턴스를 그룹화하고 기본 지속성에 관계없이 서로 인식할 수 있도록 합니다. Sling 토폴로지의 이러한 특성을 사용하면 비클러스터형, 클러스터형, 혼합 시나리오에 대한 토폴로지를 만들 수 있습니다. 인스턴스는 전체 토폴로지에 속성을 표시할 수 있습니다. 프레임워크는 토폴로지의 변경 사항(인스턴스 및 속성)을 수신할 수 있는 콜백을 제공합니다. Sling 토폴로지는 Sling 분산 작업의 기초를 제공합니다.

### Sling 분산 작업 {#sling-distributed-jobs}

분산 작업을 사용하면 토폴로지 멤버인 인스턴스 집합 간에 작업 분포를 용이하게 합니다. 슬링 직업들은 능력 개념에 기반을 두고 있다. 작업은 해당 작업 항목으로 정의됩니다. 작업을 실행하려면 인스턴스가 특정 작업 항목에 대한 작업 소비자를 제공해야 합니다. 작업 항목은 배포 메커니즘의 기본 드라이버입니다.

작업은 해당 항목에 대한 작업 소비자를 제공하는 인스턴스에만 배포됩니다. 인스턴스에서 작업 소비자를 활성화/비활성화하여 인스턴스의 기능을 정의하고 배포 메커니즘에 영향을 줄 수 있습니다. 인스턴스의 사용 가능한 작업 소비자가 전체 토폴로지로 브로드캐스트됩니다.

이러한 컨텍스트에서 배포라는 용어는 작업 소비자를 제공하는 특정 인스턴스에 작업을 할당한다는 것을 의미합니다. 인스턴스에 대한 할당이 저장소에 저장됩니다. 즉, 분산 작업은 기본적으로 토폴로지의 모든 인스턴스에 할당할 수 있습니다. 하지만 다른 작업은 동일한 저장소를 공유하는 인스턴스에서만 실행할 수 있습니다. 이는 이러한 작업은 동일한 클러스터에 속한 인스턴스에서만 실행할 수 있음을 의미합니다. 다른 클러스터의 인스턴스에 할당된 작업은 실행되지 않습니다.

### Granite offloading framework {#granite-offloading-framework}

Granite offloading 프레임워크는 비클러스터형 인스턴스에 할당된 작업을 실행하기 위해 Sling 작업 배포를 보완합니다. 배포(인스턴스 할당)를 수행하지 않습니다. 하지만 클러스터되지 않은 인스턴스로 배포된 Sling 작업을 식별하고 이를 대상 인스턴스로 전송하여 실행합니다. 현재 오프로드는 복제를 사용하여 이 작업 전송을 수행합니다. 작업을 실행하기 위해 오프로드는 입력과 출력을 정의한 다음 작업 페이로드를 작성하는 작업과 결합합니다.

분산 작업은 작업 및 배포 프레임워크를 제공합니다. Granite offloading은 작업이 클러스터되지 않은 인스턴스로 배포되는 특별한 경우에 대해서만 전송을 처리합니다.

오프로딩 프레임워크는 전송 외에도 워크플로우 엔진에 대한 확장 기능을 제공합니다. 프레임워크에서 워크플로우의 일부로 분산 작업을 만들고 워크플로우가 시작되기 전에 작업이 완료될 때까지 기다릴 수 있습니다. 워크플로우 엔진의 워크플로우 외부 단계 API를 사용하여 구현됩니다. 익스텐션 중 하나를 사용하면 일반적으로 워크플로우를 배포할 수 있습니다. 단일 워크플로우 단계 배포는 지원되지 않습니다.

오프로딩 프레임워크에는 전체 토폴로지에서 작업 주제 기능을 시각화하고 제어할 수 있는 UI(사용자 인터페이스)도 포함되어 있습니다. UI를 사용하여 분산 작업의 항목 활성화를 편리하게 구성할 수 있습니다. UI 없이 오프로드를 설정할 수도 있습니다.

## 일반 지침 및 자산 오프로딩 우수 사례 {#general-guidance-and-best-practices-for-asset-offloading}

모든 구현은 고유하며, 이와 같이 모든 구현에 적합한 단일 오프로딩 구성이 없습니다. 다음 섹션에서는 자산 통합 오프로딩에 대한 지침과 우수 사례를 제공합니다.

에셋 오프로드는 작업 오버헤드를 포함하여 시스템에 오버헤드를 발생시킵니다. 자산 통합 로드와 관련된 문제가 발생하면 먼저 오프로드하지 않고 구성을 개선하는 것이 Adobe에 좋습니다. 자산 오프로드로 이동하기 전에 다음 옵션을 고려하십시오.

* 하드웨어 확장
* 워크플로우 최적화
* 일시적인 워크플로우 사용
* 워크플로우에 사용되는 코어 수 제한

자산 오프로딩이 적절한 접근 방식이라고 결론을 내리면 Adobe은 다음 지침을 제공합니다.

* TarMK 기반 배포 권장
* TarMK 기반 자산 오프로드는 광범위한 가로 크기 조절을 위해 설계되지 않았습니다.
* 작성자와 작업자 간의 네트워크 성능이 만족스러운지 확인

### 권장 자산 {#recommended-assets-offloading-deployment} 배포 해제

AEM 및 Oak에서는 몇 가지 배포 시나리오가 가능합니다. 자산 오프로드의 경우 공유 데이터 저장소가 있는 TarMK 기반 배포를 권장합니다. 다음 다이어그램은 권장 배포에 대한 개요를 설명합니다.

![chlimage_1-56](assets/chlimage_1-56.png)

데이터 저장소 구성에 대한 자세한 내용은 [AEM](../sites-deploying/data-store-config.md)에 노드 저장소 및 데이터 저장소 구성을 참조하십시오.

### 자동 에이전트 관리 해제 {#turning-off-automatic-agent-management}

Adobe은 바이너리 없는 복제를 지원하지 않으므로 자동 에이전트 관리를 사용하지 않도록 설정하는 것이 좋습니다. 이렇게 하면 새 오프로딩 토폴로지를 설정할 때 혼란이 발생할 수 있습니다. 또한 바이너리 없는 복제에서는 필요한 전달 방식의 복제 흐름을 자동으로 지원하지 않습니다.

1. URL `http://localhost:4502/system/console/configMgr`에서 구성 관리자를 엽니다.
1. `OffloadingAgentManager`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`)에 대한 구성을 엽니다.
1. 자동 에이전트 관리를 비활성화합니다.

### 앞으로 복제 사용 {#using-forward-replication}

기본적으로 오프로딩 전송은 역복제를 사용하여 작업자에서 기본 서버로 오프로드된 자산을 다시 가져옵니다. 역방향 복제 에이전트는 바이너리 없는 복제를 지원하지 않습니다. 오프로딩을 구성하여 포워드 복제를 사용하여 오프로드된 자산을 워커에서 기본 폴더로 푸시해야 합니다.

1. 역방향 복제를 사용하여 기본 구성에서 마이그레이션하는 경우 기본 및 워커에서 &quot; `offloading_outbox`&quot; 및 &quot; `offloading_reverse_*`&quot;이라는 모든 에이전트를 비활성화하거나 삭제합니다(여기서 &amp;ast;).대상 인스턴스의 Sling id를 나타냅니다.
1. 각 워커에서 운영 체제를 가리키는 새 전달 복제 에이전트를 만듭니다. 이 절차는 기본 Worker에서 Forward 에이전트를 생성하는 것과 같습니다. 복제 에이전트 오퍼 설정에 대한 지침은 [오프로드용 복제 에이전트 만들기](../sites-deploying/offloading.md#creating-replication-agents-for-offloading)를 참조하십시오.
1. `OffloadingDefaultTransporter`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`)에 대한 구성을 엽니다.
1. 속성 `default.transport.agent-to-master.prefix` 값을 `offloading_reverse`에서 `offloading`(으)로 변경합니다.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### 공유 데이터 저장소 및 작성자와 작업자 사이의 이진 없는 복제 사용 {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

이진 없는 복제를 사용하면 자산 오프로드를 위한 전송 오버헤드를 줄일 수 있습니다. 공유 데이터 저장소에 대해 바이너리 없는 복제를 설정하는 방법을 알아보려면 AEM[의 노드 저장소 및 데이터 저장소 구성을 참조하십시오. ](/help/sites-deploying/data-store-config.md) 이 절차는 다른 복제 에이전트가 포함된다는 점을 제외하고 자산 오프로딩과 다르지 않습니다. 바이너리 없는 복제는 전방 복제 에이전트에서만 작동하므로 모든 오프로딩 에이전트에 대해 전방 복제를 사용해야 합니다.

### 전송 패키지 {#turning-off-transport-packages} 해제

기본적으로 오프로드는 오프로딩 작업과 작업 페이로드(원본 자산)가 포함된 컨텐츠 패키지를 생성하고 단일 복제 요청을 사용하여 이 단일 오프로딩 패키지를 전송합니다. 패키지를 생성할 때 바이너리는 패키지로 다시 직렬화되므로 이러한 오프로드 패키지를 생성하는 것은 이진 없는 복제를 사용할 때 역효과를 가져옵니다. 이러한 전송 패키지의 사용을 끌 수 있으므로 오프로딩 작업 및 페이로드가 각 페이로드 항목에 대해 하나의 여러 복제 요청으로 전송됩니다. 이렇게 하면 바이너리 없는 복제 방식의 이점을 활용할 수 있습니다.

1. [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)에서 *OffloadingDefaultTransporter* 구성 요소의 구성 요소 구성을 엽니다.
1. *복제 패키지(default.transport.contentpackage)* 속성을 비활성화합니다.

### 워크플로 모델 {#disabling-the-transport-of-workflow-model} 전송 비활성화

기본적으로 *DAM 자산 업데이트 오프로딩* 오프로딩 워크플로우는 작업 페이로드에서 작업자를 호출할 워크플로우 모델을 추가합니다. 이 워크플로우는 기본적으로 기본 *DAM 자산 업데이트* 모델을 따르므로 이 추가 페이로드를 제거할 수 있습니다.

작업 페이로드에서 워크플로우 모델이 비활성화된 경우 패키지 관리자와 같은 다른 도구를 사용하여 참조된 워크플로우 모델에 변경 사항을 배포해야 합니다.

워크플로우 모델의 전송을 비활성화하려면 DAM 자산 오프로딩 작업 과정을 수정합니다.

1. [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)에서 워크플로우 콘솔을 엽니다.
1. 모델 탭을 엽니다.
1. DAM 자산 오프로드 워크플로우 모델을 엽니다.
1. DAM 워크플로우 오프로드 단계의 단계 속성을 엽니다.
1. [인수] 탭을 열고 [입력할 모델 추가] 및 [출력에 모델 추가] 옵션을 선택 취소합니다.
1. 모델에 변경 사항을 저장합니다.

### 폴링 간격 최적화 {#optimizing-the-polling-interval}

워크플로우 오프로드는 작업자에서 오프로드된 워크플로우가 완료되도록 폴링하는 기본 워크플로우의 외부 워크플로우를 사용하여 구현됩니다. 외부 워크플로 프로세스의 기본 폴링 간격은 5초입니다. Adobe에서는 기본 자산의 오프로딩 오버헤드를 줄이기 위해 자산 오프로딩 단계의 폴링 간격을 최소 15초로 늘리는 것이 좋습니다.

1. [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)에서 워크플로우 콘솔을 엽니다.

1. 모델 탭을 엽니다.
1. DAM 자산 오프로드 워크플로우 모델을 엽니다.
1. DAM 워크플로우 오프로드 단계의 단계 속성을 엽니다.
1. [공용] 탭을 열고 [기간] 속성 값을 조정합니다.
1. 모델에 변경 사항을 저장합니다.

## 추가 리소스 {#more-resources}

이 문서는 자산 오프로딩에 중점을 둡니다. 오프로드에 대한 추가 설명서는 다음과 같습니다.

* [작업 오퍼](/help/sites-deploying/offloading.md)
* [자산 워크플로우 오프로더](/help/sites-administering/workflow-offloader.md)

