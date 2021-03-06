---
title: Assets의 사용자 경험 개선 사항
description: 이 문서에서는  [!DNL Experience Manager] 6.4 Assets의 사용자 경험 개선 사항에 대해 설명합니다.
contentOwner: AG
feature: Release Information
role: Leader,User
exl-id: 65029113-987e-46eb-86eb-8028233031f9
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 1%

---

# Assets의 사용자 경험 개선 사항 {#user-experience-enhancements-in-assets}

[!DNL Experience Manager] 6.4 Assets에는 원활한 사용자 경험을 제공하고 생산성을 향상시키는 몇 가지 유용성 개선 사항이 포함되어 있습니다. 시장 진출 컨텐츠를 생성/관리할 수 있는 속도 증가는 비즈니스 컨텐츠 속도를 향상시킵니다.

인터페이스는 더 반응형으로 작동하므로 대규모 자산 포트폴리오를 효율적으로 관리할 수 있습니다. 긴 항목 목록을 빠르게 검색, 표시, 정렬 및 원활하게 스크롤할 수 있습니다.

카드, 목록, 열 보기 등 다양한 보기를 개인화할 수 있습니다. 예를 들어 카드 보기에 표시할 축소판의 크기를 구성할 수 있습니다. 목록 보기의 경우, 목록에 있는 자산에 대해 표시할 세부 정보 수준을 구성할 수 있습니다. [!DNL Experience Manager] 6.4 자산에는 자산 저장소를 편리하게 탐색하고 자산을 찾을 수 있는 새로운 트리 보기가 포함되어 있습니다.

## 지연 로드 {#lazy-loading}

[!DNL Experience Manager] 6.4 Assets에서 자산을 탐색/검색하면 한 번에 최대 200개의 자산이 표시됩니다. 결과를 더 빨리 스크롤할 수 있으므로 긴 결과 목록을 탐색할 때 특히 유용합니다. 한 번에 많은 자산이 로드되므로 탐색 경험이 원활합니다.

자산을 탭/클릭하여 세부 사항 페이지를 검토하는 경우, 도구 모음에서 뒤로 단추를 탭/클릭하여 결과 페이지로 돌아갈 수 있습니다.

## 카드 보기 개선 사항 {#card-view-improvements}

사용하는 장치 및 필요한 세부 정보에 따라 카드 보기에서 자산 축소판의 크기를 조정할 수 있습니다. 이 방법으로 뷰를 개인화하고 표시되는 축소판 수를 제어할 수 있습니다.

카드 보기에서 축소판의 크기를 조정하려면 다음 단계를 수행합니다.

1. 도구 모음에서 레이아웃 아이콘을 탭/클릭한 다음 **[!UICONTROL 설정 보기]** 옵션을 선택합니다.

   ![view_settings](assets/view_settings.png)

1. **[!UICONTROL 설정 보기]** 대화 상자에서 원하는 축소판 크기를 선택한 다음 **[!UICONTROL 업데이트]**&#x200B;를 탭/클릭합니다.

   ![view_settings_dialog](assets/view_settings_dialog.png)

1. 선택한 크기로 표시되는 축소판을 검토합니다.

   ![축소판 그림_changed](assets/thumbnails_changed.png)

이제 카드 보기의 타일에 게시 상태와 같은 추가 정보가 표시됩니다.

![publish_status](assets/publish_status.png)

## 목록 보기 개선 사항 {#list-view-improvements}

목록 보기에서 첫 번째 열에 이제 기본적으로 자산의 파일 이름이 표시됩니다. 게시 및 처리 상태 및 로케일과 같은 추가 정보도 표시됩니다.

![list_view](assets/list_view.png)

표시할 세부 사항의 양을 구성하도록 선택할 수 있습니다. 레이아웃 아이콘을 탭/클릭하고 **[!UICONTROL 보기 설정]** 옵션을 선택한 다음 **[!UICONTROL 보기 설정]** 대화 상자에 표시할 열을 지정합니다.

![view_settings_dialoglistview](assets/view_settings_dialoglistview.png)

## 열 보기 개선 사항 {#column-view-improvements}

이제 카드 및 목록 보기 외에도 열 보기에서 자산의 세부 사항 페이지로 이동할 수 있습니다. 열 보기에서 자산을 선택한 다음 자산 스냅샷 아래에 있는 **[!UICONTROL 더 자세히]**&#x200B;를 탭/클릭합니다.

![more_details](assets/more_details.png)

## 트리 보기 {#tree-view}

[!DNL Experience Manager] 6.4 자산에는 자산 계층 구조를 편리하게 탐색하고 원하는 자산 또는 폴더로 이동할 수 있는 트리 보기가 포함되어 있습니다.

트리 보기를 열려면 `Assets UI`에서 GlobalNav 아이콘을 탭/클릭하고 메뉴에서 **[!UICONTROL 컨텐츠 트리]**&#x200B;를 선택합니다.

![content_tree](assets/content_tree.png)

컨텐츠 계층 구조에서 원하는 자산으로 이동합니다.

![navigate_contenttree](assets/navigate_contenttree.png)

## 자산 세부 사항 탐색 {#navigating-asset-details}

이제 자산 세부 사항 페이지에 도구 모음의 이전 및 다음 단추가 포함되므로 폴더의 모든 이미지를 연속적으로 볼 수 있습니다.

장치에 따라 키보드의 화살표 키를 밀거나 사용하여 이미지 간을 앞뒤로 이동할 수도 있습니다.

선택한 레이아웃에 따라 다음과 같은 방법으로 자산에 대한 세부 사항 페이지를 열 수 있습니다.

| **보기** | **자산 세부 사항 페이지를 여는 방법** |
|---|---|
| [!UICONTROL 카드 보기] | 자산 타일을 탭/클릭합니다. |
| [!UICONTROL 목록 보기] | 목록의 자산에 대한 행 항목을 탭/클릭합니다. |
| [!UICONTROL 열 보기] | 자산 스냅샷에서 **[!UICONTROL 더 자세히]** 단추를 탭/클릭합니다. |

이전/다음 단추를 사용하여 자산 간을 앞뒤로 이동합니다.

![prev_next_buttons](assets/prev_next_buttons.png)
