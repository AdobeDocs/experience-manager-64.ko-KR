---
title: 커뮤니티 구성 요소 안내서
seo-title: Community Components Guide
description: SCF(소셜 구성 요소 프레임워크) 사용을 위한 대화형 개발 도구입니다
seo-description: An interactive development tool to get started with the social component framework (SCF)
uuid: 120e56d1-b93c-4f92-bab4-6bb5e40e0ddf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a777a3f1-b39f-4d90-b9b6-02d3e321a86f
exl-id: 8cdd7b94-b247-4598-bb0f-36c5ec1319ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 2%

---

# 커뮤니티 구성 요소 안내서 {#community-components-guide}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

커뮤니티 구성 요소 안내서는 를 위한 대화형 개발 도구입니다 [SCF(소셜 구성 요소 프레임워크)](scf.md). 사용 가능한 AEM Communities 구성 요소 목록이나 여러 구성 요소로 구성된 더 복잡한 기능 목록을 제공합니다.

이 안내서에서는 각 구성 요소에 대한 기본 정보와 함께 SCF 구성 요소/기능의 작동 방식과 구성 또는 사용자 정의 방법을 실험해 볼 수 있습니다.

각 구성 요소와 관련된 개발 핵심 요소에 대한 자세한 내용은 [기능 및 구성 요소 핵심 사항](essentials.md).

## 시작하기 {#getting-started}

이 안내서는 작성자(localhost:4502) 및 게시(localhost:4503) 인스턴스의 개발 설치에 사용하기 위한 것입니다.

커뮤니티 구성 요소 사이트에는

