---
title: 커뮤니티 그룹
seo-title: 커뮤니티 그룹
description: 커뮤니티 그룹 만들기
seo-description: 커뮤니티 그룹 만들기
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---


# 커뮤니티 그룹 {#community-groups}

커뮤니티 그룹 기능은 게시 및 작성 환경에서 승인된 사용자(커뮤니티 구성원 및 작성자)가 커뮤니티 사이트 내에서 하위 커뮤니티를 동적으로 만드는 기능입니다.

이 기능은 [groups 함수](functions.md#groups-function)가 [커뮤니티 사이트](sites-console.md) 구조에 있을 때 제공됩니다.

커뮤니티 그룹이 동적으로 생성될 때 [커뮤니티 그룹 템플릿](tools-groups.md)은 커뮤니티 그룹 페이지의 디자인을 제공합니다.

커뮤니티 사이트 구조나 커뮤니티 사이트 템플릿에 함수가 추가되면 그룹 기능에 대해 하나 이상의 그룹 템플릿이 선택됩니다. 이 그룹 템플릿 목록은 커뮤니티 사이트 내에서 새 그룹을 동적으로 만드는 구성원 또는 작성자에게 제공됩니다.

## 새 그룹 {#creating-a-new-group} 만들기

새 커뮤니티 그룹을 만드는 기능은 ` [Reference Site Template](sites.md)`에서 만든 그룹 기능과 같은 그룹 기능을 포함하는 커뮤니티 사이트의 기존 여부에 따라 달라집니다.

다음 예제에서는 [AEM Communities 시작](getting-started.md) 튜토리얼에 설명된 대로 `Reference Site Template`에서 만든 커뮤니티 사이트를 사용합니다.

**[!UICONTROL 그룹]** 메뉴 항목을 선택하면 게시 시 로드되는 페이지입니다.

![chlimage_1-236](assets/chlimage_1-236.png)

**[!UICONTROL 새 그룹]** 아이콘을 선택하면 편집 대화 상자가 열립니다.

**[!UICONTROL 설정]** 탭에서 그룹의 기본 기능을 제공합니다.

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 그룹]**
이름커뮤니티 사이트에 표시할 그룹의 제목입니다.

* **[!UICONTROL 설명]**
커뮤니티 사이트에 표시할 그룹의 설명입니다.

* **[!UICONTROL 초대]**
그룹에 가입하도록 초대할 구성원 목록입니다. 사전 검색 기능을 사용하면 커뮤니티 구성원이 초대할 수 있는 사항을 제안할 수 있습니다.

* **[!UICONTROL 그룹 URL]**
이름URL의 일부가 되는 그룹 페이지의 이름입니다.

* **[!UICONTROL 그룹]**
열기선택 
`Open Group` 는 익명의 사이트 방문자가 컨텐츠를 볼 수 있으며 선택 취소됨을 나타냅니다 `Member Only Group`.

* **[!UICONTROL 구성원 전용]**
그룹선택 
`Member Only Group` 은 그룹의 구성원만 콘텐트를 볼 수 있으며 선택 취소됨을 나타냅니다 `Open Group`.

**[!UICONTROL 템플릿]** 탭에서는 그룹 함수가 커뮤니티 사이트의 구조 또는 커뮤니티 사이트 템플릿에 포함될 때 지정된 커뮤니티 그룹 템플릿 목록에서 선택할 수 있습니다.

![chlimage_1-238](assets/chlimage_1-238.png)

**[!UICONTROL 이미지]** 탭 아래에서 커뮤니티 사이트의 그룹 페이지에 그룹에 대해 표시할 이미지를 업로드할 수 있습니다. 기본 스타일 시트는 이미지의 크기를 170 x 90픽셀로 조정합니다.

![chlimage_1-239](assets/chlimage_1-239.png)

**[!UICONTROL 그룹 만들기]** 단추를 선택하면 그룹의 페이지가 선택한 템플릿을 기반으로 만들어지고 사용자 그룹이 멤버십에 대해 생성되며 그룹 페이지가 업데이트되어 새 하위 커뮤니티를 표시합니다.

예를 들어 이미지 축소판이 업로드된 &quot;포커스 그룹&quot;이라는 새로운 하위 커뮤니티가 있는 그룹 페이지가 다음과 같이 표시됩니다(커뮤니티 그룹 관리자로 계속 로그인됨).

![chlimage_1-240](assets/chlimage_1-240.png)

`Focus Group` 링크를 선택하면 선택한 템플릿을 기반으로 초기 모양이 나타나는 브라우저의 [포커스 그룹] 페이지가 열리고 기본 커뮤니티 사이트 메뉴 아래에 하위 메뉴가 포함됩니다.

![chlimage_1-241](assets/chlimage_1-241.png)

## 커뮤니티 그룹 구성원 목록 구성 요소 {#community-group-member-list-component}

`Community Group Member List` 구성 요소는 그룹 템플릿 개발자가 사용하도록 만들어졌습니다.

## 추가 정보 {#additional-information}

개발자를 위한 [커뮤니티 그룹 필수 요소](essentials-groups.md) 페이지에 자세한 내용이 표시될 수 있습니다.

커뮤니티 그룹과 관련된 기타 정보는 [사용자 및 사용자 그룹 관리](users.md)를 참조하십시오.
