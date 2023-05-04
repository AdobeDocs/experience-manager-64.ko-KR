---
title: UI 선택
seo-title: Selecting your UI
description: AEM에서 작업하는 데 사용할 인터페이스를 구성합니다
seo-description: Configure which interface you will use to work in AEM
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
exl-id: 415efbe0-95f5-4c9e-ac33-c4a384a8271e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 3%

---

# UI 선택{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## UI 이해

작성 환경에서는 다음 작업을 수행할 수 있습니다.

* [작성](/help/sites-authoring/author.md) (포함) [페이지 작성](/help/sites-authoring/author-environment-tools.md), [자산 관리](/help/assets/home.md), [커뮤니티](/help/communities/author-communities.md))

* [관리](/help/sites-administering/home.md) 웹 사이트에서 컨텐츠를 생성하고 유지 관리할 때 필요한 작업

이를 위해 두 개의 그래픽 사용자 인터페이스가 제공됩니다. 최신 브라우저를 통해 액세스할 수 있습니다.

1. 터치 활성화 UI

   * 최신 기본 AEM UI입니다.
   * 대개 회색이며 깔끔하고 평면 인터페이스입니다.
   * 터치 및 데스크톱 장치에서 모두 사용하도록 설계되었지만 모든 장치에서 모양과 느낌은 동일합니다 [리소스 보기 및 선택](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) 약간 다릅니다(탭과 클릭).

      * 데스크탑:

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * 태블릿 장치(또는 폭이 1024픽셀 미만인 데스크톱):

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. 클래식 UI

   * 레거시 UI이며 수년 동안 AEM에서 사용할 수 있습니다.
   * 주로 녹색입니다.
   * 데스크탑 장치에서 사용하도록 설계되었습니다.
   * 다음 설명서는 최신 UI에 중점을 둡니다. 클래식 UI의 작성에 대한 자세한 내용은 [클래식 UI에 대한 설명서 작성](/help/sites-classic-ui-authoring/classicui.md).

   ![chlimage_1-232](assets/chlimage_1-232.png)

## UI 전환

터치 지원 UI가 이제 표준 UI이고 [기능 패리티](../release-notes/touch-ui-features-status.md) 사이트 관리 및 편집에 거의 도달했습니다. 사용자가 로 전환하려는 경우가 있을 수 있습니다 [클래식 UI](/help/sites-classic-ui-authoring/classicui.md). 이를 위해 몇 가지 옵션이 있습니다.

>[!NOTE]
>
>클래식 UI의 기능 패리티 상태에 대한 자세한 내용은 [터치 UI 기능 패리티](../release-notes/touch-ui-features-status.md) 문서.

사용할 UI를 정의할 수 있는 다양한 위치가 있습니다.

