---
title: 배지 콘솔
seo-title: 배지 콘솔
description: 커뮤니티 배지 콘솔에서는 회원이 획득(수상)할 때 또는 커뮤니티(할당됨)에서 특정 역할을 수행할 때 표시할 수 있는 사용자 지정 배지를 추가할 수 있습니다
seo-description: 커뮤니티 배지 콘솔에서는 회원이 획득(수상)할 때 또는 커뮤니티(할당됨)에서 특정 역할을 수행할 때 표시할 수 있는 사용자 지정 배지를 추가할 수 있습니다
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---


# 배지 콘솔 {#badges-console}

## 배지 정보 {#about-badges}

커뮤니티 배지 콘솔은 회원이 획득(수상)할 때 또는 커뮤니티(지정)에서 특정 역할을 수행할 때 회원에게 표시할 수 있는 사용자 지정 배지를 추가하는 기능을 제공합니다.

### 배지 가시성 {#badge-visibility}

현재, 회원이 번 또는 할당된 커뮤니티 멤버가 다음 위치에 이름과 아바타와 함께 표시됩니다.

* 프로파일
* [포럼](forum.md)
* [QnA](working-with-qna.md)
* [리더보드](enabling-leaderboard.md)
* [관념화](ideation-feature.md)

작성 환경에서 Badges 콘솔에 도달하려면

* 전역 탐색에서:**[!UICONTROL 도구 > 커뮤니티 > 배지]**

이 콘솔에는 현재 사용 가능한 배지와 새 배지를 추가할 수 있는 배지가 표시됩니다.

![chlimage_1-242](assets/chlimage_1-242.png)

## 배지 만들기 {#create-badge}

배지는 26-32픽셀 높이의 적절하게 작은 이미지(72dpi)를 업로드하고 이름을 제공하여 만듭니다. 배지 이미지는 `/etc/community/badging/images`의 저장소에 저장되고 게시 환경에 자동으로 복제됩니다.

게시 환경이 게시자의 팜인 경우 [사용자 동기화](sync.md)를 구성해야 합니다.

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL 이미지 업로드]**

   (*필수*) JPEG 또는 PNG 형식의 권장 크기가 32 x 32픽셀인 배지 이미지입니다.

* **[!UICONTROL 이름]**

   (*필수*) 배지 이름입니다. 저장소 노드 이름은 물론 기본 `Display Name`입니다. `Name`이(가) 유효한 저장소 노드 이름이 아닌 경우 수정됩니다.

* **[!UICONTROL 표시 이름]**

   (*선택적*) UI에서 배지에 대해 표시할 이름입니다. 기본값은 `Name`에 대해 입력한 변경되지 않은 텍스트입니다.

* **[!UICONTROL 설명]**

   (*선택적*) 배지에 대한 설명입니다.

## 추가 정보 {#additional-information}

점수 지정 및 배지 규칙 설정에 대한 자세한 내용은 [점수 지정 및 배지](implementing-scoring.md)를 참조하십시오.

구성원에 대한 배지를 관리하려면 [구성원 콘솔](members.md)을 참조하십시오.
