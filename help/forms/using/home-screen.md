---
title: 홈 화면
seo-title: Home screen
description: AEM Forms 앱 홈 화면의 구성 요소에 대한 설명
seo-description: Description of the components of the AEM Forms app Home screen
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# 홈 화면 {#home-screen}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 앱에 로그인하면 홈 화면으로 리디렉션됩니다.

## 기본 홈 화면 {#default-home-screen}

기본적으로 홈 화면에는 연결된 축소판과 함께 시작 지점 및 작업(연결된 서버가 AEM Forms Workflow가 활성화된 경우)을 포함한 모든 양식이 표시됩니다. AEM Forms 서버에서 미리 보기를 지정할 수 있습니다.

다음 그림은 기본 홈 화면의 필수 구성 요소에 대한 콜아웃과 함께 주석을 달았습니다.
![Forms 앱 홈 화면](assets/home-screen-1.png)
[확대하려면 클릭](assets/home-screen-1-1.png)

1. **메뉴 단추**: 탭하기 **메뉴** 작업, Forms, Outbox 및 설정으로 이동하는 단추. AEM Forms 앱이 AEM Forms JEE 서버에 연결된 경우 작업 옵션을 볼 수 있습니다. 작업 옵션은 작업에서 생성된 초안을 프로세스에 저장합니다. AEM Forms OSGi 서버의 경우 작업 옵션이 표시되지 않습니다. 보낼 편지함은 서버와 동기화되기 전에 저장된 양식과 초안을 저장합니다. 보낼 편지함에 있는 저장된 모든 양식 및 초안은 앱이 있을 때 AEM Forms 서버에 업로드됩니다 [서버와 동기화](/help/forms/using/sync-app.md). 설정에 대한 자세한 내용은 [일반 설정 업데이트](/help/forms/using/update-general-settings.md).
1. **작업 또는 양식**: 작업할 나열된 작업 또는 양식을 누릅니다.
1. **가로 줄임표**: 양식에 작업을 사용할 수 있음을 나타냅니다. 생략 부호를 탭하면 제공된 작업 및 설명 작성자가 표시됩니다. 다음 **초안 삭제** 및 **완료** 생략 부호를 탭하면 옵션이 표시됩니다.
1. **새로 고침 아이콘**: 앱을 AEM Forms 서버와 동기화하려면 새로 고침 아이콘을 탭합니다.

## 홈 화면 사용자 지정 {#customizing-the-home-screen}

![일반 설정](assets/gen-settings.png)

앱에서 또는 **[일반 설정](/help/forms/using/update-general-settings.md)** 앱 또는 **기본 설정** HTML 작업 공간 의 탭입니다.

앱에서 홈 화면 설정을 변경하면 현재 로그인한 사용자 또는 현재 모바일 장치의 홈 화면에 영향을 줍니다.

그러나 Analysis Workspace에서 변경된 사항은 AEM Forms 서버에 로그온한 모든 AEM Forms 앱 사용자에게 영향을 줍니다.
