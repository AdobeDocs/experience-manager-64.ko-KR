---
title: 모양 변경
seo-title: Alter the Appearance
description: 스크립트 수정
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# 모양 변경 {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 스크립트 수정 {#modify-the-script}

comment.hbs 스크립트는 각 주석에 대한 전체 HTML을 생성합니다.

게시된 각 댓글 옆에 아바타를 표시하지 않으려면:

1. 복사 `comment.hbs`변환 전: `libs`to `apps`
   1. 선택 `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. 선택 **[!UICONTROL 복사]**
   1. 선택 `/apps/social/commons/components/hbs/comments/comment`
   1. 선택 **[!UICONTROL 붙여넣기]**
1. 오버레이된 `comment.hbs`
   * 노드를 두 번 클릭  `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. 다음 줄을 찾아 삭제하거나 주석을 답니다.

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

행을 삭제하거나 &#39;&lt;!>—&#39; 및 &#39;—>&#39;을(를) 주석 처리하여 또한 &#39;xxx&#39;라는 캐릭터를 아바타 위치에 대한 시각적 표시기로 추가할 예정이다.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## 오버레이 복제 {#replicate-the-overlay}

복제 도구를 사용하여 오버레이된 주석 구성 요소를 게시 인스턴스에 푸시합니다.

>[!NOTE]
>
>더욱 강력한 복제 방식은 패키지 관리자에서 패키지를 만들고 [활성화](../../help/sites-administering/package-manager.md#replicating-packages) 그래 패키지를 내보내고 보관할 수 있습니다.

전역 탐색에서 를 선택합니다 **[!UICONTROL 도구 > 배포 > 복제]** 그리고 **[!UICONTROL 트리 활성화]**.

Start Path에 대해 를 입력합니다. `/apps/social/commons` 을(를) 선택합니다. **[!UICONTROL 활성화]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## 결과 보기 {#view-results}

관리자로 게시 인스턴스에 로그인하는 경우(예: 관리자/관리자로 http://localhost:4503/crx/de) 오버레이된 구성 요소가 있는지 확인할 수 있습니다.

로그아웃한 다음 다시 로그인하는 경우 `aaron.mcdonald@mailinator.com/password` 페이지를 새로 고치면 게시된 주석이 더 이상 아바타와 함께 표시되지 않고 간단한 &#39;xxx&#39;가 표시됩니다.

![chlimage_1-43](assets/chlimage_1-43.png)
