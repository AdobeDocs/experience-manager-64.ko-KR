---
title: 적응형 양식 만들기
seo-title: Creating an adaptive form
description: AEM Forms을 사용하여 적응형 양식을 만드는 방법. 적응형 양식은 정보 수집 및 처리를 간소화하는 반응형 HTML5 양식입니다.
seo-description: How to create an adaptive form using AEM Forms. Adaptive forms are responsive HTML5 forms that streamline information gathering and processing.
uuid: 444f461a-9e88-4385-b5ee-e985067ab7bc
content-type: reference
topic-tags: author
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f06b8cb2-6f98-465f-beec-1e91e3f45707
feature: Adaptive Forms
exl-id: 4b6d3533-cd1f-4944-b580-49fd90fcf87a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2053'
ht-degree: 0%

---

# 적응형 양식 만들기 {#creating-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## <strong>적응형 양식 만들기</strong> {#strong-create-an-adaptive-form-strong}

적응형 양식을 만들려면 다음 단계를 따르십시오.

1. 에서 AEM Forms 작성자 인스턴스에 액세스합니다 `https://[server]:[port]/<custom-context-if-any>.`

   ```
   
   ```

1. AEM 로그인 페이지에서 자격 증명을 입력합니다.

   로그인하고 왼쪽 상단 모서리에서 을(를) 탭합니다 **[!UICONTROL Adobe Experience Manager > Forms > Forms 및 문서]**.

   >[!NOTE]
   >
   >기본 설치의 경우 로그인은 다음과 같습니다 `admin` 그리고 암호는 `admin`.

