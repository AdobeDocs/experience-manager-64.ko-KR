---
title: 이미지 기능
seo-title: Ideation Feature
description: 이미지 기능 추가 및 구성
seo-description: Adding and configuring the Ideation feature
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 1%

---

# 이미지 기능 {#ideation-feature}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

비디오 기능은 게시 환경에서 로그인한 사이트 방문자(커뮤니티 구성원)를 위한 영역을 제공합니다.

* 커뮤니티와 공유할 아이디어 만들기
* 아이디어를 보고 주석을 답니다
* 아이디어를 따르세요
* 아이디어를 투표할 수 있습니다

설명서의 이 섹션에서는 다음 사항에 대해 설명합니다

* AEM 사이트에 이미지 기능 추가
* 이미지 구성 요소에 대한 구성 설정

## 페이지에 이미지 추가 {#adding-a-ideation-to-a-page}

을(를) 추가하려면 `Ideation` 구성 요소를 페이지에 작성자 모드에서 사용하려면 구성 요소 브라우저를 사용하여 를 찾습니다 `Communities / Ideation` 아이디어가 나타날 페이지로 끌어서 놓습니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md).

이 [필수 클라이언트 측 라이브러리](ideation.md#essentials-for-client-side) 포함된 경우, 다음과 같이 하십시오 `Ideation`구성 요소가 표시됩니다.

![chlimage_1-29](assets/chlimage_1-29.png)

## 이미지 구성 {#configuring-an-ideation}

배치된 항목을 선택합니다 `Ideation` 액세스하여 선택할 구성 요소 `Configure` 아이콘 편집 대화 상자를 엽니다.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### 설정 탭 {#settings-tab}

아래에 **[!UICONTROL 설정]** 탭에서 아이디어 및 주석에 대한 설정을 지정합니다.

* **[!UICONTROL 이미지 제목]**
아이디어 표시 제목입니다. 기본값은 입니다. 
`Ideation`.

* **[!UICONTROL 이미지 설명]**
아이디어를 위한 하위 제목으로서 표시할 설명입니다. 기본값은 설명이 없습니다.

* **[!UICONTROL 페이지당 항목 수]**
페이지당 표시되는 아이디어/게시물 수를 정의합니다. 기본값은 10입니다.

* **[!UICONTROL 중재됨]**
이 확인란을 선택하면 게시 사이트에 게시하기 전에 아이디어 및 댓글 게시를 승인해야 합니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 닫힘]**
이 확인란을 선택하면 아이디어 포럼이 새로운 아이디어 및 댓글에 대해 닫힙니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 리치 텍스트 편집기]**
이 확인란을 선택하면 아이디어 및 주석을 마크업에 입력할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 태깅 허용]**
이 확인란을 선택하면 구성원이 게시물에 태그 레이블을 추가할 수 있습니다( **[!UICONTROL 태그 필드]** 탭). 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 파일 업로드 허용]**
이 옵션을 선택하면 아이디어 또는 주석에 첨부 파일을 추가할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 최대 파일 크기]**
관련성이 있는 경우에만 
`Allow File Uploads` 이(가) 선택되어 있습니다. 이 필드는 업로드된 파일의 크기(바이트)를 제한합니다. 기본값은 104857600(10Mb)입니다.

* **[!UICONTROL 허용되는 파일 형식]**
관련성이 있는 경우에만 
`Allow File Uploads` 이(가) 선택되어 있습니다. 점이 구분되어 있는 쉼표로 구분된 파일 확장자 목록입니다. 예: .jpg, .jpeg, .png, .doc, .docx, .pdf 파일 유형을 지정하면, 지정되지 않은 파일 유형은 업로드할 수 없습니다. 기본값은 지정되지 않아서 모든 파일 유형이 허용됩니다.

* **[!UICONTROL 최대 첨부 이미지 파일 크기]**
파일 업로드 허용 이 선택된 경우에만 관련됩니다. 업로드된 이미지 파일의 최대 바이트 수입니다. 기본값은 2097152(2Mb)입니다.

* **[!UICONTROL 답글 허용]**
이 옵션을 선택하면 해당 아이디어를 게시한 댓글에 대한 답글을 허용합니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 사용자가 주석 및 항목을 삭제할 수 있도록 허용]**
이 옵션을 선택하면 구성원이 게시한 댓글과 아이디어를 삭제할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 다음 허용]**
이 옵션을 선택하면 구성원이 [알림](notifications.md) 새 게시물입니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 이메일 구독 허용]**
이 확인란을 선택하면 구성원이 이메일로 새 게시물에 대한 알림을 받을 수 있습니다([구독](subscriptions.md)). 필요한 경우 `Allow Following` 확인 후 [전자 메일 구성](email.md). 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 투표 허용]**
이 옵션을 선택하면 아이디어 댓글에 대한 투표를 허용합니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 배지 표시]**
선택한 경우, 기한 및 지정된 항목을 표시합니다 [배지](implementing-scoring.md) 회원의 아이디어로 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 추천 콘텐츠 허용]**
이 옵션을 선택하면 [주요 콘텐츠](featured.md). 기본값은 선택 취소되어 있습니다.

### 사용자 중재 탭 {#user-moderation-tab}

아래에 **[!UICONTROL 사용자 중재]** 탭에서 게시된 아이디어 및 댓글(사용자가 생성한 컨텐츠)을 관리하는 방법을 지정합니다. 자세한 내용은 [사용자가 생성한 컨텐츠 중재](moderate-ugc.md).

