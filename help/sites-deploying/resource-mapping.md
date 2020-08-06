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
translation-type: tm+mt
source-git-commit: c4ac10736c937198aa0c81ecf547dd489ef93366
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 1%

---


# 리소스 매핑{#resource-mapping}

리소스 매핑은 AEM용 리디렉션, 별칭 URL 및 가상 호스트를 정의하는 데 사용됩니다.

예를 들어 다음 매핑을 사용할 수 있습니다.

* 웹 사이트 방문자가 내부 구조를 `/content` 숨길 수 있도록 모든 요청에 접두사를 붙입니다.
* 웹 사이트의 페이지에 대한 모든 요청이 리디렉션되도록 리디렉션 `/content/en/gateway` 을 정의합니다 `https://gbiv.com/`.

가능한 HTTP 매핑 [은 /content가 있는 모든 요청에 대해 접두사를 지정합니다](#configuring-an-internal-redirect-to-content). 이와 같은 매핑을 사용하면 웹 사이트 방문자로부터 내부 구조를 숨길 수 있습니다.

`localhost:4503/content/geometrixx/en/products.html`

을 사용하여 액세스하십시오.

`localhost:4503/geometrixx/en/products.html`

as the mapping will automatically add the prefix to `/content` `/geometrixx/en/products.html`.

>[!CAUTION]
>
>별칭 URL은 정규식 패턴을 지원하지 않습니다.

>[!NOTE]
>
>자세한 내용은 Sling 설명서 및 리소스 [해상도 및 리소스에](https://sling.apache.org/site/resources.html) 대한 [매핑](https://sling.apache.org/site/mappings-for-resource-resolution.html) 을 참조하십시오.

## 매핑 정의 보기 {#viewing-mapping-definitions}

매핑은 JCR 리소스 확인자가 일치하는 항목을 찾기 위해 평가한 두 개의 목록(위쪽-아래쪽)과 같습니다.

이러한 목록은 Felix 콘솔의 **JCR ResourceResolver** 옵션 아래에서 구성 정보와 함께 볼 수 있습니다. 예를 들면 다음과 같습니다. `https://<host>:<port>/system/console/jcrresolver`

* 구성

   Apache Sling 리소스 확인자에 대해 정의된 대로 현재 [구성을 표시합니다](/help/sites-deploying/osgi-configuration-settings.md).

* 구성 테스트

   이를 통해 URL 또는 리소스 경로를 입력할 수 있습니다. 해결 **또는** 맵 **** 을 클릭하여 시스템에서 항목을 변형하는 방법을 확인합니다.

* **해결 프로그램 맵 항목** ResourceResolver.resolve 메서드에서 URL을 리소스에 매핑하는 데 사용되는 항목 목록입니다.

* **매핑 맵 항목**&#x200B;리소스 해결 프로그램.map 메서드에서 리소스 경로를 URL에 매핑하는 데 사용되는 항목 목록입니다.

두 목록에는 애플리케이션에서 기본값으로 정의한 항목을 비롯하여 다양한 항목이 표시됩니다. 이러한 URL은 사용자의 URL을 단순화하는 데 사용됩니다.

목록은 요청에 **대응한 정규식**&#x200B;패턴과 적용할 리디렉션을 정의하는 **바꾸기** 기능을함께 제공합니다.

예를 들면 다음과 같습니다.

**패턴** `^[^/]+/[^/]+/welcome$`

는 다음을 트리거합니다.

**대체** `/libs/cq/core/content/welcome.html`.

요청을 리디렉션하려면:

`http://localhost:4503/welcome`

끝:

`http://localhost:4503/libs/cq/core/content/welcome.html`

저장소 내에 새 매핑 정의가 만들어집니다.

>[!NOTE]
>
>정규 표현식을 정의하는 방법을 설명하는 데 도움이 되는 많은 리소스가 있습니다. 예: [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## AEM에서 매핑 정의 만들기 {#creating-mapping-definitions-in-aem}

AEM의 표준 설치에서는 폴더를 찾을 수 있습니다.

`/etc/map/http`

HTTP 프로토콜에 대한 매핑을 정의할 때 사용되는 구조입니다. 매핑할 다른 프로토콜에 대해 다른 폴더( `sling:Folder`) `/etc/map` 를 만들 수 있습니다.

### /content로 내부 리디렉션 구성 {#configuring-an-internal-redirect-to-content}

모든 요청의 접두사를 http://localhost:4503/으로 지정하는 매핑을 만들려면 `/content`:

1. CRXDE를 사용하여 탐색합니다 `/etc/map/http`.

1. 새 노드 만들기:

   * **유형** `sling:Mapping`

      이 노드 유형은 반드시 사용해야 하는 것은 아니지만 이러한 매핑에 사용됩니다.

   * **이름** `localhost_any`

1. 모두 **저장을 클릭합니다**.
1. **이 노드에 다음 속성을 추가합니다** .

   * **이름** `sling:match`

      * **유형** `String`
      * **값** `localhost.4503/`
   * **이름** `sling:internalRedirect`

      * **유형** `String`
      * **값** `/content/`


1. 모두 **저장을 클릭합니다**.

이렇게 하면 다음과 같은 요청이 처리됩니다.\
`localhost:4503/geometrixx/en/products.html`\
as:\
`localhost:4503/content/geometrixx/en/products.html`\
이 요청되었습니다.

>[!NOTE]
>
>사용 가능한 슬링 [속성과](https://sling.apache.org/site/mappings-for-resource-resolution.html) 이러한 속성을 구성할 수 있는 방법에 대한 자세한 내용은 Sling 설명서의 리소스를 참조하십시오.

>[!NOTE]
>
>게시 환경 `/etc/map.publish` 에 대한 구성을 유지하는 데 사용할 수 있습니다. 그런 다음 이러한 항목을 복제해야 하며, 게시 환경의 Apache Sling 리소스 확인자 `/etc/map.publish`의 **매핑 위치** 에 대해 구성된 새 위치( [)](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) 를복제해야 합니다.

