---
title: 적응형 템플릿 렌더링
seo-title: 적응형 템플릿 렌더링
description: 적응형 템플릿 렌더링
seo-description: 'null'
uuid: 97226ae1-e42a-40ae-a5e0-886cd77559d8
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: f5cb0e98-0d6e-4f14-9b94-df1a9d8cbe5b
exl-id: a2adc825-2a18-42b8-a639-c48243b2279c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 4%

---

# 적응형 템플릿 렌더링{#adaptive-template-rendering}

적응형 템플릿 렌더링에서는 변형으로 페이지를 관리하는 방법을 제공합니다. 원래 모바일 장치용 다양한 HTML 출력(예: 기능 전화기와 스마트폰)을 전달하는 데 유용했지만, 다른 마크업 또는 HTML 출력이 필요한 다양한 장치에 경험을 전달해야 할 때 유용합니다.

## 개요 {#overview}

템플릿은 일반적으로 응답형 그리드를 기반으로 작성되며, 이러한 템플릿을 기반으로 작성된 페이지는 완전히 응답형이며, 클라이언트 장치의 뷰포트에 자동으로 조정됩니다. 작성자는 페이지 편집기에서 에뮬레이터 도구 모음을 사용하여 레이아웃을 특정 장치에 타깃팅할 수 있습니다.

적응형 렌더링을 지원하도록 템플릿을 설정할 수도 있습니다. 장치 그룹이 올바르게 구성되면 에뮬레이터 모드에서 장치를 선택할 때 URL에서 다른 선택기로 페이지가 렌더링됩니다. 선택기를 사용하면 URL을 통해 특정 페이지 렌더링을 직접 호출할 수 있습니다.

장치 그룹을 설정할 때 다음 사항을 기억하십시오.

* 모든 장치는 하나 이상의 장치 그룹에 있어야 합니다.
* 장치는 여러 장치 그룹에 있을 수 있습니다.
* 장치는 여러 장치 그룹에 있을 수 있으므로 선택기를 결합할 수 있습니다.
* 선택기의 조합은 저장소에서 유지되므로 하향식으로 평가됩니다.

>[!NOTE]
>
>응답형 디자인을 지원하는 것으로 인식되는 장치는 적응형 레이아웃이 필요하지 않다고 가정하므로 장치 그룹 **응답형 장치**&#x200B;에는 선택기가 없습니다

## 구성 {#configuration}

적응형 렌더링 선택기는 기존 장치 그룹에 대해 구성하거나 직접 만든 [그룹에 구성할 수 있습니다.](/help/sites-developing/mobile.md#device-groups)

이 예에서는 We.Retail 내에서 **경험 페이지** 템플릿의 일부로 기존 장치 그룹 **스마트 폰**&#x200B;을 구성하려고 합니다.

1. `http://localhost:4502/miscadmin#/etc/mobile/groups`에서 적응형 선택기가 필요한 장치 그룹을 편집합니다

   **에뮬레이터 사용 안 함** 옵션을 설정하고 저장합니다.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. 장치 그룹 **스마트 폰**&#x200B;이 다음 단계의 템플릿 및 페이지 구조에 추가된 경우 선택기는 **Blackberry** 및 **iPhone 4**&#x200B;에 사용할 수 있습니다.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. CRX DE Lite를 사용하면 템플릿 구조의 다중 값 문자열 속성 `cq:deviceGroups`에 추가하여 템플릿에서 장치 그룹을 사용할 수 있습니다.

   `/conf/<your-site>/settings/wcm/templates/<your-template>/structure/jcr:content`

   예를 들어 스마트폰 장치 그룹을 추가하려는 경우:

   `/conf/we-retail/settings/wcm/templates/experience-page/structure/jcr:content`

   ![chlimage_1-159](assets/chlimage_1-159.png)

1. CRX DE Lite를 사용하면 장치 그룹을 사이트 구조의 다중 값 문자열 속성 `cq:deviceGroups`에 추가하여 사이트에서 사용할 수 있습니다.

   `/content/<your-site>/jcr:content`

   예를 들어 **스마트 폰** 장치 그룹을 허용하려는 경우:

   `/content/we-retail/jcr:content`

   ![chlimage_1-160](assets/chlimage_1-160.png)

이제 페이지 편집기에서 [에뮬레이터](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints)를 사용하고(예: [레이아웃](/help/sites-authoring/responsive-layout.md)을 수정하는 경우) 구성된 장치 그룹의 장치를 선택하면 페이지가 URL의 일부로 선택기로 렌더링됩니다.

이 예제에서는 **Experience Page** 템플릿을 기반으로 페이지를 편집하고 에뮬레이터에서 iPhone 4를 선택하면 선택기를 `arctic-surfing-in-lofoten.html` 대신 `arctic-surfing-in-lofoten.smart.html`으로 포함하는 페이지가 렌더링됩니다

이 선택기를 사용하여 페이지를 직접 호출할 수도 있습니다.

![chlimage_1-161](assets/chlimage_1-161.png)
