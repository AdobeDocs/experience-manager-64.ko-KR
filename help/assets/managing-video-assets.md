---
title: 비디오 자산 관리
description: 비디오 에셋을 업로드, 미리 보기, 주석 달기 및 게시하는 방법에 대해 알아봅니다.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 1%

---


# 비디오 자산 관리 {#managing-video-assets}

AEM(Adobe Experience Manager) 자산에서 비디오 자산을 관리하고 편집하는 방법을 알아봅니다. 또한 Dynamic Media을 사용할 수 있는 라이센스가 있는 경우 [Dynamic Media 비디오 설명서](video.md)를 참조하십시오.

## 비디오 자산 업로드 및 미리 보기 {#uploading-and-previewing-video-assets}

AEM Assets에서는 확장 MP4를 사용하여 비디오 자산에 대한 미리 보기를 생성합니다. 에셋의 형식이 MP4가 아닌 경우 FFmpeg 팩을 설치하여 미리 보기를 생성합니다. FFmpeg는 OGG 및 MP4 유형의 비디오 변환을 만듭니다. AEM Assets 사용자 인터페이스에서 이러한 변환을 미리 볼 수 있습니다.

1. 디지털 자산 폴더 또는 하위 폴더에서 디지털 자산을 추가할 위치로 이동합니다.
1. 자산을 업로드하려면 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭하거나 탭한 다음 **[!UICONTROL 파일]**&#x200B;을 선택합니다. 또는 자산 영역에 직접 놓습니다. 업로드 작업에 대한 자세한 내용은 [자산 업로드](managing-assets-touch-ui.md#uploading-assets)를 참조하십시오.
1. 카드 보기에서 비디오를 미리 보려면 비디오 자산에서 **[!UICONTROL 재생]** 단추를 누릅니다.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   **[!UICONTROL 카드]** 보기에서만 비디오를 일시 중지하거나 재생할 수 있습니다. 재생/일시 정지 단추는 **[!UICONTROL 목록]** 보기에서 사용할 수 없습니다.

1. 카드의 **[!UICONTROL 편집]** 아이콘을 눌러 **[!UICONTROL 세부 사항]** 보기에서 비디오를 미리 봅니다.

   비디오가 브라우저의 기본 비디오 플레이어에서 재생됩니다. 비디오를 재생, 일시 정지, 볼륨 조절 및 전체 화면으로 확대/축소할 수 있습니다.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## 2GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}보다 큰 자산을 업로드하기 위한 구성

기본적으로 AEM Assets에서는 파일 크기 제한으로 인해 2GB보다 큰 에셋을 업로드할 수 없습니다. 그러나 CRXDE Lite으로 이동하여 `/apps` 디렉터리 아래에 노드를 만들면 이 제한을 덮어쓸 수 있습니다. 노드에는 동일한 노드 이름, 디렉토리 구조 및 이와 비교할 수 있는 노드 속성이 있어야 합니다.

AEM Assets 구성 외에도 큰 자산을 업로드하려면 다음 구성을 변경하십시오.

* 토큰 만료 시간을 늘립니다. `https://[aem_server]:[port]/system/console/configMgr`의 웹 콘솔에서 [!UICONTROL Adobe Granite CSRF Servlet]을 참조하십시오. 자세한 내용은 [CSRF 보호](/help/sites-developing/csrf-protection.md)를 참조하십시오.
* Dispatcher 구성에서 `receiveTimeout`을(를) 늘립니다. 자세한 내용은 [Experience Manager 디스패처 구성](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)을 참조하십시오.

>[!NOTE]
>
>AEM Classic 사용자 인터페이스에 2GB의 파일 크기 제한이 없습니다. 또한 대형 비디오에 대한 엔드 투 엔드 워크플로우는 완벽하게 지원되지 않습니다.

더 높은 파일 크기 제한을 구성하려면 `/apps` 디렉토리에서 다음 단계를 수행하십시오.

