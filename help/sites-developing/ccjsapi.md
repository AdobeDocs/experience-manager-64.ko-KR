---
title: Client Context Javascript API
seo-title: Client Context Javascript API
description: Client Context용 Javascript API
seo-description: The Javascript API for Client Context
uuid: be58998c-f23e-4768-8394-1f1ad3994c4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: a6e5810b-dac5-4137-93cf-5d8d53cacc49
feature: Context Hub
exl-id: 6678e462-d40b-4b55-8f7e-98fab2273898
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3189'
ht-degree: 2%

---

# Client Context Javascript API{#client-context-javascript-api}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## CQ_Analytics.ClientContextMgr {#cq-analytics-clientcontextmgr}

CQ_Analytics.ClientContextMgr 개체는 자체 등록된 세션 저장소 집합을 포함하는 단일 항목이며 세션 저장소를 등록, 유지 및 관리하는 방법을 제공합니다.

CQ_Analytics.PersistentSessionStore를 확장합니다.

### 메서드 {#methods}

#### getRegisteredStore(name) {#getregisteredstore-name}

지정된 이름의 세션 저장소를 반환합니다. 참조 - [세션 저장소 액세스](/help/sites-developing/client-context.md#accessing-session-stores).

**매개변수**

* 이름: 문자열. 세션 저장소의 이름입니다.

**반환**

지정된 이름의 세션 저장소를 나타내는 CQ_Analytics.SessionStore 개체입니다. 반환 `null` 지정된 이름의 저장소가 없는 경우

#### register(sessionstore) {#register-sessionstore}

Client Context에 세션 저장소를 등록합니다. 완료되면 상점 레지스터를 실행하고 업데이트 이벤트를 저장합니다.

**매개변수**

* sessionstore: CQ_Analytics.SessionStore입니다. 등록할 세션 저장소 개체입니다.

**반환**

반환된 값이 없습니다.

## CQ_Analytics.ClientContextUtils {#cq-analytics-clientcontextutils}

세션 저장소 활성화 및 등록을 수신하는 방법을 제공합니다. 참조 - [세션 저장소가 정의되고 초기화되었는지 확인](/help/sites-developing/client-context.md#checking-that-a-session-store-is-defined-and-initialized).

### 메서드 {#methods-1}

#### onStoreInitialized(storeName, callback, delay) {#onstoreinitialized-storename-callback-delay}

세션 저장소가 초기화될 때 호출되는 콜백 함수를 등록합니다. 여러 번 초기화된 저장소의 경우 콜백 함수가 한 번만 호출되도록 콜백 지연을 지정합니다.

* 이전 초기화의 지연 기간 동안 저장소가 초기화되면 이전 함수 호출이 취소되고 현재 초기화에 대해 함수가 다시 호출됩니다.
* 후속 초기화가 발생하기 전에 지연 기간이 경과하면 콜백 함수가 두 번 실행됩니다.

예를 들어 세션 저장소는 JSON 개체를 기반으로 하며 JSON 요청을 통해 검색됩니다. 다음과 같은 초기화 시나리오가 가능합니다.

* 요청이 완료되고 데이터가 검색되고 저장소에 로드됩니다. 이 경우 초기화는 한 번 발생합니다.
* 요청이 실패합니다(시간 제한). 이 경우 초기화가 발생하지 않고 저장소에 데이터가 없습니다.
* 이 저장소는 기본값(init 속성)으로 미리 채워지지만 요청이 실패합니다(시간 초과). 초기화는 기본값이 있는 하나만 있습니다.
* 그 가게는 미리 채워져 있다.

지연이 로 설정된 경우 `true` 또는 메서드가 콜백 메서드를 호출하기 전에 대기하는 시간(밀리초)입니다. 지연이 전달되기 전에 다른 초기화 이벤트가 트리거되는 경우 초기화 이벤트 없이 지연 시간이 초과될 때까지 대기합니다. 이렇게 하면 두 번째 초기화 이벤트가 트리거될 때까지 기다렸다가 가장 적합한 경우에서 콜백 함수를 호출할 수 있습니다.

**매개변수**

* storeName: 문자열. 리스너를 추가할 세션 저장소의 이름입니다.
* 콜백: 함수 위에 있어야 합니다. 저장소 초기화 시 호출할 함수입니다.
* 지연: 부울 또는 숫자입니다. 콜백 함수 호출을 지연하는 시간(밀리초)입니다. 부울 값 `true` 의 기본 지연 시간을 사용합니다. `200 ms`. 부울 값 `false` 또는 음수로 인해 지연이 사용되지 않습니다.

**반환**

반환된 값이 없습니다.

#### onStoreRegistered(storeName, callback) {#onstoreregistered-storename-callback}

세션 저장소가 등록될 때 호출되는 콜백 함수를 등록합니다. 등록 이벤트는 스토어가 [CQ_Analytics.ClientContextMgr](#cq-analytics-clientcontextmgr).

**매개변수**

* storeName: 문자열. 리스너를 추가할 세션 저장소의 이름입니다.
* 콜백: 함수 위에 있어야 합니다. 저장소 초기화 시 호출할 함수입니다.

**반환**

반환된 값이 없습니다.

## CQ_Analytics.JSONPStore {#cq-analytics-jsonpstore}

JSON 데이터를 포함하는 비지속적인 세션 저장소. 외부 JSONP 서비스에서 데이터를 검색합니다. 를 사용하십시오 `getInstance` 또는 `getRegisteredInstance` 이 클래스의 인스턴스를 만드는 메서드입니다.

CQ_Analytics.JSONStore를 확장합니다.

### 속성 {#properties}

상속된 속성에 대해서는 CQ_Analytics.JSONStore 및 CQ_Analytics.SessionStore 를 참조하십시오.

### 메서드 {#methods-2}

상속된 메서드는 CQ_Analytics.JSONStore 및 CQ_Analytics.SessionStore를 참조하십시오.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback}

CQ_Analytics.JSONPStore 개체를 만듭니다.

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다. storeName을 제공하지 않으면 이 메서드는 null을 반환합니다.
* serviceURL: 문자열. JSONP 서비스의 URL입니다
* dynamicData: (선택 사항) 객체. 콜백 함수가 호출되기 전에 저장소의 초기화 데이터에 추가할 JSON 데이터입니다.
* deferLoading: (선택 사항) 부울. true 값을 지정하면 개체를 만들 때 JSONP 서비스가 호출되지 않습니다. false 값을 지정하면 JSONP 서비스가 호출됩니다.
* loadingCallback: (선택 사항) 문자열입니다. JSONP 서비스가 반환하는 JSONP 개체 처리를 위해 호출할 함수의 이름입니다. 콜백 함수는 CQ_Analytics.JSONPStore 객체인 단일 매개 변수를 정의해야 합니다.

**반환**

새 CQ_Analytics.JSONPStore 개체 또는 storeName이 null이면 null입니다.

#### getServiceURL() {#getserviceurl}

이 개체가 JSON 데이터를 검색하는 데 사용하는 JSONP 서비스의 URL을 검색합니다.

**매개변수**

없음.

**반환**

서비스 URL을 나타내는 문자열이거나, 서비스 URL이 구성되지 않은 경우 null입니다.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback}

JSONP 서비스를 호출합니다. JSONP URL은 지정된 콜백 함수 이름이 있는 서비스 URL입니다.

**매개변수**

* serviceURL: (선택 사항) 문자열입니다. 호출할 JSONP 서비스입니다. null 값을 지정하면 이미 구성된 서비스 URL이 사용됩니다. null이 아닌 값은 이 개체에 사용할 JSONP 서비스를 설정합니다. (setServiceURL을 참조하십시오.)
* dynamicData: (선택 사항) 객체. 콜백 함수가 호출되기 전에 저장소의 초기화 데이터에 추가할 JSON 데이터입니다.
* 콜백: (선택 사항) 문자열입니다. JSONP 서비스가 반환하는 JSONP 개체 처리를 위해 호출할 함수의 이름입니다. 콜백 함수는 CQ_Analytics.JSONPStore 객체인 단일 매개 변수를 정의해야 합니다.

**반환**

반환된 값이 없습니다.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback}

