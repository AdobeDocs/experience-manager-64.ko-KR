---
title: AEM 3D 에셋 작업
seo-title: 3D 자산 작업
description: AEM 3D에서 3D 에셋을 사용하여 작업하는 방법 살펴보기
seo-description: AEM 3D에서 3D 에셋을 사용하여 작업하는 방법 살펴보기
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 5%

---


# Working with AEM 3D assets {#working-with-d-assets}

>[!IMPORTANT]
>
>AEM 6.4의 AEM 3D는 더 이상 지원되지 않습니다. Adobe에서는 AEM의 3D 자산 기능을 Cloud Service [또는](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) [AEM 6.5.3 이상으로 사용하는 것이 좋습니다.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

AEM 3D(Adobe Experience Manager 3D)를 사용하면 3D 컨텐츠를 업로드, 관리, 확인 및 렌더링할 수 있습니다. 확인 및 렌더링에 대한 지원은 개별 개체를 위해 최적화되어 있습니다.

[AEM 3D 릴리스 노트](/help/release-notes/aem3d-release-notes.md)를 참조하십시오.

[AEM 3D 설치 및 구성](install-config-3d.md)을 참조하십시오.

## AEM 3D의 모델 및 단계 정보 {#about-models-and-stages-in-aem-d}

AEM 3D를 사용하면 단계라는 미리 정의된 환경에서 고품질의 정적 독립 실행형 3D 모델을 보고 렌더링할 수 있습니다. 기본적으로 스테이지는 3D 장면에 대해 &quot;조명&quot;을 제공하고 Autodesk® Maya® 또는 Autodesk 3ds Max®와 같은 기본 애플리케이션에서 렌더링하기 위한 설정을 제공합니다. 또한 스테이지에 미리 정의된 카메라, 배경 및 지표 평면 도형이 선택적으로 포함될 수 있습니다.

조명이 포함된 업로드된 3D 파일은 스테이지로 간주됩니다. 자산 세부 사항 페이지에서 자산을 열어 이러한 자산을 간단한 3D 개체로 되돌릴 수 있습니다. 속성 **[!UICONTROL 보기를]**&#x200B;누른 다음 **[!UICONTROL 기본]** 탭을 누릅니다. 메타데이터 머리글 아래의 자산 클래스 드롭다운 목록에서 **[!UICONTROL 3D 개체를 선택합니다]**.

AEM 3D에서 사용할 3D 모델을 만들 때는 다음 사항에 주의하십시오.

* 3D 모델 파일은 배경, 지표 평면, 장면 조명 또는 카메라가 없는 하나의 개체만 포함해야 합니다.
* 지표 평면 위에 모델을 배치합니다. 이 위치는 지표 평면을 제공하는 스테이지로 보거나 렌더링할 때 특히 중요합니다. Rapid Refine으로 렌더링하거나 미리 볼 때 개체가 지표 평면 위로 이동되도록 하는 구성 설정을 사용할 수 있으며, 기본적으로 활성화되어 있습니다. 이 설정은 타사 렌더링(예: Maya의 방법)을 사용한 렌더링에는 영향을 주지 않으므로 지표 평면 위에 있지 않은 개체는 부분적으로 숨겨질 수 있습니다.
* 좌표계 원점(0,0,0)을 자연스럽게 가운데에 있도록 모델을 배치합니다. 이를 통해 인터랙티브한 시청 경험을 제공할 수 있습니다.
* 텍스처 맵 외에 외부 파일 참조가 지원됩니다. 따라서, AEM에 업로드하기 전에 기본 모델 파일에 참조되는 컨텐트를 포함시켜야 합니다.

   [AEM에서의 3D 자산 업로드 및 처리 정보](upload-processing-3d-assets.md)를 참조하십시오.

* 일반 장면 조명은 스테이지에서 제공합니다. 따라서 Adobe에서는 3D 모델 파일에 조명을 포함시키는 것이 권장되지 않습니다. 모델에 조명을 포함할 수 있습니다. 하지만, 모델에만 해당되어야 합니다. 예를 들어 다른 부분으로 가려져 있는 개체의 일부를 밝게 하려면 추가 조명을 포함해야 할 수도 있습니다. 따라서 무대 전등만으로 충분히 볼 수 있는 것은 아닙니다.

## AEM 3D에서 지원되는 파일 {#supported-files-in-aem-d}

일반적인 3D 자산에는 기본 모델 파일이 있으며 참조되는 파일이 하나 이상 없습니다. 참조되는 파일에는 텍스처 맵 또는 **IBL(이미지 기반 조명) 이미지와 같은** 이미지가 포함됩니다.

### 기본 3D 모델 파일 정보 {#about-the-primary-d-model-file}

기본 3D 모델 파일에는 모델 서피스에 적용되는 실제 3D 모델 형상과 (기본) 재질에 대한 정의가 포함되어 있습니다. AEM 3D는 다음과 같은 기본 3D 모델 파일 포맷을 지원합니다.

* Wavefront OBJ 파일 형식(`.obj`)

   OBJ 형식에는 하나 이상의 별도의 외부 MTL 파일(Material Template Library)(`.mtl`)이 필요합니다.

* Autodesk FBX(Filmbox) 파일 포맷(`.fbx`)

   Autodesk 3D 파일 교환 형식;바이너리 및 ASCII 형식 모두 사용할 수 있습니다.

   타사 애플리케이션에서 FBX 파일을 만들 때 Adobe은 다음 구성 설정을 권장합니다(아래 표 참조). 이러한 설정을 사용하면 AEM에서 사용하려는 3D 파일에 대한 최상의 결과를 얻을 수 있습니다. 옵션 이름은 [Autodesk Maya FBX 내보내기 옵션] **[!UICONTROL 대화 상자에서]** 가져옵니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Autodesk Maya FBX 내보내기 대화 상자의 옵션</strong></td> 
   <td><strong>설명</strong></td> 
  </tr> 
  <tr> 
   <td>참조 유지<br /> </td> 
   <td><p>선택 취소.</p> <p>AEM 3D는 현재 외부 참조를 지원하지 않습니다.</p> </td> 
  </tr> 
  <tr> 
   <td>매끄러운 메쉬<br /> </td> 
   <td>선택.</td> 
  </tr> 
  <tr> 
   <td>NURBS 표면을</td> 
   <td><strong>Software Render Mesh</strong></td> 
  </tr> 
  <tr> 
   <td>애니메이션</td> 
   <td><p>선택 또는 선택 취소합니다.</p> <p>이 옵션을 선택하면 AEM 3D는 파일의 애니메이션 정보를 무시합니다.</p> </td> 
  </tr> 
  <tr> 
   <td>카메라</td> 
   <td><p>3D 단계 <strong>에 대해 선택합니다</strong>.</p> <p>3D 모델의 경우 선택 취소합니다.</p> </td> 
  </tr> 
  <tr> 
   <td>조명</td> 
   <td><p>3D 단계 <strong>에 대해 선택합니다</strong>.</p> <p>3D 모델의 경우 <strong>선택 취소합니다</strong>.</p> </td> 
  </tr> 
  <tr> 
   <td>판매량 - 자동</td> 
   <td>선택. AEM 3D를 가져올 때 전환됩니다.</td> 
  </tr> 
  <tr> 
   <td>축 변환 - 위쪽 축</td> 
   <td><p><strong>Y-up</strong></p> <p>Y-up을 사용하면 Maya에서 내보낼 때 일관된 결과를 얻을 수 있으며 이 AEM 3D 릴리스에서 FBX 파일에 대해 선호하는 좌표 시스템입니다.</p> </td> 
  </tr> 
  <tr> 
   <td>미디어 포함</td> 
   <td>두 옵션이 모두 지원됩니다. 임베드된 미디어를 선택한 경우 AEM 3D는 임베드된 미디어를 모델 파일과 동일한 이름의 인접한 폴더에 <code>.fbm</code> 추출합니다.</td> 
  </tr> 
  <tr> 
   <td>FBX 파일 형식 - 유형</td> 
   <td>바이너리 <strong></strong><strong>또는 </strong>ASCII가 모두 지원됩니다.</td> 
  </tr> 
  <tr> 
   <td>FBX 파일 형식 - 버전</td> 
   <td>FBX 2014/2015가 권장됩니다. 다른 버전도 문제 없습니다.</td> 
  </tr> 
 </tbody> 
</table>

AEM 제작 서버에 Autodesk Maya가 설치 및 구성된 경우 다음과 같은 추가 파일 포맷이 지원됩니다.

* Autodesk Maya

   ASCII `.ma` 및 바이너리 `.mb` 포맷

* `Jupiter Tesselation (ISO 14306-1).jt`.

   업계 표준의 CAD 데이터 교환, 공동 작업 및 제품 시각화 형식입니다.

### 텍스처 맵 파일 지원 {#support-for-texture-map-files}

3D 모델 파일의 재료 정의는 텍스처 맵을 제공하는 외부 이미지 파일에 대한 참조를 포함할 수 있습니다. AEM 3D는 다음과 같은 유형의 텍스처 맵 파일을 지원합니다.

* 확산 색상 텍스처
* 반사 색상 텍스처
* 주변 색상 텍스처
* 변위 맵(범프 맵이라고도 함)
* 표준 맵
* 불투명도 맵
* 거칠음 맵(광택, 반사 또는 코사인 파워 맵이라고도 함)

기본 3D 모델 파일의 재료는 AEM 3D에서 무시되는 다른 유형의 맵을 참조할 수 있습니다.

### IBL(이미지 기반 조명) 이미지 {#ibl-image-based-lighting-images}

스테이지를 정의하는 3D 모델 파일은 단일 IBL 환경 이미지를 참조할 수 있습니다. 현재 AEM 3D는 확산 IBL 및 반사 시 위도/경도 포맷의 32비트 TIFF 이미지만 지원합니다. 구형 장면 배경의 경우 8비트 RGB 이미지도 지원됩니다.

See [About working with IBL stages](working-with-ibl-stages.md).

>[!NOTE]
>
>기본 3D 모델 파일에 있는 위에서 설명한 파일 참조와 다른 파일 참조는 현재 무시됩니다. AEM 3D는 보조 3D 모델 파일에 대한 참조를 지원하지 않습니다.
Y-up은 이번 릴리스에서 FBX 파일에 대해 권장되는 좌표계입니다.

## 기본 3D 모델 파일의 재료 음영 {#material-shading-in-a-primary-d-model-file}

원본 기본 모델 파일에는 블린, 램버트 또는 절차용 섀더와 같은 쉐이더에 사용되는 재료 정의가 포함될 수 있습니다. 잠재적으로 복잡할 수 있는 이러한 자료는 해당 기본 응용 프로그램(예: Autodesk Maya)을 사용하여 렌더링하는 경우에만 지원됩니다.

보기 목적으로 또는 기본 Rapid Refine™ 렌더러를 사용하여 렌더링할 때 모든 재질이 단순화되거나 대체되며, 둘 다 Phony와 같은 쉐이더와 함께 사용할 수 있습니다. 이 셰이더는 제한된 속성 집합을 지원합니다. 재료 정의의 다른 속성은 무시됩니다.

[3D 자산 보기](viewing-3d-assets.md)를 참조하십시오.

[3D 자산 렌더링](rendering-3d-assets.md)을 참조하십시오.

## 기본 3D 모델 파일의 재료 이름 지정 {#naming-materials-in-a-primary-d-model-file}

서피스 *(* surface)는 동일한 재질로 덮여있는 3D 모델의 서피스 영역으로 정의됩니다. 이 물질은 표면의 이름도 제공합니다. 따라서, Adobe은 기본 3D 모델 파일에 포함된 자료의 이름을 그에 따라 지정하는 것이 좋습니다. 예를 들어 &quot;Body&quot;, &quot;Windows&quot;, &quot;Ties&quot; 또는 &quot;Rims&quot;와 같은 특정 이름을 사용하는 것이 &quot;Red&quot;, &quot;Glass&quot;, &quot;Rubber&quot;, &quot;Aluminum&quot;과 같은 모호한 이름을 사용하는 것이 좋습니다.

