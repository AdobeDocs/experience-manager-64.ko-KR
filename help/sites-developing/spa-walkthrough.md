---
title: SPA 소개 및 워크스루
seo-title: SPA Introduction and Walkthrough
description: 이 문서에서는 SPA 개념을 소개하고, 작성용 기본 SPA 애플리케이션을 사용하는 과정을 안내하고, 기본 AEM SPA 편집기와 관련되는 방식을 보여 줍니다.
seo-description: This article introduces the concepts of a SPA and walks through using a basic SPA application for authoring, showing how it relates to the underlying AEM SPA Editor.
uuid: 97a199af-b684-433d-b7b1-a8378513cb3d
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 77b42490-15db-41d5-9757-17009f1c1efd
exl-id: 85179139-a841-42b0-8590-d1fb88c1ebbf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 61%

---

# SPA 소개 및 워크스루{#spa-introduction-and-walkthrough}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

SPA(단일 페이지 애플리케이션)는 웹 사이트 사용자에게 적합한 멋진 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크를 사용하여 사이트를 작성하려고 하며 작성자는 해당 프레임워크를 통해 빌드된 사이트의 AEM 내에서 콘텐츠를 원활하게 편집하려고 합니다.

SPA 편집기는 AEM 내에서 SPA를 지원하는 복합 솔루션을 제공합니다. 이 문서에서는 작성용 SPA 애플리케이션을 사용하는 과정을 안내하고 기본 AEM SPA 편집기와 관련되는 방식을 보여 줍니다.

>[!NOTE]
>
>단일 페이지 애플리케이션(SPA) 편집기 기능을 사용하려면 AEM 6.4 서비스 팩 2 이상이 필요합니다.
>
>SPA 편집기는 SPA 프레임워크 기반 클라이언트측 렌더링(예: React 또는 Angular)이 필요한 프로젝트에 권장되는 솔루션입니다.

## 소개 {#introduction}

### 문서 목표 {#article-objective}

이 문서에서는 SPA 편집기를 독자에게 설명하기 전에 간단한 SPA 애플리케이션을 통해 기본적인 콘텐츠 편집을 시연하여 SPA의 기본 개념을 소개합니다. 그런 다음 페이지 구성을 다루고 SPA 애플리케이션이 AEM SPA 편집기와 관련되는 방식과 상호 작용하는 방법에 대해 자세히 설명합니다.

이 소개 및 워크스루의 목표는 AEM 개발자에게 SPA가 관련이 있는 이유, 일반적인 작동 방식, AEM SPA 편집기에서 SPA를 처리하는 방법과 표준 AEM 애플리케이션과 어떤 차이가 있는지 보여 주는 것입니다.

이 연습은 표준 AEM 기능과 샘플 We.Retail Journal 앱을 기반으로 합니다. 다음 요구 사항을 충족해야 합니다.

* [AEM 버전 6.4(서비스 팩 2 이상 포함)](/help/release-notes/sp-release-notes.md)
* [GitHub에서 사용할 수 있는 샘플 We.Retail Journal 앱을 여기에 설치합니다.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)

>[!CAUTION]
>
>이 문서에서는 [We.Retail 저널 앱](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) 를 사용하십시오. 프로젝트 작업에 사용해서는 안 됩니다.
>
>AEM 프로젝트는 React 또는 Angular를 통해 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 활용해야 합니다.

### SPA란 무엇입니까? {#what-is-a-spa}

단일 페이지 애플리케이션(SPA)은 데이터를 로드하여 페이지를 동적으로 업데이트하는 Ajax 호출을 통해 클라이언트측에서 렌더링되고 주로 JavaScript를 기반으로 하는 기존 페이지와 다릅니다. 페이지와의 사용자 상호 작용을 기반으로 필요에 따라 대부분의 콘텐츠 또는 모든 콘텐츠를 추가 리소스가 비동기적으로 로드된 단일 페이지 로드에서 한 번 검색합니다.

