---
title: 새로운 기능 요약 | AEM 6.4 Forms
seo-title: 새로운 기능 요약 | AEM 6.4 Forms
description: AEM 6.4 Forms의 새로운 기능 및 개선 사항에 대한 요약입니다.
seo-description: AEM 6.4 Forms의 새로운 기능 및 개선 사항에 대한 요약입니다.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
translation-type: tm+mt
source-git-commit: f2b0d37a0666f2a0be9e7034da12dddf0c56fb25
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---


# 새로운 기능 요약 | AEM 6.4 Forms {#new-features-summary-aem-forms}

AEM 6.4 Forms의 새로운 기능 및 개선 사항에 대한 요약입니다.

AEM Forms에는 적응형 양식 및 인터랙티브한 커뮤니케이션을 통해 작성, 관리 및 사용자 경험을 보다 효율적으로 관리할 수 있는 새로운 기능과 향상된 기능이 포함되어 있습니다.

새로운 기능과 향상된 기능에 대한 빠른 소개를 살펴보십시오. 자세한 내용은 설명서를 참조하십시오. 또한 AEM 6.4 Forms [릴리스 노트](/help/release-notes/forms.md)를 참조하십시오. 전체 AEM 6.4 Forms 문서는 [AEM 6.4 Forms Guide](/help/forms/home.md)를 참조하십시오.

## 대화형 통신 {#interactive-communications}

![통신 관리](assets/correspondence-management.png)

Interactive Communications는 비즈니스 서신, 편지, 문서, 명세서, 혜택 정보, 자산 관리 설명서, 마케팅 이메일, 청구서 및 환영 키트와 같은 안전하고 개인화된 인터랙티브한 통신의 작성, 조합 및 전달을 중앙 집중화하고 관리합니다.

인터랙티브 커뮤니케이션은 적응형 양식과 동일한 기본 기술, 프로세스 및 구성 요소를 사용하여 반응형 적응형 양식과 유사한 반응형 멀티채널 커뮤니케이션을 제작할 수 있습니다.

인터랙티브한 커뮤니케이션은 다음과 같은 이점을 제공합니다.

* 양식 데이터 모델과 OOTB 통합을 통해 백엔드 데이터베이스 및 MS Dynamics와 같은 기타 CRM 시스템에 간편하고 간소화된 액세스를 제공할 수 있습니다.
* 인쇄 및 웹 채널을 위한 통합 저작 인터페이스 제공
* 인쇄 및 웹 채널에 대해 적응형 Forms 작성과 유사한 드래그 앤 드롭 기반 제작 인터페이스를 제공합니다.

인터랙티브한 커뮤니케이션은 고객 커뮤니케이션을 제작하는 데 기본적으로 권장되고 있습니다. AEM 6.3 Forms 및 AEM 6.2 Forms에서 문자를 계속 사용하려면 호환성 패키지를 설치해야 합니다.

### 다중 채널 대화형 통신 제작 {#multi-channel-interactive-communication-authoring}

인터랙티브한 커뮤니케이션을 통해 하나의 문서 편집기에서 인쇄 및 웹 문서를 모두 작성하고 편집할 수 있습니다. 동일한 문서 조각을 사용하여 두 채널의 변환을 구축하면 중복 작업을 없앨 수 있습니다.
![printweb_2](assets/printweb_2.png)

자세한 내용은 [대화형 통신 개요](/help/forms/using/interactive-communications-overview.md)를 참조하십시오.

### WYSIWYG 문서 편집기 {#wysiwyg-document-editor}

WYSIWYG 드래그 앤 드롭 방식의 문서 편집기는 비즈니스에 적합합니다. 직관적인 인터페이스, 드래그 앤 드롭 기능, 표준 구성 요소, 데이터 모델 및 에셋 통합 저장소를 통해 인터랙티브한 커뮤니케이션을 빠르고 손쉽게 제작할 수 있습니다.

