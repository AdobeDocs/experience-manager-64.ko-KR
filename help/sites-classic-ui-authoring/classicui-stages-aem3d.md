---
title: AEM 3D의 스테이지 사용에 대하여
seo-title: AEM 3D의 스테이지 사용에 대하여
description: 스테이지는 기본 보기 환경(광원, 배경, 지표 평면 또는 기타 고정 기하학적 구조), 선택 사항인 사전 정의된 카메라, 타사 렌더러에 대한 렌더링 설정을 제공하는 경량 3D 장면 파일입니다.
seo-description: 스테이지는 기본 보기 환경(광원, 배경, 지표 평면 또는 기타 고정 기하학적 구조), 선택 사항인 사전 정의된 카메라, 타사 렌더러에 대한 렌더링 설정을 제공하는 경량 3D 장면 파일입니다.
uuid: 303ecbbd-131e-4c6f-812a-1e056b1e1d63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: cbcfbe88-e60c-446c-bbfe-2509831d6c22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 91%

---


# AEM 3D의 스테이지 사용에 대하여{#about-the-use-of-stages-in-aem-d}

스테이지는 기본 보기 환경(광원, 배경, 지표 평면 또는 기타 고정 기하학적 구조), 선택 사항인 사전 정의된 카메라, 타사 렌더러에 대한 렌더링 설정을 제공하는 경량 3D 장면 파일입니다.

>[!NOTE]
>
>OBJ 3D 형식은 광원을 지원하지 않습니다. 따라서, AEM 3D에 스테이지를 제공하는 데 사용할 수 없습니다.

스테이지의 파일 형식은 해당 스테이지에 사용할 수 있는 렌더러를 판별합니다. For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. 기본 Rapid Refine™ 렌더러만 사용하려는 경우에는 지원되는 스테이지 파일 형식이 허용됩니다.

출력 이미지 유형 및 크기를 제외한 AEM 3D의 모든 렌더링 설정은 사전에 구성하고 AEM에 업로드하기 전에 스테이지 파일로 저장해야 합니다.

