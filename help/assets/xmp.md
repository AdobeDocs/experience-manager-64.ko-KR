---
title: XMP 메타데이터
description: AEM Assets에서 메타데이터 관리를 위해 사용하는 XMP(Extensible Metadata Platform) 메타데이터 표준에 대해 알아봅니다. XMP은 다양한 애플리케이션을 위한 메타데이터 생성, 처리 및 교환을 위한 표준 형식을 제공합니다.
contentOwner: AG
feature: 메타데이터
role: Business Practitioner,Administrator
exl-id: 32c4ca3d-2e9e-46a3-b4c7-70dcc50daaaa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# XMP 메타데이터 {#xmp-metadata}

XMP(Extensible Metadata Platform)은 모든 메타데이터 관리를 위해 AEM Assets에서 사용하는 메타데이터 표준입니다. XMP은 다양한 애플리케이션을 위한 메타데이터 생성, 처리 및 교환을 위한 표준 형식을 제공합니다.

모든 파일 형식에 포함할 수 있는 범용 메타데이터 인코딩을 제공하는 것 외에도 XMP은 풍부한 [컨텐츠 모델](xmp.md#xmp-core-concepts) 및 Adobe](xmp.md#advantages-of-xmp) 및 다른 회사에서 지원하는 [를 제공하므로 AEM Assets과 결합하여 XMP을 사용하는 사용자는 강력한 플랫폼을 기반으로 할 수 있습니다.

[XMP 사양](https://www.adobe.com/devnet/xmp.html)은 Adobe에서 사용할 수 있습니다.

## XMP이란?{#what-is-xmp}

AEM Assets은 기본적으로 Adobe에 의해 실행되는 확장 가능한 메타데이터 플랫폼인 XMP을 지원합니다. XMP은 표준화된 독점 메타데이터를 디지털 자산에 처리하고 저장하는 표준입니다. XMP은 여러 애플리케이션이 메타데이터로 효과적으로 작동할 수 있도록 하는 일반적인 표준으로 설계되었습니다.

예를 들어, 프로덕션 전문가가 Adobe 애플리케이션 내에서 내장된 XMP 지원을 사용하여 여러 파일 형식에 대한 정보를 전달합니다. AEM Assets 리포지토리는 XMP 메타데이터를 추출하고 사용하여 컨텐츠 라이프사이클을 관리하고 자동화 워크플로우를 만드는 기능을 제공합니다.

XMP은 데이터 모델, 스토리지 모델 및 스키마를 제공하여 메타데이터 정의, 생성 및 처리 방법을 표준화합니다. 이러한 모든 개념은 이 섹션에서 다룹니다.

EXIF, ID3 또는 Microsoft Office의 모든 레거시 메타데이터는 자동으로 XMP으로 변환되며, 제품 카탈로그와 같은 고객별 메타데이터 스키마를 지원하도록 확장할 수 있습니다.

XMP의 메타데이터는 속성 세트로 구성됩니다. 이러한 속성은 항상\
리소스라는 특정 엔터티즉, 속성은 리소스에 대한 &quot;정보&quot;입니다. XMP의 경우 리소스는 항상 자산입니다.

### Adobe {#adobe}

Adobe은 Adobe Acrobat 소프트웨어 제품의 일부로 XMP 표준을 처음 도입했습니다. 그 이후 XMP 표준이 채택됐다.

### XMP 에코시스템 {#xmp-ecosystem}

XMP은 정의된 메타데이터 항목 세트와 함께 사용할 수 있는 [메타데이터](https://en.wikipedia.org/wiki/Metadata) 모델을 정의합니다. 또한 XMP은 최종 이미지에 결합하기 위해 사진 편집 단계(예: [자르기](https://en.wikipedia.org/wiki/Cropping_%28image%29) 또는 색상 조정)를 통해 촬영되거나, 스캔되거나, 텍스트로 작성된 리소스를 여러 처리 단계를 거칠 때 리소스의 내역을 기록하는 데 유용한 기본 속성을 위해 특정 [스키마](https://en.wikipedia.org/wiki/XML_schema)를 정의합니다. [](https://en.wikipedia.org/wiki/Image_scanner) XMP에서는 각 소프트웨어 프로그램 또는 장치가 디지털 리소스에 자체 정보를 추가할 수 있도록 허용하며 이를 최종 디지털 파일에 유지할 수 있습니다.

XMP은 가장 일반적으로 직렬화되어 [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework)(RDF)의 하위 집합을 사용하여 저장됩니다. 이 하위 집합은 [XML](https://en.wikipedia.org/wiki/XML)로 표시됩니다.

## XMP {#advantages-of-xmp}의 이점

XMP은 다른 인코딩 표준 및 스키마에 비해 다음과 같은 이점이 있습니다.

* XMP 기반 메타데이터는 매우 강력하고 세분화됩니다.
* XMP을 사용하면 하나의 속성에 대해 여러 값을 사용할 수 있습니다.
* XMP에는 표준화된 인코딩이 있어서 메타데이터를 쉽게 교환할 수 있습니다.
* XMP은 확장 가능합니다. 자산에 추가 정보를 추가할 수 있습니다.

### 확장 가능 {#extensible}

XMP 표준은 확장 가능하도록 설계되었으므로 사용자 지정 메타데이터 유형을 XMP 데이터에 추가할 수 있습니다. 반면 EXIF에는 확장할 수 없는 고정 속성 목록이 있습니다.

>[!NOTE]
>
>XMP에서는 일반적으로 이진 데이터 형식을 포함할 수 없습니다. 이진 데이터를 XMP으로 가져오려면 축소판 이미지와 같이 Base64와 같은 XML에 친숙한 형식으로 인코딩해야 합니다.

## XMP 코어 개념 {#xmp-core-concepts}

다음 섹션에서는 네임스페이스와 스키마, 속성 및 값, 언어 대체 요소를 포함한 XMP의 핵심 개념을 설명합니다.

### 네임스페이스 및 스키마 {#namespaces-and-schemata}

XMP 스키마는\
데이터 유형 및 설명 정보입니다. XMP 스키마는 XML 네임스페이스 URI로 식별됩니다. 네임스페이스를 사용하면 이름이 같지만 의미가 다른 여러 스키마에서 속성 간에 충돌이 발생하지 않습니다.

예를 들어, 독립적으로 디자인된 두 개의 스키마에서 **Creator** 속성은 자산을 만든 사람이나 자산을 만든 응용 프로그램(예: Adobe Photoshop)을 의미할 수 있습니다.

### 속성 및 값 {#properties-and-values}

XMP에는 하나 이상의 스키마의 속성이 포함될 수 있습니다.

예를 들어, 여러 Adobe 애플리케이션에서 사용하는 일반적인 하위 집합에는 다음이 포함될 수 있습니다.

* 더블린 코어 스키마:dc:title, dc:creator, dc:subject, dc:format, dc:rights
* XMP 기본 스키마:xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* XMP 권한 관리 스키마:xmpRights:WebStatement, xmpRights:Marked
* XMP Media 관리 스키마:xmpMM:DocumentID

### 언어 대체 요소 {#language-alternatives}

XMP에서는 텍스트 속성에 **xml:lang** 속성을 추가하여 텍스트 언어를 지정할 수 있는 기능을 제공합니다.
