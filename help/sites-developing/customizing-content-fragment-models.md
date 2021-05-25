---
title: 컨텐츠 조각 모델을 게시하지 않지만 DELETE 사용자 지정 컨텐츠 조각 모델을 게시하지 않습니다
seo-title: 컨텐츠 조각 모델 사용자 지정
description: 컨텐츠 조각 모델은 사용자 지정하고 확장할 수 있습니다.
seo-description: 컨텐츠 조각 모델은 사용자 지정하고 확장할 수 있습니다.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# DELETE을 게시하지 말고 컨텐츠 조각 모델 사용자 지정({#do-not-publish-but-do-not-delete-customizing-content-fragment-models})은 게시하지 마십시오

컨텐츠 조각 모델 편집기는 다음에서 상속된 `Formbuilder` 기반의 마법사입니다.

`granite/ui/components/foundation/form/formbuilder`

이 구성 요소에는 각 모델의 데이터 유형과 속성을 포함하여 모델 편집기의 끌어서 놓기 인터페이스를 렌더링하는 데 필요한 도구가 있습니다.

## 위치 {#locations}

모델은 `/conf` 아래에 저장되고 [컨텐츠 조각 모델 속성](/help/assets/content-fragments-models.md#enable-content-fragment-models)이 활성화된 폴더 아래에 만들어집니다. 이 설정은 **[구성 브라우저](/help/sites-administering/configurations.md)**&#x200B;에서 액세스할 수 있는 **구성 속성**&#x200B;에서도 볼 수 있습니다.

1. **도구**, **일반**, **구성 브라우저**를 통해 브라우저로 이동합니다.
예, 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 브라우저에서 적절한 구성을 선택하고 도구 모음에서 **속성** 을 선택합니다.

   예를 들어 `global`에 대한 속성은 다음과 같습니다.`http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

모델 콘솔에서 **컨텐츠 조각 모델** 속성이 있는 모든 폴더가 표시됩니다. **도구**, **자산**, **컨텐츠 조각 모델**;을 통해 탐색합니다.예: `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`

사용자는 [모델 만들기&#x200B;**마법사(**&#x200B;콘솔에서 만들기&#x200B;**사용)를 사용하여 컨텐츠 조각 모델](/help/assets/content-fragments-models.md#creating-a-content-fragment-model)을 만들 수 있습니다.**

>[!CAUTION]
>
>***은 `/libs` 경로에서 아무 것도 변경하지 않아야 합니다.***
>
>이는 다음 번에 인스턴스를 업그레이드할 때 `/libs` 컨텐츠를 덮어쓰게 되기 때문입니다(핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있음).

## 모델 {#structure-of-a-model} 구조

마법사가 이 구조를 사용하여 항목을 만듭니다.

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   모든 모델은 이 폴더의 하위 폴더 아래에 저장됩니다.

* `jcr:content`

   모든 모델에는 다음과 같은 `jcr:content` 노드가 포함됩니다.

   * `jcr:title`, `lastModified`, `lastModifiedBy` 등의 모델에 대한 정보 속성을 포함합니다.
   * 일반적으로 `dam/cfm/models/console/components/data/entity/default` 중 `sling:ResourceType`이 있습니다.

      `dam/cfm/models/console/components/data/entity` 중 `sling:ResourceSuperType` 사용

* `model`

   `model` 노드에는 모델 편집기에 사용되는 데이터 유형을 결정하는 데 사용되는 속성 `dataTypesConfig`이 포함되어 있습니다.

* `items`

   `items` 노드 아래에 모델에 추가된 모든 데이터 유형이 저장됩니다(모델 편집기에서 드래그 앤 드롭된 대로). 각 항목에는 임의 노드 이름이 지정되지만 컨텐츠 조각 편집기가 이 모델에서 작동하려면 각 항목에 `name` 속성이 있어야 합니다. 또한 이 노드에서 구성 요소를 렌더링하는 데 필요한 기본 속성을 포함하여 특정 데이터 유형에 대한 모든 구성 속성이 저장됩니다.

>[!CAUTION]
>
>모델 편집기에 드래그 앤 드롭되는 모든 데이터 유형이며, 이와 같이 인스턴스화될 경우 **반드시** 사용자가 `name` 속성을 입력해야 합니다.
>
>모델 편집기의 **속성** 탭에서 **속성 이름 &amp;ast;**&#x200B;로 표시됩니다.

## 모델 편집기 {#structure-of-the-model-editor} 구조

**컨텐츠 조각 모델 편집기**&#x200B;에는 두 가지 부분이 있습니다.

* 항목을 놓을 수 있는 왼쪽의 미리 보기 또는 보기 패널입니다. 이 기능은

   * 인스턴스화된 **데이터 유형**&#x200B;의 미리 보기를 표시합니다.
   * 모델 편집기 내에서 순서 지정을 허용합니다.

* 오른쪽 패널의 **데이터 유형**/**속성** 탭. 이 기능은

   * 드래그하여 인스턴스화할 수 있는 데이터 유형 목록을 표시합니다.
   * 기본 모델 편집기의 경우 목록이 다음 위치에 있습니다.

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 렌더링된 모든 데이터 유형에는 인스턴스화될 때 뷰(왼쪽에서 렌더링된 구성 요소)와 사용자가 특정 구성 요소에 대해 정의할 수 있는 속성을 정의하는 **속성** 탭이 있는 두 개의 스크립트 태그가 있습니다.

>[!CAUTION]
>
>***은 `/libs` 경로에서 아무 것도 변경하지 않아야 합니다.***
>
>이는 다음 번에 인스턴스를 업그레이드할 때 `/libs` 컨텐츠를 덮어쓰게 되기 때문입니다(핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있음).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

데이터 유형이 인스턴스화될 때, 구성 요소를 컨텐츠 조각에서 렌더링해야 하는 모든 속성에 대해 HTML 입력이 생성됩니다. 예를 들어 다음과 같습니다.

* **속성 이름 &amp;ast;** (  `name`) - 구성 요소에 대한 식별자 역할을 합니다

* **렌더링** (  `metaType`) - 렌더링할 구성 요소를 다음과 같이 입력합니다

* **설명** (  `fieldDescription`) - 컨텐츠 조각에 있는 구성 요소에 대한 설명입니다

* 기타

