---
title: 마케팅 캠페인 관리자 작업
seo-title: Working with the Marketing Campaign Manager
description: MCM(마케팅 캠페인 관리자)은 다중 채널 캠페인을 관리하는 데 도움이 되는 콘솔입니다. 이 마케팅 자동화 소프트웨어를 사용하여 모든 브랜드, 캠페인 및 경험을 관련 세그먼트, 목록, 리드 및 보고서와 함께 관리할 수 있습니다.
seo-description: The Marketing Campaign Manager (MCM) is a console that helps you manage multi-channel campaigns. With this marketing automation software you can manage all your brands, campaigns and experiences together with the related segments, lists, leads, and reports.
uuid: 3df6c0b8-dc0a-4a02-a38c-8250fb829404
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 1445437e-7f22-49ad-9bde-f3c0ff7d5142
exl-id: 63bf891c-572a-40e0-945f-d20a0a029224
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 2%

---

# 마케팅 캠페인 관리자 작업{#working-with-the-marketing-campaign-manager}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서 MCM(마케팅 캠페인 관리자)은 다중 채널 캠페인을 관리하는 데 도움이 되는 콘솔입니다. 이 마케팅 자동화 소프트웨어를 사용하여 모든 브랜드, 캠페인 및 경험을 관련 세그먼트, 목록, 리드 및 보고서와 함께 관리할 수 있습니다.

AEM의 다양한 위치에서 MCM에 액세스할 수 있습니다. 예를 들어, 캠페인 아이콘 또는 URL을 사용하는 시작 화면이 표시됩니다.

`https://<hostname>:<port>/libs/mcm/content/admin.html`

예:

`http://localhost:4502/libs/mcm/content/admin.html`

![screen_shot_2012-02-21at114636am](assets/screen_shot_2012-02-21at114636am.png)

MCM에서 다음 항목에 액세스할 수 있습니다.

