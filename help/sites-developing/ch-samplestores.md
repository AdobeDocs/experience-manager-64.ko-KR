---
title: 샘플 ContextHub 저장소 후보
seo-title: 샘플 ContextHub 저장소 후보
description: ContextHub는 솔루션에서 사용할 수 있는 몇 가지 샘플 저장소 후보자를 제공합니다
seo-description: ContextHub는 솔루션에서 사용할 수 있는 몇 가지 샘플 저장소 후보자를 제공합니다
uuid: feccd813-6077-4e87-a96e-d451114e5527
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 7f813b59-d904-49b6-994c-be3badf74464
exl-id: 776ceb9f-f835-4dbb-9100-f456a36b6dcd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 3%

---

# 샘플 ContextHub 저장소 후보{#sample-contexthub-store-candidates}

ContextHub는 솔루션에서 사용할 수 있는 몇 가지 샘플 저장소 후보자를 제공합니다. 각 샘플에 대해 다음 정보가 제공됩니다.

* 학습 목적으로 열 수 있도록 소스 코드를 찾을 위치.
* 스토어 후보로부터 만든 스토어를 구성하는 방법입니다.
* 액세스할 수 있도록 저장소 데이터를 구성하는 방법입니다.

>[!WARNING]
>
>샘플 저장소 후보들은 프로젝트에 대한 자체 전용 구성을 구축하는 데 도움이 되는 참조 구성으로 제공되며, 이러한 구성은 직접 사용하지 않아야 합니다.

## aem.segmentation 샘플 저장소 후보 {#aem-segmentation-sample-store-candidate}

해결된 및 해결되지 않은 ContextHub 세그먼트를 저장합니다. ContextHub 세그먼트 관리자에서 세그먼트를 자동으로 검색합니다.

### 소스 위치 {#source-location-segmentation}

`/libs/settings/cloudsettings/legacy/contexthub/segmentation`

### 기본 구현 {#base-implementation-segmentation}

aem.segmentation store 후보는 [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)을 확장합니다.

### 구성 {#configuration-segmentation}

aem.segmentation 저장소를 만들 때 세부 구성을 제공할 필요가 없습니다. 기본 구성은 ContextHub 세그먼트 정의의 위치를 지정합니다.

```xml
{
   "service":{
      "jsonp":false,
      "timeout":1000,
      "path":"/etc/segmentation/contexthub.segment.js"
   }
}
```

## contexthub.geolocation 샘플 저장소 후보 {#contexthub-geolocation-sample-store-candidate}

contexthub.geolocation 샘플 저장소 후보 는 Google Map을 사용하여 클라이언트 위치에 대한 정보를 가져와 저장합니다.

### 소스 위치 {#source-location-geolocation}

`/libs/settings/cloudsettings/legacy/contexthub/geolocation`

### 기본 구현 {#base-implementation-geolocation}

contexthub.geolocation 저장소 후보가 [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)을 확장합니다.

### 구성 {#configuration-geolocation}

기본 구성은 Google 서비스에 대한 정보와 초기 위도 및 경도 좌표에 대한 정보를 지정합니다.

```xml
{
        "service": {
            "jsonp": false,
            "timeout": 1000,
            "ttl": 1800000,
            "secure": false,
            "host": "maps.googleapis.com",
            "port": 80,
            "path": "/maps/api/geocode/json"
        },

        "eventDeferring": 16,

        "html5coordinatesDiscoveryAPI": {
            "timeout": 30000,
            "ttl": 900000,
            "highAccuracy": false
        },

        "initialValues": {
            "latitude": 37.331375,
            "longitude": -121.893992
        }
    }
```

### 데이터 항목 {#data-items-geolocation}

저장소는 다음 예와 유사한 데이터 트리를 사용합니다.

```xml
{
   "latitude":"37.331375",
   "longitude":"-121.893992"
}
```

