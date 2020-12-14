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

기본 구성 설정은 일반적인 사용 사례에 적절하지만 일부 상황에서는 변경해야 할 수 있습니다.

다음 고급 구성 설정은 Maya 및 비 Maya 배포에 대한 AEM 3D 통합에 적용됩니다.

모든 설정은 AEM의 **CRXDE Lite**(**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)을 사용하여 액세스합니다.

>[!NOTE]
>
>패키지를 다시 설치하면 모든 설정이 기본값으로 재설정됩니다.

>[!CAUTION]
>
>아래 표에 나열되지 않은 설정을 편집하면 예기치 않은 프로그램 비헤이비어가 발생할 수 있습니다.

## 자산 유형 구성 {#asset-types-configuration}

AEM(**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)의 **CRXDE Lite**&#x200B;에서 다음 구성에 액세스합니다.

| 경로 | 설명 |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | 통합 중에 만든 중간 3D 형식의 파일 유형을 지정합니다. &#39;fbx&#39; 및 &#39;obj&#39; 파일 형식에는 비워 두고, Maya에서 사용하는 형식에는 &#39;fbx&#39;를 입력해야 합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | **[!UICONTROL assetTypes]** 목록에서 이 항목을 활성화하거나 비활성화하려면 true 또는 false로 설정합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | 이 자산 유형과 연결할 하나 이상의 쉼표로 구분된 파일 접미어 또는 파일 확장자를 지정합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | FBX 및 OBJ 파일 형식의 경우 `native`, Maya에서 사용하는 형식의 경우 `maya`이어야 합니다. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | 이 자산 유형의 MIME 형식을 지정합니다. Maya에서 활성화된 형식의 경우 `application/x-ext`을 사용하는 것이 좋습니다. 여기서 `ext`은 `Extension` 값으로 지정된 문자열입니다. |

## 통합 구성 {#ingestion-configuration}

