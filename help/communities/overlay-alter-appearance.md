---
title: 모양 변경
seo-title: 모양 변경
description: 스크립트 수정
seo-description: 스크립트 수정
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
translation-type: tm+mt
source-git-commit: 1ae2d7f99286e0b958d343778159e2d35095510e
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---


# 모양 변경 {#alter-the-appearance}

## 스크립트 수정 {#modify-the-script}

comment.hbs 스크립트에서는 각 댓글에 대한 전체 HTML을 만듭니다.

게시된 각 댓글 옆에 아바타를 표시하지 않으려면:

1. 복사 `comment.hbs`위치 `libs`는 `apps`
   1. 선택 `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. 복사 **[!UICONTROL 선택]**
   1. 선택 `/apps/social/commons/components/hbs/comments/comment`
   1. 붙여넣기 **[!UICONTROL 선택]**
1. 오버레이된 `comment.hbs`
   * 노드 `comment.hbs`를 두 번 클릭 `/apps/social/commons/components/hbs/comments/comment folder`
1. 다음 줄을 찾아 삭제하거나 주석을 답니다.

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

행을 삭제하거나 &#39;&lt;!—&#39; 및 &#39;—>&#39;을(를) 사용하여 주석을 지정합니다. 또한 &#39;xxx&#39; 문자는 아바타가 있었던 위치를 보여주는 시각적 표시기로 추가되고 있습니다.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## 오버레이 복제 {#replicate-the-overlay}

복제 도구를 사용하여 겹쳐진 주석 구성 요소를 게시 인스턴스에 푸시합니다.

>[!NOTE]
>
>더욱 강력한 복제 방식은 패키지 관리자에서 패키지를 만들어 [활성화하](../../help/sites-administering/package-manager.md#replicating-packages) 는 것입니다. 패키지를 내보내고 보관할 수 있습니다.

전역 탐색에서 **[!UICONTROL 도구 > 배포 > 복제를]** 선택한 다음 트리 **[!UICONTROL 활성화를 선택합니다]**.

시작 경로 `/apps/social/commons` 에 입력하고 활성화 **[!UICONTROL 를 선택합니다]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## 결과 보기 {#view-results}

게시 인스턴스에 관리자로 로그인하는 경우(예: http://localhost:4503/crx/de as admin/admin), 겹쳐진 구성 요소가 있는지 확인할 수 있습니다.

로그아웃한 후 다시 로그인하고 페이지를 새로 고치면 게시된 댓글이 더 이상 아바타와 함께 표시되지 않고 간단한 &#39;xxx&#39;이 표시됩니다. `aaron.mcdonald@mailinator.com/password`

![chlimage_1-43](assets/chlimage_1-43.png)

