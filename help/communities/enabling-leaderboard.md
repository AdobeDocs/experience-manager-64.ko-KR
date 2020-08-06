---
title: 리드 보드 기능
seo-title: 리드 보드 기능
description: 페이지에 리드 보드 구성 요소 추가
seo-description: 페이지에 리드 보드 구성 요소 추가
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 7%

---


# 리드 보드 기능 {#leaderboard-feature}

## 소개 {#introduction}

구성 요소는 `Leaderboard` 획득한 점수(기본 점수) 또는 해당 전문 지식(고급 점수)에 따라 구성원을 순위를 매기면서 커뮤니티 내에서 구성원이 상호 작용하는 방식을 파악하는 기능을 제공합니다.

페이지에 리더보드 구성 요소를 포함하기 전에 [커뮤니티 점수 및 배지를 구성해야 합니다](implementing-scoring.md).

설명서의 이 섹션에서는

* 커뮤니티 사이트에 구성 `Leaderboard` 요소 [추가](overview.md#community-sites)

* 구성 요소에 대한 `Leaderboard` 구성 설정

## Adding a Leaderboard to a Page {#adding-a-leaderboard-to-a-page}

작성 모드에서 페이지에 `Leaderboard` 구성 요소를 추가하려면 구성 요소를 찾습니다

* `Communities / Leaderboard`

페이지로 드래그하여 놓습니다.

필요한 정보를 보려면 커뮤니티 구성 요소 [기본 사항을 방문하십시오](basics.md).

커뮤니티 사이트의 페이지에 처음 배치하면 구성 요소가 표시되는 방식입니다.

![chlimage_1-8](assets/chlimage_1-8.png)

## 리드 보드 구성 {#configuring-leaderboard}

액세스할 배치된 `Leaderboard` 구성 요소를 선택하고 편집 대화 상자를 여는 `Configure` 아이콘을 선택합니다.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### 설정 탭 {#settings-tab}

설정 **[!UICONTROL 탭]** 아래에서, 멤버와 관련된 정보를 표시할 정보를 지정합니다.

* **[!UICONTROL 표시 이름]**&#x200B;배지 및 점수를 표시하기 위해 선택한 규칙을 반영하여 보드에 표시할 설명형 이름입니다.

   기본값은 입력한 내용이 `Leaderboard`없는 경우 입니다.

* **[!UICONTROL 배지]**&#x200B;이 선택된 경우 배지 아이콘에 대한 열이 리더보드에 포함됩니다.

   기본값은 선택 취소입니다.

* **[!UICONTROL 배지 이름]**&#x200B;이 선택된 경우 배지 이름의 열이 리더보드에 포함됩니다.

   기본값은 선택 취소입니다.

* **[!UICONTROL 아바타]**&#x200B;사용 이 확인란을 선택하면 멤버의 아바타 이미지가 구성원 프로필에 대한 이름 링크 옆에 있는 리더보드에 포함됩니다.

   기본값은 선택 취소입니다.

### 규칙 탭 {#rules-tab}

규칙 **[!UICONTROL 탭]** 아래에서 커뮤니티 사이트, 점수 및 배지 규칙

* **[!UICONTROL 규칙 위치]**(필수) 점수/배지 규칙이 구성된 위치입니다.

* **[!UICONTROL 점수 지정 규칙]**(필수) 표시할 점수를 생성하는 특정 규칙입니다.

* **[!UICONTROL 배지 규칙]**(필수) 표시할 배지를 생성하는 특정 규칙입니다.

* **[!UICONTROL 표시 제한]**&#x200B;페이지당 표시할 구성원 수입니다.

   기본값은 10입니다.

## 예: 참가자 경영진 {#example-participants-leaderboard}

이 리더보드 보고서는 기본 점수 지정 규칙을 적용한 결과를 보고합니다.

리드 보드 구성:

* **[!UICONTROL 설정]** 탭:

   * 표시 이름 = `Participation Board`
   * `checked`:

      * 배지
      * 배지 이름
      * 아바타 사용

* **[!UICONTROL 규칙]** 탭:

   * 규칙 위치 = `/content/sites/communities/jcr:content`
   * 점수 지정 규칙 = `/etc/community/scoring/rules/forums-scoring`
   * 배지 규칙 = `/etc/community/badging/rules/reference-badging`
   * 표시 제한 = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## 예: 전문가 경영진 {#example-experts-leaderboard}

이 리더보드 보고서는 고급 점수 지정 규칙을 적용한 결과를 보고합니다.

리드 보드 구성:

* **[!UICONTROL 설정]** 탭:

   * 표시 이름 = `Expertise Board`
   * `checked`:

      * 배지
      * 아바타 사용

* **[!UICONTROL 규칙]** 탭:

   * 규칙 위치 = `/content/sites/communities/jcr:content`
   * 점수 지정 규칙 = `/etc/community/scoring/rules/adv-forums-scoring`
   * 배지 규칙 = `/etc/community/badging/rules/adv-forums-badging`
   * 표시 제한 = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## 추가 정보 {#additional-information}

개발자를 위한 Leaderboard Essentials [페이지에](leaderboard.md) 대한 자세한 내용이 나와 있습니다.

규칙 만들기에 대한 지침은 관리자를 위한 [커뮤니티 점수 및 배지](implementing-scoring.md) 페이지에 제공됩니다.
