---
title: 커뮤니티 기능
seo-title: 커뮤니티 기능
description: 커뮤니티 기능 콘솔에 액세스하는 방법 알아보기
seo-description: 커뮤니티 기능 콘솔에 액세스하는 방법 알아보기
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 3%

---

# 커뮤니티 기능 {#community-functions}

커뮤니티 경험에서 예상되는 기능 유형은 잘 알려져 있습니다. 커뮤니티 기능은 커뮤니티 기능으로 사용할 수 있습니다. 기본적으로 이 구성 요소는 작성 모드에서 페이지에 구성 요소를 추가하는 것 이상이 필요한 커뮤니티 기능을 구현하기 위해 사전에 연결된 하나 이상의 페이지입니다. 커뮤니티 사이트가 [작성된 ](sites-console.md)커뮤니티 사이트 템플릿](sites.md)의 구조를 정의하는 데 사용되는 빌딩 블록입니다.[

커뮤니티 사이트가 만들어지면 표준 [AEM 작성 모드](../../help/sites-authoring/editing-content.md)를 사용하여 결과 페이지에 컨텐츠가 추가될 수 있습니다.

커뮤니티 기능 콘솔에서 볼 수 있듯이 많은 커뮤니티 기능을 즉시 사용할 수 있습니다. 향후 릴리스에서 더 많은 커뮤니티 기능이 제공되고 사용자 지정 기능도 제공될 수 있습니다.

>[!NOTE]
>
>[커뮤니티 사이트](sites-console.md), [커뮤니티 사이트 템플릿](sites.md), [커뮤니티 그룹 템플릿](tools-groups.md) 및 [커뮤니티 함수](functions.md)를 만드는 콘솔은 작성 환경에서만 사용할 수 있습니다.

## 커뮤니티 기능 콘솔 {#community-functions-console}

작성 환경에서 커뮤니티 기능 콘솔에 도달하려면

* 전역 탐색에서: **[!UICONTROL 도구 > 커뮤니티 > 커뮤니티 함수]**

![chlimage_1-379](assets/chlimage_1-379.png)

## 사전 빌드된 함수 {#pre-built-functions}

다음은 AEM Communities과 함께 제공되는 기능에 대한 간략한 설명입니다. 각 함수는 [커뮤니티 사이트 템플릿](sites.md)에 쉽게 통합되는 기능에 연결된 커뮤니티 구성 요소가 포함된 하나 이상의 AEM 페이지로 구성됩니다.

커뮤니티 사이트 템플릿은 로그인, 사용자 프로필, 알림, 메시지, 사이트 메뉴, 검색, 테마 및 브랜딩 기능을 포함한 커뮤니티 사이트의 구조를 제공합니다.

### 제목 및 URL 설정 {#title-and-url-settings}

**** 제목 및  **** URL은 모든 커뮤니티 기능에 공통되는 속성입니다.

커뮤니티 사이트 템플릿에 커뮤니티 함수가 추가되거나 [이 커뮤니티 사이트의 구조를 수정](sites-console.md#modifying-site-properties)할 때 추가되면 제목 및 URL이 구성될 수 있도록 함수의 대화 상자가 열립니다.

#### 구성 기능 세부 사항 {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL 제목]**
(
*필수*) 사이트의 기능 메뉴에 나타나는 텍스트입니다

* **[!UICONTROL URL]**
(*필수*) URI를 생성하는 데 사용되는 이름입니다. 이름은 AEM 및 JCR에서 지정한 [이름 지정 규칙](../../help/sites-developing/naming-conventions.md)을 준수해야 합니다.

예를 들어, [시작하기](getting-started.md) 자습서(다음의 경우)에서 만든 사이트를 사용합니다.

* 제목 = 웹 페이지
* URL = page

그런 다음 페이지의 URL은 http://local_host:4503/content/sites/engage/en/page.html 이고 페이지의 메뉴 링크는 다음과 같이 나타납니다.

![chlimage_1-381](assets/chlimage_1-381.png)

### 활동 스트림 기능 {#activity-stream-function}

활동 스트림 함수는 [활동 스트림 구성 요소](activities.md)가 있는 페이지에 모든 보기(모든 활동, 사용자 활동 및 후속)가 선택되어 있습니다. 개발자용 [Activity Stream Essentials](essentials-activities.md)도 참조하십시오.

템플릿에 추가하면 다음 대화 상자가 열립니다.

#### 구성 기능 세부 사항 {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL &quot;내 활동&quot;]**
보기 표시이 확인란을 선택하면 활동 페이지에 현재 구성원이 커뮤니티 내에서 생성한 활동을 기준으로 하는 탭이 포함됩니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL &quot;모든 활동&quot;]**
보기 표시이 확인란을 선택하면 활동 페이지에 현재 구성원이 액세스할 수 있는 커뮤니티 내에서 생성된 모든 활동이 포함된 탭이 포함됩니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL &quot;뉴스 피드&quot;]**
보기 표시이 옵션을 선택하면 활동 페이지에 현재 구성원이 따르는 활동을 필터링하는 탭이 포함됩니다. 기본값이 선택되어 있습니다.

