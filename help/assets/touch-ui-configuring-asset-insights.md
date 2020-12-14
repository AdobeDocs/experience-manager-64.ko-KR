---
title: 자산 통찰력 구성
description: AEM Assets에서 자산 인사이트를 구성하는 방법을 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 2%

---


# 자산 인사이트 구성 {#configuring-asset-insights}

Adobe Experience Manager(AEM) 자산은 Adobe Analytics의 제3자 웹 사이트에서 사용하는 AEM 자산에 대한 사용 데이터를 가져옵니다. 자산 인사이트에서 이 데이터를 검색하고 인사이트를 생성하려면 먼저 Adobe Analytics과 통합할 기능을 구성합니다.

>[!NOTE]
>
>인사이트는 이미지만 지원되고 제공됩니다.

1. AEM에서 **[!UICONTROL 도구 > 자산]**&#x200B;을 클릭합니다.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. **[!UICONTROL 인사이트 구성]** 카드를 클릭합니다.
1. 마법사에서 데이터 센터를 선택하고 조직의 이름, 사용자 이름 및 암호를 포함한 자격 증명을 제공합니다.

   ![chlimage_1-211](assets/insights_config2.png)

1. **[!UICONTROL 인증]**&#x200B;을 클릭/탭합니다.
1. AEM에서 자격 증명을 인증한 후, **[!UICONTROL 보고서 세트]** 목록에서 자산 인사이트에서 데이터를 가져올 Adobe Analytics 보고서 세트를 선택합니다. **[!UICONTROL 추가]**&#x200B;를 클릭합니다.
1. AEM에서 보고서 세트를 설정한 후 **[!UICONTROL 완료]**&#x200B;를 클릭/탭합니다.

## 페이지 추적기 {#page-tracker}

Analytics 계정을 구성하면 페이지 추적기 코드가 자동으로 생성됩니다. 자산 통찰력을 사용하여 타사 웹 사이트에서 사용되는 AEM 자산을 추적하려면 웹 사이트 코드에 페이지 추적기 코드를 포함시킵니다. AEM Assets의 페이지 추적기 유틸리티를 사용하여 페이지 추적기 코드를 생성합니다. 타사 웹 페이지에 페이지 추적기 코드를 포함하는 방법에 대한 자세한 내용은 [페이지 추적기 및 웹 페이지에 포함 코드 사용](touch-ui-using-page-tracker.md)을 참조하십시오.

1. AEM에서 **[!UICONTROL 도구 > 자산]**&#x200B;을 클릭합니다.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. **[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL 인사이트 페이지 추적기]** 카드를 클릭합니다.
1. 페이지 추적기 코드를 다운로드하려면 **[!UICONTROL 다운로드]** 아이콘을 클릭합니다.