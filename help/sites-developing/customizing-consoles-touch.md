---
title: 콘솔 사용자 지정
seo-title: Customizing the Consoles
description: AEM에서는 작성 인스턴스의 콘솔을 사용자 지정할 수 있는 다양한 메커니즘을 제공합니다
seo-description: AEM provides various mechanisms to enable you to customize the consoles of your authoring instance
uuid: f10cea87-ef8a-468e-94ca-89a1017dcf44
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 221ed05b-855d-4dc2-9df6-12fdeabb157a
exl-id: 31bced35-4845-40d1-9bfd-5c75d54e1a83
source-git-commit: 51358642a2fa8f59f3f5e3996b0c37269632c4cb
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 2%

---

# 콘솔 사용자 지정{#customizing-the-consoles}

>[!CAUTION]
>
>이 문서에서는 터치가 활성화된 최신 UI에서 콘솔을 사용자 지정하는 방법에 대해 설명하고 클래식 UI에는 적용되지 않습니다.

AEM에서는 콘솔(및 [페이지 작성 기능](/help/sites-developing/customizing-page-authoring-touch.md)) 내의 아무 곳에나 삽입할 수 있습니다.

* Clientlibs

   Clientlibs를 사용하면 표준 함수, 개체 및 메서드를 재사용하는 동안 기본 구현을 확장하여 새로운 기능을 구현할 수 있습니다. 사용자 지정할 때 아래에 고유한 clientlib을 만들 수 있습니다. `/apps.` 예를 들어 사용자 지정 구성 요소에 필요한 코드를 보유할 수 있습니다.

* 오버레이

   오버레이는 노드 정의를 기반으로 하며 표준 기능(에서)을 오버레이할 수 있도록 해줍니다. `/libs`) 내의 고유한 사용자 지정 기능( `/apps`). 오버레이를 만들 때 sling 리소스 병합에서 상속을 허용하므로 원본의 1:1 복사본이 필요하지 않습니다.

AEM 콘솔을 확장하는 데 여러 가지 방법으로 사용할 수 있습니다. 작은 선택 항목이 아래에 (높은 수준에서) 표시됩니다.

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* 사용 및 만들기 [clientlibs](/help/sites-developing/clientlibs.md).
>* 사용 및 만들기 [오버레이](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)
>
>이 주제는에서 다룹니다 [AEM Gems 세션 - AEM 6.0의 사용자 인터페이스 사용자 지정](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-user-interface-customization-for-aem6.html).

>[!CAUTION]
>
>사용자 ***반드시*** 에서 아무것도 변경하지 않음 `/libs` 경로.
>
>왜냐하면 `/libs` 는 다음에 인스턴스를 업그레이드할 때 덮어쓰여지며, 핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있습니다.
>
>구성 및 기타 변경에 대해 권장되는 방법은 다음과 같습니다.
>
>1. 필요한 항목(즉, 가 존재함에 따라)을 다시 만듭니다 `/libs`) 아래의 `/apps`
>
>1. 내에서 변경 `/apps`

>


예를 들어 `/libs` 구조를 오버레이할 수 있습니다.

* 콘솔(Granite UI 페이지를 기반으로 하는 모든 콘솔); 예:

   * `/libs/wcm/core/content`

<!-- Needs a review by Engineering -->
<!--
* secondary (inner) rails; for example:

    * `/libs/wcm/core/content/search`

* toolbar(s) (dependent on console; for example sites):

    * default 

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/default`

    * selection mode

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/selection`

