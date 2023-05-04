---
title: 커뮤니티 구성 요소용 Clientlibs
seo-title: Clientlibs for Communities Components
description: Communities용 클라이언트 측 라이브러리
seo-description: Client-side libraries for Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 3%

---

# 커뮤니티 구성 요소용 Clientlibs {#clientlibs-for-communities-components}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

설명서의 이 섹션에서는 커뮤니티 구성 요소의 페이지에 클라이언트측 라이브러리(clientlibs)를 추가하는 방법을 설명합니다.

기본 정보는 다음을 참조하십시오.

* [클라이언트측 라이브러리 사용](../../help/sites-developing/clientlibs.md) 사용 세부 사항 및 디버깅 도구를 제공합니다.
* [SCF용 Clientlibs](client-customize.md#clientlibs) SCF 구성 요소를 사용자 지정할 때 유용한 정보를 제공합니다.

## Clientlibs가 필요한 이유 {#why-clientlibs-are-required}

Clientlibs는 구성 요소의 적절한 작동(JavaScript) 및 스타일(CSS)에 필요합니다.

가 있는 경우 [커뮤니티 기능](functions.md) 기능의 경우 필수 clientlibs를 포함한 필요한 모든 구성 요소 및 구성이 커뮤니티 사이트에 있을 것입니다. 작성자가 추가 구성 요소를 사용할 수 있어야 clientlibs를 추가해야 합니다.

필요한 clientlibs가 없으면 [페이지에 커뮤니티 구성 요소 추가](author-communities.md) 예기치 않은 모양일 뿐만 아니라 javascript 오류가 발생할 수 있습니다.

### 예: Clientlibs 없이 평가된 항목 {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### 예: Clientlibs를 사용하여 검토함 {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## 필수 Clientlibs 식별 {#identifying-required-clientlibs}

개발자를 위한 필수 기능 정보는 필요한 clientlibs를 식별합니다.

또한 AEM 인스턴스에서 [커뮤니티 구성 요소 안내서](components-guide.md) 구성 요소에 필요한 clientlib 카테고리 목록에 대한 액세스 권한을 제공합니다.

예를 들어, 맨 위의 [검토 페이지](http://localhost:4502/content/community-components/en/reviews.html) 나열된 필수 clientlibs는 다음과 같습니다

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## 필수 Clientlibs 추가 {#adding-required-clientlibs}

페이지에 Communities 구성 요소를 추가하려면, 아직 없는 경우 구성 요소에 필요한 clientlibs를 추가해야 합니다.

사용 [CRXDE|Lite](#using-crxde-lite) 커뮤니티 사이트 페이지에 대한 기존 clientlibslist를 수정하려면

를 사용하여 커뮤니티 사이트에 대한 clientlib을 추가하려면 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 찾아보기 [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* 을(를) 찾습니다 `clientlibslist` 구성 요소를 추가할 페이지의 노드입니다

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* 사용 `clientlibslist` 노드 선택

   * 문자열 찾기[] 속성 `scg:requiredClientLibs`
   * 선택 `Value` 문자열 배열 대화 상자에 액세스하려면

      * 필요한 경우 아래로 스크롤합니다.
      * 선택 `+` 새 클라이언트 라이브러리를 입력하려면

         * 을 반복하여 클라이언트 라이브러리를 더 추가합니다
      * 선택 **[!UICONTROL 확인]**
   * 선택 **[!UICONTROL 모두 저장]**



>[!NOTE]
>
>사이트가 커뮤니티 사이트가 아닌 경우, 사이트에 대해 사용 중인 클라이언트 라이브러리의 존재 또는 위치를 검색해야 합니다.

사용 [AEM Communities 시작하기](getting-started.md) 예, 여기서 `site-name` is *참여*: 검토 구성 요소를 추가할 때 clientliblist가 표시되는 방식입니다.

![chlimage_1-247](assets/chlimage_1-247.png)
