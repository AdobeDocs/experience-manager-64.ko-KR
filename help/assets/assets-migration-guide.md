---
title: 자산을 Adobe Experience Manager Assets로 일괄 마이그레이션
description: 자산을 AEM으로 가져오고, 메타데이터를 적용하고, 변환을 생성하고, 인스턴스를 게시하도록 활성화하는 방법.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 976d037d701eb7cc61a62e14e554675961d6179c
workflow-type: tm+mt
source-wordcount: '1789'
ht-degree: 0%

---


# 자산 마이그레이션 안내서 {#assets-migration-guide}

자산을 AEM으로 마이그레이션할 때 고려해야 할 몇 가지 단계가 있습니다. 현재 홈에서 에셋과 메타데이터를 추출하는 작업은 구현 간에 다양하므로 이 문서의 범위를 벗어납니다. 대신 이 문서에서는 이러한 자산을 AEM으로 가져오고, 해당 메타데이터를 적용하고, 변환을 생성하고, 자산을 활성화 또는 게시하는 방법에 대해 설명합니다.

## 전제 조건 {#prerequisites}

아래 설명된 단계를 수행하기 전에 [자산 성능 조정 팁](performance-tuning-guidelines.md)에 대한 지침을 검토하고 구현합니다. 최대 동시 작업 구성과 같은 많은 단계는 로드 중인 서버의 안정성과 성능을 향상시킵니다. 시스템에 에셋이 로드되면 파일 데이터 저장소 구성과 같은 다른 단계는 수행하기가 어렵습니다.

>[!NOTE]
>
>다음 에셋 마이그레이션 도구는 Adobe Experience Manager의 일부가 아닙니다. Adobe 고객 지원 센터는 이러한 도구를 지원하지 않습니다.
>
>* ACS AEM Tools Tag Maker
>* ACS AEM 도구 CSV 자산 가져오기
>* ACS 커머스 벌크 워크플로우 관리자
>* ACS 커머스 빠른 작업 관리자
>* 합성 워크플로우

