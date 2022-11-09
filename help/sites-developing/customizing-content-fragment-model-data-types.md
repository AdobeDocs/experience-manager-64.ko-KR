---
title: 게시하지 않지만 컨텐츠 조각 모델에 대한 데이터 유형 사용자 지정을 DELETE 하지 않습니다
seo-title: Customizing Data Types for Content Fragment Models
description: 컨텐츠 조각 모델에 사용된 데이터 유형을 사용자 지정할 수 있습니다.
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: AEM Docs
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 1%

---


# 게시하지 않지만 컨텐츠 조각 모델에 대한 데이터 유형 사용자 지정을 DELETE 하지 않습니다{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[컨텐츠 조각](/help/assets/content-fragments.md) 다음 기준 [컨텐츠 조각 모델](/help/assets/content-fragments-models.md). 이러한 모델은 [요소](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) 다양한 데이터 유형.

한 줄 텍스트, 여러 줄 서식 있는 텍스트, 숫자 필드, 부울 선택기, 드롭다운 메뉴 옵션, 날짜 및 시간 등을 비롯한 다양한 데이터 유형을 바로 사용할 수 있습니다. AEM 사용자는 해당 조각의 편집 의도를 기반으로 데이터 유형을 선택할 수 있습니다. 이렇게 하면 다양한 유형의 컨텐츠가 있는 복잡한 모델과 관련 조각 작성 경험을 통해 단순 텍스트 모델을 제공할 수 있습니다.

