---
title: 통합 문제 해결
seo-title: 통합 문제 해결
description: 통합 문제를 해결하는 방법을 알아봅니다.
seo-description: 통합 문제를 해결하는 방법을 알아봅니다.
uuid: fe080e58-a855-4308-a611-f72eb47ba82d
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 422ee332-23ae-46bd-8394-a4e0915beaa2
translation-type: tm+mt
source-git-commit: a210d3bf80b7e7ec62c76a21f1cc2e71e986a4dc
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 2%

---


# 통합 문제 해결{#troubleshooting-integration-issues}

## 일반 문제 해결 팁 {#general-troubleshooting-tips}

### JavaScript 오류가 없는지 확인 {#ensure-there-are-no-javascript-errors}

브라우저의 JavaScript 콘솔에 오류가 표시되는지 확인합니다. 처리되지 않은 오류로 인해 후속 코드가 제대로 실행되지 않을 수 있습니다. 오류가 있는 경우 오류가 발생하는 스크립트와 오류가 발생하는 영역을 확인합니다. 스크립트에 대한 경로는 스크립트가 속한 기능에 대한 표시를 줄 수 있습니다.

### 구성 요소 수준에서 로깅 {#logging-on-component-level}

경우에 따라 구성 요소 수준에 다른 문을 추가하는 것이 도움이 될 수 있습니다. 구성 요소가 렌더링되므로 임시 마크업을 추가하여 잠재적 문제를 식별하는 데 도움이 되는 변수 값을 표시할 수 있습니다. 예:

```
<%
log.info("myVariable={}", myVariable);
%>
  
<!--
<%= myJspVariable %>
-->

<!--
${ myHtlVariable }
-->
```

로깅에 대한 자세한 내용은 로깅 및 [감사](/help/sites-deploying/configure-logging.md) 레코드 및 [로그 파일](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) 페이지를 참조하십시오.

## Analytics 통합 문제 {#analytics-integration-issues}

### 보고서 가져오기 기능으로 인해 높은 CPU/메모리 사용 {#the-report-importer-causes-high-cpu-memory-usage}

보고서 가져오기 기능을 사용하면 CPU/메모리 사용량이 높거나 예외가 `OutOfMemoryError` 발생합니다.

#### 솔루션 {#solution}

이 문제를 해결하려면 다음을 시도해 보십시오.

* 등록된 PollingImporter의 양이 많지 않은지 확인하십시오(아래의 &quot;PollingImporter로 인해 시스템 종료에 시간이 오래 걸립니다&quot; 섹션 참조).
* OSGi 콘솔에서 구성에 대한 CRON 표현식을 사용하여 특정 시간에 보고서 `ManagedPollingImporter` 가져오기 도구를 [실행합니다](/help/sites-deploying/configuring-osgi.md).

AEM에서 사용자 지정 데이터 가져오기 서비스를 만드는 방법에 대한 자세한 내용은 다음 문서 https://helpx.adobe.com/experience-manager/using/polling.html을 [참조하십시오](https://helpx.adobe.com/experience-manager/using/polling.html).

### PollingImporter로 인해 종료에 시간이 오래 걸립니다. {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

분석은 상속 메커니즘을 고려하여 설계되었습니다. 일반적으로 페이지 속성 Cloud Services 탭 내에서 Analytics 구성에 참조를 추가하여 사이트에 대한 Analytics를 [활성화합니다](/help/sites-developing/extending-cloud-config.md) . 그러면 이 구성은 페이지가 다른 구성을 필요로 하지 않는 한 다시 참조할 필요 없이 자동으로 모든 하위 페이지에 상속됩니다. 사이트에 참조를 추가하면 Analytics 데이터를 AEM으로 가져오는 데 사용되는 PollingImporters를 인스턴스화하는 유형의 노드(AEM 6.3 및 이전 버전의 경우 12개 또는 AEM 6.4의 경우 6) `cq;PollConfig` 가 자동으로 만들어집니다. 그 결과:

* Analytics를 참조하는 페이지가 많으면 PollingImporters가 많아집니다.
* 또한 Analytics 구성에 대한 참조를 사용하여 페이지를 복사하고 붙여넣으면 PollingImporters가 중복됩니다.

#### 솔루션 {#solution-1}

먼저 [error.log를](/help/sites-deploying/configure-logging.md) 분석하면 활성 또는 등록된 PollingImporter의 양에 대한 인사이트를 얻을 수 있습니다. 예:

```
# Count PollingImporter entries
$ sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\),interval.*/\1/p" error.log | wc -l
86415
# Count PollingImporter entries for last30days
$ sed -n "s/.*(aem-analytics-integration-last30Days).*target=\(.*\),interval.*/\1/p" error.log | wc -l
14531
# Count unique paths of PollingImporter registrations
sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\)\/jcr:content.*/\1/p" error.log | sort | uniq -c
28115
```

