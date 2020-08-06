---
title: 컨텐츠 조각 모델을 사용자 정의하도록 DELETE을 사용하지 않음
seo-title: 컨텐츠 조각 모델 사용자 정의
description: 컨텐츠 조각 모델을 사용자 정의하고 확장할 수 있습니다.
seo-description: 컨텐츠 조각 모델을 사용자 정의하고 확장할 수 있습니다.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 컨텐츠 조각 모델을 사용자 정의하도록 DELETE을 사용하지 않음{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

컨텐츠 조각 모델 편집기는 다음을 통해 상속되는 마법사 `Formbuilder`를 기반으로 합니다.

`granite/ui/components/foundation/form/formbuilder`

이 구성 요소에는 각 모델의 데이터 유형과 속성이 포함된 모델 편집기의 드래그 앤 드롭 인터페이스를 렌더링하는 데 필요한 도구가 있습니다.

## 위치 {#locations}

모델은 저장 및 생성되며 `/conf`컨텐트 조각 모델 속성이 활성화된 폴더 아래에 [있습니다](/help/assets/content-fragments-models.md#enable-content-fragment-models) . 이 설정은 구성 브라우저에서 액세스할 수 있는 **구성**&#x200B;속성에서도 **확인할 수 있습니다**.

1. 도구, **일반**, **구성 브라우저**&#x200B;를 통해 브라우저 **로**&#x200B;이동합니다. 예: 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 브라우저에서 적절한 구성을 선택하고 도구 모음에서 **속성** 을 선택합니다.

   예를 들어 다음과 같은 속성 `global`을 사용할 수 있습니다. `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

모델 콘솔에서 **컨텐츠 조각 모델** 속성이 있는 모든 폴더가 나타납니다. 도구, **자산**, **컨텐츠 조각**&#x200B;모델 **을 통해 이동**; 예를 들면 다음과 같습니다 `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

사용자는 [모델 생성](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) 마법사(콘솔에서 **만들기** 사용)를 사용하여 컨텐츠 조각 모델 **을** 만들수 있습니다.

>[!CAUTION]
>
>경로 ***에서 어떤 것도 변경하지*** 않아야 `/libs` 합니다.
>
>이는 다음에 인스턴스를 업그레이드할 때 `/libs` 의 콘텐트가 덮어쓰기되기 때문입니다(핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있습니다).

## 모델의 구조 {#structure-of-a-model}

이 구조를 갖는 항목이 만들어집니다.

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   모든 모델은 이 폴더의 하위 폴더 아래에 저장됩니다.

* `jcr:content`

   모든 모델에는 다음과 같은 `jcr:content` 노드가 포함됩니다.

   * 에,, `jcr:title``lastModified``lastModifiedBy`
   * 보통 `sling:ResourceType` 는 `dam/cfm/models/console/components/data/entity/default`

      의 `sling:ResourceSuperType` `dam/cfm/models/console/components/data/entity`

* `model`

   노드 `model` 에 속성 `dataTypesConfig`이 있으며, 모델 편집기에서 사용되는 데이터 유형을 결정하는 데 사용됩니다.

* `items`

   노드 아래에 `items` 모델에 추가된 모든 데이터 유형이 저장됩니다(모델 편집기에서 드래그하여 놓임). 각 항목에는 임의 노드 이름이 지정되지만 컨텐츠 조각 편집기가 이 모델에서 작업하려면 각 항목에는 속성이 있어야 `name` 합니다. 또한 이 노드에서 구성 요소를 렌더링하는 데 필요한 기본 속성을 비롯하여 특정 데이터 유형에 대한 모든 구성 속성이 저장됩니다.

>[!CAUTION]
>
>모델 편집기에서 드래그 앤 드롭한 모든 데이터 유형으로서 인스턴스화된 모든 데이터 유형에는 사용자의 **속성 입력이 있어야** 합니다 `name` .
>
>속성 **이름 &amp;ast;로 표시됩니다.** 를 **클릭합니다** .

## 모델 편집기의 구조 {#structure-of-the-model-editor}

컨텐츠 **조각 모델 편집기에는** 두 개의 부분이 있습니다.

* 항목을 놓을 수 있는 왼쪽에 있는 미리 보기 또는 보기 패널입니다. 이 기능은

   * 인스턴스화된 **데이터 유형** 미리 보기를 표시합니다.
   * 모델 편집기 내에서 주문 허가

* 오른쪽의 **패널에 있는****데이터 유형** /속성탭 이 기능은

   * 드래그하여 인스턴스화할 수 있는 데이터 유형 목록을 표시합니다.
   * 기본 모델 편집기의 경우 목록이 다음 위치에 있습니다.

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 렌더링된 모든 데이터 유형에는 인스턴스화될 때 뷰(왼쪽에서 렌더링된 구성 요소)와 지정된 구성 요소에 대해 사용자가 정의할 수 있는 속성을 정의하는 **속성** 탭을 형성하는 두 개의 스크립트 태그가 있습니다.

>[!CAUTION]
>
>경로 ***에서 어떤 것도 변경하지*** 않아야 `/libs` 합니다.
>
>이는 다음에 인스턴스를 업그레이드할 때 `/libs` 의 콘텐트가 덮어쓰기되기 때문입니다(핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있습니다).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

데이터 유형이 인스턴스화될 때 구성 요소를 컨텐츠 조각으로 렌더링해야 하는 모든 속성에 대해 HTML 입력이 생성됩니다. 예를 들어 다음과 같습니다.

* **속성 이름 &amp;ast;** ( `name`) - 구성 요소의 식별자 역할

* **렌더링 형식** ( `metaType`) - 렌더링할 구성 요소를

* **설명** ( `fieldDescription`) - 컨텐츠 조각에 있는 구성 요소에 대한 설명

* 및 기타.

