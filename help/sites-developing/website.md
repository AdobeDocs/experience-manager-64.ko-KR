---
title: 모든 기능을 갖춘 웹 사이트(JSP) 만들기
seo-title: Create a Fully-Featured Website (JSP)
description: 이 자습서에서는 AEM에서 모든 기능을 갖춘 웹 사이트를 만들 수 있습니다
seo-description: This tutorial enables you to create a fully featured website with AEM
uuid: bb8d4efd-7631-4cc5-8084-b03c6aabdef3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8d14017d-d311-45e9-8aea-4a5ca46f1a07
exl-id: 6d408fd6-9241-4069-9b04-806e30e03ff2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4935'
ht-degree: 3%

---

# 모든 기능을 갖춘 웹 사이트(JSP) 만들기{#create-a-fully-featured-website-jsp}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>이 문서에서는 JSP를 사용하고 클래식 UI를 기반으로 웹 사이트를 만드는 방법에 대해 설명합니다. Adobe은 문서에 자세히 설명된 대로 웹 사이트에 대한 최신 AEM 기술을 활용할 것을 권장합니다 [AEM Sites 개발 시작](/help/sites-developing/getting-started.md).

이 자습서에서는 AEM(Adobe Experience Manager)을 사용하여 모든 기능을 갖춘 웹 사이트를 만들 수 있습니다. 웹 사이트는 일반 웹 사이트를 기반으로 하며 주로 웹 개발자를 대상으로 합니다. 모든 개발 작업은 작성 환경 내에서 수행됩니다.

이 자습서에서는 다음 방법을 설명합니다.

1. AEM을 설치합니다.
1. 액세스 CRXDE Lite(개발 환경)입니다.
1. CRXDE Lite에서 프로젝트 구조를 설정합니다.
1. 컨텐츠 페이지를 만드는 기준으로 사용되는 템플릿, 구성 요소 및 스크립트를 만듭니다.
1. 웹 사이트의 루트 페이지를 만든 다음 컨텐츠 페이지를 만듭니다.
1. 페이지에서 사용할 다음 구성 요소를 만듭니다.

   * **[!UICONTROL 위쪽 탐색]**
   * **[!UICONTROL 하위 목록]**
   * **[!UICONTROL 로고]**
   * **[!UICONTROL 이미지]**
   * **[!UICONTROL 텍스트 이미지]**
   * **[!UICONTROL 검색]**

1. 다양한 기초 구성 요소를 포함합니다.

모든 단계를 수행하면 페이지가 다음과 같이 표시됩니다.

![chlimage_1-99](assets/chlimage_1-99.png)

**최종 결과 다운로드**

연습을 수행하지 않고 자습서와 함께 따라 하려면 웹 사이트-1.0.zip을 다운로드하십시오. 이 파일은 이 자습서의 결과를 포함하는 AEM 컨텐츠 패키지입니다. 사용 [패키지 관리자](/help/sites-administering/package-manager.md) 를 클릭하여 작성자 인스턴스에 패키지를 설치합니다.

>[!NOTE]
>이 패키지를 설치하면 이 자습서를 사용하여 만든 작성 인스턴스에 있는 리소스를 덮어씁니다.

웹 사이트 컨텐츠 패키지

[파일 가져오기](assets/website-1_0.zip)

## Adobe Experience Manager 설치 {#installing-adobe-experience-manager}

