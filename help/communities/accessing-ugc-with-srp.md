---
title: SRP를 사용하여 UGC 액세스
seo-title: SRP를 사용하여 UGC 액세스
description: 사이트가 ASRP 또는 MSRP를 사용하도록 구성된 경우 실제 UGC는 AEM의 노드 저장소(JCR)에 저장되지 않습니다.
seo-description: 사이트가 ASRP 또는 MSRP를 사용하도록 구성된 경우 실제 UGC는 AEM의 노드 저장소(JCR)에 저장되지 않습니다.
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192

---


# SRP를 사용하여 UGC 액세스 {#accessing-ugc-with-srp}

## SRP 정보 {#about-srp}

모든 AEM Communities 구성 요소 및 기능은 SocialResourceProvider API를 호출하여 모든 사용자 생성 콘텐츠(UGC)에 액세스하는 [소셜 구성 요소 프레임워크(SCF)](scf.md)기반으로 구축됩니다.

커뮤니티 사이트를 만들기 전에 기본 [토폴로지와](working-with-srp.md) 일치하는 구현을 선택하도록 SRP( [저장소 리소스 공급자)](topologies.md)를 구성해야 합니다. SRP 구현은 다음 세 가지 스토리지 옵션을 기반으로 합니다.

1. [ASRP](asrp.md) - Adobe On-Demand 스토리지
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## UGC 스토리지 정보 {#about-ugc-storage}

UGC의 스토리지에 대해 알아야 할 중요한 것은 사이트가 ASRP 또는 MSRP를 사용하도록 구성된 경우 실제 UGC는 AEM의 [노드 저장소](../../help/sites-deploying/data-store-config.md) (JCR)에 저장되지 않습니다.

JCR에 유용한 메타데이터를 제공하기 위해 UGC를 그림자로 표시하는 노드가 있을 수 있지만 이러한 노드는 실제 UGC와 혼동하지 않습니다.

스토리지 [리소스 공급자 개요를 참조하십시오.](srp.md)

## 모범 사례 {#best-practice}

사용자 정의 구성 요소를 개발할 때 개발자는 현재 선택된 토폴로지와 독립적으로 코드를 작성하도록 주의해야 합니다. 따라서 향후 새로운 토폴로지로 유연하게 이동할 수 있습니다.

### JCR을 사용할 수 없다고 가정 {#assume-jcr-not-available}

JCR에 관련된 메서드는 사용하지 않아야 합니다.

사용 방법:

* Sling API(Sling Resource)
   * JCR 노드가 있다고 가정하지 않음

* OSGi 이벤트
   * JCR 이벤트가 있다고 가정하지 않음

* [소셜 리소스 유틸리티](socialutils.md#socialresourceutilities-package)
* [SCF 유틸리티](socialutils.md#scfutilities-package)

피하는 방법:

* 노드 API
* JCR 이벤트
* 워크플로우 런터(JCR 이벤트 사용)

### 검색 컬렉션 사용 {#use-search-collections}

SRP마다 다른 기본 쿼리 언어를 사용할 수 있습니다. com.adobe.cq.sosocial.ugc.api [패키지의](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) 메서드를 사용하여 적절한 쿼리 언어를 호출하는 것이 좋습니다.

자세한 내용은 Search Essentials [를 참조하십시오](search-implementation.md).

## 리소스 {#resources}

* [커뮤니티 컨텐츠](working-with-srp.md) 저장소 - UGC 일반 스토어에 사용할 수 있는 SRP에 대해 설명합니다.
* [스토리지 자원 공급자 개요](srp.md) - 소개 및 저장소 사용 개요
* [SRP 및 UGC Essentials](srp-and-ugc.md) - SRP 유틸리티 방법 및 예제
* [Search Essentials](search-implementation.md) - UGC 검색을 위한 필수 정보
* [SocialUtils 리팩토링](socialutils.md) - 사용되지 않는 유틸리티 메서드를 현재 SRP 유틸리티 메서드에 매핑
