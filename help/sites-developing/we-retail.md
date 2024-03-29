---
title: We.Retail 참조 구현
seo-title: We.Retail Reference Implementation
description: We.Retail은 AEM을 사용하여 온라인 상태를 설정하는 권장 방법을 보여주는 참조 구현의 기술 미리 보기입니다
seo-description: We.Retail is a technology preview of a reference implementation that illustrates the recommended way of setting up an online presence with AEM
uuid: d8833192-b592-4812-bf9b-bd882e8ee7f0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: f50150af-deff-4c29-bfe0-1cfc67b29d51
exl-id: 66c19394-9d2f-4bdd-9c17-f0ec8090f0b4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 10%

---

# We.Retail 참조 구현{#we-retail-reference-implementation}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

We.Retail은 Adobe Experience Manager을 사용하여 온라인 상태를 설정하는 권장 방법을 보여주는 참조 구현 및 샘플 컨텐츠입니다.

We.Retail에서는 HTL, 응답형 레이아웃, 편집 가능한 템플릿, 핵심 구성 요소 등과 같은 최신 AEM 기술을 사용합니다.

소매 카테고리를 설명하지만, 사이트 설정 방법은 모든 세로에 적용할 수 있으며, 제품 카탈로그 및 장바구니 기능만 소매별로 다릅니다.

## 기능 {#features}

We.Retail은 AEM 표준 참조 구현으로서 AEM의 가장 강력한 기능 중 일부를 소개합니다.

