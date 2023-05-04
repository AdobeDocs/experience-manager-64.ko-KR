---
title: 호환성 패키지
seo-title: Compatibility Package
description: AEM Forms 6.4에 호환성 패키지를 설치하면 AEM Forms 6.3의 서신 관리 자산 및 더 이상 사용되지 않는 적응형 양식 템플릿 및 페이지를 사용할 수 있습니다
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 3%

---

# 호환성 패키지 설치 {#compatibility-package}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 6.4에 호환성 패키지를 설치하면 AEM Forms 6.3의 서신 관리 자산 및 더 이상 사용되지 않는 적응형 양식 템플릿 및 페이지를 사용할 수 있습니다

## 개요 {#overview}

대화형 커뮤니케이션은 AEM Forms 6.4에서 고객 커뮤니케이션을 만드는 기본적이고 권장되는 방법입니다. AEM 6.3 Forms 및 AEM 6.2 Forms의 문자를 계속 사용하려면 [AEMFD 호환성 패키지](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

AEMFD 호환성 패키지를 사용하면 AEM Forms 6.4에서 AEM Forms 6.3 및 6.2의 다음 자산을 사용할 수 있습니다.

* AEM Forms 6.3 및 6.2에서 작성된 문서 조각
* 편지
* 데이터 사전
* 사용되지 않는 적응형 양식 템플릿 및 페이지

자세한 내용은 [호환성 패키지를 설치하여 AEM Forms 6.4와 호환되는 자산](/help/forms/using/compatibility-package.md#assetsmadecompatible).

## AEM Forms 6.4에서 AEM Forms 6.3 및 6.2 자산에 대한 지원 추가 {#add-support-for-aem-forms-and-assets-in-aem-forms}

업그레이드를 수행한 후 다음을 수행하여 AEMFD 호환성 패키지를 설치하고 자산을 6.4와 호환하도록 합니다.

다음을 확인하십시오 [AEM 호환성 패키지](/help/sites-deploying/backward-compatibility.md) 사전 설치.

1. 설치 [호환성 패키지](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

   패키지 업로드 및 설치에 대한 자세한 내용은 [패키지 작업 방법](/help/sites-administering/package-manager.md).

1. 로그가 안정되면 서버를 다시 시작합니다.
1. 자산이 6.4와 호환되도록 하려면 마이그레이션 유틸리티를 사용하십시오.

   자세한 내용은 [마이그레이션 유틸리티](/help/forms/using/migration-utility.md).

## 호환성 패키지를 설치하여 AEM Forms 6.4와 호환되는 자산 {#assetsmadecompatible}

호환성 패키지를 설치하여 AEM Forms 6.4와 호환되는 다음 자산 및 템플릿을 만들 수 있습니다.

* AEM 6.3 및 이전 버전의 서신 관리 자산

   * [편지](/help/forms/using/create-letter.md)
   * [데이터 사전](/help/forms/using/data-dictionary.md)
   * 문서 단편

* 사용되지 않는 적응형 양식 템플릿

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleRegulationTemplate
   * /libs/fd/af/templates/simpleRegulationTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabRegulationTemplate
   * /libs/fd/af/templates/tabRegulationTemplate2
   * /libs/fd/afaddon/templates/advancedRegulationTemplate
   * /libs/fd/afaddon/templates/advancedRegulationTemplate2

* 사용되지 않는 적응형 양식 페이지:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrolment
   * /libs/fd/afaddon/components/page/advanced/renderment
