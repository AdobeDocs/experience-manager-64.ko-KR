---
title: 고급 구성 설정
seo-title: 고급 구성 설정
description: Maya 및 비 Maya 배포에 대한 AEM 3D 통합에 적용되는 고급 구성 설정에 대해 알아봅니다.
seo-description: Maya 및 비 Maya 배포에 대한 AEM 3D 통합에 적용되는 고급 구성 설정에 대해 알아봅니다.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 1%

---


# 고급 구성 설정 {#advanced-configuration-settings}

기본 구성 설정은 일반적인 사용 사례에 적합하지만 일부 상황에서는 변경을 요구할 수 있습니다.

다음 고급 구성 설정은 Maya 및 비 Maya 배포에 대한 AEM 3D 통합에 적용됩니다.

모든 설정은 AEM의 **CRXDE Lite** (**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)를 사용하여 액세스합니다.

>[!NOTE]
>
>패키지를 다시 설치하면 모든 설정이 기본값으로 재설정됩니다.

>[!CAUTION]
>
>아래 표에 나와 있지 않은 설정을 편집하면 예기치 않은 프로그램 비헤이비어가 발생할 수 있습니다.

## 자산 유형 구성 {#asset-types-configuration}

AEM의 **CRXDE Lite** (**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)에서 다음 구성에 액세스합니다.

| 경로 | 설명 |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | 통합 중에 만든 중간 3D 형식의 파일 유형을 지정합니다. &#39;fbx&#39; 및 &#39;obj&#39; 파일 포맷의 경우 비어 있거나, Maya에서 사용하는 포맷의 경우 &#39;fbx&#39;가 비어 있어야 합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | assetTypes 목록에서 이 항목을 활성화하거나 비활성화하려면 **[!UICONTROL true 또는 false로]** 설정합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | 이 자산 유형과 연결할 하나 이상의 쉼표로 구분된 파일 접미어 또는 파일 확장자를 지정합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | FBX 및 OBJ 파일 형식 `native` 과 Maya에서 사용하는 형식 `maya` 에 사용해야 합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | 이 자산 유형의 MIME 형식을 지정합니다. Maya에서 활성화된 형식의 경우, 여기서 `application/x-ext`는 값으로 지정된 문자열 `ext` 입니다 `Extension` . |

## 통합 구성 {#ingestion-configuration}

