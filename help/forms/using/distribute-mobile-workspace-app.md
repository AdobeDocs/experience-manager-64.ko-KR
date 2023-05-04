---
title: AEM Forms 앱 배포
seo-title: Distribute AEM Forms app
description: 모바일 장치에서 대규모 앱 배포에 모바일 장치 관리(MDM)를 사용합니다.
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: c1bf0a0e-70f7-41dd-8b1a-c114d89a265b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 2%

---

# AEM Forms 앱 배포 {#distribute-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

모바일 장치 관리(MDM)를 통해 모바일 장치에서 앱을 대규모로 배포할 수 있습니다.

>[!NOTE]
>
>이 배포는 iOS 및 Android 장치에만 적용됩니다.

## 일반적으로 MDM 솔루션에서 제공하는 주요 기능: {#main-features-generally-provided-by-mdm-solutions}

* 엔터프라이즈 환경에서 장치 등록 활성화
* 장치 설정 구성 및 업데이트 허용
* 보안 규정 준수
* 기업 리소스에 대한 안전한 모바일 액세스

Mobile Application Management와 함께 MDM 솔루션을 사용하면 기업의 모바일 장치에서 내부, 공용 및 구입한 앱을 관리할 수 있습니다.

MDM 관리자는 ipa 및 apk 파일을 모두 MDM 서버에 업로드하고 ipa 또는 apk 파일에 액세스할 수 있는 사용자를 제어할 수 있습니다. 관리자는 각 응용 프로그램에 해당하는 프로파일 설정을 제어할 수도 있습니다.

## AEM Forms 앱에 영향을 주는 프로필 설정 {#profile-settings-affecting-the-aem-forms-app-br}

장치에 대한 다음 프로필 설정은 장치에서 AEM Forms 앱의 기능에 영향을 줍니다.

* **카메라 사용 허용** 에서 **장치 기능** 섹션

비활성화한 경우 **카메라 사용 허용**, 의 카메라 기능 [사진 주석](/help/forms/using/add-attachments.md) 작동하지 않습니다. 앱에서 카메라를 사용하려면 이 옵션을 활성화해야 합니다.

* **장치에 암호 필요** 암호 정책 섹션에서

활성화하려면 **애플리케이션 데이터 암호화**&#x200B;를 사용 가능하도록 설정하는 것이 좋습니다 **암호** 디바이스 장치에서 암호 코드가 설정되지 않은 경우 장치에 저장된 응용 프로그램 데이터는 암호화되지 않습니다.
