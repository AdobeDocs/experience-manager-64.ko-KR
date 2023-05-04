---
title: 개발 및 페이지 비교
seo-title: Developing and Page Diff
description: 개발 및 페이지 비교
seo-description: null
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
exl-id: 365e944d-d8a3-4f4e-8925-88629845232f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 5%

---

# 개발 및 페이지 비교{#developing-and-page-diff}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 기능 개요 {#feature-overview}

콘텐츠 작성은 반복적 프로세스입니다. 효율적인 작성을 위해서는 한 이터레이션에서 다른 이터레이션으로 변경된 사항을 확인할 수 있어야 합니다. 한 페이지 버전을 확인한 다음, 다른 버전을 확인하는 것은 비효율적이며 오류가 발생하기 쉽습니다. 작성자는 현재 페이지를 이전 버전과 비교하여 강조 표시된 차이점을 나란히 비교하려고 합니다.

페이지 차이를 사용하면 사용자가 현재 페이지를 실행, 이전 버전 등과 비교할 수 있습니다. 이 사용자 기능에 대한 자세한 내용은 [페이지 비교](/help/sites-authoring/page-diff.md).

## 작업 세부 정보 {#operation-details}

페이지 버전을 비교할 때 사용자가 비교하려는 이전 버전은 비교를 쉽게 하기 위해 백그라운드에서 AEM에 의해 다시 생성됩니다. 콘텐츠를 렌더링하려면 다음이 필요합니다 [을 참조하십시오](/help/sites-authoring/page-diff.md#presentation-of-differences).

이 레크리에이션 작업은 AEM에서 내부적으로 수행되며 사용자에게 투명하며 간섭이 필요하지 않습니다. 그러나 CRX DE Lite와 같이 리포지토리를 보는 관리자는 컨텐츠 구조 내에서 이러한 재구성된 버전을 볼 수 있습니다.

AEM 패치 수준에 따라 동작이 다르며, 제대로 작동하려면 특정 권한이 필요할 수 있습니다.

### AEM 6.4.3 이전 {#prior-to-aem}

컨텐츠를 비교할 때 비교할 페이지까지의 전체 트리가 다음 위치에 다시 만들어집니다.

`/content/versionhistory/<userId>/<site structure>`

페이지 차이 메커니즘을 사용할 때 AEM에서는 페이지의 이전 버전을 다시 생성하므로 사용자가 특정 JCR 권한을 가지고 있어야 합니다.

>[!CAUTION]
>
>페이지 비교 기능을 사용하려면 사용자에게 **수정/만들기/삭제** 노드의 권한 `/content/versionhistory`.

### AEM 6.4.3 기준 {#as-of-aem}

컨텐츠를 비교할 때 비교할 페이지까지의 전체 트리가 다음 위치에 다시 만들어집니다.

`/tmp/versionhistory/`

이 콘텐츠는 현재 사용자의 가시성을 제한하는 권한이 있는 서비스 사용자가 만듭니다. 따라서 특별한 권한이 필요하지 않습니다.

이 임시 콘텐츠를 정리하기 위해 정리 작업이 자동으로 실행됩니다.

## 개발자 제한 사항 {#developer-limitations}

이전에는 클래식 UI에서 AEM을 쉽게 하기 위해(예: 사용) 특수 개발 고려 사항을 적용했습니다 `cq:text` 태그 라이브러리 또는 사용자 정의 통합 `DiffService` 구성 요소에 OSGi 서비스 참조). 이러한 diff는 DOM 비교를 통해 클라이언트측에서 수행되므로 더 이상 새로운 diff 기능에 필요하지 않습니다.

그러나 개발자는 많은 제한 사항을 고려해야 합니다.

* 이 기능은 AEM Product에 간격이 있지 않은 CSS 클래스를 사용합니다. 이름이 같은 다른 사용자 지정 CSS 클래스나 타사 CSS 클래스가 페이지에 포함되어 있는 경우 비교 표시가 영향을 받을 수 있습니다.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* 비교는 클라이언트측이며 페이지 로드 시 실행되므로 클라이언트측 차이 서비스가 실행된 후 DOM에 대한 모든 조정은 계산되지 않습니다. 영향을 줄 수 있습니다

   * AJAX을 사용하여 컨텐츠를 포함하는 구성 요소
   * SPA (Single Page Applications)
   * 사용자 상호 작용 시 DOM을 조작하는 Javascript 기반 구성 요소입니다.
