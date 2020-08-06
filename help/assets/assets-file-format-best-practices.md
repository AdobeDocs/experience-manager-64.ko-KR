---
title: 자산 파일 형식 우수 사례
description: AEM Assets의 파일 지원에 대한 모범 사례
contentOwner: AG
translation-type: tm+mt
source-git-commit: a892ef7ab018aca715693125808d7ade540c8242
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 3%

---


# 자산 파일 형식 우수 사례 {#assets-file-format-best-practices}

AEM Assets은 사용자의 다양한 파일 지원 요구 사항을 충족하기 위해 많은 독점적 및 타사 파일 포맷 라이브러리를 지원합니다. 지원되는 Adobe 라이브러리에는 Adobe Camera Raw, 깁슨, Adobe PDF 래스터라이저, Adobe InDesign Server 등이 있습니다. 또한 AEM Assets은 ImageMagick, TwentyMonkeys 등을 비롯한 타사 라이브러리를 지원합니다.

For the supported file formats, see [Assets supported formats](assets-formats.md).

## Adobe Camera Raw 도서관 {#adobe-camera-raw-library}

최적의 성능을 위해 Adobe은 다음 용도로 Adobe Camera Raw 라이브러리를 사용하는 것이 좋습니다.

* RAW
* DNG

Adobe Camera Raw 라이브러리는 CMYK 색상 프로파일을 입력으로 지원합니다. 그러나 RGB 색상 공간에서 출력을 생성하고 JPEG 포맷에서만 출력을 지원합니다. 축소판의 소스 파일 색상 공간(예: CMYK)은 유지되지 않습니다.

자세한 내용은 AEM Assets의 [Camera Raw 지원을](camera-raw.md) 참조하십시오.

## Adobe PDF 래스터라이저 라이브러리 {#adobe-pdf-rasterizer-library}

최상의 결과를 얻으려면 다음 파일에 Adobe PDF 래스터라이저 라이브러리를 사용하는 것이 좋습니다.

* 컨텐츠가 많은 대용량 PDF 파일
* 축소판이 있는 AI 파일이 박스 밖으로 생성되지 않음
* PMS(스팟)가 있는 AI 파일의 경우

PDF 래스터라이저를 사용하여 생성된 축소판 및 미리 보기가 내장된 래스터 출력 결과와 비교하여 더 나은 품질을 제공합니다. Adobe PDF 래스터라이저 라이브러리는 색상 공간 변환을 지원하지 않습니다. 소스 PDF 파일의 색상 공간에 관계없이 Adobe PDF 래스터라이저는 RGB 출력만 생성합니다.

## Adobe InDesign 서버 {#adobe-indesign-cc-server}

Adobe은 Adobe InDesign 서버를 사용하여 IDML 및 HTML과 같은 Adobe InDesign 전용 변환을 추출하는 것이 좋습니다. 자세한 내용은 Adobe InDesign에서 [AEM 자산을 참조로 추가를 참조하십시오](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media는 글로벌, 확장 가능하고 성능에 최적화된 네트워크를 통해 다양한 유형의 리치 컨텐츠를 실시간으로 생성 및 전달합니다. 인터랙티브한 보기 경험을 제공하고 디지털 캠페인 관리 프로세스를 간소화합니다. 다이내믹 미디어 활성화에 대한 자세한 내용은 [다이내믹 미디어 구성을 참조하십시오](config-dynamic.md).

현재 Dynamic Media는 파일당 최대 15GB의 컨텐츠를 지원할 수 있습니다.

## ImageMagick 라이브러리 {#imagemagick-library}

Adobe은 다음 시나리오에서 ImageMagick 라이브러리를 사용하는 것이 좋습니다.

* EPS 파일에 대한 축소판 변환을 생성하려면
* 이미지 프로필 정보를 유지하려면
* 투명도를 유지하려면
* PSD 및 PSB 파일을 처리하려면

AEM에서 ImageMagic 라이브러리를 설정하는 방법을 알아보려면 ImageMagick [사용을 참조하십시오](media-handlers.md#an-example-using-imagemagick). 최적의 사용을 위해서는 ImageMagick을 구성하기 [위한 우수 사례를 참조하십시오](best-practices-for-imagemagick.md).

## 이미지 트랜스코딩 라이브러리 {#image-transcoding-library}

Adobe 이미징 트랜스코딩 라이브러리는 이미지 인코딩, 트랜스코딩, 리샘플링, 크기 조정 등 핵심 이미지 처리 기능을 수행하는 이미지 처리 솔루션입니다.

이미징 트랜스코딩 라이브러리는 다음과 같은 MIME 유형을 지원합니다.

* JPG/JPEG
* PNG(8비트 및 16비트)
* GIF
* BMP
* TIFF/Compressed TIFF(32비트 Tiff 및 PTiffs 분리).
* ICO
* ICN

자세한 내용은 [이미징 트랜스코딩 라이브러리를 참조하십시오](imaging-transcoding-library.md).