1. 탭 **[!UICONTROL 만들기]** 을(를) 선택합니다. **[!UICONTROL 적응형 양식]**.
1. 템플릿을 선택하는 옵션이 나타납니다. 템플릿에 대한 자세한 내용은 [적응형 양식 템플릿](/help/forms/using/creating-adaptive-form.md#p-adaptive-form-templates-p). 템플릿을 탭하여 선택하고 다음 을 탭합니다.
1. &#39;속성 추가&#39; 옵션이 나타납니다. 다음 속성 필드에 값을 지정합니다. 제목 및 이름 필드는 필수입니다.

   * **[!UICONTROL 제목:]** 양식의 표시 이름을 지정합니다. 제목은 AEM Forms 사용자 인터페이스에서 양식을 식별하는 데 도움이 됩니다.
   * **[!UICONTROL 이름:]** 양식의 이름을 지정합니다. 지정된 이름의 노드가 저장소에 생성됩니다. 제목을 입력을 시작하면 이름 필드의 값이 자동으로 생성됩니다. 제안된 값을 변경할 수 있습니다. 이름 필드에는 영숫자, 하이픈 및 밑줄만 포함할 수 있습니다. 잘못된 입력은 모두 하이픈으로 대체됩니다.
   * **[!UICONTROL 설명:]** 양식에 대한 자세한 정보를 지정합니다.
   * **[!UICONTROL 태그:]** 적응형 양식을 고유하게 식별할 태그를 지정합니다. 태그는 양식을 검색하는 데 도움이 됩니다. 태그를 만들려면 **태그** 상자.

1. 다음 양식 모델 중 하나를 기반으로 적응형 양식을 만들 수 있습니다.

   * [양식 데이터 모델](#fdm)
   * [XFA 양식 템플릿](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p)
   * [XML 또는 JSON 스키마](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-xml-or-json-schema-p)
   * 없음 또는 양식 모델 없음

   다음 위치에서 이러한 매개 변수를 구성할 수 있습니다. **[!UICONTROL 양식 모델]** 탭에서 다음을 수행합니다. **[!UICONTROL 속성 추가]** 페이지. 기본적으로 선택한 양식 모델은 다음과 같습니다 **[!UICONTROL 없음]**.

1. 탭 **만들기**. 적응형 양식이 만들어지고 편집할 양식을 여는 대화 상자가 나타납니다.

   모든 등록 정보 지정을 완료한 후 **[!UICONTROL 만들기]**. 적응형 양식이 만들어지고 편집할 양식을 여는 대화 상자가 나타납니다.

   모든 등록 정보 지정을 완료한 후 **[!UICONTROL 만들기]**. 적응형 양식이 만들어지고 편집할 양식을 여는 대화 상자가 나타납니다.

1. 탭 **[!UICONTROL 열기]** 새 탭에서 새로 만든 양식을 열려면 다음을 수행하십시오. 편집하기 위해 양식이 열리고 템플릿에서 사용할 수 있는 컨텐츠가 표시됩니다. 또한 필요에 따라 새로 만든 양식을 사용자 지정하는 사이드바가 표시됩니다.

   적응형 양식 유형에 따라 관련 XFA 양식 템플릿, XML 스키마 또는 JSON 스키마에 있는 양식 요소가 **[!UICONTROL 데이터 모델 개체]** 의 탭 **[!UICONTROL 컨텐츠 브라우저]** 을 클릭합니다. 이러한 요소를 드래그하여 놓아 적응형 양식을 작성할 수도 있습니다.

   적응형 양식 작성 인터페이스 및 사용 가능한 구성 요소에 대한 자세한 내용은 [적응형 양식 작성 소개](/help/forms/using/introduction-forms-authoring.md).

   >[!NOTE]
   >
   >브라우저에서 팝업 창을 열어 새 탭에서 새로 만든 양식을 열 수 있도록 합니다.

## 양식 데이터 모델을 기반으로 적응형 양식 만들기 {#fdm}

[AEM Forms 데이터 통합](/help/forms/using/data-integration.md) 여러 데이터 소스를 통합하고 해당 엔티티와 서비스를 함께 가져와서 양식 데이터 모델을 만들 수 있습니다. JSON 스키마의 확장입니다. 양식 데이터 모델을 사용하여 적응형 양식을 만들 수 있습니다. 양식 데이터 모델에 구성된 엔티티 또는 데이터 모델 개체는 양식 작성을 위한 데이터 모델 개체로 사용할 수 있습니다. 각 데이터 소스에 바인딩되고 양식을 미리 채우고 제출된 데이터를 각 데이터 소스에 다시 쓰는 데 사용됩니다. 적응형 양식 규칙을 사용하여 양식 데이터 모델에 구성된 서비스를 호출할 수도 있습니다.

적응형 양식을 만들기 위해 양식 데이터 모델을 사용하려면 다음을 수행하십시오.

1. 속성 추가 화면의 양식 모델 탭에서 을 선택합니다 **[!UICONTROL 양식 데이터 모델]** 에서 **[!UICONTROL 선택 위치]** 드롭다운 목록.

   ![create-af-1-1](assets/create-af-1-1.png)

1. 탭하여 확장 **[!UICONTROL 양식 데이터 모델 선택]**. 사용 가능한 모든 양식 데이터 모델이 나열됩니다.

   데이터 모델에서 을 선택합니다.

   ![create-af-2-1](assets/create-af-2-1.png)

>[!NOTE]
>
>적응형 양식에 대한 양식 데이터 모델을 변경할 수도 있습니다. 자세한 단계는 [적응형 양식의 양식 모델 속성 편집](#edit-form-model).

## XFA 양식 템플릿을 기반으로 적응형 양식 만들기 {#create-an-adaptive-form-based-on-an-xfa-form-template}

XFA 양식 템플릿을 재사용하여 적응형 양식을 만들 수 있습니다. 용도를 변경하려면 XFA 양식 템플릿을 적응형 양식과 업로드하고 연결합니다. 양식 템플릿(XFA 양식)의 요소는 적응형 양식 작성 시 컨텐츠 파인더에서 사용할 수 있습니다. 컨텐츠 파인더에서 양식 템플릿 요소를 양식에 드래그하여 놓을 수 있습니다.

>[!NOTE]
>
>[XFA 양식 템플릿 업로드](/help/forms/using/get-xdp-pdf-documents-aem.md) AEM Forms에 액세스하려면 양식 템플릿을 기반으로 적응형 양식을 만들기 전에 하십시오.

적응형 양식의 양식 모델로 XFA 양식 템플릿을 사용하려면 다음을 수행하십시오.

1. 설정 **[!UICONTROL 속성 추가]** 페이지를 열고 **[!UICONTROL 양식 모델]** 탭.
1. 양식 모델 탭의 드롭다운 목록에서 **[!UICONTROL 양식 템플릿]**. AEM Forms UI를 통해 리포지토리에 업로드된 모든 양식 템플릿을 선택할 수 있습니다. 목록에서 템플릿을 선택합니다.

   ![XFA 양식 템플릿을 적응형 양식과 연결](assets/form_model_xfa_associate.png)
   **그림:** *양식 템플릿 선택*

   >[!NOTE]
   >
   >적응형 양식의 양식 템플릿을 변경할 수도 있습니다. 자세한 단계는 [적응형 양식의 양식 모델 속성 편집](#edit-form-model).

## XML 또는 JSON 스키마를 기반으로 적응형 양식 만들기 {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML 및 JSON 스키마는 조직의 백엔드 시스템에서 데이터를 생성하거나 사용하는 구조를 나타냅니다. 스키마를 적응형 양식에 연결하고 해당 요소를 사용하여 적응형 양식에 동적 컨텐츠를 추가할 수 있습니다. 스키마의 요소는 적응형 양식을 작성할 컨텐츠 브라우저의 데이터 모델 개체 탭에서 사용할 수 있습니다. 스키마 요소를 드래그하여 놓아 양식을 작성할 수 있습니다.

적응형 양식 작성을 위한 XML 또는 JSON 스키마를 디자인하는 방법을 이해하려면 다음 문서를 참조하십시오.

* [XML 스키마를 사용하여 적응형 양식 만들기](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [JSON 스키마를 사용하여 적응형 양식 만들기](/help/forms/using/adaptive-form-json-schema-form-model.md)

적응형 양식의 양식 모델로 XML 또는 JSON 스키마를 사용하려면 다음을 수행하십시오.

1. 설정 **[!UICONTROL 속성 추가]** 적응형 양식 작성 페이지에서 탭하기 **[!UICONTROL 양식 모델]** 탭.
1. 양식 모델 탭에서 을 선택합니다 **[!UICONTROL 스키마]** 에서 **[!UICONTROL 선택 위치]** 드롭다운 필드.

1. 탭 **[!UICONTROL 스키마 선택]** 다음 중 하나를 수행합니다.

   * **[!UICONTROL 디스크에서 업로드]** - 이 옵션을 선택하고 스키마 정의 업로드 를 탭하여 파일 시스템에서 XML 스키마 또는 JSON 스키마를 찾아 업로드합니다. 업로드된 스키마 파일은 양식에 포함되어 있으며 다른 적응형 양식에 액세스할 수 없습니다.
   * **[!UICONTROL 저장소에서 검색]** - 리포지토리에서 사용할 수 있는 스키마 정의 파일 목록에서 선택하려면 이 옵션을 선택합니다. XML 또는 JSON 스키마 파일을 양식 모델로 선택합니다. 선택한 스키마는 참조용으로 양식과 연결되며 다른 적응형 양식에서 사용할 수 있도록 액세스할 수 있습니다.

   >[!CAUTION]
   >
   >JSON 스키마 파일 이름이 다음으로 끝나야 합니다. **.schema.json**. 예: mySchema.schema.json

   ![XML 또는 JSON 스키마 선택](assets/upload-schema.png)
   **그림:** *XML 또는 JSON 스키마 선택*

1. (XML 스키마에만 해당) XML 스키마를 선택하거나 업로드한 후에는 선택한 XSD 파일의 루트 요소를 지정하여 적응형 양식에 매핑하십시오.

   ![XSD 루트 요소 선택](assets/xsd-root-element.png)
   **그림:** *XSD 루트 요소 선택*

>[!NOTE]
>
>적응형 양식의 스키마를 변경할 수도 있습니다. 자세한 단계는 [적응형 양식의 양식 모델 속성 편집](#edit-form-model).

## 적응형 양식 템플릿 {#adaptive-form-templates}

템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 여기에는 특정 속성 및 컨텐츠 구조를 포함하는 사전 형식의 구성 요소가 있습니다. 곧바로 사용할 수 있는 AEM Forms에서는 몇 가지 적응형 양식 템플릿을 제공합니다. 고급 템플릿을 포함한 전체 템플릿 패키지를 가져오려면 AEM Forms 추가 기능 패키지를 설치해야 합니다. 자세한 내용은 [AEM Forms 추가 기능 패키지 설치](/help/forms/using/installing-configuring-aem-forms-osgi.md).

또한 템플릿 편집기를 사용하여 나만의 템플릿을 생성할 수 있습니다. 템플릿 작업에 대한 자세한 내용은 [적응형 양식 템플릿](/help/forms/using/template-editor.md).

>[!NOTE]
>
>편집을 위해 고급 템플릿을 사용하여 만든 적응형 양식을 열면 오류 메시지가 나타납니다. 고급 템플릿에는 서명 단계 구성 요소가 있으며, 기본적으로 Acrobat Sign이 활성화되어 있습니다. 만들기 및 선택 [Acrobat Sign 클라우드 구성](/help/forms/using/adobe-sign-integration-adaptive-forms.md) 및 [서명자 구성](/help/forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) 오류를 해결하려면

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model}

적응형 양식은 양식 모델 없이(양식 모델의 경우 없음 옵션 사용) 또는 양식 템플릿, XML 스키마 또는 JSON 스키마 또는 양식 데이터 모델과 같은 양식 모델을 사용하여 만들어집니다. 적응형 양식에 대한 양식 모델을 없음에서 다른 양식 모델로 변경할 수 있습니다. 양식 모델을 기반으로 하는 적응형 양식의 경우 동일한 양식 모델에 대해 다른 양식 템플릿, XML 스키마, JSON 스키마 또는 양식 데이터 모델을 선택할 수 있습니다. 그러나 한 양식 모델에서 다른 양식 모델로 변경할 수는 없습니다.

1. 적응형 양식을 선택하고 **속성** 아이콘.
1. 를 엽니다. **[!UICONTROL 양식 모델]** 탭하고 다음 중 하나를 수행합니다.

   * 적응형 양식이 양식 모델이 없는 경우 다른 양식 모델을 선택하여 양식 템플릿, XML 또는 JSON 스키마 또는 양식 데이터 모델을 선택할 수 있습니다.
   * 적응형 양식이 양식 모델을 기반으로 하는 경우 다른 양식 템플릿, XML 또는 JSON 스키마 또는 동일한 양식 모델에 대한 양식 데이터 모델을 선택할 수 있습니다.

1. 탭 **[!UICONTROL 저장]** 속성을 저장합니다.

## 적응형 양식 자동 저장 {#auto-save-an-adaptive-form}

기본적으로 적응형 양식의 컨텐츠는 저장 단추를 누르는 것과 같은 사용자 작업에 저장됩니다. 이벤트나 시간 간격을 기준으로 콘텐츠 저장을 자동으로 시작하도록 적응형 양식을 구성할 수도 있습니다. 자동 저장 옵션은 다음과 같은 경우에 유용합니다.

* 익명 및 로그인한 사용자를 위해 콘텐츠를 자동으로 저장
* 사용자 개입 없이 또는 최소한의 양식 컨텐츠 저장
* 사용자 이벤트를 기반으로 양식 콘텐츠 저장 시작
* 지정된 시간 간격 후에 양식 내용을 반복적으로 저장

### 적응형 양식에 대해 자동 저장 활성화 {#enable-auto-save-for-an-adaptive-form}

기본적으로 자동 저장 옵션은 활성화되지 않습니다. 적응형 양식의 자동 저장 탭에서 자동 저장 옵션을 활성화할 수 있습니다. 자동 저장 탭에서도 여러 가지 다른 구성 옵션이 제공됩니다. 적응형 양식에 대해 자동 저장 옵션을 활성화하고 구성하려면 다음 단계를 수행하십시오.

1. 속성에서 자동 저장 섹션에 액세스하려면 구성 요소를 선택한 다음 ![필드 수준](assets/field-level.png) > **[!UICONTROL 적응형 양식 컨테이너]**&#x200B;를 누른 다음 탭합니다. ![cmppr](assets/cmppr.png).
1. 에서 **[!UICONTROL 자동 저장]** 섹션, **[!UICONTROL 활성화]** 자동 저장 선택 사항.
1. 에서 **[!UICONTROL 적응형 양식 이벤트]** 상자에 1이나 TRUE를 지정하여 브라우저에서 양식을 로드할 때 자동으로 양식 저장을 시작합니다. 이벤트에 대한 조건부 표현식을 지정할 수도 있습니다. 이 식은 트리거되고 true를 반환하는 경우 양식의 컨텐츠 저장을 시작합니다.
1. 트리거 를 지정합니다. 자동 저장은 구성에 따라 트리거됩니다. 옵션은 다음과 같습니다.

   * **[!UICONTROL 시간 기반:]** 특정 시간 간격에 따라 컨텐츠 저장을 시작하려면 옵션을 선택합니다.
   * **[!UICONTROL 이벤트 기반:]** 이벤트가 트리거될 때 기반으로 컨텐츠 저장을 시작하려면 옵션을 선택합니다.

   트리거를 선택하면 전략 구성 상자가 활성화됩니다. 전략 구성 상자를 사용하여 다음을 수행할 수 있습니다.

   * 선택하는 경우 시간 간격을 지정합니다 **[!UICONTROL 시간 기반]** 트리거합니다.
   * 선택하는 경우 이벤트 이름을 지정합니다 **[!UICONTROL 이벤트 기반]** 트리거합니다.

   자신만의 사용자 지정 전략을 만들어 목록에 추가할 수도 있습니다. 자세한 내용은 [사용자 지정 전략을 구현하여 양식을 자동으로 저장](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (시간 기반 자동 저장만 해당) 다음 단계를 수행하여 시간 기반 자동 저장에 대한 옵션을 구성합니다.

   1. 에서 **[!UICONTROL 이 간격 자동 저장]** 상자에서 시간 간격을 초 단위로 지정합니다. 간격 상자에 지정된 초 수가 경과하면 양식이 반복적으로 저장됩니다.

1. (이벤트 기반 자동 저장만) 다음 단계를 수행하여 이벤트 기반 자동 저장 옵션을 구성합니다.

   1. 에서 **이 이벤트 후 자동 저장** 상자에서 다음을 지정합니다 [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html) 이벤트. 표현식이 TRUE로 평가될 때마다 양식이 저장됩니다.

1. (선택 사항) 익명 사용자를 위해 콘텐츠를 자동으로 저장하려면 **익명 사용자에 대해 자동 저장 사용** 옵션을 선택하고 **[!UICONTROL 확인]**.

   >[!NOTE]
   >
   >익명 사용자에 대해 자동 저장 옵션이 작동하려면 모든 사용자가 양식을 미리 보고, 확인하고, 서명할 수 있도록 Forms 일반 구성 서비스 를 구성해야 합니다.
   >
   >서비스를 구성하려면 다음 위치에서 AEM Web Console 구성으로 이동합니다. `https://[server]:[host]/system/console/configMgr` 및 편집 **[!UICONTROL Forms 일반 구성 서비스]** 을 선택합니다. **[!UICONTROL 모든 사용자]** 옵션 **[!UICONTROL 허용]** 필드를 작성하고 구성을 저장합니다.
