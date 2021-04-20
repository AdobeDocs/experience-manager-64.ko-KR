---
title: 3D 자산 렌더링
seo-title: 3D 자산 렌더링
description: AEM에서 조작하고 저장한 3D 에셋을 렌더링하여 웹 페이지용 2D 이미지를 만드는 방법을 살펴봅니다.
seo-description: AEM에서 조작하고 저장한 3D 에셋을 렌더링하여 웹 페이지용 2D 이미지를 만드는 방법을 살펴봅니다.
uuid: ee4d669c-72b1-4f7a-9a68-a7c6d59c7856
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5b044519-d034-4f05-98c5-f1b299a3ea37
exl-id: 3eecec53-0b39-4783-8730-f08705183941
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 72%

---

# 3D 자산 렌더링 {#rendering-d-assets}

AEM에서 조작하고 저장한 3D 자산을 렌더링하여 웹 컨텐츠 페이지에서 사용할 2D 이미지를 만들 수 있습니다.

[페이지 컨텐츠 편집](/help/sites-authoring/qg-page-authoring.md#editing-your-page-content)을 참조하십시오.

## 3D 자산을 렌더링할 때의 성능 고려 사항 {#performance-considerations-when-rendering-d-assets}

3D 컨텐츠를 렌더링하는 데에는 CPU나 메모리와 같은 중요한 서버 리소스가 소모됩니다. 따라서 렌더링에는 때로 많은 시간이 소요될 수 있습니다. 렌더링 시간은 명백한 모델 크기 및 서버 하드웨어 외에도 다양한 요소에 따라 상당히 달라집니다.

* **렌더러 선택**.

    AEM 3D의 기본 Rapid Refine™ 렌더러는 더 빠른 렌더링 시간을 위해 품질과 타협하고 있지만, 여전히 많은 애플리케이션에 대해 고품질 결과를 만들어내고 있습니다. 타사 애플리케이션을 통해 제공되는 렌더러(예를 들어, Autodesk® Maya® 또는 Autodesk® 3ds Max®에 배포되는 V-Ray™나 NVIDIA® Mental Ray®)는 광범위하게 구성할 수 있으며, 스테이지를 설계할 때 성능과 품질의 교환이 이루어집니다.

* **IBL과 기존 조명**.

   이 요인은 기본 Rapid Refine 렌더러에는 큰 영향이 없는 데 반해, Mental Ray와 같은 타사 렌더러는 기존 점 광원이나 스폿 광원을 사용할 때보다 IBL 스테이지에서 렌더링이 크게 느려집니다.

Rapid Refine 렌더러는 더 큰 이미지를 렌더링하는 데 일반적으로 수 분이 소요됩니다. 그러나 타사 렌더러는 종종 수십 분이 소요되며 최대 품질을 얻도록 구성되는 경우에는 수 시간도 소요됩니다.

서버 과부하를 방지하기 위해 전환, 처리 및 렌더링 작업은 필요에 따라 서버의 큐에 오르게 됩니다. &quot;렌더링 대기 중...&quot;이라는 메시지가 카드 보기에서 최근 업로드된 자산에 표시됩니다. 이 상태는 현재 렌더링 작업이 시작되려면 먼저 다른 처리 또는 렌더링 작업이 완료되어야 함을 나타냅니다.

>[!NOTE]
>
>3D 자산은 AEM 3D 대화형 보기에 표시된 재료와 관계 없이 항상 원래 재료로 렌더링됩니다. 이 기능은 내장 Rapid Refine 렌더러와 모든 기본 렌더러 모두에 적용됩니다.

**3D 자산을 렌더링하려면**:

1. 볼 3D 자산을 엽니다.

   [3D 자산 보기](viewing-3d-assets.md)를 참조하십시오.

1. Adobe Experience Manager의 **[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL 자산]**&#x200B;을 탭합니다.
1. 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 보기]** 드롭다운 목록에서 **[!UICONTROL 카드 보기]**&#x200B;를 탭합니다.
1. 렌더링할 3D 개체로 이동합니다.
1. 3D 개체의 카드를 탭하여 자산 세부 사항 페이지에서 엽니다.
1. 페이지의 왼쪽 위 모서리 근처에 있는 드롭다운 목록을 탭한 다음, **[!UICONTROL 렌더링]**&#x200B;을 선택합니다.

   ![chlimage_1-369](assets/chlimage_1-369.png)

1. 자산 세부 사항 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 스테이지 선택기]** 아이콘(스포트라이트)을 탭한 다음, 3D 개체에 적용할 배경과 조명이 있는 스테이지 이름을 선택합니다.

   ](about-the-use-of-stages-in-aem-3d.md)AEM 3D의 단계 사용 정보[를 참조하십시오.

   ![chlimage_1-370](assets/chlimage_1-370.png)

   **[!UICONTROL 스테이지 선택기 아이콘]**

1. 자산 세부 사항 페이지의 왼쪽에 있는 **[!UICONTROL 렌더링]** 드롭다운 목록에서 렌더러를 선택합니다.

   기본 렌더러인 **Rapid Refine** 렌더러는 항상 사용 가능합니다. 선택한 스테이지가 기본 형식인 경우, 해당하는 타사 렌더러도 사용자가 선택하는 목록에서 사용할 수 있게 됩니다.

   ](about-the-use-of-stages-in-aem-3d.md)AEM 3D의 단계 사용 정보[를 참조하십시오.

1. 다음을 수행합니다.

   * **[!UICONTROL 너비]** 및 **[!UICONTROL 높이]** 필드에 이미지를 렌더링할 픽셀 너비와 높이를 입력합니다.
   * **[!UICONTROL 이미지 이름]** 필드에 렌더링된 이미지의 이름을 입력합니다.
   * **[!UICONTROL 내보내기 경로]** 필드에 렌더링된 이미지를 저장할 경로를 입력합니다. 또는 **[!UICONTROL 찾아보기]** 아이콘을 탭하고 원하는 위치로 이동합니다.
   * (선택 사항) **[!UICONTROL 기존 이미지]e** 덮어쓰기 확인란을 선택하거나 선택 취소합니다.

1. 자산 세부 사항 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 카메라 선택기]** 아이콘을 탭합니다. 렌더링된 이미지에 적용할 카메라 보기를 선택하십시오.

   왼쪽과 오른쪽 막대 또는 위쪽과 아래쪽 막대는 보기에서 렌더링될 부분에 대한 시각적 표시입니다. 선택한 스테이지에서 카메라가 제공되면 사전 정의된 카메라를 선택할 수 있습니다.

   ![chlimage_1-371](assets/chlimage_1-371.png)

   **[!UICONTROL 카메라 선택기 아이콘]**

1. **[!UICONTROL 렌더링 시작]**&#x200B;을 탭하여 렌더링 프로세스를 시작합니다.

   렌더링이 시작되었음을 나타내는 메시지가 일시적으로 표시됩니다. 편의상 이 메시지에는 선택한 [대상 폴더]에 대한 링크도 포함되어 있어서 이 폴더로 바로 이동할 수 있습니다.
