---
title: 게시하지 말고 컨텐츠 조각 모델을 사용자 정의하는 DELETE을 사용하지 마십시오.
seo-title: 컨텐츠 조각 모델 사용자 정의
description: 컨텐츠 조각 모델을 사용자 정의하고 확장할 수 있습니다.
seo-description: 컨텐츠 조각 모델을 사용자 정의하고 확장할 수 있습니다.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 게시하지 말고 컨텐츠 조각 모델 사용자 지정 DELETE을 사용하지 마십시오{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

컨텐츠 조각 모델 편집기는 다음에서 상속된 `Formbuilder`을 기반으로 하는 마법스입니다.

`granite/ui/components/foundation/form/formbuilder`

이 구성 요소에는 각 모델의 데이터 유형과 속성이 포함된 모델 편집기의 드래그 앤 드롭 인터페이스를 렌더링하는 데 필요한 도구가 있습니다.

## 위치 {#locations}

모델은 `/conf`컨텐트 조각 모델 속성](/help/assets/content-fragments-models.md#enable-content-fragment-models)이(가) 활성화된 폴더 아래에 저장되고 만들어집니다. [ 이 설정은 **[구성 브라우저](/help/sites-administering/configurations.md)**&#x200B;에서 액세스할 수 있는 **구성 속성**&#x200B;에서도 볼 수 있습니다.

1. **도구**, **일반**, **구성 브라우저**를 통해 브라우저로 이동합니다.
예를 들어 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 브라우저에서 적절한 구성을 선택하고 도구 모음에서 **속성**&#x200B;을 선택합니다.

   예를 들어 `global`의 속성은 다음과 같습니다.`http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

모델 콘솔에서 **컨텐츠 조각 모델** 속성이 있는 모든 폴더가 표시됩니다. **도구**, **자산**, **컨텐츠 조각 모델**;을 통해 탐색예: `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`

사용자는 **모델 만들기** 마법사를 사용하여 [컨텐트 조각 모델](/help/assets/content-fragments-models.md#creating-a-content-fragment-model)을 만들 수 있습니다(콘솔에서 **만들기** 사용).

>[!CAUTION]
>
>***은(는) `/libs` 경로에서 아무 것도 변경하지 않아야 합니다.***
>
>이는 다음 번에 인스턴스를 업그레이드할 때 `/libs`의 콘텐트가 덮어쓰여지고 핫픽스 또는 기능 팩을 적용할 때 덮어쓰여질 수 있기 때문입니다.

## 모델 {#structure-of-a-model} 구조

이 구조를 갖는 항목이 만들어집니다.

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   모든 모델은 이 폴더의 하위 폴더 아래에 저장됩니다.

* `jcr:content`

   모든 모델에는 다음과 같은 `jcr:content` 노드가 포함됩니다.

   * `jcr:title`, `lastModified`, `lastModifiedBy` 등의 모델에 대한 정보 속성을 포함합니다.
   * 일반적으로 `dam/cfm/models/console/components/data/entity/default`의 `sling:ResourceType`이(가) 있습니다.

      `dam/cfm/models/console/components/data/entity`의 `sling:ResourceSuperType`과 함께

* `model`

   `model` 노드에는 모델 편집기에 사용되는 데이터 유형을 결정하는 데 사용되는 속성 `dataTypesConfig`이 있습니다.

* `items`

   `items` 노드 아래에 모델에 추가된 모든 데이터 유형이 저장됩니다(모델 편집기에서 드래그하여 놓임). 각 항목에는 임의 노드 이름이 지정되어 있지만 컨텐츠 조각 편집기가 이 모델에서 작업하려면 각 항목에는 `name` 속성이 있어야 합니다. 또한 이 노드에서 구성 요소를 렌더링하는 데 필요한 기본 속성을 비롯하여 특정 데이터 유형에 대한 모든 구성 속성이 저장됩니다.

>[!CAUTION]
>
>모델 편집기에서 드래그 앤 드롭한 모든 데이터 유형으로서 인스턴스화된 **은(는) 사용자가 `name` 속성을 입력해야 합니다.**
>
>모델 편집기의 **속성** 탭에 있는 **속성 이름 &amp;ast;**&#x200B;로 표시됩니다.

## 모델 편집기 {#structure-of-the-model-editor} 구조

**컨텐츠 조각 모델 편집기**&#x200B;에는 두 개의 부분이 있습니다.

* 항목을 놓을 수 있는 왼쪽에 있는 미리 보기 또는 보기 패널입니다. 이 기능은

   * 인스턴스화된 **데이터 유형**&#x200B;의 미리 보기를 표시합니다.
   * 모델 편집기 내에서 순서를 지정할 수 있습니다.

* 오른쪽의 패널에 있는 **데이터 유형**/**속성** 탭. 이 기능은

   * 드래그하여 인스턴스화할 수 있는 데이터 유형 목록을 표시합니다.
   * 기본 모델 편집기의 경우 목록이 다음 위치에 있습니다.

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 렌더링된 모든 데이터 유형에는 인스턴스화될 때 뷰(왼쪽에서 렌더링된 구성 요소)와 사용자가 지정된 구성 요소에 대해 정의할 수 있는 속성을 정의하는 **속성** 탭이 포함되는 2개의 스크립트 태그가 있습니다.

>[!CAUTION]
>
>***은(는) `/libs` 경로에서 아무 것도 변경하지 않아야 합니다.***
>
>이는 다음 번에 인스턴스를 업그레이드할 때 `/libs`의 콘텐트가 덮어쓰여지고 핫픽스 또는 기능 팩을 적용할 때 덮어쓰여질 수 있기 때문입니다.

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

데이터 유형이 인스턴스화될 때 구성 요소를 컨텐츠 조각에서 렌더링해야 하는 모든 속성에 대해 HTML 입력이 생성됩니다. 예를 들어 다음과 같습니다.

* **속성 이름 마지막;** (  `name`) - 구성 요소의 식별자 역할

* **렌더링 형식** (  `metaType`) - 렌더링할 구성 요소를

* **설명** (  `fieldDescription`) - 컨텐츠 조각에 있는 구성 요소에 대한 설명

* 다른 사용자와 공유하십시오.

