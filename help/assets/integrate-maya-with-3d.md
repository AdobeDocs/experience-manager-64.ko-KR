---
title: Autodesk Maya와 AEM 3D 통합
seo-title: Autodesk Maya와 AEM 3D 통합
description: 선택적으로 AEM 3D를 Autodesk® Maya® 소프트웨어와 통합하여 기본 Maya 파일(.MA 및 .MB)에 대한 지원을 활성화하고 사용 가능한 Maya 렌더러와 함께 AEM에서 3D 에셋을 렌더링할 수 있습니다.
seo-description: 선택적으로 AEM 3D를 Autodesk® Maya® 소프트웨어와 통합하여 기본 Maya 파일(.MA 및 .MB)에 대한 지원을 활성화하고 사용 가능한 Maya 렌더러와 함께 AEM에서 3D 에셋을 렌더링할 수 있습니다.
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 0%

---


# AEM 3D와 Autodesk Maya 통합 {#integrating-aem-d-with-autodesk-maya}

>[!NOTE]
>
>이 작업은 선택 사항이며 Windows에만 적용됩니다.

선택적으로 AEM 3D를 Autodesk® Maya® 소프트웨어와 통합하여 기본 Maya 파일(`.MA` 및 `.MB`)에 대한 지원을 활성화하고 사용 가능한 Maya 렌더러와 함께 AEM에서 3D 에셋을 렌더링할 수 있습니다.

*이 통합은 Windows에만 해당됩니다*.

Autodesk Maya와 통합할 때 Autodesk Maya를 설치 및 구성하고, Maya 실행 폴더에 대한 경로를 추가하고, 통합 및 렌더링에 Maya를 활성화하고, 통합을 테스트해야 합니다.

[고급 구성 설정](advanced-config-3d.md)을 참조하십시오.

[AutoDesk 3ds Max](integrating-aem-3d-with-autodesk-3ds-max.md)와 AEM 3D 통합을 참조하십시오.

**AEM 3D를 Autodesk Maya와 통합하려면 다음을 수행합니다**.

1. AEM이 호스팅된 동일한 서버에 Autodesk Maya 2016 소프트웨어를 설치합니다.

   설치 후 Maya를 열고 사용할 수 있으며 라이센스 문제가 없는지 확인합니다.

   >[!NOTE]
   >
   >AEM에서는 Maya 명령줄 렌더링 도구(`render.exe`)만 사용합니다. 단일 Maya 네트워크 라이센스를 사용하면 Maya 컨텐츠를 동시에 처리하거나 렌더링할 수 있는 서버가 최대 5개까지 가능합니다.

1. Maya에서 Autodesk FBX® 플러그인을 활성화합니다.
1. MentalRay 렌더링 플러그인이나 원하는 다른 렌더러를 설치합니다.

   설치 후 MentalRay가 Maya에서 사용 가능한지 확인합니다.

1. Maya 실행 폴더의 경로를 Windows PATH 환경 변수에 추가합니다.

   예를 들어 Windows Server 2012의 경우 **[!UICONTROL 시작] > [!UICONTROL Campaign 컨트롤 패널] > [!UICONTROL  시스템 및 보안] >  > [!UICONTROL 고급 시스템 설정] > [!UICONTROL 환경 변수]**. `Maya2016\bin` 폴더의 전체 경로를 `Path`시스템 변수에 추가합니다.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Maya를 통합 및 렌더링에 사용하려면 **[!UICONTROL CRXDE Lite]**&#x200B;을 열고 `/libs/settings/dam/v3D/assetTypes/maya`로 이동한 다음 **[!UICONTROL Enabled]** 속성을 `true`로 설정합니다.

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. JT(Siemens PLM Open CAD) 파일 형식을 활성화하려면 `/libs/settings/dam/v3D/assetTypes/jt`으로 이동하여 **[!UICONTROL Enabled]** 속성을 `true`으로 설정합니다.
1. AEM에서 Maya를 렌더러로 활성화합니다. **[!UICONTROL 도구 > 일반 > CRXDE Lite]**&#x200B;로 이동하는 것으로 시작합니다.
1. 왼쪽 패널의 **[!UICONTROL CRXDE Lite]** 페이지에서 다음 페이지로 이동합니다.

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. **[!UICONTROL Enabled]** 속성을 `true`로 설정합니다.

1. **[!UICONTROL CRXDE Lite]** 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장]**&#x200B;을 탭합니다.

   이제 Maya가 렌더러로 활성화됩니다.

## Autodesk Maya와 AEM 3D 통합 테스트 {#testing-the-integration-of-aem-d-with-autodesk-maya}

