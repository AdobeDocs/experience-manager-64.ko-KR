---
title: AEM 및 웹 접근성 지침
seo-title: AEM 및 웹 접근성 지침
description: AEM을 사용하여 액세스 가능한 웹 사이트 및 컨텐츠를 만드는 방법을 알아봅니다.
seo-description: AEM을 사용하여 액세스 가능한 웹 사이트 및 컨텐츠를 만드는 방법을 알아봅니다.
uuid: b68281af-3e8a-4842-b762-1c59f9132795
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing-accessibility, introduction
content-type: reference
discoiquuid: 13c7e0bd-54af-49f3-9743-075ce6f3314d
exl-id: f0ccdeae-3dbb-4dba-89cf-4c8b759da22b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 48%

---

# AEM 및 웹 접근성 지침{#aem-and-the-web-accessibility-guidelines}

장애나 제한 사항에 관계없이 웹 컨텐츠를 타겟 대상자가 가능한 한 이용할 수 있도록 설계해야 할 많은 사회적, 경제적 및 법적 동기가 있습니다. 따라서 웹 액세스 가능성은 좋은 웹 디자인의 측면에서 점점 더 중요해지고 있습니다.

AEM에 영향을 주는 액세스 가능한 웹 사이트 및 컨텐츠 만들기:

* 액세스 가능성 기능이 올바로 활성화되도록 AEM(Adobe Experience Manager)을 구성할 책임이 있는 관리자
* WCAG 2.0의 주요 지침을 지원하는 웹 사이트를 만들기 위해 이러한 기능을 사용하는 작성자

   액세스 가능한 컨텐츠를 만드는 것은 프로세스입니다. AEM에서는 기능을 제공하지만 컨텐츠 작성자는 액세스 가능한 컨텐츠를 만드는 데 필요한 기법을 따라야 합니다.

* 템플릿 개발자도 웹 사이트 디자인을 구현할 때 이러한 문제를 알고 있어야 합니다.

## 추가 정보 {#further-information}

다음 페이지 및 섹션에서는 정보 및 지침을 제공합니다.

* [액세스 가능한 사이트를 만들려면 리치 텍스트 편집기 구성 참조](/help/sites-administering/rte-accessible-content.md)

   관리자가 액세스 가능한 컨텐츠를 만들려면 AEM을 구성하는 방법에 대한 지침입니다.

* [액세스 가능한 컨텐츠 만들기(WCAG 2.0 적합성)](/help/sites-authoring/creating-accessible-content.md)

   WCAG 2.0 지침에서는 레벨 A 및 레벨 AA 적합성 수준에 대한 성공 기준 목록을 제공합니다. 이 페이지에서는 AEM에서 다루는 성공 기준과 컨텐츠를 생성할 때 충족하는 방법을 자세히 설명합니다.

* [WCAG 2.0에 대한 빠른 안내서](/help/managing/qg-wcag.md)

   WCAG 2.0에 대한 배경 정보.

* [액세스 가능한 응용 Forms 만들기](/help/forms/using/creating-accessible-adaptive-forms.md)

   Adobe Experience Manager(AEM)에는 다양한 기능을 가진 사용자를 위해 적응형 양식의 유용성을 향상시키는 많은 기능이 포함되어 있습니다. 또한 이 솔루션은 양식 작성자가 액세스 가능한 적응형 양식을 만드는 데 도움이 됩니다.

## World Wide Web Consortium 및 WCAG 2.0 {#world-wide-web-consortium-and-wcag}

[World Wide Web Consortium(W3C)](https://www.w3.org/)은 웹 표준 개발을 위한 국제 커뮤니티입니다. 웹 디자이너와 개발자가 액세스 가능한 웹 사이트를 제작할 수 있도록 지원하기 위해 [Web Accessibility Initiative(WAI)](https://www.w3.org/WAI/)에서는 2008년 12월에 [웹 컨텐츠 액세스 가능성 지침(WCAG) 2.0](https://www.w3.org/TR/WCAG20/)을 발행했습니다(1999년에 게시된 원래 버전 업데이트).

>[!NOTE]
>
>[이(가) 업데이트된 버전의 지침](https://www.w3.org/TR/WCAG21/)은 현재 개발 중이지만 이 버전의 AEM에서는 고려되지 않습니다.

컨텐츠 작성자 및/또는 웹 사이트 소유자는 Adobe Experience Manager을 사용하여 WCAG 2.0 Level A 및 Level AA 성공 기준을 충족하는 웹 컨텐츠를 만들 수 있습니다.

WCAG 2.0의 구체적인 특징은 [WCAG 2.0에 대한 빠른 안내서](/help/managing/qg-wcag.md)에 설명되어 있습니다.

### WCAG 2.0 액세스 가능성 적합성 수준 {#wcag-accessibility-conformance-levels}

WCAG 2.0에서는 액세스 가능성 수준](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html)에 대한 [지침(관련 성공 기준 포함)을 제공합니다.

AEM과 관련된 이러한 적합성[레벨 A 및 AA 적합성](/help/sites-authoring/creating-accessible-content.md)에 대해 다룹니다. 사이트를 만들 때에는 사이트가 따라야 할 전반적인 수준을 결정해야 합니다.

>[!NOTE]
>
>특정 유형의 컨텐츠에 대한 Level AAA 성공 기준을 모두 만족시킬 수는 없으므로 이것을 필요한 적합성 수준으로 권장하지는 않습니다.

## Adobe에서의 액세스 가능성 {#accessibility-at-adobe}

자세한 내용은 [Adobe 액세스 가능성 리소스 센터](https://www.adobe.com/accessibility/)에서 확인하십시오.