이렇게 하면 페이지 새로 고침의 필요성이 줄어들고 사용자에게 원활하고 빠르며 기본 앱 환경과 같은 경험을 제공할 수 있습니다.

AEM SPA 편집기를 통해 프론트엔드 개발자가 AEM 사이트에 통합할 수 있는 SPA를 만들게 되면 콘텐츠 작성자는 다른 AEM 콘텐츠와 같이 SPA 콘텐츠를 손쉽게 편집할 수 있습니다.

### 왜 SPA입니까? {#why-a-spa}

더 빠르고 유동적이며 기본 애플리케이션과 매우 유사한 SPA는 작동 방법의 특성으로 인해 웹 페이지 방문자뿐만 아니라 마케터와 개발자에게도 매우 매력적인 경험입니다.

![screen_shot_2018-08-20at135550](assets/screen_shot_2018-08-20at135550.png)

**방문자 수**

* 방문자는 콘텐츠와 상호 작용할 때 네이티브와 같은 경험을 원합니다.
* 페이지가 빠를수록 전환될 가능성이 더 높아진다는 명확한 데이터가 있습니다.

**마케터**

* 마케터는 방문자 참여를 유도함으로써 다양하고 네이티브와 같은 경험을 제공하려고 합니다.
* 개인화는 이 경험을 더욱 매력적으로 만들 수 있습니다.

**개발자**

* 개발자는 콘텐츠와 프레젠테이션 사이의 문제를 명확하게 구분하려고 합니다.
* 명확하게 구분하여 시스템을 좀 더 많이 확장 가능하게 하고 독립적인 프론트엔드를 개발할 수 있습니다.

### SPA는 어떻게 작동합니까? {#how-does-a-spa-work}

SPA의 기본 생각은 서버 호출로 인한 지연을 최소화하여 SPA이 기본 애플리케이션의 응답성에 근접하도록 서버에 대한 호출과 종속성을 줄이는 것입니다.

기존 순차적 웹 페이지에서는 직접적인 페이지에 필요한 데이터만 로드합니다. 즉, 방문자가 다른 페이지로 이동하는 경우 서버는 추가 리소스에 대해 호출됩니다. 방문자가 페이지의 요소와 상호 작용하므로 추가 호출이 필요할 수 있습니다. 해당 다중 호출은 페이지가 방문자의 요청을 확인하므로 지연 시간 또는 지연을 파악할 수 있습니다.

![screen_shot_2018-08-20at140449](assets/screen_shot_2018-08-20at140449.png)

방문자가 모바일, 기본 앱에서 예상하는 것에 접근하는 보다 유연한 환경을 위해 SPA은 첫 번째 로드 시 방문자를 위해 필요한 모든 데이터를 로드합니다. 처음에는 시간이 다소 걸릴 수 있지만 서버 호출을 추가할 필요가 없습니다.

클라이언트측에서 렌더링하면 페이지 요소가 더 빨리 반응하고 방문자가 페이지와의 상호 작용이 바로 나타납니다. 페이지 속도를 최대화하기 위해 필요한 추가 데이터는 비동기식으로 호출됩니다.

>[!NOTE]
>
>AEM에서 SPA이 작동하는 방식에 대한 자세한 내용은 문서를 참조하십시오 [AEM에서 SPA 시작하기](/help/sites-developing/spa-getting-started-react.md).
>
>SPA 편집기의 디자인, 아키텍처 및 기술 워크플로우에 대한 자세한 내용은 문서를 참조하십시오 [SPA 편집기 개요](/help/sites-developing/spa-overview.md).

## SPA를 통한 콘텐츠 편집 경험 {#content-editing-experience-with-spa}

AEM SPA 편집기를 활용하기 위해 SPA을 빌드하면 컨텐츠 작성자는 컨텐츠를 편집하고 작성할 때 아무런 차이가 없음을 알려줍니다. 일반적인 AEM 기능을 사용할 수 있고 작성자의 워크플로를 변경할 수 없습니다.

