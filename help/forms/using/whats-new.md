---
title: 새로운 기능 요약 | AEM 6.4 Forms
seo-title: 새로운 기능 요약 | AEM 6.4 Forms
description: AEM 6.4 Forms의 새로운 기능 및 개선 사항 요약
seo-description: AEM 6.4 Forms의 새로운 기능 및 개선 사항 요약
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
exl-id: 21b8ed83-9c0c-41ee-9fbb-56ccebaee132
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---

# 새로운 기능 요약 | AEM 6.4 Forms {#new-features-summary-aem-forms}

AEM 6.4 Forms의 새로운 기능 및 개선 사항 요약

AEM Forms에는 적응형 양식 및 대화형 커뮤니케이션으로 만들기, 관리 및 사용자 경험을 더욱 간소화하는 몇 가지 새로운 기능과 개선 사항이 포함되어 있습니다.

새로운 기능 및 개선 사항에 대한 빠른 소개를 살펴보십시오. 자세한 내용을 제공하는 리소스는 설명서 를 참조하십시오. 또한 AEM 6.4 Forms [릴리스 노트](/help/release-notes/forms.md)를 참조하십시오. 전체 AEM 6.4 Forms 설명서는 [AEM 6.4 Forms 안내서](/help/forms/home.md)를 참조하십시오.

## 대화형 통신 {#interactive-communications}

![서신 관리](assets/correspondence-management.png)

Interactive Communications는 비즈니스 서신, 편지, 문서, 명세서, 혜택 공지, 재산 관리 설명서, 마케팅 이메일, 청구서 및 환영 키트와 같은 안전하고 개인화된 인터랙티브한 통신의 작성, 수집 및 전달을 중앙 집중화하여 관리합니다.

대화형 커뮤니케이션은 적응형 양식과 동일한 기본 기술, 프로세스 및 구성 요소를 사용하여 반응형 적응형 양식과 같은 반응형 다중 채널 통신을 만듭니다.

대화형 커뮤니케이션은 다음과 같은 중요한 이점을 제공합니다.

* 양식 데이터 모델과 OOTB를 통합하여 백엔드 데이터베이스 및 MS Dynamics 등의 기타 CRM 시스템에 쉽고 효율적으로 액세스할 수 있도록 합니다
* 인쇄 및 웹 채널을 위한 통합 제작 인터페이스 제공
* 인쇄 및 웹 채널 모두를 위한 적응형 Forms 작성과 유사한 드래그 앤 드롭 기반 작성 인터페이스를 제공합니다.

대화형 커뮤니케이션은 고객 커뮤니케이션을 만드는 기본적이고 권장되는 방법입니다. AEM 6.3 Forms 및 AEM 6.2 Forms에서 문자를 계속 사용하려면 호환성 패키지를 설치해야 합니다.

### 다중 채널 대화형 통신 작성 {#multi-channel-interactive-communication-authoring}

대화형 커뮤니케이션을 사용하면 하나의 문서 편집기에서 인쇄 문서와 웹 문서를 모두 작성 및 편집할 수 있습니다. 동일한 문서 조각을 사용하여 두 채널의 렌디션을 작성하면 중복 작업을 제거할 수 있습니다.
![printweb_2](assets/printweb_2.png)

자세한 내용은 [대화형 통신 개요](/help/forms/using/interactive-communications-overview.md)를 참조하십시오.

### WYSIWYG 문서 편집기 {#wysiwyg-document-editor}

WYSIWYG 드래그 앤 드롭 문서 편집기는 비즈니스 친화적입니다. 직관적인 인터페이스, 드래그 앤 드롭 기능, 표준 구성 요소, 데이터 모델 및 자산을 위한 통합 저장소를 통해 대화형 커뮤니케이션을 빠르고 쉽게 작성할 수 있습니다.

