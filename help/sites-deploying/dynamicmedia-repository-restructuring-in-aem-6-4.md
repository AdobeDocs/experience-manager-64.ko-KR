---
title: AEM 6.4의 Dynamic Media 저장소 구조 변경
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: AEM 6.4 for Dynamic Media의 새 저장소 구조로 마이그레이션하기 위해 필요한 변경 작업을 수행하는 방법을 알아봅니다.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 5%

---

# AEM 6.4의 Dynamic Media 저장소 구조 변경{#dynamic-media-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

상위에 설명된 대로 [AEM 6.4의 저장소 구조 변경](/help/sites-deploying/repository-restructuring.md) 페이지에서 AEM 6.4로 업그레이드하는 고객은 이 페이지에서 Dynamic Media 솔루션에 영향을 주는 저장소 변경 사항과 관련된 작업 작업을 평가해야 합니다. 일부 변경 사항은 AEM 6.4 업그레이드 프로세스 중에 작업 노력이 필요한 반면, 다른 변경 사항은 6.5 업그레이드 전까지 지연될 수 있습니다.

**6.5 이전 업그레이드**

* [사용자 지정 응용 비디오 인코딩 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Dynamic Media (DMS7) 클라우드 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Dynamic Media(DM 하이브리드) Cloud Service 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - YouTube Cloud Service 구성](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Misc](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## 6.5 이전 업그레이드 {#prior-to-upgrade}

### 사용자 지정 응용 비디오 인코딩 구성  {#custom-adaptive-video-encoding-configurations}

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
   <td>해당 없음<br /> </td> 
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
   <td>해당 없음<br /> </td> 
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
   <td><p>1. YouTube에서 모든 비디오 게시 취소<br /> 2. 새 TouchUI( <code>/conf</code>)을 클릭하여 이전 위치에서 모든 채널을 복사합니다<br /> 3. 모든 비디오를 다시 YouTube에 게시합니다.</p> <p>이 워크플로우는 새 YouTube URL을 생성합니다. 새 TouchUI YouTube 구성을 만들기 전에 게시 취소를 하지 않는 경우 기회가 주어지면 다시 생성된 채널이 다시 게시되므로 속성 아래에 여러 YouTube URL이 표시됩니다. 즉, 속성 아래에 불필요한 URL이 표시됩니다.</p> </td> 
  </tr>
  <tr>
   <td><strong>메모</strong></td> 
   <td>해당 없음<br /> </td> 
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
