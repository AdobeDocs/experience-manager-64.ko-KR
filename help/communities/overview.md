---
title: AEM Communities 개요
seo-title: AEM Communities 개요
description: AEM Communities 기능 및 설정에 대한 개요
seo-description: AEM Communities 기능 및 설정에 대한 개요
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 4%

---

# AEM Communities 개요 {#aem-communities-overview}

AEM(Adobe Experience Manager) Communities는 성능 및 사이트 관리를 향상시키고 사이트 방문자가 중요한 커뮤니티 구성원으로 전환할 수 있도록 권장하는 On-Premise 커뮤니티 사이트를 빠르게 생성하는 기능을 제공합니다.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## 커뮤니티 기능 {#communities-features}

AEM Communities을 사용하면 블로그, Q&amp;A 및 이벤트 달력을 통해 정보를 제공하는 사이트 방문자와 관계를 개발할 수 있을 뿐만 아니라 포럼, 댓글 및 기타 커뮤니티 콘텐츠를 통해 통찰력을 얻을 수 있습니다(종종 사용자 생성 콘텐츠(UGC)라고도 함).

또한 AEM Communities에서는 게시 환경에서 신뢰할 수 있는 구성원이 중재할 수 있고, Twitter 및 Facebook으로 소셜 로그인, 커뮤니티 콘텐츠의 인라인 번역, 게시된 커뮤니티 사이트에서 커뮤니티 그룹 만들기, 수상 배지에 대한 점수 책정, 파일 공유, 알림 및 활동 스트림을 사용할 수 있습니다.

커뮤니티 기능은 GitHub.com에서 공개적으로 제공되는 [AEM 데모 컴퓨터](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki)를 사용하거나 새로운 We.Retail 참조 구현을 통해 보여줄 수 있습니다.

## 커뮤니티 사이트 {#community-sites}

커뮤니티 사이트는 간단한 마법사를 사용하여 만든 AEM 사이트로서, 이를 통해 사이트에 사전 연결되는 많은 일반적인 기능이 있는 웹 사이트를 만듭니다.

[사이트 만들기 마법사](sites-console.md):

