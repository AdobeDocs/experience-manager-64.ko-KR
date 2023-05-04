---
title: ImageMagick 설치 및 구성 [!DNL Experience Manager] 자산
description: ImageMagick 소프트웨어, 설치 방법, 명령줄 프로세스 단계 설정, 이미지 축소판 편집, 작성 및 생성 등에 사용
contentOwner: AG
feature: Renditions,Developer Tools
role: Admin
exl-id: 9aeda88a-fd66-4fad-b496-3352a6ecab81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 2%

---

# ImageMagick 설치 및 구성 [!DNL Experience Manager Assets] {#install-and-configure-imagemagick-to-work-with-aem-assets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

ImageMagick는 비트맵 이미지를 생성, 편집, 작성 또는 변환하는 소프트웨어 플러그인입니다. PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF 및 SVG을 포함하여 다양한 형식(200개 이상)으로 이미지를 읽고 쓸 수 있습니다. ImageMagick를 사용하여 이미지의 크기 조정, 대칭 이동, 미러, 회전, 왜곡, 전단 및 변환. 또한 ImageMagick를 사용하여 이미지 색상을 조정하거나 다양한 특수 효과를 적용하거나 텍스트, 선, 다각형, 타원 및 커브를 그릴 수도 있습니다.

명령줄에서 Adobe Experience Manager 미디어 핸들러를 사용하여 ImageMagick를 통해 이미지를 처리합니다. ImageMagick를 사용하여 다양한 파일 형식으로 작업하려면 [자산 파일 형식 우수 사례](assets-file-format-best-practices.md). 지원되는 모든 파일 형식에 대해 알아보려면 [자산 지원 형식](assets-formats.md).

ImageMagick를 사용하여 대용량 파일을 처리하려면 일반적인 메모리 요구 사항보다 높은 용량, IM 정책에 필요한 잠재적인 변경 사항 및 성능에 대한 전반적인 영향을 고려해야 합니다. 메모리 요구 사항은 해상도, 비트 깊이, 색상 프로필 및 파일 형식과 같은 다양한 요소에 따라 다릅니다. ImageMagick를 사용하여 매우 큰 파일을 처리하려는 경우 [!DNL Experience Manager] server. 유용한 리소스 중 일부는 끝에 제공됩니다.

>[!NOTE]
>
>사용 중인 경우 [!DNL Experience Manager] AMS(Adobe Managed Services)에서 대규모 PSD 또는 PSB 파일을 처리할 계획이라면 Adobe 고객 지원 센터에 문의하십시오. Experience Manager는 30000 x 23000픽셀이 넘는 고해상도 PSB 파일을 처리하지 못할 수 있습니다.

## ImageMagick 설치 {#installing-imagemagick}

다양한 운영 체제에서 여러 버전의 ImageMagic 설치 파일을 사용할 수 있습니다. 운영 체제에 적합한 버전을 사용하십시오.

