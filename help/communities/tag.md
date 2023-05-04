---
title: 태그 핵심 사항
seo-title: Tag Essentials
description: 태그 개요
seo-description: Tag overview
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
exl-id: 863ee5e3-daa7-4f7d-8897-291d367cf29d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 4%

---

# 태그 핵심 사항 {#tag-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Communities 구성 요소가 태깅을 사용하도록 구성되면 커뮤니티 구성원은 게시 환경에서 게시할 콘텐츠에 태그를 지정할 수 있습니다.

게시 환경에 적용되는 태그의 기본 인프라는 페이지 및 자산과 같이 작성 환경의 컨텐츠에 적용되는 태그와 동일합니다.

* 자세한 내용은 [태그 관리](../../help/sites-administering/tags.md) 및 [사용자 생성 컨텐츠에 태깅](tag-ugc.md) (UGC) 를 참조하십시오.

* 자세한 내용은 [개발자를 위한 태깅](../../help/sites-developing/tags.md) 에 대한 정보 [태그 프레임워크](../../help/sites-developing/framework.md) 태그 포함 및 확장 [사용자 정의 애플리케이션](../../help/sites-developing/building.md).

* 자세한 내용은 [Social Tag Cloud 사용](tagcloud.md) 를 참조하십시오 `social tag cloud` 구성 요소를 페이지에 추가하여 게시 환경에서 UGC에 적용된 태그를 강조 표시합니다.

* 자세한 내용은 [태깅 지원 리소스](tag-resources.md) 을 참조하십시오.

UGC의 태깅은 다음을 구성할 때 활성화할 수 있습니다 [커뮤니티 사이트](sites-console.md#tagging) 또는 다음 기능 중 하나:

* [블로그](blog-feature.md)
* [달력](calendar.md)
* [파일 라이브러리](file-library.md)
* [포럼](forum.md)
* [QnA](working-with-qna.md)

## 클라이언트측 핵심 사항 {#essentials-for-client-side}

### 소셜 태그 클라우드 {#social-tag-cloud}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/commons/components/hbs/tagcloud</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>포함 가능</strong></a></td> 
   <td>아니요</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.tagcloud</td> 
  </tr>
  <tr>
   <td> <strong>템플릿</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td> 
  </tr>
  <tr>
   <td><strong>속성</strong></td> 
   <td>자세한 내용은 <a href="tagcloud.md">Social Tag Cloud 사용</a></td> 
  </tr>
 </tbody>
</table>

* [클라이언트측 사용자 지정](client-customize.md)

## 서버측 핵심 사항 {#essentials-for-server-side}

* [Social Tag Cloud API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [소셜 태그 관리자](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [서버측 사용자 지정](server-customize.md)

## 태그 검색 {#tag-searching}

기준 [기능 팩 1](deploy-communities.md#latestfeaturepack) (FP1), 태그 검색은 [태그 제목](../../help/sites-developing/framework.md#tag-characteristics).

FP1 이전에는 [태그 id](../../help/sites-developing/framework.md#tagid).
