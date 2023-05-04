---
title: 자산 통찰력 구성
description: 에서 자산 통찰력을 구성하는 방법을 알아봅니다. [!DNL Experience Manager] 자산.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 12%

---

# 자산 통찰력 구성 {#configuring-asset-insights}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets는 주변의 사용 데이터를 가져옵니다 [!DNL Experience Manager] Adobe Analytics의 타사 웹 사이트에서 사용하는 자산. 자산 통찰력 이 데이터를 검색하고 인사이트를 생성할 수 있도록 하려면 먼저 Adobe Analytics과 통합하도록 기능을 구성합니다.

>[!NOTE]
>
>인사이트는 이미지에서만 지원되고 제공됩니다.

1. In AEM, click **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Click the **[!UICONTROL Insights Configuration]** card.
1. 마법사에서 데이터 센터를 선택하고 조직 이름, 사용자 이름 및 암호를 포함하는 자격 증명을 제공합니다.

   ![chlimage_1-211](assets/insights_config2.png)

1. Click/tap **[!UICONTROL Authenticate]**.
1. 후 [!DNL Experience Manager] 에서 자격 증명을 인증합니다. **[!UICONTROL 보고서 세트]** 목록에서 자산 통찰력 이 데이터를 가져올 Adobe Analytics 보고서 세트를 선택합니다. 클릭 **[!UICONTROL 추가]**.
1. 후 [!DNL Experience Manager] 보고서 세트를 설정하고, 클릭/탭합니다. **[!UICONTROL 완료]**.

## 페이지 추적기 {#page-tracker}

Analytics 계정을 구성하면 페이지 추적기 코드가 생성됩니다. Assets Insights가 추적하도록 하려면 다음을 수행하십시오 [!DNL Experience Manager] 타사 웹 사이트에서 사용되는 자산은 웹 사이트 코드에 페이지 추적기 코드를 포함합니다. 에서 Page Tracker 유틸리티 사용 [!DNL Experience Manager] 페이지 추적기 코드를 생성할 자산입니다. 타사 웹 페이지에 페이지 추적기 코드를 포함하는 방법에 대한 자세한 내용은 다음을 참조하십시오 [웹 페이지에서 페이지 추적기 및 포함 코드 사용](touch-ui-using-page-tracker.md).

1. AEM에서 **[!UICONTROL 도구 > 자산]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. From the **[!UICONTROL Navigation]** page, click the **[!UICONTROL Insights Page Tracker]** card.
1. 을(를) 클릭합니다. **[!UICONTROL 다운로드]** 아이콘 을 클릭하여 페이지 추적기 코드를 다운로드합니다.
