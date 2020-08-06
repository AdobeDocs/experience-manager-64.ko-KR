---
title: 3D 자산 보기
seo-title: 3D 자산 보기
description: AEM의 자산 세부 사항 페이지에서 사용할 수 있는 대화형 3D 뷰어와 이 뷰어를 사용하여 3D 자산을 보는 방법에 대해 알아보십시오.
seo-description: AEM의 자산 세부 사항 페이지에서 사용할 수 있는 대화형 3D 뷰어와 이 뷰어를 사용하여 3D 자산을 보는 방법에 대해 알아보십시오.
uuid: 7d8133ac-3110-4979-8e19-e65090e791be
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 65040923-a8a8-4e27-82c0-67a04348e238
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 36%

---


# 3D 자산 보기 {#viewing-d-assets}

이 문서에서는 자산 세부 사항으로 3D 자산을 보는 방법과 사이트의 3D 구성 요소에 있는 자산을 보는 방법에 대해 설명합니다.

## 자산 세부 사항 페이지에서 3D 자산 보기 {#viewing-d-assets-in-the-asset-details-page}

대화형 3D 뷰어는 AEM의 자산 세부 사항 페이지에서 사용할 수 있습니다. 이 뷰어에는 3D 자산을 궤도를 따라 이동하고, 확대/축소하고, 패닝할 수 있는 대화형 카메라 컨트롤 컬렉션이 포함되어 있습니다.

![chlimage_1-139](assets/chlimage_1-139.png)

AEM 3D에서 기본 단계를 사용하는 것외에도, 타사 애플리케이션에서 만들어 AEM에 업로드한 단계를 사용할 수도 있습니다.

[AEM 3D의 단계 사용 정보](about-the-use-of-stages-in-aem-3d.md)를 참조하십시오.

>[!NOTE]
>
>3D 자산을 보려면 장치 또는 데스크톱 브라우저가 WebGL을 지원해야 합니다. 또한 기본 그래픽 하드웨어에는 원하는 크기와 복잡도의 모델을 렌더링하는 데 필요한 기능과 메모리가 충분해야 합니다. 그림자 설정과 같은 특정 미리 보기 기능은 일부 브라우저에서 사용할 수 없습니다.

### 3D 자산을 볼 때의 성능 고려 사항 {#performance-considerations-when-you-view-d-assets}

자산 세부 사항 페이지 보기에서 3D 자산을 여는 데 걸리는 시간은 몇 가지 요인에 따라 다릅니다. 이러한 요인에는 다음이 포함됩니다.

* 서버에 대한 대역폭 및 대기 시간
* 모델 크기(면 수)
* 맵의 수 및 크기
* 단계의 복잡성 예: IBL 이미지의 크기

또한 카메라를 대화형으로 조작할 때 워크스테이션, 노트북 또는 모바일 터치 장치와 같은 클라이언트 컴퓨터의 기능도 고려해야 합니다. 그래픽 성능이 좋은 강력한 시스템에서는 대화형 3D 보기 환경이 좀 더 원활하고 유용할 수 있습니다.

**3D 자산을 보려면**:

1. 3D 자산을 AEM에 업로드했는지 확인합니다.

   [AEM에서의 3D 자산 업로드 및 처리 정보](upload-processing-3d-assets.md)를 참조하십시오.

