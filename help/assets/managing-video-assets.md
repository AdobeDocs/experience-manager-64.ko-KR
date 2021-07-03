---
title: 비디오 자산 관리
description: 비디오 자산을 업로드, 미리 보기, 주석 달기 및 게시하는 방법을 알아봅니다.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: 자산 관리,비디오
role: User
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: 1795b0faed0570e8130c1ba60de07bda49db8fde
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 1%

---

# 비디오 자산 관리 {#managing-video-assets}

Adobe Experience Manager(AEM) Assets에서 비디오 자산을 관리하고 편집하는 방법을 알아봅니다. 또한 Dynamic Media 사용 권한이 있는 경우 [Dynamic Media 비디오 설명서](video.md)를 참조하십시오.

## 비디오 자산 업로드 및 미리 보기 {#uploading-and-previewing-video-assets}

AEM Assets은 확장 MP4를 사용하여 비디오 자산에 대한 미리 보기를 생성합니다. 자산의 형식이 MP4가 아닌 경우, FFmpeg 팩을 설치하여 미리 보기를 생성합니다. FFmpeg는 OGG 및 MP4 유형의 비디오 표현물을 만듭니다. AEM Assets 사용자 인터페이스에서 이러한 렌디션을 미리 볼 수 있습니다.

1. 디지털 자산 폴더 또는 하위 폴더에서 디지털 자산을 추가할 위치로 이동합니다.
1. 자산을 업로드하려면 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭하거나 탭한 다음 **[!UICONTROL 파일]**&#x200B;을 선택합니다. 또는 자산 영역에 직접 놓습니다. 업로드 작업에 대한 자세한 내용은 [자산 업로드](managing-assets-touch-ui.md#uploading-assets)를 참조하십시오.
1. 카드 보기에서 비디오를 미리 보려면 비디오 자산에서 **[!UICONTROL Play]** 단추를 누릅니다.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   **[!UICONTROL 카드]** 보기에서만 비디오를 일시 중지하거나 재생할 수 있습니다. 재생/일시 중지 단추는 **[!UICONTROL 목록]** 보기에서 사용할 수 없습니다.

1. 카드에서 **[!UICONTROL 편집]** 아이콘을 탭하여 **[!UICONTROL 세부 정보]** 보기에서 비디오를 미리 봅니다.

   비디오는 브라우저의 기본 비디오 플레이어에서 재생됩니다. 비디오를 전체 화면으로 재생, 일시 정지, 볼륨 제어 및 확대/축소할 수 있습니다.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## 2GB보다 큰 자산을 업로드하도록 구성 {#configuration-to-upload-video-assets-that-are-larger-than-gb}

기본적으로 AEM Assets에서는 파일 크기 제한으로 인해 2GB보다 큰 자산을 업로드할 수 없습니다. 그러나 CRXDE Lite으로 이동하여 `/apps` 디렉토리 아래에 노드를 만들어 이 제한을 덮어쓸 수 있습니다. 노드에는 동일한 노드 이름, 디렉토리 구조 및 이와 비교할 수 있는 노드 속성이 있어야 합니다.

AEM Assets 구성 외에 다음 구성을 변경하여 큰 자산을 업로드합니다.

