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
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 17%

---


# AEM Foundation 및 리포지토리 {#aem-foundation-repository}

## 변경 사항 목록 {#list-of-changes}

### 저장소 {#repository}

* Oak 세그먼트 Tar MicroKernel

   * 온라인 개정 정리를 위한 빠른 완료 모드(세부 구성)
   * 향상된 쓰기 속도
   * JMXBean을 통해 노출된 세그먼트 작업 상태
   * 오프라인 개정 정리 예상 기간

* 오크 몬고 마이크로커널

   * MongoMK에 대한 지속적인 개정 정리가 예약된 정리 유지 관리를 대체합니다.

* 문서 노드 수정 효율성 향상
* 수정된 문제에 대한 전체 개요는 [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) 및 [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt)를 참조하십시오.

>[!CAUTION]
>
>* AEM 6.3에는 리포지토리 마이그레이션이 필요하므로 Oak Segment Tar의 새 버전이 표시됩니다. 이전 버전의 TarMK에서 업그레이드하거나 다른 유형의 지속성에서 새 Segment Tar를 전환하려는 경우에는 이 단계가 필수입니다. 새 세그먼트 타르의 이점에 대한 자세한 내용은 [Oak 세그먼트 Tar로 마이그레이션 FAQ](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar)을 참조하십시오.

>



### 검색 및 색인 생성 {#search-amp-indexing}

* Oak-run(CLI)을 통한 인덱싱 작업에 대한 향상된 지원:

   * 색인 일관성 확인
   * 인덱싱 통계
   * 색인 구성 Im/내보내기
   * 다시 색인화

* Lucene 관련 저장소 증가 감소 - 전반적인 시스템 성능 향상
* 동기 Lucene 속성 인덱스 [(추가 정보)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* 색인 관리자에서 쿼리 설명 지원 AEM QueryBuilder 구문
* 이제 색인 관리자가 색인 지표를 노출하고 있습니다.크기, 마지막 업데이트 및 일관성 확인

### 사용자 인터페이스 {#user-interface}

* UI의 생산성을 높이고 사용하기 쉽게 만들기 위해 다양한 개선 사항이 적용되었습니다.
* 새 컨텐츠 트리 레일을 사용하여 계층 구조를 빠르게 탐색할 수 있습니다. 목록 보기와 함께 클래식 UI 상호 작용 모델이 복원됩니다.
* 큰 폴더의 카드 및 목록 보기에서의 스크롤이 개선되었습니다.
* 검색 결과와의 상호 작용 개선 - 뒤로 단추를 누르면 이전 검색 결과가 복원됩니다.
* 특정 레일 열기, 항목 편집, 이동 및 삭제, 속성 열기 등 대부분의 일반적인 작업을 위한 추가 키보드 단축키입니다.
* 키보드 단축키 비활성화(환경 설정에서 활성화/비활성화)
* 7일 이후 모든 UI에 대해 타임스탬프 표시 중지(기본 설정에서 기본값 설정).

>[!CAUTION]
>
>* Adobe는 향후 클래식 UI를 개선할 계획이 없습니다. AEM 6.4에는 클래식 UI가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 있는 그대로 사용할 수 있습니다. 클래식 UI는 [더 보기](/help/sites-deploying/ui-recommendations.md)로 더 이상 사용하지 않는 동안 완전히 지원되는 상태로 유지됩니다.

>



### 컨텐츠 배포 {#content-distribution}

* 대규모 볼륨 자산 게시를 지원하는 복제 성능 향상
* 배포 전송에서 OAuth 2.0 인증 지원
* VLT 패키지의 성능 개선

### 모니터링 {#monitoring}

* 새 시스템 개요는 모든 성능 관련 시스템 상태 및 활동에 대한 스냅샷 보기를 제공합니다.
* 새 상태 검사:

   * 큰 Lucene 인덱스 감지
   * 비동기 인덱싱 상태
   * 큰 Lucene 색인
   * 쿼리 성능
   * 쿼리 순회 제한
   * 동기화된 시계
   * 시스템 유지 관리 - 개정 정리
   * 시스템 유지 관리 - DataStore GC
   * 시스템 유지 관리 - 연속 개정 GC

* 이제 사용자가 status.zip 다운로드 범위를 정의할 수 있습니다.

### 유지 관리 {#maintenance}

* 유지 관리 작업을 사용하여 Lucene 바이너리의 활성 삭제
* MongoDB에 대한 RevisionGC 유지 관리 작업이 이제 연속 개정 정리 대신 비활성화되었습니다. 위의 저장소 섹션을 참조하십시오.
* 버전 삭제 구성을 사용하면 최소 버전 수를 유지할 수 있습니다.
* 버전 삭제는 유지 관리 창의 끝에 중지됩니다. 수동으로 시작 및 중지할 수 있으며 다음 단계부터 점진적으로 계속 진행합니다.

### 업그레이드 {#upgrade}

* 이전 버전과의 호환성:6.4의 이전 버전과 호환되는 기능을 통해 대부분의 경우 사용자 정의 코드가 계속 호환되고 업그레이드 작업이 줄어듭니다.
* 업그레이드 복잡성 평가:새로운 패턴 감지 툴을 사용하여 업그레이드의 복잡성을 평가할 수 있습니다.
* 지속적인 업그레이드:개발 주기 동안 효율적이고 원활한 다음 버전으로 업그레이드하기 위해 모범 사례를 손쉽게 따를 수 있도록 해주는 API 표면 및 컨텐츠 분류 기능
* 저장소 재구성:업그레이드 작업을 용이하게 하고 구현 우수 사례를 촉진하기 위해(주로/등)를 대대적으로 개편합니다. [자세한 내용](/help/sites-deploying/repository-restructuring.md)
* 이러한 기능에 대한 자세한 내용은 [업그레이드 설명서](/help/sites-deploying/upgrade.md)를 참조하십시오.

### 클라우드 서비스 {#cloud-services}

* 이제 터치 UI를 통해 많은 Cloud Services을 구성할 수 있습니다.나머지 항목은 이전 Cloud Services 카드 아래에 구성할 수 있습니다.
* 사이트 및 자산 폴더는 컨텍스트 인식 방식으로 로드된 Cloud Services으로 구성할 수 있습니다.

### 보안 {#security}

* 여러 사용자 프로파일에 대한 지원을 통해 사용자 생성 UI가 개선되고 간소화되었습니다.
* 사용자를 위한 대규모 그룹 구성원 자격 성능이 개선되었습니다.

### 프로젝트 및 워크플로우 {#projects-and-workflows}

* UI 기반의 워크플로우 편집기를 사용하여 보다 간소화된 방식으로 워크플로우 모델을 관리할 수 있습니다.
* 유지 관리 작업의 프로젝트 작업 삭제를 지원합니다.

