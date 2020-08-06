---
title: 모양 변경(HBS)
seo-title: 모양 변경
description: HBS 스크립트 수정
seo-description: HBS 스크립트 수정
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---


# 모양 변경(HBS) {#alter-the-appearance-hbs}

이제 응용 프로그램 디렉터리(/apps)의 사용자 지정 주석 시스템에 대한 구성 요소가 제대로 사용되고, resourceSuperType이 기본 주석 시스템 및 등록된 사용자 지정 모델/보기를 참조하므로 구현을 수정할 수 있습니다.

간단한 데모에서는 댓글을 게시한 로그인한 사용자의 아바타가 제거됩니다.

>[!NOTE]
>
>확장 기능을 사용하려면, 영향을 받을 웹 사이트의 댓글 시스템 인스턴스(/content)가 resourceType을 사용자 지정 주석 시스템으로 설정해야 합니다.

## HBS 스크립트 수정 {#modify-the-hbs-scripts}

CRXDE Lite [사용](../../help/sites-developing/developing-with-crxde-lite.md):

* /apps/custom/components/comments/comment/comment.hbs [열기](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * 댓글 게시물에 대한 아바타가 포함된 태그에 주석 추가(~ 줄 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* /apps/custom/components/comments/comments.hbs [열기](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * 다음 주석 항목에 대한 아바타가 포함된 태그에 주석 추가(~ 줄 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* 모두 **저장 선택**

## 사용자 정의 앱 복제 {#replicate-custom-app}

애플리케이션을 수정한 후에는 사용자 지정 구성 요소를 다시 복제해야 합니다.

방법 중 하나는

* 주 메뉴에서

   * 도구 **[!UICONTROL > 작업 > 복제를 선택합니다.]**
   * 선택 `Activate Tree`
   * 설정 `Start Path`: to `/apps/custom`
   * 선택 취소 `Only Modified`
   * 선택 `Activate` 단추

## 게시된 샘플 페이지에서 수정된 주석 보기 {#view-modified-comment-on-published-sample-page}

[동일한 사용자로 로그인되어 있는 게시 인스턴스에서 경험을](extend-sample-page.md#publish-sample-page) 계속 진행하면 이제 아바타를 제거하기 위한 수정 사항을 보기 위해 게시 환경에서 페이지를 새로 고칠 수 있습니다.

![chlimage_1-81](assets/chlimage_1-81.png)

## 샘플 주석 확장 패키지 {#sample-comment-extension-package}

이 튜토리얼에서 만든 사용자 지정 댓글 응용 프로그램의 패키지가 첨부됩니다.

[파일 가져오기](assets/sample-comment-extension-6-1-fp3.zip)