| **특별 포함** | **설명** | **관심 있어?** |
|---|---|---|
| [세계화된 사이트 구조](/help/sites-administering/tc-bp.md) | We.Retail에는 국가별 사이트에 라이브로 복사된 언어 마스터가 포함되어 있습니다. | [해 봐!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [응답형 레이아웃](/help/sites-authoring/responsive-layout.md) | 모든 페이지에는 화면 및 장치 크기에 맞게 동적으로 조정되는 응답형 레이아웃이 포함되어 있습니다. | [해 봐!](/help/sites-developing/we-retail-responsive-layout.md) |
| [편집 가능한 템플릿](/help/sites-developing/page-templates-editable.md) | 모든 페이지는 편집 가능한 템플릿을 기반으로 하므로 개발자가 아닌 사용자가 템플릿을 조정하고 사용자 지정할 수 있습니다. | [해 봐!](/help/sites-developing/we-retail-editable-templates.md) |
| [HTML 템플릿 언어](https://helpx.adobe.com/experience-manager/htl/user-guide.html) | 모든 구성 요소는 HTL을 기반으로 합니다 |  |
| [eCommerce 기능](/help/sites-developing/ecommerce.md) | 제품 카탈로그 기능 |  |
| [커뮤니티 사이트](/help/communities/overview.md) | 방문자가 커뮤니티 토론, 블로그 읽기 등에 참여할 수 있도록 허용 |  |
| [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko) | 모든 구성 요소는 새로운 핵심 구성 요소를 기반으로 하며 보다 편리하게 사용할 수 있으며 사용자가 즉시 구성할 수 있습니다 | [해 봐!](/help/sites-developing/we-retail-core-components.md) |
| [콘텐츠 조각](/help/assets/content-fragments.md) | We.Retail 경험 섹션에서는 컨텐츠 조각을 통해 컨텐츠를 재사용하는 기능을 보여줍니다. | [한번 해봐!](/help/sites-developing/we-retail-content-fragments.md) |
| [경험 조각](/help/sites-authoring/experience-fragments.md) | 경험 조각 은 페이지 내에서 참조할 수 있는 컨텐츠 및 레이아웃을 포함한 하나 이상의 구성 요소 그룹입니다. | [한번 해봐!](/help/sites-developing/we-retail-experience-fragments.md) |

## 시작하기 {#getting-started}

We.Retail은 AEM 샘플 컨텐츠로 제공됩니다. 사용하려면 [평소대로 AEM을 시작합니다.](/help/sites-deploying/deploy.md#getting-started): 샘플 컨텐츠가 비활성화되지 않았는지 확인합니다.

>[!CAUTION]
>
>We.Retail은 프로덕션 인스턴스에 설치하지 않아야 합니다. 프로덕션 인스턴스는 `nosamplecontent` [runmode](/help/sites-deploying/configure-runmodes.md).

>[!CAUTION]
>
>We.Retail은 최신 AEM 기술을 기반으로 하므로 지원되지 않습니다 [클래식 UI 작성](/help/sites-classic-ui-authoring/home.md).

### 최신 버전 {#latest-version}

We.Retail은 AEM 릴리스와 함께 배포되지만, 컨텐츠 및 해당 기능에 대한 업데이트가 릴리스 후에 제공될 수 있습니다. 따라서 다음을 수행할 수 있습니다 [gitHub에서 최신 릴리스 다운로드](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) 그리고 [업로드](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) 및 [설치](/help/sites-administering/package-manager.md#installing-packages) AEM 인스턴스에서 패키지로 사용됩니다.

### 첫 단계 {#first-steps}

1. AEM이 시작되면(및/또는 We.Retail이 설치됨) 사이트에 **We.Retail** 다음에서 사용 가능합니다. [사이트 콘솔](/help/sites-authoring/basic-handling.md#global-navigation).
1. 예를 들어 다음 페이지를 열 수 있으며 이 페이지는 [부록](#appendix) 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## We.Retail 및 Geometrixx {#we-retail-geometrixx}

Geometrixx과 그 많은 양식은 이전 버전의 AEM에서 샘플 콘텐츠로 제공되었습니다. 버전 6.3 이후, We.Retail은 AEM과 함께 제공되는 샘플 컨텐츠이며, 새로운 표준 참조 구현 역할을 합니다.

We.Retail은 기술적으로 더 강력하며 최신 AEM 기술을 활용하여 보다 유연하고 확장 가능하며, 제품의 최신 기능을 보여줍니다.

### 기능 비교 {#feature-comparison}

다음 표는 Geometrixx과 비교하여 We.Retail에서 사용할 수 있는 주요 기능에 대한 개요를 제공합니다.

* **사용 가능** 는 기능의 예가 샘플 컨텐츠에 있음을 의미합니다.
* **사용할 수 없음** 은 기능의 예를 샘플 컨텐츠에서 사용할 수 없지만 기능 자체가 아니라는 것을 의미합니다.

| **특별 포함** | **We.Retail** | **Geometrixx** |
|---|---|---|
| 세계화된 사이트 구조 | 언어 마스터가 국가별 사이트에 라이브로 복사됩니다. | 사용할 수 없음 |
| 콘텐츠 조각 | 사용 가능 | 사용할 수 없음 |
| 경험 조각 | 사용 가능 | 사용할 수 없음 |
| 반응형 레이아웃 | 모든 페이지에 대해 | Geometrixx Media 전용 |
| 편집 가능한 템플릿 | 모든 페이지에 대해 | 사용할 수 없음 |
| HTL | 모든 구성 요소 | 제한적 |
| 타깃팅 | 모든 페이지에 대해 | Geometrixx Outdoors 전용 |
| Screens | 사용 가능 | 사용할 수 없음 |
| 모바일 | 사용할 수 없음 | 사용 가능 |
| 원고 | 사용할 수 없음 | 사용 가능 |
| 회전판, 다운로드, 차트 구성 요소 | 사용할 수 없음 | 사용 가능 |
| 열 컨트롤 | 레이아웃 컨테이너로 대체됨 | 사용 가능 |
| Forms | 사용할 수 없음 | 사용 가능 |
| 캠페인 | 이메일 샘플 없음 | 사용 가능 |

>[!NOTE]
>
>이 목록은 완성을 위해 노력하고 있지만 완전한 것으로 간주되어서는 안 됩니다.

## Contribute {#contribute}

We.Retail은 오픈 소스 프로젝트로 출시되었으며 최신 버전의 소스 코드는 GitHub에서 다운로드할 수 있습니다.

GITHUB의 코드

GitHub에서 이 페이지의 코드를 찾을 수 있습니다

* [GitHub에서 aem-sample-we-retail 프로젝트 열기](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* 다음 이름으로 프로젝트를 다운로드합니다 [ZIP 파일](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/archive/master.zip)

최신 릴리스는 [직접 다운로드](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/latest) 를 설치 가능한 패키지로 사용합니다.

문제가 발생하면 파일을 제출하십시오 [GitHub 문제](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

포크하거나 기여할 수 있습니다. [가져오기 요청](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls).

## 미리보기 {#preview}

We.Retail 시작 페이지의 미리 보기:

![screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
