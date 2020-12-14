---
title: 페이지에 Dynamic Media 자산 추가
seo-title: 페이지에 Dynamic Media 자산 추가
description: AEM에서 페이지에 Dynamic Media 구성 요소를 추가하는 방법
seo-description: AEM에서 페이지에 Dynamic Media 구성 요소를 추가하는 방법
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2829'
ht-degree: 39%

---


# 페이지에 Dynamic Media 자산 추가 {#adding-dynamic-media-assets-to-pages}

웹 사이트에서 사용하는 자산에 다이내믹 미디어 기능을 추가하려면 페이지에 직접 **Dynamic Media** 또는 **대화형 미디어** 구성 요소를 추가할 수 있습니다. 이렇게 하려면 레이아웃 모드로 전환하고 다이내믹 미디어 구성 요소를 활성화합니다. 그런 다음이 구성 요소를 페이지에 추가하고 자산을 구성 요소에 추가할 수 있습니다. 다이내믹 미디어 및 대화형 미디어 구성 요소는 편리하게도 이미지를 추가할지 아니면 비디오를 추가할지를 판단하고 그에 따라 사용 가능한 선택 사항도 달라집니다.

AEM을 WCM으로 사용하는 경우에는 다이내믹 미디어 자산을 페이지에 직접 추가합니다. WCM에 제3자를 사용하는 경우 [link](linking-urls-to-yourwebapplication.md) 또는 [embed](embed-code.md) 에셋을 참조하십시오. 응답형 제3자 웹 사이트는 응답형 사이트[에 최적화된 이미지 제공을 참조하십시오.](responsive-site.md)

>[!NOTE]
>
>AEM의 페이지에 자산을 추가하기 전에 자산을 게시해야 합니다. [Dynamic Media 자산 게시](publishing-dynamicmedia-assets.md)를 참조하십시오.

## 페이지에 Dynamic Media 구성 요소 추가 {#adding-a-dynamic-media-component-to-a-page}

페이지에 Dynamic Media 구성 요소를 추가하는 것은 페이지에 구성 요소를 추가하는 것과 같습니다. Dynamic Media 구성 요소는 다음 섹션에 자세히 설명되어 있습니다.

>[!NOTE]
>
>웹 페이지에 읽기 전용 권한이 있는 사용자가 액세스하는 Dynamic Media 구성 요소가 있으면 페이지가 중단되고 구성 요소가 올바르게 렌더링되지 않습니다. 이유는 구성 요소의 속성이 양호하고 참조된 자산 및 구성에 액세스할 수 있도록 페이지를 재구성하기 때문입니다. 그러면 페이지가 다시 렌더링되어 구성 요소가 중단됩니다.사용자의 읽기 전용 액세스 때문에 페이지의 각 구성 요소 코드를 다시 렌더링할 수 없습니다.
>  
>이 문제를 방지하려면 AEM Sites 사용자에게 에셋에 액세스할 수 있는 권한이 있는지 확인하십시오.

