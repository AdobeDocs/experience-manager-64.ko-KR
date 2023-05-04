---
title: 비디오 구성 요소 구성
seo-title: Configure the Video component
description: 비디오 구성 요소를 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure the Video Component.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---

# 비디오 구성 요소 구성 {#configure-the-video-component}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다음 [비디오 구성 요소](/help/sites-authoring/default-components-foundation.md#video) 사전 정의된 OOTB(기본 제공) 비디오 요소를 페이지에 배치할 수 있습니다.

변환이 올바르게 수행되려면 관리자가 [FFmpeg 설치 및 AEM 구성](#install-ffmpeg) 별개입니다. 이러한 기능은 [비디오 프로필 구성](#configure-video-profiles) HTML5 요소에 사용할 수 있습니다.

>[!CAUTION]
>
>이 구성 요소는 광범위한 프로젝트 수준 사용자 지정 없이 더 이상 기본 작동하지 않을 것입니다.

## 비디오 프로필 구성 {#configure-video-profiles}

HTML 5 요소에 사용할 비디오 프로필을 정의할 수 있습니다. 여기서 선택된 것은 순서대로 사용됩니다. 액세스하려면 [디자인 모드](/help/sites-authoring/default-components-designmode.md) (클래식 UI만 해당) 및 **[!UICONTROL 프로필]** 탭:

![chlimage_1-317](assets/chlimage_1-317.png)

비디오 구성 요소 및 매개 변수의 디자인을 구성할 수도 있습니다 [!UICONTROL 재생], [!UICONTROL Flash], 및 [!UICONTROL 고급].

## FFmpeg 설치 및 AEM 구성 {#install-ffmpeg}

비디오 구성 요소는 비디오에서 다운로드할 수 있는 적절한 코드 변환을 위해 타사 오픈 소스 제품 FFmpeg를 사용합니다. [https://ffmpeg.org/](https://ffmpeg.org/). FFmpeg를 설치한 후에는 특정 오디오 코덱과 특정 런타임 옵션을 사용하도록 AEM을 구성해야 합니다.

**플랫폼용 FFmpeg를 설치하려면 다음을 수행하십시오**:

* **Windows의 경우:**

   1. 컴파일된 바이너리를 다음으로 다운로드 `ffmpeg.zip`
   1. 폴더의 압축을 해제합니다.
   1. 시스템 환경 변수 설정 `PATH` to `<*your-ffmpeg-locatio*n>\bin`
   1. AEM을 다시 시작합니다.

* **Mac OS X의 경우:**

   1. Xcode([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. XQuartz/X11을 설치합니다.
   1. MacPorts 설치([https://www.macports.org/](https://www.macports.org/))
   1. 콘솔에서 다음 명령을 실행하고 지침을 따릅니다.

      `sudo port install ffmpeg`

      `FFmpeg` 다음 위치에 있어야 합니다. `PATH` AEM에서 명령줄을 통해 가져올 수 있습니다.

* **OS X 10.6용 사전 컴파일된 버전 사용:**

   1. 미리 컴파일된 버전을 다운로드합니다.
   1. 에 추출합니다. `/usr/local` 디렉토리.
   1. 터미널에서 다음을 실행합니다.

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**AEM을 구성하려면**:

1. 열기 [!UICONTROL CRXDE Lite] 참조하십시오. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. 을(를) 선택합니다 `/libs/settings/dam/video/format_aac/jcr:content` 노드 이름을 입력하고 노드 속성이 다음과 같은지 확인합니다.

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. 구성을 사용자 지정하려면 `/apps/settings/` 노드 및 이동 `/conf/global/settings/` 노드 아래에 있어야 합니다. 에서는 편집할 수 없습니다 `/libs` 노드 아래에 있어야 합니다. 예를 들어, 오버레이 경로 `/libs/settings/dam/video/fullhd-bp`에서 만듭니다. `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >수정해야 하는 속성뿐만 아니라 전체 프로필 노드를 오버레이하고 편집합니다. 이러한 리소스는 SlingResourceMerger를 통해 해결되지 않습니다.

1. 속성을 변경한 경우 **[!UICONTROL 모두 저장]**.

>[!NOTE]
>
>AEM 인스턴스를 업그레이드할 때 OOTB 워크플로우 모델은 유지되지 않습니다. Adobe은 OOTB 워크플로우 모델을 편집하기 전에 복사할 것을 권장합니다. 예를 들어, DAM 자산 업데이트 모델의 FFmpeg 코드 변환 단계를 편집하기 전에 OTB DAM 자산 업데이트 모델을 복사하여 업그레이드 전에 있던 비디오 프로필 이름을 선택합니다. 그런 다음 를 오버레이할 수 있습니다 `/apps` 노드 아래에 있는 OOTB 모델에 대한 사용자 지정 변경 사항을 AEM에서 검색할 수 있도록 합니다.
