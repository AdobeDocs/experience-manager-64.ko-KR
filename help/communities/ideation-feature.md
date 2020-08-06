---
title: 아이디어 기능
seo-title: 아이디어 기능
description: 아이디어 기능 추가 및 구성
seo-description: 아이디어 기능 추가 및 구성
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---


# 아이디어 기능 {#ideation-feature}

## 소개 {#introduction}

아이디어 기능은 게시 환경에서 로그인된 사이트 방문자(커뮤니티 구성원)를 위한 영역을 제공합니다.

* 커뮤니티와 공유할 아이디어 제작
* 아이디어 보기 및 주석 달기
* 아이디어 표현
* 아이디어 투표

설명서의 이 섹션에서는

* AEM 사이트에 비디오 기능 추가
* 아이디어 구성 요소에 대한 구성 설정

## Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

작성 모드에서 페이지에 `Ideation` `Communities / Ideation` 구성 요소를 추가하려면 구성 요소 브라우저를 사용하여 구성 요소를 찾아 아이디어가 표시되어야 하는 페이지에 놓습니다.

필요한 정보를 보려면 커뮤니티 구성 요소 [기본 사항을 방문하십시오](basics.md).

[필요한 클라이언트측 라이브러리가](ideation.md#essentials-for-client-side) 포함되어 있으면 `Ideation`구성 요소가 표시되는 방식입니다.

![chlimage_1-29](assets/chlimage_1-29.png)

## 아이디어 구성 {#configuring-an-ideation}

액세스할 배치된 `Ideation` 구성 요소를 선택하고 편집 대화 상자를 여는 `Configure` 아이콘을 선택합니다.

![chlimage_1-30](assets/chlimage_1-30.png)![chlimage_1-31](assets/chlimage_1-31.png)

### 설정 탭 {#settings-tab}

설정 **[!UICONTROL 탭]** 아래에서 아이디어 및 주석 설정을 지정합니다.

* **[!UICONTROL 관념화 제목]**&#x200B;아이디어를 표시하는 제목입니다. 기본값은 
`Ideation`.

* **[!UICONTROL 아이디어 설명]**&#x200B;아이디어를 위한 하위 제목으로서 표시할 설명입니다. 기본값은 설명이 아닙니다.

* **[!UICONTROL 페이지당 항목]**&#x200B;페이지당 표시되는 아이디어/게시물 수를 정의합니다. 기본값은 10입니다.

* **[!UICONTROL 중재됨]**&#x200B;이 확인란을 선택하면 아이디어 및 댓글이 게시 사이트에 표시되기 전에 게시 승인이 필요합니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 닫힘]**&#x200B;이 선택되어 있으면 아이디어 포럼이 새로운 아이디어와 주석으로 닫힙니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 리치 텍스트 편집기]**&#x200B;를 선택하면 아이디어 및 주석을 마크업으로 입력할 수 있습니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 태그 지정 허용]**&#x200B;이 선택된 경우, 구성원이 게시물에 태그 레이블을 추가할 수 있도록 합니다(태그 필드 탭 **[!UICONTROL 참조]** ). 기본값은 선택 취소입니다.

* **[!UICONTROL 파일 업로드]**&#x200B;허용 이 확인란을 선택하면 아이디어 또는 댓글에 파일 첨부 파일을 추가할 수 있습니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 최대 파일 크기]**&#x200B;는 
`Allow File Uploads` 이 선택되어 있습니다. 이 필드는 업로드된 파일의 크기(바이트)를 제한합니다. 기본값은 104857600(10Mb)입니다.

* **[!UICONTROL 허용되는 파일 유형]**&#x200B;은 
`Allow File Uploads` 이 선택되어 있습니다. &quot;점&quot; 구분 기호가 있는 쉼표로 구분된 파일 확장자 목록입니다. 예: .jpg, .jpeg, .png, .doc, .docx, .pdf. 파일 유형을 지정하면 지정되지 않은 파일 유형을 업로드할 수 없습니다. 모든 파일 유형이 허용되도록 기본값이 지정되지 않았습니다.

* **[!UICONTROL 최대 첨부 이미지 파일 크기]**&#x200B;는 파일 업로드 허용이 선택된 경우에만 해당됩니다. 업로드된 이미지 파일의 최대 바이트 수입니다. 기본값은 2097152(2Mb)입니다.

* **[!UICONTROL 답글 허용]**&#x200B;이 선택된 경우 아이디어에 게시된 댓글에 대한 답글을 허용합니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 사용자가 댓글 및 항목 삭제 허용]**&#x200B;이 선택된 경우, 회원은 게시된 댓글과 아이디어를 삭제할 수 있습니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 다음]**&#x200B;허용 이 확인란을 선택하면 구성원에게 새 게시물에 대한 [알림을 받을](notifications.md) 수 있는 아이디어 게시물에 대해 다음 기능을 포함합니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 이메일 구독]**&#x200B;허용 이 확인란을 선택하면 구성원이 이메일([구독](subscriptions.md))로 새 게시물에 대한 알림을 받을 수 있습니다. 확인 및 `Allow Following` 이메일 구성 [](email.md)필요 기본값은 선택 취소입니다.

* **[!UICONTROL 투표 허용]**&#x200B;이 선택된 경우 아이디어의 댓글에 투표를 허용합니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 배지]**&#x200B;표시이 확인란을 선택하면 [멤버 아이디어가 있는 획득 배지](implementing-scoring.md) 및 지정된 배지가 표시됩니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 주요 컨텐츠]**&#x200B;허용(선택한 경우)을 [주요 컨텐츠로 식별할 수 있습니다](featured.md). 기본값은 선택 취소입니다.

### 사용자 중재 탭 {#user-moderation-tab}

사용자 중재 **[!UICONTROL 탭]** 아래에서 게시된 아이디어와 댓글(사용자가 생성한 컨텐츠)을 관리하는 방법을 지정합니다. 자세한 내용은 사용자 생성 [컨텐츠 중재를 참조하십시오](moderate-ugc.md).

* **[!UICONTROL 게시물]**&#x200B;거부 이 확인란을 선택하면 신뢰할 수 있는 멤버 중재자가 게시물을 거부할 수 있으며 공개 포럼에 게시물이 표시되지 않게 됩니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 주제 닫기/다시 열기]**&#x200B;이 선택된 경우 신뢰할 수 있는 멤버 중재자는 항목을 닫고 추가 편집 및 주석을 달 수 있으며 항목을 다시 열 수도 있습니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 게시물]**&#x200B;플래그 이 확인란을 선택하면 구성원이 다른 사용자의 주제나 댓글에 부적절한 플래그를 지정할 수 있습니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 플래그 이유 목록]**&#x200B;이 확인란을 선택하면 구성원이 드롭다운 목록에서 주제나 댓글에 플래그를 지정하는 이유를 부적절한 것으로 선택할 수 있습니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 사용자 지정 플래그 이유]**&#x200B;이 확인란을 선택하면 구성원이 주제 또는 댓글에 대한 자신만의 이유를 입력할 수 있습니다. 기본값은 선택 취소입니다.

* **[!UICONTROL 중재 임계값]**&#x200B;중재자에게 알림을 보내기 전에 주제 또는 댓글에 대해 구성원이 플래그를 지정해야 하는 횟수를 입력합니다. 기본값은 1입니다(한 번).

* **[!UICONTROL 제한 플래그]**&#x200B;가 공개 보기에서 숨겨지기 전에 주제나 댓글에 플래그를 지정해야 하는 횟수를 입력합니다. -1로 설정하면 플래그가 지정된 토픽이나 댓글은 공개 보기에서 숨겨지지 않습니다. 그렇지 않은 경우 이 숫자는 중재 임계값보다 크거나 같아야 합니다. 기본값은 5입니다.

### 태그 필드 탭 {#tag-field-tab}

[ **[!UICONTROL 태그] 필드]** 탭 아래에서 **[!UICONTROL 설정]** 탭 아래에서 허용되는 경우 적용할 수 있는 태그는 선택한 네임스페이스에 따라제한됩니다.

* **[!UICONTROL 허용되는 네임스페이스]**&#x200B;는 
`Allow Tagging` 은 설정 **탭 아래에서** 선택되어 있습니다. 적용할 수 있는 태그는 확인된 네임스페이스 범주 내의 태그로 제한됩니다. 네임스페이스 목록에는 &quot;표준 태그&quot;(기본 네임스페이스)와 &quot;모든 태그 포함&quot;이 포함되어 있습니다. 기본값은 선택되어 있지 않으므로 모든 네임스페이스가 허용됩니다.

* **[!UICONTROL 제안 한도]**&#x200B;포럼 게시에 대한 회원에게 제안으로 표시할 태그의 수를 입력합니다. 값 
**1은** 제한이 없음을 의미합니다. 기본값은 0입니다.

### 정렬 설정 탭 {#sort-settings-tab}

정렬 설정 **[!UICONTROL 탭]** 아래에서, 표시할 때 게시된 댓글이 정렬되는 방식을 지정합니다.

* **[!UICONTROL 정렬 기준]**&#x200B;허용되는 모든 정렬 선택 사항 확인: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 기본값은 `Newest, Oldest, Last Updated`입니다.

* **[!UICONTROL 기본]**&#x200B;풀다운으로 설정하여 선택된 정렬 옵션 중 하나를 기본값으로 선택합니다. 기본값은 
`Newest`.

* **[!UICONTROL Analytics 정렬]**&#x200B;풀다운에 대한 시간 옵션을 선택하여 다음 중 하나를 선택합니다. 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. 기본값은 `All`입니다.

## 사이트 방문자 경험 {#site-visitor-experience}

### 아이디어 만들기 {#creating-idea}

모든 커뮤니티 기능과 마찬가지로, 로그인하지 않은 경우 사이트 방문자는 의견과 투표/좋아요 등을 통해 아이디어를 읽고 다른 의견만 볼 수 있습니다.

로그인하면 멤버가 새로운 아이디어를 만들 수 있습니다.

![chlimage_1-32](assets/chlimage_1-32.png)

아이디어를 제출하기 전에 멤버가 초안을 저장할 수 있습니다.

단추를 선택하면 `Save as Draft` 초안이 저장됩니다.

![chlimage_1-33](assets/chlimage_1-33.png)

탭에서 저장된 초안을 볼 때 `My Drafts` 편집 모드 `Read More` 를 다시 입력하려면 선택합니다.

![chlimage_1-34](assets/chlimage_1-34.png)

#### 피드백 제공 {#providing-feedback}

아이디어가 게시되면 다른 구성원은 로그인하여 아이디어를 열고 ( `Read More`) 아이디어를 좋아하여 투표 수에 추가하고 의견을 추가할 수 있습니다.

![chlimage_1-35](assets/chlimage_1-35.png)

### 추가 정보 {#additional-information}

개발자를 위한 Ideation Essentials [페이지에](ideation.md) 대한 자세한 내용이 나와 있습니다.

게시된 항목 및 댓글에 대한 중재는 사용자 생성 [컨텐츠 중재를 참조하십시오](moderate-ugc.md).

게시된 항목 및 댓글에 태그를 지정하려면 사용자 생성 컨텐츠 [태그 지정을 참조하십시오](tag-ugc.md).
