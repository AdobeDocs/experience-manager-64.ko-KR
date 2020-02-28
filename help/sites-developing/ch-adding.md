---
title: 페이지에 ContextHub 추가 및 저장소 액세스
seo-title: 페이지에 ContextHub 추가 및 저장소 액세스
description: 페이지에 ContextHub를 추가하여 ContextHub 기능을 활성화하고 ContextHub Javascript 라이브러리에 연결
seo-description: 페이지에 ContextHub를 추가하여 ContextHub 기능을 활성화하고 ContextHub Javascript 라이브러리에 연결
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243

---


# 페이지에 ContextHub 추가 및 저장소 액세스 {#adding-contexthub-to-pages-and-accessing-stores}

페이지에 ContextHub를 추가하여 ContextHub 기능을 활성화하고 ContextHub Javascript 라이브러리에 연결

ContextHub Javascript API는 ContextHub에서 관리하는 컨텍스트 데이터에 대한 액세스를 제공합니다. 이 페이지에서는 컨텍스트 데이터 액세스 및 조작을 위한 API의 주요 기능에 대해 간략히 설명합니다. 자세한 정보 및 코드 예를 보려면 API 참조 설명서 링크를 따르십시오.

## 페이지 구성 요소에 ContextHub 추가 {#adding-contexthub-to-a-page-component}

ContextHub 기능을 활성화하고 ContextHub Javascript 라이브러리에 연결하려면 페이지의 `head` 섹션에 contexthub 구성 요소를 포함합니다. 페이지 구성 요소에 대한 JSP 코드는 다음과 같습니다.

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

