---
title: 도구 콘솔
seo-title: 도구 콘솔
description: AEM 전체에서 다양한 도구 콘솔에 대해 알아봅니다.
seo-description: AEM 전체에서 다양한 도구 콘솔에 대해 알아봅니다.
uuid: d01382f8-0c8f-4d76-9271-bed9e34b3b4b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 2bf8496d-a485-4b39-a6c9-07222b66d0cd
translation-type: tm+mt
source-git-commit: e9c5fcd8f939d88317c5184b6352b227918088e5
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 36%

---


# 도구 콘솔{#tools-consoles}

**도구** 콘솔에서는 웹 사이트, 디지털 자산 및 콘텐츠 저장소의 다른 측면을 관리하는 데 도움이 되는 많은 전문 도구에 액세스할 수 있습니다. 현재 사용 중인 UI에 따라 **도구** 콘솔의 두 가지 버전이 있습니다.

* [도구 - 클래식 UI](#tools-classic-ui)
* [도구 - 터치에 적합한 UI](#tools-touch-optimized-ui)

## 도구 - 클래식 UI {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>페이지 또는 폴더</th> 
   <th> </th> 
   <th>목적</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM 제어 센터</a></td> 
   <td> </td> 
   <td>여러 사이트를 중앙에서 관리</td> 
  </tr> 
  <tr> 
   <td>클라이언트 컨텍스트 구성<br /> </td> 
   <td> </td> 
   <td><a href="/help/sites-developing/client-context.md">Client Context</a>은 사용자 데이터의 동적으로 어셈블된 컬렉션을 나타냅니다. 기본 및 Marketing Cloud 구성이 여기에 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>Cloud Services 구성<br /> </td> 
   <td> </td> 
   <td><a href="/help/sites-administering/marketing-cloud.md">Adobe Marketing Cloud</a>과(와) 관련된 구성을 보유합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">상거래</a></td> 
   <td> </td> 
   <td>가져오기 도구 및 다양한 제품 데이터에 액세스할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>디지털 권한 정보 및 라이선스에 대한 액세스 권한을 제공합니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - 상태 검사기<br /> </td> 
   <td> </td> 
   <td><code>/var/dam</code> 및 <code>/content/dam</code>을 비교하고<br />의 불일치를 확인합니다. 나열된 모든 파일/폴더를 동기화하거나 삭제할 수 있습니다. 폴더 비교를 위한 노드 유형은 웹 콘솔에서 구성할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - Adobe Indesign<br /> </td> 
   <td> </td> 
   <td>Adobe Indesign과 함께 사용할 스크립트입니다.</td> 
  </tr> 
  <tr> 
   <td>DAM - 비디오 프로필<br /> </td> 
   <td> </td> 
   <td>ffmpeg 트랜스코딩에 대한 구성 가능한 프로필.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">대시보드</a></td> 
   <td> </td> 
   <td>보고 대시보드를 만들 수 있습니다.이렇게 하면 통합 데이터를 표시하는 페이지를 정의하는 사용자 정의 가능한 방법을 제공합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">디자인</a></td> 
   <td> </td> 
   <td>사용할 그래픽 및 css 파일을 비롯하여 정의된 디자인 목록을 포함합니다.</td> 
  </tr> 
  <tr> 
   <td>맞춤형 설명서</td> 
   <td> </td> 
   <td>설명서 및 온라인 도움말을 확장할 때 사용됩니다.</td> 
  </tr> 
  <tr> 
   <td>양식 제출</td> 
   <td> </td> 
   <td>수신한 양식 목록을 보관합니다.</td> 
  </tr> 
  <tr> 
   <td>가져오기 프로그램 - <a href="/help/sites-administering/bulk-editor.md">벌크 편집기</a></td> 
   <td> </td> 
   <td>항목을 검색하고 일괄적으로 편집할 수 있습니다. 컨텐츠를 저장소에 일괄적으로 내보내고 가져올 수도 있습니다.</td> 
  </tr>
  <tr> 
   <td>Importer - Feed Importer</td> 
   <td> </td> 
   <td><p>Feed Importer는 외부 소스의 컨텐츠를 저장소로 반복적으로 가져오는 프레임워크입니다. Feed Importer의 아이디어는 원격 리소스를 지정된 간격으로 폴링하고, 구문 분석하고, 원격 리소스의 컨텐츠를 나타내는 노드를 컨텐츠 저장소에서 만드는 것입니다.</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">외부 링크 확인</a></td> 
   <td> </td> 
   <td>AEM 인스턴스 내의 모든 컨텐츠 페이지를 스캔하고 모든 외부 링크를 확인합니다. 유효하고 잘못된 링크 목록이 표시됩니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">모바일</a></td> 
   <td> </td> 
   <td>모바일 장치용으로 디자인된 웹 사이트를 만들 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>다국어 및 다국적 콘텐츠를 처리하여 중앙에서 브랜딩을 현지화된 콘텐츠와 균형을 맞출 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">알림</a></td> 
   <td> </td> 
   <td>알림 템플릿.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">패키지</a></td> 
   <td> </td> 
   <td>AEM WCM용으로 로드된 패키지를 표시하는 패키지 관리자의 대체 링크입니다. CRX의 패키지 관리자에 표시되는 정보와 유사합니다.</td> 
  </tr> 
  <tr> 
   <td>복제 - <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">복제 에이전트</a></td> 
   <td> </td> 
   <td>페이지를 게시할 때 작성자의 데이터를 게시로 복제하거나, 게시 환경에서 작성자에게 사용자 주석을 반환하는 역 복제와 함께 데이터를 복제하는 데 사용됩니다.</td> 
  </tr> 
  <tr> 
   <td>가져오기 프로그램 - <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">트리 활성화</a></td> 
   <td> </td> 
   <td>웹 사이트 탭에서 개별 페이지를 활성화할 수 있습니다. 동일한 루트 페이지 아래에서 수많은 컨텐츠 페이지를 입력하거나 업데이트한 경우 전체 트리를 한 번에 활성화하면 더욱 편리할 수 있습니다. 연습 실행을 통해 활성화를 에뮬레이션하여 활성화될 페이지를 강조할 수도 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">보고서</a></td> 
   <td> </td> 
   <td>AEM에서는 사용자 지정된 보고서 범위를 제공하며, 사용자 지정된 보고서를 만들거나 직접 개발할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">기본 페이지 스캐폴딩</a></td> 
   <td> </td> 
   <td>스캐폴딩을 사용하면 페이지에 적용할 구조를 반영하는 필드가 포함된 양식(스캐폴드)을 만든 후 이 양식을 이용하여 해당 구조를 갖는 페이지를 손쉽게 만들 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>보안 - <a href="/help/sites-administering/notification.md">셀프 서비스 구성 </a> </td> 
   <td> </td> 
   <td>사용자가 계정을 만들거나 암호를 재설정할 때 자동으로 받는 이메일을 구성하고 재설정된 암호를 확인할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">세그멘테이션</a></td> 
   <td> </td> 
   <td>사이트 방문자가 갖는 관심사와 목표는 매우 다양합니다. 이러한 목표를 이해하고 방문자의 기대를 충족할 수 있어야 온라인 마케팅의 성공이 보장됩니다. 세그먼테이션은 방문자의 세부 사항을 분석 및 특정하여 이를 실현하는 데 도움이 됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>기본 SRP 구성을 참조하십시오. <a href="/help/communities/srp-config.md">스토리지 구성</a> 콘솔을 참조하십시오.</td> 
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
   <td>작업 공간 마운트 기능을 사용하여 가상 리포지토리를 설정하여 CRX 및 JCR 커넥터를 기반으로 하는 JCR 컨텐츠 인프라에 간편하게 액세스할 수 있는 JCR 지원 컨텐츠 애플리케이션을 제공할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>감시자</td> 
   <td> </td> 
   <td>사용 중단됨. <a href="/help/communities/moderate-ugc.md#watchwords">커뮤니티 콘텐츠 중재 참조</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">워크플로우</a></td> 
   <td> </td> 
   <td>워크플로우는 모든 편집 프로세스를 지원하는 페이지 또는 디지털 자산에 대한 일련의 작업을 제어합니다.</td> 
  </tr> 
 </tbody> 
</table>

## 도구 - 터치에 적합한 UI {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>섹션</th> 
   <th>옵션</th> 
   <th>목적</th> 
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
   <td><a href="/help/sites-administering/workflows.md">워크플로우</a></td> 
   <td>워크플로우 모델링 및 관리.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">복제</a></td> 
   <td>여러 웹 사이트를 제작하고 관리할 수 있습니다.</td> 
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
   <td>오프로드를 관리합니다.</td> 
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
>위의 옵션 중 일부는 실제로 클래식 UI에 링크됩니다.

