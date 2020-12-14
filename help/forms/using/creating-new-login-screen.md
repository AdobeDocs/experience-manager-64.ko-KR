---
title: 새 로그인 화면 만들기
seo-title: 새 로그인 화면 만들기
description: 'LiveCycle 모듈의 로그인 페이지를 수정하는 방법(예: AEM Forms 작업 영역 또는 Forms Manager).'
seo-description: 'LiveCycle 모듈의 로그인 페이지를 수정하는 방법(예: AEM Forms 작업 영역 또는 Forms Manager).'
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 4%

---


# 새 로그인 화면 {#creating-a-new-login-screen} 만들기

AEM Forms 로그인 화면을 사용하는 모든 AEM Forms 모듈의 로그인 화면을 수정할 수 있습니다. 예를 들어 수정 사항은 Forms Manager 및 AEM Forms 작업 영역의 로그인 화면에 영향을 줍니다.

## 전제 조건 {#prerequisite}

1. 관리자 권한으로 `/lc/crx/de`에 로그인합니다.
1. 다음 작업을 수행합니다.

   1. 계층 구조 복제:/ `/apps/livecycle/core/content`에 있는 `/libs/livecycle/core/content`. 동일한(노드/폴더) 속성과 액세스 제어를 유지 관리합니다.
   1. 콘텐트 폴더를 복사합니다.`/libs/livecycle/core`에서 `/apps/livecycle/core`까지.
   1. `/apps/livecycle/core` 폴더의 내용을 삭제합니다.

1. 다음 작업을 수행합니다.

   1. 계층 구조 복제:/ `/apps/livecycle/core/components/login`에 있는 `/libs/livecycle/core/components/login`. 동일한(노드/폴더) 속성과 액세스 제어를 유지 관리합니다.
   1. 구성 요소 폴더를 복사합니다.`/libs/livecycle/core`에서 `/apps/livecycle/core`까지.
   1. 폴더 내용을 삭제합니다.`/apps/livecycle/core/components/login`.

## 새 로케일 {#adding-a-new-locale} 추가

1. `i18n` 폴더를 복사합니다.

   * 변환 전: `/libs/livecycle/core/components/login`
   * 끝 `/apps/livecycle/core/components/login`

1. `i18n` 내의 모든 폴더를 삭제합니다(단, `en`).
1. `en` 폴더에서 다음 작업을 수행합니다.

   1. 폴더의 이름을 지원할 로케일 이름으로 변경합니다. 예, `ar`.
   1. 속성 `jcr:language` 값을 `ar`(`ar` 폴더의 경우)으로 변경합니다.

   >[!NOTE]
   >
   >로케일이 언어 국가 코드 조합인 경우, 예를 들어 `ar-DZ` 폴더 이름과 속성 값을 `ar-DZ`으로 변경합니다.

1. 복사 `login.jsp`:

   * 변환 전: `/libs/livecycle/core/components/login`
   * 끝 `/apps/livecycle/core/components/login`

1. `/apps/livecycle/core/components/login/login.jsp`에 대한 다음 코드 조각을 수정합니다.

   ***로케일은 언어 코드입니다.***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("ar")) {
               browserLocale = "ar";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***로케일은 언어 국가 코드입니다.***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
               browserLocale = "ar-DZ";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***기본 로케일을 변경하려면***

   ```
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)
   
   To
   
   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
   ```

## 새 텍스트 추가 또는 기존 텍스트 {#adding-new-text-or-modifying-existing-text} 수정

1. `i18n` 폴더 복사:

   * 변환 전: `/libs/livecycle/core/components/login`
   * 끝 `/apps/livecycle/core/components/login`

1. 이제 텍스트를 변경할 노드(원하는 로케일 코드 폴더 아래)의 속성 `sling:message` 값을 수정합니다. 변환은 노드의 `sling:key` 속성 값에 언급된 키를 통해 수행됩니다.
1. 새 키-값 쌍을 추가하려면 다음 작업을 수행하십시오. 다음에 나오는 스크린샷의 예를 확인하십시오.

   1. `sling:MessageEntry` 유형의 노드를 만들거나 기존 노드를 복사하고 모든 로케일 폴더 아래에 이름을 변경합니다.
   1. 복사 `login.jsp` :

      * 변환 전: `/libs/livecycle/core/components/login`
      * 끝 `/apps/livecycle/core/components/login`
   1. 새로 추가된 텍스트를 통합하려면 `/apps/livecycle/core/components/login/login.jsp`을(를) 수정합니다.

   ![capture](assets/capture.png)

   ```
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   
   To
   
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   ```

## 새 스타일 추가 또는 기존 스타일 {#adding-new-style-or-modifying-existing-style} 수정

1. `login` 노드 복사:

   * 변환 전: `/libs/livecycle/core/content`
   * 끝 `/apps/livecycle/core/content`

1. `/apps/livecycle/core/content/login.` 노드에서 `login.js` 및 `jquery-1.8.0.min.js` 파일을 삭제합니다.
1. CSS 파일에서 스타일을 수정합니다.
1. 새 스타일을 추가하려면:

   1. `/apps/livecycle/core/content/login/login.css`에 새 스타일 추가
   1. 복사 `login.jsp`

      * 변환 전: `/libs/livecycle/core/components/login`
      * 끝 `/apps/livecycle/core/components/login`
   1. 새로 추가된 스타일을 통합하려면 `/apps/livecycle/core/components/login/login.jsp`을(를) 수정합니다.


1. 예:

   * `/apps/livecycle/core/content/login/login.css`에 다음을 추가합니다.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * /apps/livecycle/core/components/login.jsp에서 다음을 수정합니다.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>`/apps/livecycle/core/content/login`(`/libs/livecycle/core/content/login`에서 복사)의 기존 이미지가 제거되면 CSS에서 해당 참조를 제거합니다.

## 새 이미지 추가 {#add-new-images}

1. 새 스타일 추가 또는 기존 스타일 수정(위에 문서됨)의 단계를 따릅니다.
1. `/apps/livecycle/core/content/login`에 새 이미지를 추가합니다. 이미지를 추가하려면:

   1. WebDAV 클라이언트를 설치합니다.
   1. webDAV 클라이언트를 사용하여 `/apps/livecycle/core/content/login` 폴더로 이동합니다. 자세한 내용은 다음을 참조하십시오.[https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. 새 이미지 추가

1. `/apps/livecycle/core/content/login`에 추가된 새 이미지에 해당하는 새 스타일을 `/apps/livecycle/core/content/login/login.css,`에 추가합니다.
1. `/apps/livecycle/core/components`의 `login.jsp`에 새 스타일을 사용합니다.
1. 예:

   * `/apps/livecycle/core/content/login/login.css`에 다음 추가

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * /apps/livecycle/core/components/login.jsp에서 다음을 수정합니다.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
