---
title: URL 표면화
seo-title: URL 표면화
description: Externalizer는 리소스 경로를 프로그래밍 방식으로 외부 및 절대 URL로 변환할 수 있는 OSGI 서비스입니다
seo-description: Externalizer는 리소스 경로를 프로그래밍 방식으로 외부 및 절대 URL로 변환할 수 있는 OSGI 서비스입니다
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---


# URL 표면화{#externalizing-urls}

AEM에서 **Externalizer**&#x200B;는 프로그래밍 방식으로 리소스 경로(예:사전 구성된 DNS로 경로를 접두사로 사용하여 외부 및 절대 URL(예: `https://www.mycompany.com/path/to/my/page`)에 `/path/to/my/page`) 추가

인스턴스가 웹 레이어 뒤에 실행 중일 경우 외부에서 볼 수 있는 URL을 알 수 없으므로 요청 범위 외부에서 링크를 만들어야 하는 경우가 있으므로 이 서비스는 이러한 외부 URL을 구성하고 작성할 수 있는 중앙 위치를 제공합니다.

이 페이지에서는 **Externalizer** 서비스를 구성하는 방법과 이 서비스를 사용하는 방법에 대해 설명합니다. 자세한 내용은 [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html)을 참조하십시오.

## Externalizer 서비스 {#configuring-the-externalizer-service} 구성

**Externalizer** 서비스를 사용하면 프로그래밍 방식으로 리소스 경로에 접두사를 지정하는 데 사용할 수 있는 여러 도메인을 중앙에서 정의할 수 있습니다. 각 도메인은 프로그래밍 방식으로 도메인을 참조하는 데 사용되는 고유한 이름으로 식별됩니다.

**Externalizer** 서비스에 대한 도메인 매핑을 정의하려면:

1. **도구**&#x200B;를 통해 구성 관리자로 이동한 다음 **웹 콘솔**&#x200B;을(를) 사용하거나 `https://<host>:<port>/system/console/configMgr.`를 입력합니다.
1. **Day CQ Link Externalizer**&#x200B;를 클릭하여 구성 대화 상자를 엽니다.

   >[!NOTE]
   >
   >구성에 대한 직접 링크는 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`입니다.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 도메인 매핑 정의:매핑은 도메인, 공간 및 도메인을 참조하는 코드에 사용할 수 있는 고유한 이름으로 구성됩니다.

   `<unique-name> [scheme://]server[:port][/contextpath]`, where:

   * **일반적으로** http 또는 https이지만 ftp 등일 수도 있습니다.;원하는 경우 https를 사용하여 https 링크를 적용합니다.URL의 외부화를 요청할 때 클라이언트 코드가 스키마를 무시하지 않는 경우에 사용됩니다.
   * **서버** 는 호스트 이름입니다(도메인 이름 또는 ip 주소).
   * **port** (선택 사항)는 포트 번호입니다.
   * **contextpath** (선택 사항)는 AEM이 다른 컨텍스트 경로 아래에 웹 앱으로 설치된 경우에만 설정됩니다.

   예를 들어,`production https://my.production.instance`

   다음 매핑 이름은 미리 정의되며 AEM이 매핑 이름에 의존할 때 항상 설정해야 합니다.

   * **local**  - 로컬 인스턴스
   * **작성자**  - 저작 시스템 DNS
   * **게시**  - 공개 웹 사이트 DNS

   >[!NOTE]
   >
   >사용자 지정 구성을 사용하면 &quot;프로덕션&quot;, &quot;스테이징&quot; 또는 &quot;내-내부-웹 서비스&quot;와 같은 외부 비-AEM 시스템이나 같은 새 범주를 추가할 수 있으며, 이러한 URL을 프로젝트의 코드 베이스의 여러 위치에서 하드 코딩하지 않는 데 유용합니다.

1. **저장**&#x200B;을 클릭하여 변경 내용을 저장합니다.

>[!NOTE]
>
>Adobe에서는 [구성을 저장소](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)에 추가하는 것이 좋습니다.

## Externalizer 서비스 {#using-the-externalizer-service} 사용

이 섹션에서는 **Externalizer** 서비스를 사용할 수 있는 방법에 대한 몇 가지 예를 보여 줍니다.

**JSP에서 Externalizer 서비스를 가져오려면 다음을 수행하십시오.**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**&#39;게시&#39; 도메인으로 경로를 외부화하려면:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

도메인 매핑 &quot; `publish https://www.website.com`&quot;이라고 가정할 경우 myExternalizedUrl은 &quot; `https://www.website.com/contextpath/my/page.html`&quot; 값으로 끝납니다.

**&#39;author&#39; 도메인으로 경로를 외부화하는 방법:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

도메인 매핑 &quot; `author https://author.website.com`&quot;이라고 가정할 경우 myExternalizedUrl은 &quot; `https://author.website.com/contextpath/my/page.html`&quot; 값으로 끝납니다.

**&#39;local&#39; 도메인으로 경로를 외부화하려면:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

도메인 매핑 &quot; `local https://publish-3.internal`&quot;이라고 가정할 경우 myExternalizedUrl은 &quot; `https://publish-3.internal/contextpath/my/page.html`&quot; 값으로 끝납니다.

[Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html)에서 더 많은 예를 찾을 수 있습니다.