* **[!UICONTROL 게시물 거부]**
이 확인란을 선택하면 신뢰할 수 있는 구성원 중재자가 게시물을 거부하고 공개 포럼에 게시물이 표시되지 않도록 할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 항목 닫기/다시 열기]**
이 옵션을 선택하면 신뢰할 수 있는 멤버 중재자는 항목을 닫고 추가 편집 및 주석을 편집할 수 있으며 항목을 다시 열 수도 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 게시물 플래그 지정]**
이 확인란을 선택하면 구성원이 다른 사용자의 주제나 댓글에 대해 부적절한 플래그를 지정할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 플래그 이유 목록]**
이 확인란을 선택하면 구성원이 드롭다운 목록에서 주제 또는 댓글에 대한 플래그 지정을 부적절한 것으로 선택할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 사용자 지정 플래그 이유]**
이 옵션을 선택하면 구성원이 주제 또는 댓글에 대한 플래그 지정 이유를 부적절한 것으로 입력할 수 있습니다. 기본값은 선택 취소되어 있습니다.

* **[!UICONTROL 중재 임계값]**
중재자에게 통지하기 전에 구성원에 의해 주제나 댓글에 플래그를 지정해야 하는 횟수를 입력합니다. 기본값은 1입니다(한 번).

* **[!UICONTROL 플래그 지정 제한]**
주제 또는 댓글이 공개 보기에서 숨겨지기 전에 플래그를 지정해야 하는 횟수를 입력합니다. -1로 설정하면 플래그가 지정된 주제나 주석이 공개 보기에서 숨겨지지 않습니다. 그렇지 않은 경우 이 숫자는 중재 임계값보다 크거나 같아야 합니다. 기본값은 5입니다.

### 태그 필드 탭 {#tag-field-tab}

아래에 **[!UICONTROL 태그 필드]** 탭, **[!UICONTROL 설정]** 탭은 선택한 네임스페이스에 따라 제한됩니다.

* **[!UICONTROL 허용되는 네임스페이스]**
관련 있는 경우 
`Allow Tagging` 이(가) **설정** 탭. 적용할 수 있는 태그는 선택한 네임스페이스 카테고리 내의 태그로 제한됩니다. 네임스페이스 목록에는 &quot;표준 태그&quot;(기본 네임스페이스)와 &quot;모든 태그 포함&quot;이 포함되어 있습니다. 기본값이 선택되어 있지 않으므로 모든 네임스페이스가 허용됩니다.

* **[!UICONTROL 제안 제한]**
포럼에 게시하기 위해 회원에게 제안으로 표시할 태그의 수를 입력합니다. 값 
**-** 1은 제한이 없음을 의미합니다. 기본값은 0입니다.

### 정렬 설정 탭 {#sort-settings-tab}

아래에 **[!UICONTROL 정렬 설정]** 탭에서 표시되는 경우 게시된 주석이 정렬되는 방법을 지정합니다.

* **[!UICONTROL 정렬 기준]**
허용되는 모든 정렬 선택을 확인합니다. 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`을 따르지 않는 경우입니다. 기본값은 입니다. `Newest, Oldest, Last Updated`.

* **[!UICONTROL 기본값으로 설정]**
기본값으로 표시할 선택된 정렬 옵션 중 하나를 선택하려면 풀다운을 클릭합니다. 기본값은 입니다. 
`Newest`.

* **[!UICONTROL Analytics 정렬을 위한 시간 옵션 선택]**
아래로 당기면 다음 중 하나를 선택합니다. 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`을 따르지 않는 경우입니다. 기본값은 입니다. `All`.

## 사이트 방문자 경험 {#site-visitor-experience}

### 아이디어 만들기 {#creating-idea}

모든 커뮤니티 기능과 마찬가지로, 로그인하지 않은 경우 사이트 방문자는 아이디어를 읽거나 다른 의견(댓글 및 투표/좋아요)을 볼 수만 있습니다.

로그인하면 구성원이 새 아이디어를 만들 수 있습니다.

![chlimage_1-32](assets/chlimage_1-32.png)

아이디어를 제출하기 전에 구성원이 초안을 저장할 수 있습니다.

을(를) 선택하여 `Save as Draft` 버튼을 누르면 초안이 저장됩니다.

![chlimage_1-33](assets/chlimage_1-33.png)

에서 저장된 초안을 볼 때 `My Drafts` 탭, 선택 `Read More` 편집 모드를 다시 입력하려면

![chlimage_1-34](assets/chlimage_1-34.png)

#### 피드백 제공 {#providing-feedback}

아이디어가 게시되면 다른 구성원이 로그인한 다음 아이디어를 열 수 있습니다( `Read More`)과 마찬가지로, 따라서 투표 수에 추가하고, 의견을 작성하십시오.

![chlimage_1-35](assets/chlimage_1-35.png)

### 추가 정보 {#additional-information}

자세한 내용은 [Ideation Essentials](ideation.md) 개발자를 위한 페이지입니다.

게시된 항목 및 댓글에 대한 중량은 [사용자가 생성한 컨텐츠 중재](moderate-ugc.md).

게시된 항목 및 댓글에 태깅하려면 다음을 참조하십시오 [사용자 생성 컨텐츠에 태깅](tag-ugc.md).
