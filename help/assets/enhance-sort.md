---
title: AEM에서 자산 정렬이 개선되었습니다.
description: AEM Assets에서 클라이언트 측의 배치로 정렬하는 대신 서버 측 정렬을 배포하여 폴더 자산 또는 검색 쿼리를 한 번에 정렬하는 방법을 알아봅니다.
contentOwner: AG
feature: 검색
role: Business Practitioner
exl-id: aa24ca68-d94e-4bd4-a5cc-113906650a2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 5%

---

# AEM {#enhanced-sorting-of-assets-in-aem}에서 자산의 정렬이 개선되었습니다.

AEM Assets에서 클라이언트 측의 배치로 정렬하는 대신 서버 측 정렬을 배포하여 폴더 자산 또는 검색 쿼리를 한 번에 정렬하는 방법을 알아봅니다.

폴더 목록 보기 및 검색 결과 페이지에서 많은 수의 자산을 효율적으로 정렬하도록 Adobe Experience Manager(AEM) Assets의 검색 기능이 향상되었습니다. 타임라인 항목을 정렬할 수도 있습니다.

AEM Assets에서는 서버측 정렬을 배포하여 폴더 또는 클라이언트 측의 배치로 정렬하는 대신 한 번에 검색 쿼리 내에서 전체 자산(몇 번 큰 자산)을 정렬합니다. 이렇게 하면 사용자 인터페이스에 프리페치된 결과를 빠르게 표시할 수 있으므로 정렬 작업이 보다 응답적이고 신속하게 수행될 수 있습니다.

## 목록 보기에서 자산 정렬 {#sorting-assets-in-list-view}

AEM Assets을 사용하면 다음 필드를 기반으로 폴더 자산을 정렬할 수 있습니다.

* 로케일
* 상태
* 유형
* 크기
* 등급
* 수정한 날짜
* 게시된 날짜
* 사용량
* 클릭 수
* 노출 횟수
* 체크아웃함

1. 많은 자산이 들어 있는 폴더로 이동합니다.
1. 레이아웃 아이콘을 클릭/탭하고 목록 보기로 전환합니다.

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. 자산 목록의 열 헤더 옆에 있는 정렬 아이콘을 클릭/탭합니다.

   ![chlimage_1-395](assets/chlimage_1-395.png)

   자산 목록은 필드 값을 기반으로 정렬됩니다.

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>`Name` 또는 `Title`열의 값을 정렬하려면 `/libs/dam/gui/content/commons/availablecolumns`를 오버레이하고 `sortable` 값을 `True`로 변경하십시오.

## 검색 결과의 자산 정렬 {#sorting-assets-in-search-results}

다음 필드를 기준으로 검색 결과를 정렬할 수 있습니다.

* 제목
* 상태
* 유형
* 크기
* 수정한 날짜
* 게시된 날짜

1. OmniSearch 상자에서 원하는 기준에 따라 자산을 검색합니다.

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. 레이아웃 아이콘을 클릭/탭하고 목록 보기로 전환합니다. 검색 결과가 목록 보기에 이미 표시되면 이 단계를 건너뜁니다.
1. 자산 목록의 열 헤더 옆에 있는 정렬 아이콘을 클릭/탭합니다. 자산 목록은 필드 값을 기반으로 정렬됩니다.

   ![chlimage_1-398](assets/chlimage_1-398.png)

## 타임라인에서 자산 정렬 {#sorting-assets-in-timeline}

AEM Assets을 사용하면 주석, 버전, 워크플로우 및 활동과 같은 타임라인 항목을 시간순으로 정렬할 수 있습니다.

1. 자산 UI에서 타임라인을 표시할 자산을 선택합니다.
1. GlobalNav 아이콘을 클릭/탭하고 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다.

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. 타임라인의 목록에서 항목을 선택합니다. 예를 들어 **[!UICONTROL 주석]**&#x200B;을 선택하여 자산과 연결된 주석 목록을 표시합니다.

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. **[!UICONTROL Date]** 레이블 옆에 있는 **[!UICONTROL 정렬]** 아이콘을 클릭/탭합니다. 선택한 항목에 따라 주석이 자산에 추가되는 시간 기준/시간 기준 순서대로 나열됩니다.

   ![chlimage_1-401](assets/chlimage_1-401.png)
