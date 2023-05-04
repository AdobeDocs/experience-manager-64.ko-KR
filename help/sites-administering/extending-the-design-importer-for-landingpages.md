---
title: 랜딩 페이지용 디자인 Importer 확장 및 구성
seo-title: Extending and Configuring the Design Importer for Landing Pages
description: 랜딩 페이지용 디자인 가져오기 프로그램을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure the Design Importer for landing pages.
uuid: b2bfe831-bfaf-43f3-babc-687bf229dd44
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: f8991416-995b-4160-a705-d131e78089ee
exl-id: 4b37c866-30c3-45ff-b7a3-013b69598668
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3526'
ht-degree: 0%

---

# 랜딩 페이지용 디자인 Importer 확장 및 구성{#extending-and-configuring-the-design-importer-for-landing-pages}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 섹션에서는 랜딩 페이지용 디자인 가져오기를 구성하고 원하는 경우 확장하는 방법을 설명합니다. 가져오기 후 랜딩 페이지 작업이에서 다룹니다 [랜딩 페이지.](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)

**디자인 가져오기로 사용자 지정 구성 요소 추출**

디자인 가져오기가 사용자 지정 구성 요소를 인식하도록 하는 논리 단계는 다음과 같습니다

1. TagHandler 만들기

   * 태그 처리기는 특정 종류의 HTML 태그를 처리하는 POJO입니다. TagHandler가 처리할 수 있는 HTML 태그의 &quot;종류&quot;는 TagHandlerFactory의 OSGi 속성 &quot;tagpattern.name&quot;을 통해 정의됩니다. 이 OSGi 속성은 기본적으로 처리할 입력 html 태그와 일치해야 하는 regex입니다. 중첩된 모든 태그가 처리를 위해 태그 처리기에 반환됩니다. 예를 들어, 중첩된 div가 포함된 div에 등록하는 경우 &lt;p> 태그, &lt;p> 태그가 TagHandler에 반환되고 이를 처리하는 방식은 사용자에게 달려 있습니다.
   * 태그 처리기 인터페이스는 SAX 컨텐츠 처리기 인터페이스와 유사합니다. 이 확장은 각 html 태그에 대한 SAX 이벤트를 수신합니다. 태그 처리기 공급자의 경우, 디자인 가져오기 프레임워크에서 자동으로 호출하는 특정 라이프사이클 메서드를 구현해야 합니다.

1. 해당 TagHandlerFactory를 만듭니다.

   * 태그 처리기 팩터리는 태그 처리기의 인스턴스를 발생시킬 책임이 있는 OSGi 구성 요소(singleton)입니다.
   * 태그 처리기 팩터리는 입력 html 태그에 대해 값이 일치하는 &quot;tagpattern.name&quot;이라는 OSGi 속성을 노출해야 합니다.
   * 입력 html 태그와 일치하는 태그 처리기가 여러 개 있는 경우 등급이 높은 처리기가 선택됩니다. 등급 자체는 OSGi 속성으로 노출됩니다 **service.ranking**.
   * TagHandlerFactory는 OSGi 구성 요소입니다. TagHandler에 제공할 모든 참조는 이 팩터리를 통해야 합니다.

1. 기본값을 무시하려면 TagHandlerFactory가 더 높은 등급인지 확인하십시오.

## 가져올 HTML 준비 {#preparing-the-html-for-import}

Importer 페이지를 만들면 전체 HTML 랜딩 페이지를 가져올 수 있습니다. HTML 랜딩 페이지를 가져오려면 먼저 컨텐츠를 디자인 패키지에 zip으로 압축해야 합니다. 디자인 패키지에는 참조된 자산(이미지, css, 아이콘, 스크립트 등)과 함께 HTML 랜딩 페이지가 들어 있습니다.

다음 치트 시트에서는 가져올 HTML 준비 방법에 대한 샘플을 제공합니다.

랜딩 페이지 치트 시트

[파일 가져오기](assets/cheatsheet.zip)

### Zip 파일 레이아웃 및 요구 사항 {#zip-file-layout-and-requirements}

>[!NOTE]
>
>이때 ZIP 파일은 하나의 HTML 페이지나 페이지의 한 부분만 포함할 수 있습니다.