1. 적절한 [ImageMagick 설치 파일](https://www.imagemagick.org/script/download.php) 사용 중인 운영 체제용.
1. ImageMagick를 설치하려면 [!DNL Experience Manager] 서버에서 설치 파일을 시작합니다.

1. 경로 환경 변수를 ImageMagic 설치 디렉터리로 설정합니다.
1. 설치가 성공했는지 확인하려면 `identify -version` 명령.

## 명령줄 프로세스 단계 설정 {#set-up-the-command-line-process-step}

특정 사용 사례에 대해 명령줄 프로세스 단계를 설정할 수 있습니다. 다음 단계를 수행하여 JPEG 이미지 파일을 추가할 때마다 뒤집힌 이미지와 축소판(140x100, 48x48, 319x319 및 1280x1280)을 생성합니다 `/content/dam` on [!DNL Experience Manager] server:

1. 설정 [!DNL Experience Manager] 서버에서 워크플로우 콘솔(`https://[aem_server]:[Port]/workflow`)를 클릭하여 엽니다. **[!UICONTROL DAM 자산 업데이트]** 워크플로우 모델.
1. 에서 **[!UICONTROL DAM 자산 업데이트]** 워크플로우 모델, 열기 **[!UICONTROL EPS 축소판(ImageMagick 제공)]** 단계.
1. 에서 **[!UICONTROL 인수 탭]**, 추가 `image/jpeg` 변환 후 **[!UICONTROL Mime 유형]** 목록.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. 에서 **[!UICONTROL 명령]** 상자에 다음 명령을 입력합니다.

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. 을(를) 선택합니다 **[!UICONTROL 생성된 표현물 삭제]** 및 **[!UICONTROL 웹 표현물 생성]** 플래그.

   ![select_flags](assets/select_flags.png)

1. 에서 **[!UICONTROL 웹 사용 이미지]** 탭에서 1280x1280픽셀로 표현물에 대한 세부 사항을 지정합니다. 또한,*이미지/jpeg* 에서 **[!UICONTROL Mime 유형]** 상자.

   ![web_enabled_image](assets/web_enabled_image.png)

1. 탭/클릭 **[!UICONTROL 확인]** 변경 사항을 저장하려면 을 클릭합니다.

   >[!NOTE]
   >
   >다음 `convert` 명령이 기본 버전과 충돌하므로 특정 Windows 버전(예: Windows SE)에서 실행되지 않을 수 있습니다 `convert` Windows 설치의 일부인 유틸리티 이 경우 ImageMagick 유틸리티의 전체 경로를 설명합니다. 예를 들어,
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. 를 엽니다. **[!UICONTROL 프로세스 축소판]** 단계를 수행하고 MIME 유형을 추가합니다. `image/jpeg` 아래에 **[!UICONTROL Mime 유형 건너뛰기]**.

   ![skip_mime_types](assets/skip_mime_types.png)

1. 에서 **[!UICONTROL 웹 사용 이미지]** 탭에서 MIME 유형을 추가합니다 `image/jpeg` 아래에 **[!UICONTROL 목록 건너뛰기]**. 탭/클릭 **[!UICONTROL 확인]** 변경 사항을 저장하려면 을 클릭합니다.

   ![web_enabled](assets/web_enabled.png)

1. 워크플로우를 저장합니다.
1. ImageMagic에서 이미지를 제대로 처리할 수 있는지 확인하려면 JPG 이미지를 [!DNL Assets]. 전환된 이미지와 표현물이 생성되었는지 확인합니다.

## 보안 취약점 완화 {#mitigating-security-vulnerabilities}

ImageMagick를 사용하여 이미지를 처리하는 것과 관련된 여러 보안 취약점이 있습니다. 예를 들어 사용자가 제출한 이미지를 처리하면 RCE(원격 코드 실행)가 발생할 수 있습니다.

또한 PHP의 이미지, Ruby의 빠른 이미지 및 페이퍼클립, Node.js의 이미지 매그릭 등 다양한 이미지 처리 플러그인은 ImageMagick 라이브러리에 따라 다릅니다.

ImageMagick 또는 영향을 받는 라이브러리를 사용하는 경우, Adobe은 다음 작업(하지만 둘 다) 중 하나 이상을 수행하여 알려진 취약점을 완화할 것을 권장합니다.

1. 모든 이미지 파일이 예상대로 시작되는지 확인합니다 [&quot;magic bytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures) 를 처리 위해 ImageMagick로 보내기 전에 지원하는 이미지 파일 유형에 해당합니다.
1. 취약한 ImageMagick 코드를 비활성화하려면 정책 파일을 사용하십시오. ImageMagick에 대한 글로벌 정책은 `/etc/ImageMagick`.

>[!MORELIKETHIS]
>
>* [를 사용하여 다양한 파일 형식을 처리하는 우수 사례 [!DNL Assets]](assets-file-format-best-practices.md)
>* [ImageMagick용 명령줄 옵션](https://www.imagemagick.org/script/command-line-options.php)
>* [ImageMagick 사용의 기본 및 고급 예](https://www.imagemagick.org/Usage/)
>* [ImageMagick용 자산 성능 조정](performance-tuning-guidelines.md)
>* [에서 지원하는 전체 파일 형식 목록 [!DNL Assets]](assets-formats.md)
>* [파일 형식 및 이미지 메모리 비용 이해](https://www.scantips.com/basics1d.html)