CQ_Analytics.JSONPStore 개체를 만들고 Client Context에 스토어를 등록합니다.

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다. storeName을 제공하지 않으면 이 메서드는 null을 반환합니다.
* serviceURL: (선택 사항) 문자열입니다. JSONP 서비스의 URL입니다.
* dynamicData: (선택 사항) 객체. 콜백 함수가 호출되기 전에 저장소의 초기화 데이터에 추가할 JSON 데이터입니다.
* 콜백: (선택 사항) 문자열입니다. JSONP 서비스가 반환하는 JSONP 개체 처리를 위해 호출할 함수의 이름입니다. 콜백 함수는 CQ_Analytics.JSONPStore 객체인 단일 매개 변수를 정의해야 합니다.

**반환**

등록된 CQ_Analytics.JSONPStore 개체입니다.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl}

JSON 데이터 검색에 사용할 JSONP 서비스의 URL을 설정합니다.

**매개변수**

* serviceURL: 문자열. JSON 데이터를 제공하는 JSONP 서비스의 URL입니다

**반환**

반환된 값이 없습니다.

## CQ_Analytics.JSONStore {#cq-analytics-jsonstore}

JSON 개체의 컨테이너입니다. JSON 데이터를 포함하는 지속되지 않은 세션 저장소를 만들려면 이 클래스의 인스턴스를 만듭니다.

