---
title: 배지 콘솔
seo-title: 배지 콘솔
description: Communities Badge 콘솔을 사용하면 수익을 낼 때(수상) 또는 커뮤니티에서 특정 역할을 수행할 때(지정된) 회원에게 표시될 수 있는 사용자 지정 배지를 추가할 수 있습니다
seo-description: Communities Badge 콘솔을 사용하면 수익을 낼 때(수상) 또는 커뮤니티에서 특정 역할을 수행할 때(지정된) 회원에게 표시될 수 있는 사용자 지정 배지를 추가할 수 있습니다
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Administrator
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---

# 배지 콘솔 {#badges-console}

## 배지 정보 {#about-badges}

Communities Badge 콘솔에서는 수익을 내거나 커뮤니티에서 특정 역할을 수행할 때(지정된) 회원에게 표시될 수 있는 사용자 지정 배지를 추가하는 기능을 제공합니다.

### 배지 가시성 {#badge-visibility}

현재, 한 커뮤니티 구성원이 번거나 배정되는 배지는 다음 위치에 그들의 이름과 아바타와 함께 나타납니다.

* 프로파일
* [포럼](forum.md)
* [QnA](working-with-qna.md)
* [리드보드](enabling-leaderboard.md)
* [관념화](ideation-feature.md)

작성 환경에서 Badge 콘솔에 연결합니다

* 전역 탐색에서:**[!UICONTROL 도구 > 커뮤니티 > Badge]**

이 콘솔에는 현재 사용 가능한 배지와 새 배지를 추가할 수 있는 배지가 표시됩니다.

![chlimage_1-242](assets/chlimage_1-242.png)

## 배지 만들기 {#create-badge}

배지는 26~32픽셀 범위의 높이로 적절하게 작은 이미지(72dpi)를 업로드하고 이름을 제공하여 만들어집니다. 배지 이미지는 `/etc/community/badging/images`의 리포지토리에 저장되며 게시 환경에 자동으로 복제됩니다.

게시 환경이 게시자의 팜인 경우 [사용자 동기화](sync.md)를 구성해야 합니다.

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL 이미지 업로드]**

   (*필수*) 72dpi에서 32 x 32픽셀(JPEG 또는 PNG 형식)의 배지 이미지입니다.

* **[!UICONTROL 이름]**

   (*필수*) 배지 이름입니다. 저장소 노드 이름과 기본 `Display Name` 입니다. `Name` 이 유효한 저장소 노드 이름이 아닌 경우 수정됩니다.

* **[!UICONTROL 표시 이름]**

   (*선택 사항*) UI에서 배지에 대해 표시할 이름입니다. 기본값은 `Name`에 대해 입력한 변경되지 않은 텍스트입니다.

* **[!UICONTROL 설명]**

   (*선택 사항*) 배지에 대한 설명입니다.

## 추가 정보 {#additional-information}

점수 및 배지 규칙 설정에 대한 자세한 내용은 [점수 및 배지](implementing-scoring.md)를 참조하십시오.

구성원에 대한 배지를 관리하려면 [구성원 콘솔](members.md)을 참조하십시오.
