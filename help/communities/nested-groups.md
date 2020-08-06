---
title: 중첩된 그룹 작성
seo-title: 중첩된 그룹 작성
description: 중첩된 그룹 만들기
seo-description: 중첩된 그룹 만들기
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 4%

---


# 중첩된 그룹 작성 {#authoring-nested-groups}

## 작성자에 대한 그룹 만들기 {#creating-groups-on-author}

작성자, 전역 탐색에서

* 커뮤니티 **[!UICONTROL > 사이트 선택]**
* 폴더 **[!UICONTROL 참여]** 선택
* 시작 자습서 **[!UICONTROL 영어 사이트에 사용할 카드를]** 선택합니다.
   * 카드 이미지 선택
   * 아이콘을 *선택하지* 않음

그 결과 [그룹 콘솔에 도달합니다](groups.md).

![chlimage_1-53](assets/chlimage_1-53.png)

그룹 함수는 그룹 인스턴스가 만들어지는 폴더로 표시됩니다. [그룹] 폴더를 선택하여 엽니다. 게시에서 만든 그룹이 표시됩니다.

![chlimage_1-54](assets/chlimage_1-54.png)

## 메인 아트 그룹 만들기 {#create-main-arts-group}

참여를 위한 사이트 구조에 그룹 기능이 포함되어 있으므로 이 그룹을 만들 수 있습니다. 사이트 내에서 함수 구성이 `Reference Template` 기본적으로 활성화되는 그룹 템플릿을 선택할 수 있도록 합니다. 따라서 이 새 그룹에 대해 선택한 템플릿이 `Reference Group`됩니다.

이러한 콘솔은 커뮤니티 사이트 콘솔과 매우 유사합니다.

* 그룹 **[!UICONTROL 만들기 선택]**
* `1 Community Group Template`:
   * 커뮤니티 그룹 제목: 예술
   * 커뮤니티 그룹 설명: 다양한 아트 그룹의 상위 그룹입니다.
   * 커뮤니티 그룹 루트: *기본으로*
   * 추가 사용 가능한 커뮤니티 그룹 언어:풀다운 메뉴를 사용하여 사용 가능한 커뮤니티 그룹 언어를 선택합니다. 메뉴는 상위 커뮤니티 사이트를 만든 모든 언어를 표시합니다. 사용자는 이러한 언어 중에서 선택하여 이 단일 단계에서 여러 로케일에 그룹을 만들 수 있습니다. 동일한 그룹이 각 커뮤니티 사이트의 그룹 콘솔에서 지정된 여러 언어로 만들어집니다.
   * 커뮤니티 그룹 이름: 예술
   * 템플릿: 아래로 이동하여 선택 `Reference Group`
   * 선택 `Next`

      ![parentestedgroup](assets/parenttonestedgroup.png)

다음 설정을 사용하여 다른 패널을 계속 진행합니다.

* **2 디자인**
   * 디자인을 변경하거나 기본 상위 사이트의 디자인을 허용할 수 있습니다
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
* **3 설정**
   * **중재**
      * 비워 둡니다(상위 사이트에서 상속).
   * **멤버십**
      * use default `Optional Membership`
   * **썸네일**
      * `optional`
   * 선택 `Next`
* **[!UICONTROL 만들기]**&#x200B;를 선택합니다

### 아트 그룹 내 그룹 중첩 {#nesting-groups-within-arts-group}

이제 `groups` 폴더에는 두 개의 그룹이 있어야 합니다(페이지를 새로 고쳐야 할 수 있음).

![createcommunitygroup](assets/createcommunitygroup.png)

#### 그룹 게시 {#publish-group}

그룹 내에 중첩된 그룹을 만들기 전에 `arts``arts` 카드 위로 마우스를 가져간 다음 게시 아이콘을 선택하여 게시합니다.

![chlimage_1-55](assets/chlimage_1-55.png)

그룹이 게시되었다는 확인을 기다립니다.

![chlimage_1-56](assets/chlimage_1-56.png)

그룹에는 `arts` 폴더가 하나 `groups` 있지만 비어 있고 새 그룹을 만들 수 있는 폴더가 있어야 합니다. 아트 그룹 폴더로 이동하여 각각 다른 멤버십 설정으로 3개의 중첩된 그룹을 만듭니다.

1. 시각적
   * 제목: `Visual Arts`
   * 이름: `visual`
   * 템플릿: `Reference Group`
   * 멤버십: 공개 `Optional Membership`그룹 선택, 모든 구성원에게 열기
1. 청각
   * 제목: `Auditory Arts`
   * 이름: `auditory`
   * 템플릿: `Reference Group`
   * 멤버십: 구성원 `Required Membership`이 참여할 수 있는 열린 그룹 선택

1. 역사

   * 제목: `Art History`
   * 이름: `history`
   * 템플릿: `Reference Group`
   * 멤버십: `Restricted Membership`초대된 구성원만 볼 수 있는 비밀 그룹을 선택합니다. 초대 
[데모 사용자](tutorials.md#demo-users) `emily.andrews@mailinator.com`

페이지를 새로 고쳐 세 개의 중첩된 그룹(하위 커뮤니티)을 모두 봅니다.

필요한 경우 커뮤니티 사이트 콘솔에서 중첩된 그룹으로 이동하려면 다음을 수행하십시오.

* 참여 **[!UICONTROL 폴더 선택]**
* 시작하기 자습서 **[!UICONTROL 카드]** 선택
* 그룹 **[!UICONTROL 폴더 선택]**
* 아트 **[!UICONTROL 카드 선택]**
* 그룹 **[!UICONTROL 폴더 선택]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 게시 그룹 {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

기본 커뮤니티 사이트를 게시한 후에는

* 각 그룹을 개별적으로 게시
   * 그룹이 게시되었다는 확인을 기다리는 중
* 상위 그룹을 게시한 후
   * 모든 그룹은 하향식 방식으로 게시되어야 합니다.

![chlimage_1-59](assets/chlimage_1-59.png)

## 게시 경험 {#experience-on-publish}

로그인하면 다른 그룹을 경험할 수 있습니다. 예를 들어 [데모 사용자는](tutorials.md#demo-users)

* 아트/작업 내역 그룹 구성원: emily.andrews@mailinator.com/password
   * 제한적(비밀) 그룹, 예술/역사
   * 선택적(공개) 그룹을 볼 수 있습니다.
   * 제한된(열린) 그룹에 참여할 수 있음
* 그룹 관리자: aaron.mcdonald@mailinator.com/password
   * 선택적(공개) 그룹을 볼 수 있습니다.
   * 제한적(열린) 그룹에 참여할 수 있음
   * 반환(비밀) 그룹이 표시되지 않음

작성자의 커뮤니티 [구성원 및 그룹 콘솔에](members.md) 액세스하여 커뮤니티 그룹에 해당하는 다양한 구성원 그룹에 다른 사용자를 추가합니다.
