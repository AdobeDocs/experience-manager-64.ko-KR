---
title: 액세스 가능한 HTML5 양식 디자인
seo-title: 액세스 가능한 HTML5 양식 디자인
description: HTML5 양식은 ARIA HTML5 액세스 가능성 표준을 사용합니다. 이러한 양식은 탭 탐색 기능을 지원하고 일반 화면 판독기와 호환될 수 있도록 인증되었습니다.
seo-description: HTML5 양식은 ARIA HTML5 액세스 가능성 표준을 사용합니다. 이러한 양식은 탭 탐색 기능을 지원하고 일반 화면 판독기와 호환될 수 있도록 인증되었습니다.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: Mobile Forms
exl-id: 64d8cf2c-8180-49ce-a725-48cd03476fb8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 액세스 가능한 HTML5 양식 디자인 {#designing-accessible-html-forms}

HTML5 양식은 ARIA HTML5 액세스 가능성 표준을 사용하여 액세스 가능한 HTML 양식을 생성합니다. 이러한 양식은 탭 탐색(Mozilla FireFox 제외)을 지원하며, 일반 화면 판독기와 호환되도록 인증되었습니다. 액세스 가능성 기능이 뛰어난 HTML5 양식을 생성하려면 일부 [기본 디자인 지침](/help/forms/using/best-practices-for-html5-forms.md)을 기반으로 XFA 양식 템플릿을 디자인합니다. 디자인 지침에는 올바른 탭 순서를 구성하고 각 양식 컨트롤에 대해 텍스트 사용 콘텐츠를 제공하는 것이 포함됩니다. AEM Forms 디자이너는 액세스 가능한 PDF 및 HTML5 양식을 생성하기 위해 이러한 양식 제어 속성의 설정을 지원합니다.

*참고:탭 탐색은 값 합계를 표시하는 계산 필드와 같은 보호된 필드를 포함하지 않습니다. 화면 판독기에서 보호된 필드의 값을 읽으려면 보호된 필드의 위나 옆에 빈 읽기 전용 필드를 배치합니다. 보호된 필드의 값을 새 읽기 전용 필드에 할당합니다. 화면 판독기 또는 탭 탐색에서는 이 읽기 전용 필드를 선택하고 보호된 필드의 값으로 말할 수 있습니다.*

AEM Forms Designer에는 화면 판독기에 전달할 수 있는 다양한 텍스트 옵션이 포함되어 있습니다. 양식의 각 개체에 대해 사용자는 화면 판독기 텍스트에 대한 여러 설정 중 하나를 지정할 수 있습니다.

* 사용자 지정 화면 판독기 텍스트로서, 액세서빌러티 팔레트를 사용하여 설정할 수 있습니다. 작성자는 단추 및 필드의 이름과 목적에 주석을 달 수 있습니다.
* 도구 설명(액세서빌러티 팔레트에서 설정할 수 있음).
* 양식의 필드에 대한 캡션
* 바인딩 탭의 이름 옵션에 지정된 객체 이름

![접근성](assets/accessibility.png)

Form 컨트롤에서 도구 설명, 화면 Reader 텍스트 및 캡션과 같은 여러 옵션을 사용할 수 있으면 화면 Reader에서 이러한 속성 중 하나만 사용합니다. 기본 순서는 사용자 정의 화면 Reader 텍스트, 도구 설명, 캡션 및 이름입니다. 액세스 가능성 팔레트에서 화면 Reader **우선순위** 옵션을 사용하여 기본 순서를 재정의할 수 있습니다.
