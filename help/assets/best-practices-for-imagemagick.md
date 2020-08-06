---
title: AEM Assets에서 작동하도록 ImageMagick 설치 및 구성
description: ImageMagick 소프트웨어에 대한 자세한 내용, 설치 방법, 명령줄 프로세스 단계 설정, 이미지 축소판 편집, 작성 및 생성 등에 사용할 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: af5f8a24db589ecdbe28d603ab9583f11d29212c
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 2%

---


# AEM Assets에서 작동하도록 ImageMagick 설치 및 구성 {#install-and-configure-imagemagick-to-work-with-aem-assets}

ImageMagick은 비트맵 이미지를 생성, 편집, 구성 또는 변환할 수 있는 소프트웨어 플러그인입니다. PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF, SVG 등 다양한 형식(200개 이상)으로 이미지를 읽고 쓸 수 있습니다. ImageMagick을 사용하여 이미지 크기 조정, 뒤집기, 거울, 회전, 왜곡, 기울임 및 변형 또한 ImageMagick을 사용하여 이미지 색상을 조정하거나 다양한 특수 효과를 적용하거나 텍스트, 선, 다각형, 타원 및 곡선을 그릴 수도 있습니다.

명령줄에서 Adobe Experience Manager(AEM) 미디어 핸들러를 사용하여 ImageMagick을 통해 이미지를 처리합니다. ImageMagick을 사용하여 다양한 파일 포맷으로 작업하려면 [에셋 파일 포맷 우수 사례를 참조하십시오](assets-file-format-best-practices.md). 지원되는 모든 파일 형식에 대해 알아보려면 [자산 지원 형식을 참조하십시오](assets-formats.md).

ImageMagick을 사용하여 대용량 파일을 처리하려면 일반적인 메모리 요구 사항보다 높은 수치, IM 정책에 필요한 잠재적 변경 사항 및 성능에 대한 전반적인 영향을 고려해야 합니다. 메모리 요구 사항은 해상도, 비트 심도, 색상 프로파일 및 파일 포맷과 같은 다양한 요소에 따라 다릅니다. ImageMagick을 사용하여 매우 큰 파일을 처리하려는 경우 AEM 서버를 제대로 벤치마킹합니다. 유용한 리소스는 마지막에 제공됩니다.

>[!NOTE]
>
>Adobe Managed Services(AMS)에서 AEM을 사용하는 경우 대용량 PSD 또는 PSB 파일을 처리할 계획인 경우 Adobe 고객 지원 센터에 문의하십시오. Experience Manager은 3000 x 23000픽셀이 넘는 매우 고해상도 PSB 파일을 처리하지 못할 수 있습니다.

## ImageMagick 설치 {#installing-imagemagick}

다양한 운영 체제에서 ImageMagic 설치 파일을 사용할 수 있습니다. 운영 체제에 적합한 버전을 사용하십시오.

