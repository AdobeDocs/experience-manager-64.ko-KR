---
title: 양식 데이터 모델 사용
seo-title: 양식 데이터 모델 사용
description: 양식 데이터 모델을 사용하여 적응형 양식 및 대화형 커뮤니케이션을 만들고 사용하는 방법을 알아봅니다.
seo-description: 양식 데이터 모델을 사용하여 적응형 양식 및 대화형 커뮤니케이션을 만들고 사용하는 방법을 알아봅니다.
uuid: 9a8bd44a-34a1-41ef-a57b-d5e3dd0a77ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 7a1bfd43-39b1-478b-a294-92c78eaebbf2
feature: 양식 데이터 모델
exl-id: 39408af6-439c-4ade-8062-155be9141dfa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 0%

---

# 양식 데이터 모델 {#use-form-data-model} 사용

![](do-not-localize/data-integeration.png)

AEM Forms 데이터 통합을 사용하면 서로 다른 백엔드 데이터 소스를 사용하여 다양한 적응형 양식 및 대화형 통신 워크플로우에서 스키마로 사용할 수 있는 양식 데이터 모델을 만들 수 있습니다. 데이터 소스를 구성하고 데이터 소스에서 사용할 수 있는 데이터 모델 개체 및 서비스를 기반으로 양식 데이터 모델을 만들어야 합니다. 자세한 내용은 다음을 참조하십시오.

* [AEM Forms 데이터 통합](/help/forms/using/data-integration.md)
* [데이터 소스 구성](/help/forms/using/configure-data-sources.md)
* [양식 데이터 모델 만들기](/help/forms/using/create-form-data-models.md)
* [양식 데이터 모델 작업](/help/forms/using/work-with-form-data-model.md)

양식 데이터 모델은 JSON 스키마의 확장으로, 다음 용도로 사용할 수 있습니다.

