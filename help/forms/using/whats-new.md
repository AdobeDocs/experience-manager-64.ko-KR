---
title: 새로운 기능 요약 | AEM 6.4 Forms
seo-title: 새로운 기능 요약 | AEM 6.4 Forms
description: Summary of new features and enhancements in AEM 6.4 Forms.
seo-description: AEM 6.4 Forms의 새로운 기능 및 개선 사항에 대한 요약
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc
workflow-type: tm+mt
source-wordcount: '2017'
ht-degree: 0%

---


# 새로운 기능 요약 | AEM 6.4 Forms {#new-features-summary-aem-forms}

AEM 6.4 Forms의 새로운 기능 및 개선 사항에 대한 요약

AEM Forms에는 적응형 양식 및 인터랙티브한 커뮤니케이션을 통해 작성, 관리 및 사용자 경험을 보다 효율적으로 수행할 수 있는 몇 가지 새로운 기능과 향상된 기능이 포함되어 있습니다.

새로운 기능 및 개선 사항에 대한 빠른 소개를 살펴보십시오. 자세한 내용은 설명서를 참조하십시오. 또한 AEM 6.4 Forms [릴리스 노트를 참조하십시오](/help/release-notes/forms.md). 전체 AEM 6.4 Forms 문서를 보려면 AEM [6.4 Forms 사용 안내서를 참조하십시오](/help/forms/home.md).

## 대화형 통신 {#interactive-communications}

![통신 관리](assets/correspondence-management.png)

Interactive Communications는 비즈니스 서신, 서신, 문서, 명세서, 혜택 정보, 자산 관리 설명서, 마케팅 이메일, 청구서 및 환영 키트 등 안전하고 개인화된 인터랙티브한 통신의 작성, 수집 및 전달을 중앙 집중화하여 관리합니다.

인터랙티브 커뮤니케이션은 적응형 양식과 동일한 기본 기술, 프로세스 및 구성 요소를 사용하므로 반응형 적응형 양식과 유사한 반응형 멀티채널 커뮤니케이션을 제작할 수 있습니다.

Interactive communication offers significant advantages:

* 양식 데이터 모델과 OOTB를 통합하여 백엔드 데이터베이스 및 MS Dynamics와 같은 기타 CRM 시스템에 간편하고 간소화된 액세스를 제공합니다.
* 인쇄 및 웹 채널을 위한 통합 저작 인터페이스 제공
* 적응형 Forms 제작과 유사한 드래그 앤 드롭 기반 제작 인터페이스를 인쇄 및 웹 채널에 제공합니다.

인터랙티브한 커뮤니케이션은 고객 커뮤니케이션을 제작하는 데 기본적으로 권장되고 있습니다. AEM 6.3 Forms 및 AEM 6.2 Forms에서 문자를 계속 사용하려면 호환성 패키지를 설치해야 합니다.

### 멀티채널 인터랙티브한 커뮤니케이션 제작 {#multi-channel-interactive-communication-authoring}

인터랙티브한 커뮤니케이션을 사용하면 하나의 문서 편집기에서 인쇄 및 웹 문서를 모두 작성하고 편집할 수 있습니다. 동일한 문서 조각을 사용하여 두 채널의 변환을 구축하면 중복 작업을 방지할 수 있습니다.
![printweb_2](assets/printweb_2.png)

자세한 내용은 [대화형 통신 개요를 참조하십시오](/help/forms/using/interactive-communications-overview.md).

### WYSIWYG 문서 편집기 {#wysiwyg-document-editor}

The WYSIWYG drag-and-drop document editor is business friendly. The intuitive interface, drag-and-drop functionality, standard components, data models, and integrated repository for assets facilitate quick and easy authoring of interactive communication.

Interactive communication을 생성하거나 기존 커뮤니케이션을 편집하려면 비즈니스 사용자는 다음 기본 구성 요소를 사용할 수 있습니다. 채널, 컨텐트, 속성, 자산, 구성 요소 및 데이터 소스.

![drag-n-drop-lf](assets/drag-n-drop-lf.png)