1. AEM에서 Dynamic Media 구성 요소를 추가할 페이지를 엽니다.
1. 페이지 왼쪽의 패널에서(사이드 패널의 표시를 전환해야 할 수 있음) **[!UICONTROL 구성 요소]** 아이콘을 클릭합니다.
1. **[!UICONTROL 구성 요소]** 머리글의 드롭다운 목록에서 **[!UICONTROL Dynamic Media]**&#x200B;을 선택합니다. 사용 가능한 Dynamic Media 구성 요소 목록이 없는 경우 사용하려는 Dynamic Media 구성 요소를 활성화해야 합니다. [Dynamic Media 구성 요소 활성화](#enabling-dynamic-media-components)를 참조하십시오.

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. 사용할 Dynamic Media 구성 요소를 원하는 위치의 페이지로 드래그합니다.
1. 마우스 포인터를 구성 요소 바로 위에 놓습니다. 구성 요소가 파란색 상자로 둘러싸인 경우 한 번 탭하여 구성 요소의 도구 모음을 표시합니다. **[!UICONTROL Configuration]** (공구모양) 아이콘을 누릅니다.
1. [필요한 ](#dynamic-media-components) 구성 요소를 편집하고 체크 표시를 클릭하여 변경 내용을 저장합니다.

### Dynamic Media 구성 요소 {#enabling-dynamic-media-components} 활성화

페이지에 추가할 수 있는 Dynamic Media 구성 요소가 없는 경우 먼저 사용할 구성 요소를 활성화해야 합니다.

1. AEM에서 Dynamic Media 구성 요소를 추가할 페이지를 엽니다.
1. 페이지 상단 근처의 도구 모음 왼쪽의 페이지 정보 아이콘을 누른 다음 드롭다운 목록에서 **[!UICONTROL 템플릿 편집]**&#x200B;을 누릅니다.

   ![편집 템플릿](/help/assets/assets-dm/edit-template.png)

1. 페이지 상단 근처의 도구 모음 오른쪽에 있는 드롭다운 목록에서 **[!UICONTROL 구조]**&#x200B;를 누릅니다.

   ![정책](/help/assets/assets-dm/structure-mode.png)

1. 페이지 하단 근처에 있는 **[!UICONTROL 레이아웃 컨테이너]**&#x200B;를 눌러 해당 도구 모음을 연 다음 정책 아이콘을 누릅니다.
1. **[!UICONTROL 레이아웃 컨테이너]** 페이지의 **[!UICONTROL 속성]** 머리글 아래에서 **[!UICONTROL 허용된 구성 요소]** 탭이 선택되어 있는지 확인합니다.

   ![허용된 구성 요소](/help/assets/assets-dm/allowed-components.png)

1. **[!UICONTROL Dynamic Media]**&#x200B;이 표시될 때까지 스크롤합니다.
1. **[!UICONTROL Dynamic Media]**&#x200B;의 왼쪽에 있는 > 아이콘을 눌러 목록을 확장하고 활성화할 Dynamic Media 구성 요소를 선택합니다.

   ![Dynamic Media 구성 요소 목록](/help/assets/assets-dm/dm-components-select.png)

1. **[!UICONTROL 레이아웃 컨테이너]** 페이지의 오른쪽 위 모서리 근처에 있는 완료(확인 표시) 아이콘을 탭합니다.

1. 페이지 위쪽 근처 도구 모음 오른쪽의 드롭다운 목록에서 **[!UICONTROL 초기 컨텐츠]**&#x200B;를 누른 다음 [Dynamic Media 구성 요소를 평소대로 페이지](#adding-a-dynamic-media-component-to-a-page)에 추가합니다.

## Dynamic Media 구성 요소 지역화 {#localizing-dynamic-media-components}

다음 두 가지 방법 중 하나로 Dynamic Media 구성 요소를 현지화할 수 있습니다.

* 사이트의 웹 페이지 내에서 **[!UICONTROL 속성]**&#x200B;을 열고 **[!UICONTROL 고급]** 탭을 선택합니다. 현지화를 위해 원하는 언어를 선택합니다.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* 사이트 선택기에서 원하는 페이지 또는 페이지 그룹을 선택합니다. **[!UICONTROL 속성]**&#x200B;을 누르고 **[!UICONTROL 고급]** 탭을 선택합니다. 현지화를 위해 원하는 언어를 선택합니다.

   >[!NOTE]
   >
   >현재 **[!UICONTROL 언어]** 메뉴에서 사용할 수 있는 일부 언어에는 토큰이 할당되지 않았습니다.

## Dynamic Media 구성 요소 {#dynamic-media-components}

Dynamic Media 및 대화형 미디어는 [!UICONTROL 구성 요소]의 [!UICONTROL Dynamic Media] 탭에서 사용할 수 있습니다. 대화형 비디오, 대화형 이미지 또는 회전 메뉴 세트와 같은 대화형 자산에 [!UICONTROL 대화형 미디어] 구성 요소를 사용합니다. 기타 모든 다이내믹 미디어 구성 요소의 경우에는 Dynamic Media 구성 요소를 사용하십시오.

>[!NOTE]
>
>이러한 구성 요소는 기본적으로 사용할 수 없으며 사용하기 전에 템플릿 편집기를 통해 사용할 수 있어야 합니다. [템플릿 편집기](/help/sites-authoring/templates.md#editing-templates-template-authors) 에서 사용할 수 있게 되면 다른 AEM 구성 요소처럼 페이지에 구성 요소를 추가할 수 있습니다.

![chlimage_1-539](assets/chlimage_1-539.png)

### Dynamic Media 구성 요소 {#dynamic-media-component}

Dynamic Media 구성 요소는 편리하게도 이미지를 추가하는지 아니면 비디오를 추가하는지에 따라 사용 가능한 선택 사항이 달라집니다. 이 구성 요소는 이미지 사전 설정, 이미지 세트와 같은 이미지 기반 뷰어, 스핀 세트, 혼합 미디어 세트 및 비디오를 지원합니다. 또한 뷰어는 응답형입니다. 즉, 화면 크기가 스크린의 크기에 따라 자동으로 변경됩니다. 모든 뷰어는 HTML5 뷰어입니다.

>[!NOTE]
>
>읽기 전용 권한이 있는 사용자가 액세스하는 웹 페이지에 Dynamic Media 구성 요소, 대화형 미디어 구성 요소 또는 둘 다가 있는 경우, 페이지가 중단되고 구성 요소가 올바르게 렌더링되지 않습니다. 이유는 구성 요소의 속성이 양호하고 참조된 자산 및 구성에 액세스할 수 있도록 페이지를 재구성하기 때문입니다. 그러면 페이지가 다시 렌더링되어 구성 요소가 중단됩니다.사용자의 읽기 전용 액세스 때문에 페이지의 각 구성 요소 코드를 다시 렌더링할 수 없습니다.
>  
>이 문제를 방지하려면 AEM Sites 사용자에게 에셋에 액세스할 수 있는 권한이 있는지 확인하십시오.

>[!NOTE]
>
>Dynamic Media 구성 요소를 추가하고 **[!UICONTROL Dynamic Media 설정]**&#x200B;이 비어 있거나 자산을 제대로 추가할 수 없는 경우, 다음을 확인하십시오.
>
>* [Dynamic Media를 활성화](config-dynamic.md)했습니다. Dynamic Media는 기본적으로 비활성화됩니다.
>* 이미지에 피라미드형 tiff 파일이 있습니다. 다이내믹 미디어를 활성화하기 전에 가져온 이미지에는 피라미드형 tiff 파일이 없습니다.

>



#### 이미지 작업 시 {#when-working-with-images}

Dynamic Media 구성 요소를 사용하면 이미지 세트, 스핀 세트 및 혼합 미디어 세트를 포함한 다이내믹 이미지를 추가할 수 있습니다. 확대하거나 축소할 수 있고, 해당하는 경우 스핀 세트 내의 이미지를 회전하거나 다른 유형의 세트에서 이미지를 선택할 수 있습니다.

구성 요소에서 바로 뷰어 사전 설정, 이미지 사전 설정 또는 이미지 형식을 구성할 수도 있습니다. 이미지가 응답하도록 하기 위해 중단점을 설정하거나 응답형 이미지 사전 설정을 적용할 수 있습니다.

구성 요소에서 **[!UICONTROL 편집]** 아이콘을 클릭한 다음 **[!UICONTROL Dynamic Media 설정]**&#x200B;을 클릭하여 다음 Dynamic Media 설정을 편집해야 합니다.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>기본적으로 Dynamic Media 이미지 구성 요소는 적응형입니다. 고정 크기로 설정하려면 **[!UICONTROL 너비]** 및 **[!UICONTROL 높이]** 설정과 함께 **[!UICONTROL 고급]** 탭의 구성 요소에서 설정을 설정하십시오.

* **[!UICONTROL 뷰어 사전 설정]** 드롭다운 메뉴에서 기존 뷰어 사전 설정을 선택합니다. 보려는 뷰어 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 뷰어 사전 설정 관리를 참조하십시오. 이미지 사전 설정을 사용 중일 때는 뷰어 사전 설정을 선택할 수 없고 그 반대의 경우도 마찬가지입니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우 사용할 수 있는 유일한 선택 사항입니다. 표시되는 뷰어 사전 설정은 편리하게도 적절한 뷰어 사전 설정만 표시됩니다.

* **[!UICONTROL 뷰어]**
수정자뷰어 수정자는 이름=값 쌍의 형식을 &amp; 구분 기호와 함께 사용하고 뷰어 참조 안내서에 설명된 대로 뷰어를 변경할 수 있습니다. 뷰어 수정자의 예는 posteimage=img.jpg&amp;caption=text.vtt, 1 - 비디오 축소판의 다른 이미지를 설정하고 닫힌 캡션/자막 파일을 비디오에 연결합니다.

* **[!UICONTROL 이미지 사전 설정]** 드롭다운 메뉴에서 기존 이미지 사전 설정을 선택합니다. 보려는 이미지 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 이미지 사전 설정 관리를 참조하십시오. 이미지 사전 설정을 사용 중일 때는 뷰어 사전 설정을 선택할 수 없고 그 반대의 경우도 마찬가지입니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL 이미지]**
수정자추가 이미지 명령을 제공하여 이미지 효과를 적용할 수 있습니다. 이러한 내용은 이미지 사전 설정 및 이미지 제공 명령 참조에 설명되어 있습니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL 중단점]**
반응형 사이트에서 이 자산을 사용하는 경우 이미지 중단점을 추가해야 합니다. 이미지 중단점은 쉼표(,)로 구분해야 합니다. 이 선택 사항은 이미지 사전 설정에 정의된 높이나 폭이 없는 경우에 작동합니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.
구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 고급 설정을 편집할 수 있습니다.

