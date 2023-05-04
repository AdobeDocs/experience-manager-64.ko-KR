---
title: 소셜 그래프 사용
seo-title: Using Social Graph
description: 페이지에 다음 구성 요소 추가
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 5%

---

# 소셜 그래프 사용 {#using-social-graph}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

커뮤니티 구성원이 수행할 수 있는 기능 [활동](activities.md) 또한 다음 두 가지 구성 요소를 통해 구축됩니다. `Follow`및 `Following`.

다음 `Follow`구성 요소는 다른 리소스와 연결되어야 하며 이 연결은 이미 커뮤니티 구성원 및 기능에 대해 설정되어 있습니다.

다음 `Following`구성 요소는 현재 멤버를 따르거나 현재 멤버가 뒤에 오는 멤버만 나열합니다. 멤버 간의 관계에 대한 이 소셜 그래프는 [커뮤니티 사이트](overview.md#communitiessites).

## 페이지에 다음 추가 {#adding-following-to-a-page}

를 추가하려면 `Following`구성 요소를 페이지에 작성자 모드에서 찾아 구성 요소를 찾습니다 `Communities / Following` 소셜 그래프가 표시되는 페이지에 드래그합니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md).

이 [필수 클라이언트 측 라이브러리](essentials-socialgraph.md#essentials-for-client-side) 포함된 경우, 다음과 같이 하십시오 `Following` 구성 요소가 표시됩니다.

![chlimage_1-447](assets/chlimage_1-447.png)

## 다음 구성 {#configuring-following}

현재 속성을 설정하여 구성 요소에 `follows`관계 또는 `following`관계.

## 추가 정보 {#additional-information}

자세한 내용은 [소셜 그래프 핵심 사항](essentials-socialgraph.md) 개발자를 위한 페이지입니다.
