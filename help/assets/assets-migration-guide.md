---
title: 자산을 Adobe Experience Manager Assets으로 일괄 마이그레이션
description: 자산을 AEM으로 가져오고, 메타데이터를 적용하고, 렌디션을 생성하고, 인스턴스를 활성화하는 방법.
contentOwner: AG
feature: 마이그레이션,표현물,자산 관리
role: Architect,Administrator
exl-id: 31da9f3d-460a-4b71-9ba0-7487f1b159cb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1795'
ht-degree: 0%

---

# 자산 마이그레이션 안내서 {#assets-migration-guide}

자산을 AEM으로 마이그레이션할 때 고려해야 할 몇 가지 단계가 있습니다. 현재 홈에서 자산 및 메타데이터를 추출하는 것은 구현 간에 다양하므로 이 문서의 범위를 벗어납니다. 대신, 이 문서에서는 이러한 자산을 AEM으로 가져오고, 메타데이터를 적용하고, 렌디션을 생성하고, 자산을 활성화하거나 게시하는 방법에 대해 설명합니다.

## 전제 조건 {#prerequisites}

아래 설명된 단계를 수행하기 전에 [자산 성능 조정 팁](performance-tuning-guidelines.md)에 대한 지침을 검토하고 구현합니다. 최대 동시 작업 구성과 같은 많은 단계는 로드 중인 서버의 안정성 및 성능을 향상시킵니다. 시스템이 자산과 함께 로드되면 파일 데이터 저장소 구성과 같은 다른 단계를 수행하기가 어렵습니다.

>[!NOTE]
>
>다음 자산 마이그레이션 도구는 Adobe Experience Manager의 일부가 아닙니다. Adobe 고객 지원 센터는 이러한 도구를 지원하지 않습니다.
>
>* ACS AEM Tools Tag Maker
>* ACS AEM 도구 CSV 자산 가져오기
>* ACS Commons Bulk Workflow Manager
>* ACS Commons Fast Action Manager
>* 합성 워크플로우

