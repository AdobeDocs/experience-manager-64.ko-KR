---
title: HTTP 토큰을 사용하여 SSO 인증을 수행하는 Flash Builder 응용 프로그램 만들기
seo-title: Creating Flash Builder applicationsthat perform SSO authentication using HTTP tokens
description: HTTP 토큰을 사용하여 SSO(Single Sign On) 인증을 수행하는 Flash Builder을 사용하여 클라이언트 응용 프로그램을 만듭니다. 한 번에 작업을 위한 사용자를 인증하고 해당 인증을 사용하여 여러 AEM Forms 작업을 수행합니다.
seo-description: Create a client application using Flash Builder that performs single-sign on (SSO) authentication using HTTP tokens. Authenticate a user for an operation once and use that authentication to perform multiple AEM Forms operations.
uuid: 273db00a-a665-4e52-88fa-4fca06d05f8c
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: coding
discoiquuid: 0ff30df7-b3ad-4c34-9644-87c689acc294
role: Developer
exl-id: e4e99b9d-3023-4b9b-9c93-be04c7a871ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---

# HTTP 토큰을 사용하여 SSO 인증을 수행하는 Flash Builder 응용 프로그램 만들기 {#creating-flash-builder-applicationsthat-perform-sso-authentication-using-http-tokens}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

HTTP 토큰을 사용하여 SSO(Single Sign On) 인증을 수행하는 Flash Builder을 사용하여 클라이언트 응용 프로그램을 만들 수 있습니다. 예를 들어 Flash Builder을 사용하여 웹 기반 응용 프로그램을 만든다고 가정합니다. 다음으로, 각 보기가 다른 AEM Forms 작업을 호출하는 애플리케이션에 서로 다른 보기가 있다고 가정합니다. 각 Forms 작업에 대해 사용자를 인증하는 대신 사용자가 한 번 인증할 수 있는 로그인 페이지를 만들 수 있습니다. 인증되면 사용자는 다시 인증하지 않고도 여러 작업을 호출할 수 있습니다. 예를 들어 사용자가 Workspace(또는 다른 Forms 애플리케이션)에 로그인한 경우 사용자를 다시 인증할 필요가 없습니다.

클라이언트 응용 프로그램에는 SSO 인증을 수행하는 데 필요한 응용 프로그램 로직이 포함되어 있지만 AEM Forms 사용자 관리에서는 실제 사용자 인증을 수행합니다. HTTP 토큰을 사용하여 사용자를 인증하기 위해 클라이언트 응용 프로그램은 Authentication Manager 서비스의 `authenticateWithHTTPToken` 작업. 사용자 관리에서는 HTTP 토큰을 사용하여 사용자를 인증할 수 있습니다. AEM Forms에 대한 후속 원격 또는 웹 서비스 호출의 경우 인증을 위해 자격 증명을 전달할 필요가 없습니다.

>[!NOTE]
>
>이 섹션을 읽기 전에 Remoting을 사용하여 AEM Forms을 호출하는 것에 익숙해지는 것이 좋습니다. (자세한 내용은 [AEM Forms Remoting을 사용하여 AEM Forms 호출](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting))

다음과 같은 AEM Forms 단기 프로세스가 이름이 지정됩니다. `MyApplication/EncryptDocument`사용자가 SSO를 사용하여 인증되면 이 호출됩니다. 입력 및 출력 값과 같은 이 프로세스에 대한 자세한 내용은 [단기 프로세스 예](/help/forms/developing/aem-forms-processes.md))

![cf_encryptdocumentprocess2](assets/cf_cf_encryptdocumentprocess2.png)

