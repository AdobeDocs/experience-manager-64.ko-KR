---
title: AEM 3D 릴리스 노트
seo-title: AEM 3D 릴리스 노트
description: Adobe Experience Manager Assets의 3D 컨텐츠와 관련된 릴리스 노트입니다.
seo-description: Adobe Experience Manager Assets의 3D 컨텐츠와 관련된 릴리스 노트입니다.
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
content-type: reference
topic-tags: 3D
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: 7c850ed0d20dd2ba2626242c67ba190e371f049f

---


# AEM 3D 릴리스 노트 {#aem-d-release-notes}

AEM-6.4-DynamicMedia-3D 버전 3.1.0(2018년 10월 10일)

AEM 3D 기능 팩은 AEM Assets에서 3D 컨텐츠를 지원합니다. 3D 자산을 업로드, 관리, 미리 보기 및 렌더링하는 기능을 제공합니다. 보기 및 렌더링 지원은 여러 개체가 있는 복잡한 장면이 아니라 개별 개체에 맞게 최적화되어 있습니다.

AEM 3D는 Adobe Dimension(Dn) 및 glTF 자산 유형을 지원합니다. 이러한 자산 유형에 대한 구현은 이 설명서에 설명된 기존 3D 유형의 구현과 실질적으로 다릅니다. Adobe [Dimension 자산](/help/assets/working-dimension-assets.md)작업을 참조하십시오.

Autodesk® Maya®(Windows 전용)와의 서버측 통합도 포함되어 있습니다. AEM 파섹 서버에 3ds Max를 설치 및 구성하면 기본 .max 파일 형식을 지원합니다.

Autodesk [Maya와 통합을 참조하십시오](/help/assets/integrate-maya-with-3d.md).

AEM [3D 자산 설치 및 구성](/help/assets/install-config-3d.md) 및 고급 [구성 설정을](/help/assets/advanced-config-3d.md)참조하십시오.

3D [에셋](/help/assets/assets-3d.md)작업을 참조하십시오.

## 시스템 요구 사항 {#system-requirements}

**전제 조건**

* AEM 6.4.2(서비스 팩 2 포함 AEM 6.4)
* Autodesk® FBX® SDK 2016.1.2

**지원되는 운영 체제**

* Microsoft Windows 2012 Server 이상
* Apple OS X El Capitan 10.6 이상
* RedHat Enterprise Linux 7.3

**AEM 자산에 대해 지원되는 웹 브라우저**

* Google Chrome 53 이상(권장).
* Apple Safari 9.1 이상.
* Firefox 48 이상.
* Microsoft Edge 25.10586 이상.

다른 브라우저는 AEM에서 3D 컨텐츠의 대화형 보기를 지원하지 않을 수 있습니다. Google Chrome만 미리 보기에서 캐스트 그림자를 지원합니다.

**하드웨어 요구 사항 및 권장 사항**

* CPU - 3D 처리 및 렌더링은 컴퓨터 CPU에서 매우 까다롭습니다. 따라서 최소 8개의 CPU 코어를 사용하는 최신 서버를 권장합니다.
* 메모리 - 최소 32GB가 권장됩니다.
* 대용량 스토리지 - 고대역폭 SSD 스토리지가 권장됩니다.

   업로드 시 3D 에셋은 빠르고 인터랙티브한 방식으로 볼 수 있는 독점적인 포맷으로 변환됩니다. 3D 자산의 유형에 따라 업로드된 3D 자산의 2-3배 크기의 저장 공간이 필요합니다.

3D [에셋](/help/assets/assets-3d.md)작업을 참조하십시오.

## AEM 3D 설치 및 구성 {#installing-and-configuring-aem-d}

See [Installing and configuring AEM 3D](/help/assets/install-config-3d.md).

AEM [3D와 Autodesk Maya 통합](/help/assets/integrate-maya-with-3d.md) 및 AEM 3D와 [Autodesk 3ds Max 통합을 참조하십시오](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md).

## 지원되는 3D 파일 포맷 {#supported-d-file-formats}