AEM의 **CRXDE Lite** (**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)에서 다음 구성에 액세스합니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>경로</strong></td> 
   <td><strong>설명</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>IBL 스테이지를 보거나 렌더링할 때 주변과 격리된 그림자를 생성할 수 있습니다. RapidRefine을 사용하여 미리 보기 및 렌더링에 적용</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>변환 및 렌더링 후 MayaWork 폴더에 임시 파일을 유지하려면 <strong>false</strong> 로 설정합니다. Maya 변환 및 렌더링 문제를 디버깅할 때 유용할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>활성화되면 ImageMagick이 서버에 설치되고 magickPath가 구성됩니다. Rapid Refine은 카드 보기 및 기타 보기에서 축소판으로 사용되는 간단한 3D 개체에 대한 애니메이션을 만드는 데 사용됩니다.</p> <p>애니메이션을 만드는 데 통합 프로세스 동안 상당한 CPU 리소스가 소모됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>통합 시 조명 맵을 자동으로 만들 수 있습니다. 자동 광원 <strong></strong> 맵 생성을 비활성화하려면 false로 설정합니다. Rapid Refine을 사용하면 미리 보기와 렌더링을 위해 품질이 저하되는 데 따른 비용 절감 효과로 CPU 사용량을 크게 줄일 수 있습니다. Maya와의 렌더링에는 영향을 주지 않습니다.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>true <strong></strong> (기본값)로 설정하면 필요한 경우 개체를 세로로 이동하여 개체의 모든 부분이 지표 평면 위에 있는지 확인합니다(y=0).</p> <p>false(기본값)로 설정하면 <strong>개체가 다시 배치되지 않고 스테이지의 지표 평면에 의해 부분적으로 숨겨질 수 있습니다</strong> . (Rapid Refine을 사용한 미리 보기 및 렌더링에만 적용됩니다.) 그러나 Maya와의 렌더링에는 영향을 주지 않습니다. true로 설정된 경우 Maya에서 개체의 세로 위치는 미리 보기나 Rapid Refine으로 렌더링할 때와 다를 수 있습니다 <strong></strong>.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>ImageMagick 변환 유틸리티의 경로 및 이름입니다. 애니메이션 축소판 제작이 활성화된 경우 절대 경로가 필요합니다.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>3D 자산의 통합 처리에 가장 많이 사용되는 CPU 수를 지정합니다.</p> <p>값이 높으면 인제션이 빨라지지만 AEM의 전체 응답 속도가 느려질 수 있습니다. 이 설정은 대략적입니다. 즉, 사용 가능한 CPU 코어 수로 정확도가 높아집니다.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Cloud Services 구성 설정 {#cloud-services-configuration-settings}

다음 설정에 대한 값은 Adobe 계정 관리자, 프로비저닝 전문가 또는 지원 담당자가 제공합니다.

| **경로** | **설명** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | Adobe AWS 계정의 계정 ID입니다. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | S3 전송 버킷의 이름 보통 `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | Adobe이 조직에 할당한 고유 ID입니다. AWS Cognito 사용자 ID로 사용됨. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | 이 customerId와 연결된 암호입니다. AWS Cognito 암호로 사용됨. |
| `/libs/settings/dam/v3D/services/aws/region` | 클라우드 서비스가 배포된 AWS 지역. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | 해당 AWS Cognito 사용자 풀 ID. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | dncr 전환 서비스에 대한 AWS Cognito 클라이언트 ID입니다. |

## 일반적인 처리 설정 {#common-processing-settings}

AEM의 **CRXDE Lite** (**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)에서 다음 구성에 액세스합니다.

| **경로** | **설명** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Maya 변환 및 렌더링을 위한 작업 폴더의 이름 및 위치입니다. 폴더가 없으면 자동으로 만들어집니다. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | 3ds 최대 전환에 대한 작업 폴더의 이름 및 위치입니다. 폴더가 없으면 자동으로 만들어집니다. |
| `/libs/settings/dam/v3D/settings/debugNative` | RapidRefine 렌더러를 사용하여 렌더링하고 포맷을 변환하는 동안 디버그 정보를 생성할 수 있도록 하려면 **[!UICONTROL true]** 로 설정합니다. |

## 렌더러 구성 {#renderer-configuration}

AEM의 **CRXDE Lite** (**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)에서 다음 구성에 액세스합니다.

| **경로** | **설명** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | true로 **[!UICONTROL 설정하고]** 미리 생성된 조명 맵을 사용할 수 없는 경우(invokeLightMapsOnIngest=false), 렌더링 중에 Rapid Refine 렌더러는 광원 맵을 만들어 렌더링 품질을 향상시킵니다. 이 설정은 렌더링 시간을 크게 늘릴 수 있습니다. [ **[!UICONTROL false]로]** 설정하면 이러한 상황에서 CPU 사용을 최소화하지만 렌더링 품질이 저하될 수 있습니다. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | 렌더러를 각각 **[!UICONTROL 활성화]** 또는 비활성화하려면 **[!UICONTROL true]** 또는 false로 설정합니다. |
| `/libs/settings/dam/v3D/renderers/*/Display` | 렌더링 패널의 렌더러 선택기에서 활성화된 렌더러에 대해 표시되는 문자열을 변경할 수 있습니다. |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | 3D 장면을 렌더링하는 데 가장 많이 사용되는 CPU 수를 지정합니다. 값이 높으면 렌더링 속도가 빨라지지만 AEM의 전체 응답 속도가 느려질 수 있습니다. 이 설정은 대략적입니다. 즉, 사용 가능한 CPU 코어 수로 정확도가 높아집니다. |

## 3D 에셋 미리 보기 설정 {#d-asset-preview-settings}

AEM의 **CRXDE Lite** (**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)에서 다음 구성에 액세스합니다.

| 경로 | 설명 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | 페이지 로드 시 자동 회전(자동 카메라 궤도)을 **[!UICONTROL 활성화]** 또는 비활성화하려면 **[!UICONTROL true]** 또는 false로 설정합니다. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | 재설정을 누른 후 자동 회전을 다시 시작하려면 **[!UICONTROL true]** 로 **[!UICONTROL 설정합니다]** . 자동 회전이 비활성화되면 무시됩니다. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | 속도(분당 레볼루션)와 자동 회전 방향을 지정합니다. 이 경우 오른쪽에서 왼쪽으로 표기하는 경우 음수 값과 왼쪽에서 오른쪽 회전 값이 사용됩니다. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | 터치 및 마우스 제스처에 대한 뷰어 응답의 점진적 페이드아웃으로 연속 연결을 비활성화하려면 **[!UICONTROL false]** 로 설정합니다. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | 로드 및 초기화 동안 선택적으로 3D 자산 미리 보기의 뷰포트를 덮을 수 있는 로드 커튼의 색상을 지정합니다. R,G,B 값, 각 색상 구성 요소가 0에서 255 사이의 값으로, |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | 이 값이 **[!UICONTROL true로 설정되면]**&#x200B;뷰어 초기화 후 부분이 점차 사라집니다. false로 **[!UICONTROL 설정하면]**&#x200B;로딩 및 초기화가 완료될 때까지 커튼이 불투명하게 유지됩니다. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | 3D 에셋 미리 보기에 대한 로드 커튼을 활성화하거나 비활성화하려면 **[!UICONTROL true]** 또는 **[!UICONTROL false로]** 설정합니다. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | 자동 회전이 활성화되고 활성화되면 카메라의 세로 위치가 3D 개체 높이를 기준으로 자동으로 조정됩니다. 0.5로 설정하면 카메라가 개체의 높이와 1/2로 세로로 배치되고, 이로 인해 시야에서 수평선이 세로로 가운데에 놓입니다. 값이 클수록 카메라가 개체를 내려다보고 렌더링된 수평선의 높이를 높이면 카메라가 개체를 위로 보고 수평선을 낮춥니다. |

## 3D 사이트 구성 요소 설정 {#d-sites-component-settings}

AEM의 **CRXDE Lite** (**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)에서 다음 구성에 액세스합니다.

| 경로 | 설명 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | 홈을 누른 후 자동 회전(자동 카메라 궤도)을 다시 활성화하려면 **[!UICONTROL true]** 로 설정합니다. 자동 회전이 비활성화되면 무시됩니다. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | 터치 및 마우스 제스처에 대한 뷰어 응답의 점진적 페이드아웃으로 연속 연결을 비활성화하려면 **[!UICONTROL false]** 로 설정합니다. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | 로드 중에 선택적으로 3D 사이트 구성 요소의 뷰포트를 덮을 수 있는 로드 커튼의 색상을 지정합니다. R,G,B 값, 각 색상 구성 요소가 0에서 255 사이의 값으로, |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | 이 **[!UICONTROL true]**&#x200B;로 설정하면 로드 및 초기화 후단에서 로드 커튼이 서서히 사라집니다. false로 **[!UICONTROL 설정하면]**&#x200B;로딩 및 초기화가 완료될 때까지 커튼이 불투명하게 유지됩니다. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | 3D 사이트 구성 요소의 로드 커튼을 **[!UICONTROL 활성화]** 또는 비활성화하려면 **[!UICONTROL true]** 또는false로 설정합니다. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | 자동 회전이 활성화되고 활성화되면 카메라의 세로 위치가 3D 개체 높이를 기준으로 자동으로 조정됩니다. 0.5로 설정하면 카메라가 개체의 높이와 1/2로 세로로 배치되고, 이로 인해 시야에서 수평선이 세로로 가운데에 놓입니다. 값이 클수록 카메라가 개체를 내려다보고 렌더링된 수평선의 높이를 높이면 카메라가 개체를 위로 보고 수평선을 낮춥니다. |

