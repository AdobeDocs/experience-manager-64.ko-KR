---
title: URL 표면화
seo-title: Externalizing URLs
description: Externalizer는 리소스 경로를 프로그래밍 방식으로 외부 및 절대 URL로 변환할 수 있는 OSGI 서비스입니다
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# URL 표면화{#externalizing-urls}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서 **외부 도우미** 는 리소스 경로(예: )를 프로그래밍 방식으로 변환할 수 있는 OSGI 서비스입니다. `/path/to/my/page`)을 외부 및 절대 URL에 넣습니다(예: `https://www.mycompany.com/path/to/my/page`) 접두사가 있는 DNS로 경로를 고정합니다.

인스턴스가 웹 레이어 뒤에서 실행 중인 경우 외부에서 볼 수 있는 URL을 알 수 없고, 경우에 따라 요청 범위 외부에서 링크를 만들어야 하기 때문에 이 서비스는 이러한 외부 URL을 구성하고 빌드할 수 있는 중앙 위치를 제공합니다.

이 페이지에서는 를 구성하는 방법을 설명합니다 **외부 도우미** 서비스 및 사용 방법. 자세한 내용은 [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Externalizer 서비스 구성 {#configuring-the-externalizer-service}

다음 **외부 도우미** 서비스를 사용하면 프로그래밍 방식으로 리소스 경로를 접두사로 추가하는 데 사용할 수 있는 여러 도메인을 중앙에서 정의할 수 있습니다. 각 도메인은 프로그래밍 방식으로 도메인을 참조하는 데 사용되는 고유한 이름으로 식별됩니다.

에 대한 도메인 매핑을 정의하려면 **외부 도우미** 서비스:

1. 를 통해 구성 관리자로 이동합니다 **도구**, 그런 다음 **웹 콘솔**, 또는 를 입력합니다. `https://<host>:<port>/system/console/configMgr.`
1. 클릭 **Day CQ Link Externalizer** 구성 대화 상자를 열려면 다음을 수행하십시오.

   >[!NOTE]
   >
   >구성에 대한 직접 링크는 다음과 같습니다 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 도메인 매핑 정의: 매핑은 코드 내에서 도메인, 공간 및 도메인을 참조하는 데 사용할 수 있는 고유한 이름으로 구성됩니다.

   `<unique-name> [scheme://]server[:port][/contextpath]`, 다음의 경우:

   * **체계** 는 일반적으로 http 또는 https이지만 ftp 등일 수 있습니다.; 원하는 경우 https 링크를 적용하려면 https를 사용하십시오. URL의 외부화를 요청할 때 클라이언트 코드가 스키마를 재정의하지 않는 경우 사용됩니다.
   * **server** 호스트 이름입니다(도메인 이름 또는 ip 주소일 수 있음).
   * **포트** (선택 사항)은 포트 번호입니다.
   * **contextpath** (선택 사항) AEM이 다른 컨텍스트 경로 아래에 웹 앱으로 설치된 경우에만 설정됩니다.

   예를 들어`production https://my.production.instance`

   다음 매핑 이름은 사전 정의되어 있으며, AEM이 매핑 이름을 사용함에 따라 항상 설정되어야 합니다.

   * **로컬** - 로컬 인스턴스
   * **작성자** - 작성 시스템 DNS
   * **게시** - 공개 웹 사이트 DNS

   >[!NOTE]
   >
   >사용자 지정 구성을 사용하면 &quot;프로덕션&quot;, &quot;스테이징&quot; 및 같은 새 카테고리 또는 &quot;my-internal-webservice&quot;와 같은 외부 비 AEM 시스템도 추가할 수 있으며, 이러한 URL을 프로젝트 코드 베이스의 여러 위치에서 하드코딩하지 않는 데 유용합니다.

1. 클릭 **저장** 변경 사항을 저장하려면 을 클릭합니다.

>[!NOTE]
>
>Adobe은 다음을 수행하는 것을 권장합니다. [저장소에 구성 추가](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Externalizer 서비스 사용 {#using-the-externalizer-service}

이 섹션에서는 **외부 도우미** 서비스를 사용할 수 있습니다.

**JSP에서 Externalizer 서비스를 가져오려면 다음을 수행하십시오.**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**&#39;publish&#39; 도메인으로 경로를 구체화하려면**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

도메인 매핑 &quot;이 가정함 `publish https://www.website.com`&quot;, myExternalizedUrl은 &quot; 값으로 끝납니다. `https://www.website.com/contextpath/my/page.html`&quot;.

**&#39;author&#39; 도메인으로 경로를 표면화하려면**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

도메인 매핑 &quot;이 가정함 `author https://author.website.com`&quot;, myExternalizedUrl은 &quot; 값으로 끝납니다. `https://author.website.com/contextpath/my/page.html`&quot;.

**&#39;local&#39; 도메인으로 경로를 표면화하려면**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

도메인 매핑 &quot;이 가정함 `local https://publish-3.internal`&quot;, myExternalizedUrl은 &quot; 값으로 끝납니다. `https://publish-3.internal/contextpath/my/page.html`&quot;.

자세한 예제는 [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