* ****
제목이미지의 제목을 변경합니다.

* **[!UICONTROL 대체]**
텍스트그래픽을 해제한 사용자를 위해 이미지에 제목을 추가합니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL URL,]**
열기링크를 열도록 자산을 설정할 수 있습니다. URL을 설정하고 여는 위치에 같은 창에서 열지 또는 새 창에서 열지를 지정합니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **** 가로  ****
및 높임이미지가 고정 크기로 되려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

#### 비디오 작업 시 {#when-working-with-video}

Dynamic Media 구성 요소를 사용하여 웹 페이지에 다이내믹 비디오를 추가하십시오. 구성 요소를 편집할 때 페이지에서 비디오를 재생하기 위해 사전 설정된 비디오 뷰어 사전 설정을 사용하도록 선택할 수 있습니다.

![chlimage_1-540](assets/chlimage_1-540.png)

구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 Dynamic Media 설정을 편집해야 합니다.

>[!NOTE]
>
>기본적으로 Dynamic Media 비디오 구성 요소는 적응형입니다. 고정 크기로 설정하려면 **[!UICONTROL 고급]** 탭에서 **[!UICONTROL 폭]** 및 [!UICONTROL 높이]로 구성 요소를 설정하십시오.

* **[!UICONTROL 뷰어]**
사전 설정드롭다운 메뉴에서 기존 비디오 뷰어 사전 설정을 선택합니다. 보려는 뷰어 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 뷰어 사전 설정 관리를 참조하십시오.

