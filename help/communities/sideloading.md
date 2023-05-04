---
title: 구성 요소 테스트로드
seo-title: Component Sideloading
description: 커뮤니티 구성 요소 테스트로드는 웹 페이지가 사이트 방문자가 선택한 내용에 따라 표시되는 내용을 동적으로 변경하는 간단한 단일 페이지 앱으로 디자인될 때 유용합니다
seo-description: Communities component sideloading is useful when a web page is designed as a simple, single page app that dynamically alters what is displayed depending on what is selected by the site visitor
uuid: 8c9a5fde-26a3-4610-bc14-f8b665059015
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9cb5294-e5ab-445b-b7c2-ffeecda91c50
exl-id: 12fdc503-29b6-4970-a883-c22162f7a9eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 2%

---

# 구성 요소 테스트로드 {#component-sideloading}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

커뮤니티 구성 요소 테스트로드는 웹 페이지가 사이트 방문자가 선택한 내용에 따라 표시되는 내용을 동적으로 변경하는 간단한 단일 페이지 앱으로 디자인될 때 유용합니다.

이 작업은 커뮤니티 구성 요소가 페이지 템플릿에 없을 때 수행되지만 사이트 방문자가 선택한 후에 대신 동적으로 추가됩니다.

SCF(소셜 구성 요소 프레임워크)가 가볍기 때문에 초기 페이지 로드 시 존재하는 SCF 구성 요소만 등록됩니다. 페이지 로드 후 동적으로 추가된 SCF 구성 요소를 등록하려면 구성 요소의 &quot;사이드로드&quot;에 SCF를 호출해야 합니다.

페이지가 커뮤니티 구성 요소를 테스트하도록 디자인되면 전체 페이지를 캐시할 수 있습니다.

SCF 구성 요소를 동적으로 추가하는 단계는 다음과 같습니다.

1. [DOM에 구성 요소 추가](#dynamically-add-component-to-dom)

1. [구성 요소를 테스트하여 로드합니다](#sideload-by-invoking-scf) 다음 두 방법 중 하나를 사용합니다.

* [동적 포함](#dynamic-inclusion)
   * 동적으로 추가된 모든 구성 요소를 부트스트랩
* [동적 로드](#dynamic-loading)
   * 온디맨드 한 개의 특정 구성 요소 추가

>[!NOTE]
>
>테스트용 로드 [비기존 리소스](scf.md#add-or-include-a-communities-component) 은 지원되지 않습니다.

## 동적으로 DOM에 구성 요소 추가 {#dynamically-add-component-to-dom}

구성 요소가 동적으로 포함되거나 동적으로 로드되는지 여부에 관계없이 먼저 DOM에 추가해야 합니다.

SCF 구성 요소를 추가할 때 사용하는 가장 일반적인 태그는 DIV 태그이지만 다른 태그도 사용할 수 있습니다. SCF는 페이지가 처음 로드될 때 DOM만 검사하므로, SCF가 명시적으로 호출될 때까지 DOM에 대한 이러한 추가는 간과되지 않습니다.

어떤 태그를 사용하든, 적어도 이러한 두 속성을 포함함으로써 요소는 일반적인 SCF 루트 요소 패턴을 준수해야 합니다.

* **data-component-id**
추가된 구성 요소의 유효 경로

* **data-scf-component**
구성 요소의 resourceType

다음은 추가된 댓글 구성 요소의 한 예입니다.

```xml
<div
    class="scf-commentsystem scf translation-commentsystem" 
    data-component-id="<%= currentPage.getPath()%>/jcr:content/content-left/comments"
    data-scf-component="social/commons/components/hbs/comments"
>
</div>
```

## SCF를 호출하여 테스트용 로드 {#sideload-by-invoking-scf}

### 동적 포함 {#dynamic-inclusion}

동적 포함에서는 SCF가 페이지에 있는 모든 SCF 구성 요소를 부트하고 DOM을 검사하는 부스트랩 요청을 사용합니다.

페이지 로드 후 언제든지 SCF 구성 요소를 초기화하려면 다음과 같이 JQuery 이벤트를 실행하면 됩니다.

$(document).trigger(SCF.events.BOOTSTRAP_REQUEST);

### 동적 로드 {#dynamic-loading}

동적 로드는 SCF 구성 요소 로드를 제어할 수 있도록 합니다.

DOM에 있는 모든 SCF 구성 요소를 부트스트랩하는 대신 이 JavaScript 메서드를 사용하여 로드할 특정 SCF 구성 요소를 지정할 수 있습니다.

SCF.addComponent(document.getElementById()*someId*));

위치 *someId* 는 의 값입니다 **data-component-id** 속성을 사용합니다.
