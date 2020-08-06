---
title: AEM FAQ
seo-title: AEM 6.4 FAQ
description: 이러한 FAQ를 사용하여 AEM의 일반적인 워크플로우 또는 문제를 이해, 구성 및 해결할 수 있습니다.
seo-description: 이러한 FAQ를 사용하여 AEM의 일반적인 워크플로우 또는 문제를 이해, 구성 및 해결할 수 있습니다.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 1%

---


# AEM FAQ{#aem-faqs}

AEM 문제 해결 및 구성 문제에 대한 답변을 얻으려면 이 페이지를 따르십시오.

## 사이트 {#sites}

### 바이너리 없는 분포를 구성하려면 어떻게 해야 합니까? {#how-do-i-configure-binary-less-distribution}

바이너리 없는 배포는 공유 데이터 저장소에 대한 배포에 대해 지원되며 Vault 기반 배포 패키지 내보내기(팩토리 PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) 패키지 빌더.

바이너리 없는 모드가 활성화된 경우 배포된 컨텐츠 패키지에 실제 바이너리가 아닌 바이너리에 대한 참조가 포함되어 있습니다.

### 바이너리 없는 배포를 활성화하려면 어떻게 해야 합니까? {#how-do-i-enable-binary-less-distribution}

바이너리 없는 배포를 활성화하려면 공유 물방울 스토어로 배포하십시오.\
에이전트가 사용 중인 팩토리 PID() `useBinaryReferences` `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`**를 사용하여 OSGI 구성의 속성을 확인합니다.

### AEM 사이트 콘솔에서 페이지 계층 구조를 탐색하는 동안 오류 메시지를 사용자 지정하려면 어떻게 합니까? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

개인 설정(JS가 축소되지 않음)이 있는 네트워크 패널(크롬 브라우저)을 확인합니다.

요청을 `Initiator` 시작한 사람이 어떤 사람인지 확인할 수 있습니다. AJAX 호출이 수행되는 위치와 파일 번호를 제공합니다. 나중에 오류 처리 함수를 추적하고 요구 사항에 따라 오류 메시지를 변경할 수 있습니다.

### AEM에서 컨텐츠 작성자용 언어 사본을 만드는 동안 권한을 활성화하는 방법? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

언어 복사 기능을 만들려면 컨텐츠 작성자가 `/content/projects` 위치에서 권한이 있어야 합니다.

작성자도 프로젝트를 관리해야 하는 경우 `project-administrators` 그룹에 작성자를 추가하는 것이 해결 방법입니다.

### 프로젝트의 언어 사본을 만드는 동안 형식을 변경하는 방법? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

번역 프로젝트를 만들기 전에 루트 안에 언어 루트 및 언어 사본을 만듭니다.

예,\
Create a language root at `/content/geometrixx` name `fr_LU` (and title as French (Luxembourg)). 그런 다음 참조 패널에서 페이지의 언어 사본을 만들고 의 `Create structure only` 옵션으로 이동합니다 `Create & Translate`. 마지막으로 번역 프로젝트를 만든 다음 번역 작업에 언어 사본을 추가합니다.

자세한 내용은 아래 추가 리소스를 참조하십시오.

* [번역 내용 준비](/help/sites-administering/tc-prep.md)
* [번역 프로젝트 관리](/help/sites-administering/tc-manage.md)

### 로그인 시도 및 ACL 또는 권한 변경과 같은 AEM 기능을 감사하는 방법은 무엇입니까? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM은 향상된 문제 해결 및 감사를 위해 관리 변경 사항을 기록할 수 있는 기능을 도입했습니다. 기본적으로 정보는 `error.log` 파일에 기록됩니다. 모니터링을 쉽게 하려면 별도의 로그 파일로 리디렉션하는 것이 좋습니다.\
출력을 별도의 로그 파일로 리디렉션하려면 AEM [에서 사용자 관리 작업을 감사하는 방법을 참조하십시오](/help/sites-administering/audit-user-management-operations.md).

### 기본적으로 SSL을 활성화하는 방법? {#how-to-enable-ssl-by-default}

Adobe Experience Manager(AEM) 6.4는 SSL 마법사와 함께 제공되며 Jetty 및 Granite Jetty SSL 지원을 구성하는 사용자 인터페이스를 제공합니다.

기본적으로 SSL을 활성화하려면 기본적으로 [SSL을 참조하십시오](/help/sites-administering/ssl-by-default.md).

### 모바일 앱의 AEM Content Services를 사용할 때 가장 적합한 아키텍처는 무엇입니까? 가장 이상적인 방법은 &quot;기본 대응&quot; 방식입니까? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

