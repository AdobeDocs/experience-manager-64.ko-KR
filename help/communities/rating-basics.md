---
title: 등급 핵심 사항
seo-title: Rating Essentials
description: 등급 구성 요소 개요
seo-description: Rating component overview
uuid: 48ef61ad-be7a-4a6b-a284-23e5bb4f1671
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7dc3ef57-05c3-45d4-ace3-bb3ba6ea768b
exl-id: f722051c-9512-4420-b12e-cb20aa6759f7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 3%

---

# 등급 핵심 사항 {#rating-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

등급 구성 요소, a [총계](tally.md) 하위 클래스를 사용하면 커뮤니티 구성원이 웹 사이트의 기능을 평가할 수 있습니다.

동일한 페이지에 투표 구성 요소의 여러 인스턴스를 배치할 수 있습니다. 각 인스턴스는 고유한 로 구성해야 합니다 `tally name` 속성을 사용합니다.

등급 익명의 게시는 지원되지 않습니다. 한 번만 등급에 참여하려면 사이트 방문자가 등록하고 로그인해야 합니다. 로그인한 방문자(구성원)는 언제든지 등급을 변경할 수 있습니다.

## 클라이언트측 핵심 사항 {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td> 소셜/총계/구성 요소/hbs/등급</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>포함 가능</strong></a></td> 
   <td>예 - 속성은 편집 가능합니다. <i>디자인 </i>모드</td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.rating</td> 
  </tr> 
  <tr> 
   <td> <strong>템플릿</strong></td> 
   <td><p> /libs/social/tally/components/hbs/rating/rating.hbs<br /> /libs/social/tally/components/hbs/rating/display.hbs<br /> /libs/social/tally/components/hbs/rating/histogram.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/rating/clientlibs/ratingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>속성</strong></td> 
   <td><p>자세한 내용은 <a href="rating.md">등급 사용</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [클라이언트측 사용자 지정](client-customize.md)

## 서버측 핵심 사항 {#essentials-for-server-side}

* [총계 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [집계 끝점](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [서버측 사용자 지정](server-customize.md)

### 게시된 등급 액세스(UGC) {#accessing-posted-ratings-ugc}

조정을 위한 표준 방법 중 하나를 사용하여 UGC가 중재되어야 합니다.\
자세한 내용은 [사용자가 생성한 컨텐츠 중재](moderate-ugc.md).

AEM 6.1 Communities에서 [일반 상점](working-with-srp.md) UGC의 경우 선택한 저장소 옵션(예: ASRP, MSRP 또는 JSRP)에 관계없이 UGC에 프로그래밍 방식으로 액세스할 수 있습니다.

**저장소에서 UGC의 위치와 형식은 경고 없이 변경될 수 있습니다**.

다음을 참조하십시오.

* [저장소 리소스 공급자 개요](srp.md) - 소개 및 저장소 사용 개요
* [SRP 및 UGC 핵심 사항](srp-and-ugc.md) - SRP 유틸리티 메서드 및 예제
* [SRP를 사용하여 UGC 액세스](accessing-ugc-with-srp.md) - 코딩 지침
* [SocialUtils 리팩터링](socialutils.md) - 사용 중단된 유틸리티 메서드를 현재 SRP 유틸리티 메서드에 매핑