Interactive communication을 생성하거나 기존 커뮤니케이션을 편집하려면 비즈니스 사용자는 다음 기본 구성 요소를 사용할 수 있습니다.채널, 컨텐츠, 속성, 자산, 구성 요소 및 데이터 소스.

![drag-n-drop-lf](assets/drag-n-drop-lf.png)

자세한 내용은 [대화형 통신 작성 소개](/help/forms/using/introduction-interactive-communication-authoring.md)를 참조하십시오.

### 인터랙티브한 커뮤니케이션에서 인쇄 컨텐츠에서 웹 버전 자동 생성 {#auto-generate-web-version-from-print-content-in-interactive-communication}

작성자는 인쇄 문서에서 웹 문서 컨텐츠를 자동으로 생성하여 동일한 편집기에서 인쇄 및 웹 문서를 모두 작성, 미리 보기 및 편집할 수 있습니다. 인터랙티브한 커뮤니케이션 작성자는 한 번의 제작으로 모든 채널에 퍼블리싱할 수 있습니다. 인터랙티브한 커뮤니케이션 작성자는 인쇄 및 웹 채널에서 동일한 문서 조각을 사용하여 중복 작업을 방지할 수 있습니다.

자세한 내용은 [인쇄 채널 및 웹 채널](/help/forms/using/web-channel-print-channel.md)을 참조하십시오.

### 테마를 사용하여 대화형 커뮤니케이션의 웹 채널 스타일 지정 {#use-themes-to-style-web-channel-of-interactive-communication}

인터랙티브한 커뮤니케이션은 테마를 지원합니다. 테마를 만들고 인터랙티브한 커뮤니케이션에 적용할 수 있습니다. 테마는 구성 요소 및 패널에 대한 스타일 세부 사항을 포함합니다. 서로 다른 인터랙티브한 커뮤니케이션에서 테마를 재사용하여 공통적이고 일관된 모양과 브랜딩을 제공할 수 있습니다.

AEM Forms에는 대화형 통신을 위한 기본 테마가 포함되어 있습니다. 테마를 사용하여 대화형 통신이 장치에서 어떻게 보이는지를 사용자 정의할 수도 있습니다.

