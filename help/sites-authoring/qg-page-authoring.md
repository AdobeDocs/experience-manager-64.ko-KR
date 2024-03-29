---
title: 페이지 작성에 대한 빠른 안내
seo-title: Quick Guide to Authoring Pages
description: 페이지 컨텐츠를 작성하는 주요 작업에 대한 빠른 개요 안내서
seo-description: A quick, high-level guide to the key actions of authoring page content
uuid: 35442d98-caf9-4cdb-8e68-4fc611e66290
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 163a4887-7c33-4305-8c48-882630f2caa1
exl-id: c63e44e7-cc89-4fa0-8ba4-460d682df601
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 60%

---

# 페이지 작성에 대한 빠른 안내{#quick-guide-to-authoring-pages}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이러한 절차는 AEM에서 페이지 컨텐츠를 작성하는 주요 작업에 대한 빠른 안내(개요)를 위한 것입니다.

절차는 다음과 같습니다.

* 포괄적인 내용을 담고 있지는 않습니다.
* 자세한 설명서에 대한 링크를 제공합니다.

AEM을 사용한 작성 작업에 대한 자세한 내용은 다음을 참조하십시오.

* [작성자를 위한 첫 번째 단계](/help/sites-authoring/first-steps.md)
* [작성 환경 사용](/help/sites-authoring/author-environment-tools.md)

## 몇 가지 빠른 힌트 {#a-few-quick-hints}

여기에는 세부 사항 개요를 제공하기 전에 기억해야 하는(특히 를 사용하는 경우) 몇 가지 팁과 힌트가 나와 있습니다 [클래식 UI 작성 환경](/help/sites-classic-ui-authoring/classicui.md).

### 사이트 콘솔 {#sites-console}

* **만들기**

   * 이 버튼은 여러 콘솔에서 사용할 수 있습니다. 제공된 옵션은 상황에 맞는 옵션이므로 시나리오에 따라 달라질 수 있습니다.

