---
title: Leaderboard Essentials
seo-title: Leaderboard Essentials
description: 리드 보드 기능 개요
seo-description: Leaderboard feature overview
uuid: 815a6928-b147-496d-9751-13159ad1304d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7449f99e-77d7-4c0f-96d5-b67d5e1f124a
exl-id: 20c16e96-2ba8-4f2d-8cfa-8cd804e3441f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 9%

---

# Leaderboard Essentials {#leaderboard-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 페이지에서는 리드 보드 기능 작업에 필요한 필수 정보를 제공합니다.

페이지에 리드 보드 구성 요소를 포함하기 전에 다음을 구성해야 합니다 [커뮤니티 점수 및 배지](implementing-scoring.md). 참조 - [점수 책정 및 배지 핵심 사항](configure-scoring.md).

## 클라이언트측 핵심 사항 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>소셜/게임화/구성 요소/hbs/leadboard</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>포함 가능</strong></a></td> 
   <td>아니요</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.gamification.hbs.leaderboard</td> 
  </tr>
  <tr>
   <td> <strong>템플릿</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/leaderboard.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/clientlibs/leaderboard.css</td> 
  </tr>
  <tr>
   <td><strong> 속성</strong></td> 
   <td>자세한 내용은 <a href="enabling-leaderboard.md">리드 보드 기능</a></td> 
  </tr>
 </tbody>
</table>

* [클라이언트측 사용자 지정](client-customize.md)

### 파일 라이브러리 기능 {#file-library-function}

다음을 포함하는 커뮤니티 사이트 구조 [리드 보드 기능](functions.md#leaderboard-function), 구성된 포함 `leaderboard` 구성 요소.
