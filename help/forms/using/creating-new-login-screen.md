---
title: 새 로그인 화면 만들기
seo-title: Creating a new login screen
description: AEM Forms 작업 공간 또는 Forms Manager와 같은 LiveCycle 모듈의 로그인 페이지를 수정하는 방법
seo-description: How-to modify the login page of LiveCycle modules, for example of AEM Forms workspace or Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
exl-id: caa4f835-c353-49d5-b18c-4d0538c1136f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 5%

---

# 새 로그인 화면 만들기 {#creating-a-new-login-screen}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 로그인 화면을 사용하는 모든 AEM Forms 모듈의 로그인 화면을 수정할 수 있습니다. 예를 들어 수정 사항은 Forms Manager 및 AEM Forms 작업 공간의 로그인 화면에 모두 영향을 줍니다.

## 전제 조건 {#prerequisite}

1. 에 로그인합니다. `/lc/crx/de` 관리자 권한 사용.
1. 다음 작업을 수행합니다.

   1. 계층 구조를 복제합니다. 의 `/libs/livecycle/core/content` at `/apps/livecycle/core/content`. 동일한(노드/폴더) 속성 및 액세스 제어를 유지 관리합니다.
   1. 컨텐츠 폴더를 복사합니다. 변환 전: `/libs/livecycle/core` to `/apps/livecycle/core`.
   1. 다음 내용의 내용을 삭제합니다. `/apps/livecycle/core` 폴더를 입력합니다.

1. 다음 작업을 수행합니다.

   1. 계층 구조를 복제합니다. 의 `/libs/livecycle/core/components/login` at `/apps/livecycle/core/components/login`. 동일한(노드/폴더) 속성 및 액세스 제어를 유지 관리합니다.
   1. 구성 요소 폴더를 복사합니다. 변환 전: `/libs/livecycle/core` to `/apps/livecycle/core`.
   1. 폴더의 컨텐츠를 삭제합니다. `/apps/livecycle/core/components/login`.

## 새 로케일 추가 {#adding-a-new-locale}

1. 를 복사합니다. `i18n` 폴더:

   * 변환 전: `/libs/livecycle/core/components/login`
   * 끝 `/apps/livecycle/core/components/login`

1. 내의 모든 폴더 삭제 `i18n` 한 명 빼고 `en`.
1. 폴더에서 `en`, 다음 작업을 수행합니다.

   1. 지원하려는 로케일 이름으로 폴더 이름을 변경합니다. (예: `ar`)
   1. 속성 변경 `jcr:language` 값 `ar`( `ar` 폴더).

   >[!NOTE]
   >
   >로케일이 언어 국가 코드 조합인 경우, `ar-DZ`그런 다음 폴더 이름 및 속성 값을 로 변경합니다. `ar-DZ`.

1. 복사 `login.jsp`:

   * 변환 전: `/libs/livecycle/core/components/login`
   * 끝 `/apps/livecycle/core/components/login`

1. 다음에 대한 코드 조각을 수정합니다 `/apps/livecycle/core/components/login/login.jsp`:

   ***로케일은 언어 코드입니다***

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

   ***로케일은 언어 국가 코드입니다***

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

## 새 텍스트 추가 또는 기존 텍스트 수정 {#adding-new-text-or-modifying-existing-text}

1. 복사 `i18n` 폴더:

   * 변환 전: `/libs/livecycle/core/components/login`
   * 끝 `/apps/livecycle/core/components/login`

1. 이제 속성 값을 수정합니다 `sling:message` 텍스트를 변경할 노드(원하는 로케일 코드 폴더 아래)의 이름입니다. 번역은 다음 값에 언급된 키를 통해 수행됩니다. `sling:key` 노드의 속성입니다.
1. 새 키-값 쌍을 추가하려면 다음 작업을 수행합니다. 다음에 나오는 스크린샷의 예를 확인하십시오.

   1. 유형의 노드 만들기 `sling:MessageEntry`또는 모든 로케일 폴더 아래에서 기존 노드를 복사하고 이름을 변경합니다.
   1. 복사 `login.jsp` :

      * 변환 전: `/libs/livecycle/core/components/login`
      * 끝 `/apps/livecycle/core/components/login`
   1. 수정 `/apps/livecycle/core/components/login/login.jsp` 새로 추가된 텍스트를 통합하는 데 사용됩니다.

   ![캡처](assets/capture.png)

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

## 새 스타일 추가 또는 기존 스타일 수정 {#adding-new-style-or-modifying-existing-style}

1. 복사 `login` 노드:

   * 변환 전: `/libs/livecycle/core/content`
   * 끝 `/apps/livecycle/core/content`

1. 파일 삭제 `login.js` 및 `jquery-1.8.0.min.js`: 노드에서 `/apps/livecycle/core/content/login.`
1. CSS 파일에서 스타일을 수정합니다.
1. 새 스타일을 추가하려면 다음을 수행합니다.

   1. 에 새 스타일 추가 `/apps/livecycle/core/content/login/login.css`
   1. 복사 `login.jsp`

      * 변환 전: `/libs/livecycle/core/components/login`
      * 끝 `/apps/livecycle/core/components/login`
   1. 수정 `/apps/livecycle/core/components/login/login.jsp` 새로 추가한 스타일을 통합합니다.


1. 예:

   * 에 다음 내용을 추가합니다 `/apps/livecycle/core/content/login/login.css`.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * /apps/livecycle/core/components/login.jsp에서 다음 내용을 수정합니다.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>의 기존 이미지가 `/apps/livecycle/core/content/login` (복사 대상) `/libs/livecycle/core/content/login`)가 제거되고 CSS에서 해당 참조를 제거합니다.

## 새 이미지 추가 {#add-new-images}

1. 새 스타일을 추가하거나 기존 스타일(위에 문서화됨)을 수정하는 단계를 수행합니다.
1. 에서 새 이미지 추가 `/apps/livecycle/core/content/login`. 이미지를 추가하려면 다음을 수행하십시오.

   1. WebDAV 클라이언트를 설치합니다.
   1. 다음으로 이동 `/apps/livecycle/core/content/login` 폴더(webDAV 클라이언트 사용) 자세한 내용은 다음을 참조하십시오. [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. 새 이미지를 추가합니다.

1. 에 새 스타일 추가 `/apps/livecycle/core/content/login/login.css,` 에 추가된 새 이미지에 해당합니다. `/apps/livecycle/core/content/login`.
1. 에서 새 스타일 사용 `login.jsp` at `/apps/livecycle/core/components`.
1. 예:

   * 에 다음 내용을 추가합니다 `/apps/livecycle/core/content/login/login.css`

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * /apps/livecycle/core/components/login.jsp에서 다음 내용을 수정합니다.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
