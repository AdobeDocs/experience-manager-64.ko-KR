---
title: 템플릿 및 구성 요소 만들기 및 추가
seo-title: Creating and Adding Templates and Components
description: 앱에 템플릿 및 구성 요소를 만들고 추가하는 방법에 대해 알려면 이 페이지를 따르십시오. 이 페이지에서는 샘플 앱 템플릿 및 페이지 템플릿을 포함하는 앱으로 Geometrixx Unlimited 앱을 사용합니다.
seo-description: Follow this page to learn about creating and adding templates and components to your app. The page uses Geometrixx Unlimited App as the app that contains a sample app template and page templates.
uuid: 3a93017c-8094-413f-a01c-9b72025a2b20
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: ec4ada04-e429-4ad4-a060-2dccac847cf0
exl-id: 84eb552c-ba47-46e1-86e3-9460bd77dfbe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 1%

---

# 템플릿 및 구성 요소 만들기 및 추가 {#creating-and-adding-templates-and-components}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>단일 페이지 애플리케이션 프레임워크 기반 클라이언트측 렌더링(예: React)이 필요한 프로젝트에 SPA 편집기를 사용하는 것이 좋습니다. [자세히 알아보기](/help/sites-developing/spa-overview.md).

AEM Mobile 온디맨드는 완전히 구성된 앱 템플릿, 문서 템플릿 및 문서 구성 요소를 제공합니다.

We.Unlimited App은 구성 가능하고 관리하기 쉬운 AEM Mobile On-Demand 애플리케이션의 셸을 나타내는 샘플 템플릿입니다.

새 앱을 만들 때 이 샘플 템플릿을 선택하면 AEM Mobile 기능이 풍부한 대시보드가 제공됩니다.

![chlimage_1-70](assets/chlimage_1-70.png)

