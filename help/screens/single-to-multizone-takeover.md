---
title: 단일 영역을 다중 영역 인계
seo-title: 단일 영역을 멀티존 인계
description: 'AEM Screens 프로젝트에서 단일 영역을 멀티존 인계에 대해 알려면 이 페이지를 따르십시오.  '
seo-description: 'AEM Screens 프로젝트에서 단일 영역을 멀티존 인계에 대해 알려면 이 페이지를 따르십시오.    '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# 단일 영역을 다중 영역 인계 {#single-zoneto-multizone}

## 사용 사례 설명 {#use-case-description}

이 섹션에서는 단일 영역 레이아웃 채널과 대체되는 다중 영역 레이아웃 채널을 설정하는 방법을 강조하는 사용 사례 예제를 설명합니다. 각 채널에는 이미지/비디오 에셋이 순서대로 지정됩니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해해야 합니다.

* **[채널 만들기 및 관리](/help/screens/managing-channels.md)**
* **[위치 만들기 및 관리](/help/screens/managing-locations.md)**
* **[예약 만들기 및 관리](/help/screens/managing-schedules.md)**
* **[장치 등록](/help/screens/device-registration.md)**

### 주요 배우 {#primary-actors}

컨텐츠 작성자

## 프로젝트 설정 {#setting-up-the-project}

아래 절차에 따라 프로젝트를 설정하십시오.

1. 아래와 같이 ZonesDemo **로**&#x200B;명명된 AEM Screens 프로젝트를 만듭니다.

   >[!NOTE]
   >
   >AEM Screens에서 프로젝트를 만들고 관리하는 방법에 대한 자세한 내용은 프로젝트 [만들기를 참조하십시오](/help/screens/creating-a-screens-project.md).

   ![screen_shot_2019-02-21at35809pm](assets/SZtoMZ1.png)

1. **하나의 이미지로 시퀀스 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.
   1. 마법사에서 **시퀀스** 채널을 선택하고 FullScreenOne이라는 이름의 채널을 **만듭니다**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ2.png)
   1. 채널을 선택하고 작업 **표시줄에서** 편집을 클릭하여 편집기를 열고 이미지를 해당 채널에 드래그하여 놓습니다.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ3.png)

1. **4개의 이미지가 포함된 2X2 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.

   1. 마법사에서 **2X2 분할 화면** 채널 템플릿을 선택하고 TwobyTwoChannel이라는 이름의 채널을 **만듭니다**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ4.png)
   1. 채널을 선택하고 작업 **표시줄에서** 편집을 클릭하여 편집기를 열고 아래 표시된 대로 4개의 이미지(4개의 다른 영역)를 해당 채널에 드래그하여 놓습니다.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ5.png)

1. **2개의 이미지로 1X2 분할 화면 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.

   1. 마법사에서 **1X2 분할 화면** 채널 템플릿을 선택하고 OnedbyTwoChannel이라는 이름의 채널을 **만듭니다**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ6.png)
   1. 채널을 선택하고 작업 **표시줄에서** 편집을 클릭하여 편집기를 열고 아래에 표시된 것처럼 두 개의 이미지(두 개의 다른 영역)를 해당 채널에 드래그하여 놓습니다.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ7.png)

1. **하나의 전체 화면 비디오가 포함된 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.

   1. 마법사에서 **시퀀스** 채널 템플릿을 선택하고 FullScreensVideo라는 이름의 채널을 **만듭니다**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ8.png)
   1. 채널을 선택하고 작업 **표시줄에서 편집을** 클릭하여 편집기를 열고 비디오 구성 요소를 해당 채널에 드래그하여 놓은 다음 아래와 같이 원하는 비디오를 추가합니다.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ9.png)

## 단일 영역에서 다중 영역으로 전환 인수 채널 설정 {#takeover-channel-setup}

1. **다중 영역 인수에 대한 단일 영역 채널 편집**

   1. 1단계에서 만든 채널(**FullScreenOne)** 을 선택합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다. 두 개의 채널 구성 요소와 하나의 비디오 구성 요소를 편집기에 드래그하여 놓습니다.
   ![screen_shot_2019-02-21at40516pm](assets/SZtoMZ10.png)

1. **FullScreenOne 채널에 추가된 구성 요소 채우기**

   1. FullScreenOne 편집기에서 첫 번째 채널 구성 요소를 **선택하고** 구성을 **클릭하여** 이전 단계에서 만든 채널을 가리킵니다. 채널 경로에서 채널 구성 요소 **모두에** 대한 경로를 추가하고 비디오를 아래 표시된 대로 비디오 구성 요소에 드래그하여 놓습니다.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo1.gif)

1. **전환하는 동안 채널에 대한 시간 설정**

   >[!NOTE]
   >
   >기본적으로 자산은 8초마다 전환되지만, 특정 기간 후에 자산을 전환하려면 아래 단계를 따르십시오.

   1. FullScreenOne의 편집기에서 두 번째 채널 구성 요소를 **선택하고** 설정을 **클릭하여** 이 채널의 지속 시간을 구성합니다. 마찬가지로, 아래에 표시된 것처럼 채널 2의 시간 기간을 설정합니다.
이 예에서 시간은 3초로 설정됩니다.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo2.gif)

## 결과 미리 보기 {#previewing-result}

편집기에서 미리 **보기를** 클릭하고 자산이 단일 영역에서 다중 영역으로 어떻게 전환되는지 확인할 수 있습니다.

![](assets/SZ_MZvideo3.gif)
