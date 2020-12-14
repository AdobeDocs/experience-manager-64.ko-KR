---
title: AEM Sites 릴리스 노트
seo-title: AEM Sites
description: Adobe Experience Manager 6.4 Sites에 관한 릴리스 노트입니다.
seo-description: Adobe Experience Manager 6.4 Sites에 관한 릴리스 노트입니다.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 15%

---


# AEM Sites 릴리스 노트 {#aem-sites-release-notes}

## 사이트 {#sites}

AEM Sites 6.4 개선 사항에 대한 자세한 정보는 다음을 참조하십시오.

### 사이트 관리 {#site-administration}

* 새 컨텐츠 트리 레일을 사용하여 사이트 계층 구조를 빠르게 탐색할 수 있습니다. 목록 보기와 함께 클래식 UI 상호 작용 모델이 복원되어 사이트를 찾습니다.
* 큰 폴더의 카드 및 목록 보기에서의 스크롤이 개선되었습니다.
* 검색 결과와의 상호 작용 개선 - 뒤로 단추를 누르면 이전 검색 결과가 복원됩니다.
* 특정 레일 열기, 페이지 편집, 이동 및 삭제, 속성 열기 등 대부분의 일반적인 작업을 위한 추가 키보드 단축키입니다.
* 키보드 단축키 비활성화(환경 설정에서 활성화/비활성화)
* 7일 이후 모든 UI에 대해 타임스탬프 표시 중지(기본 설정에서 기본값 설정).

### 페이지 편집기 {#page-editor}

* 반응형 사이트 미리 보기를 위해 업데이트된 디바이스 목록(현재 Apple iPhone 8, 8 Plus 및 X, Samsung S7 포함)
* 템플릿 디자인 정보의 기본 위치를 /etc/design에서 /conf의 사이트 특정 설정을 지원하도록 이동했습니다. 이전 AEM 릴리스에서 업그레이드한 고객은 /etc/design을 계속 사용할 수 있습니다.

### 구성 요소 및 템플릿 개발 {#component-amp-template-development}