<table> 
 <tbody>
  <tr>
   <td><strong>형식</strong></td> 
   <td><strong>설명</strong></td> 
   <td><strong>플랫폼</strong></td> 
   <td><strong>메모</strong></td> 
  </tr>
  <tr>
   <td>DN</td> 
   <td>Adobe Dimension</td> 
   <td>모든</td> 
   <td>클라우드 기반의 전환 서비스를 이용해야 합니다.</td> 
  </tr>
  <tr>
   <td>GLTZ</td> 
   <td>압축된 gITF</td> 
   <td>모든</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>GLB</td> 
   <td>바이너리 gITF</td> 
   <td>모든</td> 
   <td>다운로드만(GLB 변환은 DN 자산에 대해 생성).</td> 
  </tr>
  <tr>
   <td>OBJ</td> 
   <td>Wavefront OBJ 3D </td> 
   <td>모든</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>FBX</td> 
   <td>Autodesk FBX(Kaydara Filmbox)</td> 
   <td>모든</td> 
   <td>Autodesk FBX SDK는 작성자 노드에 설치되어 있어야 합니다.</td> 
  </tr>
  <tr>
   <td>MA, MB</td> 
   <td>기본 Autodesk Maya</td> 
   <td>Windows 전용</td> 
   <td>Autodesk Maya는 작성자 노드에서 이러한 파일 형식을 활성화해야 합니다. Autodesk <a href="/help/assets/integrate-maya-with-3d.md" target="_blank">Maya와 AEM 3D 통합을 참조하십시오</a>.</td> 
  </tr>
  <tr>
   <td>JT</td> 
   <td>Siemens PLM Open CAD</td> 
   <td>Windows 전용</td> 
   <td>Autodesk Maya는 작성자 노드에서 이러한 파일 형식을 활성화해야 합니다. Autodesk <a href="/help/assets/integrate-maya-with-3d.md">Maya와 AEM 3D 통합을 참조하십시오</a>.</td> 
  </tr>
  <tr>
   <td>*</td> 
   <td><p>Autodesk Maya에서 지원하는 추가 3D 입력 형식을 사용할 수 있습니다.</p> <p>Maya <a href="/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya" target="_blank">에서 지원하는 추가 형식 사용을 참조하십시오</a>.</p> </td> 
   <td>Windows 전용</td> 
   <td>Autodesk Maya는 작성자 노드에서 이러한 파일 형식을 활성화해야 합니다. Autodesk <a href="/help/assets/integrate-maya-with-3d.md">Maya와 AEM 3D 통합을 참조하십시오</a>.</td> 
  </tr>
  <tr>
   <td>MAX</td> 
   <td>기본 Autodesk 3ds Max</td> 
   <td>Windows 전용</td> 
   <td>Autodesk 3ds Max는 작성자 노드에서 이 파일 형식을 활성화해야 합니다. AEM <a href="/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md">3D와 Autodesk 3ds Max 통합을 참조하십시오</a>.</td> 
  </tr>
 </tbody>
</table>

## 향상된 기능 및 새로운 기능 {#enhancements-and-new-features}

버전 3.0

* Autodesk 3ds Max 기본 파일 포맷 지원
* 안정성, 품질 및 사용자 경험을 개선하기 위한 다양한 변경 사항 및 버그 수정
* 구성 설정이 `/libs/settings/dam/v3d/`

버전 3.1

* Adobe Dimension 기본 파일 형식(.dn)에 대한 지원이 제한됩니다.
* glTF 자산에 대한 새로운 3D 뷰어입니다.
* Amazon AWS에서 호스팅되는 클라우드 기반의 Adobe 관리 전환 서비스에 대한 새로운 인터페이스. 처음에는 이 서비스는 Dn에서 glTF 형식으로만 변환합니다.

## 제한 및 알려진 문제 {#restrictions-and-known-issues}

### Adobe Dimension 지원 {#adobe-dimension-support}

* 이 버전의 AEM3D는 Adobe Dimension으로 만든 .dn 파일에 대한 지원이 제한되어 있습니다.
* 업로드 처리 중 AEM은 클라우드 기반의 Adobe 호스팅 전환 서비스를 활용하여 기본 .dn 파일에서 glTF 변환을 만듭니다. 전환 서비스에 액세스하고 Amazon AWS 엔드포인트를 선택해야 합니다.
* AEM 자산 및 사이트/스크린에서 Dn 자산을 볼 수 있도록 지원하는 새 glTF 뷰어가 제공됩니다. 뷰어의 단계에 대한 지원은 아직 사용할 수 없습니다.
* DN 모델은 IBL 조명 및 표시되는 배경(있는 경우)을 포함할 수 있습니다. 또는 뷰어에서 기본 조명, 기본 배경색 또는 둘 다를 적용합니다.
* Dn 자산에 대한 고품질 렌더링은 아직 사용할 수 없습니다.
* 텍스처 맵과 같은 종속성은 Dn 자산에 포함되며 AEM에서 명시적으로 관리할 수 없습니다.

### 호환성 {#compatibility}

* **Windows 서비스로 실행하는 것은 지원되지 않습니다(Windows만 해당)** - 이 작업은 작동하지만 테스트되지 않았습니다.
* **다이내믹 미디어** ( `dynamicmedia-scene7` 모드) - AEM 6.4에서 릴리스된 새로운 다이내믹 미디어 솔루션과 AEM3D의 호환성이 아직 완전히 확인되지 않았습니다. Dynamic Media와 AEM3D가 함께 배포된 경우, 3D 자산과 해당 종속성을 Dynamic Media에 할당되지 않은 AEM Assets 저장소의 영역에만 배치하는 것이 좋습니다. 이 권장 사항은 3D 스테이지에 필요하지만 Dynamic Media에서 지원되지 않는 32비트 TIFF 파일에 특히 중요합니다.