1. From AEM, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Assets]**.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL Card View]**.
1. 보려는 3D 자산으로 이동합니다.
1. 3D 자산의 카드를 탭하여 자산 세부 사항 페이지에서 엽니다.
1. 다음 중 하나를 수행합니다.

   * 자산 세부 사항 페이지의 오른쪽 아래 모서리에서 카메라 제어 팔레트를 사용하여 자산의 다양한 보기를 변경합니다.

      스크롤 휠이 없는 비터치식 입력 장치를 사용하는 경우에도(예: 클래식 Apple 단일 단추 마우스) 각 모드에서 3D 자산의 확대/축소 또는 원근감을 변경할 수 있습니다. `SHIFT` 키를 누른 상태로 마우스 단추를 누르고 위아래로 끌어 동작을 수행합니다.

      일반 노트북 컴퓨터의 터치 패드를 사용하는 경우 두 손가락 제스처로 확대/축소 또는 원근 동작을 제어하기 어려운 경우가 많습니다. 이러한 경우 `SHIFT` 키를 누른 상태로 동작을 수행할 수 있습니다. 이러한 종류의 노력은 핀치 제스처의 속도를 줄어주므로, 원하는 정확한 확대/축소 수준 또는 원근 상태에 보다 쉽게 도달할 수 있습니다. 또는 `SHIFT` 키를 누른 채로 한 손가락을 사용해서 위아래로 끌어 확대/축소 또는 원근 동작에 영향을 줄 수 있습니다.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>카메라 컨트롤 이름</strong><br /> </td> 
      <td><strong>설명</strong></td> 
      </tr> 
      <tr> 
      <td><p>확대/축소</p> <p>또는</p> <p>Presp</p> </td> 
      <td><p>탭하거나 클릭하여 확대/축소 모드와 원근 모드 간을 전환합니다.</p> <p>Or, press and hold down the <code>ALT/OPTION</code> key during the action to temporarily toggle to Perspective<br /> mode. 키를 떼면 확대/축소 모드로 돌아갑니다.</p> 
      <ul> 
      <li><strong>확대</strong>-돌리 인/축소 비헤이비어를 사용하여 카메라를 보고 있는 자산에서<br /> 더 가깝게 또는 멀리 이동합니다. 확대/축소는 마우스의 스크롤 휠(사용 가능한 경우), 모바일 장치에서의 두 손가락 핀치 제스처 또는 Shift 키를 누른 채로 마우스 왼쪽 단추를 사용하여 위아래로 끌 때의 기본 동작입니다.</li> 
      <li><strong>원근</strong>-보기에서 자산의 상대적 크기를 유지하면서 카메라의 초점 거리(FIELD-OF-VIEW라고도 함)를 변경합니다. 원근은 스크롤 휠(사용 가능한 경우), 모바일 장치에서의 두 손가락 핀치 제스처 또는 Shift 키를 누른 채로 마우스 왼쪽 단추를 사용하여 위아래로 끌 때의 대체 동작입니다.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>궤도</p> <p>또는</p> <p>팬</p> </td> 
      <td><p>궤도 모드와 팬 모드 간을 전환하려면 탭하거나 클릭합니다.</p> <p>Or, press and hold the <code>ALT/OPTION</code> key during the action to temporarily toggle to Pan mode. 키를 떼면 궤도 모드로 돌아갑니다.</p> 
      <ul> 
      <li><strong>궤도</strong>- 3D 자산의 중앙 근처에 있는 대상 점을 중심으로 하는 구에서 보기 카메라를 이동합니다. 궤도는 모바일 장치에서 왼쪽 단추 드래그 또는 단일 터치 드래그의 기본 동작입니다.</li> 
      <li><strong>패닝</strong>- 보기 평면에서 카메라를 이동합니다. 그에 따라 대상 지점이 이동되므로, 후속 궤도 동작은 새 대상 지점에 따라 카메라를 이동합니다. 패닝은 이동은 왼쪽 단추 드래그 및 단일 터치 드래그의 대체 동작입니다.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>검사</p> <p>또는</p> <p>타겟</p> </td> 
      <td><p>을 탭하거나 클릭하여 검사 모드와 Target 모드 간을 전환합니다.</p> 
      <ul> 
      <li><strong>검사</strong>-탭하거나 클릭하여 Target 모드로 전환합니다.</li> 
      <li><strong>Target</strong>-3D 자산의 아무 곳이나 탭하거나 클릭하여 자산의 해당 부분에 있는 보기를 가운데로 정렬합니다.<br /> 궤도 동작은 새 대상 포인트를 사용합니다.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>재설정</td> 
      <td>뷰 대상 점을 모델의 중심으로 복원하려면 탭하거나 클릭합니다. Reset also moves the camera<br /> closer or further away to show the asset in its entirety and at a reasonable viewing size.</td> 
      </tr> 
    </tbody> 
    </table>

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Stage Selector]** icon. 3D 자산에 적용할 배경 및 조명이 있는 단계 이름을 선택하십시오.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   단계는 3D 모델을 보는 환경 배경, 지표 평면 및 조명을 제공합니다.

   ](about-the-use-of-stages-in-aem-3d.md)AEM 3D의 단계 사용 정보[를 참조하십시오.

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Camera Selector]** icon, then select a camera view that you want to apply to the 3D asset.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   단계는 종종 사전 정의된 카메라를 제공합니다. 현재 카메라를 다시 선택하여 미리 정의된 설정으로 복원할 수 있습니다.

   ](about-the-use-of-stages-in-aem-3d.md)AEM 3D의 단계 사용 정보[를 참조하십시오.

1. 페이지 상단 오른쪽에서 **[!UICONTROL 저장]**&#x200B;을 탭합니다.
1. 다음 중 하나를 수행하십시오.

   * 3D 자산을 렌더링합니다.

      [3D 자산 렌더링](rendering-3d-assets.md)을 참조하십시오.

   * 페이지 상단 오른쪽에서 **[!UICONTROL 닫기]**&#x200B;를 탭하여 자산 페이지로 돌아갑니다.

## 사이트 3D 구성 요소에서 3D 자산 보기 {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>이 섹션은 Adobe Dimension 이외의 3D 자산 유형에 사용되는 클래식 webGL 뷰어에만 적용됩니다.

장치 유형에 따라 다양한 방법으로 3D 구성 요소 기능에 액세스합니다.

자세한 내용은 다음을 참조하십시오.

* [터치스크린 디바이스](#touchscreen-devices)
* [터치패드 장치](#touchpad-devices)
* [마우스 및 트랙볼 장치](#mouse-and-trackball-devices)

3D 구성 [요소가 있는 웹 페이지 미리 보기를 참조하십시오](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component).

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### 터치스크린 디바이스 {#touchscreen-devices}

터치스크린 디바이스에서 3D 구성 요소를 사용하여 작업하려면

1. 한 손가락으로 끌거나 밀어 개체 주위로 시점(&quot;카메라&quot;)을 이동(&quot;궤도&quot;)합니다. 어떤 방향으로든 객체를 볼 수 있습니다.

1. 두 손가락을 모으고 펴서 카메라를 오브젝트에서 가깝거나 멀게 이동합니다. 이 동작은 확대 또는 축소와 유사하며 개체에 대한 세부 사항을 검사할 수 있습니다. 또는 + 또는 - 단추를 눌러 카메라를 오브젝트에서 더 가깝게 또는 더 멀리 이동합니다.

1. 두 손가락으로 끌면 카메라를 패닝할 수 있습니다. 이 작업을 수행하면 카메라가 수평으로 움직이므로 확대하면서 오브젝트의 다른 부분을 볼 수 있습니다. 또는 [궤도/ **[!UICONTROL 팬 전환]** ] 단추를 눌러 [팬] 모드로 전환한 다음 한 손가락 드래그하여 카메라를 이동합니다. 궤도/ **[!UICONTROL 이동 전환]** 단추를 눌러 궤도 **[!UICONTROL 모드로 돌아갑니다]** .

1. 뷰어 **[!UICONTROL 재설정을]** 눌러 카메라를 재설정합니다. 이 작업을 수행하면 개체가 다시 전체 보기로 돌아가게 되고 활성화된 경우 자동 회전이 다시 시작됩니다.

1. 전체 화면 **[!UICONTROL 을]** 눌러 전체 화면 모드로 전환합니다(장치에서 지원하는 경우). [ **[!UICONTROL 전체 화면]** ]을 다시 눌러 3D 뷰어를 페이지 포함 모드로 복원합니다.

### 터치패드 장치 {#touchpad-devices}

터치패드 디바이스에서 3D 구성 요소 사용 방법:

1. 터치패드 버튼을 아래로 누른 상태에서 한 손가락으로 드래그하면 개체 주위의 시점(&quot;카메라&quot;)을 이동할 수 있습니다. 어떤 방향으로든 객체를 볼 수 있습니다.

1. 터치패드 버튼을 위로 두 손가락으로 아래로 또는 위로 드래그하여 카메라를 개체와 더 가깝거나 멀리 이동할 수 있습니다. 이 작업은 확대 또는 축소와 유사하며 개체에 대한 세부 사항을 검사할 수 있습니다. 또는 [확대] 또는 [ **[!UICONTROL 확대]** ] **[!UICONTROL 축소]** 단추를 클릭하여 카메라를 오브젝트에서 더 가깝게 또는 더 멀리 이동합니다.

1. ALT **/option** 키 및 터치패드 버튼을 누른 상태에서 한 손가락으로 드래그하여 카메라를 패닝합니다. 이 작업을 수행하면 카메라가 수평으로 움직이므로 확대하면서 오브젝트의 다른 부분을 볼 수 있습니다. 또는 [ **[!UICONTROL 궤도/이동 전환]** ] 단추를 클릭하여 **[!UICONTROL 이동]** 모드로 전환한 다음 (왼쪽) 단추를 누른 상태에서 한 손가락을 드래그하여 카메라를 패닝합니다. 궤도/ **[!UICONTROL 이동 전환]** 단추를 다시 클릭하여 **[!UICONTROL 궤도]** 모드로 돌아갑니다.

1. [뷰어 **[!UICONTROL 재설정]** ]을 클릭하여 카메라를 재설정합니다. 이 작업을 수행하면 개체가 다시 전체 보기로 돌아가게 되고 활성화된 경우 자동 회전이 다시 시작됩니다.

1. 전체 화면 **[!UICONTROL 을]** 클릭하여 전체 화면 모드로 전환합니다. 키보드의 **Escape** 키를 사용하거나 **[!UICONTROL 전체 화면]** 을 다시 클릭하여 3D 뷰어를 페이지 포함 모드로 복원합니다.

### 마우스 및 트랙볼 장치 {#mouse-and-trackball-devices}

마우스와 트랙볼 장치에서 3D 구성 요소를 사용하여 작업하려면

1. 마우스 왼쪽 버튼을 누른 상태에서 마우스로 아래로 드래그하여 개체 주위로 시점(&quot;카메라&quot;)을 이동합니다. 어떤 방향으로든 객체를 볼 수 있습니다.

1. 스크롤 휠을 사용하여 카메라를 개체와 더 가깝거나 멀어진 위치로 이동합니다. 확대/축소 기능과 비슷하며 개체에 대한 세부 사항을 확인할 수 있습니다. 또는 [확대] 또는 [ **[!UICONTROL 확대]** ] **[!UICONTROL 축소]** 단추를 클릭하여 카메라를 오브젝트에서 더 가깝게 또는 더 멀리 이동합니다.

1. Alt **/Option** 키와 마우스 왼쪽 버튼을 누른 상태에서 드래그하여 카메라를 이동합니다. 확대하면서 개체의 다른 부분을 볼 수 있도록 카메라를 수평으로 이동합니다. 또는 [궤도/ **[!UICONTROL 팬 전환]** ] 단추를 클릭하여 **[!UICONTROL 이동]** 모드로 전환한 다음 왼쪽 마우스 단추를 누른 상태에서 드래그하여 카메라를 이동합니다. 궤도/ **[!UICONTROL 팬 전환]** 을 다시 클릭하여 **[!UICONTROL 궤도]** 모드로 돌아갑니다.
1. [뷰어 **[!UICONTROL 재설정]** ]을 클릭하여 카메라를 재설정합니다. 이 작업을 수행하면 개체가 다시 전체 보기로 돌아가게 되고 활성화된 경우 자동 회전이 다시 시작됩니다.
1. 전체 화면 **[!UICONTROL 을]** 클릭하여 전체 화면 모드로 전환합니다. 키보드의 **[!UICONTROL Escape]** 키를 사용하거나 **[!UICONTROL 전체 화면]** 을 다시 클릭하여 3D 뷰어를 페이지 포함 모드로 복원합니다.