* 프로젝트 원형 13+의 릴리스 노트는 [Github for release notes](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases)을 참조하십시오.
* HTL 버전 1.3.1의 경우 [Github 릴리스 노트](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1)를 참조하십시오.
* 코어 구성 요소 2.0.4+의 경우 [Github 릴리스 노트](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases)를 참조하십시오.
* 스타일 시스템

   * CSS 클래스를 구성 요소에 할당하고 페이지 편집기의 사용자가 UI를 통해 스타일 하위 세트에서 선택할 수 있도록 하는 완전히 새로운 개념을 추가했습니다.
   * 구성 요소 주위에 렌더링되는 HTML 요소 이름을 정의하는 기능(예:&lt;main>, &lt;aside>

* 레이아웃 컨테이너 그리드 시스템의 경우 [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid)를 참조하십시오.
* 템플릿 편집기 및 정책

   * 이제 정책은 구성 요소당, 컨테이너당, 템플릿별 스타일 시스템 구성을 지원합니다.
   * 편집 가능한 구성 요소의 템플릿에서 레이아웃 정의에 대한 지원 개선

* Reference Site We.Retail 3.0의 경우 [Github 릴리스 노트](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases)를 참조하십시오.

>[!CAUTION]
>
>AEM에는 기존 사용자 정의 코드와의 최대 호환성을 제공하기 위해 jQuery 라이브러리의 버전 1.12.4가 포함됩니다. 알려진 보안 문제를 해결하기 위해 Adobe에서 수정을 완료했습니다.

### 컨텐츠 조각 및 편집기 {#content-fragments-amp-editor}

* 컨텐츠 조각의 기초로 도입된 구조화된 컨텐츠 모델

   * 모델 편집기 UI
   * 컨텐츠 조각 모델에 대해 사전 구성된 데이터 요소(단일 행 텍스트, 여러 줄 텍스트, 숫자, 부울, 날짜&amp;시간, 열거형, 컨텐츠 참조, 태그)

* AEM 컨텐츠 조각 편집기의 유용성 개선

   * 모든 요소 보기 개요
   * 단일 요소를 위한 전체 화면 편집
   * 향상된 서식 있는 텍스트 편집 기능(글머리 기호 목록, 번호 매기기 목록, 들여쓰기, 하이퍼링크, 표, 찾기&amp;바꾸기, 맞춤법 검사)

* AEM 컨텐츠 조각에 대한 향상된 출력 옵션이 추가되었습니다.

   * 핵심 구성 요소의 일부로 새 컨텐츠 조각 구성 요소. [GitHub에서 코드를 참조하십시오.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Sling Model Exporter를 통한 JSON 출력 관련 컨텐츠 서비스 지원

### 경험 조각 {#experience-fragments}

* 구성 요소를 그룹화하고 변형 내에서 쉽게 참조할 수 있도록 하여 경험 조각 변형 간의 컨텐츠를 쉽게 재사용할 수 있도록 경험 조각 구성 요소를 도입했습니다.
* 참조 레일을 통해 경험 조각을 번역 프로젝트에 추가하는 기능을 추가했습니다.
* 타임라인 레일을 통해 경험 조각으로 워크플로우를 시작하는 기능을 추가했습니다.
* 이제 참조 레일에 AEM에서 경험 조각을 사용하는 위치가 표시됩니다.
* 이제 템플릿 위치 구성을 통해 작성자는 경험 조각 템플릿을 사용할 수 있는 항목을 글로벌 또는 폴더 수준에서 정의할 수 있습니다
* 패싯된 검색은 이제 게시됨/게시되지 않음, 소셜 미디어 및 Adobe Target으로 내보내기와 같은 고급 필터링을 지원합니다
* 경험 조각을 Pinterest 또는 Facebook으로 내보낼 때 단일 소셜 미디어 로그인 추가
* Adobe Target과 AEM 경험 조각 통합 경험 조각을 Target에 동기화하면 Target의 Visual Experience Composer와 함께 사용하여 Target이 활성화된 경험에 포함할 수 있는 오퍼가 Adobe Target에 생성됩니다.

### 번역 {#translation}

* AEM 번역 프로젝트의 유용성 향상:

   * 하나의 프로젝트에서 다양한 대상 언어 지원
   * 번역 실행을 자동으로 승격 및 삭제하는 옵션
   * 번역 프로젝트의 반복 실행을 예약하는 옵션(일일, 주별, 월별, 연간)
   * 보다 자세한 상태 정보와 함께 향상된 번역 프로젝트 타일

* AEM에서 로컬 컨텐츠를 편집한 후 타사 번역 관리 시스템에서 번역 메모리를 업데이트하기 위해 역 번역 메모리 업데이트를 도입했습니다.
* 번역 워크플로우에서 그룹화된 언어 루트 지원
* 언어 루트에 임의 이름을 지정하고 ISO 코드에 매핑하기 위해 JCR 속성을 사용하는 기능이 추가되었습니다.
* 이제 고급 번역 업데이트는 언어 마스터 분기에 추가된 새 페이지를 인식합니다.
* 사이트 관리 목록 보기에서 번역 상태 보고를 도입했습니다.

### Multi-Site Management(MSM) {#multi-site-management-msm}

* Oak 기반 인덱스와 메모리 내(LiveCopyIndex)를 사용하여 MSM 확장성을 개선했습니다.

### 론치 {#launches}

* 큰 사이트 트리가 들어 있고 활성 론치가 많이 있는 론치의 성능이 개선되었습니다.
* 여러 루트 페이지로 론치의 자동 홍보 및 게시가 개선되었습니다.
* 반응형 장치 미리 보기가 론치 컨텍스트에서 편집한 페이지로 작동하지 않는 문제를 해결했습니다.

### 컨텐츠 타깃팅 및 시뮬레이션 {#content-targeting-simulation}

* 사이트/컨텍스트에 따라 세그먼트를 구성하기 위한 지원 폴더(CQ-94620)
* 세그먼트에 대한 기본 위치를 /conf로 이동하여 사이트/컨텍스트별 세그먼트 목록을 보유합니다.

### AEM 및 Adobe Target  {#aem-amp-adobe-target-nbsp}

* Adobe Target과 AEM 경험 조각 통합 경험 조각을 Target에 동기화하면 Target의 Visual Experience Composer와 함께 사용하여 Target이 활성화된 경험에 포함할 수 있는 오퍼가 Adobe Target에 생성됩니다.
* 이제 Adobe Target mbox.js 버전 63이 포함되어 있습니다. Adobe에서는 구현을 at.js로 전환하는 것이 좋습니다.
* 이제 at.js version 1.2.2이 포함됩니다. Adobe은 다이내믹 태그 관리(DTM) 또는 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html)을 사용하여 at.js를 사이트에 프로비저닝하는 것이 좋습니다.

### AEM 및 Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5가 이제 포함되어 있습니다. Adobe은 구현을 AppMeasurement.js로 전환하는 것이 좋습니다.
* 이제 AppMeasurement.js 1.8.0이 포함됩니다. Adobe은 다이내믹 태그 관리(DTM) 또는 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) 중 하나를 사용하여 AppMeasurement.js를 사이트에 프로비저닝할 것을 권장합니다.

## Communities 추가 기능 {#communities-add-on}

[Communities 릴리스 노트 페이지](/help/release-notes/communities-release-notes.md)를 참조하십시오.

## 화면 추가 기능 {#screens-add-on}

* 명령 및 제어 및 채널 다운로드를 위해 AEM 게시 서버에 연결할 수 있도록 스크린 플레이어에 대한 지원을 AEM 작성자에게 직접 연결하는 대신 추가했습니다.
* 일정에서 채널 지정을 그룹화하는 기능을 추가했습니다.
* 이제 채널 할당에 시작 및 종료 날짜가 있습니다.
* 이제 장치 대시보드에 플레이어 셸 및 펌웨어 버전이 표시됩니다.
* 장치 대시보드 목록에 플레이어의 연결 상태가 표시됩니다.
* AEM Screens Player에 대한 Google Chrome OS 지원이 추가되었습니다.
* AEM Screens Player용 Microsoft Windows 10 추가
