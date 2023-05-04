---
title: AEM Forms 앱용 환경 설정
seo-title: Set up environment for AEM Forms app
description: AEM Forms 앱을 빌드하고 배포할 하드웨어, 소프트웨어 및 라이센스입니다.
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%

---

# AEM Forms 앱용 환경 설정 {#set-up-environment-for-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 앱을 빌드하고 배포하려면 다음 하드웨어, 소프트웨어 및 라이센스가 필요합니다.

## Windows 장치의 경우 {#for-windows-devices}

* Microsoft Windows 8.1 또는 Windows 10
* Microsoft Visual Studio 2015
* Apache Cordova용 Microsoft Visual Studio 도구

## iOS 장치 {#for-ios-devices}

* Mac OS X 10.9.5 이상을 실행하는 인텔 기반 Apple Mac
* iOS SDK 8.4 이상
* Xcode 버전: OS X 이상용 Xcode 6.4
* iOS Developer Enterprise 프로그램의 멤버십
* 사내 iOS 앱 배포를 위한 엔터프라이즈 인증서
* Apple iPad과 iOS 8.4 이상

## Android 장치의 경우 {#for-android-devices}

* 에서 다운로드할 수 있는 Android Development Toolkit(ADT 번들) [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* MAC 시스템에 환경이 설정된 경우 Applications 폴더에 ADT를 설치해야 합니다.
* ADT가 MAC의 다른 위치에 설치되어 있거나 Windows 시스템에서 환경이 설정된 경우 ADT SDK 경로를 업데이트해야 합니다. `local.properties` 에서 사용할 수 있는 파일 `src\android` 추출된 소스 아카이브의 폴더 `mobileworkspace-src.zip`. 이 파일에서 `sdk.dir` 변수를 데스크탑 ADT SDK 위치에 추가합니다.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip에 PhoneGap SDK 5.0이 포함되어 있습니다. PhoneGap SDK가 사전 설치되어 있지 않은지 확인하십시오.
