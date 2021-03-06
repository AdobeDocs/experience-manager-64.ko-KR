---
title: Adobe Analytics에 대한 비디오 추적 구성
seo-title: Adobe Analytics에 대한 비디오 추적 구성
description: SiteCatalyst에 대한 비디오 추적 구성에 대해 알아봅니다.
seo-description: SiteCatalyst에 대한 비디오 추적 구성에 대해 알아봅니다.
uuid: c72d2d59-915d-4af1-aeb9-821915979571
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: e7672b23-a4af-49bb-bba7-0565d3bda802
exl-id: 24dd0d05-6327-47e2-a3d1-6ed40af06783
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1776'
ht-degree: 1%

---

# Adobe Analytics{#configuring-video-tracking-for-adobe-analytics}에 대한 비디오 추적 구성

비디오 이벤트를 추적하는 데 사용할 수 있는 방법에는 몇 가지가 있으며, 그 중 2가지는 이전 버전의 Adobe Analytics에 대한 레거시 옵션입니다. 이러한 기존 옵션은 다음과 같습니다.이전 이정표 및 이전 초.

>[!NOTE]
>
>계속하기 전에 AEM 내에 재생 가능한 비디오&#x200B;**가 업로드되어 있는지 확인하십시오.**
>
>비디오가 페이지에서 재생되도록 하려면 AEM에서 비디오 파일을 코드 변환하는 방법에 대한 자세한 내용은 **[이 자습서](/help/sites-authoring/default-components-foundation.md#video)**&#x200B;를 참조하십시오.

다음 절차를 사용하여 각 메서드를 사용하여 비디오 추적에 대한 프레임워크를 설정합니다.

>[!NOTE]
>
>새 구현의 경우, 비디오 추적에 **기존 옵션을 사용하지 않는 것이 좋습니다.** 대신 **Milestones** 메서드를 사용하십시오.

## 일반적인 단계 {#common-steps}

1. 사이드 킥에서 **비디오 구성 요소**&#x200B;를 드래그하고 구성 요소에 대해 재생 가능한 **비디오를 자산**&#x200B;으로 추가하여 웹 페이지를 설정합니다

1. [Adobe Analytics 구성 및 프레임워크를 만듭니다](/help/sites-administering/adobeanalytics.md).

   * 다음에 나오는 섹션의 예제는 구성에 **my-sc-configuration** 및 프레임워크에 **videofw** 이름을 사용합니다.

1. 프레임워크 페이지에서 RSID를 선택하고 사용을 모두 로 설정합니다. ([http://localhost:4502/cf#/etc/cloudservices/sitecatalyst/videoconf/videofw.html](http://localhost:4502/cf#/etc/cloudservices/sitecatalyst/videoconf/videofw.html))
1. 사이드 킥의 일반 구성 요소 카테고리에서 비디오 구성 요소를 프레임워크로 드래그합니다.
1. 추적 메서드를 선택합니다.

   * [이정표](/help/sites-administering/adobeanalytics.md)
   * [비레거시 이정표](/help/sites-administering/adobeanalytics.md)
   * [이전 이정표](/help/sites-administering/adobeanalytics.md)
   * [이전 초](/help/sites-administering/adobeanalytics.md)

1. 추적 방법을 선택하면 그에 따라 CQ 변수 목록이 변경됩니다. 구성 요소를 추가로 구성하고 CQ 변수를 Adobe Analytics 속성에 매핑하는 방법에 대한 자세한 내용은 다음에 나오는 섹션을 사용합니다.

## 이정표 {#milestones}

Milestones 메서드는 비디오에 대한 가장 많은 정보를 추적하며, 사용자 지정이 가능하고, 구성하기에 쉽습니다.

이정표 방법을 사용하려면 시간 기반 추적 오프셋을 지정하여 이정표를 정의합니다. 비디오 재생이 이정표를 지나면 페이지에서 Adobe Analytics을 호출하여 이벤트를 추적합니다. 정의한 각 이정표에 대해 구성 요소는 Adobe Analytics 속성에 매핑할 수 있는 CQ 변수를 만듭니다. 이러한 CQ 변수의 이름은 다음 형식을 사용합니다.

```shell
eventdata.events.milestoneXX
```

XX 접미사는 이정표를 정의하는 추적 오프셋입니다. 예를 들어 4, 8, 16, 20 및 28초의 추적 오프셋을 지정하면 다음 CQ 변수가 생성됩니다.

* `eventdata.events.milestone4`
* `eventdata.events.milestone8`
* `eventdata.events.milestone16`
* `eventdata.events.milestone20`
* `eventdata.events.milestone28`

다음 표는 Milestones 메서드에 제공된 기본 CQ 변수를 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <th>CQ 변수</th> 
   <th>Adobe Analytics 속성</th> 
  </tr> 
  <tr> 
   <td>eventdata.videoName </td> 
   <td>여기에 매핑된 변수에는 DAM에 설정된 경우 비디오의 <strong>사용자에게 친숙한</strong> 이름(<strong>제목</strong>)이 포함됩니다.이 값을 설정하지 않으면 비디오의 <strong>파일 이름</strong>이 대신 전송됩니다. 비디오 재생 시작 시 한 번만 전송됩니다.</td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFileName </td> 
   <td>여기에 매핑된 변수에는 파일 이름이 포함됩니다. eventdata.events.a.media.view와 함께 전송됩니다. </td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFilePath </td> 
   <td>이 변수에 매핑된 변수에는 서버의 파일 경로가 포함됩니다. eventdata.events.a.media.view와 함께 전송됩니다. </td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.segmentView </td> 
   <td>세그먼트 이정표를 전달할 때마다 전송됩니다 </td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.timePlayed</td> 
   <td>이정표가 트리거될 때마다 전송되며 사용자가 주어진 세그먼트를 보는 데 걸린 시간(초)도 이 이벤트와 함께 전송됩니다. 예: eventX=21<br /> </td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.view </td> 
   <td>비디오 보기 초기화 시 전송됩니다.</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.complete </td> 
   <td>비디오가 재생을 마치면 전송됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>eventdata.events.milestoneX </td> 
   <td>지정된 이정표가 통과되면 X는 <br />에서 이정표가 트리거되는 두 번째 이정표를 의미합니다. </td> 
  </tr> 
  <tr> 
   <td>eventdata.a.contentType </td> 
   <td>모든 이정표에 전송는 Adobe Analytics 호출에서 pev3로 표시되며, 일반적으로 "video"<br />로 전송됩니다 </td> 
  </tr> 
  <tr> 
   <td>eventdata.a.media.name </td> 
   <td>eventdata.videoName과 정확히 일치합니다 </td> 
  </tr> 
  <tr> 
   <td>eventdata.a.media.segment </td> 
   <td>본 세그먼트에 대한 정보를 포함합니다(예: 2:O:4-8) </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>DAM에서 편집할 비디오를 열고 **Title** 메타데이터 필드를 원하는 이름으로 설정하여 비디오의 **사용자에게 친숙한 **이름을 설정할 수 있습니다.

1. 추적 방법으로 이정표를 선택한 후 오프셋 추적 상자에 쉼표로 구분된 추적 오프셋 목록을 초 단위로 입력합니다. 예를 들어 다음 값은 비디오 시작 후 4, 8, 16, 20 및 28초에 이정표를 정의합니다.

   ```xml
   4,8,16,20,24
   ```

   오프셋 값은 0보다 큰 정수여야 합니다. 기본값은 `10,25,50,75`입니다.

1. CQ 변수를 Adobe Analytics 속성에 매핑하려면 구성 요소의 CQ 변수 옆에 있는 ContentFinder에서 Adobe Analytics 속성을 드래그합니다.

   매핑 최적화에 대한 자세한 내용은 Adobe Analytics에서 [비디오 측정](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/setup/setup-overview.html) 안내서를 참조하십시오.

1. [페이지에 ](/help/sites-administering/adobeanalytics.md) 프레임워크를 추가합니다.
1. **미리 보기 모드**&#x200B;에서 설정을 테스트하려면 비디오를 재생하여 트리거할 Adobe Analytics 호출을 가져옵니다.

다음에 오는 Adobe Analytics 추적 데이터 예는 4,8,16,20 및 24의 추적 오프셋을 사용하여 이정표 추적과 CQ 변수에 대해 다음 매핑을 적용하는 것입니다.

<table> 
 <tbody> 
  <tr> 
   <th>CQ 변수</th> 
   <th>Adobe Analytics 속성</th> 
  </tr> 
  <tr> 
   <td>eventdata.videoName </td> 
   <td>prop2</td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFileName </td> 
   <td>prop3 </td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFilePath </td> 
   <td>prop4</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.segmentView </td> 
   <td>event1</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.timePlayed</td> 
   <td>event2<br /> </td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.view </td> 
   <td>event3</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.a.media.complete </td> 
   <td>event4<br /> </td> 
  </tr> 
  <tr> 
   <td>eventdata.events.milestone4</td> 
   <td>event10</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.milestone8</td> 
   <td>event11</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.milestone16</td> 
   <td>event12</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.milestone20</td> 
   <td>event13</td> 
  </tr> 
  <tr> 
   <td>eventdata.events.milestone24</td> 
   <td>event14</td> 
  </tr> 
  <tr> 
   <td>eventdata.a.contentType </td> 
   <td>eVar3</td> 
  </tr> 
  <tr> 
   <td>eventdata.a.media.name </td> 
   <td>eVar1, prop1 </td> 
  </tr> 
  <tr> 
   <td>eventdata.a.media.segment </td> 
   <td>eVar2</td> 
  </tr> 
 </tbody> 
</table>

이 예제에서 비디오 구성 요소는 프레임워크 페이지에 다음과 같이 나타납니다.

![video1](assets/video1.png)

>[!NOTE]
>
>Adobe Analytics에 대한 호출을 보려면 DigitalPulse Debugger 또는 Fiddler와 같은 적절한 도구를 사용하십시오.

제공된 예제를 사용하는 Adobe Analytics 호출은 DigitalPulse Debugger를 사용하여 볼 때 다음과 같이 표시됩니다.

![chlimage_1-156](assets/chlimage_1-156.png)

*다음은&#x200B;**다음**값을 포함하는 Adobe Analytics에 대한 첫 번째 호출입니다.*

* *eventdata.a.media.name,*
* *prop2-4, contentType(비디오) 및 세그먼트(1:O:1-4)가 포함된 eVar2 및 eVar3과 함께*
* *event3. events.a.media.view에 매핑되었습니다.*

![chlimage_1-157](assets/chlimage_1-157.png)

*Adobe Analytics에&#x200B;**대해 세**번째 호출입니다.*

* *prop1 및 eVar1에 포함`a.media.name;`*
* *event1. 세그먼트를 보았으므로*
* *event2 sent with time played = 4*
* *eventdata.events.milestones8에 도달했으므로 event11이 전송되었습니다.*
* *prop2를 4로 전송하지 않습니다(eventdata.events.a.media.view가 트리거되지 않았으므로).*

## 비레거시 이정표 {#non-legacy-milestones}

비레거시 이정표 방법은 추적 길이 백분율을 사용하여 이정표를 정의한다는 점을 제외하면 이정표 메서드와 유사합니다. 일반적인 내용은 다음과 같습니다.

* 비디오 재생이 이정표를 지나면 페이지에서 Adobe Analytics을 호출하여 이벤트를 추적합니다.
* Adobe Analytics 속성을 사용한 매핑에 대해 정의된 [CQ 변수](#milestones)의 정적 집합입니다.
* 정의한 각 이정표에 대해 구성 요소는 Adobe Analytics 속성에 매핑할 수 있는 CQ 변수를 만듭니다.

이러한 CQ 변수의 이름은 다음 형식을 사용합니다.

XX 접미사는 이정표를 정의하는 추적 길이의 백분율입니다. 예를 들어 10, 25, 50 및 75의 백분율을 지정하면 다음 CQ 변수가 생성됩니다.

* `eventdata.events.milestone10`
* `eventdata.events.milestone25`
* `eventdata.events.milestone50`
* `eventdata.events.milestone75`

```shell
eventdata.events.milestoneXX
```

1. 추적 방법으로 비레거시 이정표를 선택한 후 오프셋 추적 상자에 쉼표로 구분된 추적 길이 백분율 목록을 입력합니다. 예를 들어 다음 기본값은 트랙 길이의 10, 25, 50 및 75%에서 이정표를 정의합니다.

   ```xml
   10,25,50,75
   ```

   오프셋 값은 0보다 큰 정수여야 합니다.

1. CQ 변수를 Adobe Analytics 속성에 매핑하려면 구성 요소의 CQ 변수 옆에 있는 ContentFinder에서 Adobe Analytics 속성을 드래그합니다.

   매핑 최적화에 대한 자세한 내용은 Adobe Analytics에서 [비디오 측정](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/setup/setup-overview.html) 안내서를 참조하십시오.

1. [페이지에 ](/help/sites-administering/adobeanalytics.md) 프레임워크를 추가합니다.
1. **미리 보기 모드**&#x200B;에서 설정을 테스트하려면 비디오를 재생하여 트리거할 Adobe Analytics 호출을 가져옵니다.

## 이전 이정표 {#legacy-milestones}

이 메서드는 *추적 오프셋* 필드에 지정된 이정표가 비디오 내에서 설정된 포인트가 아닌 백분율로 차이가 있는 이정표 메서드와 유사합니다.

>[!NOTE]
>
>추적 오프셋 필드는 1과 100 사이의 정수가 포함된 쉼표로 구분된 목록만 허용합니다.

1. 트랙 오프셋을 설정합니다.

   * e.g.10,50,75,100

   또한 Adobe Analytics으로 전송된 정보는 사용자 지정이 덜 됩니다.매핑에 사용할 수 있는 변수는 3개뿐입니다.

<table> 
 <tbody> 
  <tr> 
   <td>eventdata.videoName <br /> </td> 
   <td>여기에 매핑된 변수에는 DAM에 설정된 경우 비디오의 <strong>사용자에게 친숙한</strong> 이름(<strong>제목</strong>)이 포함됩니다.제목이 설정되지 않은 경우 비디오의 <strong>파일 이름</strong>이 대신 전송됩니다. 비디오 재생 시작 시 한 번만 전송됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFileName </td> 
   <td>여기에 매핑된 변수에는 파일 이름이 포함됩니다. 비디오 재생 시작 시 한 번만 전송됩니다.</td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFilePath </td> 
   <td>이 변수에 매핑된 변수에는 서버의 파일 경로가 포함됩니다. 비디오 재생 시작 시 한 번만 전송됩니다.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>DAM에서 편집할 비디오를 열고 **Title **메타데이터 필드를 원하는 이름으로 설정하여 비디오의 **사용자에게 친숙한 **이름을 설정할 수 있습니다. 또한 완료되면 변경한 내용을 저장해야 합니다.

1. 이러한 변수를 prop 1에서 3에 매핑합니다

   호출에서 나머지 관련 정보&#x200B;**는** a4/>pev3 **라는 이름의 하나** 변수로 전송됩니다.****

   **제공된 예제를** 사용하는 Adobe Analytics에 대한 샘플 호출은 DigitalPulse Debugger를 사용하여 볼 때 다음과 같이 표시됩니다.

   ![이정표1](assets/lmilestones1.png)

   *호출에서&#x200B;**전송된 pev3**변수에는 다음 정보가 포함됩니다.*

   * *Name*  - 비디오 파일의 이름(*film.avi*)
   * *길이*  - 비디오 파일의 길이(초)*(100*)입니다
   * *플레이어 이름*  - 비디오 파일을 재생하는 데 사용되는 비디오 플레이어(*HTML5 비디오*)입니다
   * *재생된 총 시간(초)*  - 비디오가 재생된 총 시간(*25*)입니다
   * *시작 타임스탬프*  - 비디오 재생이 시작되는 시기를 식별하는 타임스탬프입니다(*133103567*)
   * *재생 세션*  - 재생 세션의 세부 정보입니다. 이 필드는 사용자가 비디오와 상호 작용한 방식을 나타냅니다. 여기에는 비디오 재생을 시작한 위치, 비디오 슬라이더를 사용하여 비디오를 진행했는지 여부, 비디오 재생을 중지했는지 여부 등의 데이터가 포함될 수 있습니다(*L10E24S58L58 - 비디오가 초 단위로 중지됨). L10 섹션 25을 건너뛰고 초 단위로 건너뛰었습니다. 48*)

## 기존 초 {#legacy-seconds}

** 이전 초** 메서드를 사용할 때 Adobe Analytics 호출이 N초마다 트리거되며, 여기서 N은 추적 오프셋 필드에 지정됩니다.

1. 트랙 오프셋을 초 단위로 설정합니다.

   * 예: 6
   >[!NOTE]
   >
   >추적 오프셋 필드는 0보다 큰 정수만 허용합니다

   Adobe Analytics으로 전송된 정보는 사용자 지정이 덜 됩니다. 매핑에 사용할 수 있는 변수는 3개뿐입니다.

<table> 
 <tbody> 
  <tr> 
   <td>eventdata.videoName <br /> </td> 
   <td>여기에 매핑된 변수에는 DAM에 설정된 경우 비디오의 <strong>사용자에게 친숙한</strong> 이름(<strong>제목</strong>)이 포함됩니다.제목이 설정되지 않은 경우 비디오의 <strong>파일 이름</strong>이 대신 전송됩니다. 비디오 재생 시작 시 한 번만 전송됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFileName </td> 
   <td>여기에 매핑된 변수에는 파일 이름이 포함됩니다. 비디오 재생 시작 시 한 번만 전송됩니다.</td> 
  </tr> 
  <tr> 
   <td>eventdata.videoFilePath </td> 
   <td>이 변수에 매핑된 변수에는 서버의 파일 경로가 포함됩니다. 비디오 재생 시작 시 한 번만 전송됩니다.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>DAM에서 편집할 비디오를 열고 **Title** 메타데이터 필드를 원하는 이름으로 설정하여 비디오의 **사용자에게 친숙한 **이름을 설정할 수 있습니다. 또한 완료되면 변경한 내용을 저장해야 합니다.

1. 이러한 변수를 prop1, prop2 및 prop3에 매핑

   호출에서 나머지 관련 정보&#x200B;**는** a4/>pev3 **라는 이름의 하나** 변수로 전송됩니다.****

   제공된 예제를 사용하는 Adobe Analytics 호출은 DigitalPulse Debugger를 사용하여 볼 때 다음과 같이 표시됩니다.

   ![lseconds](assets/lseconds.png)

   *호출은 위의 이전 이정표 호출과 유사합니다.](/help/sites-administering/adobeanalytics.md)**에 제공된 pev3**[에 대한 정보를 참조하십시오.*

**이 자습서에 사용된 참조:**

[0] [https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/setup/setup-overview.html](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/setup/setup-overview.html)
