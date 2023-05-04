---
title: Ideation Essentials
seo-title: Ideation Essentials
description: 이미지 기능 개요
seo-description: Ideation feature overview
uuid: abaf03ee-8bf4-4241-96c3-474c95a30a88
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9e4f2f0-d1ff-40c0-abcf-645e40586a84
exl-id: 7fb68293-c6e3-4793-b433-205bcfc23e20
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Ideation Essentials {#ideation-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 페이지에서는 포럼과 유사하지만 초안으로 저장하는 기능 및 보다 공동 작업 느낌을 갖는 아이디어 기능 작업에 필요한 정보를 제공합니다.

## 클라이언트측 핵심 사항 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>소셜/관념화/구성 요소/hbs/관념화</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>포함 가능</strong></a></td> 
   <td>아니요</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.voting<br /> cq.social.hbs.linking<br /> cq.social.hbs.ideation</td> 
  </tr>
  <tr>
   <td> <strong>템플릿</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/ideation.hbs<br /> /libs/social/ideation/components/hbs/ideation/ideationlists.hbs<br /> /libs/social/ideation/components/hbs/ideation/composer.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/clientlibs/ideation.css</td> 
  </tr>
  <tr>
   <td><strong> 속성</strong></td> 
   <td>자세한 내용은 <a href="ideation-feature.md">이미지 기능</a></td> 
  </tr>
 </tbody>
</table>

* [클라이언트측 사용자 지정](client-customize.md)

### 관념화 기능 {#ideation-function}

다음을 포함하는 커뮤니티 사이트 구조 [관념화 함수](functions.md#ideation-function), 구성된 포함 `ideation` 구성 요소.
