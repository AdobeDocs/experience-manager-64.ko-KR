---
title: Assignments Essentials
seo-title: Assignments Essentials
description: 역량 강화 커뮤니티를 위한 할당 기능 개요
seo-description: 역량 강화 커뮤니티를 위한 할당 기능 개요
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 12%

---


# 할당 필수 {#assignments-essentials}

이 페이지에서는 [지원 커뮤니티](overview.md#enablement-community) 사이트의 할당 기능 작업에 필요한 정보를 제공합니다.

할당 기능은 역량 강화 커뮤니티 구성원에게 역량 강화 리소스 및 학습 경로를 할당하는 기능입니다.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>includable</strong></a></td> 
   <td>아니오</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learning 경로</td> 
  </tr>
  <tr>
   <td> <strong>템플릿</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> 속성</strong></td> 
   <td><a href="assignments.md">할당 기능</a> 참조</td> 
  </tr>
 </tbody>
</table>

### 완료 및 성공 상태 {#completion-and-success-status}

완료 및 성공 상태는 보고와 할당의 상태 배너에서 사용됩니다.

완료 상태:

* 지정되지 않음
* 시작하지 않음(새로 만들기)
* 진행 중
* 완료

성공 상태:

* 알 수 없음
* 합격
* 실패

완료 및 성공 상태의 조합만 가능합니다.

| **완료** | **성공** |
|---|---|
| 시작되지 않음 | 알 수 없음 |
| 진행 중 | 알 수 없음 |
| 완료 | 합격 |
| 완료 | 실패 |

## Essentials for Server-Side {#essentials-for-server-side}

### 지정 기능 {#assignments-function}

[할당 함수](functions.md#assignments-function)을 포함하는 커뮤니티 사이트 구조에는 구성된 ` [assignments](assignments.md)` 구성 요소가 포함됩니다.

### 참조 API {#reference-apis}

* [활성 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [보고 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [보고 분석 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)