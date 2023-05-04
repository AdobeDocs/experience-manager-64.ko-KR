---
title: 집계된 사용 통계 수집 선택
seo-title: Opting Into Aggregated Usage Statistics Collection
description: 총 사용 통계를 확인하는 방법을 알아봅니다.
seo-description: Learn how to opt into aggregated usage statistics.
uuid: 835fd281-da4f-42ef-bae8-9ca91a29bc65
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 0c2b1c67-2fa4-4b2e-8512-0973177656e2
exl-id: f3cfa30a-ca15-48db-bacf-1aebbd0ad458
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 5%

---

# 집계된 사용 통계 수집 선택{#opting-into-aggregated-usage-statistics-collection}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

AEM과 상호 작용하는 방법에 대한 Adobe 통계를 보내어 Adobe Marketing Cloud을 개선하는 데 도움이 될 수 있습니다. 이 정보는 회사의 사이트 방문자에 대한 데이터를 포함하지 않으며 Adobe이 사용자 경험을 게재, 지원 및 개선하는 데 사용됩니다.

Touch UI 또는 웹 콘솔을 사용하여 사용 통계 수집을 옵트인할 수 있습니다.

>[!NOTE]
>
>다양한 데이터 보호 및 개인 정보 보호 규정이 있습니다. 예를 들어 GDPR 및 CCPA가 포함됩니다. AEM Sites은 고객이 데이터 보호 및 개인 정보 보호 규정 준수 의무를 준수할 수 있도록 지원할 준비가 되어 있습니다. 이 페이지에서는 고객에게 집계된 사용 통계 수집을 옵트인(또는 옵트아웃하는) 절차를 안내합니다.
>
>자세한 내용은 [Adobe 개인 정보 보호 센터](https://www.adobe.com/kr/privacy.html).

>[!NOTE]
>
>또한 를 사용하여 언제든지 옵트아웃할 수 있습니다 [웹 콘솔](/help/sites-deploying/opt-in-aggregated-usage-statistics.md#opt-in-by-using-the-web-console) 또는 AEM 옵트인 화면에서 옵트인 옵션을 선택하지 않습니다.

## Touch UI를 사용하여 옵트인 {#opt-in-by-using-the-touch-ui}

AEM을 처음 시작할 때 다음과 같이 Touch UI를 사용하여 옵트인할 수 있습니다.

1. AEM 탐색 화면에서 **받은 편지함** (종) 아이콘을 클릭합니다.

   ![usage_통계학적 탐색 화면](assets/usage_statisticsnavigationscreen.png)

1. 드롭다운 목록에서 &quot;**집계된 사용 통계 수집 활성화**&quot;.

   ![usage_staticsnavigationscreen2](assets/usage_statisticsnavigationscreen2.png)

1. 옵트인 화면에서 &quot; &quot;을 선택합니다.**집계된 사용 통계 수집 허용**&quot;.

   ![usage_staticopt-inscreen](assets/usage_statisticsopt-inscreen.png)

1. 클릭 &quot;**완료**&quot;.

## 웹 콘솔을 사용하여 옵트인 {#opt-in-by-using-the-web-console}

다음과 같이 웹 콘솔을 사용하여 옵트인(또는 옵트아웃)할 수 있습니다.

1. AEM 탐색 화면에서 를 클릭합니다. **도구** 그리고 **작업**.

   ![usage_staticsopsdashboard](assets/usage_statisticsopsdashboard.png)

1. 작업 창에서 **웹 콘솔**.

   ![usage_staticswebconsole](assets/usage_statisticswebconsole.png)

1. &quot; 검색&#x200B;**집계된 사용 통계 수집**&quot;.
1. 을(를) 클릭합니다. **편집** 아이콘.

   ![usage_staticsclectionedit](assets/usage_statisticscollectionedit.png)

1. **활성화** 확인란을 선택합니다. 또는 사용 통계 수집을 옵트아웃하려는 경우 확인란을 선택 취소할 수 있습니다.

   ![usage_staticsselect](assets/usage_statisticsselect.png)

1. **저장**&#x200B;을 클릭합니다.
