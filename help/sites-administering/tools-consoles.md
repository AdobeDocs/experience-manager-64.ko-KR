---
title: 도구 콘솔
description: Adobe Experience Manager 전체에서 다양한 도구 콘솔에 대해 알아봅니다.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
exl-id: 7566e1bc-8571-4b3c-b420-4324026bd4dd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 20%

---

# 도구 콘솔{#tools-consoles}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

**도구** 콘솔에서는 웹 사이트, 디지털 자산 및 콘텐츠 저장소의 다른 측면을 관리하는 데 도움이 되는 많은 전문 도구에 액세스할 수 있습니다. 현재 두 가지 맛이 있습니다 **도구** 사용 중인 UI에 따라 콘솔:

* [도구 - 클래식 UI](#tools-classic-ui)
* [도구 - 터치에 적합한 UI](#tools-touch-optimized-ui)

## 도구 - 클래식 UI {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>페이지 또는 폴더</th> 
   <th> </th> 
   <th>용도</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM Control Center</a></td> 
   <td> </td> 
   <td>여러 사이트를 관리하기 위한 중앙 집중화된 지점</td> 
  </tr> 
  <tr> 
   <td>Client Context 구성<br /> </td> 
   <td> </td> 
   <td>다음 <a href="/help/sites-developing/client-context.md">Client Context</a> 사용자 데이터의 동적으로 어셈블된 컬렉션을 나타냅니다. 기본 및 marketing cloud 구성은 여기에서 설명합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>클라우드 서비스 구성<br /> </td> 
   <td> </td> 
   <td>관련 구성을 보유합니다. <a href="/help/sites-administering/marketing-cloud.md">Adobe Marketing Cloud과 통합</a>.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">상거래</a></td> 
   <td> </td> 
   <td>가져오기 및 다양한 제품 데이터에 액세스할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>디지털 권한 정보 및 라이센스에 대한 액세스 권한을 제공합니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - 상태 검사<br /> </td> 
   <td> </td> 
   <td>비교 <code>/var/dam</code> 및 <code>/content/dam</code> 및 는<br /> 일치하지 않습니다. 그러면 나열된 모든 파일/폴더를 동기화하거나 삭제할 수 있습니다. 폴더 비교를 위한 노드 유형은 웹 콘솔에서 구성할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - Adobe Indesign<br /> </td> 
   <td> </td> 
   <td>Adobe Indesign과 함께 사용할 스크립트입니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - 비디오 프로필<br /> </td> 
   <td> </td> 
   <td>ffmpeg 전송에 대해 구성 가능한 프로필.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">대시보드</a></td> 
   <td> </td> 
   <td>보고 대시보드를 만들 수 있습니다. 이렇게 하면 통합 데이터를 표시하는 페이지를 정의하는 사용자 지정 가능한 방법을 제공합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">디자인</a></td> 
   <td> </td> 
   <td>사용할 그래픽 및 css 파일을 포함하여 정의된 디자인 목록을 포함합니다.</td> 
  </tr> 
  <tr> 
   <td>사용자 지정 설명서</td> 
   <td> </td> 
   <td>설명서 및 온라인 도움말을 확장할 때 사용됩니다.</td> 
  </tr> 
  <tr> 
   <td>양식 제출</td> 
   <td> </td> 
   <td>받은 양식 제출 목록을 보관합니다.</td> 
  </tr> 
  <tr> 
   <td>가져오기 - <a href="/help/sites-administering/bulk-editor.md">대량 편집기</a></td> 
   <td> </td> 
   <td>항목을 검색하고 일괄적으로 편집할 수 있습니다. 컨텐츠를 저장소로 내보내고(일괄적으로) 가져올 수도 있습니다.</td> 
  </tr>
  <tr> 
   <td>가져오기 - 피드 가져오기</td> 
   <td> </td> 
   <td><p>Feed Importer는 외부 소스의 컨텐츠를 리포지토리로 반복적으로 가져오는 프레임워크입니다. Feed Importer의 아이디어는 지정된 간격으로 원격 리소스를 폴링하고, 구문 분석하고, 원격 리소스의 컨텐츠를 나타내는 컨텐츠 저장소에 노드를 만드는 것입니다.</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">외부 링크 확인</a></td> 
   <td> </td> 
   <td>AEM 인스턴스 내에서 모든 컨텐츠 페이지를 검색하고 외부 링크를 확인합니다. 유효한 링크와 잘못된 링크의 목록이 표시됩니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">모바일</a></td> 
   <td> </td> 
   <td>모바일 장치용으로 설계된 웹 사이트를 만드는 데 도움이 됩니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>다국어 및 다국적 컨텐츠를 처리하여 지역화된 콘텐츠와 중앙 브랜딩의 균형을 맞출 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">알림</a></td> 
   <td> </td> 
   <td>알림 템플릿.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">패키지</a></td> 
   <td> </td> 
   <td>AEM WCM용으로 로드된 패키지를 표시하는 패키지 관리자에 대한 대체 링크입니다. CRX의 패키지 관리자에 표시된 정보와 유사합니다.</td> 
  </tr> 
  <tr> 
   <td>복제 - <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">복제 에이전트</a></td> 
   <td> </td> 
   <td>페이지를 게시할 때 작성자에서 게시로 데이터를 복제하거나, 게시 환경에서 작성자에게 사용자 주석을 반환할 때 역방향 복제로 데이터를 복제하는 데 사용됩니다.</td> 
  </tr> 
  <tr> 
   <td>가져오기 - <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">트리 활성화</a></td> 
   <td> </td> 
   <td>웹 사이트 탭에서 개별 페이지를 활성화할 수 있습니다. 동일한 루트 페이지 아래에 있는 수많은 컨텐츠 페이지를 입력하거나 업데이트한 경우 전체 트리를 한 번에 활성화하면 더욱 편리할 수 있습니다. 연습 실행을 통해 활성화를 에뮬레이션하여 활성화될 페이지를 강조 표시할 수도 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">보고서</a></td> 
   <td> </td> 
   <td>AEM에서는 사용자 지정된 다양한 보고서를 제공하며, 사용자 지정된 보고서를 만들거나 직접 개발할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">기본 페이지 스캐폴딩</a></td> 
   <td> </td> 
   <td>스캐폴딩을 사용하면 페이지에 적용할 구조를 반영하는 필드가 포함된 양식(스캐폴드)을 만든 다음 이 양식을 사용하여 이 구조를 기반으로 페이지를 쉽게 만들 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>보안 - <a href="/help/sites-administering/notification.md">셀프 서비스 구성 </a> </td> 
   <td> </td> 
   <td>계정을 만들거나 암호를 재설정할 때 사용자가 자동으로 받는 이메일을 구성하고, 재설정된 암호를 확인할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">세분화</a></td> 
   <td> </td> 
   <td>사이트 방문자가 사이트를 방문할 때는 서로 다른 관심사와 목표를 갖습니다. 이러한 목표를 이해하고 기대를 충족시키는 것은 온라인 마케팅의 중요한 성공 요소입니다. 세그멘테이션은 방문자의 세부 사항을 분석하고 특성을 지정하여 이를 달성하는 데 도움이 됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>기본 SRP 구성입니다. 자세한 내용은 <a href="/help/communities/srp-config.md">스토리지 구성</a> 콘솔.</td> 
  </tr> 
  <tr> 
   <td>작업 관리</td> 
   <td> </td> 
   <td>이 항목과 관련된 활성 기능이 없습니다.</td> 
  </tr> 
  <tr> 
   <td>세입자</td> 
   <td> </td> 
   <td>이 항목과 관련된 활성 기능이 없습니다.</td> 
  </tr> 
  <tr> 
   <td>버전 관리 - <a href="/help/sites-deploying/version-purging.md">버전 삭제</a></td> 
   <td> </td> 
   <td>필요에 따라 페이지 버전을 삭제할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>가상 저장소</td> 
   <td> </td> 
   <td>작업 공간 마운트 기능을 사용하여 가상 리포지토리를 설정하여 JCR 지원 컨텐츠 응용 프로그램에 CRX 및 JCR 커넥터를 기반으로 하는 JCR 컨텐츠 인프라에 대한 간단한 액세스를 제공할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>어워치</td> 
   <td> </td> 
   <td>더 이상 사용되지 않음. 자세한 내용은 <a href="/help/communities/moderate-ugc.md#watchwords">커뮤니티 콘텐츠 중재</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">워크플로</a></td> 
   <td> </td> 
   <td>워크플로우는 편집 프로세스를 지원하는 페이지 또는 디지털 자산에 대한 일련의 작업을 제어합니다.</td> 
  </tr> 
 </tbody> 
</table>

## 도구 - 터치에 적합한 UI {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>섹션</th> 
   <th>옵션</th> 
   <th>용도</th> 
  </tr> 
  <tr> 
   <td>작성</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-classic-ui-authoring/classic-personalization-campaigns.md">캠페인</a></td> 
   <td>마케팅 캠페인을 관리합니다.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/launches.md">론치</a></td> 
   <td>마케팅 시작 관리</td> 
  </tr> 
  <tr> 
   <td>작업</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/task-content.md">받은 편지함</a></td> 
   <td>받은 편지함 항목을 관리합니다.</td> 
  </tr> 
  <tr> 
   <td>작업</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/security.md">사용자 및 그룹</a></td> 
   <td>사용자 및 그룹을 관리합니다.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/tags.md">태그 관리</a></td> 
   <td>태그와 해당 네임스페이스를 구성합니다.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">클라우드 서비스</a></td> 
   <td>Adobe Marketing Cloud에 연결.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/workflows.md">워크플로</a></td> 
   <td>워크플로우 모델링 및 관리.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">복제</a></td> 
   <td>여러 웹 사이트를 만들고 관리합니다.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/reporting.md">보고서</a></td> 
   <td>사용자 정의 보고서 작성 및 모니터링.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/hobbes.md">테스트</a></td> 
   <td>응용 프로그램에 대해 정의된 테스트 실행.</td> 
  </tr> 
  <tr> 
   <td>Granite 작업</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE Lite</a></td> 
   <td>웹 기반 IDE로 애플리케이션 개발.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md">패키지</a></td> 
   <td>애플리케이션 패키지 및 공유.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md#package-share">패키지 공유</a></td> 
   <td>Adobe와 커뮤니티에서 애플리케이션 다운로드.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md#administering-topologies">토폴로지 브라우저</a></td> 
   <td>인스턴스 토폴로지 보기.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md">오프로드 브라우저</a></td> 
   <td>오프로딩을 관리합니다.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#backups">백업</a></td> 
   <td>백업 작업 수행.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>웹 콘솔<br /> </td> 
   <td>애플리케이션 플랫폼 구성 및 관리.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>웹 콘솔 구성 덤프<br /> </td> 
   <td>웹 콘솔에서 구성 상태를 다운로드합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>사용자</td> 
   <td>사용자 관리.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>그룹</td> 
   <td>그룹 관리.</td> 
  </tr> 
  <tr> 
   <td>외부 리소스<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>설명서</td> 
   <td>웹 경험 관리 설명서 보기.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>개발자 리소스</td> 
   <td>개발자 리소스 및 다운로드.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>위의 옵션 중 일부는 실제로 클래식 UI에 연결됩니다.
