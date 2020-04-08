---
title: 더 이상 사용되지 않는 및 제거된 기능
seo-title: 더 이상 사용되지 않는 및 제거된 기능
description: Adobe Experience Manager 6.4의 더 이상 사용되지 않는 및 제거된 기능에 관한 릴리스 노트입니다.
seo-description: Adobe Experience Manager 6.4의 더 이상 사용되지 않는 및 제거된 기능에 관한 릴리스 노트입니다.
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: 3316dbc8ef268be2b305d22da9003ae40414b4e1

---


# 더 이상 사용되지 않는 및 제거된 기능 {#deprecated-and-removed-features}

Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다.

예정된 AEM 기능의 제거/교체를 알리려면 다음 규칙이 적용됩니다.

1. 사용 중지 공지가 먼저 표시됩니다. 사용 중지 중에도 기능이 계속 지원되지만 더 이상 개선되지는 않습니다.
1. 더 이상 사용되지 않는 기능의 제거는 이르면 다음 주요 릴리스에서 실행됩니다. 실제 제거 대상일이 공지됩니다.

이 프로세스에서 고객에게 하나 이상의 릴리스 주기를 제공하여, 실제 제거 전에 더 이상 사용되지 않는 기능의 새 버전이나 후속 버전에 대한 구현을 채택할 수 있도록 합니다.

## 더 이상 사용되지 않는 기능 {#deprecated-features}

이 섹션에서는 AEM 6.4에서 더 이상 사용되지 않는 것으로 표시된 기능을 제시합니다. 일반적으로 이후 릴리스에서 제거될 예정인 기능은 먼저 사용 중지로 설정되고 대체 기능과 함께 제공됩니다.

고객은 현재 배포에서 기능을 사용할지 검토하고 대체 기능을 사용할 수 있도록 구현 변경을 계획하는 것이 좋습니다.

