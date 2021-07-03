---
title: AEM Assets에서 지원되는 파일 형식
description: AEM Assets에서 지원하는 파일 형식 및 MIME 유형과 각 형식에 대해 지원되는 기능 목록입니다.
contentOwner: AG
feature: 자산 관리,표현물
role: User,Admin
exl-id: ee25fe8f-36fb-42b3-9f90-0ea77bc02e2f
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1651'
ht-degree: 9%

---

# AEM Assets에서 지원되는 파일 형식 {#assets-supported-formats}

AEM Assets은 다양한 파일 형식을 지원하며 각 기능은 다양한 MIME 유형에 대한 다양한 지원을 제공합니다.

AEM Assets을 다른 표준 준수 DAM(Digital Asset Management) 솔루션 및 데스크탑 소프트웨어와 통합하려면 Adobe의 XMP(Extensible Metadata Platform)를 사용합니다.

지원 수준을 이해하려면 범례를 사용합니다.

| 지원 수준 | 설명 |
|:---:|---|
| ✓ | 지원됨 |
| * | 추가 기능 지원 |
| - | 해당 사항 없음 |

## 래스터 이미지 형식 {#supported-raster-image-formats}

자산 관리 기능에 대해 지원되는 래스터 이미지 형식은 다음과 같습니다.

| 형식 | 저장 용량 | 메타데이터 관리 | 메타데이터 추출 | 축소판 생성 | 대화형 편집 | 메타데이터 원본에 쓰기 | 인사이트 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PNM | ✓ | ✓ |  |  |  |  | ✓ |
| PGM | ✓ | ✓ |  |  |  |  | ✓ |
| PBM | ✓ | ✓ |  |  |  |  | ✓ |
| PPM | ✓ | ✓ |  |  |  |  | ✓ |
| PSD **** | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| PICT |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

**병합된 ‡ 이미지는 PSD 파일에서 추출됩니다.** Adobe Photoshop에서 생성하여 PSD 파일에 포함된 이미지입니다. 설정에 따라 병합된 이미지가 실제 이미지이거나 아닐 수 있습니다.

Dynamic Media 기능에 대해 지원되는 래스터 이미지 형식은 다음과 같습니다.

| 형식 | 업로드<br> (입력 형식) | <br> 이미지<br> 사전 설정<br>(출력 형식) 만들기 | 미리 보기<br> 동적<br> 변환 | 배달<br> 동적<br> 변환 | <br> dynamic<br> 변환 다운로드 |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |
| PSB |  |  |  |  |  |

**병합된 ‡ 이미지는 PSD 파일에서 추출됩니다.** Adobe Photoshop에서 생성하여 PSD 파일에 포함된 이미지입니다. 설정에 따라 병합된 이미지가 실제 이미지이거나 아닐 수 있습니다.

위의 정보 외에 다음 사항을 고려하십시오.