둘째, 상위 페이지(계층 구조 높음)만 Analytics 구성을 참조하도록 하십시오.

AEM에서 사용자 지정 데이터 가져오기 서비스를 만드는 방법에 대한 자세한 내용은 다음 문서 https://helpx.adobe.com/experience-manager/using/polling.html을 [참조하십시오](https://helpx.adobe.com/experience-manager/using/polling.html).

## DTM(기존) 문제 {#dtm-legacy-issues}

### DTM 스크립트 태그가 페이지 소스에서 렌더링되지 않습니다. {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

페이지 속성 [Cloud Services](/help/sites-administering/dtm.md) 탭에서 구성을 참조했지만 DTM [](/help/sites-developing/extending-cloud-config.md) 스크립트 태그가 페이지에 제대로 포함되지 않습니다.

#### 솔루션 {#solution-2}

문제를 해결하려면 다음을 시도해 보십시오.

* 암호화된 속성의 암호를 해독할 수 있는지 확인하십시오. 단, 암호화가 각 AEM 인스턴스에서 자동으로 생성된 다른 키를 사용할 수 있습니다. 자세한 내용은 구성 속성에 대한 [암호화 지원을 참조하십시오](/help/sites-administering/encryption-support-for-configuration-properties.md).
* 다음에 있는 구성 다시 게시 `/etc/cloudservices/dynamictagmanagement`
* ACL을 확인합니다 `/etc/cloudservices`. ACL은 다음과 같아야 합니다.

   * allow; jcr:read; webservice-support-servicelibfinder
   * allow; jcr:read; everyone; rep:glob:&amp;ast;/defaults/&amp;ast;
   * allow; jcr:read; everyone; rep:glob:&amp;ast;/defaults
   * allow; jcr:read; everyone; rep:glob:&amp;ast;/public/&amp;ast;
   * allow; jcr:read; everyone; rep:glob:&amp;ast;/public

