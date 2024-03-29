---
title: 보고서 개발
seo-title: Developing Reports
description: AEM에서는 보고 프레임워크를 기반으로 다양한 표준 보고서를 제공합니다
seo-description: AEM provides a selection of standard reports based on a reporting framework
uuid: 1b406d15-bd77-4531-84c0-377dbff5cab2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 50fafc64-d462-4386-93af-ce360588d294
exl-id: 837c79af-a50f-40bb-b60d-205e1cac3f39
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '5274'
ht-degree: 0%

---

# 보고서 개발{#developing-reports}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서는 [표준 보고서](/help/sites-administering/reporting.md) 대부분은 보고 프레임워크를 기반으로 합니다.

프레임워크를 사용하여 이러한 표준 보고서를 확장하거나 완전히 새로운 보고서를 개발할 수 있습니다. Reporting 프레임워크는 기존 CQ5 개념 및 원칙과 긴밀하게 통합되어 있으므로 개발자가 기존 CQ5에 대한 지식을 보고서 개발을 위한 발판으로 사용할 수 있습니다.

AEM과 함께 제공된 표준 보고서의 경우:

* 이러한 보고서는 보고 프레임워크를 기반으로 작성됩니다.

   * [구성 요소 보고서](/help/sites-administering/reporting.md#component-report)
   * [페이지 활동 보고서](/help/sites-administering/reporting.md#page-activity-report)
   * [사용자 보고서](/help/sites-administering/reporting.md#user-report)
   * [워크플로우 상속 보고서](/help/sites-administering/reporting.md#workflow-instance-report)

* 다음 보고서는 개별 원칙을 기반으로 하므로 확장할 수 없습니다.

   * [디스크 사용량](/help/sites-administering/reporting.md#disk-usage)
   * [상태 검사](/help/sites-administering/reporting.md#health-check)
   * [워크플로우 보고서](/help/sites-administering/reporting.md#workflow-report)

>[!NOTE]
>
>자습서 [고유한 보고서 만들기 - 예](#creating-your-own-report-an-example) 또한 아래 원칙 중 몇 개를 사용할 수 있는지를 보여줍니다.
>
>표준 보고서를 참조하여 구현의 다른 예를 볼 수도 있습니다.

>[!NOTE]
>
>아래 예와 정의에서는 다음 표기법이 사용됩니다.
>
>* 각 행은 다음과 같은 노드 또는 속성을 정의합니다.
>
>  * `N:<name> [<nodeType>]`

   > 
   >     이름이 인 노드를 설명합니다. `<*name*>` 및 노드 유형 `<*nodeType*>`*.*
>
>  * `P:<name> [<propertyType]`
   >
   >     이름이 `<*name*>` 및 속성 유형 `<*propertyType*>`.
>
>  * `P:<name> = <value>`
   >
   >     속성에 대해 설명합니다. `<name>` 값을 `<value>`.
>
>* 들여쓰기는 노드 간의 계층 구조를 보여 줍니다.
>* 항목 구분 | 가능한 항목의 목록을 나타냅니다. 예를 들어 유형 또는 이름이 있습니다.
>
>  예 `String|String[]` 는 속성이 String 또는 String일 수 있음을 의미합니다.[].
>
>* `[]` 어레이를 나타냅니다. 문자열 등[] 또는 의 [쿼리 정의](#query-definition).
>
>별도로 명시되어 있지 않는 한 기본 유형은 다음과 같습니다.
>
>* 노드 - `nt:unstructured`
>* 속성 - `String`


## Reporting Framework {#reporting-framework}

보고 프레임워크는 다음 원칙에 따라 작동합니다.

* CQ5 QueryBuilder에서 실행하는 쿼리에 의해 반환되는 결과 세트를 기반으로 합니다.
* 결과 세트는 보고서에 표시되는 데이터를 정의합니다. 결과 세트의 각 행은 보고서의 테이블 형식 보기에서 행에 해당합니다.
* 결과 세트에서 실행할 수 있는 작업은 RDBMS 개념과 유사합니다. 주로 *그룹화* 및 *집계*.

* 대부분의 데이터 검색 및 처리는 서버 측에서 수행됩니다.
* 클라이언트는 전적으로 사전 처리된 데이터를 표시할 책임이 있습니다. 작은 처리 작업(예: 셀 컨텐츠에서 링크 만들기)만 클라이언트측에서 실행됩니다.

보고 프레임워크(표준 보고서의 구조로 그림)는 처리 큐에서 제공하는 다음 기본 구성 요소를 사용합니다.

![chlimage_1-248](assets/chlimage_1-248.png)

### 보고서 페이지 {#report-page}

보고서 페이지:

* 표준 CQ5 페이지입니다.
* 는 [보고서에 대해 구성된 표준 CQ5 템플릿](#report-template).

### 보고서 기본 {#report-base}

다음 [ `reportbase` 구성 요소](#report-base-component) 는 다음과 같은 보고서의 기초가 됩니다.

* 의 정의를 보유합니다 [쿼리](#the-query-and-data-retrieval) 에서는 데이터의 기본 결과 세트를 제공합니다.

* 모든 열( `columnbase`)가 보고서에 추가되었습니다.
* 사용 가능한 차트 유형과 현재 활성 상태를 정의합니다.
* 사용자가 보고서의 특정 측면을 구성할 수 있는 편집 대화 상자를 정의합니다.

### 열 기본 {#column-base}

각 열은 의 인스턴스입니다 [ `columnbase` 구성 요소](#column-base-component) 해당:

* parsys( `reportbase`) 내의 아무 곳에나 삽입할 수 있습니다.
* 에 대한 링크를 정의합니다 [기본 결과 집합](#the-query-and-data-retrieval); 즉, 이 결과 세트 내에서 참조되는 특정 데이터와 그 처리 방법을 정의합니다.
* 추가 정의를 보유합니다. 사용 가능한 합계 및 필터(예: 기본값 포함).

### 쿼리 및 데이터 검색 {#the-query-and-data-retrieval}

쿼리:

* 의 일부로 정의됩니다 [ `reportbase`](#report-base) 구성 요소.
* 는 [CQ QueryBuilder](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html).
* 보고서의 기반으로 사용되는 데이터를 검색합니다. 결과 집합(테이블)의 각 행은 쿼리에서 반환한 대로 노드에 연결됩니다. 에 대한 특정 정보 [개별 열](#column-base-component) 그런 다음 이 데이터 세트에서 추출됩니다.

* 일반적으로 다음 항목으로 구성됩니다.

   * 루트 경로.

      검색할 저장소의 하위 트리를 지정합니다.

      성능 영향을 최소화하려면 쿼리를 저장소의 특정 하위 트리로 제한(시도)하는 것이 좋습니다. 루트 경로는 [보고서 템플릿](#report-template) 또는 에서 사용자가 설정합니다. [구성(편집) 대화 상자](#configuration-dialog).

   * [하나 이상의 기준](#query-definition).

      (초기) 결과 세트를 생성하기 위해 적용됩니다. 여기에는 노드 유형에 대한 제한 또는 속성 제약 조건이 포함됩니다.

**여기에서 중요한 점은 쿼리의 결과 세트에서 반환되는 각 단일 노드가 보고서에서 단일 행을 생성하는 데 사용된다는 것입니다(따라서 1:1 관계).**

개발자는 보고서에 대해 정의된 쿼리가 해당 보고서에 적합한 노드 세트를 반환하도록 해야 합니다. 그러나 노드 자체에서 모든 필수 정보를 보유할 필요는 없으며, 상위 및/또는 하위 노드에서도 파생될 수 있습니다. 예를 들어 [사용자 보고서](/help/sites-administering/reporting.md#user-report) 노드 유형에 따라 노드를 선택합니다(이 경우 `rep:user`). 그러나 이 보고서의 대부분의 열은 이러한 노드에서 직접 데이터를 가져오지 않고 하위 노드에서 데이터를 가져옵니다 `profile`.

### 처리 큐 {#processing-queue}

다음 [쿼리](#the-query-and-data-retrieval) 보고서에서 행으로 표시할 데이터 세트 결과를 반환합니다. 결과 세트의 각 행은 [여러 단계](#phases-of-the-processing-queue): 보고서에 표시하기 위해 클라이언트로 전송되기 전에

이를 통해 다음을 수행할 수 있습니다.

* 기본 결과 집합에서 값 추출 및 파생.

   예를 들어 두 속성 간의 차이를 계산하여 두 속성 값을 단일 값으로 처리할 수 있습니다.

* 추출된 값 해결 이 작업은 다양한 방법으로 수행할 수 있습니다.

   예를 들어, 경로는 제목에 매핑할 수 있습니다(각 페이지의 보다 사람이 읽을 수 있는 콘텐츠에서처럼) *jcr:title* Analytics JavaScript용 URL 섹션을 참조하십시오.

* 다양한 지점에서 필터 적용.
* 필요한 경우 조합 값을 만듭니다.

   예를 들어, 사용자에게 표시되는 텍스트로 구성된 경우, 정렬에 사용할 값과 링크를 만드는 데 사용되는 추가 URL(클라이언트 측)이 있습니다.

#### 처리 큐의 워크플로우 {#workflow-of-the-processing-queue}

다음 워크플로우는 처리 큐를 나타냅니다.

![chlimage_1-249](assets/chlimage_1-249.png)

#### 처리 큐 단계 {#phases-of-the-processing-queue}

자세한 단계 및 요소는 다음과 같습니다.

1. 에서 반환한 결과를 변환합니다. [초기 쿼리(reportbase)](#query-definition) 값 추출기를 사용하여 기본 결과 집합에 추가할 수 있습니다.

   값 추출기는 [열 유형](#column-specific-definitions). 기본 JCR 쿼리에서 값을 읽고 이 값에서 결과 세트를 만드는 데 사용됩니다. 이후 추가 처리가 적용될 수 있습니다. 예를 들어 `diff` 를 입력하면 값 추출기가 두 개의 속성을 읽고 결과 세트에 추가되는 단일 값을 계산합니다. 값 추출기를 구성할 수 없습니다.

1. 원시 데이터를 포함하는 초기 결과 세트에 대해 [초기 필터링](#column-specific-definitions) (*원시* 위상)이 적용됩니다.

1. 값은 다음과 같습니다 [사전 처리](#processing-queue); 에 대해 정의된 대로 *적용* 단계.

1. [필터링](#column-specific-definitions) (지정됨 *사전 처리* 단계)가 사전 처리된 값에서 실행됩니다.

1. 값이 해결됨; 에 따르면 [정의된 확인자](#processing-queue).
1. [필터링](#column-specific-definitions) (지정됨 *해결됨* 단계)가 해결된 값에서 실행됩니다.

1. 데이터는 [그룹화되고 집계됨](#column-specific-definitions).
1. 배열 데이터는 (문자열 기반) 목록으로 변환하여 해결됩니다.

   이는 다중 값 결과를 표시할 수 있는 목록으로 변환하는 암시적 단계입니다. 다중 값 JCR 속성을 기반으로 하는 (집계되지 않은) 셀 값에 필요합니다.

1. 값이 다시 표시됩니다. [사전 처리](#processing-queue); 에 대해 정의된 대로 *afterApply* 단계.

1. 데이터가 정렬됩니다.
1. 처리된 데이터는 클라이언트에 전송됩니다.

>[!NOTE]
>
>기본 데이터 결과 세트를 반환하는 초기 쿼리는 `reportbase` 구성 요소.
>
>처리 큐의 다른 요소는 `columnbase` 구성 요소.

## 보고서 구성 및 구성 {#report-construction-and-configuration}

보고서를 구성하고 구성하려면 다음 항목이 필요합니다.

* a [보고서 구성 요소의 정의에 대한 위치](#location-of-report-components)
* a [ `reportbase` 구성 요소](#report-base-component)
* 하나 이상, [ `columnbase` 구성 요소](#column-base-component)
* a [페이지 구성 요소](#page-component)
* a [보고서 디자인](#report-design)
* a [보고서 템플릿](#report-template)

### 보고서 구성 요소의 위치 {#location-of-report-components}

기본 보고 구성 요소는 아래에 있습니다 `/libs/cq/reporting/components`.

그러나 이러한 노드를 업데이트하지 말고 아래에 고유한 구성 요소 노드를 만드는 것이 좋습니다 `/apps/cq/reporting/components` 더 적절한 경우 `/apps/<yourProject>/reports/components`.

여기서(예: ):

```
N:apps 
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:components [sling:Folder]
```

이 아래에서 보고서의 루트를 만들고, 이 아래에서 보고서 기본 구성 요소와 열 기본 구성 요소를 만듭니다.

```
N:apps 
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:components [sling:Folder]
                N:<reportname> [sling:Folder]
                        N:<reportname> [cq:Component]  // report base component
                        N:<columnname> [cq:Component]  // column base component
```

### 페이지 구성 요소 {#page-component}

보고서 페이지는 `sling:resourceType` 의 `/libs/cq/reporting/components/reportpage`.

사용자 지정된 페이지 구성 요소는 필요하지 않습니다(대부분의 경우).

## 보고서 기본 구성 요소 {#report-base-component}

각 보고서 유형에는 `/libs/cq/reporting/components/reportbase`.

이 구성 요소는 전체 보고서의 컨테이너 역할을 하며, 다음에 대한 정보를 제공합니다.

* 다음 [쿼리 정의](#query-definition).
* An [(선택 사항) 대화 상자](#configuration-dialog) 보고서 구성에 대해 설명합니다.
* 임의 [차트](#chart-definitions) 통합되었습니다.

```
N:<reportname> [cq:Component]
    P:sling:resourceSuperType = "cq/reporting/components/reportbase"
    N:charting
    N:dialog [cq:Dialog]
    N:queryBuilder
```

### 쿼리 정의 {#query-definition}

```xml
N:queryBuilder
    N:propertyConstraints
    [
        N:<name> // array of nodes (name irrelevant), each with the following properties:
            P:name
            P:value
    ]
    P:nodeTypes [String|String[]] 
    P:mandatoryProperties [String|String[]
  ]
```

* `propertyConstraints`

   결과 세트를 특정 값과 함께 특정 속성이 있는 노드로 제한하는 데 사용할 수 있습니다. 여러 제약 조건을 지정하는 경우 노드는 모든 제약 조건(AND 작업)을 충족해야 합니다.

   예:

   ```
   N:propertyConstraints
    [
    N:0
    P:sling:resourceType
    P:foundation/components/textimage
    N:1
    P:jcr:modifiedBy
    P:admin
    ]
   ```

   모두 `textimage` 마지막으로 수정한 구성 요소 `admin` 사용자.

* `nodeTypes`

   결과 집합을 지정된 노드 유형으로 제한하는 데 사용됩니다. 여러 노드 유형을 지정할 수 있습니다.

* `mandatoryProperties`

   결과 집합을 *모두* 지정한 속성의 값입니다. 속성 값은 고려되지 않습니다.

모두 선택 사항이며 필요에 따라 결합할 수 있지만, 하나 이상의 항목을 정의해야 합니다.

### 차트 정의 {#chart-definitions}

```xml
N:charting
    N:settings
        N:active [cq:WidgetCollection]
        [
            N:<name> // array of nodes, each with the following property
                P:id   // must match the id of a child node of definitions 
        ]
    N:definitions [cq:WidgetCollection]
    [
        N:<name> // array of nodes, each with the following properties
            P:id
            P:type
            // additional, chart type specific configurations
    ]
```

* `settings`

   활성 차트에 대한 정의를 보유합니다.

   * `active`

      여러 설정을 정의할 수 있으므로 이 설정을 사용하여 현재 활성화된 설정을 정의할 수 있습니다. 이러한 항목은 노드 배열에 의해 정의됩니다. 이 노드에는 필수 이름 지정 규칙이 없지만 표준 보고서에서는 종종 `0`, `1`.. `x`)에 포함되어 있어야 합니다.

      * `id`

         활성 차트에 대한 식별 이 값은 차트 중 하나의 ID와 일치해야 합니다 `definitions`.

* `definitions`

   보고서에 사용할 수 있는 차트 유형을 정의합니다. 다음 `definitions` 사용할 항목은 `active` 설정.

   이 정의는 노드 배열을 사용하여 지정합니다(종종 이름이 지정됨) `0`, `1`.. `x`)에 포함되어 있어야 합니다.

   * `id`

      차트 식별

   * `type`

      사용 가능한 차트 유형입니다. 다음 중에서 선택합니다.

      * `pie`
파이 차트입니다. 현재 데이터에서만 생성됩니다.

      * `lineseries`
일련의 선(실제 스냅샷을 나타내는 연결 점) 내역 데이터에서만 생성됩니다.
   * 차트 유형에 따라 추가 속성을 사용할 수 있습니다.

      * 차트 유형에 대해 `pie`:

         * `maxRadius` ( `Double/Long`)

            파이 차트에 허용되는 최대 반경입니다. 따라서 범례 없이 차트에 사용할 수 있는 최대 크기입니다. 다음 경우 무시됨 `fixedRadius` 가 정의된 횟수.

         * `minRadius` ( `Double/Long`)

            파이 차트에 허용되는 최소 반경입니다. 다음 경우 무시됨 `fixedRadius` 가 정의된 횟수.

         * `fixedRadius` ( `Double/Long`) 원형 차트의 고정 반경을 정의합니다.
      * 차트 유형에 대해 [`lineseries`](/help/sites-administering/reporting.md#display-limits):

         * `totals` ( `Boolean`)

            True로 설정되어 있는 경우 **합계** 을 표시해야 합니다.
기본값: `false`

         * `series` ( `Long`)

            표시할 라인/시리즈 수입니다.
기본값: `9` (최대 허용)

         * `hoverLimit` ( `Long`)

            사용자가 차트 범례에서 개별 값 또는 해당 레이블을 마우스로 가리키면 팝업을 표시할 최대 집계 스냅샷(각 가로 행에 표시되며 고유 값을 나타내는 점)의 수입니다.

            기본값: `35` (즉, 현재 차트 설정에 적용할 수 있는 고유 값이 35개 이상인 경우에는 팝업이 표시되지 않습니다.)

            병렬로 표시할 수 있는 팝업이 10개로 추가로 제한됩니다(범례 텍스트를 마우스로 가리키면 여러 팝업을 표시할 수 있음).



### 구성 대화 상자 {#configuration-dialog}

모든 보고서에는 보고서에 대한 다양한 매개 변수를 지정할 수 있는 구성 대화 상자가 있을 수 있습니다. 이 대화 상자는 **편집** 단추 사용

이 대화 상자는 표준 CQ입니다 [대화 상자](/help/sites-developing/components-basics.md#dialogs) 및 는 다음과 같이 구성할 수 있습니다( [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog) 추가 정보).

예제 대화 상자의 모양은 다음과 같습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    jcr:primaryType="cq:Dialog"
    height="{Long}424">
    <items jcr:primaryType="cq:WidgetCollection">
        <props jcr:primaryType="cq:Panel">
            <items jcr:primaryType="cq:WidgetCollection">
                <title
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/title.infinity.json"
                    xtype="cqinclude"/>
                <description
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/description.infinity.json"
                    xtype="cqinclude"/>
                <rootPath
                    jcr:primaryType="cq:Widget"
                    fieldLabel="Root path"
                    name="./report/rootPath"
                    rootPath=""
                    rootTitle="Repository root"
                    xtype="pathfield"/>
                <processing
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/processing.infinity.json"
                    xtype="cqinclude"/>
                <scheduling
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/scheduling.infinity.json"
                    xtype="cqinclude"/>
            </items>
        </props>
    </items>
</jcr:root>
```

사전 구성된 구성 요소가 몇 개 제공됩니다. 대화 상자에서 `xtype` 값이 인 속성 `cqinclude`:

* **`title`**

   `/libs/cq/reporting/components/commons/title`

   보고서 제목을 정의하는 텍스트 필드.

* **`description`**

   `/libs/cq/reporting/components/commons/description`

   보고서 설명을 정의하는 텍스트 영역.

* **`processing`**

   `/libs/cq/reporting/components/commons/processing`

   보고서의 처리 모드에 대한 선택기(수동으로/자동으로 데이터 로드).

* **`scheduling`**

   `/libs/cq/reporting/components/commons/scheduling`

   기록 차트의 스냅샷을 예약하기 위한 선택기입니다.

>[!NOTE]
>
>참조된 구성 요소는 `.infinity.json` 접미사(위 예제 참조).

### 루트 경로 {#root-path}

보고서에 대한 루트 경로를 정의할 수도 있습니다.

* **`rootPath`**

   이 옵션은 성능 최적화에 권장되는 저장소의 특정 섹션(트리 또는 하위 트리)으로 보고서를 제한합니다. 루트 경로는 `rootPath` 속성 `report` 각 보고서 페이지의 노드(페이지 작성 시 템플릿에서 가져옴).

   다음 방법으로 지정할 수 있습니다.

   * a [보고서 템플릿](#report-template) (고정 값으로 또는 구성 대화 상자의 기본값으로)
   * 사용자(이 매개 변수 사용)

## 열 기본 구성 요소 {#column-base-component}

각 열 유형에는 `/libs/cq/reporting/components/columnbase`.

열 구성 요소는 다음과 같은 조합을 정의합니다.

* 다음 [열 특정 쿼리](#column-specific-query) 구성.
* 다음 [해상도 및 사전 처리](#resolvers-and-preprocessing).
* 다음 [열 특정 정의](#column-specific-definitions) 필터 및 골재 등 `definitions` 하위 노드).
* [열 기본값](#column-default-values).
* 다음 [클라이언트 필터](#client-filter) 는 서버에서 반환한 데이터에서 표시할 정보를 추출합니다.
* 또한 열 구성 요소는 `cq:editConfig`. 를 정의하려면 [이벤트 및 작업](#events-and-actions) 필수 여부.
* 에 대한 구성 [일반 열](#generic-columns).

```
N:<columnname> [cq:Component]
    P:componentGroup
    P:jcr:title
    P:sling:resourceSuperType = "cq/reporting/components/columnbase"
    N:cq:editConfig [cq:EditConfig] // <a href="#events-and-actions">Events and Actions</a>
    N:defaults // <a href="#column-default-values">Column Default Values</a>
    N:definitions
      N:queryBuilder // <a href="#column-specific-query">Column Specific Query</a>
        P:property [String|String[]] // Column Specific Query
        P:subPath // Column Specific Query
        P:secondaryProperty [String|String[]] // Column Specific Query
        P:secondarySubPath // Column Specific Query
      N:data
        P:clientFilter [String] // <a href="#client-filter">Client Filter</a>
        P:resolver // <a href="#resolvers-and-preprocessing">Resolvers and Preprocessing</a>
        N:resolverConfig // Resolvers and Preprocessing
        N:preprocessing // Resolvers and Preprocessing
      P:type // <a href="#column-specific-definitions">Column Specific Definitions</a>
      P:groupable [Boolean] // Column Specific Definitions
      N:filters [cq:WidgetCollection] // Column Specific Definitions
      N:aggregates [cq:WidgetCollection] // Column Specific Definitions
```

참조 - [새 보고서 정의](#defining-your-new-report).

### 열 특정 쿼리 {#column-specific-query}

여기에서 특정 데이터 추출을 정의합니다 [보고서 데이터 결과 세트](#the-query-and-data-retrieval))을 사용 할 수도 있습니다.

```xml
N:definitions 
    N:queryBuilder
        P:property [String|String[]] 
        P:subPath
        P:secondaryProperty [String|String[]]
        P:secondarySubPath
```

* `property`

   실제 셀 값을 계산하는 데 사용할 속성을 정의합니다.

   속성이 String으로 정의된 경우[] 여러 속성을 순서대로 검사하여 실제 값을 찾습니다.

   예를 들어, 의 경우:

   `property = [ "jcr:lastModified", "jcr:created" ]`

   해당 값 추출기(여기에서 제어됨)는 다음 작업을 수행합니다.

   * 사용할 수 있는 jcr:lastModified 속성이 있는지 확인하고 있는 경우 사용합니다.
   * 사용할 수 있는 jcr:lastModified 속성이 없으면 jcr:created의 콘텐츠가 대신 사용됩니다.

* `subPath`

   쿼리로 반환된 노드에 결과가 없으면 `subPath` 은 속성이 실제로 있는 위치를 정의합니다.

* `secondaryProperty`

   실제 셀 값을 계산하는 데도 사용해야 하는 두 번째 속성을 정의합니다. 특정 열 유형(diff 및 sortable)에만 사용됩니다.

   예를 들어, 워크플로우 인스턴스 보고서의 경우 지정된 속성을 사용하여 시작 시간과 종료 시간 사이의 시간 차이 실제 값(밀리초)을 저장합니다.

* `secondarySubPath`

   SubPath와 유사하며 `secondaryProperty` 이 사용됩니다.

대부분의 경우, `property` 이 사용됩니다.

### 클라이언트 필터 {#client-filter}

클라이언트 필터는 서버에서 반환한 데이터에서 표시할 정보를 추출합니다.

>[!NOTE]
>
>이 필터는 전체 서버측 처리가 적용된 후 클라이언트측에서 실행됩니다.

```xml
N:definitions
    N:data
        P:clientFilter [String]
```

`clientFilter` 는 다음과 같은 JavaScript 함수로 정의됩니다.

* 입력으로 하나의 매개 변수를 받습니다. 서버에서 반환된 데이터(완전히 사전 처리됨)
* 출력으로 필터링된(처리된) 값을 반환합니다. 입력 정보에서 추출되거나 파생된 데이터

다음 예제에서는 구성 요소 경로에서 해당 페이지 경로를 추출합니다.

```
function(v) {
    var sepPos = v.lastIndexOf('/jcr:content');
    if (sepPos < 0) {
        return v;
    }
    return v.substring(sepPos + '/jcr:content'.length, v.length);
}
```

### 해상도 및 사전 처리 {#resolvers-and-preprocessing}

다음 [처리 큐](#processing-queue) 다양한 해상도를 정의하고 사전 처리를 구성합니다.

```xml
N:definitions
    N:data
        P:resolver
        N:resolverConfig
        N:preprocessing
            N:apply
            N:applyAfter
```

* `resolver`

   사용할 해결 방법을 정의합니다. 다음 해상도를 사용할 수 있습니다.

   * `const`

      값을 다른 값에 매핑 예를 들어 다음과 같은 상수를 확인하는 데 사용됩니다. `en` 동등 값 `English`.

   * `default`

      기본 해결자입니다. 이 확인자는 실제로 아무 것도 해결하지 않는 더미 확인자입니다.

   * `page`

      해당 페이지의 경로에 대한 경로 값을 확인합니다. 보다 정확하게, `jcr:content` 노드 아래에 있어야 합니다. 예, `/content/.../page/jcr:content/par/xyz` 확인됨: `/content/.../page/jcr:content`.

   * `path`

      선택적으로 하위 경로를 추가하고 노드의 속성에서 실제 값을 가져와 경로 값을 해결합니다(에 의해 정의됨) `resolverConfig`)를 클릭하여 제품에서 사용할 수 있습니다. 예: `path` 의 `/content/.../page/jcr:content` 의 콘텐츠로 확인할 수 있습니다. `jcr:title` 속성은 페이지 경로가 페이지 제목으로 확인됨을 의미합니다.

   * `pathextension`

      경로를 앞에 두고 확인된 경로에 있는 노드의 속성에서 실제 값을 사용하여 값을 확인합니다. 예: 값 `de` 경로 앞에 `/libs/wcm/core/resources/languages`: 속성에서 값을 가져오는 중 `language`를 입력하여 국가 코드를 확인합니다. `de` 언어 설명에 `German`.

* `resolverConfig`

   해결 프로그램에 대한 정의를 제공합니다. 사용 가능한 옵션은 `resolver` 선택:

   * `const`

      속성을 사용하여 확인할 상수를 지정합니다. 속성 이름은 확인할 상수를 정의합니다. 속성 값은 확인된 값을 정의합니다.

      예를 들어 **이름**= `1` 및 **값** `=One` 1에서 1로 해결됩니다.

   * `default`

      구성을 사용할 수 없습니다.

   * `page`

      * `propertyName` (옵션)

         값을 확인하는 데 사용할 속성의 이름을 정의합니다. 지정하지 않으면 기본값이 *jcr:title* (페이지 제목) 이 사용됩니다. 대상 `page` 해결자: 첫 번째 경로는 페이지 경로로 확인된 다음 페이지 제목으로 확인됨을 의미합니다.
   * `path`

      * `propertyName` (옵션)

         값을 확인하는 데 사용할 속성의 이름을 지정합니다. 지정하지 않으면 기본값이 `jcr:title` 이 사용됩니다.

      * `subPath` (옵션)

         이 속성은 값이 확인되기 전에 경로에 추가할 접미사를 지정하는 데 사용할 수 있습니다.
   * `pathextension`

      * `path` (필수입니다)

         추가할 경로를 정의합니다.

      * `propertyName` (필수입니다)

         실제 값이 있는 확인된 경로에서 속성을 정의합니다.

      * `i18n` (선택 사항) type boolean)

         확인된 값을 사용할지 여부를 결정합니다 *국제* (예: [CQ5의 국제화 서비스](/help/sites-administering/tc-manage.md)).



* `preprocessing`

   사전 처리는 선택 사항이며 처리 단계에 별도로 바인딩할 수 있습니다 *적용* 또는 *applyAfter*:

   * `apply`

      초기 사전 처리 단계([처리 대기열 표시의 3단계](#processing-queue)).

   * `applyAfter`

      사전 처리 후 적용([처리 대기열 표현 9단계](#processing-queue)).

#### Resolver {#resolvers}

해상도는 필요한 정보를 추출하는 데 사용됩니다. 다양한 해상도의 예는 다음과 같습니다.

**Const**

다음은 contentant value of를 해결합니다. `VersionCreated` 문자열 `New version created`.

자세한 내용은 `/libs/cq/reporting/components/auditreport/typecol/definitions/data`.

```xml
N:data
    P:resolver=const
    N:resolverConfig
        P:VersionCreated="New version created"
```

**페이지**

해당 페이지의 jcr:content (child) 노드에서 jcr:description 속성의 경로 값을 확인합니다.

자세한 내용은 `/libs/cq/reporting/components/compreport/pagecol/definitions/data`.

```xml
N:data
    P:resolver=page
    N:resolverConfig
        P:propertyName="jcr:description"
```

**경로**

다음 항목이 의 경로를 확인합니다. `/content/.../page` 의 `jcr:title` 속성은 페이지 경로가 페이지 제목으로 확인됨을 의미합니다.

자세한 내용은 `/libs/cq/reporting/components/auditreport/pagecol/definitions/data`.

```xml
N:data
    P:resolver=path
    N:resolverConfig
        P:propertyName="jcr:title"
        P:subPath="/jcr:content"
```

**경로 확장**

다음은 값 앞에 추가됩니다 `de` 경로 확장 사용 `/libs/wcm/core/resources/languages`그런 다음 속성에서 값을 가져옵니다 `language`를 입력하여 국가 코드를 확인합니다. `de` 언어 설명에 `German`.

자세한 내용은 `/libs/cq/reporting/components/userreport/languagecol/definitions/data`.

```xml
N:data
    P:resolver=pathextension
    N:resolverConfig
        P:path="/libs/wcm/core/resources/languages"
        P:propertyName="language"
```

#### 사전 처리 {#preprocessing}

다음 `preprocessing` 정의는 다음 중 하나에 적용할 수 있습니다.

* 원래 값:

   원본 값에 대한 사전 처리 정의가 `apply` 및/또는 `applyAfter` 직접 액세스할 수 있습니다.

* 합계된 상태의 값:

   필요한 경우 각 집계에 대해 별도의 정의를 제공할 수 있습니다.

   집계된 값에 대한 명시적 사전 처리를 지정하려면 사전 처리 정의가 각 값에 있어야 합니다 `aggregated` 하위 노드( `apply/aggregated`, `applyAfter/aggregated`). 개별 집계에 대한 명시적 사전 처리가 필요한 경우 사전 처리 정의는 각 집계의 이름을 사용하는 하위 노드에 있습니다(예: `apply/aggregated/min/max` 또는 기타 집계)를 사용할 수 있습니다.

사전 처리 중에 사용할 다음 중 하나를 지정할 수 있습니다.

* [패턴 찾기 및 바꾸기](#preprocessing-find-and-replace-patterns)
지정한 패턴(정규 표현식으로 정의됨)은 다른 패턴으로 대체됩니다. 예를 들어 원본에서 하위 문자열을 추출하는 데 사용할 수 있습니다.

* [데이터 유형 서식](#preprocessing-data-type-formatters)

   숫자 값을 상대 문자열로 변환합니다. 예를 들어, &quot;1시간의 시간 차이를 나타내는 값은 다음과 같은 문자열로 확인됩니다 `1:24PM (1 hour ago)`.

예:

```xml
N:definitions
    N:data
        N:preprocessing
            N:apply|applyAfter
                P:pattern         // regex
                P:replace         // replacement for regex
                // and/or
                P:format          // data type formatter
```

#### 사전 처리 - 패턴 찾기 및 바꾸기 {#preprocessing-find-and-replace-patterns}

전처리에 대해 `pattern` (으로 정의됨 [정규 표현식](https://en.wikipedia.org/wiki/Regular_expression) 또는 regex)로 대체됩니다 `replace` 패턴:

* `pattern`

   하위 문자열을 찾는 데 사용되는 정규 표현식입니다.

* `replace`

   원래 문자열을 대체하여 사용할 문자열 또는 문자열 표현입니다. 일반식으로 제공되는 문자열의 하위 문자열을 나타내는 경우가 많습니다 `pattern`.

교체 예는 다음과 같이 분류할 수 있습니다.

* 노드의 경우 `definitions/data/preprocessing/apply` 다음 두 가지 속성을 사용합니다.

   * `pattern`: `(.*)(/jcr:content)(/|$)(.*)`
   * `replace`: `$1`

* 다음과 같이 도착하는 문자열:

   * `/content/geometrixx/en/services/jcr:content/par/text`

* 4개 섹션으로 분할됩니다.

   * `$1` - `(.*)` - `/content/geometrixx/en/services`
   * `$2` - `(/jcr:content)` - `/jcr:content`
   * `$3` - `(/|$)` - `/`
   * `$4` - `(.*)` - `par/text`

* 및 를 로 나타내는 문자열로 대체했습니다. `$1`:

   * `/content/geometrixx/en/services`

#### 사전 처리 - 데이터 유형 서식 파일 {#preprocessing-data-type-formatters}

이러한 형식은 숫자 값을 상대 문자열로 변환합니다.

예를 들어 `min`, `avg` 및 `max` 합계. 로서의 `min`/ `avg`/ `max` 집계는 *시간 차이* (예: `10 days ago`)이면 데이터 포맷터가 필요합니다. 이를 위해 `datedelta` 포맷터가 `min`/ `avg`/ `max` 합계된 값. 다음과 같은 경우 `count` 집계를 사용할 수도 있고 이 경우 형식도 필요하지 않고 원래 값도 필요하지 않습니다.

현재 사용 가능한 데이터 유형 형식은 다음과 같습니다.

* `format`

   데이터 유형 포맷터:

   * `duration`

      지속 시간은 정의된 두 날짜 사이의 시간 범위입니다. 예를 들어, 11:23부터 1시간 후에 12:23까지 그리고 1시간 후에 2/13/11 12:23에 끝나는 워크플로우 작업의 시작 및 종료 시간이 1시간이 걸렸습니다.

      숫자 값(밀리초로 해석됨)을 기간 문자열로 변환합니다. 예 `30000` 형식은 * `30s`.*

   * `datedelta`

      Datadelta는 과거의 날짜 사이의 시간 범위이며 &quot;지금&quot;입니다. 따라서 보고서가 나중에 표시되면 다른 결과가 표시됩니다.

      숫자 값(일 단위의 시간 차이로 해석됨)을 상대적 날짜 문자열로 변환합니다. 예를 들어 1은 1일 전으로 형식이 지정됩니다.

다음 예제에서는 `datedelta` 서식 `min` 및 `max` 합계:

```xml
N:definitions
    N:data
        N:preprocessing
            N:apply
                N:aggregated
                    N:min
                        P:format = "datedelta"
                    N:max
                        P:format = "datedelta"
```

### 열 특정 정의 {#column-specific-definitions}

열 특정 정의는 해당 열에 사용할 수 있는 필터 및 합계를 정의합니다.

```xml
N:definitions
    P:type
    P:groupable [Boolean]
    N:filters [cq:WidgetCollection] 
    [
        N:<name> // array of nodes (names irrelevant) with the following properties:
            P:filterType
            P:id
            P:phase
    ]
    N:aggregates [cq:WidgetCollection]
    [
        N:<name> // array of nodes (names irrelevant) with the following properties:
            P:text
            P:type
    ]
```

* `type`

   다음은 표준 옵션으로 사용할 수 있습니다.

   * `string`
   * `number`
   * `int`
   * `date`
   * `diff`
   * `timeslot`

      합계에 필요한 날짜의 일부를 추출하는 데 사용됩니다(예: 연도별 그룹화하여 각 연도의 데이터를 집계함).

   * `sortable`

      정렬 및 표시에 다른 값(다른 속성에서 가져온 것)을 사용하는 값에 사용됩니다.
   게다가 위의 항목 중 하나를 다중 값으로 정의할 수 있습니다. 예 `string[]` 는 문자열의 배열을 정의합니다.

   값 추출기는 열 유형에 의해 선택됩니다. 열 유형에 값 추출기를 사용할 수 있으면 이 추출기가 사용됩니다. 그렇지 않으면 기본값 추출기가 사용됩니다.

   유형은 매개 변수를 사용할 수 있습니다(선택 사항). 예, `timeslot:year` 날짜 필드에서 연도를 추출합니다. 매개 변수를 사용하는 유형:

   * `timeslot` - 이 값은 의 해당 상수와 비교할 수 있습니다 `java.utils.Calendar`.

      * `timeslot:year` - `Calendar.YEAR`
      * `timeslot:month-of-year` - `Calendar.MONTH`
      * `timeslot:week-of-year` - `Calendar.WEEK_OF_YEAR`
      * `timeslot:day-of-month` - `Calendar.DAY_OF_MONTH`
      * `timeslot:day-of-week` - `Calendar.DAY_OF_WEEK`
      * `timeslot:day-of-year` - `Calendar.DAY_OF_YEAR`
      * `timeslot:hour-of-day` - `Calendar.HOUR_OF_DAY`
      * `timeslot:minute-of-hour` - `Calendar.MINUTE`


* `groupable`

   보고서를 이 열로 그룹화할 수 있는지 여부를 정의합니다.

* `filters`

   필터 정의.

   * `filterType`

      사용 가능한 필터는 다음과 같습니다.

      * `string`

         문자열 기반 필터입니다.
   * `id`

      필터 식별자.

   * `phase`

      사용 가능한 단계:

      * `raw`

         원시 데이터에 필터가 적용됩니다.

      * `preprocessed`

         미리 처리된 데이터에 필터가 적용됩니다.

      * `resolved`

         해결된 데이터에 필터가 적용됩니다.


* `aggregates`

   합계 정의.

   * `text`

      합계의 텍스트 이름입니다. If `text` 을 지정하지 않으면 합계의 기본 설명이 사용됩니다. 예 `minimum` 에 `min` 합계.

   * `type`

      집계 유형입니다. 사용 가능한 집계는 다음과 같습니다.

      * `count`

         행 수를 계산합니다.

      * `count-nonempty`

         비어 있지 않은 행 수를 계산합니다.

      * `min`

         최소값을 제공합니다.

      * `max`

         최대값을 제공합니다.

      * `average`

         평균 값을 제공합니다.

      * `sum`

         모든 값의 합계를 제공합니다.

      * `median`

         중간값을 제공합니다.

      * `percentile95`

         모든 값의 95번째 백분위수를 구합니다.

### 열 기본값 {#column-default-values}

열의 기본값을 정의하는 데 사용됩니다.

```xml
N:defaults
    P:aggregate
```

* `aggregate`

   유효한 `aggregate` 값은 과 동일합니다 `type` 아래에 `aggregates` 자세한 내용은 [열 특정 정의(정의 - 필터/집계)](#column-specific-definitions) ).

### 이벤트 및 작업 {#events-and-actions}

구성 편집은 수신기가 이벤트를 감지하고 이러한 이벤트가 발생한 후 적용할 작업을 정의하는 데 필요한 이벤트를 정의합니다. 자세한 내용은 [구성 요소 개발 소개](/help/sites-developing/components.md) 을 참조하십시오.

필요한 모든 작업이 준비되도록 다음 값을 정의해야 합니다.

```xml
N:cq:editConfig [cq:EditConfig] 
    P:cq:actions [String[]] = "insert", "delete" 
    P:cq:dialogMode = "floating"
    P:cq:layout = "auto"
    N:cq:listeners [cq:EditListenersConfig]
        P:aftercreate = "REFRESH_INSERTED"
        P:afterdelete = "REFRESH_SELF"
        P:afteredit = "REFRESH_SELF"
        P:afterinsert = "REFRESH_INSERTED"
        P:aftermove = "REFRESH_SELF"
        P:afterremove = "REFRESH_SELF"
```

### 일반 열 {#generic-columns}

일반 열은 (대부분의) 열 정의가 구성 요소 노드가 아니라 열 노드의 인스턴스에 저장되는 확장입니다.

개별 일반 구성 요소에 대해 사용자 지정하는 (표준) 대화 상자를 사용합니다. 이 대화 상자에서는 보고서 사용자가 메뉴 옵션을 사용하여 보고서 페이지에서 일반 열의 열 속성을 정의할 수 있습니다 **열 속성...**).

예를 들면 다음과 같습니다 **일반** 열 **사용자 보고서**; 참조 `/libs/cq/reporting/components/userreport/genericcol`.

열을 일반 상태로 만들려면:

* 설정 `type` 열 속성 `definition` 노드 끝 `generic`.

   자세한 내용은 `/libs/cq/reporting/components/userreport/genericcol/definitions`

* 열의 `definition` 노드 아래에 있어야 합니다.

   자세한 내용은 `/libs/cq/reporting/components/userreport/genericcol/definitions/dialog`

   * 대화 상자의 필드는 해당 구성 요소 속성(해당 경로 포함)과 동일한 이름을 참조해야 합니다.

      예를 들어, 대화 상자를 통해 일반 열의 유형을 구성할 수 있도록 하려면 이름이 인 필드를 사용합니다. `./definitions/type`.

   * UI/대화 상자를 사용하여 정의된 속성이 `columnbase` 구성 요소.

* 구성 편집을 정의합니다.

   자세한 내용은 `/libs/cq/reporting/components/userreport/genericcol/cq:editConfig`

* 표준 AEM 방법론을 사용하여 (추가) 열 속성을 정의합니다.

   구성 요소와 열 인스턴스 둘 다에 정의된 속성의 경우 열 인스턴스의 값이 우선합니다.

   일반 열에 사용할 수 있는 속성은 다음과 같습니다.

   * `jcr:title` - 열 이름
   * `definitions/aggregates` - 집계
   * `definitions/filters` - 필터
   * `definitions/type`- 열 유형(선택기/콤보 상자 또는 숨김 필드를 사용하여 대화 상자에서 정의해야 함)
   * `definitions/data/resolver` 및 `definitions/data/resolverConfig` (하지만 아님) `definitions/data/preprocessing` 또는 `.../clientFilter`) - 해결자 및 구성
   * `definitions/queryBuilder` - query builder 구성
   * `defaults/aggregate` - 기본 합계

   일반 열의 새 인스턴스인 경우 **사용자 보고서** 대화 상자로 정의된 속성은 다음 아래에 유지됩니다.

   `/etc/reports/userreport/jcr:content/report/columns/genericcol/settings/generic`

## 보고서 디자인 {#report-design}

디자인은 보고서를 만들 수 있는 열 유형을 정의합니다. 또한 열이 추가되는 단락 시스템도 정의합니다.

각 보고서에 대한 개별 디자인을 만드는 것이 좋습니다. 이렇게 하면 완벽한 유연성이 보장됩니다. 참조 - [새 보고서 정의](#defining-your-new-report).

기본 보고 구성 요소는 아래에 있습니다 `/etc/designs/reports`.

보고서 위치는 구성 요소를 찾은 위치에 따라 달라질 수 있습니다.

* `/etc/designs/reports/<yourReport>` 보고서가 보다 작은 위치에 있는 경우에 적합합니다 `/apps/cq/reporting`

* `/etc/designs/<yourProject>/reports/<*yourReport*>` 를 사용하여 보고서를 만들 때 `/apps/<yourProject>/reports` 패턴

필요한 디자인 속성이 `jcr:content/reportpage/report/columns` (예: `/etc/designs/reports/<reportName>/jcr:content/reportpage/report/columns`):

* `components`

   보고서에서 허용되는 모든 구성 요소 및/또는 구성 요소 그룹입니다.

* `sling:resourceType`

   값이 있는 속성 `cq/reporting/components/repparsys`.

디자인 코드 조각(구성 요소 보고서의 디자인에서 가져옴)의 예는 다음과 같습니다.

```xml
<!-- ... -->
    <jcr:content
        jcr:primaryType="nt:unstructured"
        jcr:title="Component Report"
        sling:resourceType="wcm/core/components/designer">
        <reportpage jcr:primaryType="nt:unstructured">
            <report jcr:primaryType="nt:unstructured">
                <columns
                    jcr:primaryType="nt:unstructured"
                    sling:resourceType="cq/reporting/components/repparsys"
                    components="group:Component Report"/>
            </report>
        </reportpage>
    </jcr:content>
<!-- ... -->
```

개별 열에 대한 디자인을 지정할 필요는 없습니다. 사용 가능한 열은 디자인 모드에서 정의할 수 있습니다.

>[!NOTE]
>
>표준 보고서 디자인을 변경하지 않는 것이 좋습니다. 핫픽스를 업그레이드하거나 설치할 때 변경 사항이 손실되지 않도록 하기 위한 것입니다.
>
>표준 보고서를 사용자 지정하려면 보고서 및 해당 디자인을 복사하십시오.

>[!NOTE]
>
>보고서를 만들 때 기본 열을 자동으로 만들 수 있습니다. 템플릿에 지정됩니다.

## 보고서 템플릿 {#report-template}

각 보고서 유형마다 템플릿을 제공해야 합니다. 이것은 표준입니다 [CQ 템플릿](/help/sites-developing/templates.md) 와 은 이와 같이 구성할 수 있습니다.

템플릿은 다음을 수행해야 합니다.

* 설정 `sling:resourceType` to `cq/reporting/components/reportpage`

* 사용할 디자인을 나타냅니다
* 만들기 `report` 컨테이너를 참조하는 하위 노드( `reportbase`) 구성 요소를 사용할 수 없습니다 `sling:resourceType` 속성

구성 요소 보고서 템플릿에서 가져온 템플릿 코드 조각 예는 다음과 같습니다.

```xml
<!-- ... -->
    <jcr:content
        cq:designPath="/etc/designs/reports/compreport"
        jcr:primaryType="cq:PageContent"
        sling:resourceType="cq/reporting/components/reportpage">
        <report
            jcr:primaryType="nt:unstructured"
            sling:resourceType="cq/reporting/components/compreport/compreport"/>
    </jcr:content>
<!-- .. -->
```

루트 경로(사용자 보고서 템플릿에서 선택됨)의 정의를 보여주는 템플릿 코드 예는 다음과 같습니다.

```xml
<!-- ... -->
    <jcr:content
        cq:designPath="/etc/designs/reports/userreport"
        jcr:primaryType="cq:PageContent"
        sling:resourceType="cq/reporting/components/reportpage">
        <report
            jcr:primaryType="nt:unstructured"
            rootPath="/home/users"
            sling:resourceType="cq/reporting/components/compreport/compreport"/>
    </jcr:content>
<!-- .. -->
```

기본 보고 템플릿은 `/libs/cq/reporting/templates`.

그러나 이러한 노드를 업데이트하지 말고 아래에 고유한 구성 요소 노드를 만드는 것이 좋습니다 `/apps/cq/reporting/templates` 더 적절한 경우 `/apps/<yourProject>/reports/templates`.

예: [보고서 구성 요소의 위치](#location-of-report-components)):

```xml
N:apps 
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:templates [sling:Folder]
```

이 아래에서 템플릿의 루트를 만듭니다.

```xml
N:apps 
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:templates [sling:Folder]
                N:<reportname> [sling:Folder]
```

## 고유한 보고서 만들기 - 예 {#creating-your-own-report-an-example}

### 새 보고서 정의 {#defining-your-new-report}

새 보고서를 정의하려면 다음을 만들고 구성해야 합니다.

1. 보고서 구성 요소의 루트입니다.
1. 보고서 기본 구성 요소입니다.
1. 열 기본 구성 요소가 하나 이상 있습니다.
1. 보고서 디자인.
1. 보고서 템플릿의 루트입니다.
1. 보고서 템플릿입니다.

이러한 단계를 보여주기 위해 다음 예에서는 리포지토리 내의 모든 OSGi 구성을 나열하는 보고서를 정의합니다. 즉, `sling:OsgiConfig` 노드 아래에 있어야 합니다.

>[!NOTE]
>
>기존 보고서를 복사한 다음 새 버전을 사용자 지정하는 것이 대체 방법입니다.

1. 새 보고서에 대한 루트 노드를 만듭니다.

   예를 들면 다음과 같습니다. `/apps/cq/reporting/components/osgireport`.

   ```xml
   N:cq [nt:folder]
       N:reporting [sling:Folder]
           N:components [sling:Folder]
               N:osgireport [sling:Folder]
   ```

1. 보고서 기준을 정의합니다. 예 `osgireport[cq:Component]` 아래에 `/apps/cq/reporting/components/osgireport`.

   ```xml
   N:osgireport [sling:Folder]
       N:osgireport [cq:Component]
           P:sling:resourceSuperType [String] = "cq/reporting/components/reportbase"
           N:charting [nt:unstructured]
               N:settings [nt:unstructured]
                   N:active [cq:WidgetCollection]
                       N:0 [nt:unstructured]
                           P:id [String] = "pie"
                       N:1 [nt:unstructured]
                           P:id [String] = "lineseries"
               N:definitions [cq:WidgetCollections]
                   N:0 [nt:unstructured]
                       P:id [String] = "pie"
                       P:maxRadius [Long] = 180
                       P:type [String] = "pie"
                   N:1 [nt:unstructured]
                       P:id [String] = "lineseries"
                       P:type [String] = "lineseries"
           N:dialog [cq:Dialog]
               P:height [Long] = 424
               N:items [cq:WidgetCollection]
                   N:props [cq:Panel]
                       N:items [cq:WidgetCollection]
                           N:title [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/title.infinity.json"
                               P:xtype [String] = "cqinclude"
                           N:description [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/description.infinity.json"
                               P:xtype [String] = "cqinclude"
                           N:rootPath [cq:Widget]
                               P:fieldLabel [String] = "Root path"
                               P:name [String] = "./report/rootPath"
                               P:xtype [String] = "pathfield"
                           N:processing [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/processing.infinity.json"
                               P:xtype [String] = "cqinclude"
                           N:scheduling [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/scheduling.infinity.json"
                               P:xtype [String] = "cqinclude"
           N:queryBuilder [nt:unstructured]
               P:nodeTypes [String[]] = "sling:OsgiConfig"
   ```

   이는 다음과 같은 보고서 기본 구성 요소를 정의합니다.

   * 유형의 모든 노드 검색 `sling:OsgiConfig`
   * 둘 다 표시 `pie` 및 `lineseries` 차트
   * 사용자가 보고서를 구성할 수 있는 대화 상자를 제공합니다

1. 첫 번째 열(columnbase) 구성 요소를 정의합니다. 예 `bundlecol[cq:Component]` 아래에 `/apps/cq/reporting/components/osgireport`.

   ```xml
   N:osgireport [sling:Folder]
       N:bundlecol [cq:Component]
           P:componentGroup [String] = "OSGi Report"
           P:jcr:title = "Bundle"
           P:sling:resourceSuperType [String] = "cq/reporting/components/columnbase"
           N:cq:editConfig [cq:EditConfig]
               P:cq:actions [String[]] = "insert", "delete"
               P:cq:dialogMode [String] = "floating"
               P:cq:layout [String] = "auto"
               N:cq:listeners [cq:EditListenersConfig]
                   P:aftercreate [String] "REFRESH_INSERTED"
                   P:afterdelete [String] "REFRESH_SELF"
                   P:afteredit [String] "REFRESH_SELF"
                   P:afterinsert [String] "REFRESH_INSERTED"
                   P:aftermove [String] "REFRESH_SELF"
                   P:afterremove [String] "REFRESH_SELF"
           N:defaults [nt:unstructured]
               P:aggregate [String] = "count"
           N:definitions [nt:unstructured]
               P:groupable [Boolean] = false
               P:type [String] = "string"
               N:queryBuilder [nt:unstructured]
                   P:property [String] = "jcr:path"
   ```

   이는 다음과 같은 열 기본 구성 요소를 정의합니다.

   * 서버에서 받은 값을 검색하고 반환합니다. 이 경우 `jcr:path` 다음 `sling:OsgiConfig` 노드
   * 은 `count` 합계
   * 그룹화할 수 없습니다.
   * 에는 제목이 있습니다 `Bundle` (표 내의 열 제목)
   * 사이드 킥에 있음 `OSGi Report`
   * 지정된 이벤트 시 새로 고침

   >[!NOTE]
   >
   >이 예에는 `N:data` 및 `P:clientFilter`. 이것은 서버에서 받은 값이 기본 동작인 1:1 단위로 반환되기 때문입니다.
   >
   >정의와 동일합니다.
   >
   >
   ```
   >N:data [nt:unstructured]
   >   P:clientFilter [String] = "function(v) { return v; }"
   >```
   >여기서 함수는 수신하는 값을 단순히 반환합니다.

1. 보고서 디자인을 정의합니다. 예 `osgireport[cq:Page]` 아래에 `/etc/designs/reports`.

   ```xml
   N:osgireport [cq:Page]
       N:jcr:content [nt:unstructured]
           P:jcr:title [String] = "OSGi report"
           P:sling:resourceType [String] = "wcm/core/components/designer"
           N:reportpage [nt:unstructured]
               N:report [nt:unstructured]
                   N:columns [nt:unstructured]
                       P:components [String] = "group:OSGi Report"
                       P:sling:resourceType [String] = "cq/reporting/components/repparsys"
   ```

1. 새 보고서 템플릿에 대한 루트 노드를 만듭니다.

   예를 들면 다음과 같습니다. `/apps/cq/reporting/templates/osgireport`.

   ```xml
   N:cq [nt:folder]
       N:reporting [sling:Folder]
           N:templates [sling:Folder]
               N:osgireport [cq:Template]
   ```

1. 보고서 템플릿을 정의합니다. 예 `osgireport[cq:Template]` 아래에 `/apps/cq/reporting/templates`.

   ```xml
   N:osgireport [cq:Template]
       P:allowedPaths [String[]] = "/etc/reports(/.*)?"
       P:jcr:description [String] = "Use this report generator to create a new OSGi report."
       P:jcr:title [String] = "OSGi Report Template"
       P:ranking [Long] = 100
       P:shortTitle [String] = "OSGi Report"
       N:jcr:content [cq:PageContent]
           P:cq:designPath [String] = "/etc/designs/reports/osgireport"
           P:sling:resourceType [String] = "cq/reporting/components/reportpage"
           N:report [nt:unstructured]
               P:rootPath [String] = "/"
               P:sling:resourceType [String] = "cq/reporting/components/osgireport/osgireport"
       N:thumbnail.png [nt:file]
   ```

   이 템플릿은 다음과 같은 템플릿을 정의합니다.

   * 는 을 정의합니다. `allowedPaths` 결과 보고서의 경우 - 위의 경우 `/etc/reports`
   * 템플릿에 대한 제목 및 설명을 제공합니다
   * 템플릿 목록에서 사용할 축소판 이미지를 제공합니다. 이 노드의 전체 정의는 위에 나열되지 않습니다. 기존 보고서에서 thumbnail.png 인스턴스를 복사하는 것이 더 쉽습니다.

### 새 보고서의 인스턴스 만들기 {#creating-an-instance-of-your-new-report}

이제 새 보고서의 인스턴스를 만들 수 있습니다.

1. 를 엽니다. **도구** 콘솔.

1. 선택 **보고서** 왼쪽 창에 있습니다.
1. Then **새로 만들기...** 를 클릭합니다. 정의 **제목** 및 **이름**&#x200B;새 보고서 유형(예: **OSGi 보고서 템플릿**)을 클릭한 다음 **만들기**.
1. 새 보고서 인스턴스가 목록에 나타납니다. 열려면 이 아이콘을 두 번 클릭합니다.
1. 구성 요소를 드래그합니다(이 예제의 경우 **번들** 에서 **OSGi 보고서** 그룹) 사이드킥에서 첫 번째 열 및 [보고서 정의 시작](/help/sites-administering/reporting.md#the-basics-of-report-customization).

   >[!NOTE]
   >
   >이 예제에 그룹 가능한 열이 없으므로 차트를 사용할 수 없습니다. 차트를 보려면 `groupable` to `true`:
   >
   >
   ```
   >N:osgireport [sling:Folder]
   > N:bundlecol [cq:Component]
   > N:definitions [nt:unstructured]
   > P:groupable [Boolean] = true
   >```

## 보고서 프레임워크 서비스 구성 {#configuring-the-report-framework-services}

이 섹션에서는 보고서 프레임워크를 구현하는 OSGi 서비스에 대한 고급 구성 옵션에 대해 설명합니다.

웹 콘솔의 구성 메뉴를 사용하여 볼 수 있습니다(예: `http://localhost:4502/system/console/configMgr`). AEM을 사용하여 작업하는 경우 이러한 서비스에 대한 구성 설정을 관리하는 방법에는 몇 가지가 있습니다. 참조 [OSGi 구성](/help/sites-deploying/configuring-osgi.md) 자세한 내용 및 권장 지침

### 기본 서비스(일 CQ 보고 구성) {#basic-service-day-cq-reporting-configuration}

* **표준 시간대** 시간대 기록 데이터가 만들어지는 을 정의합니다. 이것은 기록 차트에 전 세계 각 사용자에 대해 동일한 데이터가 표시되도록 하기 위한 것입니다.
* **로케일** 는 **표준 시간대** 참조하십시오. 로케일은 일부 로케일 특정 달력 설정(예: 주의 첫 번째 날이 일요일인지 월요일인지)을 결정하는 데 사용됩니다.

* **스냅샷 경로** 기록 차트의 스냅샷이 저장되는 루트 경로를 정의합니다.
* **보고서 경로** 보고서가 있는 경로를 정의합니다. 이 기능은 스냅샷 서비스에서 실제로 스냅샷을 만들 보고서를 결정하는 데 사용됩니다.
* **일별 스냅샷** 일별 스냅샷을 가져올 각 날의 시간을 정의합니다. 지정한 시간은 서버의 로컬 시간대로 지정됩니다.
* **시간별 스냅샷** 시간별 스냅샷을 가져올 각 시간의 분을 정의합니다.
* **행(최대)** 각 스냅샷에 대해 저장되는 최대 행 수를 정의합니다. 이 값은 합리적으로 선택되어야 합니다. 너무 높으면 저장소 크기에 영향을 주며 너무 낮으면 내역 데이터를 처리하는 방식 때문에 데이터가 정확하지 않을 수 있습니다.
* **거짓 데이터**, 활성화된 경우 `fakedata` 선택기; 비활성화된 경우 `fakedata` 선택기에서 예외를 throw합니다.

   데이터가 가짜이므로 반드시 *전용* 테스트 및 디버깅 용도로 사용됩니다.

   사용 `fakedata` 선택기가 암시적으로 보고서를 완료하므로 기존의 모든 데이터가 손실됩니다. 데이터를 수동으로 복원할 수 있지만 시간이 많이 걸릴 수 있습니다.

* **스냅샷 사용자** 스냅샷 작성에 사용할 수 있는 선택적 사용자를 정의합니다.

   기본적으로 보고서가 완료된 사용자를 위해 스냅샷을 만듭니다. 대신 사용되는 대체 사용자를 지정하려는 경우(예: 게시 시스템에서 이 사용자가 해당 계정이 복제되지 않아 존재하지 않는 경우) 이러한 상황이 발생할 수 있습니다.

   또한 사용자를 지정하면 보안 위험이 발생할 수 있습니다.

* **스냅샷 사용자 적용**&#x200B;를 활성화한 경우, *스냅샷 사용자*. 제대로 처리되지 않으면 심각한 보안 문제가 발생할 수 있습니다.

### 캐시 설정(일 CQ 보고 캐시) {#cache-settings-day-cq-reporting-cache}

* **활성화** 보고서 데이터의 캐싱을 활성화하거나 비활성화할 수 있습니다. 보고서 캐시를 활성화하면 여러 요청 중에 보고서 데이터가 메모리에 유지됩니다. 이 경우 성능이 향상될 수 있지만 메모리 사용량이 더 늘어날 수 있으며, 극단적인 경우 메모리 부족 상황이 발생할 수 있습니다.
* **TTL** 보고서 데이터가 캐시되는 시간(초)을 정의합니다. 숫자가 높을수록 성능이 향상되지만 기간 내에 데이터가 변경되는 경우 부정확한 데이터를 반환할 수 있습니다.
* **최대 항목 수** 언제든지 캐싱할 최대 보고서 수를 정의합니다.

>[!NOTE]
>
>보고서 데이터는 각 사용자 및 언어별로 다를 수 있습니다. 따라서 보고서 데이터는 보고서, 사용자 및 언어별로 캐시됩니다. 이것은 **최대 항목 수** 값 `2` 실제로 다음 중 하나에 대해 데이터를 캐시합니다.
>
>* 언어 설정이 다른 두 사용자를 위한 보고서 1개
>* 사용자 1명과 보고서 2개
>

