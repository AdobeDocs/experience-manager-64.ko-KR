---
title: Autodesk Maya 및 Mental Ray로 표준 스테이지 설정
seo-title: Autodesk Maya 및 Mental Ray로 표준 스테이지 설정
description: Autodesk Maya 및 Mental Ray로 표준 스테이지를 설정하는 방법
seo-description: Autodesk Maya 및 Mental Ray로 표준 스테이지를 설정하는 방법
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 85%

---


# Autodesk Maya 및 Mental Ray로 표준 스테이지 설정 {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. Maya에서 빈 장면을 새로 만듭니다.
1. 전형적인 모델에 대한 (임시)참조를 만듭니다. 이렇게 하면 조명 평가, 카메라 설정, 렌더러 구성이 용이해집니다.

1. 평소대로 광원을 추가합니다. 현재, AEM 3D는 다음 광원 유형을 지원합니다.

   * 방향 광원
   * 스폿 광원
   * 점 광원

   다른 광원 유형은 무시되거나 스테이지가 AEM 3D에 업로드될 때 위의 지원되는 유형 중 하나로 변환됩니다. 변환된 유형은 자산을 볼 때와 내장된 Rapid Refine 렌더러를 사용하여 렌더링할 때 사용됩니다. Maya로 렌더링할 때에는 원래 광원 유형이 사용됩니다.

1. 필요한 경우 지표 평면을 만들고 적절한 재질을 적용합니다.

   지표 평면은 단면으로 설정하는 것이 좋습니다. 그렇게 하면 AEM 3D에서 지표 평면이 자산을 가리지 않고 아래쪽에서 자산을 볼 수 있습니다.

1. (선택 사항) 카메라를 만들고 구성합니다.

   카메라를 자산이 삽입될 장면의 중앙을 향하게 합니다. 카메라는 반드시 렌더링 가능으로 설정하십시오.

1. Mental Ray로 렌더링을 설정합니다.

   다음 제안 내용으로 Render Settings(렌더링 설정)를 구성하십시오.

   * **[!UICONTROL 일반]** 탭

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

   * **[!UICONTROL Quality(품질) 탭]**

      * **[!UICONTROL 전체 품질]**`- 0.5` 이하
      * **[!UICONTROL 간접 확산(GI) 모드]** - `Final Gather`
      * **[!UICONTROL 필터 크기]** - `2.0`, `2.0`
   * 사용할 장면을 일반 이미지 크기로 렌더링합니다. 필요할 경우 광원이나 Render(렌더링) 설정을 미세 조정하거나 두 가지 모두를 조정하여 원하는 결과를 얻도록 합니다.

      이미지 기반 조명을 사용하는 Mental Ray로 렌더링하는 것은 속도가 매우 느리고 CPU를 많이 사용합니다. 따라서, 원하는 렌더링 품질을 만들 수 있는 가장 낮은 품질 설정을 구성하는 것이 좋습니다.


1. 2단계에서 만든 참조를 제거합니다.

1. 장면을 저장한 다음, Autodesk Maya를 종료합니다.
1. 장면을 AEM에 업로드하고 업로드 처리가 완료될 때까지 기다립니다.

   [자산 업로드](managing-assets-touch-ui.md#uploading-assets)를 참조하십시오.

   AEM 서버에 Autodesk® Maya®가 구성되어 있지 않은 경우 Maya에서 FBX를 내보내고 AEM에 업로드하십시오.

1. AEM에서 [자산 속성]을 엽니다. **[!UICONTROL 제목]** 을 **[!UICONTROL 스테이지 선택기]** 드롭다운 목록에 표시할 적절한 문자열로 설정합니다. **[!UICONTROL 클래스]**&#x200B;가 **[!UICONTROL 3D 스테이지]**&#x200B;로 설정되어 있는지 확인합니다. 저장하고 종료하십시오.
1. 3D 자산을 열고 새 스테이지를 선택한 다음, 미리 보기에 예상대로 표시되고 렌더링되는지 확인합니다.

