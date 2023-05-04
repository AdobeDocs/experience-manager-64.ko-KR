---
title: SocialUtils 리팩터링
seo-title: SocialUtils Refactoring
description: 패키지 com.adobe.cq.social.ugcbase.SocialUtils는 AEM 6.1에서 더 이상 사용되지 않습니다
seo-description: The package com.adobe.cq.social.ugcbase.SocialUtils was deprecated in AEM 6.1
uuid: 54a0d98e-5ead-4c12-850f-8252ea9b3263
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4ade0d6b-041e-4a2f-98f8-3b8fcae0fb29
exl-id: ba23188b-a72a-4349-b3e5-0fb50fd6312f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 3%

---

# SocialUtils 리팩터링 {#socialutils-refactoring}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## SocialUtils 패키지 사용 안 함 {#socialutils-package-deprecated}

패키지 **com.adobe.cq.social.ugcbase.SocialUtils** 는 AEM 6.1에서 더 이상 사용되지 않습니다.

다음 표에는 SocialUtils 메서드 대신 사용할 메서드가 나와 있습니다.

## SocialResourceUtilities 패키지  {#socialresourceutilities-package}

| com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities의 메서드 |
|---|
| 부울 checkPermission(ResourceResolver, String path, String action) |  |
| SocialResourceProvider getSocialResourceProvider(리소스) |  |
| SocialResourceConfiguration getStorageConfig(리소스) |  |
| 리소스 getUGCRessource(Resource userResource) |  |
| 리소스 getUGCRessource(Resource userResource, ResourceResolverFactory rrrf) | 새 항목 |
| 리소스 getUGCRessource(Resource userResource, ResourceResolverFactory rrrrf, String resourceTypeHint) | 새 항목 |
| 리소스 getUGCRessource(Resource userResource, String resourceTypeHint) |  |
| boolean hasModeratePermissions(리소스 리소스) |  |
| String resourceToACLPath(리소스) |  |
| String resourceToUGCtoragePath(리소스) | string resourceToUGCPath(리소스) 대체 |
| 문자열 UCToResourcePath(리소스) |  |
| 문자열 UCToResourcePath(String ugcPath) | 메서드 서명이 변경되었습니다. |
| String UGCoResourcePath(String ugcPath, ResourceResolver) | 새 항목 |

| 의 메서드 `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities |
|---|
| SocialResourceProvider getSocialResourceProvider(리소스) | 는 SocialResourceProvider getConfiguredProvider(리소스) 대체 |

## SCFUtifications 패키지 {#scfutilities-package}

| 의 메서드 `com.adobe.cq.social.`utilities.scf.api.SCFUtilites |
|---|
| String getAvatar(UserProperties userProperties) |
| String getAvatar(UserProperties userProperties, int size) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar, SocialUtils.AVATAR_SIZE) |
| Page getContainingPage(리소스) |
| String getSocialProfileURL(String 사용자 이름, ResourceResolver, Page) |
| UserProperties getUserProperties(ResourceResolver, String userId) |

## 내부용 {#for-internal-use-only}

| 부울 canAddNode(세션, 문자열 경로) |
|---|
| 문자열 createUniqueNameHint(문자열 메시지) |
| 문자열 createUniqueNameHint(문자열 메시지, int numRandomChars) |
| 문자열 generateRandomString(int length) |
| SocialResourceConfiguration getDefaultStorageConfig() |
| Page getPage(문자열 경로, ResourceResolver) |
| String getPagePath(리소스) |
| String getPagePath(문자열 경로) |
| String getResourceTypeForIncludedResource(리소스 구성 요소, String defaultResourceType, String designPropertyName) |
| String getResourceTypeFromDesign(Resource, String styleProperty, String defaultValue) |
| 부울 isResourceOwner(Resource) |
| String mapUGCPath(리소스) |
| String mapUGCPath(String ugcPath, ResourceResolver) |
| boolean mayPost(ResourceResolver, Resource resource) |
| String prepareUserGeneratedContent(ResourceResolver, String path) |

## 더 이상 메서드를 사용할 수 없습니다. {#methods-no-longer-available}

| 노드 createNode(ResourceResolver, String path, String nodeType) |
|---|
| 리소스 getResourceAtPath(ResourceResolver, String path) |
| 리소스 getResourceAtPath(ResourceResolver, String path, String resourceType) |
| 구성 getStorageCloudServiceConfig(리소스) |
| TranslationManager getTranslationManager() |
| TranslationSaveQueue getTranslationSaveQueue() |
| boolean mayAccessUGC(ResourceResolver) |
