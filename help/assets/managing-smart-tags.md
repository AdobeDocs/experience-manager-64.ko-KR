---
title: 스마트 태그 관리
description: 부정확한 스마트 태그를 업데이트하거나 제거하여 태그의 관련성을 개선합니다
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 4%

---

# 스마트 태그 관리 {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

스마트 태그를 조정하여 브랜드 이미지에 할당되었을 수 있는 부정확한 태그를 제거하여 가장 관련성이 높은 태그만 표시할 수 있습니다.

또한 스마트 태그를 중재하면 가장 관련성이 높은 태그를 검색 결과에 표시하는 방식으로 태그 기반 검색을 통해 이미지를 검색할 수 있습니다. 기본적으로, 이것은 관련 없는 이미지가 검색 결과에 나타날 가능성을 제거하는데 도움이 된다.

태그에 높은 등급을 할당하여 이미지에 대한 관련성을 높일 수도 있습니다. 이미지에 대한 태그를 승격하면 특정 태그를 기반으로 검색을 수행할 때 검색 결과에 이미지가 표시될 가능성이 높아집니다.

1. OmniSearch 상자에서 태그를 기반으로 자산을 검색합니다.
1. Inspect 검색 결과를 통해 검색과 관련이 없는 이미지를 식별합니다.
1. 이미지를 선택한 다음, **[!UICONTROL 태그 관리]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
1. 에서 **[!UICONTROL 태그 관리]** 페이지에서 태그를 검사합니다. 특정 태그를 기반으로 이미지를 검색하지 않으려면 태그를 선택한 다음 **[!UICONTROL 삭제]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 또는 (**[!UICONTROL X]**) 레이블 옆에 표시되는 기호입니다.
1. 태그에 높은 등급을 지정하려면 태그를 선택하고 **[!UICONTROL 홍보]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 프로모션하는 태그는 **[!UICONTROL 태그]** 섹션을 참조하십시오.
1. Click/tap **[!UICONTROL Save]**, and then click/tap **[!UICONTROL OK]** to close the Success dialog.
1. 이미지의 속성 페이지로 이동합니다. 프로모션한 태그에 높은 관련성이 할당되므로 검색 결과에서 더 높게 표시됩니다.

## 이해 [!DNL Experience Manager] 스마트 태그가 있는 결과 검색 {#understand-search-results-with-smart-tags}

기본적으로 [!DNL Experience Manager] 검색은 검색어와 `AND` 절. 스마트 태그를 사용하면 이 기본 동작이 변경되지 않습니다. 스마트 태그를 사용하면 추가 기능이 추가됩니다 `OR` 적용 스마트 태그에서 검색어 중 하나를 찾기 위한 절. 예를 들어 `woman running`. 자산 전용 `woman` 또는 `running` 메타데이터의 키워드는 기본적으로 검색 결과에 표시되지 않습니다. 그러나 다음 중 하나가 태그된 자산 `woman` 또는 `running` 이러한 검색 쿼리에 스마트 태그 사용이 나타납니다. 따라서 검색 결과는

* 두 키워드가 모두 있는 자산 `woman` 및 `running` 참조하십시오.
* 키워드 중 하나로 태그가 지정된 자산

메타데이터 필드의 모든 검색어와 일치하는 검색 결과가 먼저 표시되고, 그 뒤에는 스마트 태그의 검색어와 일치하는 검색 결과가 표시됩니다. 위의 예에서 검색 결과의 대략적인 표시 순서는 다음과 같습니다.

1. 일치 `woman running` 를 입력합니다.
1. 일치 `woman running` 를 참조하십시오.
1. 일치 `woman` 또는 `running` 를 참조하십시오.
