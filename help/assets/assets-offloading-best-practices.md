---
title: 자산 오프로딩 우수 사례
description: AEM Assets에서 자산 통합 및 복제 워크플로우를 오프로드하기 위한 권장 사용 사례 및 모범 사례
uuid: 7d08fda2-1c59-44ad-bd35-83d199642e01
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: cdb175f4-a7c6-4d9f-994a-5fc8eca51f03
translation-type: tm+mt
source-git-commit: c0d2172c8797a187e316e45e3f3bea0c6c7a15eb

---


# 자산 오프로딩 우수 사례 {#assets-offloading-best-practices}

>[!WARNING]
>
>이 기능은 AEM 6.4 이상 버전에서 더 이상 사용되지 않으며 AEM 6.5에서 제거됩니다.그에 따라 계획을 수립합니다.

AEM(Adobe Experience Manager)에서 대용량 파일 처리 및 실행 워크플로우를 수행할 때 에셋은 상당한 CPU, 메모리 및 I/O 리소스를 사용할 수 있습니다. 특히 자산 크기, 워크플로우, 사용자 수 및 자산 수집의 빈도는 전체 시스템 성능에 영향을 줄 수 있습니다. 리소스를 많이 사용하는 작업에는 AEM 자산 통합 및 복제 워크플로우가 포함됩니다. 단일 AEM 작성 인스턴스에서 이러한 워크플로우를 집중적으로 사용하면 저작 효율성이 저하될 수 있습니다.

이러한 작업을 전용 작업자 인스턴스로 오프로드하면 CPU, 메모리 및 IO 오버헤드가 줄어듭니다. 일반적으로, 오프로딩(offloading)의 이면에는 집약적인 CPU/메모리/IO 리소스를 사용하는 작업을 전용 작업자 인스턴스에 배포해야 합니다. 다음 섹션에는 자산 오프로딩 권장 사용 사례가 포함됩니다.

## AEM 자산 오프로딩 {#aem-assets-offloading}

AEM Assets는 오프로드를 위한 기본 자산별 워크플로우 확장을 구현합니다. 오프로딩 프레임워크에서 제공하는 일반 워크플로우 익스텐션을 기반으로 구축되지만 구현에 자산별 추가 기능이 포함되어 있습니다. 자산 오프로드의 목표는 업로드된 자산에서 DAM 자산 업데이트 워크플로우를 효율적으로 실행하는 것입니다. 자산 오프로딩을 통해 통합 워크플로우를 보다 효과적으로 제어할 수 있습니다.

## AEM 자산 오프로딩 구성 요소 {#aem-assets-offloading-components}

