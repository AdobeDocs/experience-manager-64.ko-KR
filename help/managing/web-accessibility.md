---
title: AEM 및 웹 접근성 지침
seo-title: AEM 및 웹 접근성 지침
description: AEM에서 액세스 가능한 웹 사이트와 컨텐츠를 만드는 방법을 알아봅니다.
seo-description: AEM에서 액세스 가능한 웹 사이트와 컨텐츠를 만드는 방법을 알아봅니다.
uuid: b68281af-3e8a-4842-b762-1c59f9132795
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
content-type: reference
topic-tags: introduction
discoiquuid: 13c7e0bd-54af-49f3-9743-075ce6f3314d
translation-type: tm+mt
source-git-commit: 40c4631e29093e5425cf0b7bd4bcd543a969bd1e
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 48%

---


# AEM 및 웹 접근성 지침{#aem-and-the-web-accessibility-guidelines}

장애나 제한 사항에 관계없이 웹 컨텐츠를 타겟 대상자가 가능한 한 이용할 수 있도록 설계해야 할 많은 사회적, 경제적 및 법적 동기가 있습니다. 따라서 웹 액세스 가능성은 좋은 웹 디자인의 측면에서 점점 더 중요해지고 있습니다.

액세스 가능한 웹 사이트 및 컨텐츠를 제작하여 AEM 효과를 낼 수 있습니다.

* 액세스 가능성 기능이 올바로 활성화되도록 AEM(Adobe Experience Manager)을 구성할 책임이 있는 관리자
* 이러한 기능을 사용하여 WCAG 2.0의 주요 지침을 지원하는 웹 사이트를 제작할 수 있습니다.

   액세스 가능한 컨텐츠를 만드는 것은 프로세스입니다. AEM에서는 기능을 제공하지만 컨텐츠 작성자는 액세스 가능한 컨텐츠를 만드는 데 필요한 기법을 따라야 합니다.

* 템플릿 개발자도 웹 사이트 디자인을 구현할 때 이러한 문제를 알고 있어야 합니다.

## 추가 정보 {#further-information}

다음 페이지 및 섹션에서는 정보 및 지침을 제공합니다.

* [액세스 가능한 사이트 제작을 위한 리치 텍스트 편집기 구성](/help/sites-administering/rte-accessible-content.md)

   관리자가 액세스 가능한 컨텐츠를 제작하기 위해 AEM을 구성할 수 있는 방법에 대한 지침

* [액세스 가능한 컨텐츠 만들기(WCAG 2.0 적합성)](/help/sites-authoring/creating-accessible-content.md)

   WCAG 2.0 지침에서는 레벨 A 및 레벨 AA 적합성 수준에 대한 성공 기준 목록을 제공합니다. 이 페이지에서는 AEM에서 다루는 성공 기준과 컨텐츠를 생성할 때 충족하는 방법을 자세히 설명합니다.

* [WCAG 2.0에 대한 빠른 안내서](/help/managing/qg-wcag.md)

   WCAG 2.0에 대한 배경 정보입니다.

* [액세스 가능한 응용 Forms 만들기](/help/forms/using/creating-accessible-adaptive-forms.md)

   Adobe Experience Manager(AEM)에는 다양한 기능을 가진 사용자를 위한 적응형 양식의 유용성을 높여주는 다양한 기능과 기능이 포함되어 있습니다. 또한 이 솔루션은 양식 작성자가 액세스 가능한 적응형 양식을 만드는 데 도움이 됩니다.

## World Wide Web Consortium 및 WCAG 2.0 {#world-wide-web-consortium-and-wcag}

[World Wide Web Consortium(W3C)](https://www.w3.org/)은 웹 표준 개발을 위한 국제 커뮤니티입니다. 웹 디자이너와 개발자가 액세스 가능한 웹 사이트를 제작할 수 있도록 WAI( [Web Accessibility Initiative)](https://www.w3.org/WAI/) 가 2008년 12월(1999년 [게시되었던 원본 버전 업데이트)](https://www.w3.org/TR/WCAG20/) WCAG(Web Content Accessibility Guidelines) 2.0을 게시했습니다.

>[!NOTE]
>
>An [updated version of the guidelines](https://www.w3.org/TR/WCAG21/) is currently in development, but will not be considered for this version of AEM.

컨텐츠 작성자 및/또는 웹 사이트 소유자는 Adobe Experience Manager을 사용하여 WCAG 2.0 레벨 A 및 레벨 AA 성공 기준을 충족하는 웹 컨텐츠를 만들 수 있습니다.

WCAG 2.0의 구체적인 특징은 [WCAG 2.0에 대한 빠른 안내서](/help/managing/qg-wcag.md)에 설명되어 있습니다.

### WCAG 2.0 접근성 적합성 수준 {#wcag-accessibility-conformance-levels}

WCAG 2.0은 접근성 수준을 다루는 [지침(관련 성공 기준 포함)을 제공합니다](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html).

AEM과 관련되면 레벨 A 및 AA 적합성 [에 적용됩니다](/help/sites-authoring/creating-accessible-content.md). 사이트를 만들 때에는 사이트가 따라야 할 전반적인 수준을 결정해야 합니다.

>[!NOTE]
>
>특정 유형의 컨텐츠에 대한 Level AAA 성공 기준을 모두 만족시킬 수는 없으므로 이것을 필요한 적합성 수준으로 권장하지는 않습니다.

## Adobe에서의 액세스 가능성 {#accessibility-at-adobe}

자세한 내용은 [Adobe 액세스 가능성 리소스 센터](https://www.adobe.com/accessibility/)에서 확인하십시오.
