---
title: 컨텐츠 조각 모델에 대해 데이터 유형 사용자 지정을 DELETE으로 지정하지 마십시오.
seo-title: 컨텐츠 조각 모델에 대한 데이터 유형 사용자 정의
description: 컨텐츠 조각 모델에 사용되는 데이터 유형을 사용자 정의할 수 있습니다.
seo-description: 컨텐츠 조각 모델에 사용되는 데이터 유형을 사용자 정의할 수 있습니다.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# 컨텐츠 조각 모델에 대해 데이터 유형 사용자 지정을 DELETE으로 지정하지 마십시오.{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[컨텐츠 조각](/help/assets/content-fragments.md) 은 [컨텐츠 조각 모델을 기반으로 합니다](/help/assets/content-fragments-models.md). 이러한 모델은 서로 다른 데이터 유형의 [요소](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) 로 구성됩니다.

단일 행 텍스트, 여러 줄 서식 있는 텍스트, 숫자 필드, 부울 선택기, 드롭다운 메뉴 옵션, 날짜 및 시간 등 다양한 데이터 유형을 바로 사용할 수 있습니다. AEM 사용자는 해당 조각의 편집 의도를 기반으로 데이터 유형을 선택할 수 있습니다. 이를 통해 다양한 유형의 컨텐츠가 포함된 복잡한 모델과 관련 조각 작성 경험을 통해 간단한 텍스트 모델을 처리할 수 있습니다.