>
>
이 소프트웨어는 오픈 소스이며 [Apache v2 License](https://adobe-consulting-services.github.io/pages/license.html)에서 다룹니다. 질문하거나 문제를 보고하려면 ACS AEM 도구](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) 및 [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues)에 대한 해당 [GitHub 문제를 방문하십시오.

## AEM {#migrate-to-aem}으로 마이그레이션

AEM으로 에셋을 마이그레이션하려면 몇 가지 단계가 필요하며 단계적인 프로세스로 간주해야 합니다. 마이그레이션 단계는 다음과 같습니다.

1. 워크플로우 비활성화.
1. 태그를 로드합니다.
1. 자산 인제스트.
1. 변환을 처리합니다.
1. 자산을 활성화합니다.
1. 워크플로우 활성화.

![chlimage_1-223](assets/chlimage_1-223.png)

### 워크플로 사용 안 함 {#disable-workflows}

마이그레이션을 시작하기 전에 `DAM Update Asset` 작업 과정에 대한 방사포를 비활성화합니다. 모든 자산을 시스템에 인제스트한 다음 워크플로우를 일괄적으로 실행하는 것이 가장 좋습니다. 마이그레이션이 진행되는 동안 이미 라이브된 경우 이러한 활동이 비시간 동안 실행되도록 예약할 수 있습니다.

### 태그 {#load-tags} 로드

이미지에 적용하는 태그 분류법이 이미 있을 수 있습니다. CSV 자산 가져오기 도구 및 메타데이터 프로필 기능과 같은 도구를 사용하여 자산에 대한 태그 적용을 자동화할 수 있습니다. 그 전에 Experience Manager에 태그를 추가합니다. [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) 기능을 사용하면 시스템에 로드된 Microsoft Excel 스프레드시트를 사용하여 태그를 채울 수 있습니다.

### 자산 인제스트 {#ingest-assets}

에셋을 시스템에 인제스트할 때 성능과 안정성은 중요한 문제입니다. Experience Manager에서 많은 데이터를 로드할 때 시스템이 제대로 작동하는지 확인합니다. 이렇게 하면 데이터를 추가하는 데 필요한 시간이 최소화되고 시스템 오버로딩이 방지됩니다. 이는 특히 이미 생산 중인 시스템에서 시스템 충돌을 방지하는 데 도움이 됩니다.

자산을 시스템에 로드하는 방법은 두 가지가 있습니다.HTTP를 사용하는 푸시 기반 접근 방식 또는 JCR API를 사용하는 풀 기반 접근 방식

#### HTTP {#push-through-http}를 통해 푸시

Adobe Managed Services 팀은 Logton이라는 도구를 사용하여 고객 환경에 데이터를 로드합니다. Logton은 AEM 인스턴스의 한 디렉토리에서 다른 디렉토리에 있는 모든 에셋을 로드하는 작은 Java 애플리케이션입니다. 풀톤 대신 Perl 스크립트와 같은 도구를 사용하여 에셋을 저장소에 게시할 수도 있습니다.

https를 통해 푸시하는 접근 방식을 사용하는 두 가지 주요 단점이 있습니다.

1. HTTP를 통해 에셋을 서버로 전송합니다. 이 작업은 약간의 오버헤드가 필요하며 시간이 많이 소요되므로 마이그레이션 수행에 소요되는 시간이 길어집니다.
1. 자산에 적용해야 하는 태그와 사용자 지정 메타데이터가 있는 경우 이 방법을 사용하려면 자산을 가져온 후 이 메타데이터를 자산에 적용하려면 실행해야 하는 두 번째 사용자 지정 프로세스가 필요합니다.

에셋을 인제스트하는 또 다른 방법은 로컬 파일 시스템에서 에셋을 가져오는 것입니다. 그러나 가져오기 기반 접근 방식을 수행하기 위해 외부 드라이브 또는 네트워크 공유를 서버에 마운트할 수 없는 경우 HTTP를 통해 에셋을 게시하는 것이 가장 좋습니다.

#### 로컬 파일 시스템 {#pull-from-the-local-file-system}에서 가져오기

[ACS AEM Tools CSV Asset Importer](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html)는 파일 시스템에서 자산 및 자산 가져오기에 대한 CSV 파일의 자산 메타데이터를 가져옵니다. AEM Asset Manager API는 자산을 시스템으로 가져오고 구성된 메타데이터 속성을 적용하는 데 사용됩니다. 네트워크 파일 마운트 또는 외부 드라이브를 통해 서버에 에셋을 마운트하는 것이 좋습니다.

자산을 네트워크를 통해 전송하지 않으면 전반적인 성능이 크게 향상됩니다. 이 방법은 일반적으로 저장소에 자산을 로드하는 가장 효율적인 방법입니다. 또한 모든 자산 및 메타데이터를 메타데이터 습득 기능이 지원되므로 한 번에 가져올 수 있습니다. 별도의 도구를 사용하는 것과 같이 메타데이터를 적용하는 데는 다른 단계가 필요하지 않습니다.

### 변환 처리 {#process-renditions}

자산을 시스템에 로드한 후 DAM 자산 업데이트 작업 과정을 통해 자산을 처리하여 메타데이터를 추출하고 변환을 생성해야 합니다. 이 단계를 수행하려면 먼저 필요에 맞게 DAM 자산 업데이트 워크플로우를 복제하고 수정해야 합니다. Scene7 PTIFF 생성 또는 InDesign 서버 통합과 같이 기본 워크플로우의 일부 단계는 필요하지 않을 수 있습니다.

필요에 따라 워크플로우를 구성한 후에는 두 가지 옵션을 사용하여 워크플로우를 실행합니다.

1. 가장 간단한 방법은 [ACS Commons의 벌크 워크플로 관리자](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html)입니다. 이 도구를 사용하면 쿼리를 실행하고 워크플로우를 통해 쿼리 결과를 처리할 수 있습니다. 일괄 처리 크기를 설정하는 옵션도 있습니다.
1. [Synthetic Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html)와 함께 [ACS Commons 빠른 작업 관리자](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)를 사용할 수 있습니다. 이러한 접근 방식은 서버 리소스 사용을 최적화하는 동시에 AEM 워크플로우 엔진의 오버헤드를 제거할 수 있습니다. 또한 Fast Action Manager는 서버 리소스를 동적으로 모니터링하고 시스템에 배치한 로드를 조절하여 성능을 더욱 향상합니다. 예제 스크립트는 ACS Commons 기능 페이지에 제공되었습니다.

### 자산 활성화 {#activate-assets}

게시 티어가 있는 배포의 경우 게시 팜에서 자산을 활성화해야 합니다. Adobe에서는 단일 게시 인스턴스 이상을 실행하는 것이 좋지만, 모든 자산을 단일 게시 인스턴스에 복제한 다음 해당 인스턴스를 복제하는 것이 가장 효율적입니다. 대량의 자산을 활성화할 때 트리 활성화를 트리거한 후 개입해야 할 수 있습니다. 그 이유는 다음과 같습니다.활동을 시작하면 항목이 Sling 작업/이벤트 대기열에 추가됩니다. 이 큐의 크기가 약 40,000개 항목을 초과할 때 처리 속도가 크게 느려집니다. 이 큐의 크기가 100,000개 항목을 초과하면 시스템 안정성이 손상되기 시작합니다.

이 문제를 해결하려면 [빠른 작업 관리자](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)를 사용하여 자산 복제를 관리할 수 있습니다. 이는 서버가 과부하가 되지 않도록 작업 로드를 제한하면서 Sling 대기열을 사용하지 않고 오버헤드를 낮추면서 작동합니다. FAM을 사용하여 복제를 관리하는 예는 해당 기능의 설명서 페이지에 나와 있습니다.

게시 팜에 에셋을 가져오기 위한 다른 옵션에는 Jackrabbit의 일부로 제공되는 [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) 또는 [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)을 사용하는 옵션이 있습니다. 또 다른 옵션은 AEM 인프라에 대해 VLT보다 더 빠른 성능을 요구하는 [Grabbit](https://github.com/TWCable/grabbit)이라는 오픈 소스 도구를 사용하는 것입니다.

이러한 접근 방식의 경우, 주의해야 할 사항은 작성자 인스턴스의 에셋이 활성화된 것으로 표시되지 않는다는 것입니다. 이러한 자산에 대한 플래그를 올바른 활성화 상태로 처리하려면 자산을 활성화됨으로 표시하는 스크립트도 실행해야 합니다.

>[!NOTE]
>
>Adobe은 Grabbit를 유지 관리하거나 지원하지 않습니다.

### 복제 게시 {#clone-publish}

자산이 활성화되면 게시 인스턴스를 복제하여 배포에 필요한 만큼 사본을 만들 수 있습니다. 서버 복제는 매우 간단하지만 기억해야 할 몇 가지 중요한 단계가 있습니다. 게시를 복제하려면:

1. 소스 인스턴스와 데이터 저장소를 백업합니다.
1. 인스턴스 및 데이터 저장소의 백업을 대상 위치로 복원합니다. 다음 단계는 모두 이 새 인스턴스를 참조합니다.
1. `sling.id`에 대해 `crx-quickstart/launchpad/felix` 아래에서 파일 시스템 검색을 수행합니다. 이 파일을 삭제합니다.
1. 데이터 저장소의 루트 경로 아래에서 `repository-XXX` 파일을 찾아 삭제합니다.
1. 새 환경의 데이터 저장소 위치를 가리키도록 `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` 및 `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config`을 편집합니다.
1. 환경을 시작합니다.
1. 새 인스턴스에서 올바른 게시 인스턴스 또는 디스패처 플러시 에이전트를 가리키도록 작성자의 복제 에이전트 구성을 업데이트하여 새 환경에 대한 올바른 디스패처를 가리킵니다.

### 워크플로 사용 {#enable-workflows}

마이그레이션이 완료되면 DAM 자산 업데이트 워크플로우에 대한 방사선을 다시 활성화하여 지속적인 시스템 사용을 위해 렌디션 생성 및 메타데이터 추출을 지원할 수 있습니다.

## AEM 배포 간 에셋 마이그레이션 {#migrate-between-aem-instances}

일반적이지는 않지만 AEM 인스턴스에서 다른 인스턴스로 대량의 데이터를 마이그레이션해야 하는 경우가 있습니다.예를 들어 AEM 업그레이드를 수행할 때 하드웨어를 업그레이드하거나 AMS 마이그레이션과 같은 새로운 데이터 센터로 마이그레이션할 수 있습니다.

이 경우 자산은 이미 메타데이터로 채워지고 표현물이 이미 생성됩니다. 한 인스턴스에서 다른 인스턴스로 자산을 이동하는 데 집중할 수 있습니다. AEM 인스턴스 간 마이그레이션 시 다음 단계를 수행합니다.

1. 워크플로우 비활성화:Adobe 자산과 함께 표현물을 마이그레이션하기 때문에 DAM Update Asset에 대한 워크플로우 릴리스를 비활성화할 수 있습니다.

1. 태그 마이그레이션:소스 AEM 인스턴스에 이미 태그가 로드되어 있으므로 콘텐츠 패키지에서 태그를 빌드하고 대상 인스턴스에 패키지를 설치할 수 있습니다.

1. 자산 마이그레이션:한 AEM 인스턴스에서 다른 인스턴스로 자산을 이동하는 데 권장되는 두 가지 도구가 있습니다.

   * **저장소 원격 복사** 또는 네트워크 `vlt rcp`에서 변수를 사용할 수 있습니다. 소스 디렉토리 및 대상 디렉토리를 지정할 수 있고, vlt는 하나의 인스턴스에서 모든 저장소 데이터를 다운로드하고 다른 인스턴스로 로드할 수 있습니다. Vlt rcp는 [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)에 문서화되어 있습니다.
   * **Grabbitis** 는 AEM 구현을 위해 Time Warner Cable에서 개발한 오픈 소스 컨텐츠 동기화 툴입니다. vlt rcp에 비해 연속 데이터 스트림을 사용하기 때문에 지연 시간이 단축되고 vlt rcp에 비해 2-10배 빠른 속도 개선을 주장합니다. 또한 Grabbit는 델타 컨텐츠 동기화만 지원하므로 초기 마이그레이션 통과가 완료된 후 변경 사항을 동기화할 수 있습니다.

1. 자산 활성화:AEM로의 초기 마이그레이션을 위해 문서화된 [자산](#activate-assets)을 활성화하는 지침을 따릅니다.

1. 복제 게시:새 마이그레이션과 마찬가지로, 단일 게시 인스턴스를 로드하고 복제하는 것이 두 노드에서 컨텐츠를 활성화하는 것보다 효율적입니다. [게시 복제 참조](#clone-publish)

1. 워크플로우 활성화:마이그레이션을 완료한 후 DAM 자산 업데이트 워크플로우에 대한 방사포를 다시 활성화하여 지속적인 시스템 사용을 위해 변환 생성 및 메타데이터 추출을 지원할 수 있습니다.
