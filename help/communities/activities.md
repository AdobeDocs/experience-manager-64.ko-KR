---
title: 활동 스트림 기능
seo-title: Activity Streams Feature
description: 로그인한 커뮤니티 구성원의 활동
seo-description: Activities of a signed-in community member
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 3%

---

# 활동 스트림 기능 {#activity-streams-feature}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

커뮤니티 구성원의 활동들(예: 포럼 또는 블로그에 게시)은 스트림에 수집되며, 스트림에는 이러한 구성을 통해 다양한 방법으로 필터링 및 표시할 수 있다 `Activity Streams` 구성 요소.

팔로우하는 기능은 커뮤니티 구성원이 관심 있는 게시를 따르거나 다른 커뮤니티 구성원의 활동을 따를 때 다른 활동 보기를 추가합니다.

설명서의 이 섹션에서는 다음 사항에 대해 설명합니다

* AEM 사이트에 Activity Streams 구성 요소 추가
* 활동 스트림 구성 요소에 대한 구성 설정

## 페이지에 활동 스트림 추가 {#adding-activity-streams-to-a-page}

를 추가하려면 `Activity Streams` 구성 요소를 페이지에 작성자 모드에서 사용하려면 구성 요소 브라우저를 사용하여 를 찾습니다

* `Communities / Activity Streams`

활동 스트림이 표시되어야 하는 페이지에 드래그합니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md).

이 [필수 클라이언트 측 라이브러리](essentials-activities.md#essentials-for-client-side) 포함된 경우, 다음과 같이 하십시오 `Activity Streams` 구성 요소가 표시됩니다.

![chlimage_1-195](assets/chlimage_1-195.png)

## 활동 스트림 구성 {#configuring-activity-streams}

배치된 항목을 선택합니다 `Activity Streams` 액세스하여 선택할 구성 요소 `Configure` 아이콘 편집 대화 상자를 엽니다.

![chlimage_1-196](assets/chlimage_1-196.png)

아래에 **[!UICONTROL 사용자 활동]** 탭에서 표시할 활동을 지정합니다.

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL 최대 활동 수]**
표시할 활동 수
* **[!UICONTROL 스트림 리소스 경로]**
커뮤니티 사이트 또는 커뮤니티 그룹으로 기본적으로 비워 둡니다. 스트림 리소스 경로는 활동의 소스를 식별합니다. 기본값은 비어 있습니다.
* **[!UICONTROL 사용자 활동 보기 표시]**
선택된 경우 활동 페이지에는 현재 구성원이 커뮤니티 내에서 생성한 활동을 기준으로 활동을 필터링하는 탭이 포함됩니다. 기본값이 선택되어 있습니다.
* **[!UICONTROL 모든 활동 보기 표시]**
선택된 경우 활동 페이지에는 현재 구성원이 액세스할 수 있는 커뮤니티 내에서 생성된 모든 활동이 포함된 탭이 포함됩니다. 기본값이 선택되어 있습니다.
* **[!UICONTROL 다음 보기 표시]**
이 옵션을 선택하면 활동 페이지에 현재 구성원이 따르는 활동을 필터링하는 탭이 포함됩니다. 기본값이 선택되어 있습니다.

## 다음 보기 {#following-view}

다음을 사용하도록 구성 요소를 구성해야 합니다. 다음을 허용하는 기능은 다음과 같습니다 [블로그](blog-feature.md), [포럼](forum.md), [QnA](working-with-qna.md), [달력](calendar.md), [파일 라이브러리](file-library.md), 및 [댓글](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

다음 **팔로우** 버튼은 항목을 활동으로 따르는 수단을 제공합니다. [알림](notifications.md), 및/또는 [구독](subscriptions.md). 매번 **팔로우** 단추를 선택하면 선택 항목을 켜거나 끌 수 있습니다. 다음 `Email Subscriptions` 선택 항목은 구성된 경우에만 나타납니다.

다음 방법을 선택하면 단추의 텍스트가 **다음**. 편의를 위해 선택할 수 있습니다 `Unfollow All` 를 눌러 모든 메서드를 해제합니다.

다음 **팔로우** 버튼이 표시됩니다.

* 다른 구성원의 프로파일을 볼 때
* 포럼, QnA 및 블로그 등의 기본 기능 페이지
   * 일반 기능에 대한 모든 활동을 따릅니다

* 포럼 주제, 질문 또는 블로그 문서와 같은 특정 항목의 경우
   * 특정 항목에 대한 모든 활동을 따릅니다

## 추가 정보 {#additional-information}

자세한 내용은 [Activity Streams Essentials](essentials-activities.md) 개발자를 위한 페이지입니다.
