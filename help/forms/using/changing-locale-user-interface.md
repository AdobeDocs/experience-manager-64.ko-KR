---
title: AEM Forms 작업 공간 사용자 인터페이스의 로케일 변경
seo-title: AEM Forms 작업 공간 사용자 인터페이스의 로케일 변경
description: 인터페이스에서 텍스트, 축소된 카테고리, 큐 및 프로세스를 현지화하도록 AEM Forms 작업 공간을 수정하는 방법 및 날짜 선택기를 사용합니다.
seo-description: 인터페이스에서 텍스트, 축소된 카테고리, 큐 및 프로세스를 현지화하도록 AEM Forms 작업 공간을 수정하는 방법 및 날짜 선택기를 사용합니다.
uuid: f8e7d399-98d9-4655-b51f-0346a5713f06
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: e4ca8188-fb9a-44bf-8437-a98abaa7521a
exl-id: 9968f399-454b-4cb2-b6af-2c16428ca7b4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# AEM Forms 작업 공간 사용자 인터페이스 {#changing-the-locale-of-aem-forms-workspace-user-interface} 로케일 변경

AEM Forms workspace는 영어, 프랑스어, 독일어 및 일본어 지원을 즉시 제공합니다. 또한 AEM Forms 작업 공간 사용자 인터페이스를 다른 언어로 현지화하는 기능도 제공합니다.

AEM Forms 작업 공간 사용자 인터페이스를 원하는 언어로 현지화하려면:

* AEM Forms 작업 영역의 텍스트를 현지화합니다.
* 축소된 카테고리, 큐 및 프로세스를 현지화합니다.
* 날짜 선택기 현지화

위의 단계를 수행하기 전에 AEM Forms 작업 공간 사용자 지정을 위한 [일반 단계에 나열된 단계를 따라야 합니다](/help/forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>AEM Forms 작업 영역의 로그인 화면 언어를 변경하려면 [새 로그인 화면 만들기](/help/forms/using/creating-new-login-screen.md)를 참조하십시오.

## 텍스트 현지화 {#localizing-text}

다음 단계를 수행하여 언어 *New* 및 브라우저 로케일 코드 *nw*&#x200B;에 대한 지원을 추가합니다.

1. CRXDE Lite에 로그인합니다.

   CRXDE Lite의 기본 URL은 `https://[server]:[port]/lc/crx/de/index.jsp`입니다.

1. `apps/ws/locales` 위치로 이동하고 새 폴더 `nw.`를 만듭니다
1. `/apps/ws/locales/en-US` 위치에서 `translation.json` 파일을 `/apps/ws/locales/nw` 위치에 복사합니다.
1. `/apps/ws/locales/nw`(으)로 이동하고 편집할 `translation.json` 을 엽니다. translation.json 파일을 로케일별로 변경합니다.

   다음 예에는 영어 및 AEM Forms 작업 공간의 프랑스어 로케일에 대한 translation.json 파일이 포함되어 있습니다.

   ![translation_json_in_](assets/translation_json_in_en.png) ![entrsation_json_in_fr](assets/translation_json_in_fr.png)

## 축소된 카테고리, 큐 및 프로세스 현지화 {#localizing-collapsed-categories-queues-and-processes}

AEM Forms 작업 영역은 이미지를 사용하여 카테고리, 큐 및 프로세스의 헤더를 표시합니다. 이러한 헤더를 현지화하려면 개발 패키지가 필요합니다. 개발 패키지 만들기에 대한 자세한 내용은 [AEM Forms 작업 공간 코드 작성](introduction-customizing-html-workspace.md#building-html-workspace-code) 을 참조하십시오.

다음 단계에서는 현지화된 새 이미지 파일이 *Categories_nw.png*, *Queue_nw.png* 및 *Processes_nw.png*&#x200B;라고 가정합니다. 이미지의 권장 너비는 19px입니다.

>[!NOTE]
>
>브라우저의 브라우저 언어 로케일 코드를 찾으려면 열기 `https://[server]:[port]/lc/libs/ws/Locale.html`.

![collecting_panels_image](assets/collapsing_panels_image.png)

이미지를 현지화하려면 다음 단계를 수행하십시오.

1. WebDAV 클라이언트를 사용하여 */apps/ws/images* 폴더에 이미지 파일을 배치합니다.
1. */apps/ws/css*&#x200B;로 이동합니다. 편집할 *newStyle.css*&#x200B;를 열고 다음 항목을 추가합니다.

   ```
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. [작업 공간 사용자 지정](/help/forms/using/introduction-customizing-html-workspace.md) 문서에 나열된 모든 의미 변경 작업을 수행합니다.
1. *js/runtime/utility* 폴더로 이동하고 편집할* usersession.js* 파일을 엽니다.
1. 원래 코드 블록에 나열된 코드를 찾고 조건 *lang !== &#39;nw&#39;* 를 if 문에 추가합니다.

   ```
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## 날짜 선택기 현지화 {#localizing-date-picker}

*datepicker *API를 현지화하려면 개발 패키지가 필요합니다. 개발 패키지 만들기에 대한 자세한 내용은 [AEM Forms 작업 공간 코드 작성](introduction-customizing-html-workspace.md#building-html-workspace-code)을 참조하십시오.

1. [jQuery UI 패키지](https://jqueryui.com/download/all/)를 다운로드하고 추출하려면 *&lt;extracted jquery UI 패키지>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n으로 이동합니다.
1. 이제 로케일 코드의 jquery.ui.datepicker-nw.js 파일을 apps/ws/js/libs/jqueryui에 복사하고 파일에 로케일 특정 변경 작업을 수행합니다.
1. `apps/ws/js` 로 이동하고 편집할 `jquery.ui.datepicker-nw.js` 파일을 엽니다.
1. main.js 파일에서 `jquery.ui.datepicker-nw.js.` 파일에 대한 별칭을 만듭니다. `jquery.ui.datepicker-nw.js` 파일에 대한 별칭을 만드는 코드는 다음과 같습니다.

   ```
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. 별칭 `jqueryuidatepickernw`을 사용하여 datepicker를 사용하는 모든 파일에 `jquery.ui.datepicker-nw.js` 파일을 포함합니다. datepicker는 다음 파일에서 사용됩니다.

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   아래 샘플 코드는 jquery.ui.datepicker-nw.js 항목을 추가하는 방법을 보여 줍니다.

   ```
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. Datepicker API를 사용하는 모든 파일에서 기본 datepicker API 설정을 변경합니다. Datepicker API는 다음 파일에서 사용됩니다.

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   다음 코드를 변경하여 새 로케일을 추가합니다.

   ```
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

끝

```
if (locale === 'ja-JP') {
    $.datepicker.setDefaults($.datepicker.regional.ja);
} else if (locale === 'de-DE') {
    $.datepicker.setDefaults($.datepicker.regional.de);
} else if (locale === 'fr-FR') {
    $.datepicker.setDefaults($.datepicker.regional.fr);
} else if (locale === 'nw') {
    $.datepicker.setDefaults($.datepicker.regional.nw);
} else {
    $.datepicker.setDefaults($.datepicker.regional['']);
}
```
