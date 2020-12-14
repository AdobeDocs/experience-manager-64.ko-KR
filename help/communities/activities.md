---
title: 활동 스트림 기능
seo-title: 활동 스트림 기능
description: 로그인한 커뮤니티 구성원의 활동
seo-description: 로그인한 커뮤니티 구성원의 활동
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 1%

---


# 활동 스트림 기능 {#activity-streams-feature}

## 소개 {#introduction}

포럼이나 블로그에 게시하는 등 커뮤니티 멤버의 서명된 활동은 `Activity Streams` 구성 요소의 구성을 통해 다양한 방법으로 필터링되어 표시할 수 있는 스트림에 수집됩니다.

팔로우하는 능력은 커뮤니티 회원이 관심 있는 게시물을 팔로우하거나 다른 커뮤니티 회원의 활동을 따를 때 다른 활동 관점을 더해줍니다.

설명서의 이 섹션에서는

* AEM 사이트에 활동 스트림 구성 요소 추가
* 활동 스트림 구성 요소에 대한 구성 설정

## 페이지 {#adding-activity-streams-to-a-page}에 활동 스트림 추가

작성 모드에서 페이지에 `Activity Streams` 구성 요소를 추가하려면 구성 요소 브라우저를 사용하여

* `Communities / Activity Streams`

활동 스트림이 표시되어야 하는 페이지에 드래그합니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md)을 방문하십시오.

[필수 클라이언트측 라이브러리](essentials-activities.md#essentials-for-client-side)가 포함될 때 `Activity Streams` 구성 요소가 표시되는 방식입니다.

![chlimage_1-195](assets/chlimage_1-195.png)

## 활동 스트림 구성 {#configuring-activity-streams}

액세스할 배치된 `Activity Streams` 구성 요소를 선택하고 편집 대화 상자를 여는 `Configure` 아이콘을 선택합니다.

![chlimage_1-196](assets/chlimage_1-196.png)

**[!UICONTROL 사용자 활동]** 탭에서 표시할 활동을 지정합니다.

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL 최대]**
활동표시할 활동 수입니다.
* **[!UICONTROL 스트림 리소스]**
경로커뮤니티 사이트 또는 커뮤니티 그룹에 기본적으로 대해 비워 둡니다. 스트림 리소스 경로는 활동의 소스를 식별합니다. 기본값은 비어 있습니다.
* **[!UICONTROL 사용자 활동]**
보기 표시를 선택하면 활동 페이지에 현재 구성원이 커뮤니티 내에서 생성한 활동을 기준으로 하는 탭이 포함됩니다. 기본값은 선택되었습니다.
* **[!UICONTROL 모든 활동]**
보기 표시이 선택된 경우 활동 페이지에는 현재 구성원이 액세스할 수 있는 커뮤니티 내에서 생성된 모든 활동이 포함된 탭이 포함됩니다. 기본값은 선택되었습니다.
* **[!UICONTROL 다음]**
보기 표시이 선택된 경우 활동 페이지에는 현재 구성원이 팔로우하는 활동을 필터링하는 탭이 포함됩니다. 기본값은 선택되었습니다.

## 다음 보기 {#following-view}

다음을 사용하도록 구성 요소를 구성해야 합니다. 다음을 허용하는 기능은 [블로그](blog-feature.md), [포럼](forum.md), [QnA](working-with-qna.md), [달력](calendar.md), [filelibrary](file-library.md) 및 [comments](comments.md)입니다.

![chlimage_1-198](assets/chlimage_1-198.png)

**Follow** 단추는 [notifications](notifications.md) 및/또는 [구독](subscriptions.md)으로 항목을 팔로우할 수 있는 수단을 제공합니다. **팔로우** 단추를 선택할 때마다 선택 항목을 켜거나 끌 수 있습니다. `Email Subscriptions` 선택 항목은 구성된 경우에만 존재합니다.

다음 방법을 선택하면 단추의 텍스트가 **Following**&#x200B;으로 변경됩니다. 편의를 위해 `Unfollow All`을 선택하여 모든 메서드를 전환할 수 있습니다.

**Follow** 단추가 표시됩니다.

* 다른 멤버의 프로필을 볼 때
* 포럼, QnA 및 블로그와 같은 기본 기능 페이지
   * 해당 일반 기능에 대한 모든 활동을 수행합니다.

* 포럼 주제, QnA 질문 또는 블로그 기사 등 특정 항목의 경우
   * 해당 특정 항목에 대한 모든 활동을 팔로우합니다.

## 추가 정보 {#additional-information}

개발자를 위한 [Activity Streams Essentials](essentials-activities.md) 페이지에서 자세한 내용을 확인할 수 있습니다.