또한 ContextHub 도구 모음이 미리 보기 모드에 나타나는지 여부를 구성해야 합니다. ContextHub [UI 표시 및 숨기기를 참조하십시오](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## ContextHub 저장소 정보 {#about-contexthub-stores}

ContextHub 저장소를 사용하여 컨텍스트 데이터를 유지합니다. ContextHub에서는 모든 저장소 유형의 기반이 되는 다음과 같은 유형의 저장소를 제공합니다.

* [PersistentStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistentJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

모든 스토어 유형은 [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) 클래스의 확장입니다. 새 스토어 유형을 만드는 방법에 대한 자세한 내용은 사용자 정의 스토어 [만들기를 참조하십시오](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). 샘플 스토어 유형에 대한 자세한 내용은 샘플 [ContextHub 스토어 지원자를 참조하십시오](/help/sites-developing/ch-samplestores.md).

### 지속성 모드 {#persistence-modes}

Context Hub 저장소는 다음 지속성 모드 중 하나를 사용합니다.

* **** 로컬:HTML5 localStorage를 사용하여 데이터를 유지합니다. 로컬 저장소는 세션 간에 브라우저에 유지됩니다.
* **** 세션:HTML5 sessionStorage를 사용하여 데이터를 유지합니다. 세션 스토리지는 브라우저 세션 동안 지속되며 모든 브라우저 창에서 사용할 수 있습니다.
* **** 쿠키:데이터 저장을 위해 브라우저의 기본 쿠키 지원을 사용합니다. 쿠키 데이터는 HTTP 요청에서 서버로 전송되거나 서버에서 전송됩니다.
* **** Window.name:window.name 속성을 사용하여 데이터를 유지합니다.
* **** 메모리:Javascript 개체를 사용하여 데이터를 유지합니다.

기본적으로 Context Hub에서는 로컬 지속성 모드를 사용합니다. 브라우저가 HTML5 localStorage를 지원하지 않거나 허용하지 않으면 세션 지속성이 사용됩니다. 브라우저가 HTML5 sessionStorage를 지원하지 않거나 허용하지 않으면 Window.name 지속성이 사용됩니다.

### 데이터 저장 {#store-data}

내부적으로 데이터 양식을 트리 구조로 저장하여 기본 유형 또는 복잡한 객체로 값을 추가할 수 있습니다. 저장소에 복잡한 개체를 추가하면 개체 속성이 데이터 트리에서 분기됩니다. 예를 들어 다음 복잡한 개체가 location이라는 빈 저장소에 추가됩니다.

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

저장소 데이터의 트리 구조는 다음과 같이 개념화할 수 있습니다.

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

트리 구조는 저장소의 데이터 항목을 키/값 쌍으로 정의합니다. 위의 예에서 키는 값과 `/number` 일치하고 `321`키는 `/data/country` 값과 `Switzerland`일치합니다.

### 개체 조작 {#manipulating-objects}

ContextHub은 Javascript 개체를 조작하기 위한 [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) 클래스를 제공합니다. JavaScript 개체를 스토어에 추가하기 전에 또는 스토어에서 가져온 후에 조작하는 경우 이 클래스의 함수를 사용합니다.

또한 이 [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) 클래스는 객체를 트리거로 직렬화하고 문자열을 객체로 역직렬화하는 기능을 제공합니다. 기본적으로 `JSON.parse` 및 `JSON.stringify` 함수를 포함하지 않는 브라우저를 지원하려면 JSON 데이터를 처리하는 데 이 클래스를 사용하십시오.

## ContextHub Store와 상호 작용 {#interacting-with-contexthub-stores}

Javascript [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) 개체를 사용하여 Javascript 개체로 스토어를 가져옵니다. 저장소 개체를 가져오면 포함된 데이터를 조작할 수 있습니다. 또는 [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) 함수를 사용하여 스토어를 [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) 가져옵니다.

### 저장소 데이터 액세스 {#accessing-store-data}

Javascript [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) 클래스는 저장소 데이터와 상호 작용하기 위한 여러 함수를 정의합니다. 다음 함수는 개체에 포함된 여러 데이터 항목을 저장하고 검색합니다.

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

개별 데이터 항목은 키/값 쌍 세트로 저장됩니다. 값을 저장하고 검색하려면 해당 키를 지정합니다.

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

사용자 지정 스토어 지원자는 데이터 저장에 대한 액세스 권한을 제공하는 추가 기능을 정의할 수 있습니다.

>[!NOTE]
>
>ContextHub은 기본적으로 현재 게시 서버에 로그인한 사용자를 인식하지 않으며 이러한 사용자는 ContextHub에서 &quot;익명&quot;으로 간주합니다.
>
>We.Retail 참조 사이트에 [](/help/sites-developing/we-retail.md)구현된 대로 프로필 스토어를 로드하여 ContextHub에서 로그인한 사용자를 인식하도록 할 수 있습니다. 여기에서 GitHub의 [관련 코드를 참조하십시오](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub 이벤트 {#contexthub-eventing}

ContextHub에는 스토어 이벤트에 자동으로 반응할 수 있는 이벤트 프레임워크가 포함되어 있습니다. 각 저장소 객체에는 스토어의 [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) [`eventing`](/help/sites-developing/contexthub-api.md#eventing) 속성으로 사용할 수 있는 객체가 포함되어 있습니다. JavaScript 함수를 스토어 이벤트에 바인딩하려면 [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) 또는 [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) 함수를 사용합니다.

## 컨텍스트 허브를 사용하여 쿠키 조작 {#using-context-hub-to-manipulate-cookies}

Context Hub Javascript API는 브라우저 쿠키 처리에 대한 브라우저 간 지원을 제공합니다. 네임스페이스는 쿠키를 만들고, 조작하고, 삭제하는 몇 가지 함수를 정의합니다. [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie)

## 해결된 ContextHub 세그먼트 결정 {#determining-resolved-contexthub-segments}

ContextHub 세그먼트 엔진을 사용하면 현재 컨텍스트에서 해결될 등록된 세그먼트 중 어떤 세그먼트를 결정할 수 있습니다. 해결된 세그먼트를 검색하려면 클래스의 getResolvedSegments 함수를 [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) 사용합니다. 그런 다음 `getName` 클래스의 또는 `getPath` [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) 함수를 사용하여 세그먼트를 테스트합니다.

### 설치된 세그먼트 {#installed-segments}

ContextHub 세그먼트는 `/conf/we-retail/settings/wcm/segments` 노드 아래에 설치됩니다.

* 여성
* over-30
* 여성 이하 30세
* 남성
* 남성-초과-30
* 남성-하위 30
* order-value-75-to-100
* order-value-over-100
* 초과-30
* 여름
* 여름 여성
* 여름 여성-over-30
* 여름 여성-이하-30
* 여름 남자
* summer-male-over-30
* summer-male-under-30
* 30세 미만
* 겨울
* 겨울 여성
* 겨울 여자-over-30
* 겨울 여성-언더파-30
* 겨울 남자
* winter-male-over-30
* 겨울 남자-언더파-20

이러한 세그먼트를 해결하는 데 사용되는 규칙은 다음과 같이 요약됩니다.

* 여성 또는 남성은 `gender` 프로필 [](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) 저장소의 데이터 항목에서 결정됩니다.

* 나이는 프로필 저장소의 연령 데이터 항목에서 결정됩니다.
* 계절은 지리적 위치 [저장소의 위도 데이터 항목과](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) surferinfo 스토어의 월 데이터 항목으로 결정됩니다.

>[!WARNING]
>
>설치된 세그먼트는 프로젝트에 대한 고유한 전용 구성을 작성하는 데 도움이 되는 참조 구성으로 제공되며 이러한 구성을 직접 사용해서는 안 됩니다.

## ContextHub에 대한 디버그 메시지 로깅 {#logging-debug-messages-for-contexthub}

개발 시 유용한 세부 디버그 메시지를 기록하도록 Adobe Granite ContextHub OSGi 서비스(PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`)를 구성합니다.

서비스를 구성하려면 웹 콘솔을 사용하거나 [저장소에서](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) JCR [노드를](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository)사용할 수 있습니다.

* 웹 콘솔:디버그 메시지를 기록하려면 디버그 속성을 선택합니다.
* JCR 노드:디버그 메시지를 기록하려면 부울 `com.adobe.granite.contexthub.debug` 속성을 로 설정합니다 `true`.

## ContextHub 프레임워크 개요 보기 {#see-an-overview-of-the-contexthub-framework}

ContextHub에서는 ContextHub 프레임워크의 개요를 볼 수 있는 [진단 페이지를](/help/sites-developing/ch-diagnostics.md) 제공합니다.