1. AEM Assets을 열고 `sample-3D-content/models`에 있는 `.MA` 파일을 `test3d` 폴더에 업로드합니다.

   `sample-3D-content.zip`은(는) 기본 3D 기능의 유효성을 검사하기 위해 이전에 다운로드되었습니다.

1. **[!UICONTROL 카드]** 보기로 돌아가서 업로드된 자산에 표시된 메시지 배너를 확인합니다.

   Maya가 기본 `.MA` 형식을 `.FBX`로 변환하는 동안 형식 변환 배너가 표시됩니다.

1. 모든 처리가 완료되면 `logo-sphere.ma` 에셋을 열고 `stage-helipad.ma` 스테이지를 선택합니다.

   미리 보기 환경은 `logo_sphere.fbx` 및 `stage-helipad.fbx`과 동일합니다.

1. 페이지의 왼쪽 위 모서리 근처에 있는 드롭다운 목록을 탭하거나 클릭한 다음 **[!UICONTROL CRender]**&#x200B;를 선택합니다.

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. **[!UICONTROL 렌더러]** 드롭다운 목록에서 **[!UICONTROL Autodesk Maya]**&#x200B;를 선택한 다음 **[!UICONTROL 렌더링 시작]**&#x200B;을 누릅니다.
1. 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 닫기]**&#x200B;를 탭하거나 클릭하여 **[!UICONTROL 카드]** 보기로 돌아갑니다.

   다른 이미지 이름을 지정하지 않은 경우 렌더링하는 이미지 자산에 대한 메시지 배너를 관찰합니다(`logo-sphere`). 배너의 진행률 표시줄에 렌더링 진행 상태가 표시됩니다.

   >[!NOTE]
   >
   >렌더링은 CPU 사용량이 매우 높으므로 완료하는 데 몇 분이 소요될 수 있습니다.

1. 렌더링이 완료되면 렌더링된 이미지 에셋을 엽니다.

   렌더링된 이미지가 **[!UICONTROL 지금 렌더링]**&#x200B;을 클릭한 시간에 보고 있던 이미지와 일치하는지 확인합니다.

## Maya {#enabling-additional-formats-supported-by-maya}에서 지원하는 추가 형식 활성화

(선택 사항) Maya는 많은 3D 입력 형식을 지원하며, AEM이 파일 유형을 인식할 수 있도록 모든 입력 형식을 활성화할 수 있습니다. 활성화된 경우 AEM은 파일을 Maya로 전송하여 AEM에서 직접 인제스트할 수 있는 중간 형식으로 변환합니다.

형식에 따라 기능 지원이 제한될 수 있으며(예: 자료를 전달하지 않을 수 있음) 품질/정확도가 제한될 수 있습니다(예: 반대로 얼굴을 바꾸는 경우). Adobe은 일반 메커니즘만 지원하지만 특정 형식 변환은 지원하지 않습니다.

[지원되는 데이터 가져오기 형식 참조 | Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html)에서 Maya가 지원하는 형식에 대한 자세한 내용을 보려면

**AEM에서 지원하는 추가 형식을 활성화하려면 다음을 수행합니다**.

1. **[!UICONTROL CRXDE Lite]**&#x200B;을 사용하여 `/libs/settings/dam/v3D/assetTypes`로 이동합니다.
1. **[!UICONTROL jt]** 노드를 복사합니다. **[!UICONTROL jt]** 노드를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 복사]**&#x200B;를 선택한 다음 **[!UICONTROL assetTypes]** 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 붙여넣기]**&#x200B;를 선택합니다. 이렇게 하면 새 노드 `/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`이 생성됩니다.
1. 추가할 파일 유형을 나타내는 고유한 이름을 지정하려면 새 노드의 이름을 변경합니다. 파일 접미어를 사용하거나 기타 고유 식별자를 사용할 수 있습니다.

1. 새 노드의 **[!UICONTROL Enabled]** 속성을 `true`로 설정합니다.

1. 새 메모의 **[!UICONTROL Extension]** 속성을 추가할 형식의 파일 접미어/확장명으로 설정합니다.
1. **[!UICONTROL MimeType]** 속성을 적절한 값으로 설정합니다. `application/x-` 뒤에 Extensionproperty 값이  **** 와야 대부분의 파일 유형에 대해 작동합니다.
1. **[!UICONTROL Conversion]** 속성이 `fbx` 및 **[!UICONTROL IngestRestruction]**&#x200B;로 `Maya`로 설정되어 있는지 확인합니다.
1. 페이지의 왼쪽 위 근처에 있는 **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

다음 스크린샷에서는 COLLADA DAE를 예로 사용하여 추가된 파일 형식을 보여 줍니다.

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)