* 폴더의 페이지 순서 재지정

   * 이 작업은 [목록 보기](/help/sites-authoring/basic-handling.md#list-view)에서 수행할 수 있습니다. 변경 사항이 적용되고 다른 보기에서 볼 수 있습니다.

* UI 변경

   * 이 작업은 다양한 위치에서 수행할 수 있습니다. 자세한 내용은 [UI 선택](/help/sites-authoring/select-ui.md).

### 페이지 작성 {#page-authoring}

* 링크 탐색

   * ***링크를 탐색에 사용할 수 없습니다*** 언제 **편집** 모드. 링크를 사용하여 탐색하려면 다음 중 하나를 사용하여 [페이지 미리보기](/help/sites-authoring/editing-content.md#previewing-pages)를 수행해야 합니다.

      * [미리보기 모드](/help/sites-authoring/editing-content.md#preview-mode)
      * [게시됨으로 보기](/help/sites-authoring/editing-content.md#view-as-published)

* 워크플로우 및 버전은 더 이상 페이지 편집기에서 시작/작성되지 않습니다. 다음에서 이 작업을 수행합니다. [타임라인](/help/sites-authoring/basic-handling.md#timeline) (콘솔에서 액세스 가능).

>[!NOTE]
>
>작성 작업을 더 쉽게 해 줄 수 있는 다양한 키보드 단축키가 있습니다.
>
>* [페이지 편집 시 키보드 단축키](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
>* [콘솔용 키보드 단축키](/help/sites-authoring/keyboard-shortcuts.md)


## 페이지 찾기 {#finding-your-page}

1. Adobe Experience Manager 링크(왼쪽 상단)를 선택하면 트리거되는(드롭다운) **전역 탐색**&#x200B;에서 **사이트** 옵션을 사용하여 [사이트](/help/sites-authoring/basic-handling.md#global-navigation) 콘솔을 엽니다.

1. 해당 페이지를 탭/클릭하여 트리 아래로 탐색합니다. 페이지 리소스가 표시되는 방식은 사용 중인 보기([카드, 목록 또는 열](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources))에 따라 다릅니다.

   ![screen_shot_2018-03-21at160214](assets/screen_shot_2018-03-21at160214.png)

1. [헤더에서 탐색 표시](/help/sites-authoring/basic-handling.md#the-header)를 사용하여 트리 위로 탐색합니다. 그러면 선택한 위치로 돌아갈 수 있습니다.

   ![chlimage_1-95](assets/chlimage_1-95.png)

### 새 페이지 만들기 {#creating-a-new-page}

1. 새 페이지를 만들 [위치로 이동](#finding-your-page)합니다.
1. 를 사용하십시오 **만들기** 아이콘을 클릭한 다음 **페이지** 목록에서 다음을 수행합니다.

   ![screen_shot_2018-03-21at160324](assets/screen_shot_2018-03-21at160324.png)

1. 그러면 필요한 정보를 수집하는 과정을 안내하는 마법사가 열립니다 [새 페이지 만들기](/help/sites-authoring/managing-pages.md#creating-a-new-page). 화면에 표시되는 안내를 따르십시오.

## 추가 작업을 위한 페이지 선택 {#selecting-your-page-for-further-action}

작업을 수행할 수 있도록 페이지를 선택할 수 있습니다. 페이지를 선택하면 도구 모음이 자동으로 업데이트되어 해당 리소스와 관련된 작업이 표시됩니다.

페이지 선택 방법은 콘솔에서 사용 중인 보기에 따라 다릅니다.

1. 카드 보기:

   * 다음 방법으로 선택 모드 시작 [필요한 리소스 선택](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) 사용:

      * 모바일 장치: 길게 누르기
      * 데스크탑: a [빠른 작업](/help/sites-authoring/basic-handling.md#quick-actions) - 확인 표시 아이콘:

         ![screen_shot_2018-03-21at160503](assets/screen_shot_2018-03-21at160503.png)

      * 카드 위에 확인 표시가 나타나 페이지가 선택되었음을 나타냅니다.
   >[!NOTE]
   >
   >선택 모드에 있는 경우 **선택** 아이콘(확인 표시)이 **선택 취소** 아이콘(십자).

1. 목록 보기:

   * 필요한 리소스에 대한 썸네일을 탭/클릭합니다. 썸네일 위에 확인 표시가 나타나 페이지가 선택되었음을 나타냅니다.

1. 열 보기:

   * 필요한 리소스에 대한 썸네일을 탭/클릭합니다. 썸네일 위에 확인 표시가 나타나 페이지가 선택되었음을 나타냅니다.

## 빠른 작업(카드 보기/데스크탑 전용) {#quick-actions-card-view-desktop-only}

1. 작업을 수행할 [페이지로 이동](#finding-your-page)합니다.
1. 필요한 리소스를 나타내는 카드 위에 마우스 포인터를 놓습니다. 빠른 작업이 표시됩니다.

   ![screen_shot_2018-03-21at160503-1](assets/screen_shot_2018-03-21at160503-1.png)

## 페이지 콘텐츠 편집 {#editing-your-page-content}

1. 편집할 [페이지로 이동](#finding-your-page)합니다.
1. [편집(연필) 아이콘을 사용하여](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing) 편집할 페이지를 엽니다.

   ![screen_shot_2018-03-21at160607](assets/screen_shot_2018-03-21at160607.png)

   다음 방법 중 하나로 해당 아이콘에 액세스할 수 있습니다.

   * [빠른 작업(카드 보기/데스크탑 전용)](#quick-actions-card-view-desktop-only) 을 참조하십시오.
   * [페이지를 선택했을 때](#selecting-your-page-for-further-action)의 도구 모음

1. 편집기가 열리면 다음과 같은 작업을 수행할 수 있습니다.

   * [페이지에 새 구성 요소 추가](/help/sites-authoring/editing-content.md#inserting-a-component) 기준:

      * 사이드 패널 열기
      * 구성 요소 탭( [구성 요소 브라우저](/help/sites-authoring/author-environment-tools.md#components-browser))
      * 필요한 구성 요소를 페이지로 드래그

      다음 아이콘을 사용하여 사이드 패널을 열고 닫을 수 있습니다.

      ![](do-not-localize/screen_shot_2018-03-21at160738.png)

   * [페이지의](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) 기존 구성 요소 콘텐츠를 편집합니다.

      * 탭하거나 클릭하여 구성 요소 도구 모음을 엽니다. 를 사용하십시오 **편집** (연필) 아이콘을 클릭하여 대화 상자를 엽니다.
      * 탭한 상태를 유지하거나 느리게 더블 클릭하여 구성 요소에 대한 즉석 편집기를 엽니다. 사용 가능한 작업이 표시됩니다(일부 구성 요소의 경우 선택이 제한됨).
      * 사용 가능한 모든 작업을 보려면 다음을 사용하여 전체 화면 모드로 들어갑니다.

      ![](do-not-localize/screen_shot_2018-03-21at160706.png)

   * [기존 구성 요소의 속성 구성](/help/sites-authoring/editing-content.md#component-edit-dialog)

      * 탭하거나 클릭하여 구성 요소 도구 모음을 엽니다. 를 사용하십시오 **구성** (공구모양) 아이콘을 클릭하여 대화 상자를 엽니다.
   * [구성 요소 이동](/help/sites-authoring/editing-content.md#moving-a-component) 다음 중 하나를 선택합니다.

      * 필요한 구성 요소를 새 위치로 드래그합니다.
      * 탭하거나 클릭하여 구성 요소 도구 모음을 엽니다. 필요한 경우 **잘라내기** 및 **붙여넣기** 아이콘을 사용합니다.
   * [복사(및 붙여넣기)](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) 구성 요소:

      * 탭하거나 클릭하여 구성 요소 도구 모음을 엽니다. 필요에 따라 **복사** 및 **붙여넣기** 아이콘을 사용합니다.
      >[!NOTE]
      >
      >같은 페이지나 다른 페이지에 구성 요소를 **붙여넣을** 수 있습니다. 잘라내기/복사 작업 전에 이미 열려 있었던 다른 페이지에 붙여넣은 경우 해당 페이지를 새로 고쳐야 합니다.

   * 구성 요소 [삭제:](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)

      * 탭하거나 클릭하여 구성 요소 도구 모음을 열고 **삭제** 아이콘을 사용합니다.
   * [주석 추가](/help/sites-authoring/annotations.md#annotations) 아래와 같이 변경하는 것을 의미합니다.

      * 을(를) 선택합니다 **주석 달기** 모드(음성 버블 아이콘). 를 사용하여 주석 추가 **주석 추가** (더하기) 아이콘. 오른쪽 상단의 X를 사용하여 주석 모드를 끝냅니다.

      ![](do-not-localize/screen_shot_2018-03-21at160813.png)

   * [페이지 미리보기](/help/sites-authoring/editing-content.md#preview-mode)(게시 환경에 표시될 모양 보기)

      * 도구 모음에서 **미리보기**&#x200B;를 선택합니다.
   * 를 사용하여 편집 모드로 돌아가거나 다른 모드를 선택합니다. **편집** 드롭다운 선택기.

   >[!NOTE]
   >
   >콘텐츠에서 링크를 사용하여 탐색하려면 [미리보기 모드](/help/sites-authoring/editing-content.md#preview-mode)를 사용해야 합니다.

## 페이지 속성 편집 {#editing-the-page-properties}

에는 두 가지(기본) 방법이 있습니다 [페이지 속성 편집](/help/sites-authoring/editing-page-properties.md):

* **사이트** 콘솔에서:

   1. [페이지로 이동합니다](#finding-your-page) 게시하려는 경우
   1. 을(를) 선택합니다 **속성** 다음 중 하나에서 아이콘을 클릭합니다.

      * [빠른 작업(카드 보기/데스크탑 전용)](#quick-actions-card-view-desktop-only) 을 참조하십시오.
      * [페이지를 선택했을 때](#selecting-your-page-for-further-action)의 도구 모음

   ![screen_shot_2018-03-21at160850](assets/screen_shot_2018-03-21at160850.png)

* 페이지 속성이 표시됩니다. 필요에 따라 업데이트한 다음 [저장]을 사용하여 이러한 내용을 유지할 수 있습니다.

   * When [페이지 편집](#editing-your-page-content):

      1. 를 엽니다. **페이지 정보** 메뉴 아래의 제품에서 사용할 수 있습니다.
      1. 선택 **속성 열기** 를 클릭하여 속성을 편집할 대화 상자를 엽니다.

         ![screen_shot_2018-03-21at160920](assets/screen_shot_2018-03-21at160920.png)

## 페이지 게시(또는 게시 취소) {#publishing-your-page-or-unpublishing}

다음과 같은 두 가지 주요 방법이 있습니다 [페이지 게시](/help/sites-authoring/publishing-pages.md) (및 게시 취소에도 있음):

* **사이트** 콘솔에서:

   1. [페이지로 이동합니다](#finding-your-page) 게시하려는 경우
   1. 다음 중 하나에서 **빠른 게시** 아이콘을 선택합니다.

      * [빠른 작업(카드 보기/데스크탑 전용)](#quick-actions-card-view-desktop-only) 을 참조하십시오.
      * [페이지를 선택했을 때](#selecting-your-page-for-further-action)(또는 [나중에 게시](/help/sites-authoring/publishing-pages.md#manage-publication)에 액세스할 때)의 도구 모음

   ![screen_shot_2018-03-21at160957](assets/screen_shot_2018-03-21at160957.png)

* When [페이지 편집](#editing-your-page-content):

   1. 를 엽니다. **페이지 정보** 메뉴 아래의 제품에서 사용할 수 있습니다.
   1. 선택 **페이지 게시**.

   ![screen_shot_2018-03-21at161026](assets/screen_shot_2018-03-21at161026.png)

* **게시 관리** 옵션을 통해서만 콘솔에서 페이지의 게시를 취소할 수 있으며, 이 옵션은 빠른 작업이 아닌 도구 모음에서만 사용할 수 있습니다.

   다음 **페이지 게시 취소** 옵션을 통해 계속 사용할 수 있습니다. **페이지 정보** 메뉴의 편집기.

   ![screen_shot_2018-03-21at161059](assets/screen_shot_2018-03-21at161059.png)

   자세한 내용은 [페이지 게시](/help/sites-authoring/publishing-pages.md#unpublishing-pages) 추가 정보.

## 페이지 이동, 복사 및 붙여넣기 또는 삭제 {#move-copy-and-paste-or-delete-your-page}

1. [페이지로 이동합니다](#finding-your-page) 이동, 복사 및 붙여넣기, 삭제하려는 경우
1. 복사(및 붙여넣기)를 선택하고 필요한 경우 다음 중 하나를 사용하여 아이콘을 이동하거나 삭제합니다.

   * 필요한 리소스에 대한 [빠른 작업(카드 보기/데스크탑 전용)](#quick-actions-card-view-desktop-only)
   * [페이지를 선택했을 때](#selecting-your-page-for-further-action)의 도구 모음

   * 복사:

      * 새 위치로 이동한 후 붙여넣어야 합니다.
   * 이동:

      * 마법사가 열리고 페이지 이동에 필요한 정보를 수집합니다. 화면의 지시를 따르십시오.
   * 삭제:

      * 작업을 확인하는 메시지가 나타납니다.
   >[!NOTE]
   >
   >삭제는 빠른 작업으로 사용할 수 없습니다.

## 페이지 잠금(및 잠금 해제) {#locking-your-page-then-unlocking}

[Locking a page](/help/sites-authoring/editing-content.md#locking-a-page) prevents other authors from working on it while you are. The Lock (and Unlock) icon/button can be found:

* [페이지를 선택했을 때](#selecting-your-page-for-further-action)의 도구 모음
* 페이지를 편집할 때 [[페이지 정보] 드롭다운 메뉴](#editing-the-page-properties)
* 페이지를 편집할 때 페이지 도구 모음(페이지가 잠겨 있을 때)

예를 들어 잠금 아이콘은 다음과 같습니다.

![screen_shot_2018-03-21at161124](assets/screen_shot_2018-03-21at161124.png)

## 페이지 참조에 액세스 {#accessing-page-references}

페이지에 대한 참조 및 페이지에서의 [참조에 대한 빠른 액세스](/help/sites-authoring/author-environment-tools.md#references)는 참조 레일에서 사용할 수 있습니다.

1. **페이지를 선택**&#x200B;하기 전이나 후에 도구 모음 아이콘을 사용하여 [참조](#selecting-your-page-for-further-action)를 선택합니다.

   ![screen_shot_2018-03-21at161210](assets/screen_shot_2018-03-21at161210.png)

   참조 유형 목록이 표시됩니다.

   ![screen_shot_2018-03-21at161315](assets/screen_shot_2018-03-21at161315.png)

1. 필요한 참조 유형을 탭하거나 클릭하여 자세한 내용을 표시하고(해당되는 경우) 추가 작업을 수행합니다.

## 페이지 버전 만들기 {#creating-a-version-of-your-page}

1. 타임라인 레인을 열려면 **[페이지를 선택](/help/sites-authoring/basic-handling.md#timeline)**&#x200B;하기 전이나 후에 도구 모음 아이콘을 사용하여 [타임라인](#selecting-your-page-for-further-action)을 선택합니다.

   ![screen_shot_2018-03-21at161355](assets/screen_shot_2018-03-21at161355.png)

1. 타임라인 열 오른쪽 하단에 있는 위쪽 화살표를 탭하거나 클릭하여 다음을 포함한 추가 단추를 표시합니다 **다른 버전으로 저장**.

   ![screen_shot_2018-03-21at161507](assets/screen_shot_2018-03-21at161507.png)

1. **다른 버전으로 저장**&#x200B;을 선택한 후 **만들기**&#x200B;를 선택합니다.

## 페이지 버전 복원/비교 {#restoring-comparing-a-version-of-your-page}

페이지 버전을 복원 및/또는 비교할 때 동일한 기본 메커니즘이 사용됩니다.

1. **[페이지를 선택](/help/sites-authoring/basic-handling.md#timeline)**&#x200B;하기 전이나 후에 도구 모음 아이콘을 사용하여 [타임라인](#selecting-your-page-for-further-action)을 선택합니다.

   ![screen_shot_2018-03-21at161355-1](assets/screen_shot_2018-03-21at161355-1.png)

   페이지 버전이 이미 저장된 경우 타임라인에 나열됩니다.

1. 복원할 버전을 탭하거나 클릭합니다. 그러면 다음과 같은 추가 작업 버튼이 표시됩니다.

   * **이 버전으로 되돌리기**

      * 버전이 복원됩니다.
   * **차이 표시**

      * 두 버전 간의 차이가 강조 표시된 채로 페이지가 열립니다.