* **[!UICONTROL 뷰어]**
수정자뷰어 수정자는 이름=값 쌍의 형식을 &amp; 구분 기호와 함께 사용하고 Adobe 뷰어 참조 안내서에 설명된 대로 뷰어를 변경할 수 있습니다. 뷰어 수정자의 예는 posterimage=img.jpg&amp;caption=text.vtt,1입니다.

   예를 들어 뷰어 수정자를 사용하여 다음을 수행할 수 있습니다.

   * 캡션 파일을 비디오 [캡션과 연결합니다.](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * 탐색 파일을 비디오 [탐색과 연결합니다.](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 [!UICONTROL 고급 설정]을 편집할 수 있습니다.

* ****
제목비디오 제목을 변경합니다.

* **[!UICONTROL 너비]** 및  ****
높이비디오의 크기를 고정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 적응형으로 설정됩니다.

#### 스마트 자르기 작업 시 {#when-working-with-smart-crop}

Dynamic Media 구성 요소를 사용하여 웹 페이지에 스마트 자르기 이미지 자산을 추가합니다. 구성 요소를 편집할 때 페이지에서 비디오를 재생하기 위해 사전 설정된 비디오 뷰어 사전 설정을 사용하도록 선택할 수 있습니다.

[이미지 프로필](image-profiles.md)도 참조하십시오.

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 [!UICONTROL Dynamic Media 설정]을 편집할 수 있습니다.

>[!NOTE]
>
>기본적으로 Dynamic Media 이미지 구성 요소는 적응형입니다. 고정 크기로 설정하려면 [!UICONTROL 고급] 탭의 구성 요소에서 **[!UICONTROL 폭]** 및 **[!UICONTROL 높이]**&#x200B;를 설정하십시오.

* **[!UICONTROL 이미지]**
수정자추가 이미지 명령을 제공하여 이미지 효과를 적용할 수 있습니다. 이러한 내용은 이미지 사전 설정 및 이미지 제공 명령 참조에 설명되어 있습니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 **[!UICONTROL 고급]** 설정을 편집할 수 있습니다.

* **[!UICONTROL 제목]**
스마트 자르기 이미지의 제목을 변경합니다.

* **[!UICONTROL 대체]**
텍스트그래픽을 해제한 사용자를 위해 스마트 자르기 이미지에 제목을 추가합니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL URL,]**
열기링크를 열도록 자산을 설정할 수 있습니다. URL을 설정하고 여는 위치에 같은 창에서 열지 또는 새 창에서 열지를 지정합니다.
이미지 세트, 스핀 세트 또는 혼합 미디어 세트를 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL 높이]** 및  ****
너비스마트 자르기 이미지를 고정 크기로 설정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 적응형으로 설정됩니다.

