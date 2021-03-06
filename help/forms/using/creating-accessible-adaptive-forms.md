---
title: 액세스 가능한 적응형 양식 만들기
seo-title: 액세스 가능한 적응형 양식 만들기
description: AEM Forms은 액세스 가능한 적응형 양식을 만들고 액세스 가능성 표준을 준수하는 데 도움이 되는 도구 및 도구를 제공합니다.
seo-description: AEM Forms은 액세스 가능한 적응형 양식을 만들고 액세스 가능성 표준을 준수하는 데 도움이 되는 도구 및 도구를 제공합니다.
uuid: eceb3282-0b90-4e0a-8b89-137d27029747
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 96d9ad52-074b-4084-b818-abce79282776
feature: 적응형 양식
exl-id: adad26fa-b27a-4bd7-806c-4ddfbaae7a37
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# 액세스 가능한 적응형 양식 만들기 {#creating-accessible-adaptive-forms}

## 소개 {#introduction}

액세스 가능한 양식은 특별한 요구 사항이 있는 사용자를 비롯하여 모든 사용자가 사용할 수 있는 양식입니다. Adobe Experience Manager(AEM)에는 다양한 기능을 가진 사용자를 위해 적응형 양식의 유용성을 향상시키는 많은 기능이 포함되어 있습니다. 또한 이 솔루션은 양식 작성자가 액세스 가능한 적응형 양식을 만드는 데 도움이 됩니다.

적응형 양식으로 액세서빌러티를 구축하면 가능한 많은 컨텐츠를 제공할 수 있을 뿐만 아니라 접근성 표준을 준수하는 권한이 있는 지리적 위치에 문서를 제공할 때에도 요구 사항이 됩니다. AEM Forms은 양식 개발자가 액세스 가능성 표준을 준수하는 데 도움이 됩니다.

적응형 양식을 작성하는 동안 작성자는 다음 사항을 고려하여 액세스 가능한 적응형 양식을 만들어야 합니다.

* 양식 컨트롤에 적절한 레이블 제공
* 이미지에 상응하는 텍스트를 제공합니다
* 충분한 색상 대비 제공
* 양식 컨트롤에 키보드 액세스 가능 여부 확인

## 양식 컨트롤 {#provide-proper-labels-for-form-controls}에 적절한 레이블을 제공합니다.

구성 요소의 레이블이나 제목은 양식 구성 요소가 나타내는 것을 식별합니다. 예를 들어 &quot;이름&quot; 텍스트는 사용자에게 텍스트 필드에 이름을 입력해야 한다고 알려줍니다. 화면 판독기에서 액세스할 수 있도록 레이블은 양식 구성 요소와 프로그래밍 방식으로 연결됩니다. 또는 양식 컨트롤은 추가 액세스 가능성 정보로 구성됩니다.

화면 판독기에서 인식하는 레이블이 시각적 캡션과 동일할 필요는 없습니다. 경우에 따라 컨트롤의 목적에 대해 더 자세히 알고 싶을 수 있습니다. 양식의 각 필드 개체에 대해 액세스 가능성 옵션을 사용하여 화면 판독기에서 특정 양식 필드를 식별하기 위해 알리는 내용을 지정할 수 있습니다.

액세스 가능성 옵션을 사용하려면 다음 단계를 수행합니다.

1. 구성 요소를 선택하고 ![cmppr](assets/cmppr.png)을 누릅니다.
1. 사이드바에서 **액세서빌러티** 를 클릭하여 원하는 액세서빌러티 옵션을 선택합니다.

### 양식 구성 요소 {#accessibility-options-in-form-components}의 액세스 가능성 옵션

![양식 구성 요소의 액세스 가능성 옵션](assets/accessibility-options.png)

**사용자** 지정 TextForm 작성자는 액세스 가능성 옵션 사용자 지정 텍스트 필드에 콘텐츠를 제공합니다. 화면 판독기와 같은 보조 기술은 이 사용자 지정 텍스트를 사용합니다. 대부분의 시나리오에서 제목 설정을 사용하는 것이 가장 좋습니다. 제목 또는 간단한 설명을 사용할 수 없는 경우에만 사용자 지정 화면 Reader 텍스트 만들기를 고려해 보십시오.

**짧은** 설명대부분의 구성 요소의 경우 사용자가 구성 요소 위에 포인터를 놓으면 런타임에 짧은 설명이 나타납니다. 도움말 콘텐츠 선택 사항에서 간단한 설명 필드에서 이 옵션을 설정할 수 있습니다.

