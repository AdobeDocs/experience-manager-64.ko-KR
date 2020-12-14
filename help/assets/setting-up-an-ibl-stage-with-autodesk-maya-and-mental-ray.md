---
title: Autodesk Maya 및 Mental Ray로 IBL 스테이지 설정
seo-title: Autodesk Maya 및 Mental Ray로 IBL 스테이지 설정
description: Autodesk Maya 및 Mental Ray로 IBL 스테이지를 설정하는 방법
seo-description: Autodesk Maya 및 Mental Ray로 IBL 스테이지를 설정하는 방법
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 75%

---


# Autodesk Maya 및 Mental Ray로 IBL 스테이지 설정 {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. Maya에서 빈 장면을 새로 만듭니다.

1. 전형적인 모델에 대한 (임시)참조를 만듭니다. 이렇게 하면 조명 평가, 카메라 설정, 렌더러 구성이 용이해집니다.
1. 이미지 기반 조명을 설정합니다.

   1. **[!UICONTROL 렌더링 설정]**&#x200B;에서 **[!UICONTROL 렌더 다음을 선택합니다.mental ray]** 및 [장면] 탭을 엽니다.
   1. **[!UICONTROL 렌더링 환경]** 아코디언을 열고 **[!UICONTROL 이미지 기반 조명 렌더링]**&#x200B;을 클릭합니다.
   1. 상자 왼쪽에 오른쪽 화살표가 있는 상자 아이콘을 클릭하여 IBL 노드 `mentalRayIblShape1`을 선택한 다음 **[!UICONTROL 렌더링 설정]**&#x200B;을 종료합니다.
   1. **[!UICONTROL 속성 편집기]**&#x200B;에서 변환 노드 `mentalRayIbl1`을 선택한 다음 변환 노드의 이름을 `AdobeIbl`으로 바꿉니다.
   1. 노드의 Scale(배율)을 환경계가 이 스테이지와 함께 표시할 가장 큰 3D 개체보다 훨씬 크게 만들도록 설정합니다(예: `10000,10000,10000`).
   1. `AdobeIblShape` 노드를 선택하고 다음과 같이 구성하십시오.

      * **[!UICONTROL Mapping]**(매핑) - Spherical(구형)
      * **[!UICONTROL Type]**(유형) - Image File(이미지 파일)
      * **[!UICONTROL Emit Light]**(빛 발산) - true
   1. 원하는 32비트 TIFF 이미지를 `AdobeIbl` 노드에 첨부합니다.


1. 지표 평면을 설정합니다.

   * 지표 평면으로 사용할 적절한 평면을 만들고 좌표 원점을 통과하는 IBL 구 안에 적당히 맞게 크기를 지정합니다.
   * **[!UICONTROL Use Background]**(배경 사용) 재료를 지표 평면에 첨부하고 이름을 `AdobeUseBackground`로 지정한 다음, 지표 평면 개체에 첨부합니다.

1. (선택 사항) 카메라를 만들고 구성합니다.

   카메라를 자산이 삽입될 장면의 중앙을 향하게 합니다. 카메라는 반드시 렌더링 가능으로 설정하십시오.

1. Mental Ray로 렌더링을 설정합니다.

   다음 제안 내용으로 **[!UICONTROL 렌더링 설정]**&#x200B;을 구성합니다.

   * **** 일반 탭

      모든 **[!UICONTROL 렌더링 가능 카메라]**&#x200B;에 대한 **[!UICONTROL 알파 채널(마스크)]** 확인란을 선택 취소합니다.

   * **[!UICONTROL Quality(품질) 탭]**

      * **Overall quality**(전체 품질) - `0.5` 이하
      * **간접 확산(GI) 모드** -  `Final Gather`
      * **필터 크기** -  `2.0`,  `2.0`
   * 사용할 장면을 일반 이미지 크기로 렌더링합니다. 필요할 경우 광원, Render(렌더링) 설정 또는 두 가지 모두를 미세 조정하여 원하는 결과를 얻도록 합니다.

      이미지 기반 조명을 사용하는 Mental Ray로 렌더링하는 것은 속도가 매우 느리고 CPU를 많이 사용합니다. 따라서, 원하는 렌더링 품질을 만들 수 있는 가장 낮은 품질 설정을 구성하는 것이 좋습니다.


1. 2단계에서 만든 참조를 제거합니다.

1. 장면을 저장한 다음, Autodesk Maya를 종료합니다.

1. 장면과 IBL PTIFF를 AEM에 업로드하고 업로드 처리가 완료될 때까지 기다립니다.

   [자산 업로드](managing-assets-touch-ui.md#uploading-assets)를 참조하십시오.

1. 파일 종속성을 해결합니다.

   [파일 종속성 해결](resolve-file-dependencies.md)을 참조하십시오.

   AEM 3D가 스테이지에 구성된 IBL 이미지를 감지하지 못할 수 있습니다. 이러한 경우 감지하지 못한 종속성을 수동으로 해결해야 합니다. 감지하지 못한 각 종속성에 대해 이전에 업로드한 동일한 IBL PTIFF 이미지를 지정할 수 있습니다. 또는 다른 이미지를 지정하여 IBL 효과를 추가로 제어할 수 있습니다. 종속성을 해결한 후 반드시 **[!UICONTROL 저장]**&#x200B;을 탭하여 재처리를 시작해야 합니다.

1. AEM에서 [자산 속성]을 엽니다. **[!UICONTROL 제목]**&#x200B;이 **[!UICONTROL 스테이지 선택기]** 드롭다운 목록에 표시될 적절한 문자열로 설정합니다. **[!UICONTROL 클래스]**&#x200B;가 **[!UICONTROL 3D 스테이지]**&#x200B;로 설정되어 있는지 확인합니다. 저장하고 종료하십시오.

1. 3D 자산을 열고 새 스테이지를 선택한 다음, 미리 보기에 예상대로 표시되고 렌더링되는지 확인합니다.

