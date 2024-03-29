---
title: 캠페인 설정
seo-title: Setting up your campaign
description: 새 캠페인을 설정하려면 캠페인을 개최할 브랜드를 만들고, 경험을 제공할 캠페인을 만들고, 마지막으로 새 캠페인에 대한 속성을 정의해야 합니다.
seo-description: Setting up a new campaign requires creating a brand to hold your campaigns, creating a campaign to hold experiences, and finally defining the properties for your new campaign.
uuid: 86fcd398-803e-4aa5-998c-7624afa7e839
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e30e5a21-ac86-4653-bd1f-7351852db3f3
exl-id: 41727155-2a67-44b6-b925-22001891a348
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2293'
ht-degree: 4%

---

# 캠페인 설정{#setting-up-your-campaign}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

새 캠페인을 설정하려면 다음과 같은(일반) 단계를 수행하십시오.

1. [브랜드 만들기](#creating-a-new-brand) 캠페인을 벌이기 위해
1. 필요한 경우 다음을 수행할 수 있습니다. [새 브랜드에 대한 속성 정의](#defining-the-properties-for-your-new-brand).
1. [캠페인 만들기](#creating-a-new-campaign) 경험을 보유하려면 예를 들어 티저 페이지 또는 뉴스레터가 있습니다.
1. 필요한 경우 다음을 수행할 수 있습니다. [새 캠페인에 대한 속성 정의](#defining-the-properties-for-your-new-campaign).

만들고 있는 경험의 유형에 따라 다음을 수행해야 합니다 [경험 만들기](#creating-a-new-experience). 경험의 세부 사항 및 경험 만들기 이후의 작업은 만들려는 경험 유형에 따라 달라집니다.

* Teaser를 만드는 경우:

   1. [티저 경험 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingateaserexperience).
   1. [티저에 컨텐츠를 추가합니다](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#addingcontenttoyourteaser).
   1. [티저에 대한 터치포인트 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatouchpointforyourteaser) 컨텐츠 페이지에 티저를 추가합니다.

* 뉴스레터를 만드는 경우:

   1. [뉴스레터 경험 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatinganewsletterexperience).
   1. [뉴스레터에 컨텐츠를 추가합니다.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#addingcontenttonewsletters)
   1. [뉴스레터를 개인화합니다.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#personalizingnewsletters)
   1. [매력적인 뉴스레터 랜딩 페이지 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupanewsletterlandingpage).
   1. [뉴스레터 전송](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#sendingnewsletters) 가입자 또는 리드에 대한 ID입니다.

* Adobe Target(이전 Test&amp;Target) 오퍼를 만드는 경우

   1. [Adobe Target 오퍼 경험 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatesttargetofferexperience).
   1. [Adobe Target과 통합](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#integratewithadobetesttarget)

>[!NOTE]
>
>자세한 내용은 [세그먼테이션](/help/sites-administering/campaign-segmentation.md) 세그먼트 정의에 대한 자세한 지침

## 새 브랜드 만들기 {#creating-a-new-brand}

새 브랜드를 만들려면:

1. 를 엽니다. **MCM** 을(를) 선택합니다. **캠페인** 왼쪽 창에 있습니다.

1. 선택 **새로 만들기...** 을 입력합니다. **제목** 및 **이름** 및 템플릿을 사용하여 새 브랜드에 사용할 수 있습니다.

   ![chlimage_1-37](assets/chlimage_1-37.png)

1. **만들기**&#x200B;를 클릭합니다. 새 브랜드가 MCM에 기본 아이콘으로 표시됩니다.

### 새 브랜드에 대한 속성 정의 {#defining-the-properties-for-your-new-brand}

1. From **캠페인** 왼쪽 창에서 오른쪽 창에서 새 브랜드 아이콘을 선택하고 **속성...**

   을(를) 입력할 수 있습니다 **제목**, **설명** 및 아이콘으로 사용할 이미지입니다.

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. 클릭 **확인** 저장

## 새 캠페인 만들기 {#creating-a-new-campaign}

새 캠페인을 만들려면:

1. From **캠페인**&#x200B;왼쪽 창에서 새 브랜드를 선택하거나 오른쪽 창에서 아이콘을 두 번 클릭합니다.

   개요가 표시됩니다(새 브랜드이면 비어 있음).

1. 클릭 **새로 만들기...** 그리고 **제목**, **이름** 및 템플릿을 사용하여 새 캠페인에 사용할 수 있습니다.

   ![chlimage_1-39](assets/chlimage_1-39.png)

1. **만들기**&#x200B;를 클릭합니다. 새 캠페인이 MCM에 표시됩니다.

### 새 캠페인에 대한 속성 정의 {#defining-the-properties-for-your-new-campaign}

동작을 제어하는 캠페인 속성을 구성합니다.

* **우선 순위:** 다른 캠페인에 상대적인 이 캠페인의 우선 순위입니다. 여러 캠페인이 동시에 켜지면 우선순위가 가장 높은 캠페인이 방문자 경험을 제어합니다.
* **설정 및 해제 시간:** 이러한 속성은 캠페인이 방문자 경험을 제어하는 기간을 제어합니다. 설정 시간 속성은 캠페인이 경험 제어를 시작하는 시간을 제어합니다. 해제 시간 속성은 캠페인이 경험 제어를 중지하는 시기를 제어합니다.
* **이미지:** AEM에서 캠페인을 나타내는 이미지입니다.
* **Cloud Services:** 캠페인이 통합된 Cloud Service 구성입니다. (자세한 내용은 [Adobe Marketing Cloud과 통합](/help/sites-administering/marketing-cloud.md))

* **Adobe Target:** Adobe Target과 통합된 캠페인을 구성하는 속성입니다. (자세한 내용은 [Adobe Target과 통합](/help/sites-administering/target.md))

1. From **캠페인**&#x200B;브랜드를 선택합니다. 오른쪽 창에서 캠페인을 선택하고 을(를) 클릭합니다 **속성**.

   다음을 포함한 다양한 속성을 입력할 수 있습니다 **제목**, **설명** 그리고 **Cloud Services** 원하시는군요

   ![chlimage_1-40](assets/chlimage_1-40.png)

1. 클릭 **확인** 저장

## 새 경험 만들기 {#creating-a-new-experience}

새 경험을 만드는 절차는 경험 유형에 따라 다릅니다.

* [티저 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingateaser)
* [뉴스레터 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatinganewsletter)
* [Adobe Target 오퍼 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatesttargetoffer)

>[!NOTE]
>
>이전 릴리스와 마찬가지로 에서도 경험을 페이지로 만들 수 있습니다 **웹 사이트** 콘솔(및 이전 릴리스에서 만든 이러한 페이지는 여전히 완전히 지원됩니다.)
>
>이제 경험을 만들기 위해 MCM을 사용하는 것이 좋습니다.

## 새 경험 구성 {#configuring-your-new-experience}

경험에 대한 기본 골격을 만들었으므로 이제 경험 유형에 따라 다음 작업을 계속 수행해야 합니다.

* [티저](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers):

   * [Teaser 페이지를 방문자 세그먼트에 연결합니다.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#applyingasegmenttoyourteaser)
   * [티저에 대한 터치포인트 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingatouchpointforyourteaser) 컨텐츠 페이지에 티저를 추가합니다.

* [뉴스레터](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters):

   * [뉴스레터에 컨텐츠를 추가합니다.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#addingcontenttonewsletters)
   * [뉴스레터를 개인화합니다.](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#personalizingnewsletters)
   * [뉴스레터 전송](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#sendingnewsletters) 가입자 또는 리드에 대한 ID입니다.
   * [매력적인 뉴스레터 랜딩 페이지 만들기](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupanewsletterlandingpage).

* [Adobe Target 오퍼](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#testtargetoffers):

   * [Adobe Target과 통합](/help/sites-administering/target.md)

### 새 터치 포인트 추가 {#adding-a-new-touchpoint}

기존 경험이 있는 경우 MCM의 달력 보기에서 직접 터치포인트를 추가할 수 있습니다.

1. 캠페인에 대한 달력 보기를 선택합니다.

1. 클릭 **터치 포인트 추가...** 대화 상자를 엽니다. 추가할 경험을 지정합니다.

   ![chlimage_1-41](assets/chlimage_1-41.png)

1. 클릭 **확인** 저장

## 리드 작업 {#working-with-leads}

>[!NOTE]
>
>Adobe은 이 기능(리드 관리)을 추가로 개선할 계획이 없습니다.\
>권장 사항은 다음과 같습니다 [Adobe Campaign과 AEM 통합 활용](/help/sites-administering/campaign.md).

AEM MCM에서는 리드를 수동으로 입력하거나 메일링 목록과 같이 쉼표로 구분된 목록을 가져와서 리드를 구성하고 추가할 수 있습니다. 리드를 생성하는 또 다른 방법은 뉴스레터 등록 또는 커뮤니티 등록입니다. 적절한 구성을 통해 이러한 등록으로부터 리드를 생성하는 워크플로우를 시작할 수 있습니다.

리드는 일반적으로 분류되어 목록에 배치되므로 이후에 목록 단위로 작업을 수행할 수 있습니다. 예를 들어 특정 목록에 사용자 지정 이메일을 보낼 수 있습니다.

대시보드에서 **리드** 왼쪽 창에서 실행하십시오. 또한 **목록** 창

![screen_shot_2012-02-21at114748am](assets/screen_shot_2012-02-21at114748am.png)

>[!NOTE]
>
>사용자 아바타를 추가하거나 수정하려면 Clickstream Cloud(Ctrl+Alt+c)를 열고 프로필을 로드한 다음 을 클릭합니다 **편집**.

### 새 리드 만들기 {#creating-new-leads}

새 리드를 만든 후에는 다음을 확인하십시오 [활성화](#activating-or-deactivating-leads) 이를 통해 게시 인스턴스에서 해당 활동을 추적하고 해당 경험을 개인화할 수 있습니다.

새 리드를 수동으로 만들려면:

1. AEM에서 MCM으로 이동합니다. 대시보드에서 **리드**.
1. 클릭 **새로 만들기**. 다음 **새로 만들기** 창이 열립니다.

   ![screen_shot_2012-02-21at115008am](assets/screen_shot_2012-02-21at115008am.png)

1. 필드에 정보를 적절히 입력합니다. 을(를) 클릭합니다. **주소** 탭.

   ![screen_shot_2012-02-21at115045am](assets/screen_shot_2012-02-21at115045am.png)

1. 주소 정보를 적절히 입력합니다. 클릭 **저장** 리드를 저장합니다. 리드를 더 추가하려면** 저장하고 새로 만들기** 클릭합니다.

   리드 창에 새 리드가 나타납니다. 항목을 클릭하면 입력된 모든 정보가 오른쪽 창에 나타납니다. 리드를 만든 후 목록에 추가할 수 있습니다.

   ![screen_shot_2012-02-21at120307pm](assets/screen_shot_2012-02-21at120307pm.png)

### 리드 활성화 또는 비활성화 {#activating-or-deactivating-leads}

리드를 활성화하면 게시 인스턴스에서 리드의 활동을 추적하고 리드의 환경을 개인화할 수 있습니다. 더 이상 해당 활동을 추적하지 않으려면 비활성화할 수 있습니다.

리드를 활성화하거나 비활성화하려면 다음을 수행하십시오.

1. AEM에서 MCM으로 이동하고 **리드**.

1. 활성화하거나 비활성화할 리드를 선택하고 를 클릭합니다 **활성화** 또는 **비활성화**.

   ![screen_shot_2012-02-21at120620pm](assets/screen_shot_2012-02-21at120620pm.png)

   AEM 페이지와 마찬가지로 게시 상태가 **게시됨** 열.

   ![screen_shot_2012-02-21at122901pm](assets/screen_shot_2012-02-21at122901pm.png)

### 새 리드 가져오기 {#importing-new-leads}

새 리드를 가져올 때 기존 목록에 자동으로 추가하거나 새 목록을 만들어 이러한 리드를 포함할 수 있습니다.

쉼표로 구분된 목록에서 리드를 가져오려면 다음을 수행하십시오.

1. AEM에서 MCM으로 이동하고 **리드**.

   >[!NOTE]
   >
   >또는 다음 중 하나를 수행하여 리드를 가져올 수 있습니다.
   >
   >* 대시보드에서 **리드 가져오기** 에서 **목록** 창
   >* 클릭 **목록** 그리고 **도구** 메뉴, 선택 **리드 가져오기**.


1. 에서 **도구** 메뉴, 선택 **리드 가져오기**.
1. 샘플 데이터에 설명된 대로 정보를 입력합니다. 다음 필드를 가져올 수 있습니다. email,familyName,givenName,gender,aboutMe,city,country,phoneNumber,postalCode,region,streetAddress

   >[!NOTE]
   >
   >CSV 목록의 첫 번째 행은 사전 정의된 레이블로 예제와 동일하게 작성해야 합니다.
   >
   >`email,givenName,familyName` -으로 작성된 경우 `givenname`예를 들어 시스템은 이를 인식하지 못합니다.

   ![screen_shot_2012-02-21at123055pm](assets/screen_shot_2012-02-21at123055pm.png)

1. **다음**&#x200B;을 클릭합니다. 여기에서 리드를 미리 보고 정확한지 확인합니다.

   ![screen_shot_2012-02-21at123104pm](assets/screen_shot_2012-02-21at123104pm.png)

1. **다음**&#x200B;을 클릭합니다. 리드가 속할 목록을 선택합니다. 목록에 속하지 않도록 하려면 필드에서 정보를 삭제합니다. 기본적으로 AEM은 날짜 및 시간을 포함하는 목록 이름을 만듭니다. 클릭 **가져오기**.

   ![screen_shot_2012-02-21at123123pm](assets/screen_shot_2012-02-21at123123pm.png)

   리드 창에 새 리드가 나타납니다. 항목을 클릭하면 입력된 모든 정보가 오른쪽 창에 나타납니다. 리드를 만든 후 목록에 추가할 수 있습니다.

### 목록에 리드 추가 {#adding-leads-to-lists}

기존 목록에 리드를 추가하려면

1. MCM에서 **리드** 사용 가능한 모든 리드를 표시합니다.

1. 목록에 추가할 리드를 선택합니다. 리드 옆의 확인란을 선택합니다. 리드를 원하는 만큼 추가할 수 있습니다.

   ![screen_shot_2012-02-21at123835pm](assets/screen_shot_2012-02-21at123835pm.png)

1. 에서 **도구** 메뉴, 선택 **목록에 추가....** **목록에 추가 **창이 열립니다.

   ![screen_shot_2012-02-21at124019pm](assets/screen_shot_2012-02-21at124019pm.png)

1. 리드를 추가할 목록을 선택하고 를 클릭합니다 **확인**. 리드가 해당 목록에 추가됩니다.

### 리드 정보 보기 {#viewing-lead-information}

리드 정보를 보려면 MCM에서 리드 옆의 확인란을 클릭하십시오. 그러면 오른쪽 창에 목록 소속을 포함하여 리드의 정보가 모두 표시됩니다.

![screen_shot_2012-02-21at124228pm](assets/screen_shot_2012-02-21at124228pm.png)

### 기존 리드 수정 {#modifying-existing-leads}

기존 리드 정보를 수정하려면

1. MCM에서 **리드**. 리드 목록에서 편집할 리드 옆의 확인란을 선택합니다. 오른쪽 창에 모든 리드 정보가 표시됩니다.

   ![screen_shot_2012-02-21at124514pm](assets/screen_shot_2012-02-21at124514pm.png)

   >[!NOTE]
   >
   >리드를 한 번에 하나씩만 편집할 수 있습니다. 동일한 목록에 속하는 리드를 수정해야 하는 경우, 대신 목록을 수정할 수 있습니다.

1. 클릭 **편집**. 다음 **리드 편집** 창이 열립니다.

   ![screen_shot_2012-02-21at124609pm](assets/screen_shot_2012-02-21at124609pm.png)

1. 필요에 따라 편집하고 **저장** 변경 사항을 저장하려면 을 클릭합니다.

   >[!NOTE]
   >
   >리드 아바타를 변경하려면 사용자 프로필로 이동합니다. Clickstream Cloud에서 프로필을 로드하려면 Ctrl+Alt+C를 누르고 **로드**&#x200B;을 선택한 후 프로필을 선택합니다.

### 기존 리드 삭제 {#deleting-existing-leads}

MCM에서 기존 리드를 삭제하려면 리드 옆의 확인란을 선택하고 **삭제**. 리드가 리드 목록과 모든 관련 목록에서 제거됩니다.

>[!NOTE]
>
>삭제가 실행되기 전에 기존 리드를 삭제할지 확인하는 메시지가 AEM에서 나타납니다. 삭제된 항목은 복원할 수 없습니다.

## 목록 작업 {#working-with-lists}

>[!NOTE]
>
>Adobe은 이 기능(목록 관리)을 추가로 개선할 계획이 없습니다.\
>권장 사항은 다음과 같습니다 [Adobe Campaign과 AEM 통합 활용](/help/sites-administering/campaign.md).

목록을 통해 리드를 그룹으로 구성할 수 있습니다. 목록을 사용하여 마케팅 캠페인을 특정 사용자 그룹으로 타깃팅할 수 있습니다. 예를 들어 특정 목록에 타깃팅된 뉴스레터를 보낼 수 있습니다. 목록은 MCM에서 대시보드에서 확인하거나 **목록**. 둘 다 목록의 이름과 구성원 수를 제공합니다.

![screen_shot_2012-02-21at125021pm](assets/screen_shot_2012-02-21at125021pm.png)

를 클릭하면 **목록**&#x200B;또한 목록이 다른 목록의 구성원인지 보고 설명을 볼 수도 있습니다.

![screen_shot_2012-02-21at124828pm](assets/screen_shot_2012-02-21at124828pm.png)

### 새 목록 만들기 {#creating-new-lists}

새 목록(그룹)을 만들려면

1. MCM 대시보드에서 **새 목록 ...** 또는 **목록**&#x200B;를 클릭합니다. **새로 만들기** ... 목록 생성 창이 열립니다.

   ![screen_shot_2012-02-21at125147pm](assets/screen_shot_2012-02-21at125147pm.png)

1. 이름(필수)을 입력하고 원하는 경우 설명을 입력하고 을 클릭합니다 **저장**. 목록이 **목록** 창

   ![screen_shot_2012-02-21at125320pm](assets/screen_shot_2012-02-21at125320pm.png)

### 기존 목록 수정 {#modifying-existing-lists}

기존 목록을 수정하려면 다음을 수행합니다.

1. MCM에서 **목록**.

1. 목록에서 편집할 목록 옆의 확인란을 선택하고 **편집**. 다음 **목록 편집** 창이 열립니다.

   ![screen_shot_2012-02-21at125452pm](assets/screen_shot_2012-02-21at125452pm.png)

   >[!NOTE]
   >
   >목록을 한 번에 하나씩만 편집할 수 있습니다.

1. 필요에 따라 편집하고 **저장** 변경 사항을 저장하려면 을 클릭합니다.

### 기존 목록 삭제 {#deleting-existing-lists}

기존 목록을 삭제하려면 MCM에서 목록 옆의 확인란을 선택하고 를 클릭합니다 **삭제**. 목록이 제거됩니다. 목록에 속한 리드는 제거되지 않으며 목록에 속한 리드만 삭제됩니다.

>[!NOTE]
>
>삭제하기 전에 AEM에서 기존 목록을 삭제할지 확인하는 메시지가 나타납니다. 삭제된 항목은 복원할 수 없습니다.

### 목록 병합 {#merging-lists}

기존 목록을 다른 목록과 병합할 수 있습니다. 이렇게 하면 병합하는 목록이 다른 목록의 멤버가 됩니다. 또한 별도의 엔티티로 존재하며 삭제할 수 없습니다.

서로 다른 두 위치에 동일한 회의가 있고 모든 회의의 참석자 목록에 병합하려는 경우 목록을 병합할 수 있습니다.

기존 목록을 병합하려면 다음을 수행합니다.

1. MCM에서 **목록**.

1. 다른 목록을 병합할 목록 옆의 확인란을 선택합니다.

1. 에서 **도구** 메뉴, 선택 **목록 병합**.

   >[!NOTE]
   >
   >목록을 한 번에 하나씩만 병합할 수 있습니다.

1. 에서 **목록 병합** 창에서 병합할 목록을 선택하고 를 클릭합니다 **확인**.

   ![screen_shot_2012-02-21at10259pm](assets/screen_shot_2012-02-21at10259pm.png)

   병합한 목록은 한 명의 멤버로 증가해야 합니다. 목록이 병합되었는지 확인하려면 병합한 목록과 **도구** 메뉴, 선택 **리드 표시**.

1. 원하는 목록을 모두 병합할 때까지 이 단계를 반복합니다.

   ![screen_shot_2012-02-21at10538pm](assets/screen_shot_2012-02-21at10538pm.png)

>[!NOTE]
>
>병합된 목록을 멤버십에서 제거하는 것은 목록에서 리드를 제거하는 것과 동일합니다. 를 엽니다. **목록** 탭에서 병합된 목록이 포함된 목록을 선택하고 목록 옆의 빨간색 원을 클릭하여 멤버 자격을 제거합니다.

### 목록의 리드 보기 {#viewing-leads-in-lists}

언제든지 구성원을 검색하거나 검색하여 특정 목록에 속하는 리드를 볼 수 있습니다.

목록에 속하는 리드를 보려면

1. MCM에서 **목록**.

1. 구성원을 확인할 목록 옆의 확인란을 선택합니다.

1. 에서 **도구** 메뉴, 선택 **리드 표시**. AEM에는 해당 목록에 속하는 리드가 표시됩니다. 목록을 살펴보거나 구성원을 검색할 수 있습니다.

   >[!NOTE]
   >
   >또한 리드를 선택한 다음 를 클릭하여 리드를 목록에서 삭제할 수 있습니다 **멤버십 제거**.

   ![screen_shot_2012-02-21at10828pm](assets/screen_shot_2012-02-21at10828pm.png)

1. 클릭 **닫기** mcm으로 돌아갑니다.
