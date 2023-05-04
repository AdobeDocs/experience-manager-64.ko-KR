---
title: 페이지 비교
seo-title: Page Diff
description: 페이지 비교 기능을 사용하면 두 페이지를 둘 사이의 차이점이 강조 표시된 상태로 편리하게 나란히 비교할 수 있습니다.
seo-description: The page diff feature allows for the convenient side-by-side comparison of two pages with their differences highlighted.
uuid: cf029ed8-606e-4f12-ac8e-5ea9ebd70b1b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5a771d8c-cc56-4979-aeab-b508755a2078
exl-id: 1b1fa592-a145-4abe-a455-df24d551b937
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 56%

---

# 페이지 비교{#page-diff}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

콘텐츠 작성은 반복적 프로세스입니다. 효율적인 작성을 위해서는 한 이터레이션에서 다른 이터레이션으로 변경된 사항을 확인할 수 있어야 합니다. 한 페이지 버전을 확인한 다음, 다른 버전을 확인하는 것은 비효율적이며 오류가 발생하기 쉽습니다. 작성자는 현재 페이지를 다른 버전과 나란히 쉽게 비교할 수 있기를 바랍니다.

페이지 비교 기능을 사용하면 두 페이지를 둘 사이의 차이점이 강조 표시된 상태로 편리하게 나란히 비교할 수 있습니다.

>[!CAUTION]
>
>AEM 6.4.3 이전 버전을 실행 중인 경우 사용자에게 **수정/만들기/삭제** 노드의 권한 `/content/versionhistory` 를 클릭하여 피쳐를 사용합니다.
>
>이 기능에 대한 자세한 내용은 [개발 및 페이지 비교](/help/sites-developing/pagediff.md#operation-details)를 참조하십시오.

## 사용 {#use}

이러한 병렬 비교에서 비교할 수 있는 내용은 다음과 같습니다.

* [버전](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) - 페이지의 이전 버전과 현재 상태
* [](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page)Live Copy - Live Copy와 블루프린트
* [론치](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) - 론치와 소스
* [](/help/sites-administering/tc-manage.md#comparing-language-copies)언어 사본 - (재)번역 전후 페이지

해당 컨텍스트 내에서 비교를 시작하는 방법에 대한 각 항목을 참조하십시오.

### 차이점 표시 {#presentation-of-differences}

비교하는 콘텐츠에 관계없이 차이점 표시 방법은 동일하게 유지됩니다.

* 비교를 시작할 때 선택한 콘텐츠는 왼쪽(비교 시작 지점)에 표시됩니다.
* 비교 대상 콘텐츠는 오른쪽(선택한 콘텐츠를 비교할 대상)에 표시됩니다.

예를 들어 버전을 비교하는 경우 현재 버전은 왼쪽에 표시되고 이전 버전이 오른쪽에 표시됩니다.

두 페이지의 소스가 브라우저 창 위쪽에 있는 헤더 막대에 명확하게 표시됩니다.

![chlimage_1-355](assets/chlimage_1-355.png)

비교는 구성 요소 및 HTML 수준에서 변경 사항을 검색합니다. 변경된 항목은 다른 색상으로 강조 표시됩니다.

**구성 요소 변경 사항**

* 연한 녹색 - 추가된 구성 요소
* 분홍 - 제거된 구성 요소
* 파란색 - 변경된 구성 요소
* 파란색 - 이동된 구성 요소

참고: 변경된 색상과 이동된 색상은 동일합니다.

**HTML 변경 사항**

* 어두운 녹색 - HTML 추가됨
* 빨간색 - 제거된 HTML

>[!NOTE]
>
>언어 사본을 비교할 때, 번역에서는 모든 내용이 변경되고 강조 표시가 아무런 소용이 없으므로 강조 표시가 비활성화됩니다.

### 전체 화면 및 종료 {#fullscreen-and-exiting}

특정 콘텐츠에 집중할 수 있도록 병렬 비교의 어느 &quot;한 쪽&quot;에 대한 전체 화면 아이콘을 클릭하여 전체 브라우저 창으로 확대할 수 있습니다.

![](do-not-localize/chlimage_1-24.png)

선택한 쪽이 전체 창을 채우지만, 막대는 두 페이지 간에 전환할 수 있도록 맨 위에 남아 있습니다.

![chlimage_1-356](assets/chlimage_1-356.png)

전체 화면 종료 아이콘을 클릭하여 전체 화면 보기를 닫을 수도 있습니다.

![](do-not-localize/chlimage_1-25.png)

언제든지 헤더에서 [닫기] 버튼을 클릭하여 병렬 비교를 종료할 수 있습니다.

## 제한 사항 {#limitations}

페이지 차이 가 예상대로 차이를 감지하지 못하는 경우가 있습니다.

* 버전과 론치를 비교할 때, 탐색 표시, 메뉴, 제품 목록 또는 로고(콘텐츠를 렌더링하기 위해 사이트 구조에 의존하는 구성 요소)와 같은 동적 구성 요소는 고려되지 않습니다.
* 버전 비교 시 액세스 제어 정책 및 Live Copy 관계가 다시 만들어지지 않습니다.
* alt, title 또는 src 속성의 수정과 같이 이미지에 변경 사항이 생기면 변경되는 대로 파란색으로 강조 표시됩니다. 그러나 일부 경우에는 이미지에 src 속성의 Base64 표현이 있으며, 두 이미지가 동일하게 보이는데도 비교 시에는 src 특성 비교로 인해 다르게 표시됩니다.
* 비교 시 이미지 회전은 감지할 수 없습니다.
* 페이지가 이동되면 이동 전에 만들어진 버전과 더 이상 비교할 수 없습니다.

   * 차이에 문제가 발생하는 경우 [타임라인](/help/sites-authoring/basic-handling.md#timeline) 페이지를 이동했는지 확인합니다.

>[!NOTE]
>
>버전을 서로 비교할 수 없습니다. 현재 버전만 페이지의 다른 버전과 비교할 수 있습니다. 현재 버전은 항상 변경 사항이 강조 표시된 버전입니다.

>[!NOTE]
>
>페이지 차이 메커니즘 작업 및 페이지 차이에 영향을 줄 수 있는 제한 사항에 대한 자세한 내용은 [개발자 설명서](/help/sites-developing/pagediff.md) 이 기능에 대해 자세히 알아보십시오.