>[!NOTE]
>
>Chrome 50.x에 도입된 보안 정책을 사용하려면 모든 지리적 위치 관련 호출이 보안 연결을 통해 수행되어야 합니다. 따라서 AEM이 https를 통해 실행 중인 경우 AEM에서는 지리적 위치 API 호출에 https 사용을 강제 적용합니다. 그렇지 않으면 동일한 원본 정책을 준수하기 위해 http를 사용합니다. Chrome의 변경 사항에 대한 자세한 내용은 [이 Google 블로그 게시물](https://developers.google.com/web/updates/2016/04/geolocation-on-secure-contexts-only)을 참조하십시오.

## contexthub.surferinfo 샘플 저장소 후보 {#contexthub-surferinfo-sample-store-candidate}

장치, 창, 브라우저, 날짜 및 시간과 같은 현재 클라이언트 환경에 대한 정보를 저장합니다.

### 소스 위치 {#source-location-surferinfo}

`/libs/settings/cloudsettings/legacy/contexthub/surferinfo`

### 기본 구현 {#base-implementation-surferinfo}

contexthub.datetime 저장소 후보가 [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)을(를) 확장합니다.

### 구성 {#configuration-surferinfo}

기본 구성은 `ContextHub.Store.PersistedStore`에서 상속됩니다.

### 데이터 항목 {#data-items-surferinfo}

이 저장소 후보자를 사용하는 저장소는 다음 예와 유사한 데이터 트리를 갖습니다.

```xml
{
   "display":{
      "resolution":{
         "width":1440,
         "height":900
      },
      "devicePixelRatio":1,
      "colorDepth":24,
      "nrOfColors":16777216,
      "pixelsPerInch":96,
      "orientation":{
         "mode":"landscape",
         "direction":"normal"
      }
   },
   "window":{
      "dimension":{
         "width":1395,
         "height":652
      },
      "percentageUsage":0.7
   },
   "browser":{
      "version":"39.0",
      "family":"Firefox",
      "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:39.0) Gecko/20100101 Firefox/39.0"
   },
   "device":{
      "category":"Desktop",
      "type":"Desktop",
      "model":"PC",
      "version":""
   },
   "isMobile":true,
   "os":{
      "name":"Mac OS X",
      "version":"10"
   },
   "year":2015,
   "month":7,
   "day":22,
   "hour":14,
   "minutes":1
}
```

## granite.에뮬레이터 샘플 저장소 후보 {#granite-emulators-sample-store-candidate}

granite.에뮬레이터 샘플 저장소 후보 는 클라이언트 장치에 대한 정보를 저장합니다.

### 소스 위치 {#source-location-emulators}

`/libs/settings/cloudsettings/legacy/contexthub/emulators`

### 기본 구현 {#base-implementation-emulators}

contexthub.geolocation 저장소 후보가 [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)을 확장합니다.

### 구성 {#configuration-emulators}

기본 구성에는 다른 장치에 대한 정보를 포함하는 `defaultEmulators` 배열이 포함되어 있습니다. 저장소를 만들 때 다음 예제에 표시된 형식을 사용하여 필요에 따라 세부 구성 속성에 다른 장치 프로필을 제공합니다.

```xml
{
   "defaultEmulators":[
        {
            "id": "iphone-6",
            "title": "iPhone 6",
            "type": "mobile",
            "platform": "iOS",
            "platformVersion": "8.1.3",
            "width": 750,
            "height": 1334,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 2
        },
        {
            "id": "iphone-6-plus",
            "title": "iPhone 6 Plus",
            "type": "mobile",
            "platform": "iOS",
            "platformVersion": "8.1.3",
            "width": 1080,
            "height": 1920,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 3
        },
        {
            "id": "galaxy-s4",
            "title": "Samsung Galaxy S4",
            "type": "mobile",
            "platform": "Android",
            "platformVersion": "4.4.2 KitKat",
            "width": 1080,
            "height": 1920,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 3
        }
    ]
}
```

### 데이터 항목 {#data-items-emulators}

저장소 데이터 트리는 다음 예와 유사합니다.

```xml
{
   "devices":[
      {"id":"native",
      "title":"Native",
      "type":"screen",
      "width":1395,
      "height":374,
      "orientation":"Landscape",
      "platform":"Mac OS X",
      "platformVersion":"10",
      "canRotate":false
      },
      {"id":"ipad-3",
      "title":"iPad 3 / 4 / Air",
      "type":"tablet",
      "platform":"iOS",
      "platformVersion":"8.1.3",
      "width":1536,
      "height":2048,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":2
      },
      {"id":"iphone-6",
      "title":"iPhone 6",
      "type":"mobile",
      "platform":"iOS",
      "platformVersion":"8.1.3",
      "width":750,
      "height":1334,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":2
      },
      {"id":"galaxy-s4",
      "title":"Samsung Galaxy S4",
      "type":"mobile",
      "platform":"Android",
      "platformVersion":"4.4.2 KitKat",
      "width":1080,
      "height":1920,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":3
      }
   ],
   "currentDeviceId":"native",
   "orientations":[
      {"id":"landscape",
      "title":"Landscape"
      },
      {"id":"portrait",
       "title":"Portrait"
      }
   ],
   "currentDevice":{
      "id":"native",
      "title":"Native",
      "type":"screen",
      "width":1395,
      "height":374,
      "orientation":"Landscape",
      "platform":"Mac OS X",
      "platformVersion":"10",
      "canRotate":false
   }
}
```

## granite.profile Sample Store 후보 {#granite-profile-sample-store-candidate}

현재 사용자에 대한 정보를 저장합니다.

### 소스 위치 {#source-location-profile}

`/libs/settings/cloudsettings/legacy/contexthub/profile`

### 기본 구현 {#base-implementation-profile}

contexthub.datetime 저장소 후보가 [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)을(를) 확장합니다.

### 구성 {#configuration-profile}

다음 기본 구성이 사용됩니다. 이 구성을 변경하면 안 됩니다.

```xml
{
   "service":{
      "jsonp":false,
      "timeout":1000,
      "path":"${contexthub:/store/profile/path}.infinity.json"
   },
   "initialValues":{"path":"/home/users/a/anonymous"}
}
```

### 데이터 항목 {#data-items-profile}

이 저장소 후보자를 사용하는 저장소는 다음 예와 유사한 데이터 트리를 갖습니다.

```xml
{
   "displayName":"anonymous",
   "path":"/home/users/6/6zavE_DGre6Ad9Y5E0Ba",
   "avatar":"/etc/designs/default/images/social/avatar.png",
   "authorizableId":"anonymous"
}
```
