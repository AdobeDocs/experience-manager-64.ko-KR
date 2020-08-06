---
title: 개발자 모드
seo-title: 개발자 모드
description: 개발자 모드에서는 개발자에게 현재 페이지에 대한 정보를 제공하는 여러 개의 탭이 있는 사이드 패널이 열립니다
seo-description: 개발자 모드에서는 개발자에게 현재 페이지에 대한 정보를 제공하는 여러 개의 탭이 있는 사이드 패널이 열립니다
uuid: 2ff0d85e-fe49-4506-b6d6-74cc060d7ea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: efbe46a3-c37f-4b67-8b3a-188cfc75118b
translation-type: tm+mt
source-git-commit: 185bdd83b8b67671a31aa3f341b80614ed819b6c
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 2%

---


# 개발자 모드{#developer-mode}

AEM에서 페이지를 편집할 때 개발자 모드를 비롯한 여러 [모드를](/help/sites-authoring/author-environment-tools.md#page-modes) 사용할 수 있습니다. 이렇게 하면 개발자에게 현재 페이지에 대한 정보를 제공하는 여러 탭이 있는 사이드 패널이 열립니다. 세 탭은 다음과 같습니다.

* **[구조](#components)**및 성능 정보를 보기 위한 구성 요소입니다.
* **[테스트 실행](#tests)**및 결과 분석 테스트
* **[오류가](#errors)**발생하여 문제가 발생할 수 있습니다.

이러한 도움말은 개발자가 다음을 수행하는 데 도움이 됩니다.

* Discover: 어떤 페이지로 구성됩니까?
* 디버그: 언제 어디에서 그리고 언제 어떤 일이 발생하는지를 이해하는 데 도움이 됩니다.
* 테스트: 는 응용 프로그램이 예상대로 작동합니까?

>[!CAUTION]
>
>개발자 모드:
>
>* 터치 활성화 UI에서만 사용할 수 있습니다(페이지 편집 시).
>* 모바일 장치나 데스크탑의 작은 창에서는 사용할 수 없습니다(공간 제한 때문).
   >   * 너비가 1024px 미만이면 발생합니다.
>* 그룹의 구성원인 사용자만 사용할 수 `administrators` 있습니다.


>[!CAUTION]
>
>개발자 모드는 nosamplecontent 실행 모드를 사용하지 않는 표준 작성 인스턴스에서만 사용할 수 있습니다.
>
>필요한 경우 다음을 사용하도록 구성할 수 있습니다.
>
>* nosampleconcontent run-mode를 사용하는 작성 인스턴스에서
>* 게시 인스턴스

>
>
사용 후 다시 비활성화해야 합니다.

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* 기술 자료 문서, [AEM TouchUI 문제](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)해결, 추가 팁 및 도구를 참조하십시오.
>* AEM Gems 세션 - [AEM 6.0 개발자 모드](https://docs.adobe.com/content/ddc/en/gems/aem-6-0-developer-mode.html).


## 개발자 모드 열기 {#opening-developer-mode}

개발자 모드는 페이지 편집기에 사이드 패널로 구현됩니다. 패널을 열려면 페이지 편집기의 도구 모음 **에 있는 모드 선택기에서** 개발자를 선택합니다.

![chlimage_1-229](assets/chlimage_1-229.png)

패널은 두 개의 탭으로 나뉘어집니다.

* **[구성 요소](/help/sites-developing/developer-mode.md#components)**- 작성자의[컨텐츠 트리와 유사한 구성 요소](/help/sites-authoring/author-environment-tools.md#content-tree)트리를 보여줍니다

* **[오류](/help/sites-developing/developer-mode.md#errors)**- 문제가 발생하면 각 구성 요소에 대한 세부 정보가 표시됩니다.

### 구성 요소 {#components}

![chlimage_1-230](assets/chlimage_1-230.png)

다음과 같은 구성 요소 트리가 표시됩니다.

* 페이지에서 렌더링되는 구성 요소 및 템플릿의 체인(SLY, JSP 등)에 대한 개요를 설명합니다. 계층 내의 컨텍스트를 표시하도록 트리를 확장할 수 있습니다.
* 구성 요소를 렌더링하는 데 필요한 서버측 계산 시간을 표시합니다.
* 트리를 확장하고 트리 내의 특정 구성 요소를 선택할 수 있습니다. 선택 기능에서는 구성 요소 세부 사항에 액세스할 수 있습니다. 예:

   * 저장소 경로
   * 스크립트 링크(CRXDE Lite에서 액세스)

* 선택한 구성 요소(컨텐츠 플로우에서 파란색 테두리로 표시됨)가 컨텐츠 트리에서 강조 표시됩니다(또는 그 반대).

이를 통해 다음을 수행할 수 있습니다.

* 구성 요소당 렌더링 시간을 결정하고 비교합니다.
* 계층 구조를 보고 이해합니다.
* 느린 구성 요소를 찾아 페이지 로드 시간을 파악하고 개선합니다.

각 구성 요소 항목은 다음과 같이 표시될 수 있습니다.

![chlimage_1-231](assets/chlimage_1-231.png)

* **세부 사항 보기**: 목록이 표시되는 링크:

   * 구성 요소를 렌더링하는 데 사용되는 모든 구성 요소 스크립트.
   * 이 특정 구성 요소에 대한 저장소 컨텐츠 경로입니다.

   ![chlimage_1-232](assets/chlimage_1-232.png)

* **스크립트 편집**: 링크:

   * CRXDE Lite에서 구성 요소 스크립트를 엽니다.

* 구성 요소 항목(화살표 머리)을 확장하면 다음 항목이 표시될 수도 있습니다.

   * 선택한 구성 요소 내의 계층 구조.
   * 분리된 선택된 구성 요소의 렌더링 시간, 그 안에 중첩된 개별 구성 요소 및 결합된 합계에 대한 렌더링 시간입니다.

   ![chlimage_1-233](assets/chlimage_1-233.png)

>[!CAUTION]
>
>일부 링크는 아래의 스크립트를 가리킵니다 `/libs`. 그러나 이러한 항목은 참조용이므로, 변경 사항이 손실될 수 있으므로 아래의 어떤 것도 편집할 **수** 없습니다 `/libs`. 이는 핫픽스/기능 팩을 업그레이드하거나 적용할 때마다 이 분기가 변경될 수 있기 때문입니다. 필요한 모든 변경 사항은 Overlays 및 Overrides `/apps`를 [참조하십시오](/help/sites-developing/overlays.md).

### 오류 {#errors}

![chlimage_1-234](assets/chlimage_1-234.png)

오류 **탭이 항상 비어** 있기를 바라지만(위와 같이) 문제가 발생하면 각 구성 요소에 대해 다음 세부 정보가 표시됩니다.

* 구성 요소가 오류 로그에 오류 내용과 오류 세부 정보를 포함한 항목을 기록하는 경우 경고 및 CRXDE Lite 내의 해당 코드에 직접 연결합니다.
* 구성 요소에서 관리 세션을 여는 경우 경고.

예를 들어 정의되지 않은 메서드가 호출되는 경우 오류 **탭에 오류가** 표시됩니다.

![chlimage_1-235](assets/chlimage_1-235.png)

구성 요소 탭의 트리에 있는 구성 요소 항목에도 오류가 발생하면 표시기로 표시됩니다.

### 테스트 {#tests}

>[!CAUTION]
>
>AEM 6.2에서는 개발자 모드의 테스트 기능이 독립 실행형 도구 애플리케이션으로 재구현되었습니다.
>
>자세한 내용은 UI [테스트를 참조하십시오](/help/sites-developing/hobbes.md).