`myjsonstore = new CQ_Analytics.JSONStore`

초기화 시 저장소를 채우는 데이터 세트를 정의할 수 있습니다.

CQ_Analytics.SessionStore를 확장합니다.

### 속성 {#properties-1}

#### STORKEY {#storekey}

저장소를 식별하는 키입니다. 를 사용하십시오 `getInstance` 이 값을 검색하는 메서드입니다.

#### STORNAME {#storename}

저장소의 이름입니다. 를 사용하십시오 `getInstance` 이 값을 검색하는 메서드입니다.

### 메서드 {#methods-3}

상속된 메서드는 CQ_Analytics.SessionStore도 참조하십시오.

#### 지우기() {#clear}

세션 저장소 데이터를 제거하고 모든 초기화 속성을 제거합니다.

**매개변수**

없음.

**반환**

반환된 값이 없습니다.

#### getInstance(storeName, jsonData) {#getinstance-storename-jsondata}

지정된 이름으로 CQ_Analytics.JSONStore 개체를 만들고 지정된 JSON 데이터로 초기화합니다(initJSON 메서드 호출).

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다.
* jsonData: 개체. JSON 데이터를 포함하는 객체입니다.

**반환**

CQ_Analytics.JSONStore 개체.

#### getJSON() {#getjson}

세션 저장소의 데이터를 JSON 형식으로 검색합니다.

**매개변수**

없음.

**반환**

JSON 형식으로 저장소 데이터를 나타내는 객체입니다.

#### init() {#init}

세션 저장소를 지우고 초기화 속성으로 초기화합니다. 초기화 플래그를 로 설정합니다. `true` 그런 다음 `initialize` 및 `update` events.

**매개변수**

없음.

**반환**

반환된 데이터가 없습니다.

#### initJSON(jsonData, doNotClear) {#initjson-jsondata-donotclear}

JSON 개체의 데이터에서 초기화 속성을 만듭니다. 모든 기존 초기화 속성을 선택적으로 제거할 수 있습니다.

속성 이름은 JSON 개체에 있는 데이터의 계층에서 파생됩니다. 다음 예제 코드는 JSON 개체를 나타냅니다.

```xml
{
A: "valueA",  
B: {
     B1: "valueBB1"
    }
}
```

이 예에서는 저장소에 다음 속성이 만들어집니다.

```xml
A: "valueA" 
B/B1: "valueBB1"
```

**매개변수**

* jsonData: 저장할 데이터를 포함하는 JSON 개체입니다.
* doNotClear: true 값을 지정하면 기존 초기화 속성이 유지되고 JSON 객체에서 파생된 속성이 추가됩니다. false 값은 JSON 개체에서 파생된 초기화 속성을 추가하기 전에 기존 초기화 속성을 제거합니다.

**반환**

반환된 값이 없습니다.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata}

지정된 이름으로 CQ_Analytics.JSONStore 개체를 만들고 지정된 JSON 데이터로 초기화합니다(initJSON 메서드 호출). 새 개체는 Clickstream Cloud Manager에 자동으로 등록됩니다.

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다.
* jsonData: 개체. JSON 데이터를 포함하는 객체입니다.