zip의 샘플 레이아웃은 다음과 같습니다.

* /index.html -> 랜딩 페이지 HTML 파일
* /css -> CSS clientlib에 추가
* /img -> 모든 이미지 및 자산
* /js -> JS clientlib에 추가

레이아웃은 HTML5 표준 문안 우수 사례 레이아웃을 기반으로 합니다. 자세한 내용은 [https://html5boilerplate.com/](https://html5boilerplate.com/)

>[!NOTE]
>
>최소한 디자인 패키지 **반드시** 다음을 포함합니다. **index.html** 파일을 루트 수준에서 지정합니다. 가져올 랜딩 페이지에 모바일 버전도 있는 경우, zip에 다음과 같은 항목이 포함되어야 합니다. **mobile.index.html** 및 **index.html** 루트 수준에 있습니다.

### 랜딩 페이지 HTML 준비 {#preparing-the-landing-page-html}

HTML을 가져오려면 랜딩 페이지 HTML에 캔버스 div를 추가해야 합니다.

canvas div는 html입니다. **div** with `id="cqcanvas"` HTML 내에 삽입해야 합니다 `<body>` 태깅하고 전환을 위한 컨텐츠를 둘러싸야 합니다.

canvas div 추가 후 랜딩 페이지 HTML의 샘플 코드 조각은 다음과 같습니다.

```xml
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
  <meta name="description" content="">
</head>
<body>
 <div id="cqcanvas">
  <!-- HTML content intended for conversion -->
 </div>
</body>
</html>
```

### 편집 가능한 AEM 구성 요소를 포함하도록 HTML 준비 {#preparing-the-html-to-include-editable-aem-components}

랜딩 페이지를 가져올 때는 페이지를 있는 그대로 가져올 수 있습니다. 즉, 랜딩 페이지를 가져온 후에는 AEM에서 가져온 항목을 편집할 수 없습니다(페이지에 AEM 구성 요소를 더 추가할 수도 있음).

랜딩 페이지를 가져오기 전에 AEM 구성 요소를 편집할 수 있도록 랜딩 페이지의 일부 부분을 전환할 수 있습니다. 이렇게 하면 랜딩 페이지 디자인을 가져온 후에도 랜딩 페이지의 일부를 빠르게 편집할 수 있습니다.

다음을 추가하여 이 작업을 수행합니다 `data-cq-component` 를 클릭하여 제품에서 사용할 수 있습니다.

다음 섹션에서는 랜딩 페이지의 특정 부분을 편집 가능한 다른 AEM 구성 요소로 변환하도록 HTML 파일을 편집하는 방법을 설명합니다. 구성 요소는 다음에서 자세히 설명합니다. [랜딩 페이지 구성 요소](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md).

>[!NOTE]
>
>랜딩 페이지의 일부를 AEM 구성 요소로 변환하는 HTML 마크업에는 긴 양식과 축약형 태그 선언이 모두 있습니다. 둘 다 각 구성 요소에 대해 설명합니다.

### 제한 사항 {#limitations}

가져오기 전에 다음 제한 사항을 참고하십시오.

### &amp;lt;body> 태그에 적용된 클래스 또는 id와 같은 속성은 유지되지 않습니다 {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

예를 들어, id 또는 class와 같은 속성이 body 태그에 적용되는 경우, `<body id="container">` 그러면 가져오기 후에도 유지되지 않습니다. 따라서 가져오는 디자인에는 `<body>` 태그에 가깝게 포함했습니다.

### zip 드래그 앤 드롭 {#drag-and-drop-zip}

zip 드래그/드롭 업로드는 Internet Explorer 및 Firefox 버전 3.6 이하에서 지원되지 않습니다. 이러한 브라우저를 사용할 때 디자인을 업로드하려면 드롭 파일 영역을 클릭하여 파일 업로드 대화 상자를 열고 해당 대화 상자를 사용하여 디자인을 업로드합니다.

디자인 zip의 &quot;드래그 앤 드롭&quot;을 지원하는 브라우저는 Chrome, Safari5.x, Firefox 4 이상입니다.

### Modernizr는 지원되지 않습니다 {#modernizr-is-not-supported}

`Modernizr.js` 는 브라우저의 기본 기능을 감지하고 html5 요소에 적합한지를 탐지하는 javascript 기반 도구입니다. 다양한 브라우저의 이전 버전에서 지원을 개선하기 위해 Modernizr를 사용하는 디자인은 랜딩 페이지 솔루션에서 가져오기 문제를 일으킬 수 있습니다. `Modernizr.js` 스크립트는 디자인 가져오기에서 지원되지 않습니다.

### 디자인 패키지를 가져올 때 페이지 속성이 유지되지 않습니다 {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

모든 페이지 속성(예: 사용자 지정 도메인, HTTPS 적용 등)은 디자인 패키지를 가져오기 전에(빈 랜딩 페이지 템플릿을 사용하는) 페이지에 대해 설정된 설정은 디자인을 가져온 후 손실됩니다. 따라서 디자인 패키지를 가져온 후 페이지 속성을 설정하는 것이 좋습니다.

### HTML 전용 마크업 가정됨 {#html-only-markup-assumed}

가져오기 시 보안상의 이유로 마크업이 정리되어 잘못된 마크업을 가져오거나 게시하지 않습니다. 여기서는 HTML 전용 마크업 및 인라인 SVG 또는 웹 구성 요소와 같은 기타 모든 유형의 요소가 필터링된다고 가정합니다.

### 텍스트 {#text}

텍스트 구성 요소를 삽입하는 HTML 마크업( `foundation/components/text`) 내의 HTML을 만들 수 있습니다.

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

HTML에 위의 마크업을 포함하면 다음과 같이 됩니다.

* 편집 가능한 AEM 텍스트 구성 요소( `sling:resourceType=foundation/components/text`)을 클릭하여 제품에서 사용할 수 있습니다.
* 를 설정합니다. `text` 만든 텍스트 구성 요소의 속성을 HTML 내에 `div`.

**축약형 구성 요소 태그 선언**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**목록이 있는 텍스트**

목록이 있는 텍스트를 추가하려면:

* 1st
* 2nd

RTE 편집기에서 편집할 수 있습니다.

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**색상이 있는 텍스트**

RTE 편집기에서 편집할 수 있는 색상(분홍)이 있는 텍스트를 추가하려면:

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### 제목 {#title}

제목 구성 요소를 삽입하는 HTML 마크업( `wcm/landingpage/components/title`) 내의 HTML을 만들 수 있습니다.

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

HTML에 위의 마크업을 포함하면 다음과 같이 됩니다.

* 편집 가능한 AEM 제목 구성 요소( `sling:resourceType=wcm/landingpage/components/title`)을 클릭하여 제품에서 사용할 수 있습니다.
* 를 설정합니다. `jcr:title` div 내에 래핑된 제목 태그 내의 텍스트에 대해 생성된 제목 구성 요소의 속성입니다.
* 를 설정합니다. `type` 제목 태그에 속성(이 경우) `h1`.

제목 구성 요소는 7가지 유형을 지원합니다. `h1, h2, h3, h4, h5, h6` 및 `default`.

**축약형 구성 요소 태그 선언**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### 이미지 {#image}

디자인 패키지 내의 HTML에 이미지 구성 요소를 삽입하는 HTML 마크업(foundation/components/image):

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

HTML에 위의 마크업을 포함하면 다음과 같이 됩니다.

* 편집 가능한 AEM 이미지 구성 요소( `sling:resourceType=foundation/components/image`)을 클릭하여 제품에서 사용할 수 있습니다.
* 를 설정합니다. `fileReference` 만들어진 이미지 구성 요소의 속성 - src 속성에 지정된 이미지를 가져오는 경로입니다.
* 를 설정합니다. `alt` 속성 을 img 태그에 있는 alt 특성의 값으로 설정합니다.
* 를 설정합니다. `title` 속성 을 img 태그에 있는 title 속성 값으로 설정합니다.
* 를 설정합니다. `width` 속성 을 img 태그에 있는 width 특성의 값으로 설정합니다.
* 를 설정합니다. `height` 속성 을 img 태그에 있는 height 특성의 값으로 설정합니다.

**축약형 구성 요소 태그 선언:**

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### 절대 URL img src는 이미지 구성 요소 Div 내에서 지원되지 않음 {#absolute-url-img-src-not-supported-within-image-component-div}

다음과 같은 경우 `<img>` 절대 url src가 있는 태그는 적절한 구성 요소 변환에 대해 시도됩니다. **지원되지 않는 TagContentException** 이 발생합니다. 예를 들어 지원되지 않는 항목은 다음과 같습니다.

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

그러나 그렇지 않으면, 절대 URL 이미지는 이미지 구성 요소 div의 일부가 아닌 img 태그에 대해 지원됩니다.

### 클릭유도문안 구성 요소 {#call-to-action-components}

가져올 랜딩 페이지의 일부를 &quot;편집 가능한 클릭유도문안 구성 요소&quot;로 표시할 수 있습니다. 이렇게 가져온 클릭유도문안 구성 요소는 랜딩 페이지를 가져온 후 편집할 수 있습니다. AEM에는 다음 CTA 구성 요소가 포함되어 있습니다.

* 클릭스루 링크 - 클릭하면 방문자를 타겟 URL로 이동시키는 텍스트 링크를 추가할 수 있습니다.
* 그래픽 링크 - 클릭하면 방문자가 타겟 URL로 이동하는 이미지를 추가할 수 있습니다.

#### 클릭스루 링크 {#click-through-link}

이 CTA 구성 요소는 랜딩 페이지에서 텍스트 링크를 추가하는 데 사용할 수 있습니다.

지원되는 속성

* 굵게, 기울임체 및 밑줄 옵션이 있는 레이블
* Target URL, 타사 및 AEM URL 지원
* 페이지 렌더링 옵션(동일한 창, 새 창 등)은

가져온 zip에 클릭스루 구성 요소를 포함하도록 HTML 태그입니다. 여기 href는 타겟 url에 매핑하고, &quot;제품 세부 정보 보기&quot;는 레이블 등으로 매핑합니다.

```xml
<div id="cqcanvas">
.
.
                <div data-cq-component="clickThroughLink">
        <a href="/content/we-retail/us/en/products/equipment/snow-sports/flying-snowboard.html">View Product Details  ></a>
  </div>
.
.
</div>
```

이 구성 요소는 독립 실행형 애플리케이션에서 사용하거나 zip에서 가져올 수 있습니다.

**축약형 구성 요소 태그 선언**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### 그래픽 링크 {#graphical-link}

이 CTA 구성 요소는 랜딩 페이지에서 링크가 있는 그래픽 이미지를 추가하는 데 사용할 수 있습니다. 이미지는 간단한 단추나 배경용 그래픽 이미지일 수 있습니다. 이미지를 클릭하면 구성 요소 속성에 지정된 타겟 URL로 이동합니다. 클릭유도문안 그룹의 일부입니다.

지원되는 속성

* 이미지 자르기, 회전
* 텍스트, 설명, px 크기를 마우스로 가리키기
* Target URL, 타사 및 AEM URL 지원
* 페이지 렌더링 옵션(동일한 창, 새 창 등)은

가져온 zip에 그래픽 링크 구성 요소를 포함하는 HTML 태그입니다. 여기 href는 타겟 url에 매핑되고, img src는 렌더링 이미지이고, &quot;title&quot;은 마우스로 가리키면 텍스트 등으로 가져옵니다.

```xml
<div id="cqcanvas">
  <div data-cq-component="clickThroughGraphicalLink"><a href="https://www.adobe.com/go/wem"><img src="img/call-to-action-button.png" title="Click Here to Learn More" /></a></div>
</div>
```

**축약형 구성 요소 태그 선언**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughGraphicalLink"><img src="linkimage.png" alt="Click Through Graphical Link shorthand"/></a>
```

>[!NOTE]
>
>clickthroughgraphical 링크를 만들려면, 다음과 같이 div 내에서 anchor 태그와 image 태그를 둘러싸야 합니다 `data-cq-component="clickthroughgraphicallink"` 속성을 사용합니다.
>
>예. `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>CSS를 사용하여 이미지를 앵커 태그와 연결하는 다른 방법은 지원되지 않습니다. 예를 들어 다음 마크업은 작동하지 않습니다.
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>관련 `css .hasbackground { background-image: pathtoimage }`

### 리드 양식 {#lead-form}

리드 양식은 방문자/리드의 프로필 정보를 수집하는 데 사용되는 양식입니다. 이 정보는 저장했다가 나중에 사용하여 정보를 기반으로 효과적인 마케팅을 수행할 수 있습니다. 이 정보에는 일반적으로 제목, 이름, 이메일, 생년월일, 주소, 관심사 등이 포함됩니다. CTA 리드 양식 그룹의 일부입니다.

**지원되는 기능**

* 사전 정의된 리드 필드(이름, 성, 주소, dob, 성별, 정보, userId, emailId, 제출 단추)는 사이드 킥에서 사용할 수 있습니다. 리드 양식에서 필요한 구성 요소를 드래그/드롭하면 됩니다.
* 이러한 구성 요소 작성자의 도움으로 독립형 리드 양식을 디자인할 수 있으며, 이 필드는 리드 양식 필드에 해당합니다. 독립형 또는 가져온 zip 애플리케이션에서 사용자는 요구 사항에 따라 cq:form 또는 cta 리드 양식 필드를 사용하여 필드를 더 추가하고 이름을 지정하고 디자인할 수 있습니다.
* CTA 리드 양식의 사전 정의된 특정 이름을 사용하여 리드 양식 필드를 매핑할 수 있습니다. 예를 들어, 리드 양식의 첫 번째 이름에 firstName을 매핑할 수 있습니다.
* 리드 양식에 매핑되지 않은 필드는 cq:form 구성 요소(텍스트, 라디오, 확인란, 드롭다운, 숨김, 암호)에 매핑됩니다.
* 사용자는 &quot;label&quot; 태그를 사용하여 제목을 제공하고, 스타일 속성 &quot;class&quot;(CTA 리드 양식 구성 요소에만 사용 가능)를 사용하여 스타일을 제공할 수 있습니다.
* 감사 인사 페이지 및 구독 목록은 양식의 숨겨진 매개 변수(index.htm에 있음)로 제공하거나 &quot;리드 양식 시작&quot;의 편집 막대에서 추가/편집할 수 있습니다

   &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

   &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* 필수 구성 요소와 같은 제한 사항은 각 구성 요소의 편집 구성에서 제공할 수 있습니다.

가져온 zip에 그래픽 링크 구성 요소를 포함하는 HTML 태그입니다. 여기서 &quot;firstName&quot;은 확인란을 제외하고 리드 양식 firstName 등에 매핑됩니다. 이 두 확인란은 cq:form 드롭다운 구성 요소에 매핑됩니다.

```xml
<div id="cqcanvas">
   <div id="form_wrapper">
    <h2>NEWSLETTER SIGN UP</h2>
       <div data-cq-component="leadFormGeneration">
       <form method="post" action="#" onsubmit="return popupBox()">
       <label for="firstName" class="checkText">
        FIRST NAME
       </label><br />
       <input name="firstName" class="text pink" type="text" /><br />
       <label for="lastName" class="checkText">
        LAST NAME
       </label><br />
       <input name="lastName" class="text pink" type="text" /><br />
       <label for="emailId" class="checkText">
        EMAIL ADDRESS
       </label><br />
       <input name="emailId" class="text pink" type="text" /><br />

       <div class="checkboxes">
       <input type="checkbox" class="check" name="send_news" /> <label for="send_news" class="checkText">Send me the latest We.Retail news and announcements.</label><br />
       <input type="checkbox" class="check" name="send_offers" /> <label for="send_offers" class="checkText">Send me We.Retail deals and special offers.</label><br />
       </div>
       <input type="submit" name="submit" class="submit pink" value="Sign Up >" />
       </form>
     </div>
   </div>
```

### Parsys {#parsys}

AEM parsys 구성 요소는 다른 AEM 구성 요소를 포함할 수 있는 컨테이너 구성 요소입니다. 가져온 HTML에 parsys 구성 요소를 추가할 수 있습니다. 이렇게 하면 사용자가 편집 가능한 AEM 구성 요소를 가져온 후에도 랜딩 페이지에 추가/삭제할 수 있습니다.

단락 시스템을 사용하면 사이드킥을 사용하여 구성 요소를 추가할 수 있습니다.

parsys 구성 요소를 삽입하는 HTML 마크업( `foundation/components/parsys`) 내의 HTML을 만들 수 있습니다.

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

HTML에 위의 마크업을 포함하면 다음과 같은 작업이 수행됩니다.

* 디자인 패키지를 가져온 후 만든 랜딩 페이지에 AEM parsys 구성 요소(foundation/components/parsys)를 삽입합니다.
* 사이드 킥을 기본 구성 요소로 초기화합니다. 사이드킥의 구성 요소를 parsys 구성 요소로 드래그하여 랜딩 페이지에 새 구성 요소를 추가할 수 있습니다.
* 두 제목 구성 요소도 parsys의 일부입니다.

### 대상 {#target}

타겟 구성 요소는 페이지에서 경험의 컨텐츠를 보여줍니다. 캠페인에서 만들어진 많은 경험이 있을 수 있으며 타겟 구성 요소는 페이지를 방문하는 다양한 사용자에게 서로 다른 경험의 컨텐츠를 동적으로 표시할 수 있습니다.

타겟 구성 요소를 삽입하고 캠페인에서 다른 경험을 만드는 html 마크업:

```xml
<div data-cq-component="target">
 <section data-cq-component="experience" data-cq-experience="default">
  <p data-cq-component="text">Default content. Select this campaign in client context to view other experiences</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="over-30">
  <p data-cq-component="text">Content for Over 30</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="under-30">
  <p data-cq-component="text">Content for Under 30</p>
 </section>
</div>
```

## 추가 가져오기 옵션 {#additional-importing-options}

가져온 구성 요소가 편집 가능한 AEM 구성 요소인지 여부를 지정하는 것 외에, 디자인 패키지를 가져오기 전에 다음을 구성할 수도 있습니다.

* 가져온 HTML에 정의된 메타데이터를 추출하여 페이지 속성을 설정합니다.
* HTML에서 charset 인코딩 지정
* Importer 페이지 템플릿 오버레이

### 가져온 HTML에 정의된 메타데이터를 추출하여 페이지 속성 설정 {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

가져온 HTML의 헤드에 선언된 다음 메타데이터는 디자인 가져오기가 추출하여 속성 &quot;jcr:description&quot;으로 보존합니다.

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

HTML 태그에 설정된 Lang 속성은 디자인 가져오기가 추출하여 속성 &quot;jcr:language&quot;로 보존합니다

* &lt;html lang=&quot;en&quot;>

### html에서 charset 인코딩 지정 {#specifying-the-charset-encoding-in-the-html}

디자인 가져오기는 가져온 HTML에 지정된 인코딩을 읽습니다. 인코딩은 다음과 같이 지정할 수 있습니다.

`<meta charset="UTF-8">`

*또는*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

가져온 HTML에 지정된 인코딩이 없으면 디자인 가져오기에서 설정한 기본 인코딩은 UTF-8입니다.

### 템플릿 오버레이 {#overlaying-template}

빈 랜딩 페이지 템플릿은 다음에 새 템플릿을 만들어 오버레이할 수 있습니다. `/apps/<appName>/designimporter/templates/<templateName>`

AEM에서 새 템플릿을 만드는 단계는 설명되어 있습니다 [여기](/help/sites-developing/templates.md).

### 랜딩 페이지에서 구성 요소 참조 {#referring-a-component-from-landing-page}

디자인 가져오기가 이 위치에서 구성 요소 포함을 렌더링하도록 data-cq-component 특성을 사용하여 HTML에서 참조할 구성 요소가 있다고 가정합니다. 예: 표 구성 요소( `resourceType = /libs/foundation/components/table`). HTML에 다음을 추가해야 합니다.

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

data-cq-component의 경로는 구성 요소의 resourceType이어야 합니다.

### 모범 사례 {#best-practices}

가져올 때 구성 요소 변환용으로 표시된 요소에 사용할 때는 다음과 유사한 CSS 선택기를 사용하지 않는 것이 좋습니다.

| E > F | E 요소의 F 요소 하위 | [하위 콤비네이터](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | F 요소가 E 요소 바로 앞에 옵니다. | [인접 동기 콤비네이터](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | F 요소가 E 요소 앞에 옵니다. | [일반 동기 콤비네이터](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | E 요소, 문서의 루트 | [구조적 의사 클래스](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | E 요소, 상위의 n번째 하위 | [구조적 의사 클래스](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | E 요소, 상위의 n번째 하위, 마지막 요소로부터 계산 | [구조적 의사 클래스](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | E 요소, 해당 유형의 n번째 동기 | [구조적 의사 클래스](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | E 요소, 해당 유형의 n번째 동기, 마지막 항목부터 셈 | [구조적 의사 클래스](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

이것은 다음과 같은 추가 html 요소가 &lt;div> 태그는 가져오기 후에 생성된 HTML에 추가됩니다.

* 위와 유사한 구조에 의존하는 스크립트도 AEM 구성 요소로 전환하도록 표시된 요소와 함께 사용하는 것이 좋습니다.
* 와 같은 구성 요소 전환을 위해 마크업 태그에서 스타일 사용 &lt;div data-cq-component=&quot;”&amp;ast;”&quot;> 은 권장되지 않습니다.
* 디자인 레이아웃은 HTML5 표준 문안의 우수 사례를 따라야 합니다. 다음 문서를 참조하십시오. [https://html5boilerplate.com/](https://html5boilerplate.com/).

## OSGI 모듈 구성 {#configuring-osgi-modules}

OSGI 콘솔을 통해 구성할 수 있는 속성을 표시하는 구성 요소는 다음과 같습니다.

* 랜딩 페이지 디자인 가져오기
* 랜딩 페이지 빌더
* 모바일 랜딩 페이지 빌더
* 랜딩 페이지 항목 사전 처리기

아래 표에서는 속성에 대해 간략하게 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>구성 요소</strong></td> 
   <td><strong>속성 이름</strong></td> 
   <td><strong>속성 설명 </strong></td> 
  </tr> 
  <tr> 
   <td>랜딩 페이지 디자인 가져오기</td> 
   <td>추출 필터</td> 
   <td>추출에서 파일을 필터링하는 데 사용할 정규 표현식 목록입니다. <br /> 지정된 패턴 중 하나와 일치하는 Zip 항목은 추출에서 제외됩니다</td> 
  </tr> 
  <tr> 
   <td>랜딩 페이지 빌더</td> 
   <td>파일 패턴</td> 
   <td>랜딩 페이지 빌더를 구성하여 파일 패턴으로 정의된 정규식과 일치하는 HTML 파일을 처리할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>모바일 랜딩 페이지 빌더</td> 
   <td>파일 패턴</td> 
   <td>랜딩 페이지 빌더를 구성하여 파일 패턴으로 정의된 정규식과 일치하는 HTML 파일을 처리할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>장치 그룹</td> 
   <td>지원할 장치 그룹 목록입니다.</td> 
  </tr> 
  <tr> 
   <td>랜딩 페이지 항목 사전 처리기</td> 
   <td>검색 패턴 </td> 
   <td>아카이브 항목 컨텐츠에서 검색할 패턴입니다. 이 정규 표현식은 라인별로 시작 컨텐츠 라인과 대응됩니다. 일치 시 일치하는 텍스트는 지정된 대체 패턴으로 대체됩니다.<br /> <br /> 랜딩 페이지 항목 사전 처리기의 현재 제한 사항에 대해서는 아래 참고 사항을 참조하십시오.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>패턴 바꾸기</td> 
   <td>찾은 일치 항목을 대체하는 패턴입니다. $1, $2 등의 regex 그룹 참조를 사용할 수 있습니다. 또한 이 패턴은 가져오는 동안 실제 값으로 확인되는 {designPath} 등의 키워드를 지원합니다.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**랜딩 페이지 입력 사전 처리기의 현재 제한 사항:**
>검색 패턴을 변경해야 하는 경우, felix 속성 편집기를 열 때 수동으로 백슬래시 문자를 추가하여 regex 메타문자를 이스케이프 처리해야 합니다. 수동으로 백슬래시 문자를 추가하지 않는 경우 regex가 유효하지 않은 것으로 간주되며 이전 백슬래시 문자를 대체하지 않습니다.
>
>예를 들어, 기본 구성이
>
>`/\&ast *CQ_DESIGN_PATH *\*/ *(['"])`
>
>그리고 당신은 `CQ_DESIGN_PATH` with `VIPURL` 검색 패턴에서 검색 패턴은 다음과 같아야 합니다.
>
>`/\* *VIPURL *\*/ *(['"])`

## 문제 해결 {#troubleshooting}

디자인 패키지를 가져올 때 이 섹션에 설명된 몇 가지 오류가 발생할 수 있습니다.

### 랜딩 페이지 관련 구성 요소를 사용한 사이드킥의 초기화 {#initialization-of-sidekick-with-landing-page-relevant-components}

디자인 패키지에 parsys 구성 요소 마크업이 포함된 경우 가져오기 후 사이드킥이 랜딩 페이지 관련 구성 요소를 표시하기 시작합니다. 랜딩 페이지 내에서 새 구성 요소를 parsys 구성 요소로 끌어다 놓을 수 있습니다. 디자인 모드로 이동하여 사이드킥에 새 구성 요소를 추가할 수도 있습니다.

### 가져오는 동안 표시되는 오류 메시지 {#error-messages-displayed-during-import}

오류가 발생하면(예: 가져온 패키지가 올바른 zip이 아님) 디자인 가져오기에서 패키지를 가져오지 않고 대신 드래그 앤 드롭 상자 바로 위의 페이지 맨 위에 오류 메시지가 표시됩니다. 오류 시나리오의 예는 여기에 나와 있습니다. 오류를 수정한 후 업데이트된 zip을 동일한 빈 랜딩 페이지로 다시 가져올 수 있습니다. 오류가 발생하는 다양한 시나리오는 다음과 같습니다.

* 가져온 디자인 패키지는 올바른 zip 아카이브가 아닙니다.
* 가져온 디자인 패키지에는 맨 위 수준에 index.html이 없습니다.

### 가져오기 후 표시되는 경고 {#warnings-displayed-after-import}

경고가 발생하면(예: HTML이 패키지 내에 없는 이미지를 참조) 디자인 가져오기에서 zip을 가져오지만, 동시에 결과 창에 문제/경고 목록이 표시됩니다. 문제 링크를 클릭하면 디자인 패키지 내의 문제를 가리키는 경고 목록이 표시됩니다. 디자인 가져오기에서 포착하고 표시하는 경고가 표시되는 다양한 시나리오는 다음과 같습니다.

* HTML이 패키지 내에 없는 이미지를 참조합니다.
* HTML이 패키지 내에 없는 스크립트를 참조합니다.
* HTML이 패키지 내에 없는 스타일을 참조합니다.

### ZIP 파일의 파일은 AEM에 어디에 저장됩니까? {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

랜딩 페이지를 가져온 후 파일(이미지, css, js 등)은 디자인 패키지 내에서 는 AEM의 다음 위치에 저장됩니다.

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

랜딩 페이지가 캠페인 We.Retail에서 만들어지고 랜딩 페이지의 이름이 다음과 같다고 가정합니다 **myBlankLandingPage** zip 파일이 저장되는 위치는 다음과 같습니다.

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### 서식이 유지되지 않음 {#formatting-not-preserved}

CSS를 만들 때는 다음 제한 사항을 알아 두십시오.

텍스트 및 편집 가능한) 이미지가 다음과 같은 경우

```xml
<div class="box">
<p><div data-cq-component="image"><img src="assets/image.jpg" width="115"
height="116" /></div>Some Text </p>
</div>
```

CSS가 클래스에 적용된 상태로 `box` 아래와 같이 변경하는 것을 의미합니다.

```xml
.box

{ width: 450px; padding:10px; border: 1px #C5DBE7 solid; margin: 0px auto 0 auto; background-image:url(assets/box.gif); background-repeat:repeat-x,y; font-family:Verdana, Arial, Helvetica, sans-serif; font-size:12px; color:#6D6D6D; }
```

Then `box img` 디자인 가져오기에서 이 사용되면 결과 랜딩 페이지에 서식이 유지되지 않습니다. 이 문제를 해결하려면 AEM이 CSS에서 div 태그를 추가하고 그에 따라 코드를 다시 작성해야 합니다. 그렇지 않으면 일부 CSS 규칙이 올바르지 않습니다.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
>
>또한 디자이너는 **id=cqcanvas** 태그는 가져오기가 인식하며, 그렇지 않으면 디자인이 유지되지 않습니다.
