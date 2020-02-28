---
title: 경험 조각 사용
seo-title: 경험 조각 사용
description: 'AEM Screens에서 경험 조각 사용에 대해 알려면 이 페이지를 따르십시오. '
seo-description: 'AEM Screens에서 경험 조각 사용에 대해 알려면 이 페이지를 따르십시오. '
uuid: 77ca8b98-1a0f-4517-a493-04a03acdea36
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: a310dd2f-02bd-44bc-9ad8-bf7450648054
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 경험 조각 사용{#using-experience-fragments}

경험 조각을 사용하면 다음 주제를 다룹니다.

* **개요**
* **AEM Screens에서의 경험 조각 사용**
* **마스터 페이지에서 변경 내용 전파**

## 개요 {#overview}

***경험 조각***&#x200B;은 페이지 내에서 참조할 수 있는 컨텐츠 및 레이아웃을 포함한 하나 이상의 구성 요소 그룹입니다. 경험 조각은 단락 시스템 내에 어떤 것이든 포함할 수 있는 하나 이상의 구성 요소 등, 구성 요소를 포함할 수 있으며, 이러한 구성 요소는 완전한 경험에 참조되거나 세 번째 종단점에 의해 요청됩니다.


## AEM Screens에서의 경험 조각 사용 {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>
>다음 예에서는 **사이트** 페이지에서 AEM Screens 프로젝트로 경험 조각을 활용하는 **데모** 프로젝트로 We.Retail을 사용합니다.

예를 들어 다음 워크플로우는 사이트에서 We.Retail에서 경험 조각을 사용하는 방법을 보여줍니다. 웹 페이지를 선택하고 프로젝트 중 하나에서 AEM Screens 채널의 해당 컨텐츠를 활용할 수 있습니다.

### 전제 조건 {#pre-requisites}

**채널을 사용하여 데모 프로젝트 만들기**

***프로젝트 만들기***

1. Click Screens and select **Create** --> **Create Project **to create a new project.

1. **스크린 프로젝트 만들기 **마법사에서 **스크린*을 선택합니다.

1. 제목을 **DemoProject**&#x200B;로 입력합니다.
1. **만들기**&#x200B;를 클릭합니다.

DemoProject **가** AEM Screens에 추가됩니다.  ***채널 생성***

1. Navigate to the **DemoProject** you created and select the **Channels** folder.

1. Click **Create** from the action bar (see the figure below). 마법사가 열립니다.
1. Choose the **Sequence Channel** and click **Next**.

1. Enter the **Title** as **TestChannel** and click **Create**.

TestChannel **이** DemoProject에 **추가됩니다**.\
![screen_shot_2018-05-24at22228pm](assets/screen_shot_2018-05-24at22228pm.png)

>[!NOTE]
>
>프로젝트 만들기 및 채널 만들기에 대한 자세한 내용은 프로젝트 [만들기](creating-a-screens-project.md) 및 채널 [관리를](managing-channels.md) 참조하십시오.

### 경험 조각 생성 {#creating-an-experience-fragment}

아래 절차에 따라 We.Retail의 컨텐츠를 **DemoProject의** TestChannel **에** 활용하십시오 ****.

1. **We.Retail에서 사이트 페이지로 이동**

   1. 사이트로 이동하고 **We.Retail **->** 미국 **->** **영어 **를 선택하고 장비** 페이지를 선택하여스크린 채널에 대한 경험 조각으로 사용합니다.
   1. 작업 **표시줄에서** 편집을 클릭하여 스크린 채널에 대한 경험 조각으로 사용할 페이지를 엽니다.
   ![screen_shot_2018-06-06at105309am](assets/screen_shot_2018-06-06at105309am.png)

1. **컨텐츠 다시 사용**

   1. 채널에 포함할 조각을 선택합니다.
   1. 오른쪽의 마지막 아이콘을 클릭하여 경험 조각으로 **변환** 대화 상자를 엽니다.
   ![screen_shot_2018-06-06at115741am](assets/screen_shot_2018-06-06at115741am.png)

1. **경험 조각 만들기**

   1. 작업을 **새** 경험 **조각 만들기로 선택합니다**.
   1. 상위 **경로를**&#x200B;선택합니다.
   1. 템플릿을 **선택합니다**. 여기에서 **We.Retail** 템플릿을 선택합니다.
   1. Enter the **Fragment Title **as **ScreensFragment**.
   1. 확인 표시를 클릭하여 새 경험 조각 생성을 완료합니다.
   ![screen_shot_2018-06-06at115009am](assets/screen_shot_2018-06-06at115009am.png)

1. **경험 조각의 Live Copy 만들기**

   1. AEM 홈 페이지로 이동합니다.
   1. 경험 **조각을** 선택하고 **ScreensFragment를** 강조 표시한 다음 **아래 그림과**&#x200B;같이 Variation as live-Copy를클릭합니다.
   ![screen_shot_2018-06-06at100729pm](assets/screen_shot_2018-06-06at100729pm.png)

   c.Live Copy 생성** **마법사에서** * ScreensFragment를 선택하고 다음을 **클릭합니다**.

   d.제목 및 **이름을** **스크린으로** 입력합니다 ****.

   e.만들기를 **클릭하여** Live Copy를 만듭니다.

   ![screen_shot_2018-06-06at101031pm](assets/screen_shot_2018-06-06at101031pm.png)

1. **스크린 채널에서 경험 조각 사용**

   1. 스크린 조각을 사용할 스크린 채널로 **이동합니다** .
   1. TestChannel **을** 선택하고 **막대에서 편집을** 클릭합니다.
   1. 사이드 탭에서 구성 요소 아이콘을 클릭합니다.
   1. 포함된 페이지를 **채널에** 드래그하여 놓습니다.
   ![screen_shot_2018-06-03at100512pm](assets/screen_shot_2018-06-03at100512pm.png)

   e.포함된 페이지 **구성 요소를** 선택하고 왼쪽 상단(렌치) 아이콘을 선택하여 페이지 **대화 상자를** 엽니다.

   f.** **Path** ** *필드에서 3단계에서 생성한 조각의* ScreensLive Copy를 선택합니다.

   ![screen_shot_2018-06-06at101421pm](assets/screen_shot_2018-06-06at101421pm.png)

   h.** 지속 시간** 필드에 초를 입력합니다.

   i.확인 표시를 클릭하여 프로세스를 완료합니다.

   ![screen_shot_2018-06-08at120448pm](assets/screen_shot_2018-06-08at120448pm.png)

### 결과 유효성 확인 {#validating-the-result}

준비 단계를 완료한 후 TestChannel에서 경험 조각의 유효성을 다음과 같이 확인할 **수** 있습니다.

1. TestChannel으로 **이동합니다**.
1. 작업 **표시줄에서** 미리 보기를 선택합니다.

아래 그림과 같이, **채널의 사이트** 페이지(경험 조각의 Live Copy)에서 컨텐츠를 볼 수 있습니다.\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## 마스터 페이지에서 변경 내용 전파 {#propagating-changes-from-the-master-page}

***LiveCopy*** 는 롤아웃 구성에 정의된 대로 동기화 작업으로 유지 관리되는 소스의 사본을 참조합니다.

경험 조각 이후, 생성된 것은 사이트 **페이지의** Live Copy이므로, 마스터 페이지에서 특정 조각을 변경하면, 채널이나 경험 조각을 사용한 대상의 변경 사항을 볼 수 있습니다.

>[!NOTE]
>
>Live Copy에 대한 자세한 내용은 컨텐츠 [재사용을 참조하십시오.다중 사이트 관리자 및 Live Copy](/help/sites-administering/msm.md).

아래 절차에 따라 마스터 채널에서 대상 채널에 변경 사항을 전파하십시오.

1. 사이트(마스터) 페이지에서 **경험** 조각을 선택하고 연필 아이콘을 클릭하여 경험 조각에서 항목을 편집합니다.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. 경험 조각을 선택하고 렌치 아이콘을 클릭하여 이미지를 편집할 대화 상자를 엽니다.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. 제품 **그리드** 대화 상자가 열립니다.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 이미지를 편집할 수 있습니다. 예를 들어 이 조각에서 첫 번째 이미지가 대체되었습니다.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. 경험 조각을 선택하고 롤아웃 아이콘을 클릭하여 채널에서 사용되는 조각에 대한 변경 사항을 전파합니다.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. 롤아웃을 클릭하여 변경 사항을 확인합니다.

   변경 내용이 롤아웃되는 것을 확인할 수 있습니다.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 변경 사항 유효성 확인 {#validating-the-changes}

아래 절차에 따라 채널의 변경 사항을 확인합니다.

1. 스크린 -> **채널** -> **테스트** 채널로 **이동합니다**.

1. 작업 **표시줄에서** 미리 보기를 클릭하여 변경 내용을 확인합니다.

다음 이미지는 TestChannel의 변경 사항을 **보여줍니다**.\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)