**반환**

CQ_Analytics.JSONStore 개체.

## CQ_Analytics.Observable {#cq-analytics-observable}

이벤트를 실행하고 다른 개체가 이러한 이벤트를 수신하고 응답할 수 있도록 합니다. 이 클래스를 확장하는 클래스는 리스너를 호출하는 이벤트를 실행할 수 있습니다.

### 메서드 {#methods-4}

#### addListener(event, fct, scope) {#addlistener-event-fct-scope}

이벤트에 대한 리스너를 등록합니다. 참조 - [세션 저장소 업데이트에 응답할 리스너 생성](/help/sites-developing/client-context.md#creating-a-listener-to-react-to-a-session-store-update).

**매개변수**

* 이벤트: 문자열. 수신할 이벤트의 이름입니다.
* fct: 함수 위에 있어야 합니다. 이벤트가 발생할 때 호출되는 함수입니다.
* 범위: (선택 사항) 객체. 처리기 함수를 실행할 범위입니다. 처리기 함수의 &quot;this&quot; 컨텍스트입니다.

**반환**

반환된 값이 없습니다.

#### removeListener(event, fct) {#removelistener-event-fct}

이벤트에 대해 지정된 이벤트 처리기를 제거합니다.

**매개변수**

* 이벤트: 문자열. 이벤트의 이름입니다.
* fct: 함수 위에 있어야 합니다. 이벤트 처리기입니다.

**반환**

반환된 값이 없습니다.

## CQ_Analytics.PersistedJSONPStore {#cq-analyics-persistedjsonpstore}

원격 JSONP 서비스에서 검색한 JSON 개체의 지속된 컨테이너입니다.

CQ_Analytics.PersistentJSONStore를 확장합니다.

### 메서드 {#methods-5}

상속된 메서드는 CQ_Analytics.PersistentJSONStore 를 참조하십시오.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback-1}

CQ_Analytics.PersistentJSONPStore 개체를 만듭니다.

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다. storeName을 제공하지 않으면 이 메서드는 null을 반환합니다.
* serviceURL: 문자열. JSONP 서비스의 URL입니다
* dynamicData: (선택 사항) 객체. 콜백 함수가 호출되기 전에 저장소의 초기화 데이터에 추가할 JSON 데이터입니다.
* deferLoading: (선택 사항) 부울. true 값을 지정하면 개체를 만들 때 JSONP 서비스가 호출되지 않습니다. false 값을 지정하면 JSONP 서비스가 호출됩니다.
* loadingCallback: (선택 사항) 문자열입니다. JSONP 서비스가 반환하는 JSONP 개체 처리를 위해 호출할 함수의 이름입니다. 콜백 함수는 CQ_Analytics.JSONPStore 객체인 단일 매개 변수를 정의해야 합니다.

**반환**

새 CQ_Analytics.PersistedJSONPStore 개체를 만들거나 storeName이 null인 경우 null입니다.

#### getServiceURL() {#getserviceurl-1}

이 개체가 JSON 데이터를 검색하는 데 사용하는 JSONP 서비스의 URL을 검색합니다.

**매개변수**

없음.

**반환**

서비스 URL을 나타내는 문자열이거나, 서비스 URL이 구성되지 않은 경우 null입니다.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback-1}

JSONP 서비스를 호출합니다. JSONP URL은 지정된 콜백 함수 이름이 있는 서비스 URL입니다.

**매개변수**

* serviceURL: (선택 사항) 문자열입니다. 호출할 JSONP 서비스입니다. null 값을 지정하면 이미 구성된 서비스 URL이 사용됩니다. null이 아닌 값은 이 개체에 사용할 JSONP 서비스를 설정합니다. (setServiceURL을 참조하십시오.)
* dynamicData: (선택 사항) 객체. 콜백 함수가 호출되기 전에 저장소의 초기화 데이터에 추가할 JSON 데이터입니다.
* 콜백: (선택 사항) 문자열입니다. JSONP 서비스가 반환하는 JSONP 개체 처리를 위해 호출할 함수의 이름입니다. 콜백 함수는 CQ_Analytics.JSONPStore 객체인 단일 매개 변수를 정의해야 합니다.

**반환**

반환된 값이 없습니다.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback-1}

