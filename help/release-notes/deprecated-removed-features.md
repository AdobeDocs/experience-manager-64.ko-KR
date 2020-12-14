---
title: 더 이상 사용되지 않는 및 제거된 기능
description: Adobe Experience Manager 6.4의 더 이상 사용되지 않는 및 제거된 기능에 관한 릴리스 노트입니다.
translation-type: tm+mt
source-git-commit: 8e82c691affe3b2c4108beec394cc0ba2d607b61
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 30%

---


# 더 이상 사용되지 않는 및 제거된 기능 {#deprecated-and-removed-features}

Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다.

예정된 AEM 기능의 제거/교체를 알리려면 다음 규칙이 적용됩니다.

1. 사용 중지 공지가 먼저 표시됩니다. 사용 중지 중에도 기능이 계속 지원되지만 더 이상 개선되지는 않습니다.
1. 더 이상 사용되지 않는 기능의 제거는 이르면 다음 주요 릴리스에서 실행됩니다. 실제 제거 대상일이 공지됩니다.

이 프로세스에서 고객에게 하나 이상의 릴리스 주기를 제공하여, 실제 제거 전에 더 이상 사용되지 않는 기능의 새 버전이나 후속 버전에 대한 구현을 채택할 수 있도록 합니다.

## 더 이상 사용되지 않는 기능 {#deprecated-features}

아래 표에는 AEM 6.4에서 더 이상 사용되지 않는 것으로 표시된 기능 및 기능이 나열됩니다. 일반적으로 향후 릴리스에서 제거될 예정인 기능은 먼저 사용되지 않고 제공된 대체 요소로 설정됩니다.

고객은 현재 배포에서 기능을 사용할지 검토하고 대체 기능을 사용할 수 있도록 구현 변경을 계획하는 것이 좋습니다.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| 영역 | 기능 | 대체 |
|---|---|---|
| UI | Adobe는 향후 클래식 UI를 개선할 계획이 없습니다. AEM 6.4에는 클래식 UI가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 있는 그대로 사용할 수 있습니다. 클래식 UI가 더 이상 사용되지 않는 동안에도 계속 지원됩니다. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (페이지 편집기) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | 고객은 새로운 AEM UI를 사용하도록 전환해야 합니다. |
| 구성 요소 | Adobe은 아래 나열된 기초 구성 요소를 추가로 개선할 계획이 없습니다. AEM 6.4에는 기초 구성 요소가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 있는 그대로 사용할 수 있습니다. 기초 구성 요소가 더 이상 사용되지 않는 동안에도 계속 지원됩니다. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordset </li> <li> foundation/components/account/requestconfiration </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> 재단/구성 요소/양식/신용 카드 </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | 고객은 향후 프로젝트를 위해 코어 구성 요소를 사용하는 것이 좋습니다. 기존 사이트는 변경할 필요가 없습니다. |
| 구성 요소 | Adobe은 아래 나열된 기초 구성 요소를 추가로 개선할 계획이 없습니다. AEM 6.4에는 기초 구성 요소가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 있는 그대로 사용할 수 있습니다. 기초 구성 요소가 더 이상 사용되지 않는 동안에도 계속 지원됩니다. <ul><li>foundation/components/timing</li></ul> | Adobe은 교체를 제공할 계획이 없습니다. |
| 포털 Director | 포털 Director은 제3자 서버에서 포틀릿을 통해 AEM 컨텐츠를 호스팅할 수 있는 기능 세트입니다. Adobe은 아래 나열된 위치 아래에서 포털 Director 기능을 추가로 개선할 계획이 없습니다. AEM 6.4에는 포털 Director이 포함되어 있으며 이전 릴리스에서 업그레이드한 고객은 그대로 사용할 수 있습니다. Portal Direct는 더 이상 사용하지 않는 동안 완전히 지원되는 상태로 유지됩니다. <ul><li>/libs/portal/director</li></ul> | Adobe은 교체를 제공할 계획이 없습니다. |
| 포틀릿 구성 요소 | /foundation/components/portlet 아래의 포틀릿 구성 요소를 사용하면 AEM에서 JSR 포틀릿을 구성 요소로 호스팅할 수 있습니다. Adobe은 포틀릿 구성 요소 기능을 추가로 개선할 계획이 없습니다. AEM 6.4에는 포틀릿 구성 요소가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 그대로 사용할 수 있습니다. 포틀릿 구성 요소는 더 이상 사용하지 않는 동안 완전히 지원되는 상태로 유지됩니다. | Adobe은 교체를 제공할 계획이 없습니다. |
| 양식 | Adobe Central 제품이 더 이상 지원되지 않으므로 Adobe Central 마이그레이션 브리지 서비스에 대한 지원이 더 이상 사용되지 않습니다. | 교체 없음 |
| 양식 | 쿼리 및 작업 옵션에서 JSONObject를 사용하지 않습니다. 다음 API는 더 이상 사용되지 않습니다. <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | `IValueMap` API 사용 |
| 양식 | 사용되지 않는 Central Migration Bridge 서비스입니다. | 교체 서비스를 제공하지 않습니다. |
| 자산 | 자산 오프로드는 AEM 6.4부터 더 이상 사용되지 않습니다. |  |
| 개발자 | 클라이언트 라이브러리 로대시/밑줄 표시 Adobe은 배포의 일부로 배송된 로대시/밑줄 클라이언트 라이브러리를 추가로 유지 관리하고 업데이트할 계획이 없습니다(빠른 시작). | Adobe에서는 코드에 로대시/밑줄을 추가하여 프로젝트 코드 베이스에 추가하는 것이 좋습니다. |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## 제거된 기능 {#removed-features}

아래 표에는 AEM 6.4에서 제거된 기능 및 기능이 나와 있습니다. 이전 릴리스에는 이러한 기능이
사용되지 않습니다.

