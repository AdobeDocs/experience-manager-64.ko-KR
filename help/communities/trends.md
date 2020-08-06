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
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 5%

---


# 활동 트렌드 {#activity-trends}

## 소개 {#introduction}

이 구성 요소는 컨텐츠의 게시물 및 보기뿐만 아니라 구성원의 게시물 및 보기와 관련된 트렌드 정보를 추가하는 기능을 제공합니다. `Community Activity List`

설명서의 이 섹션에서는

* 커뮤니티 사이트에 구성 `Community Activity List` 요소 [추가](overview.md#community-sites)

* 구성 요소에 대한 `Community Activity List` 구성 설정

## 요구 사항 {#requirement}

커뮤니티 사이트 `Community Activity List` 에 대한 Adobe Analytics 라이선스가 부여되고 구성된 경우에만 해당 사이트의 데이터를 사용할 수 있습니다.

커뮤니티 [기능에 대한 분석 구성을 참조하십시오](analytics.md).

## 페이지에 커뮤니티 활동 목록 추가 {#adding-a-community-activity-list-to-a-page}

작성 모드에서 페이지에 `Community Activity List` 구성 요소를 추가하려면 구성 요소를 찾아 페이지에 `Communities / Community Activity List` 배치합니다.

필요한 정보를 보려면 커뮤니티 구성 요소 [기본 사항을 방문하십시오](basics.md).

커뮤니티 사이트의 페이지에 처음 배치하면 구성 요소가 표시되는 방식입니다.

![chlimage_1-227](assets/chlimage_1-227.png)

## 커뮤니티 활동 목록 구성  {#configuring-community-activity-list}

액세스할 배치된 `Community Activity List` 구성 요소를 선택하고 편집 대화 상자를 여는 `Configure` 아이콘을 선택합니다.

![chlimage_1-228](assets/chlimage_1-228.png)

[ **[!UICONTROL 주석]** ] 탭에서 업로드한 파일에 대한 댓글이 표시되는 여부와 방법을 지정합니다.

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL 유형]**

   커뮤니티 구성원 또는 사용자 생성 콘텐츠(UGC)에 대한 데이터를 표시할지 여부를 지정합니다.

   선택 위치
   * `Members`
   * `Content`

   기본값은 `Members`입니다.

* **[!UICONTROL 표시 제목]**

   데이터 위에 표시할 설명 제목입니다(예: `Trending Content`).

   기본값은 제목이 아닙니다.

* **[!UICONTROL 표시 개수]**

   나열할 항목 수입니다.

   기본값은 10입니다.

* **[!UICONTROL 활동 유형]**

   다음 중 하나 선택
   * `Views`(페이지 방문 횟수)
   * `Posts`(UGC 만들기)
   * `Follows`
   * `Likes`

   기본값은 뷰입니다.

* **[!UICONTROL 기간]**

   다음 중 하나 선택
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

   선택 취소(꺼짐)되면 최상위 게시물만 카운트됩니다. 예를 들어, 컨텍스트가 루트 페이지(기본값)인 경우 루트 페이지 `Activity Type`에 컨텐츠를 게시할 수 `Posts`있는 기능이 없기 때문에 어떤 활동도 표시되지 않습니다. 이 확인란을 선택하면 모든 하위 페이지의 카운트가 포함됩니다.

   기본값은 선택되어 있습니다.

## 4개의 구성 요소가 있는 예제 페이지 {#example-page-with-components}

**상위 방문자** 구성: 유형 = 멤버, 활동 유형 = 보기

**상위 작성자** 구성: 유형 = 멤버, 활동 유형 = 게시물

**상위 컨텐츠** 구성: 유형 = 컨텐트, 활동 유형 = 보기,

**트렌드 콘텐츠** 구성: 유형 = 컨텐츠, 활동 유형 = 게시물

![chlimage_1-230](assets/chlimage_1-230.png)
