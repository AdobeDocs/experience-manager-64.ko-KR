---
title: AEM FAQ
seo-title: AEM 6.4 frequently asked questions
description: AEM의 일반 워크플로우 또는 문제를 이해, 구성 및 해결하려면 이러한 FAQ를 사용하십시오.
seo-description: Use these FAQs to understand, configure, and troubleshoot common workflows or issues in AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
exl-id: 76110cf4-0fd8-4203-b256-c0818a1b64d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---

# AEM FAQ{#aem-faqs}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM 문제 해결 및 구성 문제에 대한 답변을 보려면 이 페이지를 따르십시오.

## Sites {#sites}

### 바이너리가 없는 배포를 구성하려면 어떻게 해야 합니까? {#how-do-i-configure-binary-less-distribution}

이진 없는 배포는 공유 데이터 저장소를 통한 배포에 대해 지원되며 저장소 기반 배포 패키지 내보내기(출하 시 PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) 패키지 빌더.

바이너리 없는 모드가 활성화된 경우 배포된 컨텐츠 패키지에 실제 바이너리가 아닌 바이너리에 대한 참조가 포함되어 있습니다.

### 바이너리 없는 배포를 활성화하려면 어떻게 해야 합니까? {#how-do-i-enable-binary-less-distribution}

바이너리가 없는 배포를 활성화하려면 공유 blob 저장소를 사용하여 배포합니다.\
을(를) 확인합니다. `useBinaryReferences` 출하 시 PID를 사용하여 OSGI 구성의 속성 `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* 에이전트가 사용 중임을 나타냅니다.

### AEM Sites 콘솔에서 페이지 계층 구조를 탐색하는 동안 오류 메시지를 사용자 지정하려면 어떻게 해야 합니까? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

개인 설정(JS가 축소되지 않은 Chrome 브라우저의 네트워크 패널)을 확인합니다.

보기 `Initiator` 열에서 요청의 시작자가 무엇인지 확인합니다. AJAX 호출이 이루어지는 위치와 행 번호를 제공합니다. 나중에 오류 처리 함수를 추적하고 필요에 따라 오류 메시지를 변경할 수 있습니다.

### AEM에서 컨텐츠 작성자용 언어 사본을 만드는 동안 권한을 활성화하는 방법 {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

언어 복사 기능을 만들려면 컨텐츠 작성자가 다음에 대한 권한이 있어야 합니다. `/content/projects` 위치.

작성자가 프로젝트를 관리해야 하는 경우 해결 방법은 작성자를 `project-administrators` 그룹에 속해 있어야 합니다.

### 프로젝트에 대한 언어 사본 을 만드는 동안 형식을 변경하는 방법 {#how-to-change-the-format-while-creating-language-copy-for-a-project}

번역 프로젝트를 만들기 전에 루트 내에 언어 루트와 언어 사본을 만듭니다.

예를 들어\
에서 언어 루트 만들기 `/content/geometrixx` 이름 포함 `fr_LU` (그리고 프랑스어(룩셈부르크)로 제목이 지정됩니다.) 그런 다음 참조 패널에서 페이지의 언어 사본을 만들고 로 이동합니다 `Create structure only` 옵션 `Create & Translate`. 마지막으로 번역 프로젝트를 만든 다음 번역 작업에 언어 사본을 추가합니다.

자세한 내용은 아래 추가 리소스를 참조하십시오.

* [컨텐츠 번역 준비](/help/sites-administering/tc-prep.md)
* [번역 프로젝트 관리](/help/sites-administering/tc-manage.md)

### 로그인 시도 및 ACL 또는 권한 변경 등의 AEM 기능을 감사하는 방법 {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM에서는 향상된 문제 해결 및 감사를 위해 관리 변경 사항을 기록하는 기능을 도입했습니다. 기본적으로 이 정보는 `error.log` 파일. 모니터링을 쉽게 하려면 별도의 로그 파일로 리디렉션하는 것이 좋습니다.\
출력을 별도의 로그 파일로 리디렉션하려면 를 참조하십시오 [AEM에서 사용자 관리 작업을 감사하는 방법](/help/sites-administering/audit-user-management-operations.md).

### 기본적으로 SSL을 활성화하는 방법 {#how-to-enable-ssl-by-default}

AEM(Adobe Experience Manager) 6.4는 SSL 마법사와 함께 제공되며 Jetty 및 Granite Jetty SSL 지원을 구성할 수 있는 사용자 인터페이스를 제공합니다.

기본적으로 SSL을 사용하려면 다음을 참조하십시오 [기본적으로 SSL](/help/sites-administering/ssl-by-default.md).

### 모바일 앱에서 AEM Content Services를 사용할 때 권장되는 아키텍처는 무엇입니까?(이상적인 React Native?) {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

컨텐츠 서비스는 Sling 모델을 기반으로 하며 AEM 개발자는 내보내는 각 구성 요소에 대해 Sling 모델 도구를 제공해야 합니다.

React 애플리케이션에서 AEM 컨텐츠 서비스를 사용하는 방법을 이해하려면 [AEM 컨텐츠 서비스 시작](https://helpx.adobe.com/kr/experience-manager/kt/sites/using/content-services-tutorial-use.html) 자습서입니다.

또한 개발자가 구성 요소 트리를 내보내려는 경우 을 구현할 수도 있습니다 `ComponentExporter` 및 `ContainerExporter` 인터페이스 및 사용 `ModelFactory` 를 눌러 하위 컴포넌트를 반복하여 해당 모델 표현을 반환합니다. 아래 리소스를 참조하십시오.

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2개] [Apache Sling : Sling 모델](https://sling.apache.org/documentation/bundles/models.html)

### AEM 6.4 설문 조사 팝업을 비활성화하는 방법 {#how-to-disable-aem-survey-pop-up}

Touch UI 또는 웹 콘솔을 사용하여 사용 통계 수집을 옵트인할 수 있습니다. 자세한 지침은 [집계된 사용 통계 수집 선택](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### AEM 6.4로 업그레이드하는 주요 기능을 강조 표시하는 리소스가 있습니까? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

을(를) 참조하십시오. [AEM 업그레이드 이유 이해하기](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) 에서는 최신 버전의 Adobe Experience Manager으로 업그레이드하려는 고객을 위한 주요 기능에 대한 높은 수준의 분류를 설명합니다.

### PorterStem 필터를 사용하도록 AEM 인스턴스를 구성하는 방법 {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

PorterStem 필터는 영어에 대한 Porter Steaming 알고리즘을 적용합니다. 결과는 Snowball Porter Stemmer와 비슷합니다 *language=&quot;English&quot;* 변합니다. 하지만 이 줄기세포주는 Java로 직접 코딩되어 있으며 Snowball을 기반으로 하지 않습니다. 보호된 단어 목록은 허용되지 않으며 영어 텍스트에만 적합합니다.

Oak는 AEM에서 사용할 lucene 제공 분석기 구성 요소 집합을 표시합니다. 필터 사용 방법에 대해 알아보려면 **Apache Oak Analyzers** in [단순 검색 구현 안내서](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

### 전체 재색인을 수행하는 방법 {#how-to-perform-a-full-re-indexing}

재색인화는 AEM 전체 성능에 미치는 영향에 대해 항상 적절한 고려와 함께 접근해야 하며, 낮은 활동이나 유지 관리 기간 동안 수행해야 합니다.

자세한 내용은 [쿼리 및 색인 생성에 대한 우수 사례](/help/sites-deploying/best-practices-for-queries-and-indexing.md) 색인을 다시 작성하는 이유를 이해하기 위해

### 디자인 가져오기에서 축소된 JS 링크를 지원합니까? {#do-we-support-minified-js-libs-in-design-importer}

Granite HTML 라이브러리 관리자의 JS 프로세서 기본 구성 속성을 다음으로 변경해야 합니다. ***min:gcc***. 디자인 패키지를 성공적으로 가져오려면 미리 축소된 타사 라이브러리를 Adobe의 클라이언트 측 라이브러리에 포함하는 것이 좋습니다.

## Assets {#assets}

### MP4 파일을 업로드하는 동안(예를 들어 드래그 앤 드롭 방법 사용) 자산 워크플로우가 반복되는 이유는 무엇입니까? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

사용자가 동영상 파일을 업로드해도 자산 노드에서 삭제 권한이 없으면 삭제 청크 노드가 실패하여 업로드가 다시 시작됩니다.

### AEM 6.4로 한 번에 운영할 수 있는 최대 디지털 자산 수는 얼마입니까? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager(AEM) 6.4를 사용하면 현재 한 번에 최대 2GB의 자산을 업로드할 수 있습니다.

AEM 6.4로 작업할 수 있는 최대 자산 수에 대한 자세한 내용은 [자산 크기 조정 가이드](/help/assets/assets-sizing-guide.md).

### 언어 사본을 만드는 동안 OOTB 구성에 대한 기본 설정은 무엇입니까? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

클래식 UI를 통해 언어 사본을 만들 때 자산은 새 언어 계층 구조로 이동되지 않고 언어 마스터에서 사용됩니다.

반면에 Touch UI를 통해 언어 사본을 만들 때(**참조** -> **언어 사본 업데이트**)이면 새 DAM 폴더가 새 언어로 생성되고, 자산이 여기에서 참조됩니다.

OOTB 구성에 대한 기본 설정입니다. 다음을 설정할 수 있습니다 **페이지 자산 번역** = **번역 안 함** 변환 구성에서 사용할 수 있습니다.\
AEM 6.4의 경우, **도구** > **Cloud Services** > **번역 클라우드 서비스**.

### AEM SegmentStore에 대한 기하급수적인 증가를 초래하는 AEM 구성 요소를 비활성화하는 방법(AEM 6.3.1.1) {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

OSGi 구성 요소 비활성화 를 비활성화할 수 있습니다. 이 서비스를 사용하려면 [OSGi 구성 요소 비활성화](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

해결 방법으로, UI 또는 를 통해 구성 요소를 수동으로 비활성화할 수도 있습니다 `curl` 명령을 실행합니다(아래 예).

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### AEM 6.4 인스턴스로 자산 통찰력을 구성하는 방법 {#how-to-configure-asset-insights-with-aem-instance}

DTM(Adobe 활성화)을 통해 배포되는 Experience Manager에 대한 자산 통찰력을 설정하고 구성하려면 다음을 참조하십시오 [AEM Assets을 사용하여 자산 통찰력 설정](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### 관리 콘솔을 사용자 지정하는 방법 {#how-to-customize-admin-consoles}

AEM에서는 작성 인스턴스의 콘솔 및 페이지 작성 기능을 사용자 지정할 수 있는 다양한 메커니즘을 제공합니다.
사용자 지정 콘솔을 만들고 콘솔에 대한 기본 보기를 사용자 지정하는 방법에 대해 알아보려면 [콘솔 사용자 지정](/help/sites-developing/customizing-consoles-touch.md).

### CoralUI 2와 CoralUI 3 기반 구성 요소의 차이점은 무엇입니까? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Granite UI Foundation의 새 Sling 구성 요소 세트는 Coral3용으로 만들어진 다음 아래에 있습니다 [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) CoralUI 2 기반 구성 요소에 대해 한 세트, CoralUI 3 기반 구성 요소에 대해 한 세트가 있습니다. 새 집합은 이전 집합의 복사-붙여넣기만 할 것이 아니라 정리됩니다(예: 정리하기, 더 이상 사용되지 않는 기능 제거). 따라서 페이지에는 CoralUI 3 기반 또는 CoralUI 2 기반 세트만 사용하는 것이 좋습니다.

자세한 내용은 [CoralUI 3 기반의 마이그레이션 안내서](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### AEM Assets에서 검색 구성 요소를 사용자 지정하는 방법 {#how-to-customize-the-search-component-in-aem-assets}

검색 증가/순위 지정 및 추가 구현 정보에 대해 알아보려면 [단순 검색 구현 안내서.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

단순 검색 구현은 2017년 Summit Lab AEM Search Demystified의 자료입니다.

### 고객이 AEM에서 사이트 라이센스만 구입하는 경우 여전히 자산에 액세스할 수 있습니까? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

아니요. 고객은 자산(또는 사이트 이외의 항목)에 액세스할 수 없습니다. 모든 Adobe Experience Manager(AEM) 온프레미스가 JAR에 포함되어 있어도 고객은 계약에 라이센스가 있는 JAR의 구성 요소에만 액세스할 수 있는 권한을 부여합니다. 다른 구성 요소를 탐색하려는 경우 최대 45일 동안 AEM 평가판 프로그램을 사용하거나 Assets와 같은 구성 요소를 평가할 수 있도록 하는 $0 판매 주문에 서명할 수 있습니다.

AEM On-premise 소프트웨어 및 Adobe Managed Services에 대한 자세한 내용은 다음 리소스를 참조하십시오.

* [Adobe Experience Manager On-premise Software](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### 고객이 페이지나 자산의 기본 속성을 어떻게 확장할 수 있습니까? {#how-to-extend-default-properties-page-or-asset}

페이지 또는 자산의 기본 속성을 확장하는 방법에 대해 알아보려면 아래 리소스를 참조하십시오.

* [자산의 메타데이터 스키마](/help/assets/metadata-schemas.md)
* [페이지 속성 보기 사용자 지정](/help/sites-developing/page-properties-views.md)