### 일반 {#general}

* **종속성 해결 단축키** - 이 단축키는 3D 자산의 카드 보기에서 사용할 수 있습니다. 카드 보기의 자산 카드에 &quot;해결되지 않은 종속성&quot; 배너가 표시됩니다. 단축키는 종속성 **탭 대신 기본** 속성 **탭을** 엽니다. 해결 방법:종속성 탭으로 수동으로 이동합니다.

* **스테이지 선택기 사용 불가** - 조명을 포함하는 3D 자산은 AEM에서 3D 단계로 자동으로 태그됩니다. 세부 사항 보기에서 단계에 대해 단계 선택기를 사용할 수 없습니다. 3D 자산을 3D 개체로 표시하려면 **기본 속성으로**&#x200B;이동하고 **자산 클래스를** **** 3D 개체로 **변경한 다음 저장을**&#x200B;클릭합니다.

* **종속 항목 및 표현물이** 포함된 3D 자산 다운로드 **- 종속성** 및 표현물이 모두 **선택된 상태로 AEM에서 3D 자산을 다운로드할 때** 다운로드에는 기본 3D자산의 변환뿐만 아니라 모든 종속 항목의 변환도 포함됩니다.

* **Autodesk 3ds Max 통합** - 현재 3ds Max를 사용한 렌더링은 지원되지 않습니다.

### 파일 유형 제한 {#file-type-restrictions}

* **매스매티카 파일** (.ma) - 매스매티카 파일은 기본 Maya 파일과 동일한 파일 접미어를 사용합니다. Feature Pack이 설치되고 Maya .ma 파일 포맷이 활성화되면 AEM3D에서 Maya 파일로 매스매티카 파일을 인제스트할 수 없습니다. 이러한 자산은 카드 보기에 오류 배너를 표시합니다.

* **Targa(.tga) 이미지 파일** - 이전 3D 모델 파일에는 TGA 파일에 대한 참조가 포함될 수 있습니다. 이 형식은 AEM에서 지원되지 않습니다. 3D 자산을 AEM으로 업로드하기 전에 이러한 파일을 다른 형식으로 변환하는 것이 좋습니다.
* **HDR 이미지** - HDR 이미지는 IBL(이미지 기반 조명)을 사용하는 단계에 사용됩니다. 현재 32비트 TIFF 이미지만 지원됩니다.
* **32비트 TIFF 이미지** - 32비트 TIFF 이미지는 이미지 기반 조명이 있는 단계에 사용됩니다. AEM에서는 이러한 자산에 대한 표현물 작성을 지원하지 않으므로 빈 축소판을 만들고 미리 보기를 수행할 수 없습니다. IBL 스테이지에서 에셋을 사용할 때에도 여전히 올바르게 작동합니다.
* **Autodesk 3ds Max(.max) 파일** - Autodesk 3ds Max가 작성자 노드에 설치 및 구성된 경우 AEM은 .max 파일의 통합 및 변환을 지원합니다. 지금은 .max 파일을 스테이지로 사용할 수 없습니다.

### 자동 종속성 확인 {#automatic-dependency-resolution}

* **업로드** 후 해결되지 않은 파일 종속성 - 3D 자산 및 종속 항목이 동일한 업로드 작업으로 업로드되면 일부 종속 항목이 자동으로 확인되지 않을 수 있습니다. 종속 파일이 큰 경우 이 문제가 발생할 가능성이 높습니다. 이 문제를 해결하려면 업로드 후 **해결되지 않은 종속 항목을** 표시하는 자산의 속성/종속성 페이지에 액세스하십시오. 이제 이전에 해결되지 않은 종속 항목이 표시됩니다. 저장을 **클릭하여** 자산을 마무리합니다. 향후 이 문제를 방지하려면 3D 개체를 업로드하기 전에 별도의 트랜잭션에 모든 종속 항목을 업로드할 수 있습니다.

* **대/소문자 구분** - 자동 종속성 해상도는 대소문자를 구분하는 방식으로 파일 이름과 일치시키려고 시도합니다. 예를 들어 3D 자산에서 발견된 원래 종속성이 `image.jpg`있는 경우 종속성이 `Image.jpg`또는 `image.JPG`기타 대/소문자 변형이라는 자산으로 확인됩니다.

### 3D 단계 {#d-stages}