데이터 유형은 저장소의 [특정 위치에 있는 노드 속성의](#properties) 조합으로 정의됩니다 [](#locations-in-the-repository). 고유한 [데이터 유형](#creating-your-data-type) 및 field [속성을 만들 수도 있습니다](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## 저장소의 위치 {#locations-in-the-repository}

기본적으로 제공되는 모든 데이터 유형은

`/libs/settings`

다음과 같이 노드 구조를 오버레이하여 새 데이터 유형을 추가할 수 있습니다 `/apps`.

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>경로에서 어떤 것도 변경해서는 안 `/libs` 된다.
>
>다음 업그레이드 또는 서비스 또는 수정 팩을 설치할 때 변경할 수 있는 모든 사항이 있습니다.

## 속성 {#properties}

노드 속성은 데이터 유형을 정의하는 데 사용됩니다.

* [데이터 유형 속성](#data-type-properties)
* 및 해당 [field속성 내](#fieldproperties)

### 데이터 유형 속성 {#data-type-properties}

모든 데이터 유형은 다음과 같이 노드 구조로 표시됩니다.

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

아래의 각 노드에는 `/items` 모델 편집기 내에서 해당 데이터 유형을 표현하는 방법을 정의하는 속성이 있습니다.

데이터 유형이 모델 편집기에 표시되도록 하려면 다음 속성이 모두 있어야 합니다.

* `fieldIcon`

   [모델 편집기 UI에서 데이터 유형을 나타내는 CoralUI 아이콘](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) .

* ` [fieldProperties](#fieldproperties)`

   각 데이터 유형에 대한 구성 속성을 나타내는 배열입니다.

* `fieldResourceType`

   컨텐츠 조각에서 데이터 유형을 렌더링하는 데 사용되는 Sling 리소스 유형입니다. 다양한 방식으로 렌더링할 수 있는 데이터 유형(예: 간단한 텍스트 입력 및/또는 여러 줄 텍스트 입력)의 경우 이 속성을 모든 리소스 유형이 포함된 배열로 만들어야 합니다. 이 `renderasfield` 속성은 사용자가 모델에 추가할 리소스 유형을 선택할 수 `fieldProperties` 있도록 자동으로 추가됩니다.

* `fieldPropResourceType`

   데이터 유형에 대한 기본 속성을 렌더링하는 데 사용되는 Sling 리소스 유형입니다.

   예를 들어 데이터 유형의 경우

   * 단일 행 텍스트, 구성 요소 `fieldPropResourceType` 가 `textfield` 됩니다.
   * 부울, 구성 요소 `fieldPropResourceType` 가 `checkbox` 됩니다.

* `fieldViewResourceType`

   모델을 구성할 때 미리 보기에서 데이터 유형을 렌더링하는 데 사용되는 Sling 리소스 유형입니다. 사용자가 데이터 유형을 모델 편집기의 왼쪽으로 드래그하면 속성은 해당 `fieldViewResourceType` 위치에서 렌더링되는 구성 요소를 나타냅니다. 전체 구성 요소를 렌더링하지 않고 모델 편집기로 오버헤드를 최소화하는 대체물을 렌더링하려는 경우에만 사용됩니다.

* `fieldTitle`

   이 데이터 형식의 제목을 정의하는 속성입니다. 예를 들어, **구성 요소에 대한 단일 행 텍스트** , 다중 필드 구성 요소에 `textfield` 대한 **여러 줄 텍스트** 를예로 들 수 있습니다.

* `valueType`

   데이터 유형이 내부적으로 저장될 때 반환하는 값 유형입니다. 매핑을 [참조하십시오](#mappings).

* `renderType`

   데이터 유형의 내부 표현입니다. UI 구성 요소 `valueType` 에 연결합니다. 매핑을 [참조하십시오](#mappings).

* `listOrder`

   각 데이터 유형에는 목록에서 해당 순서를 나타내는 값이 필요합니다. 모델 편집기를 저장할 때 다양한 필드(드래그 앤 드롭으로 추가/이동)의 올바른 순서를 유지하는 데 사용됩니다. 이 값은 정수여야 하며, 오름차순과 순서가 지정된 방법으로 숫자를 지정하는 것이 좋습니다. 새 데이터 유형을 만들 때는 목록의 마지막 데이터 유형(데이터 유형에 있는 가장 높은 값)을 기준으로 값을 할당하는 것이 가장 `listOrder` 좋습니다.

#### 매핑 {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>데이터 유형<br /> </td> 
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
   <td>long</td> 
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
   <td>time</td> 
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
>일부 유형(예: `string`다른 유형 `long`중)은 다중값일 수 있습니다. 이 경우 렌더링 및 편집에 사용되는 구성 요소는 일반적으로 다중 필드 구성 요소( `granite/ui/components/coral/foundation/form/multifield`)로 래핑됩니다. 단, 편집 구성 요소가 올바르게 렌더링할 책임이 있는 태그는 예외입니다.

### fieldProperties {#fieldproperties}

각 데이터 유형에 대한 구성 속성입니다. 값 `fieldProperties`:

* `base`

   모든 구성 요소의 기본입니다 `fieldProperties` . 정의는 아래에 `/libs/dam/cfm/models/editor/components/datatypeproperties/base`있다.

   이 변수에는 변수 `fieldRoot`가 포함되어 있으며, 이 변수에는 올바른 경로를 검색할 수 있도록 입력을 만들 `fieldProperties` 때 사용할 수 있습니다.

   예: 필드 레이블에 대한 올바른 경로를 **얻으려면** 이 필드가 속한 구성 요소를 식별하는 키가 필요합니다. 이 필드에 대한 입력은 `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   이 구성 요소는 `Boolean` 데이터 유형에 대한 기본 확인란뿐만 아니라 Sling 매개 변수 `checked@Delete` 및 `checked@TypeHint`를 추가합니다.

* `datepickerfields`

   날짜 선택기 구성 요소가 작동하는 데 필요한 숨겨진 입력을 추가하는 구성 요소입니다. 속성, 속성 `defaultDateField`, `displayedFormat``emptyText`, `valueFormat`및 `minDate` 속성 만들기 `maxDate`를 포함합니다.

* `datetimepickerfields`

   이렇게 하면 `Date&Time` 데이터 유형에 대한 선택 필드가 추가되어 `Date` 와 `Date&Time` 옵션을 구분하게 됩니다.

* `datevaluefield`

   이렇게 하면 사용자가 데이터 유형에 대한 기본값을 선택할 수 있도록 속성에 날짜 `Date&Time` 떨림이 추가됩니다.

* `descriptionfield`

   이 구성 요소는 여러 줄 편집기에서 현재 선택된 구성 요소의 설명을 나타내는 여러 줄 텍스트 필드를 추가합니다. 각 데이터 유형 속성의 끝에 모델 편집기 렌더러가 자동으로 추가됩니다.

* `labelfield`

   필드 레이블을 가질 수 있는 데이터 유형에 대한 필드 레이블을 추가하는 `textfield` 입력을 추가하는 구성 요소입니다.

* `maptopropertyfield`

   이 구성 요소는 속성의 `Name` 필드를 추가하여 데이터 유형의 선택된 구성 요소에 식별자를 제공합니다. 모든 데이터 유형에 있어야 합니다.

* `maxlengthfield`

   이 속성은 이 속성을 허용하는 데이터 유형에 사용할 `maxLength` 속성을 추가하는 데 사용됩니다. 예를 들어 **단일 행 텍스트**, **번호**&#x200B;등이 있습니다.

* `multieditorfield`

   그러면 여러 줄 편집기가 작동하기 위해 필요한 모든 숨김 필드가 추가되어 **여러 줄 텍스트** 데이터 유형으로 표시됩니다.

* `mvfields`

   다중 필드 구성 요소가 작동하는 데 필요한 모든 숨김 필드를 추가하는 구성 요소입니다. 예를 들어, 단일 행 텍스트 **데이터 유형의 두 번째 옵션에** 대해 설명합니다. 다중 필드로 렌더링되는 모든 구성 요소에 대해 추가해야 합니다.

* `numbertypefield`

   데이터 유형에 대해 정수 **또는** 분수 **를** 선택할 수 있는 숫자 **데이터****유형** 에 대한 옵션을선택합니다.

* `numbervaluefield`

   숫자 `numberfield` 에 대한 **기본값 선택기** 는 선택 상자 구성 요소의 값을 결정하는 데 사용되는 열거형 `type.options`**데이터 유형에 대한 옵션** 입력을 추가합니다.

* `placeholderfield`

   구성 요소의 속성에 대한 입력으로 사용되는 `emptyText` 텍스트 필드입니다. 자리 표시자를 받아들이는 모든 데이터 유형에서 사용해야 합니다(매우 복잡하지는 않음). 예: **단일 행 텍스트**, **번호**&#x200B;등).

* `renderasfield`

   데이터 유형 노드의 속성에 여러 개 `fieldResourceTypes` 가 있을 때 자동으로 렌더링되는 구성 요소입니다.

* `requiredfield`

   구성 요소의 속성을 나타내는 `required` 확인란입니다. 대부분의 구성 요소는 필드를 `required` 허용하므로 대부분의 데이터 유형에 이 필드를 사용할 수 있습니다.

* `tagsfields`

   구성 요소를 렌더링하는 데 필요한 입력 사항을 추가하는 구성 요소 `tagfield` 는 태그 **** 데이터 유형에 사용됩니다.

* `tagsroot`

   구성 요소의 루트 경로를 설정하기 위해 **태그** 데이터 유형이 사용하는 `tagsfield` 경로 선택기.

* `textfield`

   이 데이터 유형에 의해 정의된 확인란 필드 레이블을 설정하는 데 `Boolean` 데이터 유형에 의해 사용됩니다.

* `textvaluefield`

   단일 행 텍스트 **데이터 유형에 대한** 기본값 속성입니다.

## 데이터 유형 만들기 {#creating-your-data-type}

고유한 데이터 유형을 만들려면 다음을 수행해야 합니다.

* [노드 구조 만들기](#creating-the-node-structure)
* [데이터 유형에 대한 속성 정의](#defining-the-properties-for-your-data-type)

그런 다음 데이터 유형을 [사용할 수 있습니다](#using-your-data-type).

또한 [직접 만들 수도 있습니다 `fieldProperties`](#creating-your-own-fieldproperties-property).

### 노드 구조 만들기 {#creating-the-node-structure}

데이터 유형을 오버레이하려면 노드 구조 `/apps` 를 아래에 만들어야 합니다. 아직 없는 경우 다음을 만들어야 합니다.

1. 아직 없는 경우 다음을 만들어야 합니다.

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
   >`/apps/settings/dam` 가 이미 존재해야 합니다.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` 은 지정된 nodetype으로 만들어야 합니다.

1. 아래에서 새 노드를 추가하여 새 데이터 유형을 나타낼 수 있습니다. `/items`

   * 노드 유형: `nt:unstructured`
   * &quot;속성: 데이터 [유형에 대한 속성 정의를 참조하십시오.](#defining-the-properties-for-your-data-type)

### 데이터 유형에 대한 속성 정의 {#defining-the-properties-for-your-data-type}

1. 데이터 유형에 필요한 다음 [데이터 유형 속성의](#data-type-properties) 값을 결정합니다.

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   데이터 유형에 대한 구성 요소가 렌더링되는 방식을 정의합니다. 모든 구성 요소가 될 수 있습니다. 사용자 지정 구성 요소(일치하는 세트 필요 ` [fieldProperties](#fieldproperties)`) 포함

   데이터 유형에 대한 노드에서 적절한 값을 사용하여 이러한 속성을 정의합니다.

1. 사용할 항목 ` [fieldProperties](#fieldproperties)` 을 결정합니다. 이것은 사용자가 필요로 하는 속성이나 속성에 따라 `fieldResourceType` 다릅니다.

   예를 들어 레이블 이름 `granite/ui/components/coral/foundation/form/textfield`, **최대 길이**, 자리 표시자 텍스트 **및 FacebookDefault Value 속성이 있어야****** **** 합니다.

   기본 필드 속성 [에서 선택하거나 고유한 속성을](#fieldproperties)만들 수 있습니다 [](#creating-your-own-fieldproperties-property).

   데이터 유형에 대한 노드에서 적절한 값을 사용하여 이러한 속성을 정의합니다.

1. 다음 [데이터 유형 속성의 값을 결정합니다](#data-type-properties).

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   데이터 유형에 대한 노드에서 적절한 값을 사용하여 이러한 속성을 정의합니다.

### 데이터 유형 사용 {#using-your-data-type}

모든 속성이 적용된 이 노드 구조를 저장한 후 모델 편집기로 모델을 열고 새 데이터 유형을 보고 사용할 수 있습니다.

## 고유한 필드 만들기속성 {#creating-your-own-fieldproperties-property}

기본적으로 제공되는 [필드](#fieldproperties)속성 중에서 선택하거나 직접 속성을 만들 수 있습니다.

1. 다음 위치에서 구성 요소를 만듭니다.

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   경로가 존재하지 않으면 노드를 사용하여 경로를 만들 수 `nt:folder` 있습니다.

   1. 변수에 액세스하려면 이 구성 요소가 확장되어야 합니다.

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. 구성 요소는 다음을 통해 포함할 수 있어야 합니다.

      `sling:include`

   1. 이 구성 요소는 필드를 렌더링하거나(사용자가 데이터를 도입해야 하는 경우) 데이터 유형에 필요한 속성을 사용하여 숨겨진 입력을 렌더링해야 합니다. 예를 들어, 다중 필드 구성 요소에는 복제할 필드 유형을 가진 하위 노드가 있어야 하므로 특정 유형의 하위 노드를 만들(슬링 POST 메커니즘을 통해) 수 있는 입력이 있어야 합니다.

1. 이 구성 요소의 기본 이름을 에 추가해야 합니다 `fieldProperties`.
1. 필요한 모든 속성에 대해 이 단계를 반복합니다.