컨텐트 서비스는 Sling 모델을 기반으로 하며 AEM 개발자는 내보낼 각 구성 요소에 대해 Sling 모델 도구를 제공해야 합니다.

Response 애플리케이션에서 AEM 컨텐츠 서비스를 사용하는 방법을 알아보려면 AEM [컨텐츠 서비스 시작하기 자습서를](https://helpx.adobe.com/kr/experience-manager/kt/sites/using/content-services-tutorial-use.html) 참조하십시오.

또한, 개발자가 구성 요소 트리를 내보내려는 경우, 구성 요소 `ComponentExporter` 및 `ContainerExporter` 인터페이스를 구현하고 하위 구성 요소를 반복하여 해당 `ModelFactory` 의 모델 표현을 반환하는 데도 사용할 수 있습니다. 아래 리소스를 참조하십시오.

[1] Adobe- [Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling: Sling Models](https://sling.apache.org/documentation/bundles/models.html)

### AEM 6.4 설문 조사 팝업을 비활성화하는 방법? {#how-to-disable-aem-survey-pop-up}

터치 UI 또는 웹 콘솔을 사용하여 사용 통계 수집을 선택할 수 있습니다. 자세한 지침은 집계된 사용 통계 [수집에 동의하기를 참조하십시오](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### AEM 6.4로 업그레이드할 수 있는 주요 기능을 설명하는 유용한 리소스가 있습니까? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

최신 [Adobe Experience Manager 버전으로 업그레이드하는 것을 고려 중인 고객을 위한 주요 기능의 고급 분류를 설명하는 AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) 업그레이드해야 하는 이유 이해를 참조하십시오.

### PorterStem 필터를 사용하도록 AEM 인스턴스를 구성하는 방법 {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

PorterStem 필터는 영어에 대한 포터 형태소 형태소 알고리즘을 적용합니다. 그 결과는 *language=&quot;English&quot; 논쟁과 함께 Snowball Porter Stemmer를 사용하는 것과* 비슷합니다. 하지만 이 형태는 Java로 직접 코딩되며 Snowball을 기반으로 하지 않습니다. 보호된 단어 목록은 허용되지 않으며 영어 텍스트에만 적합합니다.

Oak는 AEM에서 사용할 lucene-provides 분석기 구성 요소 집합을 표시합니다. 필터 사용 방법에 대한 자세한 내용은 **단순 검색 구현 안내서의** [Apache Oak Analyzers를](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)참조하십시오.

### 전체 다시 색인을 수행하는 방법 {#how-to-perform-a-full-re-indexing}

색인 재지정 작업은 AEM 전체 성능에 미치는 영향을 적절히 고려하여 항상 이에 대해 접근해야 하며, 활동이 낮거나 유지 관리 기간이 낮은 기간 동안 수행해야 합니다.

색인 재지정 [이유를 이해하려면 쿼리 및 색인](/help/sites-deploying/best-practices-for-queries-and-indexing.md) 우수 사례를 참조하십시오.

### Design Importer에서 축소 가능한 JS 라이브러리를 지원합니까? {#do-we-support-minified-js-libs-in-design-importer}

Adobe [화강암 HTML 라이브러리 관리자]의 JS 프로세서 기본 구성 속성을 ***min:gcc로 변경해야 합니다***. 디자인 패키지를 성공적으로 가져오려면 클라이언트 측 라이브러리에 사전 구성된 타사 라이브러리를 포함하는 것이 좋습니다.

## 자산 {#assets}

### MP4 파일을 업로드하는 동안 에셋 워크플로우가 반복되는 이유는(예: 드래그 앤 드롭 방식 사용) {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

사용자가 동영상 파일을 업로드해도 자산 노드에서 삭제 권한이 없으면 삭제 청크 노드가 실패하여 업로드가 다시 시작됩니다.

### AEM 6.4에서 한 번에 실행할 수 있는 디지털 자산의 최대 수는 얼마입니까? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager(AEM) 6.4를 사용하면 현재 한 번에 최대 2GB의 자산을 업로드할 수 있습니다.

AEM 6.4에서 실행할 수 있는 최대 자산 수에 대한 자세한 내용은 [자산 크기 조정 가이드를 참조하십시오](/help/assets/assets-sizing-guide.md).

### 언어 사본을 만드는 동안 OOTB 구성에 대한 기본 설정은 무엇입니까? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

클래식 UI를 통해 언어 사본을 만드는 경우, 자산은 새 언어 계층 아래로 이동되지 않고 언어 마스터에서 사용됩니다.

반면에 터치 UI를 통해 언어 사본을 만드는 경우(**참조** -> **언어 사본**&#x200B;업데이트) 새 언어 아래에 새 DAM 폴더가 만들어지고 여기에서 자산이 참조됩니다.

OOTB 구성에 대한 기본 설정입니다. 번역 **페이지 자산** = 번역 구성 **에서 번역** 안 함을 설정할 수 있습니다.\
AEM 6.4의 경우 **도구** > **Cloud Services** > **Translation Cloud 서비스**.

### AEM 구성 요소를 비활성화하여 AEM SegmentStore(AEM 6.3.1.1)에 대해 지수 성장을 야기하는 방법? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

OSGi 구성 요소 비활성화 기능을 비활성화할 수 있습니다. 이 서비스를 사용하려면 OSGi [구성 요소 비활성화를 참조하십시오](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

AEM을 다시 시작할 때마다 UI나 `curl` 명령(예: 아래)을 통해 구성 요소를 수동으로 비활성화할 수도 있습니다.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### AEM 6.4 인스턴스로 자산 인사이트를 구성하는 방법? {#how-to-configure-asset-insights-with-aem-instance}

DTM(Adobe 활성화)을 통해 배포된 Experience Manager에 대한 자산 인사이트를 설정하고 구성하려면 AEM Assets [에서 자산 인사이트 설정을 참조하십시오](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### 관리 콘솔을 사용자 지정하는 방법 {#how-to-customize-admin-consoles}

AEM에서는 작성 인스턴스의 콘솔 및 페이지 작성 기능을 사용자 정의할 수 있도록 해주는 다양한 메커니즘을 제공합니다.
사용자 정의 콘솔을 만들고 콘솔에 대한 기본 보기를 사용자 지정하는 방법에 대해 알아보려면 콘솔 사용자 [지정을 참조하십시오](/help/sites-developing/customizing-consoles-touch.md).

### CoralUI 2와 CoralUI 3 기반 구성 요소의 차이점은 무엇입니까? {#what-is-the-difference-between-coralui-and-coralui-based-components}

[MOCK] A new set of Sling components of Granal UI Foundation is created for Coral3 and is located under [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) CoralUI 2 기반 구성 요소에 대한 세트 하나와 CoralUI 3 기반 구성 요소에 대한 세트 하나가 있습니다. 새 세트는 이전 세트의 복사하여 붙여넣은 것이 아니라 정리됩니다(예: 능률적으로, 사용되지 않는 기능 제거). 따라서 페이지는 CoralUI 3 기반 또는 CoralUI 2 기반 세트만 사용하는 것이 좋습니다.

자세한 내용은 CoralUI 3 기반 [으로 마이그레이션 안내서를 참조하십시오](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### AEM Assets에서 검색 구성 요소를 사용자 지정하는 방법 {#how-to-customize-the-search-component-in-aem-assets}

검색 증폭/순위 지정 및 추가 구현 정보에 대한 자세한 내용은 [간단한 검색 구현 안내서를 참조하십시오.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

단순 검색 구현은 2017년 Summit 랩 AEM Search Demided의 자료입니다.

### 고객이 AEM에서 사이트 라이선스만 구입하는 경우 자산에 계속 액세스할 수 있습니까? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

아니오. 고객은 자산(또는 사이트 이외의 것)에 액세스할 수 없습니다. 모든 Adobe Experience Manager(AEM) 온프레미스가 JAR에 포함되어 있더라도 고객은 JAR에서 해당 구성 요소에 대한 액세스 권한을 부여받아 해당 계약에 라이센스가 부여됩니다. 다른 구성 요소를 탐색하려는 경우 최대 45일 동안 AEM 시험버전 프로그램을 사용하거나 자산과 같은 구성 요소를 평가(프로덕션 사용 안 함)할 수 있도록 허용하는 $0 판매 주문에 서명할 수 있습니다.

AEM 온프레미스 소프트웨어 및 Adobe Managed Services에 대한 자세한 내용은 다음 리소스를 참조하십시오.

* [Adobe Experience Manager 온프레미스 소프트웨어](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### 고객은 페이지 또는 자산의 기본 속성을 어떻게 확장할 수 있습니까? {#how-to-extend-default-properties-page-or-asset}

페이지 또는 자산의 기본 속성을 확장하는 방법에 대한 자세한 내용은 아래 리소스를 참조하십시오.

* [자산의 메타데이터 스키마](/help/assets/metadata-schemas.md)
* [페이지 속성 보기 사용자 지정](/help/sites-developing/page-properties-views.md)
