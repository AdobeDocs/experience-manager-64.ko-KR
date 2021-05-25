---
title: 활동 트렌드
seo-title: 활동 트렌드
description: 페이지에 커뮤니티 활동 목록 구성 요소 추가
seo-description: 페이지에 커뮤니티 활동 목록 구성 요소 추가
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 5%

---

# 활동 트렌드 {#activity-trends}

## 소개 {#introduction}

`Community Activity List` 구성 요소는 컨텐츠 게시물 및 뷰뿐만 아니라 구성원의 게시물 및 보기에 대한 트렌드 정보를 추가할 수 있는 기능을 제공합니다.

설명서의 이 섹션에서는 다음 사항에 대해 설명합니다

* [커뮤니티 사이트](overview.md#community-sites)에 `Community Activity List` 구성 요소 추가

* `Community Activity List` 구성 요소에 대한 구성 설정

## 요구 사항 {#requirement}

`Community Activity List` 데이터는 Adobe Analytics에 대한 라이센스가 있고 커뮤니티 사이트에 대해 구성된 경우에만 사용할 수 있습니다.

[커뮤니티 기능에 대한 분석 구성](analytics.md)을 참조하십시오.

## 페이지에 커뮤니티 활동 목록 추가 {#adding-a-community-activity-list-to-a-page}

작성자 모드의 페이지에 `Community Activity List` 구성 요소를 추가하려면 구성 요소 `Communities / Community Activity List`을 찾아 페이지에 배치합니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md)을 방문하십시오.

커뮤니티 사이트의 페이지에 처음 배치되면 구성 요소가 다음과 같이 나타납니다.

![chlimage_1-227](assets/chlimage_1-227.png)

## 커뮤니티 활동 목록 구성 중 {#configuring-community-activity-list}

액세스할 배치된 `Community Activity List` 구성 요소를 선택하고 편집 대화 상자를 여는 `Configure` 아이콘을 선택합니다.

![chlimage_1-228](assets/chlimage_1-228.png)

**[!UICONTROL 댓글]** 탭에서 업로드된 파일에 대한 주석이 표시되는 여부와 방법을 지정합니다.

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL 유형]**

   커뮤니티 구성원과 관련된 데이터를 표시할지 또는 UGC(사용자 생성 콘텐츠)에 데이터를 표시할지를 지정합니다.

   선택 위치
   * `Members`
   * `Content`

   기본값은 `Members`입니다.

* **[!UICONTROL 표시 제목]**

   데이터 위에 표시할 설명 제목(예: `Trending Content`)입니다.

   기본값은 제목이 아닙니다.

* **[!UICONTROL 표시 개수]**

   나열할 항목의 수입니다.

   기본값은 10입니다.

* **[!UICONTROL 활동 유형]**

   다음 중 하나를 선택합니다
   * `Views`(페이지 방문 횟수)
   * `Posts`(UGC 만들기)
   * `Follows`
   * `Likes`

   기본값은 보기입니다.

* **[!UICONTROL 기간]**

   다음 중 하나를 선택합니다
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   기본값은 `Total`입니다.

* **[!UICONTROL 컨텍스트 경로]**

   특정 블로그와 같이 활동의 범위를 사이트의 하위 집합으로 지정하는 기능을 제공합니다.

   기본값은 전체 커뮤니티 사이트입니다.

* **[!UICONTROL 구성원 수 집계]**

   선택 취소(꺼짐)되면 최상위 게시물만 카운트됩니다. 예를 들어 컨텍스트가 루트 페이지(기본값)인 경우 루트 페이지에 컨텐츠를 게시할 수 없으므로 `Posts`의 `Activity Type`은 활동을 표시하지 않습니다. 이 옵션을 선택하면 모든 하위 페이지의 카운트가 포함됩니다.

   기본값이 선택되어 있습니다.

## 4개의 구성 요소 {#example-page-with-components}가 있는 예제 페이지

**상위** 방문자 구성:유형 = 구성원, 활동 유형 = 보기

**상위** 기여도 구성:유형 = 구성원, 활동 유형 = 게시물

**상위** 콘텐츠 구성:유형 = 컨텐츠, 활동 유형 = 보기,

**트렌드** 콘텐츠 구성:유형 = 컨텐츠, 활동 유형 = 게시물

![chlimage_1-230](assets/chlimage_1-230.png)
