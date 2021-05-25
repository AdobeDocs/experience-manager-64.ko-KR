---
title: eCommerce 개요
seo-title: eCommerce 개요
description: 'AEM 일반 eCommerce는 표준 설치의 일부로 사용할 수 있으며 eCommerce 프레임워크의 전체 기능을 제공합니다.  '
seo-description: 'AEM 일반 eCommerce는 표준 설치의 일부로 사용할 수 있으며 eCommerce 프레임워크의 전체 기능을 제공합니다.  '
uuid: 7be42b1e-f1d6-4891-96f8-0133b3a299a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: cb043066-aefc-4b68-b302-2b5dd710a786
feature: 전자 상거래 통합 프레임워크
exl-id: d84cd0ec-4586-45c1-a07a-a4d50fcbb629
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 6%

---

# eCommerce 개요{#ecommerce-overview}

AEM 일반 eCommerce는 표준 설치의 일부로 사용할 수 있으며 eCommerce 프레임워크의 전체 기능을 제공합니다.

Adobe은 두 가지 버전의 Commerce Integration Framework를 제공합니다.

|  | CIF on-prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| 지원되는 AEM 버전 | AEM on-prem 또는 AMS 6.x | AEM AMS 6.4 및 6.5 |
| 백엔드 | - AEM, Java <br> - 단일 통합, 빌드 전 매핑(템플릿)<br> - JCR 저장소 | - Magento <br> - Java 및 Javascript <br> - JCR 저장소에 저장된 상거래 데이터가 없습니다 |
| 프런트엔드 | AEM 서버측 렌더링 페이지 | 혼합 페이지 애플리케이션(하이브리드 렌더링) |
| 제품 카탈로그 | - AEM <br>에서 제품 가져오기, 편집기, 캐싱 - AEM 또는 프록시 페이지가 있는 일반 카탈로그 | - 제품 가져오기 없음 <br> - 일반 템플릿 <br> - 커넥터를 통한 온디맨드 데이터 |
| 확장성 | - 최대 수백만 개의 제품(사용 사례에 따라 다름) <br> - Dispatcher에서 캐싱 | - 볼륨 제한 없음 <br> - Dispatcher 또는 CDN에 캐싱 |
| 표준화된 데이터 모델 | 아니오 | 예, Magento GraphQL 스키마 |
| 사용 가능 | 예:<br> - SAP Commerce Cloud(AEM 6.4 및 Hybris 5(기본값)를 지원하도록 업데이트되고, Hybris 4 <br>- Salesforce Commerce Cloud(AEM 6.4를 지원하도록 열린 커넥터) 와의 호환성을 유지합니다. | GitHub를 통해 오픈 소스를 통해 지원. <br> Magento Commerce(Magento 2.3.2(기본값)를 지원하고 Magento 2.3.1과 호환됩니다.) |
| 사용 시기 | 제한된 사용 사례:작은 정적 카탈로그를 가져와야 하는 시나리오의 경우 | 대부분의 사용 사례에서 선호하는 솔루션 |


## 다른 구현 배포 {#deploying-other-implementations}

* [SAP Commerce Cloud](/help/sites-deploying/sap-commerce-cloud.md)
* [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>개념 및 eCommerce 구현 관리에 대한 자세한 내용은 [eCommerce](/help/sites-administering/ecommerce.md) 관리를 참조하십시오.
>
>eCommerce 기능 확장에 대한 자세한 내용은 [eCommerce 개발](/help/sites-developing/ecommerce.md)을 참조하십시오.