자세한 내용은 AEM Forms](/help/forms/using/themes.md)의 [테마를 참조하십시오.

### 향상된 에이전트 인터페이스 {#enhanced-agent-interface}

이제 Agent 사용자 인터페이스는 대화형 통신의 인쇄 및 웹 미리 보기를 지원합니다. 동일한 에이전트 사용자 인터페이스에서 인쇄 채널을 편집하고 다중 채널 대화형 커뮤니케이션의 웹 채널을 미리 보도록 선택할 수 있습니다. 인쇄 채널의 필드, 변수, FDM 요소 및 문서 조각은 에이전트 사용자 인터페이스에서 에이전트가 수정하도록 구성할 수 있습니다. 양식 데이터 모델 지원을 통해 데이터의 자동 완성 결과를 통해 미리 보기를 생성할 수 있습니다.

자세한 내용은 에이전트 UI[를 사용하여 대화형 통신 준비 및 전송을 참조하십시오.](/help/forms/using/prepare-send-interactive-communication.md)

### 차트에 정보 표시{#present-information-in-charts}

인터랙티브한 커뮤니케이션은 보다 풍부한 커뮤니케이션을 위해 웹과 인쇄 채널의 차트를 지원합니다. 파이, 도넛, 막대 및 열과 같은 차트를 사용하여 많은 정보를 압축하고 시각적으로 표시하여 쉽게 해석하고 분석할 수 있습니다.

![chart-2](assets/chart-2.png) ![차트](assets/chart.png)

자세한 내용은 [Interactive Communications에서 차트 사용](/help/forms/using/chart-component-interactive-communications.md)을 참조하십시오.

### 바로 사용 가능한 데이터 커넥터로 문서를 미리 채우기 {#out-of-the-box-data-connectors-to-prefill-documents}

인터랙티브한 커뮤니케이션은 비즈니스 툴과 데이터를 통합하여 CRM 시스템 등 다양한 비즈니스 시스템과 연계하고 데이터를 문서로 개인화할 수 있습니다.

![fdm_ad](assets/fdm_ad.png)

자세한 내용은 [양식 데이터 모델 사용](/help/forms/using/using-form-data-model.md)을 참조하십시오.

### 향상된 문서 조각 편집기 {#enhanced-document-fragment-editor}

이제 대화형 통신의 문서 단편 내에서 FDM 요소 및 규칙을 사용할 수 있습니다.

* 양식 데이터 모델 요소 지원
* 규칙을 사용하여 자산/텍스트 조각 표시 또는 숨기기
* 요소/변수의 값 유효성 확인
* 함수를 실행하여 수학 표현식의 값을 계산합니다.

자세한 내용은 다음을 참조하십시오.

* [인터랙티브 커뮤니케이션의 텍스트](/help/forms/using/texts-interactive-communications.md)
* [인터랙티브 커뮤니케이션의 조건](/help/forms/using/conditions-interactive-communications.md)

### 기존 에셋에 대한 호환성 패키지 {#compatibility-package-for-existing-assets}

기본적으로 이 릴리스에서는 이전 버전의 AEM Forms의 편지 에셋이 지원되지 않습니다. AEM 6.3 Forms 및 AEM 6.2 Forms의 문자를 계속 사용하려면 호환성 패키지를 설치해야 합니다.

## 데이터 통합 {#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms 데이터 ](/help/forms/using/data-integration.md) 통합을 사용하여 서로 다른 데이터 소스를 구성할 수 있습니다.데이터베이스, RESTful 또는 SOAP 기반 웹 서비스, OData 서비스 등적응형 양식 및 문서에서 데이터를 바인딩하고, 미리 채우고, 서비스를 호출하는 데 사용할 수 있는 양식 데이터 모델을 만듭니다.

이번 릴리스에는 여러 가지 새로운 기능과 향상된 데이터 통합 기능이 있습니다.

### 데이터 소스 {#create-form-data-model-without-data-source} 없이 양식 데이터 모델 만들기

이제 비즈니스 사용자와 양식 작성자는 데이터 소스를 구성하지 않고도 개체 및 속성을 비롯한 양식 데이터 모델을 만들 수 있으며 적응형 양식 및 문서를 작성하는 데 사용할 수 있습니다. 나중에 양식 데이터 모델을 데이터 소스에 바인딩할 수 있습니다. 양식 데이터 모델을 사용하여 양식과 문서를 작성할 때 데이터 소스에 대한 의존성을 없애줍니다.

마찬가지로 기존 양식 데이터 모델에서 엔티티와 자식 속성을 만들고 나중에 데이터 소스의 해당 엔티티와 속성에 바인딩할 수 있습니다.

자세한 내용은 [양식 데이터 모델 만들기](/help/forms/using/create-form-data-models.md)를 참조하십시오.

### 계산된 속성 {#create-computed-properties} 만들기

Forms 작성자 및 개발자는 양식 데이터 모델에서 계산된 속성을 만들 수 있습니다. 구성된 데이터 소스에서 사용할 수 있는 데이터에 대한 규칙 또는 논리를 만들어 속성 값을 계산할 수 있습니다. 규칙은 데이터 데이터가 양식 데이터 모델에서 로드되거나 표현식의 속성 값을 변경할 때 평가되는 표현식입니다. 예를 들어, 할부로 불리는 계산된 속성은 데이터 소스에 지정된 이자율과 양식에 사용자가 지정한 대출 금액 및 테뉴어를 기준으로 대부에 대해 지급될 월별 금액을 계산합니다.

계산된 속성은 양식 데이터 모델에 로컬로 있으며 데이터 소스에 존재하지 않습니다. 계산된 속성을 적응형 양식 및 대화형 커뮤니케이션에서 사용할 수 있습니다.

자세한 내용은 [양식 데이터 모델 작업](/help/forms/using/work-with-form-data-model.md)을 참조하십시오.

### 양식 및 문서 미리 보기(샘플 데이터 {#preview-forms-and-documents-with-sample-data})

양식 데이터 모델을 사용하면 양식 데이터 모델에 있는 모든 엔티티의 속성에 대한 샘플 데이터를 생성할 수 있습니다. 생성된 데이터는 속성에 구성된 데이터 유형에 해당합니다. 양식 데이터 모델과 연관된 적응형 양식 또는 문서를 미리 보면 데이터의 자동 완성 결과가 나타납니다.

샘플 데이터는 생성할 때마다 변경되는 임의 값 세트입니다. 그러나 다시 생성되더라도 지속되는 샘플 데이터를 편집하고 저장할 수 있습니다. 예를 들어 이름 및 성 속성에 대한 샘플 데이터를 편집 및 저장하고 나중에 양식 데이터 모델에서 다른 속성 또는 엔티티를 추가하고 샘플 데이터를 다시 생성하는 경우 이름 및 성 속성은 저장된 값을 표시하고 다른 속성에 대한 값은 다시 생성됩니다.

자세한 내용은 [양식 데이터 모델 사용](/help/forms/using/using-form-data-model.md)을 참조하십시오.

### 데이터 소스 정의 새로 고침 {#refresh-data-source-definitions}

데이터 소스 엔티티 또는 속성의 업데이트는 관련 양식 데이터 모델에 자동으로 반영되지 않습니다. 양식 데이터 모델 편집기는 이제 서버 캐시를 무효화하고 데이터 소스에서 업데이트된 스키마를 가져와서 양식 데이터 모델에 즉시 반영하도록 ![refresh_forms_di](assets/refresh_forms_di.png)(데이터 소스 정의 새로 고침) 기능을 제공합니다.

### 터치 사용자 인터페이스 {#configure-data-sources-using-touch-user-interface}을(를) 사용하여 데이터 소스 구성

이번 릴리스에서는 Touch 사용자 인터페이스에서 데이터 소스에 대한 클라우드 서비스 구성을 사용할 수 있습니다. 또한 클라우드 서비스를 구성할 위치가 **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**&#x200B;로 변경되었습니다. [데이터 소스 구성](/help/forms/using/configure-data-sources.md)을 참조하십시오.

## 적응형 양식 {#adaptive-forms}

![simplify-of-authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### 향상된 지연 로딩 {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading} 기능으로 적응형 양식의 성능 향상

적응형 양식의 레이지 로드 기능은 필요한 양식 조각에 대한 초기화를 정의합니다. 양식을 렌더링하는 데 필요한 시간을 최소화하여 큰 양식의 성능을 향상시킴으로써 사용자 경험이 향상됩니다.

이 릴리스에는 레이지 로드 기능이 몇 가지 개선되었습니다.

* 파일 첨부 파일 및 약관 구성 요소는 지연 로딩이 활성화된 양식 조각에서 지원됩니다.
* 레이지 로딩이 활성화된 적응형 양식 조각은 반복 가능한 패널에서 지원됩니다.
* 레이지 로딩 지원 조각이 있는 적응형 양식이 AEM Forms 앱에서 지원됩니다.

## Forms 중심의 AEM 워크플로우 {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

Forms 중심의 AEM 워크플로우 기능을 사용하면 OSGi 스택에서 다양한 작업을 위한 워크플로우를 신속하게 구축하고 배포할 수 있습니다. 더 이상 JEE 스택에 사용할 수 있는 프로세스 관리 기능을 설치하지 않아도 되므로 배포 작업을 단순화하고 애플리케이션 서버 및 인프라 비용을 절감할 수 있습니다. 자세한 내용은 OSGi](/help/forms/using/aem-forms-workflow.md)의 [Forms 중심 워크플로우를 참조하십시오.

Forms 중심의 AEM 워크플로우의 향상된 기능은 다음과 ・ 같습니다.

* 워크플로우 모델 편집기는 터치 사용자 인터페이스에서 사용할 수 있습니다. 양식 중심의 AEM 워크플로우를 만드는 데 필요한 시간을 줄일 수 있습니다.
* 이메일을 보내는 워크플로우 단계 예를 들어 이메일 단계를 사용하여 워크플로우 완료 시 기록 문서를 보낼 수 있습니다.
* 워크플로우 모델에서 양식 데이터 모델 서비스를 사용하는 워크플로우 단계 이 단계에서는 사용자 지정 코드를 작성하지 않고도 데이터 통합 서비스를 호출할 수 있습니다. 예를 들어, GET 서비스를 호출하여 사용자 정의 코드를 작성하지 않고도 데이터베이스 아카이브에서 직원 세부 정보를 가져올 수 있습니다.

## AEM Forms 앱 {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

현장 작업자는 AEM Forms 앱을 사용하여 모바일 장치를 AEM Forms 서버와 동기화하고 양식을 편집할 수 있습니다. 디바이스가 오프라인 상태인 경우 디바이스가 디바이스에서 로컬로 데이터를 저장하고 디바이스가 다시 온라인 상태일 때 서버와 데이터를 동기화하면 애플리케이션이 원활하게 작동합니다. 자세한 내용은 [AEM Forms 앱](/help/forms/using/aem-forms-app.md)을 참조하십시오.

AEM Forms 앱의 향상된 기능은 다음과 같습니다.

* 레이지 로딩 지원 조각이 있는 적응형 양식이 AEM Forms 앱에서 지원됩니다.
* 양식 데이터 모델이 있는 적응형 양식은 AEM Forms 앱에서 지원됩니다.

## 문서 보안 {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

문서 보안을 사용하면 지원되는 형식으로 저장한 모든 정보를 안전하게 배포할 수 있습니다. 문서 보안은 권한이 있는 사용자만 문서를 사용할 수 있도록 합니다. 다음은 문서 보안의 주요 변경 사항입니다.

* 문서 보안은 문서를 AEM Forms 서버로 전송하지 않고 문서를 로컬에서 보호할 수 있는 [PPL(Portable Protection Library)](/help/forms/using/document-security-offerings.md)을 제공합니다. 보안 자격 증명과 정책 세부 사항만 네트워크를 통해 AEM Forms 서버로 이동합니다. AEM 6.4 Forms은 OSGi 번들 포맷의 PPL(Portable Protection Library)을 도입했습니다. 이제 AEM Forms 서버에 PPL 라이브러리를 직접 설치하고 AEM 및 PPL의 기능을 함께 사용할 수 있습니다.
* 문서 보안 C++ SDK 및 C++ PPL 라이브러리는 Microsoft Visual Studio 2013으로 컴파일할 수 있습니다. 이전에 지원되는 버전은 Microsoft Visual Studio 2010입니다.

## 지원되는 플랫폼 {#supported-platforms}

AEM Forms은 지원되는 운영 체제, 애플리케이션 서버, 데이터베이스, 데이터베이스 드라이버, JDK, LDAP 서버 및 이메일 서버를 조합하여 설정할 수 있습니다. 지원되는 플랫폼의 주요 변경 사항은 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td>구성 요소</td> 
   <td>지원 추가됨</td> 
   <td>제거된 지원</td> 
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
   <td>응용 프로그램 서버<br /> </td> 
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
     <li>macOS의 Apple Safari 11.x</li> 
     <li>iOS의 Apple Safari 11.x</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Blackberry Z30 및 Q10 디바이스용 Blackberry 브라우저</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms 앱<br /> </td> 
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
