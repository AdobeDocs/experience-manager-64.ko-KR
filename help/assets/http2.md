---
title: 컨텐츠의 HTTP2 전달
seo-title: 컨텐츠의 HTTP2 전달
description: HTTP/2는 브라우저 및 서버의 통신 방식을 개선하여 정보를 더 빨리 전송하면서도 필요한 처리 능력을 줄일 수 있습니다.
seo-description: HTTP/2는 브라우저 및 서버의 통신 방식을 개선하여 정보를 더 빨리 전송하면서도 필요한 처리 능력을 줄일 수 있습니다.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
exl-id: 59cd9f8c-6d01-448d-bf57-bdc9fd2e381b
feature: 자산 관리
role: Administrator,Business Practitioner
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 3%

---

# 컨텐츠의 HTTP2 전달 {#http-delivery-of-content}

Adobe에서는 전반적인 성능이 개선된 HTTP/2 컨텐츠 제공을 발표하게 되었습니다.

## HTTP/2란?{#what-is-http}

HTTP/2는 브라우저 및 서버의 통신 방식을 개선하여 정보를 더 빨리 전송하면서도 필요한 처리 능력을 줄일 수 있습니다.

다음 웹 사이트에서는 HTTP/2 및 그 이점을 간략하게 설명합니다.

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## 컨텐츠 전달을 위해 HTTP/2로 이동하여 얻을 수 있는 주요 이점은 무엇입니까?{#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

성능 향상은 웹 사이트의 코드, Dynamic Media 사용 방법, 소비자의 장치, 화면 및 위치 등과 같은 요인에 따라 광범위하게 달라집니다.

Adobe의 자체 테스트에서는 다음 결과가 도출되었습니다.

* 이미지의 경우 응답 시간이 장치 및 브라우저에 따라 7%~28% 개선되었습니다. 가장 주목할 만한 성능 향상은 iOS 장치였습니다.
* 뷰어의 경우 로드 시간 성능이 15% 향상되었습니다.

다음 데모에서는 HTTP/1과 HTTP/2 로드 간의 차이점을 보여 줍니다.

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## HTTP/2로 전환할 수 있습니까?{#am-i-eligible-to-switch-over-to-http}

HTTP/2를 사용하려면 다음 요구 사항을 충족해야 합니다.

* 리치 미디어 요청에 보안 HTTPS를 사용합니다.
* Dynamic Media 라이센스의 일부로 Adobe 번들 CDN(컨텐츠 전달 네트워크)을 사용합니다.
* 전용(company-h.assetsadobe#.com) 도메인을 사용합니다.

   이미 전용 도메인이 있는 경우 기술 지원을 통해 옵트인할 수 있습니다.

   전용 도메인이 없는 경우 Adobe이 2018년 HTTP/2로 전환을 예약합니다.

## Dynamic Media 계정에 대해 HTTP/2를 활성화하는 프로세스는 무엇입니까?{#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

HTTP/2로 전환하는 요청을 시작해야 합니다.자동으로 수행되지 않습니다.

1. HTTP2로 전환하려면 기술 지원 요청을 시작합니다. [AEM 지원 포털에 액세스](https://helpx.adobe.com/kr/experience-manager/kb/accessing-aem-support-portal.html)를 참조하십시오.

   1. 지원 요청에서 다음 정보를 제공합니다.

      1. 기본 연락처 이름, 이메일, 전화
      1. HTTP2로 전환할 모든 도메인.
      1. 리치 미디어 요청에 보안 HTTPS를 사용하고 있는지 확인합니다.
      1. Adobe을 통해 CDN을 사용하고 있으며 직접 관계로 관리되지 않는지 확인합니다.
      1. 전용 도메인을 사용하고 있는지 확인합니다. Dynamic Media을 사용하는 경우 이미 전용 도메인을 사용하고 있습니다.
   1. 기술 지원에서 요청을 제출한 순서에 따라 HTTP/2 고객 대기 목록에 추가합니다.
   1. Adobe이 요청을 처리할 준비가 되면 지원을 통해 전환을 조정하고 대상 날짜를 설정할 수 있습니다.
   1. 완료 후 알림을 받게 되며 HTTP2로 성공적으로 전환되었는지 확인할 수 있습니다.

      브라우저에 이 사실을 나타내지 않으므로 확장을 다운로드해야 합니다.

      Firefox 및 Chrome의 경우 &quot;HTTP/2 및 SPDY Indicator&quot;라는 확장이 있습니다. 브라우저는 http/2만 안전하게 지원하므로 확인하려면 https가 있는 URL을 호출해야 합니다. http/2가 지원되는 경우 확장이 파란색 Flash 기호 형태로 표시되고 헤더 &quot;X-Firefox-Spdy&quot; 가 표시됩니다.&quot;h2&quot;.


## 언제 HTTP/2로 전환할 수 있습니까?{#when-can-i-expect-to-be-transitioned-over-to-http}

요청은 기술 지원에서 수신하는 순서로 처리됩니다.

>[!NOTE]
>
>HTTP/2로 전환하면 캐시를 지워야 하므로 리드 타임이 오래 걸릴 수 있습니다. 따라서 한 번에 몇 개의 고객 전환만 처리할 수 있습니다.

## HTTP/2로 이동할 때 어떤 위험이 있습니까?{#what-are-the-risks-with-moving-to-http}

HTTP/2로 전환하면 새 CDN 구성으로 이동해야 하므로 CDN에서 캐시를 지웁니다.

캐싱되지 않은 컨텐츠는 캐시가 다시 빌드될 때까지 Adobe의 원본 서버에 직접 연결됩니다. 이러한 이유로 Adobe은 한 번에 몇 개의 고객 전환을 처리하여 오리진에서 요청을 가져올 때 허용 가능한 성능이 유지되도록 합니다.

## URL 또는 웹 사이트가 HTTP/2로 활성화되었는지 어떻게 확인할 수 있습니까?{#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

브라우저에 이 사실을 나타내지 않으므로 확장을 다운로드해야 합니다.

Firefox 및 Chrome의 경우 &quot;HTTP/2 및 SPDY Indicator&quot;라는 확장이 있습니다. 브라우저는 http/2만 안전하게 지원하므로 확인하려면 https가 있는 URL을 호출해야 합니다. http/2가 지원되는 경우 확장이 파란색 Flash 기호 형태로 표시되고 헤더 &quot;X-Firefox-Spdy&quot; 가 표시됩니다.&quot;h2&quot;.
