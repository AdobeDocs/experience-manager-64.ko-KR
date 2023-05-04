---
title: 지정 필수 항목
seo-title: Assignments Essentials
description: 지원 커뮤니티에 대한 지정 기능 개요
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 14%

---

# 지정 필수 항목 {#assignments-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 페이지에서는 [지원 커뮤니티](overview.md#enablement-community) 사이트.

지정 기능은 지원 커뮤니티 구성원에게 지원 리소스와 학습 경로를 할당하는 기능입니다.

## 클라이언트측 핵심 사항 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>포함 가능</strong></a></td> 
   <td>아니요</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrums<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learning path</td> 
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
   <td>자세한 내용은 <a href="assignments.md">지정 기능</a></td> 
  </tr>
 </tbody>
</table>

### 완료 및 성공 상태 {#completion-and-success-status}

완료 및 성공 상태는 보고서 및 지정 시 상태 배너에 사용됩니다.

완료 상태:

* 지정되지 않음
* 시작되지 않음(신규)
* 진행 중
* 완료

성공 상태:

* 알 수 없음
* 합격
* 실패

완료 및 성공 상태의 조합은 다음과 뿐입니다.

| **완료** | **성공** |
|---|---|
| 시작되지 않음 | 알 수 없음 |
| 진행 중 | 알 수 없음 |
| 완료 | 합격 |
| 완료 | 실패 |

## 서버측 핵심 사항 {#essentials-for-server-side}

### 지정 기능 {#assignments-function}

다음을 포함하는 커뮤니티 사이트 구조 [지정 함수](functions.md#assignments-function), 구성된 포함 ` [assignments](assignments.md)` 구성 요소.

### 참조 API {#reference-apis}

* [지원 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [보고 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [Reporting Analytics API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
