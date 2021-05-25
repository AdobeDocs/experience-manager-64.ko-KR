---
title: 커뮤니티 구성 요소용 Clientlibs
seo-title: 커뮤니티 구성 요소용 Clientlibs
description: Communities용 클라이언트 측 라이브러리
seo-description: Communities용 클라이언트 측 라이브러리
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 1%

---

# 커뮤니티 구성 요소용 Clientlibs {#clientlibs-for-communities-components}

## 소개 {#introduction}

설명서의 이 섹션에서는 커뮤니티 구성 요소의 페이지에 클라이언트측 라이브러리(clientlibs)를 추가하는 방법을 설명합니다.

기본 정보는 다음을 참조하십시오.

* [사용 세부 ](../../help/sites-developing/clientlibs.md) 사항과 디버깅 도구를 제공하는 클라이언트측 라이브러리 사용
* [SCF 구성 ](client-customize.md#clientlibs) 요소를 사용자 지정할 때 유용한 정보를 제공하는 SCF용 Clientlibs
* [블로그:예를 들어 AEM 클라이언트 라이브러리 설명](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Clientlibs가 필요한 이유 {#why-clientlibs-are-required}

Clientlibs는 구성 요소의 적절한 작동(JavaScript) 및 스타일(CSS)에 필요합니다.

기능에 대한 [커뮤니티 함수](functions.md)가 있으면 필요한 clientlibs를 포함한 필요한 모든 구성 요소 및 구성이 커뮤니티 사이트에 표시됩니다. 작성자가 추가 구성 요소를 사용할 수 있어야 clientlibs를 추가해야 합니다.

필요한 clientlibs가 없으면 [Communities 구성 요소를 페이지](author-communities.md)에 추가하면 Javascript 오류와 예기치 않은 모양새가 발생할 수 있습니다.

### 예:Clientlibs {#example-placed-reviews-without-clientlibs} 없이 검토함

![chlimage_1-244](assets/chlimage_1-244.png)

### 예:Clientlibs {#example-placed-reviews-with-clientlibs}과 함께 검토함

![chlimage_1-245](assets/chlimage_1-245.png)

## 필수 Clientlibs 식별 {#identifying-required-clientlibs}

개발자를 위한 필수 기능 정보는 필요한 clientlibs를 식별합니다.

또한 AEM 인스턴스에서 [커뮤니티 구성 요소 안내서](components-guide.md)로 이동하면 구성 요소에 필요한 clientlib 카테고리 목록에 액세스할 수 있습니다.

예를 들어, [검토 페이지](http://localhost:4502/content/community-components/en/reviews.html)의 맨 위에 나열된 필요한 clientlibs는 다음과 같습니다

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## 필수 Clientlibs 추가 {#adding-required-clientlibs}

페이지에 Communities 구성 요소를 추가하려면, 아직 없는 경우 구성 요소에 필요한 clientlibs를 추가해야 합니다.

커뮤니티 사이트 페이지에 대한 기존 clientlibslist를 수정하려면 [CRXDE|Lite](#using-crxde-lite) 를 사용하십시오.

[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)를 사용하여 커뮤니티 사이트에 대한 clientlib을 추가하려면:

* [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de) 로 이동합니다.
* 구성 요소를 추가할 페이지에 대한 `clientlibslist` 노드를 찾습니다

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* `clientlibslist` 노드를 선택한 상태에서

   * String[] 속성 `scg:requiredClientLibs` 찾기
   * `Value` 을 선택하여 문자열 배열 대화 상자에 액세스합니다

      * 필요한 경우 아래로 스크롤합니다.
      * `+` 을 선택하여 새 클라이언트 라이브러리를 입력합니다

         * 을 반복하여 클라이언트 라이브러리를 더 추가합니다
      * **[!UICONTROL 확인]** 선택
   * **[!UICONTROL 모두 저장]** 선택



>[!NOTE]
>
>사이트가 커뮤니티 사이트가 아닌 경우, 사이트에 대해 사용 중인 클라이언트 라이브러리의 존재 또는 위치를 검색해야 합니다.

[AEM Communities 시작하기](getting-started.md) 예를 사용합니다. 여기서 `site-name`는 *engage*&#x200B;입니다. 다음은 검토 구성 요소를 추가할 때 clientliblist가 표시되는 방식입니다.

![chlimage_1-247](assets/chlimage_1-247.png)
