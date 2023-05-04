---
title: Dynamic Media 자산 제공
seo-title: Delivering Dynamic Media Assets
description: 다이내믹 미디어 자산을 제공하는 방법을 알아봅니다
seo-description: Learn how to deliver dynamic media assets
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 23%

---

# Dynamic Media 자산 제공 {#delivering-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다이내믹 미디어 자산(비디오와 이미지 모두)을 제공할 수 있는 방법은 웹 사이트가 구현되는 방식에 따라 다릅니다.

Dynamic Media을 사용하면 다음과 같은 몇 가지 옵션이 있습니다.

* 웹 사이트가 AEM에서 호스팅되는 경우 Dynamic Media 자산을 페이지에 바로 추가할 수 있습니다.
* 웹 사이트가 AEM에 없는 경우 다음 중 하나를 선택할 수 있습니다.

   * 웹 사이트에 비디오 또는 이미지를 포함합니다.
   * 웹 애플리케이션에 URL 연결. 비디오 플레이어를 팝업 또는 모달 창으로 전달하려는 경우 링크를 사용합니다.
   * 사이트가 응답형인 경우 [최적화된 이미지를 제공합니다.](responsive-site.md)

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정에서 작동하며 마지막 전달 순간에 인텔리전스를 사용하여 브라우저 또는 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다. 자세한 내용은 [스마트 이미징](imaging-faq.md) 추가 정보.

자세한 내용은 다음 주제를 참조하십시오.

* [웹 페이지에 Dynamic Media 자산 추가](adding-dynamic-media-assets-to-pages.md)
* [웹 페이지에 비디오 또는 이미지 뷰어 포함](embed-code.md)
* [Dynamic Media에서 핫링크 보호 활성화](https://helpx.adobe.com/kr/experience-manager/6-4/assets/using/hotlink-protection.html)
* Dynamic Media과 디지털 비표시 워터마크(Digimarc) 통합(준비 중)
* [URL을 웹 애플리케이션에 연결](linking-urls-to-yourwebapplication.md)
* [응답형 사이트용으로 최적화된 이미지 제공](responsive-site.md)
* [컨텐츠의 HTTP2 전달](http2.md)
* [CDN 캐시 콘텐츠 무효화](invalidate-cdn-cached-content.md)
* [규칙 세트를 사용하여 URL 변환](using-rulesets-to-transform-urls.md)

## Dynamic Media 자산의 HTTP/2 전달 {#http-delivery-of-dynamic-media-assets}

이제 AEM에서는 HTTP/2를 통해 모든 Dynamic Media 컨텐츠(이미지 및 비디오)의 전달을 지원합니다. 즉, 이미지나 비디오에 대해 게시된 URL 또는 포함 코드는 호스팅된 자산을 허용하는 모든 애플리케이션과 통합할 수 있습니다. 게시된 자산은 HTTP/2 프로토콜을 통해 전달됩니다. 이 전달 방법은 브라우저 및 서버의 통신 방식을 개선하여 모든 Dynamic Media 자산의 응답 및 로드 시간을 향상시킬 수 있습니다.

자세한 내용은 [컨텐츠의 HTTP/2 전달 FAQ](/help/sites-administering/scene7-http2faq.md) 추가 정보
