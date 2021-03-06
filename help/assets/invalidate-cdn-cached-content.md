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
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 1%

---

# CDN 캐시 콘텐츠 무효화 {#invalidating-your-cdn-cached-content}

Dynamic Media 자산은 CDN에 의해 캐시되어 빠른 전달을 제공합니다. 그러나 자산을 업데이트할 때 이러한 변경 사항을 즉시 적용할 수 있습니다. CDN(Content Delivery Network) 캐시 콘텐츠를 무효화하면 캐시가 만료될 때까지 기다리는 대신 Dynamic Media에서 제공하는 자산을 빠르게 업데이트할 수 있습니다.

Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html)에서 [캐시 개요 를 참조하십시오.

**CDN 캐시 컨텐츠를 무효화하려면:**

1. Dynamic Media Classic 데스크탑 애플리케이션에 로그인합니다.

   [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)

   자격 증명과 로그온은 프로비저닝 시 Adobe에서 제공되었습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.

1. **[!UICONTROL 설정 > 응용 프로그램 설정 > 일반 설정]**&#x200B;을 클릭합니다.
1. 응용 프로그램 일반 설정 페이지의 서버 그룹 제목 아래에서 **[!UICONTROL CDN 무효화 템플릿]** 텍스트 상자를 찾습니다.

1. CDN(Content Delivery Network) 캐시를 무효화하는 데 사용되는 템플릿을 지정합니다.

   예를 들어 다음 예제와 같이 특정 이미지 ID 대신 `<ID>`을 참조하는 이미지 URL(이미지 사전 설정 또는 수정자 포함)을 입력한다고 가정합니다.

   `https://server.com/is/image/Company/<ID>?$product$`

   템플릿에 `<ID>`만 포함되어 있으면 Dynamic Media은 `https://<server>/is/image`로 채워집니다. 여기서 `<server>`는 일반 설정에 정의된 게시 서버 이름이고 &lt;ID>는 무효화되도록 선택한 자산입니다.

1. 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 닫기]**&#x200B;를 클릭합니다.
1. Dynamic Media Classic 데스크탑 애플리케이션의 사용자 인터페이스에서 자산을 한 개 이상 선택한 다음 **[!UICONTROL 파일 > CDN 무효화]**&#x200B;를 클릭합니다. 만든 템플릿과 선택한 자산에서 생성된 하나 이상의 URL 목록이 표시됩니다. 응용 프로그램 일반 설정 아래의 &quot;게시된 서버 이름&quot; 아래에 나열된 서버 URL을 사용합니다.

   예를 들어 이전 단계에서 CDN 무효화 템플릿 을 설정한 경우 `Backpack_B` 이라는 단일 이미지 자산 이미지를 선택했다고 가정해 보겠습니다. **[!UICONTROL 파일 > CDN 무효화]**&#x200B;를 클릭하면 CDN 무효화 사용자 인터페이스에 다음 생성 URL이 생성됩니다.

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. URL 목록 상자에서 **[!UICONTROL 계속]**&#x200B;을 클릭하여 각 특정 URL에 대한 캐시를 지웁니다. URL을 편집하거나 URL 목록 상자에 URL을 입력하거나 붙여넣어 URL을 추가할 수 있습니다. cdn 무효화 템플릿을 미리 설정할 필요가 없습니다.

   **[!UICONTROL 계속]**&#x200B;을 클릭하면 캐시를 지우는 데 걸리는 시간을 예상할 수 있는 표시기가 표시됩니다.

   여러 자산을 선택한 다음 **[!UICONTROL 파일 > CDN 무효화]**&#x200B;를 클릭한 경우, 각 자산은 저장된 **[!UICONTROL 템플릿 URL]**&#x200B;에서 참조됩니다. 따라서 웹 사이트에서 참조되는 각 URL 이미지 사전 설정을 참조하는 **[!UICONTROL CDN Invalidate Template]**&#x200B;을 정의할 수 있습니다(예: 제품 세부 사항, 검색 결과 등). 그런 다음 캐시에서 무효화에 사용할 이미지를 선택하면 URL이 자동으로 인터페이스를 채웁니다.

   >[!NOTE]
   >
   >자산을 선택한 다음 **[!UICONTROL 파일 > CDN 무효화]**&#x200B;를 클릭하면, Dynamic Media은 CDN 템플릿을 사용하여 CDN(Content Delivery Network)에서 무효화할 URL을 자동으로 만듭니다. **[!UICONTROL CDN 템플릿 무효화]** 텍스트 상자에 아무 것도 없으면 빈 URL 목록이 표시됩니다. CDN의 캐싱은 자산 기반이 아닙니다. URL을 기반으로 합니다. 따라서 웹 사이트에 있는 전체 URL을 알고 있어야 합니다. 이러한 URL을 결정한 후 단계 앞부분에서 **[!UICONTROL CDN 템플릿 무효화]** 텍스트 상자에 추가할 수 있습니다. 그런 다음 해당 자산을 선택하고 한 단계에서 URL을 무효화할 수 있습니다.
   >
   >다른 옵션은 전체 URL을 **[!UICONTROL CDN 무효화]** 목록에 추가하는 것입니다. 이 접근 방식을 따르는 경우 **[!UICONTROL 파일 > CDN 무효화]** 옵션으로 이동하기 전에 Dynamic Media Classic에서 자산을 선택할 필요가 없습니다.
