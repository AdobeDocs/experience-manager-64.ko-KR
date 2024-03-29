---
title: 이미지 품질 최적화 모범 사례
description: Dynamic Media의 이미지 품질 최적화 우수 사례 학습
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 2e90bea1-eaac-457b-8588-b18d3a6e8d91
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1497'
ht-degree: 6%

---

# 이미지 품질 최적화 모범 사례 {#best-practices-for-optimizing-the-quality-of-your-images}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

허용되는 결과를 렌더링하는 데 많은 요소가 기여하므로 이미지 품질 최적화는 시간이 많이 걸릴 수 있습니다. 개인이 화질을 다르게 인식하기 때문에 결과는 어느 정도 주관적이다. 구조화된 실험이 핵심입니다.

AEM에는 이미지를 조정 및 최적화하고 렌더링 결과를 렌더링하기 위한 100개 이상의 dynamic media 이미지 전달 명령이 포함되어 있습니다. 다음 지침을 통해 프로세스를 간소화하고 몇 가지 필수 명령과 모범 사례를 사용하여 신속하게 좋은 결과를 얻을 수 있습니다.

## 이미지 형식에 대한 우수 사례(&amp;fmt=) {#best-practices-for-image-format-fmt}

* JPG 또는 PNG는 고품질, 크기 및 가중치를 관리하기 쉬운 이미지를 제공하는 데 가장 적합한 제품입니다.
* URL에 형식 명령을 제공하지 않으면 Dynamic Media 이미지 배달의 기본값은 전달 JPG으로 설정됩니다.
* JPG은 10:1의 비율로 압축되며 일반적으로 더 작은 이미지 파일 크기를 생성합니다. PNG는 이미지가 흰색 배경을 포함하는 경우처럼 일부 경우를 제외하고 약 2:1의 비율로 압축됩니다. 일반적으로 PNG 파일 크기는 JPG 파일보다 큽니다.
* JPG은 손실 압축을 사용합니다. 즉, 압축 중에 그림 요소(픽셀)가 삭제됩니다. 반면 PNG는 무손실 압축을 사용합니다.
* JPG은 날카로운 모서리와 대비가 있는 합성 이미지보다 선명도가 향상된 사진 이미지를 자주 압축합니다.
* 이미지에 투명도가 포함되어 있는 경우 JPG이 투명도를 지원하지 않으므로 PNG를 사용합니다.

이미지 형식에 대한 우수 사례로서, 가장 일반적인 설정으로 시작하십시오 `&fmt=JPG`.

## 이미지 크기에 대한 우수 사례 {#best-practices-for-image-size}

가장 일반적인 작업 중 하나가 동적으로 이미지 크기를 줄이는 것입니다. 이 작업에는 크기를 지정하고, 필요에 따라 이미지를 축소하는 데 사용할 다운샘플링 모드를 지정하는 작업이 포함됩니다.

* 이미지 사이징의 경우 가장 간편하고 최상의 방법은 `&wid=<value>` 및 `&hei=<value>,`또는 `&hei=<value>`. 이러한 매개 변수는 종횡비에 따라 이미지 너비를 자동으로 설정합니다.
* `&resMode=<value>`다운샘플링에 사용되는 알고리즘을 제어합니다. 다음으로 시작 `&resMode=sharp2`. 이 값은 최상의 이미지 품질을 제공합니다. 다운샘플링 사용 중 `value =bilin` 가 빨라지면 가공물의 앨리어싱이 발생하는 경우가 많습니다.

이미지 크기를 조정하는 우수 사례로, `&wid=<value>&hei=<value>&resMode=sharp2` 또는 `&hei=<value>&resMode=sharp2`

## 이미지 선명하게 하기 위한 우수 사례 {#best-practices-for-image-sharpening}

이미지 선명하게 하기는 웹 사이트에서 이미지를 제어하는 가장 복잡한 측면이며 오류가 많은 경우입니다. AEM에서 을 참조하여 선명하게 하고 선명하게 표시되지 않는 마스킹이 작동하는 방식에 대해 자세히 알아보십시오 [Adobe Dynamic Media Classic 이미지 품질 및 선명하게 하기 우수 사례](/help/assets/assets/sharpening_images.pdf) AEM에도 적용되는 안내서입니다.

