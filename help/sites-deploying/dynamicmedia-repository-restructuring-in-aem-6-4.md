---
title: AEM 6.4의 Dynamic Media 저장소 구조 변경
seo-title: AEM 6.4의 Dynamic Media 저장소 구조 변경
description: AEM 6.4 for Dynamic Media의 새 저장소 구조로 마이그레이션하기 위해 필요한 변경 작업을 수행하는 방법을 알아봅니다.
seo-description: AEM 6.4 for Dynamic Media의 새 저장소 구조로 마이그레이션하기 위해 필요한 변경 작업을 수행하는 방법을 알아봅니다.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: 업그레이드
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 4%

---

# AEM 6.4의 Dynamic Media 저장소 구조 변경{#dynamic-media-repository-restructuring-in-aem}

AEM 6.4에서 상위 [저장소 구조 변경 페이지에 설명된 대로 AEM 6.4로 업그레이드하는 고객은 이 페이지에서 Dynamic Media 솔루션에 영향을 주는 저장소 변경 사항과 관련된 작업 작업을 평가해야 합니다. ](/help/sites-deploying/repository-restructuring.md) 일부 변경 사항은 AEM 6.4 업그레이드 프로세스 중에 작업 노력이 필요한 반면, 다른 변경 사항은 6.5 업그레이드 전까지 지연될 수 있습니다.

**6.5 이전 업그레이드**

* [사용자 지정 응용 비디오 인코딩 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Dynamic Media (DMS7) 클라우드 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Dynamic Media(DM 하이브리드) Cloud Service 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - YouTube Cloud Service 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Misc](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## 6.5 이전 업그레이드 {#prior-to-upgrade}

### 사용자 지정 응용 비디오 인코딩 구성 {#custom-adaptive-video-encoding-configurations}

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

### Dynamic Media (DMS7) 클라우드 구성 {#dynamic-media-dms-cloud-configuration}

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
   <td><p>고객은 이 위치에서 마이그레이션 스크립트를 실행할 수 있습니다.<br /> </p> 
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

### Dynamic Media(DM 하이브리드) Cloud Service 구성 {#cloudserviceconfiguration}

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
   <td><p>최신 모델에 맞게 아래 마이그레이션 스크립트를 실행할 수 있습니다.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media - YouTube Cloud Service 구성  {#youtubecloudserviceconfiguration}

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
   <td><p>1. YouTube<br /> 2에서 모든 비디오를 게시 취소합니다. 이전 위치<br /> 3에서 모든 채널 복사를 포함하여 새 TouchUI(<code>/conf</code>에서)를 사용하여 YouTube 구성을 만듭니다. 모든 비디오를 다시 YouTube에 게시합니다.</p> <p>이 워크플로우는 새 YouTube URL을 생성합니다. 새 TouchUI YouTube 구성을 만들기 전에 게시 취소를 하지 않는 경우 기회가 주어지면 다시 생성된 채널이 다시 게시되므로 속성 아래에 여러 YouTube URL이 표시됩니다. 즉, 속성 아래에 불필요한 URL이 표시됩니다.</p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Misc {#misc}

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
   <td>해당 없음</td> 
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
   <td>해당 없음</td> 
  </tr>
 </tbody>
</table>
