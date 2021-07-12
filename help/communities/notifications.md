---
title: 커뮤니티 알림
seo-title: 커뮤니티 알림
description: AEM Communities에는 로그인한 커뮤니티 구성원에게 관심 이벤트를 표시하는 알림이 있습니다
seo-description: AEM Communities에는 로그인한 커뮤니티 구성원에게 관심 이벤트를 표시하는 알림이 있습니다
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 1%

---

# 커뮤니티 알림 {#communities-notifications}

## 개요 {#overview}

AEM Communities에서는 로그인한 커뮤니티 구성원에게 관심 이벤트를 표시하는 알림 섹션을 제공합니다.

알림은 [활동](essentials-activities.md) 및 [구독](subscriptions.md)과 비슷하며,

* 컨텐츠 게시 멤버
* 다른 멤버를 따르도록 선택한 멤버
* 특정 주제, 문서 및 기타 컨텐츠 스레드를 따르도록 선택한 구성원

활동 및 구독과 알림을 구분하는 것은 무엇입니까

* 알림 섹션에 대한 링크가 항상 커뮤니티 사이트의 헤더에 표시됩니다
   * 활동을 사용하려면 커뮤니티 사이트의 구조에 [활동 스트림 함수](functions.md#activity-stream-function)를 포함해야 합니다
   * 가입에는 [전자 메일](email.md)의 구성이 필요합니다
* 알림의 구현은 확장 가능한 채널을 통해 수행됩니다
   * 활동은 웹에서만 사용할 수 있습니다
   * 구독은 이메일을 사용해야만 사용할 수 있습니다

커뮤니티 [FP1](deploy-communities.md#latestfeaturepack)부터 사용 가능한 알림 채널은 다음과 같습니다

* `Notifications` 링크를 사용하여 액세스하는 웹 채널
* 이메일이 올바르게 구성된 경우 사용할 수 있는 이메일 채널

향후 채널은 모바일 및 데스크탑입니다.

### 요구 사항 {#requirements}

**이메일 구성**

알림이 작동하도록 이메일 채널을 구성하려면 이메일을 구성해야 합니다.

이메일 설정에 대한 지침은 [이메일 구성](analytics.md)을 참조하십시오.

**팔로우 활성화**

다음을 사용하도록 구성 요소를 구성해야 합니다. 다음을 허용하는 기능은 [블로그](blog-feature.md), [포럼](forum.md), [QnA](working-with-qna.md), [달력](calendar.md), [파일 라이브러리](file-library.md) 및 [주석](comments.md)입니다.

참고 사항

* 커뮤니티 [사이트 템플릿](sites.md) 및 [그룹 템플릿](tools-groups.md)에서 사용되는 구성 요소는 다음을 허용하도록 이미 구성되어 있을 수 있습니다

* 구성원 프로필이 이미 다른 구성원이 팔로우할 수 있도록 구성되어 있습니다

## 다음에서 알림 {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

**팔로우** 버튼은 항목을 활동, 구독 및/또는 알림으로 따르는 수단을 제공합니다. **팔로우** 단추를 선택할 때마다 선택 항목을 켜거나 끌 수 있습니다. `Email Subscriptions` 선택 항목은 구성된 경우에만 나타납니다.

다음 방법을 선택하면 단추의 텍스트가 **Following**&#x200B;으로 변경됩니다. 편의를 위해 `Unfollow All` 을 선택하여 모든 메서드를 해제할 수 있습니다.

**팔로우** 단추가 나타납니다

* 다른 구성원의 프로파일을 볼 때
* 포럼, QnA 및 블로그 등의 기본 기능 페이지
   * 일반 기능에 대한 모든 활동을 따릅니다
* 포럼 주제, 질문 또는 블로그 문서와 같은 특정 항목의 경우
   * 특정 항목에 대한 모든 활동을 따릅니다

## 알림 설정 관리 {#managing-notification-settings}

[알림] 페이지에서 [알림 설정] 링크를 선택하면 각 구성원이 알림 수신 방식을 관리할 수 있습니다.

웹 채널은 항상 활성화되어 있습니다.

![chlimage_1-255](assets/chlimage_1-255.png)

적절한 [이메일](email.md)구성 을 사용하는 이메일 채널은 웹 채널에 대해 와 동일한 설정을 제공합니다.

이메일 채널은 기본적으로 꺼져 있습니다.

![chlimage_1-256](assets/chlimage_1-256.png)

구성원에 의해 설정될 수 있지만 구성된 이메일에 따라 다릅니다.

![chlimage_1-257](assets/chlimage_1-257.png)

## 알림 보기 {#viewing-notifications}

### 웹 알림 {#web-notifications}

커뮤니티 사이트](sites-console.md)에서 만든 [마법사에 배너 위의 사이트 헤더 막대에 있는 `Notifications` 기능에 대한 링크가 포함됩니다. 메시지와 달리, 모든 커뮤니티 사이트에 대한 알림이 생성되지만 사이트 작성 프로세스 중에 메시지를 활성화해야 합니다.

게시된 사이트를 방문할 때 `Notifications` 링크를 선택하면 구성원의 모든 알림이 표시됩니다.

![chlimage_1-258](assets/chlimage_1-258.png)

### 이메일 알림 {#email-notifications}

이메일 채널이 활성화되면 구성원은 웹의 컨텐츠에 대한 링크가 포함된 이메일을 수신하게 됩니다.

![chlimage_1-259](assets/chlimage_1-259.png)
