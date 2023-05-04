---
title: 파노라마 이미지
description: Dynamic Media에서 파노라마 이미지로 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 5%

---

# 파노라마 이미지 {#panoramic-images}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 섹션에서는 공간, 속성, 위치 또는 조경의 몰입형 360° 보기 환경을 위해 파노라마 뷰어를 사용하여 구형 파노라마 이미지를 렌더링하는 방법에 대해 설명합니다.

참조 - [뷰어 사전 설정 관리](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## 파노라마 이미지 뷰어에서 사용할 자산 업로드 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

업로드된 자산이 파노라마 이미지 뷰어와 함께 사용할 구형 파노라마 이미지로 분류되도록 하려면 자산에 다음 중 하나 또는 둘 다 있어야 합니다.

* 2 종횡비입니다.

   기본 종횡비 설정인 2를 재정의할 수 있습니다 **[!UICONTROL CRXDE Lite]** 다음을 수행하십시오.

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* 키워드가 태그됨 `equirectangular`, 또는 `spherical`및 `panorama`, 또는 `spherical` 및 `panoramic`. 자세한 내용은 [태그 사용](/help/sites-authoring/tags.md).

Both the aspect ratio and keyword criteria apply to panoramic assets for the asset details page and the **[!UICONTROL Panoramic Media]** component.

파노라마 이미지 뷰어에 사용할 자산을 업로드하려면 를 참조하십시오 [자산 업로드](managing-assets-touch-ui.md#uploading-assets).

## Dynamic Media Classic 구성 {#configuring-dynamic-media-classic-scene}

파노라마 이미지 뷰어가 AEM 내에서 제대로 작동하려면 JCR에서 뷰어 사전 설정이 업데이트되도록 Dynamic Media Classic 및 Dynamic Media Classic 관련 메타데이터와 파노라마 이미지 뷰어 사전 설정을 동기화해야 합니다. 이를 수행하려면 다음 방법으로 Dynamic Media Classic을 구성하십시오.

1. [Dynamic Media Classic 데스크탑 애플리케이션에 로그인](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) 각 회사 계정에 대해

1. 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 설정 > 애플리케이션 설정 > 게시 설정 > 이미지 서버]**.
1. 설정 **[!UICONTROL 이미지 서버 게시]** 페이지, **[!UICONTROL 게시 컨텍스트]** 상단 근처에 있는 드롭다운 메뉴에서 **[!UICONTROL 이미지 제공]**.

1. 동일한 **[!UICONTROL 이미지 서버 게시]** 페이지에서 제목을 찾습니다 **[!UICONTROL 요청 속성]**.
1. 아래에 **[!UICONTROL 요청 속성]** 제목, 위치 **[!UICONTROL 회신 이미지 크기 제한]**. 그런 다음 연결된 **[!UICONTROL 너비]** 및 **[!UICONTROL 높이]** 필드에서 파노라마 이미지에 사용할 수 있는 최대 이미지 크기를 늘립니다.

   Dynamic Media Classic은 25,000,000픽셀로 제한됩니다. 2:1 종횡비를 갖는 이미지의 최대 허용 크기는 7000 x 3500입니다. 그러나 일반적인 데스크탑 화면의 경우 4096 x 2048 픽셀로도 충분합니다.

   >[!NOTE]
   >
   >허용되는 최대 이미지 크기에 해당하는 이미지만 지원됩니다. 크기 제한을 초과하는 이미지에 대한 요청은 403 응답을 생성합니다.

1. 아래에 **[요청 속성]** 제목, 다음을 수행합니다.

   * 설정 **[!UICONTROL 요청 난독화 모드]** to **[!UICONTROL 비활성화됨]**.
   * 설정 **[!UICONTROL 요청 잠금 모드]** to **[!UICONTROL 비활성화됨]**.

   이러한 설정은 **[!UICONTROL 파노라마 미디어]** 구성 요소를 생성하지 않습니다.

1. 아래쪽에서 **[!UICONTROL 이미지 서버 게시]** 페이지의 왼쪽에서 **[!UICONTROL 저장]**.

1. 오른쪽 아래 모서리에서 **[!UICONTROL 닫기]**.

### 파노라마 미디어 구성 요소 문제 해결 {#troubleshooting-the-panoramic-media-wcm-component}

이미지를 **[!UICONTROL 파노라마 미디어]** 구성 요소가 축소되고 구성 요소 자리 표시자가 축소되면 다음 문제를 해결할 수 있습니다.

* 403 금지된 오류가 발생한 경우 요청된 이미지 크기가 너무 커서 오류가 발생했을 수 있습니다. 를 검토합니다. *회신 이미지 크기 제한* 설정 [Dynamic Media Classic 구성](#configuring-dynamic-media-classic-scene).

* 대상 *잘못된 잠금* 또는 *구문 분석 오류* 페이지에 표시된 다음 **[!UICONTROL 요청 난독화 모드]** 및 **[!UICONTROL 요청 잠금 모드]** 비활성화되어 있는지 확인하십시오.
* 오염된 캔버스 오류에 대해 다음을 설정하십시오. **[!UICONTROL 규칙 세트 정의 파일 경로 및 CTN 무효화]** 이미지 자산에 대한 이전 요청의 경우
* 지원되는 제한을 초과하는 크기 조정을 갖는 이미지 요청 이후에 이미지 품질이 매우 낮은 경우 **[!UICONTROL JPEG 인코딩 속성 > 품질]** 설정이 비어 있지 않습니다. 에 대한 일반적인 설정 **[!UICONTROL 품질]** 필드: `95`. 에서 설정을 찾을 수 있습니다. **[!UICONTROL 이미지 서버 게시]** 페이지. 페이지에 액세스하려면 다음을 참조하십시오 [Dynamic Media Classic 구성](#configuring-dynamic-media-classic-scene).

## 파노라마 이미지 미리 보기 {#previewing-panoramic-images}

자세한 내용은 [자산 미리 보기](previewing-assets.md).

## 파노라마 이미지 게시 {#publishing-panoramic-images}

자세한 내용은 [자산 게시](publishing-dynamicmedia-assets.md).
