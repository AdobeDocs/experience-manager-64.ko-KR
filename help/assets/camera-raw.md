---
title: Camera Raw 지원
description: Adobe Experience Manager Assets에서 Camera Raw 지원을 활성화하는 방법을 알아봅니다.
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 4%

---

# 이미지를 처리하려면 Camera Raw 사용 {#camera-raw-support}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Camera Raw 지원을 통해 CR2, NEF 및 RAF와 같은 원시 파일 형식을 처리하고 이미지를 JPEG 형식으로 렌더링할 수 있습니다. 이 기능은 [Camera Raw 패키지](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) 소프트웨어 배포에서 사용할 수 있습니다.

>[!NOTE]
>
>이 기능은 JPEG 표현물만 지원합니다. Windows 64비트, Mac OS 및 RHEL 7.x에서 지원됩니다.

Adobe Experience Manager Assets에서 Camera Raw 지원을 활성화하려면 다음 단계를 수행하십시오.

1. 다운로드 [Camera Raw 패키지](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) 소프트웨어 배포

1. 액세스 `https://[aem_server]:[port]/workflow`. 를 엽니다. **[!UICONTROL DAM 자산 업데이트]** 워크플로우.

1. 를 엽니다. **[!UICONTROL 프로세스 축소판]** 단계.

1. 에서 다음 구성을 제공합니다. **[!UICONTROL 축소판 그림]** 탭:

   * **[!UICONTROL 축소판 그림]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL MIME 유형 건너뛰기]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage](assets/chlimage_1-334.png)

1. 에서 **[!UICONTROL 웹 사용 이미지]** 탭, **[!UICONTROL 목록 건너뛰기]** 필드, 지정 `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![chlimage](assets/chlimage_1-335.png)

1. 사이드 패널에서 **[!UICONTROL Camera Raw/DNG 처리기]** 아래의 단계 **[!UICONTROL 축소판 만들기]** 단계.

1. 에서 **[!UICONTROL Camera Raw/DNG 처리기]** 단계에서 다음 구성을 **[!UICONTROL 인수]** 탭:

   * **[!UICONTROL Mime 유형]**: `image/dng` 및 `image/x-raw-(.*)`
   * **[!UICONTROL 명령]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

>[!NOTE]
>
>위의 구성이 **[!UICONTROL 샘플 DAM Camera Raw 및 DNG 처리 단계를 통해 자산 업데이트]** 구성.

이제 Camera Raw 파일을 [!DNL Experience Manager] 자산. Camera Raw 패키지를 설치하고 필요한 워크플로우를 구성한 후, **[!UICONTROL 이미지 조정]** 옵션 이 측면 창 목록에 나타납니다.

![chlimage_1-337](assets/chlimage_1-337.png)

*그림: 사이드 창의 옵션*

![chlimage_1-338](assets/chlimage_1-338.png)

*그림: 옵션을 사용하여 이미지를 간단히 편집할 수 있습니다*

편집 내용을 Camera Raw 이미지에 저장한 후 새 표현물 `AdjustedPreview.jpg` 이미지용으로 생성됩니다. Camera Raw을 제외한 다른 이미지 유형의 경우, 변경 사항이 모든 변환에 반영됩니다.

## 우수 사례, 알려진 문제 및 제한 사항 {#best-practices}

기능에는 다음과 같은 제한 사항이 있습니다.

* 이 기능은 JPEG 표현물만 지원합니다. Windows 64비트, Mac OS 및 RHEL 7.x에서 지원됩니다.
* 메타데이터 원본에 쓰기 작업은 RAW 및 DNG 형식에 대해 지원되지 않습니다.
* Camera Raw 라이브러리에는 한 번에 처리할 수 있는 총 픽셀에 대한 제한이 있습니다. 현재 파일의 긴 쪽에서는 최대 65000 픽셀이나 먼저 조건에 맞는 512MP를 처리할 수 있습니다.
