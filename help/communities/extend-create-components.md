---
title: 구성 요소 만들기
seo-title: 구성 요소 만들기
description: 댓글 구성 요소 만들기
seo-description: 댓글 구성 요소 만들기
uuid: ea6e00d4-1db7-40ef-ae49-9ec55df58adf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 83c4f18a-d7d6-4090-88c7-41a9075153b5
exl-id: 48809969-5d14-41bb-bc6d-5857e679ceba
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 4%

---

# 구성 요소 {#create-the-components} 만들기

구성 요소 확장 예제는 실제로 두 구성 요소로 구성된 주석 시스템을 사용합니다

* 주석 - 페이지에 배치된 구성 요소인 감싸는 주석 시스템
* 댓글 - 게시된 댓글의 인스턴스를 캡처하는 구성 요소입니다

두 구성 요소를 모두 배치해야 합니다. 특히 게시된 메모의 모양을 사용자 지정할 때 이러한 기능이 적용되어야 합니다.

>[!NOTE]
>
>사이트 페이지당 하나의 댓글 시스템만 허용됩니다.
>
>많은 커뮤니티 기능에는 확장된 주석 시스템을 참조하도록 resourceType을 수정할 수 있는 주석 시스템이 이미 포함되어 있습니다.

## 댓글 구성 요소 {#create-the-comments-component} 만들기

이러한 지침은 구성 요소 브라우저(사이드 킥함)에서 구성 요소를 사용할 수 있도록 **Group** 이외의 값을 지정합니다.`.hidden`

자동 생성된 JSP 파일의 삭제는 기본 HBS 파일이 대신 사용되기 때문입니다.

1. **CRXDE|Lite**([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp))로 이동합니다.

1. 사용자 정의 응용 프로그램의 위치를 만듭니다.

   * `/apps` 노드를 선택합니다

      * **사용자** 지정 폴더  **[!UICONTROL 만들기]**
   * `/apps/custom` 노드를 선택합니다

      * **폴더** 이름이 지정된  **[!UICONTROL 구성 요소 만들기]**


1. `/apps/custom/components` 노드를 선택합니다

   * **[!UICONTROL 만들기 > 구성 요소..]**

      * **레이블**: *댓글*
      * **제목**: *대체 댓글*
      * **설명**: *대체 댓글 스타일*
      * **수퍼 유형**: *social/commons/components/hbs/comments*
      * **그룹**: *사용자 지정*
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
   * **[!UICONTROL 확인]** 선택


1. 방금 생성된 노드를 확장합니다.`/apps/custom/components/comments`
1. **[!UICONTROL 모두 저장]** 선택
1. `comments.jsp` 마우스 오른쪽 단추 클릭
1. **[!UICONTROL 삭제]** 선택
1. **[!UICONTROL 모두 저장]** 선택

![chlimage_1-70](assets/chlimage_1-70.png)

### 하위 주석 구성 요소 {#create-the-child-comment-component} 만들기

다음 지침은 상위 구성 요소만 페이지 내에 포함해야 하므로 **그룹**&#x200B;을 `.hidden`로 설정합니다.

자동 생성된 JSP 파일의 삭제는 기본 HBS 파일이 대신 사용되기 때문입니다.

1. `/apps/custom/components/comments` 노드로 이동합니다.
1. 노드를 마우스 오른쪽 단추로 클릭합니다.

   * **[!UICONTROL 만들기 > 구성 요소... 를 선택합니다.]**

      * **레이블**: *댓글*
      * **제목**: *대체 주석*
      * **설명**: *대체 주석 스타일*
      * **수퍼 유형**: *social/commons/components/hbs/comments/comment*
      * **그룹**: `*.hidden*`
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
   * **[!UICONTROL 확인]** 선택


1. 방금 생성된 노드를 확장합니다.`/apps/custom/components/comments/comment`
1. **[!UICONTROL 모두 저장]** 선택
1. `comment.jsp` 마우스 오른쪽 단추 클릭
1. **[!UICONTROL 삭제]** 선택
1. **[!UICONTROL 모두 저장]** 선택

![chlimage_1-71](assets/chlimage_1-71.png) ![chlimage_1-72](assets/chlimage_1-72.png)

### 기본 HBS 스크립트 복사 및 수정 {#copy-and-modify-the-default-hbs-scripts}

[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) 사용:

* 복사 `comments.hbs`

   * [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)에서
   * 대상 [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* `comments.hbs` 편집 대상:

   * `data-scf-component` 특성 값 변경(~20행):

      * 시작 `social/commons/components/hbs/comments`
      * 끝 `/apps/custom/components/comments`
   * 사용자 지정 주석 구성 요소(~75행)를 포함하도록 수정합니다.

      * 바꾸기 `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * 사용 `{{include this resourceType='/apps/custom/components/comments/comment'}}`


* 복사 `comment.hbs`

   * [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)에서
   * 대상 [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* `comment.hbs` 편집 대상:

   * data-scf-component 속성(~ 라인 19)의 값을 변경합니다.

      * 시작 `social/commons/components/hbs/comments/comment`
      * 끝 `/apps/custom/components/comments/comment`

* `/apps/custom` 노드 선택
* **[!UICONTROL 모두 저장]** 선택

## 클라이언트 라이브러리 폴더 {#create-a-client-library-folder} 만들기

이 클라이언트 라이브러리를 명시적으로 포함해야 하지 않도록 하기 위해 기본 주석 시스템의 clientlib에 대한 카테고리 값을 사용할 수 있습니다( `cq.social.author.hbs.comments`). 그러나 이 clientlib은 기본 구성 요소의 모든 인스턴스에도 포함됩니다.

[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) 사용:

* `/apps/custom/components/comments` 노드 선택
* **[!UICONTROL 노드 만들기]** 를 선택합니다.

   * **이름**: `clientlibs`
   * **유형**: `cq:ClientLibraryFolder`
   * **[!UICONTROL 속성]** 탭에 추가:

      * **** `categories` **** `String` **NameTypeValue** `cq.social.author.hbs.comments` `Multi`
      * **** `dependencies` **** `String` **NameTypeValue** `cq.social.scf` `Multi`

* **[!UICONTROL 모두 저장]** 선택
* `/apps/custom/components/comments/clientlib`s 노드를 선택한 상태에서 3개의 파일을 만드십시오.

   * **이름**: `css.txt`
   * **이름**: `js.txt`
   * **이름**:customexsystem.js

* `js.txt`의 콘텐츠로 &#39;customcommentsystem.js&#39;를 입력합니다.
* **[!UICONTROL 모두 저장]** 선택

![chlimage_1-73](assets/chlimage_1-73.png)

## SCF 모델 및 보기 {#register-the-scf-model-view} 등록

SCF 구성 요소를 확장(재정의)할 때 resourceType은 다릅니다(오버레이하면 resourceType이 동일하게 유지되도록 `/libs` 전에 `/apps`을 통해 검색하는 상대 검색 메커니즘을 사용합니다.). 따라서 사용자 지정 resourceType에 대해 SCF JS 모델을 등록하고 보기를 등록하기 위해 클라이언트 라이브러리에서 JavaScript를 작성해야 합니다.

다음 텍스트를 `customcommentsystem.js` 의 컨텐츠로 입력합니다.

### customexsystem.js {#customcommentsystem-js}

```xml
(function($CQ, _, Backbone, SCF) {
    "use strict";
 
    var CustomComment = SCF.Components["social/commons/components/hbs/comments/comment"].Model;
    var CustomCommentView = SCF.Components["social/commons/components/hbs/comments/comment"].View;

    var CustomCommentSystem = SCF.Components["social/commons/components/hbs/comments"].Model;
    var CustomCommentSystemView = SCF.Components["social/commons/components/hbs/comments"].View;
 
    SCF.registerComponent('/apps/custom/components/comments/comment', CustomComment, CustomCommentView);
    SCF.registerComponent('/apps/custom/components/comments', CustomCommentSystem, CustomCommentSystemView);

})($CQ, _, Backbone, SCF);
```

* **[!UICONTROL 모두 저장]** 선택

## 앱 {#publish-the-app} 게시

게시 환경에서 확장 구성 요소를 경험하려면 사용자 지정 구성 요소를 복제해야 합니다.

한 가지 방법은 다음과 같습니다

* 전역 탐색에서

   * **[!UICONTROL 도구 > 배포 > 복제]**&#x200B;를 선택합니다.
   * 선택 `Activate Tree`
   * `Start Path` 설정:`/apps/custom`
   * `Only Modified` 선택을 취소합니다.
   * `Activate`단추 선택
