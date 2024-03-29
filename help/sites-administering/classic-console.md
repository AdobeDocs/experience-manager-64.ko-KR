---
title: 클래식 UI 태깅 콘솔
seo-title: Classic UI Tagging Console
description: 클래식 UI 태깅 콘솔에 대해 알아봅니다.
seo-description: Learn about the Classic UI Tagging Console.
uuid: c3080c82-0b34-4922-a263-1674a9522649
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: a7f31bc8-c583-439f-b2af-1dcc58f9c481
exl-id: 0c989965-c6cc-4ec7-a90f-6c52e8362485
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 1%

---

# 클래식 UI 태깅 콘솔{#classic-ui-tagging-console}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 섹션은 클래식 UI 태깅 콘솔을 위한 것입니다.

터치에 적합한 UI 태깅 콘솔은 다음과 같습니다 [여기](/help/sites-administering/tags.md#tagging-console).

클래식 UI 태깅 콘솔에 액세스하려면:

* 작성자
* 관리 권한으로 로그인
* 콘솔 찾아보기

   예 [http://localhost:4502/tagging](http://localhost:4502/tagging)

![managing_tags_usingthentagationconsole-1](assets/managing_tags_usingthetagasministrationconsole-1.png)

## 태그 및 네임스페이스 만들기 {#creating-tags-and-namespaces}

1. 시작하는 수준에 따라 를 사용하여 태그나 네임스페이스를 만들 수 있습니다 **새로 만들기**:

   선택하는 경우 **태그** 네임스페이스를 만들 수 있습니다.

   ![creating_tags_andnamespace-1](assets/creating_tags_andnamespaces-1.png)

   네임스페이스를 선택하는 경우(예: **데모**) 해당 네임스페이스 내에 태그를 만들 수 있습니다.

   ![creating_tags_andnamespacesinnewnamespace](assets/creating_tags_andnamespacesinnewnamespace.png)

1. 두 경우 모두 를 입력합니다.

   * **제목**
(
*필수 여부*) 태그의 표시 제목입니다. 문자를 입력할 수 있지만

      특수 문자 는 사용하지 않는 것이 좋습니다.

      * `colon (:)` - 네임스페이스 구분 기호
      * `forward slash (/)` - 하위 태그 구분 기호

      입력할 경우 이러한 문자가 표시되지 않습니다.

   * **이름**

      (*필수 여부*) 태그의 노드 이름입니다.

   * **설명**

      (*선택 사항입니다*) 태그에 대한 설명입니다.

   * 선택 **만들기**


## 태그 편집 {#editing-tags}

1. 오른쪽 창에서 편집할 태그를 선택합니다.
1. 클릭 **편집**.
1. 을 수정할 수 있습니다 **제목** 그리고 **설명**.
1. 클릭 **저장** 을 클릭하여 대화 상자를 닫습니다.

## 태그 삭제 {#deleting-tags}

1. 오른쪽 창에서 삭제할 태그를 선택합니다.
1. **삭제**&#x200B;를 클릭합니다.
1. 클릭 **예** 을 클릭하여 대화 상자를 닫습니다.

   더 이상 태그를 나열하지 않아야 합니다.

## 태그 활성화 및 비활성화 {#activating-and-deactivating-tags}

1. 오른쪽 창에서 활성화(게시) 또는 비활성화(게시 취소)할 네임스페이스 또는 태그를 선택합니다.
1. 클릭 **활성화** 또는 **비활성화** 필요한 경우.

## 목록 - 태그를 참조하는 위치 표시 {#list-showing-where-tags-are-referenced}

**목록** 강조 표시된 태그를 사용하여 모든 페이지의 경로를 보여 주는 새 창을 엽니다.

![list_showing_whretagresorecreferenced](assets/list_showing_wheretagsarereferenced.png)

## 태그 이동 {#moving-tags}

태그 관리자 및 개발자가 분류 체계를 정리하거나 태그 ID의 이름을 바꾸는 데 도움이 되도록 태그를 새 위치로 이동할 수 있습니다.

1. 를 엽니다. **태깅** 콘솔.
1. 태그를 선택하고 을(를) 클릭합니다 **이동...** 위쪽 도구 모음(또는 컨텍스트 메뉴)에 있는 Windows Media Optimizer 또는 SADV 메뉴의 )을 클릭합니다.
1. 에서 **태그 이동** 을(를) 정의합니다.

   * **to**: 대상 노드입니다.
   * **이름 바꾸기**: 새 노드 이름입니다.

1. 클릭 **이동**.

다음 **태그 이동** 대화 상자의 모양은 다음과 같습니다.

![move_tag](assets/move_tag.png)

>[!NOTE]
>
>작성자는 태그를 이동하거나 태그 ID의 이름을 변경하면 안 됩니다. 필요한 경우 작성자만 [태그 제목 변경](#editing-tags).

## 태그 병합 {#merging-tags}

분류 체계에 중복이 있는 경우 태그 병합을 사용할 수 있습니다. 태그 A를 태그 B로 병합하면 태그 A가 지정된 모든 페이지에 태그 B가 적용되고 작성자는 태그 A를 더 이상 사용할 수 없습니다.

태그를 다른 태그로 병합하려면

1. 를 엽니다. **태깅** 콘솔.
1. 태그를 선택하고 을(를) 클릭합니다 **병합...** 위쪽 도구 모음(또는 컨텍스트 메뉴)에 있는 Windows Media Optimizer 또는 SADV 메뉴의 )을 클릭합니다.
1. 에서 **태그 병합** 을(를) 정의합니다.

   * **변환**: 대상 노드입니다.

1. 클릭 **병합**.

다음 **태그 병합** 대화 상자의 모양은 다음과 같습니다.

![mergetag](assets/mergetag.png)

## 태그 사용 계산 {#counting-usage-of-tags}

태그가 몇 번이나 사용되는지 보려면:

1. 를 엽니다. **태깅** 콘솔.
1. 클릭 **사용 횟수** 상단 도구 모음에서: 카운트 열에 결과가 표시됩니다.

## 다른 언어로 태그 관리 {#managing-tags-in-different-languages}

선택 사항입니다 `title`태그의 속성은 여러 언어로 번역될 수 있습니다. 태그 `titles` 그런 다음 사용자 언어 또는 페이지 언어에 따라 표시될 수 있습니다.

### 여러 언어로 태그 제목 정의 {#defining-tag-titles-in-multiple-languages}

다음 절차에서는 `title`태그 **동물** 영어, 독일어 및 프랑스어로 변환:

1. 로 이동합니다. **태깅** 콘솔.
1. 태그 편집 **동물** 아래 **태그** > **스톡 사진**.
1. 다음 언어로 번역을 추가합니다.

   * **영어**: 동물
   * **독일어**: 티에르
   * **프랑스어**: Animaux

1. 변경 사항을 저장합니다.

대화 상자의 모양은 다음과 같습니다.

![edit_tag](assets/edit_tag.png)

Tagging 콘솔에서는 사용자 언어 설정을 사용하므로 Animal 태그의 경우 사용자 속성에서 언어를 프랑스어로 설정한 사용자에 대해 &#39;Animaux&#39;가 표시됩니다.

대화 상자에 새 언어를 추가하려면 섹션을 참조하십시오 [태그 편집 대화 상자에 새 언어 추가](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog) 에서 **개발자를 위한 태깅** 섹션을 참조하십시오.

### 페이지 속성에 지정된 언어로 태그 제목 표시 {#displaying-tag-titles-in-page-properties-in-a-specified-language}

기본적으로 태그입니다 `titles`페이지 속성에서 페이지 언어로 표시됩니다. 페이지 속성의 태그 대화 상자에는 태그를 표시할 수 있는 언어 필드가 있습니다 `titles`다른 언어로 표시합니다. 다음 절차에서는 태그를 표시하는 방법을 설명합니다 `titles`프랑스어:

1. 에 프랑스어 번역을 추가하려면 이전 섹션을 참조하십시오. **동물** 아래 **태그** > **스톡 사진**.
1. 페이지의 **제품** 페이지의 **Geometrixx** 사이트.
1. 를 엽니다. **태그/키워드** 대화 상자(태그/키워드 표시 영역 오른쪽에 있는 풀다운 메뉴 선택)를 선택하고 **프랑스어** 오른쪽 아래 모서리에 있는 풀다운 메뉴의 언어.
1. 을(를) 선택할 때까지 왼쪽 오른쪽 화살표를 사용하여 스크롤합니다. **스톡 사진** 탭

   을(를) 선택합니다 **동물** (**Animaux**) 태그를 사용하여 대화 상자 외부를 선택하여 태그를 닫고 페이지 속성에 추가합니다.

   ![프랑스어_tag](assets/french_tag.png)

기본적으로 페이지 속성 대화 상자에는 태그가 표시됩니다 `titles`페이지 언어에 따라 다릅니다.

일반적으로 페이지 언어가 사용 가능한 경우 페이지 언어로 태그의 언어를 가져옵니다. 이 [태그 위젯](/help/sites-developing/building.md#tagging-on-the-client-side) 가 다른 경우에 사용됩니다(양식 또는 대화 상자 등에서). 태그 언어는 컨텍스트에 따라 다릅니다.

>[!NOTE]
>
>표준 페이지 구성 요소의 태그 클라우드 및 메타 키워드는 현지화된 태그를 사용합니다 `titles`가능한 경우 페이지 언어를 기반으로 합니다.
