---
title: AEM 6.4 Communities로 업그레이드
seo-title: AEM 6.4 Communities로 업그레이드
description: 이전 버전에서 AEM 6.4 Communities로 업그레이드하는 방법
seo-description: 이전 버전에서 AEM 6.4 Communities로 업그레이드하는 방법
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 3%

---

# AEM 6.4 Communities로 업그레이드 {#upgrading-to-aem-communities}

각 사이트의 토폴로지 및 기능에 따라 AEM Communities 6.4로 업그레이드하거나 최신 기능 팩을 설치할 때 다음 작업이 필요할 수 있습니다.

이 섹션은 Communities에만 해당되며 [AEM 6.4](../../help/sites-deploying/upgrade.md)(플랫폼)으로 업그레이드하는 데 제공된 정보를 보완합니다.

## AEM 6.1 이상에서 업그레이드 {#upgrading-from-aem-or-later}

### Solr {#reindex-solr} 다시 색인화

MSRP로 구성된 배포에 새 커뮤니티 기능 팩을 설치할 때 다음이 필요합니다.

1. [최신 기능 팩](deploy-communities.md#latestfeaturepack) 설치
2. [최신 Solr 구성 파일 설치](msrp.md#upgrading)
3. MSRP 다시 색인화

   [MSRP 재인덱스 도구](msrp.md#msrp-reindex-tool) 섹션을 참조하십시오.

### 사용 2.0 {#enablement}

AEM 6.3부터 사용 기능은 더 이상 MySQL에 보고 정보를 저장하지 않습니다. MySQL 종속성은 SCORM 컨텐츠를 추적하기 위해서만 있습니다.

지원 1.0에서 콘텐츠 마이그레이션에 대한 도움이 필요하면 [고객 지원 센터](https://helpx.adobe.com/kr/marketing-cloud/contact-support.html)에 문의하십시오.

## AEM 6.0에서 업그레이드 {#upgrading-from-aem}

사전 기존 UGC를 유지해야 하는 경우 그렇게 하는 방법은 배포에 UGC [온-프레미스](#on-premise-storage) 또는 [Adobe 클라우드](#adobe-cloud-storage)가 저장되어 있는지 여부에 따라 다릅니다.

### Adobe 클라우드 저장소 {#adobe-cloud-storage}

업그레이드된 사이트가 Adobe 클라우드 저장소를 사용하도록 구성된 경우 SRP 메서드가 이전 위치에서 기존 UGC를 찾을 수 없어서 모든 UGC가 손실된 것처럼(잘못) 표시될 수 있습니다.

따라서 ASRP에서 `AEM 6.0 compatability-mode`을 사용하여 UGC에 액세스하도록 지시하는 기능이 있습니다.

모든 AEM 6.3 작성자 및 게시 인스턴스의 경우

1. 관리자 권한으로 로그인
2. [ASRP](asrp.md) 구성
3. 기존 UGC를 표시하려면 다음 단계를 따르십시오.
나.예를 들어 웹 콘솔을 찾습니다
   [https://&lt;host>:&lt;port>/system/console/](http://localhost:4502/system/console/configMgr)
configMgrii. **[!UICONTROL AEM Communities 유틸리티]** 구성 찾기
3. 구성 패널을 확장하려면 선택합니다
   * *선택을 취소합니다* **`Cloud Storage`**
   * **[!UICONTROL 저장]**&#x200B;을 선택합니다

![chlimage_1-126](assets/chlimage_1-126.png)

### 온-프레미스 스토리지 {#on-premise-storage}

업그레이드된 사이트에서 클라우드 저장소를 사용하지 않는 경우 기존 UGC를 AEM 6.1 Communities에 도입된 새로운 구조를 준수하도록 변환해야 공통 스토어를 지원합니다.

이를 위해 GitHub에서 오픈 소스 마이그레이션 도구를 사용할 수 있습니다.\
[AEM Communities UGC 마이그레이션 도구](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java API {#java-apis}

AEM 6.0 소셜 커뮤니티에서 AEM 6.3 Communities로 업그레이드할 때 많은 API가 다른 패키지로 재구성되었습니다. 커뮤니티 기능 사용자 지정에 IDE를 사용할 때 대부분의 문제를 쉽게 해결해야 합니다.

더 이상 사용되지 않는 SocialUtils 패키지에 대한 자세한 내용은 [SocialUtils 리팩터링](socialutils.md)을 참조하십시오.

[Communities에 Maven 사용](maven.md)을 참조하십시오.

### JSP 구성 요소 템플릿 {#no-jsp-component-templates} 없음

[소셜 구성 요소 프레임워크](scf.md) (SCF)는 AEM 6.0 이전에 사용된 JSP(Java Server Page) 대신 [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) 템플릿 언어를 사용합니다.

AEM 6.0에서 JSP 구성 요소는 일반적으로 &quot;hbs&quot;라는 하위 폴더에 있는 HBS 구성 요소를 사용하여 같은 위치에서 새 HBS 프레임워크 구성 요소와 함께 남아 있습니다.

AEM 6.1부터 JSP 구성 요소가 완전히 제거되었습니다. Communities에서는 JSP 구성 요소의 모든 사용을 SCF 구성 요소로 대체하는 것이 좋습니다.

## AEM Communities UGC 마이그레이션 도구 {#aem-communities-ugc-migration-tool}

[AEM Communities UGC 마이그레이션 도구](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)는 GitHub에서 사용할 수 있는 오픈 소스 마이그레이션 도구로서, 이전 버전의 AEM social communities에서 UGC를 내보내고 AEM Communities 6.1 이상으로 가져올 수 있도록 사용자 지정할 수 있습니다.

이전 버전에서 UGC를 이동하는 것 외에도 도구를 사용하여 MSRP에서 DSRP로 등의 UGC를 하나의 [SRP](working-with-srp.md)에서 다른 로 이동할 수도 있습니다.

## AEM 5.6.1 또는 이전 {#upgrading-from-aem-or-earlier}에서 업그레이드

개념적으로, 다음과 같은 세 세대의 커뮤니티 구성 요소가 있습니다.

**1** 세대:대략 CQ 5.4부터 AEM 5.6.0까지입니다.  **** 이러한 구성 요소는 플랫폼 간에 UGC를 동기화하는 수단으로 복제를 사용하여 로컬 저장소에 UGC를 저장하는 구성 요소입니다. 다른 차이점은 작성 환경에서만 작성으로 구성된 블로그 기능뿐만 아니라 Java Server Pages(JSP)를 사용하는 구현과 관련되어 있습니다.

**2세대**:AEM 5.6.1부터 AEM 6.1까지 -  **** 컬렉션 및  **** 소셜 구성 요소가 혼합되어 있습니다. AEM 6.0에는 새로운 [소셜 구성 요소 프레임워크](scf.md)(SCF) 및 AEM 6.2가 도입되었으며, 여기서 UGC는 [스토리지 리소스 공급자](srp.md)(SRP)를 사용하여 액세스할 수 있습니다.[](working-with-srp.md)

**3세대**:AEM 6.2부터 SCF에 HBS(Handlebars) 구성 요소로 구현된  **** 소셜 구성 요소만 UGC에 대한 SRP를 선택해야 합니다.
