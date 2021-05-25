---
title: 리소스 매핑
seo-title: 리소스 매핑
description: 리소스 매핑을 사용하여 AEM용 리디렉션, 별칭 URL 및 가상 호스트를 정의하는 방법을 알아봅니다.
seo-description: 리소스 매핑을 사용하여 AEM용 리디렉션, 별칭 URL 및 가상 호스트를 정의하는 방법을 알아봅니다.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
feature: 구성
exl-id: 81dddbab-1a9e-49ee-b2a5-a8e4de3630d1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---

# 리소스 매핑{#resource-mapping}

리소스 매핑은 AEM에 대한 리디렉션, 별칭 URL 및 가상 호스트를 정의하는 데 사용됩니다.

예를 들어 다음 매핑을 사용하여 다음을 수행할 수 있습니다.

* 웹 사이트 방문자가 내부 구조를 숨기지 않도록 모든 요청에 `/content` 접두사를 붙입니다.
* 웹 사이트의 `/content/en/gateway` 페이지에 대한 모든 요청이 `https://gbiv.com/` (으)로 리디렉션되도록 리디렉션을 정의합니다.

가능한 HTTP 매핑 [은 /content](#configuring-an-internal-redirect-to-content)이 있는 localhost:4503에 모든 요청을 접두사로 추가합니다. 다음과 같은 매핑을 사용하여 방문자가 웹 사이트를 방문하도록 내부 구조를 숨길 수 있습니다.

`localhost:4503/content/geometrixx/en/products.html`

를 사용하여 액세스하려면

`localhost:4503/geometrixx/en/products.html`

매핑은 자동으로 `/content` 접두사를 `/geometrixx/en/products.html`에 추가합니다.

>[!CAUTION]
>
>별칭 URL은 정규 표현식 패턴을 지원하지 않습니다.

>[!NOTE]
>
>자세한 내용은 Sling 설명서 및 [리소스 해상도](https://sling.apache.org/site/resources.html) 및 [리소스](https://sling.apache.org/site/mappings-for-resource-resolution.html)매핑 을 참조하십시오.

## 매핑 정의 보기 {#viewing-mapping-definitions}

매핑은 JCR Resource Resolver가 평가하고(하향식) 일치하는 항목을 찾는 두 개의 목록에서 가져옵니다.

이러한 목록은 Felix 콘솔의 **JCR ResourceResolver** 옵션 아래에서 구성 정보와 함께 볼 수 있습니다.예: `https://<host>:<port>/system/console/jcrresolver`:

* 구성

   현재 구성( [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md)에 대해 정의된 대로)을 표시합니다.

* 구성 테스트

   URL 또는 리소스 경로를 입력할 수 있습니다. **Resolve** 또는 **맵**&#x200B;을 클릭하여 시스템이 항목을 변환하는 방법을 확인합니다.

* **Resolver Map**
EntriesResourceResolver에서 사용하는 항목 목록입니다.URL을 Resources에 매핑하는 메서드.

* **매핑 맵**
항목리소스 경로를 URL에 매핑하기 위해 ResourceResolver.map 메서드에서 사용하는 항목 목록입니다.

두 목록에는 응용 프로그램에 의해 기본값으로 정의된 항목을 포함하여 다양한 항목이 표시됩니다. 이러한 목표는 종종 사용자의 URL을 단순화하는 것입니다.

이 목록은 요청에 일치하는 정규식 **Pattern**&#x200B;을 추가하고, 적용할 리디렉션을 정의하는 **Replacement**&#x200B;를 추가합니다.

예를 들어,

**패턴** `^[^/]+/[^/]+/welcome$`

은(는) 다음을 트리거합니다.

**대체** `/libs/cq/core/content/welcome.html`.

요청을 리디렉션하려면:

`http://localhost:4503/welcome`

끝:

`http://localhost:4503/libs/cq/core/content/welcome.html`

저장소 내에 새 매핑 정의가 만들어집니다.

>[!NOTE]
>
>정규 표현식을 정의하는 방법을 설명하는 데 도움이 되는 사용 가능한 리소스는 많습니다.예: [https://www.regular-expressions.info/](https://www.regular-expressions.info/)

## AEM {#creating-mapping-definitions-in-aem}에서 매핑 정의 만들기

표준 AEM 설치에서 폴더를 찾을 수 있습니다.

`/etc/map/http`

HTTP 프로토콜에 대한 매핑을 정의할 때 사용되는 구조입니다. 매핑할 다른 프로토콜에 대해 `/etc/map` 아래에 다른 폴더( `sling:Folder`)를 만들 수 있습니다.

### /content {#configuring-an-internal-redirect-to-content}에 대한 내부 리디렉션 구성

모든 요청의 접두사를 `/content`과 함께 http://localhost:4503/에 추가하는 매핑을 생성하려면:

1. CRXDE를 사용하여 `/etc/map/http`으로 이동합니다.

1. 새 노드를 만듭니다.

   * **유형** `sling:Mapping`

      이 노드 유형은 필수가 아니지만 매핑에 사용됩니다.

   * **이름** `localhost_any`

1. **모두 저장**&#x200B;을 클릭합니다.
1. **** 이 노드에 다음 속성을 추가합니다.

   * **이름** `sling:match`

      * **유형** `String`
      * **값** `localhost.4503/`
   * **이름** `sling:internalRedirect`

      * **유형** `String`
      * **값** `/content/`


1. **모두 저장**&#x200B;을 클릭합니다.

이렇게 하면 다음과 같은 요청이 처리됩니다.\
`localhost:4503/geometrixx/en/products.html`\
로서의\
`localhost:4503/content/geometrixx/en/products.html`\
이 요청되었습니다.

>[!NOTE]
>
>사용 가능한 sling 속성 및 이 속성을 구성하는 방법에 대한 자세한 내용은 Sling 설명서의 [리소스](https://sling.apache.org/site/mappings-for-resource-resolution.html)를 참조하십시오.

>[!NOTE]
>
>`/etc/map.publish` 을 사용하여 게시 환경에 대한 구성을 보유할 수 있습니다. 그런 다음 이러한 위치를 복제해야 하며, 게시 환경의 [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver)의 **매핑 위치**&#x200B;에 대해 구성된 새 위치( `/etc/map.publish`)를 복제해야 합니다.
