---
title: 관념화 기능
seo-title: 관념화 기능
description: 관념화 기능 추가 및 구성
seo-description: 관념화 기능 추가 및 구성
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

아이디어 기능은 게시 환경에서 로그인된 사이트 방문자(커뮤니티 구성원)를 위한 영역을 제공하여 다음을 수행합니다.

* 커뮤니티와 공유할 아이디어 만들기
* 아이디어 보기 및 주석 달기
* 아이디어 표현
* 아이디어 투표

설명서의 이 섹션에서는

* AEM 사이트에 비디오 기능 추가
* 아이디어 구성 요소에 대한 구성 설정

## 페이지 {#adding-a-ideation-to-a-page}에 아이디어 추가

작성 모드에서 페이지에 `Ideation` 구성 요소를 추가하려면 구성 요소 브라우저를 사용하여 `Communities / Ideation`을(를) 찾아 아이디어가 나타날 페이지로 드래그합니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md)을 방문하십시오.

[필수 클라이언트측 라이브러리](ideation.md#essentials-for-client-side)가 포함될 때 `Ideation`구성 요소가 표시되는 방식입니다.

![chlimage_1-29](assets/chlimage_1-29.png)

## 아이디어 구성 {#configuring-an-ideation}

액세스할 배치된 `Ideation` 구성 요소를 선택하고 편집 대화 상자를 여는 `Configure` 아이콘을 선택합니다.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### 설정 탭 {#settings-tab}

**[!UICONTROL 설정]** 탭에서 아이디어 및 주석 설정을 지정합니다.

* **[!UICONTROL 아이디어]**
제목아이디어를 위한 표시 제목입니다. 기본값은 
`Ideation`.

* **[!UICONTROL 아이디어]**
설명아이디어를 위한 하위 제목으로서 표시할 설명입니다. 기본값은 설명이 없습니다.

* **[!UICONTROL 페이지당]**
항목페이지당 표시되는 아이디어/게시물 수를 정의합니다. 기본값은 10입니다.

* **[!UICONTROL 중재됨]**
이 선택된 경우, 아이디어 및 댓글 게시가 게시 사이트에 표시되기 전에 승인되어야 합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 닫힘]**
이 선택되어 있으면 아이디어 포럼이 새 아이디어 및 주석으로 닫힙니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 리치 텍스트]**
편집기이 확인란을 선택하면 아이디어 및 주석을 마크업으로 입력할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 태그]**
지정 허용이 선택된 경우, 구성원이 태그 레이블을 게시물에 추가할 수 있도록 허용합니다(태그  **[!UICONTROL fieldtab]** 참조). 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 파일 업로드]**
허용이 선택된 경우 파일 첨부 파일을 아이디어 또는 댓글에 추가할 수 있도록 허용합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 최대 파일]**
크기관련성 
`Allow File Uploads` 이 선택되어 있는지 확인합니다. 이 필드는 업로드된 파일의 크기(바이트)를 제한합니다. 기본값은 104857600(10Mb)입니다.

* **[!UICONTROL 허용되는 파일]**
형식관련성이 있는 경우는 
`Allow File Uploads` 이 선택되어 있는지 확인합니다. &quot;점&quot; 구분 기호가 있는 쉼표로 구분된 파일 확장자 목록입니다. 예:.jpg, .jpeg, .png, .doc, .docx, .pdf 파일 유형을 지정한 경우 지정되지 않은 파일 유형은 업로드되지 않습니다. 모든 파일 형식을 사용할 수 있도록 기본값이 지정되지 않았습니다.

* **[!UICONTROL 최대 첨부 이미지 파일]**
크기 파일 업로드 허용이 선택된 경우에만 관련됩니다. 업로드된 이미지 파일에 포함할 수 있는 최대 바이트 수입니다. 기본값은 2097152(2Mb)입니다.

* **[!UICONTROL 답글]**
허용이 선택된 경우 아이디어에 게시된 댓글에 대한 답글을 허용합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 사용자가 댓글 및 항목]**
을 삭제할 수 있도록 허용이 선택된 경우, 구성원이 게시한 주석 및 아이디어를 삭제할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 팔로잉]**
허용이 선택된 경우, 구성원에게 새 게시물에 대한 알림을 받을 수  [](notifications.md) 있는 아이디어 게시물에 대해 다음 기능을 포함합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 이메일 구독]**
허용이 선택된 경우, 구성원에게 이메일([가입](subscriptions.md))로 새 게시물에 대한 알림을 보낼 수 있습니다. `Allow Following`을(를) 확인하고 [전자 메일로 구성된](email.md)이(가) 필요합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 투표]**
허용이 선택된 경우 아이디어의 댓글에 투표를 허용합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 디스플레이]**
배지If를 선택하면  [](implementing-scoring.md) 멤버의 아이디어를 통해 언드 및 배지 배지 역할을 지정합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 추천 콘텐츠]**
를 허용 확인란을 선택하면 아이디어를  [주요 컨텐츠로 식별할 수 있습니다](featured.md). 기본값은 선택되어 있지 않습니다.

### 사용자 중재 탭 {#user-moderation-tab}

