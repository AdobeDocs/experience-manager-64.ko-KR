---
title: 3D 자산 작업
seo-title: 3D 자산 작업
description: AEM 3D에서 3D 자산으로 작업하는 방법 학습
seo-description: AEM 3D에서 3D 자산으로 작업하는 방법 학습
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 7c850ed0d20dd2ba2626242c67ba190e371f049f

---


# 3D 자산 작업 {#working-with-d-assets}

AEM 3D(Adobe Experience Manager 3D)를 사용하면 3D 컨텐츠를 업로드, 관리, 확인 및 렌더링할 수 있습니다. 확인 및 렌더링에 대한 지원은 개별 개체를 위해 최적화되어 있습니다.

[AEM 3D 릴리스 노트](/help/release-notes/aem3d-release-notes.md)를 참조하십시오.

[AEM 3D 설치 및 구성](install-config-3d.md)을 참조하십시오.

## AEM 3D의 모델 및 단계 정보 {#about-models-and-stages-in-aem-d}

AEM 3D를 사용하면 스테이지라는 미리 정의된 환경에서 고품질의 정적 독립 실행형 3D 모델을 보고 렌더링할 수 있습니다. 기본적으로 스테이지는 3D 장면에 대한 &quot;조명&quot;과 Autodesk® Maya® 또는 Autodesk 3ds Max®와 같은 기본 애플리케이션에서 렌더링하기 위한 설정을 제공합니다. 또한 스테이지에 사전 정의된 카메라, 배경 및 지표 평면 도형이 선택적으로 포함될 수 있습니다.

조명이 포함된 업로드된 3D 파일은 스테이지로 간주됩니다. 자산 세부 사항 페이지에서 자산을 열어 이러한 자산을 간단한 3D 개체로 되돌릴 수 있습니다. 속성 **[!UICONTROL 보기를]**&#x200B;누른 다음 기본 **[!UICONTROL 탭을]** 누릅니다. 메타데이터 머리글의 자산 클래스 드롭다운 목록에서 **[!UICONTROL 3D 개체를]**&#x200B;선택합니다.

AEM 3D에서 사용할 3D 모델을 만들 때는 다음 사항에 유의하십시오.

* 3D 모델 파일에는 배경, 지표 평면, 장면 조명 또는 카메라가 없는 하나의 오브젝트만 들어 있어야 합니다.
* 지표 평면 위에 모델을 배치합니다. 이 위치는 지표 평면을 제공하는 스테이지로 보거나 렌더링할 때 특히 중요합니다. Rapid Refine으로 미리 보거나 렌더링할 때 지표 평면 위로 개체를 이동시키는 구성 설정을 사용할 수 있으며(기본적으로 활성화됨) 이 설정은 타사 렌더러로 렌더링하는 데 영향을 주지 않으므로(예: Maya의 경우) 지표 평면 위에 있지 않은 개체는 부분적으로 숨겨질 수 있습니다.
* 좌표계 원점(0,0,0)을 합리적으로 가운데에 배치하도록 모델을 배치합니다. 이렇게 하면 인터랙티브한 보기 환경이 제공됩니다.
* 텍스처 맵 외에 외부 파일 참조가 지원됩니다. 따라서 AEM에 업로드하기 전에 기본 모델 파일에 참조된 컨텐트를 포함시켜야 합니다.

   [AEM에서의 3D 자산 업로드 및 처리 정보](upload-processing-3d-assets.md)를 참조하십시오.

* 일반 장면 조명은 스테이지에서 제공합니다. 따라서 Adobe에서는 3D 모델 파일에 조명을 포함시키는 것이 권장되지 않습니다. 모델에 조명을 포함할 수 있습니다. 그러나 모델에만 해당되어야 합니다. 예를 들어 다른 부분으로 가려진 개체의 일부를 밝게 하려면 추가 조명을 포함해야 할 수 있습니다. 따라서, 이것은 단지 무대 전등에서만 충분히 볼 수 없을 것입니다.

## AEM 3D에서 지원되는 파일 {#supported-files-in-aem-d}

일반적인 3D 자산에는 기본 모델 파일이 있으며 참조된 파일이 없습니다. 참조된 파일에는 텍스처 맵 또는 IBL(이미지 **기반 조명)** 이미지와 같은 것이 포함되어 있습니다.

### 기본 3D 모델 파일 정보 {#about-the-primary-d-model-file}

기본 3D 모델 파일에는 실제 3D 모델 형상과 모델 서피스에 적용되는 (기본) 재질에 대한 정의가 포함되어 있습니다. AEM 3D는 다음과 같은 기본 3D 모델 파일 형식을 지원합니다.

* Wavefront OBJ 파일 포맷(`.obj`)

   OBJ 형식에는 하나 이상의 별도의 외부 MTL 파일(재료 템플릿 라이브러리)(`.mtl`)이 필요합니다.

