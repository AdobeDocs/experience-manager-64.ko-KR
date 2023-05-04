---
title: 웹 페이지에 Dynamic Media 비디오 또는 이미지 뷰어 포함
seo-title: Embedding the Dynamic Media Video or Image viewer on a web page
description: 웹 페이지에 Dynamic Media 비디오 또는 이미지를 포함하는 방법을 알아봅니다
seo-description: Learn how to embed Dynamic media video or images on a web page
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
exl-id: bff564a8-e982-4e1a-a9b5-05e44e3e4d46
feature: Components
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 22%

---

# 웹 페이지에 Dynamic Media 비디오 또는 이미지 뷰어 포함 {#embedding-the-video-or-image-viewer-on-a-web-page}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Use the **[!UICONTROL Embed Code]** feature when you want to play the video or view an asset embedded on a web page. You copy the embed code to the clipboard so you can paste it in your web pages. Editing of the code is not permitted in the **[!UICONTROL Embed Code]** dialog box.

다음과 같은 경우에만 URL을 포함합니다 _not_ 사용 [!DNL Experience Manager] WCM으로 사용할 수 있습니다. 사용 중인 경우 [!DNL Experience Manager] WCM으로, [자산을 페이지에 직접 추가합니다.](adding-dynamic-media-assets-to-pages.md)

자세한 내용은 [URL을 웹 애플리케이션에 연결합니다.](linking-urls-to-yourwebapplication.md)

자세한 내용은 [응답형 사이트용으로 최적화된 이미지 제공.](responsive-site.md)

>[!NOTE]
>
>선택한 자산을 게시하기 전까지는 포함 코드를 복사할 수 없습니다. 또한 뷰어 사전 설정 또는 이미지 사전 설정도 게시해야 합니다.
>
>자세한 내용은 [자산 게시](publishing-dynamicmedia-assets.md).
>
>자세한 내용은 [뷰어 사전 설정 게시](managing-viewer-presets.md#publishing-viewer-presets).
>
>자세한 내용은 [이미지 사전 설정 게시](managing-image-presets.md#publishing-image-presets).

**웹 페이지에 Dynamic Media 비디오 또는 이미지 뷰어를 포함하려면**:

1. 로 이동합니다 *게시됨* 포함 코드를 복사할 비디오 또는 이미지 자산입니다.

   Remember that the embed code is only available to copy *after* you have first *published* the assets. In addition, the viewer preset or image preset must also be published.

   자세한 내용은 [자산 게시.](publishing-dynamicmedia-assets.md)

   자세한 내용은 [뷰어 사전 설정 게시](managing-viewer-presets.md#publishing-viewer-presets).

   자세한 내용은 [이미지 사전 설정 게시](managing-image-presets.md#publishing-image-presets).

1. 왼쪽 레일에서 드롭다운 메뉴를 선택하고 을 누릅니다 **[!UICONTROL 뷰어]**.
1. 왼쪽 레일에서 뷰어 사전 설정 이름을 탭합니다. 뷰어 사전 설정이 자산에 적용됩니다.
1. 탭 **[!UICONTROL 포함]**.
1. 에서 **[!UICONTROL 포함 코드]** 대화 상자에서 전체 코드를 클립보드에 복사한 다음 **[!UICONTROL 닫기]**.
1. 포함 코드를 웹 페이지에 붙여넣습니다.

## HTTP/2를 사용하여 Dynamic Media 자산 전달 {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2는 브라우저 및 서버의 통신 방식을 향상시키는 업데이트된 새로운 웹 프로토콜입니다. 보다 신속하게 정보를 전송할 수 있고 필요한 처리 능력을 줄일 수 있습니다. 이제 Dynamic Media 자산의 배달이 HTTP/2를 통해 수행될 수 있으므로 로드 시간이 향상됩니다.

자세한 내용은 [컨텐츠의 HTTP2 전달](http2.md) Dynamic Media 계정으로 HTTP/2 사용을 시작하는 방법에 대한 전체 세부 사항을 살펴보십시오.
