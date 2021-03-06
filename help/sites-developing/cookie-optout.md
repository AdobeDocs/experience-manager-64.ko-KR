---
title: 쿠키 사용 구성
seo-title: 쿠키 사용 구성
description: AEM은 웹 페이지에서 쿠키가 사용되는 방식을 구성하고 제어할 수 있도록 해주는 서비스를 제공합니다
seo-description: AEM은 웹 페이지에서 쿠키가 사용되는 방식을 구성하고 제어할 수 있도록 해주는 서비스를 제공합니다
uuid: 10d95176-0a56-41f1-9d36-01dbdac757d4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 5773ec1a-f15b-462d-8f9f-54ee1d7ead44
exl-id: 7f604d89-c6ad-405d-98cd-80f057466e61
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# 쿠키 사용 구성{#configuring-cookie-usage}

AEM은 웹 페이지에서 쿠키가 사용되는 방식을 구성하고 제어할 수 있도록 해주는 서비스를 제공합니다.

* 구성 가능한 서버측 서비스는 사용할 수 있는 쿠키 목록을 유지합니다.
* Javascript API를 사용하면 Javascript 코드에서 쿠키가 사용될 수 있는지 확인할 수 있습니다.

이 기능을 사용하여 페이지가 쿠키 사용에 대한 사용자의 동의를 준수하도록 하십시오.

## 허용된 쿠키 구성 {#configuring-allowed-cookies}

Granite 옵트아웃 서비스 Adobe을 구성하여 웹 페이지에서 쿠키가 사용되는 방식을 지정합니다. 다음 표에서는 구성할 수 있는 속성에 대해 설명합니다.

서비스를 구성하려면 [웹 콘솔](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) 또는 [OSGi 구성을 저장소](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)에 추가할 수 있습니다. 다음 표에서는 두 방법 중 하나에 필요한 속성에 대해 설명합니다. OSGi 구성의 경우 서비스 PID는 `com.adobe.granite.optout`입니다.

| 속성 이름(웹 콘솔) | OSGi 속성 이름 | 설명 |
|---|---|---|
| 옵트아웃 쿠키 | optout.cookies | 사용자의 장치에 있을 때 사용자가 쿠키 사용에 동의하지 않았음을 나타내는 쿠키의 이름입니다. |
| 옵트아웃 HTTP 헤더 | optout.headers | 사용자가 쿠키 사용에 동의하지 않았음을 나타내는 HTTP 헤더의 이름입니다. |
| 허용 목록 쿠키 | optout.whitelist.cookies | 웹 사이트의 기능에 중요하며 사용자의 동의 없이 사용할 수 있는 쿠키 목록입니다. |

## 쿠키 사용 확인 {#validating-cookie-usage}

클라이언트측 Javascript를 사용하여 Granite 옵트아웃 서비스를 호출하여 Adobe을 사용할 수 있는지 확인합니다. Granite.OptOutUtil javascript 개체를 사용하여 다음 작업을 수행합니다.

* 사용자가 추적 목적으로 쿠키를 사용하는 것에 동의하지 않는다는 것을 나타내는 쿠키 이름 목록을 얻습니다.
* 사용할 수 있는 쿠키 목록을 가져옵니다.
* 웹 브라우저에 사용자가 추적을 위해 쿠키 사용에 동의하지 않음을 나타내는 쿠키가 포함되어 있는지 여부를 결정합니다.
* 특정 쿠키를 사용할 수 있는지 여부를 결정합니다.

granite.utils [클라이언트 라이브러리 폴더](/help/sites-developing/clientlibs.md#referencing-client-side-libraries)은 Granite.OptOutUtil 개체를 제공합니다. 페이지 헤드 JSP에 다음 코드를 추가하여 Javascript 라이브러리에 대한 링크를 포함합니다.

`<ui:includeClientLib categories="granite.utils" />`

예를 들어 다음 javascript 함수는 COOKIE_NAME 쿠키를 쓰기 전에 사용할 수 있는지 여부를 결정합니다.

```
function writeCookie(value){
   if (!Granite.OptOutUtil.maySetCookie("COOKIE_NAME")) 
      return;
   if (value) {
      value = encodeURIComponent(value);
      document.cookie = "COOKIE_NAME=" + value; 
   }
}
```

## Granite.OptOutUtil Javascript 개체 {#the-granite-optoututil-javascript-object}

Granite.OptOutUtil을 사용하면 쿠키 사용이 허용되는지 여부를 확인할 수 있습니다.

### getCookieNames() 함수 {#getcookienames-function}

쿠키의 이름을 반환하며 쿠키가 있을 때 사용자가 쿠키 사용에 동의하지 않았음을 나타냅니다.

**매개 변수**

없음.

**반환**

쿠키 이름의 배열입니다.

#### getWhitelistCookieNames() 함수 {#getwhitelistcookienames-function}

사용자의 동의에 관계없이 사용할 수 있는 쿠키의 이름을 반환합니다.

**매개 변수**

없음.

**반환**

쿠키 이름의 배열입니다.

#### isOptedOut() 함수 {#isoptedout-function}

사용자의 브라우저에 쿠키 사용에 대한 동의를 받지 않았음을 나타내는 쿠키가 포함되어 있는지 여부를 결정합니다.

**매개 변수**

없음.

**반환**

동의가 없음을 나타내는 쿠키가 발견되면 `true` 의 부울 값과, 쿠키가 동의하지 않음을 나타내는 경우 `false` 의 값입니다.

### maySetCookie(cookieName) 함수 {#maysetcookie-cookiename-function}

사용자의 브라우저에서 특정 쿠키를 사용할 수 있는지 여부를 결정합니다. 이 함수는 `getWhitelistCookieNames` 함수가 반환하는 목록에 해당 쿠키가 포함되어 있는지 여부를 확인하는 것과 함께 `isOptedOut` 함수를 사용하는 것과 같습니다.

**매개 변수**

* cookieName:문자열. 쿠키의 이름입니다.

**반환**

`cookieName` 를 사용할 수 있는 경우 `true` 의 부울 값을 사용하거나 `cookieName` 를 사용할 수 없는 경우 `false` 값을 지정하십시오.