* help menu options (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/help`

* information shown on the card view (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/content/content/items/childpages`

-->
>[!NOTE]
>
>기술 자료 문서를 참조하십시오. [AEM TouchUI 문제 해결](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html): 추가 팁과 도구를 참조하십시오.

<!-- Needs a review by Engineering -->
<!--
## Code Samples {#code-samples}

Various packages have been made available on Github. These provide code samples related to the tasks covered on this page.

### aem-admin-extension-new-console {#aem-admin-extension-new-console}

`aem-admin-extension-new-console` is a sample package showing how to [create a new AEM 6 console](#create-a-custom-console). This package provides a UI for managing [Launches](/help/sites-authoring/launches.md) and adds a link in the navigation:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)

### aem-admin-extension-customize-sites {#aem-admin-extension-customize-sites}

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Create a Custom Console {#create-a-custom-console}

1. You can create a custom console with related actions; for example, Launches at the top level (below Sites):

   This involves:

    * creating the root space definition of your new console ``; for example:

        * `/apps/<yourProject>/admin/ext/launches`

    * this can contain (according to requirements):

        * the corresponding [clientlibs](/help/sites-developing/clientlibs.md) for custom actions and `less`/ `css` definitions

            * `/apps/<yourProject>/admin/ext/launches/clientlibs`

        * components that need to be redefined/adjusted; for example, the breadcrumbs, datasource and the launch

            * `/apps/<yourProject>/admin/ext/launches/components`

        * the Granite UI page resource:

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content`

              property: `sling:resourceType`

        * the page definition of the console

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/head`
            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body`

   ![chlimage_1-236](assets/chlimage_1-236.png)

   To use the new console (for example in the [rail for navigation](#add-new-navigation-option-to-rail)) an ID is used, so that it can be explicitly referenced. The ID is used to connect the console and its navigation definition. The ID is defined in the `rail` node of the page; for example, for the Sites console:

    * the rail node is: 

      `/libs/wcm/core/content/sites/jcr:content/body/rail`

        * here the `currentId` property is defined: 

          `currentId` = `cq-sites`

   For the Launches console example:

    * the node is:

        * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`

    * with the following properties:

        * `currentId` = `cq-launches`
        * `sling:resourceType` = `granite/ui/components/endor/navcolumns`
        * `srcPath` = `cq/core/content/nav`
-->

## 콘솔에 대한 기본 보기 사용자 지정 {#customizing-the-default-view-for-a-console}

콘솔에 대한 기본 보기(열, 카드, 목록)를 사용자 지정할 수 있습니다.

1. 아래의 필수 항목을 오버레이하여 보기 순서를 변경할 수 있습니다.

   `/libs/wcm/core/content/sites/jcr:content/views`

   첫 번째 항목이 기본값입니다.

   사용 가능한 노드는 사용 가능한 보기 옵션과 상호 연결됩니다.

   * `column`
   * `card`
   * `list`

1. 예를 들어, 목록에 대한 오버레이에서 다음을 수행합니다.

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   다음 속성을 정의합니다.

   * **이름**: `sling:orderBefore`
   * **유형**: `String`
   * **값**: `column`

<!-- Needs a review by Engineering -->
<!--
`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
### Add New Navigation Option to Rail {#add-new-navigation-option-to-rail}

1. You can add a navigation entry in the rail (for example, a [custom console](#create-a-custom-console) such as Launches).

   To do this, you create an overlay of:

   `/libs/cq/core/content/nav`

   In the `/apps` overlay:

   `/apps/cq/core/content/nav`

   Create the new nodes and properties:

   ![chlimage_1-237](assets/chlimage_1-237.png)

    * Extend navigation:

        * `/apps/cq/core/content/nav/launches`

    * Specify location in the tree:

        * property: `sling:orderBefore`

    * To create the connection, the `id` property references (i.e. must be the same as) the `currentID` property [for the appropriate console](#create-a-custom-console):

        * property: `id`
        * value: same as for your console (e.g. `cq-launches`) 

          for example: the same value as the `currentId` property on:

          `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`
-->

## 도구 모음에 새 작업 추가 {#add-new-action-to-the-toolbar}

1. 자체 구성 요소를 작성하고 사용자 지정 작업을 위해 해당 클라이언트 라이브러리를 포함할 수 있습니다. 예: **twitter으로 승격** 작업 위치:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   그런 다음 콘솔의 도구 모음 항목에 연결할 수 있습니다.

   `/apps/<yourProject>/admin/ext/launches`

   예를 들어 선택 모드에서 다음을 수행합니다.

   `content/jcr:content/body/content/header/items/selection/items/twitter`

## 도구 모음 작업을 특정 그룹으로 제한 {#restrict-a-toolbar-action-to-a-specific-group}

1. 사용자 지정 렌더링 조건을 사용하여 표준 작업을 오버레이하고 렌더링하기 전에 충족해야 하는 특정 조건을 적용할 수 있습니다.

   예를 들어 그룹에 따라 렌더링 조건을 제어하는 구성 요소를 만듭니다.

   `/apps/myapp/components/renderconditions/group`

1. 사이트 콘솔의 사이트 만들기 작업에 적용하려면 다음을 수행하십시오.

   `/libs/wcm/core/content/sites`

   오버레이를 만듭니다.

   `/apps/wcm/core/content/sites`

1. 그런 다음 작업에 대한 렌더링 조건을 추가합니다.

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   이 노드에서 속성을 사용하여 `groups` 특정 작업을 수행할 수 있습니다. 예 `administrators`

<!-- Needs a review by Engineering -->
<!--
## Remove Access to Navigation Option on Rail {#remove-access-to-navigation-option-on-rail}

1. You can rename a navigation entry in the rail by overlaying the required entry from under:

   `/libs/cq/core/content/nav`

   The nodes available correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`

1. For example, on a overlay at:

   `/apps/cq/core/content/nav/sites`

   Define the following property:

    * **Name**: `sling:hideResource`
    * **Type**: `String` 
    * **Value**: `true`

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Restrict Access to Navigation Option on Rail {#restrict-access-to-navigation-option-on-rail}

You can restrict access to a navigation option using ACLs:

1. Open the [user and/or group management](/help/sites-administering/security.md) and select the user/group you want to restrict access for.

   >[!NOTE]
   >
   >Avoid assigning/restricting permissions on a user-by-user basis. It is [recommended to use groups](/help/sites-administering/security.md#best-practices).

1. Remove access [permissions](/help/sites-administering/security.md#permissions) to the appropriate node(s) under `/libs/cq/core/content/nav/sites`. These correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`
-->

## 목록 보기에서 열 사용자 지정 {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>이 기능은 텍스트 필드 열에 최적화되었습니다. 다른 데이터 유형의 경우 오버레이할 수 있습니다 `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps`.

<!-- Needs a review by Engineering -->
<!--
CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-sites-extension-listview-columns project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns/archive/master.zip)
-->

목록 보기에서 열을 사용자 정의하려면

1. 사용 가능한 열 목록을 오버레이합니다.

   * 노드에서 다음을 수행합니다.

      `/apps/wcm/core/content/common/availablecolumns`

   * 새 열을 추가하거나 기존 열을 제거합니다.
   자세한 내용은 [오버레이 사용(및 Sling Resource Merger)](/help/sites-developing/overlays.md) 추가 정보.

1. 원할 경우:

   * 추가 데이터를 플러그하려면 ` [PageInforProvider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html)` 사용

      `pageInfoProviderType` 속성.
   예를 들어 아래의 (GitHub에서) 첨부된 클래스/번들을 참조하십시오.

1. 이제 목록 뷰의 열 구성자에서 열을 선택할 수 있습니다.

## 리소스 필터링 {#filtering-resources}

콘솔을 사용할 때 일반적인 사용 사례는 리소스(예: 페이지, 구성 요소, 자산 등)에서 사용자가 선택해야 하는 때입니다. 예를 들어 작성자가 항목을 선택해야 하는 목록 형태를 취할 수 있습니다.

목록을 적절한 크기로 유지하거나 사용 사례와 관련이 있도록 사용자 지정 설명 형태로 필터를 구현할 수 있습니다. 자세한 내용은 [이 문서](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) 자세한 내용