* [인스턴스에 대한 기본 UI 구성](#configuring-the-default-ui-for-your-instance) - 사용자가 이 설정을 재정의하고 계정 또는 현재 세션에 대해 다른 UI를 선택할 수 있지만, 이렇게 하면 사용자 로그인 시 기본 UI가 표시되도록 설정됩니다.

* [계정용 클래식 UI 작성 설정](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) - 이 설정을 사용하면 사용자가 이 설정을 재정의하고 계정 또는 현재 세션에 대해 다른 UI를 선택할 수 있지만 페이지를 편집할 때 기본적으로 사용할 UI가 설정됩니다.

* [현재 세션에 대한 클래식 UI로 전환](#switching-to-classic-ui-for-the-current-session) - 현재 세션에 대한 클래식 UI로 전환합니다.

* 의 경우 [시스템을 작성하는 페이지는 UI와 관련하여 특정 항목을 무시합니다](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>클래식 UI로 전환하는 다양한 옵션은 즉시 사용할 수 없습니다. 인스턴스에 대해 특별히 구성되어 있어야 합니다.
>
>자세한 내용은 [클래식 UI에 대한 액세스 활성화](/help/sites-administering/enable-classic-ui.md) 추가 정보.

>[!NOTE]
>
>이전 버전에서 업그레이드된 인스턴스는 페이지 작성을 위해 클래식 UI를 유지합니다.
>
>업그레이드 후에 페이지 작성이 터치 지원 UI로 자동 전환되지 않지만 [OSGi 구성](/help/sites-deploying/configuring-osgi.md) 의 **WCM 작성 UI 모드 서비스** ( `AuthoringUIMode` 서비스). 자세한 내용은 [편집기에 대해 UI 무시](#ui-overrides-for-the-editor).

## 인스턴스에 대한 기본 UI 구성 {#configuring-the-default-ui-for-your-instance}

시스템 관리자는 를 사용하여 시작 및 로그인 시 표시되는 UI를 구성할 수 있습니다 [루트 매핑](/help/sites-deploying/osgi-configuration-settings.md).

사용자 기본값이나 세션 설정에 의해 대체할 수 있습니다.

## 계정용 클래식 UI 작성 설정 {#setting-classic-ui-authoring-for-your-account}

각 사용자가 자신의 액세스 권한을 갖습니다 [사용자 환경 설정](/help/sites-authoring/user-properties.md) 페이지 작성에 클래식 UI를 사용할지 여부를 정의합니다(기본 UI 대신).

세션 설정에 의해 무시될 수 있습니다.

## 현재 세션에 대한 클래식 UI로 전환 {#switching-to-classic-ui-for-the-current-session}

터치 지원 UI를 사용할 때 데스크톱 사용자는 클래식(데스크톱 전용) UI로 되돌릴 수 있습니다. 현재 세션에 대한 클래식 UI로 전환하는 방법에는 몇 가지가 있습니다.

* **탐색 링크**

   >[!CAUTION]
   >
   >클래식 UI로 전환하는 이 옵션은 즉시 사용할 수 없습니다. 인스턴스에 대해 특별히 구성되어 있어야 합니다.
   >
   >
   >자세한 내용은 [클래식 UI에 대한 액세스 활성화](/help/sites-administering/enable-classic-ui.md) 추가 정보.

   이 옵션이 활성화되어 있으면 적용 가능한 콘솔 위에 마우스를 올려 놓을 때마다 아이콘(모니터 기호)이 나타나고, 이 아이콘을 탭/클릭하면 클래식 UI에서 해당 위치가 열립니다.

   예를 들어 의 링크가 **Sites** to **siteadmin**:

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   클래식 UI는 시작 화면의 URL을 사용하여 액세스할 수 있습니다. `welcome.html`. 예:

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >터치 지원 UI는 를 통해 액세스할 수 있습니다 `sites.html`. 예:
   >
   >
   >`http://localhost:4502/sites.html`

### 페이지를 편집할 때 클래식 UI로 전환 {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>클래식 UI로 전환하는 이 옵션은 즉시 사용할 수 없습니다. 인스턴스에 대해 특별히 구성되어 있어야 합니다.
>
>자세한 내용은 [클래식 UI에 대한 액세스 활성화](/help/sites-administering/enable-classic-ui.md) 추가 정보.

활성화된 경우 **클래식 UI 열기** 다음에서 사용 가능합니다. **페이지 정보** 대화 상자:

![chlimage_1-49](assets/chlimage_1-49.png)

### 편집기에 대해 UI 무시 {#ui-overrides-for-the-editor}

사용자 또는 시스템 관리자가 정의한 설정은 페이지 작성의 경우 시스템에 의해 덮어쓸 수 있습니다.

* 페이지를 작성할 때:

   * 클래식 편집기는 `cf#` 를 입력합니다. 예:

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * 사용할 때는 터치 지원 편집기를 사용할 수 밖에 없습니다 `/editor.html` 를 클릭하거나 터치 장치를 사용할 때 사용됩니다. 예:

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* 이러한 강제성은 모두 일시적이며 브라우저 세션에 대해서만 유효합니다

   * 설정된 쿠키는 터치 활성화( `editor.html`) 또는 classic( `cf#`사용)

* 페이지를 통과할 때 `siteadmin`은(는) 다음 항목이 있는지 확인하게 됩니다.

   * 쿠키
   * 사용자 환경 설정
   * 어느 쪽도 없을 경우에는, 기본적으로 [OSGi 구성](/help/sites-deploying/configuring-osgi.md) 의 **WCM 작성 UI 모드 서비스** ( `AuthoringUIMode` 서비스).

>[!NOTE]
>
>If [사용자가 페이지 작성에 대한 환경 설정을 이미 정의했습니다.](#setting-classic-ui-authoring-for-your-account): OSGi 속성을 변경하여 재정의되지 않습니다.

>[!CAUTION]
>
>이미 설명한 대로 쿠키의 사용으로 인해 다음 중 하나를 사용하지 않는 것이 좋습니다.
>
>* URL 수동 편집 - 비표준 URL은 알 수 없는 상황과 기능 부족을 초래할 수 있습니다.
>* 두 편집기를 동시에 열기. 예를 들어 별도의 창으로 엽니다.
>