1. AEM에서 **[!UICONTROL 도구 > 일반 > CRXDE Lite]**&#x200B;을 탭합니다.
1. **[!UICONTROL CRXDE Lite]** 페이지의 왼쪽에 있는 디렉토리 창에서 `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`로 이동합니다. 디렉토리 창을 보려면 `>>` 아이콘을 터치하십시오.
1. 도구 모음에서 **[!UICONTROL 오버레이 노드]**&#x200B;를 누릅니다. 또는 컨텍스트 메뉴에서 **[!UICONTROL 오버레이 노드]**&#x200B;를 선택합니다.
1. **[!UICONTROL 오버레이 노드]** 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 탭합니다.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. 브라우저를 새로 고칩니다. 오버레이 노드 `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`이(가) 선택됩니다.
1. **[!UICONTROL 속성]** 탭에서 원하는 크기로 크기 제한을 늘리려면 적절한 값을 바이트 단위로 입력합니다. 예를 들어 크기 제한을 30GB로 늘리려면 `32212254720` 값을 입력합니다.

1. 도구 모음에서 **[!UICONTROL 모두 저장]**&#x200B;을 누릅니다.
1. AEM에서 **[!UICONTROL 도구 > 작업 > 웹 콘솔]**&#x200B;을 탭합니다.
1. **[!UICONTROL Adobe Experience Manager 웹 콘솔 번들]** 페이지의 테이블의 **[!UICONTROL 이름]** 열에서 **[!UICONTROL Adobe Granite Workflow 외부 프로세스 작업 처리기]**&#x200B;를 찾아 탭합니다.
1. **[!UICONTROL Adobe Granite Workflow 외부 프로세스 작업 핸들러]** 페이지에서 **[!UICONTROL 기본 시간 초과]** 및 **[!UICONTROL 최대 시간 초과`18000`(5시간) 필드 모두에 대한 초를 설정합니다.]**
1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.
1. AEM에서 **[!UICONTROL 도구 > 워크플로 > 모델]**&#x200B;을 탭합니다.
1. **[!UICONTROL 워크플로우 모델]** 페이지에서 **[!UICONTROL Dynamic Media 인코딩 비디오]**&#x200B;을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 탭합니다.
1. **[!UICONTROL 워크플로우]** 페이지에서 **[!UICONTROL Dynamic Media 비디오 서비스 프로세스]** 구성 요소를 두 번 누릅니다.
1. **[!UICONTROL 단계 속성]** 대화 상자의 **[!UICONTROL 일반]** 탭에서 **[!UICONTROL 고급 설정]**&#x200B;을 확장합니다.
1. **[!UICONTROL 시간 초과]** 필드에서 `18000` 값을 지정한 다음 **[!UICONTROL 확인]**&#x200B;을 눌러 **[!UICONTROL Dynamic Media 비디오 인코딩]** 워크플로우 페이지로 돌아갑니다.
1. 페이지 상단의 **[!UICONTROL Dynamic Media 인코딩 비디오]** 페이지 제목 아래에 있는 **[!UICONTROL 저장]**&#x200B;을 탭합니다.

## 비디오 자산 {#publishing-video-assets} 게시

비디오 에셋이 게시된 후에는 URL을 통해 웹 페이지에 포함하거나 웹 페이지에 포함시키는 데 사용할 수 있습니다. [자산 게시](publishing-dynamicmedia-assets.md)를 참조하십시오.

## 비디오 자산 {#annotating-video-assets}에 주석 추가

1. 자산 콘솔에서 자산 카드의 **[!UICONTROL 편집]** 아이콘을 눌러 자산 세부 사항 페이지를 표시합니다.
1. **[!UICONTROL 미리 보기]** 아이콘을 눌러 비디오를 재생합니다.
1. 비디오에 주석을 추가하려면 **[!UICONTROL 주석(]**) 단추를 누릅니다. 비디오의 특정 시간(프레임)에 주석이 추가됩니다.

   주석을 달 때 캔버스에서 그리고 그림에 주석을 추가할 수 있습니다. 주석은 Adobe Experience Manager Assets에 자동으로 저장됩니다.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   주석 마법사를 종료하려면 **[!UICONTROL 닫기]**&#x200B;를 누릅니다.

1. 비디오의 특정 지점으로 이동하려면 텍스트 필드에서 시간(초)을 지정하고 **[!UICONTROL 점프]**&#x200B;를 클릭합니다. 예를 들어 비디오의 처음 20초를 건너뛰려면 텍스트 필드에 `20`을 입력합니다.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. 타임라인에서 주석을 클릭하여 표시합니다. 타임라인에서 주석을 제거하려면 **[!UICONTROL 삭제]**&#x200B;를 누릅니다.

   ![chlimage_1-206](assets/chlimage_1-206.png)