>
>
이 소프트웨어는 오픈 소스이며 [Apache v2 License](https://adobe-consulting-services.github.io/pages/license.html)에서 다룹니다. 질문하거나 문제를 보고하려면 ACS AEM 도구에 대한 [GitHub 문제](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) 및 [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues)를 방문하십시오.

## AEM {#migrate-to-aem}으로 마이그레이션

자산을 AEM으로 마이그레이션하려면 몇 가지 단계가 필요하며 단계적인 프로세스로 간주해야 합니다. 마이그레이션 단계는 다음과 같습니다.

1. 워크플로우를 비활성화합니다.
1. 태그를 로드합니다.
1. 자산 수집
1. 표현물을 처리합니다.
1. 자산을 활성화합니다.
1. 워크플로우를 활성화합니다.

![chlimage_1-223](assets/chlimage_1-223.png)

### 워크플로우 비활성화 {#disable-workflows}

마이그레이션을 시작하기 전에 `DAM Update Asset` 워크플로우에 대한 런처를 비활성화합니다. 모든 자산을 시스템에 수집한 다음 워크플로우를 일괄로 실행하는 것이 가장 좋습니다. 마이그레이션이 진행되는 동안 이미 라이브 상태인 경우, 이러한 활동을 오프 시간 동안 실행하도록 예약할 수 있습니다.

### 태그 로드 {#load-tags}

이미지에 적용하는 태그 분류법이 이미 있을 수 있습니다. CSV 자산 가져오기 및 메타데이터 프로필 기능과 같은 도구를 사용하면 자산에 태그 적용을 자동화하는 데 도움이 될 수 있습니다. 그 전에 Experience Manager에서 태그를 추가합니다. [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) 기능을 사용하면 시스템에 로드된 Microsoft Excel 스프레드시트를 사용하여 태그를 채울 수 있습니다.

### 자산 처리 {#ingest-assets}

시스템 내로 자산을 섭취할 때 성능과 안정성은 중요한 문제입니다. Experience Manager에서 많은 데이터를 로드할 때 시스템이 제대로 작동하는지 확인하십시오. 이렇게 하면 데이터를 추가하는 데 필요한 시간이 최소화되고 시스템 오버로드가 방지됩니다. 이렇게 하면 특히 이미 운영 중인 시스템에서 시스템 충돌을 방지할 수 있습니다.

자산을 시스템에 로드하는 방법에는 두 가지가 있습니다.HTTP를 사용하는 푸시 기반 접근 방식 또는 JCR API를 사용하는 가져오기 기반 접근 방식.

#### HTTP {#push-through-http} 를 통해 푸시

Adobe의 Managed Services 팀은 Glutton이라는 도구를 사용하여 고객 환경에 데이터를 로드합니다. Glutton은 한 디렉토리의 모든 자산을 AEM 인스턴스의 다른 디렉토리에 로드하는 작은 Java 애플리케이션입니다. Glutton 대신 Perl 스크립트와 같은 도구를 사용하여 자산을 저장소에 게시할 수도 있습니다.

https를 통해 푸시하는 방법을 사용하는 두 가지 기본 다운사이드가 있습니다.

1. HTTP를 통해 자산을 서버로 전송합니다. 이렇게 하려면 오버헤드가 꽤 발생하고 시간이 많이 소요되므로 마이그레이션을 수행하는 데 시간이 오래 걸립니다.
1. 자산에 적용해야 하는 태그와 사용자 지정 메타데이터가 있는 경우 이 접근 방식을 사용하려면 자산을 가져온 후 이 메타데이터를 자산에 적용하려면 실행해야 하는 두 번째 사용자 지정 프로세스가 필요합니다.

자산을 수집하는 다른 방법은 로컬 파일 시스템에서 자산을 가져오는 것입니다. 그러나 외부 드라이브나 네트워크 공유를 서버에 마운트하여 풀 기반 접근 방식을 수행할 수 없다면 HTTP를 통해 자산을 게시하는 것이 가장 좋습니다.

#### 로컬 파일 시스템 {#pull-from-the-local-file-system}에서 가져오기

[ACS AEM 도구 CSV 자산 가져오기](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html)는 파일 시스템에서 자산을 가져오고 자산을 가져올 CSV 파일에서 자산 메타데이터를 가져옵니다. AEM Asset Manager API는 자산을 시스템으로 가져오고 구성된 메타데이터 속성을 적용하는 데 사용됩니다. 자산은 네트워크 파일 마운트 또는 외부 드라이브를 통해 서버에 마운트되는 것이 좋습니다.

자산을 네트워크를 통해 전송하지 않으면 전반적인 성능이 크게 향상됩니다. 일반적으로 이 방법은 자산을 저장소에 로드하는 가장 효율적인 방법입니다. 또한 도구가 메타데이터 수집을 지원하므로 모든 자산 및 메타데이터를 단일 단계로 가져올 수 있습니다. 별도의 도구 사용과 같이 메타데이터를 적용하는 데에는 다른 단계가 필요하지 않습니다.

### 변환 처리 {#process-renditions}

자산을 시스템에 로드한 후 DAM 자산 업데이트 워크플로우를 통해 자산을 처리하여 메타데이터를 추출하고 렌디션을 생성해야 합니다. 이 단계를 수행하기 전에 필요에 따라 DAM 자산 업데이트 워크플로우를 복제하고 수정해야 합니다. Dynamic Media Classic PTIFF 생성 또는 InDesign 서버 통합과 같은 기본 워크플로우의 일부 단계는 필요하지 않을 수 있습니다.

필요에 따라 워크플로우를 구성한 후 실행할 수 있는 두 가지 옵션이 있습니다.

1. 가장 간단한 방법은 [ACS Commons&#39;Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html)입니다. 이 도구를 사용하면 쿼리를 실행하고 워크플로우를 통해 쿼리 결과를 처리할 수 있습니다. 일괄 처리 크기 설정 옵션도 있습니다.
1. [합성 워크플로우](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html)와 함께 [ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)를 사용할 수 있습니다. 이 접근 방식이 훨씬 더 많이 포함되지만, 서버 리소스 사용을 최적화하는 동시에 AEM 워크플로우 엔진의 오버헤드를 제거할 수 있습니다. 또한 Fast Action Manager는 서버 리소스를 동적으로 모니터링하고 시스템에 배치된 로드를 조절하여 성능을 더욱 향상시킵니다. ACS Commons 기능 페이지에 예제 스크립트가 제공되었습니다.

### 자산 활성화 {#activate-assets}

게시 계층이 있는 배포의 경우 게시 팜에서 자산을 활성화해야 합니다. Adobe은 단일 게시 인스턴스 이상을 실행하는 것이 좋지만 모든 자산을 단일 게시 인스턴스에 복제한 다음 해당 인스턴스를 복제하는 것이 가장 효율적입니다. 많은 수의 자산을 활성화할 때 트리 활성화를 트리거한 후 개입해야 할 수 있습니다. 이유는 다음과 같습니다.활동을 시작할 때 항목이 Sling 작업/이벤트 큐에 추가됩니다. 이 큐의 크기가 약 40,000개의 항목을 초과하기 시작하면 처리 속도가 크게 느려집니다. 이 큐의 크기가 100,000개 항목을 초과하면 시스템 안정성이 저하되기 시작합니다.

이 문제를 해결하려면 [빠른 작업 관리자](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)를 사용하여 자산 복제를 관리할 수 있습니다. 이 작업은 Sling 큐를 사용하지 않고 오버헤드를 낮추면서 작업 로드를 조절하여 서버가 오버로드되지 않도록 합니다. FAM을 사용하여 복제를 관리하는 예는 기능 설명서 페이지에 나와 있습니다.

게시 팜에 자산을 가져오는 기타 옵션은 Jackrabbit의 일부로 도구로 제공되는 [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) 또는 [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)을 사용하는 것입니다. 다른 옵션은 [Grabbit](https://github.com/TWCable/grabbit)이라는 AEM 인프라에 대해 오픈 소스 도구를 사용하는 것입니다. 이 도구를 사용하면 성능보다 성능이 더 빠릅니다.

이러한 접근 방법 중 하나에서 주의해야 할 사항은 작성 인스턴스의 자산이 활성화된 것으로 표시되지 않는다는 것입니다. 활성화 상태가 올바른 자산인 이러한 자산에 대한 플래그를 처리하려면 자산을 활성화됨으로 표시하는 스크립트도 실행해야 합니다.

>[!NOTE]
>
>Adobe은 Grabbit을 유지 관리하거나 지원하지 않습니다.

### 복제 게시 {#clone-publish}

자산이 활성화되면 게시 인스턴스를 복제하여 배포에 필요한 만큼 사본을 만들 수 있습니다. 서버 복제는 매우 간단하지만 기억해야 할 몇 가지 중요한 단계가 있습니다. 게시를 복제하려면

1. 소스 인스턴스와 데이터 저장소를 백업합니다.
1. 인스턴스 및 데이터 저장소의 백업을 대상 위치로 복원합니다. 다음 단계는 모두 이 새 인스턴스를 참조합니다.
1. `sling.id`에 대해 `crx-quickstart/launchpad/felix`에서 파일 시스템 검색을 수행합니다. 이 파일을 삭제합니다.
1. 데이터 저장소의 루트 경로 아래에서 `repository-XXX` 파일을 찾아 삭제합니다.
1. `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` 및 `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config`을 편집하여 새 환경의 데이터 저장소 위치를 가리킵니다.
1. 환경을 시작합니다.
1. 작성자의 복제 에이전트 구성을 업데이트하여 새 인스턴스의 올바른 게시 인스턴스 또는 디스패처 초기화 에이전트를 가리키도록 새 환경에 대한 올바른 디스패처를 가리킵니다.

### 워크플로우 활성화 {#enable-workflows}

마이그레이션을 완료하면 DAM 자산 업데이트 워크플로우의 런처를 다시 활성화하여 지속적인 시스템 사용을 위해 렌디션 생성 및 메타데이터 추출을 지원해야 합니다.

## AEM 배포 간 자산 마이그레이션 {#migrate-between-aem-instances}

거의 일반적이지는 않지만 경우에 따라 많은 양의 데이터를 한 AEM 인스턴스에서 다른 인스턴스로 마이그레이션해야 합니다.예를 들어 AEM 업그레이드를 수행하거나 하드웨어를 업그레이드하거나 AMS 마이그레이션과 같은 새 데이터 센터로 마이그레이션합니다.

이 경우 자산이 이미 메타데이터로 채워지고 렌디션이 이미 생성됩니다. 한 인스턴스에서 다른 인스턴스로 자산을 이동하는 데 집중할 수 있습니다. AEM 인스턴스 간에 마이그레이션할 때 다음 단계를 수행하십시오.

1. 워크플로우 비활성화:Adobe Assets와 함께 표현물을 마이그레이션하고 있으므로 DAM Update Asset에 대한 워크플로우 런처를 비활성화하려고 합니다.

1. 태그 마이그레이션:소스 AEM 인스턴스에 이미 태그가 로드되어 있으므로 컨텐츠 패키지에서 태그를 작성하고 대상 인스턴스에 패키지를 설치할 수 있습니다.

1. 자산 마이그레이션:한 AEM 인스턴스에서 다른 인스턴스로 자산을 이동하는 데 권장되는 두 가지 도구가 있습니다.

   * **Vault Remote Copy** 또는  `vlt rcp`를 사용하면 네트워크에서 vlt를 사용할 수 있습니다. 소스 및 대상 디렉토리를 지정하고 한 인스턴스에서 모든 저장소 데이터를 다운로드하여 다른 인스턴스로 로드할 수 있습니다. Vlt rcp는 [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)에 설명되어 있습니다.
   * **** Grabbitis는 AEM 구현을 위해 Time Warner Cable에서 개발한 오픈 소스 컨텐츠 동기화 도구입니다. vlt rcp에 비해 연속적인 데이터 스트림을 사용하므로 지연 시간이 짧고 vlt rcp보다 2~10배 빠르게 속도가 향상될 것으로 예상됩니다. 또한 Grabbit은 델타 컨텐츠 동기화만 지원하므로 초기 마이그레이션 패스가 완료된 후 변경 사항을 동기화할 수 있습니다.

1. 자산 활성화:AEM으로의 초기 마이그레이션에 대해 설명된 [assets](#activate-assets)활성화 지침을 따르십시오.

1. 복제 게시:새 마이그레이션과 마찬가지로, 단일 게시 인스턴스를 로드하고 복제하는 것이 두 노드에서 컨텐츠를 활성화하는 것보다 더 효율적입니다. [게시 복제 를 참조하십시오.](#clone-publish)

1. 워크플로우 활성화:마이그레이션을 완료한 후 DAM 자산 업데이트 워크플로우에 대한 런처를 다시 활성화하여 지속적인 시스템 사용을 위해 렌디션 생성 및 메타데이터 추출을 지원합니다.
