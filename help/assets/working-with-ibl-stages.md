---
title: IBL 단계 작업 정보
seo-title: IBL 단계 작업 정보
description: AEM 3D는 대화형 보기와 내장 Adobe Rapid Refine™ 렌더러 및 타사 렌더러를 통한 렌더링을 위해 IBL(이미지 기반 조명)을 지원합니다.
seo-description: AEM 3D는 대화형 보기와 내장 Adobe Rapid Refine™ 렌더러 및 타사 렌더러를 통한 렌더링을 위해 IBL(이미지 기반 조명)을 지원합니다.
uuid: 495ba9cc-02f5-4ce5-9503-9f61ca5482db
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 658ff671-16b9-41bd-ba24-b77a32b3346b
translation-type: tm+mt
source-git-commit: 5964edfadf597652f754ca3c64343b0b90e40796
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 54%

---


# IBL 단계 작업 정보 {#about-working-with-ibl-stages}

AEM 3D는 대화형 보기와 내장 Adobe Rapid Refine™ 렌더러 및 타사 렌더러를 통한 렌더링을 위해 IBL(이미지 기반 조명)을 지원합니다. Autodesk® Maya® 또는 Autodesk® 3ds Max®와 같은 일반적인 작성 도구를 사용하여 IBL 단계를 만들 수 있습니다.

## IBL용 이미지 {#images-for-ibl}

이미지 기반 조명에 사용되는 이미지에는 최상의 결과를 얻기 위해 HDR(높은 동적 범위)이 적용되어야 합니다. 이러한 이미지는 구형 매핑의 위도/경도 형식으로 전체 환경을 나타내야 합니다.

현재, AEM 3D는 32비트 TIFF만 지원합니다. 필요한 경우 Adobe Photoshop이나 유사한 도구를 사용하여 Adobe Photoshop TIFF 내보내기 대화 상자의 다음 설정을 통해 HDR 이미지를 TIFF로 변환하십시오.

