---
title: 테스트 및 추적 도구
seo-title: 테스트 및 추적 도구
description: AEM은 구성 요소 UI를 테스트하는 프레임워크와 구성 요소를 테스트 및 디버깅하는 메커니즘을 제공합니다
seo-description: AEM은 구성 요소 UI를 테스트하는 프레임워크와 구성 요소를 테스트 및 디버깅하는 메커니즘을 제공합니다
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
translation-type: tm+mt
source-git-commit: 60f36a33471dbbd9ca877dbbedc82ade606a125c
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 4%

---


# 테스트 및 추적 도구{#testing-and-tracking-tools}

## 테스트 {#testing}

AEM 제공:

* [구성 요소 UI 테스트를 위한 프레임워크입니다](/help/sites-developing/hobbes.md).
* [구성 요소를 테스트 및 디버깅하는 메커니즘입니다](/help/sites-developing/developer-mode.md).

다음은 두 개의 오픈 소스 테스트 도구입니다.

**셀레늄**

Selenium은 활동당 한 명의 사용자가 있는 브라우저에서 함수 테스트에 사용됩니다. 테스트 단계(클릭)를 HTML 테이블 또는 Java 클래스로 기록합니다.

자세한 내용은 https://www.seleniumhq.org/을 [참조하십시오](https://www.seleniumhq.org/).

**JMeter**

JMeter는 요청을 추적하는 데 사용되며 기능, 성능 및 스트레스 테스트에 사용할 수 있습니다.

자세한 내용은 http://jakarta.apache.org/jmeter/을 [참조하십시오](http://jakarta.apache.org/jmeter/).

또한 테스트 자동화 및 테스트 계획 관리를 위한 많은 독점적인 툴이 있습니다.

## 추적 {#tracking}

다음 도구는 쉽게 사용할 수 있습니다. 그러나 모든 경우에 있어서 중요한 문제는 파트너 및 고객 등 프로젝트 팀의 모든 구성원에게 데이터를 사용할 수 있다는 것입니다.

**벅질라**

자체 요구 사항에 맞게 구성할 수 있는 버그 추적 시스템.

**스프레드시트**

버그 추적 툴은 아니지만 이해하기 쉬울 뿐만 아니라 대부분의 사용자가 자신의 기능을 직접 경험할 수 있으므로 스프레드시트는 이러한 용도로 악용되는 경우가 많습니다.

추적에 사용되는 경우:

* 간단해야 한다.
* 개별 스프레드시트의 수는 최소한으로 유지되어야 합니다.
* 정기적으로 업데이트해야 합니다.
* 마스터 사본은 한 개만 유지 관리되어야 하며 모든 사람이 마스터 사본이 어디에 있는지 알아야 합니다.
* 모든 프로젝트 구성원이 액세스할 수 있어야 합니다.
* 보안은 문제가 되고(대기업에서 종종 발생) 일반 액세스가 불가능할 경우, 모두가 이것이 복사본이라고 알고 있고 업데이트할 수 없는 한 사본을 배포할 수 있습니다.

버그 및 기능 요구 사항을 추적하기 위한 다양한 독점적 툴이 있습니다.
