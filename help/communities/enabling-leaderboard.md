---
title: 리드 보드 기능
seo-title: Leaderboard Feature
description: 페이지에 리드 보드 구성 요소 추가
seo-description: Adding a Leaderboard component to a page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 8%

---

# 리드 보드 기능 {#leaderboard-feature}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

다음 `Leaderboard` 구성 요소는 획득한 점수(기본 점수) 또는 전문 지식(고급 점수)에 따라 구성원이 커뮤니티 내에서 상호 작용하는 방법을 이해하는 기능을 제공합니다.

페이지에 리드 보드 구성 요소를 포함하기 전에 다음을 구성해야 합니다 [커뮤니티 점수 및 배지](implementing-scoring.md).

설명서의 이 섹션에서는 다음 사항에 대해 설명합니다

* 추가 `Leaderboard` 구성 요소를 [커뮤니티 사이트](overview.md#community-sites)

* 에 대한 구성 설정 `Leaderboard` 구성 요소

## 페이지에 리드 보드 추가 {#adding-a-leaderboard-to-a-page}

을(를) 추가하려면 `Leaderboard` 구성 요소를 페이지에 작성자 모드에서 찾아 구성 요소를 찾습니다

* `Communities / Leaderboard`

페이지로 끌어서 놓습니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md).

커뮤니티 사이트의 페이지에 처음 배치되면 구성 요소가 다음과 같이 나타납니다.

![chlimage_1-8](assets/chlimage_1-8.png)

## 리드 보드 구성 {#configuring-leaderboard}

배치된 항목을 선택합니다 `Leaderboard` 액세스하여 선택할 구성 요소 `Configure` 아이콘 편집 대화 상자를 엽니다.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### 설정 탭 {#settings-tab}

아래에 **[!UICONTROL 설정]** 탭에서 멤버와 관련된 정보가 표시되는 정보를 지정합니다.

* **[!UICONTROL 표시 이름]**
배지 및 점수를 표시하기 위해 선택한 규칙을 반영하며 보드에 표시할 설명 이름입니다.

   기본값은 입니다. `Leaderboard`입력한 내용이 없는 경우

* **[!UICONTROL 배지]**
이 확인란을 선택하면 배지 아이콘 열이 리더보드에 포함됩니다.

   기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 배지 이름]**
이 확인란을 선택하면 배지 이름에 대한 열이 리더보드에 포함됩니다.

   기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 아바타 사용]**
이 옵션을 선택하면 멤버의 아바타 이미지가 리더보드에 포함되며 구성원 프로필에 대한 이름 링크 옆에 있습니다.

   기본값은 선택 취소되어 있습니다.

### 규칙 탭 {#rules-tab}

아래에 **[!UICONTROL 규칙]** 탭, 커뮤니티 사이트, 점수 및 배지 규칙

* **[!UICONTROL 규칙 위치]**
(필수) 점수부여/배지 규칙이 구성되는 위치입니다.

* **[!UICONTROL 점수 규칙]**
(필수) 표시할 점수를 생성하는 특정 규칙입니다.

* **[!UICONTROL 배지 규칙]**
(필수) 표시할 배지를 생성하는 특정 규칙입니다.

* **[!UICONTROL 표시 제한]**
페이지당 표시할 구성원 수입니다.

   기본값은 10입니다.

## 예: 참가자 리더보드 {#example-participants-leaderboard}

이 리더보드 보고서는 기본 점수 규칙을 적용하여 결과를 보고합니다.

리드 보드 구성 요소 구성:

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

## 예: 전문가 리더보드 {#example-experts-leaderboard}

이 리더보드 보고서는 고급 점수 규칙을 적용하여 결과를 보고합니다.

리드 보드 구성 요소 구성:

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

자세한 내용은 [Leaderboard Essentials](leaderboard.md) 개발자를 위한 페이지입니다.

규칙 만들기에 대한 지침은 [커뮤니티 점수 및 배지](implementing-scoring.md) 관리자용 페이지입니다.
