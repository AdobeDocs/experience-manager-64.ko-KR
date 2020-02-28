---
title: HTML5 양식의 양식 템플릿 디자인
seo-title: HTML5 양식의 양식 템플릿 디자인
description: 'AEM Forms에서는 XFA 양식 템플릿을 HTML5 형식으로 렌더링합니다. 양식 디자이너는 Designer를 사용하여 양식 템플릿을 디자인하고 HTML5 변환 기능을 사용할 수 있습니다. '
seo-description: 'AEM Forms에서는 XFA 양식 템플릿을 HTML5 형식으로 렌더링합니다. 양식 디자이너는 Designer를 사용하여 양식 템플릿을 디자인하고 HTML5 변환 기능을 사용할 수 있습니다. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# HTML5 양식의 양식 템플릿 디자인 {#designing-form-templates-for-html-forms}

AEM의 HTML5 양식 구성 요소는 XFA 양식 템플릿을 HTML5 형식으로 렌더링합니다. 양식 디자이너는 양식 디자이너를 사용하여 양식 템플릿을 디자인하고 [HTML](https://www.adobe.com/go/learn_aemforms_designer_63) 5 변환 기능을 사용할 수 있습니다. 이러한 양식 템플릿은 해당 자산과 함께 AEM 저장소, 파일 시스템에 상주하거나 http를 통해 노출할 수 있습니다. 그러나 Forms 관리자를 사용하여 양식을 관리하려면 템플릿 및 자산이 AEM 저장소에 상주해야 합니다.

HTML5 양식은 PDF 양식의 비헤이비어와 상당히 비슷하지만 두 형식 모두 다른 형식에 적용할 수 없는 일부 기능이 있습니다. 예를 들어 Adobe Reader에서 PDF 양식에 바코드가 적용되는 방법은 모바일 양식이나 양식에 따라 다르며 양식에 디지털 서명이 적용되는 방법도 서로 다릅니다. 이러한 변형에 대한 자세한 내용은 HTML5 [양식과 PDF 양식 간의 차별화된 기능을 참조하십시오](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

일반적인 XFA 기능을 보려면 다음 우수 사례 및 가이드라인을 참조하십시오.

## HTML5 양식용 AEM Forms 디자이너의 기능 {#capabilities-in-aem-forms-designer-for-html-forms}

### HTML 미리 보기 {#preview-html}

양식 디자이너가 디자인 프로세스 중에 HTML5 형식으로 양식을 미리 볼 수 있도록 양식 디자이너를 위한 디자인 모드에 HTML 미리 보기 탭이 추가됩니다. AEM Forms 디자이너에서 이 기능을 활성화하고 구성하는 방법에 대한 자세한 내용은 HTML 미리 [보기를 참조하십시오](/help/forms/using/preview-xdp-forms-html.md).

### 스크리블 서명 {#scribble-signature}

HTML5 양식의 주요 목표는 터치 디바이스입니다. 따라서 AEM Forms Designer에 새로운 낙서 서명 컨트롤이 추가됩니다. 양식 서식 파일에서 자유 서명 컨트롤을 클릭하거나 드래그하여 놓고 구성할 수 있습니다. HTML5 변환에서 자유 필드로 렌더링되며 터치 장치에서 서명을 자유롭게 쓰는 데 사용할 수 있습니다. 데스크톱 컴퓨터에서는 마우스 컨트롤을 사용하여 자유 필드로 사용할 수 있습니다. 이 기능을 사용하는 방법에 대한 자세한 내용은 XFA 스크리블 [필드를 참조하십시오](/help/forms/using/scribble-signature.md).

![4](assets/4.png)

[지원 문의](https://www.adobe.com/account/sign-in.supportportal.html)
