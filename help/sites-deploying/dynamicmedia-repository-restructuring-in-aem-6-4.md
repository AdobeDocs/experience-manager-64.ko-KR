---
title: AEM 6.4에서 Dynamic Media 리포지토리 재구성
seo-title: AEM 6.4에서 Dynamic Media 리포지토리 재구성
description: Dynamic Media용 AEM 6.4의 새로운 저장소 구조로 마이그레이션하기 위해 필요한 변경 방법을 알아봅니다.
seo-description: Dynamic Media용 AEM 6.4의 새로운 저장소 구조로 마이그레이션하기 위해 필요한 변경 방법을 알아봅니다.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
translation-type: tm+mt
source-git-commit: 5dce4bcf4b10cce65798fd142a3eeb1956caf726
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 4%

---


# AEM 6.4에서 Dynamic Media 리포지토리 재구성{#dynamic-media-repository-restructuring-in-aem}

AEM 6.4 [페이지의 상위](/help/sites-deploying/repository-restructuring.md) 저장소 재구성 페이지에 설명된 대로 AEM 6.4로 업그레이드하는 고객은 이 페이지를 사용하여 Dynamic Media 솔루션에 영향을 주는 저장소 변경과 관련된 작업 노력을 평가해야 합니다. 일부 변경 사항은 AEM 6.4 업그레이드 프로세스 중에 작업해야 하는 반면, 다른 변경 사항은 6.5 업그레이드 때까지 연기될 수 있습니다.

**6.5 이전 업그레이드**

* [사용자 정의 응용 비디오 인코딩 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [다이내믹 미디어(DMS7) 클라우드 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [다이내믹 미디어(DM 하이브리드) Cloud Service 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [다이내믹 미디어 - YouTube Cloud Service 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [기타](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## 6.5 이전 업그레이드 {#prior-to-upgrade}

### 사용자 정의 응용 비디오 인코딩 구성  {#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>이전 위치</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>새 위치</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>구조 조정 지침</strong></td> 
   <td><p>다음 마이그레이션 스크립트를 실행하여 새 위치로 마이그레이션할 수 있습니다.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>또는 AEM UI에서 구성을 편집할 수 있으며 변경 사항이 새 위치에 저장됩니다.</p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media (DMS7) Cloud configuration {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>이전 위치</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>새 위치</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>구조 조정 지침</strong></td> 
   <td><p>고객은 다음 위치에서 마이그레이션 스크립트를 실행할 수 있습니다.<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Dynamic Media OSGi 번들을 다시 시작합니다.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

### 다이내믹 미디어(DM 하이브리드) Cloud Service 구성 {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>이전 위치</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>새 위치</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>구조 조정 지침</strong></td> 
   <td><p>아래 마이그레이션 스크립트를 실행하여 최신 모델에 정렬할 수 있습니다.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### 다이내믹 미디어 - YouTube Cloud Service 구성  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>이전 위치</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>새 위치</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>구조 조정 지침</strong></td> 
   <td><p>1. YouTube<br /> 2에서 모든 비디오를 게시 취소합니다. 이전 위치 <code>/conf</code><br /> 3에서 모든 채널 복사를 포함하여 새 TouchUI(보낸 사람)를 사용하여 YouTube 구성을 만듭니다. 모든 비디오를 YouTube에 다시 게시합니다.</p> <p>이 워크플로우는 새 YouTube URL을 만듭니다. 새로운 TouchUI YouTube 구성을 만들기 전에 게시 취소를 하지 않으면 재구성된 채널이 주어진 경우 다시 게시되므로 속성 아래에 여러 개의 YouTube URL이 나열됩니다. 즉, 속성 아래에 불필요한 URL이 나열됩니다.</p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### 기타 {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>이전 위치</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>새 위치</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>구조 조정 지침</strong></td> 
   <td><p>고객은 아래 마이그레이션 스크립트를 실행할 수 있습니다.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>또는 AEM UI에서 구성을 편집할 수 있으며 변경 사항이 새 위치에 저장됩니다.</p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>이전 위치</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>새 위치</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>구조 조정 지침</strong></td> 
   <td><p>고객은 아래 마이그레이션 스크립트를 실행할 수 있습니다.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