참조 - [언샵 마스크로 이미지 선명하게 하기](https://helpx.adobe.com/photoshop/using/adjusting-image-sharpness-blur.html).

AEM을 사용하면 섭취, 게재 시 또는 둘 다에 따라 이미지를 선명하게 할 수 있습니다. 그러나 대부분의 경우 한 가지 방법 또는 다른 방법만 사용하여 이미지를 선명하게 해야 하지만 두 방법 모두 이미지를 선명하게 해야 합니다. 배달 시 URL에서 이미지를 선명하게 하면 일반적으로 최상의 결과를 제공합니다.

사용할 수 있는 이미지 선명하게 하기 방법에는 두 가지가 있습니다.

* 단순 선명하게 하기( `&op_sharpen`) - Photoshop에서 사용되는 선명 효과 필터와 유사한 간단한 선명도 동적 크기 조정을 통해 이미지의 최종 보기에 기본 선명도 적용됩니다. 그러나 이 방법은 사용자가 구성할 수 없습니다. 가장 좋은 방법은 필요한 경우가 아니면 &amp;op_선명하게 하기를 사용하지 않는 것입니다.
* 언샵 마스킹( `&op_USM`) - 언샵 마스킹은 업계 표준 선명도 필터입니다. 가장 좋은 방법은 아래 지침에 따라 언샵 마스킹으로 이미지를 선명하게 하는 것입니다. 언샵 마스킹을 사용하면 다음 세 가지 매개변수를 제어할 수 있습니다.

   * `&op_sharpen=`amount,radius,임계값

      * **[!UICONTROL 금액]** (0-5, 효과의 강도)
      * **[!UICONTROL 반경]** (0-250, 선명하게 표시된 개체 주위에 그려지는 &quot;선명하게 하기 선&quot;의 너비(픽셀 단위)입니다.)

             매개변수 반경과 양이 서로 작용한다는 점을 명심하십시오. 감소 반경은 양을 증가시켜 보상할 수 있다. 반경은 값이 낮을수록 가장자리 픽셀만 선명하게 표시되므로 보다 세밀하게 제어할 수 있지만 값이 높을수록 더 넓은 범위의 픽셀 범위가 선명하게 표시됩니다.
         
      * **[!UICONTROL 임계값]** (0-255, 효과 민감도)

             This parameter determines how different the sharpened pixels must be from the surrounding area before they are considered edge pixels and the filter sharpens them. The **[!UICONTROL threshold]** parameter helps to avoid over-sharpening areas with similar colors, such as skin tones. For example, a threshold value of 12 ignores slight variations in skin tone brightness to avoid adding &quot;noise&quot;, while still adding edge contrast to high contrast areas, such as where eyelashes meet skin.
         
         필터에 사용하는 우수 사례를 비롯하여 이러한 세 매개 변수를 설정하는 방법에 대한 자세한 내용은 [Adobe Dynamic Media Classic 이미지 품질 및 선명하게 하기 우수 사례](/help/assets/assets/sharpening_images.pdf) 안내서(AEM의 Dynamic Media에도 적용).
   * AEM에서 네 번째 매개 변수를 제어할 수도 있습니다. 모노크롬(0,1) 이 매개 변수는 값 0을 사용하여 각 색상 구성 요소에 개별적으로 또는 값 1을 사용하여 이미지 명도/강도에 언샵 마스킹이 적용되는지 여부를 결정합니다.


가장 좋은 방법은 언샵 마스크 반경 매개 변수로 시작하십시오. 시작할 수 있는 반경 설정은 다음과 같습니다.

* **[!UICONTROL 웹 사이트]**: 0.2-0.3픽셀
* **[!UICONTROL 사진 인쇄(250-300ppi)]**: 0.3-0.5픽셀
* **[!UICONTROL 오프셋 인쇄(266-300ppi)]**: 0.7-1.0픽셀
* **[!UICONTROL 캔버스 인쇄(150ppi)]**: 1.5-2.0픽셀

1.75에서 4로 점진적으로 증가시키세요. 선명하게 하기가 여전히 원하는 방식이 아닌 경우 반지름을 소수점으로 늘린 다음 양을 1.75에서 4로 다시 실행합니다. 필요에 따라 반복합니다.

모노크롬 매개 변수 설정을 0으로 둡니다.

### JPEG 압축에 대한 우수 사례(&amp;qlt=) {#best-practices-for-compression-qlt}

* 이 매개 변수는 JPG 인코딩 품질을 제어합니다. 값이 높을수록 화질이 높지만 파일 크기가 커집니다. 또는 값이 낮을수록 품질이 떨어지지만 파일 크기가 작다는 의미입니다. 이 매개 변수의 범위는 0-100입니다.
* 품질에 최적화하려면 매개 변수 값을 100으로 설정하지 마십시오. 90 또는 95와 100의 설정 차이는 거의 알 수 없지만 100은 이미지 파일의 크기를 불필요하게 증가시킵니다. 따라서 품질에 최적화되지만 이미지 파일이 너무 커지지 않도록 하려면 `qlt=<value>` 90 또는 95까지.
* 작은 이미지 파일 크기에 맞게 최적화하되, 이미지 품질을 허용 수준으로 유지하려면, `qlt=<value>` 80까지. 70~75보다 낮은 값은 상당한 이미지 품질이 저하됩니다.
* 가장 좋은 방법으로서, 중간에 있으려면, `qlt=<value>` 85에 도착해서 중간에 있어요
* 에서 색상 플래그 사용 `qlt=`

   * 다음 `qlt=` 매개 변수에는 값을 사용하여 RGB 색상 차이 다운샘플링을 설정할 수 있는 두 번째 설정이 있습니다 `,1` 또는 값 사용 안 함 `,0`.
   * 간소화를 위해 RGB 색상/도색 다운샘플링을 해제한 상태로 시작하십시오(`,0`). 이 설정을 사용하면 일반적으로 이미지 품질이 향상됩니다. 특히 가장자리와 대비가 선명한 합성 이미지의 경우 더욱 그러합니다.

JPG 압축 사용에 대한 우수 사례입니다 `&qlt=85,0`.

## JPEG 크기 조정 우수 사례(&amp;jpegSize=) {#best-practices-for-jpeg-sizing-jpegsize}

jpegSize는 메모리가 제한된 장치로 이미지를 전달할 때 일정 크기를 초과하지 않도록 하는 경우에 유용합니다.

* 이 매개 변수는 KB(`jpegSize=<size_in_kilobytes>`). 이미지 전달에 허용되는 최대 크기를 정의합니다.
* `&jpegSize=` JPG 압축 매개 변수와 상호 작용함 `&qlt=`. 지정한 JPG 압축 매개 변수(`&qlt=`)은 jpegSize 값을 초과하지 않으며, 이미지가 `&qlt=` 정의됨. 그렇지 않으면, `&qlt=` 이미지가 허용되는 최대 크기에 맞을 때까지 또는 시스템에 맞지 않는다고 판단되어 오류가 반환될 때까지 점차 감소합니다.

가장 좋은 방법은 `&jpegSize=` 매개 변수를 추가하고 `&qlt=` 메모리가 제한된 장치로 JPG 이미지를 전달하는 경우

## 모범 사례 요약 {#best-practices-summary}

높은 이미지 품질과 작은 파일 크기를 얻으려면 다음 매개 변수의 조합으로 시작하십시오.

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

이러한 설정 제품을 조합하면 대부분의 상황에서 우수한 결과를 얻을 수 있습니다.

이미지를 추가로 최적화해야 하는 경우 반경이 0.2 또는 0.3으로 설정된 상태에서 시작하여 서서히 선명도(언샵 마스킹) 매개 변수를 세밀하게 조정할 수 있습니다. 그런 다음 크기를 1.75에서 최대 4개(Photoshop의 400%에 해당)로 점차 늘리십시오. 원하는 결과가 달성되었는지 확인합니다.

선명하게 하기 결과가 여전히 만족스럽지 않으면 반지름을 십진수 증분으로 늘리십시오. 10진마다 증가하기 위해 1.75로 다시 시작하고 점차 4로 늘립니다. 원하는 결과를 얻을 때까지 이 프로세스를 반복합니다. 위의 값은 Creative Studio에서 검증한 접근 방법이지만 다른 값으로 시작하고 다른 전략을 따를 수 있습니다. 결과가 만족스럽든 아니든 주관적인 문제가 되므로 구조화된 실험이 관건이다.

실험하면서 워크플로우를 최적화하는 데 유용한 다음과 같은 일반적인 제안을 찾을 수도 있습니다.

* URL에서 직접 다양한 매개 변수를 실시간으로 테스트해 보십시오.
* Dynamic Media 이미지 제공 명령을 이미지 사전 설정으로 그룹화할 수 있는 것이 좋습니다. 이미지 사전 설정은 기본적으로 다음과 같은 사용자 지정 사전 설정 이름을 사용하는 URL 명령 매크로입니다 `$thumb_low$` 및 `&product_high$`. URL 경로의 사용자 지정 사전 설정 이름은 이러한 사전 설정을 호출합니다. 이러한 기능은 웹 사이트에서 이미지의 다양한 사용 패턴에 대한 명령 및 품질 설정을 관리하고 전체 URL 길이를 줄이는 데 도움이 됩니다.
* 또한 AEM에서는 섭취 시 선명도 이미지를 적용하는 것과 같이 이미지 품질을 조정하는 고급 방법을 제공합니다. 렌더링 결과를 추가로 조정하고 최적화하는 옵션이 있을 수 있는 고급 사용 사례의 경우, [Adobe Professional Services](https://www.adobe.com/kr/experience-cloud/consulting-services.html) 은 사용자 정의된 통찰력과 모범 사례를 활용할 수 있습니다.
