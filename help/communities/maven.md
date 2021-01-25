---
title: 커뮤니티에 대한 Maven 사용
seo-title: 커뮤니티에 대한 Maven 사용
description: AEM Communities API jar 및 AEM Uber API jar
seo-description: AEM Communities API jar 및 AEM Uber API jar
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
translation-type: tm+mt
source-git-commit: 5affffac6f953bcf1d436d8492ad6dd2a041b3b4
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# 커뮤니티 {#using-maven-for-communities}에 대한 마비사항 사용

## 개요 {#overview}

AEM Communities 설명서의 이 섹션에서는 다음과 같은 항목을 다룹니다.

* [Apache Maven을 사용하여 AEM 프로젝트 제작](../../help/sites-developing/ht-projects-maven.md).

개별 아티팩트를 대체하는 &quot;우버&quot; 아티팩트는 하나만 있습니다.

* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

>[!NOTE]
>
>AEM 6.4부터 커뮤니티 API는 명시적으로 릴리스되지 않습니다. 이제 모든 커뮤니티 API가 Uber jar 자체에 포함됩니다.
>
>최신 커뮤니티 릴리스를 최신 상태로 유지하는 것이 좋습니다.
>
>최신 버전을 확인하려면 [최신 릴리스](deploy-communities.md#latest-releases) 섹션을 참조하십시오.

## 종속 관계 예 {#maven-dependency-example}

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.4.8.3</version>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>최신 Uber jar 아티팩트를 식별하려면 [AEM Uber jar 리포지토리](https://mvnrepository.com/artifact/com.adobe.aem/uber-jar)을 참조하십시오.

<!--
# Using Maven for Communities {#using-maven-for-communities}

## Overview {#overview}

This section of the AEM Communities documentation is in addition to:

* [How to Build AEM Projects using Apache Maven](../../help/sites-developing/ht-projects-maven.md)

There are now two "uber" artifacts that replace individual artifacts:

* AEM [Communities API jar](#communities-api-jar-artifact)
* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Following is an example of a GAV for the AEM Communities API jar:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>

```

Ensure thet the version specified corresponds with the Communities package version installed for AEM Communities. To verify the installed version number:

1. Login with adminstrative privileges.
2. Browse to [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

3. locate the package *cq-socialcommunities-pkg-1.x.xxx*
4. extract the version from the package name
    * first version for AEM 6.3 is version 1.11.170
    * feature packs will be versions 1.12.xxx
    
>[!NOTE]
>
>It is recommended to keep up-to-date with the most recent Communities release.
>
>Visit the [Latest Releases](deploy-communities.md#latest-releases) section to identify the most recent version.

## Maven Dependency Example {#maven-dependency-example}

The Communities API jar must be specified before the Uber API jar.

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.3.0</version>
    <scope>provided</scope>
    <classifier>apis</classifier>
</dependency>
```
-->