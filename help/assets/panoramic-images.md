---
title: 파노라마 이미지
description: Dynamic Media에서 파노라마 이미지로 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: 파노라마 이미지
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 1%

---

# 파노라마 이미지 {#panoramic-images}

이 섹션에서는 공간, 속성, 위치 또는 조경의 몰입형 360° 보기 환경을 위해 파노라마 뷰어를 사용하여 구형 파노라마 이미지를 렌더링하는 방법에 대해 설명합니다.

또한 [뷰어 사전 설정 관리](managing-viewer-presets.md)를 참조하십시오.

![파노라마 이미지2](assets/panoramic-image2.png)

## 파노라마 이미지 뷰어에서 사용할 자산 업로드 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

업로드된 자산이 파노라마 이미지 뷰어와 함께 사용할 구형 파노라마 이미지로 분류되도록 하려면 자산에 다음 중 하나 또는 둘 다 있어야 합니다.

* 2 종횡비입니다.

   다음 위치에서 **[!UICONTROL CRXDE Lite]**&#x200B;에서 기본 종횡비 설정 2를 무시할 수 있습니다.

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* `equirectangular` 또는 `spherical`와 `panorama`, 또는 `spherical` 및 `panoramic` 키워드가 태그되었습니다. [태그 사용](/help/sites-authoring/tags.md)을 참조하십시오.

종횡비와 키워드 기준은 모두 자산 세부 사항 페이지와 **[!UICONTROL 파노라마 미디어]** 구성 요소의 파노라마 자산에 적용됩니다.

파노라마 이미지 뷰어에서 사용할 자산을 업로드하려면 [자산 업로드](managing-assets-touch-ui.md#uploading-assets)를 참조하십시오.

## Dynamic Media Classic 구성 {#configuring-dynamic-media-classic-scene}

파노라마 이미지 뷰어가 AEM 내에서 제대로 작동하려면 JCR에서 뷰어 사전 설정이 업데이트되도록 Dynamic Media Classic 및 Dynamic Media Classic 관련 메타데이터와 파노라마 이미지 뷰어 사전 설정을 동기화해야 합니다. 이를 수행하려면 다음 방법으로 Dynamic Media Classic을 구성하십시오.

1. [각 회사 계정의 Dynamic Media Classic 데스크탑 ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) 애플리케이션에 로그인합니다.

1. 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 설정 > 애플리케이션 설정 > 게시 설정 > 이미지 서버]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 이미지 서버 게시]** 페이지의 맨 위에 있는 **[!UICONTROL 게시 컨텍스트]** 드롭다운 메뉴에서 **[!UICONTROL 이미지 제공]**&#x200B;을 선택합니다.

1. 동일한 **[!UICONTROL 이미지 서버 게시]** 페이지에서 **[!UICONTROL 요청 속성]** 제목을 찾습니다.
1. **[!UICONTROL 요청 속성]** 제목 아래에서 **[!UICONTROL 회신 이미지 크기 제한]**&#x200B;을 찾습니다. 그런 다음 연결된 **[!UICONTROL Width]** 및 **[!UICONTROL Height]** 필드에서 파노라마 이미지에 사용할 수 있는 최대 이미지 크기를 늘립니다.

   Dynamic Media Classic의 제한 픽셀은 25,000,000픽셀입니다. 2:1 종횡비를 갖는 이미지의 최대 허용 크기는 7000 x 3500입니다. 그러나 일반적인 데스크탑 화면의 경우 4096 x 2048 픽셀로도 충분합니다.

   >[!NOTE]
   >
   >허용되는 최대 이미지 크기에 해당하는 이미지만 지원됩니다. 크기 제한을 초과하는 이미지에 대한 요청은 403 응답을 생성합니다.

1. **[요청 속성]** 제목 아래에서 다음을 수행합니다.

   * **[!UICONTROL 요청 난독화 모드]**&#x200B;를 **[!UICONTROL Disabled]**&#x200B;로 설정합니다.
   * **[!UICONTROL 요청 잠금 모드]**&#x200B;를 **[!UICONTROL Disabled]**&#x200B;로 설정합니다.

   이러한 설정은 AEM에서 **[!UICONTROL 파노라마 미디어]** 구성 요소를 사용하는 데 필요합니다.

1. **[!UICONTROL 이미지 서버 게시]** 페이지 하단의 왼쪽의 **[!UICONTROL 저장]**&#x200B;을 탭합니다.

1. 오른쪽 아래 모서리에서 **[!UICONTROL 닫기]**&#x200B;를 탭합니다.

### 파노라마 미디어 구성 요소 문제 해결 {#troubleshooting-the-panoramic-media-wcm-component}

이미지를 WCM의 **[!UICONTROL 파노라마 미디어]** 구성 요소에 끌어다 놓고 구성 요소 자리 표시자가 축소된 경우 다음 문제를 해결할 수 있습니다.

* 403 금지된 오류가 발생한 경우 요청된 이미지 크기가 너무 커서 오류가 발생했을 수 있습니다. [Dynamic Media Classic 구성](#configuring-dynamic-media-classic-scene)에서 *회신 이미지 크기 제한* 설정을 검토하십시오.

* 자산의 *잘못된 잠금* 또는 페이지에 표시된 *구문 분석 오류*&#x200B;에 대해서는 **[!UICONTROL 요청 난독화 모드]** 및 **[!UICONTROL 요청 잠금 모드]**&#x200B;가 비활성화되어 있는지 확인하십시오.
* 오염된 캔버스 오류에 대해 이미지 자산에 대한 이전 요청에 대해 **[!UICONTROL 규칙 세트 정의 파일 경로를 설정하고 CTN]**&#x200B;을 무효화합니다.
* 이미지 요청의 크기가 지원되는 제한보다 큰 경우 이미지 요청이 발생하면 **[!UICONTROL JPEG 인코딩 속성 > 품질]** 설정이 비어 있지 않은지 확인하십시오. **[!UICONTROL Quality]** 필드에 대한 일반적인 설정은 `95`입니다. **[!UICONTROL 이미지 서버 게시]** 페이지에서 설정을 찾을 수 있습니다. 페이지에 액세스하려면 [Dynamic Media Classic 구성](#configuring-dynamic-media-classic-scene)을 참조하십시오.

## 파노라마 이미지 미리 보기 {#previewing-panoramic-images}

[자산 미리 보기](previewing-assets.md)를 참조하십시오.

## 파노라마 이미지 게시 {#publishing-panoramic-images}

[자산 게시](publishing-dynamicmedia-assets.md)를 참조하십시오.