* **단계의** 축소판 - 단계에 대해 자동으로 생성된 축소판은 스테이지를 정확하게 나타내지 않을 수 있습니다.
* **비IBL 단계의** 스테이지 모양 - Rapid Refine 렌더러는 배경 및 지표 평면을 비롯한 비IBL 조명이 있는 단계의 형상을 렌더링하지 않습니다. 이러한 도형은 여전히 자산 세부 사항 보기(3D 미리 보기)에서 합리적으로 표시됩니다.

* **IBL 조명이** 있는 FBX 단계 - IBL 조명을 사용하여 FBX 단계를 업로드할 수 있습니다. 그러나 FBX 형식에는 IBL 이미지 이름을 전송할 수 있는 기능이 없습니다. 따라서 파일 종속성 확인에 실패합니다. IBL 이미지는 업로드 후 스테이지에 수동으로 할당해야 합니다. 동일한 32비트 TIFF 이미지를 확산 조명 환경 이미지, **반사 환경 이미지**&#x200B;및 **배경 환경 이미지**&#x200B;또는 **다른 이미지를**&#x200B;지정할 수 있습니다.

* **IBL 단계의** 배경 이미지 - 일부 IBL 장면의 경우 배경 이미지의 품질이 너무 밝거나 흐리게 할 수 있습니다. IBL 단계의 이미지 배경을 최대화하려면 별도의 고해상도 8비트 JPEG 이미지를 준비한 다음 배경 환경 이미지로 IBL 스테이지에 첨부할 **것을 권장합니다**.

* **IBL 스테이지를** 사용하여 Maya로 렌더링할 때 검정 이미지 - 스테이지에서 참조한 원본 IBL 이미지가 다른 이름으로 대체되었기 때문에 Maya가 IBL 이미지 종속성을 찾지 못해 이 문제가 발생할 수 있습니다. 이 문제를 방지하려면 Maya IBL 스테이지에서 참조하는 세 가지 종속성 중 적어도 하나가 Maya 파일의 원본 IBL 파일 참조와 이름이 같은지 확인하십시오.
* **IBL 단계의** 반전 배경 이미지 - IBL 단계의 이미지는 Autodesk Maya와 함께 제공되는 NVIDIA mental ray 렌더러의 동작과 일치하도록 의도적으로 수평으로 뒤집습니다. 해결 방법:업로드하기 전에 Photoshop에서 IBL 단계에 사용된 이미지를 뒤집습니다.
* **IBL 단계의** 밝기 - IBL 이미지의 자동 분석으로 인해 너무 어둡거나 너무 밝은 장면이 발생할 수 있습니다. IBL 단계의 조명 밝기를 조정하려면 기본 **속성으로** 이동하여 **필요에 따라 환경** 조명의 **밝은** 값을조정합니다.

### AEM Sites 3D 구성 요소 {#aem-sites-d-component}

* **페이지당** 하나의 3D 구성 요소 - 현재 각 웹 페이지에서 3D 구성 요소의 인스턴스는 하나만 허용됩니다. 동일한 페이지에 2개 이상의 3D 구성 요소가 추가된 경우 3D 구성 요소 중 제대로 작동하지 않습니다.
* **사이트에서 미리 볼 때 3D 보기 누락** - **사이트에서 미리** 보기를 사용할 때 3D 뷰어를 완전히 초기화하려면 브라우저에서 페이지를 다시 로드해야 합니다. 이 문제는 웹 페이지를 직접 볼 때(즉, 경로에서 제거될 때) 작성자 노드나 게시 노드에서 문제가 `edit.html` 아닙니다.

* **iOS 장치에서** 전체 화면 모드를 사용할 수 없음 - 사용된 브라우저와 상관없이 iOS 장치에서 전체 화면 단추를 사용할 수 없습니다.

### 3D 컨텐츠 게시 {#publishing-d-content}

* **3D 구성 요소 구성** - 모든 활성 게시 노드에 3D 기능 팩을 설치해야 하며, 각 노드는 **CRXDE Lite** 를 사용하여 동일한 구성 옵션으로 구성해야 합니다 `/libs/settings/dam/v3D/WebGLSites`.

* **게시** 후 텍스처, 배경 또는 조명 누락 - **AEM Sites의** 게시 메커니즘은 3D 모델 및 3D 구성 요소에서 참조한 3D 스테이지를 포함하여 페이지의 기본 종속성을 자동으로 게시합니다. 3D 단계 및 3D 모델은 일반적으로 IBL 이미지와 텍스처 맵의 보조 에셋에 따라 달라지며, 사이트 게시 메커니즘은 자동으로 게시되지 않습니다. 해결 방법:사이트에서 웹 페이지를 게시하기 전에 자산에서 모든 3D 자산을 게시합니다. 이렇게 하면 3D 자산에 대한 모든 종속성을 게시 노드에서 사용할 수 있습니다.

