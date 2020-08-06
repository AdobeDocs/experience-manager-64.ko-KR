---
title: 커뮤니티 알림
seo-title: 커뮤니티 알림
description: AEM Communities에 서명된 커뮤니티 구성원에게 관심 이벤트를 표시하는 알림이 있습니다.
seo-description: AEM Communities에 서명된 커뮤니티 구성원에게 관심 이벤트를 표시하는 알림이 있습니다.
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 1%

---


# 커뮤니티 알림 {#communities-notifications}

## 개요 {#overview}

AEM Communities은 로그인한 커뮤니티 회원에게 관심 이벤트를 표시하는 알림 섹션을 제공합니다.

알림은 [활동](essentials-activities.md) 및 [구독과](subscriptions.md) 비슷하며

* 컨텐츠 게시 멤버
* 다른 구성원을 팔로우하도록 선택한 구성원
* 특정 주제, 아티클 및 기타 컨텐츠 스레드를 따르도록 선택한 구성원

활동 및 구독과 알림을 구분하는 것은

* 알림 섹션에 대한 링크는 항상 커뮤니티 사이트의 헤더에 있습니다.
   * 활동을 위해서는 [활동 스트림 기능이](functions.md#activity-stream-function) 커뮤니티 사이트의 구조에 포함되어야 합니다.
   * 가입에는 이메일 [구성이 필요합니다.](email.md)
* 알림의 구현은 확장 가능하고 플러그 가능한 채널을 통해 이루어집니다
   * 활동은 웹에서만 사용할 수 있습니다.
   * 구독은 이메일을 통해서만 사용할 수 있습니다.

Communities [FP1](deploy-communities.md#latestfeaturepack)의 알림 채널은

* 링크를 사용하여 액세스한 웹 `Notifications` 채널
* 이메일이 올바르게 구성된 경우 사용할 수 있는 이메일 채널

모바일 채널과 데스크탑

### 요구 사항 {#requirements}

**이메일 구성**

알림이 제대로 작동하도록 이메일 채널을 구성해야 합니다.

이메일 설정에 대한 지침은 이메일 [구성을 참조하십시오](analytics.md).

**팔로우 활성화**

다음을 사용하도록 구성 요소를 구성해야 합니다. 다음을 수행할 수 있는 기능은 [블로그](blog-feature.md), 포럼 [,](forum.md)달력, [라이브러리](working-with-qna.md)[](calendar.md)[](file-library.md)[](comments.md),라이브러리,및 comments입니다.

참고:

* 커뮤니티 [사이트 템플릿](sites.md) 및 [그룹 템플릿](tools-groups.md) 내에서 사용되는 구성 요소는 다음을 허용하도록 이미 구성할 수 있습니다.

* 다른 구성원이 팔로우할 수 있도록 구성원 프로필이 이미 구성되었습니다.

## 다음에서 알림 {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

[ **따라하기** ] 단추를 사용하면 항목을 활동, 가입 및/또는 알림으로 팔로우할 수 있습니다. [ **따라하기** ] 단추를 선택할 때마다 선택 항목을 켜거나 끌 수 있습니다. 이 선택 `Email Subscriptions` 사항은 구성된 경우에만 표시됩니다.

다음 방법을 선택한 경우 단추 텍스트가 **팔로잉으로 변경됩니다**. 편의를 위해 모든 방법 `Unfollow All` 을 전환할 수 있습니다.

[ **따라하기** ] 단추가 나타납니다

* 다른 멤버의 프로필을 볼 때
* 포럼, QnA 및 블로그와 같은 기본 기능 페이지
   * 해당 일반 기능에 대한 모든 활동을 수행합니다.
* 포럼 주제, QnA 질문 또는 블로그 아티클과 같은 특정 항목의 경우
   * 해당 특정 항목에 대한 모든 활동을 팔로우합니다.

## 알림 설정 관리 {#managing-notification-settings}

알림 페이지에서 알림 설정 링크를 선택하면 각 구성원이 알림을 받는 방식을 관리할 수 있습니다.

웹 채널은 항상 활성화되어 있습니다.

![chlimage_1-255](assets/chlimage_1-255.png)

적절한 이메일 [구성에 의존하는 이메일](email.md)채널은 웹 채널과 동일한 설정을 제공합니다.

이메일 채널은 기본적으로 꺼져 있습니다.

![chlimage_1-256](assets/chlimage_1-256.png)

회원이 설정할 수 있지만 구성된 이메일에 따라 다릅니다.

![chlimage_1-257](assets/chlimage_1-257.png)

## 알림 보기 {#viewing-notifications}

### 웹 알림 {#web-notifications}

이제 [마법사에서 커뮤니티 사이트를](sites-console.md) 만든 경우 배너 위에 있는 사이트의 헤더 막대에 있는 `Notifications` 기능에 대한 링크가 포함됩니다. 메시지와 달리, 알림은 모든 커뮤니티 사이트에 대해 작성되지만, 사이트 작성 프로세스 동안 메시지가 활성화되어 있어야 합니다.

게시된 사이트를 방문할 때 링크를 선택하면 해당 멤버에 대한 모든 알림이 `Notifications` 표시됩니다.

![chlimage_1-258](assets/chlimage_1-258.png)

### 이메일 알림 {#email-notifications}

이메일 채널이 활성화되면 멤버는 웹의 컨텐츠에 대한 링크가 포함된 이메일을 수신하게 됩니다.

![chlimage_1-259](assets/chlimage_1-259.png)