### 대화형 미디어 구성 요소 {#interactive-media-component}

대화형 미디어 구성 요소는 핫스팟이나 이미지 맵과 같은 상호 작용이 있는 자산을 위한 것입니다. 대화형 이미지, 대화형 비디오 또는 회전 배너가 있는 경우 대화형 미디어 구성 요소를 사용하십시오.

대화형 미디어 구성 요소는 편리하게도 이미지를 추가하는지 아니면 비디오를 추가하는지에 따라 다양한 옵션이 있습니다. 또한 뷰어는 응답형이어서 화면 크기가 스크린의 크기에 따라 자동으로 변경됩니다. 모든 뷰어는 HTML5 뷰어입니다.

>[!NOTE]
>
>읽기 전용 권한이 있는 사용자가 액세스하는 웹 페이지에 Dynamic Media 구성 요소, 대화형 미디어 구성 요소 또는 둘 다가 있는 경우, 페이지가 중단되고 구성 요소가 올바르게 렌더링되지 않습니다. 이유는 구성 요소의 속성이 양호하고 참조된 자산 및 구성에 액세스할 수 있도록 페이지를 재구성하기 때문입니다. 그러면 페이지가 다시 렌더링되어 구성 요소가 중단됩니다.사용자의 읽기 전용 액세스 때문에 페이지의 각 구성 요소 코드를 다시 렌더링할 수 없습니다.
> 
>이 문제를 방지하려면 AEM Sites 사용자에게 에셋에 액세스할 수 있는 권한이 있는지 확인하십시오.

![chlimage_1-541](assets/chlimage_1-541.png)

구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 **[!UICONTROL 일반]** 설정을 편집할 수 있습니다.

* **[!UICONTROL 뷰어 사전 설정]** 드롭다운 메뉴에서 기존 뷰어 사전 설정을 선택합니다. 보려는 뷰어 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 뷰어 사전 설정을 사용하려면 먼저 게시해야 합니다. 뷰어 사전 설정 관리를 참조하십시오.