데이터 유형은 [노드 속성의 조합](#properties) 보류 [저장소의 특정 위치](#locations-in-the-repository). 직접 만들 수도 있습니다 [데이터 유형](#creating-your-data-type) 및 [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## 저장소의 위치 {#locations-in-the-repository}

모든 기본 데이터 유형은 다음과 같이 선언됩니다.

`/libs/settings`

다음과 같이 노드 구조를 오버레이하여 새 데이터 유형을 추가할 수 있습니다 `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>에서는 아무 것도 변경하지 마십시오 `/libs` 경로.
>
>다음 업그레이드 또는 서비스 또는 수정 팩 설치 시 변경될 수 있는 모든 내용이 있습니다.

## 속성 {#properties}

노드 속성은 데이터 유형을 정의하는 데 사용됩니다.

* [데이터 유형 속성](#data-type-properties)
* 그리고 그 안에서 [fieldProperties](#fieldproperties)

### 데이터 유형 속성 {#data-type-properties}

모든 데이터 유형은 다음과 같이 노드 구조로 표시됩니다.

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

아래의 각 노드 `/items` 에는 모델 편집기 내에 데이터 유형을 표시하는 방법을 정의하는 속성이 있습니다.

데이터 유형이 모델 편집기에 표시되도록 하려면 다음 속성이 모두 있어야 합니다.

* `fieldIcon`

   [CoralUI 아이콘](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) 모델 편집기 UI에서 데이터 유형을 나타냅니다.

* ` [fieldProperties](#fieldproperties)`

   각 데이터 유형의 구성 속성을 나타내는 배열입니다.

* `fieldResourceType`

   컨텐츠 조각에서 데이터 유형을 렌더링하는 데 사용되는 Sling 리소스 유형입니다. 다양한 방법으로 렌더링할 수 있는 데이터 유형(예: 간단한 텍스트 입력 및/또는 여러 줄 텍스트 입력)의 경우 이 속성을 모든 리소스 유형을 포함하는 배열로 만들어야 합니다. 다음 `renderasfield` 속성이 자동으로 `fieldProperties` 사용자가 모델에 추가해야 하는 리소스 유형을 선택할 수 있도록 하려면,

* `fieldPropResourceType`

   데이터 형식에 대한 기본 속성을 렌더링하는 데 사용되는 Sling 리소스 유형입니다.

   예를 들어, 데이터 유형의 경우:

   * 단일 행 텍스트, `fieldPropResourceType` 만약 `textfield` 구성 요소
   * 부울, `fieldPropResourceType` 만약 `checkbox` 구성 요소

* `fieldViewResourceType`

   모델을 구성할 때 미리 보기에서 데이터 유형을 렌더링하는 데 사용되는 Sling 리소스 유형입니다. 사용자가 데이터 유형을 모델 편집기의 왼쪽으로 드래그하면 `fieldViewResourceType` 속성은 해당 위치에 렌더링되는 구성 요소를 나타냅니다. 전체 구성 요소를 렌더링하지 않고 모델 편집기에 오버헤드를 최소화하는 대체 요소만 렌더링하려는 경우에 사용됩니다.

* `fieldTitle`

   이 데이터 형식의 제목을 정의하는 속성입니다. 예, **한 줄 텍스트** 대상 `textfield` 구성 요소, **여러 줄 텍스트** 복수 필드 구성 요소에 사용할 수 있습니다.

* `valueType`

   데이터 형식이 내부적으로 저장될 때 반환하는 값의 유형입니다. 자세한 내용은 [매핑](#mappings).

* `renderType`

   이는 데이터 유형의 내부 표현입니다. 를 연결합니다 `valueType` UI 구성 요소에 매핑해야 합니다. 자세한 내용은 [매핑](#mappings).

* `listOrder`

   각 데이터 유형에는 목록에서 해당 순서를 나타내는 값이 필요합니다. 모델 편집기를 저장할 때 다양한 필드(드래그 앤 드롭으로 추가/이동)의 올바른 순서를 지정하는 데 사용됩니다. 이 값은 정수여야 하며, 오름차순으로 숫자를 할당하는 것이 좋습니다. 새 데이터 유형을 만들 때는 목록에서 마지막 데이터 유형(가장 높은 값)을 기반으로 값을 할당하는 것이 가장 좋습니다 `listOrder` 값)을 포함합니다.

#### 매핑 {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>데이터 형식<br /> </td> 
   <td>값 유형<br /> </td> 
   <td>렌더링 유형</td> 
  </tr> 
  <tr> 
   <td>한 줄 텍스트</td> 
   <td>문자열</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>여러 줄 텍스트</td> 
   <td>문자열, 컨텐츠 유형<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>숫자(정수/긴)<br /> </td> 
   <td>장기간</td> 
   <td>개수</td> 
  </tr> 
  <tr> 
   <td>숫자(이중/부동)</td> 
   <td>이중</td> 
   <td>개수</td> 
  </tr> 
  <tr> 
   <td>부울</td> 
   <td>부울</td> 
   <td>부울</td> 
  </tr> 
  <tr> 
   <td>날짜 및 시간</td> 
   <td>달력</td> 
   <td>시간</td> 
  </tr> 
  <tr> 
   <td>열거</td> 
   <td>문자열/긴</td> 
   <td>열거형</td> 
  </tr> 
  <tr> 
   <td>태그</td> 
   <td>문자열</td> 
   <td>태그</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>일부 유형(예: `string`, `long`, 기타 중에서)는 여러 값을 가질 수 있습니다. 이 경우 렌더링 및 편집에 사용되는 구성 요소는 일반적으로 다중 필드 구성 요소( `granite/ui/components/coral/foundation/form/multifield`). 단, 태그는 편집 구성 요소가 올바로 렌더링하도록 담당합니다.

### fieldProperties {#fieldproperties}

각 데이터 유형에 대한 구성 속성입니다. 값 `fieldProperties`:

* `base`

   이것은 모든 사람의 기본이다 `fieldProperties` 구성 요소. 정의는 다음과 같습니다 `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   여기에는 변수가 포함되어 있습니다 `fieldRoot`: 다음에 `fieldProperties` 입력을 만들어 올바른 경로를 검색할 때 를 사용할 수 있습니다.

   예: 올바른 경로를 **필드 레이블** 이 구성 요소가 속한 구성 요소를 식별하는 키가 있어야 하며 이 필드에 대한 입력은 `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   이 구성 요소는 `Boolean` Sling 매개 변수와 데이터 유형 `checked@Delete` 및 `checked@TypeHint`.

* `datepickerfields`

   날짜 선택기 구성 요소가 작동하는 데 필요한 숨겨진 입력을 추가하는 구성 요소입니다. 속성 만들기를 포함합니다 `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` 및 `maxDate`.

* `datetimepickerfields`

   이에 대한 선택 필드가 추가됩니다 `Date&Time` 구분하기 위한 데이터 유형 `Date` 및 `Date&Time` 옵션.

* `datevaluefield`

   이렇게 하면 사용자가 속성에 대한 기본값을 선택할 수 있도록 데이터 깜박임이 추가됩니다 `Date&Time` 데이터 유형.

* `descriptionfield`

   이 구성 요소는 여러 줄 편집기에서 현재 선택한 구성 요소의 설명을 나타내는 여러 줄 텍스트 필드를 추가합니다. 이 렌더러는 각 데이터 유형 속성의 끝에 모델 편집기 렌더러에 의해 자동으로 추가됩니다.

* `labelfield`

   를 추가하는 구성 요소 `textfield` 필드 레이블이 있을 수 있는 데이터 유형에 대한 필드 레이블을 추가하는 입력.

* `maptopropertyfield`

   이 구성 요소는 `Name` 필드의 필드에 값을 지정하여 데이터 유형의 선택한 구성 요소에 식별자를 지정합니다. 모든 데이터 유형에 있어야 합니다.

* `maxlengthfield`

   를 추가하는 데 사용됩니다 `maxLength` 이 속성을 허용하는 데이터 형식과 함께 사용할 속성입니다. 예를 들어, **단일 행 텍스트**, **숫자**&#x200B;등

* `multieditorfield`

   이렇게 하면 여러 줄 편집기가 작동하는 데 필요한 모든 숨김 필드가 추가되며 이것은 **여러 줄 텍스트** 데이터 유형.

* `mvfields`

   다중 필드 구성 요소가 작동하는 데 필요한 모든 숨김 필드를 추가하는 구성 요소입니다. 예를 들어, **단일 행 텍스트** 데이터 유형. 다중 필드로 렌더링되는 모든 구성 요소에 대해 이 값을 추가해야 합니다.

* `numbertypefield`

   에 대한 옵션을 선택합니다 **숫자** 다음 사이 **정수** 또는 **분수** 대상 **숫자** 데이터 유형.

* `numbervaluefield`

   A `numberfield` 기본값 선택기 **숫자** `type.options` 그러면 에 대한 옵션 입력이 추가됩니다. **열거형** 선택 상자 구성 요소의 값을 결정하는 데 사용되는 데이터 유형입니다.

* `placeholderfield`

   이 필드는 `emptyText` 구성 요소의 속성입니다. 자리 표시자를 허용하는 모든 데이터 유형에서 사용해야 합니다(매우 복잡하지 않음). 예 **단일 행 텍스트**, **숫자**&#x200B;등)

* `renderasfield`

   이 구성 요소는 다음과 같은 경우에 자동으로 렌더링됩니다 `fieldResourceTypes` 는 데이터 유형 노드의 속성에 있습니다.

* `requiredfield`

   이 확인란은 `required` 구성 요소의 속성입니다. 대부분의 구성 요소가 `required` 필드에서 이 필드를 대부분의 데이터 유형에 사용할 수 있습니다.

* `tagsfields`

   에 필요한 입력을 추가하는 구성 요소 `tagfield` 렌더링할 구성 요소, **태그** 데이터 유형.

* `tagsroot`

   에서 사용하는 경로 선택기 **태그** 루트 경로를 설정할 데이터 유형 `tagsfield` 구성 요소.

* `textfield`

   에서 사용 `Boolean` 이 데이터 유형에 의해 정의된 확인란의 필드 레이블을 설정하는 데이터 유형입니다.

* `textvaluefield`

   에 대한 기본값 속성 **단일 행 텍스트** 데이터 유형.

## 데이터 유형 만들기 {#creating-your-data-type}

고유한 데이터 유형을 만들려면 다음을 수행해야 합니다.

* [노드 구조 만들기](#creating-the-node-structure)
* [데이터 유형에 대한 속성 정의](#defining-the-properties-for-your-data-type)

그러면 다음 작업을 수행할 수 있습니다 [데이터 유형 사용](#using-your-data-type).

다음을 수행할 수도 있습니다 [직접 만들기 `fieldProperties`](#creating-your-own-fieldproperties-property).

### 노드 구조 생성 {#creating-the-node-structure}

노드 구조는 아래에 만들어야 합니다. `/apps` 를 사용하여 데이터를 오버레이할 수 있습니다. 아직 존재하지 않는 경우 다음을 만들어야 합니다.

1. 아직 존재하지 않는 경우 다음을 만들어야 합니다.

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` 은 이미 있어야 합니다.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` 지정한 노드 유형을 사용하여 만들어야 할 수 있습니다.

1. 아래 `/items` 새 노드를 추가하여 새 데이터 유형을 나타낼 수 있습니다.

   * 노드 유형: `nt:unstructured`
   * &quot;속성: 참조 [데이터 유형에 대한 속성 정의](#defining-the-properties-for-your-data-type)

### 데이터 유형에 대한 속성 정의 {#defining-the-properties-for-your-data-type}

1. 다음 값을 결정합니다 [데이터 유형 속성](#data-type-properties) 데이터 유형에 필요합니다.

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   이러한 항목은 데이터 유형에 대한 구성 요소가 렌더링되는 방식을 정의합니다. 구성 요소일 수 있습니다. 고유한 사용자 지정 구성 요소 포함(일치하는 ` [fieldProperties](#fieldproperties)`).

   데이터 유형의 노드에서 적절한 값을 사용하여 이러한 속성을 정의합니다.

1. 을(를) 결정합니다 ` [fieldProperties](#fieldproperties)` 사용할 수 없습니다. 이는 사용자의 `fieldResourceType` 필요합니다.

   예: `granite/ui/components/coral/foundation/form/textfield`다음과 같이 해야 합니다. **레이블 이름**, **최대 길이**, **자리 표시자 텍스트** 그리고 **기본값** 속성을 사용합니다.

   기본 제공 중에서 선택할 수 있습니다 [fieldProperties](#fieldproperties), 또는 [고유한 속성 만들기](#creating-your-own-fieldproperties-property).

   데이터 유형의 노드에서 적절한 값을 사용하여 이러한 속성을 정의합니다.

1. 다음 값을 결정합니다 [데이터 유형 속성](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   데이터 유형의 노드에서 적절한 값을 사용하여 이러한 속성을 정의합니다.

### 데이터 유형 사용 {#using-your-data-type}

모든 속성이 적용된 이 노드 구조를 저장하면 모델 편집기로 모델을 열고 새 데이터 유형을 보고 사용할 수 있습니다.

## 고유한 필드 만들기Properties 속성 {#creating-your-own-fieldproperties-property}

기본 제공 중에서 선택할 수 있습니다 [fieldProperties](#fieldproperties)또는 직접 만듭니다.

1. 다음 위치에서 구성 요소를 만듭니다.

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   경로가 존재하지 않으면 을 사용하여 만들 수 있습니다 `nt:folder` 노드 아래에 나열됩니다.

   1. 변수에 액세스하려면 이 구성 요소가 확장되어야 합니다.

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. 구성 요소는 다음을 통해 포함할 수 있습니다.

      `sling:include`

   1. 이 구성 요소는 필드를 렌더링하거나(사용자가 데이터를 도입해야 하는 경우) 데이터 유형에 필요한 속성을 사용하여 숨겨진 입력을 렌더링해야 합니다. 예를 들어 다중 필드 구성 요소에는 중복해야 하는 필드 유형을 갖는 하위 노드가 필요하므로, Sling POST 메커니즘을 통해 특정 유형의 하위 노드를 생성할 수 있는 입력이 있어야 합니다.

1. 이 구성 요소의 기본 이름을 `fieldProperties`.
1. 필요한 모든 속성에 대해 이 작업을 반복합니다.