* **[!UICONTROL 비트 심도]** - 32비트(부동)
* **[!UICONTROL 픽셀 순서]** - 인터리브(RGBRGB)
* **[!UICONTROL 이미지 압축]** - LZW
* **[!UICONTROL 바이트 순서** - IBM PC

종종 IBL 단계는 단일 HDR 이미지로 충분하지만, AEM 3D는 최대 3개의 별도 이미지를 허용하여 IBL 효과를 추가로 제어할 수 있도록 합니다.

* **확산 조명 환경 이미지** - 이 유형의 이미지는 HDR 이미지여야 하지만, 확산 조명에 사용하기 전에 과도하게 필터링되므로 상대적으로 작을 수 있습니다.
* **반사 환경 이미지** - 이 유형의 이미지는 개체 표면에서 반사를 만드는 데 사용됩니다. 반사의 원하는 품질과 선명도를 제공하는 크기와 해상도를 갖는 표준 8비트 RGB 이미지일 수 있습니다. HDR 이미지가 지정된 경우 AEM 3D는 독점 알고리즘을 사용하기 전에 8비트 RGB로 변환합니다.
* **배경 환경 이미지** - 이 유형의 이미지는 배경으로 사용됩니다. 표준 8비트 RGB 이미지일 수 있으며, 단계 배경에 필요한 상세 크기/해상도/수준이어야 합니다. HDR 이미지가 지정된 경우 AEM 3D는 독점 알고리즘을 사용하여 8비트 RGB로 변환합니다.

>[!NOTE]
>
>특정 IBL 이미지에서는 변환 알고리즘이 어려울 수 있습니다. 이러한 문제는 미리 보기를 사용하거나 Rapid Refine으로 렌더링할 때 배경이 너무 밝거나, 과도하게 포화된 경우에 나타날 수 있습니다. 이러한 경우, Photoshop이나 유사한 도구를 사용하여 IBL 이미지를 8비트 RGB 이미지로 수동으로 변환하는 것이 좋습니다. 이 이미지를 별도로 업로드한 후 단계에 배경 환경 이미지로 연결하십시오. 확산 조명 및 반사 환경 이미지는 항상 32비트 TIFF여야 합니다.

## IBL 단계 모양 조절 {#adjusting-the-ibl-stage-appearance}

다음 단계 속성을 사용하여 IBL 단계의 모양을 미세 조정할 수 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>속성</strong><br /> </td> 
   <td><strong>설명</strong></td> 
  </tr> 
  <tr> 
   <td>IBL Sun 세부 사항</td> 
   <td><p>태양을 시뮬레이션하는 보조 광원의 방향과 강도를 조정할 수 있습니다. <span class="diff-html-added">이 광원은 조명 밝기를 늘리고 개체 그림자가 지면 평면에 투사되도록 합니다. 그림자 투사는 Rapid Refine으로 렌더링할 때와 Google Chrome에서 미리 보기를 수행할 때 지원되지만, 다른 브라우저에서는 현재 지원되지 않습니다.</span></p> 
    <ul> 
     <li><strong>위도</strong> - 태양 광원의 수직 위치(<code>0.0</code>-<code>1.0</code>)입니다.<br /> 의 설정 <code>0.0</code> 은 수평선(확산 조명 환경 이미지의 수직 중심)에 있습니다. <code>1.0</code> 는 천정(확산 조명 환경 이미지의 위쪽 가장자리)에 있습니다.</li> 
     <li><strong>긴</strong> - 태양 광원의 가로 위치(<code>0.0</code>-<code>1.0</code>)입니다.<br /> 0.0 설정은 왼쪽에 해당합니다.1.0은 확산 조명 환경 이미지의 오른쪽 가장자리에 해당합니다.<br /> </li> 
     <li><strong>밝기</strong> - 태양 광원의 밝기입니다. 태양 광원을 밝게 하려면 이 값을 늘리고, 어둡게 하려면 이 값을 줄입니다. <br /> 보조 조명을 <code>0</code> 비활성화하고 그림자 표시를 비활성화합니다. 이 매개 변수는 환경 반사에 영향을 미치지 않습니다.<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>IBL 카메라 높이</td> 
   <td>IBL 배경이 수평선 근처에서 왜곡되어 나타나면 이 속성을 조정하여 왜곡을 줄이거나 없앨 수 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td>환경 조명</td> 
   <td><p><span class="diff-html-added">확산 조명을 제어할 수 있습니다. 확산 조명 환경 이미지가 비정상적으로 밝거나 어두운 경우(예: 야경) 이 속성을 수동으로 조정하여 조명 밝기를 수정해야 할 수 있습니다.</span></p> 
    <ul> 
     <li><strong>r, g, b</strong> - 현재 사용되지 않습니다.</li> 
     <li><strong>밝기</strong> - <span class="diff-html-added">밝기 배수입니다. 이 값을 늘리거나 줄이면 전체 조명 강도(기본 IBL 조명 및 태양 광원의 밝기)가 높아지거나 감소합니다.</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## IBL 스테이지의 구형 배경 지름 증가 {#increasing-the-spherical-background-diameter-of-an-ibl-stage}

IBL 단계는 기본적으로 직경이 20m인 구형 배경 이미지를 사용합니다. 이런 단계는 10m의 물체에 잘 작용한다. 그러나 큰 개체를 표시하는 경우 IBL 스테이지의 구형 배경 지름을 늘릴 수 있습니다.

**IBL 스테이지의 구형 배경 직경을 증가시키려면**

1. CRXDE Lite에서 늘릴 구형 배경 지름의 스테이지로 이동합니다. 예,

   `/content/dam/test3d/stage-helipad.fbx`

1. 스테이지 노드를 다음으로 `jcr:content/metadata`확장합니다.
1. 속성을 원하는 밀리미터 값 `dam:gPlaneRadius` 으로 설정합니다.

   렌더링 효율성을 위해 이 값을 스테이지에 표시하려는 가장 큰 개체의 약 가장 큰 차원으로 제한하는 것이 좋습니다.

   예를 들어 길이가 20m인 제트기 모델은 잘 표시됩니다 `dam:gPlaneRadius=20000`.

1. CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장을 탭합니다]**.

