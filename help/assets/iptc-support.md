---
title: IPTC 메타데이터 지원
description: Adobe Experience Manager(AEM) Assets가 Adobe Bridge 및 기타 Creative 앱을 통해 자산에 추가된 IPTC 메타데이터, 크리에이티브 등급 및 키워드를 지원하는 방법을 알아봅니다.
contentOwner: AG
feature: 메타데이터
role: Business Practitioner,Administrator,Leader
exl-id: 3e22e8e4-3675-4d6d-94f4-fc1a4d4801e8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# IPTC 메타데이터 {#support-for-iptc-metadata} 지원

Adobe Experience Manager(AEM) Assets가 Adobe Bridge 및 기타 Creative 앱을 통해 자산에 추가된 IPTC 메타데이터, 크리에이티브 등급 및 키워드를 지원하는 방법을 알아봅니다.

Adobe Experience Manager (AEM) Assets는 자산을 설명하는 데 일반적으로 사용되는 IPTC 메타데이터 표준을 지원합니다. 이러한 방식으로, AEM Assets은 사진사, 크리에이티브 에이전시, 도서관, 박물관 등을 포함한 다양한 파티들 사이에서 이미지 수락을 강화한다.

이제 자산에 대한 기본 메타데이터 스키마에는 IPTC 코어 및 IPTC 확장 메타데이터 스키마가 통합되어 사용자가 이미지에 표시된 사람, 위치 및 제품에 대한 정확하고 안정적인 데이터를 추가할 수 있는 포괄적인 메타데이터 속성을 정의합니다. 또한 이미지 만들기에 대한 날짜, 이름 및 식별자 및 권한 정보를 표현할 수 있는 유연한 방법을 지원합니다.

이제 자산에 대한 속성 페이지에는 편집 가능한 필드에 IPTC 코어 및 IPTC 확장 메타데이터를 표시하는 별도의 탭이 포함되어 있습니다.

1. Assets 사용자 인터페이스에서 이미지를 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]** 아이콘을 클릭하거나 탭합니다.
1. 속성 페이지에서 **[!UICONTROL IPTC]** 탭을 클릭/탭하여 자산에 대한 IPTC 메타데이터를 봅니다.
1. 필요에 따라 IPTC 메타데이터 속성을 편집합니다.

   ![iptc_tab](assets/iptc_tab.png)

1. **[!UICONTROL IPTC Extension]** 탭을 클릭/탭하여 자산에 대한 IPTC Extension 메타데이터를 봅니다.
1. 필요에 따라 ITPC 확장 메타데이터 속성을 편집합니다.
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 탭/클릭하여 변경 사항을 저장합니다.

## 광고 등급 지원 {#creative-rating-support}

속성 페이지에는 개별 사용자 등급 및 전체 등급이 표시되는 것 외에도 Adobe Bridge 및 기타 Creative 앱을 통해 자산에 지정된 등급이 표시됩니다

이러한 등급은 **[!UICONTROL 고급]** 탭 내의 **[!UICONTROL 크리에이티브 등급]** 섹션에서 사용할 수 있습니다.

이 등급은 읽기 전용 속성이며 1~5 범위의 범위입니다. 검색 패널에서 광고 등급을 기준으로 자산을 검색할 수 있습니다.

그러나 이 속성은 현재 사용자가 수행한 사용자 지정 변경 사항과 충돌을 방지하기 위해 색인화되지 않습니다.

## 키워드 지원 {#keyword-support}

속성 페이지의 **[!UICONTROL IPTC]** 탭에는 Adobe Bridge 및 기타 Creative 앱을 통해 자산에 추가된 키워드도 표시됩니다. 이러한 키워드를 편집하고 **[!UICONTROL IPTC]** 탭에서 키워드를 추가할 수도 있습니다.

![키워드](assets/keywords.png)