다음 다이어그램은 자산 오프로딩 프로세스의 기본 구성 요소를 보여 줍니다.

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM 자산 업데이트 오프로드 워크플로우 {#dam-update-asset-offloading-workflow}

DAM 자산 오프로딩 워크플로우는 사용자가 자산을 업로드하는 마스터(작성자)에서 실행됩니다. 이 워크플로우는 일반 워크플로우 실행 프로그램에 의해 트리거됩니다. 업로드된 에셋을 처리하는 대신 이 오프로딩 워크플로우는 항목 *com/adobe/granite/workflow/offloading을 사용하여 새 작업을 만듭니다*. 오프로딩 워크플로우는 대상 워크플로우의 이름(이 경우 DAM 자산 업데이트 워크플로우)과 자산의 작업 페이로드에 대한 경로를 추가합니다. 오프로딩 작업을 만든 후, 마스터의 오프로딩 워크플로우는 오프로딩 작업이 실행될 때까지 기다립니다.

### 작업 관리자 {#job-manager}

작업 관리자는 새 작업을 작업자 인스턴스에 배포합니다. 배포 메커니즘을 디자인할 때는 주제 역량 강화를 고려해야 합니다. 작업의 주제가 활성화된 인스턴스에만 작업을 지정할 수 있습니다. 마스터에서 주제 *com/adobe/granite/workflow/offloading* 을 비활성화하고 작업자가 작업을 작업자에게 할당하도록 작업자를 활성화할 수 있습니다.

### AEM 오프로딩 {#aem-offloading}

오프로드 프레임워크는 작업자 인스턴스에 할당된 작업을 오프로드하는 워크플로우를 식별하고 복제를 사용하여 페이로드(예: 인제스트할 이미지)를 비롯한 작업을 작업자에게 물리적으로 전송합니다.

### 작업 소비자 오프로드 워크플로우 {#workflow-offloading-job-consumer}

작업자가 작업자에게 작업을 작성하면 작업 관리자는 *com/adobe/granite/workflow/offloading* 항목을 담당하는 작업 소비자를 호출합니다. 그런 다음 작업 소비자가 자산에서 DAM 자산 업데이트 워크플로우를 실행합니다.

## Sling 토폴로지 {#sling-topology}

Sling 토폴로지는 AEM 인스턴스를 그룹화하며 기본 지속성과는 별도로 서로를 인식할 수 있도록 합니다. Sling 토폴로지의 이러한 특성을 사용하면 비클러스터형, 클러스터형 및 혼합 시나리오에 대한 토폴로지를 만들 수 있습니다. 인스턴스는 전체 토폴로지에 속성을 표시할 수 있습니다. 프레임워크는 토폴로지의 변경 사항(인스턴스 및 속성)을 수신할 수 있는 콜백을 제공합니다. Sling 토폴로지는 Sling 분산 작업의 기초를 제공합니다.

### 분산된 작업 처리 {#sling-distributed-jobs}

분산 작업을 사용하면 토폴로지 멤버인 인스턴스 집합 간에 작업을 쉽게 배포할 수 있습니다. 슬링 직업들은 능력 개념에 기반을 두고 있다. 작업은 해당 작업 항목으로 정의됩니다. 작업을 실행하려면 인스턴스가 특정 작업 항목에 대한 작업 소비자를 제공해야 합니다. 작업 항목은 배포 메커니즘의 기본 드라이버입니다.

작업은 주제에 대한 작업 소비자를 제공하는 인스턴스에만 배포됩니다. 인스턴스에서 작업 소비자를 활성화/비활성화하여 인스턴스의 기능을 정의하고 배포 메커니즘에 영향을 줄 수 있습니다. 인스턴스의 사용 가능한 작업 소비자가 전체 토폴로지로 브로드캐스트됩니다.

이러한 컨텍스트에서 배포라는 용어는 작업 소비자를 제공하는 특정 인스턴스에 작업을 할당한다는 것을 의미합니다. 인스턴스에 대한 할당이 저장소에 저장됩니다. 즉, 분산 작업은 기본적으로 토폴로지의 모든 인스턴스에 할당할 수 있습니다. 그러나 다른 작업은 동일한 저장소를 공유하는 인스턴스에서만 실행할 수 있습니다. 이는 이러한 작업을 동일한 클러스터의 일부인 인스턴스에서만 실행할 수 있음을 의미합니다. 다른 클러스터의 인스턴스에 할당된 작업은 실행되지 않습니다.

### Granite offloading framework {#granite-offloading-framework}

Granite 오프로드 프레임워크는 Sling 작업 배포를 보완하여 비클러스터형 인스턴스에 할당된 작업을 실행합니다. 배포(인스턴스 할당)를 수행하지 않습니다. 하지만, 클러스터되지 않은 인스턴스로 배포된 Sling 작업을 식별하고 이를 대상 인스턴스로 전송하여 실행합니다. 현재 오프로드는 복제를 사용하여 이 작업 전송을 수행합니다. 작업을 실행하기 위해 오프로드는 입력과 출력을 정의한 다음 작업 페이로드를 작성하는 작업과 결합합니다.

분산 작업은 작업 및 배포 프레임워크를 제공합니다. [MOCK] Granite offloading only care of the transport for the special case where jobs are distributed to non-clustered instances.

전송 외에도 오프로딩 프레임워크는 워크플로우 엔진에 대한 확장 기능을 제공합니다. 이 프레임워크를 사용하면 워크플로우의 일부로 분산 작업을 만들 수 있으며 워크플로우가 시작되기 전에 작업이 완료될 때까지 기다릴 수 있습니다. 워크플로우 엔진의 워크플로우 외부 단계 API를 사용하여 구현됩니다. 익스텐션 중 하나를 사용하면 워크플로우의 일반적인 배포가 용이합니다. 단일 워크플로우 단계 배포는 지원되지 않습니다.

오프로딩 프레임워크에는 전체 토폴로지에서 작업 주제 활성화를 시각화하고 제어할 수 있는 유저 인터페이스(UI)도 포함되어 있습니다. UI를 사용하면 분산 작업 스링의 주제 활성화를 편리하게 구성할 수 있습니다. UI 없이 오프로드를 설정할 수도 있습니다.

## 자산 오프로딩을 위한 일반 지침 및 우수 사례 {#general-guidance-and-best-practices-for-asset-offloading}

모든 구현은 고유하며, 이와 같이, 모든 구현 중에 하나로 모두 맞는 것은 없습니다. 다음 섹션에서는 자산 섭취 오프로딩에 대한 지침과 우수 사례를 제공합니다.

자산 오프로드는 작업 오버헤드를 포함하여 시스템에 오버헤드를 발생시킵니다. 자산 통합 로드와 관련된 문제가 발생하는 경우 먼저 오프로드를 하지 않고 구성을 개선하는 것이 좋습니다. 자산 오프로드로 이동하기 전에 다음 옵션을 고려하십시오.

* 하드웨어 확장
* 워크플로우 최적화
* 일시적인 워크플로우 사용
* 워크플로우에 사용되는 코어 수 제한

에셋 오프로딩이 귀하에게 적합한 접근 방식이라고 결론을 내리면 Adobe는 다음 지침을 제공합니다.

* TarMK 기반 배포 권장
* TarMK 기반 자산 오프로드는 광범위한 가로 크기 조절을 위해 설계되지 않았습니다.
* 작성자와 작업자 간의 네트워크 성능이 만족스러운지 확인

### 배포 오프로드 해제 권장 자산 {#recommended-assets-offloading-deployment}

AEM 및 Oak에서는 몇 가지 배포 시나리오가 가능합니다. 자산 오프로드의 경우 공유 데이터 저장소를 사용한 TarMK 기반 배포를 권장합니다. 다음 다이어그램은 권장 배포에 대한 개요를 설명합니다.

![chlimage_1-56](assets/chlimage_1-56.png)

데이터 저장소 구성에 대한 자세한 내용은 AEM의 [노드 저장소 및 데이터 저장소 구성을 참조하십시오](../sites-deploying/data-store-config.md).

### 자동 에이전트 관리 해제 {#turning-off-automatic-agent-management}

자동 에이전트 관리는 바이너리 없는 복제를 지원하지 않으므로 비활성화하고 새 오프로딩 토폴로지를 설정할 때 혼란을 일으킬 수 있습니다. 또한 바이너리 없는 복제에서는 앞으로 진행되는 복제 흐름을 자동으로 지원하지 않습니다.

1. URL에서 구성 관리자를 엽니다 `http://localhost:4502/system/console/configMgr`.
1. 구성을 `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`)으로 엽니다.
1. 자동 에이전트 관리를 비활성화합니다.