자세한 내용은 대화형 통신 [작성 소개를 참조하십시오](/help/forms/using/introduction-interactive-communication-authoring.md).

### 인터랙티브한 커뮤니케이션에서 인쇄 컨텐츠에서 웹 버전 자동 생성 {#auto-generate-web-version-from-print-content-in-interactive-communication}

작성자는 인쇄 문서에서 웹 문서 컨텐츠를 자동으로 생성하여 동일한 편집기에서 인쇄 및 웹 문서를 작성, 미리 보기 및 편집할 수 있습니다. 인터랙티브한 커뮤니케이션 작성자는 한 번의 제작으로 모든 채널에 퍼블리싱할 수 있습니다. 인터랙티브한 커뮤니케이션 작성자는 인쇄 및 웹 채널에서 동일한 문서 조각을 사용하여 중복 작업을 방지할 수 있습니다.

자세한 내용은 [채널 및 웹 채널 인쇄를 참조하십시오](/help/forms/using/web-channel-print-channel.md).

### 테마를 사용하여 인터랙티브한 커뮤니케이션의 웹 채널 스타일 지정 {#use-themes-to-style-web-channel-of-interactive-communication}

인터랙티브한 커뮤니케이션은 테마를 지원합니다. 테마를 만들어 인터랙티브한 커뮤니케이션에 적용할 수 있습니다. 테마는 구성 요소 및 패널에 대한 스타일 세부 사항을 포함합니다. 서로 다른 인터랙티브 커뮤니케이션에서 테마를 재사용하여 공통적이고 일관된 모양과 브랜딩을 제공할 수 있습니다.

AEM Forms에는 인터랙티브 커뮤니케이션을 위한 특별 테마가 포함되어 있습니다. 테마를 사용하여 대화형 통신이 장치에서 어떻게 보이는지 사용자 정의할 수도 있습니다.

자세한 내용은 AEM Forms의 [테마를 참조하십시오](/help/forms/using/themes.md).

### 향상된 에이전트 인터페이스 {#enhanced-agent-interface}

이제 에이전트 사용자 인터페이스는 인터랙티브 커뮤니케이션의 인쇄 및 웹 미리 보기를 지원합니다. 동일한 에이전트 사용자 인터페이스에서 인쇄 채널을 편집하고 다중 채널 대화형 커뮤니케이션의 웹 채널을 미리 볼 수 있습니다. 인쇄 채널의 필드, 변수, FDM 요소 및 문서 조각은 에이전트 사용자 인터페이스에서 에이전트가 수정하도록 구성할 수 있습니다. 양식 데이터 모델 지원을 사용하면 데이터의 자동 완성 결과를 통해 미리 보기를 생성할 수 있습니다.

자세한 내용은 [에이전트 UI를 사용하여 대화형 통신 준비 및 전송을 참조하십시오](/help/forms/using/prepare-send-interactive-communication.md).

### 차트에 정보 제공 {#present-information-in-charts}

인터랙티브한 커뮤니케이션은 리치 커뮤니케이션을 위해 웹과 인쇄 채널에서 차트를 지원합니다. 파이, 도넛, 막대 및 열과 같은 차트를 사용하면 많은 정보를 압축하고 시각적으로 표시하여 쉽게 해석하고 분석할 수 있습니다.

![차트-2](assets/chart-2.png) ![차트](assets/chart.png)

자세한 내용은 Interactive Communications [에서 차트 사용을 참조하십시오](/help/forms/using/chart-component-interactive-communications.md).

### 즉시 사용 가능한 데이터 커넥터를 통해 문서 미리 채우기 {#out-of-the-box-data-connectors-to-prefill-documents}

인터랙티브한 커뮤니케이션은 비즈니스 툴과 데이터를 통합하여 CRM 시스템 등 다양한 비즈니스 시스템과 연결하고 데이터를 문서로 개인화합니다.

![fdm_ad](assets/fdm_ad.png)

자세한 내용은 양식 데이터 모델 [사용을 참조하십시오](/help/forms/using/using-form-data-model.md).

