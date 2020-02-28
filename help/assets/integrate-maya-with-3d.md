---
title: Autodesk Maya와 AEM 3D 통합
seo-title: Autodesk Maya와 AEM 3D 통합
description: 선택적으로 AEM 3D를 Autodesk® Maya® 소프트웨어와 통합하여 기본 Maya 파일(.MA 및 .MB)에 대한 지원을 활성화하고 사용 가능한 모든 Maya 렌더러와 함께 AEM에서 3D 자산을 렌더링할 수 있습니다.
seo-description: 선택적으로 AEM 3D를 Autodesk® Maya® 소프트웨어와 통합하여 기본 Maya 파일(.MA 및 .MB)에 대한 지원을 활성화하고 사용 가능한 모든 Maya 렌더러와 함께 AEM에서 3D 자산을 렌더링할 수 있습니다.
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# Autodesk Maya와 AEM 3D 통합 {#integrating-aem-d-with-autodesk-maya}

>[!NOTE]
>
>이 작업은 선택 사항이며 Windows에만 적용됩니다.

선택적으로 AEM 3D를 Autodesk® Maya® 소프트웨어와 통합하여 기본 Maya 파일(`.MA` 및 `.MB`)에 대한 지원을 활성화하고 사용 가능한 Maya 렌더러를 사용하여 AEM에서 3D 자산을 렌더링할 수 있습니다.

*이 통합은 Windows 전용입니다*.

Autodesk Maya와 통합할 때 Autodesk Maya를 설치 및 구성하고, Maya 실행 폴더에 대한 경로를 추가하고, 통합 및 렌더링을 위해 Maya를 활성화하고, 통합을 테스트해야 합니다.

고급 [구성 설정을](advanced-config-3d.md)참조하십시오.

AEM [3D와 AutoDesk 3ds Max 통합을 참조하십시오](integrating-aem-3d-with-autodesk-3ds-max.md).

**AEM 3D를 Autodesk Maya와 통합하려면**:

1. AEM이 호스팅된 동일한 서버에 Autodesk Maya 2016 소프트웨어를 설치합니다.

   설치 후 Maya를 열어 사용할 수 있으며 라이센스 문제가 없는지 확인하십시오.

   >[!NOTE]
   >
   >AEM에서는 Maya 명령줄 렌더링 도구(`render.exe`)만 사용합니다. 단일 Maya 네트워크 라이센스를 사용하면 Maya 컨텐츠를 동시에 처리하거나 렌더링할 수 있는 최대 5대의 서버를 사용할 수 있습니다.

1. Maya에서 Autodesk FBX® 플러그인을 활성화합니다.
1. MentalRay 렌더링 플러그인이나 원하는 다른 렌더러를 설치합니다.

   설치 후 MentalRay가 Maya에서 사용 가능한지 확인합니다.

