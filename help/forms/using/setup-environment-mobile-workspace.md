---
title: AEM Forms 앱용 환경 설정
seo-title: AEM Forms 앱용 환경 설정
description: AEM Forms 앱을 빌드하고 배포할 하드웨어, 소프트웨어 및 라이센스.
seo-description: AEM Forms 앱을 빌드하고 배포할 하드웨어, 소프트웨어 및 라이센스.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# AEM Forms 앱용 환경 설정 {#set-up-environment-for-aem-forms-app}

AEM Forms 앱을 빌드하고 배포하려면 다음 하드웨어, 소프트웨어 및 라이선스가 필요합니다.

## Windows 장치의 경우 {#for-windows-devices}

* Microsoft Windows 8.1 또는 Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## iOS 장치용 {#for-ios-devices}

* Mac OS X 10.9.5 이상을 실행하는 Intel 기반 Apple Mac
* iOS SDK 8.4 이상
* Xcode 버전: OS X 이상용 Xcode 6.4
* iOS Developer Enterprise 프로그램의 멤버십
* 사내 iOS 앱 배포를 위한 기업 인증서
* iOS 8.4 이상이 설치된 Apple iPad

## Android 장치용 {#for-android-devices}

* https://developer.android.com/sdk/index.html에서 다운로드할 수 있는 Android Development Toolkit(ADT 번들) [](https://developer.android.com/sdk/index.html)
* MAC 시스템에 환경이 설정되어 있는 경우 응용 프로그램 폴더에 ADT가 설치되어 있어야 합니다.
* ADT가 MAC의 다른 위치에 설치되어 있거나 Windows 시스템에 환경이 설정되어 있는 경우 소스 아카이브의 압축을 푼 폴더에 있는 `local.properties` 파일에서 ADT SDK 경로를 `src\android` 업데이트해야 합니다 `mobileworkspace-src.zip`. 이 파일에서 `sdk.dir` 변수를 데스크탑에서 ADT SDK 위치로 가리킵니다.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip에 PhoneGap SDK 5.0이 포함되어 있습니다. PhoneGap SDK가 미리 설치되지 않았는지 확인하십시오.
