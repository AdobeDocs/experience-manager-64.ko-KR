---
title: Dynamic Media 자산 제공
seo-title: Dynamic Media 자산 제공
description: 다이내믹 미디어 에셋을 제공하는 방법 학습
seo-description: 다이내믹 미디어 에셋을 제공하는 방법 학습
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 33%

---


# Dynamic Media 자산 제공 {#delivering-dynamic-media-assets}

비디오 및 이미지 등 다이내믹 미디어 자산을 제공하는 방법은 웹 사이트 구현 방법에 따라 다릅니다.

Dynamic Media에는 다음의 몇 가지 선택 사항이 있습니다.

* 웹 사이트가 AEM에서 호스팅된다면, 다이내믹 미디어 자산을 페이지에 바로 추가할 수 있습니다.
* 웹 사이트가 AEM에 없다면 다음 중 하나를 선택할 수 있습니다.

   * 웹 사이트에 비디오 또는 이미지 임베드
   * 웹 응용 프로그램에 URL을 연결합니다. 비디오 플레이어를 팝업 또는 모달 창으로 제공하려는 경우 링크를 사용합니다.
   * 사이트가 응답형인 경우 [최적화된 이미지를 제공할 수 있습니다.](responsive-site.md)

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정에서 작동하며 마지막 전달 순간에 인텔리전스를 사용하여 브라우저 또는 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다. 자세한 내용은 [스마트 이미징](imaging-faq.md)을 참조하십시오.

자세한 내용은 다음 항목을 참조하십시오.

* [웹 페이지에 Dynamic Media 자산 추가](adding-dynamic-media-assets-to-pages.md)
* [웹 페이지에 비디오 또는 이미지 뷰어 포함](embed-code.md)
* [Dynamic Media에서 핫링크 보호 활성화](https://helpx.adobe.com/experience-manager/6-4/assets/using/hotlink-protection.html)
* 디지털 보이지 않는 워터마크(Digimarc)와 Dynamic Media 통합(준비 중)
* [URL을 웹 애플리케이션에 연결](linking-urls-to-yourwebapplication.md)
* [응답형 사이트용으로 최적화된 이미지 제공](responsive-site.md)
* [컨텐츠의 HTTP2 전달](http2.md)
* [CDN 캐시 콘텐츠 무효화](invalidate-cdn-cached-content.md)
* [규칙 세트를 사용하여 URL 변환](using-rulesets-to-transform-urls.md)

## Dynamic Media 에셋 {#http-delivery-of-dynamic-media-assets} HTTP/2 전달

AEM은 이제 HTTP/2를 통해 모든 Dynamic Media 컨텐츠(이미지 및 비디오)를 전달할 수 있습니다. 즉, 이미지 또는 비디오에 대해 게시된 URL 또는 포함 코드는 호스팅된 자산을 허용하는 모든 응용 프로그램과 통합할 수 있습니다. 이렇게 게시된 자산은 HTTP/2 프로토콜을 통해 전달됩니다. 이 방식의 전달은 브라우저 및 서버의 통신 방식을 개선하여 모든 Dynamic Media 에셋에 대한 응답 및 로드 시간을 향상시킵니다.

자세한 내용은 [HTTP/2 FAQ 배달](/help/sites-administering/scene7-http2faq.md)을 참조하십시오.