### 전달 복제 사용 {#using-forward-replication}

기본적으로 오프로드 전송은 역복제를 사용하여 작업자에서 마스터로 오프로드된 자산을 다시 가져옵니다. 역방향 복제 에이전트는 바이너리 없는 복제를 지원하지 않습니다. 오프라인으로 로드된 자산을 작업자에서 마스터로 다시 푸시하도록 오프로딩을 구성해야 합니다.

1. 역방향 복제를 사용하여 기본 구성에서 마이그레이션하는 경우 마스터 및 작업자에서 &quot; `offloading_outbox`&quot; 및 &quot; `offloading_reverse_*`&quot;라는 모든 에이전트(&amp;ast;)를 비활성화하거나 삭제합니다.대상 인스턴스의 Sling ID를 나타냅니다.
1. 각 작업자에서 마스터를 가리키는 새 전달 복제 에이전트를 만듭니다. 이 절차는 마스터에서 워커로의 전달 에이전트를 만드는 것과 같습니다. 복제 [에이전트 오프로딩](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) 설정에 대한 지침은 오프로드용 복제 에이전트 만들기를 참조하십시오.
1. ( `OffloadingDefaultTransporter``http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`)에 대한 구성을 엽니다.
1. 속성 값을 `default.transport.agent-to-master.prefix` 에서 `offloading_reverse` 로 변경합니다 `offloading`.

### 작성자 및 작업자 간의 공유 데이터 저장소 및 바이너리 없는 복제 사용 {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

