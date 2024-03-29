---
title: 컨텐츠 속성을 사용하여 컨텐츠 내보내기
seo-title: Using Content Properties to Export Content
description: 다음 페이지에는 앱 속성 및 노드가 표시됩니다.
seo-description: The following page shows App Properties and Nodes.
uuid: 73f1832f-e457-47d0-a0e1-80af90897d31
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a3006835-b1d2-47d6-959a-cdb692e34e1e
exl-id: 27aa405d-2388-4f91-85d0-1a8709e0d5d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 6%

---

# 컨텐츠 속성을 사용하여 컨텐츠 내보내기{#using-content-properties-to-export-content}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>단일 페이지 애플리케이션 프레임워크 기반 클라이언트측 렌더링(예: React)이 필요한 프로젝트에 SPA 편집기를 사용하는 것이 좋습니다. [자세히 알아보기](/help/sites-developing/spa-overview.md).

앱은 *cq:페이지* AEM에서 확인하십시오.

이들 속성은 다음 위치에서 동일한 공통 속성을 공유합니다 *cq:Page* 아래에 표시된 것 외에도 통합 지원 속성을 나타냅니다.

## 앱 속성 {#app-properties}

다음 표는 다음과 같습니다 **앱 속성 및 노드**.

<table>
 <tbody>
  <tr>
   <td><strong>PropertyName</strong></td>
   <td><strong>유형</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>dps-cloudConfig</td>
   <td>문자열:경로</td>
   <td><p>구성된 Mobile On-Demand Cloud Service에 대한 경로입니다. AEM Mobile에서 Mobile On-Demand 작업(API 호출)에 사용됩니다.</p> <p>이 연결은 작성자가 앱을 연결할 Mobile On-Demand Cloud Service을 선택할 때 연결 관리 타일을 통해 구성됩니다.</p> </td>
  </tr>
  <tr>
   <td>dps-exportTemplate</td>
   <td>문자열:경로</td>
   <td><p>앱의 내보내기 구성에 대한 경로입니다. 내보내기 구성은 두 개의 하위 ContentSync 내보내기 구성 템플릿이 있는 폴더입니다.</p> <p><i>dps 문서</i>: 문서 컨텐츠를 내보내기 위한 ContentSync 내보내기 구성</p> <p><i>dps-HTMLResources</i>: 앱/문서 공유 리소스를 내보내기 위한 ContentSync 내보내기 구성</p> </td>
  </tr>
  <tr>
   <td>dps-projectId</td>
   <td>문자열</td>
   <td><p>이 앱이 연결/연결되어 있는 Mobile On-Demand 프로젝트의 ID/URI입니다.</p> <p>이 연결은 작성자가 연결된 Mobile On-Demand Cloud Service에 사용할 수 있는 프로젝트 목록에서 프로젝트를 선택할 때 연결 관리 타일을 통해 구성됩니다.</p> </td>
  </tr>
  <tr>
   <td>dps-projectTitle</td>
   <td>문자열</td>
   <td>앱 제목.</td>
  </tr>
  <tr>
   <td>dps-resourceType</td>
   <td>문자열</td>
   <td>컨텐츠 유형.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLRessources-lastUploaded</td>
   <td>날짜</td>
   <td>AEM에서 AEM Mobile으로 공유 리소스를 마지막으로 업로드한 날짜입니다.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLRessources-lastUploadedBy</td>
   <td>문자열:userid</td>
   <td>AEM에서 AEM Mobile으로 공유 리소스 요청의 마지막 업로드를 수행한 사용자의 ID입니다.</td>
  </tr>
  <tr>
   <td>page-dashboard-config</td>
   <td>문자열:경로</td>
   <td>대시보드 구성에 대한 경로입니다. 필요에 따라 경로를 사용자 지정 대시보드 구성으로 리디렉션할 수 있습니다.</td>
  </tr>
  <tr>
   <td>sling:resourceType</td>
   <td>문자열:경로</td>
   <td><p>또는 확장하는 cq:Component에 대한 경로 <i>mobileapps/core/components/instance.</i></p> <p>이렇게 하면 앱 카탈로그의 존재 여부 및 렌더링이 제공됩니다.</p> </td>
  </tr>
 </tbody>
</table>

다음을 사용할 수 있습니다 ***컨텐츠 속성*** 콘텐츠를 만들려면 문서 및 공유 리소스를 만들고 내보내려면 다음 리소스를 참조하십시오.

* [컨텐츠 속성](/help/mobile/content-properties.md)
* [문서 내보내기 구성 만들기](/help/mobile/creating-article-export-configuration.md)
* [공유 리소스 내보내기 구성 만들기](/help/mobile/creating-shared-resources-export-configuration.md)
