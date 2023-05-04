---
title: AEM Communities 개요
seo-title: AEM Communities Overview
description: AEM Communities 기능 및 설정에 대한 개요
seo-description: An overview of AEM Communities features and setup
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---

# AEM Communities 개요 {#aem-communities-overview}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager (AEM) Communities는 성능 향상, 사이트 관리 개선 사항을 포함한 온-프레미스 커뮤니티 사이트를 빠르게 생성하고 사이트 방문자를 중요한 커뮤니티 구성원으로 전환할 수 있도록 권장하는 기능을 제공합니다.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## 커뮤니티 기능 {#communities-features}

AEM Communities을 사용하면 블로그, Q&amp;A 및 이벤트 달력을 통해 정보를 제공하는 사이트 방문자와 관계를 개발할 수 있을 뿐만 아니라 포럼, 댓글 및 기타 커뮤니티 콘텐츠를 통해 통찰력을 얻을 수 있습니다(종종 사용자 생성 콘텐츠(UGC)라고도 함).

또한 AEM Communities에서는 게시 환경에서 신뢰할 수 있는 구성원이 중재할 수 있고, Twitter 및 Facebook으로 소셜 로그인, 커뮤니티 콘텐츠의 인라인 번역, 게시된 커뮤니티 사이트에서 커뮤니티 그룹 만들기, 수상 배지에 대한 점수 책정, 파일 공유, 알림 및 활동 스트림을 사용할 수 있습니다.

커뮤니티 기능은 [AEM 데모 컴퓨터](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) GitHub.com 또는 새로운 We.Retail 참조 구현에서 공개적으로 제공됩니다.

## 커뮤니티 사이트 {#community-sites}

커뮤니티 사이트는 간단한 마법사를 사용하여 만든 AEM 사이트로서, 이를 통해 사이트에 사전 연결되는 많은 일반적인 기능이 있는 웹 사이트를 만듭니다.

다음 [사이트 만들기 마법사](sites-console.md):

