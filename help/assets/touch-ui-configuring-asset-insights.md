---
title: 자산 통찰력 구성
description: ' [!DNL Experience Manager] 자산에서 자산 통찰력을 구성하는 방법을 알아봅니다.'
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 2%

---

# 자산 통찰력 구성 {#configuring-asset-insights}

Adobe Experience Manager Assets는 Adobe Analytics의 타사 웹 사이트에서 사용하는 [!DNL Experience Manager] 자산 관련 사용 데이터를 가져옵니다. 자산 통찰력 이 데이터를 검색하고 인사이트를 생성할 수 있도록 하려면 먼저 Adobe Analytics과 통합하도록 기능을 구성합니다.

>[!NOTE]
>
>인사이트는 이미지에서만 지원되고 제공됩니다.

1. AEM에서 **[!UICONTROL 도구 > Assets]**&#x200B;를 클릭합니다.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. **[!UICONTROL 인사이트 구성]** 카드를 클릭합니다.
1. 마법사에서 데이터 센터를 선택하고 조직 이름, 사용자 이름 및 암호를 포함하는 자격 증명을 제공합니다.

   ![chlimage_1-211](assets/insights_config2.png)

1. **[!UICONTROL 인증]**&#x200B;을 클릭/탭합니다.
1. [!DNL Experience Manager]이 자격 증명을 인증하면 **[!UICONTROL 보고서 세트]** 목록에서 자산 통찰력이 데이터를 가져오려는 Adobe Analytics 보고서 세트를 선택합니다. **[!UICONTROL 추가]**&#x200B;를 클릭합니다.
1. [!DNL Experience Manager] 보고서 세트를 설정한 후에는 **[!UICONTROL 완료]**&#x200B;를 클릭/탭합니다.

## 페이지 추적기 {#page-tracker}

Analytics 계정을 구성하면 페이지 추적기 코드가 생성됩니다. 자산 통찰력 이 타사 웹 사이트에서 사용되는 [!DNL Experience Manager] 자산을 추적하도록 하려면 웹 사이트 코드에 페이지 추적기 코드를 포함하십시오. [!DNL Experience Manager] Assets의 Page Tracker 유틸리티를 사용하여 페이지 추적기 코드를 생성합니다. 타사 웹 페이지에 페이지 추적기 코드를 포함하는 방법에 대한 자세한 내용은 [웹 페이지에 페이지 추적기 및 포함 코드 사용](touch-ui-using-page-tracker.md)을 참조하십시오.

1. AEM에서 **[!UICONTROL 도구 > Assets]**&#x200B;를 클릭합니다.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. **[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL 인사이트 페이지 추적기]** 카드를 클릭합니다.
1. **[!UICONTROL 다운로드]** 아이콘을 클릭하여 페이지 추적기 코드를 다운로드합니다.
