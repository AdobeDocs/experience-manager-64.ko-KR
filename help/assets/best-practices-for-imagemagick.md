---
title: ' [!DNL Experience Manager] Assets에서 작동하도록 ImageMagick 설치 및 구성'
description: ImageMagick 소프트웨어, 설치 방법, 명령줄 프로세스 단계 설정, 이미지 축소판 편집, 작성 및 생성 등에 사용
contentOwner: AG
feature: Renditions,Developer Tools
role: Admin
exl-id: 9aeda88a-fd66-4fad-b496-3352a6ecab81
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# [!DNL Experience Manager Assets]에서 작동하도록 ImageMagick 설치 및 구성 {#install-and-configure-imagemagick-to-work-with-aem-assets}

ImageMagick는 비트맵 이미지를 생성, 편집, 작성 또는 변환하는 소프트웨어 플러그인입니다. PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF 및 SVG을 포함하여 다양한 형식(200개 이상)으로 이미지를 읽고 쓸 수 있습니다. ImageMagick를 사용하여 이미지의 크기 조정, 대칭 이동, 미러, 회전, 왜곡, 전단 및 변환. 또한 ImageMagick를 사용하여 이미지 색상을 조정하거나 다양한 특수 효과를 적용하거나 텍스트, 선, 다각형, 타원 및 커브를 그릴 수도 있습니다.

명령줄에서 Adobe Experience Manager 미디어 핸들러를 사용하여 ImageMagick를 통해 이미지를 처리합니다. ImageMagick를 사용하여 다양한 파일 형식으로 작업하려면 [자산 파일 형식 우수 사례](assets-file-format-best-practices.md)를 참조하십시오. 지원되는 모든 파일 형식에 대해 알아보려면 [자산 지원 형식](assets-formats.md)을 참조하십시오.

ImageMagick를 사용하여 대용량 파일을 처리하려면 일반적인 메모리 요구 사항보다 높은 용량, IM 정책에 필요한 잠재적인 변경 사항 및 성능에 대한 전반적인 영향을 고려해야 합니다. 메모리 요구 사항은 해상도, 비트 깊이, 색상 프로필 및 파일 형식과 같은 다양한 요소에 따라 다릅니다. ImageMagick를 사용하여 매우 큰 파일을 처리하려는 경우 [!DNL Experience Manager] 서버를 올바르게 벤치마킹하십시오. 유용한 리소스 중 일부는 끝에 제공됩니다.

>[!NOTE]
>
>AMS(Adobe Managed Services)에서 [!DNL Experience Manager]을(를) 사용하는 경우, 대규모 PSD 또는 PSB 파일을 많이 처리할 계획이면 Adobe 고객 지원 센터에 문의하십시오. Experience Manager은 30000 x 23000 픽셀 이상의 고해상도 PSB 파일을 처리하지 못할 수 있습니다.

## ImageMagick 설치 {#installing-imagemagick}

다양한 운영 체제에서 여러 버전의 ImageMagic 설치 파일을 사용할 수 있습니다. 운영 체제에 적합한 버전을 사용하십시오.