**[!UICONTROL 사용자 중재]** 탭에서 게시된 아이디어 및 댓글(사용자가 생성한 컨텐츠)의 관리 방법을 지정합니다. 자세한 내용은 [사용자 생성 콘텐츠 중재](moderate-ugc.md)를 참조하십시오.

* **[!UICONTROL 게시물]**
거부이 확인란을 선택하면 신뢰할 수 있는 멤버 중재자가 게시물을 거부할 수 있고 공개 포럼에 게시물이 표시되지 않도록 방지할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 주제 닫기/다시]**
열기이 확인란을 선택하면 신뢰할 수 있는 멤버 중재자는 항목을 닫고 추가 편집 및 주석을 달 수 있으며 항목을 다시 열 수도 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 게시물]**
플래그 이 확인란을 선택하면 구성원이 다른 사용자의 주제나 댓글에 부적절한 플래그를 지정할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 플래그 이유 목록]**
이 선택된 경우, 멤버가 드롭다운 목록에서 주제 또는 댓글에 대한 플래그를 지정한 이유를 부적절한 것으로 선택할 수 있도록 허용합니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 사용자 지정 플래그]**
이유이 확인란을 선택하면 구성원이 주제 또는 댓글에 대한 자신의 이유를 부적절한 것으로 입력할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 중재]**
임계값 중재자에게 알림을 보내기 전에 주제나 댓글에 대해 구성원이 플래그를 지정해야 하는 횟수를 입력합니다. 기본값은 1입니다(한 번).

* **[!UICONTROL 플래그]**
제한주제 또는 댓글이 공개 보기에서 숨겨지기 전에 플래그를 지정해야 하는 횟수를 입력합니다. -1로 설정하면 플래그가 지정된 주제 또는 댓글이 공개 보기에서 숨겨지지 않습니다. 그렇지 않은 경우 이 숫자는 중재 임계값보다 크거나 같아야 합니다. 기본값은 5입니다.

### 태그 필드 탭 {#tag-field-tab}

**[!UICONTROL 태그 필드]** 탭 아래에서 **[!UICONTROL 설정]** 탭 아래에서 허용되는 경우 적용할 수 있는 태그는 선택한 네임스페이스에 따라 제한됩니다.

* **[!UICONTROL 허용되는]**
네임스페이스관련 있는 경우 
`Allow Tagging` 는 [설정] 탭에서  **** 체크됩니다. 적용할 수 있는 태그는 확인된 네임스페이스 범주 내의 태그로 제한됩니다. 네임스페이스 목록에는 &quot;표준 태그&quot;(기본 네임스페이스)와 &quot;모든 태그 포함&quot;이 포함되어 있습니다. 기본값은 선택되어 있지 않으므로 모든 네임스페이스가 허용됩니다.

* **[!UICONTROL 제안]**
제한포럼 게시에 대한 회원에게 제안으로 표시할 태그의 수를 입력합니다. 값 
**-** 1은 제한이 없음을 의미합니다. 기본값은 0입니다.

### 정렬 설정 탭 {#sort-settings-tab}

**[!UICONTROL 정렬 설정]** 탭에서 게시된 주석이 표시될 때 정렬되는 방법을 지정합니다.

* **[!UICONTROL 정렬]**
기준허용되는 모든 정렬 선택 사항 확인: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 기본값은 `Newest, Oldest, Last Updated`입니다.

* **[!UICONTROL DefaultPull]**
으로 설정하면 선택된 정렬 옵션 중 하나를 기본값으로 선택할 수 있습니다. 기본값은 
`Newest`.

* **[!UICONTROL Analytics]**
정렬 시간을 선택하여 풀다운 중 하나를 선택합니다. 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. 기본값은 `All`입니다.

## 사이트 방문자 경험 {#site-visitor-experience}

### {#creating-idea} 아이디어 만들기

모든 커뮤니티 기능과 마찬가지로, 로그인하지 않은 경우 사이트 방문자는 의견과 투표/좋아요를 통해서만 아이디어를 읽고 다른 의견을 볼 수 있습니다.

로그인하면 멤버가 새 아이디어를 만들 수 있습니다.

![chlimage_1-32](assets/chlimage_1-32.png)

아이디어를 제출하기 전에 멤버가 초안을 저장할 수 있습니다.

`Save as Draft` 단추를 선택하면 초안이 저장됩니다.

![chlimage_1-33](assets/chlimage_1-33.png)

`My Drafts` 탭에서 저장된 초안을 볼 때 `Read More`을 선택하여 편집 모드를 다시 시작합니다.

![chlimage_1-34](assets/chlimage_1-34.png)

#### 피드백 제공 중 {#providing-feedback}

아이디어가 게시되면 다른 멤버가 로그인하여 아이디어( `Read More`)를 열고 아이디어를 좋아하여 투표 수에 추가하고 의견을 추가할 수 있습니다.

![chlimage_1-35](assets/chlimage_1-35.png)

### 추가 정보 {#additional-information}

개발자를 위한 [Ideation Essentials](ideation.md) 페이지에 자세한 내용이 표시될 수 있습니다.

게시된 항목 및 댓글을 중재하려면 [사용자 생성 콘텐츠 중재](moderate-ugc.md)를 참조하십시오.

게시된 항목 및 댓글에 태그를 지정하려면 [사용자 생성 컨텐츠 태그 지정](tag-ugc.md)을 참조하십시오.
