---
title: 홈 화면
seo-title: 홈 화면
description: AEM Forms 앱 홈 화면의 구성 요소에 대한 설명
seo-description: AEM Forms 앱 홈 화면의 구성 요소에 대한 설명
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# 홈 화면 {#home-screen}

AEM Forms 앱에 로그인하면 홈 화면으로 리디렉션됩니다.

## 기본 홈 화면 {#default-home-screen}

기본적으로 홈 화면에는 시작 지점 및 작업(연결된 서버가 AEM Forms 워크플로우가 활성화된 경우)을 포함한 모든 양식과 연관된 축소판이 표시됩니다. AEM Forms 서버에서 축소판을 지정할 수 있습니다.

다음 그림은 기본 홈 화면에서 기본 구성 요소에 대한 설명으로 주석을 달 수 있습니다.
![Forms 앱 홈 화면](assets/home-screen-1.png)[을 클릭하여 확대](assets/home-screen-1-1.png)

1. **메뉴 단추**: 메뉴 **단추를** 눌러 작업, Forms, 보낼 편지함 및 설정으로 이동합니다. AEM Forms 앱이 AEM Forms JEE 서버에 연결되어 있는 경우 작업 옵션을 볼 수 있습니다. 작업 옵션은 프로세스의 작업에서 생성된 초안을 저장합니다. AEM Forms OSGi 서버의 경우 작업 옵션이 숨겨집니다. 출력소는 저장된 양식과 초안을 서버와 동기화하기 전에 저장합니다. 앱이 서버와 [동기화되면 보낼 편지함에 저장된 모든 양식과 초안이 AEM Forms 서버에](/help/forms/using/sync-app.md)업로드됩니다. 설정에 대한 자세한 내용은 일반 [설정 업데이트를 참조하십시오](/help/forms/using/update-general-settings.md).
1. **작업 또는 양식**: 작업할 나열된 작업 또는 양식을 누릅니다.
1. **수평 줄임표**: 양식에서 작업을 사용할 수 있음을 나타냅니다. 줄임표를 누르면 작성자가 제공한 작업 및 설명이 표시됩니다. 초안 **삭제** 및 **전체** 옵션은 줄임표를 누를 때 볼 수 있습니다.
1. **새로 고침 아이콘**: 새로 고침 아이콘을 눌러 앱을 AEM Forms 서버와 동기화합니다.

## 홈 화면 사용자 정의 {#customizing-the-home-screen}

![일반 설정](assets/gen-settings.png)

앱의 **[일반 설정](/help/forms/using/update-general-settings.md)**또는 HTML 작업 영역의&#x200B;**기본 설정**탭에서 앱의 기본 홈 화면을 변경할 수 있습니다.

앱의 홈 화면 설정이 변경되면 현재 로그인한 사용자 또는 현재 모바일 장치의 사용자에 대한 홈 화면이 나타납니다.

그러나 HTML 작업 영역의 변경 사항은 모든 AEM Forms 앱 사용자가 AEM Forms 서버에 로그온한 영향을 줍니다.