바이너리 없는 복제를 사용하면 에셋 오프로딩 시 전송 오버헤드를 줄일 수 있습니다. 공유 데이터 저장소에 대해 바이너리 없는 복제를 설정하는 방법에 대해서는 AEM의 [노드 저장소 및 데이터 저장소 구성을 참조하십시오](/help/sites-deploying/data-store-config.md). 자산 오프로딩에 대한 절차는 다른 복제 에이전트가 포함된다는 점을 제외하고는 다릅니다. 바이너리 없는 복제는 앞으로 감기 복제 에이전트에서만 작동하므로 모든 오프로딩 에이전트에 대해서도 전방 복제를 사용해야 합니다.

### 전송 패키지 해제 {#turning-off-transport-packages}

기본적으로 오프로드는 오프로드 작업 및 작업 페이로드(원본 자산)가 포함된 컨텐츠 패키지를 생성하고 단일 복제 요청을 사용하여 이 단일 오프로드 패키지를 전송합니다. 바이너리는 패키지를 생성할 때 패키지로 다시 직렬화되므로 이러한 오프로드 패키지를 생성하는 것은 바이너리 없는 복제를 사용할 때 역효과를 냅니다. 이러한 전송 패키지의 사용을 끌 수 있으므로, 각 페이로드 항목에 대해 하나씩, 오프로드 작업 및 페이로드가 여러 복제 요청으로 전송됩니다. 이렇게 하면 바이너리 없는 복제의 이점을 활용할 수 있습니다.

1. http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter에서 OffloadingDefaultTransporter 구성 *요소의* 구성 요소를 [엽니다.](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. 복제 패키지( *default.transport.contentpackage)*&#x200B;속성을 비활성화합니다.

### 워크플로우 모델 전송 비활성화 {#disabling-the-transport-of-workflow-model}

기본적으로 DAM 자산 *오프로딩* 워크플로우는 작업 페이로드에 대해 작업자를 호출할 워크플로우 모델을 추가합니다. 이 워크플로우는 기본적으로 기본 DAM 자산 *업데이트* 모델을 따르므로 이 추가 페이로드를 제거할 수 있습니다.

작업 페이로드에서 워크플로우 모델이 비활성화된 경우, 패키지 관리자와 같은 다른 도구를 사용하여 참조된 워크플로우 모델에 변경 사항을 배포해야 합니다.

워크플로우 모델의 전송을 비활성화하려면 DAM 자산 오프로드 워크플로우를 수정합니다.

1. http://localhost:4502/libs/cq/workflow/content/console.html에서 워크플로우 콘솔을 [엽니다](http://localhost:4502/libs/cq/workflow/content/console.html).
1. 모델 탭을 엽니다.
1. DAM 자산 오프로드 워크플로우 모델을 엽니다.
1. DAM 워크플로우 오프로드 단계의 단계 속성을 엽니다.
1. 인수 탭을 열고 입력에 모델 추가 및 출력에 모델 추가 옵션을 선택 취소합니다.
1. 모델에 변경 사항을 저장합니다.

### 폴링 간격 최적화 {#optimizing-the-polling-interval}

워크플로우의 오프로드는 작업자에서 오프로드된 워크플로우가 완료되도록 폴링하는 마스터의 외부 워크플로우를 사용하여 구현됩니다. 외부 워크플로우 프로세스의 기본 폴링 간격은 5초입니다. Adobe에서는 마스터의 오버로드 오버헤드를 줄이기 위해 자산 오프로드 단계의 폴링 간격을 최소 15초로 늘리는 것이 좋습니다.

1. http://localhost:4502/libs/cq/workflow/content/console.html에서 워크플로우 콘솔을 [엽니다](http://localhost:4502/libs/cq/workflow/content/console.html).

1. 모델 탭을 엽니다.
1. DAM 자산 오프로드 워크플로우 모델을 엽니다.
1. DAM 워크플로우 오프로드 단계의 단계 속성을 엽니다.
1. [공용] 탭을 열고 [기간] 속성의 값을 조정합니다.
1. 모델에 변경 사항을 저장합니다.

## 추가 리소스 {#more-resources}

이 문서는 자산 오프로딩에 중점을 둡니다. 다음은 오프로드에 대한 추가 설명서입니다.

* [작업 오프로딩](/help/sites-deploying/offloading.md)
* [자산 워크플로우 오프로더](/help/sites-administering/workflow-offloader.md)

