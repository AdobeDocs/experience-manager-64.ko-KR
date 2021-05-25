---
title: 자산 파일 형식 우수 사례
description: AEM Assets의 파일 지원 우수 사례
contentOwner: AG
feature: 자산 관리,개발자 도구
role: Administrator
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 2%

---

# 자산 파일 형식 우수 사례 {#assets-file-format-best-practices}

AEM Assets은 사용자의 다양한 파일 지원 요구 사항을 충족하도록 많은 독점 및 타사 파일 형식 라이브러리를 지원합니다. 지원되는 Adobe 라이브러리에는 Adobe Camera Raw, Gibson, Adobe PDF Rasterizer 및 Adobe InDesign Server이 있습니다. 또한 AEM Assets은 ImageMagick, TweteenMonkeys 등을 포함한 타사 라이브러리를 지원합니다.

지원되는 파일 형식에 대해서는 [자산 지원 형식](assets-formats.md)을 참조하십시오.

## Adobe Camera Raw 라이브러리 {#adobe-camera-raw-library}

최적의 성능을 위해 Adobe은 다음 용도로 Adobe Camera Raw 라이브러리를 사용하는 것을 권장합니다.

* RAW
* DNG

Adobe Camera Raw 라이브러리는 CMYK 색상 프로파일을 입력으로 지원합니다. 그러나 RGB 색상 공간으로 출력을 생성하고 JPEG 형식으로만 출력을 지원합니다. 원본 파일 색상 공간(예: CMYK)은 축소판에 유지되지 않습니다.

자세한 내용은 AEM Assets에서 [Camera Raw 지원](camera-raw.md)을 참조하십시오.

## Adobe PDF 래스터라이저 라이브러리 {#adobe-pdf-rasterizer-library}

최상의 결과를 얻으려면 다음 파일에 Adobe PDF Rasterizer 라이브러리를 사용하는 것이 좋습니다.

* 컨텐츠가 많은 대용량 PDF 파일
* 미리 보기가 있는 AI 파일이 즉시 생성되지 않습니다
* SPOT(PMS) 색상을 사용하는 AI 파일의 경우

PDF Rasterizer를 사용하여 생성된 축소판 및 미리 보기는 기본 래스터 출력보다 품질이 향상됩니다. Adobe PDF Rasterizer 라이브러리는 색상 공간 변환을 지원하지 않습니다. 소스 PDF 파일의 색상 공간에 관계없이 Adobe PDF Rasterizer는 RGB 출력만 생성합니다.

## Adobe InDesign 서버 {#adobe-indesign-cc-server}

Adobe은 Adobe InDesign 서버를 사용하여 IDML 및 HTML과 같은 Adobe InDesign 관련 렌디션을 추출할 것을 권장합니다. 자세한 내용은 Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign)에서 [AEM 자산을 참조로 추가 를 참조하십시오.

## Dynamic Media  {#dynamic-media}

Dynamic Media은 글로벌, 확장 가능 및 성능 최적화 네트워크를 통해 실시간으로 다양한 유형의 풍부한 컨텐츠를 생성하고 전달합니다. 대화형 보기 환경을 제공하고 디지털 캠페인 관리 프로세스를 간소화합니다. Dynamic Media 활성화에 대한 자세한 내용은 [Dynamic Media 구성](config-dynamic.md)을 참조하십시오.

현재 Dynamic Media은 파일당 최대 15GB의 컨텐츠를 지원할 수 있습니다.

## ImageMagick 라이브러리 {#imagemagick-library}

Adobe은 다음 시나리오에서 ImageMagick 라이브러리를 사용하는 것이 좋습니다.

* EPS 파일에 대한 축소판 변환을 생성하려면
* 이미지 프로필 정보를 유지하려면
* 투명도를 유지하려면
* PSD 및 PSB 파일을 처리하려면

AEM에서 ImageMagic 라이브러리를 설정하는 방법은 [ImageMagick](media-handlers.md#an-example-using-imagemagick) 사용을 참조하십시오. 최적의 사용을 위해 [ImageMagick](best-practices-for-imagemagick.md) 구성에 대한 우수 사례 를 참조하십시오.

## 이미지 코드 변환 라이브러리 {#image-transcoding-library}

Adobe 이미징 트랜스코딩 라이브러리는 이미지 인코딩, 트랜스코딩, 리샘플링, 크기 조정 등 핵심 이미지 처리 기능을 수행하는 이미지 처리 솔루션입니다.

이미징 코드 변환 라이브러리는 다음과 같은 MIME 유형을 지원합니다.

* JPG/JPEG
* PNG(8비트 및 16비트)
* GIF
* BMP
* TIFF/압축 TIFF(32비트 Tiff 및 PTiffs 제외).
* 아이콘
* ICN

자세한 내용은 [이미징 코드 변환 라이브러리](imaging-transcoding-library.md)를 참조하십시오.