* [적응형 양식 및 조각 만들기](#create-af)
* [텍스트, 목록 및 조건 조각과 같은 인터랙티브 통신 및 빌딩 블록 만들기](#create-ic)
* [샘플 데이터를 사용한 대화형 커뮤니케이션 미리 보기](#preview-ic)
* [적응형 양식 및 대화형 커뮤니케이션 미리 채우기](#prefill)
* [제출된 적응형 양식 데이터를 다시 데이터 소스에 쓰기](#write-af)
* [적응형 양식 규칙을 사용하여 서비스 호출](#invoke-services)

## 적응형 양식 및 조각 만들기 {#create-af}

양식 데이터 모델을 기반으로 [적응형 양식](/help/forms/using/creating-adaptive-form.md) 및 [적응형 양식 조각](/help/forms/using/adaptive-form-fragments.md)을 만들 수 있습니다. 적응형 양식 또는 적응형 양식 조각을 만들 때 양식 데이터 모델을 사용하려면 다음을 수행하십시오.

1. 속성 추가 화면의 양식 모델 탭에서 **[!UICONTROL 양식 데이터 모델]**&#x200B;선택&#x200B;]**드롭다운 목록에서 을 선택합니다.**[!UICONTROL 

   ![create-af-1](assets/create-af-1.png)

1. 를 눌러 **[!UICONTROL 양식 데이터 모델 선택]**. 사용 가능한 모든 양식 데이터 모델이 나열됩니다.

   데이터 모델에서 을 선택합니다.

   ![create-af-2](assets/create-af-2.png)

1. (**적응형 양식 조각만**) 양식 데이터 모델에 있는 하나의 데이터 모델 개체만 기반으로 적응형 양식 조각을 만들 수 있습니다. **[!UICONTROL 양식 데이터 모델 정의]** 드롭다운을 확장합니다. 지정된 양식 데이터 모델의 모든 데이터 모델 개체가 나열됩니다. 목록에서 데이터 모델 개체를 선택합니다.

   ![create-af-3](assets/create-af-3.png)

양식 데이터 모델을 기반으로 하는 적응형 양식 또는 적응형 양식 조각이 만들어지면 양식 데이터 모델 개체가 적응형 양식 편집기에서 컨텐츠 브라우저의 **[!UICONTROL 데이터 모델 개체]** 탭에 표시됩니다.

>[!NOTE]
>
>적응형 양식 조각의 경우 작성 시 선택한 데이터 모델 객체와 관련 데이터 모델 객체만 데이터 모델 객체 탭에 표시됩니다.

![data-model-objects-tab](assets/data-model-objects-tab.png)

데이터 모델 개체를 적응형 양식 또는 조각으로 끌어서 놓아 양식 필드를 추가할 수 있습니다. 추가된 양식 필드는 메타데이터 속성을 유지하고 데이터 모델 개체 속성을 사용하여 바인딩합니다. 바인딩은 양식을 렌더링할 때 필드 값이 양식 제출 시 해당 데이터 소스에서 업데이트되고 미리 입력되도록 합니다.

## 대화형 통신 만들기 {#create-ic}

구성된 데이터 소스의 데이터로 대화형 커뮤니케이션을 미리 채우는 데 사용할 수 있는 양식 데이터 모델을 기반으로 대화형 커뮤니케이션을 만들 수 있습니다. 또한, 텍스트, 목록, 조건 문서 조각과 같은 대화형 커뮤니케이션의 기본 구성요소는 양식 데이터 모델을 기반으로 할 수 있다.

대화형 통신 또는 문서 조각을 만들 때 양식 데이터 모델을 선택할 수 있습니다. 다음 이미지는 [대화형 통신 만들기] 대화 상자의 [일반] 탭을 보여 줍니다.

![create-ic](assets/create-ic.png)

대화형 통신 만들기 대화 상자의 일반 탭

자세한 내용은 다음을 참조하십시오.

[대화형 통신 만들기](/help/forms/using/create-interactive-communication.md)

[대화형 커뮤니케이션의 텍스트](/help/forms/using/texts-interactive-communications.md)

[대화형 커뮤니케이션의 조건](/help/forms/using/conditions-interactive-communications.md)

[목록 조각](/help/forms/using/lists.md)

## 샘플 데이터 {#preview-ic}로 미리 보기

양식 데이터 모델 편집기를 사용하면 양식 데이터 모델에서 데이터 모델 개체에 대한 샘플 데이터를 생성하고 편집할 수 있습니다. 이 데이터를 사용하여 대화형 통신 및 적응형 양식을 미리 보고 테스트할 수 있습니다. [양식 데이터 모델로 작업](/help/forms/using/work-with-form-data-model.md#sample)에 설명된 대로 미리 보기 전에 샘플 데이터를 생성해야 합니다.

샘플 양식 데이터 모델 데이터를 사용하여 대화형 커뮤니케이션을 미리 보려면 다음을 수행하십시오.

1. AEM 작성자 인스턴스에서 **[!UICONTROL Forms > Forms 및 문서]**&#x200B;로 이동합니다.
1. 대화형 커뮤니케이션을 선택하고 도구 모음에서 **[!UICONTROL 미리 보기]**&#x200B;를 탭하여 **[!UICONTROL 웹 채널]**, **[!UICONTROL 인쇄 채널]** 또는 **[!UICONTROL 두 채널 모두]**&#x200B;을 선택하여 대화형 커뮤니케이션을 미리 봅니다.
1. 미리 보기 [*채널*] 대화 상자에서 **[!UICONTROL 양식 데이터 모델 테스트]**&#x200B;가 선택되어 있는지 확인하고 **[!UICONTROL 미리 보기]**&#x200B;를 탭합니다.

대화형 커뮤니케이션은 미리 채워진 샘플 데이터를 사용하여 열립니다.

![web-preview](assets/web-preview.png)

마찬가지로 샘플 데이터가 있는 적응형 양식을 미리 보려면 작성자 모드에서 적응형 양식을 열고 **[!UICONTROL 미리 보기]**&#x200B;를 누릅니다.

## 양식 데이터 모델 서비스를 사용하여 미리 채우기 {#prefill}

AEM Forms은 양식 데이터 모델을 기반으로 적응형 양식 및 대화형 커뮤니케이션에 사용할 수 있도록 해주는 기본 양식 데이터 모델 미리 채우기 서비스를 제공합니다. 미리 채우기 서비스는 적응형 양식 및 대화형 커뮤니케이션에서 데이터 모델 개체에 대한 데이터 소스를 쿼리하여 폼이나 통신을 렌더링하는 동안 데이터를 미리 채웁니다.

적응형 양식에 대해 양식 데이터 모델 미리 채우기 서비스를 활성화하려면 적응형 양식 컨테이너 속성을 열고 기본 아코디언 중 **[!UICONTROL 미리 채우기 서비스]** 드롭다운에서 **[!UICONTROL 양식 데이터 모델 미리 채우기 서비스]**&#x200B;를 선택합니다. 그런 다음 속성을 저장합니다.

![미리 채우기 서비스](assets/prefill-service.png)

대화형 커뮤니케이션에서 양식 데이터 모델 미리 채우기 서비스를 구성하려면 속성을 수정하는 동안 미리 채우기 서비스 드롭다운에서 양식 데이터 모델 미리 채우기 서비스를 선택할 수 있습니다.

![edit-ic-props](assets/edit-ic-props.png)

대화형 커뮤니케이션에 대한 속성 편집 대화 상자

## 제출된 적응형 양식 데이터를 데이터 소스에 쓰기 {#write-af}

사용자가 양식 데이터 모델을 기반으로 양식을 제출할 때 데이터 모델 개체에 대해 제출된 데이터를 해당 데이터 소스에 기록하도록 양식을 구성할 수 있습니다. 이 사용 사례를 달성하기 위해 AEM Forms은 [양식 데이터 모델 제출 작업](/help/forms/using/configuring-submit-actions.md)을 제공합니다. 이 작업은 양식 데이터 모델을 기반으로 하는 적응형 양식에 대해서만 기본적으로 사용할 수 있습니다. 데이터 소스에 데이터 모델 개체에 대해 제출된 데이터를 기록합니다.

양식 데이터 모델 제출 작업을 구성하려면 적응형 양식 컨테이너 속성을 열고 제출 아코디언 아래의 작업 제출 드롭다운에서 **[!UICONTROL 양식 데이터 모델을 사용하여 제출]**&#x200B;을 선택합니다. 그런 다음 제출하려는 데이터 모델 개체의 **[!UICONTROL 이름 드롭다운에서 데이터 모델 개체를 찾아 선택합니다.]** 속성을 저장합니다.

양식 제출 시 구성된 데이터 모델 개체의 데이터가 각 데이터 소스에 기록됩니다.

![데이터 제출](assets/data-submission.png)

이진 데이터 모델 개체 속성을 사용하여 데이터 소스에 양식 첨부 파일을 제출할 수도 있습니다. JDBC 데이터 소스에 첨부 파일을 제출하려면 다음을 수행합니다.

1. 양식 데이터 모델에 이진 속성을 포함하는 데이터 모델 개체를 추가합니다.
1. 적응형 양식의 구성 요소 브라우저에서 **[!UICONTROL 파일 첨부 파일]** 구성 요소를 적응형 양식으로 드래그합니다.
1. 추가된 구성 요소를 선택하려면 탭하고 ![settings_icon](assets/settings_icon.png) 을 탭하여 구성 요소에 대한 속성 브라우저를 엽니다.
1. 참조 바인딩 필드에서 ![foldersearch_18](assets/foldersearch_18.png)을(를) 탭하고 양식 데이터 모델에서 추가한 이진 속성을 선택합니다. 필요에 따라 다른 속성을 구성합니다.

   ![check-button](assets/check-button.png)을 눌러 속성을 저장합니다. 이제 첨부 파일 필드가 양식 데이터 모델의 이진 속성에 바인딩됩니다.

1. 적응형 양식 컨테이너 속성의 제출 섹션에서 **[!UICONTROL 양식 첨부 파일 제출]**&#x200B;을 활성화합니다. 양식 제출 시 이진 속성 필드의 첨부 파일을 데이터 소스로 제출합니다.

## 규칙 {#invoke-services}을 사용하여 적응형 양식에서 서비스 호출

양식 데이터 모델을 기반으로 하는 적응형 양식에서는 [규칙](/help/forms/using/rule-editor.md)을 만들어 양식 데이터 모델에 구성된 서비스를 호출할 수 있습니다. 규칙의 **[!UICONTROL 서비스 호출]** 작업은 양식 데이터 모델에서 사용 가능한 모든 서비스를 나열하며 서비스에 대한 입력 및 출력 필드를 선택할 수 있도록 해줍니다. 또한 **값 설정** 규칙 유형을 사용하여 양식 데이터 모델 서비스를 호출하고 필드의 값을 서비스가 반환한 출력으로 설정할 수도 있습니다.

예를 들어, 다음 규칙은 사원 ID를 입력으로 사용하는 get 서비스를 호출하고 반환된 값은 해당 종속 ID, 성, 이름 및 성별 필드에 형식으로 채워집니다.

![invoke-service](assets/invoke-service.png)

또한 `guidelib.dataIntegrationUtils.executeOperation` API를 사용하여 규칙 편집기의 코드 편집기에서 JavaScript를 작성할 수 있습니다. API 세부 정보에 대해서는 [API를 사용하여 양식 데이터 모델 서비스](/help/forms/using/invoke-form-data-model-services.md)를 호출하십시오.
