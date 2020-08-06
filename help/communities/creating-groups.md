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

이 기능은 [그룹 기능이](functions.md#groups-function) [커뮤니티 사이트](sites-console.md) 구조에 있을 때 제공됩니다.

커뮤니티 그룹 템플릿 [](tools-groups.md) 은 커뮤니티 그룹이 동적으로 생성될 때 커뮤니티 그룹 페이지의 디자인을 제공합니다.

커뮤니티 사이트의 구조나 커뮤니티 사이트 템플릿에 기능이 추가되면 그룹 기능에 대해 하나 이상의 그룹 템플릿이 선택됩니다. 이 그룹 템플릿 목록은 커뮤니티 사이트 내에서 새 그룹을 동적으로 만드는 구성원 또는 작성자에게 표시됩니다.

## Creating a New Group {#creating-a-new-group}

새 커뮤니티 그룹을 만드는 기능은 그룹 기능을 포함하는 커뮤니티 사이트의 존재(예: 그룹에서 만든 그룹)에 의존합니다 ` [Reference Site Template](sites.md)`.

다음에 나오는 예는 AEM Communities `Reference Site Template` 시작하기 튜토리얼에 설명된 대로, 에서 만든 커뮤니티 사이트 [를 사용합니다](getting-started.md) .

[그룹] 메뉴 항목을 선택하면 게시 시 **[!UICONTROL 로드되는]** 페이지입니다.

![chlimage_1-236](assets/chlimage_1-236.png)

새 그룹 **[!UICONTROL 아이콘]** 을 선택하면 편집 대화 상자가 열립니다.

설정 **[!UICONTROL 탭]** 아래에서 그룹의 기본 기능을 제공합니다.

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 그룹 이름]**&#x200B;커뮤니티 사이트에 표시할 그룹의 제목입니다.

* **[!UICONTROL 설명]**&#x200B;커뮤니티 사이트에 표시할 그룹의 설명입니다.

* **[!UICONTROL 초대]**&#x200B;그룹에 가입하도록 초대할 구성원 목록입니다. 사전 입력 검색은 커뮤니티 구성원이 초대할 수 있는 제안을 제공합니다.

* **[!UICONTROL 그룹 URL 이름]** URL의 일부가 되는 그룹 페이지의 이름입니다.

* **[!UICONTROL 그룹 선택]**&#x200B;열기 
`Open Group` 익명의 사이트 방문자가 컨텐츠를 볼 수 있으며 선택 취소됨을 나타냅니다 `Member Only Group`.

* **[!UICONTROL 구성원 전용 그룹]**&#x200B;선택 
`Member Only Group` 은 그룹의 구성원만 콘텐트를 볼 수 있으며 선택 취소됨을 나타냅니다 `Open Group`.

[ **[!UICONTROL 템플릿]** ] 탭 아래에는 그룹 함수가 커뮤니티 사이트의 구조나 커뮤니티 사이트 템플릿에 포함될 때 지정된 커뮤니티 그룹 템플릿 목록에서 선택할 수 있는 기능이 있습니다.

![chlimage_1-238](assets/chlimage_1-238.png)

[ **[!UICONTROL 이미지]** ] 탭 아래에서는 커뮤니티 사이트의 [그룹] 페이지에서 그룹에 대해 표시할 이미지를 업로드할 수 있습니다. 기본 스타일 시트는 이미지의 크기를 170 x 90픽셀로 지정합니다.

![chlimage_1-239](assets/chlimage_1-239.png)

그룹 **[!UICONTROL 만들기]** 단추를 선택하면 그룹의 페이지가 선택한 템플릿을 기반으로 만들어지고 사용자 그룹이 멤버십에 대해 만들어지고 그룹 페이지가 업데이트되어 새 하위 커뮤니티가 표시됩니다.

예를 들어 이미지 축소판이 업로드된 새 하위 커뮤니티인 &quot;포커스 그룹&quot;이 있는 그룹 페이지는 다음과 같이 표시됩니다(커뮤니티 그룹 관리자로 로그인됨).

![chlimage_1-240](assets/chlimage_1-240.png)

링크를 선택하면 선택한 템플릿을 기반으로 초기 모양이 나타나는 브라우저의 [포커스 그룹] 페이지가 열리고 기본 커뮤니티 사이트의 메뉴 아래에 하위 메뉴가 포함됩니다. `Focus Group`

![chlimage_1-241](assets/chlimage_1-241.png)

## Community Group Member List Component {#community-group-member-list-component}

구성 요소 `Community Group Member List` 는 그룹 템플릿의 개발자가 사용하도록 만들어졌습니다.

## 추가 정보 {#additional-information}

개발자를 위한 [커뮤니티 그룹 필수](essentials-groups.md) 사항 페이지에서 자세한 내용을 확인할 수 있습니다.

커뮤니티 그룹과 관련된 기타 정보는 사용자 및 사용자 그룹 [관리를 참조하십시오](users.md).
