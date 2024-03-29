---
title: We.Retail에서 핵심 구성 요소 시험 사용
seo-title: Trying out Core Components in We.Retail
description: We.Retail에서 핵심 구성 요소 시험 사용
seo-description: null
uuid: 8d1cea0b-99d9-49b2-b275-41f14864b1ff
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: af3cd818-61cf-4da1-bfb5-87540911ddd5
exl-id: b77d0e6b-3005-4dba-8e88-70b4d04b1eba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 7%

---

# We.Retail에서 핵심 구성 요소 시험 사용{#trying-out-core-components-in-we-retail}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

핵심 구성 요소는 쉬운 확장성을 제공하고 프로젝트에 간편하게 통합할 수 있는 현대적이고 유연한 구성 요소입니다. 핵심 구성 요소는 HTL, 사용 편의성, 구성 기능, 버전 관리 및 확장성과 같은 몇 가지 주요 디자인 원칙에 따라 구축되었습니다. We.Retail은 핵심 구성 요소를 기반으로 구축되었습니다.

## 사용해 보기 {#trying-it-out}

1. We.Retail 샘플 컨텐츠로 AEM을 시작하고 [구성 요소 콘솔](/help/sites-authoring/default-components-console.md).

   **전역 탐색 -> 도구 -> 구성 요소**

1. 구성 요소 콘솔에서 레일을 열면 특정 구성 요소 그룹에 대해 필터링할 수 있습니다. 핵심 구성 요소는

   * `.core-wcm`: 표준 코어 구성 요소
   * `.core-wcm-form`: 양식 제출 핵심 구성 요소

   선택 `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. 모든 핵심 구성 요소의 이름은 다음과 같습니다 **v1**&#x200B;를 반영하는 것은 이 핵심 구성 요소의 첫 번째 버전임을 나타냅니다. 앞으로 일반 버전은 AEM과 버전 호환되며 간편한 업그레이드를 통해 최신 기능을 이용할 수 있습니다.
1. 클릭 **텍스트(v1)**.

   다음을 참조하십시오. **리소스 유형** 구성 요소의 `/apps/core/wcm/components/text/v1/text`. 핵심 구성 요소는 `/apps/core/wcm/components` 및 은 구성 요소별로 버전이 지정됩니다.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. 을(를) 클릭합니다. **설명서** 탭하여 구성 요소에 대한 개발자 설명서를 참조하십시오.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. 구성 요소 콘솔로 돌아갑니다. 그룹에 대한 필터링 **We.Retail** 을(를) 선택하고 을(를) 선택합니다. **텍스트** 구성 요소.
1. 다음을 참조하십시오. **리소스 유형** 은 구성 요소에 예상대로 다음 값을 가리킵니다. `/apps/weretail` 하지만 **리소스 슈퍼 유형** 핵심 구성 요소로 돌아갑니다. `/apps/core/wcm/components/text/v1/text`.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. 을(를) 클릭합니다. **라이브 사용량** 탭하여 이 구성 요소가 현재 사용 중인 페이지를 확인합니다. 첫 번째 **감사합니다** 페이지를 편집할 수 있습니다.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. 감사 인사 페이지에서 텍스트 구성 요소를 선택하고 구성 요소의 편집 메뉴에서 상속 취소 아이콘을 클릭합니다.

   [We.Retail은 세계화된 사이트 구조를 가지고 있습니다](/help/sites-developing/we-retail-globalized-site-structure.md) 컨텐츠가 언어 마스터에서 로 푸시되는 위치 [상속이라는 메커니즘을 통한 라이브 카피](/help/sites-administering/msm.md). 이러한 이유로 사용자가 수동으로 텍스트를 편집할 수 있도록 하려면 상속을 취소해야 합니다.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. 을 클릭하여 취소를 확인합니다 **예**.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. 상속이 취소되고 텍스트 구성 요소를 선택하면 더 많은 옵션을 사용할 수 있습니다. 편집** 클릭합니다**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. 이제 텍스트 구성 요소에 사용할 수 있는 편집 옵션을 확인할 수 있습니다.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. 에서 **페이지 정보** 메뉴 선택 **템플릿 편집**.
1. 페이지의 템플릿 편집기에서 **정책** 아이콘 사용 **레이아웃 컨테이너** 섹션에 있는 마지막 항목이 될 필요가 없습니다.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. 핵심 구성 요소를 사용하면 템플릿 작성자가 페이지 작성자가 사용할 수 있는 속성을 구성할 수 있습니다. 여기에는 허용되는 붙여넣기 소스, 서식 옵션, 사용 가능한 단락 스타일 등과 같은 기능이 포함됩니다.

   이러한 디자인 대화 상자는 많은 핵심 구성 요소에 대해 사용할 수 있으며 템플릿 편집기와 함께 작동합니다. 활성화되면 구성 요소 편집기를 통해 작성자가 사용할 수 있습니다.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## 추가 정보 {#further-information}

핵심 구성 요소에 대한 자세한 내용은 작성 문서를 참조하십시오 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko) 핵심 구성 요소 및 개발자 문서의 기능에 대한 개요 [핵심 구성 요소 개발](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) 기술 개요

또한 당신은 더 많은 조사를 원할 수도 있습니다 [편집 가능한 템플릿](/help/sites-developing/we-retail-editable-templates.md). 작성 문서를 참조하십시오 [페이지 템플릿 만들기](/help/sites-authoring/templates.md) 또는 개발자 문서 페이지 [템플릿 - 편집 가능](/help/sites-developing/page-templates-editable.md) 를 참조하십시오.
