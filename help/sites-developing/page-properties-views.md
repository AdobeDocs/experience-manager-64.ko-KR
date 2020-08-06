---
title: 페이지 속성 보기 사용자 지정
seo-title: 페이지 속성 보기 사용자 지정
description: 모든 페이지에는 필요에 따라 편집할 수 있는 속성 세트가 있습니다
seo-description: 모든 페이지에는 필요에 따라 편집할 수 있는 속성 세트가 있습니다
uuid: cbfca6e6-cb9e-43b1-8889-09a7cc9f8a51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6f8e08d1-831e-441a-ad1a-f5c8788f32d7
translation-type: tm+mt
source-git-commit: b4fa2d443f43cdfbf5caca4da7dcb935d099b795
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 4%

---


# 페이지 속성 보기 사용자 지정{#customizing-views-of-page-properties}

모든 페이지에는 사용자가 보고 편집할 수 있는 [속성](/help/sites-authoring/editing-page-properties.md) 세트가 있습니다. 일부는 페이지를 만들 때(보기 만들기) 필요하고, 다른 일부는 나중에 단계에서 보고 편집(보기 편집)할 수 있습니다. 이러한 페이지 속성은 해당 페이지 구성 요소의 대화 상자( `cq:dialog`)에 의해 정의되고 사용 가능합니다.

>[!CAUTION]
>
>클래식 UI에서는 페이지 속성 보기 사용자 지정을 사용할 수 없습니다.

모든 페이지 속성의 기본 상태는 다음과 같습니다.

* 숨김(예: 페이지 **만들기** 마법사)

* 편집 보기에서 사용 가능(예: 속성 **보기**)

변경이 필요한 경우 필드를 구체적으로 구성해야 합니다. 이 작업은 적절한 노드 속성을 사용하여 수행됩니다.

* 페이지 속성을 만들기 보기에서 사용할 수 있습니다(예: 페이지 **만들기** 마법사).

   * 이름: `cq:showOnCreate`
   * 유형: `Boolean`

* 편집 보기에서 사용할 수 있는 페이지 속성(예: **보기**/**편집****** ):

   * 이름: `cq:hideOnEdit`
   * 유형: `Boolean`

예를 들어, 기본 페이지 구성 요소의 **기본** 탭에서 추가 제목 및 설명 아래에 그룹화된 필드 설정을 **** 참조하십시오. 다음과 같이 페이지 **만들기** 마법사에서 `cq:showOnCreate` 볼 수 있습니다 `true`.

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>페이지 [속성 사용자 지정에 대한 안내서는 페이지 속성 확장 자습서를](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) 참조하십시오.

## 페이지 속성 구성 {#configuring-your-page-properties}

페이지 구성 요소의 대화 상자를 구성하고 적절한 노드 속성을 적용하여 사용 가능한 필드를 구성할 수도 있습니다.

예를 들어 기본적으로 페이지 [**만들기&#x200B;**마법사는](/help/sites-authoring/managing-pages.md#creating-a-new-page)추가 제목 및 설명**&#x200B;아래에 그룹화된 필드를&#x200B;**표시합니다. 이러한 항목을 숨기려면 다음을 구성합니다.

1. 아래에 페이지 구성 요소를 만듭니다 `/apps`.
1. 페이지 구성 요소의 섹션에 대한 대체(Sling Resource Commodification *에서* 제공하는 [대화 상자 비교](/help/sites-developing/sling-resource-merger.md)사용) `basic` 를 만듭니다. 예를 들면 다음과 같습니다.

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >참조:
   >
   >
   ```
   >/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog
   >```
   >
   >하지만 경로에서 아무 것도 ***변경해야*** 합니다 `/libs` .
   >
   >이는 다음에 인스턴스를 업그레이드할 때 `/libs` 의 컨텐츠를 덮어쓰고, 핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있기 때문입니다.
   >
   >구성 및 기타 변경에 대해 권장되는 방법은 다음과 같습니다.
   >
   >1. 필요한 항목(예: 존재함)을 `/libs``/apps`
   >1. Make any changes within `/apps`


1. 기본 탭 `path` `basic` 의 재정의를 가리키도록 속성을 설정합니다(다음 단계도 참조). 예:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. 해당 경로에서 `basic` - 섹션 `moretitles` 재정의를 만듭니다. 예를 들면 다음과 같습니다.

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. 적절한 노드 속성을 적용합니다.

   * **이름**: `cq:showOnCreate`
   * **유형**: `Boolean`
   * **값**: `false`

   더 **많은 제목 및 설명** 섹션이 더 이상 페이지 **만들기 마법사에 표시되지** 않습니다.

>[!NOTE]
>
>Live Copy에 사용할 페이지 속성을 구성할 때 [자세한 내용은 페이지 속성에서](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) MSM 잠금 구성을 참조하십시오.

## 페이지 속성의 샘플 구성 {#sample-configuration-of-page-properties}

이 샘플에서는 Sling Resource Combination의 대화 [비교 기술을 보여 줍니다](/help/sites-developing/sling-resource-merger.md). 를 [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties)포함합니다. 또한 `cq:showOnCreate` 및 `cq:hideOnEdit`의 사용을 보여줍니다.

GITHUB에 대한 코드

GitHub에서 이 페이지의 코드를 찾을 수 있습니다

* [GitHub에서 aem-authoring-extension-page-dialog 프로젝트 열기](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
