---
title: 커뮤니티 구성 요소 기본 사항
seo-title: Communities Components Basics
description: 편집 모드에서 AEM 사이트에 커뮤니티 기능 추가 및 구성 요소 구성
seo-description: Add Communities features to AEM sites in edit mode and configure components
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
exl-id: 17fbee1c-5657-442a-8c9d-1456b853f666
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 4%

---

# 커뮤니티 구성 요소 기본 사항 {#communities-components-basics}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

설명서의 작성 섹션에서는 작성자 편집 모드에서 AEM 사이트에 커뮤니티 기능을 추가하는 방법과 구성 요소 구성을 설명합니다.

구성 요소는 AEM 인스턴스 및 대화형 을 사용하여 탐색할 수 있습니다 [커뮤니티 구성 요소 안내서](components-guide.md).

## 커뮤니티 구성 요소 액세스 {#accessing-communities-components}

페이지 컨텐츠를 작성할 때 기본 템플릿으로 페이지의 디자인을 변경할 수 있는 경우 구성 요소 브라우저에서 사이트 디자인의 일부로 아직 사용할 수 없는 구성 요소를 활성화할 수 있습니다.

사용 가능한 커뮤니티 구성 요소가 나열됩니다 [여기](author-communities.md#available-communities-components).

>[!NOTE]
>
>일반 작성 정보에 대해서는 [페이지 작성에 대한 빠른 안내](../../help/sites-authoring/qg-page-authoring.md).
>
>AEM에 익숙하지 않은 경우 다음 문서를 참조하십시오. [기본 처리](../../help/sites-authoring/basic-handling.md).

### 디자인 모드 시작 {#entering-design-mode}

다음과 같은 경우 **커뮤니티** 구성 요소 브라우저(사이드 킥함)에 구성 요소를 찾을 수 없으면 를 입력해야 합니다 `Design Mode` 다른 커뮤니티 구성 요소를 추가하려면 [필수 클라이언트 측 라이브러리](#required-clientlibs) (clientlibs)도 추가해야 할 수 있습니다.

자세한 내용은 [디자인 모드에서 구성 요소 구성](../../help/sites-authoring/default-components-designmode.md).

다음은 몇 개의 커뮤니티 구성 요소를 선택하고 구성 요소 브라우저에서 보는 이미지입니다.

![chlimage_1-424](assets/chlimage_1-424.png)

이제 선택한 구성 요소를 구성 요소 브라우저에서 사용할 수 있습니다.

![chlimage_1-425](assets/chlimage_1-425.png)

## 필수 Clientlibs {#required-clientlibs}

[클라이언트 측 라이브러리](../../help/sites-developing/clientlibs.md) (clientlibs)는 구성 요소의 적절한 작동(JavaScript) 및 스타일(CSS)에 필요합니다.

페이지에 Communities 구성 요소를 추가할 때 결과가 오류이거나 예기치 않은 모양일 경우 먼저 Communities 구성 요소에 필요한 clientlibs를 추가해 보십시오. 자세한 내용은 [커뮤니티 구성 요소용 Clientlibs](clientlibs.md).

### 예: 처음에 클라이언트 라이브러리 없이 검토함.. {#example-initially-placed-reviews-without-client-libraries}

![chlimage_1-426](assets/chlimage_1-426.png)

### ... 클라이언트 라이브러리 사용 {#and-with-client-libraries}

![chlimage_1-427](assets/chlimage_1-427.png)

## 태그 지정 {#tagging}

많은 커뮤니티 기능을 구성원이 게시 환경에 입력(게시된)된 컨텐츠에 태그를 지정할 수 있도록 구성할 수 있습니다.

태깅이 허용되면 커뮤니티 사이트의 구성을 설정하여 게시 환경의 구성원에게 제공되는 네임스페이스를 제한할 수 있습니다. 자세한 내용은 [커뮤니티 사이트 콘솔](sites-console.md#tagging).

태깅을 허용하는 기능: [블로그](blog-feature.md), [달력](calendar.md), [파일 라이브러리](file-library.md), [포럼](forum.md)

태그를 사용하는 기능: [카탈로그](catalog.md), [검색](search.md), [소셜 태그 클라우드](tagcloud.md)

작성 정보:

* [태그 사용](../../help/sites-authoring/tags.md)

관리 정보:

* 태그 네임스페이스(분류) 만들기: [태그 관리](../../help/sites-administering/tags.md)
* 커뮤니티 사이트 구성: 참조 [태깅](sites-console.md#tagging)
* [사용자 생성 컨텐츠에 태깅](../../help/sites-authoring/tags.md)
* [태깅 지원 리소스](tag-resources.md)

개발자 정보:

* [AEM 태그 지정 프레임워크](../../help/sites-developing/framework.md)
* [태깅 핵심 사항](tag.md)
