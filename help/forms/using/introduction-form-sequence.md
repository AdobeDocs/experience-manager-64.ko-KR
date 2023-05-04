---
title: 다단계 양식 시퀀스 소개
seo-title: Introduction to multi-step form sequence
description: AEM Forms을 사용하면 사용자가 적응형 양식을 탐색하고 채울 양식 패널 시퀀스를 정의할 수 있습니다.
seo-description: With AEM Forms, you can define a sequence of form panel in which you want users to navigate and fill an adaptive form.
uuid: b2b94e4c-0c28-47ba-8e23-fd8742baf71c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 4a51ebc4-e019-4fc5-93a1-d97f695126f5
feature: Adaptive Forms
exl-id: eec8bcbe-e2ba-42f1-98ea-08a4ca723e48
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 51%

---

# 다단계 양식 시퀀스 소개 {#introduction-to-multi-step-form-sequence}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

적응형 양식을 사용하면 양식 작성자가 여러 단계로 구성된 데이터 캡처 경험을 손쉽게 만들 수 있습니다. 여러 패널을 만들고 각 패널을 다른 탐색 패턴과 연결하는 기본 제공 지원이 제공됩니다. 양식 작성자는 논리 섹션의 양식 필드를 그룹화하고 그룹을 패널로 나타낼 수 있습니다. 패널 레이아웃을 사용하여 패널 간 전체 탐색을 제어합니다. 작성자는 마법사 레이아웃을 사용하여 순차적으로 배치하거나 탭 레이아웃을 사용하여 임시 방식으로 패널을 다른 레이아웃으로 배치하도록 선택할 수 있습니다. 패널 레이아웃에 대한 자세한 내용은 [적응형 양식의 레이아웃 기능](/help/forms/using/layout-capabilities-adaptive-forms.md).

일반적인 양식 작성 경험에는 단순히 데이터를 캡처하는 것 이외의 단계가 추가되어 있습니다. 완벽한 양식 제출에는 디지털 양식 서명, 양식에 채워진 정보 확인, 처리 결제 등 다른 단계가 포함될 수 있습니다. 상황에 따라 다릅니다.

사용 사례에서 데이터 캡처 단계 세트를 요구하는 경우 또는 특정 단계를 수행해야 하는 규정이 있는 경우 AEM Forms에서 양식 간에 이러한 공통된 구조를 적용하는 방법을 제공합니다. 양식 구조의 사전 계획된 구현은 양식에 대한 단계 시퀀스를 정의합니다. ![다단계 양식 시퀀스의 예](assets/formpipeline.png)

양식의 채우기, 확인, 서명 및 확인 단계에 대한 시퀀스를 만들어야 하는 사용 사례를 살펴보겠습니다. 해당 시퀀스를 생성하는 단계는 다음과 같습니다.

1. 양식 템플릿을 정의하고 필요한 패널을 추가합니다. 시퀀스의 각 단계마다 패널이 하나씩 있어야 합니다. 하지만 패널 내에 하위 패널을 포함할 수 있습니다.

   이 예에서 다음 패널을 추가할 수 있습니다.

   * **채우기**: 데이터 캡처에 대한 양식 필드가 포함됩니다. 여기서는 중첩된 하위 패널을 포함하여 개인, 가족, 재무 등과 같은 다양한 유형의 정보에 대한 섹션을 만들 수 있습니다.
   * **확인**: 여기에는 다음 항목이 포함되어 있습니다 **확인** XFA 기반 적응형 양식에 사용할 수 있는 구성 요소입니다. 확인을 위해 채우기 패널에서 캡처된 정보를 읽기 전용 모드로 표시합니다.
   * **전자 서명**: 여기에는 다음 항목이 포함되어 있습니다 **Sign** XFA 기반 적응형 양식에 사용할 수 있는 구성 요소입니다. 다음과 같은 서명 서비스를 제공합니다.

      * Adobe Document Cloud eSign 서비스
      * 스크리블 서명
   * **확인**: 사용자가 양식에 서명하고 시퀀스의 확인(요약) 단계에 도달하면 양식 제출 확인 메시지를 표시하는 **요약** 구성 요소가 포함됩니다. 작성자는 요약 구성 요소의 텍스트를 구성하고, 감사 메시지를 표시하고, 생성된 PDF 등의 링크를 표시합니다.


1. 루트 패널의 레이아웃을 **[!UICONTROL 마법사]**&#x200B;로 선택합니다.
1. 나머지 단계를 완료하여 양식 템플릿을 만듭니다. 자세한 내용은 [사용자 지정 적응형 양식 템플릿 만들기](/help/forms/using/custom-adaptive-forms-templates.md).

양식 템플릿에서 양식 시퀀스를 정의하고 나서 이를 사용하여 기본 구조를 시퀀스로 바로 정의하는 양식을 생성할 수 있지만 항상 요구 사항에 맞게 양식을 사용자 지정할 수 있습니다.
