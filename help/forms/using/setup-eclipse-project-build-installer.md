---
title: AEM Forms Android 앱 빌드
seo-title: Build the AEM Forms Android app
description: Android Studio 프로젝트를 설정하고 Android용 AEM Forms 앱용 .apk 파일을 빌드하는 절차
seo-description: Steps to set up the Android Studio project and build the .apk file for the AEM Forms app for Android
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
exl-id: dbeed62e-eff1-47bc-b6da-cad543295170
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 8%

---

# AEM Forms Android 앱 빌드 {#build-the-aem-forms-android-app}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

권장 시퀀스에서 다음 단계를 수행하여 AEM Forms용 Android 앱을 빌드합니다.

1. [AEM Forms 앱 소스 코드 패키지 다운로드](#download-android-zip)
1. [환경 변수 설정](#set-environment-variable-android)
1. [표준 AEM Forms 앱 구축](#set-up-the-xcode-project)

## AEM Forms 앱 소스 코드 패키지 다운로드 {#download-android-zip}

AEM Forms 앱 소스 코드 패키지는 `adobe-lc-mobileworkspace-src-<version>.zip` 보관. 이 아카이브에는 사용자 지정 AEM Forms 앱을 빌드하는 데 필요한 소스 코드가 포함되어 있습니다. 아카이브는 `adobe-aemfd-forms-app-src-pkg-<version>.zip`소프트웨어 배포에서 사용할 수 있는 패키지입니다.

다음 단계를 수행하여 을 다운로드합니다. `adobe-aemfd-forms-app-src-pkg-<version>.zip` 파일:

1. [소프트웨어 배포](https://experience.adobe.com/downloads)를 엽니다. 소프트웨어 배포에 로그인하려면 Adobe ID가 필요합니다.
1. 헤더 메뉴에 제공된 **[!UICONTROL Adobe Experience Manager]**&#x200B;를 누릅니다.
1. 에서 **[!UICONTROL 필터]** 섹션:
   1. 선택 **[!UICONTROL Forms]** 에서 **[!UICONTROL 솔루션]** 드롭다운 목록.
   2. 패키지의 버전 및 유형을 선택합니다. 를 사용할 수도 있습니다 **[!UICONTROL 다운로드 검색]** 결과를 필터링하는 옵션.
1. 운영 체제에 해당하는 패키지 이름을 탭하고 **[!UICONTROL EULA 약관 동의]**, 탭 **[!UICONTROL 다운로드]**.
1. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)를 열고 **[!UICONTROL 패키지 업로드]**&#x200B;를 클릭하여 패키지를 업로드합니다.
1. 패키지를 선택하고 **[!UICONTROL 설치]**&#x200B;를 클릭합니다.
1. 소스 코드 아카이브를 다운로드하려면 **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** 브라우저에서 Android 앱 .zip 파일이 장치에 다운로드됩니다.
1. 로컬 파일 시스템의 폴더에 .zip 파일의 컨텐츠를 추출합니다. 예, *C:\Folder Structure\adobe-lc-mobileworkspace-src-2.4.20*

다음 이미지는 `adobe-lc-mobileworkspace-src-<version>.zip\android`폴더를 입력합니다.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## 환경 변수 설정 {#set-environment-variable-android}

AEM Forms 앱에 대한 빌드 프로세스를 시작하기 전에 다음 환경 변수를 설정하십시오.

* JAVA_HOME 환경 변수를 로컬 파일 시스템의 JDK 소프트웨어 위치로 설정합니다. 예: C:\Program Files\Java\jdk1.8.0_181
* 설정 `ANDROID_SDK_ROOT` 시스템 환경 변수를 Android용 SDK 위치에 지정합니다. 예: C:\Users\username\AppData\Local\Android\Sdk
* 설정 `Path` Android용 platform-tools 및 tools 폴더 위치를 포함하는 시스템 환경 변수입니다. 예: C:\Users\username\AppData\Local\Android\Sdk\platform-tools and C:\Users\username\AppData\Local\Android\Sdk\tools.

## 표준 AEM Forms 앱 구축 {#set-up-the-xcode-project}

adobe-lc-mobileworkspace-src를 저장했으면&lt;version>로컬 파일 시스템에서 .zip 파일을 설정하고 환경 변수를 설정하고 다음 옵션 중 하나를 사용하여 표준 AEM Forms Android 앱을 빌드합니다.

* [Android Studio를 사용하여 AEM Forms 앱 빌드](#using-android-studio)
* [Android Studio를 사용하여 .apk 파일 생성](#generate-apk-android-studio)

### Android Studio를 사용하여 AEM Forms 앱 빌드 {#using-android-studio}

Android Studio를 사용하여 AEM Forms 앱을 빌드하려면 다음 단계를 수행하십시오.

1. 컴퓨터에서 Android Studio 애플리케이션을 시작합니다.
1. 클릭 **기존 Android Studio 프로젝트를 엽니다.**. 기존 프로젝트를 여는 대화 상자가 자동으로 표시되지 않으면 **파일** > **열기**.
1. 다음으로 이동 *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* 로컬 파일 시스템에서 **확인**.

   다음 **android** 옵션이 왼쪽 창에 표시됩니다.

   ![android_folder_studio](assets/android_folder_studio.png)

1. 선택 **android** 왼쪽 창에서 **실행** > **&#39;android&#39;를 실행합니다.**.
1. 배포 Target 선택 대화 상자의 연결된 장치 섹션에서 Android 장치를 선택하고 확인을 클릭합니다.

   개발 환경을 성공적으로 빌드하면 이제 앱에 사용자 지정 사항을 적용할 수 있습니다. 다음 문서를 사용하여 앱을 사용자 지정합니다.

   * [브랜딩 사용자 지정](/help/forms/using/branding-customization.md)
   * [테마 사용자 지정](/help/forms/using/theme-customization.md)
   * [제스처 사용자 지정](/help/forms/using/gesture-customization.md)

   앱에 적절한 사용자 지정 사항을 적용한 후 배포할 .apk 파일을 생성할 수 있습니다.

### Android Studio를 사용하여 .apk 파일 생성 {#generate-apk-android-studio}

다음 단계를 실행하여 Android Studio를 사용하여 .apk 파일을 생성합니다.

1. 컴퓨터에서 Android Studio 애플리케이션을 시작합니다.
1. 선택 **기존 Android Studio 프로젝트를 엽니다.**. 기존 프로젝트를 여는 대화 상자가 자동으로 표시되지 않으면 **파일** > **열기**.
1. 다음으로 이동 *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* 로컬 파일 시스템에서 **확인**.

   왼쪽 창에 android 옵션이 표시됩니다.

1. 선택 **빌드** > **APK 빌드** .apk 파일을 생성합니다.

   선택(선택 사항) **빌드** > **서명된 APK 생성** 생성하다 [서명 버전](https://developer.android.com/studio/publish/app-signing) .apk 파일의 .apk 값을 반환합니다.

## Android Debug Bridge 사용 {#build-android-debug-bridge}

.apk 파일이 생성되면 다음 명령을 실행하여 [Android Debug Bridge](https://developer.android.com/tools/help/adb.html).

**Windows 사용자:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Mac 사용자:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