**** 제목AEM Forms에서 양식 필드와 관련된 시각적 레이블을 화면 판독기 텍스트로 사용할 수 있도록 하려면 이 옵션을 사용합니다.

**** 이름바인딩 탭의 이름 필드에 값을 지정할 수 있습니다. 이름에는 공백을 포함할 수 없습니다.

**** 없음없음을 선택하면 양식 개체에 게시된 양식의 이름이 없습니다. None은 양식 컨트롤에 권장되는 설정이 아닙니다.

>[!NOTE]
>
>라디오 단추 및 확인란에는 두 가지 액세스 가능성(즉, 사용자 지정 텍스트 및 제목)만 있을 수 있습니다.

>[!NOTE]
>
>XFA 기반 적응형 양식의 경우 액세스 가능성 옵션은 XDP에 설정된 액세스 가능성 옵션에서 상속됩니다. XDP의 도구 팁은 짧은 설명에 매핑되고 캡션은 제목에 매핑됩니다. 다른 옵션은 그대로 작동합니다.

## {#provide-text-equivalents-for-images} 이미지에 상응하는 텍스트를 제공합니다.

이미지는 일부 사용자의 이해도를 개선하는 데 도움이 될 수 있습니다. 그러나 화면 판독기를 사용하는 사용자의 경우 이미지가 양식의 액세스 가능성을 낮춰줍니다. 이미지를 사용하도록 선택하는 경우 모든 이미지에 대한 텍스트 설명을 제공합니다.

텍스트가 개체와 해당 목적을 양식에 설명하도록 하십시오. 화면 판독기는 이미지가 발생하면 이 대체 텍스트를 읽습니다. 이미지에는 항상 대체 텍스트가 지정되어 있어야 합니다.

이미지 구성 요소를 선택하고 ![cmppr](assets/cmppr.png)을 누릅니다. 사이드바의 속성 아래에서 이미지에 대한 대체 텍스트를 지정합니다.

![이미지에 대한 대체 텍스트](assets/image-properties.png)

## 충분한 색상 대비 {#provide-sufficient-color-contrast} 제공

접근성 설계에는 색상 사용에 대한 추가 지침을 고려해야 합니다. 양식 작성자는 다양한 양식 구성 요소를 강조 표시하여 양식의 모양을 향상시키는 데 색상을 사용할 수 있습니다. 하지만, 색의 부적절한 사용은 다양한 능력을 가진 사람들이 읽는 것을 어렵거나 불가능하게 만들 수 있습니다.

시각 장애가 있는 사용자는 디지털 컨텐츠를 읽기 위해 텍스트와 배경 간의 대비가 높습니다. 충분한 대비책이 없으면 일부 사용자가 읽을 수 있도록 양식을 읽기 어려울 수 있습니다.

기본 글꼴과 배경색(흰색 배경의 검정 색상)을 사용하는 것이 좋습니다. 기본 색상을 변경할 경우 밝은 배경색의 어두운 전경색을 선택하거나 그 반대로 선택합니다.

적응형 양식의 색상 대비 및 테마 변경에 대한 자세한 내용은 [적응형 양식의 사용자 지정 테마 만들기](/help/forms/using/creating-custom-adaptive-form-themes.md) 를 참조하십시오.

## 양식 컨트롤이 키보드 액세스 가능 {#ensure-that-form-controls-are-keyboard-accessible} 인지 확인합니다.

액세스 가능한 양식은 키보드나 그에 상응하는 입력 장치만 사용하여 완전히 채울 수 있습니다. 이동성이 저하되거나 시각 장애가 있는 사용자는 키보드를 사용할 수 밖에 없고 마우스를 사용할 수 있는 많은 사용자가 키보드 입력을 선호할 수 있습니다. 다양한 입력 방법을 허용하여 액세스 가능한 양식을 만들 뿐만 아니라 모든 사용자의 환경 설정에 더 적합한 양식을 만들 수도 있습니다.

AEM Forms에서는 다음 키보드 단축키를 사용할 수 있습니다.

| 작업 | 키보드 단축키 |
|---|---|
| 양식을 통해 커서를 앞으로 이동 | 탭 |
| 양식을 통해 커서 뒤로 이동 | Shift+Tab |
| 다음 패널로 이동 | Alt+오른쪽 화살표 |
| 이전 패널로 이동 | Alt+왼쪽 화살표 |
| 채워진 데이터를 양식에서 다시 설정합니다 | Alt+R |
| 양식 제출 | Alt+S | configuring-watched-folder-endpoints.md |