* EPS 파일에 대한 지원은 래스터 이미지만 적용됩니다. 예를 들어 EPS 벡터 이미지에 대한 축소판 생성은 기본적으로 지원되지 않습니다. 지원을 추가하려면 [ImageMagick](best-practices-for-imagemagick.md)을 구성합니다. 타사 도구를 통합하여 추가 기능을 활성화하려면 [명령줄 기반 미디어 핸들러](media-handlers.md#command-line-based-media-handler)를 참조하십시오.

* 메타데이터 원본에 쓰기 저장(writeback)은 PSB 파일 형식이 `NComm` 처리기에 추가되면 작동합니다.

* Dynamic Media을 사용하여 EPS 파일에 대한 동적 렌디션을 미리 보고 생성하려면 [Adobe Illustrator(AI), Postscript(EPS) 및 PDF 파일 형식을 참조하십시오.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* EPS 파일의 경우, PS-Adobe 버전 3.0 이상에서 메타데이터 원본에 쓰기 기능이 지원됩니다.

## Dynamic Media에서 지원되지 않는 래스터 이미지 형식 {#unsupported-image-formats-dynamic-media}

다음 목록에서는 Dynamic Media에서 지원되지 않는 *래스터 이미지 파일 형식의 하위 유형을 설명합니다.*

또한 [Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html)에 대해 지원되지 않는 파일 형식 감지를 참조하십시오.

* IDAT 청크 크기가 100MB보다 큰 PNG 파일.
* PSB 파일.
* CMYK, RGB, 회색 음영 또는 비트맵 이외의 색상 공간이 있는 PSD 파일은 지원되지 않습니다. DuoTone, Lab 및 Indexed 색상 공백은 지원되지 않습니다.
* 비트 깊이가 16보다 큰 PSD 파일.
* 부동 소수점 데이터가 있는 TIFF 파일입니다.
* Lab 색상 공간이 있는 TIFF 파일입니다.

## PDF 래스터라이저 라이브러리 {#supported-pdf-rasterizer-library}

Adobe PDF Rasterizer 라이브러리는 크고 컨텐츠가 많은 Adobe Illustrator 및 PDF 파일을 위한 고품질 축소판 및 미리 보기를 생성합니다. Adobe은 다음과 같은 경우 PDF 래스터라이저 라이브러리를 사용하는 것이 좋습니다.

* 리소스를 많이 사용하는 AI/PDF 파일을 처리할 수 있습니다.
* 축소판이 기본적으로 생성되지 않는 AI/PDF 파일입니다.
* PMS(Pantone Matching System) 색상을 사용하는 AI 파일입니다.

[PDF 래스터라이저 사용](aem-pdf-rasterizer.md)을 참조하십시오.

## 이미지 코드 변환 라이브러리 {#supported-image-transcoding-library}

Adobe 이미징 코드 변환 라이브러리는 인코딩, 코드 변환, 리샘플링 및 크기 조정과 같은 핵심 이미지 처리 기능을 수행하는 이미지 처리 솔루션입니다.

이미징 코드 변환 라이브러리는 JPG/JPEG, PNG(8비트 및 16비트), GIF, BMP, TIFF/압축 TIFF(32비트 TIFF 파일 및 PTIFF 파일 제외), ICO 및 ICN MIME 유형을 지원합니다.

[이미징 코드 변환 라이브러리](imaging-transcoding-library.md)를 참조하십시오.

## Camera Raw {#supported-camera-raw}

Adobe Camera Raw 라이브러리를 사용하면 AEM Assets에서 원시 이미지를 수집할 수 있습니다. [Camera Raw 지원](camera-raw.md)을 참조하십시오.

## 문서 형식 {#supported-document-formats}

자산 관리 기능에 대해 지원되는 문서 형식은 다음과 같습니다.

| 형식 | 저장 용량 | 메타데이터<br> 관리 | 전체 텍스트<br> 추출 | 메타데이터<br> 추출 | 축소판 그림<br> 생성 | Subasset<br> 추출 | 메타데이터<br> 원본에 쓰기 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| DOC | ✓ | ✓ | ✓ | ✓ |  |  |  |
| DOCX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODT | ✓ | ✓ | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |  |  |  |  |
| RTF | ✓ | ✓ | ✓ |  |  |  |  |
| TXT | ✓ | ✓ | ✓ |  |  |  |  |
| XLS | ✓ | ✓ | ✓ |  |  |  |  |
| XLSX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODS | ✓ | ✓ | ✓ |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ODP | ✓ | ✓ | ✓ |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| PS | ✓ | ✓ |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |
| EPUB | ✓ | ✓ |  | ✓ | ✓ |  |  |

Dynamic Media 기능에 대해 지원되는 문서 형식은 다음과 같습니다.

| 형식 | 업로드<br> (입력 형식) | <br> 이미지<br> 사전 설정<br>(출력 형식) 만들기 | 미리 보기<br> 동적<br> 변환 | 배달<br> 동적<br> 변환 | <br> dynamic<br> 변환 다운로드 |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| 문서 |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

위의 기능 외에 다음 사항을 고려하십시오.

* Dynamic Media을 사용하여 PDF 파일에 대한 동적 변환을 생성하려면 [Adobe Illustrator(AI), Postscript(EPS) 및 PDF 파일 형식을 참조하십시오.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Dynamic Media을 사용하여 AI 파일에 대한 동적 렌디션을 미리 보고 생성하려면 [Adobe Illustrator(AI), Postscript(EPS) 및 PDF 파일 형식을 참조하십시오.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Dynamic Media을 사용하여 INDD 파일에 대한 동적 변환을 생성하려면 [InDesign(INDD) 파일 형식](../assets/managing-image-presets.md#indesign-indd-file-format)을 참조하십시오.

## 멀티미디어 형식 {#supported-multimedia-formats}

| 형식 | 저장 용량 | 메타데이터 관리 | 메타데이터 추출 | 축소판 생성 | FFMPEG 코드 변환 |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | - | * |
| MIDI | ✓ | ✓ |  | - | * |
| 3GP | ✓ | ✓ |  | - | * |
| MP3 | ✓ | ✓ | ✓ | - | * |
| MPG | ✓ | ✓ |  | - | * |
| OGA | ✓ | ✓ |  | - | * |
| OGG | ✓ | ✓ |  | - | * |
| RA | ✓ | ✓ |  | - | * |
| WAV | ✓ | ✓ |  | - | * |
| WMA | ✓ | ✓ |  | - | * |
| DVI | ✓ | ✓ |  | * | * |
| FLV | ✓ | ✓ |  | * | * |
| M4V | ✓ | ✓ |  | * | * |
| MPEG | ✓ | ✓ |  | * | * |
| OGV | ✓ | ✓ |  | * | * |
| 이동 | ✓ | ✓ |  | * | * |
| WMV | ✓ | ✓ |  | * | * |
| SWF | ✓ | ✓ |  |  |  |

## Dynamic Media 코드 변환용 비디오 형식 입력 {#supported-input-video-formats-for-dynamic-media-transcoding}

| 비디오 파일 확장 | 컨테이너 | 권장 비디오 코덱스 | 지원되지 않는 비디오 코덱입니다 |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC(모든 프로필) |  |
| 이동, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV(DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF(벡터 애니메이션 파일) |
| WMV | Windows Media 9 | WMV3(v9), WMV2(v8), WMV1(v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen(MSS2), Microsoft Photo Story(WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | 애플 아이튠스 | H264/AVC |  |
| AVI | A/V 인터리브 | XVID, DIVX, HDV, MiniDV(DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indfo3(IV30), MJPEG, Microsoft 비디오 1(MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | 마트로스카 | H264/AVC |  |
| R3D, RM | Red Raw 비디오 | MJPEG 2000 |  |
| RAM, RM | RealVideo | 지원되지 않음 | Real G2(RV20), Real 8(RV30), Real 10(RV40) |
| FLAC | 네이티브 Flash | 무손실 오디오 코덱이 있습니다 |  |
| MJ2 | 동작 JPEG 2000 | 모션 JPEG 2000 코덱을 |  |

## 아카이브 형식 {#supported-archive-formats}

지원되는 아카이브 형식 및 공통 DAM 워크플로우의 적용 사례는 다음 표에서 다룹니다.

| 형식 | 저장 용량 | 버전 관리 | 워크플로우 | 게시 | 액세스 제어 | Dynamic Media 게재 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP **†** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

**†** 병합된 이미지가 PSD 파일에서 추출됩니다. Adobe Photoshop에서 생성하여 PSD 파일에 포함된 이미지입니다. 설정에 따라 병합된 이미지가 실제 이미지이거나 아닐 수 있습니다. `Deflate64` 알고리즘을 사용하여 만든 ZIP 아카이브는 AEM에서 지원이 제한되었습니다. 보관 및 보관 해제 작업은 지원되지 않습니다. 하지만 업로드, 탐색 및 다운로드와 같은 작업이 지원됩니다.

## 기타 지원되는 형식 {#other-supported-formats}

다른 몇 가지 파일 형식에 대한 일반적인 DAM 워크플로우의 적용성은 아래 표에 설명되어 있습니다.

| 형식 | 저장 용량 | 버전 관리 | 워크플로우 | 게시 | 액세스 제어 | Dynamic Media 게재 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript(자체 게재 도메인으로 구성된 경우) |  |  |  |  |  | ✓ |

**#** 다른 형식은 저장, 버전 관리, ACL, 워크플로우, 게시 및 메타데이터 관리를 위해 DAM에서 지원됩니다.

## 지원되는 MIME 유형 {#supported-mime-types}

기본적으로 AEM은 파일 확장자를 사용하여 파일 유형을 감지합니다. AEM은 파일의 내용에서 검색할 수 있습니다. 후자의 경우, AEM 웹 콘솔에서 [!UICONTROL 일 CQ DAM MIME 유형 서비스]에서 [!UICONTROL 컨텐츠에서 MIME 감지 옵션을 선택합니다.]

지원되는 MIME 유형 목록은 `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes` CRXDE Lite에서 사용할 수 있습니다.

| 파일 확장명 | MIME 유형/인터넷 미디어 유형 | 기본 jobParam 값 | 허용되는 jobParam 값 |
|---|---|---|---|
| 이미지 | 이미지/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | 기본 jobParam 은 모든 이미지 MIME 유형 자산에 적용됩니다.<ul><li>[ckoutBackgroundOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | 비디오/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | 오디오/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | 텍스트/css |  |  |
| 문서 | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>애플리케이션/eps</li><li>application/x-eps</li><li>이미지/eps</li><li>이미지/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | 이미지/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 이동 | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| RTF | application/x-font-ttf |  |  |
| VOB | 비디오/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | 텍스트/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [MIME 유형 기반 Assets/Dynamic Media Classic 업로드 작업 매개 변수 지원을 활성화합니다](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).
>* [업로드 작업 매개 변수 지원을 위해 MIME 유형 기반의 를 구성합니다](config-dynamic.md).

