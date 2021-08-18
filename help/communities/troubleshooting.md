---
title: 문제 해결
seo-title: 문제 해결
description: 알려진 문제를 포함한 커뮤니티 문제 해결
seo-description: 알려진 문제를 포함한 커뮤니티 문제 해결
uuid: 99225430-fa2a-4393-ae5a-18b19541c358
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cdb2d80a-2fbf-4ee6-b89b-b5d74e6d3bfc
exl-id: 1a1de20d-53f6-4787-92e3-e12f30d925d3
source-git-commit: a70f874ad7fcae59ee4c6ec20e23ffb2e339590b
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 1%

---

# 문제 해결 {#troubleshooting}

이 섹션에는 일반적인 문제와 알려진 문제가 포함되어 있습니다.

## 알려진 문제 {#known-issues}

### Dispatcher 새로 고침에 실패 {#dispatcher-refetch-fails}

최신 버전의 Jetty와 함께 Dispatcher 4.1.5를 사용하는 경우 레퍼치는 요청 시간이 초과될 때까지 기다린 후 &#39;원격 서버에서 응답을 받을 수 없음&#39;을 초래할 수 있습니다.

Dispatcher 4.1.6 이상을 사용하면 이 문제가 해결됩니다.

### CQ 5.4에서 업그레이드한 후 포럼 게시물에 액세스할 수 없음 {#cannot-access-forum-post-after-upgrading-from-cq}

CQ 5.4에서 포럼을 만들고 게시한 주제를 게시한 다음, 사이트가 AEM 5.6.1 이상으로 업그레이드된 경우 기존 게시물을 보려고 하면 페이지에 오류가 발생할 수 있습니다.

잘못된 패턴 문자 &#39;a&#39;\
이 서버에서 /content/demoforums/forum-test.html에 요청을 제공할 수 없습니다.

그리고 로그에는 다음이 포함됩니다.

```xml
20.03.2014 22:49:35.805 ERROR [10.177.45.32 [1395380975744] GET /content/demoforums/forum-test.html HTTP/1.1] com.day.cq.wcm.tags.IncludeTag Error while executing script content.jsp
org.apache.sling.api.scripting.ScriptEvaluationException: 
at org.apache.sling.scripting.core.impl.DefaultSlingScript.call(DefaultSlingScript.java:388)
at org.apache.sling.scripting.core.impl.DefaultSlingScript.eval(DefaultSlingScript.java:171)
```

문제는 com.day.cq.commons.date.RelativeTimeFormat의 형식 문자열이 5.4에서 5.5 사이에 변경되었으므로 &quot;ago&quot;의 &quot;a&quot;가 더 이상 허용되지 않습니다.

따라서 RelativeTimeFormat() API를 사용하는 모든 코드는 변경해야 합니다

* 시작: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r a", resourceBundle);`
* 끝: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r", resourceBundle);`

작성자 및 게시에서 이 오류는 다릅니다. 작성자는 자동으로 실패하고 포럼 주제가 표시되지 않습니다. 게시 시 페이지에 오류가 발생합니다.

자세한 내용은 [com.day.cq.commons.date.RelativeTimeFormat](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/date/RelativeTimeFormat.html) API를 참조하십시오.

## 일반적인 문제 {#common-concerns}

### 로그에 경고: 사용되지 않는 Handlebars {#warning-in-logs-handlebars-deprecated}

시작 중(1일 아님, 이후 모든 항목)에는 다음 경고가 로그에 표시될 수 있습니다.

* 11.04.2014 08:38:07.223 **WARN** [FelixStartLevel]com.github.jknack.handlebars.Handlebars Helper &#39;i18n&#39;이 &#39;com.adobe.cq.social.handlebars.I18nHelper@15bac645&#39;으로 대체되었습니다.

이 경고는 [SCF](scf.md#handlebarsjavascripttemplatinglanguage)에 사용되는 jknack.handlebars.Handlebars와 자체 i18n 도우미 유틸리티가 함께 제공되는 것으로 무시해도 안전합니다. 시작할 때 AEM 관련 [i18n helper](handlebars-helpers.md#i-n)로 대체됩니다. 이 경고는 기존 도우미의 재정의를 확인하기 위해 타사 라이브러리에서 생성합니다.

### 로그에 경고: OakResourceListener 프로세스OsgiEventQueue {#warning-in-logs-oakresourcelistener-processosgieventqueue}

많은 소셜 커뮤니티 포럼 항목을 게시하면 OakResourceListener processOsgiEventQueue에서 경고 및 정보 로그가 대량으로 발생할 수 있습니다.

이러한 경고는 무시해도 됩니다.

```xml
23.04.2014 14:21:18.900 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.frq/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.908 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.prx/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
```

### 로그에 오류: IndexElementFactory에 대한 NoClassDefFoundError {#error-in-logs-noclassdeffounderror-for-indexelementfactory}

AEM 5.6.1 GA를 최신 cq-socialcommunities-pkg-1.4.x로 업그레이드하거나 AEM 6.0으로 업그레이드하면 시작 중에 로그 파일에 오류가 발생하여 다시 시작 시 표시되지 않는 오류로 인해 자체적인 문제가 해결됩니다.

```xml
14.11.2013 20:52:39.453 ERROR [Apache Sling JCR Resource Event Queue Processor for path '/'] com.adobe.cq.social.storage.index.impl.IndexService Error occurred while processing event java.util.ConcurrentModificationException
14.11.2013 20:52:40.716 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory) java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory
14.11.2013 20:52:40.717 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Failed creating the component instance; see log for reason
```
