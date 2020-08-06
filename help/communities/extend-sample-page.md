---
title: 샘플 페이지에 주석 추가
seo-title: 샘플 페이지에 주석 추가
description: 페이지에 사용자 지정 주석 추가
seo-description: 페이지에 사용자 지정 주석 추가
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
translation-type: tm+mt
source-git-commit: 44c56ec5de6e9a832aaa52ab4a6c4978af7a9865
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# 샘플 페이지에 주석 추가 {#add-comment-to-sample-page}

사용자 지정 댓글 시스템의 구성 요소가 응용 프로그램 디렉토리(/apps)에 배치되었으므로 확장 구성 요소를 사용할 수 있습니다. 영향을 받을 웹 사이트의 주석 시스템 인스턴스는 resourceType을 사용자 지정 주석 시스템으로 설정하고 필요한 모든 클라이언트 라이브러리를 포함해야 합니다.

## 필수 클라이언트 식별 {#identify-required-clientlibs}

기본 주석의 스타일 및 기능에 필요한 클라이언트 라이브러리는 확장된 주석에도 필요합니다.

커뮤니티 [구성 요소 안내서는](components-guide.md) 필요한 클라이언트 라이브러리를 식별합니다. 구성 요소 안내서로 이동하고 주석 구성 요소를 봅니다. 예:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

주석을 렌더링하고 제대로 작동하는 데 필요한 세 개의 클라이언트 라이브러리를 확인하십시오. 확장된 주석을 참조하거나 [확장된 댓글 클라이언트 라이브러리](extend-create-components.md#create-a-client-library-folder) ()를 참조하면 `apps.custom.comments`포함됩니다.

![chlimage_1-47](assets/chlimage_1-47.png)

## 페이지에 사용자 지정 주석 추가 {#add-custom-comments-to-a-page}

페이지당 하나의 주석 시스템만 있을 수 있으므로 짧은 샘플 페이지 [만들기 자습서에 설명된 대로 샘플 페이지를 만드는 것이](create-sample-page.md) 쉽습니다.

일단 만들어지면 디자인 모드로 전환하고 사용자 지정 구성 요소 그룹을 사용하여 구성 요소를 페이지에 추가할 수 있도록 `Alt Comments` 합니다.

주석이 표시되고 제대로 작동하려면, 댓글용 클라이언트 라이브러리를 페이지의 clientlibslist에 추가해야 합니다(커뮤니티 구성 요소의 [클라이언트 라이브러리 참조](clientlibs.md)).

### 샘플 페이지의 댓글 클라이언트 {#comments-clientlibs-on-sample-page}

![샘플 페이지의 댓글 클라이언트](assets/chlimage_1-48.png)

### 작성자: 샘플 페이지의 대체 주석 {#author-alt-comment-on-sample-page}

![샘플 페이지의 대체 주석](assets/chlimage_1-49.png)

### 작성자: 샘플 페이지 주석 노드 {#author-sample-page-comments-node}

샘플 페이지의 주석 노드 속성을 확인하여 CRXDE의 resourceType을 확인할 수 있습니다 `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### 게시 샘플 페이지 {#publish-sample-page}

사용자 지정 구성 요소가 페이지에 추가되면 페이지를 [게시해야 합니다](sites-console.md#publishing-the-site).

### 게시: 샘플 페이지의 대체 주석 {#publish-alt-comment-on-sample-page}

사용자 지정 응용 프로그램과 샘플 페이지를 모두 게시한 후에는 댓글을 입력할 수 있습니다. 데모 사용자 [](tutorials.md#demo-users) 또는 관리자를 사용하여 로그인하면 댓글을 게시할 수 있습니다.

aaron.mcdonald@mailinator.com댓글을 게시합니다.

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

확장 구성 요소가 기본 모양으로 올바르게 작동하므로 이제 모양을 수정할 때가 되었습니다.

