---
title: CDN 캐시 콘텐츠 무효화
seo-title: Invalidating your CDN cached content
description: CDN(Content Delivery Network) 캐시 콘텐츠를 무효화하면 캐시가 만료될 때까지 기다리는 대신 Dynamic Media에서 제공하는 자산을 빠르게 업데이트할 수 있습니다.
seo-description: Invalidating your CDN (Content Delivery Network) cached content lets you quickly update assets that are delivered by Dynamic Media, instead of waiting for the cache to expire.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
exl-id: 335c7a78-a00f-451b-8e53-225830d429c6
feature: Asset Management,CDN Cache
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 28%

---

# CDN 캐시 콘텐츠 무효화 {#invalidating-your-cdn-cached-content}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Dynamic Media 자산은 CDN에 의해 캐시되어 빠른 전달을 제공합니다. 그러나 자산을 업데이트할 때 이러한 변경 사항을 즉시 적용할 수 있습니다. CDN(Content Delivery Network) 캐시 콘텐츠를 무효화하면 캐시가 만료될 때까지 기다리는 대신 Dynamic Media에서 제공하는 자산을 빠르게 업데이트할 수 있습니다.

참조 - [Dynamic Media Classic의 캐시 개요](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**CDN 캐시 컨텐츠를 무효화하려면:**

1. Dynamic Media Classic 데스크탑 애플리케이션에 로그인합니다.

   [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)

   자격 증명과 로그온은 프로비저닝 시 Adobe에서 제공되었습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.

1. Click **[!UICONTROL Setup > Application Setup > General Settings]**.
1. 응용 프로그램 일반 설정 페이지의 서버 그룹 머리글 아래에서 **[!UICONTROL CDN 무효화 템플릿]** 텍스트 상자

1. CDN(Content Delivery Network) 캐시를 무효화하는 데 사용되는 템플릿을 지정합니다.

   예를 들어 이미지 사전 설정 또는 수정자 등의 이미지 URL을 `<ID>`다음 예와 같이 특정 이미지 ID 대신

   `https://server.com/is/image/Company/<ID>?$product$`

   템플릿에 `<ID>`을 입력한 다음 Dynamic Media이 채워집니다 `https://<server>/is/image` 여기서 `<server>` 일반 설정에 정의된 게시 서버 이름입니다. &lt;id> 은 무효화하도록 선택한 자산입니다.

1. 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 닫기]**.
1. Dynamic Media Classic 데스크탑 애플리케이션의 사용자 인터페이스에서 자산을 한 개 이상 선택한 다음 를 클릭합니다 **[!UICONTROL 파일 > CDN 무효화]**. 만든 템플릿과 선택한 자산에서 생성된 하나 이상의 URL 목록이 표시됩니다. 응용 프로그램 일반 설정 아래의 &quot;게시된 서버 이름&quot; 아래에 나열된 서버 URL을 사용합니다.

   예를 들어 이전 단계에서 CDN 무효화 템플릿 을 설정한 경우 이름이 인 단일 이미지 자산 이미지를 선택했다고 가정합니다. `Backpack_B`. 를 클릭하면 **[!UICONTROL 파일 > CDN 무효화]** 이를 통해 CDN 무효화 사용자 인터페이스에 다음 생성 URL이 생성됩니다.

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. URL 목록 상자에서 **[!UICONTROL 계속]** 를 눌러 각 특정 URL에 대한 캐시를 지웁니다. URL을 편집하거나 URL 목록 상자에 URL을 입력하거나 붙여넣어 URL을 추가할 수 있습니다. cdn 무효화 템플릿을 미리 설정할 필요가 없습니다.

   을 클릭한 후 **[!UICONTROL 계속]**&#x200B;에 표시기가 표시되어 캐시를 지우는 데 걸리는 시간을 예상할 수 있습니다.

   If you selected multiple assets, then clicked **[!UICONTROL File > Invalidate CDN]**, each asset is referenced in the saved **[!UICONTROL Template URL]**. Therefore, you can define a **[!UICONTROL CDN Invalidate Template]** referencing each URL image preset that is referenced on your website (such as product detail, search results, and so forth). Then, when you select one or images for invalidation from cache, the URLs automatically populate the interface.

   >[!NOTE]
   >
   >When you select assets, and then click **[!UICONTROL File > Invalidate CDN]**, Dynamic Media uses an invalidate CDN template to automatically create URLs to invalidate from the Content Delivery Network (CDN). If there is nothing in the **[!UICONTROL CDN Invalidate Template]** text box, then you get a blank URL list. Caching at the CDN is not asset-based; it is URL-based. Therefore, it is necessary to be aware of the complete URLs that are on your website. After you determine those URLs, you can add them to the **[!UICONTROL Invalidate CDN Template]** text box earlier in the steps. Then, you can select those assets, and invalidate the URLs in one step.
   >
   >또 다른 옵션은 전체 URL을 **[!UICONTROL CDN 무효화]** 목록. 이 방법을 따르면, **[!UICONTROL 파일 > CDN 무효화]** 선택 사항입니다.