웹 사이트 개발을 위한 AEM 인스턴스를 설치하려면 다음을 설정하는 지침을 따르십시오 [작성자 및 게시 인스턴스를 사용한 배포 환경](/help/sites-deploying/deploy.md#author-and-publish-installs), 또는 [일반 설치](/help/sites-deploying/deploy.md#default-local-install). 일반 설치에는 AEM Quickstart JAR 파일을 다운로드하고 JAR 파일과 동일한 디렉토리에 license.properties 파일을 지정한 다음 JAR 파일을 두 번 클릭해야 합니다.

AEM을 설치한 후 시작 페이지에서 CRXDE Lite 링크를 클릭하여 CRXDE Lite 개발 환경에 액세스합니다.

![chlimage_1-100](assets/chlimage_1-100.png)

>[!NOTE]
>
>기본 포트를 사용하여 로컬에 설치된 AEM 작성 인스턴스의 CRXDE Lite URL은 [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/).

## CRXDE Lite에서 프로젝트 구조 설정 {#setting-up-the-project-structure-in-crxde-lite}

CRXDE Lite을 사용하여 저장소에서 웹 사이트 응용 프로그램 구조를 만듭니다.

1. CRXDE Lite 왼쪽에 있는 트리에서 **`/apps`** 폴더를 클릭한 다음 **[!UICONTROL 만들기 > 폴더 만들기]**. 에서 **폴더 만들기** 대화 상자, 유형 `mywebsite` 을 폴더 이름으로 사용하고 을 클릭합니다. **확인**.
1. 마우스 오른쪽 단추를 클릭합니다. `/apps/mywebsite` 폴더를 클릭한 다음 **[!UICONTROL 만들기 > 폴더 만들기]**. 에서 **[!UICONTROL 폴더 만들기]** 대화 상자, 유형 `components` 을 폴더 이름으로 사용하고 을 클릭합니다. **[!UICONTROL 확인]**.
1. 마우스 오른쪽 단추를 클릭합니다. `/apps/mywebsite` 폴더를 클릭한 다음 **[!UICONTROL 만들기 > 폴더 만들기]**. 에서 **[!UICONTROL 폴더 만들기]** 대화 상자, 유형 `templates` 을 폴더 이름으로 사용하고 을 클릭합니다. **[!UICONTROL 확인]**.

   이제 트리의 구조가 다음과 같이 표시됩니다.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. 클릭 **[!UICONTROL 모두 저장]**.

## 디자인 설정 {#setting-up-the-design}

이 섹션에서는 디자이너 도구를 사용하여 응용 프로그램의 디자인을 만듭니다. 이 디자인은 웹 사이트에 대한 CSS 및 이미지 리소스를 제공합니다.

>[!NOTE]
>
>다음 링크를 클릭하여 다운로드합니다 ``mywebsite.zip``. 아카이브에 디자인을 위한 static.css 및 이미지 파일이 포함되어 있습니다.

샘플 정적.css 파일 및 이미지

[파일 가져오기](assets/mywebsite.zip)

1. AEM 시작 페이지에서 **[!UICONTROL 도구]**. ([http://localhost:4502/libs/cq/core/content/welcome.html](http://localhost:4502/libs/cq/core/content/welcome.html))

   ![chlimage_1-102](assets/chlimage_1-102.png)

1. 폴더 트리에서 **[!UICONTROL 디자인]** 폴더를 만든 다음 **[!UICONTROL 새로 만들기 > 새 페이지]**. 유형 `mywebsite` 제목으로 를 클릭하고 **[!UICONTROL 만들기]**.

1. mywebsite 항목이 테이블에 나타나지 않으면 트리 또는 테이블을 새로 고칩니다.

1. [WebDAV 사용](/help/sites-administering/webdav-access.md) http://localhost:4502에서 URL에 액세스하여 샘플을 복사합니다 `static.css` 파일 및 `images` 다운로드한 mywebsite.zip 파일의 폴더를 `/etc/designs/mywebsite` 폴더를 입력합니다.

   ![chlimage_1-103](assets/chlimage_1-103.png)

## 컨텐츠 페이지 템플릿, 구성 요소 및 스크립트 만들기 {#creating-the-contentpage-template-component-and-script}

이 섹션에서 다음을 생성합니다.

* 예제 웹 사이트에서 컨텐츠 페이지를 만드는 데 사용할 컨텐츠 페이지 템플릿
* 컨텐츠의 페이지를 렌더링하는 데 사용할 컨텐츠 페이지 구성 요소입니다
* 콘텐츠 페이지 스크립트

### 컨텐트 페이지 템플릿 만들기 {#creating-the-contentpage-template}

사이트의 웹 페이지를 기반으로 사용할 템플릿을 만듭니다.

템플릿은 새 페이지의 기본 컨텐츠를 정의합니다. 복잡한 웹 사이트에서는 사이트에서 다른 유형의 페이지를 만드는 데 여러 템플릿을 사용할 수 있습니다. 이 연습에서는 모든 페이지가 하나의 간단한 템플릿을 기반으로 합니다.

1. CRXDE Lite의 폴더 트리에서 마우스 오른쪽 버튼을 클릭합니다 `/apps/mywebsite/templates` 을(를) 클릭합니다. **[!UICONTROL 만들기 > 템플릿 만들기]**.

1. 템플릿 만들기 대화 상자에서 다음 값을 입력한 다음 을 클릭합니다 **[!UICONTROL 다음]**:

   * **[!UICONTROL 레이블]**: contentpage
   * **[!UICONTROL 제목]**: 내 웹 사이트 컨텐츠 페이지 템플릿
   * **[!UICONTROL 설명]**: 내 웹 사이트 컨텐츠 페이지 템플릿입니다.
   * **[!UICONTROL 리소스 유형]**: 웹 사이트/구성 요소/콘텐츠 페이지

   Ranking 속성에 기본값을 사용합니다.

   ![chlimage_1-104](assets/chlimage_1-104.png)

   리소스 유형은 페이지를 렌더링하는 구성 요소를 식별합니다. 이 경우 컨텐트 페이지 템플릿을 사용하여 만든 모든 페이지는 `mywebsite/components/contentpage` 구성 요소.

1. 이 템플릿을 사용할 수 있는 페이지의 경로를 지정하려면 더하기 단추를 클릭하고 다음을 입력합니다 `/content(/.*)?` 표시되는 텍스트 상자에 나타납니다. 그런 다음 **[!UICONTROL 다음]**.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   허용되는 경로 속성 값은 *정규 표현식.* 표현식과 일치하는 경로가 있는 페이지에서는 템플릿을 사용할 수 있습니다. 이 경우 정규 표현식이 `/content` 폴더 및 모든 하위 페이지.

   작성자가 아래 페이지를 만들 때 `/content`, **[!UICONTROL contentpage]** 사용할 수 있는 템플릿 목록에 템플릿이 표시됩니다.

1. 클릭 **[!UICONTROL 다음]** 에서 **[!UICONTROL 허용된 부모]** 및 **[!UICONTROL 허용된 하위]** 패널 및 클릭 **[!UICONTROL 확인]**. CRXDE Lite에서 **[!UICONTROL 모두 저장]**.

   ![chlimage_1-106](assets/chlimage_1-106.png)

#### 컨텐츠 페이지 구성 요소 만들기 {#creating-the-contentpage-component}

만들기 *구성 요소* 컨텐츠는 정의하고 컨텐트 페이지 템플릿을 사용하는 페이지를 렌더링합니다. 구성 요소의 위치는 contentpage 템플릿의 리소스 유형 속성 값과 일치해야 합니다.

1. CRXDE Lite에서 마우스 오른쪽 단추 클릭 `/apps/mywebsite/components` 을(를) 클릭합니다. **[!UICONTROL 만들기 > 구성 요소]**.
1. 에서 **[!UICONTROL 구성 요소 만들기]** 대화 상자에서 다음 속성 값을 입력합니다.

   * **[!UICONTROL 레이블]**: contentpage
   * **[!UICONTROL 제목]**: 내 웹 사이트 컨텐츠 페이지 구성 요소
   * **[!UICONTROL 설명]**: 내 웹 사이트 컨텐츠 페이지 구성 요소입니다

   ![chlimage_1-107](assets/chlimage_1-107.png)

   새 구성 요소의 위치는 다음과 같습니다 `/apps/mywebsite/components/contentpage`. 이 경로는 컨텐츠 페이지 템플릿의 리소스 유형(초기값을 뺀)에 해당합니다 `/apps/` 패스에 속해 있어야 합니다.

   이 서신은 템플릿을 구성 요소에 연결하며 웹 사이트의 올바른 기능에 중요합니다.

1. 클릭 **[!UICONTROL 다음]** 까지 **[!UICONTROL 허용된 하위]** 대화 상자의 패널이 나타나고 **[!UICONTROL 확인]**. CRXDE Lite에서 **[!UICONTROL 모두 저장]**.

   이제 구조가 다음과 같이 표시됩니다.

   ![chlimage_1-108](assets/chlimage_1-108.png)

#### 컨텐츠 페이지 구성 요소 스크립트 개발 {#developing-the-contentpage-component-script}

contentpage.jsp 스크립트에 코드를 추가하여 페이지 컨텐츠를 정의합니다.

1. CRXDE Lite에서 파일을 엽니다 `contentpage.jsp` in `/apps/mywebsite/components/contentpage`. 파일에는 기본적으로 다음 코드가 포함되어 있습니다.

   ```java
   <%--
   
     My Website Content Page Component component.
   
     This is My Website Content Page Component.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %><%
   %><%
       /* TODO add you code here */
   %>
   ```

1. 다음 코드를 복사하여 기본 코드 뒤에 contentpage.jsp에 붙여넣습니다.

   ```java
   <%@ page language="java" contentType="text/html; charset=ISO-8859-1"
       pageEncoding="ISO-8859-1"%>
   <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
   "https://www.w3.org/TR/html4/loose.dtd">
   <html>
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
   <title>My title</title>
   </head>
   <body>
   <div>My body</div>
   </body>
   </html>
   ```

1. 클릭 **[!UICONTROL 모두 저장]** 변경 사항을 저장하려면 을 클릭합니다.

### 웹 사이트 페이지 및 컨텐츠 페이지 만들기 {#creating-your-website-page-and-content-pages}

이 섹션에서는 모두 컨텐트 페이지 템플릿을 사용하는 다음 페이지를 만듭니다. 내 웹 사이트, 영어, 제품, 서비스 및 고객.

1. AEM 시작 페이지([http://localhost:4502/libs/cq/core/content/welcome.html](http://localhost:4502/libs/cq/core/content/welcome.html))에서 웹 사이트 를 클릭합니다.

   ![chlimage_1-109](assets/chlimage_1-109.png)

1. 폴더 트리에서 **[!UICONTROL 웹 사이트]** 폴더를 만든 다음 **[!UICONTROL 새로 만들기 > 새 페이지]**.
1. 에서 **[!UICONTROL 페이지 만들기]** 창에서 다음을 입력합니다.

   * **[!UICONTROL 제목]**: `My Website`
   * **[!UICONTROL 이름]**: `mywebsite`
   * 을(를) 선택합니다 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

   ![chlimage_1-110](assets/chlimage_1-110.png)

1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 폴더 트리에서 `/Websites/My Website` 페이지를 클릭하고 **[!UICONTROL 새로 만들기 > 새 페이지]**.
1. 에서 **[!UICONTROL 페이지 만들기]** 대화 상자에서 다음 속성 값을 입력한 다음 만들기를 클릭합니다.

   * **[!UICONTROL 제목]**: 영어
   * **[!UICONTROL 이름]**: en
   * 을(를) 선택합니다 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

1. 폴더 트리에서 `/Websites/My Website/English` 페이지를 클릭하고 **[!UICONTROL 새로 만들기 > 새 페이지]**.
1. 에서 **[!UICONTROL 페이지 만들기]** 대화 상자에서 다음 속성 값을 입력한 다음 **[!UICONTROL 만들기]**:

   * **[!UICONTROL 제목]**: 제품
   * 을(를) 선택합니다 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

1. 폴더 트리에서 `/Websites/My Website/English` 페이지를 클릭하고 **[!UICONTROL 새로 만들기 > 새 페이지]**.
1. 에서 **[!UICONTROL 페이지 만들기]** 대화 상자에서 다음 속성 값을 입력한 다음 **[!UICONTROL 만들기]**:

   * **제목**: 서비스
   * 을(를) 선택합니다 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

1. 폴더 트리에서 `/Websites/My Website/English` 페이지를 클릭하고 **[!UICONTROL 새로 만들기 > 새 페이지]**.
1. 에서 **[!UICONTROL 페이지 만들기]** 대화 상자에서 다음 속성 값을 입력한 다음 **[!UICONTROL 만들기]**:

   * **제목**: 고객
   * 을(를) 선택합니다 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

   구조가 다음과 같습니다.

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. 페이지를 웹 사이트 디자인에 연결하려면 CRXDE Lite에서 `/content/mywebsite/en/jcr:content` 노드 아래에 있어야 합니다. 설정 **[!UICONTROL 속성]** 탭에서 새 속성에 대해 다음 값을 입력한 다음 추가를 클릭합니다.

   * **[!UICONTROL 이름]**: cq:designPath
   * **[!UICONTROL 유형]**: 문자열
   * **[!UICONTROL 값]**: /etc/designs/mywebsite

   ![chlimage_1-112](assets/chlimage_1-112.png)

1. 새 웹 브라우저 탭 또는 창에서 엽니다. [http://localhost:4502/content/mywebsite/en/products.html](http://localhost:4502/content/mywebsite/en/products.html) 제품 페이지를 보려면 다음을 수행하십시오.

   ![chlimage_1-113](assets/chlimage_1-113.png)

### 콘텐츠 페이지 스크립트 개선 {#enhancing-the-contentpage-script}

이 섹션에서는 AEM 기초 구성 요소 스크립트를 사용하여 컨텐츠 페이지 스크립트를 강화하고 스크립트를 작성하는 방법을 설명합니다.

다음 **[!UICONTROL 제품]** 페이지 모습은 다음과 같습니다.

![chlimage_1-4](assets/chlimage_1-4.jpeg)

#### 기초 페이지 스크립트 사용 {#using-the-foundation-page-scripts}

이 연습에서는 상위 유형이 AEM 페이지 구성 요소되도록 Pagecontent 구성 요소를 구성합니다. 구성 요소는 상위 유형의 기능을 상속하므로 페이지 컨텐츠는 페이지 구성 요소의 스크립트와 속성을 상속합니다.

예를 들어, 구성 요소 JSP 코드에서는 수퍼 유형 구성 요소가 제공하는 스크립트를 구성 요소에 포함된 것처럼 참조할 수 있습니다.

1. CRXDE Lite에서 속성을 `/apps/mywebsite/components/contentpage` 노드 아래에 있어야 합니다.

   1. 을(를) 선택합니다 `/apps/mywebsite/components/contentpage` 노드 아래에 있어야 합니다.
   1. 속성 탭 하단에서 다음 속성 값을 입력한 다음 추가를 클릭합니다.

      * **[!UICONTROL 이름]**: sling:resourceSuperType
      * **[!UICONTROL 유형]**: 문자열
      * **[!UICONTROL 값]**: foundation/components/page
   1. 클릭 **[!UICONTROL 모두 저장]**.


1. 를 엽니다. `contentpage.jsp` 파일 위치 `/apps/mywebsite/components/contentpage` 및 는 기존 코드를 다음 코드로 바꿉니다.

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" contentType="text/html; charset=utf-8" %><%
   %><!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "https://www.w3.org/TR/html4/strict.dtd">
   <html>
   <cq:include script="head.jsp"/>
   <cq:include script="body.jsp"/>
   </html>
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 다음과 같습니다.

   ![chlimage_1-5](assets/chlimage_1-5.jpeg)

   페이지 소스를 열어 head.jsp 및 body.jsp 스크립트가 생성한 javascript 및 HTML 요소를 확인합니다. 페이지를 열 때 다음 스크립트 코드 조각은 사이드 킥을 엽니다.

   ```java
   CQ.WCM.launchSidekick("/content/mywebsite/en/products",
               {propsDialog: "/libs/foundation/components/page/dialog",
                  locked: false locked: false
                }); 
   ```

#### 자체 스크립트 사용 {#using-your-own-scripts}

이 섹션에서는 각각 페이지 본문의 일부를 생성하는 여러 스크립트를 만듭니다. 그런 다음 pagecontent 구성 요소에서 body.jsp 파일을 만들어 AEM Page 구성 요소의 body.jsp를 재정의합니다. body.jsp 파일에는 페이지 본문의 다른 부분을 생성하는 스크립트가 포함됩니다.

**팁:** 구성 요소의 상위 형식에 파일과 동일한 이름 및 상대 위치를 갖는 파일이 구성 요소에 포함되어 있으면 이 파일을 라고 합니다 *오버레이*.

1. CRXDE Lite에서 파일을 만듭니다 `left.jsp` 아래에 `/apps/mywebsite/components/contentpage`:

   1. 노드를 마우스 오른쪽 단추로 클릭합니다. `/apps/mywebsite/components/contentpage`를 선택하고 을 선택합니다. **[!UICONTROL 만들기]** 그런 다음 **[!UICONTROL 파일 만들기]**.
   1. 창에 `left.jsp` ** 이름** 을 클릭하고 **[!UICONTROL 확인]**.

1. 파일 편집 `left.jsp` 기존 콘텐츠를 제거하고 다음 코드로 대체합니다.

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="left">
   <div>logo</div>
   <div>newslist</div>
   <div>search</div>
   </div>
   ```

1. 변경 사항을 저장합니다.
1. CRXDE Lite에서 파일을 만듭니다 `center.jsp` 아래에 `/apps/mywebsite/components/contentpage`:

   1. 노드를 마우스 오른쪽 단추로 클릭합니다. `/apps/mywebsite/components/contentpage`, 선택 **[!UICONTROL 만들기]**, 그런 다음 **[!UICONTROL 파일 만들기]**.
   1. 대화 상자에서 다음을 입력합니다 `center.jsp` 로서의 **[!UICONTROL 이름]** 을(를) 클릭합니다. **[!UICONTROL 확인]**.

1. 파일 편집 `center.jsp` 기존 콘텐츠를 제거하고 다음 코드로 바꿉니다.

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="center">
   <div>trail</div>
   <div>title</div>
   <div>parsys</div>
   </div>
   ```

1. 변경 사항을 저장합니다.
1. CRXDE Lite에서 파일을 만듭니다 `right.jsp` 아래에 `/apps/mywebsite/components/contentpage`:

   1. 노드를 마우스 오른쪽 단추로 클릭합니다. `/apps/mywebsite/components/contentpage`, 선택 **[!UICONTROL 만들기]**, 그런 다음 **[!UICONTROL 파일 만들기]**.
   1. 대화 상자에서 다음을 입력합니다 `right.jsp` 로서의 **[!UICONTROL 이름]** 을(를) 클릭합니다. **[!UICONTROL 확인]**.

1. 파일 편집 `right.jsp` 기존 콘텐츠를 제거하고 다음 코드로 대체합니다.

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="right">
   <div>iparsys</div>
   </div>
   ```

1. 변경 사항을 저장합니다.
1. CRXDE Lite에서 파일을 만듭니다 `body.jsp` 아래에 `/apps/mywebsite/components/contentpage`:
1. 파일 편집 `body.jsp` 기존 콘텐츠를 제거하고 다음 코드로 대체합니다.

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><body>
   <div id="CQ">
   <div class="topnav">topnav</div>
   <div class="content">
   <cq:include script="left.jsp" />
   <cq:include script="center.jsp" />
   <cq:include script="right.jsp" />
   </div>
   <div class="footer">
   <div class="toolbar">toolbar</div>
   </div>
   </div>
   </body>
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 다음과 같습니다.

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

### 위쪽 탐색 구성 요소 만들기 {#creating-the-top-navigation-component}

이 섹션에서는 탐색을 쉽게 하기 위해 웹 사이트의 모든 상위 수준 페이지에 대한 링크를 표시하는 구성 요소를 만듭니다. 이 구성 요소 컨텐츠는 컨텐트 페이지 템플릿을 사용하여 만든 모든 페이지의 맨 위에 나타납니다.

위쪽 탐색 구성 요소의 첫 번째 버전(위쪽 탐색)에서는 탐색 항목이 텍스트 링크만 됩니다. 두 번째 버전에서는 이미지 탐색 링크를 사용하여 위쪽 탐색을 구현합니다.

위쪽 탐색은 다음과 같습니다.

![chlimage_1-114](assets/chlimage_1-114.png)

#### 위쪽 탐색 구성 요소 만들기 {#creating-the-top-navigation-component-1}

1. CRXDE Lite에서 마우스 오른쪽 단추 클릭 `/apps/mywebsite/components`, 선택 **[!UICONTROL 만들기]**, 그런 다음 **[!UICONTROL 구성 요소 만들기]**.
1. 에서 **[!UICONTROL 구성 요소 만들기]** 창에서 다음을 입력합니다.

   * **[!UICONTROL 레이블]**: `topnav`
   * **[!UICONTROL 제목]**: `My Top Navigation Component`
   * **[!UICONTROL 설명]**: `This is My Top Navigation Component`

1. 클릭 **[!UICONTROL 다음]** 마지막 창으로 이동하여 **[!UICONTROL 확인]**. 변경 사항을 저장합니다.

#### 텍스트 링크로 위쪽 탐색 스크립트 만들기 {#creating-the-top-navigation-script-with-textual-links}

위쪽 탐색에 렌더링 스크립트를 추가하여 하위 페이지에 대한 텍스트 링크를 생성합니다.

1. CRXDE Lite에서 파일을 엽니다 `topnav.jsp` 아래에 `/apps/mywebsite/components/topnav`.
1. 다음 코드를 복사하여 붙여 넣어 해당 코드를 바꿉니다.

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><% 
   %><%@ page import="java.util.Iterator,
           com.day.text.Text, 
           com.day.cq.wcm.api.PageFilter, com.day.cq.wcm.api.Page" %><% 
       /* get starting point of navigation */
       Page navRootPage = currentPage.getAbsoluteParent(2); 
       if (navRootPage == null && currentPage != null) { 
       navRootPage = currentPage; 
       }
       if (navRootPage != null) { 
           Iterator<Page> children = navRootPage.listChildren(new PageFilter(request));
           while (children.hasNext()) { 
               Page child = children.next(); 
               %><a href="<%= child.getPath() %>.html"><%=child.getTitle() %></a><% 
           } 
       } 
   %> 
   ```

#### Contentpage 구성 요소에 위쪽 탐색 포함 {#including-top-navigation-in-the-contentpage-component}

contentpage 구성 요소에 topnav를 포함하려면

1. CRXDE Lite에서 `body.jsp` 아래에 `/apps/mywebsite/components/contentpage`및 바꾸기:

   ```xml
   <div class="topnav">topnav</div>
   ```

   with:

   ```xml
   <cq:include path="topnav" resourceType="mywebsite/components/topnav" />
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 위쪽 탐색은 다음과 같이 나타납니다.

   ![chlimage_1-115](assets/chlimage_1-115.png)

#### 자막을 사용하여 페이지 개선 {#enhancing-pages-with-subtitles}

다음 **[!UICONTROL 페이지]** 구성 요소는 페이지에 자막을 제공할 수 있는 속성을 정의합니다. 페이지 컨텐츠에 대한 정보를 제공하는 자막을 추가합니다.

1. 브라우저에서 **[!UICONTROL 제품]** 페이지.
1. 사이드 킥에서 **[!UICONTROL 페이지]** 탭, **[!UICONTROL 페이지 속성]**.
1. 설정 **[!UICONTROL 기본]** 대화 상자의 탭에서 다음을 확장합니다. **[!UICONTROL 추가 제목 및 설명]** 및 **[!UICONTROL 자막]** property, type `what we do`. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.
1. 이전 단계를 반복하여 자막을 추가합니다 **서비스 정보** 변환 후 **[!UICONTROL 서비스]** 페이지.
1. 이전 단계를 반복하여 자막을 추가합니다 **우리가 얻는 신뢰** 변환 후 **[!UICONTROL 고객]** 페이지.

   **팁:** CRXDE Lite에서 /content/mywebsite/en/products/jcr:content 노드를 선택하여 자막 속성이 추가되었는지 확인합니다.

#### 이미지 링크를 사용하여 위쪽 탐색 기능 향상 {#enhance-top-navigation-by-using-image-links}

탐색 컨트롤에 하이퍼텍스트 대신 이미지 링크를 사용하도록 topnav 구성 요소의 렌더링 스크립트를 개선합니다. 이미지에는 링크 대상의 제목과 부제가 포함됩니다.

이 연습은 [Sling 요청 처리](/help/sites-developing/the-basics.md#sling-request-processing). topnav.jsp 스크립트는 페이지 탐색 링크에 사용할 이미지를 동적으로 생성하는 스크립트를 호출하도록 수정되었습니다. 이 연습에서 Sling은 이미지 소스 파일의 URL을 구문 분석하여 이미지를 렌더링하는 데 사용할 스크립트를 결정합니다.

예를 들어 제품 페이지에 대한 이미지 링크의 소스는 http://localhost:4502/content/mywebsite/en/products.navimage.png일 수 있습니다. Sling은 이 URL을 구문 분석하여 리소스 유형과 리소스를 렌더링하는 데 사용할 스크립트를 결정합니다.

1. Sling은 전송할 리소스의 경로를 결정합니다 `/content/mwebysite/en/products.png.`
1. Sling이 `/content/mywebsite/en/products` 노드 아래에 있어야 합니다.
1. Sling이 을 결정합니다 `sling:resourceType` 이 노드의 `mywebsite/components/contentpage`.

1. Sling은 이 구성 요소에서 URL 선택기( `navimage`) 및 파일 이름 확장명( ) `png`).

이 연습에서 Sling은 이러한 URL을 사용자가 작성하는 /apps/mywebsite/components/contentpage/navimage.png.java 스크립트에 연결합니다.

1. CRXDE Lite에서 `topnav.jsp` 아래에 `/apps/mywebsite/components/topnav.`앵커 요소의 컨텐츠(14행)를 찾습니다.

   ```xml
   <%=child.getTitle() %>
   ```

1. 앵커 컨텐츠를 다음 코드로 바꿉니다.

   ```xml
   <img alt="<%= child.getTitle() %>" src="<%= child.getPath() %>.navimage.png">
   ```

1. 변경 사항을 저장합니다.
1. 마우스 오른쪽 단추를 클릭합니다. `/apps/mywebsite/components/contentpage` 노드 및 **[!UICONTROL 만들기 > 파일 만들기]**.
1. 에서 **[!UICONTROL 파일 만들기]** 다음과 같이 **[!UICONTROL 이름]**, 유형 `navimage.png.java`.

   .java 파일 이름 확장자는 Apache Sling Scripting Java 지원을 사용하여 스크립트를 컴파일하고 서블릿을 만들어야 함을 Sling에 나타냅니다.

1. 다음 코드를에 복사합니다. `navimage.png.java.`이 코드는 AbstractImageServlet 클래스를 확장합니다.

   * [AbstractImageServlet](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html) 현재 리소스의 속성을 저장하는 ImageContext 개체를 만듭니다.
   * 리소스의 상위 페이지는 ImageContext 개체에서 추출됩니다. 그러면 페이지 제목과 부제목을 얻습니다.
   * [ImageHelper](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/ImageHelper.html) 사이트 디자인의 navimage_bg.jpg 파일, 페이지 제목 및 페이지 자막에서 이미지를 생성하는 데 사용됩니다.

   ```java
   package apps.mywebsite.components.contentpage;
   
   import java.awt.Color; 
   import java.awt.Paint; 
   import java.awt.geom.Rectangle2D; 
   
   import java.io.IOException;
   import javax.jcr.RepositoryException; 
   
   import com.day.cq.wcm.api.Page; 
   import com.day.cq.wcm.api.PageManager; 
   import com.day.cq.wcm.api.components.Component; 
   import com.day.cq.wcm.api.designer.Designer;
   
   import com.day.cq.commons.SlingRepositoryException; 
   import com.day.cq.wcm.commons.WCMUtils; 
   import com.day.cq.wcm.commons.AbstractImageServlet; 
   import com.day.cq.commons.ImageHelper; 
   
   import com.day.image.Font; 
   import com.day.image.Layer; 
   
   import org.apache.sling.api.SlingHttpServletRequest; 
   import org.apache.sling.api.SlingHttpServletResponse; 
   import org.apache.sling.api.resource.Resource; 
   import org.apache.sling.api.servlets.SlingSafeMethodsServlet; 
   
   /**
     * Renders the navigation image
     */ 
   public class navimage_png extends AbstractImageServlet {
   
         protected Layer createLayer(ImageContext ctx)
                throws RepositoryException, IOException {
            PageManager pageManager = ctx.resolver.adaptTo(PageManager.class);
            Page currentPage = pageManager.getContainingPage(ctx.resource);
   
            /* constants for image appearance */
            int scale = 6;
            int paddingX = 24;
            int paddingY = 24;
            Color bgColor = new Color(0x004a565c, true);
   
            /* obtain the page title */
            String title = currentPage.getTitle();
            if (title == null) {
                title = currentPage.getName();
            }
   
            /* format the title text */
            title = title.toUpperCase();
            Paint titleColor = Color.WHITE;
            Font titleFont = new Font("Myriad Pro", 10 * scale, Font.BOLD);
            int titleBase = 10 * scale;
   
            /* obtain and format the page subtitle */
            String subtitle = currentPage.getProperties().get("subtitle", "");
            Paint subtitleColor = new Color(0xffa9afb1, true);
            Font subTitleFont = new Font("Tahoma", 7);
            int subTitleBase = 20;
   
            /* create a layer that contains the background image from the mywebsite design */
            Designer dg = ctx.resolver.adaptTo(Designer.class);
            String imgPath = new String(dg.getDesignPath(currentPage)+"/images/navimage_bg.jpg");
            Layer bg = ImageHelper.createLayer(ctx.resolver.resolve(imgPath));
   
            /* draw the title text (4 times bigger) */
            Rectangle2D titleExtent = titleFont.getTextExtent(0, 0, 0, 0, title, Font.ALIGN_LEFT, 0, 0);
            Rectangle2D subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
   
            /* ensure subtitleExtent is wide enough */
            if ( subtitle.length() > 0 ) {
                int titleWidth = (int)titleExtent.getWidth() / scale;
                if ( subtitleExtent.getWidth() > titleWidth && subtitleExtent.getWidth() + 2 * paddingX >
    bg.getWidth() ) {
                    int charWidth = (int)subtitleExtent.getWidth() / subtitle.length();
                    int maxWidth = (bg.getWidth() > titleWidth + 2  * paddingX ? bg.getWidth() - 2 * paddingX : titleWidth);
                    int len = (maxWidth - ( 2 * charWidth) ) / charWidth;
                    subtitle = subtitle.substring(0, len) + "...";
                    subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
                }
            }
            int width = Math.max((int) titleExtent.getWidth(), (int) subtitleExtent.getWidth());
           /* create the text layer */
            Layer text = new Layer(width, (int) titleExtent.getHeight() + 40, new Color(0x01ffffff, true));
            text.setPaint(titleColor);
            text.drawText(0, titleBase, 0, 0, title, titleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0);
            text.resize(text.getWidth() / scale, text.getHeight() / scale);
            text.setX(0);
            text.setY(0);
   
            if (subtitle.length() > 0) {
                /* draw the subtitle normal sized */
                text.setPaint(subtitleColor);
                text.drawText(0, subTitleBase, 0, 0, subtitle, subTitleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0); 
            }
   
            /* merge the image and text layers */
            text.setY(paddingY);
            text.setX(paddingX);
            text.setBackgroundColor(bgColor);
   
            int bgWidth = bg.getWidth();
            if ( text.getWidth() + 2 * paddingX > bgWidth ) {
                bgWidth = text.getWidth() + 2 * paddingX;
                bg.resize(bgWidth, bg.getHeight());
            }
            bg.merge(text);
   
            return bg;
        }
    }
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 이제 위쪽 탐색이 다음과 같이 나타납니다.

   ![screen_shot_2012-03-07at10047pm](assets/screen_shot_2012-03-07at10047pm.png)

### 목록 하위 구성 요소 생성 {#creating-the-list-children-component}

제목, 설명 및 페이지 날짜(예: 제품 페이지)를 포함하는 페이지 링크 목록을 생성하는 목록 하위 구성 요소를 만듭니다. 링크는 현재 페이지의 하위 페이지나 구성 요소 대화 상자에 지정된 루트 페이지의 하위 페이지를 타겟팅합니다.

![chlimage_1-116](assets/chlimage_1-116.png)

#### 제품 페이지 만들기 {#creating-product-pages}

아래에 있는 두 페이지를 만듭니다. **[!UICONTROL 제품]** 페이지. 두 가지 특정 제품을 설명하는 각 페이지에 대해 제목, 설명 및 날짜를 설정합니다.

1. 의 폴더 트리에서 **[!UICONTROL 웹 사이트]** 페이지에서 을 선택합니다 **[!UICONTROL 웹 사이트/내 웹 사이트/영어/제품]** 항목을 선택하고 **[!UICONTROL 새로 만들기 > 새 페이지]**.
1. 대화 상자에서 다음 속성 값을 입력한 다음 를 클릭합니다 **[!UICONTROL 만들기]**:

   * **[!UICONTROL 제목]**: 제품 1.
   * **[!UICONTROL 이름]**: product1.
   * 선택 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

1. 다음 속성 값을 사용하여 제품 아래에 다른 페이지를 만듭니다.

   * **[!UICONTROL 제목]**: 제품 2
   * **[!UICONTROL 이름]**: product2
   * 선택 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

1. CRXDE Lite에서 제품 1 페이지의 설명 및 날짜를 설정합니다.

   1. 을(를) 선택합니다 `/content/mywebsite/en/products/product1/jcr:content` 노드 아래에 있어야 합니다.
   1. 에서 **[!UICONTROL 속성]** 탭에서 다음 값을 입력합니다.

      * **[!UICONTROL 이름]**: `jcr:description`
      * **[!UICONTROL 유형]**: `String`
      * **[!UICONTROL 값]**: `This is a description of the Product 1!.`
   1. 클릭 **[!UICONTROL 추가]**.
   1. 에서 **[!UICONTROL 속성]** 탭에서 다음 값을 사용하여 다른 속성을 만듭니다.

      * **[!UICONTROL 이름]**: 날짜
      * **[!UICONTROL 유형]**: 문자열
      * **[!UICONTROL 값]**: 02/14/2008
      * 클릭 **[!UICONTROL 추가]**.
   1. 클릭 **[!UICONTROL 모두 저장]**.



1. CRXDE Lite에서 제품 2 페이지의 설명 및 날짜를 설정합니다.

   1. 을(를) 선택합니다 `/content/mywebsite/en/products/product2/jcr:content` 노드 아래에 있어야 합니다.
   1. 에서 **[!UICONTROL 속성]** 탭에서 다음 값을 입력합니다.

      * **[!UICONTROL 이름]**: jcr:description
      * **[!UICONTROL 유형]**: 문자열
      * **[!UICONTROL 값]**: 제품 2!
   1. 클릭 **[!UICONTROL 추가]**.
   1. 동일한 텍스트 상자에서 이전 값을 다음 값으로 바꿉니다.

      * **[!UICONTROL 이름]**: 날짜
      * **[!UICONTROL 유형]**: 문자열
      * **[!UICONTROL 값]**: 05/11/2012
      * 클릭 **[!UICONTROL 추가]**.
   1. 클릭 **[!UICONTROL 모두 저장]**.



#### 목록 하위 구성 요소 생성 {#creating-the-list-children-component-1}

listchildren 구성 요소를 만들려면

1. CRXDE Lite에서 마우스 오른쪽 단추 클릭 `/apps/mywebsite/components`, 선택 **[!UICONTROL 만들기]**, 그런 다음 **[!UICONTROL 구성 요소 만들기]**.
1. 대화 상자에서 다음 속성 값을 입력한 다음 를 클릭합니다 **[!UICONTROL 다음]**:

   * **[!UICONTROL 레이블]**: listchildren.
   * **[!UICONTROL 제목]**: 내 Listchildren 구성 요소입니다.
   * **[!UICONTROL 설명]**: My Listchildren 구성 요소입니다.

1. 계속 클릭 **[!UICONTROL 다음]** 까지 **[!UICONTROL 허용된 하위]** 패널이 나타나고 **[!UICONTROL 확인]**.

#### 목록 하위 스크립트 만들기 {#creating-the-list-children-script}

listchildren 구성 요소에 대한 스크립트를 개발합니다.

1. CRXDE Lite에서 파일을 엽니다 `listchildren.jsp` 아래에 `/apps/mywebsite/components/listchildren`.
1. 기본 코드를 다음 코드로 바꿉니다.

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="java.util.Iterator,
            com.day.cq.wcm.api.PageFilter"%><%
        /* Create a new Page object using the path of the current page */ 
         String listroot = properties.get("listroot", currentPage.getPath());
        Page rootPage = pageManager.getPage(listroot);
        /* iterate through the child pages and gather properties */
        if (rootPage != null) {
            Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
            while (children.hasNext()) {
                Page child = children.next();
                String title = child.getTitle() == null ? child.getName() : child.getTitle();
                String date = child.getProperties().get("date","");
                %><div class="item">
                <a href="<%= child.getPath() %>.html"><b><%= title %></b></a>
                <span><%= date %></span><br>
                <%= child.getProperties().get("jcr:description","") %><br>
                </div><%
            }
        }
    %>
   ```

1. 변경 사항을 저장합니다.

#### 하위 목록 대화 상자 만들기 {#creating-the-list-children-dialog}

listchildren 구성 요소 속성을 구성하는 데 사용되는 대화 상자를 만듭니다.

1. listchildren 구성 요소 아래에 대화 상자 노드를 만듭니다.

   1. CRXDE Lite에서 `/apps/mywebsite/components/listchildren`노드 및 **[!UICONTROL 만들기 > 대화 상자 만들기]**.
   1. 대화 상자에서 다음 속성 값을 입력하고 확인을 클릭합니다

      * **[!UICONTROL 레이블]**: `dialog`
      * **[!UICONTROL 제목]**: `Edit Component` 을(를) 클릭합니다. **[!UICONTROL 확인]**.

   ![screen_shot_2012-03-07at45818pm](assets/screen_shot_2012-03-07at45818pm.png)

   다음 속성을 사용합니다.

   ![screen_shot_2012-03-07at50415pm](assets/screen_shot_2012-03-07at50415pm.png)

1. 을(를) 선택합니다 `/apps/mywebsite/components/listchildren/dialog/items/items/tab1` 노드 아래에 있어야 합니다.
1. 에서 **[!UICONTROL 속성]** 탭에서 값 변경 **[!UICONTROL 제목]** 속성 대상 `List Children`

   ![chlimage_1-117](assets/chlimage_1-117.png)

1. 을(를) 선택합니다 **tab1** 노드 및 **[!UICONTROL 만들기 > 노드 만들기]**&#x200B;다음 속성 값을 입력하고 **[!UICONTROL 확인]**:

   * **[!UICONTROL 이름]**: 항목
   * **[!UICONTROL 유형]**: cq:WidgetCollection

   ![screen_shot_2012-03-07at51018pm](assets/screen_shot_2012-03-07at51018pm.png)

1. 다음 속성 값을 사용하여 항목 노드 아래에 노드를 만듭니다.

   * **[!UICONTROL 이름]**: listroot
   * **[!UICONTROL 유형]**: cq:Widget

   ![screen_shot_2012-03-07at51031pm](assets/screen_shot_2012-03-07at51031pm.png)

1. 목록 루트 노드에 대한 속성을 추가하여 텍스트 필드로 구성합니다. 다음 테이블의 각 행은 속성을 나타냅니다. 완료되면 를 클릭합니다 **[!UICONTROL 모두 저장]**.

   | 이름 | 유형 | 값 |
   |---|---|---|
   | fieldLabel | 문자열 | 목록 루트의 경로 |
   | 이름 | 문자열 | ./listroot |
   | xtype | 문자열 | 텍스트 필드 |

   ![screen_shot_2012-03-07at51433pm](assets/screen_shot_2012-03-07at51433pm.png)

#### 컨텐트 페이지 구성 요소에 목록 하위 포함 {#including-list-children-in-the-contentpage-component}

컨텐트 페이지 구성 요소에 listchildren 구성 요소를 포함하려면 다음과 같이 진행하십시오.

1. CRXDE Lite에서 파일을 엽니다 `left.jsp` 아래에 `/apps/mywebsite/components/contentpage` 다음 코드(4행)를 찾습니다.

   ```xml
   <div>newslist</div>
   ```

1. 해당 코드를 다음 코드로 바꿉니다.

   ```xml
   <cq:include path="newslist" resourceType="mywebsite/components/listchildren" />
   ```

1. 변경 사항을 저장합니다.

#### 페이지에서 목록 하위 보기 {#viewing-list-children-in-a-page}

이 구성 요소의 전체 작업을 보려면 제품 페이지를 볼 수 있습니다.

* 상위 페이지(&quot;목록 루트의 경로&quot;)가 정의되지 않은 경우.
* 상위 페이지(&quot;목록 루트의 경로&quot;)가 정의된 경우

1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. listchildren 구성 요소는 다음과 같이 나타납니다.

   ![chlimage_1-118](assets/chlimage_1-118.png)

1. ![chlimage_1-119](assets/chlimage_1-119.png)

1. 목록 루트의 경로로 다음을 입력합니다. `/content/mywebsite/en`. **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 이제 페이지의 listchildren 구성 요소는 다음과 같습니다.

   ![chlimage_1-120](assets/chlimage_1-120.png)

### 로고 구성 요소 만들기 {#creating-the-logo-component}

회사 로고를 표시하고 사이트의 홈 페이지에 대한 링크를 제공하는 구성 요소를 만듭니다. 구성 요소에는 속성 값이 사이트 디자인(/etc/designs/mywebsite)에 저장되도록 디자인 모드 대화 상자가 포함되어 있습니다.

* 속성 값은 디자인을 사용하는 페이지에 추가되는 구성 요소의 모든 인스턴스에 적용됩니다.
* 속성은 디자인을 사용하는 페이지에 있는 구성 요소의 모든 인스턴스를 사용하여 구성할 수 있습니다.

디자인 모드 대화 상자에는 이미지와 링크 경로를 설정하기 위한 속성이 포함되어 있습니다. 로고 구성 요소는 웹 사이트에 있는 모든 페이지의 왼쪽 상단에 배치됩니다.

다음과 같이 표시됩니다.

![chlimage_1-121](assets/chlimage_1-121.png)

>[!NOTE]
>
>Adobe Experience Manager은 더 많은 기능을 갖춘 로고 구성 요소( `/libs/foundation/components/logo`).

#### 로고 구성 요소 노드 만들기 {#creating-the-logo-component-node}

로고 구성 요소를 만들려면 다음 단계를 수행합니다.

1. CRXDE Lite에서 /apps/mywebsite/components를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 만들기]**, 그런 다음 **[!UICONTROL 구성 요소 만들기]**.
1. 구성 요소 만들기 대화 상자에서 다음 속성 값을 입력한 다음 다음을 클릭합니다.

   * **[!UICONTROL 레이블]**: `logo`.
   * **[!UICONTROL 제목]**: `My Logo Component`.
   * **[!UICONTROL 설명]**: `This is My Logo Component`.

1. 대화 상자의 최종 패널에 도달할 때까지 다음 을 클릭한 다음 을 클릭합니다 **[!UICONTROL 확인]**.

#### 로고 스크립트 만들기 {#creating-the-logo-script}

이 섹션에서는 홈 페이지 링크와 함께 로고 이미지를 표시하는 스크립트를 만드는 방법을 설명합니다.

1. CRXDE Lite에서 파일을 엽니다 `logo.jsp` 아래에 `/apps/mywebsite/components/logo`.
1. 다음 코드는 사이트 홈 페이지에 대한 링크를 만들고 로고 이미지에 참조를 추가합니다. 에 코드 복사 `logo.jsp`:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.text.Text,
                      com.day.cq.wcm.foundation.Image,
                      com.day.cq.commons.Doctype" %><%
       /* obtain the path for home */
       long absParent = currentStyle.get("absParent", 2L);
       String home = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);
       /* obtain the image */
       Resource res = currentStyle.getDefiningResource("imageReference");
       if (res == null) {
           res = currentStyle.getDefiningResource("image");
       }
       /* if no image use text link, otherwise draw the image */
       %>
   <a href="<%= home %>.html"><%
       if (res == null) {
           %>Home<%
       } else {
           Image img = new Image(res);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out);
       }
       %></a>
   ```

1. 변경 사항을 저장합니다.

#### 로고 디자인 대화 상자 만들기 {#creating-the-logo-design-dialog}

디자인 모드에서 로고 구성 요소를 구성하는 대화 상자를 만듭니다. 디자인 모드 대화 상자 노드의 이름을 지정해야 합니다 `design_dialog`.

1. 로고 구성 요소 아래에 대화 상자 노드를 만듭니다.

   1. 마우스 오른쪽 단추를 클릭합니다. `/apps/mywebsite/components/logo` 노드 및 **[!UICONTROL 만들기 > 대화 상자 만들기]**.
   1. 다음 속성 값을 입력한 다음 **[!UICONTROL 확인]**:

      * **[!UICONTROL 레이블]** `design_dialog`
      * **[!UICONTROL 제목]** `Logo (Design)`

1. design_dialog 분기에서 tab1 노드를 마우스 오른쪽 버튼으로 클릭하고 삭제를 클릭합니다. 클릭 **[!UICONTROL 모두 저장]**.
1. 아래에 `design_dialog/items/items`노드, 이름이 인 새 노드 만들기 `img` 유형 `cq:Widget`. 다음 속성을 추가하고 을(를) 클릭합니다 **[!UICONTROL 모두 저장]**:

   | 이름 | 유형 | 값 |
   |---|---|---|
   | fileNameParameter | 문자열 | ./imageName |
   | fileReferenceParameter | 문자열 | ./imageReference |
   | 이름 | 문자열 | ./이미지 |
   | 제목 | 문자열 | 이미지 |
   | xtype | 문자열 | html5smartimage |

   ![chlimage_1-122](assets/chlimage_1-122.png)

#### 로고 렌더링 스크립트 만들기 {#creating-the-logo-render-script}

로고 이미지를 검색하고 페이지에 기록하는 스크립트를 만듭니다.

1. 로고 구성 요소 노드를 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL 만들기 > 파일 만들기]** img.GET.java라는 스크립트 파일을 만들려면
1. 파일을 열고 다음 코드를 파일에 복사한 다음 **[!UICONTROL 모두 저장]**:

```java
package apps.mywebsite.components.logo;

import java.io.IOException;
import java.io.InputStream;

import javax.jcr.RepositoryException;
import javax.jcr.Property;
import javax.servlet.http.HttpServletResponse;

import com.day.cq.wcm.foundation.Image;
import com.day.cq.wcm.commons.RequestHelper;
import com.day.cq.wcm.commons.WCMUtils;
import com.day.cq.wcm.commons.AbstractImageServlet;
import com.day.cq.commons.SlingRepositoryException;
import com.day.image.Layer;
import org.apache.commons.io.IOUtils;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ValueMap;
import org.apache.sling.api.servlets.SlingSafeMethodsServlet;

/**
 * Renders an image
 */
public class img_GET extends AbstractImageServlet {

    protected Layer createLayer(ImageContext c)
            throws RepositoryException, IOException {
        /* don't create the layer yet. handle everything later */
        return null;
    }

    protected void writeLayer(SlingHttpServletRequest req,
                              SlingHttpServletResponse resp,
                              ImageContext c, Layer layer)
            throws IOException, RepositoryException {

        Image image = new Image(c.resource);
        image.setItemName(Image.NN_FILE, "image");
        image.setItemName(Image.PN_REFERENCE, "imageReference");
        if (!image.hasContent()) {
            resp.sendError(HttpServletResponse.SC_NOT_FOUND);
            return;
        }
        /* get pure layer */
        layer = image.getLayer(false, false, false);

        /* do not re-encode layer, just spool */
        Property data = image.getData();
        InputStream in = data.getStream();
        resp.setContentLength((int) data.getLength());
        String contentType = image.getMimeType();
        if (contentType.equals("application/octet-stream")) {
            contentType=c.requestImageType;
        }
        resp.setContentType(contentType);
        IOUtils.copy(in, resp.getOutputStream());
        in.close();

        resp.flushBuffer();
    }
}
```

#### Contentpage 구성 요소에 로고 구성 요소 추가 {#adding-the-logo-component-to-the-contentpage-component}

1. CRXDE Lite에서 `left.jsp` 아래에 `/apps/mywebsite/components/contentpage file` 다음 코드 행을 찾습니다.

   ```xml
   <div>logo</div>
   ```

1. 해당 코드를 다음 코드 줄로 바꿉니다.

   ```xml
   <cq:include path="logo" resourceType="mywebsite/components/logo" />
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 로고는 현재 기본 링크만 표시되지만 다음과 같이 보입니다.

   ![chlimage_1-123](assets/chlimage_1-123.png)

#### 페이지에서 로고 이미지 설정 {#setting-the-logo-image-in-a-page}

이 섹션에서는 디자인 모드 대화 상자를 사용하여 이미지를 로고로 설정하는 방법을 설명합니다.

1. 사용 **[!UICONTROL 제품]** 브라우저에서 페이지를 열고 **[!UICONTROL 디자인]** 입력할 사이드 킥의 맨 아래에 있는 단추 **[!UICONTROL 디자인]** 모드.

   ![](do-not-localize/chlimage_1-10.png)

1. 로고 디자인 모음에서 **[!UICONTROL 편집]** 이 대화 상자를 사용하여 로고 구성 요소의 설정을 편집합니다.
1. 대화 상자에서 **[!UICONTROL 이미지]** 탭에서 `logo.png` 추출한 이미지 `mywebsite.zip` 파일을 클릭하고 **[!UICONTROL 확인]**.

   ![chlimage_1-124](assets/chlimage_1-124.png)

1. 사이드킥의 제목 표시줄에서 삼각형을 클릭하여 **[!UICONTROL 편집]** 모드.

   ![chlimage_1-7](assets/chlimage_1-7.jpeg)

1. CRXDE Lite에서 다음 노드로 이동하여 저장된 속성 값을 확인합니다.

   `/etc/designs/mywebsite/jcr:content/contentpage/logo`

### 탐색 표시 구성 요소 포함 {#including-the-breadcrumb-component}

이 섹션에서는 기초 구성 요소 중 하나인 탐색 표시(추적) 구성 요소를 포함합니다.

1. CRXDE Lite에서 `/apps/mywebsite/components/contentpage`에서 파일을 엽니다. `center.jsp` 및 바꾸기:

   ```java
   <div>trail</div>
   ```

   with:

   ```xml
   <cq:include path="trail" resourceType="foundation/components/breadcrumb" />
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품 1]** 페이지. 추적 구성 요소는 다음과 같습니다.

   ![chlimage_1-125](assets/chlimage_1-125.png)

### 제목 구성 요소 포함 {#including-the-title-component}

이 섹션에서는 기초 구성 요소 중 하나인 제목 구성 요소를 포함합니다.

1. CRXDE Lite에서 `/apps/mywebsite/components/contentpage`에서 파일을 엽니다. `center.jsp` 및 바꾸기:

   ```xml
   <div>title</div>
   ```

   with:

   ```xml
   <cq:include path="title" resourceType="foundation/components/title" />
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 제목 구성 요소는 다음과 같습니다.

   ![chlimage_1-126](assets/chlimage_1-126.png)

>[!NOTE]
>에서 다른 제목 및 유형/크기를 설정할 수 있습니다 **[!UICONTROL 편집]** 모드.

### 단락 시스템 구성 요소 포함 {#including-the-paragraph-system-component}

단락 시스템(parsys)은 단락 목록을 관리하기 때문에 웹 사이트의 중요한 부분입니다. 작성자가 페이지에 단락 구성 요소를 추가하고 구조를 제공할 수 있도록 해줍니다.

컨텐트 페이지 구성 요소에 parsys 구성 요소(기본 구성 요소 중 하나)를 추가합니다.

1. CRXDE Lite에서 `/apps/mywebsite/components/contentpage`에서 파일을 엽니다. `center.jsp` 다음 코드 행을 찾습니다.

   ```xml
   <div>parsys</div>
   ```

1. 해당 코드 행을 다음 코드로 바꾼 다음 변경 사항을 저장합니다.

   ```xml
   <cq:include path="par" resourceType="foundation/components/parsys" />
   ```

1. 브라우저에서 을(를) 새로 고칩니다. **[!UICONTROL 제품]** 페이지. 이제 parsys 구성 요소가 있으며, 다음과 같이 표시됩니다.

   ![chlimage_1-127](assets/chlimage_1-127.png)

### 이미지 구성 요소 만들기 {#creating-the-image-component}

단락 시스템에 이미지를 표시하는 구성 요소를 만듭니다. 시간을 절약하기 위해 이미지 구성 요소는 일부 속성이 변경된 로고 구성 요소의 사본으로 만들어집니다.

>[!NOTE]
>
>Adobe Experience Manager은 더 많은 기능을 갖춘 이미지 구성 요소( `/libs/foundation/components/image`).

#### 이미지 구성 요소 만들기 {#creating-the-image-component-1}

1. 마우스 오른쪽 단추를 클릭합니다. `/apps/mywebsite/components/logo` 노드 및 **[!UICONTROL 복사]**.
1. 마우스 오른쪽 단추를 클릭합니다. `/apps/mywebsite/components` 노드 및 **[!UICONTROL 붙여넣기]**.
1. 마우스 오른쪽 단추를 클릭합니다. `Copy of logo` 노드, **[!UICONTROL 이름 변경]**&#x200B;기존 텍스트 및 유형 삭제 `image`.

1. 을(를) 선택합니다 `image` 구성 요소 노드 및 다음 속성 값을 변경합니다.

   * `jcr:title:` 내 이미지 구성 요소.
   * `jcr:description`: 내 이미지 구성 요소입니다.

1. 에 속성 추가 `image` 노드(다음 속성 값 포함):

   * **[!UICONTROL 이름]**: componentGroup
   * **[!UICONTROL 유형]**: 문자열
   * **[!UICONTROL 값]**: MyWebsite

1. 아래의 `image` 노드, 이름 바꾸기 `design_dialog` 노드 끝 `dialog`.

1. 이름 변경 `logo.jsp` to `image.jsp.`

1. img.GET.java를 열고 패키지를 로 변경합니다. `apps.mywebsite.components.image`.

![chlimage_1-128](assets/chlimage_1-128.png)

#### 이미지 스크립트 만들기 {#creating-the-image-script}

이 섹션에서는 이미지 스크립트를 만드는 방법을 설명합니다.

1. 열기 `/apps/mywebsite/components/image/` `image.jsp`
1. 기존 코드를 다음 코드로 바꾼 다음 변경 사항을 저장합니다.

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.cq.commons.Doctype,
                       com.day.cq.wcm.foundation.Image,
                       com.day.cq.wcm.api.components.DropTarget,
                       com.day.cq.wcm.api.components.EditConfig,
                       com.day.cq.wcm.commons.WCMUtils" %><%
    /* global.jsp provides access to the current resource through the resource object */
           Image img = new Image(resource);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out); %>
   ```

1. 변경 사항을 저장합니다.

#### 이미지 cq:editConfig 노드 만들기 {#creating-the-image-cq-editconfig-node}

다음 `cq:editConfig` 노드 유형을 사용하면 속성을 편집할 때 구성 요소의 특정 동작을 구성할 수 있습니다.

이 섹션에서는 cq:editConfig 노드를 사용하여 Content Finder에서 이미지 구성 요소로 자산을 드래그할 수 있습니다.

1. CRXDE Lite의 /apps/mywebsite/components/image 노드에서 다음과 같이 새 노드를 만듭니다.

   * **[!UICONTROL 이름]**: cq:editConfig
   * **[!UICONTROL 유형]**: cq:EditConfig.

1. cq:editConfig 노드에서 다음과 같이 새 노드를 만듭니다.

   * **[!UICONTROL 이름]**: cq:dropTargets.
   * **[!UICONTROL 유형]**: cq:DropTargetConfig입니다.

1. cq:dropTargets 노드 아래에 다음과 같이 새 노드를 만듭니다.

   * **[!UICONTROL 이름]**: 이미지.
   * **[!UICONTROL 유형]**: nt:구조화되지 않습니다.

1. CRXDE에서 속성을 다음과 같이 설정합니다.

| 이름 | 유형 | 값 |
|---|---|---|
| 동의 | 문자열 | image/(gif) | jpeg | png) |
| 그룹 | 문자열 | 미디어 |
| propertyName | 문자열 | ./imageReference |

![chlimage_1-129](assets/chlimage_1-129.png)

#### 아이콘 추가 {#adding-the-icon}

이 섹션에서는 사이드 킥에 이미지 구성 요소가 나열되면 이미지 구성 요소 옆에 표시되는 아이콘을 추가합니다.

1. CRXDE Lite에서 파일을 마우스 오른쪽 단추로 클릭합니다. `/libs/foundation/components/image/icon.png` 을(를) 선택합니다. **[!UICONTROL 복사]**.
1. 노드를 마우스 오른쪽 단추로 클릭합니다. `/apps/mywebsite/components/image` 을(를) 클릭합니다. **[!UICONTROL 붙여넣기]**&#x200B;를 클릭한 다음 **[!UICONTROL 모두 저장]**.

#### 이미지 구성 요소 사용 {#using-the-image-component}

이 섹션에서는 **[!UICONTROL 제품]** 페이지를 방문하여 이미지 구성 요소를 단락 시스템에 추가합니다.

1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지.
1. 사이드 킥에서 **[!UICONTROL 디자인 모드]** 아이콘.
1. 을(를) 클릭합니다. **[!UICONTROL 편집]** 단락 디자인 대화 상자를 편집하는 단추입니다.
1. 대화 상자에서 다음 목록 **[!UICONTROL 허용된 구성 요소]** 가 표시됩니다. 이동 **[!UICONTROL MyWebsite]**&#x200B;에서 을(를) 선택합니다. **[!UICONTROL 내 이미지 구성 요소]** 을(를) 클릭합니다. **[!UICONTROL 확인]**.
1. 로 돌아가기 **[!UICONTROL 편집 모드]**.
1. parsys 프레임을 두 번 클릭합니다(켜짐). **[!UICONTROL 구성 요소 또는 자산을 여기로 드래그하십시오]**). 다음 **[!UICONTROL 새 구성 요소 삽입]** 및 **[!UICONTROL 사이드킥입니다]** 선택기는 다음과 같습니다.

   ![chlimage_1-8](assets/chlimage_1-8.jpeg)

### 도구 모음 구성 요소 포함 {#including-the-toolbar-component}

이 섹션에서는 기초 구성 요소 중 하나인 도구 모음 구성 요소를 포함합니다.

디자인 모드와 편집 모드에 있는 여러 가지 옵션이 있습니다.

1. CRXDE Lite에서 `/apps/mywebsite/components/contentpage`를 열고 `body.jsp` 파일에서 다음 코드를 찾습니다.

   ```java
   <div class="toolbar">toolbar</div>
   ```

1. 해당 코드를 다음 코드로 바꾸고 변경 내용을 저장합니다.

   ```java
   <cq:include path="toolbar" resourceType="foundation/components/toolbar"/>
   ```

1. AEM 웹 사이트 페이지의 폴더 트리에서 를 선택합니다 `Websites/My Website/English`를 클릭한 다음 **[!UICONTROL 새로 만들기 > 새 페이지]**. 다음 속성 값을 지정하고 생성을 누릅니다.

   * **[!UICONTROL 제목]**: 도구 모음
   * 선택 **[!UICONTROL 내 웹 사이트 컨텐츠 페이지 템플릿]**

1. 페이지 목록에서 **[!UICONTROL 도구 모음]** 페이지를 클릭하고 **[!UICONTROL 속성]**. 선택 **[!UICONTROL 탐색 시 숨기기]**&#x200B;를 클릭하고 **[!UICONTROL 확인]**.

   다음 **[!UICONTROL 탐색 시 숨기기]** 옵션을 사용하면 topnav 및 listchildren과 같은 탐색 구성 요소에 페이지가 표시되지 않습니다.

1. 아래 **[!UICONTROL 도구 모음]**, 다음 페이지를 만듭니다 .

   * 연락처
   * 피드백
   * 로그인
   * 검색

1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 다음과 같습니다.

   ![chlimage_1-130](assets/chlimage_1-130.png)

### 검색 구성 요소 만들기 {#creating-the-search-component}

이 섹션에서는 웹 사이트에서 컨텐츠를 검색하는 구성 요소를 만듭니다. 이 검색 구성 요소는 페이지의 단락 시스템(예: 전문 검색 결과 페이지)에 배치할 수 있습니다.

검색 입력 상자는 **[!UICONTROL 영어]** 페이지:

![chlimage_1-131](assets/chlimage_1-131.png)

#### 검색 구성 요소 만들기 {#creating-the-search-component-1}

1. CRXDE Lite에서 마우스 오른쪽 단추 클릭 `/apps/mywebsite/components`, 선택 **[!UICONTROL 만들기]**, 그런 다음 **[!UICONTROL 구성 요소 만들기]**.
1. 대화 상자를 사용하여 구성 요소를 구성합니다.

   1. 첫 번째 패널 중 하나에서 다음 속성 값을 지정합니다.

      * **[!UICONTROL 레이블]**: 검색
      * **[!UICONTROL 제목]**: 내 검색 구성 요소
      * **[!UICONTROL 설명]**: 내 검색 구성 요소입니다
      * **[!UICONTROL 그룹]**: MyWebsite
   1. 클릭 **[!UICONTROL 다음]**&#x200B;를 클릭한 다음 **[!UICONTROL 다음]** 다시 한 번
   1. 설정 **[!UICONTROL 허용된 부모]** 패널에서 **[!UICONTROL +]** 버튼 및 유형 `*/parsys`.
   1. 클릭 **[!UICONTROL 다음]** 을 클릭한 다음 **[!UICONTROL 확인]**.


1. 클릭 **[!UICONTROL 모두 저장]**.
1. 다음 노드를 복사하여 `apps/mywebsite/components/search` 노드:

   * `/libs/foundation/components/search/dialog`
   * `` `/libs/foundation/components/search/i18n`
   * `/libs/foundation/components/search/icon.png`

1. 클릭 **[!UICONTROL 모두 저장]**.

#### 검색 스크립트 만들기 {#creating-the-search-script}

이 섹션에서는 검색 스크립트를 만드는 방법을 설명합니다.

1. 를 엽니다. `/apps/mywebsite/components/search/search.jsp` 파일.
1. 다음 코드를에 복사합니다. `search.jsp`:

   ```java
   <%@ page import="com.day.cq.wcm.foundation.Search,com.day.cq.tagging.TagManager" %>
   <%@include file="/libs/foundation/global.jsp" %><%
   %><cq:setContentBundle/><%
       Search search = new Search(slingRequest);
   
       String searchIn = (String) properties.get("searchIn");
       String requestSearchPath = request.getParameter("path");
       if (searchIn != null) {
           /* only allow the "path" request parameter to be used if it
            is within the searchIn path configured */
           if (requestSearchPath != null && requestSearchPath.startsWith(searchIn)) {
               search.setSearchIn(requestSearchPath);
           } else {
               search.setSearchIn(searchIn);
           }
       } else if (requestSearchPath != null) {
           search.setSearchIn(requestSearchPath);
       }
   
       pageContext.setAttribute("search", search);
       TagManager tm = resourceResolver.adaptTo(TagManager.class);
   %><c:set var="trends" value="${search.trends}"/><%
   %><center>
     <form action="${currentPage.path}.html">
       <input size="41" maxlength="2048" name="q" value="${fn:escapeXml(search.query)}"/>
       <input value="<fmt:message key="searchButtonText"/>" type="submit" />
     </form>
   </center>
   <br/>
   <c:set var="result" value="${search.result}"/>
   <c:choose>
     <c:when test="${empty result && empty search.query}">
     </c:when>
     <c:when test="${empty result.hits}">
       <c:if test="${result.spellcheck != null}">
         <p><fmt:message key="spellcheckText"/> <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${result.spellcheck}"/></c:url>"><b><c:out value="${result.spellcheck}"/></b></a></p>
       </c:if>
       <fmt:message key="noResultsText">
         <fmt:param value="${fn:escapeXml(search.query)}"/>
       </fmt:message>
     </c:when>
     <c:otherwise>
       <p class="searchmeta">Results ${result.startIndex + 1} - ${result.startIndex + fn:length(result.hits)} of ${result.totalMatches} for <b>${fn:escapeXml(search.query)}</b>. (${result.executionTime} seconds)</p>
      <br/>
   
     <div class="searchresults"> 
       <div class="results">
         <c:forEach var="hit" items="${result.hits}" varStatus="status">
           <div class="hit">
           <a href="${hit.URL}">${hit.title}</a>
           <div class="excerpt">${hit.excerpt}</div>
          <div class="hiturl"> ${hit.URL}<c:if test="${!empty hit.properties['cq:lastModified']}"> - <c:catch><fmt:formatDate value="${hit.properties['cq:lastModified'].time}" dateStyle="medium"/></c:catch></c:if> - <a href="${hit.similarURL}"><fmt:message key="similarPagesText"/></a>
           </div></div>
         </c:forEach>
       </div>
         <br/>
   
        <div class="searchRight">
             <c:if test="${fn:length(trends.queries) > 0}">
                 <p><fmt:message key="searchTrendsText"/></p>
                 <div class="searchTrends">
                     <c:forEach var="query" items="${trends.queries}">
                         <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${query.query}"/></c:url>"><span style="font-size:${query.size}px"><c:out value="${query.query}"/></span></a>
                     </c:forEach>
                 </div>
             </c:if> 
             <c:if test="${result.facets.languages.containsHit}">
                 <p>Languages</p>
                 <c:forEach var="bucket" items="${result.facets.languages.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value='<%= new java.util.Locale((String) pageContext.getAttribute("bucketValue")).getDisplayLanguage(request.getLocale()) %>'/>
                     <c:choose>
                         <c:when test="${param.language != null}">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if> 
             <c:if test="${result.facets.tags.containsHit}">
                 <p>Tags</p>
                 <c:forEach var="bucket" items="${result.facets.tags.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="tag" value="<%= tm.resolve((String) pageContext.getAttribute("bucketValue")) %>"/>
                     <c:if test="${tag != null}">
                         <c:set var="label" value="${tag.title}"/>
                         <c:choose>
                             <c:when test="<%= request.getParameter("tag") != null && java.util.Arrays.asList(request.getParameterValues("tag")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="tag" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                             <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="tag" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                         </c:choose><br/>
                     </c:if>
                 </c:forEach>
             </c:if> 
             <c:if test="${result.facets.mimeTypes.containsHit}">
                 <jsp:useBean id="fileTypes" class="com.day.cq.wcm.foundation.FileTypes"/>
                 <p>File types</p>
                 <c:forEach var="bucket" items="${result.facets.mimeTypes.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value="${fileTypes[bucket.value]}"/>
                     <c:choose>
                         <c:when test="<%= request.getParameter("mimeType") != null && java.util.Arrays.asList(request.getParameterValues("mimeType")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
             <c:if test="${result.facets.lastModified.containsHit}">
                 <p>Last Modified</p>
                 <c:forEach var="bucket" items="${result.facets.lastModified.buckets}">
                     <c:choose>
                         <c:when test="${param.from == bucket.from && param.to == bucket.to}">${bucket.value} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/><c:if test="${bucket.from != null}"><cq:addParam name="from" value="${bucket.from}"/></c:if><c:if test="${bucket.to != null}"><cq:addParam name="to" value="${bucket.to}"/></c:if></cq:requestURL>">${bucket.value} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
   
         <c:if test="${fn:length(search.relatedQueries) > 0}">
   
          <br/><br/><div class="related">
           <fmt:message key="relatedSearchesText"/>
           <c:forEach var="rq" items="${search.relatedQueries}">
               <a href="${currentPage.path}.html?q=${rq}"><c:out value="${rq}"/></a>
           </c:forEach></div>
         </c:if>
         </div> 
   
         <c:if test="${fn:length(result.resultPages) > 1}">
           <div class="pagination"> 
               <fmt:message key="resultPagesText"/>
           <c:if test="${result.previousPage != null}">
             <a href="${result.previousPage.URL}"><fmt:message key="previousText"/></a>
           </c:if>
           <c:forEach var="page" items="${result.resultPages}">
             <c:choose>
               <c:when test="${page.currentPage}">${page.index + 1}</c:when>
               <c:otherwise>
                 <a href="${page.URL}">${page.index + 1}</a>
               </c:otherwise>
             </c:choose>
           </c:forEach>
           <c:if test="${result.nextPage != null}">
             <a href="${result.nextPage.URL}"><fmt:message key="nextText"/></a>
           </c:if>
           </div>
         </c:if>
         </div>
   
     </c:otherwise>
   </c:choose>
   ```

1. 변경 사항을 저장합니다.

#### 콘텐츠 페이지 구성 요소에 검색 상자 포함 {#including-a-search-box-in-the-contentpage-component}

컨텐트 페이지의 왼쪽 섹션에 검색 입력 상자를 포함하려면 다음과 같이 진행합니다.

1. CRXDE Lite에서 파일을 엽니다 `left.jsp` 아래에 `/apps/mywebsite/components/contentpage` 다음 코드(2행)를 찾습니다.

   ```xml
   %><div class="left">
   ```

1. 다음 코드를 삽입합니다 *이전* 해당 행:

   ```java
   %><%@ page import="com.day.text.Text"%><%
   %><% String docroot = currentDesign.getPath(); 
   String home = Text.getAbsoluteParent(currentPage.getPath(), 2);%><%
   ```

1. 다음 코드 행을 찾습니다.

   ```xml
   <div>search</div>
   ```

1. 해당 코드를 다음 코드로 바꾸고 변경 내용을 저장합니다.

   ```java
   <div class="form_1">
        <form class="geo" action="<%= home %>/toolbar/search.html" id="form" >
             <p>
                  <input class="geo" type="text" name="q"><br> 
                  <a href="<%= home %>/toolbar/search.html" class="link_1">advanced search</a> 
             </p>
        </form>
   </div>
   ```

1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 검색 구성 요소는 다음과 같습니다.

   ![chlimage_1-132](assets/chlimage_1-132.png)

#### 검색 페이지에 검색 구성 요소 포함 {#including-the-search-component-in-the-search-page}

이 섹션에서는 검색 구성 요소를 단락 시스템에 추가합니다.

1. 브라우저에서 **검색** 페이지.
1. 사이드 킥에서 **[!UICONTROL 디자인]** 모드 아이콘.
1. 단락 블록 디자인(검색 제목 아래)에서 **[!UICONTROL 편집]**.
1. 대화 상자에서 아래로 스크롤하여 **[!UICONTROL 내 웹 사이트]** 그룹, 선택 **[!UICONTROL 내 검색 구성 요소]** 을(를) 클릭합니다. **[!UICONTROL 확인]**.
1. 사이드 킥에서 삼각형을 클릭하여 다음으로 돌아갑니다 **[!UICONTROL 편집]** 모드.
1. 을(를) 드래그합니다. **[!UICONTROL 내 검색]** 구성 요소를 생성하지 않습니다. 다음과 같습니다.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. 로 이동합니다. **[!UICONTROL 제품]** 페이지. 입력 상자에서 고객을 검색하고 키를 누릅니다 **[!UICONTROL Enter 키]**. 으로 리디렉션됩니다. **[!UICONTROL 검색]** 페이지. 다음으로 전환 **[!UICONTROL 미리 보기]** 모드: 출력은 다음과 유사한 형식입니다.

   ![chlimage_1-134](assets/chlimage_1-134.png)

### Iparsys 구성 요소 포함 {#including-the-iparsys-component}

이 섹션에서는 기초 구성 요소 중 하나인 상속 단락 시스템(iparsys) 구성 요소를 포함합니다. 이 구성 요소를 사용하면 상위 페이지에서 단락 구조를 만들고 하위 페이지에서 단락을 상속하도록 할 수 있습니다.

이 구성 요소의 경우 편집 모드와 디자인 모드 모두에서 여러 매개 변수를 설정할 수 있습니다.

1. CRXDE Lite에서 `/apps/mywebsite/components/contentpage`에서 파일을 엽니다. `right.jsp` 및 바꾸기:

   ```java
   <div>iparsys</div>
   ```

   with:

   ```java
   <cq:include path="rightpar" resourceType="foundation/components/iparsys" />
   ```

1. 변경 사항을 저장합니다.
1. 브라우저에서 을(를) 다시 로드합니다. **[!UICONTROL 제품]** 페이지. 전체 페이지는 다음과 같습니다.

   ![chlimage_1-9](assets/chlimage_1-9.jpeg)
