---
title: AEM Foundation 및 리포지토리
seo-title: AEM Foundation 및 리포지토리
description: Adobe Experience Manager 6.3 AEM 플랫폼 및 리포지토리에 관한 릴리스 노트입니다.
seo-description: Adobe Experience Manager 6.3 AEM 플랫폼 및 리포지토리에 관한 릴리스 노트입니다.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 17%

---

# AEM Foundation 및 리포지토리 {#aem-foundation-repository}

## 변경 사항 목록 {#list-of-changes}

### 저장소 {#repository}

* Oak 세그먼트 Tar MicroKernel

   * 온라인 개정 정리를 위한 빠른 압축 모드(테일 압축)
   * 향상된 쓰기 속도
   * JMXBean을 통해 노출된 세그먼트 작업 상태
   * 오프라인 개정 정리를 위한 예상 기간

* Oak Mongo 마이크로커널

   * MongoMK의 연속 개정 정리 는 예약된 정리 유지 관리를 대체합니다

* 문서 노드에 대한 개정 정리 효율성 향상
* 해결된 문제에 대한 전체 개요는 [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) 및 [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt)를 참조하십시오.

>[!CAUTION]
>
>* AEM 6.3에는 리포지토리 마이그레이션이 필요하므로 Oak Segment Tar의 새 버전이 표시됩니다. 이전 버전의 TarMK에서 업그레이드하거나 다른 유형의 지속성에서 새 Segment Tar를 전환하려는 경우에는 이 단계가 필수입니다. 새 Segment Tar의 이점에 대한 자세한 내용은 [Oak Segment Tar 마이그레이션 FAQ](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar) 를 참조하십시오.

>



### 검색 및 색인 생성 {#search-amp-indexing}

* oak-run(CLI)을 통한 색인 작업에 대한 지원이 향상되었습니다.

   * 인덱스 일관성 검사
   * 인덱싱 통계
   * 인덱스 구성 임/내보내기
   * 재인덱싱

* 전체 시스템 성능을 향상시키기 위해 Lucene 관련 저장소 증가 감소
* 동기 Lucene 속성 인덱스 [(추가 정보)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* 색인 관리자의 Explain Query가 이제 AEM QueryBuilder 구문을 지원합니다.
* 이제 Index Manager가 인덱스 지표를 노출합니다.크기, 마지막 업데이트 및 일관성 확인

### 사용자 인터페이스 {#user-interface}

* UI의 생산성을 높이고 쉽게 사용할 수 있도록 다양한 개선 사항이 작성되었습니다.
* 계층 구조를 빠르게 탐색하는 새 컨텐츠 트리 레일 . 목록 보기와 함께 클래식 UI 상호 작용 모델이 복원됩니다.
* 큰 폴더의 카드 및 목록 보기에서 스크롤이 개선되었습니다.
* 검색 결과와의 상호 작용 개선 - 뒤로 단추가 이전 검색 결과를 복원합니다.
* 특정 레일 열기, 항목 편집, 이동 및 삭제 또는 속성 열기 등 대부분의 일반적인 작업에 대한 추가 키보드 단축키.
* 키보드 단축키를 비활성화(환경 설정에서 활성화/비활성화)하는 기능.
* 7일 후 모든 UI에 상대적인 타임스탬프 표시를 중지합니다(기본 설정에서 기본값 설정).

>[!CAUTION]
>
>* Adobe는 향후 클래식 UI를 개선할 계획이 없습니다. AEM 6.4에는 클래식 UI가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 있는 그대로 사용할 수 있습니다. 클래식 UI는 [더 이상 사용되지 않는 동안에도 계속 지원됩니다](/help/sites-deploying/ui-recommendations.md).

>



### 컨텐츠 배포 {#content-distribution}

* 대규모 볼륨 자산 게시를 지원하도록 복제 성능 향상
* 배포 전송에서 OAuth 2.0 인증 지원
* VLT 패키지의 성능이 개선되었습니다.

### 모니터링 {#monitoring}

* 새로운 시스템 개요에서는 모든 성능 관련 시스템 상태 및 작업에 대한 스냅샷 보기를 제공합니다
* 새 상태 검사:

   * 큰 Lucene 인덱스 감지
   * 비동기 색인 상태
   * 큰 Lucene 색인
   * 쿼리 성능
   * 쿼리 순회 제한
   * 동기화된 시계
   * 시스템 유지 관리 - 개정 정리
   * 시스템 유지 관리 - DataStore GC
   * 시스템 유지 관리 - 연속 개정 GC

* 사용자는 이제 status.zip 다운로드 범위를 정의할 수 있습니다

### 유지 관리 {#maintenance}

* 유지 관리 작업을 사용하여 Lucene 바이너리의 활성 삭제
* MongoDB에 대한 RevisionGC 유지 관리 작업이 이제 연속 개정 정리를 위해 비활성화됩니다. 위의 저장소 섹션을 참조하십시오.
* 버전 삭제 구성을 사용하면 최소 버전 수를 유지할 수 있습니다
* 버전 삭제는 유지 관리 창의 끝에 중지됩니다. 또한 수동으로 시작 및 중지할 수 있으며, 다음 시작을 통해 점진적으로 계속 진행할 수 있습니다.

### 업그레이드 {#upgrade}

* 이전 버전과의 호환성:6.4의 이전 버전과 호환되는 기능에서는 대부분의 경우 사용자 지정 코드가 호환되며, 업그레이드 노력을 줄일 수 있습니다.
* 업그레이드 복잡성 평가:업그레이드의 복잡성을 평가하는 새 패턴 탐지기 도구입니다.
* 지속 가능한 업그레이드:개발 주기 내내 다음 버전으로 효율적이고 원활하게 업그레이드하기 위해 모범 사례를 쉽게 따를 수 있도록 도입된 API 표면 및 컨텐츠 분류 를 참조하십시오.
* 저장소 구조 변경:업그레이드를 용이하게 하고 구현 모범 사례를 홍보할 수 있도록 중요한 재구성(주로 /etc)을 제공합니다. [자세한 내용](/help/sites-deploying/repository-restructuring.md)
* 이러한 기능에 대한 자세한 내용은 [업그레이드 설명서](/help/sites-deploying/upgrade.md)를 참조하십시오.

### 클라우드 서비스 {#cloud-services}

* 이제 Touch UI를 통해 많은 Cloud Services을 구성할 수 있습니다.나머지 항목은 기존 Cloud Services 카드 아래에서 구성할 수 있습니다.
* 사이트 및 자산 폴더는 컨텍스트 인식 방식으로 로드된 Cloud Services으로 구성할 수 있습니다.

### 보안 {#security}

* 여러 사용자 프로필을 지원하는 간소화된 사용자 작성 UI를 제공합니다.
* 사용자를 위한 대규모 그룹 멤버십에 대한 성능이 개선되었습니다.

### 프로젝트 및 워크플로우 {#projects-and-workflows}

* Touch UI 기반 워크플로우 편집기 를 사용하여 워크플로우 모델을 보다 능률적으로 관리할 수 있습니다.
* 유지 관리 작업에서 프로젝트 작업 삭제를 지원합니다.
