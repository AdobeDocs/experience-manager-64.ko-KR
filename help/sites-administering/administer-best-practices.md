---
title: 모범 사례
description: 관리자가 시작하고 실행할 수 있도록 Adobe 엔지니어링 및 컨설팅 팀이 컴파일한 Adobe Experience Manager 우수 사례에 대해 알아보십시오.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
exl-id: 8c41dba4-bedc-4747-b67d-fd89d71c8b2c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 13%

---

# 모범 사례{#best-practices}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

우수 사례에서는 가장 효율적이고 효과적인 방법으로 AEM을 개발, 관리 또는 사용하는 방법을 설명합니다. 이러한 증가하고 있는 주제 목록에는 AEM의 다양한 영역이 포함되어 있습니다.

다음 영역에는 우수 사례에 대해 사용 가능한 설명서가 있습니다.

* [Assets](#assets)
* [Sites](#sites)

작성, 배포, 유지 관리 또는 개발에 대한 우수 사례가 필요하면 다음 중 하나를 참조하십시오.

* [작성 우수 사례](/help/sites-authoring/best-practices.md)
* [개발 우수 사례](/help/sites-developing/best-practices.md)
* [배포 우수 사례](/help/sites-deploying/best-practices.md)

특정 문서는 다음에 나오는 표에 설명되고 연결됩니다.

## Assets {#assets}

Dynamic Media 기능 및 Dynamic Media Classic 통합을 포함한 Assets에 대한 우수 사례는 다음 항목에 설명되어 있습니다.

<table> 
 <tbody>
  <tr>
   <td>로드 중인 시스템 안정성 및 성능을 향상시키기 위해 자산 주변 여러 영역에서 우수 사례를 제공합니다</td> 
   <td><a href="/help/assets/organize-assets.md">에셋에 대한 우수 사례</a></td> 
   <td>자산 주위의 다양한 영역에서 모범 사례 안내서에 대한 링크를 포함합니다. 검토하면 엔터프라이즈 자산 관리 시스템을 구축하고 관리하는 지식과 도구가 제공됩니다.</td> 
  </tr>
  <tr>
   <td>컨텐츠(폴더 계층 구조)를 구성하는 방법</td> 
   <td><a href="/help/assets/organize-assets.md">파일 관리 우수 사례</a></td> 
   <td>처리 프로필의 대부분은 비디오, 메타데이터, 이미지 처리가 항상 폴더에 적용되므로 폴더 기반입니다. 이 우수 사례 문서에서는 계층 구조가 컨텐츠 처리 방식에 큰 영향을 주므로 폴더 계층 구조를 정의하고 설정하는 방법을 설명합니다. </td> 
  </tr>
  <tr>
   <td>Dynamic Media Classic 및 AEM 통합</td> 
   <td><a href="/help/sites-administering/scene7.md#best-practices-for-integrating-scene-with-aem">Dynamic Media Classic과 AEM 통합을 위한 우수 사례</a></td> 
   <td><p>폴링 가져오기를 켜는 시기, 통합을 테스트하는 방법, 컨텐츠 브라우저를 사용하는 시점 및 자산을 직접 업로드하는 방법에 대해 설명합니다.</p> </td> 
  </tr>
  <tr>
   <td>이미지 사전 설정 옵션</td> 
   <td>이해 <a href="/help/assets/managing-image-presets.md#understanding-image-presets">이미지 사전 설정</a> 및 <a href="/help/assets/managing-image-presets.md#image-preset-options">이미지 사전 설정 우수 사례</a></td> 
   <td>에 대한 설명서의 일부로 <a href="/help/assets/managing-image-presets.md">이미지 사전 설정 관리</a>, 이 항목에서는 이미지 사전 설정 및 이미지 사전 설정 옵션 선택에 대한 우수 사례를 설명합니다.</td> 
  </tr>
  <tr>
   <td>Dynamic Media과 Dynamic Media Classic과의 직접 통합 비교</td> 
   <td><a href="/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media">Dynamic Media Classic/AEM 통합과 Dynamic Media</a></td> 
   <td>Dynamic Media 솔루션을 사용하는 것, S7을 AEM과 통합할 때 또는 두 솔루션을 모두 사용해야 하는 경우에 대해 설명합니다.</td> 
  </tr>
 </tbody>
</table>

## Sites {#sites}

웹 사이트 컨텐츠 관리 및 작성에는 다음과 같이 요약된 몇 가지 우수 사례가 있습니다.

<table> 
 <tbody>
  <tr>
   <td>GDPR 준수</td> 
   <td><a href="/help/sites-administering/gdpr-compliance-sites.md">AEM Sites GDPR 준수</a></td> 
   <td>데이터 사생활 보호권에 관한 유럽 연합의 GDPR(일반 데이터 보호 규정)은 2018년 5월에 발효됩니다. AEM Sites은 GDPR을 준수합니다. 이 페이지에서는 고객에게 AEM Sites에서 GDPR 요청을 처리하는 절차를 안내합니다. 저장된 개인 데이터의 위치와 수동으로 또는 코드로 해당 데이터를 제거하는 방법에 대해서도 설명합니다.</td> 
  </tr>
  <tr>
   <td>인스턴스에 대한 기본 UI를 정의합니다.</td> 
   <td><p><a href="/help/sites-authoring/select-ui.md#configuring-the-default-ui-for-your-instance">인스턴스에 대한 기본 UI 구성</a></p> </td> 
   <td>AEM에는 두 개의 UI가 있습니다. 터치 최적화 및 클래식. 이 섹션에서는 인스턴스에 대한 기본 UI를 정의하는 방법에 대해 자세히 설명합니다.</td> 
  </tr>
  <tr>
   <td>다중 사이트 관리</td> 
   <td><a href="/help/sites-administering/msm-best-practices.md">MSM 모범 사례</a></td> 
   <td>MSM을 사용하여 콘텐츠 배포를 자동화하는 우수 사례입니다. </td> 
  </tr>
  <tr>
   <td>컨텐츠 번역</td> 
   <td><a href="/help/sites-administering/tc-bp.md">번역 모범 사례</a></td> 
   <td>다국어 사이트 계획 및 구현에 대한 우수 사례</td> 
  </tr>
  <tr>
   <td>사용자 관리</td> 
   <td><a href="/help/sites-administering/security.md#best-practices">권한 및 권한 우수 사례</a></td> 
   <td>권한 및 권한 사용 시 모범 사례에 대해 설명합니다 </td> 
  </tr>
  <tr>
   <td>워크플로</td> 
   <td><a href="/help/sites-developing/workflows-best-practices.md#configuration">워크플로우 우수 사례 - 구성</a></td> 
   <td>워크플로우에서는 AEM(Adobe Experience Manager) 활동을 자동화할 수 있고, AEM 환경에서 발생하는 많은 처리를 나타낼 수 있으므로 워크플로우 구현을 신중하게 계획 및 구성하는 것이 좋습니다.</td> 
  </tr>
 </tbody>
</table>
