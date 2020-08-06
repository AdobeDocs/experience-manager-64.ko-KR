---
title: 3D 자산 렌더링
seo-title: 3D 자산 렌더링
description: AEM에서 조작하고 저장한 3D 자산을 렌더링하여 웹 컨텐츠 페이지에서 사용할 2D 이미지를 만들 수 있습니다.
seo-description: AEM에서 조작하고 저장한 3D 자산을 렌더링하여 웹 컨텐츠 페이지에서 사용할 2D 이미지를 만들 수 있습니다.
uuid: fbbe4fb4-cf21-4752-a2b8-bec2d40e8362
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: bf155d8c-c012-4cb4-89a6-ceead715630e
translation-type: tm+mt
source-git-commit: 284339ee1ce0ffae97f732b569f73c732f063273
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 73%

---


# 3D 자산 렌더링{#rendering-d-assets}

AEM에서 조작하고 저장한 3D 자산을 렌더링하여 웹 컨텐츠 페이지에서 사용할 2D 이미지를 만들 수 있습니다.

[페이지 컨텐츠 편집](/help/sites-authoring/qg-page-authoring.md#editing-your-page-content)을 참조하십시오.

## 3D 자산을 렌더링할 때의 성능 고려 사항 {#performance-considerations-when-rendering-d-assets}

3D 컨텐츠를 렌더링하는 데에는 CPU나 메모리와 같은 중요한 서버 리소스가 소모됩니다. 따라서 렌더링에는 때로 많은 시간이 소요될 수 있습니다. 렌더링 시간은 명백한 모델 크기 및 서버 하드웨어 외에도 다양한 요소에 따라 상당히 달라집니다.

* **렌더러 선택**.

    AEM 3D의 기본 Rapid Refine™ 렌더러는 더 빠른 렌더링 시간을 위해 품질과 타협하고 있지만, 여전히 많은 애플리케이션에 대해 고품질 결과를 만들어내고 있습니다. 타사 애플리케이션을 통해 제공되는 렌더러(예를 들어, Autodesk® Maya® 또는 Autodesk® 3ds Max®에 배포되는 V-Ray™나 NVIDIA® Mental Ray®)는 광범위하게 구성할 수 있으며, 스테이지를 설계할 때 성능과 품질의 교환이 이루어집니다.

* **IBL과 기존 조명**.

   이 요인은 기본 Rapid Refine 렌더러에는 큰 영향이 없는 데 반해, Mental Ray와 같은 타사 렌더러는 기존 점 광원이나 스폿 광원을 사용할 때보다 IBL 스테이지에서 렌더링이 크게 느려집니다.

Rapid Refine 렌더러는 더 큰 이미지를 렌더링하는 데 일반적으로 수 분이 소요됩니다. 그러나 타사 렌더러는 종종 수십 분이 소요되며 최대 품질을 얻도록 구성되는 경우에는 수 시간도 소요됩니다.

서버 과부하를 방지하기 위해 전환, 처리 및 렌더링 작업은 필요에 따라 서버의 큐에 오르게 됩니다. The message &quot;Waiting for rendering...&quot; is shown on recently uploaded assets in the [!UICONTROL Card View]. 이 상태는 현재 렌더링 작업이 시작되려면 먼저 다른 처리 또는 렌더링 작업이 완료되어야 함을 나타냅니다.

>[!NOTE]
>
>3D 자산은 AEM 3D 대화형 보기에 표시된 재료와 관계 없이 항상 원래 재료로 렌더링됩니다. 이 기능은 내장 Rapid Refine 렌더러와 모든 기본 렌더러 모두에 적용됩니다.

**3D 자산을 렌더링하려면**:

1. 볼 3D 자산을 엽니다.

   [3D 자산 보기](/help/sites-classic-ui-authoring/classicui-view-3d-assets.md)를 참조하십시오.

1. **Adobe Experience Manager**&#x200B;의 **[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL 자산**]을 탭합니다.
1. Near the upper-right corner of the page, from the **[!UICONTROL View** drop-down list, tap **[!UICONTROL Card View]**.
1. 렌더링할 3D 개체로 이동합니다.

1. 3D 개체의 카드를 탭하여 자산 세부 사항 페이지에서 엽니다.
1. 페이지의 왼쪽 위 모서리 근처에 있는 드롭다운 목록을 탭한 다음, **[!UICONTROL 렌더링]**&#x200B;을 선택합니다.

   ![chlimage_1-13](assets/chlimage_1-13.png)

1. Near the upper-right corner of the asset details page, tap the **[!UICONTROL Stage Selector]** icon (spotlight), then select a stage name with the background and lighting that you want to apply to the 3D object.

   ](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md)AEM 3D의 단계 사용 정보[를 참조하십시오.

   ![chlimage_1-14](assets/chlimage_1-14.png)

   [!UICONTROL 스테이지 선택기 아이콘]

1. On the **[!UICONTROL Render]** drop-down list on the left side of the asset details page, select a renderer.

   기본 렌더러인 **[!UICONTROL Rapid Refine]** 렌더러는 항상 사용 가능합니다. 선택한 스테이지가 기본 형식인 경우, 해당하는 타사 렌더러도 사용자가 선택하는 목록에서 사용할 수 있게 됩니다.

   ](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md)AEM 3D의 단계 사용 정보[를 참조하십시오.

1. 다음을 수행합니다.

   * In the **[!UICONTROL Width and Height]** fields, enter the pixel width and height that you want your image rendered.
   * In the **[!UICONTROL Image Name]** field, enter the name of the rendered image.
   * In the **[!UICONTROL Export Path]** field, enter the path where you want the rendered image stored. Or, tap the **[!UICONTROL Browse]** icon and navigate to a location.
   * (선택 사항) **[!UICONTROL 기존 이미지 덮어쓰기]** 확인란을 선택하거나 선택 취소합니다.

1. Near the upper-right corner of the asset details page, tap the **[!UICONTROL Camera Selector]** icon. 렌더링된 이미지에 적용할 카메라 보기를 선택하십시오.

   왼쪽과 오른쪽 막대 또는 위쪽과 아래쪽 막대는 보기에서 렌더링될 부분에 대한 시각적 표시입니다. 선택한 스테이지에서 카메라가 제공되면 사전 정의된 카메라를 선택할 수 있습니다.

   ![chlimage_1-15](assets/chlimage_1-15.png)

   [!UICONTROL 카메라 선택기 아이콘]

1. **[!UICONTROL 렌더링 시작]**&#x200B;을 탭하여 렌더링 프로세스를 시작합니다.

   렌더링이 시작되었음을 나타내는 메시지가 일시적으로 표시됩니다. For convenience, this message also includes a link to the selected [!UICONTROL Output Folder] so you can navigate to it directly.

