---
title: Dynamic Media 설정
seo-title: Setting Up Dynamic Media
description: Dynamic Media를 설정하려면 Dynamic Media를 구성하고 이미지 및 뷰어 사전 설정을 관리해야 합니다
seo-description: To set up dynamic media, you need to configure dynamic media and manage image and viewer presets
uuid: bcd1f9ab-4201-4222-9e4a-ba82b3c7cd6c
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 36a4a4e7-8bb2-4853-b335-cf9148be410c
exl-id: dd43de7b-8556-4e3f-9d90-14f0f5bd13e7
feature: Configuration
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 6%

---

# Dynamic Media 설정 {#setting-up-dynamic-media}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 은 다양한 시각적 머천다이징 및 마케팅 자산을 웹, 모바일 및 소셜 사이트에 맞게 자동으로 크기를 조정하여 주문형으로 전달하여 자산을 관리하는 데 도움이 됩니다. 마스터 자산 세트를 사용하면 Dynamic Media은 글로벌, 확장 가능 및 성능 최적화 네트워크를 통해 실시간으로 다양한 유형의 풍부한 컨텐츠를 생성하고 전달합니다.

>[!NOTE]
>
>이 설명서는 AEM에 직접 통합된 Dynamic Media 기능에 대해 설명합니다. AEM에 통합된 Dynamic Media Classic을 사용하는 경우 다음을 참조하십시오 [Dynamic Media Classic 통합 설명서](/help/sites-administering/scene7.md).
>
>자세한 내용은 [듀얼 사용 시나리오](/help/sites-administering/scene7.md#dual-use-scenario) Dynamic Media과 함께 Dynamic Media Classic과 통합된 AEM을 사용할 수 있는 경우.

Dynamic Media를 관리하는 경우 다음 항목이 관심있습니다.

* [Dynamic Media-Scene7 모드 구성](config-dms7.md) - 새 Dynamic Media 고객인 경우 이 구성을 사용하십시오.
* [Dynamic Media-Hybrid 모드 구성](config-dynamic.md) - AEM을 업그레이드하는 기존 Dynamic Media 고객의 경우 이 구성을 사용합니다.
* [이미지 사전 설정 관리](managing-image-presets.md)
* [뷰어 사전 설정 관리](managing-viewer-presets.md)
* [Dynamic Media 문제 해결 - Scene7 모드](troubleshoot-dms7.md)

다음 항목도 참조하십시오.

* [비디오 인코딩 및 비디오 프로필](video-profiles.md)
* [이미지 프로필](image-profiles.md)

>[!NOTE]
>
>**업그레이드하는 경우:**
>
>* AEM을 실행 중이면 업로드하는 모든 자산에서 자동으로 Dynamic Media이 활성화됩니다(시스템 관리자가 명시적으로 비활성화하지 않은 경우). AEM의 업그레이드된 인스턴스에서 Dynamic Media으로 새로 작업하는 경우 자산을 다시 처리하여 Dynamic Media을 활성화할 수 있습니다.

