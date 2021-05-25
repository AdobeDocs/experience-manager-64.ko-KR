---
title: eCommerce
seo-title: eCommerce
description: 'AEM eCommerce는 마케터가 웹, 모바일 및 소셜 터치포인트 간에 브랜딩되고 개인화된 쇼핑 경험을 제공하는 데 도움이 됩니다. '
seo-description: 'AEM eCommerce는 마케터가 웹, 모바일 및 소셜 터치포인트 간에 브랜딩되고 개인화된 쇼핑 경험을 제공하는 데 도움이 됩니다. '
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
feature: 전자 상거래 통합 프레임워크
exl-id: 3c046e16-5f54-4a16-aa5b-256b679808fa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 3%

---

# eCommerce{#ecommerce}

* [개념](/help/sites-administering/concepts.md)
* [관리(일반)](/help/sites-administering/generic.md)
* [SAP Commerce Cloud](/help/sites-administering/sap-commerce-cloud.md)
* [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

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

eCommerce는 PIM(제품 정보 관리)과 함께 온라인 스토어를 통해 제품 판매에 주력하는 웹 사이트의 활동을 처리합니다.

* 제품 생성, 수명 및 노후화
* 가격 관리
* 트랜잭션 관리
* 전체 카탈로그 관리
* 라이브 및 중앙 집중식 스토리지 레코드
* 웹 인터페이스

AEM eCommerce는 마케터가 웹, 모바일 및 소셜 터치포인트 간에 브랜딩되고 개인화된 쇼핑 경험을 제공하는 데 도움이 됩니다. AEM 작성 환경에서는 Target 방문자 컨텍스트 및 머천다이징 전략을 기반으로 페이지 및 구성 요소를 사용자 지정할 수 있습니다.예:

* 제품 페이지
* 장바구니 구성 요소
* 체크아웃 구성 요소

이 구현에서는 제품 정보에 실시간으로 액세스할 수 있습니다. 다음을 적용하는 데 사용할 수 있습니다.

* 제품 정보 무결성
* 가격 책정
* 재고 관리 인벤토리
* 장바구니 상태의 변형

>[!NOTE]
>
>외부 eCommerce 공급자와 통합 프레임워크를 사용하려면 먼저 필요한 패키지를 설치해야 합니다. 자세한 내용은 [eCommerce](/help/sites-deploying/ecommerce.md) 배포를 참조하십시오.
>
>eCommerce 기능 확장에 대한 자세한 내용은 [eCommerce 개발](/help/sites-developing/ecommerce.md)을 참조하십시오.

## 기본 기능 {#main-features}

AEM eCommerce는 다음을 제공합니다.

* 프로젝트에 대해 수행할 수 있는 사항을 보여주는 **기본 제공 AEM 구성 요소** 개수입니다.

   * 제품 표시
   * 장바구니
   * 체크아웃
   * 최근에 본 제품
   * 바우처
   * 및 기타

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >또한 AEM에서 제공하는 통합 프레임워크를 사용하면 특정 eCommerce 엔진과 독립적으로 상거래 기능을 위한 추가 AEM 구성 요소를 작성할 수 있습니다.

* **검색**  - 다음 중 하나를 사용합니다.

   * AEM 검색
   * 전자 상거래 시스템 검색
   * 타사 검색(예: Search &amp; Promote)
   * 또는 그 조합입니다.

   ![chlimage_1-151](assets/chlimage_1-151.png)

* AEM 기능을 사용하여 컨텐츠를 여러 채널&#x200B;**에 표시하고 전체 브라우저 창이나 모바일 장치가 되도록 합니다.** 이렇게 하면 방문자가 필요로 하는 형식으로 콘텐츠가 전달됩니다.

   ![chlimage_1-152](assets/chlimage_1-152.png)

* **AEM eCommerce framework](#the-framework)**&#x200B;를 기반으로 자체 통합 구현을 개발할 수 있는 기능.[

   현재 사용할 수 있는 두 구현은 모두 일반적인 API(프레임워크)의 맨 위에 같은 기준으로 빌드됩니다. 새 통합 구현에는 통합에 필요한 기능만 구현됩니다. 프런트엔드 구성 요소는 새로운 구현에서 인터페이스를 사용하여 사용할 수 있습니다. 즉, 구현과 독립적입니다.

* 쇼핑객의 데이터 및 활동&#x200B;**을(를) 기반으로 하여**&#x200B;경험 기반 상거래를 개발할 수 있습니다. 이를 통해 다음과 같은 많은 시나리오를 실현할 수 있습니다.

   * 한 가지 예를 들자면 총 주문이 특정 금액을 초과하는 경우 운송 비용을 줄일 수 있습니다.
   * 프로필 데이터(예: 위치)를 사용하는 계절별 오퍼를 제공할 수도 있습니다. 그런 다음 필요할 때 다른 요소에 따라 이러한 매개 변수를 다시 강조 표시할 수 있습니다.

   아래 예에는 장바구니의 컨텐츠가 $75보다 작으므로 하나의 Teaser가 표시됩니다.

   ![chlimage_1-153](assets/chlimage_1-153.png)

   장바구니의 컨텐츠가 $75를 초과하는 경우 이를 변경할 수 있습니다.

   ![chlimage_1-154](assets/chlimage_1-154.png)

* 및 기타 기능은 다음과 같습니다.

   * 세션 간에 장바구니 콘텐츠가 유지됩니다.
   * 전체 주문 내역
   * 빠른 카탈로그 업데이트

## 프레임워크 {#the-framework}

[개념](/help/sites-administering/concepts.md) 섹션에서는 프레임워크를 보다 자세히 설명하지만, 다음은 프레임워크의 고속 보기를 제공합니다.

### 뭐? {#what}

* 통합 프레임워크는 기능을 보여주는 다양한 구성 요소인 API와 연결 방법의 예를 제공하기 위한 여러 확장을 제공합니다.
* 프레임워크는 프로젝트 구현에 필요한 기본 구조를 제공합니다.
* 프레임워크는 확장 가능합니다.
* 프레임워크는 즉시 사용 가능한 사이트를 제공하지 않습니다. 프레임워크를 사양에 맞게 조정하려면 항상 특정 양의 개발 작업이 필요합니다.

### 왜? {#why}

* 사용자 지정된 eCommerce 사이트를 빠르게 구현하는 데 필요한 기본 메커니즘을 제공합니다.
* Tp는 실제 eCommerce 사이트를 개발하는 데 필요한 유연성을 제공합니다.
* 모범 사례를 보여줍니다.
