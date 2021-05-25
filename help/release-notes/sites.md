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
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 15%

---

# AEM Sites 릴리스 노트 {#aem-sites-release-notes}

## 사이트 {#sites}

AEM Sites 6.4 개선 사항에 대한 자세한 정보는 다음을 참조하십시오.

### 사이트 관리 {#site-administration}

* 사이트 계층 구조를 빠르게 탐색하는 새 컨텐츠 트리 레일 . 목록 보기와 함께 클래식 UI 상호 작용 모델이 복원되어 사이트를 탐색합니다.
* 큰 폴더의 카드 및 목록 보기에서 스크롤이 개선되었습니다.
* 검색 결과와의 상호 작용 개선 - 뒤로 단추가 이전 검색 결과를 복원합니다.
* 특정 레일 열기, 페이지 편집, 이동 및 삭제 또는 속성 열기 등 대부분의 일반적인 작업에 대한 추가 키보드 단축키.
* 키보드 단축키를 비활성화(환경 설정에서 활성화/비활성화)하는 기능.
* 7일 후 모든 UI에 상대적인 타임스탬프 표시를 중지합니다(기본 설정에서 기본값 설정).

### 페이지 편집기 {#page-editor}

* 응답형 사이트 미리 보기를 위해 Apple iPhone 8, 8 Plus 및 X, Samsung S7을 포함하여 장치 목록을 업데이트했습니다
* /conf에서 사이트 특정 설정을 지원하도록 템플릿 디자인 정보의 기본 위치를 /etc/design에서 로 이동했습니다. 이전 AEM 릴리스에서 업그레이드하는 고객은 /etc/design을 계속 사용할 수 있습니다.

### 구성 요소 및 템플릿 개발 {#component-amp-template-development}

* Project Archetype 13+의 경우 [Github 릴리스 노트](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases)를 참조하십시오.
* HTL 버전 1.3.1의 경우 [Github 릴리스 노트](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1)를 참조하십시오.
* 코어 구성 요소 2.0.4+의 경우 [Github 릴리스 노트](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases)를 참조하십시오.
* 스타일 시스템

   * CSS 클래스를 구성 요소에 할당하고 페이지 편집기의 사용자가 UI를 통해 스타일 하위 세트에서 선택할 수 있도록 하는 완전히 새로운 개념을 추가했습니다
   * 구성 요소 주위에 렌더링되는 HTML 요소 이름을 정의하는 기능이 추가되었습니다(예: ).&lt;main>, &lt;aside>

* 레이아웃 컨테이너 그리드 시스템의 경우 [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid)를 참조하십시오.
* 템플릿 편집기 및 정책

   * 이제 정책은 템플릿당 구성 요소당, 컨테이너별, 템플릿별 스타일 시스템 구성을 지원합니다.
   * 편집 가능한 구성 요소에서 템플릿의 레이아웃 정의에 대한 지원이 개선되었습니다

* Reference Site We.Retail 3.0의 경우 [Github 릴리스 노트](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases)를 참조하십시오.

>[!CAUTION]
>
>AEM에는 기존 사용자 정의 코드와의 최대 호환성을 제공하기 위해 jQuery 라이브러리의 버전 1.12.4가 포함됩니다. 알려진 보안 문제를 해결하기 위해 Adobe에서 수정을 완료했습니다.

### 컨텐츠 조각 및 편집기 {#content-fragments-amp-editor}

* 컨텐츠 조각의 기반으로서 구조화된 컨텐츠 모델 을 도입했습니다

   * 모델 편집기 UI
   * 컨텐츠 조각 모델의 사전 구성된 데이터 요소(단일 행 텍스트, 여러 줄 텍스트, 숫자, 부울, 날짜 및 시간, 열거형, 컨텐츠 참조, 태그)

* AEM 컨텐츠 조각 편집기의 유용성을 개선했습니다

   * 모든 요소 보기 개요
   * 단일 요소에 대한 전체 화면 편집
   * 향상된 리치 텍스트 편집 기능(글머리 기호 목록, 번호 목록, 들여쓰기, 하이퍼링크, 표, 찾기 및 바꾸기, 맞춤법 검사)

