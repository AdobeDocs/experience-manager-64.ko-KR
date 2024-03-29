---
title: 페이지 성능 분석
seo-title: Analyzing Page Performance
description: 작성 중인 페이지의 성능을 컨텐츠 인사이트 페이지에서 분석할 수 있습니다
seo-description: Use the Content Insight page to analyze the performance of the page that you are authoring
uuid: 6b8a489d-f262-495d-adff-125c9a2c49b9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: ead74e39-3b07-488e-aeb1-fcb4aa6ff200
exl-id: dc24edaf-ca1d-4a6b-a2dc-86677267e18d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 3%

---

# 페이지 성능 분석{#analyzing-page-performance}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

를 엽니다. [컨텐츠 인사이트](/help/sites-authoring/content-insights.md) 페이지를 사용하여 작성 중인 페이지의 성능을 분석할 수 있습니다. 분석에 집중할 보고 기간을 구성합니다.

## 페이지에 대한 Analytics 및 Recommendations 열기 {#opening-analytics-and-recommendations-for-a-page}

페이지에 대한 Analytics 및 Recommendations을 보려면 다음 절차를 사용하십시오.

1. 분석할 페이지로 이동합니다.
1. 도구 모음에서 를 클릭하거나 탭합니다 **Analytics 및 Recommendations**.

   >[!NOTE]
   >
   >페이지에 대한 AEM 및 Recommendations은를 [Adobe Analytics과 통합](/help/sites-administering/adobeanalytics-connect.md).

   ![screen_shot_2017-11-29at135651](assets/screen_shot_2017-11-29at135651.png)

## 보고 기간 변경 {#changing-the-reporting-period}

분석 보고서의 다음 시간 관련 측면을 변경합니다.

* 보고할 기간입니다.
* 데이터의 세부기간입니다.

보고서의 시간 관련 측면을 변경하는 도구는 컨텐츠 인사이트 페이지 맨 위에 표시됩니다. ![chlimage_1-249](assets/chlimage_1-249.png)

### 보고 기간 변경 {#changing-the-reporting-period-1}

페이지 활동 분석에 집중할 수 있도록 컨텐츠 인사이트 페이지의 보고 기간을 특정 기간으로 변경합니다. 보고 기간을 변경하면 보고서가 자동으로 새로 고쳐집니다. 일정의 음영 영역은 보고 기간을 나타냅니다. 일정의 날짜는 왼쪽에서 오른쪽으로 증가합니다.

![chlimage_1-250](assets/chlimage_1-250.png)

컨텐츠 인사이트 페이지의 보고 기간을 변경하려면 다음을 수행하십시오.

1. 페이지 맨 위에 일정이 표시되지 않으면 일정 전환 아이콘을 클릭하거나 탭합니다.

   ![](do-not-localize/chlimage_1-22.png)

1. 보고 기간의 시작 날짜를 변경하려면 음영 영역의 왼쪽에 나타나는 원을 원하는 시작 날짜로 드래그합니다.

   음영 영역의 왼쪽을 볼 수 없으면 스크롤 막대를 사용하여 해당 영역을 표시합니다.

1. 보고 기간의 종료 날짜를 변경하려면 음영 영역의 오른쪽에 나타나는 원을 원하는 종료 날짜로 드래그합니다.

### 보고 기간의 세부기간 변경 {#changing-the-granularity-of-the-reporting-period}

보고서에서 각 데이터 포인트가 적용되는 시간을 변경합니다. 예를 들어 주 세부기간을 선택하면 보기 보고서의 각 데이터 포인트는 1주일 동안의 보기 수를 나타냅니다.

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

세부기간은 보기 및 페이지 평균 참여 시간(분) 보고서와 같이 시간을 기준으로 데이터를 표시하는 보고서에 영향을 줍니다. 세부기간은 일정의 스케일에도 영향을 줍니다.

1. 세부기간 컨트롤이 나타나지 않으면 세부기간 전환 아이콘을 클릭하거나 탭합니다.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. 원하는 세부기간을 클릭하거나 탭합니다. 선택되면 세부기간을 반영하도록 보고서가 자동으로 업데이트됩니다.

## SEO Recommendations용 작업 할당 {#assigning-tasks-for-seo-recommendations}

SEO Recommendations 보고서를 사용하여 검색 엔진에 대한 페이지 가시성을 향상시키기 위한 작업을 만들 수 있습니다. 확인 표시가 없는 보고서의 각 권장 사항에 대해 사용자에게 지정하여 필요한 작업을 수행할 작업을 생성할 수 있습니다.

![chlimage_1-252](assets/chlimage_1-252.png)

SEO 권장 사항의 상태는 작업이 생성되었지만 아직 완료되지 않은 시기를 나타냅니다.

![chlimage_1-253](assets/chlimage_1-253.png)

생성된 작업은 사용자의 작업 목록에 나타납니다. 작업에 대한 자세한 내용은 [작업](/help/sites-authoring/task-content.md).

다음 절차를 사용하여 SEO 추천에 대한 작업을 만듭니다.

1. SEO 추천에 대한 정보 아이콘을 클릭하거나 탭합니다.

   ![](do-not-localize/chlimage_1-23.png)

1. 정보 아이콘 옆에 나타나는 원으로 둘러싸인 삼각형 아이콘을 클릭합니다.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. 표시되는 양식 필드를 채우고 만들기 를 누릅니다.

   * 프로젝트: 작업을 만들 프로젝트를 선택합니다.
   * 이름: 작업을 식별하는 이름입니다. 기본 이름은 SEO 추천의 제목입니다.
   * 할당 대상: 작업을 할당할 사용자를 선택합니다. 목록을 필터링하려면 사용자 이름을 입력합니다.
   * 설명: 작업을 완료하는 데 필요한 활동에 대한 설명입니다. 기본 설명은 SEO 추천을 동반하는 정보입니다.
   * 작업 우선 순위: 작업의 우선 순위입니다.
   * 기한: 작업을 완료해야 하는 날짜입니다.

1. 완료 를 클릭하거나 탭하여 Task Created 메시지를 닫습니다.

>[!NOTE]
>
>생성된 작업에는 SEO 추천이 적용되는 페이지의 경로가 포함됩니다.
