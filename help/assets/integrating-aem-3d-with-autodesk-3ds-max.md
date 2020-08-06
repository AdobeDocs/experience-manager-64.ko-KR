---
title: AEM 3D와 Autodesk 3ds Max 통합
seo-title: AEM 3D와 AutoDesk 3ds Max 통합
description: 선택적으로 AEM 3D를 Autodesk 3ds Max 소프트웨어와 통합하여 기본 3ds Max 파일(.MAX)을 지원할 수 있습니다. 지금은 3ds Max를 통한 렌더링이 지원되지 않습니다.
seo-description: 선택적으로 AEM 3D를 Autodesk 3ds Max 소프트웨어와 통합하여 기본 3ds Max 파일(.MAX)을 지원할 수 있습니다. 지금은 3ds Max를 통한 렌더링이 지원되지 않습니다.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# AEM 3D와 Autodesk 3ds Max 통합 {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>이 작업은 선택 사항이며 Windows에만 적용됩니다.

선택적으로 AEM 3D를 Autodesk 3ds Max 소프트웨어와 통합하여 기본 3ds Max 파일(.MAX)을 지원할 수 있습니다. 지금은 3ds Max를 통한 렌더링이 지원되지 않습니다.

고급 [구성 설정을 참조하십시오](advanced-config-3d.md).

AEM [3D와 AutoDesk Maya 통합도 참조하십시오](integrate-maya-with-3d.md).

**AEM 3D를 Autodesk 3ds Max와 통합하려면 다음을 수행하십시오**.

1. AEM 작성자 노드가 설치된 동일한 서버에 Autodesk 3ds Max 소프트웨어를 설치합니다.

   설치 후 Maya를 열어 사용할 수 있으며 라이센스 문제가 없는지 확인하십시오.

   >[!NOTE]
   >
   >액세스가 거부된 문제를 방지하려면 AEM과 동일한 관리 사용자 계정을 사용하여 3ds Max를 설치하십시오.

1. 3ds Max에서 사용자 **[!UICONTROL 지정 > 플러그인 관리자를 클릭합니다]**.

   해당 상태 `FBXMAX.DLU` 가 **[!UICONTROL [!UICONTROL이 로드되었는지]** 확인하고 **확인합니다**.

   플러그인 **[!UICONTROL 관리자]** 대화 상자와 3ds Max를 닫습니다.

1. 전환 스크립트를 업데이트합니다.

   AEM에서는 명령줄 스크립트를 사용하여 3ds Max 명령줄 유틸리티를 호출합니다 `3dsmaxcmd.exe`. 3ds Max 2016 이외의 버전을 설치하거나 표준이 아닌 위치에 3ds Max를 설치한 경우 또는 다른 파티션 또는 드라이브에 AEM을 설치한 경우 이 스크립트를 편집해야 합니다.

   1. CRXDE Lite을 열고 탐색합니다 `/libs/settings/dam/v3D/scripts/max`.
   1. 두 번 `export-fbx.bat` 클릭하여 엽니다.
   1. 필요에 따라 스크립트의 첫 번째 줄을 편집하여 유틸리티의 위치를 `3dsmaxcmd.exe` 반영합니다. 예를 들어 3ds Max 2017을 사용하고 AEM이 다른 디스크 드라이브에 설치되어 있는 경우:

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장을 탭합니다]**.

   CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장을 탭합니다]**.

1. 작업 폴더를 제거합니다(이전 .MAX 파일 인제스트를 시도한 경우에만 필요).

   1. CRXDE Lite에서 탐색합니다 `/libs/settings/dam/v3D/Paths/maxWorkPath`. 기본적으로 이 설정의 값은 AEM 설치 루트 폴더 `./MaxWork`를 기준으로 합니다.
   1. 서버 자체에 로그인하고 파일 탐색기를 사용하여 AEM 설치 루트 폴더로 이동합니다.
   1. MaxWork **[!UICONTROL 폴더]** (전체 콘텐트 포함)가 있는 경우 삭제합니다.

      다음 번에 .MAX 파일을 인제스트할 때 폴더가 자동으로 다시 생성됩니다.

1. 다음을 수행하여 3ds Max를 섭취할 수 있습니다.

   1. CRXDE Lite에서 Enabled `/libs/settings/dam/v3D/assetTypes/max` 속성을 true로 **[!UICONTROL 찾아]** 설정합니다.

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장을 탭합니다]**.

## AEM 3D와 Autodesk 3ds Max의 통합 테스트 {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. AEM Assets을 열고 `.max` 파일에 있는 파일 `sample-3D-content/models` 을 **[!UICONTROL test3d]** 폴더에 업로드합니다.

   기본 3D 기능의 유효성을 검사하기 위해 sample-3D-content.zip을 이전에 다운로드했습니다.

1. 카드 **[!UICONTROL 보기로]** 돌아가서 업로드된 자산에 표시된 메시지 배너를 확인합니다.

   기본 3ds Max 형식을 .FBX로 변환하는 동안 형식 변환 배너가 표시됩니다.

1. 처리가 완료되면 세부 사항 보기 `logo-sphere.max` 에서 **[!UICONTROL 엽니다]** .

   미리 보기 경험은 `logo_sphere.fbx`

