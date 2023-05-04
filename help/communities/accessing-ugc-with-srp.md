---
title: SRP를 사용하여 UGC 액세스
seo-title: Accessing UGC with SRP
description: 사이트가 ASRP 또는 MSRP를 사용하도록 구성된 경우 실제 UGC는 AEM 노드 저장소(JCR)에 저장되지 않습니다
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 2%

---

# SRP를 사용하여 UGC 액세스 {#accessing-ugc-with-srp}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## SRP 정보 {#about-srp}

모든 AEM Communities 구성 요소 및 기능은 [SCF(소셜 구성 요소 프레임워크)](scf.md)- SocialResourceProvider API를 호출하여 모든 사용자 생성 콘텐츠(UGC)에 액세스합니다.

커뮤니티 사이트를 만들기 전에 [저장소 리소스 공급자(SRP)](working-with-srp.md) 기본 구현과 일치하는 구현을 선택하도록 구성해야 합니다 [토폴로지](topologies.md). SRP 구현은 다음 세 가지 스토리지 옵션을 기반으로 합니다.

1. [ASRP](asrp.md) - 온디맨드 스토리지 Adobe
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## UGC 스토리지 정보 {#about-ugc-storage}

UGC 저장에 대해 알고 있어야 하는 중요한 것은 사이트가 ASRP 또는 MSRP를 사용하도록 구성된 경우 실제 UGC가 AEM에 저장되지 않는다는 것입니다 [노드 저장소](../../help/sites-deploying/data-store-config.md) (JCR).

JCR에 유용한 메타데이터를 제공하기 위해 UGC를 그림자로 표시하는 노드가 있을 수 있지만 이러한 노드는 실제 UGC와 혼동하지 않을 수 있습니다.

자세한 내용은 [저장소 리소스 공급자 개요.](srp.md)

## 우수 사례 {#best-practice}

사용자 지정 구성 요소를 개발할 때는 개발자는 현재 선택한 토폴로지와 독립적으로 코드를 작성하도록 주의하여 향후 새로운 토폴로지로 이동할 수 있는 유연성을 유지해야 합니다.

### JCR을 사용할 수 없다고 가정합니다. {#assume-jcr-not-available}

JCR에 관련된 메서드는 사용하지 않아야 합니다.

사용 방법:

* Sling API(Sling Resource)
   * JCR 노드가 있다고 가정하지 마십시오

* OSGi 이벤트
   * JCR 이벤트가 있다고 가정하지 마십시오

* [소셜 리소스 유틸리티](socialutils.md#socialresourceutilities-package)
* [SCF 유틸리티](socialutils.md#scfutilities-package)

피해야 할 방법:

* 노드 API
* JCR 이벤트
* 워크플로우 런처(JCR 이벤트를 사용하는)

### 검색 컬렉션 사용 {#use-search-collections}

SRP마다 다른 기본 쿼리 언어를 사용할 수 있습니다. 에서는 [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) 패키지를 사용하여 적절한 쿼리 언어를 호출합니다.

자세한 내용은 [검색 핵심 사항](search-implementation.md).

## 리소스 {#resources}

* [커뮤니티 컨텐츠 저장소](working-with-srp.md) - UGC 공용 스토어에 사용 가능한 SRP 선택에 대해 설명합니다.
* [저장소 리소스 공급자 개요](srp.md) - 소개 및 저장소 사용 개요
* [SRP 및 UGC 핵심 사항](srp-and-ugc.md) - SRP 유틸리티 메서드 및 예제
* [검색 핵심 사항](search-implementation.md) - UGC 검색을 위한 필수 정보
* [SocialUtils 리팩터링](socialutils.md) - 사용 중단된 유틸리티 메서드를 현재 SRP 유틸리티 메서드에 매핑