ACL 관리에 대한 자세한 내용은 [사용자 관리 및 보안](/help/sites-administering/security.md#permissions-in-aem) 페이지를 참조하십시오.

## Target 통합 문제 {#target-integration-issues}

### 사용자 지정 페이지 구성 요소를 사용할 때 미리 보기 모드에서 타깃팅된 컨텐츠가 표시되지 않음 {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

이 문제는 사용자 지정 페이지 구성 요소에 Target DTM 통합을 처리하는 올바른 JSP 또는 클라이언트 라이브러리가 포함되어 있지 않기 때문에 발생합니다.

#### 솔루션 {#solution-3}

다음 솔루션을 사용해 볼 수 있습니다.

* 사용자 지정( `headlibs.jsp` 있는 경우)에 다음이 `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`포함되어 있는지 확인합니다.

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* 사용자 지정(있는 경우) `head.html` 이 아래 예와 같은 특정 통합 헤드라인을 선택적으로 포함하지 `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`않는지 **** 확인하십시오.

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

이 `servicelibs.jsp` 는 필요한 분석 JavaScript 개체를 추가하고 웹 사이트와 연결된 클라우드 서비스 라이브러리를 로드합니다. Target 서비스의 경우 라이브러리는 `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

로드된 라이브러리 세트는 Target 구성에 사용되는 대상 클라이언트 라이브러리( `mbox.js` 또는 `at.js`)의 유형에 따라 달라집니다.

DTM을 사용하여 컨텐츠를 렌더링하기 전에 라이브러리 `mbox.js` 를 `at.js` 전달하거나 로드해야 합니다. 이러한 라이브러리를 비동기적으로 로드하는 태그 관리 시스템을 사용하면 타겟 특정 JavaScript 코드를 실행할 때 문제가 발생할 수 있습니다.

자세한 내용은 타깃팅된 컨텐츠에 [대한 개발 페이지를](/help/sites-developing/target.md#understanding-the-target-component) 참조하십시오.

### &quot;AppMeasurement 초기화에 보고서 세트 ID 누락&quot; 오류가 브라우저 콘솔에 표시됩니다 {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

이 문제는 DTM을 사용하여 웹 사이트에서 Adobe Analytics을 구현하고 사용자 지정 코드를 사용하는 경우에 나타날 수 있습니다. 원인 `s = new AppMeasurement()` 은 개체를 인스턴스화하는 데 `s` 사용됩니다.

#### 솔루션 {#solution-4}

인스턴스화 방법 `s_gi` 대신 `new AppMeasurement` 사용하십시오. 예:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### 기본 오퍼는 올바른 오퍼 대신 무작위로 표시됩니다 {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

이 문제에는 다음과 같은 여러 가지 원인이 있을 수 있습니다.

* 타사 태그 관리 시스템을 사용하여 비동기적으로 Target 클라이언트 라이브러리( `mbox.js` 또는 `at.js`)를 로드할 경우 임의로 타깃팅을 중단할 수 있습니다. Target 라이브러리는 페이지 헤드에 동기식으로 로드되어야 합니다. 라이브러리는 AEM에서 전달될 때 항상 마찬가지입니다.

* 두 개의 Target 클라이언트 라이브러리( `at.js`)를 동시에 로드합니다(예: DTM 사용 및 AEM의 Target 구성 사용). 따라서 버전이 다른 경우 `adobe.target` 정의에 `at.js` 충돌이 발생할 수 있습니다.

#### 솔루션 {#solution-5}

다음 솔루션을 사용해 볼 수 있습니다.

* DTM과 같은 라이브러리를 로드하는 고객 코드(다시 로드되는 Target 라이브러리)가 [페이지 헤드에서 동기식으로 실행되는지 확인하십시오](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages).
* 사이트가 DTM을 사용하여 Target 라이브러리를 전달하도록 구성된 경우, DTM이 **제공한 Clientlib** 옵션이 사이트에 대한 [Target 구성에서](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) 체크 인되도록 합니다.

### AT.js 1.3+를 사용할 때는 항상 올바른 오퍼 대신 기본 오퍼가 표시됩니다 {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

기본적으로 AEM 6.2 및 6.3은 AT.js 버전 1.3.0+와 호환되지 않습니다. AT.js 버전 1.3.0에서는 API에 대한 매개 변수 유효성 검사를 도입하므로 코드에 의해 제공되지 `adobe.target.applyOffer()` 않는 &quot;mbox&quot; 매개 변수가 `atjs-itegration.js` 필요합니다.

#### 솔루션 {#solution-6}

이 문제를 해결하려면 매개 변수 개체 `atjs-itegration.js` 의 `"mbox": mboxName` 필드를 다음과 같이 편집하고 `adobe.target.applyOffer()` 추가하십시오.

```
adobe.target.getOffer({
    "mbox": mboxName,
    "params": params,
    "success": function (response) {
        adobe.target.applyOffer({
            "mbox": mboxName, //<--- ADDED PARAM
            "selector": "#" + mboxName,
            "offer": response
        })
    },
```

### 목표 및 설정 페이지에는 보고 소스 섹션이 표시되지 않습니다. {#the-goals-settings-page-does-not-show-the-reporting-sources-section}

이 문제는 [A4T Analytics Cloud 구성](/help/sites-administering/target-configuring.md) 프로비저닝 문제입니다.

#### 솔루션 {#solution-7}

AEM에 다음 확인 요청을 실행하여 Target 계정에 대해 A4T가 제대로 활성화되었는지 확인해야 합니다.

```
http://localhost:4502/etc/cloudservices/testandtarget/<YOUR-CONFIG>/jcr:content.a4t.json
 
{
    "a4tEnabled": true,
    "sharedsecret": "SECRET",
    "proxyUrl": "/libs/cq/contentinsight/content/proxy.reportingservices.json",
    "active": "true",
    "pageName": "",
    "url": "https://api5.omniture.com/rs/0.5/",
    "username": "USER@DOMAIN"
}
```

응답에 라인이 포함된 경우 `a4tEnabled:false`Adobe 고객 지원 센터에 [](https://helpx.adobe.com/contact.html) 문의하여 계정을 올바르게 프로비저닝하십시오.

### 유용한 Target API {#helpful-target-apis}

아래에 제시된 Target API는 Target 문제를 해결할 때 유용할 수 있습니다.

* 지정된 clientcode에 대한 Target 끝점 검색

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json
 
{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* 클라이언트 프로필 검색

```
https://admin<N>.testandtarget.omniture.com/admin/rest/v1/clients/<CLIENT>?email=<EMAIL>&password=<PASSWORD>
 
Response for N=4, CLIENT-dayintegrationintern
{
    "clientCode": "dayintegrationintern",
    "companyName": "Day Integration - Internal",
    "omnitureCompanyId": "Day Integration Internal",
    "softTraxId": -1,
    "address1": "XYZ",
    "city": "San Francisco",
    "state": "ca",
    "zip": "94107",
    "country": "UNITED STATES",
    "locale": "de_DE",
    "timeZone": "Europe/Berlin",
    "phone": "XX-XX-XXXX",
    "serviceLevel": "Up to 100,000",
    "privileges": [
        "a4t",
        "hosts",
        "TnT-SC-integration",
        "mvt",
        "steps",
        "testing-campaigns",
        "view-snapshot",
        "on-site-editor",
        "optimizing-campaign",
        "third-party-id-support",
        "landing-page-campaigns",
        "segment",
        "rest-create-user",
        "advanced-targeting",
        "mobile-device-targeting",
        "beta",
        "geolocation"
    ]
}
```