CQ_Analytics.PersistentJSONPStore 개체를 만들고 Client Context에 스토어를 등록합니다.

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다. storeName을 제공하지 않으면 이 메서드는 null을 반환합니다.
* serviceURL: (선택 사항) 문자열입니다. JSONP 서비스의 URL입니다.
* dynamicData: (선택 사항) 객체. 콜백 함수가 호출되기 전에 저장소의 초기화 데이터에 추가할 JSON 데이터입니다.
* 콜백: (선택 사항) 문자열입니다. JSONP 서비스가 반환하는 JSONP 개체 처리를 위해 호출할 함수의 이름입니다. 콜백 함수는 CQ_Analytics.JSONPStore 객체인 단일 매개 변수를 정의해야 합니다.

**반환**

등록된 CQ_Analytics.PersistentJSONPStore 개체입니다.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl-1}

JSON 데이터 검색에 사용할 JSONP 서비스의 URL을 설정합니다.

**매개변수**

* serviceURL: 문자열. JSON 데이터를 제공하는 JSONP 서비스의 URL입니다

**반환**

반환된 값이 없습니다.

## CQ_Analytics.PersistentJSONStore {#cq-analytics-persistedjsonstore}

JSON 개체의 지속된 컨테이너입니다.

확장 `CQ_Analytics.PersistedSessionStore`.

### 속성 {#properties-2}

#### STORKEY {#storekey-1}

저장소를 식별하는 키입니다. 를 사용하십시오 `getInstance` 이 값을 검색하는 메서드입니다.

#### STORNAME {#storename-1}

저장소의 이름입니다. 를 사용하십시오 `getInstance` 이 값을 검색하는 메서드입니다.

### 메서드 {#methods-6}

상속된 메서드는 CQ_Analytics.PersistentSessionStore도 참조하십시오.

#### getInstance(storeName, jsonData) {#getinstance-storename-jsondata-1}

지정된 이름으로 CQ_Analytics.PersistentJSONtore 개체를 만들고 지정된 JSON 데이터로 초기화합니다(initJSON 메서드 호출).

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다.
* jsonData: 개체. JSON 데이터를 포함하는 객체입니다.

**반환**

CQ_Analytics.PersistentJSONStore 개체.

#### getJSON() {#getjson-1}

세션 저장소의 데이터를 JSON 형식으로 검색합니다.

**매개변수**

없음.

**반환**

JSON 형식으로 저장소 데이터를 나타내는 객체입니다.

#### initJSON(jsonData, doNotClear) {#initjson-jsondata-donotclear-1}

JSON 개체의 데이터에서 초기화 속성을 만듭니다. 모든 기존 초기화 속성을 선택적으로 제거할 수 있습니다.

속성 이름은 JSON 개체에 있는 데이터의 계층에서 파생됩니다. 다음 예제 코드는 JSON 개체를 나타냅니다.

```xml
{
A: "valueA",  
B: {
     B1: "valueBB1"
    }
}
```

이 예에서는 저장소에 다음 속성이 만들어집니다.

```xml
A: "valueA" 
B/B1: "valueBB1"
```

**매개변수**

* jsonData: 저장할 데이터를 포함하는 JSON 개체입니다.
* doNotClear: true 값을 지정하면 기존 초기화 속성이 유지되고 JSON 객체에서 파생된 속성이 추가됩니다. false 값은 JSON 개체에서 파생된 초기화 속성을 추가하기 전에 기존 초기화 속성을 제거합니다.

**반환**

반환된 값이 없습니다.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata-1}

지정된 이름으로 CQ_Analytics.PersistentJSONtore 개체를 만들고 지정된 JSON 데이터로 초기화합니다(initJSON 메서드 호출). 새 객체는 Client Context Manager에 자동으로 등록됩니다.

**매개변수**

* storeName: 문자열. STORENAME 속성으로 사용할 이름입니다. STOREKEY 속성 값은 모든 대문자가 있는 storeName으로 설정됩니다.
* jsonData: 개체. JSON 데이터를 포함하는 객체입니다.

**반환**

CQ_Analytics.PersistentJSONStore 개체.

## CQ_Analytics.PersistedSessionStore {#cq-analytics-persistedsessionstore}

