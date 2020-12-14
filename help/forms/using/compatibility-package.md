---
title: 호환성 패키지
seo-title: 호환성 패키지
description: 'AEM Forms 6.4에 호환성 패키지를 설치하면 AEM Forms 6.3의 통신 관리 에셋을 사용할 수 있으며 가치 없는 적응형 양식 템플릿 및 페이지를 사용할 수 있습니다 '
seo-description: AEM Forms 6.4에 호환성 패키지를 설치하면 AEM Forms 6.3의 통신 관리 에셋을 사용할 수 있으며 가치 없는 적응형 양식 템플릿 및 페이지를 사용할 수 있습니다
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 1%

---


# 호환성 패키지 {#compatibility-package} 설치

AEM Forms 6.4에 호환성 패키지를 설치하면 AEM Forms 6.3의 통신 관리 에셋을 사용할 수 있으며 가치 없는 적응형 양식 템플릿 및 페이지를 사용할 수 있습니다

## 개요 {#overview}

인터랙티브한 커뮤니케이션은 AEM Forms 6.4에서 고객 커뮤니케이션을 만드는 데 기본적으로 권장되는 접근 방식입니다. AEM 6.3 Forms 및 AEM 6.2 Forms의 문자를 계속 사용하려면 [AEMFD 호환성 패키지](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)을(를) 설치해야 합니다.

AEMFD 호환성 패키지를 사용하면 AEM Forms 6.4에서 AEM Forms 6.3 및 6.2의 다음 에셋을 사용할 수 있습니다.

* AEM Forms 6.3 및 6.2에서 만든 문서 조각
* 편지
* 데이터 사전
* 적응형 양식의 가치 하락 템플릿 및 페이지

자세한 내용은 호환성 패키지[을 설치하여 AEM Forms 6.4와 호환되는 에셋을 참조하십시오.](/help/forms/using/compatibility-package.md#assetsmadecompatible)

## AEM Forms 6.4의 AEM Forms 6.3 및 6.2 자산에 대한 지원 추가 {#add-support-for-aem-forms-and-assets-in-aem-forms}

업그레이드를 수행한 후 다음을 수행하여 AEMFD 호환성 패키지를 설치하고 에셋을 6.4와 호환되도록 하십시오.

[AEM 호환성 패키지](/help/sites-deploying/backward-compatibility.md)이(가) 미리 설치되어 있는지 확인합니다.

1. [호환성 패키지](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)을(를) 설치합니다.

   패키지 업로드 및 설치에 대한 자세한 내용은 [패키지 사용 방법](/help/sites-administering/package-manager.md)을 참조하십시오.

1. 로그가 안정되면 서버를 다시 시작합니다.
1. 마이그레이션 유틸리티를 사용하여 에셋을 6.4와 호환되게 합니다.

   자세한 내용은 [마이그레이션 유틸리티](/help/forms/using/migration-utility.md)를 참조하십시오.

## 호환성 패키지 {#assetsmadecompatible}을(를) 설치하여 AEM Forms 6.4와 호환되는 에셋

호환성 패키지를 설치하여 AEM Forms 6.4와 호환되는 다음 에셋 및 템플릿을 만들 수 있습니다.

* AEM 6.3 이전 버전의 메일 관리 자산

   * [편지](/help/forms/using/create-letter.md)
   * [데이터 사전](/help/forms/using/data-dictionary.md)
   * 문서 단편

* 응용 양식 가치 하락 템플릿

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* 적응형 양식의 가치 하락 페이지:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advanced롤링

