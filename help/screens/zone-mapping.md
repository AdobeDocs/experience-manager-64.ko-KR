---
title: 디스플레이 레이아웃 편집기
seo-title: 디스플레이 레이아웃 편집기
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 6c3b35bc-ea4f-46d4-bfed-2505ae21f764
contentOwner: jsyal
discoiquuid: 679da35f-2b6b-4910-92bd-5dbd4ae3742a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 디스플레이 레이아웃 편집기{#display-layout-editor}

***영역 매핑***&#x200B;을 사용하면 서로 다른 영역을 만들고, 문맥에 따라 단일 화면에서 결합할 수 있는 비디오, 이미지 및 텍스트와 같은 다양한 자산을 사용할 수 있습니다. 이미지, 비디오 및 텍스트를 가져와서 모두 함께 혼합하여 대화령의 직관적인 디지털 경험을 만들 수 있습니다. 프로젝트 요구 사항에 따라 디스플레이에 여러 영역이 필요할 수 있습니다.

예를 들어, 단일 디스플레이의 분리된 두 영역에서 관련된 소셜 미디어 피드가 실행 중인 제품 시퀀스가 있을 수 있습니다.

## 개요 {#overview}

채널용 디스플레이를 만드는 동안 채널에서 서로 다른 템플릿 선택 사항을 선택하여 컨텐츠를 보거나 관리할 수 있습니다.

디스플레이용 영역을 만드는 동안 다음 템플릿을 사용할 수 있습니다.

* 2x1
* 2x2
* 3x1
* 4x1
* 5x1

이러한 템플릿 중 하나를 사용하면 단일 화면에서 다양한 컨텐츠를 활용할 수 있는 대화형의 직관적인 디지털 그래픽을 만들 수 있습니다.

>[!NOTE]
>
>To learn in-depth about creating channels and displays, see [Managing Channels](managing-channels.md) and [Managing Displays](managing-displays.md) respectively in Authoring Screens.

## 사용 사례 설명 {#use-case-description}

이 사용 사례에서는 컨텐츠를 활용하는 채널이 있는 AEM Screens 프로젝트를 만들어 이 프로젝트를 화면에 여러 영역으로 표시할 수 있습니다.

>[!NOTE]
>
>영역은 컨텐츠 크기를 변경하지 않으며 그러한 작업은 컨텐츠를 채널에 삽입하기 전에 수행해야 합니다.

### 프로젝트 생성 절차 {#steps-for-creating-a-project}

아래 절차에 따라 AEM Screens 프로젝트용 영역 매핑을 성취하는 방법을 보여주는 AEM Screens 프로젝트를 만드십시오.

1. ***새 스크린 프로젝트 생성***

   1. Adobe Experience Manager 링크(왼쪽 위)를 선택한 다음 스크린을 선택합니다. Alternatively, you can ﻿go directly to: [http://localhost:4502/screens.html/content/screens](http://localhost:4502/screens.html/content/screens).
   1. Click **Create** to create a new Screens project.
   1. Select **Screens** from the **Create Screens Project** wizard and click **Next**.
   1. Enter the title as **Demo Mapping Project** and click **Create**.
   ![zm1](assets/zm1.gif)

1. ***새 채널 폴더 만들기***

   1. *** 영역 매핑 프로젝트**로 이동합니다.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. 마법사가 열립니다.
   1. Choose the **Channels Folder **and click **Next**.
   1. Enter the Title as **Dual Zone **and click **Create**.
   ![zm2](assets/zm2.gif)

1. ***새 채널 만들기***

   1. Navigate to the **Zone Mapping Project** you created and select the Channels folder (**Dual Zone**).
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. 마법사가 열립니다.
   1. Choose the **Sequence Channel **and click **Next**.
   1. Enter the **Title** as **Left** and click **Create**.
   유사하게, **영역 매핑 프로젝트**&#x200B;에서 **오른쪽**&#x200B;이라는 다른 시퀀스 채널을 만드십시오.

   ![zm3](assets/zm3.gif)

1. ***채널에 컨텐츠 추가***

   1. Navigate to the **Zone Mapping Project** you created and select the **Channel** you created.
   1. Click **Edit** from the action bar.
   1. The editor for the **Left** opens. 작업 표시줄의 왼쪽에 있는 사이드 패널을 전환하는 아이콘을 클릭하여 자산과 구성 요소를 엽니다.
   1. 채널에 추가할 구성 요소를 드래그하여 놓습니다.
   유사하게, **오른쪽** 채널에도 컨텐츠를 추가하십시오.

   ![zm4](assets/zm4.gif)

   >[!NOTE]
   >
   >프로젝트 요구 사항에 따라 채널의 컨텐츠를 다양한 자산(이미지, 비디오)으로 채울 수 있습니다.

1. ***새 위치 만들기***

   1. Navigate to the** Zone Mapping Project** and select the **Locations** folder.
   1. Click **Create** next to the plus icon in the action bar. 마법사가 열립니다.
   1. Select **Location** from the wizard and click **Next**.
   1. Enter the **Title** for your location (enter the title as **San Jose**) and click **Create**.
   ![zm5](assets/zm5.gif)

1. ***San Jose용 새 디스플레이 만들기***

   1. Navigate to the location where you want to create your display (**Demo Mapping Project** --> **Locations** --> **San Jose**) and select **San Jose**.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. Select **Display** from the **Create** wizard and click **Next**.
   1. Enter **Title** for your display location (enter the title as **Dual Zone**).
   1. Under the **Display** tab, choose the details of the Layout. Choose the Resolution as **Full HD**.
   1. Choose the **Number of Devices Horizontally** as **2**. Choose the **Number of Devices Vertically** as **1**.
   1. **만들기**&#x200B;를 클릭합니다.
   ![zm6](assets/zm6.gif)

1. ***채널 지정***

   1. Navigate to the display from **Zone Mapping Project** --> **Locations** --> **San Jose** --> **Dual Zone Display**.
   1. Select **Dual Zone Display **and tap/click **Assign Channel** from the action bar, Or,
   1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **채널 지정 **대화 상자가 열립니다.
   1. Enter the **Channel Role** as **Zone**.
   1. 경로별 참조 채널을 선택합니다. Select the channel folder path (**Zone Mapping Project **--> **Channels** --> **Dual Zone** ) in the Channel.
   1. Select the **Priority** for this channel as **1**. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. **저장**&#x200B;을 클릭합니다.
   ![zm7](assets/zm7.gif)

1. ***장치 등록 및 지정***

   1. 별도의 브라우저 창을 실행합니다. 웹 브라우저를 사용하여 Screens 플레이어로 이동하거나 AEM Screens 앱을 실행합니다. 장치를 열면 장치의 상태가 등록되지 않음으로 표시됩니다.
   1. From the AEM dashboard, navigate to **Zone Mapping Project** --> **Devices**.
   1. 작업 표시줄에서* 장치 관리자**를 클릭합니다.
   1. Click **Device Registration** and you will see the pending devices.
   1. Select the device you want to register and click **Register Device**.
   1. 웹 브라우저나 AEM Screens 플레이어에서 코드를 확인하여 코드의 유효성을 검사해야 합니다. Click **Validate** to navigate to **Device Registration** screen.
   1. Enter **Title** as **Zone Device** and click **Register** and the device will be registered.
   1. Click **Assign Display** to move on to the next step where you assign the device to a display.
   1. Click **Assign Device** fand select the display path for your channel () as */content/screens/Test_Project/Locations/TestLocation/TestDisplay*. Click **Assign**.
   1. Click **Finish** to complete the process, and now the device is assigned.
   ![zm8](assets/zm8.gif)

1. ***다중 영역 디스플레이 만들기***

   1. Navigate and select the display from **Zone Mapping Project** --> **Locations** --> **San Jose **--> **Dual Zone **display and click **Dashboard** from the action bar.
   1. **장치** 패널에서 플레이어의 **장치 구성** 왼쪽에 있는 아이콘을 선택하고 **속성**&#x200B;을 클릭합니다.
   1. **장치 구성** 탭으로 이동하여 **매핑** 및 **템플릿** 필드를 입력합니다. Enter *{&quot;a1&quot;:&quot;${display.channel}/left&quot;, &quot;a2&quot;: &quot;${display.channel}/right&quot;}* in the **Mapping** field and template as *grid-2x1*.
   1. Click **Save &amp; Close** and reload the player.
   >[!NOTE]
   >
   >***장치 구성의 매핑 및 템플릿 이해***
   >
   >* 식별자 &quot;a1&quot;과 &quot;a2&quot;는 템플릿에 정의된 영역, 즉 &quot;screens-zone-a1&quot;과 &quot;screens-zone-a2&quot;에 해당합니다.
   >* ${display.channel}/left&quot;는 영역에 포함할 채널을 가리키며, 여기서 &quot;display.channel&quot;은 디스플레이에 있는 현재 채널 경로를 가리킵니다. 이렇게 하면 채널의 &quot;왼쪽&quot; 및 &quot;오른쪽&quot; 하위 항목이 효과적으로 포함됩니다.


   ![screen_shot_2018-01-22at114708am](assets/screen_shot_2018-01-22at114708am.png)

#### AEM Screens 플레이어에서 컨텐츠 보기 {#viewing-content-in-aem-screens-player}

AEM Screens 플레이어를 로드하거나 웹 브라우저를 사용하십시오.

두 채널 모두(왼쪽 및 오른쪽)의 컨텐츠가 Screens 플레이어에 표시되는 것을 확인할 수 있습니다. 컨텐츠는 2x1 디스플레이 영역으로 표시됩니다.

![](do-not-localize/screen_shot_2018-01-22at120206pm.png)

### 유추 {#inference}

AEM Screens에서 채널을 만들 때 사용할 수 있는 템플릿 중 하나를 사용하는 영역 매핑 기능을 사용하면 클라이언트 측 병합을 수행할 수 있습니다. 화면에서 다양한 영역을 만들고, 나아가 영역을 비디오, 이미지 및 기타 사용 가능한 자산으로 채울 수도 있습니다.
