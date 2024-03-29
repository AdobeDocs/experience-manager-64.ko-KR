---
title: Dynamic Media의 비디오
description: Dynamic Media에서 비디오를 사용하여 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: Dynamic-Media
content-type: reference
exl-id: acb95a2b-0171-449e-97fa-f9a533f990de
feature: Video
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '10437'
ht-degree: 4%

---

# 비디오 {#video}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 섹션에서는 Dynamic Media에서 비디오 작업을 설명합니다.

## 빠른 시작: 비디오 {#quick-start-videos}

다음 단계별 워크플로우 설명은 Dynamic Media의 응용 비디오 세트를 빠르게 설정 및 실행하는 데 도움이 되도록 설계되었습니다. 각 단계 후에는 자세한 정보를 찾을 수 있는 주제 제목에 대한 상호 참조가 있습니다.

>[!NOTE]
>
>Dynamic Media에서 비디오를 사용하기 전에 AEM 관리자가 이미 Dynamic Media Cloud Services을 활성화 및 구성했는지 확인하십시오.
>
>* 자세한 내용은 [Dynamic Media 구성 - 하이브리드 모드에서 Dynamic Media Cloud Services 구성](/help/assets/config-dynamic.md)
>* 자세한 내용은 [Dynamic Media 구성 - Scene7 모드](config-dms7.md) 및 [Dynamic Media 문제 해결 - Scene7 모드](troubleshoot-dms7.md)
>


