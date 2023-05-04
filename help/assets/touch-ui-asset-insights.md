---
title: 자산 통찰력 기능을 사용하여 이미지 사용을 추적합니다
description: 자산 통찰력 기능을 사용하면 타사 웹 사이트, 마케팅 캠페인 및 Adobe의 크리에이티브 솔루션에서 사용되는 이미지의 사용자 등급 및 사용 통계를 추적할 수 있습니다.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 7%

---

# 자산 통찰력 {#asset-insights}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

자산 통찰력 기능을 사용하여 타사 웹 사이트, 마케팅 캠페인 및 Adobe의 크리에이티브 솔루션에서 사용되는 자산의 사용자 등급 및 사용 통계를 추적하는 방법을 알아봅니다.

자산 통찰력 기능을 사용하면 타사 웹 사이트, 마케팅 캠페인 및 Adobe의 크리에이티브 솔루션에서 사용되는 자산의 사용자 등급 및 사용 통계를 추적하여 해당 성능 및 인기도에 대한 통찰력을 얻을 수 있습니다.

자산 통찰력은 자산이 평가된 횟수, 클릭한 횟수 및 노출 횟수(웹 사이트에서 자산이 로드되는 횟수)와 같은 사용자 활동 세부 사항을 캡처합니다. 이 통계를 기반으로 자산에 점수를 할당합니다. 점수 및 성과 통계를 사용하여 카탈로그, 마케팅 캠페인 등에 포함할 인기 있는 자산을 선택할 수 있습니다. 이러한 통계를 기반으로 자산에 대한 아카이브 및 라이센스 갱신 정책을 작성할 수도 있습니다.

웹 사이트에서 자산에 대한 사용 통계를 캡처하려면 Assets Insights의 경우 웹 사이트 코드에 자산의 포함 코드를 포함해야 합니다.

자산 통찰력에 자산에 대한 사용 통계가 표시되도록 하려면 먼저 보고 데이터를 가져올 기능을 구성하십시오. [!DNL Adobe Analytics]. 자세한 내용은 [자산 통찰력 구성](touch-ui-configuring-asset-insights.md). 온-프레미스 설치에서 이 기능을 사용하려면 를 구입하십시오 [!DNL Adobe Analytics] 라이센스를 별도로 지정합니다. 고객이 [!DNL Managed Services] 수신 [!DNL Analytics] 번들로 제공되는 라이선스 [!DNL Experience Manager]. 자세한 내용은 [Managed Services 제품 설명](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>인사이트는 이미지에만 지원되고 제공됩니다.

## 자산에 대한 통계 보기 {#viewing-statistics-for-an-asset}

메타데이터 페이지에서 자산 통찰력 점수를 볼 수 있습니다.

1. Assets 사용자 인터페이스(UI)에서 자산을 선택한 다음, **[!UICONTROL 속성]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
1. 속성 페이지에서 **[!UICONTROL Insights]** 탭.
1. 에서 자산에 대한 사용 세부 사항을 검토합니다 **[!UICONTROL Insights]** 탭. 다음 **[!UICONTROL 점수]** 섹션에 자산의 총 자산 사용량 및 성능 저장소 가 설명되어 있습니다.

   사용 점수는 다양한 솔루션에서 자산이 사용되는 횟수를 설명합니다.

   다음 **[!UICONTROL 노출 횟수]** 점수는 웹 사이트에서 자산이 로드되는 횟수입니다. 아래에 표시되는 번호 **[!UICONTROL 클릭 수]** 은 자산을 클릭한 횟수입니다.

1. 를 검토합니다. **[!UICONTROL 사용 통계]** 섹션에 자산이 속한 엔티티와 최근에 사용한 크리에이티브 솔루션을 알아봅니다. 사용량이 많을수록 사용자 간에 자산이 인기 있을 가능성이 높습니다. 사용 데이터는 다음 헤드 아래에 표시됩니다.

   * **[!UICONTROL 자산]**: 자산이 컬렉션 또는 복합 자산의 일부인 횟수입니다
   * **[!UICONTROL 웹 및 모바일]**: 자산이 웹 사이트 및 앱의 일부인 횟수
   * **[!UICONTROL Social]**: Adobe Social 및 Adobe Campaign과 같은 솔루션에서 자산이 사용된 횟수입니다
   * **[!UICONTROL 이메일]**: 이메일 캠페인에 자산이 사용된 횟수입니다

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >자산 통찰력 기능은 솔루션 데이터를 [!DNL Adobe Analytics] 정기적으로 솔루션 섹션에는 최신 데이터가 표시되지 않을 수 있습니다. 데이터가 표시되는 기간은 Assets Insights가 검색하기 위해 실행하는 가져오기 작업의 예약에 따라 다릅니다 [!DNL Analytics] 데이터.

1. To view performance statistics for the asset graphically over a period of time, select period in the **[!UICONTROL Performance Statistics]** section. Details, including clicks and impressions are displayed as trend lines of a graph.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >솔루션 섹션의 데이터와 달리 성능 통계 섹션에는 가장 최근 데이터가 표시됩니다.

1. 성능 데이터를 가져오기 위해 웹 사이트에 포함하는 자산에 대한 포함 코드를 가져오려면 를 클릭합니다 **[!UICONTROL 포함 코드 가져오기]** 자산 축소판 아래에 표시됩니다. 타사 웹 페이지에 포함 코드를 포함하는 방법에 대한 자세한 내용은 다음을 참조하십시오 [웹 페이지에서 페이지 추적기 및 포함 코드 사용](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## 자산에 대한 통계 집계 보기 {#viewing-aggregate-statistics-for-assets}

You can view scores of all assets within a folder simultaneously using **[!UICONTROL Insights View]**.

1. 자산 UI에서 통찰력을 보려는 자산이 들어 있는 폴더로 이동합니다.
1. 도구 모음에서 레이아웃 아이콘을 탭/클릭한 다음 을 선택합니다 **[!UICONTROL 통찰력 보기]**.
1. 페이지에 자산에 대한 사용 점수가 표시됩니다. 다양한 자산의 등급을 비교하고 인사이트를 도출합니다.

## 백그라운드 작업 예약 {#scheduling-background-job}

Assets Insights는 Adobe Analytics 보고서 세트의 자산에 대한 사용 데이터를 정기적으로 가져옵니다. 기본적으로 자산 인사이트는 데이터 가져오기에 대해 오전 2시에 24시간마다 백그라운드 작업을 실행합니다. 그러나 빈도와 시간을 모두 수정하려면 **[!UICONTROL Adobe CQ DAM 자산 성과 보고서 동기화 작업]** 웹 콘솔에서 서비스를 제공합니다.

1. 탭하기 [!DNL Experience Manager] 로고로 이동하여 **[!UICONTROL 도구 > 작업 > 웹 콘솔]**.
1. 를 엽니다. **[!UICONTROL Adobe CQ DAM 자산 성과 보고서 동기화 작업]** 서비스 구성.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. 속성 스케줄러 식에서 원하는 스케줄러 빈도 및 작업의 시작 시간을 지정합니다. 변경 사항을 저장합니다.