>[!NOTE]
>
>이 프로세스는 기존 AEM Forms 프로세스를 기반으로 하지 않습니다. 이 프로세스를 호출하는 방법에 대해 설명하는 코드 예제를 따라 다음 이름을 사용하는 프로세스를 만듭니다 `MyApplication/EncryptDocument` workbench 사용. (자세한 내용은 [Workbench 사용](https://www.adobe.com/go/learn_aemforms_workbench_63))

Flash Builder을 사용하여 작성된 클라이언트 애플리케이션은 `/um/login` 및 `/um/logout`. 즉, 클라이언트 애플리케이션이 `/um/login` 시작하는 동안 URL을 사용하여 사용자의 상태를 확인합니다. 그런 다음 사용자 관리자가 사용자 상태에 응답합니다. 클라이언트 응용 프로그램 및 사용자 관리자 보안 서블릿은 HTTP를 사용하여 통신합니다.

**요청 형식**

보안 서블릿에는 다음 입력 변수가 필요합니다.

* `um_no_redirect` - 이 값은 `true`. 이 변수는 User Manager 보안 서블릿에 대한 모든 요청을 포함합니다. 또한 보안 서블릿이 flex 클라이언트나 다른 웹 응용 프로그램에서 들어오는 요청을 구분하도록 도와줍니다.
* `j_username` - 이 값은 로그인 양식에 제공된 사용자의 로그인 식별자 값입니다.
* `j_password` - 이 값은 로그인 양식에 제공된 사용자의 해당 암호입니다.

다음 `j_password` 값은 자격 증명 요청에만 필요합니다. 암호 값을 지정하지 않으면 보안 서블릿은 사용 중인 계정이 이미 인증되었는지 확인합니다. 그럴 경우 진행할 수 있습니다. 그러나 보안 서블릿은 사용자를 다시 인증하지 않습니다.

>[!NOTE]
>
>i18n을 적절히 처리하려면 이 값이 POST 형식인지 확인하십시오.

**응답 형식**

에 구성된 보안 서블릿 `/um/login` 다음 방법으로 응답합니다 `URLVariables` 형식 지정 이 형식으로 표시되는 콘텐츠 유형의 출력은 텍스트/plain입니다. 출력에 앰퍼샌드(&amp;) 문자로 구분되는 이름 값 쌍이 포함됩니다. 응답에는 다음 변수가 포함되어 있습니다.

* `authenticated` - 값은 다음 중 하나입니다. `true` 또는 `false`.
* `authstate` - 이 값은 다음 값 중 하나를 포함할 수 있습니다.

   * `CREDENTIAL_CHALLENGE` - 이 상태는 User Manager가 어떤 수단을 통해 사용자의 ID를 확인할 수 없음을 나타냅니다. 인증을 수행하려면 사용자 이름과 암호가 필요합니다.
   * `SPNEGO_CHALLENGE`- 이 상태는 다음과 동일하게 처리됩니다. `CREDENTIAL_CHALLENGE`.
   * `COMPLETE` - 이 상태는 사용자 관리자가 사용자를 인증할 수 있음을 나타냅니다.
   * `FAILED` - 이 상태는 사용자 관리자가 사용자를 인증할 수 없음을 나타냅니다. 이 상태에 대한 응답으로 flex 클라이언트는 사용자에게 오류 메시지를 표시할 수 있습니다.
   * `LOGGED_OUT` - 이 상태는 사용자가 성공적으로 로그아웃되었음을 나타냅니다.

* `assertionid` - 상태가 `COMPLETE` 그러면 사용자의 `assertionId` 값. 클라이언트 응용 프로그램은 `AuthResult` 참조하십시오.

**로그인 프로세스**

클라이언트 응용 프로그램이 시작되면 `/um/login` 보안 서블릿. 예, `https://<your_serverhost>:<your_port>/um/login?um_no_redirect=true`. 요청이 User Manager 보안 서블릿에 도달하면 다음 단계를 수행합니다.

1. 라는 쿠키를 찾습니다 `lcAuthToken`. 사용자가 이미 다른 Forms 애플리케이션에 로그인한 경우에는 이 쿠키가 있습니다. 쿠키가 발견되면 해당 컨텐츠의 유효성이 검사됩니다.
1. 헤더 기반 SSO가 활성화되어 있으면 서블릿은 사용자 ID를 결정하기 위해 구성된 헤더를 찾습니다.
1. SPNEGO가 활성화되어 있으면 서블릿은 SPNEGO를 시작하고 사용자의 ID를 확인하려고 시도합니다.

보안 서블릿이 사용자와 일치하는 유효한 토큰을 찾으면 보안 서블릿을 사용하여 계속 진행하고 응답할 수 있습니다 `authstate=COMPLETE`. 그렇지 않으면 보안 서블릿이 `authstate=CREDENTIAL_CHALLENGE`. 다음 목록에서는 다음 값에 대해 설명합니다.

* `Case authstate=COMPLETE`: 사용자가 인증되고 `assertionid` 값에는 사용자에 대한 검증 식별자가 들어 있습니다. 이 단계에서는 클라이언트 응용 프로그램이 AEM Forms에 연결할 수 있습니다. 해당 URL에 대해 구성된 서블릿은 `AuthResult` 을 호출하여 `AuthenticationManager.authenticate(HttpRequestToken)` 메서드를 사용합니다. 다음 `AuthResult` 인스턴스는 사용자 관리자 컨텍스트를 만들고 세션에 저장할 수 있습니다.
* `Case authstate=CREDENTIAL_CHALLENGE`: 보안 서블릿에 사용자의 자격 증명이 필요함을 나타냅니다. 응답으로 클라이언트 애플리케이션은 사용자에게 로그인 화면을 표시하고 획득한 자격 증명을 보안 서블릿으로 전송할 수 있습니다(예: `https://<your_serverhost>:<your_port>/um/login?um_no_redirect=true&j_username=administrator&j_password=password)`. 인증이 성공하면 보안 서블릿이 `authstate=COMPLETE`.

인증이 여전히 성공하지 않으면 보안 서블릿은 `authstate=FAILED`. 이 값에 응답하기 위해 클라이언트 응용 프로그램은 자격 증명을 다시 얻기 위한 메시지를 표시할 수 있습니다.

>[!NOTE]
>
>While `authstate=CREDENTIAL_CHALLENGE`이렇게 하려면 클라이언트가 가져온 자격 증명을 POST 양식의 보안 서블릿에 전송하는 것이 좋습니다.

**로그아웃 프로세스**

클라이언트 응용 프로그램이 로그아웃하면 다음 URL에 요청을 보낼 수 있습니다.

`https://<your_serverhost>:<your_port>/um/logout?um_no_redirect=true`

이 요청을 받을 때 User Manager 보안 서블릿은 `lcAuthToken` 쿠키 및 `authstate=LOGGED_OUT`. 클라이언트 응용 프로그램이 이 값을 수신하면 응용 프로그램이 정리 작업을 수행할 수 있습니다.

## SSO를 사용하여 AEM Forms 사용자를 인증하는 클라이언트 응용 프로그램 만들기 {#creating-a-client-application-that-authenticates-aem-forms-users-using-sso}

SSO 인증을 수행하는 클라이언트 응용 프로그램을 만드는 방법을 보여 주기 위해 예제 클라이언트 응용 프로그램이 만들어집니다. 다음 그림은 클라이언트 응용 프로그램이 SSO를 사용하여 사용자를 인증하기 위해 수행하는 단계를 보여줍니다.

![cf_flexsso](assets/cf_cf_flexsso.png)

이전 그림은 클라이언트 응용 프로그램이 시작될 때 발생하는 응용 프로그램 플로우에 대해 설명합니다.

1. 클라이언트 응용 프로그램이 `applicationComplete` 이벤트.
1. 호출 `ISSOManager.singleSignOn` 가 만들어집니다. 클라이언트 응용 프로그램이 User Manager 보안 서블릿에 요청을 보냅니다.
1. 보안 서블릿이 사용자를 인증하는 경우 `ISSOManager` 디스패치 `SSOEvent.AUTHENTICATION_SUCCESS`. 응답으로 클라이언트 응용 프로그램에 기본 페이지가 표시됩니다. 이 예에서 기본 페이지는 MyApplication/EncryptDocument라는 짧은 기간 동안 진행되는 AEM Forms 프로세스를 호출합니다.
1. 보안 서블릿이 사용자가 유효한지 여부를 확인할 수 없는 경우 응용 프로그램이 사용자 자격 증명을 다시 요청합니다. 다음 `ISSOManager` 클래스 디스패치 `SSOEvent.AUTHENTICATION_REQUIRED` 이벤트. 클라이언트 응용 프로그램에 로그인 페이지가 표시됩니다.
1. 로그인 페이지에 제공된 자격 증명은 `ISSOManager.login` 메서드를 사용합니다. 인증이 성공하면 3단계로 이동합니다. 그렇지 않으면 `SSOEvent.AUTHENTICATION_FAILED` 이벤트가 트리거됩니다. 클라이언트 응용 프로그램은 로그인 페이지와 적절한 오류 메시지를 표시합니다.

### 클라이언트 응용 프로그램 만들기 {#creating-the-client-application}

클라이언트 응용 프로그램은 다음 파일로 구성됩니다.

* `SSOStandalone.mxml`: 클라이언트 응용 프로그램을 나타내는 기본 MXML 파일입니다. (자세한 내용은 [SSOStandony.mxml 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-ssostandalone-mxml-file))
* `um/ISSOManager.as`: SSO(Single Sign On)와 관련된 작업을 노출합니다. (자세한 내용은 [ISSOManager.as 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-issomanager-as-file))
* `um/SSOEvent.as`: 다음 `SSOEvent` 은 SSO 관련 이벤트에 대해 전달됩니다. (자세한 내용은 [SOEvent.as 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-ssoevent-as-file))
* `um/SSOManager.as`: SSO 관련 작업을 관리하고 적절한 이벤트를 발송합니다. (자세한 내용은 [SOManager.as 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-ssomanager-as-file))
* `um/UserManager.as`: WSDL을 사용하여 인증 관리자 서비스를 호출하는 응용 프로그램 논리를 포함합니다. (자세한 내용은 [UserManager.as 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-usermanager-as-file))
* `views/login.mxml`: 로그인 화면을 나타냅니다. (자세한 내용은 [login.mxml 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-login-mxml-file))
* `views/logout.mxml`: 로그아웃 화면을 나타냅니다. (자세한 내용은 [logout.mxml 파일을 만드는 중](creating-flash-builder-applications-perform.md#creating-the-logout-mxml-file))
* `views/progress.mxml`: 진행률 보기를 나타냅니다. (자세한 내용은 [progress.mxml 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-progress-mxml-file))
* `views/remoting.mxml`: 원격을 사용하여 MyApplication/EncryptDocument라는 AEM Forms 단기 프로세스를 호출하는 보기를 나타냅니다. (자세한 내용은 [remoting.mxml 파일 만들기](creating-flash-builder-applications-perform.md#creating-the-remoting-mxml-file))

다음 그림은 클라이언트 응용 프로그램을 시각적으로 보여줍니다.

![cf_sso_project](assets/cf_cf_sso_project.png)

>[!NOTE]
>
>um 및 views라는 두 개의 패키지가 있습니다. 클라이언트 응용 프로그램을 만들 때 파일을 적절한 패키지에 배치해야 합니다. 또한 adobe-remoting-provider.swc 파일을 프로젝트의 클래스 경로에 추가해야 합니다. (자세한 내용은 [AEM Forms Flex 라이브러리 파일 포함](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file))

### SSOStandony.mxml 파일 만들기 {#creating-the-ssostandalone-mxml-file}

다음 코드는 SSOStandony.mxml 파일을 나타냅니다.

```as3
 <?xml version="1.0" encoding="utf-8"?> 
 <mx:Application   
                 layout="absolute" 
                 applicationComplete="initApp()" 
                 height="400" width="550" 
                 xmlns:v="views.*" 
                 backgroundColor="#EDE8F0" viewSourceURL="srcview/index.html"> 
     <mx:Script> 
         <![CDATA[ 
             import mx.utils.URLUtil; 
             import um.SSOEvent; 
             import mx.core.UIComponent; 
             import um.SSOManager; 
             import mx.rpc.events.ResultEvent; 
             import mx.utils.ObjectUtil; 
             import mx.controls.Alert; 
              
             [Bindable] 
             private var _serverURL:String; 
              
             private var _ssoManager:SSOManager; 
              
             private var _progress:UIComponent; 
              
             private var _loginPage:UIComponent; 
              
             private function initApp():void{ 
                 _serverURL = determineServerUrl(); 
                 _ssoManager = new SSOManager(_serverURL); 
                  
                 _ssoManager.addEventListener(SSOEvent.AUTHENTICATION_FAILED,loginHandler); 
                 _ssoManager.addEventListener(SSOEvent.AUTHENTICATION_SUCCESS,loginHandler); 
                 _ssoManager.addEventListener(SSOEvent.AUTHENTICATION_REQUIRED,loginHandler); 
                 _ssoManager.addEventListener(SSOEvent.LOGOUT_COMPLETE,loginHandler); 
                 _ssoManager.addEventListener(SSOEvent.AUTHENTICATION_FAULT,loginHandler); 
                  
                 trace("[Main] Add the required event handlers for authentication"); 
                 _ssoManager.singleSignOn(); 
                  
                 showBusy(); 
             } 
              
             private function determineServerUrl():String 
             { 
                 var s:String ; 
                 var appUrl:String = Application.application.url; 
                 var givenUrl:String  = ExternalInterface.call("serverUrl.toString"); 
                 trace("[Main] Application url ["+appUrl+"] Given url ["+givenUrl+"]"); 
                 if(appUrl != null && appUrl.search("^http") != -1){ 
                     s = appUrl; 
                 } 
                 if(s == null){ 
                     s = givenUrl; 
                 } 
                 if(s== null){ 
                     s = "https://hiro-xp:8080/"; 
                 } 
                 s = URLUtil.getFullURL(s,"/"); 
                 trace("[Main] Would be using ["+s+"] as serverUrl"); 
                 return s; 
             } 
              
             private function loginHandler(event:SSOEvent):void 
             { 
                 trace("[Main] Handling event "+event.type); 
                 switch(event.type) 
                 { 
                     case SSOEvent.AUTHENTICATION_FAILED: 
                         viewContent.selectedChild = login; 
                         login.showLoginFailed(); 
                         break; 
                     case SSOEvent.AUTHENTICATION_SUCCESS: 
                         viewContent.selectedChild = remoting; 
                         break; 
                     case SSOEvent.AUTHENTICATION_REQUIRED: 
                         viewContent.selectedChild = login; 
                         break; 
                     case SSOEvent.LOGOUT_COMPLETE: 
                         viewContent.selectedChild = logout; 
                         break; 
                     case SSOEvent.AUTHENTICATION_FAULT: 
                         Alert.show("Error doing authentication. Root error ["+event.rootEvent+"]","Authentication Fault",Alert.OK); 
                 } 
             } 
              
             public function get ssoManager():SSOManager 
             { 
                 return _ssoManager; 
             } 
              
             public function showBusy():void 
             { 
                 viewContent.selectedChild = progress; 
             } 
              
             public function get serverUrl():String 
             { 
                 return _serverURL; 
             } 
              
         ]]> 
     </mx:Script> 
     <mx:ViewStack x="0" y="0" id="viewContent" > 
         <v:login id="login" /> 
         <v:remoting id="remoting"  /> 
         <v:progress id="progress" /> 
         <v:logout id="logout"/> 
     </mx:ViewStack> 
 </mx:Application> 
 
```

### ISSOManager.as 파일 만들기 {#creating-the-issomanager-as-file}

다음 코드는 ISSOManager.as 파일을 나타냅니다.

```as3
 package um 
 { 
     import flash.events.IEventDispatcher; 
      
     /** 
      * The <code>ISSOManager</code> expose operations related to Single Sign On (SSO) in AEM Forms 
      * environment. The application should register appropriate <code>SSOEvent</code> handlers prior 
      * to calling any of the following operations 
      */ 
     public interface ISSOManager extends IEventDispatcher 
     { 
         /** 
          * Tries to validate whether the user has an already existing session or not (SSO Scenarios). The application  
          * may call this method during the initialization. In general this call would lead to one of the  
          * following events getting dispatched 
          * <ul> 
          * <li>SSOEvent.AUTHENTICATION_SUCCESS - If a SSO session was found and valid 
          * <li>SSOEvent.AUTHENTICATION_REQUIRED - No SSO session was found and as such authentication is required in 
          * the form of username and password. 
          * <li>SSOEvent.AUTHENTICATION_FAULT - Some error has occured while connecting to the server 
          * </ul> 
          */ 
         function singleSignOn():void; 
          
         /** 
          * Authenticates the user using username and password. It may lead to one of the following events 
          * <ul> 
          * <li>SSOEvent.AUTHENTICATION_SUCCESS - The authentication is successful and a session is established 
          * <li>SSOEvent.AUTHENTICATION_FAILED - Authentication has failed 
          * </ul> 
          */ 
         function login(username:String, password:String):void; 
          
         /** 
          * Terminates the current session and logs out the user. 
          */ 
         function logout():void; 
          
         /** 
          * Get the assertionId for the logged in user 
          */ 
         function get assertionId():String; 
     } 
 }
```

### SOEvent.as 파일 만들기 {#creating-the-ssoevent-as-file}

다음 코드는 SOEvent.as 파일을 나타냅니다.

```as3
 package um 
 { 
     import flash.events.Event; 
      
     /** 
      * The <code>SSOEvent</code> is dispatched for SSO related events 
      */ 
     public class SSOEvent extends Event 
     { 
         /** 
          * This type of event would be dispatched when the Authentication process is successful. Authentication  
          * might have been done with SSO or username and password. As a response to this event the application  
          * can show the welcome page to the user 
          * The application may want to perform specific check for permission/role so as to verify the user is allowed. 
          * So as a response to this event the application would do those checks and then only show the welcome page 
          */ 
         public static const AUTHENTICATION_SUCCESS:String = "authenticationSuccess"; 
          
         /** 
          * This type of event would be dispatched when authentication fails using the username, password. 
          * As a response to this type of event an application can show an error message to the user. 
          * This event would only happen when authentication is done using username and password and NOT in  
          * SSO case. 
          */ 
         public static const AUTHENTICATION_FAILED:String = "authenticationFailed"; 
          
         /** 
          * This type of event would be dispatched when authentication using SSO is not achieved. And due to  
          * that we require the user's username and password for authentication. As a response to this event  
          * the application can show the login page to the user. 
          */ 
         public static const AUTHENTICATION_REQUIRED:String = "authenticationRequired"; 
          
         /** 
          * This type of event would be dispatched when logout is complete. As a response to this event the  
          * application may show a logout page informing the user that he has been logged out. Or the application 
          * can take the user back to login page 
          */ 
         public static const LOGOUT_COMPLETE:String = "logoutComplete"; 
          
         /** 
          * This type of event would be dispatched when ever there is a problem in doing Authentication. The root cause 
          * can be obtained from the <code>rootEvent</code>.  
          */ 
         public static const AUTHENTICATION_FAULT:String = "authenticationFault"; 
          
         private var _rootEvent:Event; 
          
         public function SSOEvent(type:String, rootEvent:Event=null) 
         { 
             super(type,true,false); 
             _rootEvent = rootEvent; 
         } 
          
         /** 
          * The root event. If current event type is <code>AUTHENTICATION_FAULT</code> then it would be an  
          * <code>IOErrorEvent</code> in other cases it would be complete event. Its basic use is to extract the root  
          * cause in case of an authentication fault. 
          */ 
         public function get rootEvent():Event 
         { 
             return _rootEvent; 
         } 
     } 
 }
```

### SOManager.as 파일 만들기 {#creating-the-ssomanager-as-file}

다음 코드는 SOManager.as 파일을 나타냅니다.

```as3
 package um 
 { 
     import flash.events.Event; 
     import flash.events.EventDispatcher; 
     import flash.events.IOErrorEvent; 
     import flash.external.ExternalInterface; 
     import flash.net.URLLoader; 
     import flash.net.URLLoaderDataFormat; 
     import flash.net.URLRequest; 
     import flash.net.URLVariables; 
      
     import mx.utils.ObjectUtil; 
      
     /** 
      * Manages the SSO related operations and dispatches appropriate events. It would connect to the UM Filter/Servlet  
      * at <code>um/login</code> The UM response would be of form of url encoded variables. It would look for  
      * <code>authstate</code> value in the response and depending on that it would proceed. 
      * 
      * <p>If there is an IO_Error while initial attempt to UM then it would assume it as a 401 response. And it would 
      * be assumed that SPNEGO based authenticatin is not working and therefore user would be shown a login page. 
      */ 
     public class SSOManager extends EventDispatcher implements ISSOManager 
     { 
         private static const SSO_URL:String = "um/login"; 
         private static const SSO_LOGOUT_URL:String = "um/logout"; 
         private static const AUTH_COOKIE_NAME:String = "lcAuthToken"; 
          
         private var _serverUrl:String; 
         private var _assertionId:String; 
          
         /** 
          * Constructs an SSOManager with the given server url.  
          * 
          * @param serverUrl - The uri of the server to connect to. it must be without any context path e.g 
          * http://localhost:8080/. The SSOManager would directly append the path of UM exposed SSO url to it 
          * for its operations 
          */ 
         public function SSOManager(serverUrl:String) 
         { 
             _serverUrl = serverUrl; 
         } 
          
         public function singleSignOn():void 
         { 
             sendRequest(SSO_URL,true); 
         } 
          
         public function login(username:String, password:String):void 
         { 
             sendRequest(SSO_URL,false,  
                 function(request:URLRequest,vars:URLVariables):void 
                 { 
                     vars.j_username = username; 
                     vars.j_password = password; 
                 } 
             ); 
         } 
          
         public function logout():void 
         { 
             sendRequest(SSO_LOGOUT_URL); 
         } 
          
         public function get assertionId():String 
         { 
             return _assertionId;     
         } 
          
          
          
         /** 
          * Connects to the UM security service.  
          */         
         private function sendRequest(relativeUrl:String,authenticationRequest:Boolean=false, requestProcessor:Function=null):void 
         { 
             var loader:URLLoader = new URLLoader(); 
             loader.dataFormat = URLLoaderDataFormat.VARIABLES; 
             var request:URLRequest = new URLRequest(_serverUrl + relativeUrl); 
             trace("[SSOmanager] Contacting ["+request.url+"]"); 
             var vars:URLVariables = new URLVariables(); 
             vars.um_no_redirect = "true"; 
             request.data = vars; 
             if(requestProcessor != null){ 
                 requestProcessor(request,vars); 
             } 
              
             loader.addEventListener(Event.COMPLETE,authHandler); 
             //if its an authentication request then only treat io error as a possible 401 
             //for others treat them as faults 
             if(authenticationRequest){ 
                 loader.addEventListener(IOErrorEvent.IO_ERROR,httpAuthenticationHandler); 
             }else{ 
                 loader.addEventListener(IOErrorEvent.IO_ERROR,authFaultHandler); 
             } 
             trace("[SSOmanager] Sending request "+ ObjectUtil.toString(request)); 
             loader.load(request); 
         } 
          
         private function authHandler(event:Event):void 
         { 
             var loader:URLLoader = URLLoader(event.target); 
             var response:URLVariables = URLVariables(loader.data); 
             trace("[SSOmanager] Processing response ["+ObjectUtil.toString(response)+"]"); 
             handleAuthResult(response["authstate"],response); 
         } 
          
         /** 
          * Handles the IOErrorEvent. Flash would dispatch IOEvent in response to HTTP 401. 
          * There is no way to distinguish it from the genuine IOError. 
          */ 
         private function httpAuthenticationHandler(event:IOErrorEvent):void 
         { 
             trace("[SSOmanager] Processing IOErrorEvent ["+ObjectUtil.toString(event)+"]"); 
             handleAuthResult("CREDENTIAL_CHALLENGE"); 
              
         }     
          
         /** 
          * Dispatches appropriate <code>SSOEvent</code> on the basis of the <code>authstate</code>  
          * value of the response. 
          * The response is url encoded in for of 
          * <pre> 
          * authenticated=false&authstate=SPNEGO_CHALLENGE 
          * </pre> 
          * Depending on <code>authstate</code> the SSOEvent is dispatched 
          */ 
         private function handleAuthResult(authState:String,response:URLVariables = null):void  
         { 
             trace("[SSOmanager] processing state "+authState); 
             switch(authState) 
             { 
                 case "FAILED"  :  
                     dispatchEvent(new SSOEvent(SSOEvent.AUTHENTICATION_FAILED)); 
                     break; 
                 case "COMPLETE" : 
                     _assertionId = response ? response["assertionid"] : null;  
                     dispatchEvent(new SSOEvent(SSOEvent.AUTHENTICATION_SUCCESS)); 
                     break; 
                 case "CREDENTIAL_CHALLENGE" : 
                     dispatchEvent(new SSOEvent(SSOEvent.AUTHENTICATION_REQUIRED)); 
                     break; 
                 case "LOGGED_OUT" : 
                     dispatchEvent(new SSOEvent(SSOEvent.LOGOUT_COMPLETE)); 
                     break; 
                 default: 
                     dispatchEvent(new SSOEvent(SSOEvent.AUTHENTICATION_REQUIRED)); 
                     break; 
             } 
         } 
          
         private function authFaultHandler(event:Event):void 
         { 
             dispatchEvent(new SSOEvent(SSOEvent.AUTHENTICATION_FAULT,event)); 
         } 
          
     } 
 }
```

### UserManager.as 파일 만들기 {#creating-the-usermanager-as-file}

다음 코드는 UserManager.as 파일을 나타냅니다.

```as3
 package um 
 { 
     import flash.events.Event; 
     import mx.rpc.soap.WebService; 
     import mx.rpc.soap.Operation; 
     import mx.rpc.IResponder; 
     import mx.rpc.events.FaultEvent; 
     import mx.rpc.events.ResultEvent; 
     import mx.rpc.soap.LoadEvent; 
      
     public class UserManager 
     { 
         private var _ssoManager:ISSOManager; 
         private var _serverUrl:String; 
          
         public function UserManager(ssoManager:ISSOManager,serverUrl:String) 
         { 
             _serverUrl = serverUrl; 
             _ssoManager = ssoManager; 
         } 
          
         public function retrieveAssertion(responder:IResponder):String 
         { 
             var assertionId:String = _ssoManager.assertionId; 
             if(!assertionId) 
             { 
                 trace("[UserManager] AssertionId not found"); 
                 return null; 
             } 
              
             var ws:WebService = new WebService(); 
             var wsdl:String = _serverUrl+'soap/services/AuthenticationManagerService?wsdl&lc_version=8.2.1'; 
             ws.loadWSDL(wsdl); 
             ws.addEventListener(LoadEvent.LOAD, 
                 function(event:Event):void 
                 { 
                     trace("[UserManager] WSDL loaded"); 
                     var authenticate:Operation = ws.authenticateWithHttpToken as Operation; 
                     authenticate.resultFormat = "e4x"; 
                     authenticate.addEventListener(ResultEvent.RESULT,  
                         function(event:Event):void 
                         { 
                             responder.result(event); 
                         } 
                     );     
                     authenticate.send({assertionId:assertionId});              
                 } 
             ); 
              
             ws.addEventListener(FaultEvent.FAULT, 
                 function(event:Event):void 
                 { 
                     responder.fault(event);     
                 } 
             ); 
             return null; 
         } 
     } 
 }
```

### login.mxml 파일 만들기 {#creating-the-login-mxml-file}

다음 코드는 login.mxml 파일을 나타냅니다.

```as3
 <?xml version="1.0" encoding="utf-8"?> 
 <mx:Canvas  width="500" height="400"> 
     <mx:Script> 
         <![CDATA[ 
             import mx.core.Application; 
             public function showLoginFailed():void 
             { 
                 loginMessage.text = "Username or Password incorrect"; 
             } 
              
             private function doLogin():void 
             { 
                 Application.application.ssoManager.login(j_username.text,j_password.text); 
                 Application.application.showBusy(); 
             } 
              
         ]]> 
     </mx:Script> 
      
     <mx:VBox height="113" width="244" x="128" y="144" horizontalAlign="center" verticalGap="10"> 
         <mx:HBox width="100%"> 
             <mx:HBox width="100%" verticalAlign="middle" horizontalAlign="center" height="32"> 
                 <mx:Label text="Username" fontWeight="bold"/> 
                 <mx:TextInput id="j_username"/> 
             </mx:HBox> 
         </mx:HBox> 
         <mx:HBox width="100%" height="33" horizontalAlign="center" horizontalGap="10" verticalAlign="middle"> 
             <mx:Label text="Password" fontWeight="bold"/> 
             <mx:TextInput displayAsPassword="true" id="j_password"/> 
         </mx:HBox> 
         <mx:Button label="Login" click="doLogin()"/> 
     </mx:VBox> 
     <mx:Text x="128" y="122" id="loginMessage" width="230" height="14"/> 
     <mx:Label x="154" y="65" text="AEM Forms SSO Demo" fontFamily="Georgia" fontSize="20" color="#0A0A0A"/> 
 </mx:Canvas> 
 
```

### logout.mxml 파일을 만드는 중 {#creating-the-logout-mxml-file}

다음 코드는 logout.mxml 파일을 나타냅니다.

```as3
 <?xml version="1.0" encoding="utf-8"?> 
 <mx:Canvas  width="500" height="400"> 
     <mx:Label x="97" y="188" text="You have successfully logged out from the application"/> 
      
 </mx:Canvas> 
 
```

### progress.mxml 파일 만들기 {#creating-the-progress-mxml-file}

다음 코드는 progress.mxml 파일을 나타냅니다.

```as3
 <?xml version="1.0" encoding="utf-8"?> 
 <mx:Canvas > 
     <mx:Label x="151" y="141" text="Wait...."/> 
     <mx:SWFLoader source="LoadingCircle.swf" width="50" height="50" horizontalCenter="0" verticalCenter="0"/> 
 </mx:Canvas>
```

### remoting.mxml 파일 만들기 {#creating-the-remoting-mxml-file}

다음 코드는 Remoting.mxml 파일을 호출하는 것을 나타냅니다 `MyApplication/EncryptDocument` 프로세스. 문서가 프로세스에 전달되므로 이 파일에 보안 문서를 AEM Forms에 전달하는 애플리케이션 논리가 있습니다. (자세한 내용은 [Remoting을 사용하여 프로세스를 호출하는 보안 문서 전달](/help/forms/developing/invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting))

```as3
 <?xml version="1.0" encoding="utf-8"?> 
 <mx:Canvas  width="664" height="400" creationComplete="initializeChannelSet()" xmlns:views="views.*"> 
     <mx:Script> 
  
         <![CDATA[ 
              
             import mx.rpc.livecycle.DocumentReference; 
             import flash.net.FileReference; 
             import flash.net.URLRequest; 
             import flash.events.Event; 
             import flash.events.DataEvent; 
             import mx.messaging.ChannelSet; 
             import mx.messaging.channels.AMFChannel;   
             import mx.rpc.events.ResultEvent; 
             import mx.collections.ArrayCollection; 
             import mx.rpc.AsyncToken; 
             import um.UserManager; 
             import mx.rpc.events.ResultEvent; 
             import mx.rpc.events.FaultEvent; 
             import mx.core.Application; 
             import mx.rpc.Responder; 
             import mx.utils.ObjectUtil; 
              
             // Classes used in file retrieval   
             private var fileRef:FileReference = new FileReference(); 
             private var docRef:DocumentReference = new DocumentReference(); 
             private var parentResourcePath:String = "/"; 
             //private var serverPort:String = "[server]:[port]"; 
             private var serverPort:String = "[server]:[port]"; 
             private var now1:Date;     
             private var userManager:UserManager; 
          
             // Define a ChannelSet object. 
             public var cs:ChannelSet;  
              
             // Holds information returned from AEM Forms 
             [Bindable] 
             public var progressList:ArrayCollection = new ArrayCollection(); 
              
              
             // Set up channel set to invoke AEM Forms. 
             // This must be done before calling any service or process, but only  
             // once for the entire application. 
             private function initializeChannelSet():void { 
                 cs = new ChannelSet();  
                 cs.addChannel(new AMFChannel("remoting-amf", "https://" + serverPort + "/remoting/messagebroker/amf"));  
                 EncryptDocument.channelSet = cs; 
              
             //Get the user that is authenticated 
             userManager = new UserManager(Application.application.ssoManager,Application.application.serverUrl); 
             userManager.retrieveAssertion( 
                     new mx.rpc.Responder( 
                         function(event:ResultEvent):void 
                         { 
                             var name:String = XML(event.currentTarget.lastResult)..*::authenticatedUser.*::userid.text(); 
                             username.text = "Welcome "+name;                             
                         }, 
                         function(event:FaultEvent):void 
                         { 
                             mx.controls.Alert.show(event.fault.faultString,'Error') 
                         } 
                     ) 
                 ); 
              
             } 
              
             // Call this method to upload the file. 
             // This creates a file picker and lets the user select a PDF file to pass to the EncryptDocument process. 
             private function uploadFile():void { 
                 fileRef.addEventListener(Event.SELECT, selectHandler); 
                 fileRef.addEventListener(DataEvent.UPLOAD_COMPLETE_DATA,completeHandler); 
                 fileRef.browse(); 
             } 
              
             // Gets called for selected file. Does the actual upload via the file upload servlet. 
             private function selectHandler(event:Event):void { 
                 var authTokenService:RemoteObject = new RemoteObject("LC.FileUploadAuthenticator"); 
                 authTokenService.addEventListener("result", authTokenReceived); 
                 authTokenService.channelSet = cs; 
                 authTokenService.getFileUploadToken(); 
             } 
              
             private function authTokenReceived(event:ResultEvent):void 
             { 
                 var token:String = event.result as String; 
                 var request:URLRequest = DocumentReference.constructRequestForUpload("https://hiro-xp:8080", token); 
                  
                 try 
                 { 
                     fileRef.upload(request); 
                 } 
                 catch (error:Error) 
                 { 
                     trace("Unable to upload file."); 
                 }                               
             } 
              
             // Called once the file is completely uploaded. 
             private function completeHandler(event:DataEvent):void {                     
                  
                 // Set the docRefs url and referenceType parameters 
                 docRef.url = event.data as String;       
                 docRef.referenceType=DocumentReference.REF_TYPE_URL; 
                 executeInvokeProcess();  
             }       
              
             //This method invokes the EncryptDocument process 
             public function executeInvokeProcess():void { 
                 //Create an Object to store the input value for the EncryptDocument process 
                 now1 = new Date(); 
                  
                 var params:Object = new Object(); 
                 params["inDoc"]=docRef; 
                  
                 // Invoke the EncryptDocument process 
                 var token:AsyncToken;             
                 token = EncryptDocument.invoke(params); 
                 token.name = name; 
             } 
      
              
             // This method handles a successful conversion invocation 
             public function handleResult(event:ResultEvent):void 
             { 
                  
                 //Retrieve information returned from the service invocation 
                 var token:AsyncToken = event.token;         
                 var res:Object = event.result; 
                 var dr:DocumentReference = res["outDoc"] as DocumentReference; 
                 var now2:Date = new Date(); 
                          
                 // These fields map to columns in the DataGrid 
                 var progObject:Object = new Object(); 
                 progObject.filename = token.name; 
                 progObject.timing = (now2.time - now1.time).toString(); 
                 progObject.state = "Success"; 
                 progObject.link = "<a href='" + dr.url + "'> open </a>"; 
                 progressList.addItem(progObject); 
             } 
              
              
             private function resultHandler(event:ResultEvent):void { 
             // Do anything else here. 
                  
             } 
              
             private function logout():void 
             { 
                 Application.application.ssoManager.logout(); 
                 Application.application.showBusy(); 
             } 
          
              
         ]]> 
          
     </mx:Script> 
      
     <mx:RemoteObject id="EncryptDocument" destination="MyApplication/EncryptDocument" result="resultHandler(event);"> 
             <mx:method name="invoke" result="handleResult(event)"/> 
     </mx:RemoteObject> 
      
      
     <!--//This consists of what is displayed on the webpage--> 
     <mx:Panel id="lcPanel" title="EncryptDocument  (Deprecated for AEM forms) AEM Forms Remoting Example"  
           height="25%" width="25%" paddingTop="10" paddingLeft="10" paddingRight="10"  
           paddingBottom="10"> 
         <mx:Label width="100%" color="blue" 
                   id="username"/>  
          
         <mx:DataGrid x="10" y="0" width="500" id="idProgress" editable="false"  
                          dataProvider="{progressList}" height="231" selectable="false" > 
         <mx:columns> 
                 <mx:DataGridColumn headerText="Filename" width="200" dataField="filename" editable="false"/> 
                 <mx:DataGridColumn headerText="State" width="75" dataField="state" editable="false"/> 
                 <mx:DataGridColumn headerText="Timing" width="75" dataField="timing" editable="false"/> 
                 <mx:DataGridColumn headerText="Click to Open" dataField="link" editable="false" > 
                 <mx:itemRenderer> 
                          
                         <mx:Component> 
                         <mx:Text x="0" y="0" width="100%" htmlText="{data.link}"/> 
                         </mx:Component> 
                     </mx:itemRenderer> 
             </mx:DataGridColumn> 
         </mx:columns> 
     </mx:DataGrid> 
     <mx:Button label="Select File" click="uploadFile()" /> 
     <mx:Button label="Logout"  click="logout()" /> 
     </mx:Panel> 
 </mx:Canvas> 
  
 
```

### 추가 정보 {#additional-information}

다음 섹션에서는 클라이언트 애플리케이션과 User Manager 보안 서블릿 간의 통신을 설명하는 추가 세부 정보를 제공합니다.

### 새 인증이 발생합니다 {#a-new-authentication-occurs}

이 경우 사용자는 클라이언트 애플리케이션에서 AEM Forms으로 처음으로 로그인을 시도합니다. (사용자와 관련된 이전 세션이 없습니다.) 에서 `applicationComplete` event, `SSOManager.singleSignOn` 사용자 관리자에게 요청을 보내는 메서드가 호출됩니다.

`GET /um/login?um%5Fno%5Fredirect=true HTTP/1.1`

User Manager 보안 서블릿은 다음 값으로 응답합니다.

`HTTP/1.1 200 OK`

`authenticated=false&authstate=CREDENTIAL_CHALLENGE`

이 값에 대한 응답으로, `SSOEvent.AUTHENTICATION_REQUIRED` 값이 전달됩니다. 따라서 클라이언트 응용 프로그램은 사용자에게 로그인 화면을 표시합니다. 자격 증명이 User Manager 보안 서블릿으로 다시 제출됩니다.

`GET /um/login?um%5Fno%5Fredirect=true&j%5Fusername=administrator&j%5Fpassword=password HTTP/1.1`

User Manager 보안 서블릿은 다음 값으로 응답합니다.

```as3
 HTTP/1.1 200 OK 
 Set-Cookie: lcAuthToken=53630BC8-F6D4-F588-5D5B-4668EFB2EC7A; Path=/ 
 authenticated=true&authstate=COMPLETE&assertionid=53630BC8-F6D4-F588-5D5B-4668EFB2EC7A
```

결과적으로 `authstate=COMPLETE the SSOEvent.AUTHENTICATION_SUCCESS` 가 발송되었습니다. 클라이언트 응용 프로그램은 필요한 경우 추가 처리를 수행할 수 있습니다. 예를 들어 사용자가 인증된 날짜와 시간을 추적하는 로그를 만들 수 있습니다.

### 사용자가 이미 인증되었습니다 {#the-user-is-already-authenticated}

이 경우 사용자는 이미 AEM Forms에 로그인한 다음 클라이언트 애플리케이션으로 이동합니다. 클라이언트 응용 프로그램은 시작하는 동안 사용자 관리자 보안 서블릿에 연결됩니다.

```as3
 GET /um/login?um%5Fno%5Fredirect=true HTTP/1.1 
 Cookie: JSESSIONID=A4E0BCC2DD4BCCD3167C45FA350BD72A; lcAuthToken=53630BC8-F6D4-F588-5D5B-4668EFB2EC7A
```

사용자가 이미 인증되었으므로 User Manager 쿠키가 있고 User Manager 보안 서블릿으로 전송됩니다. 그러면 서블릿이 `assertionId` 값을 확인하고 유효한지 확인합니다. 유효하다면 `authstate=COMPLETE` 가 반환됩니다. 그렇지 않은 경우 `authstate=CREDENTIAL_CHALLENGE` 가 반환됩니다. 다음은 일반적인 응답입니다.

```as3
 HTTP/1.1 200 OK 
        authenticated=true&authstate=COMPLETE&assertionid=53630BC8-F6D4-F588-5D5B-4668EFB2EC7A
```

이 경우 사용자에게 로그인 화면이 표시되지 않고 대신 시작 화면으로 직접 이동합니다.