1. Maya 실행 폴더의 경로를 Windows PATH 환경 변수에 추가합니다.

   예를 들어 Windows Server 2012에서 **[!UICONTROL 시작 > 제어판 > 시스템 및 보안 > 시스템 > 고급 시스템 설정 > 환경 변수를 누릅니다**. 전체 경로를 `Maya2016\bin` 시스템 변수에 `Path`추가합니다.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Maya가 인제스트 및 렌더링을 가능하게 하려면 **[!UICONTROL CRXDE]** Lite를 열고 `/libs/settings/dam/v3D/assetTypes/maya` Enabled **[!UICONTROL 속성을 로]** 설정합니다 `true`.

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. JT(Siemens PLM Open CAD) 파일 형식을 활성화하려면 `/libs/settings/dam/v3D/assetTypes/jt` 활성화 **[!UICONTROL 속성으로 이동하여]** 설정 `true`속성을설정합니다.
1. AEM에서 Maya를 렌더러로 활성화합니다. 먼저 도구 > 일반 **[!UICONTROL > CRXDE Lite로 이동합니다]**.
1. CRXDE **[!UICONTROL Lite]** 페이지의 왼쪽 패널에서 다음 페이지로 이동합니다.

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. Enabled **[!UICONTROL 속성을]** 로 설정합니다 `true`.

1. CRXDE Lite 페이지의 왼쪽 위 모서리 **[!UICONTROL 근처에]** 있는 모두 **[!UICONTROL 저장을 탭합니다]**.

   이제 Maya가 렌더러로 활성화됩니다.

## Autodesk Maya와 AEM 3D 통합 테스트 {#testing-the-integration-of-aem-d-with-autodesk-maya}

1. AEM 자산을 연 다음 폴더에 있는 `.MA` 파일을 `sample-3D-content/models` `test3d` 폴더에 업로드합니다.

   이전에 기본 3D 기능의 유효성을 검사하기 위해 다운로드되었습니다. `sample-3D-content.zip`

1. [!UICONTROL **카드** 보기로 돌아가서 업로드된 자산에 표시된 메시지 배너를 확인합니다.

   Maya가 기본 `.MA` 형식을 (으)로 변환하는 동안 형식 변환 배너가 표시됩니다 `.FBX`.

1. 모든 처리가 완료되면 `logo-sphere.ma` 자산을 열고 `stage-helipad.ma` 단계를 선택합니다.

   미리 보기 환경은 `logo_sphere.fbx` 및 와 동일합니다 `stage-helipad.fbx`.

1. Near the upper-left corner of the page, tap or click the drop-down list and then select **[!UICONTROL CRender]**.

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. 렌더러 **[!UICONTROL 드롭다운]** 목록에서 Autodesk Maya를 **[!UICONTROL 선택한 다음]**&#x200B;렌더링 **[!UICONTROL 시작을]**&#x200B;누릅니다.
1. 페이지의 오른쪽 위 모서리 근처에 있는 닫기를 탭하거나 클릭하여 **[!UICONTROL 카드]** 보기로 **[!UICONTROL 돌아갑니다]** .

   다른 이미지 이름을 지정하지`logo-sphere`않은 경우 렌더링하는 이미지 자산에서 메시지 배너를 확인합니다. 배너의 진행률 표시줄에 렌더링 진행 상태가 표시됩니다.

   >[!NOTE]
   >
   >렌더링은 CPU를 많이 사용하므로 완료하는 데 몇 분 정도 걸릴 수 있습니다.

1. 렌더링이 완료되면 렌더링된 이미지 자산을 엽니다.

   렌더링된 이미지가 지금 렌더링을 클릭할 때 보고 있던 이미지와 **[!UICONTROL 일치하는지 확인합니다]**.

## Maya에서 지원하는 추가 포맷 활성화 {#enabling-additional-formats-supported-by-maya}

(선택 사항) Maya는 다양한 3D 입력 형식을 지원하며, AEM이 파일 유형을 인식할 수 있도록 모든 것을 활성화할 수 있습니다. 활성화되면 AEM은 파일을 Maya로 보내 AEM에서 직접 인제스트할 수 있는 중간 형식으로 변환합니다.

형식에 따라 기능 지원이 제한될 수 있으며(예: 자료를 전달하지 않을 수 있음) 품질/품질은 제한될 수 있습니다(예: 역 면). Adobe는 일반적인 메커니즘만 지원하지만 특정 포맷 변환은 지원하지 않습니다.

지원되는 [데이터 가져오기 형식 참조| Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html) - Maya에서 지원하는 포맷에 대한 정보를 제공합니다.

**AEM에서 지원되는 추가 형식을 활성화하려면**:

1. CRXDE **[!UICONTROL Lite를]**&#x200B;사용하여 로 `/libs/settings/dam/v3D/assetTypes`이동합니다.
1. jt **[!UICONTROL 노드의 복사본을]** 만듭니다. jt 노드를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 복사를]** **[!UICONTROL 선택한]**&#x200B;다음 **[!UICONTROL 자산 유형]** 폴더를 **[!UICONTROL 마우스 오른쪽 단추로 클릭하고]**&#x200B;붙여넣기를선택합니다. 이렇게 하면 새 노드가 생성됩니다 `/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`.
1. 새 노드의 이름을 변경하여 추가할 파일 유형을 나타내는 고유한 이름을 지정합니다. 파일 접미사를 사용하거나 다른 고유 식별자를 사용할 수 있습니다.

1. 새 **[!UICONTROL 노드의 Enabled]** 속성을 로 설정합니다 `true`.

1. 새 **[!UICONTROL 메모의 Extension]** 속성을 추가할 형식의 파일 접미사/확장명으로 설정합니다.
1. MimeType **[!UICONTROL 속성을]** 적절한 값으로 설정합니다. `application/x-` 그 다음에 Extension **[!UICONTROL 속성 값이]** 오는 것은 대부분의 파일 형식에서 작동해야 합니다.
1. Conversion **[!UICONTROL 속성이]** 로 설정되고 IngestPermission이 `fbx` 로 **[!UICONTROL 설정되어 있는지]** 확인합니다 `Maya`.
1. 페이지 **[!UICONTROL 왼쪽 상단]** 근처에 있는 모두 저장을 클릭합니다.

다음 스크린샷은 COLLADA DAE를 예로 사용하여 추가된 파일 형식을 보여 줍니다.

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)