### 향상된 문서 조각 편집기 {#enhanced-document-fragment-editor}

이제 대화형 통신의 문서 조각 내에서 FDM 요소 및 규칙을 사용할 수 있습니다.

* 양식 데이터 모델 요소 지원
* 규칙을 사용하여 자산/텍스트 조각 표시 또는 숨기기
* 요소/변수의 값 유효성 확인
* 함수를 실행하여 수학 표현식의 값을 계산합니다.

자세한 내용은 다음을 참조하십시오.

* [인터랙티브 커뮤니케이션의 텍스트](/help/forms/using/texts-interactive-communications.md)
* [인터랙티브 커뮤니케이션 조건](/help/forms/using/conditions-interactive-communications.md)

### 기존 에셋용 호환성 패키지 {#compatibility-package-for-existing-assets}

기본적으로 이 릴리스에서는 이전 버전의 AEM Forms의 서신 에셋이 지원되지 않습니다. AEM 6.3 Forms 및 AEM 6.2 Forms의 문자를 계속 사용하려면 호환성 패키지를 설치해야 합니다.

## 데이터 통합 {#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms 데이터 통합](/help/forms/using/data-integration.md) 기능을 사용하면 서로 다른 데이터 소스를 구성할 수 있습니다. 데이터베이스, RESTful 또는 SOAP 기반 웹 서비스, OData 서비스 등 을 클릭하여 데이터 바인딩, 자동 채우기 및 서비스 불러오기 등에 사용할 수 있는 양식 데이터 모델을 생성합니다.

이번 릴리스에는 데이터 통합에 대한 몇 가지 새로운 기능과 개선 사항이 있습니다.

### 데이터 소스 없이 양식 데이터 모델 만들기 {#create-form-data-model-without-data-source}

이제 비즈니스 사용자와 양식 작성자는 데이터 소스를 구성하지 않고 개체 및 속성을 포함한 양식 데이터 모델을 만들 수 있으며 적응형 양식 및 문서를 작성하는 데 사용할 수 있습니다. 나중에 양식 데이터 모델을 데이터 소스에 바인딩할 수 있습니다. 양식 데이터 모델을 사용하여 양식과 문서를 작성할 때 데이터 소스에 대한 의존성을 없애줍니다.

마찬가지로 기존 양식 데이터 모델에서 엔티티 및 자식 속성을 만들고 나중에 데이터 소스의 해당 엔티티 및 속성에 바인딩할 수 있습니다.

자세한 내용은 양식 데이터 모델 [만들기를 참조하십시오](/help/forms/using/create-form-data-models.md).

### 계산된 속성 만들기 {#create-computed-properties}

Forms 작성자 및 개발자는 양식 데이터 모델에서 계산된 속성을 만들 수 있습니다. 구성된 데이터 소스에서 사용할 수 있는 데이터에 대한 규칙 또는 논리를 만들어 속성 값을 계산할 수 있습니다. 규칙은 데이터 데이터가 양식 데이터 모델 또는 표현식의 속성 값으로 로드될 때 평가되는 식입니다. 예를 들어, 할부로 불리는 계산된 속성은 데이터 소스에 지정된 이자율과 양식에 사용자가 지정한 대출 금액 및 종속을 기준으로 대부에 대해 지급될 월별 금액을 계산합니다.

계산된 속성은 양식 데이터 모델에 로컬로 존재하며 데이터 소스에 존재하지 않습니다. 계산된 속성을 적응형 양식 및 인터랙티브한 커뮤니케이션에서 사용할 수 있습니다.

자세한 내용은 [양식 데이터 모델을 사용한 작업을 참조하십시오](/help/forms/using/work-with-form-data-model.md).

### 샘플 데이터로 양식 및 문서 미리 보기 {#preview-forms-and-documents-with-sample-data}

양식 데이터 모델을 사용하면 양식 데이터 모델에서 모든 개체의 속성에 대한 샘플 데이터를 생성할 수 있습니다. 생성된 데이터는 속성에 구성된 데이터 유형에 해당합니다. 양식 데이터 모델과 연관된 적응형 양식 또는 문서를 미리 보면 자동으로 채워진 샘플 데이터로 렌더링됩니다.

