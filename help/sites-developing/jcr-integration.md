---
title: JCR 통합
seo-title: JCR Integration
description: JCR 수준에서 통합해야 하는 경우를 위한 팁
seo-description: Tips for when you must integrate at the JCR level
uuid: 11518baf-521e-471d-ad4f-2baa76075cfa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: e6647a11-a36e-4808-bb61-29b2895c6b1d
exl-id: 3e9727a5-32f8-40ad-aa06-619f50d109b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 3%

---

# JCR 통합{#jcr-integration}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## JCR API보다 Sling Resource API를 선호합니다 {#prefer-the-sling-resource-api-to-jcr-api}

Sling API는 JCR API보다 더 높고 추상적인 수준에서 작동합니다. 따라서 코드를 보다 재사용이 가능하고 기본 스토리지와 독립적으로 사용할 수 있습니다. 따라서 필요한 경우 ResourceProvider 메커니즘을 통해 외부 가상 데이터를 보다 쉽게 포함할 수 있습니다.

## 가능하면 쿼리를 사용하지 마십시오 {#avoid-queries-wherever-possible}

쿼리를 실행하는 것보다 항상 데이터를 검색할 저장소를 탐색하는 것이 더 빠릅니다. 최종 사용자 쿼리 또는 전체 저장소에서 구조화된 콘텐츠를 찾아야 하는 등과 같이 쿼리가 필요한 경우가 있지만, 다른 모든 경우에는 필요한 노드로 이동하는 것이 좋습니다. 쿼리는 항상 탐색 구성 요소, &quot;최근 항목 목록&quot;, 항목 수 등과 같은 렌더링 논리에 피해야 합니다. 이러한 경우 렌더링할 때 직접 사용할 수 있도록 계층 구조를 자세히 살펴보거나 결과를 미리 캐시하는 것이 좋습니다.

## JCR 관찰 범위 제한 {#restrict-the-scope-of-jcr-observation}

저장소에서 이벤트를 수신할 때 범위를 최대한 좁히는 것이 중요합니다. 예를 들어, 에서 이벤트를 수신하는 것이 훨씬 낫다 `/etc/mycompany` 듣는것보다 `/etc`. 저장소 루트에서 이벤트를 수신하지 않습니다. 또한 콜백 메서드가 수행할 작업이 없는 경우 가능한 한 빨리 실행되도록 하십시오.

## JCR 관리자 액세스 사용 제거 {#eliminate-use-of-jcr-admin-access}

AEM 6부터는 ResourceResolverFactory에서 관리 세션을 받을 때 로그인 관리가 더 이상 사용되지 않습니다. 대신 이 유형의 액세스가 필요한 백 오피스 작업에 대해 서비스 계정을 만들어야 하며 ResourceResolverFactory를 사용하여 이 계정에 대한 ResourceResolver를 가져올 수 있습니다.
