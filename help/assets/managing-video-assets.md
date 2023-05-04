---
title: 비디오 에셋 관리
description: 비디오 자산을 업로드, 미리 보기, 주석 달기 및 게시하는 방법을 알아봅니다.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: User
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 10%

---

# 비디오 에셋 관리 {#managing-video-assets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets에서 비디오 자산을 관리하고 편집하는 방법을 알아봅니다. 또한 Dynamic Media 사용 라이센스가 있는 경우 [Dynamic Media 비디오 설명서](video.md).

## 비디오 자산 업로드 및 미리 보기 {#uploading-and-previewing-video-assets}

[!DNL Experience Manager] 자산은 확장 MP4를 사용하여 비디오 자산에 대한 미리 보기를 생성합니다. 자산의 형식이 MP4가 아닌 경우, FFmpeg 팩을 설치하여 미리 보기를 생성합니다. FFmpeg는 OGG 및 MP4 유형의 비디오 표현물을 만듭니다. 에서 이러한 표현물을 미리 볼 수 있습니다 [!DNL Experience Manager] 자산 사용자 인터페이스.

1. 디지털 자산 폴더 또는 하위 폴더에서 디지털 자산을 추가할 위치로 이동합니다.
1. 자산을 업로드하려면 을(를) 클릭하거나 탭합니다 **[!UICONTROL 만들기]** 도구 모음에서 를 선택한 다음 **[!UICONTROL 파일]**. 또는 자산 영역에 직접 놓습니다. 자세한 내용은 [자산 업로드](managing-assets-touch-ui.md#uploading-assets) 업로드 작업에 대한 자세한 정보입니다.
1. 카드 보기에서 비디오를 미리 보려면 **[!UICONTROL 재생]** 단추 사용.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   에서 비디오를 일시 중지하거나 재생할 수 있습니다 **[!UICONTROL 카드]** 보기 전용. 재생/일시 중지 단추는 다음에서 사용할 수 없습니다 **[!UICONTROL 목록]** 보기.

1. 탭하기 **[!UICONTROL 편집]** 카드의 아이콘을 클릭하여 **[!UICONTROL 세부 사항]** 보기.

   비디오는 브라우저의 기본 비디오 플레이어에서 재생됩니다. 비디오를 전체 화면으로 재생, 일시 정지, 볼륨 제어 및 확대/축소할 수 있습니다.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## 2GB보다 큰 자산을 업로드하도록 구성 {#configuration-to-upload-video-assets-that-are-larger-than-gb}

기본적으로 [!DNL Experience Manager] 파일 크기 제한으로 인해 2GB보다 큰 자산을 업로드할 수 없습니다. 그러나 CRXDE Lite으로 이동하여 아래에 노드를 만들어 이 제한을 덮어쓸 수 있습니다 `/apps` 디렉토리. 노드에는 동일한 노드 이름, 디렉토리 구조 및 이와 비교할 수 있는 노드 속성이 있어야 합니다.

추가 [!DNL Experience Manager] 자산 구성에서 다음 구성을 변경하여 큰 자산을 업로드합니다.

* 토큰 만료 시간을 늘립니다. 자세한 내용은 [!UICONTROL Adobe Granite CSRF 서블릿] 웹 콘솔에서 `https://[aem_server]:[port]/system/console/configMgr`. 자세한 내용은 [CSRF 보호](/help/sites-developing/csrf-protection.md).
* 를 늘립니다 `receiveTimeout` 참조하십시오. 자세한 내용은 [Experience Manager Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>다음 [!DNL Experience Manager] 클래식 사용자 인터페이스에는 2GB의 파일 크기 제한이 없습니다. 또한 큰 비디오에 대한 종단 간 워크플로우는 완전히 지원되지 않습니다.

더 높은 파일 크기 제한을 구성하려면 `/apps` 디렉토리.

1. In AEM, tap **[!UICONTROL Tools > General > CRXDE Lite]**.
1. 에서 **[!UICONTROL CRXDE Lite]** 페이지의 왼쪽 디렉토리 창에서 `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. 디렉터리 창을 보려면 Touch를 사용하십시오 `>>` 아이콘.
1. From toolbar, tap the **[!UICONTROL Overlay Node]**. Alternatively, select **[!UICONTROL Overlay Node]** from the context menu.
1. In the **[!UICONTROL Overlay Node]** dialog, tap **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. 브라우저를 새로 고칩니다. 오버레이 노드 `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` 이 선택되어 있습니다.
1. 에서 **[!UICONTROL 속성]** 탭에서 적절한 값(바이트)을 입력하여 크기 제한을 원하는 크기로 늘립니다. 예를 들어, 을 입력합니다. `32212254720` 값을 추가하여 크기 제한을 30GB로 늘립니다.

1. 도구 모음에서 **[!UICONTROL 모두 저장]**.
1. In AEM, tap **[!UICONTROL Tools > Operations > Web Console]**.
1. 설정 **[!UICONTROL Adobe Experience Manager Web Console 번들]** 페이지, 아래에 **[!UICONTROL 이름]** 표의 열, 위치 및 탭 **[!UICONTROL Adobe Granite Workflow 외부 프로세스 작업 처리기]**.
1. 에서 **[!UICONTROL Adobe Granite Workflow 외부 프로세스 작업 처리기]** 페이지에서 두 시간 모두에 대한 초 수를 설정합니다. **[!UICONTROL 기본 시간 초과]** 및 **[!UICONTROL 최대 시간 초과]** 필드 대상 `18000` (5시간).
1. 탭 **[!UICONTROL 저장]**.
1. AEM에서 **[!UICONTROL 도구 > 워크플로우 > 모델]**.
1. 설정 **[!UICONTROL 워크플로우 모델]** 페이지를 선택하고 **[!UICONTROL Dynamic Media 인코딩 비디오]**&#x200B;를 탭한 다음, **[!UICONTROL 편집]**.
1. 설정 **[!UICONTROL 워크플로우]** 페이지에서 두 번 누릅니다 **[!UICONTROL Dynamic Media 비디오 서비스 프로세스]** 구성 요소.
1. In the **[!UICONTROL Step Properties]** dialog box, under the **[!UICONTROL Common]** tab, expand **[!UICONTROL Advanced Settings]**.
1. In the **[!UICONTROL Timeout]** field, specify a value of `18000`, then tap **[!UICONTROL OK]** to return to the **[!UICONTROL Dynamic Media Encode Video]** workflow page.
1. 페이지 상단 근처에 있는 **[!UICONTROL Dynamic Media 인코딩 비디오]** 페이지 제목, 탭 **[!UICONTROL 저장]**.

## 비디오 자산 게시 {#publishing-video-assets}

비디오 자산이 게시되면 URL을 통해 또는 웹 페이지에 포함하거나 웹 페이지에 포함할 수 있습니다. 자세한 내용은 [자산 게시](publishing-dynamicmedia-assets.md).

## 비디오 자산에 주석 달기 {#annotating-video-assets}

1. 자산 콘솔에서 **[!UICONTROL 편집]** 자산 카드의 아이콘을 클릭하여 자산 세부 사항 페이지를 표시합니다.
1. 탭하기 **[!UICONTROL 미리 보기]** 아이콘을 클릭하여 비디오를 재생합니다.
1. 비디오에 주석을 달려면 **[!UICONTROL 주석 달기]** 버튼을 클릭합니다. 비디오의 특정 시점(프레임)에 주석이 추가됩니다.

   캔버스에 주석을 달 때 그림을 그리고 드로잉에 주석을 포함할 수 있습니다. 주석은 Adobe Experience Manager Assets에 자동으로 저장됩니다.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   주석 마법사를 종료하려면 **[!UICONTROL 닫기]**.

1. 비디오의 특정 지점으로 이동하려면 텍스트 필드에 시간을 초 단위로 지정하고 을 클릭합니다 **[!UICONTROL 점프]**. 예를 들어 비디오의 처음 20초를 건너뛰려면 를 입력합니다. `20` 를 입력합니다.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. 주석을 클릭하여 타임라인에서 볼 수 있습니다. 탭 **[!UICONTROL 삭제]** 타임라인에서 주석을 제거합니다.

   ![chlimage_1-206](assets/chlimage_1-206.png)