샘플 데이터는 생성할 때마다 변경되는 임의 값 세트입니다. 그러나 다시 생성되더라도 지속되는 샘플 데이터를 편집하고 저장할 수 있습니다. 예를 들어 이름 및 성 속성에 대한 샘플 데이터를 편집 및 저장하고 나중에 양식 데이터 모델에서 다른 속성이나 엔티티를 추가하고 샘플 데이터를 재생성하는 경우 이름 및 성 속성은 저장된 값을 표시하고 다른 속성에 대한 값은 다시 생성됩니다.

자세한 내용은 양식 데이터 모델 [사용을 참조하십시오](/help/forms/using/using-form-data-model.md).

### Refresh data source definitions {#refresh-data-source-definitions}

데이터 소스 엔티티 또는 속성의 업데이트는 관련 양식 데이터 모델에 자동으로 반영되지 않습니다. 이제 양식 데이터 모델 편집기는 서버 캐시를 무효화하고 데이터 소스에서 업데이트된 스키마를 가져와서 즉시 양식 데이터 모델에 반영하는 ![refresh_forms_di](assets/refresh_forms_di.png) (데이터 소스 정의 새로 고침)를 제공합니다.

### 터치 사용자 인터페이스를 사용하여 데이터 소스 구성 {#configure-data-sources-using-touch-user-interface}

이번 릴리스에서는 데이터 소스에 대한 클라우드 서비스 구성을 Touch 사용자 인터페이스에서 사용할 수 있습니다. 또한 클라우드 서비스 구성 위치가 **[!UICONTROL 도구 > Cloud Services > 데이터 소스로 변경되었습니다]**. 데이터 [소스 구성을 참조하십시오](/help/forms/using/configure-data-sources.md).

## 적응형 양식 {#adaptive-forms}