<table> 
 <tbody>
  <tr>
   <td>영역</td> 
   <td>기능</td> 
   <td>대체</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe는 향후 클래식 UI를 개선할 계획이 없습니다. AEM 6.4에는 클래식 UI가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 있는 그대로 사용할 수 있습니다. 클래식 UI가 더 이상 사용되지 않는 동안에도 계속 지원됩니다. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf#(페이지 편집기)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>고객은 새 AEM UI를 사용하도록 전환해야 합니다.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>구성 요소</td> 
   <td><p>Adobe는 아래 나열된 Foundation 구성 요소를 추가로 개선할 계획이 없습니다. AEM 6.4에는 Foundation 구성 요소가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 이를 그대로 계속 사용할 수 있습니다. 기초 구성 요소가 더 이상 사용되지 않는 동안에도 계속 지원됩니다. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordset</li> 
     <li>foundation/components/account/requestconfirence</li> 
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
   <td>고객은 향후 프로젝트를 위해 코어 구성 요소를 사용하는 것이 좋습니다. 기존 사이트는 변경할 필요가 없습니다.</td> 
  </tr>
  <tr>
   <td>구성 요소</td> 
   <td><p>Adobe는 아래 나열된 Foundation 구성 요소를 추가로 개선할 계획이 없습니다. AEM 6.4에는 Foundation 구성 요소가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 이를 그대로 계속 사용할 수 있습니다. 기초 구성 요소가 더 이상 사용되지 않는 동안에도 계속 지원됩니다.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>작성 시점에서 교체 서비스를 제공할 계획이 없습니다.</td> 
  </tr>
  <tr>
   <td>포털 디렉터</td> 
   <td><p>포털 디렉터는 타사 서버에서 포틀릿을 통해 AEM 컨텐츠를 호스팅할 수 있는 기능 세트입니다.</p> <p>Adobe는 아래 나열된 위치에 있는 포털 디렉터 기능을 추가로 개선할 계획이 없습니다. AEM 6.4에는 포털 디렉터가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 이를 그대로 사용할 수 있습니다. Portal Direct는 더 이상 사용하지 않는 동안 완전히 지원되는 상태로 유지됩니다.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>작성 시점에서 교체 서비스를 제공할 계획이 없습니다.</td> 
  </tr>
  <tr>
   <td>포틀릿 구성 요소</td> 
   <td><p>/foundation/components/portlet 아래의 포틀릿 구성 요소를 사용하여 AEM에서 JSR 포틀릿을 구성 요소로 호스팅할 수 있습니다.</p> <p>Adobe는 포틀릿 구성 요소 기능을 추가로 개선할 계획이 없습니다. AEM 6.4에는 포틀릿 구성 요소가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 그대로 계속 사용할 수 있습니다. 포틀릿 구성 요소는 더 이상 사용되지 않는 동안 완전히 지원되는 상태로 유지됩니다.</p> </td> 
   <td>작성 시점에서 교체 서비스를 제공할 계획이 없습니다.</td> 
  </tr>
  <tr>
   <td>양식</td> 
   <td><p>Adobe Central 제품이 더 이상 지원되지 않으므로 Adobe Central Migration Bridge 서비스에 대한 지원이 더 이상 필요하지 않습니다.</p> </td> 
   <td>교체 없음 </td> 
  </tr>
    <tr>
   <td>양식</td> 
   <td><p>쿼리 및 작업 옵션에서 JSONObject를 사용하지 않습니다. 다음 API는 더 이상 사용되지 않습니다.
   <ul><li>setArguments(JSONObject 인수)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject 인수)</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject 인수)</li></ul>
   </p> </td> 
   <td>IValueMap API 사용 </td> 
  </tr>
  <tr>
   <td>자산</td> 
   <td><p>자산 오프로드는 AEM 6.4부터 더 이상 사용되지 않습니다.</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 제거된 기능 {#removed-features}

이 섹션에는 AEM 6.4에서 제거된 기능 및 기능이 나열됩니다.이전 릴리스에는 이러한 기능이 더 이상 사용되지 않는다고 표시되었습니다.

<table> 
 <tbody>
  <tr>
   <td><strong>영역</strong></td> 
   <td><strong>기능</strong></td> 
   <td><strong>대체</strong></td> 
  </tr>
  <tr>
   <td>Analytics Activity Map</td> 
   <td>AEM 내에 포함된 Activity Map 버전.</td> 
   <td>Adobe Analytics API의 보안 변경 사항으로 인해, AEM 내에 포함된 Activity Map 버전을 더는 사용할 수 없습니다.<br><br>이제 <a href="https://docs.adobe.com/content/help/ko-KR/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">Adobe Analytics에서 제공하는 ActivityMap</a> 플러그인을 사용해야 합니다.</td> 
  </tr>
  <tr>
   <td>구성 요소</td> 
   <td>양식 Captcha<br /> (foundation/components/form/captcha)</td> 
   <td>Google별 ReCaptcha 구성 요소 대신 사용</td> 
  </tr>
  <tr>
   <td>구성 요소</td> 
   <td>슬라이드쇼<br /> (기본/구성 요소/슬라이드쇼)</td> 
   <td>교체 없음</td> 
  </tr>
  <tr>
   <td>구성 요소</td> 
   <td>Flash<br /> (기본/구성 요소/플래시)</td> 
   <td>교체 없음</td> 
  </tr>
  <tr>
   <td>구성 요소</td> 
   <td>비디오 구성 요소에서<br /> SWF 파일 재생 지원이 제거되었습니다(foundation/components/video).</td> 
   <td>Flash 기반의 비디오 포맷을 사용할 수 있습니다.</td> 
  </tr>
  <tr>
   <td>구성 요소</td> 
   <td>제품 테이블<br /> (commerce/components/product_table)</td> 
   <td>교체 없음</td> 
  </tr>
  <tr>
   <td>작업 관리</td> 
   <td>클래식 UI 작업 관리<br /> (/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>6.0부터 사용되지 않습니다.워크플로우 UI와 결합된 새 작업 관리를 사용합니다.</td> 
  </tr>
  <tr>
   <td>워크플로우</td> 
   <td>5.6-6.2<br /> 사이에 사용된 알림 UI(/libs/cq/workflow/content/notifications.html)</td> 
   <td>Workflow 받은 편지함 /aem/inbox</td> 
  </tr>
  <tr>
   <td>양식</td> 
   <td>PDF Generator를 사용하여 PDF를 PDF/E-1 포맷으로 내보내기 기능이 제거되었습니다.</td> 
   <td>PDF Generator는 PDF를 PDF/A-1a/b, PDF/A-2a/b 및 PDF/A-3a/b 포맷으로 내보낼 수 있도록 지속적으로 지원합니다.</td> 
  </tr>
  <tr>
   <td>양식</td> 
   <td>적응형 양식의 기본 AEM Captcha 서비스에 대한 지원이 제거되었습니다. </td> 
   <td>Google에서 ReCaptcha를 대신 사용하십시오.</td> 
  </tr>
  <tr>
   <td>양식</td> 
   <td>문서 조각 내의 이미지에 대한 지원이 제거되었습니다. </td> 
   <td>인터랙티브한 커뮤니케이션은 인쇄 및 웹 채널에서 직접 이미지를 사용할 수 있는 기능을 제공합니다.<br /> </td> 
  </tr>
    <tr>
   <td>양식</td> 
   <td> 즉시 업그레이드 </td> 
   <td>업그레이드 즉시 수행 지원은 제공되지 않습니다. <br/> </td> 
  </tr>
  <tr>
   <td>양식</td> 
   <td> TarMK에서 DocumentMK로 마이그레이션 시 사이드 그레이드 </td> 
   <td> 이전 시스템에서 데이터를 내보낸 다음 새로 설정한 시스템에서 가져올 수 있습니다. 자세한 지침은 JEE 업그레이드 문서의 AEM Forms를 참조하십시오. <br/> </td> 
  </tr>
    <tr>
   <td>양식</td> 
 <td>JEE 32비트 설치 관리자의 AEM Forms를 사용할 수 없습니다.</td> 
   <td>Adobe는 JEE 32비트 설치 관리자의 AEM Forms 출시를 중지했습니다. 64비트 설치 프로그램을 사용하여 JEE에 AEM Forms를 계속 설치할 수 있습니다. </td>  
  </tr>
    <tr>
    <td>양식</td> 
    <td>문서 조각 구성 요소에서 DAM 이미지 사용에 대한 지원을 제거했습니다.</td> 
    <td> 대화형 통신의 인쇄 채널에서 이미지 및 차트 구성 요소를 사용할 수 있습니다. 적응형 양식에 적응형 문서의 문서 조각 구성 요소를 사용하는 경우 AEM 6.4 Forms로 업그레이드한 후 작동이 중지됩니다. </td>  
  </tr>
  <tr>
   <td>양식</td> 
   <td> 응용 문서 기능 제거</td> 
   <td> 대화형 통신 기능을 사용하여 인쇄 및 웹 기반 통신을 만들 수 있습니다. 응용 문서를 사용하는 경우 호환성 패키지를 설치하여 기존 응용 문서를 계속 사용합니다.<br/> </td> 
  </tr>
    <tr>
    <td>양식</td> 
    <td>JEE 특정 랜딩 페이지에서 AEM Forms를 제거했습니다.</td> 
    <td>JEE의 AEM Forms 랜딩 페이지가 AEM 랜딩 페이지(/aem/start.html)으로 대체되었습니다. </td>  
  </tr>
   <tr>
   <td>양식</td> 
   <td>기본 Captcha 지원을 제거했습니다.</td> 
   <td>Google의 reCAPTCHA 서비스 사용</td> 
  </tr>
   <tr>
   <td>양식</td> 
   <td>기본 Captcha 지원을 제거했습니다.</td> 
   <td>Google의 reCAPTCHA 서비스 사용</td> 
  </tr>
  <tr>
   <td>커뮤니티</td> 
   <td>Captcha 확인 지원이 제거되었습니다.</td> 
   <td>사용자 정의 captcha 통합(예: Google의 reCAPTCHA)을 사용하여 확인합니다.</td> 
  </tr>
 </tbody>
</table>

## 다음 릴리스에 대한 사전 공지 {#pre-announcement-for-next-release}

이 섹션은 지원이 중단되지 않지만 고객에게 영향을 미치는 향후 릴리스의 변경 사항을 미리 알리기 위해 사용됩니다. 이 항목은 목표 계획용으로 제공됩니다.

<table> 
 <tbody>
  <tr>
   <td>영역<br /> </td> 
   <td>기능 <br /> </td> 
   <td>공지</td> 
  </tr>
  <tr>
   <td>브라우저 지원</td> 
   <td>Microsoft Internet Explorer</td> 
   <td>AEM 6.4는 Microsoft Internet Explorer 11을 지원하는 마지막 릴리스입니다.</td> 
  </tr>
  <tr>
   <td>Foundation</td> 
   <td>UI 프레임워크</td> 
   <td>Adobe는 2019년 Coral UI 2 구성 요소를 더 이상 사용하지 않습니다. AEM 6.4는 완전히 Coral UI 3(AEM 6.2에서 도입)을 기반으로 합니다. Adobe는 Coral 2로 사용자 정의 UI를 구축한 고객 및 파트너가 Coral 3으로 리팩토링할 것을 권장합니다. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - <a href="/help/sites-developing/dialog-conversion.md">Read more</a>.</td> 
  </tr>
 </tbody>
</table>
