---
title: AEM Forms 앱용 환경 설정
seo-title: AEM Forms 앱용 환경 설정
description: AEM Forms 앱을 빌드하고 배포할 하드웨어, 소프트웨어 및 라이센스입니다.
seo-description: AEM Forms 앱을 빌드하고 배포할 하드웨어, 소프트웨어 및 라이센스입니다.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# AEM Forms 앱 {#set-up-environment-for-aem-forms-app} 환경 설정

AEM Forms 앱을 빌드하고 배포하려면 다음 하드웨어, 소프트웨어 및 라이센스가 필요합니다.

## Windows 장치의 경우 {#for-windows-devices}

* Microsoft Windows 8.1 또는 Windows 10
* Microsoft Visual Studio 2015
* Apache Cordova용 Microsoft Visual Studio Tools

## iOS 장치의 경우 {#for-ios-devices}

* Mac OS X 10.9.5 이상을 실행하는 Intel 기반 Apple Mac
* iOS SDK 8.4 이상
* Xcode 버전:OS X 이상용 Xcode 6.4
* iOS Developer Enterprise 프로그램의 멤버십
* 사내 iOS 앱 배포를 위한 엔터프라이즈 인증서
* iOS 8.4 이상 버전의 Apple iPad

## Android 장치의 경우 {#for-android-devices}

* [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)에서 다운로드할 수 있는 Android Development Toolkit (ADT 번들)
* MAC 시스템에서 환경을 설정한 경우 Applications 폴더에 ADT를 설치해야 합니다.
* ADT가 MAC의 다른 위치에 설치되어 있거나 Windows 시스템에서 환경을 설정한 경우 추출된 소스 아카이브 `mobileworkspace-src.zip`의 `src\android` 폴더에 있는 `local.properties` 파일에서 ADT SDK 경로를 업데이트해야 합니다. 이 파일에서 `sdk.dir` 변수를 바탕 화면에서 ADT SDK 위치를 가리킵니다.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip에 PhoneGap SDK 5.0이 포함되어 있습니다. PhoneGap SDK가 사전 설치되어 있지 않은지 확인하십시오.