* [https://&lt;server>:&lt;port>/content/community-components/en.html](http://localhost:4502/content/community-components/en.html)

커뮤니티 구성 요소와의 상호 작용은 다음에 따라 달라집니다.

* 서버(작성자 또는 게시)
* 사이트 방문자가 로그인했는지 여부
* 로그인된 경우 멤버에 할당된 권한
* 기본 SRP인지 여부, [JSRP](jsrp.md), 사용 중

작성자에서 편집 모드로 전환하려면 다음 중 하나를 삽입합니다 `editor.html` 또는 `cf#` 서버 이름 뒤에 첫 번째 경로 세그먼트로 사용됩니다.

* 표준 UI:

   [https://&lt;server>:&lt;port>/editor.html/content/community-components/en.html](http://localhost:4502/editor.html/content/community-components/en.html)

* 클래식 UI:

   [https://&lt;server>:&lt;port>/cf#/content/community-components/en.html](http://localhost:4502/cf#/content/community-components/en.html)

>[!NOTE]
>
>편집 모드에서 작성자의 경우 페이지의 링크가 활성화되어 있지 않습니다.
>
>구성 요소 페이지로 이동하려면 먼저 미리 보기 모드 를 선택하여 링크를 활성화합니다.
>
>구성 요소 페이지가 브라우저에 표시되면 구성 요소의 편집 대화 상자를 열기 위해 편집 모드로 돌아갑니다.
>
>일반 작성 정보에 대해서는 [페이지 작성에 대한 빠른 안내](../../help/sites-authoring/qg-page-authoring.md).
>
>AEM에 익숙하지 않은 경우 다음 문서를 참조하십시오. [기본 처리](../../help/sites-authoring/basic-handling.md).

### 홈 페이지 {#home-page}

이 안내서에서는 페이지 왼쪽에 있는 미리 보기 및 프로토타이핑에 사용할 수 있는 SCF 구성 요소 목록을 제공합니다.

편집 모드에서 작성자 인스턴스에 표시되는 구성 요소 안내서:

![chlimage_1-404](assets/chlimage_1-404.png)

## 구성 요소 페이지 {#component-pages}

페이지 왼쪽의 목록에서 구성 요소를 선택합니다.

![chlimage_1-405](assets/chlimage_1-405.png)

안내서의 본문이 표시됩니다.

1. 제목: 선택한 구성 요소의 이름입니다
1. [클라이언트 측 라이브러리](#client-side-libraries): 하나 이상의 필수 카테고리 목록
1. [포함 가능](scf.md#add-or-include-a-communities-component): 구성 요소가 동적으로 포함될 수 있는 경우 작성 편집 모드에서 상태를 전환할 수 있습니다.

   * 추가된 경우 표시되는 텍스트는 다음과 같습니다. &quot;이 구성 요소는 해당 par 노드를 통해 포함됩니다.&quot;
   * 포함된 경우 표시되는 텍스트는 다음과 같습니다. &quot;이 구성 요소는 동적으로 포함됩니다.&quot;
   * 포함하지 않으면 텍스트가 표시되지 않습니다

1. 샘플 구성 요소 또는 기능: 구성 요소 또는 기능의 활성 인스턴스. 구성 요소가 변경되면 탭 섹션에 제공된 템플릿, CSS 및 데이터에 대한 변경 사항으로 변경될 수 있습니다.

>[!NOTE]
>
>왼쪽에서 선택한 후 구성 요소는 브라우저 창이 너무 좁을 때 구성 요소 목록이 아니라 아래에 표시됩니다.

### 작성자 상호 작용 {#author-interactions}

작성자 인스턴스에서 안내서를 사용하는 경우 해당 대화 상자를 열어 구성 요소를 구성할 수 있습니다. 개발자를 위한 정보는 [구성 요소 및 기능 핵심 사항](essentials.md) 대화 상자 설정은 설명서의 섹션에 설명되어 있습니다. [커뮤니티 구성 요소](author-communities.md) 섹션을 참조하십시오.

커뮤니티 구성 요소 안내서의 경우 일부 구성 요소 대화 상자 설정은 [포함 가능](scf.md#add-or-include-a-communities-component) 상태 전환 기존 리소스 또는 동적으로 포함된 리소스 사용 간을 전환하려면 편집 모드에서 구성 요소와 포함 가능한 텍스트를 모두 선택하고 두 번 클릭하여 편집 대화 상자를 엽니다.

![chlimage_1-406](assets/chlimage_1-406.png)

아래에 **템플릿** 탭:

![chlimage_1-407](assets/chlimage_1-407.png)

* **sling:include로 하위 구성 요소 포함**

   선택 취소하면 구성 요소 가이드는 저장소의 기존 리소스(par 노드의 하위인 jcr 노드)를 사용합니다.

   * 표시되는 텍스트: &quot;이 구성 요소는 해당 par 노드를 통해 포함됩니다.&quot;

   이 확인란을 선택하면 구성 요소 안내서에서 sling을 사용하여 하위 노드의 resourceType(존재하지 않는 리소스)의 구성 요소를 동적으로 포함합니다.

   * 표시되는 텍스트: &quot;이 구성 요소는 동적으로 포함됩니다.&quot;

   기본값은 선택 취소되어 있습니다.

### 게시 상호 작용 {#publish-interactions}

게시 인스턴스에서 안내서를 사용할 때 구성 요소 및 기능을 사이트 방문자(로그인하지 않음)로서, 로그인할 때 다양한 권한이 있는 구성원으로 경험할 수 있습니다.

>[!NOTE]
>
>SRP가 기본적으로 [JSRP](jsrp.md)를 입력하면 게시 인스턴스에 입력한 UGC가 게시물에서만 표시되며 *에서 볼 수 없음 *이 됩니다. [중재](moderate-ugc.md) 작성자 인스턴스의 콘솔.

## 클라이언트측 라이브러리 {#client-side-libraries}

각 구성 요소에 대해 나열된 클라이언트측 라이브러리(clientlibs)는 이러한 라이브러리입니다 *필수* 구성 요소를 페이지에 배치할 때 참조할 수 있도록 해줍니다. clientlibs는 브라우저에서 구성 요소를 렌더링하는 데 사용되는 Javascript 및 CSS의 다운로드를 관리 및 최적화하는 수단을 제공합니다.

자세한 내용은 [커뮤니티 구성 요소용 Clientlibs](clientlibs.md).

## 가장 {#impersonation}

관리자 또는 개발자로 종종 로그인하는 작성자 인스턴스에서 다른 사용자로 로그인한 구성 요소를 경험하려면 왼쪽 텍스트 상자를 사용합니다 **[!UICONTROL 가장 대상]** 버튼을 클릭하여 사용자 이름을 입력하거나 풀다운 목록에서 선택한 다음 버튼을 클릭합니다. 되돌아가기를 클릭하여 로그아웃하고 가장을 종료합니다.

게시 인스턴스를 가장할 필요가 없습니다. 로그인/로그아웃 링크를 사용하여 다음과 같은 다양한 사용자를 가장합니다. [데모 사용자](tutorials.md#demo-users).

## 사용자 지정 {#customization}

활성화되면 각 SCF 구성 요소를 구성 요소의 템플릿, CSS 및 데이터를 일시적으로 수정하여 가능한 사용자 지정을 프로토타이핑하는 데 사용할 수 있습니다.

### 사용자 지정 사용 {#enabling-customization}

>[!NOTE]
>
>**이 도구는 읽기 전용입니다**. 템플릿, CSS 또는 데이터에 대한 편집 내용이 저장소에 저장되지 않습니다.

사용자 지정을 빠르게 테스트하려면 `scg:showIde`속성을 구성 요소 페이지의 컨텐츠 JCR 노드에 추가하고 true로 설정해야 합니다.

작성자 또는 게시 인스턴스에서 관리자 권한으로 로그인한 댓글 구성 요소를 예로 사용합니다.

1. 찾아보기 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   예, [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

1. 구성 요소의 을(를) 선택합니다. `jcr:content` 노드

   예, `/content/community-components/en/comments/jcr:content`

1. 속성 추가

   * **이름** `scg:showIde`
   * **유형** `String`
   * **값** `true`

1. 선택 **[!UICONTROL 모두 저장]**
1. 안내서에서 댓글 페이지를 다시 로드합니다

   [http://localhost:4503/content/community-components/en/comments.html](http://localhost:4503/content/community-components/en/comments.html)

1. 이제 템플릿, CSS 및 데이터에 대한 탭이 3개 있습니다.

![chlimage_1-408](assets/chlimage_1-408.png) ![chlimage_1-409](assets/chlimage_1-409.png)

### 템플릿 탭 {#templates-tab}

템플릿 탭을 선택하여 구성 요소와 연관된 템플릿을 확인합니다.

템플릿 편집기를 사용하면 리포지토리의 구성 요소에 영향을 주지 않고 로컬 편집 내용을 컴파일하고 페이지 맨 위에 있는 샘플 구성 요소 인스턴스에 적용할 수 있습니다.

로컬 편집 시 컴파일을 실행하면 홈에 점을 두고 텍스트를 빨간색으로 표시함으로써 모든 오류가 강조 표시됩니다.

### CSS 탭 {#css-tab}

CSS 탭을 선택하여 구성 요소와 연관된 CSS를 확인합니다.

구성 요소가 여러 구성 요소의 복합체인 경우 일부 CSS가 다른 구성 요소 중 하나 아래에 나열될 수 있습니다.

CSS 편집기를 사용하면 CSS를 수정하고 페이지 맨 위에 있는 샘플 구성 요소 인스턴스에 적용할 수 있습니다.

홈에서 규칙 옆에 있는 를 클릭하여 해당 규칙을 사용하여 DOM의 부분을 강조 표시하도록 규칙을 선택할 수 있습니다.

### 데이터 탭 {#data-tab}

데이터 탭을 선택하여 .social.json 엔드포인트 데이터를 표시합니다. 이 데이터는 편집 가능하며 샘플 구성 요소 인스턴스에 적용됩니다.

구문 오류는 홈통에 표시될 수도 있고 편집기에서 강조 표시될 수도 있습니다.