### 지정 기능 {#assignments-function}

지정 함수는 [커뮤니티 사이트(](overview.md#enablement-community))를 정의하는 기본 기능입니다. 커뮤니티 구성원에게 지원 리소스를 할당할 수 있습니다. 개발자용 [Assignment Essentials](essentials-assignments.md)도 참조하십시오.

이 함수는 [지원 추가 기능](enablement.md)의 기능으로 사용할 수 있습니다. 지원 추가 기능을 사용하려면 프로덕션 환경에서 사용할 추가 라이선스가 필요합니다.

템플릿에 추가되면 유일한 구성은 [제목 및 URL 설정](#title-and-url-settings)에 대한 것입니다.

### 블로그 기능 {#blog-function}

블로그 기능은 [블로그 구성 요소](blog-feature.md)에 태깅, 파일 업로드, 팔로우, 자기편집, 투표 및 중재를 위해 구성된 페이지가 있습니다. 개발자용 [블로그 필수 요소용](blog-developer-basics.md)도 참조하십시오.

템플릿에 추가하면 다음 대화 상자가 열립니다.

![chlimage_1-383](assets/chlimage_1-383.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL 권한이 있는 구성원]**
허용 이 확인란을 선택하면 권한이 있는 구성원이 권한이 있는 구성원 그룹을 선택하여 문서를 만들  [수 있습니다](users.md#privileged-members-group). 선택하지 않으면 모든 커뮤니티 구성원이 만들 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 파일 업로드]**
허용이 선택된 경우, 구성원이 파일을 업로드할 수 있는 기능이 블로그에 포함됩니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 스레드]**
답글 허용이 선택되어 있지 않으면 블로그에 문서에 대한 답글(댓글)을 허용하지만 댓글에 대한 답글은 허용되지 않습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 주요]**
콘텐츠 허용 [을 선택하면 아이디어를 주요 콘텐츠로 식별할 수 ](featured.md)있습니다. 기본값이 선택되어 있습니다.

### 달력 기능 {#calendar-function}

달력 함수는 [달력 구성 요소](calendar.md)이 태깅을 허용하도록 구성된 페이지입니다. 개발자용 [달력 Essentials](calendar-basics-for-developers.md)도 참조하십시오.

템플릿에 추가하면 다음 대화 상자가 열립니다.

![chlimage_1-384](assets/chlimage_1-384.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL 고정]**
허용이 선택된 경우 포럼에서는 주제 응답을 주석 목록의 시작 부분에 고정시킬 수 있습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 권한이 있는 구성원]**
허용 이 확인란을 선택하면 권한이 있는 구성원이 권한이 있는 구성원 그룹을 선택하여 문서를 만들  [수 있습니다](users.md#privileged-members-group). 선택하지 않으면 모든 커뮤니티 구성원이 만들 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 파일 업로드]**
허용이 선택된 경우, 구성원이 파일을 업로드할 수 있는 기능이 블로그에 포함됩니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 스레드]**
답글 허용이 선택되어 있지 않으면 블로그에 문서에 대한 답글(댓글)을 허용하지만 댓글에 대한 답글은 허용되지 않습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 주요]**
콘텐츠 허용 [을 선택하면 아이디어를 주요 콘텐츠로 식별할 수 ](featured.md)있습니다. 기본값이 선택되어 있습니다.