>[!NOTE]
>
>이 연습은 표준 AEM 기능과 샘플 We.Retail Journal 앱을 기반으로 합니다. 다음 요구 사항을 충족해야 합니다.
>
>* [AEM 버전 6.4(서비스 팩 2 포함)](/help/release-notes/sp-release-notes.md)
>* [GitHub에서 사용할 수 있는 샘플 We.Retail Journal 앱을 여기에 설치합니다.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)
>


1. AEM에서 We.Retail 저널 앱을 편집합니다.

   `http://localhost:4502/editor.html/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at142533](assets/screen_shot_2018-06-07at142533.png)

1. 제목 구성 요소를 선택하면 다른 구성 요소에 대해 도구 모음이 표시됩니다. **[!UICONTROL 편집]**&#x200B;을 선택합니다.

   ![screen_shot_2018-06-07at142937](assets/screen_shot_2018-06-07at142937.png)

1. AEM 내에서 콘텐츠를 정상적으로 편집하고 변경 사항이 지속되고 있는지 확인합니다.

   ![screen_shot_2018-06-07at143419](assets/screen_shot_2018-06-07at143419.png)

   >[!NOTE]
   >자세한 내용은 [SPA 편집기 개요](spa-overview.md#requirements-limitations) 즉석 텍스트 편집기 및 SPA에 대한 추가 정보.

1. 에셋 브라우저를 사용하여 새 이미지를 이미지 구성 요소로 드래그 앤 드롭합니다.

   ![screen_shot_2018-06-07at143530](assets/screen_shot_2018-06-07at143530.png)

1. 변경 사항이 지속됩니다.

   ![screen_shot_2018-06-07at143732](assets/screen_shot_2018-06-07at143732.png)

페이지에서 추가 구성 요소 드래그 앤 드롭, 구성 요소 다시 정렬 및 레이아웃 수정과 같은 추가 작성 도구는 SPA이 아닌 모든 응용 프로그램에서 지원됩니다.

>[!NOTE]
>
>SPA 편집기는 애플리케이션의 DOM을 수정하지 않습니다. SPA는 자체 DOM을 담당합니다.
>
>이 작동 방식을 보려면 이 문서의 다음 섹션인 [SPA 앱 및 AEM SPA 편집기](/help/sites-developing/spa-walkthrough.md#spa-apps-and-the-aem-spa-editor)로 계속 진행합니다.

## SPA 앱 및 AEM SPA 편집기 {#spa-apps-and-the-aem-spa-editor}

SPA이 최종 사용자에 대해 동작하는 방식을 수행한 다음 SPA 페이지를 검사하면 AEM에서 SAP 앱이 SPA 편집기와 작동하는 방식을 더 잘 이해할 수 있습니다.

### SPA 애플리케이션 사용 {#using-an-spa-application}

1. 게시 서버에서 또는 옵션을 사용하여 We.Retail 저널 애플리케이션을 로드합니다 **[!UICONTROL 게시됨으로 보기]** 에서 **페이지 정보** 메뉴 아래의 페이지 편집기:

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-08at102650](assets/screen_shot_2018-06-08at102650.png)

   하위 페이지, 날씨 위젯 및 문서에 대한 탐색을 포함한 페이지 구조를 확인합니다.

1. 메뉴를 사용하여 하위 페이지로 이동한 다음 페이지가 새로 고칠 필요 없이 즉시 로드되는지 확인합니다.

   ![screen_shot_2018-06-08at102815](assets/screen_shot_2018-06-08at102815.png)

1. 브라우저 기본 제공 개발자 도구를 열고 하위 페이지를 탐색하면서 네트워크 활동을 모니터링합니다.

   ![screen_shot_2018-06-08at103922](assets/screen_shot_2018-06-08at103922.png)

   앱에서 페이지 사이를 이동할 때 트래픽이 거의 없습니다. 페이지를 다시 로드하지 않고 새 이미지만 요청합니다.

   SPA는 전적으로 클라이언트측에서 콘텐츠와 라우팅을 관리합니다.

따라서 하위 페이지를 탐색할 때 페이지가 다시 로드되지 않으면 어떻게 로드해야 합니까?

다음 섹션, [SPA 애플리케이션 로드](/help/sites-developing/spa-walkthrough.md#loading-an-spa-application): SPA을 로드하는 역학과 컨텐츠를 동기적으로 및 비동기적으로 로드하는 방법에 대해 자세히 설명합니다.

### SPA 애플리케이션 로드 {#loading-an-spa-application}

1. 아직 로드되지 않은 경우 게시 서버에서 또는 옵션을 사용하여 We.Retail 저널 애플리케이션을 로드합니다 **[!UICONTROL 게시됨으로 보기]** 에서 **페이지 정보** 메뉴 아래의 페이지 편집기:

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at144736](assets/screen_shot_2018-06-07at144736.png)

1. 브라우저 기본 제공 도구를 사용하여 페이지 소스를 봅니다.
1. 소스의 컨텐츠는 극히 제한적입니다.

   ```
   <!DOCTYPE HTML>
   <html lang="en-CH">
       <head>
       <meta charset="UTF-8">
       <title>We.Retail Journal</title>
   
       <meta name="template" content="we-retail-react-template"/>
   
   <link rel="stylesheet" href="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.css" type="text/css">
   
   <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
   
   </head>
       <body class="page basicpage">
   
   <div id="page"></div>
   
   <script type="text/javascript" src="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.js"></script>
   
       </body>
   </html>
   ```

   페이지 본문에는 콘텐츠가 없습니다. 주로 스타일시트와 React 스크립트에 대한 호출로 구성됩니다. `we-retail-journal-react.js`.

   이 React 스크립트는 이 애플리케이션의 기본 드라이버이며 모든 컨텐츠 렌더링을 담당합니다.

1. 브라우저 기본 내장 도구를 사용하여 페이지를 검사합니다. DOM 콘텐츠가 완전히 로드되어 있는지 확인합니다.

   ![screen_shot_2018-06-07at151848](assets/screen_shot_2018-06-07at151848.png)

1. 검사기의 네트워크 탭으로 전환하고 페이지를 다시 로드합니다.

   이미지 요청을 무시하면서 페이지에 로드된 기본 리소스가 페이지 자체, CSS, React JavaScript, 해당 종속성과 페이지의 JSON 데이터인지 확인합니다.

   ![screen_shot_2018-06-07at152155](assets/screen_shot_2018-06-07at152155.png)

1. 새 탭에 `react.model.json`을 로드합니다.

   `/content/we-retail-journal/react.model.json`

   ![screen_shot_2018-06-07at152636](assets/screen_shot_2018-06-07at152636.png)

   AEM SPA 편집기는 [AEM Content Services](/help/assets/content-fragments.md)를 활용하여 페이지 전체 콘텐츠를 JSON 모델로 제공합니다.

   특정 인터페이스를 구현하면 Sling 모델은 SPA에 필요한 정보를 제공합니다. JSON 데이터 게재가 각 구성 요소로 하향 위임됩니다(페이지에서 단락과 구성 요소로).

   각 구성 요소는 노출하는 내용과 렌더링되는 방법을 선택합니다(HTL을 사용하는 서버측 또는 React를 사용하는 클라이언트측). 물론 이 문서는 React를 사용한 클라이언트측 렌더링에 중점을 둡니다.

1. 또한 모델이 페이지를 그룹화할 경우 페이지를 동기적으로 로드하여 필요한 페이지 로드 횟수를 줄일 수 있습니다.

   We.Retail 저널의 예에서 `home`, `blog`, 및 `aboutus` 페이지는 일반적으로 해당 페이지를 방문하므로 동기식으로 로드됩니다. 하지만 `weather` 방문자가 페이지를 방문할 가능성이 적으므로 페이지가 비동기식으로 로드됩니다.

   이 비헤이비어는 필수 사항이 아니고 완전히 정의할 수 있습니다.

   ![screen_shot_2018-06-07at153945](assets/screen_shot_2018-06-07at153945.png)

1. 비헤이비어의 이 차이를 확인하려면  페이지를 다시 로드하고 관리자의 네트워크 활동을 지웁니다. 페이지 메뉴에서 블로그 및 미국 정보 페이지로 이동하여 보고된 네트워크 활동이 없는지 확인합니다.

   날씨 페이지로 이동하여 다음을 확인합니다. `weather.model.json` 를 비동기식으로 호출합니다.

   ![screen_shot_2018-06-07at155738](assets/screen_shot_2018-06-07at155738.png)

### SPA 편집기와의 상호 작용 {#interaction-with-the-spa-editor}

샘플 We.Retail Journal 애플리케이션을 사용하면 앱이 어떻게 동작하고 게시될 때 로드되는지 명확히 알 수 있으며, JSON 컨텐츠 전달을 위한 컨텐츠 서비스와 리소스 비동기 로드를 활용합니다.

또한 콘텐츠 작성자는 SPA 편집기를 사용하여 AEM 내에서 콘텐츠를 원활하게 생성할 수 있습니다.

다음 섹션에서는 SPA 편집기가 SPA 내부 구성 요소를 AEM 구성 요소에 연결하여 원활한 편집 경험을 제공할 수 있는 계약 내용을 살펴봅니다.

1. 편집기에서 We.Retail 저널 애플리케이션을 로드하고 로 전환합니다. **미리 보기** 모드.

   `http://localhost:4502/editor.html/content/we-retail-journal/react.html`