대화형 커뮤니케이션을 만들거나 기존 커뮤니케이션을 편집하려면 비즈니스 사용자는 다음 기본 구성 요소를 사용할 수 있습니다.채널, 컨텐츠, 속성, 자산, 구성 요소 및 데이터 소스.

![드래그 앤 드롭-lf](assets/drag-n-drop-lf.png)

자세한 내용은 [대화형 통신 작성 소개](/help/forms/using/introduction-interactive-communication-authoring.md)를 참조하십시오.

### 대화형 커뮤니케이션에서 인쇄 콘텐츠에서 웹 버전 자동 생성 {#auto-generate-web-version-from-print-content-in-interactive-communication}

작성자는 인쇄 문서에서 같은 편집기에서 인쇄 문서와 웹 문서를 모두 작성, 미리 보기 및 편집할 수 있도록 웹 문서 컨텐츠를 자동으로 생성할 수 있습니다. 대화형 통신 작성자는 한 번 만들고 모든 채널에 게시할 수 있습니다. 대화형 통신 작성자는 인쇄 및 웹 채널에서 동일한 문서 조각을 사용하여 작업의 중복을 방지할 수 있습니다.

자세한 내용은 [채널 및 웹 채널 인쇄](/help/forms/using/web-channel-print-channel.md)를 참조하십시오.

### 테마를 사용하여 대화형 커뮤니케이션의 웹 채널 스타일 지정 {#use-themes-to-style-web-channel-of-interactive-communication}

대화형 커뮤니케이션은 테마를 지원합니다. 테마를 만들고 대화형 커뮤니케이션에 적용할 수 있습니다. 테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있습니다. 다른 대화형 커뮤니케이션에서 테마를 다시 사용하여 공통적이고 일관된 모양과 브랜딩을 제공할 수 있습니다.

AEM Forms에는 대화형 커뮤니케이션에 대한 기본 테마가 포함되어 있습니다. 테마를 사용하여 대화형 커뮤니케이션이 장치에서 표시되는 방식을 사용자 지정할 수도 있습니다.