속성 및 값의 컨테이너입니다. 데이터는 CQ_Analytics.SessionPersistence를 사용하여 유지됩니다. 이 클래스의 인스턴스를 만들어 지속형 세션 저장소를 만듭니다.

`mypersistedstore = new CQ_Analytics.PersistedSessionStore`

CQ_Analytics.SessionStore를 확장합니다.

### 속성 {#properties-3}

#### STORKEY {#storekey-2}

기본값은 입니다. `key`.

### 메서드 {#methods-7}

상속된 메서드는 CQ_Analytics.SessionStore 를 참조하십시오.

상속된 메서드가 `clear`, `setProperty`, `setProperties`, `removeProperty` 저장소 데이터를 변경하는 데 사용됩니다. 변경된 속성이 notPersistent로 플래그가 지정되지 않는 한 변경 내용은 자동으로 유지됩니다.

#### getStoreKey() {#getstorekey}

를 검색합니다. `STOREKEY` 속성을 사용합니다.

**매개변수**

없음

**반환**

의 값 `STOREKEY` 속성을 사용합니다.

#### isPersistent(name) {#ispersisted-name}

데이터 속성이 지속되는지 여부를 결정합니다.

**매개변수**

* 이름: 문자열. 속성의 이름입니다.

**반환**

부울 값 `true` 속성이 유지되면 값 `false` 값이 지속된 속성이 아닌 경우.

#### persist() {#persist}

세션 저장소를 유지합니다. 기본 지속성 모드는 브라우저를 사용합니다 `localStorage` 사용 `ClientSidePersistence` 로서의( `window.localStorage.set("ClientSidePersistance", store);`)

localStorage를 사용할 수 없거나 쓸 수 없는 경우 저장소가 창의 속성으로 유지됩니다.

를 실행합니다. `persist` 완료 시 이벤트.

**매개변수**

없음

**반환**

반환된 값이 없습니다.

#### reset(deferEvent) {#reset-deferevent}

저장소에서 모든 데이터 속성을 제거하고 저장소를 유지합니다. 선택적으로 를 실행하지 않습니다 `udpate` 완료 시 이벤트.

**매개변수**

* deferEvent: true 값을 지정하면 `update` 이벤트가 실행되지 않았습니다. 값 `false` 업데이트 이벤트가 실행되도록 합니다.

**반환**

반환된 값이 없습니다.

#### setNonPersisted(name) {#setnonpersisted-name}

데이터 속성을 지속되지 않은 것으로 플래그를 지정합니다.

**매개변수**

* 이름: 문자열. 지속되지 않는 속성의 이름입니다.

**반환**

반환 값이 없습니다.

## CQ_Analytics.SessionStore {#cq-analytics-sessionstore}

CQ_Analytics.SessionStore는 세션 저장소를 나타냅니다. 이 클래스의 인스턴스를 만들어 세션 저장소를 만듭니다.

`mystore = new CQ_Analytics.SessionStore`

CQ_Analytics.Observable을 확장합니다.

### 속성 {#properties-4}

#### STORNAME {#storename-2}

세션 저장소의 이름입니다. 이 속성의 값을 검색하려면 getName을 사용하십시오.

### 메서드 {#methods-8}

#### addInitProperty(name, value) {#addinitproperty-name-value}

세션 저장소 초기화 데이터에 속성 및 값을 추가합니다.

loadInitProperties를 사용하여 세션 저장소 데이터를 초기화 값으로 채웁니다.

**매개변수**

* 이름: 문자열. 추가할 속성의 이름입니다.
* 값: 문자열. 추가할 속성의 값입니다.

**반환**

반환된 값이 없습니다.

#### 지우기() {#clear-1}

저장소에서 모든 데이터 속성을 제거합니다.

**매개변수**

없음.

**반환**

반환 값이 없습니다.

#### getData(excluded) {#getdata-excluded}

저장소 데이터를 반환합니다. 선택적으로, 데이터에서 이름 속성을 제외합니다. 호출 `init` 저장소의 데이터 속성이 없는 경우 메서드를 사용합니다.

**매개변수**

제외: (선택 사항) 반환된 데이터에서 제외할 속성 이름의 배열입니다.

**반환**

속성 및 해당 값의 객체입니다.

#### getInitProperty(name) {#getinitproperty-name}