1. 브라우저의 기본 제공 개발자 도구를 사용하여 페이지 콘텐츠를 검사합니다. 선택 도구를 사용하여 페이지에서 편집 가능한 구성 요소를 선택하고 요소 세부 정보를 조회합니다.

   구성 요소에는 새 데이터 속성 `data-cq-data-path`이 있습니다.

   ![screen_shot_2018-06-08at095124](assets/screen_shot_2018-06-08at095124.png)

   예

   `data-cq-data-path="root/responsivegrid/paragraph_1`

   이 경로를 사용하면 각 구성 요소의 편집 컨텍스트 구성 개체를 검색하고 연결할 수 있습니다.

   이는 편집기가 SPA 내에서 편집 가능한 구성 요소로 인식하는 데 필요한 유일한 마크업 속성입니다. 이 속성을 기반으로 SPA 편집기는 구성 요소와 연결된 편집 가능한 구성을 결정하므로 올바른 프레임, 도구 모음 등이 로드됩니다.

   일부 특정 클래스 이름이 자리 표시자 표기 및 에셋 드래그 앤 드롭 기능에 추가되기도 합니다.

   >[!NOTE]
   >
   >이것은 AEM의 서버 측 렌더링 페이지에서 동작이 변경되었습니다. 여기서 `cq` 편집 가능한 각 구성 요소에 삽입된 요소입니다.
   >
   >SPA에서 이 접근 방식을 사용하면 사용자 지정 요소를 주입하고 추가 데이터 속성만 사용하므로 프런트 엔드 개발자에게 마크업을 더 간단하게 만들 수 있습니다.

## 다음 단계 {#next-steps}

이제 AEM의 SPA 편집 환경과 SPA가 SPA 편집기와 관련되는 방식을 이해했으므로 SPA의 빌드 방법에 대해 자세히 알아볼 수 있습니다.

* [AEM에서 SPA 시작하기](/help/sites-developing/spa-getting-started-react.md) AEM에서 SPA 편집기와 작동하도록 기본 SPA을 빌드하는 방법을 보여 줍니다.
* [SPA 편집기 개요](/help/sites-developing/spa-overview.md)는 AEM과 SPA 간의 커뮤니케이션 모델에 대해 자세히 설명합니다.
* [AEM용 SPA 개발](/help/sites-developing/spa-architecture.md)에서는 프론트엔드 개발자를 AEM용 SPA 개발에 유도하는 방법과 SPA가 AEM의 아키텍처와 상호 작용하는 방법에 대해 설명합니다.