자세한 내용은 AEM Forms](/help/forms/using/themes.md)의 [테마 를 참조하십시오.

### 향상된 에이전트 인터페이스 {#enhanced-agent-interface}

이제 에이전트 사용자 인터페이스가 대화형 커뮤니케이션의 인쇄 및 웹 미리 보기를 지원합니다. 동일한 에이전트 사용자 인터페이스에서 인쇄 채널을 편집하고 다중 채널 대화형 커뮤니케이션의 웹 채널을 미리 보도록 선택할 수 있습니다. 인쇄 채널의 필드, 변수, FDM 요소 및 문서 조각은 에이전트 사용자 인터페이스의 에이전트가 수정하도록 구성할 수 있습니다. 양식 데이터 모델 지원을 통해 미리 채워진 샘플 데이터를 사용하여 미리 보기를 생성할 수 있습니다.

자세한 내용은 [에이전트 UI](/help/forms/using/prepare-send-interactive-communication.md)를 사용하여 대화형 통신 준비 및 전송을 참조하십시오.

### 차트 {#present-information-in-charts}에 정보 표시

대화형 커뮤니케이션은 웹 및 인쇄 채널에서 더 많은 통신을 위해 차트를 지원합니다. 파이, 도넛, 막대 및 열과 같은 차트를 사용하면 많은 정보를 압축하고 시각적으로 표시할 수 있으므로 쉽게 해석 및 분석할 수 있습니다.

![차트-2](assets/chart-2.png) ![차트](assets/chart.png)

자세한 내용은 [대화형 커뮤니케이션에서 차트 사용](/help/forms/using/chart-component-interactive-communications.md)을 참조하십시오.

### Data Connectors에서 문서 미리 채우기 {#out-of-the-box-data-connectors-to-prefill-documents}

대화형 커뮤니케이션은 비즈니스 도구와 데이터 통합을 제공하여 CRM 시스템을 비롯한 여러 비즈니스 시스템과 연결하고 데이터를 문서로 개인화합니다.

![fdm_ad](assets/fdm_ad.png)

자세한 내용은 [양식 데이터 모델 사용](/help/forms/using/using-form-data-model.md)을 참조하십시오.

### 향상된 문서 조각 편집기 {#enhanced-document-fragment-editor}

이제 대화형 커뮤니케이션의 문서 조각 내에서 FDM 요소와 규칙을 사용할 수 있습니다.

* 양식 데이터 모델 요소 지원
* 규칙을 사용하여 자산/텍스트 조각을 표시하거나 숨깁니다.
* 요소/변수의 값 유효성 검사
* 함수를 실행하여 수학 표현식의 값을 계산합니다.

자세한 내용은 다음을 참조하십시오.

* [대화형 커뮤니케이션의 텍스트](/help/forms/using/texts-interactive-communications.md)
* [대화형 커뮤니케이션의 조건](/help/forms/using/conditions-interactive-communications.md)

### 기존 자산에 대한 호환성 패키지 {#compatibility-package-for-existing-assets}

기본적으로 이 릴리스에서는 이전 버전의 AEM Forms의 편지 자산이 지원되지 않습니다. AEM 6.3 Forms 및 AEM 6.2 Forms의 문자를 계속 사용하려면 호환성 패키지를 설치해야 합니다.

## 데이터 통합 {#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms 데이터 ](/help/forms/using/data-integration.md) 통합을 사용하여 서로 다른 데이터 소스를 구성할 수 있습니다.데이터베이스, RESTful 또는 SOAP 기반 웹 서비스, OData 서비스 등적응형 양식 및 문서에서 데이터를 바인딩하고, 미리 채우고, 서비스를 호출하는 데 사용할 수 있는 양식 데이터 모델을 만드는 데 사용됩니다.

이 릴리스에는 데이터 통합에서 몇 가지 새로운 기능과 개선 사항이 있습니다.

### 데이터 소스 {#create-form-data-model-without-data-source} 없이 양식 데이터 모델 만들기

이제 비즈니스 사용자 및 양식 작성자가 데이터 소스를 구성하지 않고 엔티티 및 속성을 포함하는 양식 데이터 모델을 만들 수 있으며 적응형 양식 및 문서를 작성하는 데 사용할 수 있습니다. 나중에 양식 데이터 모델을 데이터 소스에 바인딩할 수 있습니다. 양식 데이터 모델을 사용하여 양식 및 문서를 작성하는 데 데이터 소스에 대한 종속성을 제거합니다.

마찬가지로 기존 양식 데이터 모델에서 엔티티 및 하위 속성을 만들고 나중에 데이터 소스의 해당 엔티티 및 속성에 바인딩할 수 있습니다.

자세한 내용은 [양식 데이터 모델 만들기](/help/forms/using/create-form-data-models.md)를 참조하십시오.

### 계산된 속성 {#create-computed-properties} 만들기

Forms 작성자 및 개발자는 양식 데이터 모델에서 계산된 속성을 만들 수 있습니다. 구성된 데이터 소스에서 사용할 수 있는 데이터에 대한 규칙 또는 논리를 만들어 속성에 대한 값을 계산할 수 있습니다. 규칙은 데이터가 양식 데이터 모델로 로드되거나 표현식의 속성 값이 변경될 때 평가되는 표현식입니다. 예를 들어, [할부]라는 계산된 속성은 데이터 소스에 지정된 이자율과 사용자가 양식에 지정한 대출 금액 및 종신 기간에 따라 융자에 대해 지급할 월별 금액을 계산합니다.

계산된 속성은 양식 데이터 모델에 로컬로 있고 데이터 소스에 존재하지 않습니다. 적응형 양식 및 대화형 커뮤니케이션에서 계산된 속성을 사용할 수 있습니다.

자세한 내용은 [양식 데이터 모델 작업](/help/forms/using/work-with-form-data-model.md)을 참조하십시오.

### 샘플 데이터가 있는 양식 및 문서 미리 보기 {#preview-forms-and-documents-with-sample-data}

양식 데이터 모델을 사용하면 양식 데이터 모델에서 모든 엔티티의 속성에 대한 샘플 데이터를 생성할 수 있습니다. 생성된 데이터는 속성에 대해 구성된 데이터 유형에 해당합니다. 양식 데이터 모델과 연결된 적응형 양식 또는 문서를 미리 보면 미리 채워진 샘플 데이터와 함께 렌더링됩니다.

샘플 데이터는 생성할 때마다 변경되는 무작위 값 세트입니다. 그러나 샘플 데이터를 다시 생성하더라도 유지되는 샘플 데이터를 편집하고 저장할 수 있습니다. 예를 들어, 이름(First Name) 및 성(Last Name) 속성에 대한 샘플 데이터를 편집 및 저장하고 나중에 양식 데이터 모델에서 다른 속성 또는 엔티티를 추가하고 샘플 데이터를 재생성하는 경우 이름(First Name) 및 성(Last Name) 속성에 저장된 값이 표시되고 다른 속성에 대한 값이 재생성됩니다.

자세한 내용은 [양식 데이터 모델 사용](/help/forms/using/using-form-data-model.md)을 참조하십시오.

### 데이터 소스 정의 새로 고침 {#refresh-data-source-definitions}

데이터 소스 엔티티 또는 속성의 모든 업데이트는 관련 양식 데이터 모델에 자동으로 반영되지 않습니다. 이제 양식 데이터 모델 편집기에 서버 캐시를 무효화하고 데이터 소스에서 업데이트된 스키마를 가져와 양식 데이터 모델에 즉시 반영하는 ![refresh_forms_di](assets/refresh_forms_di.png) (데이터 소스 정의 새로 고침)가 제공됩니다.

### 터치 사용자 인터페이스 {#configure-data-sources-using-touch-user-interface}를 사용하여 데이터 소스를 구성합니다

이 릴리스에서는 데이터 소스에 대한 클라우드 서비스 구성을 Touch 사용자 인터페이스에서 사용할 수 있습니다. 또한 클라우드 서비스를 구성할 위치가 **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**&#x200B;로 변경되었습니다. [데이터 소스 구성](/help/forms/using/configure-data-sources.md)을 참조하십시오.

## 적응형 양식 {#adaptive-forms}

![simpliation of-authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### 향상된 지연 로드 {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading} 를 통해 적응형 양식의 성능 개선

적응형 양식의 지연 로드 기능은 양식 조각이 필요할 때까지 초기화됩니다. 양식을 렌더링하는 데 필요한 시간을 최소화하여 큰 양식의 성능을 향상시킴으로써 사용자 경험이 향상됩니다.

이 릴리스에서는 지연 로드 기능이 다음과 같이 개선되었습니다.

* 파일 첨부 파일 및 약관 구성 요소는 지연 로딩이 활성화된 양식 조각에서 지원됩니다.
* 지연 로딩이 활성화된 적응형 양식 조각은 반복 가능한 패널에서 지원됩니다.
* 지연 로드 사용 조각이 있는 적응형 양식이 AEM Forms 앱에서 지원됩니다.

## Forms 중심의 AEM 워크플로우 {#forms-centric-aem-workflows}

![aem forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

Forms 중심의 AEM 워크플로우 기능을 사용하면 OSGi 스택에서 다양한 작업에 대한 워크플로우를 신속하게 만들고 배포할 수 있습니다. 더 이상 JEE 스택에서 사용할 수 있는 프로세스 관리 기능을 설치할 필요가 없으므로 배포를 단순화하고 애플리케이션 서버와 인프라 비용을 줄일 수 있습니다. 자세한 내용은 OSGi](/help/forms/using/aem-forms-workflow.md)의 [Forms 중심의 워크플로우 를 참조하십시오.

Forms 중심의 AEM 워크플로우의 개선 사항은 다음과 ・ 같습니다.

* 워크플로우 모델 편집기는 Touch 사용자 인터페이스에서 사용할 수 있습니다. 양식 중심의 AEM 워크플로우를 만드는 데 필요한 시간을 줄이는 데 도움이 됩니다.
* 이메일을 보내는 워크플로우 단계입니다. 예를 들어 이메일 단계를 사용하여 워크플로우 완료 시 기록 문서를 보낼 수 있습니다.
* 워크플로우 모델에서 양식 데이터 모델 서비스를 사용하는 워크플로우 단계입니다. 이 단계에서는 사용자 지정 코드를 작성하지 않고도 데이터 통합 서비스를 호출할 수 있습니다. 예를 들어 GET 서비스를 호출하여 사용자 지정 코드를 작성하지 않고도 데이터베이스 아카이브에서 직원 세부 정보를 얻을 수 있습니다.

## AEM Forms 앱 {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

AEM Forms 앱을 사용하면 필드 작업자가 모바일 장치를 AEM Forms 서버와 동기화하고 양식을 작업할 수 있습니다. 장치가 다시 온라인 상태일 때 장치에서 로컬로 데이터를 저장하고 데이터와 서버를 동기화하여 장치가 오프라인 상태에서도 응용 프로그램이 원활하게 작동합니다. 자세한 내용은 [AEM Forms app](/help/forms/using/aem-forms-app.md)을 참조하십시오.

AEM Forms 앱의 향상된 기능은 다음과 같습니다.

* 지연 로드 사용 조각이 있는 적응형 양식이 AEM Forms 앱에서 지원됩니다.
* 양식 데이터 모델이 있는 적응형 양식은 AEM Forms 앱에서 지원됩니다.

## 문서 보안 {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

문서 보안을 사용하면 지원되는 형식으로 저장한 정보를 안전하게 배포할 수 있습니다. 문서 보안은 인증된 사용자만 문서를 사용할 수 있도록 합니다. 다음은 문서 보안의 주요 변경 사항입니다.

* 문서 보안은 AEM Forms 서버에 문서를 보내지 않고 문서를 로컬로 보호하기 위해 [PPL(Portable Protection Library)](/help/forms/using/document-security-offerings.md)을 제공합니다. 보안 자격 증명 및 정책 세부 사항만 네트워크를 통해 AEM Forms 서버로 이동합니다. AEM 6.4 Forms은 OSGi 번들 포맷으로 PPL(Portable Protection Library)을 도입했습니다. 이제 AEM Forms 서버에 PPL 라이브러리를 직접 설치하고 AEM 및 PPL의 기능을 함께 사용할 수 있습니다.
* 문서 보안 C++ SDK 및 C++ PPL 라이브러리는 Microsoft Visual Studio 2013으로 컴파일할 수 있습니다. 이전에 지원되는 버전은 Microsoft Visual Studio 2010이었습니다.

## 지원되는 플랫폼 {#supported-platforms}

AEM Forms은 지원되는 운영 체제, 애플리케이션 서버, 데이터베이스, 데이터베이스 드라이버, JDK, LDAP 서버 및 이메일 서버의 모든 조합을 사용하여 설정할 수 있습니다. 지원되는 플랫폼의 주요 변경 사항은 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td>구성 요소</td> 
   <td>지원이 추가됨</td> 
   <td>지원이 제거됨</td> 
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
     <li>Oracle 다중 임차인 아키텍처</li> 
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
     <li>Oracle 디렉토리 서버 Enterprise Edition 7.0</li> 
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
     <li>macOS용 Apple Safari 11.x</li> 
     <li>iOS용 Apple Safari 11.x</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Blackberry Z30 및 Q10 장치용 Blackberry 브라우저</li> 
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