* 선택한 사이트에 따라 사이트의 기능 결합 [커뮤니티 사이트 템플릿](sites.md) 다음 중
   * 빌드됨 [커뮤니티 기능](#community-functions)
   * 선택 사항입니다 [커뮤니티 그룹](#communitygroups) 기능
* 설정을 사용하여 다음을 구성합니다.
   * 관리
   * 로그인
   * 번역
* 필수 기능 제공:
   * 반응형 디자인: 사용 [Twitter Bootstrap 테마](https://getbootstrap.com)
   * 로그인: 자체 등록, [소셜 로그인](social-login.md), 사용자 프로필
   * 알림: 구성원들은 관련성이 있는 이벤트를 봅니다
   * 메시징: 구성원은 커뮤니티 사이트 내에서 메시지를 보내거나 받을 수 있습니다
   * 검색: 커뮤니티 사이트 내에서 검색 기능
   * 언어 전환: 언어 선택 기능 [다국어 사이트](../../help/sites-administering/translation.md)
   * 관리: 커뮤니티 사이트 내에서 사용자를 중재하고 관리할 권한이 있는 구성원이 액세스할 수 있습니다
* 페이지 수준의 여러 작성 단계가 제거됩니다.
   * 브랜딩: 커뮤니티 사이트의 모든 페이지에 표시할 배너 이미지의 선택적 업로드
   * 탐색 메뉴: 탐색 링크는 커뮤니티 사이트 템플릿에 포함된 기능에 대해 제공됩니다

새 커뮤니티 사이트를 손쉽게 만들 수 있도록 하려면 를 방문하십시오. [AEM Communities 시작하기](getting-started.md).

## 커뮤니티 컨텐츠 지속성 {#community-content-persistence}

커뮤니티 컨텐츠의 성능 및 동기화를 개선하기 위해 AEM Communities에는 모든 AEM(작성자 및 게시) 인스턴스 간에 공유되는 사용자 생성 콘텐츠(UGC)를 위한 공용 저장소가 필요합니다.

SRP(Storage Resource Provider)를 통해 쉽게 액세스할 수 있습니다. SRP는 기본 토폴로지와 별도의 액세스를 제공하고 UGC를 위한 공용 저장소를 지원합니다.

커뮤니티 콘텐츠 지속성 및 권장 배포에 대해 자세히 알아보려면:

* [커뮤니티 컨텐츠 저장소](working-with-srp.md): UGC에 사용 가능한 SRP 스토리지 옵션에 대해 설명합니다.
* [권장 토폴로지](topologies.md): 사용 사례 및 SRP 선택을 기반으로 토폴로지 논의
* [AEM 6.3 Communities로 업그레이드](upgrade.md): AEM 6.3으로 이동할 때 UGC에 대한 유용한 정보를 제공합니다.

## 커뮤니티 콘솔 {#communities-consoles}

작성 환경에서 전역 탐색 콘솔은 [커뮤니티 콘솔](consoles.md):

* [Sites](sites-console.md) 콘솔

   * 사이트 만들기
   * 사이트 편집
   * 사이트 관리
   * [커뮤니티 그룹](groups.md) 콘솔

* [중재](moderation.md) 콘솔

   * 작성자 및 게시 환경을 위한 일반적인 벌크 조정 UI
   * 새 필터링 기준

* [구성원 및 그룹](members.md) 관리 콘솔

   * 작성 환경에서 게시 측 사용자(구성원)를 만들고 관리하는 기능을 제공합니다
   * 구성원 금지 기능 제공
   * 작성 환경에서 게시 측 사용자 그룹(구성원 그룹)을 만들고 관리하는 기능을 제공합니다

* [보고서](reports.md) 콘솔

   * 할당, 게시물 및 보기에 대한 보고서를 생성할 수 있는 기능을 제공합니다

* [리소스](resources.md) 콘솔

   * 지원 리소스 및 학습 경로를 만드는 기능을 제공합니다.
   * 지원 리소스 및 학습 경로에 대한 보고서에 대한 액세스 권한을 제공합니다.

전역 도구 콘솔에서는 다음 커뮤니티 도구에 액세스할 수 있습니다.

* [사이트 템플릿](tools.md#sitetemplatesconsole) 콘솔

   * 커뮤니티 사이트 템플릿 만들기 및 관리

* [그룹 템플릿](tools.md#grouptemplatesconsole) 콘솔

   * 커뮤니티 그룹 템플릿 만들기 및 관리

* [커뮤니티 함수](tools.md#communityfunctionsconsole) 콘솔

   * 커뮤니티 기능 만들기 및 관리

* [스토리지 구성](tools.md#storageconfiguratonconsole) 콘솔

   * 을(를) 선택하고 구성합니다 [일반 상점](working-with-srp.md) 사이트

* [구성 요소 가이드](components-guide.md)

   * 샘플 사이트, [커뮤니티 구성 요소](http://localhost:4502/editor.html/content/community-components/en.html)- 모든 Communities 구성 요소의 샘플에 기본 구성 및 실험할 수 있는 기능을 제공합니다

## 커뮤니티 사이트 템플릿 {#community-site-templates}

커뮤니티 사이트 만들기는 샘플 사이트와 독립적인 커뮤니티 사이트를 빠르게 설정할 수 있도록 커뮤니티 사이트 템플릿의 선택을 기반으로 합니다.

커뮤니티 기능 및 커뮤니티 그룹 템플릿으로 구성된 커뮤니티 사이트 템플릿은 로그인, 사용자 프로필, 메시징, 사이트 메뉴, 검색, 테마 및 브랜딩 기능을 포함한 커뮤니티 사이트의 구조를 제공합니다.

자세한 내용은 [사이트 템플릿 콘솔](sites.md).

## 커뮤니티 기능 {#community-functions}

커뮤니티 경험에 필요한 기능은 잘 알려져 있습니다. AEM Communities을 사용하면 이러한 기능을 커뮤니티 기능이라고 하는 빌딩 블록으로 사용할 수 있습니다.

커뮤니티 함수는 커뮤니티 사이트 템플릿에 쉽게 통합되는 기능으로 함께 연결된 구성 요소로 구성된 일반적인 AEM 페이지입니다.

자세한 내용은 [커뮤니티 기능 콘솔](functions.md).

## 커뮤니티 그룹 및 그룹 템플릿 {#community-groups-and-group-templates}

커뮤니티 그룹 기능은 작성자 및 게시 환경 모두에서 권한이 있는 사용자와 커뮤니티 구성원이 커뮤니티 사이트 내에서 하위 커뮤니티를 동적으로 만들 수 있는 기능입니다.

작성 환경에서 템플릿의 구조에 가 포함된 경우 기존 커뮤니티 사이트 내에 커뮤니티 그룹(하위 커뮤니티)을 만들거나 기존 그룹 내에 중첩될 수 있습니다 [그룹 함수](functions.md#groups-function).

커뮤니티 그룹을 만들려면 커뮤니티 그룹 페이지의 디자인을 제공하는 커뮤니티 그룹 템플릿을 선택해야 합니다. 그룹 기능이 템플릿 구조에 추가되면 그룹 템플릿을 지정하거나 새 커뮤니티 그룹을 만들 때 템플릿 선택을 제공하도록 구성됩니다.

또한 다음 문서도 참조할 수 있습니다.

* [사이트 그룹 콘솔](groups.md) - 작성 환경에서 하위 커뮤니티 만들기
* [그룹 템플릿 콘솔](tools-groups.md) - 그룹에 대한 사이트 구조 만들기
* [AEM Communities 시작하기](getting-started.md) - 중첩 그룹을 포함하는 커뮤니티 사이트를 빠르게 만들기 위한 자습서

## 커뮤니티 구성 요소 {#community-components}

다음 [커뮤니티 구성 요소](author-communities.md) 커뮤니티 사이트가 빌드된 는 AEM 사이트에 커뮤니티 기능을 추가하는 데 사용할 수 있습니다.

다음 [커뮤니티 구성 요소 안내서](components-guide.md) 구성 요소의 대화형 탐색에 사용할 수 있습니다.

## 커뮤니티 유형 {#types-of-communities}

### 참여 커뮤니티 {#engagement-community}

참여 커뮤니티는 고객이 커뮤니티의 구성원으로서 상호 작용할 수 있도록 알리고, 피드백을 요청하고, 참여하도록 하는 데 중점을 둔 커뮤니티 사이트입니다.

참여 커뮤니티의 기능은 다음과 같습니다.

* 로그인
* 메시지
* 포럼
* 댓글
* 리뷰
* 등급
* 투표
* 블로그
* 그룹
* 달력
* 번역
* 관리
* 알림
* 점수 및 배지
* Analytics 보고

새 참여 커뮤니티를 빠르게 만들 수 있는 편리한 기능을 경험해 보려면 를 방문하십시오. [AEM Communities 시작하기](getting-started.md).

### 지원 커뮤니티 {#enablement-community}

지원 커뮤니티는 온라인 학습을 위한 기능을 포함하는 커뮤니티 사이트입니다.

지원 커뮤니티의 기능은 다음과 같습니다.

* 의 모든 기능 [참여 커뮤니티](#engagement-community)
* 구성원 및 구성원 그룹에 컨텐츠 및 학습 리소스를 할당하는 기능
* 퀴즈 및 테스트와 같은 SCORM 컨텐츠 지원
* 지정 완료 추적
* 보고 및 분석에 대한 액세스
* 포럼, 메시징, 댓글 및 등급을 통해 학습 리소스에 대한 대화를 수행할 수 있습니다

사용 커뮤니티는 [사용 추가 기능이 구성되었습니다](enablement.md): 프로덕션 환경에서 사용할 추가 라이센스가 필요합니다. 지원 커뮤니티 사이트에는 [지정 함수](#community-functions).

새 지원 커뮤니티를 쉽게 만들려면 [AEM Communities for Enablement 시작하기](getting-started-enablement.md).

## AEM 데모 컴퓨터 {#aem-demo-machine}

다음 [AEM 데모 컴퓨터](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) AEM 데모 관리 및 실행 [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [자산](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [커뮤니티](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [앱](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) 및 [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)- QuickStart 인스턴스를 단순히 시작하는 것보다 더 많은 설정이 필요한 경우가 많습니다. AEM 데모 시스템이 추가 설정을 수행합니다 [인프라](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) MongoDB, Solr, MySQL, FFmpeg 및 전자 메일 서버와 같은 MongoDB, Solr, MySQL, FFmpeg 및 전자 메일 서버입니다.

AEM 데모 시스템은

* A [그래픽 사용자 인터페이스](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* 구성 가능한 Apache ANT 스크립트 [속성](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) 및 [타겟](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* AEM 데모 시스템을 설치하기 위한 패키지가 Windows, MacOS 및 Linux의 CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 및 AEM 6.3에서 성공적으로 테스트되었습니다.

AEM 데모 시스템에는 유효한 AEM 라이센스가 필요합니다.

>[!NOTE]
>
>보기 [비디오 소개](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) AEM 데모 컴퓨터 (13:26).

## AEM Communities 설명서 {#aem-communities-documentation}

* 방문 [커뮤니티 배포](deploy-communities.md) 권장 배포에 대해 자세히 알아보십시오 .

* 방문 [커뮤니티 사이트 관리](administer-landing.md) 커뮤니티 사이트 만들기, 커뮤니티 그룹 추가, 커뮤니티 사이트 템플릿 구성, 커뮤니티 콘텐츠 중재, 구성원 관리, 태깅, 알림, 점수 책정 및 배지에 대해 알아보십시오.

* 방문 [커뮤니티 개발](communities.md) SCF(소셜 구성 요소 프레임워크) 및 커뮤니티 구성 요소 및 기능 사용자 지정에 대해 알아봅니다.

* 방문 [커뮤니티 구성 요소 작성](author-communities.md) 커뮤니티 구성 요소를 사용하여 작성하고 구성하는 방법을 알아봅니다.
