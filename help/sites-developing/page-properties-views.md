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
exl-id: 25dad368-8227-424d-960b-1664d8e20a21
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 4%

---

# 페이지 속성 보기 사용자 지정{#customizing-views-of-page-properties}

모든 페이지에는 사용자가 보고 편집할 수 있는 [속성](/help/sites-authoring/editing-page-properties.md) 세트가 있습니다.일부는 페이지를 만들 때(보기 만들기) 필요하며, 일부는 나중에 보고 편집(보기 편집)할 수 있습니다. 이러한 페이지 속성은 해당 페이지 구성 요소의 대화 상자( `cq:dialog`)에서 정의하고 사용할 수 있게 됩니다.

>[!CAUTION]
>
>클래식 UI에서는 페이지 속성 보기를 사용자 지정할 수 없습니다.

모든 페이지 속성의 기본 상태는 다음과 같습니다.

* 만들기 보기에서 숨겨집니다(예:**페이지 만들기** 마법사)

* 편집 보기(예:**속성 보기**)

변경이 필요한 경우 필드를 특별히 구성해야 합니다. 이 작업은 적절한 노드 속성을 사용하여 수행됩니다.

* 만들기 보기(예:**페이지 만들기** 마법사):

   * 이름: `cq:showOnCreate`
   * 유형: `Boolean`

* 편집 보기에서 사용할 수 있는 페이지 속성(예:**보기**/**편집**) **속성** 옵션):

   * 이름: `cq:hideOnEdit`
   * 유형: `Boolean`

예를 들어, 기초 페이지 구성 요소의 **기본** 탭에서 **더 많은 제목 및 설명** 아래에 그룹화된 필드에 대한 설정을 참조하십시오. `cq:showOnCreate`이 `true`로 설정되어 있으므로 이 아이콘들은 **페이지 만들기** 마법사에 표시됩니다.

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>페이지 속성 사용자 지정에 대한 안내서는 [페이지 속성 확장 자습서](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) 를 참조하십시오.

## 페이지 속성 구성 {#configuring-your-page-properties}

페이지 구성 요소의 대화 상자를 구성하고 적절한 노드 속성을 적용하여 사용할 수 있는 필드를 구성할 수도 있습니다.

예를 들어 기본적으로 [**페이지 만들기** 마법사](/help/sites-authoring/managing-pages.md#creating-a-new-page)에는 **더 많은 제목 및 설명** 아래에 그룹화된 필드가 표시됩니다. 숨기려면 다음을 구성합니다.

1. `/apps` 아래에 페이지 구성 요소를 만듭니다.
1. 페이지 구성 요소의 `basic` 섹션에 대해 [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md)에서 제공하는 *대화 상자 차이*&#x200B;를 사용하여 무시를 만듭니다.예:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >참조용으로 다음 문서를 참조하십시오.
   >
   >
   ```
   >/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog
   >```
   >
   >그러나 ***은 `/libs` 경로에서 아무 것도 변경하지 않아야 합니다.***
   >
   >이는 다음 번에 인스턴스를 업그레이드할 때 `/libs` 컨텐츠를 덮어쓰게 되기 때문입니다(핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있음).
   >
   >구성 및 기타 변경에 대해 권장되는 방법은 다음과 같습니다.
   >
   >1. `/apps` 아래에 필요한 항목(즉, `/libs`에 있는 항목)을 다시 만듭니다.
   >1. `/apps` 내에서 변경


1. `basic`에서 `path` 속성을 설정하여 기본 탭의 재지정을 가리킵니다(다음 단계도 참조). 예:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. 해당 경로에서 `basic` - `moretitles` 섹션의 재정의를 만듭니다.예:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. 적절한 노드 속성을 적용합니다.

   * **이름**: `cq:showOnCreate`
   * **유형**: `Boolean`
   * **값**:  `false`

   **더 많은 제목 및 설명** 섹션이 **페이지 만들기** 마법사에 더 이상 표시되지 않습니다.

>[!NOTE]
>
>라이브 카피에 사용할 페이지 속성을 구성할 때 자세한 내용은 [페이지 속성에 MSM 잠금 구성](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) 을 참조하십시오.

## 페이지 속성 {#sample-configuration-of-page-properties} 의 샘플 구성

이 샘플은 [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md);의 대화 상자 차이 기술을 보여 줍니다.[`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties) 사용 포함. 또한 `cq:showOnCreate` 및 `cq:hideOnEdit` 의 사용도 보여줍니다.

GITHUB의 코드

GitHub에서 이 페이지의 코드를 찾을 수 있습니다

* [GitHub에서 aem-authoring-extension-page-dialog 프로젝트 열기](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