데이터 속성의 값을 검색합니다.

**매개변수**

* 이름: 문자열. 검색할 데이터 속성의 이름입니다.

**반환**

데이터 속성의 값입니다. 반환 `null` 세션 저장소에 지정된 이름의 속성이 없는 경우

#### getName() {#getname}

세션 저장소의 이름을 반환합니다.

**매개변수**

없음.

**반환**

저장소 이름을 나타내는 문자열 값입니다.

#### getProperty(name, raw) {#getproperty-name-raw}

속성 값을 반환합니다. 값은 원시 속성 또는 XSS 필터링된 값으로 반환됩니다. 호출 `init` 저장소의 데이터 속성이 없는 경우 메서드를 사용합니다.

**매개변수**

* 이름: 문자열. 검색할 데이터 속성의 이름입니다.
* 원시: 부울. true 값을 지정하면 원시 속성 값이 반환됩니다. false 값을 지정하면 반환된 값이 XSS 필터링됩니다.

**반환**

데이터 속성의 값입니다.

#### getPropertyNames(excluded) {#getpropertynames-excluded}

세션 저장소에 포함된 속성의 이름을 반환합니다. 호출 `init` 저장소의 데이터 속성이 없는 경우 메서드를 사용합니다.

**매개변수**

제외: (선택 사항) 결과에서 생략할 속성 이름의 배열입니다.

**반환**

세션 속성 이름을 나타내는 문자열 값의 배열입니다.

#### getSessionStore() {#getsessionstore}

현재 개체에 연결된 세션 저장소를 반환합니다.

**매개변수**

없음.

**반환**

이

#### init() {#init-1}

스토어를 초기화된 것으로 표시하고 `initialize` 이벤트.

**매개변수**

없음.

**반환**

반환된 값이 없습니다.

#### isInitialized() {#isinitialized}

세션 저장소가 초기화되었는지 여부를 나타냅니다.

**매개변수**

없음.

**반환**

값 `true` 저장소가 초기화된 경우 값 `false` 저장소가 초기화되지 않은 경우

#### loadInitProperties(obj, setValues) {#loadinitproperties-obj-setvalues}

지정된 개체의 속성을 세션 저장소의 초기화 데이터에 추가합니다. 선택적으로 개체 데이터는 저장소 데이터에도 추가됩니다.

**매개변수**

* 개체: 열거할 수 있는 속성을 포함하는 객체입니다.
* setValues: true일 경우 저장소 데이터에 이미 동일한 이름의 속성이 포함되어 있지 않은 경우 obj 속성이 세션 저장소 데이터에 추가됩니다. false이면 세션 저장소 데이터에 데이터가 추가되지 않습니다.

**반환**

반환된 값이 없습니다.

#### removeProperty(name) {#removeproperty-name}

세션 저장소에서 속성을 제거합니다. 를 실행합니다. `update` 완료 시 이벤트. 호출 `init` 저장소의 데이터 속성이 없는 경우 메서드를 사용합니다.

**매개변수**

* 이름: 문자열. 제거할 속성의 이름입니다.

**반환**

반환된 값이 없습니다.

#### 재설정() {#reset}

데이터 저장소의 초기 값을 복원합니다. 기본 구현은 모든 데이터를 제거합니다. 를 실행합니다. `update` 완료 시 이벤트.

**매개변수**

없음.

**반환**

반환된 값이 없습니다.

#### setProperties(properties) {#setproperties-properties}

여러 속성의 값을 설정합니다. 를 실행합니다. `update` 완료 시 이벤트. 호출 `init` 저장소의 데이터 속성이 없는 경우 메서드를 사용합니다.

**매개변수**

* 속성: 개체. 열거할 수 있는 속성을 포함하는 객체입니다. 각 속성 이름 및 값이 저장소에 추가됩니다.

**반환**

반환된 값이 없습니다.

#### setProperty(name, value) {#setproperty-name-value}

속성 값을 설정합니다. 를 실행합니다. `update` 완료 시 이벤트. 호출 `init` 저장소의 데이터 속성이 없는 경우 메서드를 사용합니다.

**매개변수**

* 이름: 문자열. 속성의 이름입니다.
* 값: 문자열. 속성 값.

**반환**

반환된 값이 없습니다.
