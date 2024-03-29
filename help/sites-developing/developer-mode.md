---
title: 개발자 모드
seo-title: Developer Mode
description: 개발자 모드에서는 개발자에게 현재 페이지에 대한 정보를 제공하는 여러 탭이 있는 사이드 패널을 엽니다
seo-description: Developer mode opens a side panel with several tabs that provide a developer with infomation about the current page
uuid: 2ff0d85e-fe49-4506-b6d6-74cc060d7ea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: efbe46a3-c37f-4b67-8b3a-188cfc75118b
exl-id: 733eddf1-48f9-45c2-a1b4-138cf32b4b59
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 3%

---

# 개발자 모드{#developer-mode}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서 페이지를 편집할 때 [모드](/help/sites-authoring/author-environment-tools.md#page-modes) 개발자 모드를 포함하여 을 사용할 수 있습니다. 이렇게 하면 개발자에게 현재 페이지에 대한 정보를 제공하는 여러 탭이 있는 사이드 패널이 열립니다. 세 개의 탭은 다음과 같습니다.

* **[구성 요소](#components)** 구조 및 성능 정보를 볼 수 있습니다.
* **[테스트](#tests)** 테스트 실행 및 결과 분석
* **[오류](#errors)** 문제가 발생하는지 확인합니다.

개발자는 다음 작업을 수행할 수 있습니다.

* 검색: 어떤 페이지로 구성됩니까?
* 디버그: 어디에서 언제 그리고 언제 무슨 일이 일어나는가 하는 것은 문제를 해결하는 데 도움이 됩니다.
* 테스트: 응용 프로그램이 예상대로 작동합니까?

>[!CAUTION]
>
>개발자 모드:
>
>* 터치 활성화 UI에서만 사용할 수 있습니다(페이지를 편집할 때).
>* 모바일 장치나 데스크탑의 작은 창에서 사용할 수 없습니다(공간 제한 때문에).
   >   * 너비가 1024px 미만인 경우 발생합니다.
>* 의 구성원인 사용자만 사용할 수 있습니다 `administrators` 그룹에 속해 있어야 합니다.


>[!CAUTION]
>
>개발자 모드는 nosamplecontent 실행 모드를 사용하지 않는 표준 작성자 인스턴스에서만 사용할 수 있습니다.
>
>필요한 경우 다음을 사용하도록 구성할 수 있습니다.
>
>* nosamplecontent 실행 모드를 사용하는 작성자 인스턴스
>* 게시 인스턴스
>
>사용 후 다시 비활성화해야 합니다.

>[!NOTE]
>
>다음을 참조하십시오.
>
>* 기술 자료 문서, [AEM TouchUI 문제 해결](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html): 추가 팁과 도구를 참조하십시오.
>* AEM Gems 세션 정보 [AEM 6.0 개발자 모드](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html).


## 개발자 모드 열기 {#opening-developer-mode}

개발자 모드가 페이지 편집기에 사이드 패널로 구현됩니다. 패널을 열려면 **개발자** 페이지 편집기의 도구 모음에 있는 모드 선택기에서 다음을 수행합니다.

![chlimage_1-229](assets/chlimage_1-229.png)

패널은 다음 두 개의 탭으로 나뉘어 있습니다.

* **[구성 요소](/help/sites-developing/developer-mode.md#components)** - 다음과 유사한 구성 요소 트리가 표시됩니다 [컨텐츠 트리](/help/sites-authoring/author-environment-tools.md#content-tree) 작성자

* **[오류](/help/sites-developing/developer-mode.md#errors)** - 문제가 발생하면 각 구성 요소에 대해 세부 사항이 표시됩니다.

### 구성 요소 {#components}

![chlimage_1-230](assets/chlimage_1-230.png)

다음과 같은 구성 요소 트리가 표시됩니다.

* 페이지에서 렌더링되는 구성 요소 및 템플릿 체인(SLY, JSP 등)에 대해 설명합니다. 트리를 확장하여 계층 내에 컨텍스트를 표시할 수 있습니다.
* 구성 요소를 렌더링하는 데 필요한 서버측 계산 시간을 표시합니다.
* 트리를 확장하고 트리 내에서 특정 구성 요소를 선택할 수 있습니다. 선택 사항에서는 구성 요소 세부 사항에 액세스할 수 있습니다. 예:

   * 저장소 경로
   * 스크립트에 대한 링크(CRXDE Lite에서 액세스)

* 선택한 구성 요소(컨텐츠 플로우에서 파란색 테두리로 표시됨)가 컨텐츠 트리에 강조 표시됩니다. 그 반대의 경우도 마찬가지입니다.

이를 통해 다음을 수행할 수 있습니다.

* 구성 요소당 렌더링 시간을 결정하고 비교합니다.
* 계층 구조를 보고 이해합니다.
* 느린 구성 요소를 찾아 페이지 로드 시간을 파악하고 개선합니다.

각 구성 요소 항목에는 (예:) 다음 항목이 표시될 수 있습니다.

![chlimage_1-231](assets/chlimage_1-231.png)

* **세부 사항 보기**: 다음을 보여주는 목록에 대한 링크:

   * 구성 요소를 렌더링하는 데 사용되는 모든 구성 요소 스크립트.
   * 이 특정 구성 요소의 저장소 컨텐츠 경로입니다.

   ![chlimage_1-232](assets/chlimage_1-232.png)

* **스크립트 편집**: 링크:

   * CRXDE Lite에서 구성 요소 스크립트를 엽니다.

* 구성 요소 항목(화살표 헤드)을 확장하면 다음 내용이 표시될 수도 있습니다.

   * 선택한 구성 요소 내의 계층 입니다.
   * 격리된 선택한 구성 요소의 렌더링 시간, 구성 요소 내에 중첩된 개별 구성 요소 및 결합된 합계입니다.

   ![chlimage_1-233](assets/chlimage_1-233.png)

>[!CAUTION]
>
>일부 링크는 `/libs`. 하지만 이것은 참조용입니다. **필수가 아니어야 합니다.** 다음 내용 편집 `/libs`변경한 사항이 손실될 수 있습니다. 이는 핫픽스/기능 팩을 업그레이드하거나 적용할 때마다 이 분기가 변경 사항에 영향을 주기 때문입니다. 필요한 모든 변경 사항은 `/apps`를 참조하십시오. [오버레이 및 무시](/help/sites-developing/overlays.md).

### 오류 {#errors}

![chlimage_1-234](assets/chlimage_1-234.png)

바라건대 **오류** 탭은 항상 비어 있지만(위와 같이) 문제가 발생하면 각 구성 요소에 대해 다음 세부 정보가 표시됩니다.

* 구성 요소가 오류 로그에 항목을 기록하고 오류 세부 정보와 CRXDE Lite 내의 해당 코드에 대한 직접 링크가 있는 경우 경고.
* 구성 요소에서 관리 세션을 여는 경우 경고.

예를 들어 정의되지 않은 메서드가 호출되는 상황에서는 결과 오류가 **오류** 탭:

![chlimage_1-235](assets/chlimage_1-235.png)

구성 요소 탭의 트리에 있는 구성 요소 항목에도 오류가 발생할 때 표시기가 표시됩니다.

### 테스트 {#tests}

>[!CAUTION]
>
>AEM 6.2에서 개발자 모드의 테스트 기능이 독립형 도구 애플리케이션으로 다시 구현되었습니다.
>
>자세한 내용은 [UI 테스트](/help/sites-developing/hobbes.md).
