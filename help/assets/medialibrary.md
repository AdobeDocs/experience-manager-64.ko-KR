---
title: AEM Assets 및 AEM 미디어 라이브러리에서 사용 가능한 기능 비교
description: AEM Assets 및 AEM 미디어 라이브러리에 대한 FAQ와 그 차이점
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---


# AEM Assets와 AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager(AEM) 자산은 AEM 플랫폼의 필수 요소입니다. 이러한 매끄러운 통합은 AEM의 주요 장점으로 인식되며 컨텐츠 작성자는 컨텐츠를 일관성 있게 관리하고 생산성을 높일 수 있습니다.

## FAQ {#frequently-asked-questions}

### AEM Assets 소개 {#what-is-aem-assets}

AEM Assets은 고객이 웹 기반 저장소에서 디지털 자산(이미지, 비디오, 문서 및 오디오 클립)을 관리할 수 있는 AEM 플랫폼 기반의 애플리케이션입니다. AEM Assets에는 메타데이터 지원, 변환, 디지털 자산 관리 파인더 및 AEM Assets 관리 UI가 포함되어 있습니다.

### AEM 미디어 라이브러리란? {#what-is-the-aem-media-library}

AEM 미디어 라이브러리는 이미지와 기타 공유 리소스가 저장되는 AEM WCM 컨텐츠 저장소의 지정된 부분입니다. 미디어 라이브러리는 AEM WCM의 디지털 자산 관리 기능을 사용합니다.

### AEM WCM에 포함되지 않은 AEM Assets에서 얻는 것은? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

AEM Assets 고객에게만 제공되는 고유한 기능은 다음과 같습니다.

1. 제목, 태그 및 설명 이외의 메타데이터를 추출하고 편집할 수 있습니다.
1. [AEM Assets 관리]를 클릭합니다. `siteadmin`
1. 디지털 자산 관리와 관련된 모든 워크플로우 단계(예: AEM 자산 처리, AEM Assets 삭제, AEM Assets 하위 자산 처리, AEM Assets 메타데이터 추출)
1. im 패키지 공간을 포함한 `dam` 라이브러리.

이러한 기능을 사용하려면 유효한 AEM Assets 라이선스가 필요합니다.

### AEM Assets은 별도의 패키지로 제공됩니까? {#is-aem-assets-available-as-a-separate-package}

아니오. 모든 AEM 애플리케이션 및 Add-Ons는 설치 및 배포가 용이하도록 모든 기능이 포함된 하나의 패키지로 제공됩니다. 이는 패키지의 모든 기능을 사용할 수 있는 권한이 있다는 의미는 아닙니다.

#### 디지털 자산의 메타데이터를 편집하려고 합니다. AEM Assets이 필요합니까? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

제목, 설명 및 태그 이외의 메타데이터를 편집하려면 AEM Assets 라이선스가 필요합니다.

#### 가져올 때 이미지 크기를 자동으로 조정하려고 합니다. AEM Assets이 필요합니까? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

아니오. 정적 이미지의 크기 조정 및 자동 워크플로우 기반 변환과 변환 관리 기능은 AEM Media Library에 포함되어 있습니다. 이러한 기능은 AEM Assets 라이선스가 필요하지 않습니다.

### 사용자 정의된 이미지 구성 요소를 사용하여 이미지 크기를 조정하려고 합니다. AEM Assets이 필요합니까? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

이미지 구성 요소는 AEM WCM의 일부입니다. 이미지 구성 요소(AEM Assets도 사용)에서 사용 중인 그래픽 라이브러리는 AEM 플랫폼의 일부이며 AEM Assets 라이선스가 필요하지 않습니다.

### AEM Assets 라이선스를 부여하지 않은 경우 사용자가 AEM Assets을 사용하지 못하도록 하려면 어떻게 해야 합니까? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

AEM에서 모든 AEM Assets 관련 워크플로우, 구성 요소, 분류 체계, 옵션 및 AEM Assets 관리자를 제거할 수 있습니다. 이렇게 하면 사용자가 라이선스가 부여되지 않은 AEM Assets 기능을 실수로 사용하지 않게 됩니다.

### 페이지에 이미지를 추가하고 이러한 이미지를 자르고 크기를 조정하려고 합니다. AEM Assets이 필요합니까? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

이 경우 AEM Assets을 구입할 필요는 없으며 스마트 이미지 구성 요소를 사용하면 이미지를 페이지에 직접 업로드할 수 있으므로 웹 사이트에서 이미지를 사용할 필요도 없습니다.

>[!MORELIKETHIS]
>
>* [기능 차이점 상세 목록](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

