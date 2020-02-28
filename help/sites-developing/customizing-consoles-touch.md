---
title: 콘솔 사용자 정의
seo-title: 콘솔 사용자 정의
description: AEM 파섹
seo-description: AEM 파섹
uuid: f10cea87-ef8a-468e-94ca-89a1017dcf44
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 221ed05b-855d-4dc2-9df6-12fdeabb157a
translation-type: tm+mt
source-git-commit: 1dc15f323dc30d5730e2af6c0e762d623523870d

---


# 콘솔 사용자 정의{#customizing-the-consoles}

>[!CAUTION]
>
>이 문서에서는 터치가 활성화된 최신 UI에서 콘솔을 사용자 지정하는 방법에 대해 설명하고 클래식 UI에는 적용되지 않습니다.

AEM에서는 작성 인스턴스의 콘솔(및 [페이지 작성 기능](/help/sites-developing/customizing-page-authoring-touch.md))을 사용자 지정할 수 있도록 하는 다양한 메커니즘을 제공합니다.

* Clientlibs

   Clientlibs를 사용하면 표준 함수, 개체 및 메서드를 재사용하는 동안 기본 구현을 확장하여 새로운 기능을 구현할 수 있습니다. 사용자 정의할 때 사용자 지정 구성 요소에 필요한 코드를 저장할 수 `/apps.` 있는 예를 들어 사용자 지정 clientlib 아래에 사용자 지정 clientlib을 만들 수 있습니다.

* 오버레이

   Overlays는 노드 정의를 기반으로 하며, 표준 기능(in `/libs`)을 사용자 정의된 기능(in)과 오버레이할 수 `/apps`있습니다. 오버레이를 만들 때는 소스 병합에서 상속을 허용하므로 원본의 1:1 사본이 필요하지 않습니다.

AEM 콘솔을 확장하는 방법은 여러 가지가 있습니다. 작은 선택 항목은 아래에서 수준 높게 다룹니다.

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* clientlibs 사용 및 [만들기](/help/sites-developing/clientlibs.md).
>* 오버레이 [사용 및 만들기](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)
>
>
이 항목에서는 AEM Gems 세션 - [AEM](https://docs.adobe.com/content/ddc/en/gems.html) 6.0 [에 대한 사용자 인터페이스 맞춤화에도 설명되어 있습니다](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html).

>[!CAUTION]
>
>패스에 있는 ***어떤 것도 변경하지*** 않아야 `/libs` 합니다.
>
>이는 다음에 인스턴스를 업그레이드할 때 의 컨텐츠를 `/libs` 덮어쓰게 되기 때문입니다(핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있음).
>
>구성 및 기타 변경에 대한 권장 방법은 다음과 같습니다.
>
>1. 필요한 항목(즉, 있는 대로)을 `/libs``/apps`
   >
   >
1. Make any changes within `/apps`
>



예를 들어 구조 내의 다음 위치를 `/libs` 오버레이할 수 있습니다.

* 콘솔(화강암 UI 페이지를 기반으로 하는 모든 콘솔);예를 들면 다음과 같습니다.

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
>추가 팁 및 도구는 기술 자료 문서, [AEM TouchUI 문제](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)해결을 참조하십시오.

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

## 콘솔에 대한 기본 보기 사용자 정의 {#customizing-the-default-view-for-a-console}

콘솔의 기본 보기(열, 카드, 목록)를 사용자 정의할 수 있습니다.

1. 아래 아래의 필수 항목을 오버레이하여 보기 순서를 변경할 수 있습니다.

   `/libs/wcm/core/content/sites/jcr:content/views`

   첫 번째 항목이 기본값이 됩니다.

   사용할 수 있는 노드는 사용 가능한 보기 옵션과 상호 연관됩니다.

   * `column`
   * `card`
   * `list`

1. 예를 들어 목록에 대한 오버레이에서 다음을 수행합니다.

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

1. 사용자 정의 작업을 위해 고유한 구성 요소를 만들고 해당 클라이언트 라이브러리를 포함할 수 있습니다. 예를 들어 Twitter로 **홍보** 작업:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   그러면 콘솔에서 도구 모음 항목에 연결할 수 있습니다.

   `/apps/<yourProject>/admin/ext/launches`

   예를 들어 선택 모드에서 다음을 수행합니다.

   `content/jcr:content/body/content/header/items/selection/items/twitter`

## 특정 그룹에 도구 모음 작업 제한 {#restrict-a-toolbar-action-to-a-specific-group}

1. 사용자 정의 렌더링 조건을 사용하여 표준 동작을 오버레이하고 렌더링하기 전에 충족해야 하는 특정 조건을 적용할 수 있습니다.

   예를 들어 그룹에 따라 렌더링 조건을 제어하는 구성 요소를 만듭니다.

   `/apps/myapp/components/renderconditions/group`

1. 사이트 콘솔에서 사이트 만들기 작업에 적용하려면 다음을 수행하십시오.

   `/libs/wcm/core/content/sites`

   오버레이를 만듭니다.

   `/apps/wcm/core/content/sites`

1. 그런 다음 작업에 대한 렌더링 조건을 추가합니다.

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   이 노드의 속성을 사용하여 특정 작업을 수행할 `groups` 수 있는 권한을 정의할 수 있습니다.예를 들면 `administrators`

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

## 목록 보기에서 열 사용자 정의 {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>이 기능은 텍스트 필드 열에 최적화되어 있습니다.다른 데이터 유형의 경우 오버레이할 `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` 수 `/apps`있습니다.

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
   자세한 [내용은 오버레이 사용(및 Sling 리소스 합병)](/help/sites-developing/overlays.md) 을 참조하십시오.

1. 원할 경우:

   * 추가 데이터를 연결하려면 ` [PageInforProvider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html)`

      `pageInfoProviderType` 속성.
   예를 들어 아래 GitHub에서 첨부된 클래스/번들을 참조하십시오.

1. 이제 목록 보기의 열 구성기에서 열을 선택할 수 있습니다.

## 리소스 필터링 {#filtering-resources}

콘솔을 사용할 때 일반적인 사용 사례는 사용자가 리소스(예: 페이지, 구성 요소, 자산 등)에서 선택해야 하는 때입니다. 예를 들어 작성자가 항목을 선택해야 하는 목록 형식을 사용할 수 있습니다.

적절한 크기로 유지하거나 사용 사례와 관련되도록 필터를 사용자 지정 술어의 형태로 구현할 수 있습니다. 자세한 내용은 [이 문서를](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) 참조하십시오.