* 선택한 [커뮤니티 사이트 템플릿](sites.md)을 기반으로 사이트의 기능을 결합합니다.
   * [커뮤니티 함수](#community-functions)에서 빌드됨
   * 옵션 [커뮤니티 그룹](#communitygroups) 기능
* 설정을 사용하여 다음을 구성합니다.
   * 중재
   * 로그인
   * 번역
* 필수 기능 제공:
   * 반응형 디자인:[Twitter Bootstrap 테마 사용](https://getbootstrap.com)
   * 로그인:자체 등록, [소셜 로그인](social-login.md), 사용자 프로필
   * 알림:구성원들은 관련성이 있는 이벤트를 봅니다
   * 메시징:구성원은 커뮤니티 사이트 내에서 메시지를 보내거나 받을 수 있습니다
   * 검색:커뮤니티 사이트 내에서 검색 기능
   * 언어 전환:[다국어 사이트](../../help/sites-administering/translation.md)에 사용할 언어를 선택하는 기능
   * 관리:커뮤니티 사이트 내에서 사용자를 중재하고 관리할 권한이 있는 구성원이 액세스할 수 있습니다
* 페이지 수준의 여러 작성 단계가 제거됩니다.
   * 브랜딩:커뮤니티 사이트의 모든 페이지에 표시할 배너 이미지의 선택적 업로드
   * 탐색 메뉴:탐색 링크는 커뮤니티 사이트 템플릿에 포함된 기능에 대해 제공됩니다

새 커뮤니티 사이트를 쉽게 만들 수 있도록 하려면 [AEM Communities 시작하기](getting-started.md)를 방문하십시오.

## 커뮤니티 컨텐츠 지속성 {#community-content-persistence}

커뮤니티 컨텐츠의 성능 및 동기화를 개선하기 위해 AEM Communities에는 모든 AEM(작성자 및 게시) 인스턴스 간에 공유되는 사용자 생성 콘텐츠(UGC)를 위한 공용 저장소가 필요합니다.

SRP(Storage Resource Provider)를 통해 쉽게 액세스할 수 있습니다. SRP는 기본 토폴로지와 별도의 액세스를 제공하고 UGC를 위한 공용 저장소를 지원합니다.

커뮤니티 콘텐츠 지속성 및 권장 배포에 대해 자세히 알아보려면:

* [커뮤니티 컨텐츠 저장소](working-with-srp.md):UGC에 사용 가능한 SRP 스토리지 옵션에 대해 설명합니다.
* [권장 토폴로지](topologies.md):사용 사례 및 SRP 선택을 기반으로 토폴로지 논의
* [AEM 6.3 Communities로 업그레이드](upgrade.md):AEM 6.3으로 이동할 때 UGC에 대한 유용한 정보를 제공합니다.

## 커뮤니티 콘솔 {#communities-consoles}

작성 환경에서 전역 탐색 콘솔은 다음을 포함하는 [커뮤니티 콘솔](consoles.md)에 액세스할 수 있습니다.

* [사이트](sites-console.md) 콘솔

   * 사이트 만들기
   * 사이트 편집
   * 사이트 관리
   * [커뮤니티 ](groups.md) 그룹콘솔

* [](moderation.md) Moderationconsole

   * 작성자 및 게시 환경을 위한 일반적인 벌크 조정 UI
   * 새 필터링 기준

* [구성원 및 ](members.md) 그룹관리 콘솔

   * 작성 환경에서 게시 측 사용자(구성원)를 만들고 관리하는 기능을 제공합니다
   * 구성원 금지 기능 제공
   * 작성 환경에서 게시 측 사용자 그룹(구성원 그룹)을 만들고 관리하는 기능을 제공합니다

* [](reports.md) Reportconsole

   * 할당, 게시물 및 보기에 대한 보고서를 생성할 수 있는 기능을 제공합니다

* [](resources.md) 리소스 콘솔

   * 지원 리소스 및 학습 경로를 만드는 기능을 제공합니다.
   * 지원 리소스 및 학습 경로에 대한 보고서에 대한 액세스 권한을 제공합니다.

전역 도구 콘솔에서는 다음 커뮤니티 도구에 액세스할 수 있습니다.

* [사이트 ](tools.md#sitetemplatesconsole) 템플릿 콘솔

   * 커뮤니티 사이트 템플릿 만들기 및 관리

* [그룹 ](tools.md#grouptemplatesconsole) 템플릿 콘솔

   * 커뮤니티 그룹 템플릿 만들기 및 관리

* [커뮤니티 ](tools.md#communityfunctionsconsole) 기능 콘솔

   * 커뮤니티 기능 만들기 및 관리

* [스토리지 ](tools.md#storageconfiguratonconsole) 구성 콘솔

   * 사이트에 대한 [일반 저장소](working-with-srp.md)를 선택하고 구성합니다

* [구성 요소 가이드](components-guide.md)

   * 모든 Communities 구성 요소의 샘플에 기본 구성과 실험할 수 있는 기능을 제공하는 샘플 사이트 [커뮤니티 구성 요소](http://localhost:4502/editor.html/content/community-components/en.html)

## 커뮤니티 사이트 템플릿 {#community-site-templates}

커뮤니티 사이트 만들기는 샘플 사이트와 독립적인 커뮤니티 사이트를 빠르게 설정할 수 있도록 커뮤니티 사이트 템플릿 선택에 따라 수행됩니다.

커뮤니티 기능 및 커뮤니티 그룹 템플릿으로 구성된 커뮤니티 사이트 템플릿은 로그인, 사용자 프로필, 메시징, 사이트 메뉴, 검색, 테마 및 브랜딩 기능을 포함한 커뮤니티 사이트의 구조를 제공합니다.

[사이트 템플릿 콘솔](sites.md)을 참조하십시오.

## 커뮤니티 기능 {#community-functions}

커뮤니티 경험에 필요한 기능은 잘 알려져 있습니다. AEM Communities을 사용하면 이러한 기능을 커뮤니티 기능이라고 하는 빌딩 블록으로 사용할 수 있습니다.

커뮤니티 함수는 커뮤니티 사이트 템플릿에 쉽게 통합되는 기능으로 함께 연결된 구성 요소로 구성된 일반적인 AEM 페이지입니다.

[커뮤니티 함수 콘솔](functions.md)을 참조하십시오.

## 커뮤니티 그룹 및 그룹 템플릿 {#community-groups-and-group-templates}

커뮤니티 그룹 기능은 작성자 및 게시 환경 모두에서 권한이 있는 사용자와 커뮤니티 구성원이 커뮤니티 사이트 내에서 하위 커뮤니티를 동적으로 만들 수 있는 기능입니다.

작성 환경에서 템플릿의 구조에 [그룹 함수](functions.md#groups-function)가 포함된 경우 기존 커뮤니티 사이트 내에 커뮤니티 그룹(하위 커뮤니티)을 만들거나 기존 그룹 내에 중첩할 수 있습니다.

커뮤니티 그룹을 만들려면 커뮤니티 그룹 페이지의 디자인을 제공하는 커뮤니티 그룹 템플릿을 선택해야 합니다. 그룹 기능이 템플릿 구조에 추가되면 그룹 템플릿을 지정하거나 새 커뮤니티 그룹을 만들 때 템플릿 선택을 제공하도록 구성됩니다.

참고 항목:

* [사이트 그룹 콘솔](groups.md)  - 작성 환경에서 하위 커뮤니티 만들기
* [그룹 템플릿 콘솔](tools-groups.md)  - 그룹에 대한 사이트 구조 만들기
* [AEM Communities 시작하기](getting-started.md)  - 중첩 그룹을 포함하는 커뮤니티 사이트를 빠르게 만들기 위한 자습서

## 커뮤니티 구성 요소 {#community-components}

커뮤니티 사이트가 빌드된 [커뮤니티 구성 요소](author-communities.md)는 AEM 사이트에 커뮤니티 기능을 추가하는 데 사용할 수 있습니다.

[커뮤니티 구성 요소 안내서](components-guide.md)는 구성 요소를 탐색하는 데 사용할 수 있습니다.

## 커뮤니티 유형 {#types-of-communities}

### 참여 커뮤니티 {#engagement-community}

참여 커뮤니티는 고객이 커뮤니티의 구성원으로서 상호 작용할 수 있도록 알리고, 피드백을 요청하고, 참여하도록 하는 데 중점을 둔 커뮤니티 사이트입니다.

참여 커뮤니티의 기능은 다음과 같습니다.

* 로그인
* 메시지
* 포럼
* 댓글
* 검토
* 등급
* 투표
* 블로그
* 그룹
* 달력
* 번역
* 중재
* 알림
* 점수 및 배지
* Analytics 보고

새 참여 커뮤니티를 빠르게 만들 수 있는 편리한 기능을 경험하려면 [AEM Communities 시작하기](getting-started.md)를 방문하십시오.

### 지원 커뮤니티 {#enablement-community}

지원 커뮤니티는 온라인 학습을 위한 기능을 포함하는 커뮤니티 사이트입니다.

지원 커뮤니티의 기능은 다음과 같습니다.

* [참여 커뮤니티](#engagement-community)의 모든 기능
* 구성원 및 구성원 그룹에 컨텐츠 및 학습 리소스를 할당하는 기능
* 퀴즈 및 테스트와 같은 SCORM 컨텐츠 지원
* 지정 완료 추적
* 보고 및 분석에 대한 액세스
* 포럼, 메시징, 댓글 및 등급을 통해 학습 리소스에 대한 대화를 수행할 수 있습니다

[지원 추가 기능이 구성된 경우 프로덕션 환경에서 사용할 추가 라이선스가 필요한 지원 커뮤니티를 만들 수 있습니다.](enablement.md) 지원 커뮤니티 사이트에는 [할당 함수](#community-functions)가 포함됩니다.

새 지원 커뮤니티를 쉽게 만들 수 있도록 하려면 [AEM Communities for Enablement](getting-started-enablement.md)를 방문하십시오.

## AEM 데모 컴퓨터 {#aem-demo-machine}

[AEM 데모 시스템](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine)은 AEM [사이트](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [자산](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [커뮤니티](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [앱](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) 및 [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)에 대한 데모를 관리하고 실행하며, 이 데모는 QuickStart 인스턴스를 시작하는 것보다 더 많은 설정이 필요합니다. AEM 데모 시스템은 MongoDB, Solr, MySQL, FFmpeg 및 이메일 서버와 같은 추가 [인프라](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure)를 설정합니다.

AEM 데모 시스템은

* [그래픽 사용자 인터페이스](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* 구성 가능한 [속성](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) 및 [타겟](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)이 있는 Apache ANT 스크립트
* 설치할 패키지
AEM 데모 시스템은 Windows, MacOS 및 Linux의 CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 및 AEM 6.3에서 성공적으로 테스트되었습니다.

AEM 데모 시스템에는 유효한 AEM 라이센스가 필요합니다.

>[!NOTE]
>
>AEM 데모 컴퓨터에 대한 [비디오 소개](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be)를 (13:26).

## AEM Communities 설명서 {#aem-communities-documentation}

* 권장 배포에 대해 알아보려면 [Communities 배포](deploy-communities.md)를 방문하십시오.

* 커뮤니티 사이트 만들기, 커뮤니티 그룹 추가, 커뮤니티 사이트 템플릿 구성, 커뮤니티 컨텐츠 중재, 구성원 관리, 태깅, 알림, 점수 책정 및 배지에 대해 알아보려면 [커뮤니티 사이트 관리](administer-landing.md)를 방문하십시오.

* SCF(소셜 구성 요소 프레임워크)에 대해 알아보고 커뮤니티 구성 요소 및 기능을 사용자 지정하려면 [커뮤니티 개발](communities.md)을 방문하십시오.

* 커뮤니티 구성 요소를 사용하여 작성하고 구성하는 방법을 배우려면 [커뮤니티 구성 요소 작성](author-communities.md)을 방문하십시오.