1. 운영 체제에 적합한 [ImageMagick 설치 파일](https://www.imagemagick.org/script/download.php)을 다운로드하십시오.
1. [!DNL Experience Manager] 서버를 호스팅하는 디스크에 ImageMagick를 설치하려면 설치 파일을 실행하십시오.

1. 경로 환경 변수를 ImageMagic 설치 디렉터리로 설정합니다.
1. 설치가 성공했는지 확인하려면 `identify -version` 명령을 실행합니다.

## 명령줄 프로세스 단계 설정 {#set-up-the-command-line-process-step}

특정 사용 사례에 대해 명령줄 프로세스 단계를 설정할 수 있습니다. 다음 단계를 수행하여 [!DNL Experience Manager] 서버의 `/content/dam`에 JPEG 이미지 파일을 추가할 때마다 뒤집힌 이미지와 축소판(140x100, 48x48, 319x319 및 1280x1280)을 생성합니다.

1. [!DNL Experience Manager] 서버에서 워크플로우 콘솔(`https://[aem_server]:[Port]/workflow`)로 이동하고 **[!UICONTROL DAM 자산 업데이트]** 워크플로우 모델을 엽니다.
1. **[!UICONTROL DAM 자산 업데이트]** 워크플로우 모델에서 **[!UICONTROL EPS 축소판(ImageMagick에서 제공)]** 단계를 엽니다.
1. **[!UICONTROL 인수 탭]**&#x200B;에서 **[!UICONTROL Mime 유형]** 목록에 `image/jpeg`를 추가합니다.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. **[!UICONTROL 명령]** 상자에 다음 명령을 입력합니다.

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. **[!UICONTROL 생성된 표현물 삭제]** 및 **[!UICONTROL 웹 표현물 생성]** 플래그를 선택합니다.

   ![select_flags](assets/select_flags.png)

1. **[!UICONTROL Web Enabled 이미지]** 탭에서 1280x1280픽셀로 표현물에 대한 세부 정보를 지정합니다. 또한 **[!UICONTROL Mime 유형]** 상자에 i *이미지/jpeg*&#x200B;을 지정하십시오.

   ![web_enabled_image](assets/web_enabled_image.png)

1. **[!UICONTROL 확인]**&#x200B;을 탭/클릭하여 변경 사항을 저장합니다.

   >[!NOTE]
   >
   >`convert` 명령은 특정 Windows 버전(예: Windows SE)에서 실행되지 않을 수 있습니다. 이 명령은 Windows 설치의 일부인 기본 `convert` 유틸리티와 충돌하기 때문입니다. 이 경우 ImageMagick 유틸리티의 전체 경로를 설명합니다. 예를 들어,
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. **[!UICONTROL 축소판 처리]** 단계를 열고 **[!UICONTROL Mime 유형 건너뛰기]** 아래에 MIME 유형 `image/jpeg`을 추가합니다.

   ![skip_mime_types](assets/skip_mime_types.png)

1. **[!UICONTROL 웹 지원 이미지]** 탭에서 **[!UICONTROL 목록 건너뛰기]** 아래에 MIME 유형 `image/jpeg`을 추가합니다. **[!UICONTROL 확인]**&#x200B;을 탭/클릭하여 변경 사항을 저장합니다.

   ![web_enabled](assets/web_enabled.png)

1. 워크플로우를 저장합니다.
1. ImageMagic에서 이미지를 제대로 처리할 수 있는지 확인하려면 JPG 이미지를 [!DNL Assets]으로 업로드하십시오. 전환된 이미지와 표현물이 생성되었는지 확인합니다.

## 보안 취약점 완화 {#mitigating-security-vulnerabilities}

ImageMagick를 사용하여 이미지를 처리하는 것과 관련된 여러 보안 취약점이 있습니다. 예를 들어 사용자가 제출한 이미지를 처리하면 RCE(원격 코드 실행)가 발생할 수 있습니다.

또한 PHP의 이미지, Ruby의 빠른 이미지 및 페이퍼클립, Node.js의 이미지 매그릭 등 다양한 이미지 처리 플러그인은 ImageMagick 라이브러리에 따라 다릅니다.

ImageMagick 또는 영향을 받는 라이브러리를 사용하는 경우, Adobe은 다음 작업(하지만 둘 다) 중 하나 이상을 수행하여 알려진 취약점을 완화할 것을 권장합니다.

1. 모든 이미지 파일이 처리를 위해 ImageMagick로 보내기 전에 지원하는 이미지 파일 형식에 해당하는 예상 [&quot;magic bytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures)로 시작하는지 확인합니다.
1. 취약한 ImageMagick 코드를 비활성화하려면 정책 파일을 사용하십시오. ImageMagick에 대한 글로벌 정책은 `/etc/ImageMagick`에 있습니다.

>[!MORELIKETHIS]
>
>* [를 사용하여 다양한 파일 형식을 처리하는 우수 사례 [!DNL Assets]](assets-file-format-best-practices.md)
>* [ImageMagick용 명령줄 옵션](https://www.imagemagick.org/script/command-line-options.php)
>* [ImageMagick 사용의 기본 및 고급 예](https://www.imagemagick.org/Usage/)
>* [ImageMagick용 자산 성능 조정](performance-tuning-guidelines.md)
>* [에서 지원하는 전체 파일 형식 목록 [!DNL Assets]](assets-formats.md)
>* [파일 형식 및 이미지 메모리 비용 이해](https://www.scantips.com/basics1d.html)

