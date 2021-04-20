---
title: AEM 3D의 스테이지 사용에 대하여
seo-title: AEM 3D의 스테이지 사용에 대하여
description: 단계는 기본 보기 환경을 제공하는 크기가 작은 3D 장면 파일입니다.
seo-description: 단계는 기본 보기 환경을 제공하는 크기가 작은 3D 장면 파일입니다.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
exl-id: 6d82fec0-608e-4eaa-aebd-b3ce2f7d8088
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 55%

---

# AEM 3D의 스테이지 사용에 대하여 {#about-the-use-of-stages-in-aem-d}

스테이지는 기본 보기 환경(광원, 배경, 지표 평면 또는 기타 고정 기하학적 구조), 선택 사항인 사전 정의된 카메라, 타사 렌더러에 대한 렌더링 설정을 제공하는 경량 3D 장면 파일입니다.

>[!NOTE]
>
>**[!UICONTROL OBJ 3D]** 형식은 조명을 지원하지 않습니다. 따라서, AEM 3D에 스테이지를 제공하는 데 사용할 수 없습니다.

스테이지의 파일 형식은 해당 스테이지에 사용할 수 있는 렌더러를 판별합니다. 예를 들어 Autodesk® Maya®를 고품질 렌더링에 사용하는 경우 스테이지는 `.ma` 또는 `.mb` 형식이어야 합니다. 기본 Rapid Refine™ 렌더러만 사용하려는 경우에는 지원되는 스테이지 파일 형식이 허용됩니다.

출력 이미지 유형 및 크기를 제외한 AEM 3D의 모든 렌더링 설정은 AEM에 업로드하기 전에 미리 구성하고 스테이지 파일에 저장해야 합니다.