* Autodesk FBX(Filmbox) 파일 포맷(`.fbx`)

   Autodesk 3D 파일 교환 형식;이진 및 ASCII 형식 모두 사용할 수 있습니다.

   타사 애플리케이션에서 FBX 파일을 만들 때 다음 구성 설정을 사용하는 것이 좋습니다(아래 표 참조). 이러한 설정을 사용하면 AEM에서 사용하려는 3D 파일에 대한 최상의 결과를 얻을 수 있습니다. 옵션 이름은 Autodesk Maya FBX 내보내기 **[!UICONTROL 옵션 대화 상자에서]** 가져옵니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Autodesk Maya FBX 내보내기 대화 상자의 옵션</strong></td> 
   <td><strong>설명</strong></td> 
  </tr> 
  <tr> 
   <td>참조 유지<br /> </td> 
   <td><p>선택 취소.</p> <p>현재 AEM 3D는 외부 참조를 지원하지 않습니다.</p> </td> 
  </tr> 
  <tr> 
   <td>부드러운 메시<br /> </td> 
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
   <td><p>3D <strong>단계를</strong>선택합니다.</p> <p>3D 모델의 경우 선택 취소합니다.</p> </td> 
  </tr> 
  <tr> 
   <td>조명</td> 
   <td><p>3D <strong>단계를</strong>선택합니다.</p> <p>3D 모델의 <strong>경우</strong>선택 취소합니다.</p> </td> 
  </tr> 
  <tr> 
   <td>판매량 - 자동</td> 
   <td>선택. 가져올 때 AEM 3D가 변환됩니다.</td> 
  </tr> 
  <tr> 
   <td>축 변환 - 위쪽 축</td> 
   <td><p><strong>Y-up</strong></p> <p>Y-up은 Maya에서 내보낼 때 일관된 결과를 제공하며 이 AEM 3D 릴리스에서 FBX 파일에 대해 선호하는 좌표계입니다.</p> </td> 
  </tr> 
  <tr> 
   <td>미디어 포함</td> 
   <td>두 옵션이 모두 지원됩니다. 임베드된 미디어를 선택한 경우 AEM 3D는 임베드된 미디어를 모델 파일과 이름이 같은 인접한 폴더에 <code>.fbm</code> 추출합니다.</td> 
  </tr> 
  <tr> 
   <td>FBX 파일 포맷 - 유형</td> 
   <td>이진 <strong>또는 ASCII </strong>가 모두 <strong></strong>지원됩니다.</td> 
  </tr> 
  <tr> 
   <td>FBX 파일 포맷 - 버전</td> 
   <td>FBX 2014/2015가 권장됩니다. 다른 버전도 문제 없습니다.</td> 
  </tr> 
 </tbody> 
</table>

AEM 작성 서버에 Autodesk Maya가 설치 및 구성된 경우 다음과 같은 추가 파일 형식이 지원됩니다.

* Autodesk Maya

   ASCII `.ma` 및 바이너리 `.mb` 포맷

* `Jupiter Tesselation (ISO 14306-1).jt`.

   업계 표준 CAD 데이터 교환, 공동 작업 및 제품 시각화 형식

### 텍스처 맵 파일 지원 {#support-for-texture-map-files}

3D 모델 파일의 재료 정의에는 텍스처 맵을 제공하는 외부 이미지 파일에 대한 참조가 포함될 수 있습니다. AEM 3D는 다음 유형의 텍스처 맵 파일을 지원합니다.

* 확산 색상 텍스처
* 반사 색상 텍스처
* 주변 색상 텍스처
* 변위 맵(범프 맵이라고도 함)
* 표준 맵
* 불투명도 맵
* 거칠음 맵(광택, 반사도 또는 코사인 전원 맵이라고도 함)

기본 3D 모델 파일의 재료는 AEM 3D에서 무시되는 다른 유형의 맵을 참조할 수 있습니다.

### IBL(이미지 기반 조명) 이미지 {#ibl-image-based-lighting-images}

스테이지를 정의하는 3D 모델 파일은 단일 IBL 환경 이미지를 참조할 수 있습니다. 현재 AEM 3D는 확산 IBL 및 반사 시 위도/경도 형식의 32비트 TIFF 이미지만 지원합니다. 구형 장면 배경의 경우 8비트 RGB 이미지도 지원됩니다.

See [About working with IBL stages](working-with-ibl-stages.md).

>[!NOTE]
>
>위에서 설명한 것 이외의 기본 3D 모델 파일에 있는 파일 참조는 현재 무시됩니다. AEM 3D는 보조 3D 모델 파일에 대한 참조를 지원하지 않습니다.
Y-up은 이번 릴리스에서 FBX 파일에 대해 선호하는 좌표계입니다.

## 기본 3D 모델 파일의 재료 음영 {#material-shading-in-a-primary-d-model-file}

원본 기본 모델 파일에는 블린, 램버트와 같은 셰이더나 절차적 셰이더와 함께 사용되는 재료 정의가 포함될 수 있습니다. 이러한 잠재적으로 복잡할 수 있는 자료는 해당 기본 응용 프로그램(예: Autodesk Maya)을 사용하여 렌더링할 때만 지원됩니다.

보기 목적으로 또는 기본 Rapid Refine™ 렌더러를 사용하여 렌더링할 때 모든 재질은 단순화되거나 대체되거나 둘 다 사용되므로 Phony-like 셰이더와 함께 사용할 수 있습니다. 이 셰이더는 제한된 속성 집합을 지원합니다. 재료 정의의 다른 속성은 무시됩니다.

[3D 자산 보기](viewing-3d-assets.md)를 참조하십시오.

[3D 자산 렌더링](rendering-3d-assets.md)을 참조하십시오.

## 기본 3D 모델 파일에서 재료 이름 지정 {#naming-materials-in-a-primary-d-model-file}

서피스는 ** 동일한 재질로 덮여있는 3D 모델의 서피스 영역으로 정의됩니다. 이 재료는 또한 서피스의 이름을 제공합니다. 따라서 기본 3D 모델 파일에 포함된 자료의 이름을 그에 따라 지정하는 것이 좋습니다. 예를 들어 &quot;Body&quot;, &quot;Windows&quot;, &quot;Tires&quot; 또는 &quot;Rims&quot;와 같은 특정 이름을 사용하는 것이 &quot;Red&quot;, &quot;Glass&quot;, &quot;Rubber&quot;, &quot;Aluminum&quot;과 같은 모호한 이름을 사용하는 것보다 좋습니다.

