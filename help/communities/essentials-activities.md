---
title: 활동 스트림 핵심 사항
seo-title: Activity Stream Essentials
description: 구성원이 수행한 최근 활동 목록 또는 단일 컨텐츠 스레드에서 최근 활동 목록
seo-description: List of recent activites performed by a member or a list of recent activities on a single thread of content
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
exl-id: 74dcbefa-e670-419b-af9b-b3d3c593ebaa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 4%

---

# 활동 스트림 핵심 사항 {#activity-stream-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

커뮤니티 구성원의 활동(예: 포럼 또는 블로그에 게시)은 활동 스트림 구성 요소의 구성을 통해 다양한 방법으로 필터링 및 표시할 수 있는 스트림에 수집됩니다.

팔로우하는 기능은 커뮤니티 구성원이 관심 있는 게시나 다른 커뮤니티 구성원을 따를 때 다른 일련의 활동을 추가합니다.

모두 [커뮤니티 사이트](overview.md#communitiessites) 같은 방식으로 구성원 활동을 표시할 로그인한 구성원의 사용자 프로필 페이지를 포함합니다.

## 개념 {#concepts}

An *활동 스트림* 구성원이 수행한 최근 활동 목록이나 포럼 주제 또는 블로그 등의 단일 컨텐츠 스레드에 대한 최근 활동 목록입니다.

구성원은 다른 개인 또는 콘텐츠를 팔로우하여 활동 스트림을 따를 수 있습니다.

A *뉴스 피드* 다음은 구성원이 단일 스트림으로 이동하는 활동 스트림 병합입니다.

A [소셜 그래프](essentials-socialgraph.md) 한 구성원의 다음 관계를 캡처합니다.

## 클라이언트측 핵심 사항 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystreams/components/hbs/activitystreams</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>포함 가능</strong></a></td> 
   <td>아니요</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>템플릿</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> 속성</strong></td> 
   <td>자세한 내용은 <a href="activities.md">활동 스트림 기능</a></td> 
  </tr>
 </tbody>
</table>

* [클라이언트측 사용자 지정](client-customize.md)

## 서버측 핵심 사항 {#essentials-for-server-side}

* [Activity Streams API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Activity Streams 리스너 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [서버측 사용자 지정](server-customize.md)

### 활동 스트림 기능 {#activity-stream-function}

다음을 포함하는 커뮤니티 사이트 구조 [활동 스트림 함수](functions.md#activity-stream-function), 구성된 포함 `activity streams` 구성 요소.
