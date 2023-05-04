---
title: 중첩된 그룹 작성
seo-title: Authoring Nested Groups
description: 중첩 그룹 만들기
seo-description: Create nested groups
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 5%

---

# 중첩된 그룹 작성 {#authoring-nested-groups}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 작성자에 대한 그룹 만들기 {#creating-groups-on-author}

작성 시, 전역 탐색에서

* 선택 **[!UICONTROL 커뮤니티 > 사이트]**
* 선택 **[!UICONTROL 폴더 참여]** 열다
* 사용할 카드를 선택합니다 **[!UICONTROL 시작하기 자습서]**  영어 사이트
   * 카드 이미지를 선택합니다
   * 작업 *not* 아이콘 선택

결과는 [그룹 콘솔](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

그룹 함수는 그룹 인스턴스가 만들어진 폴더로 표시됩니다. 그룹 폴더를 선택하여 엽니다. 게시할 때 만든 그룹이 표시됩니다.

![chlimage_1-54](assets/chlimage_1-54.png)

## 주 아트 그룹 만들기 {#create-main-arts-group}

참여용 사이트 구조에 그룹 기능이 포함되어 있으므로 이 그룹을 만들 수 있습니다. 사이트의 `Reference Template` 기본값은 활성화된 그룹 템플릿을 선택할 수 있도록 하는 것입니다. 따라서 이 새 그룹에 대해 선택한 템플릿은 `Reference Group`.

이러한 콘솔은 커뮤니티 사이트 콘솔과 매우 유사합니다.

* 선택 **[!UICONTROL 그룹 만들기]**
* `1 Community Group Template`:
   * 커뮤니티 그룹 제목: 예술
   * 커뮤니티 그룹 설명: 다양한 예술 그룹에 대한 상위 그룹입니다.
   * 커뮤니티 그룹 루트: *기본값으로 둡니다.*
   * 추가 사용 가능한 커뮤니티 그룹 언어: 풀다운 메뉴를 사용하여 사용 가능한 커뮤니티 그룹 언어를 선택합니다. 이 메뉴에는 상위 커뮤니티 사이트가 생성된 모든 언어가 표시됩니다. 사용자는 이러한 언어 중에서 선택하여 이 단일 단계에서 여러 로케일에 그룹을 만들 수 있습니다. 동일한 그룹은 각 커뮤니티 사이트의 그룹 콘솔에서 지정된 여러 언어로 생성됩니다.
   * 커뮤니티 그룹 이름: 예술
   * 템플릿: 선택하려면 아래로 이동하십시오. `Reference Group`
   * 선택 `Next`

      ![parentestedgroup](assets/parenttonestedgroup.png)

다음 설정을 사용하여 다른 패널을 계속 진행합니다.

* **2 디자인**
   * 디자인을 변경하거나 기본적으로 상위 사이트의 디자인을 허용할 수 있습니다
   * **[!UICONTROL 다음]**&#x200B;을 선택합니다
* **3 설정**
   * **관리**
      * 비워 둡니다(상위 사이트에서 상속).
   * **멤버십**
      * 기본값 사용 `Optional Membership`
   * **썸네일**
      * `optional`
   * 선택 `Next`
* **[!UICONTROL 만들기]**&#x200B;를 선택합니다

### 아트 그룹 내에 그룹 중첩 {#nesting-groups-within-arts-group}

다음 `groups` 폴더에는 두 개의 그룹이 있어야 합니다(페이지를 새로 고쳐야 할 수 있음).

![createcommunitygroup](assets/createcommunitygroup.png)

#### 그룹 게시 {#publish-group}

내에서 중첩된 그룹을 만들기 전에 `arts`그룹을 마우스로 가리키면 `arts` 카드를 선택하고 게시 아이콘을 선택하여 게시합니다.

![chlimage_1-55](assets/chlimage_1-55.png)

그룹이 게시되었는지 확인할 때까지 기다립니다.

![chlimage_1-56](assets/chlimage_1-56.png)

다음 `arts` 그룹도 포함해야 합니다 `groups` 폴더가 비어 있고 새 그룹을 만들 수 있는 폴더가 비어 있습니다. 아트 그룹 폴더로 이동하고 각각 다른 멤버 자격 설정을 사용하여 3개의 중첩 그룹을 만듭니다.

1. 시각적
   * 제목: `Visual Arts`
   * 이름: `visual`
   * 템플릿: `Reference Group`
   * 멤버십: 선택 `Optional Membership`
모든 구성원에게 열려 있는 공개 그룹
1. 청각
   * 제목: `Auditory Arts`
   * 이름: `auditory`
   * 템플릿: `Reference Group`
   * 멤버십: 선택 `Required Membership`
구성원이 참여할 수 있는 열린 그룹

1. 역사

   * 제목: `Art History`
   * 이름: `history`
   * 템플릿: `Reference Group`
   * 멤버십: 선택 `Restricted Membership`
초대받은 구성원에게만 표시되는 비밀 그룹에 초대 
[데모 사용자](tutorials.md#demo-users) `emily.andrews@mailinator.com`

페이지를 새로 고쳐 세 개의 중첩 그룹(하위 커뮤니티)을 모두 확인합니다.

필요한 경우 커뮤니티 사이트 콘솔에서 중첩된 그룹으로 이동하려면 다음을 수행하십시오.

* 선택 **[!UICONTROL 폴더 참여]**
* 선택 **[!UICONTROL 시작하기 자습서]** 카드
* 선택 **[!UICONTROL 그룹 폴더]**
* 선택 **[!UICONTROL 예술 카드]**
* 선택 **[!UICONTROL 그룹 폴더]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 게시 그룹 {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

기본 커뮤니티 사이트를 게시한 후에는 다음을 수행해야 합니다

* 각 그룹 개별적으로 게시
   * 그룹이 게시되었는지 확인 대기 중
* 내에 중첩된 그룹을 게시하기 전에 상위 그룹 게시
   * 모든 그룹은 하향식으로 게시해야 합니다.

![chlimage_1-59](assets/chlimage_1-59.png)

## 게시할 때의 경험 {#experience-on-publish}

로그인할 때(예: [데모 사용자](tutorials.md#demo-users) 사용됨

* 미술/기록 그룹 구성원: emily.andrews@mailinator.com/password
   * 제한된(비밀) 집단, 예술/역사 등이 보일 것이다
   * 선택적(공용) 그룹을 볼 수 있습니다
   * 제한된(열린) 그룹에 가입 가능
* 그룹 관리자: aaron.mcdonald@mailinator.com/password
   * 선택적(공용) 그룹을 볼 수 있습니다
   * 제한된(열린) 그룹에 가입할 수 있음
   * 예약된(비밀) 그룹이 표시되지 않습니다.

커뮤니티 액세스 [구성원 및 그룹 콘솔](members.md) 작성자가 커뮤니티 그룹에 해당하는 다양한 구성원 그룹에 다른 사용자를 추가할 때.