### 카탈로그 기능 {#catalog-function}

카탈로그 함수는 [지원 커뮤니티](overview.md#enablement-community) 구성원이 할당되지 않은 사용 리소스를 검색하는 기능을 제공합니다. 개발자는 [태깅 지원 리소스](tag-resources.md) 및 [카탈로그 필수 패키지](catalog-developer-essentials.md)를 참조하십시오.

커뮤니티 사이트의 모든 지원 리소스 및 학습 경로는 해당 속성 ` [Show in Catalog](resources.md)`이 true로 설정된 경우 모든 카탈로그에 표시됩니다. 리소스 및 학습 경로를 명시적으로 포함하려면 [사전 필터](catalog-developer-essentials.md#pre-filters)를 카탈로그에 적용해야 합니다.

템플릿에 추가되면 구성에서 사이트 방문자에게 표시되는 태그 필터를 구성하는 데 사용되는 태그 네임스페이스를 지정할 수 있습니다.

![카탈로그](assets/catalogfunc.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL [모든 네임스페이스] 선택]**

   * 선택한 태그 네임스페이스는 카탈로그에 나열된 사용 리소스 목록을 필터링하기 위해 방문자가 선택할 수 있는 태그를 정의합니다.
   * 이 확인란을 선택하면 커뮤니티 사이트에 대해 허용되는 모든 태그 네임스페이스를 사용할 수 있습니다.
   * 선택 취소하면 커뮤니티 사이트에 허용되는 네임스페이스를 하나 이상 선택할 수 있습니다.
   * 기본값이 선택되어 있습니다.

### 주요 콘텐츠 함수 {#featured-content-function}

주요 컨텐츠 함수는 [주요 컨텐츠 구성 요소](featured.md)가 구성되어 주석을 추가 및 삭제할 수 있도록 구성된 페이지입니다.

구성 요소별로 컨텐츠 기능을 허용하거나 허용하지 않을 수 있습니다( [블로그 함수](#blog-function), [달력 함수](#calendar-function), [포럼 함수](#forum-function), [이미지 함수](#ideation-function) 및 [QnA 함수](#qna-function) 참조).

템플릿에 추가되면 유일한 구성은 [제목 및 URL 설정](#title-and-url-settings)에 대한 것입니다.

### 파일 라이브러리 기능 {#file-library-function}

파일 라이브러리 함수는 [파일 라이브러리 구성 요소](file-library.md)가 구성되어 주석을 추가 및 삭제할 수 있도록 구성된 페이지입니다.

템플릿에 추가되면 유일한 구성은 [제목 및 URL 설정](#title-and-url-settings)에 대한 것입니다.

### 포럼 기능 {#forum-function}

포럼 함수는 [포럼 구성 요소](forum.md)가 태깅, 파일 업로드, 후속, 자가 편집, 투표 및 조정을 위해 구성된 페이지입니다.

템플릿에 추가하면 다음 대화 상자가 열립니다.

#### 구성 기능 세부 사항 {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL 고정]**
허용이 선택된 경우 포럼에서는 주제 응답을 주석 목록의 시작 부분에 고정시킬 수 있습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 권한 있는 멤버]**
허용이 선택된 경우 이 포럼에서는 권한이 있는 구성원이 권한이 있는 멤버 그룹을 선택하여 주제 [를 게시할 수 있습니다](users.md#privileged-members-group). 선택하지 않으면 모든 커뮤니티 구성원이 게시할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 파일 업로드]**
허용이 선택된 경우 구성원이 파일을 업로드할 수 있는 기능이 포럼에 포함됩니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 스레드]**
답글 허용이 선택되어 있지 않으면 포럼에 주제에 대한 댓글이 허용되지만 해당 댓글에 대한 답글은 허용되지 않습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 주요]**
콘텐츠 허용 [을 선택하면 아이디어를 주요 콘텐츠로 식별할 수 ](featured.md)있습니다. 기본값이 선택되어 있습니다.

### 그룹 함수 {#groups-function}

>[!CAUTION]
>
>그룹 함수는 *가 아니라*&#x200B;가 사이트 구조 또는 커뮤니티 사이트 템플릿에 있는 *만 함수가 되어야 합니다.*
>
>[페이지 함수](#page-function)와 같은 다른 모든 함수는 먼저 포함되고 나열되어야 합니다.

그룹 기능은 커뮤니티 구성원이 게시 환경의 커뮤니티 사이트 내에서 하위 커뮤니티를 만들 수 있는 기능을 제공합니다.

[설정](sites-console.md#groupmanagement)에 따라 그룹 함수가 [커뮤니티 사이트 템플릿](sites.md)에 포함되는 경우, 그룹은 공개 또는 비공개가 될 수 있으며, 커뮤니티 그룹이 실제로 만들어지는 경우(예: 게시 환경)에 다양한 템플릿을 제공하도록 하나 이상의 커뮤니티 그룹 템플릿을 구성할 수 있습니다. [커뮤니티 그룹 템플릿](tools-groups.md)은 포럼 및 일정 등의 그룹 페이지에 대해 생성되는 커뮤니티 기능을 지정합니다.

커뮤니티 그룹을 만들 때 새 그룹에 대해 구성원 그룹이 동적으로 생성되며, 구성원을 할당하거나 조인할 수 있습니다. 자세한 내용은 [사용자 및 사용자 그룹 관리](users.md)를 참조하십시오.

커뮤니티 [기능 팩 1](deploy-communities.md#latestfeaturepack)부터, 커뮤니티 그룹은 [커뮤니티 사이트 그룹 콘솔](groups.md)을 사용하여 작성 환경에서 만들며, 활성화되면 게시 환경에서 만들 수 있습니다.

템플릿에 추가하면 다음 대화 상자가 열립니다.

![chlimage_1-386](assets/chlimage_1-386.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL 그룹]**
템플릿 선택A 풀다운 메뉴로, 새 커뮤니티 그룹(게시 환경에서)의 향후 작성자가 선택할 수 있는 하나 이상의 활성화된 그룹 템플릿을 선택할 수 있습니다.

* **[!UICONTROL 권한 있는 멤버]**
허용이 선택된 경우 이 포럼에서는 권한이 있는 구성원이 권한이 있는 멤버 보안 그룹을 선택하여 주제 [를 게시할 수만 있습니다](users.md#privileged-members-group). 선택하지 않으면 모든 커뮤니티 구성원이 게시할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 게시 생성]**
허용이 선택된 경우 승인된 커뮤니티 구성원이 게시 환경에서 그룹을 만들 수 있습니다. 선택하지 않으면 새 그룹(하위 커뮤니티)은 커뮤니티 사이트의 그룹 콘솔에서 작성 환경에서만 만들 수 있습니다.

   기본값은 `checked`입니다.

### 관념화 기능 {#ideation-function}

이미지 함수는 [이미지 구성 요소](ideation-feature.md)가 하나 있는 페이지입니다.

템플릿에 추가하면 기본 제목 및 URL 이름과 템플릿에 대한 기본 표시 설정을 지정하는 다음 대화 상자가 열립니다.

![chlimage_1-387](assets/chlimage_1-387.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL 권한 있는 멤버]**
허용이 선택된 경우 이 포럼에서는 권한이 있는 구성원이 권한이 있는 멤버 보안 그룹을 선택하여 주제 [를 게시할 수만 있습니다](users.md#privileged-members-group). 선택하지 않으면 모든 커뮤니티 구성원이 게시할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 파일 업로드]**
허용이 선택되면 구성원이 파일을 업로드할 수 있는 기능이 포함됩니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 스레드]**
답글 허용이 선택되어 있지 않으면 이 아이디어가 주제에 답글(댓글)을 허용하지만 댓글에 답글을 달 수 없습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 주요]**
콘텐츠 허용 [을 선택하면 아이디어를 주요 콘텐츠로 식별할 수 ](featured.md)있습니다. 기본값이 선택되어 있습니다.

### 리더보드 기능 {#leaderboard-function}

리드 보드 함수는 [리드 보드 구성 요소](enabling-leaderboard.md)가 하나 있는 페이지입니다.

**참고**: 리드 보드 구성 요소는 커뮤니티 템플릿 ** 에서 리드 보드 기능을 포함하는 커뮤니티 사이트를 만든 후 추가 구성이 필요합니다. 커뮤니티 사이트에 대한 [점수 및 배지](implementing-scoring.md)의 구성에 따라 리더보드 구성 요소의 [규칙](enabling-leaderboard.md#rules-tab)을 지정해야 합니다.

템플릿에 추가하면 기본 제목 및 URL 이름과 템플릿에 대한 기본 표시 설정을 지정하는 다음 대화 상자가 열립니다.

![chlimage_1-388](assets/chlimage_1-388.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL 배지]**
표시이 확인란을 선택하면 배지 아이콘 열이 리더보드에 포함됩니다.

   기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 배지]**
이름 표시 이 확인란을 선택하면 배지 이름에 대한 열이 리더보드에 포함됩니다.

   기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 표시]**
아바타를 선택하면 멤버의 아바타 이미지가 구성원 프로필에 대한 이름 링크 옆에 있는 리더보드에 포함됩니다.

   기본값은 선택 취소되어 있습니다.

### 페이지 기능 {#page-function}

페이지 함수는 커뮤니티 사이트의 기능에 연결된 빈 페이지를 커뮤니티 사이트에 추가합니다. 로그인, 메뉴, 알림, 메시지, 테마 및 브랜딩. 컨텐츠는 [표준 AEM 작성 모드](../../help/sites-authoring/editing-content.md)를 사용하여 페이지에 추가할 수 있습니다.

템플릿에 추가되면 유일한 구성은 [제목 및 URL 설정](#title-and-url-settings)에 대한 것입니다.

### QnA 기능 {#qna-function}

QnA 함수는 태깅, 파일 업로드, 후속, 자체 편집, 투표 및 조정을 위해 구성된 [QnA 구성 요소](working-with-qna.md)가 있는 페이지입니다.

템플릿에 추가하면 구성에 권한이 있는 구성원에게 제한이 적용됩니다.

![chlimage_1-389](assets/chlimage_1-389.png)

* [제목 및 URL 설정](#title-and-url-settings)을 참조하십시오.
* **[!UICONTROL 고정]**
허용이 선택된 경우 포럼에서는 주제 응답을 주석 목록의 시작 부분에 고정시킬 수 있습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 권한 있는 멤버]**
허용이 선택된 경우 QnA 포럼에서는 권한이 있는 구성원이 권한이 있는 구성원 그룹을 선택하여 질문을 게시할  [수 있도록 합니다](users.md#privileged-members-group). 선택하지 않으면 모든 커뮤니티 구성원이 게시할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 파일 업로드]**
허용이 선택된 경우 QnA 포럼에는 구성원이 파일을 업로드할 수 있는 기능이 포함됩니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 스레드]**
답글 허용이 선택되어 있지 않으면 QnA 포럼에서는 게시된 질문에 대한 댓글(답변)을 허용하지만 응답에 대한 응답은 허용되지 않습니다. 기본값이 선택되어 있습니다.

* **[!UICONTROL 주요]**
콘텐츠 허용 [을 선택하면 아이디어를 주요 콘텐츠로 식별할 수 ](featured.md)있습니다. 기본값이 선택되어 있습니다.

## 커뮤니티 기능 만들기 {#create-community-function}

커뮤니티 함수 콘솔 상단에 있는 `Create Community Function` 아이콘을 선택하여 커뮤니티 기능을 만들 수 있습니다. 동일한 AEM 블루프린트를 기반으로 하는 여러 함수를 만든 다음 작성자 편집 모드에서 열어 고유하게 사용자 지정할 수 있습니다.

![chlimage_1-390](assets/chlimage_1-390.png)

### 커뮤니티 기능 이름 {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

커뮤니티 함수 이름 패널에서 이름, 설명 및 기능이 활성화되었는지 여부를 구성합니다.

* **[!UICONTROL 커뮤니티 함수]**
이름표시 및 저장소에 사용되는 함수 이름입니다

* **[!UICONTROL 커뮤니티 함수]**
설명표시할 함수 설명입니다

* **[!UICONTROL Disabled/]**
Enabled이 함수를 참조할 수 있는지 여부를 제어하는 전환 스위치입니다

### AEM 블루프린트 {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

`AEM Blueprint` 패널에서는 커뮤니티 함수의 기본 구현인 블루프린트를 선택할 수 있습니다.

커뮤니티 기능은 로그인, 사용자 프로필, 알림, 메시지, 사이트 메뉴, 검색, 테마 및 브랜딩 기능을 포함한 커뮤니티 사이트에 포함할 수 있도록 미리 연결되어 있는 하나 이상의 페이지로 구성된 미니 사이트입니다. 함수가 만들어지면 [작성 편집 모드에서 함수](#open-community-function)를 열고 페이지 및/또는 구성 요소 설정을 사용자 지정할 수 있습니다.

커뮤니티 함수는 [블루프린트](../../help/sites-administering/msm-livecopy.md#creatingablueprint)의 [live copy](../../help/sites-administering/msm.md#live-copies)로 구현되므로, 함수를 포함하는 [커뮤니티 사이트 템플릿](sites.md) 또는 [커뮤니티 그룹 템플릿](tools-groups.md)에서 만든 모든 커뮤니티 사이트 페이지에 영향을 주는 함수에 대한 변경 사항을 롤아웃할 수 있습니다. 페이지 수준을 수정하기 위해 상위 블루프린트에서 페이지 연결을 해제할 수도 있습니다.

[다중 사이트 관리자](../../help/sites-administering/msm.md)도 참조하십시오.

### 썸네일 {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

축소판 그림 패널에서 이미지를 업로드하여 [커뮤니티 함수 콘솔](#community-functions-console)에 표시할 수 있습니다.

## 커뮤니티 기능 열기 {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

페이지 컨텐츠를 작성하고 기능 구성 요소의 구성을 수정할 작성자 편집 모드로 전환하려면 `Open Community Function` 아이콘을 선택합니다.

### 구성 요소 구성 {#configuring-components}

커뮤니티 함수는 AEM 블루프린트의 Live Copy로 구현되며, 세부 사항은 [다중 사이트 관리자](../../help/sites-administering/msm.md) 아래에 설명되어 있습니다.

페이지 컨텐츠를 작성할 뿐만 아니라 구성 요소를 구성할 수 있습니다.

만들어진 커뮤니티 사이트의 페이지에서 구성 요소를 구성하는 경우 구성 요소를 구성하려면 [상속](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content)을 취소해야 할 수 있습니다. 구성이 완료되면 상속을 다시 설정해야 합니다.

구성에 대한 자세한 내용은 작성자를 위해 [Communities 구성 요소](author-communities.md)를 방문하십시오.

## 커뮤니티 기능 편집 {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

`Edit Community Function` 아이콘을 선택하여 [커뮤니티 함수 만들기](#create-community-function)와(과) 동일한 패널을 사용하여 함수의 속성을 편집하고, 함수를 활성화하거나 비활성화합니다.