* ****
제목비디오 제목을 변경합니다.

* **[!UICONTROL 너비]** 및  ****
높이비디오의 크기를 고정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 적응형으로 설정됩니다.

구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 **[!UICONTROL 장바구니에 추가]** 설정을 편집할 수 있습니다.

* **[!UICONTROL 제품]**
자산 표시 기본적으로 이 값이 선택됩니다. 제품 자산은 상거래 모듈에 정의된 제품의 이미지를 보여줍니다. 제품 자산을 표시하지 않도록 하려면 확인 표시를 지우십시오.

* **[!UICONTROL 제품]**
가격 표시기본적으로 이 값이 선택됩니다. 제품 가격은 상거래 모듈에 정의된 항목 가격을 보여줍니다. 제품 가격을 표시하지 않도록 하려면 확인 표시를 지우십시오.

* **[!UICONTROL 제품]**
양식 표시기본적으로 이 값은 선택되어 있지 않습니다. 제품 양식에는 크기 및 색상과 같은 모든 제품 변형이 포함됩니다. 제품 변형을 표시하지 않도록 하려면 확인 표시를 지우십시오.

### 파노라마 미디어 구성 요소 {#panoramic-media-component}

파노라마 미디어 구성 요소는 구형 파노라마 이미지인 자산을 위한 것입니다. 이러한 이미지는 회의실, 속성, 위치 또는 가로의 360° 보기 환경을 제공합니다. 이미지가 구형 파노라마의 자격을 얻으려면 다음 중 하나 또는 둘 다 있어야 합니다.

* 2:1 종횡비.
* &quot;등장방형&quot; 또는 (&quot;구형&quot; + &quot;파노라마&quot;) 또는 (&quot;구형&quot; + &quot;파노라마&quot;) 키워드로 태그가 지정됩니다. [태그 사용](/help/sites-authoring/tags.md)을 참조하십시오.

종횡비와 키워드 기준은 모두 자산 세부 사항 페이지와 &quot;파노라마 미디어&quot; WCM 구성 요소에 대한 파노라마 자산에 적용됩니다.

![panasonic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

구성 요소에서 **[!UICONTROL 구성]**&#x200B;을 탭하여 다음 설정을 편집할 수 있습니다.

* **[!UICONTROL 뷰어]**
사전 설정뷰어 사전 설정 드롭다운 메뉴에서 기존 뷰어를 선택합니다.

찾고 있는 뷰어 사전 설정이 표시되지 않는 경우 게시되었는지 확인하십시오. 뷰어 사전 설정을 사용하려면 먼저 게시해야 합니다. [뷰어 사전 설정 관리](managing-viewer-presets.md)를 참조하십시오. 

### HTTP/2를 사용하여 Dynamic Media 에셋 {#using-http-to-delivery-dynamic-media-assets} 전달

HTTP/2는 브라우저와 서버의 통신 방식을 향상시키는 업데이트된 새로운 웹 프로토콜입니다. 정보를 빠르게 전송할 수 있고 필요한 처리 능력을 줄일 수 있습니다. 이제 Dynamic Media 에셋 배달을 HTTP/2를 통해 더 나은 응답 및 로드 시간을 제공할 수 있습니다.

Dynamic Media 계정으로 HTTP/2를 사용하는 시작에 대한 자세한 내용은 [HTTP2 콘텐츠 제공](http2.md)을 참조하십시오.

>[!MORELIKETHIS]
>
>* [AEM Dynamic Media의 색상 관리 이해](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [AEM Dynamic Media에서 사용자 정의 비디오 축소판 사용](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [AEM Dynamic Media을 사용한 자산 뷰어 이해](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [AEM Dynamic Media에서 대화형 비디오 사용](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [AEM Dynamic Media에서 비디오 플레이어 사용](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [AEM Dynamic Media에서 이미지 선명하게 하기 사용](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