1. 운영 체제에 맞는 [ImageMagick 설치 파일을](https://www.imagemagick.org/script/download.php) 다운로드합니다.
1. AEM 서버를 호스팅하는 디스크에 ImageMagick을 설치하려면 설치 파일을 실행합니다.

1. 경로 환경 변수를 ImageMagic 설치 디렉토리로 설정합니다.
1. 설치 성공 여부를 확인하려면 명령을 `identify -version` 실행합니다.

## 명령줄 프로세스 단계 설정 {#set-up-the-command-line-process-step}

특정 사용 사례에 대해 명령줄 프로세스 단계를 설정할 수 있습니다. AEM 서버에 JPEG 이미지 파일을 추가할 때마다 역진행 이미지 및 축소판(140x100, 48x48, 319x319 및 1280x1280)을 생성하려면 다음 단계 `/content/dam` 를 수행하십시오.

1. AEM 서버에서 워크플로우 콘솔(`https://[aem_server]:[Port]/workflow`)로 이동하여 **[!UICONTROL DAM 자산 업데이트 워크플로우 모델을]** 엽니다.
1. DAM 자산 **[!UICONTROL 업데이트]** 워크플로우 모델에서 **[!UICONTROL EPS 축소판(ImageMagick에서 제공)]** 단계를 엽니다.
1. 인수 탭 **[!UICONTROL 에서]** MIME 형식 `image/jpeg` 목록 **[!UICONTROL 에]** 추가합니다.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. 명령 **[!UICONTROL 상자에]** 다음 명령을 입력합니다.

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. 생성된 변환 **[!UICONTROL 삭제]** 및 웹 변환 **[!UICONTROL 생성]** 플래그를 선택합니다.

   ![select_flags](assets/select_flags.png)

1. [ **[!UICONTROL 웹 사용 이미지]** ] 탭에서 1280x1280픽셀의 변환 세부 사항을 지정합니다. 또한 유형(Mimetype) 상자에서&#x200B;*이미지/jpeg* 를 **[!UICONTROL 지정합니다]** .

   ![web_enabled_image](assets/web_enabled_image.png)

1. Tap/click **[!UICONTROL OK]** to save the changes.

   >[!NOTE]
   >
   >이 명령은 Windows 설치에 포함된 기본 `convert` `convert` 유틸리티와 충돌하기 때문에 특정 Windows 버전(예: Windows SE)에서 실행할 수 없습니다. 이 경우 ImageMagick 유틸리티의 전체 경로를 언급합니다. 예를 들어,
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. [ **[!UICONTROL 프로세스 축소판]** ] 단계를 열고 [MIME 형식 건너뛰기] 아래에 MIME 형식 `image/jpeg` 을 **[!UICONTROL 추가합니다]**.

   ![skip_mime_types](assets/skip_mime_types.png)

1. [ **[!UICONTROL 웹 사용 이미지]** ] 탭에서 [건너뛰기 목록] `image/jpeg` 아래에 MIME 형식을 **[!UICONTROL 추가합니다]**. Tap/click **[!UICONTROL OK]** to save the changes.

   ![web_enabled](assets/web_enabled.png)

1. 워크플로우를 저장합니다.
1. ImageMagic에서 이미지를 제대로 처리할 수 있는지 확인하려면 JPG 이미지를 AEM Assets에 업로드하십시오. 역진행 이미지와 변환이 생성되었는지 확인합니다.

## 보안 취약점 완화 {#mitigating-security-vulnerabilities}

이미지를 처리하기 위해 ImageMagick을 사용하는 것과 관련된 여러 가지 보안 취약점이 있습니다. 예를 들어 사용자가 제출한 이미지를 처리하는 경우 RCE(원격 코드 실행)의 위험이 발생합니다.

또한 PHP의 이미지 빠른, Ruby의 빠른 및 페이퍼클립, Node.js의 이미지 빠른 클릭 등 다양한 이미지 처리 플러그인은 ImageMagick 라이브러리에 따라 다릅니다.

ImageMagick 또는 영향을 받는 라이브러리를 사용하는 경우, Adobe은 다음 작업 중 하나 이상을 수행하여 알려진 취약점을 완화시킬 것을 권장합니다(하지만 둘 다).

1. 모든 이미지 파일이 처리를 위해 ImageMagick으로 보내기 전에 지원하는 이미지 파일 [유형에](https://en.wikipedia.org/wiki/List_of_file_signatures) 해당하는 예상 &quot;매직 바이트&quot;로 시작하는지 확인합니다.
1. 취약한 ImageMagick 코더를 비활성화하려면 정책 파일을 사용합니다. ImageMagick에 대한 글로벌 정책은 `/etc/ImageMagick`

>[!MORELIKETHIS]
>
>* [AEM Assets을 사용하여 다양한 파일 포맷을 처리하는 모범 사례](assets-file-format-best-practices.md)
>* [ImageMagick의 명령줄 옵션](https://www.imagemagick.org/script/command-line-options.php)
>* [ImageMagick 사용의 기본 및 고급 예](https://www.imagemagick.org/Usage/)
>* [ImageMagick을 위한 에셋 성능 조정](performance-tuning-guidelines.md)
>* [AEM Assets에서 지원하는 전체 파일 포맷 목록](assets-formats.md)
>* [파일 포맷 및 이미지 메모리 비용 이해](https://www.scantips.com/basics1d.html)