>[!NOTE]
>
>AEM Mobile Apps Control Center에서 애플리케이션 및 모바일 앱 콘텐츠를 관리하려면 다음을 참조하십시오. [AEM Mobile 애플리케이션 대시보드](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

## 앱 템플릿 만들기 {#creating-app-templates}

앱 템플릿은 새 앱을 만드는 데 사용되며 앱의 기준선 또는 기반을 나타내는 페이지 템플릿 및 구성 요소의 컬렉션 역할을 합니다. 템플릿은 적절한 방식으로 앱을 안내하는 몇 가지 기본 속성을 스탬프합니다. 일반적으로 고객은 통틀어 너무 많은 앱을 만들지 않습니다.

앱 템플릿을 사용하면 AEM 내에서 새로운 앱을 만드는 데 사용되는 개발자가 만든 기존 디자인을 쉽게 활용할 수 있습니다.

다른 앱의 템플릿을 기반으로 새 앱을 만들 때 앱이 만들어진 시작점을 나타내는 앱이 표시됩니다.

앱 템플릿을 기반으로 새 앱을 만드는 단계:

1. AEM Mobile 앱 카탈로그로 이동합니다. *&lt;server-url>/aem/apps.html/content/mobileapps*
1. 선택 **만들기** —> **앱** 아래와 같이 표시됩니다.

이 템플릿을 사용하여 앱을 만들면 문서, 배너 및 컬렉션을 앱에 추가할 수 있습니다. 문서, 배너 및 컬렉션을 다시 방문하려면 [콘텐츠 관리 작업](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

>[!NOTE]
>
>또는 예제 앱 템플릿을 선택할 수도 있습니다 **We.Unlimited** AEM 개발자가 사용할 수 있는 앱. 앱에 대해 이 샘플 템플릿을 사용하는 경우 작업할 일부 샘플 문서와 컬렉션이 제공됩니다. 샘플 템플릿 및 구성 요소를 사용하거나, 기존 템플릿 및 구성 요소를 사용자 지정하거나, 앱에 대해 새 템플릿을 만드는 선택 사항이 제공됩니다.

>[!CAUTION]
>
>설정 ***redirectTarget*** 속성
>
>앱 템플릿 중 하나를 사용하는 동안 개발자는 애플리케이션의 콘텐츠를 정의합니다. 그러나 개발자는 jcr에서 애플리케이션이 만들어지는 위치와 값을 알고 있어야 합니다 ***redirectTarget*** 속성을 사용합니다.
>
>다음 ***redirectTarget*** 는 앱 만들기 작업의 일부로 계산되며, 앱 템플릿의 일부로 사용할 수 있는 redirectTarget 속성이 있고 redirectTarget의 값이 상대적인 것으로 정의된 경우 경로 확인을 시도합니다. 앱 만들기 프로세스에서 앱 템플릿에서 redirectTarget에 대한 상대 값을 찾으면 값이 앱이 만들어진 확인된 위치에 추가됩니다.
>
>예를 들어 앱 템플릿이 ***redirectTarget*** 값 &quot;*lanugage-masters/en*&quot;&quot;에서 앱이 생성되었습니다.*/content/mobileapps/fooApp*&quot;&quot;을(를) 만들 때 앱을 만든 후 redirectTarget에 대한 최종 값은 &quot;&quot;이 됩니다.*/content/mobileapps/fooApp/language-masters/en*&quot;.

## 콘텐츠 템플릿 만들기 {#creating-content-templates}

각 엔티티 유형에는 두 개의 기본 템플릿이 있습니다. 이 4가지 주요 원칙은 다음과 같습니다.

* **기본 템플릿:** 해당 기본 속성/구조가 있는 컨텐츠 작성에 사용됩니다.
* **가져온 템플릿:** 해당 기본 속성/구조가 있는 AEM Mobile에서 컨텐츠를 가져오는 데 사용됩니다.

### 문서 템플릿 {#article-templates}

무제한 문서는 일반적인 AEM Mobile 온디맨드 문서 레이아웃을 나타내는 샘플 템플릿입니다.

1. 클릭 **+** in **문서 관리** 새 문서를 만들려면 다음 중 하나를 선택할 수 있습니다 **제한 없는 문서** 또는 **리치 텍스트 문서**. 아래 이미지는 이러한 두 문서 템플릿 중에서 선택할 수 있는 옵션을 보여줍니다.

1. 클릭 **다음** 문서 이름/제목, 설명, 작성, 요약, 부서, 축소판 이미지, 문서 액세스 등과 같은 문서 메타 데이터를 정의하려면
1. 클릭 **다음** 광고 속성을 입력합니다.
1. 클릭 **다음** 문서 이미지 또는 소셜 미디어 이미지를 입력하려면
1. 클릭 **다음** 이 새로운 문서를 받을 컬렉션 링크를 선택하려면 다음을 수행하십시오.
1. 클릭 **다음** 소셜 공유 세부 사항을 입력합니다.
1. 클릭 **만들기** 를 클릭하여 문서를 만드는 프로세스를 완료합니다. 다음 중 하나를 클릭합니다 **완료** 또는 **문서 편집** 을 눌러 이 문서의 속성을 편집합니다.

![chlimage_1-71](assets/chlimage_1-71.png)

### 문서에 구성 요소 추가 {#adding-components-to-article}

만들어진 작성자는 텍스트 및 이미지와 같은 구성 요소를 추가하여 문서의 컨텐츠를 편집할 수 있습니다. 문서는 AEM 페이지 템플릿의 확장입니다.

편집할 문서를 선택하고 을(를) 클릭합니다 **편집** 을 클릭하여 문서에 구성 요소를 추가합니다.

![chlimage_1-72](assets/chlimage_1-72.png) ![chlimage_1-73](assets/chlimage_1-73.png)

&#39; 을(를) 선택합니다.**+**&#39;을(를) 사용하여 문서에 구성 요소를 추가합니다.

![chlimage_1-74](assets/chlimage_1-74.png)

### 기본 템플릿 만들기 {#creating-out-of-the-box-templates}

기본 제공 문서 템플릿은 없지만 사용자 지정 템플릿을 확장해야 하는 기본 템플릿이 있습니다. 앱 Geometrixx Unlimited 을 참조하십시오. [문서 템플릿 샘플](http://localhost:4502/crx/de/index.jsp#/apps/geometrixx-unlimited-app/templates/article).

일반 AEM 템플릿 이상의 주요 속성은 다음과 같습니다.

***dps-resourceType=&quot;dps:Article&quot;***

이 속성을 사용하면 AEM 페이지가 AEM Mobile 타깃팅된 문서 페이지로 인식됩니다.

AEM 템플릿에 따라 기본 속성 또는 하위 노드를 템플릿의 ***jcr:content***.

### 배너 및 컬렉션 템플릿 {#banner-and-collection-templates}

>[!CAUTION]
>
>배너 및 컬렉션에는 콘텐츠가 없으므로 만든 콘텐츠가 사용자 지정 템플릿을 지원하지 않습니다.

## 구성 요소 생성 및 추가 {#creating-and-adding-components}

구성 요소는 위젯을 사용하고 액세스할 수 있도록 하며, 이 구성 요소는 컨텐츠를 렌더링하는 데 사용됩니다.

단순 구성 요소는 코드 저장소에 포함되며 이 구성 요소의 소스가 AEM에서 찾을 수 있습니다. 그런 다음 CRXDE Lite에서 로컬로 열 수도 있습니다.

>[!NOTE]
>
>현재 AEM Mobile에 대해 기본적으로 제공되는 구성 요소가 없습니다.

페이지에 구성 요소를 추가할 수 있습니다. 모든 구성 요소는 AEM Mobile 앱에서 사용할 수 있지만 적용할 때 올바르게 렌더링되지 않을 수 있습니다.

그러나 AEM에서 렌더링되는 사용자 지정 내보내기 컨텐츠 동기화 핸들러가 없으면 사용자 지정 구성 요소를 AEM Mobile On-demand Services으로 올바로 내보내고 업로드할 수 없습니다.

구성 요소가 이미 AEM 페이지에 일부 다른 빌딩 블록 구성 요소와 함께 포함되면, 페이지에 다른 구성 요소를 추가하거나 기존 구성 요소를 편집할 수 있습니다.

**페이지에 다른 구성 요소를 추가하려면:**

1. 해당 페이지를 선택하고 편집기 헤더의 오른쪽 상단에 있는 드롭다운을 통해 편집 모드에 있는지 확인합니다
1. 편집기 헤더에서 맨 왼쪽 아이콘을 사용하여 사이드 패널을 전환합니다.
1. 을(를) 선택합니다 **구성 요소** 탭
1. 사용 가능한 구성 요소 중 하나를 페이지로 끌어다 놓습니다

![chlimage_1-75](assets/chlimage_1-75.png)

**기존 구성 요소를 편집하려면**

1. 해당 페이지를 선택하고 다음을 확인합니다. **편집** 모드 및 구성 요소 선택
1. 공구모양 아이콘을 눌러 구성 요소를 구성합니다

>[!NOTE]
>
>AEM에서 구성 요소를 만들고 을 사용하여 사용자 지정할 수 있습니다 [CRXDE Lite을 사용한 개발](/help/sites-developing/developing-with-crxde-lite.md). 기존 구성 요소를 요구 사항으로 사용자 지정하고 나면 **편집** 옵션 아래의 **문서 관리** 위의 그림에서 보듯이

>[!NOTE]
>
>을(를) 참조하십시오. [템플릿 및 구성 요소 개발에 대한 우수 사례](/help/mobile/best-practices-aem-mobile.md) AEM Mobile.

### 다음 단계 {#the-next-steps}

* [컨텐츠 속성을 사용하여 컨텐츠 내보내기](/help/mobile/on-demand-content-properties-exporting.md)
* [콘텐츠 동기화가 있는 모바일](/help/mobile/mobile-ondemand-contentsync.md)