* AEM 컨텐츠 조각에 대한 향상된 출력 옵션이 추가되었습니다

   * 핵심 구성 요소의 일부로서 새 컨텐츠 조각 구성 요소입니다. [GitHub에서 코드를 참조하십시오.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Sling Model Exporter를 통해 JSON 출력을 사용한 컨텐츠 서비스 지원

### 경험 구성요소 {#experience-fragments}

* 구성 요소를 그룹화하고 변형 내에서 쉽게 참조할 수 있도록 하여 경험 조각 변형 간에 컨텐츠를 쉽게 재사용할 수 있도록 경험 조각 구성 요소가 도입되었습니다.
* 참조 레일을 통해 번역 프로젝트에 경험 조각을 추가하는 기능을 추가했습니다
* 타임라인 레일을 통해 경험 조각으로 워크플로우를 시작하는 기능을 추가했습니다
* 이제 참조 레일에 AEM에서 경험 조각을 사용 중인 위치가 표시됩니다
* 템플릿 위치 구성을 통해 작성자는 전역 또는 폴더 수준에서 경험 조각 템플릿을 사용할 수 있도록 정의할 수 있습니다
* 이제 패싯 검색은 게시됨/게시되지 않음 과 같은 고급 필터링을 소셜 미디어 및 Adobe Target으로 내보냅니다
* 경험 구성요소를 Pinterest 또는 Facebook으로 내보낼 때 단일 소셜 미디어 로그인이 추가되었습니다
* Adobe Target과 통합된 AEM 경험 구성요소 경험 조각을 Target에 동기화하면 Adobe Target에서 Target의 시각적 경험 작성기와 함께 사용하여 Target이 활성화된 경험에 포함할 수 있는 오퍼가 생성됩니다.

### 번역 {#translation}

* AEM 번역 프로젝트의 유용성이 개선되었습니다.

   * 하나의 프로젝트에서 여러 타겟 언어 지원
   * 번역 실행을 자동으로 승격 및 삭제하는 옵션
   * 번역 프로젝트의 반복 실행을 예약하는 옵션(일별, 주별, 월별, 연간)
   * 향상된 번역 프로젝트 타일 및 자세한 상태 정보

* AEM에서 로컬 컨텐츠를 편집한 후 타사 번역 관리 시스템에서 번역 메모리를 업데이트하기 위해 역방향 번역 메모리 업데이트가 도입되었습니다
* 이제 번역 워크플로우에서 그룹화된 언어 루트를 지원합니다
* 언어 루트에 임의 이름을 지정하고 ISO 코드에 매핑하기 위해 JCR 속성을 사용하는 기능이 추가되었습니다
* 이제 스마트 번역 업데이트에서는 언어 마스터 분기에 추가된 새 페이지를 인식합니다
* Sites 관리 목록 보기에서 번역 상태 보고가 도입되었습니다

### Multi-Site Management(MSM) {#multi-site-management-msm}

* Oak 기반 색인과 in-memory (LiveCopyIndex)를 사용하여 MSM 확장성을 개선했습니다.

### 론치 {#launches}

* 활성 론치가 많은 경우, 큰 사이트 트리가 포함된 론치의 성능이 개선되었습니다
* 여러 루트 페이지를 사용하여 론치의 자동 홍보 및 게시가 개선되었습니다.
* 응답형 장치 미리 보기가 실행 컨텍스트에서 편집된 페이지에서 작동하지 않는 문제를 수정했습니다.

### 컨텐츠 타깃팅 및 시뮬레이션 {#content-targeting-simulation}

* 사이트/컨텍스트에 따라 세그먼트를 구성하기 위해 폴더를 지원합니다(CQ-94620)
* 세그먼트의 기본 위치를 사이트/컨텍스트별 세그먼트 목록이 있도록 /conf로 이동했습니다.

### AEM 및 Adobe Target  {#aem-amp-adobe-target-nbsp}

* Adobe Target과 통합된 AEM 경험 구성요소 경험 조각을 Target에 동기화하면 Adobe Target에서 Target의 시각적 경험 작성기와 함께 사용하여 Target이 활성화된 경험에 포함할 수 있는 오퍼가 생성됩니다.
* 이제 Adobe Target mbox.js 버전 63이 포함되어 있습니다. Adobe은 구현을 at.js로 전환할 것을 권장합니다.
* 이제 at.js version 1.2.2이 포함됩니다. Adobe은 DTM(Dynamic Tag Management) 또는 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) 을 사용하여 at.js를 사이트에 프로비저닝할 것을 권장합니다.

### AEM 및 Adobe Analytics {#aem-amp-adobe-analytics}

* 이제 s_code.js H.27.5가 포함됩니다. Adobe은 구현을 AppMeasurement.js로 전환하도록 권장합니다
* 이제 AppMeasurement.js 1.8.0이 포함됩니다. Adobe은 DTM(Dynamic Tag Management) 또는 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) 을 사용하여 AppMeasurement.js를 사이트에 프로비저닝할 것을 권장합니다.

## Communities 추가 기능 {#communities-add-on}

[Communities 릴리스 노트 페이지](/help/release-notes/communities-release-notes.md)를 참조하십시오.

## 화면 추가 기능 {#screens-add-on}

* 명령 및 제어 및 채널 다운로드를 위해 AEM 게시 서버에 연결할 Screens 플레이어에 대한 지원을 AEM 작성자에게 직접 연결하는 대신 추가했습니다.
* 예약에서 채널 지정을 그룹화하는 기능이 추가되었습니다.
* 이제 채널 할당에 시작 및 종료 날짜가 있습니다
* 이제 장치 대시보드에 플레이어 셸 및 펌웨어 버전이 표시됩니다
* 장치 대시보드 목록에는 플레이어의 연결 상태가 표시됩니다
* AEM Screens Player에 대한 Google Chrome OS 지원이 추가되었습니다
* AEM Screens Player용 Microsoft Windows 10 추가