1. **Dynamic Media 비디오 업로드** 다음을 수행하십시오.

   * 자신만의 비디오 인코딩 프로필을 만듭니다. 또는 Dynamic Media과 함께 제공되는 사전 정의된 &quot;응용 비디오 인코딩&quot; 프로필을 사용하면 됩니다.

      * [비디오 인코딩 프로필 만들기](video-profiles.md).
      * 추가 정보 [비디오 인코딩에 대한 우수 사례](#best-practices-for-encoding-videos).
   * 비디오 처리 프로필을 마스터 비디오를 업로드할 하나 이상의 폴더에 연결합니다.

      * [폴더에 비디오 프로필 적용](video-profiles.md#applying-a-video-profile-to-folders).
      * 추가 정보 [처리 프로필 사용을 위한 디지털 자산을 구성하는 우수 사례](organize-assets.md#organize-using-folders).
      * 추가 정보 [디지털 자산 구성](organize-assets.md).
   * 기본 소스 비디오를 폴더에 업로드합니다. 폴더에 비디오를 추가하면 폴더에 할당한 비디오 처리 프로필에 따라 인코딩됩니다.

      * Dynamic Media은 주로 최대 30분 길이의 짧은 비디오와 25x 25보다 큰 최소 해상도를 지원합니다.
      * 각각 최대 15GB의 비디오 파일을 업로드할 수 있습니다.
      * [비디오 업로드](managing-video-assets.md#uploading-and-previewing-video-assets).
      * 추가 정보 [지원되는 입력 파일 형식](assets-formats.md#supported-multimedia-formats).
   * 모니터링 방법 [비디오 인코딩이 진행 중입니다.](#monitoring-video-encoding-and-youtube-publishing-progress) 자산 또는 워크플로우 보기에서 선택합니다.




1. **Dynamic Media 비디오 관리** 다음을 수행하여 다음을 수행합니다.

   * 비디오 자산 구성, 탐색 및 검색

      * [디지털 자산 구성](organize-assets.md)

         추가 정보 [처리 프로필 사용을 위한 디지털 자산을 구성하는 우수 사례](organize-assets.md#organize-using-folders)

      * [비디오 자산 검색](search-video-assets.md) 또는 [자산 검색](managing-assets-touch-ui.md#searching-assets)
   * 비디오 자산 미리 보기 및 게시

      * 관련 축소판과 함께 비디오의 소스 비디오 및 인코딩된 표현물을 봅니다.

         [비디오 미리 보기](managing-video-assets.md#uploading-and-previewing-video-assets) 또는 [자산 미리 보기](previewing-assets.md)

         [비디오 표현물 보기](video-renditions.md)

[비디오 표현물 관리](managing-assets-touch-ui.md#managing-renditions)

      * [뷰어 사전 설정 관리](managing-viewer-presets.md)
      * [자산 게시](publishing-dynamicmedia-assets.md)
   * 비디오 메타데이터 작업

      * 프레임 속도, 오디오 및 비디오 비트율, 코덱과 같은 인코딩된 비디오 표현물의 속성을 봅니다.

         [비디오 표현물 속성 보기](video-renditions.md)

      * 제목, 설명 및 태그, 사용자 지정 메타데이터 필드와 같은 비디오의 속성을 편집합니다.

[비디오 속성 편집](managing-assets-touch-ui.md#editing-properties)

      * [디지털 자산에 대한 메타데이터 관리](metadata.md)
      * [메타데이터 스키마](metadata-schemas.md)
   * 비디오 검토, 승인 및 주석 달기

      * [비디오에 주석 달기](managing-video-assets.md#annotating-video-assets) 또는 [자산에 주석 달기](managing-assets-touch-ui.md#annotating)
      * [자산에 워크플로우 적용](assets-workflow.md) 또는 [자산에서 워크플로우 시작](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)
      * [폴더 자산 검토](bulk-approval.md)
      * [프로젝트](/help/sites-authoring/projects.md)




1. **Dynamic Media 비디오 게시** 다음 중 하나를 수행하여 다음을 수행합니다.

   * 웹 컨텐츠 관리 시스템으로 Adobe Experience Manager을 사용하는 경우 웹 페이지에 직접 비디오를 추가할 수 있습니다.

      * [웹 페이지에 비디오 추가](adding-dynamic-media-assets-to-pages.md).
   * 타사 웹 컨텐츠 관리 시스템을 사용하는 경우 웹 페이지에 비디오를 링크하거나 포함할 수 있습니다.

      * URL을 사용하여 비디오 통합:

         [URL을 웹 애플리케이션에 연결](linking-urls-to-yourwebapplication.md).
      * 웹 페이지에서 포함 코드를 사용하여 비디오 통합:

         [웹 페이지에 비디오 뷰어 포함](embed-code.md).
   * [YouTube에 비디오 게시](#publishing-videos-to-youtube).
   * [비디오 보고서 생성](#viewing-video-reports).
   * [비디오에 캡션 추가](#adding-captions-to-video).



## Dynamic Media에서 비디오를 사용한 작업 {#working-with-video-in-dynamic-media}

Dynamic Media의 비디오는 데스크탑, iOS, Android, Blackberry 및 Windows 모바일 장치를 포함하여 여러 화면에서 스트리밍을 위한 고품질 적응형 비디오를 쉽게 게시할 수 있도록 하는 종단 간 솔루션입니다. 응용 비디오 세트는 다른 비트율 및 형식(예: 400kbps, 800kbps 및 1000kbps)으로 인코딩된 동일한 비디오 버전을 그룹화합니다. 데스크탑 컴퓨터 또는 모바일 장치가 사용 가능한 대역폭을 감지합니다.

예를 들어 iOS 모바일 장치에서 3G, 4G 또는 Wi-Fi와 같은 대역폭을 감지합니다. 그런 다음 응용 비디오 세트 내의 다양한 비디오 비트 전송률 중에서 올바른 인코딩된 비디오를 자동으로 선택합니다. 비디오는 데스크탑, 모바일 장치 또는 태블릿으로 스트리밍됩니다.

또한 데스크탑 또는 모바일 장치에서 네트워크 조건이 변경되면 자동으로 비디오 품질이 전환됩니다. 또한 고객이 데스크탑에서 전체 화면 모드로 전환하면 응용 비디오 세트가 더 나은 해상도를 사용하여 응답하여 고객의 보기 환경을 개선할 수 있습니다. 응용 비디오 세트 사용은 고객이 여러 화면 및 장치에서 Dynamic Media 비디오를 재생할 수 있는 최상의 재생 기능을 제공합니다.

비디오 플레이어에서 재생할 인코딩된 비디오 또는 재생 중에 선택할 인코딩된 비디오를 결정하는 데 사용하는 로직은 다음 알고리즘을 기반으로 합니다.

1. 비디오 플레이어는 플레이어 자체에서 &quot;초기 비트율&quot;에 대해 설정된 값에 가장 가까운 비트율을 기반으로 초기 비디오 조각을 로드합니다.
1. 비디오 플레이어는 다음 기준을 사용하여 대역폭 속도 변경 사항을 기반으로 전환합니다.

   1. 플레이어가 예상 대역폭보다 작거나 같은 가장 높은 대역폭 스트림을 선택합니다.
   1. 플레이어는 사용 가능한 대역폭의 80%만 고려합니다. 그러나, 만약 그것이 전환하고 있다면, 그것은 단지 70%에서 더 보수적인데, 그것은 과대평가하고 즉시 다시 돌아서는 것을 피한다.

알고리즘에 대한 자세한 기술 정보는 [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

단일 비디오 및 응용 비디오 세트를 관리하는 경우 다음과 같이 지원됩니다.

* 지원되는 다양한 비디오 형식 및 오디오 포맷의 비디오를 업로드하고 여러 화면에서 재생되도록 비디오를 MP4 H.264 형식으로 인코딩합니다. 사전 정의된 응용 비디오 사전 설정, 단일 비디오 인코딩 사전 설정을 사용하거나 자체 인코딩을 사용자 지정하여 비디오의 품질과 크기를 제어할 수 있습니다.

   * 응용 비디오 세트가 생성되면 MP4 비디오가 포함됩니다.
   * **참고**: 기본/소스 비디오가 응용 비디오 세트에 추가되지 않습니다.

* 모든 HTML 5 비디오 뷰어의 비디오 캡션.
* 비디오 자산을 효율적으로 관리하기 위해 전체 메타데이터 지원을 사용하여 비디오를 구성, 탐색 및 검색할 수 있습니다.
* 응용 비디오 세트를 웹뿐만 아니라 iPhone, iPad, Android, Blackberry 및 Windows 휴대폰을 포함한 데스크톱 및 모바일 장치에 제공합니다.

응용 비디오 스트리밍은 다양한 iOS 플랫폼에서 지원됩니다. 자세한 내용은 [Adobe 뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

Dynamic Media은 MP4 H.264 비디오용 모바일 비디오 재생을 지원합니다. 다음 위치에서 이 비디오 형식을 지원하는 Blackberry 장치를 찾을 수 있습니다. [Blackberry에서 지원되는 비디오 형식](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

다음 위치에서 이 비디오 형식을 지원하는 Windows 장치를 찾을 수 있습니다. [Windows Phone에서 지원되는 비디오 형식](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)

* 다음을 포함하여 Dynamic Media 비디오 뷰어 사전 설정을 사용하여 비디오를 재생합니다.

   * 단일 비디오 뷰어입니다.
   * 비디오와 이미지 컨텐츠를 모두 결합하는 혼합 미디어 뷰어입니다.

* 브랜딩 요구 사항을 충족하도록 비디오 플레이어를 구성합니다.
* 간단한 URL 또는 포함 코드와 함께 웹 사이트, 모바일 사이트 또는 모바일 애플리케이션에 비디오를 통합합니다.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480). -->

참조 - [HTML5 뷰어 정보](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) Adobe Dynamic Media 뷰어 참조 가이드에서 참조할 수 있습니다.

## 우수 사례: HTML 5 비디오 뷰어 사용 {#best-practice-using-the-html-video-viewer}

Dynamic Media HTML5 비디오 뷰어 사전 설정은 강력한 비디오 플레이어입니다. HTML5 비디오 재생과 관련된 많은 일반적인 문제와 응용 스트리밍 전달 부족 및 제한된 데스크탑 브라우저 도달과 같은 모바일 장치와 관련된 문제를 방지하기 위해 이 매개 변수를 사용할 수 있습니다.

플레이어의 디자인 측면에서는 표준 웹 개발 도구를 사용하여 모든 비디오 플레이어의 기능을 디자인할 수 있습니다. 예를 들어 HTML5 및 CSS를 사용하여 단추, 컨트롤 및 사용자 지정 포스터 이미지 배경을 디자인하여 고객에게 맞춤형 모양을 만들어 줄 수 있습니다.

뷰어의 재생 측에서 브라우저의 비디오 기능을 자동으로 감지합니다. 그런 다음 HLS 스트리밍(응용 비디오 스트리밍)을 사용하여 비디오를 제공합니다. 또는 이러한 배달 방법이 없으면 HTML 5 프로그레시브가 대신 사용됩니다.

단일 플레이어에 HTML5 및 CSS를 사용하여 재생 구성 요소를 디자인하고, 포함된 재생을 사용하고, 브라우저의 기능에 따라 적응형 및 점진적 스트리밍을 사용하는 기능을 결합하면 데스크탑 및 모바일 사용자 모두에게 리치 미디어 콘텐츠의 범위를 확장하고 간소화된 비디오 경험을 제공할 수 있습니다.

참조 - [HTML5 뷰어 정보](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html) Adobe 뷰어 참조 가이드에서 참조할 수 있습니다.

### HTML 5 비디오 뷰어를 사용하여 데스크탑 컴퓨터 및 모바일 장치에서 비디오 재생 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

데스크탑 및 모바일 적응형 비디오 스트리밍의 경우 비트율 전환에 사용되는 비디오는 응용 비디오 세트의 모든 MP4 비디오를 기반으로 합니다.

비디오 재생은 HLS(HTTP Live Streaming) 비디오 스트리밍 또는 점진적 비디오 다운로드를 사용하여 발생합니다. 6.0, 6.1 및 6.2와 같은 이전 버전의 AEM에서는 비디오가 HTTP를 통해 스트리밍되었습니다.

그러나 AEM 6.3 이상에서는 DM 게이트웨이 서비스 URL이 항상 HTTPS를 사용하므로 비디오가 이제 HTTPS(즉, HLS 비디오 스트리밍)를 통해 스트리밍됩니다. 이 기본 동작에는 고객에게 영향을 주지 않습니다. 즉, 비디오 스트리밍은 브라우저가 지원하지 않는 한 항상 HTTPS를 통해 발생합니다. (다음 표를 참조하십시오.) 따라서,

* HTTPS 비디오 스트리밍이 있는 HTTPS 웹 사이트가 있는 경우 스트리밍이 좋습니다.
* HTTPS 비디오 스트리밍이 있는 HTTP 웹 사이트가 있는 경우 스트리밍이 문제가 해결되고 웹 브라우저에서 혼합 콘텐츠 문제가 발생하지 않습니다.

HLS(HTTP Live Streaming)는 네트워크 대역폭 용량에 따라 재생을 자동으로 조정하는 응용 비디오 스트리밍을 위한 Apple 표준입니다. 또한 고객이 나머지 비디오가 다운로드될 때까지 기다릴 필요 없이 비디오의 모든 지점을 &quot;찾기&quot;할 수 있습니다(HTTP Live 스트리밍 참조).

점진적 비디오는 사용자의 데스크탑 화면이나 모바일 장치에 로컬로 비디오를 다운로드하여 저장하여 전달됩니다.

다음 표에서는 Dynamic Media Video Viewer를 사용하는 데스크톱 컴퓨터 및 모바일 장치에서 비디오의 장치, 브라우저 및 재생 방법에 대해 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>장치</strong></td>
   <td><strong>브라우저</strong></td>
   <td><strong>비디오 재생 모드</strong></td>
  </tr>
  <tr> 
   <td>데스크탑</td>
   <td>Internet Explorer 9 및 10</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr> 
   <td>데스크탑</td>
   <td>Internet Explorer 11+</td>
   <td>Windows 8 및 Windows 10의 경우 - HLS가 요청될 때마다 HTTPS를 강제로 사용합니다. 알려진 제한 사항: HLS의 HTTP가 이 브라우저/운영 체제 조합에서 작동하지 않습니다<br /> <br /> Windows 7 - Progressive 다운로드의 경우. HTTP 및 HTTPS 프로토콜을 선택하는 표준 로직을 사용합니다.</td>
  </tr>
  <tr> 
   <td>데스크탑</td>
   <td>Firefox 23-44</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr> 
   <td>데스크탑</td>
   <td>Firefox 45 이상</td>
   <td>HLS 비디오 스트리밍.</td>
  </tr>
  <tr> 
   <td>데스크탑</td>
   <td>Chrome</td>
   <td>HLS 비디오 스트리밍.</td>
  </tr>
  <tr> 
   <td>데스크탑</td>
   <td>Safari(Mac)</td>
   <td>HLS 비디오 스트리밍.</td>
  </tr>
  <tr> 
   <td>모바일</td>
   <td>Chrome(Android 6 이하)</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr> 
   <td>모바일</td>
   <td>Chrome(Android 7 이상)</td>
   <td>HLS 비디오 스트리밍.</td>
  </tr>
  <tr> 
   <td>모바일</td>
   <td>Android(기본 브라우저)</td>
   <td>점진적 다운로드.</td>
  </tr>
  <tr> 
   <td>모바일</td>
   <td>Safari(iOS)</td>
   <td>HLS 비디오 스트리밍.</td>
  </tr>
  <tr> 
   <td>모바일</td>
   <td>Chrome(iOS)</td>
   <td>HLS 비디오 스트리밍.</td>
  </tr>
  <tr> 
   <td>모바일</td>
   <td>Blackberry</td>
   <td>HLS 비디오 스트리밍.</td>
  </tr>
 </tbody>
</table>

## Dynamic Media 비디오 솔루션 아키텍처 {#architecture-of-dynamic-media-video-solution}

다음 그래픽은 DMGateway를 통해 업로드 및 인코딩되고 공개 소비에 사용할 수 있는 비디오의 전체 작성 워크플로우를 보여줍니다.

![chlimage_1-427](assets/chlimage_1-427.png)

## 비디오용 하이브리드 게시 아키텍처 {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## 비디오 인코딩 우수 사례 {#best-practices-for-encoding-videos}

The **[!UICONTROL Dynamic Media Encode Video]** workflow encodes video if you have enabled dynamic media and set up video cloud services. This workflow captures workflow process history and failure information. See [Monitoring video encoding and YouTube publishing progress](#monitoring-video-encoding-and-youtube-publishing-progress). Dynamic Media을 활성화하고 Video Cloud 서비스를 설정한 경우, **[!UICONTROL Dynamic Media 인코딩 비디오]** 워크플로우는 비디오를 업로드할 때 자동으로 적용됩니다. (Dynamic Media을 사용하지 않는 경우, **[!UICONTROL DAM 자산 업데이트]** 워크플로우가 적용됩니다.)

<!-- DEAD ARTICLE AND VIDEO LINK The following are best-practice tips for encoding source video files.

For advice about video encoding, see the following:

* Article: *Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution:* [www.adobe.com/go/learn_s7_streaming101_en](https://www.adobe.com/go/learn_s7_streaming101_en).
* Video: *Video Encoding Basics:* [www.adobe.com/go/learn_s7_encoding_en](https://www.adobe.com/go/learn_s7_encoding_en). -->

### 기본 소스 비디오 파일 {#source-video-files}

비디오 파일을 인코딩할 때 가능한 가장 높은 품질의 소스 비디오 파일을 사용하십시오. 이전에 인코딩된 비디오 파일은 이미 압축되었으므로 해당 파일을 사용하지 마십시오. 또한 인코딩을 통해 하위 품질의 비디오가 생성됩니다.

* Dynamic Media은 주로 최대 30분 길이의 짧은 비디오와 25x 25보다 큰 최소 해상도를 지원합니다.
* 각각 최대 15GB의 기본 소스 비디오 파일을 업로드할 수 있습니다.

다음 표에서는 소스 비디오 파일을 인코딩하기 전에 사용해야 하는 권장 크기, 종횡비 및 최소 비트 전송률에 대해 설명합니다.

| 크기 | 종횡비 | 최소 비트 전송률 |
|--- |--- |--- |
| 1024 X 768 | 4:3 | 대부분의 비디오에는 4500kbps입니다. |
| 1280 X 720 | 16:9 | 3000 - 6000kbps(비디오의 동작 양에 따라 다름) |
| 1920 X 1080 | 16:9 | 6000 - 8000kbps(비디오의 동작 양에 따라 다름) |

### 파일의 메타데이터 가져오기 {#obtaining-a-file-s-metadata}

비디오 편집 도구를 사용하여 파일의 메타데이터를 보거나 메타데이터를 얻기 위해 디자인된 응용 프로그램을 사용하여 파일의 메타데이터를 가져올 수 있습니다. 다음은 타사 응용 프로그램인 MediaInfo를 사용하여 비디오 파일의 메타데이터를 가져오는 방법에 대한 지침입니다.

1. 다음 웹 페이지로 이동합니다. [https://mediaarea.net/en/MediaInfo](https://mediaarea.net/en/MediaInfo).
1. 사용 중인 GUI 버전에 대한 설치 관리자를 선택하여 다운로드하고 설치 지침을 따르십시오.
1. 설치 후 비디오 파일(Windows만 해당)을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL MediaInfo]**, 또는 열기 **[!UICONTROL MediaInfo]** 비디오 파일을 응용 프로그램으로 드래그합니다. 너비, 높이, fps 등 비디오 파일과 관련된 모든 메타데이터가 표시됩니다.

### 종횡비 {#aspect-ratio}

마스터 비디오 파일에 대한 비디오 인코딩 사전 설정을 선택하거나 만들 때 사전 설정이 마스터 비디오 파일과 동일한 종횡비인지 확인하십시오. 종횡비는 비디오 높이에 대한 너비의 비율입니다.

비디오 파일의 종횡비를 결정하려면 파일의 메타데이터를 가져와서 파일의 폭과 높이를 확인합니다(위의 파일 메타데이터 가져오기 참조). 다음 공식을 사용하여 종횡비를 확인합니다.

*너비/높이 = 종횡비*

다음 표에서는 공식 결과가 일반적인 종횡비 선택 사항으로 변환되는 방법을 설명합니다.

| 수식 결과 | 종횡비 |
|--- |--- |
| 1.33 | 4:3 |
| 0.75 | 3:4 |
| 1.78 | 16:9 |
| 0.56 | 9:16 |

예를 들어, 1440 너비 x 1080 높이의 비디오에는 1440/1080 또는 1.33의 종횡비가 있습니다. 이 경우 4:3 종횡비가 있는 비디오 인코딩 사전 설정을 선택하여 비디오 파일을 인코딩합니다.

### 비트율 {#bitrate}

비트율은 비디오 재생 1초를 구성하기 위해 인코딩된 데이터의 양입니다. 비트율은 초당 킬로비트(Kbps)로 측정됩니다.

모든 코덱에서는 손실 압축을 사용하므로 비디오 품질에서 비트율이 가장 중요합니다. 손실 압축을 사용하면 비디오 파일을 압축할수록 품질이 더 저하됩니다. 따라서 다른 모든 특성(해상도, 프레임 속도 및 코덱은)은 비트율이 낮을수록 압축 파일의 품질이 낮습니다.

비트율 인코딩을 선택할 때 두 가지 유형을 선택할 수 있습니다.

* **상수 비트율 인코딩** (CBR) - CBR 인코딩 중에 비트율 또는 초당 비트 수가 인코딩 프로세스 전체에서 동일하게 유지됩니다. CBR 인코딩은 전체 비디오에서 설정에 설정된 데이터 속도를 유지합니다. 또한 CBR 인코딩은 품질을 위해 미디어 파일을 최적화하지는 않지만 저장 공간에 저장합니다.

   비디오가 전체 비디오 전체에서 유사한 동작 수준을 포함하는 경우 CBR을 사용합니다. CBR은 비디오 컨텐츠를 스트리밍하는 데 가장 일반적으로 사용됩니다. 참조 - [사용자가 추가한 비디오 인코딩 매개 변수 사용](video-profiles.md#using-custom-added-video-encoding-parameters).

* **변수 비트율 인코딩** (VBR) - VBR 인코딩은 압축기에 필요한 데이터를 기준으로 사용자가 설정한 상한과 데이터 속도를 조절합니다. 즉, VBR 인코딩 프로세스 중에 미디어 파일의 비트율이 미디어 파일 비트율 요구 사항에 따라 동적으로 증가 또는 감소합니다.

   VBR은 인코딩하는 데 더 오래 걸리지만 가장 유리한 결과를 생성합니다. 미디어 파일의 품질이 우수합니다. VBR은 비디오 컨텐츠의 http 점진적 게재에 가장 일반적으로 사용됩니다.

**VBR 대 CRB는 언제 사용해야 합니까?**
VBR과 CBR을 선택하는 방법은 거의 항상 미디어 파일에 VBR을 사용하는 것이 좋습니다. VBR은 경쟁적 비트율로 더 높은 품질의 파일을 제공합니다. VBR을 사용하는 경우 2단계 인코딩에 사용하고 최대 비트율을 대상 비디오 비트율의 1.5배로 설정하십시오.

비디오 인코딩 사전 설정을 선택하는 경우 대상 최종 사용자의 연결 속도를 고려합니다. 해당 속도의 80%인 데이터 비율이 있는 사전 설정을 선택합니다. 예를 들어 대상 최종 사용자의 연결 속도가 1000Kbps인 경우 가장 좋은 사전 설정은 비디오 데이터 속도가 800Kbps인 사전 설정입니다.

이 표에서는 일반적인 연결 속도의 데이터 속도를 설명합니다.

| 속도(Kbps) | 연결 유형 |
|--- |--- |
| 256 | 전화 접속 연결입니다. |
| 800 | 일반적인 모바일 연결. 이 연결의 경우 3G 경험에 대해 400~최대 800 범위의 데이터 전송률을 타깃팅하십시오. |
| 2000 | 일반 광대역 데스크탑 연결. 이 연결의 경우 평균 1200-1500Kbps로 800-2000Kbps 범위의 데이터 속도를 타깃팅합니다. |
| 5000 | 일반적인 고속 광대역 연결 대부분의 소비자는 이 속도로 비디오를 전달할 수 없으므로 이 상위 범위의 인코딩을 사용하지 않는 것이 좋습니다. |

### 해결 {#resolution}

**해결 방법** 비디오 파일의 높이 및 너비를 픽셀 단위로 설명합니다. 대부분의 소스 비디오는 고해상도(예: 1920 x 1080)로 저장됩니다. 스트리밍을 위해 소스 비디오는 더 작은 해상도(640 x 480 이하)로 압축됩니다.

해상도 및 데이터 전송률은 비디오 품질을 결정하는 두 가지 통합 연결 요소입니다. 동일한 비디오 품질을 유지하려면 비디오 파일의 픽셀 수가 많을수록 해상도가 높을수록 데이터 속도가 빨라야 합니다. 예를 들어, 320 x 240 해상도와 640 x 480 해상도 비디오 파일에서 프레임당 픽셀 수를 고려해 보십시오.

| 해결 | 프레임당 픽셀 수 |
|--- |--- |
| 320 x 240 | 76,800 |
| 640 x 480 | 307,200 |

640 x 480 파일은 프레임당 4배 더 많은 픽셀을 가지고 있습니다. 이러한 두 가지 예제 해상도에 대해 동일한 데이터 속도를 구현하려면 640 x 480 파일에 4배 압축을 적용하여 비디오 품질을 줄일 수 있습니다. 따라서, 비디오 데이터 속도가 250Kbps이면 320 x 240 해상도로 고품질로 볼 수 있지만, 640 x 480 해상도에서는 볼 수 없습니다.

일반적으로 데이터 속도가 높을수록 비디오가 더 잘 보이고 해상도가 높을수록 보기 품질을 유지해야 하는 데이터 비율이 높아집니다(해상도가 낮은 것에 비해).

해상도와 데이터 전송률이 연결되어 있으므로 비디오를 인코딩할 때 두 가지 옵션이 있습니다.

* 데이터 비율을 선택한 다음 선택한 데이터 전송률에 적합한 최고 해상도로 인코딩하십시오.
* 해상도를 선택한 다음 선택한 해상도로 고품질의 비디오를 구현하는 데 필요한 데이터 속도로 인코딩하십시오.

마스터 비디오 파일에 대한 비디오 인코딩 사전 설정을 선택(또는 생성)할 때 이 표를 사용하여 올바른 해상도를 지정합니다.

| 해결 | 높이(픽셀) | 화면 크기 |
|--- |--- |--- |
| 240p | 240 | 작은 화면 |
| 300p | 300 | 일반적으로 모바일 장치용 작은 화면 |
| 360p | 360 | 작은 화면 |
| 480p | 480 | 미디어 화면 |
| 720p | 720 | 대형 화면 |
| 1080p | 1080 | HD 대형 화면 |

### Fps(초당 프레임 수) {#fps-frames-per-second}

미국 및 일본에서는 대부분의 비디오가 초당 29.97프레임(fps)으로 촬영됩니다. 유럽에서는 대부분의 비디오가 25fps로 촬영됩니다. 필름은 24fps로 촬영됩니다.

마스터 비디오 파일의 fps 속도와 일치하는 비디오 인코딩 사전 설정을 선택합니다. 예를 들어, 마스터 비디오가 25fps인 경우 25fps로 인코딩 사전 설정을 선택합니다. 기본적으로 모든 사용자 지정 인코딩은 마스터 비디오 파일의 fps를 사용합니다. 따라서 비디오 인코딩 사전 설정을 만들 때 fps 설정을 명시적으로 지정할 필요가 없습니다.

### 비디오 인코딩 차원 {#video-encoding-dimensions}

최적의 결과를 얻으려면 인코딩 차원을 선택하면 소스 비디오가 인코딩된 모든 비디오의 전체 배수입니다.

이 비율을 계산하려면 소스 너비를 인코딩된 너비로 나누어 너비 비율을 가져옵니다. 그런 다음 소스 높이를 인코딩된 높이로 나눈 뒤 높이 비율을 얻습니다.

결과 비율이 전체 정수인 경우 비디오 크기가 최적으로 조절됩니다. 결과 비율이 정수가 아닌 경우, 나머지 픽셀 가공물을 화면에 남겨 두면 비디오 품질에 영향을 줍니다. 이 효과는 비디오에 텍스트가 있을 때 가장 잘 보입니다.

예를 들어 소스 비디오가 1920 x 1080이라고 가정합니다. 다음 표에서 세 개의 인코딩된 비디오는 사용할 최적의 인코딩 설정을 제공합니다.

<table> 
 <tbody> 
  <tr> 
   <th><p>비디오 유형</p> </th> 
   <th><p>너비 x 높이</p> </th> 
   <th><p>폭 비율</p> </th> 
   <th><p>높이 비율</p> </th> 
  </tr>
  <tr> 
   <td><p>소스</p> </td> 
   <td><p>1920x1080</p> </td> 
   <td><p>1</p> </td> 
   <td><p>1</p> </td> 
  </tr> 
  <tr> 
   <td><p>인코딩됨</p> </td> 
   <td><p>960 x 540</p> </td> 
   <td><p>2</p> </td> 
   <td><p>2</p> </td> 
  </tr> 
  <tr> 
   <td><p>인코딩됨</p> </td> 
   <td><p>640 x 360</p> </td> 
   <td><p>3</p> </td> 
   <td><p>3</p> </td> 
  </tr> 
  <tr> 
   <td><p>인코딩됨</p> </td> 
   <td><p>480 x 270</p> </td> 
   <td><p>4</p> </td> 
   <td><p>4</p> </td> 
  </tr> 
 </tbody> 
</table>

### 인코딩된 비디오 파일 형식 {#encoded-video-file-format}

Dynamic Media에서는 MP4 H.264 비디오 인코딩 사전 설정을 사용하는 것이 좋습니다. MP4 파일은 H.264 비디오 코덱을 사용하기 때문에 고품질의 비디오를 제공하지만 압축된 파일 크기로 제공합니다.

## YouTube에 비디오 게시 {#publishing-videos-to-youtube}

온-프레미스 AEM 비디오 자산을 이전에 만든 YouTube 채널에 직접 게시할 수 있습니다.

비디오 자산을 YouTube에 게시하려면 태그가 있는 AEM Assets을 설정합니다. 이러한 태그를 YouTube 채널과 연관시킵니다. 비디오 자산의 태그가 YouTube 채널의 태그와 일치하면 비디오가 YouTube에 게시됩니다. 비디오 자산에 태그가 없으면 YouTube에 게시되지 않습니다.

YouTube에 게시하면 AEM에서 처리 프로필 시스템을 우회하므로 비디오 인코딩 프로필도 무시됩니다. 이 바이패스는 YouTube에 자체 인코딩이 있으므로 비디오 처리 프로필이 필요하지 않습니다. 그러나 대부분의 경우 비디오 자산 처리 프로필을 이미 경험했을 것입니다. 비디오 처리 프로필을 건너뛰고 YouTube에 바로 게시할 경우 AEM Asset의 비디오 자산에서 볼 수 있는 축소판이 표시되지 않습니다. 즉, dynamic media 실행 모드에서 실행되는 경우 인코딩되지 않은 비디오가 Dynamic Media 자산 유형에서 작동하지 않습니다.

YouTube 서버에 비디오 자산을 게시하려면 YouTube을 사용하여 안전하고 안전한 서버 간 인증을 위해 다음 작업을 완료해야 합니다.

1. [Google Cloud 설정 구성](#configuring-google-cloud-settings)
1. [YouTube 채널 만들기](#creating-a-youtube-channel)
1. [게시할 태그 추가](#adding-tags-for-publishing)
1. [YouTube 게시 복제 에이전트 활성화](#enabling-the-youtube-publish-replication-agent)
1. [AEM에서 YouTube 설정](#setting-up-youtube-in-aem)
1. [(선택 사항) 업로드된 비디오에 대한 기본 YouTube 속성 설정을 자동화합니다](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [YouTube 채널에 비디오 게시](#publishing-videos-to-your-youtube-channel)
1. [(선택 사항) YouTube에서 게시된 비디오를 확인합니다](video.md#optional-verifying-the-published-video-on-youtube)
1. [웹 애플리케이션에 YouTube URL 연결](#linking-youtube-urls-to-your-web-application)

다음을 수행할 수도 있습니다 [YouTube에서 제거할 비디오 게시 취소](#unpublishing-videos-to-remove-them-from-youtube).

### Google Cloud 설정 구성 {#configuring-google-cloud-settings}

YouTube에 게시하려면 Google 계정이 필요합니다. GMAIL 계정이 있는 경우 이미 Google 계정이 있습니다. Google 계정이 없는 경우 쉽게 만들 수 있습니다. 비디오 자산을 YouTube에 게시하려면 자격 증명이 필요하므로 계정이 필요합니다. 이미 만든 계정이 있는 경우 이 작업을 건너뛰고 다음 단계로 진행합니다 [YouTube 채널 만들기](#creating-a-youtube-channel).

>[!NOTE]
>
>다음 단계는 이 작성 시 정확했습니다. 그러나 Google은 사전 통지 없이 정기적으로 웹 사이트를 업데이트합니다. 따라서 이러한 단계는 약간 다를 수 있습니다.

**Google Cloud 설정을 구성하려면:**

1. 새 Google 계정을 만듭니다.

   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   이미 Google 계정이 있는 경우 다음 단계로 건너뜁니다.

1. 이동 [https://cloud.google.com/](https://cloud.google.com/).
1. Google Cloud Platform 페이지의 상단 근처에 있는 **[!UICONTROL 콘솔]**. 필요한 경우 **로그인** Google 계정 자격 증명 사용.
1. 설정 **[!UICONTROL 대시보드]** 페이지, 탭 **[!UICONTROL 프로젝트 만들기]**.
1. 에서 **[!UICONTROL 새 프로젝트]** 대화 상자에서 프로젝트 이름을 입력합니다.

   프로젝트 ID는 프로젝트 이름을 기반으로 합니다. 따라서 프로젝트 이름을 신중하게 선택합니다. 만든 후에는 변경할 수 없습니다. 또한 나중에 Adobe Experience Manager에서 YouTube을 설정할 때 동일한 프로젝트 ID를 다시 입력해야 합니다. 프로젝트의 ID를 기록할 수 있습니다.
1. 탭 **[!UICONTROL 만들기]**.

1. 프로젝트의 **[!UICONTROL 대시보드]**&#x200B;에서 **[!UICONTROL 시작하기]** 카드, 탭 **[!UICONTROL API를 활성화하고 키와 같은 자격 증명을 가져옵니다]**.
1. 위쪽 **[!UICONTROL 대시보드]** 페이지, 탭 **[!UICONTROL API 활성화]**.
1. 설정 **[!UICONTROL 라이브러리]** 페이지, YouTube API에서 탭 **[!UICONTROL YouTube 데이터 API]**.
1. 위쪽 **[!UICONTROL YouTube 데이터 API v3]** 페이지, 탭 **[!UICONTROL 활성화]** 켜는 중입니다.
1. API를 사용하려면 자격 증명이 필요할 수 있습니다. 필요한 경우 **[!UICONTROL 자격 증명 만들기]**.
1. 에서 **[!UICONTROL API는 어디에서 호출합니까?]** 드롭다운 목록에서 **[!UICONTROL 웹 서버(예: node.js, Tomcat)]**.
1. 아래 **[!UICONTROL 어떤 데이터에 액세스하시겠습니까?]** 선택 **[!UICONTROL 사용자 데이터]**.
1. 탭 **[!UICONTROL 어떤 자격 증명이 필요합니까?]** 단추.
1. 아래에 **[!UICONTROL OAuth 2.0 클라이언트 ID 만들기]** 제목을 입력하고 고유 이름을 입력합니다.
1. 다음 아래의 텍스트 필드에서 **[!UICONTROL 인증된 Javascript 원본]** 제목을 입력하고 경로에 있는 고유한 도메인과 포트 번호를 대체하는 다음 키를 누릅니다 **[!UICONTROL Enter 키]** 목록에 경로를 추가하려면 다음을 수행합니다.

   `https://<servername.domain>:<port_number>`

   예, `https://1a2b3c.mycompany.com:4321`

   **참고**: 위의 경로 예제는 그림 용도로만 사용됩니다.

1. 다음 아래의 텍스트 필드에서 **[!UICONTROL 허가된 리디렉션 URI]** 제목을 입력하고 경로에 고유한 도메인과 포트 번호를 대체한 다음 Enter 키를 눌러 목록에 경로를 추가합니다.

   `https://<servername.domain>:<port#>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   예, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **참고**: 위의 경로 예제는 그림 용도로만 사용됩니다.

1. 탭 **[!UICONTROL 클라이언트 ID 만들기]**.
1. 자격 증명 페이지의 **[!UICONTROL OAuth 2.0 동의 화면 설정]** 제목에서 현재 사용 중인 Gmail 주소를 선택합니다.
1. 다음 아래의 텍스트 필드에서 **[!UICONTROL 사용자에게 표시되는 제품 이름]** 제목, 동의 화면에 표시할 내용을 입력합니다.

   AEM 관리자가 YouTube을 인증할 때 동의 화면이 표시됩니다. AEM은 YouTube에 권한을 요청하십시오.

1. 탭 **[!UICONTROL 계속]**.
1. 아래에 **[!UICONTROL 자격 증명 다운로드]** 제목, 탭 **[!UICONTROL 다운로드]**.
1. 를 저장합니다 `client_id.json` 파일.

   나중에 Adobe Experience Manager에서 YouTube을 설정할 때 이 다운로드한 json 파일이 필요합니다.

1. 탭 **[!UICONTROL 완료]**.

   이제 YouTube 채널을 만듭니다.

### YouTube 채널 만들기 {#creating-a-youtube-channel}

YouTube에 비디오를 게시하려면 하나 이상의 채널이 있어야 합니다. YouTube 채널을 이미 만든 경우 이 작업을 건너뛰고 로 이동할 수 있습니다. **게시할 태그 추가**.

>[!CAUTION]
>
>YouTube &amp;ast;before&amp;ast;에서 이미 하나 이상의 채널을 설정했는지 확인하십시오 AEM의 YouTube 설정에서 채널을 추가합니다( [AEM에서 YouTube 설정](#setting-up-youtube-in-aem) 아래에 표시됩니다. 이 작업을 수행하지 않으면 기존 채널에 대한 경고가 표시되지 않습니다. 그러나 채널을 추가할 때는 Google 인증이 계속 발생하지만 비디오가 전송되는 채널을 선택할 수 있는 옵션이 없습니다.

**YouTube 채널을 만들려면:**

1. 이동 [https://www.youtube.com](https://www.youtube.com/) Google 계정 자격 증명을 사용하여 로그인합니다.
1. YouTube 페이지의 오른쪽 위 모서리에서 프로필 사진(단색 원 내에 문자로 표시될 수 있음)을 탭한 다음 **[!UICONTROL YouTube 설정]** (라운드 톱니바퀴 아이콘).
1. 설정 **[!UICONTROL 개요]** 페이지, 아래에 **[!UICONTROL 추가 기능]** 제목, 탭 **[!UICONTROL 내 채널을 모두 보거나 새 채널 만들기]**.
1. 설정 **[!UICONTROL 채널]** 페이지, 탭 **[!UICONTROL 새 채널 만들기]**.
1. 설정 **[!UICONTROL 브랜드 계정]** 페이지, **[!UICONTROL 브랜드 계정 이름]** 필드에서 비즈니스 이름 또는 비디오 자산을 게시할 다른 채널 이름을 입력한 다음 탭합니다 **[!UICONTROL 만들기]**.

   AEM에서 YouTube을 설정할 때 다시 입력해야 하므로 여기에 입력하는 이름을 기억하십시오.

1. (선택 사항) 필요한 경우 채널을 더 추가합니다.

   이제 게시할 태그를 추가합니다.

### 게시할 태그 추가 {#adding-tags-for-publishing}

비디오를 YouTube에 게시하기 위해 AEM은 태그를 하나 이상의 YouTube 채널에 연결합니다. 게시할 태그를 추가하려면 [태그 관리](/help/sites-administering/tags.md).

또는 AEM에서 기본 태그를 사용하려는 경우 이 작업을 건너뛰고 로 이동할 수 있습니다. [YouTube 게시 복제 에이전트 활성화](#enabling-the-youtube-publish-replication-agent).

### YouTube 게시 복제 에이전트 활성화 {#enabling-the-youtube-publish-replication-agent}

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 탭한 다음 왼쪽 레일에서 를 탭합니다 **[!UICONTROL 도구 > 배포 > 복제 > 작성자의 에이전트]**.
1. 설정 **[!UICONTROL 작성자 에이전트]** 페이지, 탭 **[!UICONTROL YouTube 게시(youtube)]**.
1. 도구 모음의 설정 오른쪽의 **[!UICONTROL 편집]**.
1. 을(를) 선택합니다 **[!UICONTROL 활성화됨]** 복제 에이전트를 켜는 확인란
1. 탭 **[!UICONTROL 확인]**.

   이제 AEM에서 YouTube을 설정합니다.

### AEM에서 YouTube 설정 {#setting-up-youtube-in-aem}

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 탭한 다음 왼쪽 레일에서 를 탭합니다 **[!UICONTROL 도구 > 배포 > Cloud Services]**.
1. 아래에 **[!UICONTROL 타사 서비스]** 제목, YouTube 아래 **[!UICONTROL 지금 구성]**.
1. 에서 **[!UICONTROL 구성 만들기]** 대화 상자에서 각 필드에 제목(필수)과 이름(선택 사항)을 입력합니다.
1. 탭 **[!UICONTROL 만들기]**.
1. 에서 **[!UICONTROL YouTube 계정 설정]** 대화 상자, **[!UICONTROL 응용 프로그램 이름]** 필드에 Google 프로젝트 ID를 입력합니다.

   처음에 Google Cloud 설정을 구성할 때 프로젝트 ID를 지정했습니다.

   을(를) 종료하십시오. **[!UICONTROL YouTube 계정 설정]** 대화 상자가 열립니다. 곧 다시 돌아올 겁니다

1. 일반 텍스트 편집기를 사용하여 Google Cloud 설정 구성 작업에서 이전에 다운로드하여 저장한 JSON 파일을 엽니다.
1. 전체 JSON 텍스트를 선택하고 복사합니다.
1. 로 돌아갑니다. **[!UICONTROL YouTube 계정 설정]** 대화 상자 In the **[!UICONTROL JSON Config]** field, paste the JSON text.
1. 탭 **[!UICONTROL 확인]**.

   이제 AEM에서 YouTube 채널을 설정합니다.

1. To the right of **[!UICONTROL Available Channels]**, tap **[!UICONTROL +]** (plus sign icon).
1. 에서 **[!UICONTROL YouTube 채널 설정]** 대화 상자, **[!UICONTROL 제목]** 필드에서 작업에서 만든 채널의 이름을 입력합니다 **C[!UICONTROL YouTube 채널 만들기]** 더 일찍

   원하는 경우 설명을 선택적으로 추가할 수 있습니다.

1. 탭 **[!UICONTROL 확인]**.
1. YouTube/Google 인증이 표시됩니다. Google Cloud 계정에 아직 로그인하지 않은 경우 이 단계를 건너뜁니다.

   * Google 프로젝트 ID 및 위의 JSON 텍스트와 연결된 Google 사용자 이름 및 암호를 입력합니다.
   * 계정에 두 개 이상의 항목이 표시되는 채널 수에 따라 다릅니다. 채널을 선택합니다. 전자 메일 주소를 선택하지 마십시오.
   * 다음 페이지에서 **[!UICONTROL 수락]** 이 채널에 대한 액세스를 허용합니다.

1. 탭 **[!UICONTROL 허용]**.

   이제 게시할 태그를 설정합니다.

1. **게시할 태그 설정** - **[!UICONTROL Cloud Services > YouTube]** 페이지에서 **[!UICONTROL 연필]** 아이콘을 사용하여 사용할 태그 목록을 편집합니다.
1. 드롭다운 목록 아이콘(위/아래로 캐럿)을 탭하여 AEM에서 사용 가능한 태그 목록을 표시합니다.
1. 태그를 하나 이상 탭하여 추가합니다.

   추가한 태그를 삭제하려면 태그를 선택하고 **[!UICONTROL X]**.

1. 원하는 태그 추가를 마치면 를 누릅니다 **[!UICONTROL 확인]**.

   이제 비디오를 YouTube 채널에 게시합니다.

### (선택 사항) 업로드된 비디오에 대한 기본 YouTube 속성 설정을 자동화합니다 {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

비디오 업로드 시 YouTube 속성 설정을 자동화할 수 있습니다. AEM에서 메타데이터 처리 프로필을 만들어 이 작업을 수행합니다.

To create the metadata processing profile, you are first going to copy values from the **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]**, and **[!UICONTROL Choices]** fields, all found in Metadata Schemas for video. Then, you will build your YouTube video metadata processing profile by adding those values to it.

**선택적으로 업로드한 비디오에 대한 기본 YouTube 속성 설정을 자동화하려면,**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 탭한 다음 왼쪽 레일에서 를 탭합니다 **[!UICONTROL 도구 > 자산 > 메타데이터 스키마]**.
1. 탭 **[!UICONTROL 기본]**. (선택 상자에 &quot;기본값&quot; 왼쪽에 선택 표시를 추가하지 마십시오.)
1. 설정 **[!UICONTROL 기본]** 페이지의 왼쪽에 있는 상자를 선택합니다. **[!UICONTROL 비디오]**&#x200B;를 탭한 다음, **[!UICONTROL 편집]**.
1. 설정 **[!UICONTROL 메타데이터 스키마 편집기]** 페이지에서 **[!UICONTROL 고급]** 탭.
1. YouTube 게시 제목 아래에서 **[!UICONTROL YouTube 카테고리]**. (YouTube 카테고리 드롭다운 목록을 탭하지 마십시오.)
1. 페이지 오른쪽의 아래에서 **[!UICONTROL 설정]** 탭에서 다음을 수행합니다.

   * 에서 **[!UICONTROL 필드 레이블]** 텍스트 필드에서 값을 선택하고 복사합니다.

      복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * 에서 **[!UICONTROL 속성에 매핑]** 텍스트 필드에서 값을 선택하고 복사합니다.

      복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * 아래 **[!UICONTROL 선택 사항]**&#x200B;을(를) 선택하고 사용할 기본값(예: 사용자 및 블로그 또는 과학 및 기술)을 복사합니다.

      복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

1. YouTube 게시 제목 아래에서 **[!UICONTROL YouTube 개인 정보]**. (YouTube 개인 정보 보호 드롭다운 목록을 탭하지 마십시오.)
1. 페이지 오른쪽의 아래에서 **[!UICONTROL 설정]** 탭에서 다음을 수행합니다.

   * 에서 **[!UICONTROL 필드 레이블]** 텍스트 필드에서 값을 선택하고 복사합니다.

      복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * 에서 **[!UICONTROL 속성에 매핑]** 텍스트 필드에서 값을 선택하고 복사합니다.

      복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * 아래 **[!UICONTROL 선택 사항]**&#x200B;을(를) 선택하고 사용할 기본값을 복사합니다. 선택 사항은 두 쌍으로 그룹화됩니다. 쌍의 맨 아래 필드는 공용, 비상장 또는 개인 등의 복사할 기본값입니다.

      복사한 값을 열려 있는 텍스트 편집기에 붙여넣습니다. 메타데이터 처리 프로필을 만들 때 나중에 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

1. 의 오른쪽 위 모서리 근처에 있습니다. **[!UICONTROL 메타데이터 스키마 편집기]** 페이지, 탭 **[!UICONTROL 취소]**.
1. AEM의 왼쪽 위 모서리에서 AEM 로고를 탭한 다음 왼쪽 레일에서 를 탭합니다 **[!UICONTROL 도구 > 자산 > 메타데이터 프로필]**.

1. 설정 **[!UICONTROL 메타데이터 프로필]** 페이지의 오른쪽 위 모서리 근처에 있는 페이지를 탭합니다. **[!UICONTROL 만들기]**. 에서 **[!UICONTROL 메타데이터 프로필 추가]** 대화 상자, **[!UICONTROL 프로필 제목]** 텍스트 필드에 이름을 입력합니다 `YouTube Video`.
1. 설정 **[!UICONTROL 메타데이터 프로필 편집기]** 페이지에서 **[!UICONTROL 고급]** 탭.
1. 다음을 수행하여 복사된 YouTube 게시 값을 프로필에 추가합니다.

   * 페이지 오른쪽에서 **[!UICONTROL 양식 작성]** 탭.
   * 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 섹션 헤더]** 왼쪽에 놓고 양식 영역에 놓습니다.
   * 탭 **[!UICONTROL 필드 레이블]** 를 클릭하여 구성 요소를 선택합니다.
   * 페이지 오른쪽의 아래에서 **[!UICONTROL 설정]** 탭, **[!UICONTROL 필드 레이블]** 텍스트 필드, 입력 `YouTube Publishing`.
   * 탭하기 **[!UICONTROL 양식 작성]** 탭을 클릭한 다음 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 단일 행 텍스트]** 아래에 놓고 **[!UICONTROL YouTube 게시]** 방금 만든 제목.
   * 탭 **[!UICONTROL 필드 레이블]** 를 클릭하여 구성 요소를 선택합니다.
   * 페이지 오른쪽의 아래에서 **[!UICONTROL 설정]** 탭에서 붙여넣습니다. **[!UICONTROL YouTube 게시]** 값 (**[!UICONTROL 필드 레이블]** 값 및 **[!UICONTROL 속성에 매핑]** 값)을 반환해야 합니다. 붙여넣기 **[!UICONTROL 선택 사항]** 값 **[!UICONTROL 기본값]** 필드.

1. 다음을 수행하여 복사된 YouTube 개인 정보 보호 값을 프로필에 추가합니다.

   * 페이지 오른쪽에서 **[!UICONTROL 양식 작성]** 탭.
   * 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 섹션 헤더]** 왼쪽에 놓고 양식 영역에 놓습니다.
   * 탭 **[!UICONTROL 필드 레이블]** 를 클릭하여 구성 요소를 선택합니다.
   * 페이지 오른쪽의 설정 탭의 필드 레이블 텍스트 필드에 를 입력합니다. `YouTube Privacy`.
   * 탭하기 **[!UICONTROL 양식 작성]** 탭을 클릭한 다음 레이블이 지정된 구성 요소를 드래그합니다. **[!UICONTROL 단일 행 텍스트]** 아래에 놓고 **[!UICONTROL YouTube 개인 정보]** 방금 만든 제목.
   * 탭 **[!UICONTROL 필드 레이블]** 를 클릭하여 구성 요소를 선택합니다.
   * 페이지 오른쪽의 아래에서 **[!UICONTROL 설정]** 탭에서 붙여넣습니다. **[!UICONTROL YouTube 게시]** 값 (**[!UICONTROL 필드 레이블]** 값 및 **[!UICONTROL 속성에 매핑]** 값)을 반환해야 합니다. 붙여넣기 **[!UICONTROL 선택 사항]** 값 **[!UICONTROL 기본값]** 필드.

1. 페이지의 오른쪽 위 모서리 근처에 있는 탭하기 **[!UICONTROL 저장]**.
1. 비디오를 업로드할 폴더에 YouTube 게시 메타데이터 프로필을 적용합니다. 메타데이터 프로필과 비디오 프로필 세트가 모두 있어야 합니다.

   See [Metadata Profiles](metadata-profiles.md) and [Video Profiles](video-profiles.md).

### YouTube 채널에 비디오 게시 {#publishing-videos-to-your-youtube-channel}

이제 이전에 비디오 자산에 추가한 태그를 연결합니다. 이 프로세스를 통해 AEM에서 YouTube 채널에 게시할 자산을 알 수 있습니다.

YouTube에서 컨텐츠를 게시하기 위해 AEM에서는 **[!UICONTROL YouTube에 게시]** 작업 과정: 진행 상황을 모니터링하고 실패 정보를 볼 수 있습니다.
See [Monitoring video encoding and YouTube publishing progress](#monitoring-video-encoding-and-youtube-publishing-progress).

**비디오를 YouTube 채널에 게시하려면:**

1. AEM에서 YouTube 채널에 게시할 비디오 자산으로 이동합니다.
1. 비디오 자산을 선택합니다.

   선택한 비디오 자산(예: 원본 소스 비디오 또는 인코딩된 표현물)에 관계없이 원래 소스 비디오는 항상 업로드됩니다.

1. 도구 모음에서 **[!UICONTROL 속성]**.
1. 에서 **[!UICONTROL 기본]** 탭의 메타데이터 제목 아래에서 을 누릅니다 **[!UICONTROL 찾아보기]** 오른쪽 **[!UICONTROL 태그]** 필드.
1. 설정 **[!UICONTROL 태그 선택]** 페이지에서 사용할 태그로 이동한 다음, 하나 이상의 태그를 선택합니다.
1. 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 확인]** 아이콘.
1. 비디오 속성 페이지의 오른쪽 위 모서리에서 을(를) 탭합니다 **[!UICONTROL 저장]**.
1. 도구 모음에서 **[!UICONTROL 게시 > 게시]**.

   YouTube 채널에서 게시된 비디오를 선택적으로 확인할 수 있습니다.

### (선택 사항) YouTube에서 게시된 비디오를 확인합니다 {#optional-verifying-the-published-video-on-youtube}

YouTube 게시(또는 게시 취소)의 진행 상황을 모니터링할 수 있습니다.

See [Monitoring video encoding and YouTube publishing progress](#monitoring-video-encoding-and-youtube-publishing-progress).

게시 시간은 마스터 비디오의 형식, 파일 크기 및 업로드 트래픽이 포함된 여러 요인에 따라 크게 달라질 수 있습니다. 게시 프로세스는 몇 분에서 몇 시간 정도 걸릴 수 있습니다. 또한 고해상도 포맷이 훨씬 느리게 렌더링된다는 점도 유념하십시오. 예를 들어 720p와 1080p는 480p보다 훨씬 오래 걸립니다.

8시간 후에도 상태 메시지에 **[!UICONTROL 업로드됨(처리 중입니다. 잠시 기다려 주십시오.)]**&#x200B;사이트에서 비디오를 제거하고 다시 업로드해 보십시오.

### 웹 애플리케이션에 YouTube URL 연결 {#linking-youtube-urls-to-your-web-application}

비디오를 게시한 후 Dynamic Media에서 생성한 YouTube URL 문자열을 가져올 수 있습니다. YouTube URL을 복사하면 클립보드에 로드되므로 웹 사이트 또는 애플리케이션의 페이지에 필요에 따라 붙여넣을 수 있습니다.

YouTube URL은 비디오 자산을 YouTube에 게시하기 전까지 복사할 수 없습니다.

**YouTube URL을 웹 애플리케이션에 연결하려면**

1. YouTube으로 이동합니다 *게시됨* 복사할 URL이 있는 비디오 자산을 선택한 다음 선택합니다.

   YouTube URL은 복사에만 사용할 수 있습니다 *after* 먼저 *게시됨* 비디오 자산을 YouTube에 추가합니다.

1. 도구 모음에서 **[!UICONTROL 속성]**.
1. 탭하기 **[!UICONTROL 고급]** 탭.
1. 아래에 **[!UICONTROL YouTube 게시]** 제목, **[!UICONTROL YouTube URL]** 목록에서 URL 텍스트를 선택하고 웹 브라우저에 복사하여 자산을 미리 보거나 웹 컨텐츠 페이지에 추가할 수 있습니다.

### YouTube에서 제거할 비디오 게시 취소 {#unpublishing-videos-to-remove-them-from-youtube}

AEM에서 비디오 자산 게시를 취소하면 비디오가 YouTube에서 제거됩니다.

>[!CAUTION]
>
>YouTube 내에서 직접 비디오를 제거하는 경우, AEM은 인식하지 못하며 비디오가 YouTube에 아직 게시되어 있는 것처럼 계속 동작합니다. 항상 AEM을 통해 YouTube에서 비디오 자산 게시를 취소합니다.

YouTube에서 컨텐츠를 제거하려면 AEM에서는 **[!UICONTROL YouTube에서 게시 취소]** 작업 과정: 진행 상황을 모니터링하고 실패 정보를 볼 수 있습니다.
See [Monitoring video encoding and YouTube publishing progress](#monitoring-video-encoding-and-youtube-publishing-progress).

**YouTube에서 제거할 비디오 게시를 취소하려면,**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 탭한 다음 왼쪽 레일에서 를 탭합니다 **[!UICONTROL 도구]** > **[!UICONTROL 자산]**.
1. YouTube 채널에서 게시를 취소하려는 비디오 자산으로 이동합니다.
1. 자산 선택 모드에서 하나 이상의 게시된 비디오 자산을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 게시 취소]** > **[!UICONTROL 게시 취소]**.

## Monitoring video encoding and YouTube publishing progress {#monitoring-video-encoding-and-youtube-publishing-progress}

새 비디오를 비디오 인코딩이 적용된 폴더에 업로드하거나 비디오를 Youtube에 게시하면 다양한 방법으로 비디오 인코딩/youtube 게시가 진행(또는 실패)되고 있음을 모니터링할 수 있습니다. 실제 YouTube 게시 진행 상태는 로그를 통해서만 사용할 수 있지만 실패 또는 성공 여부는 다음 절차에 설명된 추가 방법으로 나열되어 있습니다. 또한 YouTube 게시 워크플로우 또는 비디오 인코딩이 완료되거나 중단되면 이메일 알림을 받을 수 있습니다.

### 진행 상태 모니터링 {#monitoring-progress}

진행 상황을 모니터링하려면(실패한 인코딩/YouTube 게시 포함):

1. 자산 폴더에서 비디오 인코딩 진행 상태 보기:

   * in **[!UICONTROL 카드 보기]**, 비디오 인코딩 진행 상태가 백분율로 자산에 표시됩니다. 오류가 있으면 이 정보가 자산에도 표시됩니다.

      ![chlimage_1-429](assets/chlimage_1-429.png)

   * in **[!UICONTROL 목록 보기]**, 비디오 인코딩 진행 상태는 **[!UICONTROL 처리 상태]** 열. If there is an error, this message displays in that same column.

      ![chlimage_1-430](assets/chlimage_1-430.png)

      This column does not display by default. 열을 활성화하려면 **[!UICONTROL 설정 보기]** 에서 **[!UICONTROL 보기 횟수]** 드롭다운 메뉴를 추가하고 **[!UICONTROL 처리 상태]** 열 및 탭 **[!UICONTROL 업데이트]**.

      ![chlimage_1-431](assets/chlimage_1-431.png)

1. 자산 세부 정보에서 진행 상황을 봅니다. 자산을 탭할 때 드롭다운 메뉴를 열고 을 선택합니다 **[!UICONTROL 타임라인]**. 인코딩 또는 YouTube 게시과 같은 워크플로우 활동으로 범위를 좁히려면 **[!UICONTROL 워크플로우]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   인코딩과 같은 모든 워크플로우 정보는 타임라인에 표시됩니다. YouTube 게시의 경우 **[!UICONTROL 워크플로우]** 타임라인에는 YouTube 채널의 이름과 YouTube 비디오 URL도 포함되어 있습니다. 또한 **[!UICONTROL 워크플로우]** 타임라인 .

   >[!NOTE]
   >
   >의 여러 워크플로우 구성으로 인해 실패/오류 메시지를 최종적으로 기록하는 데 시간이 오래 걸릴 수 있습니다 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]**, 및 **[!UICONTROL timeout]** 변환 전: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), 예:
   >
   >* Apache Sling 작업 큐 구성
   >* Adobe Granite Workflow 외부 프로세스 작업 처리기
   >* Granite 워크플로우 시간 초과 큐

   > 
   >You may adjust the **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, and **[!UICONTROL timeout]** properties in these configurations.

1. 진행 중인 워크플로우에 대해서는 **워크플로우 인스턴스** 사용 가능한 **[!UICONTROL 도구 > 워크플로우 > 인스턴스]**.

   >[!NOTE]
   >
   >에 액세스하려면 관리 권한이 필요할 수 있습니다 **[!UICONTROL 도구]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   인스턴스를 선택하고 을(를) 누릅니다 **[!UICONTROL 기록 열기]**.

   ![chlimage_1-434](assets/chlimage_1-434.png)

   에서 **[!UICONTROL 워크플로우 인스턴스]** 영역에서는 워크플로우를 일시 중단, 종료 또는 이름 바꿀 수도 있습니다. 자세한 내용은 [워크플로우 관리](/help/sites-administering/workflows-administering.md) 추가 정보.

1. 실패한 작업에 대해서는 **워크플로우 실패** 사용 가능한 **[!UICONTROL 도구 > 워크플로우 > 실패]**. The **[!UICONTROL Workflow Failure]** lists all failed workflow activities.

   >[!NOTE]
   >
   >에 액세스하려면 관리 권한이 필요할 수 있습니다 **[!UICONTROL 도구]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >의 여러 워크플로우 구성으로 인해 오류 메시지가 마지막으로 기록되는 데 시간이 오래 걸릴 수 있습니다 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]**, 및 **[!UICONTROL timeout]** 변환 전: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), 예:
   >
   >* Apache Sling 작업 큐 구성
   >* Adobe Granite Workflow 외부 프로세스 작업 처리기
   >* Granite 워크플로우 시간 초과 큐

   >
   >You may adjust the **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, and **[!UICONTROL timeout]** properties in these configurations.

1. 완료된 워크플로우에 대해서는 **[!UICONTROL 워크플로우 아카이브]** 사용 가능한 **[!UICONTROL 도구 > 워크플로우 > 아카이브]**. The **[!UICONTROL Workflow Archive]** lists all completed workflow activities.

   에 액세스하려면 관리 권한이 필요할 수 있습니다 **[!UICONTROL 도구]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. 중단되거나 실패한 워크플로우 작업에 대한 이메일 알림을 받을 수 있습니다. 관리자가 이러한 이메일 알림을 구성할 수 있습니다.
자세한 내용은 [이메일 알림 구성](#configuring-e-mail-notifications).

#### 전자 메일 알림 구성 {#configuring-e-mail-notifications}

에 액세스하려면 관리 권한이 필요할 수 있습니다 **[!UICONTROL 도구]** 메뉴 아래의 제품에서 사용할 수 있습니다.

알림을 구성하는 방법은 인코딩 작업 또는 YouTube 게시 작업에 대한 알림을 원하는 지에 따라 다릅니다.

* 인코딩 작업의 경우 모든 AEM 워크플로우 이메일 알림에 대한 구성 페이지에 액세스할 수 있습니다. **[!UICONTROL 도구 > 작업 > 웹 콘솔]** 그리고 **[!UICONTROL Day CQ Workflow Email Notification Service]**. 자세한 내용은 [AEM에서 이메일 알림 구성](/help/sites-administering/notification.md). 확인란을 선택하거나 취소할 수 있습니다 **[!UICONTROL 중단 시 알림]** 또는 **[!UICONTROL 완료 시 알림]** 따라서,

* YouTube 게시 작업의 경우 다음을 수행합니다.

1. AEM에서 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]**.
1. 을(를) 선택합니다 **[!UICONTROL YouTube에 게시]** workflow를 수행한 다음 **[!UICONTROL 편집]**.
1. 마우스 오른쪽 단추를 클릭합니다. **[!UICONTROL YouTube 업로드]** 워크플로우 단계, 탭 **[!UICONTROL 편집]**.
1. 탭하기 **[!UICONTROL 인수]s** 탭.
1. 다음 확인란을 선택하거나 취소할 수 있습니다.

   * **[!UICONTROL 게시 시작]**
   * **[!UICONTROL 게시 실패]**
   * **[!UICONTROL 게시 완료]**- 채널 및 URL에 대한 정보를 포함합니다

   확인란을 지우는 것은 YouTube 게시 워크플로우에서 지정된 이메일 알림을 받지 못함을 의미합니다.

   >[!NOTE]
   >
   >이러한 이메일은 YouTube에만 해당되며 일반 워크플로우 이메일 알림 외에도 제공됩니다. 그 결과, 두 세트의 이메일 알림 즉, **Day CQ Workflow Email Notification Service** 구성 설정에 따라 YouTube에만 적용되는 구성 및 세트를 선택할 수 있습니다.

## 비디오 보고서 보기 {#viewing-video-reports}

비디오 보고서는 Dynamic Media - 하이브리드 모드를 실행할 때 사용할 수 있습니다. Dynamic Media - Scene7 모드를 실행할 때에는 보고서를 사용할 수 없습니다.

비디오 보고서에는 지정된 기간 동안 여러 개의 집계 지표가 표시되어 *게시된 *개별 및 집계 비디오가 예상대로 작동하는지 모니터링할 수 있습니다. 다음 상위 지표 데이터는 전체 웹 사이트에서 게시된 모든 비디오에 대해 집계됩니다.

* 비디오 시작
* 완료율
* 비디오의 평균 시간
* 비디오의 총 시간
* 방문당 비디오 수

테이블 *게시됨* 비디오도 나열되므로 총 비디오 시작을 기반으로 웹 사이트에서 가장 많이 본 비디오를 추적할 수 있습니다.

목록에서 비디오 이름을 탭하면 비디오의 대상 유지(드롭다운) 보고서가 라인 차트 형태로 표시됩니다. 차트는 비디오 재생 중 지정된 시간 동안의 보기 수를 표시합니다. 비디오를 재생하면 세로 막대가 플레이어의 시간 표시기와 동기식으로 추적합니다. 라인 차트 데이터의 드롭은 대상이 관심 영역에서 이탈하는 위치를 나타냅니다.

비디오가 Adobe Experience Manager Dynamic Media 외부에 인코딩된 경우 대상 유지(드롭다운) 차트와 테이블의 재생 비율 데이터를 사용할 수 없습니다.

참조 - [Dynamic Media Cloud Services 구성](/help/assets/config-dynamic.md).

>[!NOTE]
>
>추적 및 보고 데이터는 Dynamic Media의 자체 비디오 플레이어 및 관련 비디오 플레이어 사전 설정의 사용만을 기반으로 합니다. 따라서 다른 비디오 플레이어로 재생되는 비디오를 추적하고 보고할 수 없습니다.

기본적으로 비디오 보고서를 처음 입력할 때 이 보고서는 현재 달 1일에 시작하여 현재 월의 날짜로 끝나는 비디오 데이터를 표시합니다. 그러나 고유한 날짜 범위를 지정하여 기본 날짜 범위를 무시할 수 있습니다. 다음에 비디오 보고서를 입력할 때 지정한 날짜 범위가 사용됩니다.

비디오 보고서가 올바르게 작동하려면 Dynamic Media Cloud Services이 구성되면 보고서 세트 ID가 자동으로 생성됩니다. 동시에 보고서 세트 ID가 게시 서버로 푸시되어 자산을 미리 볼 때 URL 복사 기능에 사용할 수 있습니다. 그러나 게시 서버를 이미 설정해야 합니다. 게시 서버가 설정되지 않은 경우 여전히 게시하여 비디오 보고서를 볼 수 있지만 Dynamic Media 클라우드 구성으로 돌아가 탭해야 합니다 **확인**.

**비디오 보고서를 보려면 다음을 수행하십시오.**

1. AEM의 왼쪽 위 모서리에서 AEM 로고를 탭한 다음 왼쪽 레일에서 를 탭합니다 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 비디오 보고서]**.
1. 비디오 보고서 페이지에서 다음 중 하나를 수행합니다.

   * 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 비디오 보고서 새로 고침]** 아이콘.

      보고서의 종료 날짜가 현재 날짜인 경우에만 새로 고침을 사용해야 합니다. 이렇게 하면 보고서를 마지막으로 실행한 이후 발생한 비디오 추적이 표시됩니다.

   * 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 날짜 선택기]** 아이콘.

      비디오 데이터를 저장할 시작 날짜 및 종료 날짜 범위를 지정한 다음 탭합니다 **[!UICONTROL 보고서 실행]**.
   다음 **[!UICONTROL 상위 지표]** 그룹 상자는 모든 집계 측정값을 식별합니다 *게시됨* 사이트 전체에서 비디오를 업로드합니다.

1. 게시된 상위 비디오를 나열하는 테이블에서 비디오 이름을 탭하여 비디오를 재생하고 비디오의 대상 유지(드롭다운) 보고서를 볼 수 있습니다.

### Dynamic Media HTML5 Viewer SDK를 사용하여 만든 비디오 뷰어를 기반으로 비디오 보고서를 봅니다 {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Dynamic Media에서 제공하는 기본 비디오 뷰어를 사용하거나 기본 비디오 뷰어를 기반으로 사용자 지정 뷰어 사전 설정을 만든 경우 비디오 보고서를 보는 데 추가 단계가 필요하지 않습니다. 그러나 HTML5 Viewer SDK API를 기반으로 자체 비디오 뷰어를 만든 경우 다음 단계를 사용하여 비디오 뷰어가 추적 이벤트를 Dynamic Media 비디오 보고서에 보내도록 합니다.

를 사용하십시오 [Adobe Dynamic Media 뷰어 참조 안내서](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html) 그리고 [HTML5 뷰어 SDK API](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) 자신의 비디오 뷰어를 만들 수 있습니다.

HTML5 Viewer SDK API를 사용하여 만든 비디오 뷰어를 기반으로 비디오 보고서를 보려면 다음을 수행하십시오.

1. 게시된 비디오 자산으로 이동합니다.
1. Near the upper-left corner of the asset&#39;s page, from the drop-down list, select **[!UICONTROL Viewers]**.
1. 비디오 뷰어 사전 설정을 선택하고 포함 코드를 복사합니다.
1. 포함 코드에서 다음을 사용하여 줄을 찾습니다.

   `videoViewer.setParam("config2", "<value>");`

   다음 `config2` 매개 변수를 사용하면 HTML5 뷰어에서 추적을 사용할 수 있습니다. 또한 비디오 보고 및 고객별 Adobe Analytics 구성에 대한 구성 정보가 포함된 회사별 사전 설정입니다.

   The correct value for the config2 parameter is found in both the **[!UICONTROL Embed Code]** and in the copy **[!UICONTROL URL]** function. In the URL from the copy **[!UICONTROL URL]** command, the parameter to look for is `&config2=<value>` . The value is almost always `companypreset`, but in some instances it can also be `companypreset-1`, `companypreset-2`, and so forth.

1. 사용자 지정 비디오 뷰어 코드에서 다음을 수행하여 뷰어 페이지에 AppMeasurementBridge.jsp를 추가합니다.

   * 먼저, `&preset` 매개 변수.

      만약 `config2` 매개 변수: `companypreset`, 다음을 수행합니다. *not* 필요 `&preset=parameter`.

      If `config2` 이 아니면 사전 설정 매개 변수를 와 동일하게 설정합니다. `config2` 매개 변수. 예를 들어 `config2=companypreset-2`, 추가 `&param2=companypreset-2` at.js 또는 AppMeasurementBridge.jsp URL로 마이그레이션

   * 그런 다음 AppMeasurementBridge.jsp 스크립트를 추가합니다.

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. 다음을 수행하여 TrackingManager 구성 요소를 만듭니다.

   * 호출 후 `s7sdk.Util.init();` 다음을 추가하여 이벤트를 추적할 TrackingManager 인스턴스를 만듭니다.

      `var trackingManager = new s7sdk.TrackingManager();`

   * 다음을 수행하여 구성 요소를 TrackingManager에 연결합니다.

      에서 `s7sdk.Event.SDK_READY` 이벤트 처리기에서 추적할 구성 요소를 TrackingManager에 연결합니다.

      예를 들어, 구성 요소가 `videoPlayer`, 추가

      `trackingManager.attach(videoPlayer);`

      trackingManager에 구성 요소를 첨부하기 위해 페이지에서 여러 뷰어를 추적하려면 여러 추적 관리자 구성 요소를 사용합니다.

   * 다음을 추가하여 AppMeasurementBridge 개체를 만듭니다.

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

   * 다음을 추가하여 추적 함수를 추가합니다.

      ```
      trackingManager.setCallback(appMeasurementBridge.track, 
       appMeasurementBridge);
      ```
   appMeasurementBridge 개체에는 내장된 추적 함수가 있습니다. 그러나 여러 추적 시스템 또는 기타 기능을 지원하도록 자체 코드를 제공할 수 있습니다.

<!--    For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

## 비디오에 닫힌 캡션 추가 {#adding-captions-to-video}

단일 비디오나 응용 비디오 세트에 자막을 추가하여 비디오의 범위를 글로벌 마켓플레이스로 확장할 수 있습니다. 캡션을 추가하면 오디오를 복제할 필요가 없고 다른 언어별로 오디오를 다시 녹음하기 위해 기본 스피커를 사용할 필요가 없습니다. 비디오는 녹음된 언어로 재생됩니다. 외국어 자막이 나타나므로 다른 언어를 사용하는 사람들이 오디오 부분을 계속 이해할 수 있습니다.

또한 자막은 청각 장애나 난청인 사람들에게 더 많은 접근성을 가능하게 해줍니다.

>[!NOTE]
>
>사용하는 비디오 플레이어는 캡션 표시를 지원해야 합니다.

Dynamic Media에는 캡션 파일을 JSON(JavaScript 개체 표기법) 형식으로 변환하는 기능이 있습니다. 이 전환은 JSON 텍스트를 비디오의 숨겨진 완전한 텍스트 로 웹 페이지에 포함할 수 있음을 의미합니다. 그런 다음 검색 엔진은 컨텐츠를 크롤링하고 색인화하여 비디오를 보다 손쉽게 검색할 수 있게 만들고 고객에게 비디오 컨텐츠에 대한 추가 세부 사항을 제공할 수 있습니다.

자세한 내용은 [정적(비이미지) 콘텐츠 제공](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) 에서 *Dynamic Media 이미지 제공 및 렌더링 API 도움말* 를 참조하십시오.

**비디오에 캡션 또는 자막을 추가하려면**

1. 타사 응용 프로그램 또는 서비스를 사용하여 비디오 캡션/자막 파일을 만듭니다.

   만드는 파일이 WebVTT(Web Video Text Tracks) 표준을 따르는지 확인합니다. 캡션 파일 이름 확장명은 .vtt입니다. WebVTT 캡션 표준에 대한 자세한 정보를 확인할 수 있습니다.

   자세한 내용은 [WebVTT: 웹 비디오 텍스트 트랙 형식](https://dev.w3.org/html5/webvtt/).

   Dynamic Media 외부에서 캡션/자막 파일을 작성하는 데 사용할 수 있는 무료 및 프리미엄 도구와 서비스가 모두 있습니다. 예를 들어 스타일이 없는 간단한 비디오 캡션 파일을 만들려면 다음과 같은 무료 온라인 캡션 작성 및 편집 도구를 사용할 수 있습니다.

   [WebVTT 캡션 작성기](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   최상의 결과를 얻으려면 Internet Explorer 9 이상, Google Chrome 또는 Safari에서 도구를 사용하십시오.

   도구에서 **[!UICONTROL 비디오 파일의 URL 입력]** 필드에서 복사한 비디오 파일의 URL을 붙여넣은 다음 **[!UICONTROL 로드]**. See [Obtaining a URL for an Asset](linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) to get the URL to the video file itself which you can then paste into the **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome, or Safari can then natively play back the video.

   이제 사이트에서 화면의 지침에 따라 WebVTT 파일을 작성하고 저장합니다. 완료되면 캡션 파일 내용을 복사하여 일반 텍스트 편집기에 붙여넣은 다음 .vtt 파일 확장자로 저장합니다.

   >[!NOTE]
   >
   >여러 언어로 비디오 자막을 글로벌 지원하려면 WebVTT 표준을 사용하려면 지원할 각 언어에 대해 별도의 .vtt 파일과 호출을 만들어야 합니다.

   일반적으로 캡션 VTT 파일의 이름을 비디오 파일과 같은 이름으로 지정하고 -EN 또는 -FR 또는 -DE 등의 언어 로케일에 추가하려고 합니다. 이렇게 하면 기존 웹 컨텐츠 관리 시스템을 사용하여 비디오 URL의 생성을 자동화하는 데 도움이 됩니다.

1. AEM에서 WebVTT 캡션 파일을 DAM에 업로드합니다.
1. 로 이동합니다 *게시됨* 업로드한 캡션 파일과 연결할 비디오 자산입니다.

   Remember that URLs are only available to copy *after* you have first *published* the assets.

   자세한 내용은 [자산 게시.](publishing-dynamicmedia-assets.md)

1. 다음 중 하나를 수행하십시오.

   * 팝업 비디오 뷰어 환경의 경우 **[!UICONTROL URL]**. URL 대화 상자에서 URL을 선택하여 클립보드에 복사한 다음 URL을 단순 텍스트 편집기에 복사합니다. 비디오의 복사된 URL을 다음 구문과 함께 추가합니다.

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      참고 사항 `,1` 캡션 경로의 끝입니다. 경로에서 .vtt 파일 이름 확장자 바로 다음에 를 설정하여 비디오 플레이어 모음에서 닫힌 캡션 단추를 활성화(켜기) 또는 비활성화(끄기)하는 옵션이 있습니다 `,1` 또는 `,0`각각 입니다.

   * 포함된 비디오 뷰어 환경의 경우 **[!UICONTROL 포함 코드]**. 포함 코드 대화 상자에서 포함 코드를 선택하고 클립보드에 복사한 다음 단순 텍스트 편집기에 붙여넣습니다. 복사된 포함 코드를 다음 구문과 함께 추가합니다.

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      참고 사항 `,1` 캡션 경로의 끝입니다. 경로에서 .vtt 파일 이름 확장자 바로 다음에 를 설정하여 비디오 플레이어 모음에서 닫힌 캡션 단추를 활성화(켜기) 또는 비활성화(끄기)하는 옵션이 있습니다 `,1` 또는 `,0`각각 입니다.

## 비디오에 장 마커 추가 {#adding-chapter-markers-to-video}

장 마커를 단일 비디오나 응용 비디오 세트에 추가하여 긴 양식 비디오를 더 쉽게 보고 탐색할 수 있습니다. 사용자가 비디오를 재생할 때 비디오 타임라인의 장 마커(비디오 스크러버라고도 함)를 탭하여 관심 영역으로 쉽게 이동하거나 새로운 컨텐츠, 데모, 자습서 등으로 바로 이동할 수 있습니다.

>[!NOTE]
>
>사용되는 비디오 플레이어는 장 마커 사용을 지원해야 합니다. Dynamic Media 비디오 플레이어는 장 마커를 지원하지만 타사 비디오 플레이어를 사용하지 않을 수 있습니다.

원할 경우 비디오 뷰어 사전 설정을 사용하는 대신 장을 사용하여 자신만의 사용자 지정 비디오 뷰어를 만들고 브랜드화할 수 있습니다. 장 탐색을 사용하여 고유한 HTML5 뷰어를 만드는 방법에 대한 지침은 Adobe HTML5 Viewer SDK API에서 클래스 아래의 &quot;Customizing Behavior Using Modifiers&quot; 제목을 참조하십시오 `s7sdk.video.VideoPlayer` 및 `s7sdk.video.VideoScrubber`. 자세한 내용은 [HTML5 뷰어 SDK API](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) 설명서.

캡션을 만드는 것과 거의 동일한 방식으로 비디오에 대한 장 목록을 만듭니다. 즉, WebVTT 파일을 만듭니다. 그러나 이 파일은 사용할 수도 있는 WebVTT 캡션 파일과 구분되어야 합니다. 캡션과 장을 하나의 WebVTT 파일에 결합할 수 없습니다.

다음 샘플을 사용하여 장 탐색 기능을 사용하여 WebVTT 파일을 만들 수 있습니다.

### 비디오 장 탐색 기능이 있는 WebVTT 파일 {#webvtt-file-with-video-chapter-navigation}

```xml
WEBVTT 
Chapter 1 
00:00.000 --> 01:04.364 
The bicycle store behind it all. 
Chapter 2 
01:04.364 --> 02:00.944 
Creative Cloud. 
Chapter 3 
02:00.944 --> 03:02.937 
Ease of management for a working solution. 
Chapter 4 
03:02.937 --> 03:35.000 
Cost-efficient access to rapidly evolving technology.
```

위의 예에서 `Chapter 1` 는 큐 식별자이며, 선택 사항입니다. 의 큐 시간 `00:00:000 --> 01:04:364` 장의 시작 시간과 종료 시간을 지정합니다. `00:00:000` 형식 지정 마지막 세 자리는 밀리초이며 그대로 둘 수 있습니다 `000`를 설정하는 것이 좋습니다. 의 장 제목 `The bicycle store behind it all` 는 장의 내용에 대한 실제 설명입니다. 사용자가 비디오 타임라인의 시각적 큐 포인트 위에 마우스 포인터를 놓으면 큐 식별자, 시작 큐 시간 및 장 제목이 모두 비디오 플레이어의 팝업에 나타납니다.

HTML5 비디오 뷰어를 사용하고 있으므로 만드는 장 파일이 WebVTT(Web Video Text Tracks) 표준을 따르는지 확인합니다. 장 파일 확장명은 .vtt입니다. WebVTT 캡션 표준에 대한 자세한 정보를 확인할 수 있습니다.

자세한 내용은 [WebVTT: 웹 비디오 텍스트 트랙 형식](https://dev.w3.org/html5/webvtt/)

**비디오에 장 마커를 추가하려면**

1. AEM 외부의 간단한 텍스트 편집기를 사용하여 비디오 장 파일을 만듭니다.

   영어 이외의 언어로 비디오 장을 글로벌 지원하려면 WebVTT 표준을 사용하려면 지원할 각 언어에 대해 별도의 .vtt 파일과 호출을 만들어야 합니다.

1. 를 저장합니다 `.vtt` 제목 텍스트의 문자 표현물과 관련된 문제를 방지하기 위해 UTF8 인코딩으로 파일을 사용하십시오.

   일반적으로 VTT 장의 이름을 비디오 파일과 같은 이름으로 지정하고 장에 추가하려고 합니다. 이렇게 하면 기존 웹 컨텐츠 관리 시스템을 사용하여 비디오 URL의 생성을 자동화하는 데 도움이 됩니다.
1. AEM에서 WebVTT 장 파일을 업로드합니다.

   자세한 내용은 [자산 업로드](managing-assets-touch-ui.md#uploading-assets).

1. 다음 중 하나를 수행하십시오.

   <table> 
     <tbody> 
      <tr> 
       <td>팝업 비디오 뷰어 경험의 경우</td> 
       <td> 
       <ol> 
       <li>로 이동합니다 <i>게시됨 </i>업로드한 장 파일과 연결할 비디오 자산입니다. Remember that URLs are only available to copy <i>after</i> you have first <i>published</i> the assets. 자세한 내용은 <a href="/help/assets/publishing-dynamicmedia-assets.md">자산 게시.</a></li> 
       <li>드롭다운 메뉴에서 <strong>뷰어</strong>.</li> 
       <li>왼쪽 레일에서 비디오 뷰어 사전 설정 이름을 탭합니다. 비디오 미리 보기가 별도의 페이지에 열립니다.</li> 
       <li>왼쪽 레일의 하단에서 을 누릅니다 <strong>URL</strong>.</li> 
       <li>URL 대화 상자에서 URL을 선택하여 클립보드에 복사한 다음 URL을 단순 텍스트 편집기에 복사합니다.</li> 
       <li>복사한 비디오의 URL을 다음 구문과 함께 추가하여 복사한 URL과 장 파일에 연결합니다.<br /> <br /> <code>&amp;navigation=&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;</code><br /> </li> 
      </ol> </td> 
      </tr> 
      <tr> 
       <td>포함된 비디오 뷰어 경험의 경우<br /> </td> 
       <td> 
       <ol> 
       <li>로 이동합니다 <i>게시됨 </i>업로드한 장 파일과 연결할 비디오 자산입니다. Remember that URLs are only available to copy <i>after</i> you have first <i>published</i> the assets. 자세한 내용은 <a href="/help/assets/publishing-dynamicmedia-assets.md">자산 게시.</a></li> 
       <li>드롭다운 메뉴에서 <strong>뷰어</strong>.</li> 
       <li>왼쪽 레일에서 비디오 뷰어 사전 설정 이름을 탭합니다. 비디오 미리 보기가 별도의 페이지에 열립니다.</li> 
       <li>왼쪽 레일의 하단에서 을 누릅니다 <strong>포함</strong>.</li> 
       <li>포함 코드 대화 상자에서 전체 코드를 선택하고 클립보드에 복사한 다음 단순 텍스트 편집기에 붙여넣습니다.</li> 
       <li>비디오의 포함 코드를 다음 구문과 함께 추가하여 복사한 URL과 장 파일에 연결합니다.<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li> 
      </ol> </td> 
      </tr> 
     </tbody> 
    </table>

## 비디오 축소판 정보 {#about-video-thumbnails}

Dynamic Media에서 자동으로 생성된 10개의 축소판 이미지 중 하나를 선택하여 비디오에 추가할 수 있습니다. AEM Sites, AEM Mobile 또는 AEM Screens의 작성 환경에서 비디오 자산이 Dynamic Media 구성 요소와 함께 사용되는 경우 비디오 플레이어에 선택한 축소판이 표시됩니다. 축소판은 전체 비디오의 내용을 가장 잘 나타내는 정적 그림 역할을 하며 사용자가 재생 단추를 누를 것을 권장합니다.

비디오의 총 시간을 기준으로 Dynamic Media은 10(기본값) 축소판 이미지를 비디오에 캡처합니다. 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81% 및 91%입니다. 열 축소판은 지속됩니다. 즉, 나중에 다른 축소판을 선택하더라도 시리즈를 다시 생성할 필요가 없습니다. 10개의 축소판 이미지를 미리 보고 비디오에 사용할 이미지를 선택합니다. 기본적으로 변경하려면 CRXDE Lite을 사용하여 축소판 이미지가 생성되는 시간 간격을 구성할 수 있습니다. 예를 들어 비디오에서 균일하게 배치된 네 개의 축소판 이미지만 생성하려는 경우 간격 시간을 24%, 49%, 74% 및 99%로 구성할 수 있습니다.

가장 좋은 방법은 비디오를 업로드한 후 언제든지 웹 사이트에 비디오를 게시하기 전에 비디오 축소판을 추가할 수 있는 것입니다.

Dynamic Media에서 생성된 축소판을 사용하는 대신 사용자 정의 축소판을 업로드하여 비디오를 나타낼 수 있습니다. 예를 들어, 비디오의 제목, 눈길을 끄는 개방형 이미지 또는 비디오에서 캡처한 특정 이미지가 있는 사용자 정의 축소판 이미지를 만들 수 있습니다. 업로드하는 사용자 정의 비디오 축소판 이미지는 최대 해상도가 1280 x 720픽셀(최소 너비 640픽셀)이며 2MB보다 크지 않아야 합니다.

>[!NOTE]
>
>사용자 정의 비디오 축소판은 Dynamic Media - 하이브리드 모드를 실행할 때만 사용할 수 있습니다.

### 비디오 축소판 추가 {#adding-a-video-thumbnail}

1. 비디오 축소판을 추가할 업로드된 비디오 자산으로 이동합니다.
1. 자산 선택 모드에서 **[!UICONTROL 목록 보기]** 또는 **[!UICONTROL 카드 보기]**&#x200B;를 눌러 비디오 자산을 탭합니다.
1. 도구 모음에서 **[!UICONTROL 속성 보기]** 아이콘(안에 &quot;i&quot;가 있는 원).
1. 비디오의 **[!UICONTROL 속성]** 페이지, 탭 **[!UICONTROL 축소판 변경]**.
1. 설정 **[!UICONTROL 축소판 변경]** 페이지의 도구 모음에서 탭 **[!UICONTROL 프레임 선택]**.

   Dynamic Media은 사용자 정의한 기본 시간 간격이나 시간 간격에 따라 비디오에서 시리즈 축소판 이미지를 생성합니다.

1. 생성된 축소판 이미지를 미리 보고 비디오에 추가할 이미지를 선택합니다.
1. 탭 **[!UICONTROL 변경 내용 저장]**.

   선택한 축소판을 사용하도록 비디오의 축소판 이미지가 업데이트됩니다. 나중에 축소판 이미지를 변경하기로 결정한 경우 **[!UICONTROL 축소판 변경]** 페이지를 열고 새 페이지를 선택합니다.

   새 기본 시간 간격을 구성했거나 기존 비디오를 바꾸기 위해 새 비디오를 업로드한 경우 Dynamic Media에서 미리 보기를 다시 생성해야 합니다.

   자세한 내용은 [비디오 축소판이 생성되는 기본 시간 간격 구성](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

#### 비디오 축소판이 생성되는 기본 시간 간격을 구성합니다 {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

새로운 기본 시간 간격을 구성하고 저장하면 나중에 업로드하는 비디오에만 변경 사항이 자동으로 적용됩니다. 이전에 업로드한 비디오에는 새 기본값이 자동으로 적용되지 않습니다. 기존 비디오의 경우 축소판을 다시 생성해야 합니다.

자세한 내용은 [비디오 축소판 추가](#adding-a-video-thumbnail).

비디오 축소판이 생성되는 기본 시간 간격을 구성하려면

1. In AEM, tap **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. CRXDE Lite 페이지의 왼쪽 디렉토리 패널에서 `o etc/dam/imageserver/configuration/jcr:content/settings.`

   디렉토리 패널이 표시되지 않는 경우 홈 탭 왼쪽의 >> 아이콘을 탭해야 할 수 있습니다.

1. 오른쪽 아래 패널의 **[!UICONTROL 속성]** 탭, 두 번 탭 `thumbnailtime`.
1. [축소판 표시 시간 편집] 대화 상자에서 텍스트 필드를 사용하여 간격 값을 백분율로 입력합니다.

   * 더하기 기호(+) 아이콘을 탭하여 하나 이상의 간격 값 필드를 추가합니다. 아이콘을 보려면 대화 상자 아래쪽으로 스크롤해야 할 수 있습니다.
   * 간격 값 필드 오른쪽에 있는 빼기 기호(-) 아이콘을 탭하여 목록에서 삭제합니다.
   * 위쪽 화살표 아이콘과 아래쪽 화살표 아이콘을 탭하여 간격 값을 다시 정렬합니다.

1. 탭 **[!UICONTROL 확인]** 로 돌아가기 **[!UICONTROL 속성]** 탭.
1. CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장]**&#x200B;를 입력한 다음 **[!UICONTROL 백 홈]** 아이콘을 클릭하여 AEM으로 돌아갑니다.

   자세한 내용은 [비디오 축소판 추가](#adding-a-video-thumbnail)

### 사용자 지정 비디오 축소판 추가 {#adding-a-custom-video-thumbnail}

>[!NOTE]
>
>이 기능은 Dynamic Media - 하이브리드 모드를 실행하는 경우에만 사용할 수 있습니다.

1. 비디오 축소판을 추가할 업로드된 비디오 자산으로 이동합니다.
1. 자산 선택 모드에서 **[!UICONTROL 목록 보기]** 또는 **[!UICONTROL 카드 보기]**&#x200B;를 눌러 비디오 자산을 탭합니다.
1. 도구 모음에서 **[!UICONTROL 속성 보기]** 아이콘(안에 &quot;i&quot;가 있는 원).
1. 비디오의 **[!UICONTROL 속성]** 페이지, 탭 **[!UICONTROL 축소판 변경]**.
1. 설정 **[!UICONTROL 축소판 변경]** 페이지의 도구 모음에서 탭 **[!UICONTROL 새 축소판 업로드]**.
1. 사용할 축소판 이미지로 이동하여 선택한 다음 **[!UICONTROL 열기]** AEM에 이미지 업로드를 시작하려면
1. 이미지가 성공적으로 업로드되면, **[!UICONTROL 축소판 변경]** 페이지, 탭 **[!UICONTROL 변경 내용 저장]**.

   사용자 정의 축소판이 비디오에 추가됩니다.
