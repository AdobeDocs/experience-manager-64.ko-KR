---
title: 비디오 표현물
description: 비디오 표현물
contentOwner: AG
feature: 비디오,표현물
role: 비즈니스 전문가
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 4%

---


# 비디오 표현물 {#video-renditions}

Adobe Experience Manager(AEM) Assets는 OGG, FLV 등 다양한 형식의 비디오 에셋에 대한 비디오 변환을 생성합니다.

AEM Assets은 미디어 자산에 대한 정적 및 동적 변환(DM 인코딩 변환)을 지원합니다.

정적 변환은 기본적으로 FFMPEG(시스템 경로에 설치되고 사용 가능)를 사용하여 생성되며 컨텐츠 저장소에 저장됩니다.

DM 인코딩 표현물은 프록시 서버에 저장되며 런타임 시 제공됩니다.

AEM 자산은 클라이언트측에서 이러한 변환에 대한 재생 지원을 제공합니다.

특정 비디오 자산의 변환을 보려면 해당 자산 페이지를 열고 전역 탐색 아이콘을 누릅니다. 그런 다음 목록에서 **[!UICONTROL 표현물]**&#x200B;을 선택합니다.

![chlimage_1-478](assets/chlimage_1-478.png)

비디오 표현물의 목록은 **[!UICONTROL 표현물]** 패널에 표시됩니다.

![chlimage_1-479](assets/chlimage_1-479.png)

DM 인코딩 변환에 대한 프록시 서버를 구성하려면 [Dynamic Media Cloud 서비스를 구성합니다.](config-dynamic.md)

원하는 매개 변수를 사용하여 비디오 변환을 생성하려면 [해당 비디오 프로필](video-profiles.md)을(를) 만드십시오.

프록시 서버를 구성하고 비디오 프로필을 만든 후 이 비디오 사전 설정을 처리 프로필에 포함시키고 처리 프로필을 폴더에 적용할 수 있습니다.

>[!NOTE]
>
>Internet Explorer 11의 OGG 및 WAV 파일에는 오디오 재생이 작동하지 않습니다. &quot;잘못된 소스&quot; 오류가 확장명이 OGG 또는 WAV인 자산에 대한 자산 세부 사항 페이지에 표시됩니다.
>
>MS Edge 및 iPad에서 OGG 파일이 재생되지 않고 지원되지 않는 형식 오류가 발생합니다.