AEM(**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)의 **CRXDE Lite**&#x200B;에서 다음 구성에 액세스합니다.

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
   <td>변환 및 렌더링 후 MayaWork 폴더에 임시 파일을 보관하려면 <strong>false</strong>로 설정합니다. Maya 변환 및 렌더링 문제를 디버깅할 때 유용할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>활성화되면 ImageMagick이 서버에 설치되고 magickPath가 구성됩니다. Rapid Refine은 카드 보기 및 기타 보기에서 축소판으로 사용되는 3D 객체에 대한 간단한 애니메이션을 만드는 데 사용됩니다.</p> <p>애니메이션을 만드는 데는 통합 프로세스 동안 상당한 CPU 리소스가 소모됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>통합 시 조명 맵을 자동으로 만들 수 있습니다. 자동 라이트 맵 생성을 비활성화하려면 <strong>false</strong>로 설정;Rapid Refine을 사용하면 미리 보거나 렌더링하는 데 필요한 품질이 저하되는 비용 덕분에 CPU 사용량을 크게 줄일 수 있습니다. Maya를 사용한 렌더링에는 영향을 주지 않습니다.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p><strong>true</strong>(기본값)로 설정하면 필요한 경우 객체의 모든 부분이 지표 평면(y=0)보다 높게 이동됩니다.</p> <p><strong>false</strong>(기본값)로 설정하면 객체가 다시 배치되지 않고 스테이지의 지표 평면에 의해 부분적으로 숨겨질 수 있습니다. (Rapid Refine을 사용한 미리 보기 및 렌더링에만 적용됩니다.) 그러나 Maya와의 렌더링에는 영향을 주지 않습니다. <strong>true</strong>로 설정하면 Maya에서 객체의 수직 위치가 미리 보기나 Rapid Refine으로 렌더링할 때와 다를 수 있습니다.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>ImageMagick 변환 유틸리티의 경로와 이름입니다. 애니메이션 축소판 제작이 활성화된 경우 절대 경로가 필요합니다.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>3D 자산의 통합 처리에 가장 많이 사용되는 CPU 수를 지정합니다.</p> <p>값이 높을수록 인제션의 속도가 빨라지지만 AEM의 전반적인 응답 속도가 느려질 수 있습니다. 이 설정은 근사합니다. 즉, 사용 가능한 CPU 코어 수로 정확도가 높아집니다.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Cloud Services 구성 설정 {#cloud-services-configuration-settings}

다음 설정에 대한 값은 Adobe 계정 관리자, 프로비저닝 전문가 또는 지원 담당자가 제공합니다.

| **경로** | **설명** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | Adobe AWS 계정의 계정 ID입니다. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | S3 전송 버켓의 이름;일반적으로 `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | Adobe이 조직에 할당한 고유 ID입니다. AWS Cognito 사용자 ID로 사용됩니다. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | 이 customerId와 연결된 암호입니다. AWS Cognito 암호로 사용됩니다. |
| `/libs/settings/dam/v3D/services/aws/region` | 클라우드 서비스가 배포된 AWS 지역. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | 해당 AWS Cognito 사용자 풀 ID입니다. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | dncr 전환 서비스에 대한 AWS Cognito 클라이언트 ID입니다. |

## 일반적인 처리 설정 {#common-processing-settings}

AEM(**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)의 **CRXDE Lite**&#x200B;에서 다음 구성에 액세스합니다.

| **경로** | **설명** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Maya 변환 및 렌더링을 위한 작업 폴더의 이름 및 위치입니다. 폴더가 없으면 자동으로 만들어집니다. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | 3ds 최대 변환에 대한 작업 폴더의 이름 및 위치입니다. 폴더가 없으면 자동으로 만들어집니다. |
| `/libs/settings/dam/v3D/settings/debugNative` | 형식을 변환하고 RapidRefine 렌더러를 사용하여 렌더링하는 동안 디버그 정보를 만들 수 있도록 하려면 **[!UICONTROL true]**&#x200B;로 설정합니다. |

## 렌더러 구성 {#renderer-configuration}

AEM(**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)의 **CRXDE Lite**&#x200B;에서 다음 구성에 액세스합니다.

| **경로** | **설명** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | **[!UICONTROL true]**&#x200B;로 설정되고 미리 생성된 조명 맵을 사용할 수 없는 경우(invokeLightMapsOnIngest=false) 렌더링 중에 Rapid Refine 렌더러는 렌더링 품질을 개선하기 위해 광원 맵을 만듭니다. 이 설정을 사용하면 렌더링 시간이 상당히 늘어날 수 있습니다. **[!UICONTROL false]**&#x200B;로 설정하면 이러한 상황에서 CPU 사용이 최소화되지만 렌더링 품질이 저하될 수 있습니다. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | 렌더러를 각각 사용하거나 사용하지 않으려면 **[!UICONTROL true]** 또는 **[!UICONTROL false]**&#x200B;로 설정합니다. |
| `/libs/settings/dam/v3D/renderers/*/Display` | [렌더링] 패널의 [렌더러] 선택기에서 활성화된 렌더러에 대해 표시되는 문자열을 변경할 수 있습니다. |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | 3D 장면을 렌더링하는 데 가장 많이 사용되는 CPU 수를 지정합니다. 값이 높을수록 렌더링 속도가 빨라지지만 AEM의 전체 응답 속도가 느려질 수 있습니다. 이 설정은 근사합니다. 즉, 사용 가능한 CPU 코어 수로 정확도가 높아집니다. |

## 3D 자산 미리 보기 설정 {#d-asset-preview-settings}

AEM(**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)의 **CRXDE Lite**&#x200B;에서 다음 구성에 액세스합니다.

| 경로 | 설명 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | 페이지 로드 시 자동 회전(자동 카메라 궤도)을 활성화하거나 비활성화하려면 **[!UICONTROL true]** 또는 **[!UICONTROL false]**&#x200B;로 설정합니다. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | **[!UICONTROL 재설정]**&#x200B;을 누른 후 자동 회전을 다시 시작하려면 **[!UICONTROL true]**&#x200B;로 설정합니다. 자동 회전이 비활성화된 경우 무시됩니다. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | 오른쪽에서 왼쪽으로 회전 및 왼쪽에서 오른쪽 회전 값을 음수로 하여 속도(분당 레볼루션)와 자동 회전 방향을 지정합니다. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | 터치 및 마우스 제스처에 대한 뷰어 응답의 점진적 페이드아웃으로 계속을 비활성화하려면 **[!UICONTROL false]**&#x200B;로 설정합니다. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | 로드 및 초기화 동안 선택적으로 3D 자산 미리 보기의 뷰포트를 덮을 수 있는 로드 커튼 색상을 지정합니다. R,G,B 값으로, 각 색상 구성 요소가 0에서 255 사이의 범위에 있습니다. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | **[!UICONTROL true]**&#x200B;로 설정하면 뷰어 초기화의 후부분이 서서히 사라집니다. **[!UICONTROL false]**&#x200B;로 설정하면 로드 및 초기화가 완료될 때까지 커튼이 불투명하게 유지됩니다. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | 3D 자산 미리 보기에 대한 로드 커튼을 활성화하거나 비활성화하려면 **[!UICONTROL true]** 또는 **[!UICONTROL false]**&#x200B;로 설정합니다. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | 자동 회전이 활성화되고 활성화되면 3D 개체의 높이를 기준으로 카메라의 세로 위치가 자동으로 조정됩니다. 0.5로 설정하면 카메라가 개체의 높이를 1/2로 세로로 배치되고, 이로 인해 시야에서 수평선이 세로로 중앙에 배치됩니다. 값이 클수록 카메라에서 개체를 아래로 보고 렌더링된 수평선의 높이를 늘립니다. 값이 작을수록 카메라가 개체를 위로 보고 수평선을 낮춥니다. |

## 3D 사이트 구성 요소 설정 {#d-sites-component-settings}

AEM(**[!UICONTROL 도구 > 일반 > CRXDE Lite]**)의 **CRXDE Lite**&#x200B;에서 다음 구성에 액세스합니다.

| 경로 | 설명 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | 홈을 누른 후 자동 회전(자동 카메라 궤도)을 다시 활성화하려면 **[!UICONTROL true]**&#x200B;로 설정합니다. 자동 회전이 비활성화된 경우 무시됩니다. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | 터치 및 마우스 제스처에 대한 뷰어 응답의 점진적 페이드아웃으로 계속을 비활성화하려면 **[!UICONTROL false]**&#x200B;로 설정합니다. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | 로드 중 3D 사이트 구성 요소의 뷰포트를 선택적으로 덮을 수 있는 로드 커튼 색상을 지정합니다. R,G,B 값으로, 각 색상 구성 요소가 0에서 255 사이의 범위에 있습니다. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | **[!UICONTROL true]**&#x200B;로 설정하면 로드 및 초기화 후부분이 서서히 사라집니다. **[!UICONTROL false]**&#x200B;로 설정하면 로드 및 초기화가 완료될 때까지 커튼이 불투명하게 유지됩니다. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | 3D 사이트 구성 요소의 로드 커튼을 활성화 또는 비활성화하려면 **[!UICONTROL true]** 또는 **[!UICONTROL false]**&#x200B;로 설정합니다. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | 자동 회전이 활성화되고 활성화되면 3D 개체의 높이를 기준으로 카메라의 세로 위치가 자동으로 조정됩니다. 0.5로 설정하면 카메라가 개체의 높이를 1/2로 세로로 배치되고, 이로 인해 시야에서 수평선이 세로로 중앙에 배치됩니다. 값이 클수록 카메라에서 개체를 아래로 보고 렌더링된 수평선의 높이를 늘립니다. 값이 작을수록 카메라가 개체를 위로 보고 수평선을 낮춥니다. |

