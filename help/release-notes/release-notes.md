---
title: Adobe Experience Manager 6.4의 일반적인 릴리스 노트
seo-title: 릴리스 노트
description: 'Adobe Experience Manager 6.4 참고는 릴리스 정보, 새로운 기능, 설치 방법 및 상세 변경 목록을 간략하게 설명합니다. '
seo-description: 'Adobe Experience Manager 6.4 참고는 릴리스 정보, 새로운 기능, 설치 방법 및 상세 변경 목록을 간략하게 설명합니다. '
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
exl-id: ee034595-2d2a-4887-86c4-6bf0770da6a2
source-git-commit: eb55489da5e390578b2ae71be424930e9bf3efd3
workflow-type: tm+mt
source-wordcount: '2813'
ht-degree: 32%

---

# Adobe Experience Manager 6.4의 일반적인 릴리스 노트 {#general-release-notes-for-adobe-experience-manager}

## 릴리스 정보 {#release-information}

| 제품 | Adobe Experience Manager |
|---|---|
| 버전 | 6.4 |
| 유형 | 주요 릴리스 |
| 일반 공급 일자 | 2018년 4월 4일 |
| 권장 업데이트 | [AEM 릴리스 및 업데이트](https://helpx.adobe.com/kr/experience-manager/aem-releases-updates.html)를 참조하십시오 |

### 일반 {#trivia}

이 버전의 Adobe Experience Manager에 대한 릴리스 주기는 2017년 4월 27일부터 시작되었으며, 22회의 품질 보증 및 버그 수정을 거쳐 2018년 3월 22일에 종료되었습니다. 이 릴리스의 개선 사항과 새로운 기능 수정을 포함한 문제에 관련된 총 고객 수는 704명입니다.

Adobe Experience Manager 6.4는 일반적으로 2018년 4월 4일 이후에 사용할 수 있습니다.

>[!NOTE]
>
>모든 새 기능 팩은 [서비스 팩](https://helpx.adobe.com/kr/experience-manager/maintenance-releases-roadmap.html)을 통해서만 제공되므로 Adobe은 최신 서비스 팩을 설치할 것을 권장합니다.

## 새로운 기능 {#what-s-new}

Adobe Experience Manager 6.4는 Adobe Web Experience Manager 6.3 코드 베이스에 대한 업그레이드 릴리스입니다. 새롭고 향상된 기능, 주요 고객 수정 사항, 우선 순위가 높은 고객 개선 사항 및 제품 안정화를 위한 일반적인 버그 수정을 제공합니다. 여기에는 모든 Adobe Experience Manager 6.3 기능 팩, 핫픽스 및 서비스 팩 릴리스의 대부분을 포함합니다.

아래 목록은 개요를 제공하며, 후속 페이지에서 전체 세부 정보를 확인할 수 있습니다.

### Experience Manager Foundation {#experience-manager-foundation}

[AEM Foundation](wcm-platform.md)의 전체 변경 목록입니다.

Adobe Experience Manager 6.4의 플랫폼은 OSGi 기반 프레임워크(Apache Sling 및 Apache Felix)의 업데이트된 버전과 Java 컨텐츠 리포지토리인 Apache Jackrabbit Oak 1.8.2에 구축됩니다.

빠른 시작은 Eclipse Jetty 9.3.22를 서블릿 엔진으로 사용합니다.

#### 사용자 인터페이스 {#user-interface}

UI의 생산성과 사용 편의성을 향상시키기 위해 UI에 다양한 개선 사항이 적용되었습니다.

* [새 컨텐츠 트리 ](/help/sites-authoring/basic-handling.md#content-tree) 레일 을 사용하여 계층 구조를 빠르게 탐색할 수 있습니다. 목록 보기와 함께 클래식 UI 상호 작용 모델이 복원됩니다.
* 큰 폴더의 카드 및 목록 보기에서 스크롤 경험이 개선되었습니다.
* [검색 결과와의 상호 작용 개선](/help/sites-authoring/search.md)  - 뒤로 단추가 이전 검색 결과를 복원합니다.
* [추가 키보드 단축키](/help/sites-authoring/keyboard-shortcuts.md) - 특정 레일 열기, 항목 편집, 이동 및 삭제 또는 속성 열기 등 대부분의 일반적인 작업.
* [키보드 단축키를 비활성화](/help/sites-authoring/user-properties.md) (환경 설정에서 활성화/비활성화)하는 기능.
* [7일 후 모든 ](/help/sites-authoring/user-properties.md) UI에 대해 상대적 타임스탬프 표시를 중지합니다(기본 설정에서 기본값 설정).

이러한 기능에 대한 자세한 내용은 [작성 설명서](/help/sites-authoring/home.md)를 참조하십시오.

>[!CAUTION]
>
>Adobe는 향후 클래식 UI를 개선할 계획이 없습니다. AEM 6.4에는 클래식 UI가 포함되어 있으며 이전 릴리스에서 업그레이드하는 고객은 있는 그대로 사용할 수 있습니다. 클래식 UI가 더 이상 사용되지 않는 동안에도 계속 지원됩니다. [자세히 보기](/help/sites-deploying/ui-recommendations.md)

#### 컨텐츠 리포지토리 {#content-repository}

* 온라인 개정 정리를 통한 보다 빠르고 효율적인 압축. 내부 테스트에서는 새로운 테일 압축 기능이 AEM 6.3에 비해 최대 10배 더 빠르며 더 적은 IOPS로 더 많은 디스크 공간을 확보할 수 있음을 보여줍니다. 따라서 온라인 개정 정리 실행 중에 성능이 저하됩니다. 자세한 내용은 설명서 페이지](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes)를 참조하십시오.[

* MongoMK의 연속 개정 정리 는 예약된 정리 유지 관리를 대체합니다
* 문서 노드에 대한 개정 정리 효율성 향상

#### 검색 및 색인 생성 {#search-indexing}

* oak-run(CLI)을 통한 색인 지정 작업에 대한 지원이 향상되었습니다.

   * 인덱스 일관성 검사
   * 인덱싱 통계
   * 인덱스 구성 가져오기 또는 내보내기
   * 재인덱싱

* 전체 시스템 성능을 향상시키기 위해 Lucene 관련 저장소 증가 감소

자세한 내용은 [이 설명서 페이지](/help/sites-deploying/indexing-via-the-oak-run-jar.md)를 참조하십시오.

#### 모니터링 {#monitoring}

* 새 [시스템 개요](/help/sites-administering/operations-dashboard.md#system-overview)는 모든 성능 관련 시스템 상태 및 활동에 대한 스냅샷 보기를 제공합니다.
* 색인 지정, 쿼리 및 유지 관리에 대한 [상태 검사](/help/sites-administering/operations-dashboard.md#health-checks) 새 세트

#### 프로젝트 및 워크플로우 {#projects-and-workflows}

* 워크플로우 모델을 만들고 편집할 수 있는 완전히 새로운 [워크플로우 편집기](/help/sites-developing/workflows-models.md).

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### 이전 버전 {#upgrade-from-earlier-version}에서 업그레이드

* [이전 버전과의 호환성](/help/sites-deploying/backward-compatibility.md):6.4의 이전 버전과 호환되는 기능에서는 대부분의 경우 사용자 지정 코드가 호환되며, 업그레이드 노력을 줄일 수 있습니다.
* [업그레이드 복잡성 평가](/help/sites-deploying/pattern-detector.md):업그레이드하기 전에 업그레이드의 복잡성을 평가하는 새 패턴 탐지기 도구입니다.
* [저장소 구조 변경](/help/sites-deploying/repository-restructuring.md):업그레이드를 용이하게 하고 구현 모범 사례를 홍보하기 위한 중요한 재구성(주로 /etc)
* 업그레이드에 대한 자세한 내용은 [이 페이지](/help/sites-deploying/upgrade.md)를 참조하십시오.

### Experience Manager Sites {#experience-manager-sites}

[AEM Sites 및 추가 기능](sites.md)의 전체 변경 목록입니다.

#### Fluid Experiences {#fluid-experiences}

컨텐츠 조각, 경험 조각 및 컨텐츠 서비스가 지원하는 2017년 초에 Fluid Experiences의 도입은 멀티채널 최초 컨텐츠 관리로 진화를 기하기 시작했습니다. AEM 6.4는 각 영역을 크게 확장합니다.

**[컨텐츠 조각](/help/assets/content-fragments.md)**

6.4의 새로운 기능은 시각적 [컨텐츠 모델](/help/assets/content-fragments-models.md) 편집기와, 컨텐츠 서비스에 포함할 유연한 HTML 출력 및 JSON을 제공하기 위한 새로운 [구성 가능한 구성 요소](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/components/content-fragment-component.html)입니다.

**경험 조각**

동일한 컨텐츠지만 다른 레이아웃으로 조각의 변형을 만드는 것이 이제 빌딩 블록 기능 덕분에 더 효율적입니다. facebook 및 Pinterest에 경험 구성요소를 전송하는 것 외에도, 이제 오퍼로 Adobe Target으로 컨텐츠를 보낼 수 있습니다.

**컨텐츠 서비스**

Sling 모델 익스포터 및 핵심 구성 요소에 대한 다양한 개선 사항이 포함되며, 강력한 JSON 출력을 제공하여 단일 페이지 앱을 사용하여 모바일 앱 및 경험에 콘텐츠를 포함할 수 있습니다.

#### 더 빠르게 사이트 빌드 {#gettings-sites-built-quicker}

AEM 6.4는 차세대 구성 요소 모델로 변환을 완료합니다. AEM 6.3에서 도입되었으며 이제 스타일 시스템으로 결합되어 있는 코어 구성 요소 개념은 새 사이트를 작성하고 기존 사이트를 확장하는 효율적인 방법을 제공합니다.

새 구성 요소 모델을 가장 잘 활용하는 방법을 배우려면 권장되는 자습서입니다.[AEM Sites 시작하기 - WKND 자습서](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

#### 화면 추가 기능 {#screens-add-on}

AEM Screens은 디지털 간판 및 키오스크 네트워크를 포함한 모든 마케팅 채널에서 일관된 메시지를 전달하는 것을 의미합니다. AEM 6.4는 Microsoft Windows 및 Google Chrome OS 하드웨어에서 Signage Player를 실행할 수 있는 지원을 추가합니다. 또한 원격 장치 관리 및 예약(채널 그룹)에 대한 개선 사항을 사용할 수 있습니다.

스크린 업데이트에 대한 자세한 내용은 [AEM Screens 사용 안내서](https://docs.adobe.com/content/help/ko-KR/experience-manager-screens/user-guide/aem-screens-introduction.html)를 참조하십시오.

### Experience Manager Communities {#experience-manager-communities}

AEM 6.4는 커뮤니티에 많은 새로운 기능과 개선 사항을 추가합니다. 전체 변경 목록은 [AEM Communities](communities-release-notes.md)에서 사용할 수 있습니다. 이 릴리스의 주요 기능은 다음과 같습니다.

#### 중재 개선 사항 {#enhancements-to-moderation}

**자동 스팸 감지**

커뮤니티 사이트 및 그룹에서 원치 않는 사용자가 생성한 컨텐츠를 필터링하는 새로운 스팸 탐지 엔진이 제공되었습니다. system/console/configMgr에서 활성화되면 미리 정의된 스팸 단어 세트를 기반으로 사용자 생성 컨텐츠를 스팸으로 표시합니다. 스팸 감지 엔진에 대한 자세한 내용은 [콘텐츠를 생성하는 커뮤니티 사용자 자동화](/help/communities/moderate-ugc.md#spam-detection)를 참조하십시오.

![spamdetection](assets/spamdetection.png)

**QnA에 대한 새 필터**

답변됨 및 답변되지 않음 이라는 새 필터가 QnA 질문을 필터링하기 위해 대량 조정 콘솔에 추가되었습니다. 응답됨 및 응답하지 않는 상태 필터가 작동하는 방식을 알아보려면 [사용자가 생성한 콘텐츠를 대량으로 중재하십시오](/help/communities/moderation.md#main-pars-note-521961797).

**북마크 중재 필터**

중재 콘솔에 사전 정의된 중재 필터에 책갈피를 지정하는 기능이 제공되었습니다. 이러한 필터는 URL 문자열의 끝 부분에 추가되므로 나중에 공유, 재사용 및 다시 방문할 수 있습니다. [벌크 중재 콘솔](/help/communities/moderation.md#main-pars-note-429176623)에 필터를 책갈피로 지정하는 방법을 알아봅니다.

#### UGC 및 사용자 프로필 삭제 {#delete-ugc-and-user-profiles}

AEM 6.4 Communities는 최종 사용자가 데이터를 제어할 수 있도록 [기본 제공 API](/help/communities/user-ugc-management-service.md) 및 샘플 [servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet)을 표시합니다. 또한 이러한 API를 사용하면 데이터 처리 및 데이터 제어 조직이 EU GDPR 준수 요청을 제공할 수 있습니다.

#### 사이트 및 그룹 관리에 대한 개선 사항 {#enhancements-to-site-and-group-management}

**단일 단계로 다중 로케일 그룹 만들기**

단일 작업으로 다국어 그룹을 생성하는 기능이 제공되었습니다. 이러한 그룹을 만들려면 사이트 콘솔에서 원하는 커뮤니티 사이트의 그룹 컬렉션으로 이동할 수 있습니다. 그룹을 만들고 커뮤니티 그룹 템플릿 페이지에서 원하는 언어를 지정합니다. 이 기능에 대한 자세한 내용은 [커뮤니티 그룹 콘솔](/help/communities/groups.md)을 참조하십시오.

![다중 언어 그룹](assets/multilingualgroup.png)

**[클릭 시 커뮤니티 사이트 및 그룹 삭제](/help/communities/groups.md)**

이제 전역 탐색에서 탐색하는 동안 각 사이트 및 그룹에서 삭제 아이콘을 사용할 수 있습니다. 이 아이콘을 사용하면 사이트나 그룹과 연관된 모든 항목과 컨텐츠가 삭제되고 모든 사용자 연결이 제거됩니다. 이 기능에 대한 자세한 내용은 [커뮤니티 사이트 관리](/help/communities/create-site.md#main-pars-text-fe17) 및 [커뮤니티 그룹 관리](/help/communities/groups.md#main-pars-text-5e8c)를 참조하십시오.

#### 지원 {#enhancements-to-enablement} 개선 사항

이제 그룹 내에서 할당 및 카탈로그 기능을 사용할 수 있습니다. 이를 통해 특정 타깃팅된 커뮤니티 구성원에 대해 학습 컨텐츠를 생성, 관리 및 게시할 수 있습니다. 커뮤니티 그룹 활성화에 대한 자세한 내용은 [지원 리소스 관리](/help/communities/resource.md)를 참조하십시오.

![할당 카탈로그](assets/assignmentcatalog.png)

### Experience Manager 자산 {#experience-manager-assets}

AEM 6.4는 향상된 새 Creative Cloud 통합, 주요 인공 지능(AI) 혁신, 향상된 메타데이터 관리, 보고 개선 사항 및 전반적인 사용자 환경 개선 사항을 포함한 여러 가지 새로운 기능과 개선 사항을 제공합니다. [AEM Assets](assets.md)에서 사용할 수 있는 변경 사항의 전체 목록입니다. 릴리스의 주요 기능은 다음과 같습니다.

**Adobe Asset Link**

기업 Creative Cloud의 Adobe 자산 링크를 사용하면 컨텐츠 작성 프로세스에서 광고 팀과 마케터 간의 협업을 간소화할 수 있습니다. Photoshop CC, Illustrator CC 및 InDesign CC를 AEM에 연결하는 기업용 Creative Cloud의 새로운 기본 기능으로, 크리에이티브를 사용하지 않고도 원하는 도구를 사용할 수 있습니다.

이 기능, 사전 요구 사항 및 액세스 방법에 대한 자세한 내용은 [자산 링크 Adobe](https://www.adobe.com/kr/creativecloud/business/enterprise/adobe-asset-link.html)를 참조하십시오.

![adobe_asset_link](assets/adobe_asset_link.png)

**AEM Desktop App**

AEM 데스크탑 앱이 AEM 6.4와 호환되는 버전 1.8로 업데이트되었습니다. AEM 데스크탑 앱에 대한 전체 변경 사항 목록은 전용 [AEM 데스크탑 앱 릴리스 노트](https://docs.adobe.com/content/help/ko-KR/experience-manager-desktop-app/using/release-notes.html) 문서에 제공됩니다.

AEM 6.3 릴리스부터 향상된 기능에는 배경에서 계층 폴더를 업로드하는 기능, 자산 백그라운드 작업을 모니터링하는 새 UI, 향상된 캐싱, 네트워킹 및 로그인, 전반적인 안정성 개선 사항이 포함됩니다. 설명서에는 [우수 사례 가이드](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)도 포함되어 있습니다.

**Adobe Sensei 서비스**

새로운 기능에는 고객 비즈니스 분류법을 학습하고, 고객별 태그와 Smart Translation Search를 통해 디지털 자산에 자동으로 태그를 지정하고, 검색어를 즉시 번역하여 여러 언어로 검색 기능을 향상시키는 향상된 스마트 태그가 포함되어 있습니다. 이 기능에 대한 자세한 내용은 [고급 스마트 태그](/help/assets/enhanced-smart-tags.md)를 참조하십시오.

![enhanced_smart_tags2](assets/enhanced_smart_tags2.png)

**메타데이터**

다양한 개선 사항에는 [계단식 메타데이터](/help/assets/cascading-metadata.md)와 같은 많은 자산과 고급 메타데이터 구문에 대해 메타데이터를 동시에 가져오고 내보내는 기능이 포함됩니다.

**보고서**

자산 보고는 고객 사용 사례를 위한 새로운 보고 프레임워크, 사용자 경험 및 더 많은 OOTB 보고로 AEM 6.4의 대규모 점검을 거쳤습니다. 다양한 보고서를 생성하는 방법에 대해 알려면 [자산 보고서](/help/assets/asset-reports.md)를 참조하십시오.

**사용자 경험**

스크롤 경험, 검색 뒤로 단추, 향상된 검색 필터 등과 같은 Assets 사용자의 검색, 검색 및 관리 경험을 개선하기 위해 여러 개선 사항이 있습니다. [AEM Assets](assets.md)에서 사용할 수 있는 전체 목록입니다.

**Brand Portal**

메타데이터, 보고, 디지털 권한, 로그인 경험 및 자산 배포를 위한 게시 성능 영역의 다양한 개선 사항. 새로운 개선 사항 및 기능에 대해 알아보려면 [AEM Assets Brand Portal의 새로운 기능](https://docs.adobe.com/content/help/ko-KR/experience-manager-brand-portal/using/introduction/whats-new.html)을 참조하십시오.

#### Dynamic Media 추가 기능 {#dynamic-media-add-on}

AEM 6.4에는 Dynamic Media에 대한 많은 새로운 기능과 개선 사항이 포함되어 있습니다. 전체 목록은 [AEM Assets](assets.md)에서 사용할 수 있습니다. 주요 강조점은 다음과 같습니다.

**스마트 자르기**

Adobe Sensei에서 제공하는 스마트 자르기는 반응형 디자인을 위한 관심 영역을 보존하면서 이미지의 비파괴적인 자르기를 자동으로 제공합니다. 잘린 이미지 제안을 미리 보고 필요한 경우 수동으로 조정할 수 있습니다. 이 기능을 사용하면 제품 이미지에 대한 자동 견본 생성을 사용할 수 있습니다.

스마트 자르기 사용에 대한 자세한 내용은 [이미지 프로필](/help/assets/image-profiles.md) 설명서를 참조하십시오.

Dynamic Media 구성 요소에서 스마트 자르기 작업에 대한 자세한 내용은 [페이지에 Dynamic Media 자산 추가](/help/assets/adding-dynamic-media-assets-to-pages.md)를 참조하십시오.

**스마트 이미징**

스마트 이미징은 각 사용자의 고유한 보기 특성을 활용하여 환경에 맞게 최적화된 이미지를 자동으로 제공하므로 향상된 성능과 참여를 제공합니다.

자세한 내용은 [스마트 이미징](/help/assets/imaging-faq.md) 설명서 를 참조하십시오.

![smart_crop](assets/smart_crop.png)

**새롭게 향상된 미디어 및 뷰어**

파노라마 및 VR을 비롯한 새 뷰어를 통해 몰입형 경험을 제공할 수 있습니다.

자세한 내용은 [파노라마 이미지](/help/assets/panoramic-images.md) 설명서를 참조하십시오.

### Experience Manager Forms {#experience-manager-forms}

AEM 6.4 Forms에는 여러 가지 새로운 기능과 개선 사항이 제공됩니다. 주요 내용은 다음과 같습니다.

* 멀티채널 인터랙티브 통신
* 비즈니스 애플리케이션에서 대화형 커뮤니케이션 미리 채우기
* 워크플로우 현대화 및 모바일 작업자 지원
* 지연 로드 조각
* LiveCycle에서 Forms 6.4로 단일 홉으로 업그레이드

[AEM Forms](forms.md) 릴리스 노트 페이지에 대한 자세한 내용. 새로운 기능 및 향상된 설명서 리소스에 대한 자세한 내용은 AEM 6.4 Forms](/help/forms/using/whats-new.md)의 [새 기능 및 개선 사항 요약 을 참조하십시오.

### Experience Manager Livefyre {#experience-manager-livefyre}

Livefyre를 AEM 6.4 인스턴스와 통합할 수 있습니다. AEM과 Livefyre를 통합하는 방법에 대한 정보는 다음과 같습니다.

* [Livefyre 통합](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)

### 고객 중심 개발 활용 {#leverage-customer-focused-development}

Adobe는 고객 중심 개발 모델을 사용하여 고객이 사양, 개발 및 테스트 중에 개발 프로세스의 모든 단계에 기여할 수 있도록 합니다. 이 프로세스에 참여하신 모든 고객과 파트너에게 감사의 인사를 드립니다.

Adobe는 고객 중심 버그 해결 및 개선 요청 개발의 수집, 우선 순위 지정 및 추적을 위한 절차와 프로세스를 마련했습니다. [Adobe Marketing Cloud 지원 포털](https://helpx.adobe.com/kr/contact/enterprise-support.ec.html)은 Adobe 개선 및 결함 추적 시스템과 통합되었습니다. 고객 문의는 가능한 경우 고객 지원 센터에서 식별 및 해결합니다. R&amp;D로 에스컬레이션하면 모든 고객 정보가 캡처되고 우선 순위 지정 및 보고용으로 사용됩니다. 개발 중에는 유료 지원 및 보증 문제, 유료 고객 개선 사항에 우선 순위가 부여됩니다.

이러한 우선 순위 지정 프로세스를 통해 500가지 이상의 고객 중심 변경 사항이 AEM 6.4에서 수정되었습니다.

## 릴리스의 일부인 파일 목록 {#list-of-files-that-are-part-of-the-release}

**Foundation**

* 독립형 빠른 시작: cq-quickstart-6.4.0.jar
* 애플리케이션 서버 빠른 시작:cq-quickstart-6.4.0.war
* 다양한 웹 서버 및 플랫폼에 대한 4.3.1 이상 [다운로드 링크](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)를 참조하십시오.
* Eclipse IDE용 플러그인입니다. [자세한 내용을 읽고 ](/help/sites-developing/aem-eclipse.md)을 다운로드하십시오.

* 대괄호 코드 편집기의 확장입니다.[자세히 읽고 ](/help/sites-developing/aem-brackets.md) 다운로드
* Maven/Gradle 종속성. [다운로드 링크](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/)를 참조하십시오.

**사이트**

* 쿠어 구성 요소([GitHub 프로젝트](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components))
* We.Retail 참조 구현([자세히 보기](/help/sites-developing/we-retail.md))
* 프로젝트 블루프린트 원형([GitHub 프로젝트](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype))
* 다양한 대상 플랫폼에 대한 AEM Screens Players([다운로드](https://download.macromedia.com/screens/))
* 스마트 컨텐츠 언어 모델입니다. 영어는 사전 설치되어 있으며 더 많은 언어를 다운로드할 수 있습니다.

   * [독일어](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [스페인어](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [이탈리아어](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [프랑스어](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [클래식 UI ](/help/sites-developing/modernization-tools.md) 구성 요소를 Coral 3으로 마이그레이션하기 위한 AEM 현대화 도구

**에셋**

* Adobe Experience Manager 데스크탑 앱([자세히 보기](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) 및 [다운로드](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html))

* 향상된 PDF 래스터라이저 기능 추가 패키지([자세한 내용](/help/assets/aem-pdf-rasterizer.md) 및 [다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg))

* 확장된 RAW 이미지 지원 추가 패키지([자세히 보기](/help/assets/camera-raw.md))

**양식**

* AEM Forms 기능 패키지:

   * [adobe-aemfd-aix-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-AIX)
   * [adobe-aemfd-linux-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-LX)
   * [adobe-aemfd-solaris-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-SOL)
   * [adobe-aemfd-win-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-WIN)
   * [adobe-aemfd-osx-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-OSX)

## 언어 {#languages}

다음의 언어로 사용자 인터페이스를 사용할 수 있습니다.

* 영어
* 독일어
* 프랑스어
* 스페인어
* 이탈리아어
* 브라질 포르투갈어
* 일본어
* 중국어 간체
* 중국어 번체(제한된 지원)
* 한국어

Experience Manager 6.4에서는 중국어 인코딩 표준을 사용하도록 GB18030-2005 CITS에 대해 인증되었습니다.

## 설치 및 업데이트 {#install-update}

설정 요구 사항은 [설치 지침](/help/sites-deploying/custom-standalone-install.md)을 참조하십시오.

자세한 지침은 [업그레이드 설명서](/help/sites-deploying/upgrade.md)를 참조하십시오.

## 지원되는 플랫폼 {#supported-platforms}

지원되는 플랫폼이 포함된 전체 매트릭스를 찾으십시오. [AEM 6.4 기술 요구 사항](/help/sites-deploying/technical-requirements.md)에 대한 지원 수준.

>[!NOTE]
>
>Oracle은 Oracle Java SE 제품에 대한 &quot;장기 지원&quot;(LTS) 모델로 이동되었습니다. Java 9 및 10은 Oracle의 비 LTS 릴리스입니다( [Oracle Java SE 지원 로드맵](https://www.oracle.com/technetwork/java/eol-135779.html) 참조). Adobe는 프로덕션 환경에서 AEM을 실행하는 데 필요한 Java LTS 릴리스만 지원합니다. 따라서 AEM 6.4에서 사용하려면 Java 8 버전이 권장됩니다.

## 더 이상 사용되지 않는 및 제거된 기능 {#deprecated-and-removed-features}

Adobe는 제품 기능을 지속적으로 평가하고 시간이 흘러도 더욱 강력한 버전으로 기능을 대체할 계획을 세우거나 이후 기대치나 확장에 효율적으로 대비할 수 있도록 선택된 부분을 재구현할 수 있습니다.

Adobe Experience Manager 6.4의 경우 [더 이상 사용되지 않는 및 제거된 기능 목록 읽기](deprecated-removed-features.md)를 참조하십시오. 또한 이 페이지에는 2019년 변경 사항에 대한 사전 공지 및 이전 릴리스에서 업데이트하는 고객을 위한 중요 알림이 포함되어 있습니다.

## 세부 변경 사항 목록 {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[AEM Forms](forms.md)

[AEM 기반 정보](wcm-platform.md)

## 알려진 문제 {#known-issues}

[알려진 문제 목록](known-issues.md)

### 제품 다운로드 및 지원(제한됨 사이트) {#product-download-and-support-restricted-sites}

다음 사이트는 고객만 사용할 수 있습니다. 액세스가 필요한 고객의 경우 Adobe 계정 관리자에게 문의하십시오.

* [licensing.adobe.com에서 제품 다운로드](https://licensing.adobe.com/).
* [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에 추가 기능을 위한 제품 업데이트, 패치 및 패키지.
* [Admin Console ](https://adminconsole.adobe.com/)를 통한 고객 지원. 자세한 내용은 [새 Adobe 고객 지원 경험](https://docs.adobe.com/content/help/ko-KR/customer-one/using/home.html)을 참조하십시오.
