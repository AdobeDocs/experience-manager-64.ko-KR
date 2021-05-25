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
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---

# 커뮤니티 그룹 {#community-groups}

커뮤니티 그룹 기능은 게시 및 작성 환경에서 권한이 있는 사용자(커뮤니티 구성원 및 작성자)가 커뮤니티 사이트 내에서 하위 커뮤니티를 동적으로 만들 수 있는 기능입니다.

이 기능은 [그룹 함수](functions.md#groups-function)가 [커뮤니티 사이트](sites-console.md) 구조에 있을 때 제공됩니다.

[커뮤니티 그룹 템플릿](tools-groups.md)은 커뮤니티 그룹이 동적으로 생성되면 커뮤니티 그룹 페이지의 디자인을 제공합니다.

커뮤니티 사이트의 구조에 함수가 추가되거나 커뮤니티 사이트 템플릿에 추가될 때 그룹 기능에 대해 하나 이상의 그룹 템플릿이 선택됩니다. 이 그룹 템플릿 목록은 커뮤니티 사이트 내에서 새 그룹을 동적으로 만드는 구성원 또는 작성자에게 표시됩니다.

## 새 그룹 만들기 {#creating-a-new-group}

새 커뮤니티 그룹을 만드는 기능은 ` [Reference Site Template](sites.md)`에서 만든 그룹 기능과 같이 그룹 기능을 포함하는 커뮤니티 사이트의 존재 여부에 따라 다릅니다.

다음에 나오는 예제는 [AEM Communities 시작하기](getting-started.md) 자습서에 설명된 대로 `Reference Site Template`에서 만든 커뮤니티 사이트를 사용합니다.

**[!UICONTROL 그룹]** 메뉴 항목을 선택하면 게시 시 로드되는 페이지입니다.

![chlimage_1-236](assets/chlimage_1-236.png)

**[!UICONTROL 새 그룹]** 아이콘을 선택하면 편집 대화 상자가 열립니다.

**[!UICONTROL 설정]** 탭에서 그룹의 기본 기능을 제공합니다.

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 그룹]**
이름 커뮤니티 사이트에 표시할 그룹의 제목입니다.

* ****
설명 커뮤니티 사이트에 표시할 그룹의 설명입니다.

* ****
초대그룹에 가입하도록 초대할 구성원 목록입니다. 자동 완성 검색 기능을 사용하면 커뮤니티 구성원이 초대를 요청할 수 있습니다.

* **[!UICONTROL 그룹 URL]**
이름URL의 일부가 되는 그룹 페이지의 이름입니다.

* **[!UICONTROL GroupSelecting]**
열기 
`Open Group` 익명 사이트 방문자가 컨텐츠를 볼 수 있음을 나타내며 이 옵션을 선택 취소합니다  `Member Only Group`.

* **[!UICONTROL 구성원 전용]**
그룹선택 
`Member Only Group` 그룹의 구성원만 컨텐츠를 볼 수 있음을 나타내며 선택 취소됩니다  `Open Group`.

**[!UICONTROL 템플릿]** 탭에서는 그룹 함수가 커뮤니티 사이트의 구조에 포함되거나 커뮤니티 사이트 템플릿에 포함될 때 지정된 커뮤니티 그룹 템플릿 목록에서 선택하는 기능이 있습니다.

![chlimage_1-238](assets/chlimage_1-238.png)

**[!UICONTROL 이미지]** 탭에서는 커뮤니티 사이트의 그룹 페이지에 그룹에 대해 표시할 이미지를 업로드할 수 있습니다. 기본 스타일 시트는 이미지의 크기를 170 x 90픽셀로 지정합니다.

![chlimage_1-239](assets/chlimage_1-239.png)

**[!UICONTROL 그룹 만들기]** 단추를 선택하면 그룹의 페이지가 선택한 템플릿을 기준으로 작성되고 멤버십에 대한 사용자 그룹이 생성되고 그룹 페이지가 업데이트되어 새 하위 커뮤니티가 표시됩니다.

예를 들어, &quot;포커스 그룹&quot;이라는 새 하위 커뮤니티가 있는 그룹 페이지에서 이미지 축소판이 업로드되면 다음과 같이 표시됩니다(커뮤니티 그룹 관리자로 계속 로그인됨).

![chlimage_1-240](assets/chlimage_1-240.png)

`Focus Group` 링크를 선택하면 선택한 템플릿을 기반으로 초기 모양새가 있는 브라우저의 포커스 그룹 페이지가 열리고 기본 커뮤니티 사이트의 메뉴 아래에 하위 메뉴가 포함됩니다.

![chlimage_1-241](assets/chlimage_1-241.png)

## 커뮤니티 그룹 구성원 목록 구성 요소 {#community-group-member-list-component}

`Community Group Member List` 구성 요소는 그룹 템플릿 개발자가 사용하기 위한 것입니다.

## 추가 정보 {#additional-information}

개발자를 위한 [커뮤니티 그룹 필수 요소용](essentials-groups.md) 페이지에서 자세한 정보를 찾을 수 있습니다.

커뮤니티 그룹과 관련된 기타 정보는 [사용자 및 사용자 그룹 관리](users.md)를 방문하십시오.
