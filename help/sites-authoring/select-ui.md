---
title: UI 선택
seo-title: UI 선택
description: AEM에서 작업할 때 사용하려는 인터페이스를 구성합니다.
seo-description: AEM에서 작업할 때 사용하려는 인터페이스를 구성합니다.
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 70%

---


# UI 선택{#selecting-your-ui}

## UI 이해

작성 환경에서 다음 작업이 허용됩니다.

* [작성](/help/sites-authoring/author.md)([페이지 작성](/help/sites-authoring/author-environment-tools.md), [자산 관리](/help/assets/home.md), [커뮤니티](/help/communities/author-communities.md) 포함)

* [웹 사이트에서 컨텐츠를 생성하고 유지 관리할 때 필요한 작업 관리](/help/sites-administering/home.md)

이를 달성하기 위해 두 가지 그래픽 사용자 인터페이스가 제공되며, 이 인터페이스는 최신 브라우저를 통해 액세스할 수 있습니다.

1. 터치 활성화 UI

   * 최신 기본 AEM UI입니다.
   * 주로 회색이며, 깔끔하고 무난한 인터페이스입니다.
   * 터치 및 데스크톱 장치용으로 설계되었으며 [리소스를 보고 선택하는 방법](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)은 조금 다르지만(탭/클릭) 모양과 느낌은 모든 장치에서 동일합니다.

      * 데스크톱:

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * 태블릿 장치(또는 폭이 1024픽셀 미만인 데스크톱):

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. 클래식 UI

   * 레거시 UI이며 수년 동안 AEM에서 사용되고 있습니다.
   * 주로 녹색입니다.
   * 데스크톱 장치에서 사용하도록 설계되었습니다.
   * 다음 문서는 현대 UI에 중점을 둡니다. 클래식 UI의 작성에 대한 자세한 내용은 ](/help/sites-classic-ui-authoring/classicui.md)클래식 UI의 작성 설명서[를 참조하십시오.

   ![chlimage_1-232](assets/chlimage_1-232.png)

## UI 전환

Although the touch-enabled UI is now the standard UI and [feature parity](../release-notes/touch-ui-features-status.md) has been nearly reached with the administration and editing of sites, there may be times when the user wishes to switch to the [classic UI](/help/sites-classic-ui-authoring/classicui.md). 이를 위해 몇 가지 옵션을 제공합니다.

>[!NOTE]
>
>클래식 UI의 기능 패리티 상태에 대한 자세한 내용은 [터치 UI 기능 패리티](../release-notes/touch-ui-features-status.md) 문서를 참조하십시오.

어느 UI를 사용해야 하는지를 결정할 수 있는 다양한 위치가 있습니다.

* [인스턴스용](#configuring-the-default-ui-for-your-instance) 기본 UI 구성 - 사용자가 이 설정을 무시할 수 있고 계정 또는 현재 세션에 대해 다른 UI를 선택할 수 있지만 사용자 로그인 시 기본 UI가 표시되도록 설정됩니다.

* [계정에](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) 대한 클래식 UI 작성 설정 - 이 설정을 사용하면 페이지 편집 시 UI가 기본적으로 사용되도록 설정됩니다. 사용자는 이 설정을 무시할 수 있으며 계정 또는 현재 세션에 대해 다른 UI를 선택할 수 있습니다.

* [현재 세션에 대한 클래식 UI로 전환](#switching-to-classic-ui-for-the-current-session) - 현재 세션에 대한 클래식 UI로 전환합니다.

* 페이지 작성의 경우 [UI와 관련하여 특정 항목이 무시됩니다.](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>클래식 UI로 전환에 대한 여러 옵션은 즉시 사용할 수 없습니다. 인스턴스에 대해 특별히 구성되어 있어야 합니다.
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

>[!NOTE]
>
>이전 버전에서 업그레이드된 인스턴스는 페이지 작성을 위해 클래식 UI를 유지합니다.
>
>After upgrade, page authoring will not be automatically switched to the touch-enabled UI, but you can configure this using the [OSGi configuration](/help/sites-deploying/configuring-osgi.md) of the **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). [편집기에 대해 UI 무시](#ui-overrides-for-the-editor)를 참조하십시오.

## 인스턴스용 기본 UI 구성 {#configuring-the-default-ui-for-your-instance}

시스템 관리자는 [루트 매핑](/help/sites-deploying/osgi-configuration-settings.md)을 사용하여 시작 및 로그인 시 표시되는 UI를 구성할 수 있습니다.

사용자 기본값이나 세션 설정에 의해 무시될 수 있습니다.

## 계정용 클래식 UI 작성 설정 {#setting-classic-ui-authoring-for-your-account}

각 사용자는 [사용자 환경 설정](/help/sites-authoring/user-properties.md)에 액세스하여 페이지 작성을 위해 클래식 UI를 사용할지 여부를 정의할 수 있습니다(기본 UI 대신).

세션 설정에 의해 무시될 수 있습니다.

## 현재 세션을 위해 클래식 UI로 전환 {#switching-to-classic-ui-for-the-current-session}

터치 지원 UI 사용 시 데스크톱 사용자는 클래식(데스크톱 전용) UI로 되돌릴 수 있습니다. 현재 세션에 대한 클래식 UI로 전환하는 방법에는 몇 가지가 있습니다.

* **탐색 링크**

   >[!CAUTION]
   >
   >클래식 UI로 전환에 대한 이 옵션은 즉시 사용할 수 없습니다. 인스턴스에 대해 특별히 구성되어 있어야 합니다.
   >
   >
   >See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

   활성화한 경우, 적용 가능한 콘솔에 마우스 커서를 가져다 댈 때마다 아이콘(모니터 기호)이 표시되며, 이 아이콘을 탭/클릭하는 경우 클래식 UI에서 해당 위치가 열립니다.

   예: **siteadmin**&#x200B;에 대한 **사이트**&#x200B;의 링크

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   The classic UI can be accessed using the URL for the welcome screen at `welcome.html`. For example:

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >터치 지원 UI는 `sites.html`을 통해 액세스할 수 있습니다. 예:
   >
   >
   >`http://localhost:4502/sites.html`

### 페이지 편집 시 클래식 UI로 전환 {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>클래식 UI로 전환에 대한 이 옵션은 즉시 사용할 수 없습니다. 인스턴스에 대해 특별히 구성되어 있어야 합니다.
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

활성화된 경우 **페이지 정보** 대화 상자에서 **클래식 UI로 열기**&#x200B;를 사용할 수 있습니다.

![chlimage_1-49](assets/chlimage_1-49.png)

### 편집기에 대해 UI 무시 {#ui-overrides-for-the-editor}

사용자나 시스템 관리자가 정의한 설정은 페이지 작성 시 시스템에 의해 무시될 수 있습니다.

* 페이지 작성 시:

   * Use of the classic editor is forced when accessing the page using `cf#` in the URL. 예:

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Use of the touch-enabled editor is forced when using `/editor.html` in the URL or when using a touch device. 예:

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* 이러한 강제성은 모두 일시적이며 브라우저 세션에 대해서만 유효합니다.

   * A cookie set will be set dependent on whether touch-enabled ( `editor.html`) or classic ( `cf#`) is used.

* `siteadmin`을 통해 페이지를 열 때에는 다음 항목이 있는지 확인하게 됩니다.

   * 쿠키
   * 사용자 환경 설정
   * 어느 쪽도 없을 경우에는, [WCM 작성 UI 모드 서비스](/help/sites-deploying/configuring-osgi.md)(**서비스)의** OSGi 구성`AuthoringUIMode`에 설정된 정의가 기본값이 됩니다. 

>[!NOTE]
>
>사용자가 [페이지 작성에 대한 환경 설정을 이미 정의한 경우 ](#setting-classic-ui-authoring-for-your-account)OSGi 속성을 변경하여 무시할 수 없습니다.

>[!CAUTION]
>
>위의 설명처럼 쿠키의 사용 때문에 다음 중 어느 것도 권장되지 않습니다.
>
>* URL 수동 편집. 비표준 브라우저 URL은 알 수 없는 상황과 기능 부족을 초래할 수 있습니다.
>* 두 편집기를 동시에 열기. 예를 들어 별도의 창으로 엽니다.

>