* 토큰 만료 시간을 늘립니다. `https://[aem_server]:[port]/system/console/configMgr`의 웹 콘솔에서 [!UICONTROL Granite CSRF 서블릿] Adobe을 참조하십시오. 자세한 내용은 [CSRF 보호](/help/sites-developing/csrf-protection.md)를 참조하십시오.
* Dispatcher 구성에서 `receiveTimeout`을 늘립니다. 자세한 내용은 [Dispatcher 구성 Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#renders-options)를 참조하십시오.

>[!NOTE]
>
>AEM Classic 사용자 인터페이스에는 2GB의 파일 크기 제한이 없습니다. 또한 큰 비디오에 대한 종단 간 워크플로우는 완전히 지원되지 않습니다.

더 높은 파일 크기 제한을 구성하려면 `/apps` 디렉토리에서 다음 단계를 수행하십시오.

1. AEM에서 **[!UICONTROL 도구 > 일반 > CRXDE Lite]**&#x200B;를 누릅니다.
1. **[!UICONTROL CRXDE Lite]** 페이지의 왼쪽 디렉토리 창에서 `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`로 이동합니다. 디렉터리 창을 보려면 `>>` 아이콘을 누르십시오.
1. 도구 모음에서 **[!UICONTROL 오버레이 노드]**&#x200B;를 누릅니다. 또는 컨텍스트 메뉴에서 **[!UICONTROL 오버레이 노드]**&#x200B;를 선택합니다.
1. **[!UICONTROL 오버레이 노드]** 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 누릅니다.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. 브라우저를 새로 고칩니다. 오버레이 노드 `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`이(가) 선택되어 있습니다.
1. **[!UICONTROL 속성]** 탭에서 적절한 값을 바이트 단위로 입력하여 크기 제한을 원하는 크기로 늘리십시오. 예를 들어 `32212254720` 값을 입력하여 크기 제한을 30GB로 늘립니다.

1. 도구 모음에서 **[!UICONTROL 모두 저장]**&#x200B;을 누릅니다.
1. AEM에서 **[!UICONTROL 도구 > 작업 > 웹 콘솔]**&#x200B;을 누릅니다.
1. **[!UICONTROL Adobe Experience Manager Web Console 번들]** 페이지의 테이블의 **[!UICONTROL 이름]** 열 아래에서 **[!UICONTROL Granite Workflow 외부 프로세스 작업 처리기 Adobe]**&#x200B;을(를) 찾아 탭합니다.
1. **[!UICONTROL Granite Workflow 외부 프로세스 작업 핸들러 Adobe]** 페이지에서 **[!UICONTROL 기본 시간 초과]** 및 **[!UICONTROL 최대 시간 초과]** 필드 모두에 대한 초를 `18000`(5시간)로 설정합니다.
1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.
1. AEM에서 **[!UICONTROL 도구 > 워크플로우 > 모델]**&#x200B;을 탭합니다.
1. **[!UICONTROL 워크플로우 모델]** 페이지에서 **[!UICONTROL Dynamic Media 인코딩 비디오]**&#x200B;을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 탭합니다.
1. **[!UICONTROL 워크플로우]** 페이지에서 **[!UICONTROL Dynamic Media 비디오 서비스 프로세스]** 구성 요소를 두 번 탭합니다.
1. **[!UICONTROL 단계 속성]** 대화 상자의 **[!UICONTROL 공통]** 탭에서 **[!UICONTROL 고급 설정]**&#x200B;을 확장합니다.
1. **[!UICONTROL 시간 초과]** 필드에서 `18000` 값을 지정한 다음 **[!UICONTROL 확인]**&#x200B;을 탭하여 **[!UICONTROL Dynamic Media 인코딩 비디오]** 워크플로우 페이지로 돌아갑니다.
1. 페이지 상단 근처에 있는 **[!UICONTROL Dynamic Media 인코딩 비디오]** 페이지 제목 아래에서 **[!UICONTROL 저장]**&#x200B;을 탭합니다.

## 비디오 자산 게시 {#publishing-video-assets}

비디오 자산이 게시되면 URL을 통해 또는 웹 페이지에 포함하거나 웹 페이지에 포함할 수 있습니다. [자산 게시](publishing-dynamicmedia-assets.md)를 참조하십시오.

## 비디오 자산에 주석 달기 {#annotating-video-assets}

1. Assets 콘솔에서 자산 카드의 **[!UICONTROL 편집]** 아이콘을 탭하여 자산 세부 사항 페이지를 표시합니다.
1. **[!UICONTROL 미리 보기]** 아이콘을 탭하여 비디오를 재생합니다.
1. 비디오에 주석을 달려면 **[!UICONTROL 주석 달기]** 단추를 누릅니다. 비디오의 특정 시점(프레임)에 주석이 추가됩니다.

   캔버스에 주석을 달 때 그림을 그리고 드로잉에 주석을 포함할 수 있습니다. 주석은 Adobe Experience Manager Assets에 자동으로 저장됩니다.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   주석 마법사를 종료하려면 **[!UICONTROL 닫기]**&#x200B;를 누릅니다.

1. 비디오의 특정 지점으로 이동하려면 텍스트 필드에 시간을 초 단위로 지정하고 **[!UICONTROL Jump]**&#x200B;를 클릭합니다. 예를 들어 비디오의 처음 20초를 건너뛰려면 텍스트 필드에 `20`을 입력합니다.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. 주석을 클릭하여 타임라인에서 볼 수 있습니다. **[!UICONTROL 삭제]**&#x200B;를 눌러 타임라인에서 주석을 제거합니다.

   ![chlimage_1-206](assets/chlimage_1-206.png)