| 영역 | 기능 | 대체 |
|---|---|---|
| Analytics Activity Map | AEM 내에 포함된 Activity Map 버전입니다. | Adobe Analytics API의 보안 변경 사항으로 인해, AEM 내에 포함된 Activity Map 버전을 더는 사용할 수 없습니다. 이제 Adobe Analytics](https://docs.adobe.com/content/help/ko-KR/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html)에서 제공하는 [ActivityMap 플러그인을 사용해야 합니다. |
| 구성 요소-Forms | 양식 Captcha(foundation/components/form/captcha) | ReCaptcha by Google 구성 요소를 대신 사용하십시오. |
| 구성 요소 | 슬라이드쇼(기본/구성 요소/슬라이드쇼) | 교체 없음 |
| 구성 요소 | Flash(foundation/components/flash) | 교체 없음 |
| 구성 요소 | 비디오 구성 요소에서 SWF 파일 재생 지원이 제거되었습니다(기본/구성 요소/비디오). | Flash 기반의 비디오 포맷을 사용할 수 있습니다. |
| 구성 요소 | 제품 테이블(commerce/components/product_table) | 교체 없음 |
| 작업 관리 | 클래식 UI 작업 관리(/libs/cq/taskmanagement/content/taskmanager.html) | 6.0 이후 사용되지 않습니다. 워크플로 UI와 결합된 새 작업 관리를 사용하십시오. |
| 워크플로우 | 5.6~6.2 사이에 사용된 알림 UI (/libs/cq/workflow/content/notifications.html) | 워크플로우 받은 편지함/AEM/받은 편지함 |
| 양식 | PDF Generator를 사용하여 PDF/E-1 포맷으로 Export PDF이 제거되었습니다. | PDF Generator는 PDF를 PDF/A-1a/b, PDF/A-2a/b 및 PDF/A-3a/b 포맷으로 내보낼 수 있도록 지속적으로 지원합니다. |
| 양식 | 문서 조각 내의 이미지에 대한 지원이 제거되었습니다. | 인터랙티브한 커뮤니케이션은 인쇄 및 웹 채널에서 이미지를 직접 사용할 수 있는 기능을 제공합니다. |
| 양식 | 즉시 업그레이드 | 업그레이드 작업을 수행할 수 없습니다. |
| 양식 | TarMK를 DocumentMK로 마이그레이션하기 위한 Sidegrade | 이전 시스템에서 데이터를 내보낸 다음 새로 설정한 시스템에서 가져올 수 있습니다. 자세한 지침은 JEE 업그레이드 문서에 대한 AEM Forms을 참조하십시오. |
| 양식 | JEE 32비트 설치 관리자의 AEM Forms을 사용할 수 없습니다. | Adobe에서 JEE 32비트 설치 관리자의 AEM Forms 배송을 중단했습니다. 64비트 설치 프로그램을 사용하여 JEE에 AEM Forms을 계속 설치할 수 있습니다. |
| 양식 | 문서 조각 구성 요소에서 DAM 이미지 사용에 대한 지원을 제거했습니다. | 대화형 통신의 인쇄 채널에서 이미지 및 차트 구성 요소를 사용할 수 있습니다. 적응형 양식에 응용 문서의 문서 조각 구성 요소를 사용하는 경우 AEM 6.4 Forms으로 업그레이드한 후 작동이 중단됩니다. |
| 양식 | 응용 문서 기능 제거 | 대화형 통신 기능을 사용하여 인쇄 및 웹 기반 통신을 만들 수 있습니다. 적응형 문서를 사용하는 경우 기존 적응형 문서를 계속 사용하려면 호환성 패키지를 설치합니다 |
| 양식 | JEE 특정 랜딩 페이지에서 AEM Forms을 제거했습니다. | AEM Forms on JEE 랜딩 페이지가 AEM 랜딩 페이지로 대체됨(/aem/start.html) |
| 양식 | 기본 Captcha 지원을 제거했습니다. | Google에서 reCAPTCHA 서비스를 사용하십시오. |
| 양식 | AEM Designer에서 플래시 필드에 대한 지원을 제거했습니다. AEM Designer에서는 양식에 사용된 Flash 필드를 편집할 수 없습니다. | 이전 버전에 대해 릴리스된 AEM Designer를 사용하여 이러한 양식을 편집할 수 있습니다. |
| 커뮤니티 | Captcha 확인에 대한 지원이 제거되었습니다. | 확인을 위해 사용자 정의 Captcha 통합(예: Google의 reCAPTCHA)을 사용합니다. |

## 다음 릴리스에 대한 사전 공지 {#pre-announcement-for-next-release}

아래 표는 더 이상 사용되지 않지만 고객에게 영향을 줄 수 있는 향후 릴리스에 대한 변경 사항 목록을 제공합니다. 이 항목은 목표 계획용으로 제공됩니다.

| 영역 | 기능 | 공지 |
|---|---|---|
| 브라우저 지원 | Microsoft Internet Explorer | AEM 6.4는 Microsoft Internet Explorer 11을 지원하는 마지막 릴리스입니다. |
| Foundation | UI 프레임워크 | Adobe은 2019년 Coral UI 2 구성 요소를 더 이상 사용하지 않습니다. AEM 6.4는 AEM 6.2에서 소개된 Coral UI 3을 기반으로 합니다. Adobe은 Coral 2로 사용자 지정 UI를 구축한 고객 및 파트너에게 이 UI를 Coral 3으로 리팩토링하도록 권장합니다. Adobe은 Coral 2 대화 상자를 Coral 3 - [자세히 보기](/help/sites-developing/dialog-conversion.md)로 변환하는 도구를 제공합니다. |