* **[대시보드](#dashboard)**
4개의 창으로 구성되어 있습니다.

   * [목록](#lists)

      이 창에는 이미 만든 목록과 해당 목록의 리드 수가 표시됩니다. 이 창에서 직접 새 목록을 만들거나 리드를 가져와서 새 목록을 만들 수 있습니다.

      특정 목록을 선택하면 [목록](#lists) 목록에 대한 세부 사항을 보여주는 섹션.

   * [세그먼트](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#anoverviewofsegmentation)

      이 창에는 정의한 세그먼트가 표시됩니다. 세그먼트를 사용하여 특정 트레이트를 공유하는 방문자 모음을 규명할 수 있습니다.

      특정 세그먼트를 선택하면 세그먼트 정의 페이지가 열립니다.

   * [보고서](/help/sites-administering/reporting.md)\
      AEM에서는 인스턴스의 상태를 분석하고 모니터링하는 다양한 보고서를 제공합니다. 이 MCM 창에는 보고서가 표시됩니다.

      보고서를 선택하면 보고서 페이지가 열립니다.

   * [캠페인](#campaigns)

      이 창에는 다음과 같은 캠페인 경험이 나열됩니다 [뉴스레터](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) 및 [티저](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers).

* **[리드](#leads)**

   여기에서 리드를 관리할 수 있습니다. 리드를 만들거나 가져오고, 개별 리드에 대한 특정 세부 정보를 편집하거나, 더 이상 필요하지 않은 경우 삭제할 수 있습니다. 리드를 목록이라는 다른 그룹에 배치할 수도 있습니다. **참고:** Adobe은 이 기능을 추가로 개선할 계획이 없습니다.

   권장 사항은 다음과 같습니다 [Adobe Campaign과 AEM 통합 활용](/help/sites-administering/campaign.md).

* **[목록](#lists)**

   여기에서 리드 목록을 관리할 수 있습니다.**참고:** Adobe은 이 기능을 추가로 개선할 계획이 없습니다.

   권장 사항은 다음과 같습니다 [Adobe Campaign과 AEM 통합 활용](/help/sites-administering/campaign.md).

* **[캠페인](#campaigns)**
여기에서 브랜드, 캠페인 및 경험을 관리할 수 있습니다.

## 대시보드 {#dashboard}

대시보드에는 리드 목록, 세그먼트, 보고서 및 캠페인에 대한 개요를 제공하는 네 개의 창이 표시됩니다. 기본 기능에 대한 액세스 권한도 여기에서 사용할 수 있습니다.

![mcm_dashboard](assets/mcm_dashboard.png)

## 리드 {#leads}

>[!NOTE]
>
>Adobe은 이 기능(리드 관리)을 추가로 개선할 계획이 없습니다.\
>활용 [Adobe Campaign과 AEM 통합](/help/sites-administering/campaign.md).

AEM MCM에서는 리드를 수동으로 입력하거나 쉼표로 구분된 목록을 가져와서 리드를 구성하고 추가할 수 있습니다. 예를 들어 메일링 목록이 있습니다. 리드를 생성하는 또 다른 방법은 뉴스레터 등록 또는 커뮤니티 등록입니다. 적절한 구성을 통해 이러한 등록으로부터 리드를 생성하는 워크플로우를 시작할 수 있습니다. 리드는 일반적으로 분류되어 목록에 배치되므로 이후에 전체 목록에 대해 작업을 수행할 수 있습니다. 예를 들어 특정 목록에 사용자 지정 이메일을 보낼 수 있습니다.

아래 **리드** 왼쪽 창에서 리드를 만들고 가져오고 편집하고 삭제한 다음 필요에 따라 리드를 활성화하거나 비활성화할 수 있습니다. 리드를 목록에 추가하거나 이미 목록에 속해 있는 목록을 확인할 수 있습니다.

>[!NOTE]
>
>자세한 내용은 [리드 작업](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithleads) 을 참조하십시오.

![screen_shot_2012-02-21at114748am-1](assets/screen_shot_2012-02-21at114748am-1.png)

## 목록 {#lists}

>[!NOTE]
>
>Adobe은 이 기능(목록 관리)을 추가로 개선할 계획이 없습니다.\
>활용 [Adobe Campaign과 AEM 통합](/help/sites-administering/campaign.md).

목록을 통해 리드를 그룹으로 구성할 수 있습니다. 목록을 사용하여 마케팅 캠페인을 특정 사용자 그룹으로 타깃팅할 수 있습니다. 예를 들어 타깃팅된 뉴스레터를 목록에 보낼 수 있습니다.

아래 **목록**&#x200B;를 채울 때는 목록을 만들고 가져오고 편집하고 병합하고 삭제하여 관리하고, 필요에 따라 활성화하거나 비활성화할 수 있습니다. 해당 목록 내의 리드를 보거나, 목록이 다른 목록의 구성원인지 확인하거나 설명을 볼 수도 있습니다.

>[!NOTE]
>
>자세한 내용은 [목록 작업](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists) 을 참조하십시오.

![screen_shot_2012-02-21at124828pm-1](assets/screen_shot_2012-02-21at124828pm-1.png)

### 캠페인 {#campaigns}

>[!NOTE]
>
>자세한 내용은 [티저 및 전략](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists), [캠페인 설정](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupyourcampaign) 및 [뉴스레터](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) 을 참조하십시오.

기존 캠페인에 액세스하려면 MCM에서 **캠페인**.

![screen_shot_2012-02-21at11106pm](assets/screen_shot_2012-02-21at11106pm.png)

* **왼쪽 창에서**:

   모든 브랜드 및 캠페인 목록이 있습니다.

   브랜드를 한 번 클릭하면 다음 작업이 모두 수행됩니다.

   * 목록을 확장하여 왼쪽 창에 모든 관련 캠페인을 표시합니다. 이 목록에는 각 캠페인에 대해 존재하는 경험의 수도 표시됩니다.
   * 오른쪽 창에서 브랜드 개요를 엽니다.

* **오른쪽 창**:

   각 브랜드에 대해 아이콘이 표시됩니다(내역 캠페인은 표시되지 않음).

   이러한 아이콘을 두 번 클릭하면 브랜드 개요가 열립니다.

#### 브랜드 개요 {#brand-overview}

![mcm_brandoverview](assets/mcm_brandoverview.png)

여기에서 다음을 수행할 수 있습니다.

* 이 브랜드에 대해 존재하는 캠페인 및 경험의 수(왼쪽 창에 표시)를 참조하십시오.
* 만들기 **새로 만들기...** 이 브랜드에 대한 캠페인.

* 보고 있는 시간 간격을 변경합니다. 선택 **주**, **월** 또는 **분기**&#x200B;을 눌러 특정 기간을 선택하거나 **오늘**.

* 오른쪽 창에서 다음 작업을 수행할 캠페인을 선택합니다.

   * 편집 **속성...**
   * **삭제** 캠페인.

* 캠페인 개요를 엽니다(오른쪽 창에서 캠페인을 두 번 클릭하거나 왼쪽 창에서 한 번 클릭).

#### 캠페인 개요 {#campaign-overview}

개별 캠페인의 경우 다음 두 가지 보기를 사용할 수 있습니다.

1. **캘린더 보기**

   아이콘을 사용합니다.

   ![](do-not-localize/mcm_iconcalendarview.png)

   모든 터치포인트(회색)와 해당 터치포인트에 연결된 경험(녹색)의 수평 시간대 목록이 표시됩니다.

   ![mcm_banner_calendarview](assets/mcm_banner_calendarview.png)

   여기에서 다음을 수행할 수 있습니다.

   * 화살표를 사용하여 보고 있는 시간 간격을 변경하거나 **오늘**.
   * 사용 **터치 포인트 추가...** 기존 경험에 대한 새 터치포인트를 추가하려면
   * 오른쪽 창에서 Teaser를 클릭하여 **시간** 및 **해제 시간**.

1. **목록 보기**

   아이콘을 사용합니다.

   ![](do-not-localize/mcm_icon_listview.png)

   선택한 캠페인에 대한 모든 경험(예: 티저 및 뉴스레터)이 나열됩니다.

   ![mcm_banner_listview](assets/mcm_banner_listview.png)

   여기에서 다음을 수행할 수 있습니다.

   * 만들기 **새로 만들기...** 경험; 예를 들어 Adobe Target에서 오퍼, 티저 및 뉴스레터를 제공합니다.
   * **편집** 특정 티저 페이지 또는 뉴스레터의 세부 사항(두 번 클릭을 사용할 수도 있음).
   * 을(를) 정의합니다 **속성...** 특정 Teaser 페이지 또는 Newsletter에 해당됩니다.
   * **시뮬레이션** 경험의 모양 및 느낌(티저 페이지 또는 뉴스레터).

      시뮬레이션한 페이지가 열리면 사이드킥을 열어 해당 페이지에 대한 편집 모드로 전환할 수 있습니다.

   * **분석...** 페이지에 대해 생성된 노출 횟수.
   * **삭제** 더 이상 필요하지 않은 항목입니다.
   * **검색** 텍스트(경험의 제목 필드가 검색됨)에 사용할 수 있습니다.
   * 사용 **고급** 검색에 필터를 적용하려면 검색합니다.

### 캠페인 경험 시뮬레이션 {#simulating-your-campaign-experiences}

MCM에서 **캠페인**. 목록 보기가 활성화되었는지 확인하고 필요한 캠페인 경험을 선택한 다음 를 클릭합니다 **시뮬레이션**. 터치포인트(티저 또는 뉴스레터 페이지)가 열리고 선택한 경험이 방문자에게 표시됩니다.

![mcm_simulateexperience](assets/mcm_simulateexperience.png)

여기에서 사이드킥을 열어(작은 아래쪽 화살표 클릭) 페이지를 업데이트하기 위한 편집 모드로 변경할 수도 있습니다.

### Campaign 경험 분석 {#analyzing-your-campaign-experiences}

MCM에서 **캠페인**. 목록 보기가 활성화되었는지 확인하고 필요한 캠페인 경험을 선택한 다음 를 선택합니다 **분석...**. 시간 경과에 따른 페이지 노출 차트가 표시됩니다.

![mcm_campaignanalyze](assets/mcm_campaignanalyze.png)