![simplify-of-authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### 향상된 레이지 로딩을 통해 적응형 양식의 성능 향상 {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

적응형 양식의 레이지 로딩 기능은 필요한 양식 조각에 대한 초기화를 방지합니다. 양식을 렌더링하는 데 필요한 시간을 최소화하여 큰 양식의 성능을 향상시켜주므로 사용자 경험을 향상시킬 수 있습니다.

이 릴리스에는 레이지 로드 기능이 몇 가지 개선되었습니다.

* 파일 첨부 및 약관 구성 요소는 지연 로딩 기능이 활성화된 양식 조각에서 지원됩니다.
* 레이지 로딩 기능이 활성화된 적응형 양식 조각은 반복 가능한 패널에서 지원됩니다.
* 지연 로딩 지원 조각이 있는 적응형 양식은 AEM Forms 앱에서 지원됩니다.

## Forms 중심 AEM 워크플로우 {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

Forms 중심의 AEM 워크플로우 기능을 사용하면 OSGi 스택에서 다양한 작업을 위한 워크플로우를 신속하게 구축하고 배포할 수 있습니다. 더 이상 JEE 스택에서 사용할 수 있는 프로세스 관리 기능을 설치할 필요가 없으므로 배포가 단순해지고 애플리케이션 서버와 인프라 비용이 줄어듭니다. 자세한 내용은 OSGi에서 [Forms 중심의 워크플로우를 참조하십시오](/help/forms/using/aem-forms-workflow.md).

Forms 중심 AEM 워크플로우의 향상된 기능은 다음과 ・ 같습니다.

* 워크플로우 모델 편집기는 터치 사용자 인터페이스에서 사용할 수 있습니다. 양식 중심의 AEM 워크플로우를 제작하는 데 필요한 시간을 줄일 수 있습니다.
* 이메일 전송을 위한 워크플로우 단계 예를 들어 이메일 단계를 사용하여 워크플로우 완료 시 기록 문서를 보낼 수 있습니다.
* 워크플로우 모델에서 양식 데이터 모델 서비스를 사용하는 워크플로우 단계 이 단계에서는 사용자 지정 코드를 작성하지 않고도 데이터 통합 서비스를 호출할 수 있습니다. 예를 들어, 사용자 지정 코드를 작성하지 않고도 GET 서비스를 호출하여 데이터베이스 보관소에서 직원 세부 정보를 가져올 수 있습니다.

## AEM Forms 앱 {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

현장 작업자는 AEM Forms 앱을 사용하여 모바일 장치를 AEM Forms 서버와 동기화하고 양식을 작업할 수 있습니다. 디바이스가 오프라인 상태인 경우 디바이스에서 로컬로 데이터를 저장하고 디바이스가 다시 온라인 상태일 때 서버와 데이터를 동기화하면 애플리케이션이 원활하게 작동합니다. 자세한 내용은 [AEM Forms 앱을 참조하십시오](/help/forms/using/aem-forms-app.md).

AEM Forms 앱의 향상된 기능은 다음과 같습니다.

* 지연 로딩 지원 조각이 있는 적응형 양식은 AEM Forms 앱에서 지원됩니다.
* 양식 데이터 모델이 있는 적응형 양식은 AEM Forms 앱에서 지원됩니다.

## 문서 보안 {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

문서 보안을 사용하면 지원되는 형식으로 저장한 모든 정보를 안전하게 배포할 수 있습니다. 문서 보안은 권한이 있는 사용자만 문서를 사용할 수 있도록 합니다. 다음은 문서 보안의 주요 변경 사항입니다.

* 문서 보안은 PPL( [Portable Protection Library)](/help/forms/using/document-security-offerings.md) 을 제공하여 문서를 AEM Forms 서버로 전송하지 않고도 로컬에서 문서를 보호합니다. 보안 자격 증명과 정책 세부 사항만 네트워크를 통해 AEM Forms 서버로 이동합니다. AEM 6.4 Forms은 OSGi 번들 포맷으로 PL(Portable Protection Library)을 도입했습니다. 이제 AEM Forms 서버에 PPL 라이브러리를 직접 설치하고 AEM 및 PPL의 기능을 함께 사용할 수 있습니다.
* 문서 보안 C++ SDK 및 C++ PL 라이브러리는 Microsoft Visual Studio 2013으로 컴파일할 수 있습니다. 이전에 지원되는 버전은 Microsoft Visual Studio 2010입니다.

## 지원되는 플랫폼 {#supported-platforms}

AEM Forms은 지원되는 운영 체제, 애플리케이션 서버, 데이터베이스, 데이터베이스 드라이버, JDK, LDAP 서버 및 이메일 서버를 조합하여 설정할 수 있습니다. 지원되는 플랫폼의 주요 변경 사항은 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td>구성 요소</td> 
   <td>지원 추가됨</td> 
   <td>지원 제거됨</td> 
  </tr> 
  <tr> 
   <td>운영 체제</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>Oracle Linux 7 업데이트 3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>애플리케이션 서버<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>데이터베이스</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19 이상</li> 
     <li>IBM DB2 11.1</li> 
     <li>Oracle 멀티 테넌트 아키텍처</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>LDAP 서버</td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2016</li> 
     <li>IBM Tivoli Directory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2008</li> 
     <li>IBM Tivoli Directory Server 6.3</li> 
     <li>Oracle Directory Server Enterprise Edition 7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>이메일 서버</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell Groupwise 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>커넥터</td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2016용 커넥터</li> 
     <li>Connector for EMC Documentum 7.3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2007용 커넥터</li> 
     <li>Microsoft Sharepoint 2010용 커넥터</li> 
     <li>IBM Filenet 5.0용 커넥터</li> 
     <li>Connector for EMC Documentum 6.7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>브라우저</td> 
   <td> 
    <ul> 
     <li>macOS 기반의 Apple Safari 11.x</li> 
     <li>iOS 기반의 Apple Safari 11.x</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Blackberry Z30 및 Q10 디바이스용 Blackberry 브라우저</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms app<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4 이상</li> 
     <li>Apple iOS 10 이상</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. AIX 및 Solaris 운영 체제는 업그레이드 고객에게만 제공됩니다.
