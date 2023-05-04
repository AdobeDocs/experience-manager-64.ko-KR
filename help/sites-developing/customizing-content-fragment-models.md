---
title: 컨텐츠 조각 모델을 게시하지 않지만 DELETE 사용자 지정 컨텐츠 조각 모델을 게시하지 않습니다
seo-title: Customizing Content Fragment Models
description: 컨텐츠 조각 모델은 사용자 지정하고 확장할 수 있습니다.
seo-description: Content Fragment Models can be customized and extended.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: AEM Docs
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 1%

---


# 컨텐츠 조각 모델을 게시하지 않지만 DELETE 사용자 지정 컨텐츠 조각 모델을 게시하지 않습니다{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

컨텐츠 조각 모델 편집기는 컨텐츠를 기반으로 하는 마법사입니다 `Formbuilder`에서 상속됨:

`granite/ui/components/foundation/form/formbuilder`

이 구성 요소에는 각 모델의 데이터 유형과 속성을 포함하여 모델 편집기의 끌어서 놓기 인터페이스를 렌더링하는 데 필요한 도구가 있습니다.

## 위치 {#locations}

모델은 저장되고 아래에 생성됩니다 `/conf`: [컨텐츠 조각 모델 속성](/help/assets/content-fragments-models.md#enable-content-fragment-models) 활성화되었습니다. 이 설정은 **구성 속성**, 다음에서 액세스 가능 **[구성 브라우저](/help/sites-administering/configurations.md)**.

1. 를 통해 브라우저로 이동합니다 **도구**, **일반**, **구성 브라우저**
예, 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 브라우저에서 적절한 구성을 선택한 다음 **속성** 를 클릭합니다.

   예를 들어 `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

모델 콘솔에서 **컨텐츠 조각 모델** 속성이 나타납니다. 을 통해 탐색 **도구**, **자산**, **컨텐츠 조각 모델**; 예 `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

사용자는 다음을 수행할 수 있습니다 [컨텐츠 조각 모델 만들기](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) 사용 **모델 만들기** 마법사(사용 **만들기** 콘솔).

>[!CAUTION]
>
>사용자 ***반드시*** 에서 아무것도 변경하지 않음 `/libs` 경로.
>
>왜냐하면 `/libs` 는 다음에 인스턴스를 업그레이드할 때 덮어쓰여지며, 핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있습니다.

## 모델의 구조 {#structure-of-a-model}

마법사가 이 구조를 사용하여 항목을 만듭니다.

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   모든 모델은 이 폴더의 하위 폴더 아래에 저장됩니다.

* `jcr:content`

   모든 모델에는 `jcr:content` 노드:

   * 와 같은 모델에 대한 정보 속성을 포함합니다. `jcr:title`, `lastModified`, `lastModifiedBy`
   * 일반적으로 `sling:ResourceType` 의 `dam/cfm/models/console/components/data/entity/default`,

      사용 `sling:ResourceSuperType` 의 `dam/cfm/models/console/components/data/entity`

* `model`

   다음 `model` 노드에 속성이 포함되어 있습니다. `dataTypesConfig`모델 편집기에 사용되는 데이터 유형을 결정하는 데 사용됩니다.

* `items`

   아래에 `items` 노드 아래에 있는 경우 모델에 추가된 모든 데이터 유형이 저장됩니다(모델 편집기에서 드래그하여 놓으면 표시됨). 각 항목에는 임의 노드 이름이 지정되지만 컨텐츠 조각 편집기가 이 모델로 작동하려면 각 항목에 `name` 속성을 사용합니다. 또한 이 노드에서 구성 요소를 렌더링하는 데 필요한 기본 속성을 포함하여 특정 데이터 유형에 대한 모든 구성 속성이 저장됩니다.

>[!CAUTION]
>
>모델 편집기에 드래그 앤 드롭되는 모든 데이터 유형, 인스턴스화될 경우 **반드시** 있음 `name` 사용자가 입력하는 속성입니다.
>
>이것은 **속성 이름(&amp;A)** 에서 **속성** 모델 편집기의 탭입니다.

## 모델 편집기의 구조 {#structure-of-the-model-editor}

다음 **컨텐츠 조각 모델 편집기** 에는 두 가지 부분이 있습니다.

* 항목을 놓을 수 있는 왼쪽의 미리 보기 또는 보기 패널입니다. 이를 통해 다음이 가능합니다.

   * 의 미리 보기를 표시합니다 **데이터 유형** 이 인스턴스화됩니다.
   * 모델 편집기 내에서 순서 지정을 허용합니다.

* 다음 **데이터 유형**/**속성** 탭의 오른쪽 패널에 표시됩니다. 이를 통해 다음이 가능합니다.

   * 드래그하여 인스턴스화할 수 있는 데이터 유형 목록을 표시합니다.
   * 기본 모델 편집기의 경우 목록이 다음 위치에 있습니다.

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 렌더링된 모든 데이터 유형에는 인스턴스화될 때 뷰(왼쪽에 렌더링된 구성 요소)와 **속성** 탭으로서, 사용자가 특정 구성 요소에 대해 정의할 수 있는 속성을 정의합니다.

>[!CAUTION]
>
>사용자 ***반드시*** 에서 아무것도 변경하지 않음 `/libs` 경로.
>
>왜냐하면 `/libs` 는 다음에 인스턴스를 업그레이드할 때 덮어쓰여지며, 핫픽스 또는 기능 팩을 적용할 때 덮어쓸 수 있습니다.

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

데이터 유형이 인스턴스화될 때 컨텐츠 조각에서 구성 요소를 렌더링해야 하는 모든 속성에 대해 HTML 입력이 생성됩니다. 예를 들어 다음과 같습니다.

* **속성 이름(&amp;A)** ( `name`) - 구성 요소의 식별자로 작동합니다

* **다음으로 렌더링** ( `metaType`) - 렌더링할 구성 요소를 입력합니다.

* **설명** ( `fieldDescription`) - 컨텐츠 조각에 있는 구성 요소에 대한 설명입니다

* 기타

