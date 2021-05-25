---
title: HTML5 양식의 양식 템플릿 디자인
seo-title: HTML5 양식의 양식 템플릿 디자인
description: 'AEM Forms에서는 XFA 양식 템플릿을 HTML5 형식으로 렌더링합니다. 양식 디자이너는 디자이너를 사용하여 양식 템플릿을 디자인하고 HTML5 변환 기능을 사용할 수 있습니다. '
seo-description: 'AEM Forms에서는 XFA 양식 템플릿을 HTML5 형식으로 렌더링합니다. 양식 디자이너는 디자이너를 사용하여 양식 템플릿을 디자인하고 HTML5 변환 기능을 사용할 수 있습니다. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---

# HTML5 양식의 양식 템플릿 디자인 {#designing-form-templates-for-html-forms}

AEM의 HTML5 양식 구성 요소는 XFA 양식 템플릿을 HTML5 형식으로 렌더링합니다. 양식 디자이너는 [Forms 디자이너](https://www.adobe.com/go/learn_aemforms_designer_63)를 사용하여 양식 템플릿을 디자인하고 HTML5 변환 기능을 사용할 수 있습니다. 이러한 양식 템플릿은 해당 자산과 함께 AEM 저장소, 파일 시스템에 있거나 http를 통해 노출할 수 있습니다. 그러나 Forms Manager를 사용하여 양식을 관리하려는 경우 템플릿 및 자산은 AEM 저장소에 있어야 합니다.

HTML5 양식은 PDF forms의 동작과 상당히 일치하지만 두 형식 모두에 다른 형식에 적용할 수 없는 몇 가지 기능이 있습니다. 예를 들어, Adobe Reader에서 PDF 양식에 바코드가 적용되는 방식은 모바일 양식이나 디지털 서명이 있는 방식에따라 형식마다 다릅니다. 이러한 변형에 대한 자세한 내용은 [HTML5 양식과 PDF forms 간의 기능 차별화](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md)를 참조하십시오.

일반적인 XFA 기능에 대해서는 두 형식 모두에서 작동하는 양식을 디자인하기 위한 다음 모범 사례 및 지침을 참조하십시오.

## AEM Forms Designer에서 HTML5 Forms용 기능 {#capabilities-in-aem-forms-designer-for-html-forms}

### 미리 보기 HTML {#preview-html}

미리 보기 HTML 탭은 양식 디자이너가 디자인 프로세스 중에 HTML5 형식으로 양식을 미리 보기 위해 디자인 모드에 추가됩니다. AEM Forms Designer에서 이 기능을 활성화하고 구성하는 방법에 대한 자세한 내용은 [HTML 미리 보기](/help/forms/using/preview-xdp-forms-html.md)를 참조하십시오.

### 스크리블 서명 {#scribble-signature}

HTML5 양식의 주요 타겟은 터치 장치입니다. 따라서 AEM Forms Designer에 새로운 스크리블 서명 컨트롤이 추가됩니다. 양식 서식 파일에서 스크리블 서명 컨트롤을 클릭하거나 끌어서 놓고 구성할 수 있습니다. 이 레이아웃은 HTML5 표현식에서 스크리블 필드로 렌더링되며 터치 장치에서 서명을 스크리블 하는 데 사용할 수 있습니다. 데스크톱 컴퓨터에서는 마우스 컨트롤을 사용하여 스크리블 필드로 사용할 수 있습니다. 이 기능을 사용하는 방법에 대한 자세한 내용은 [XFA 스크리블 필드](/help/forms/using/scribble-signature.md)를 참조하십시오.

![4](assets/4.png)
