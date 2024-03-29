---
title: 대화형 커뮤니케이션의 조건
seo-title: Conditions in Interactive Communications
description: Interactive Communications에서 사용할 조건 조각을 만들고 편집 - 조건은 Interactive Communications를 작성하는 데 사용되는 4가지 문서 조각 유형 중 하나입니다. 다른 세 가지는 텍스트, 목록 및 레이아웃 조각입니다.
seo-description: Creating and editing conditions to be used in Interactive Communications
uuid: 93d69398-aead-4e23-8db3-b3e890477113
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3ade2a54-cb9a-4e34-808c-c6feec23cfe1
feature: Interactive Communication
exl-id: 0ffb297f-8c5a-4909-b4c0-2d8253548640
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1528'
ht-degree: 1%

---

# 대화형 커뮤니케이션의 조건 {#conditions-in-interactive-communications}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Interactive Communications에서 사용할 조건 조각을 만들고 편집 - 조건은 Interactive Communications를 작성하는 데 사용되는 4가지 문서 조각 유형 중 하나입니다. 다른 세 가지는 텍스트, 목록 및 레이아웃 조각입니다.

## 개요 {#overview}

조건은 Interactive Communication에 포함할 수 있는 문서 조각입니다. 다른 문서 조각은 [텍스트](/help/forms/using/texts-interactive-communications.md), 목록 및 레이아웃 조각 . 조건을 사용하면 제공된 데이터 및 규칙을 기반으로 대화형 커뮤니케이션에 포함된 하나 이상의 컨텍스트 자산을 정의할 수 있습니다.

예:

* 신용카드 명세서에는 고객의 신용카드 유형에 따라 신용카드 연간 수수료 및 신용 카드 이미지를 표시합니다.
* 보험료 독촉장에는 고객의 세금에따라 세금 계산을 표시하십시오.

적용된 규칙 및 규칙에 전달된 값을 기반으로 렌더링되는 조건의 자산. 조건의 규칙은 다음 유형의 데이터에서 값을 확인할 수 있습니다.

* 연결된 양식 데이터 모델의 속성
* 조건에서 만드는 모든 변수
* 문자열
* 숫자
* 수학 표현식
* 날짜

## 조건 만들기 {#createcondition}

1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL 문서 조각]**.
1. 선택 **[!UICONTROL 만들기]** > **[!UICONTROL 조건]**.
1. 다음 정보를 지정합니다.

   * **[!UICONTROL 제목]**: (선택 사항) 조건의 제목을 입력합니다. 제목은 고유해야 하며 특수 문자와 비영어 문자가 있을 수 있습니다. 조건은 축소판 그림 및 속성과 같이 해당 제목(사용 가능한 경우)으로 참조됩니다.
   * **[!UICONTROL 이름]**: 폴더 내에서 조건에 대한 고유한 이름입니다. 어떤 상태에서든 동일한 이름의 두 문서 조각(텍스트, 조건 또는 목록)은 폴더 내에 존재할 수 없습니다. 이름 필드에 영어 문자, 숫자 및 하이픈만 입력할 수 있습니다. 이름 필드는 제목 필드를 기반으로 자동으로 채워집니다. 제목 필드에 입력한 특수 문자, 공백, 숫자 및 비영어 문자는 이름 필드에서 하이픈으로 바뀝니다. 제목 필드의 값이 자동으로 이름에 복사되지만 값을 편집할 수 있습니다.
   * **[!UICONTROL 설명]**: 문서 조각에 대한 설명을 입력합니다.
   * **[!UICONTROL 양식 데이터 모델]**: 양식 데이터 모델 라디오 단추를 선택하여 양식 데이터 모델을 기반으로 조건을 생성합니다(선택적). 양식 데이터 모델 라디오 단추를 선택하면 **[!UICONTROL 양식 데이터 모델*]** 필드가 나타납니다. 양식 데이터 모델을 찾아 선택합니다. 대화형 커뮤니케이션에 대한 조건을 만드는 동안 대화형 커뮤니케이션에서 사용할 데이터 모델과 동일한 모델을 사용해야 합니다. 양식 데이터 모델에 대한 자세한 내용은 [데이터 통합](/help/forms/using/data-integration.md).
   * **[!UICONTROL 태그]**: 사용자 지정 태그를 만들려면 텍스트 필드에 값을 입력하고 Enter 키를 누릅니다(선택적). 이 조건을 저장하면 새로 추가된 태그가 생성됩니다.

1. 탭 **[!UICONTROL 다음]**.

   조건 만들기 페이지가 나타납니다.

   ![만들기](assets/createcondition.png)

1. 탭 **[!UICONTROL 자산 추가]**.

   자산 선택 페이지가 나타나고 조건에 추가할 수 있는 사용 가능한 텍스트, 목록, 조건 및 이미지가 표시됩니다.

   >[!NOTE]
   >
   >[자산 선택] 페이지에는 없음 기반 새로 생성된 자산 및 FDM 기반 자산(생성 중인 조건과 동일한 FDM을 사용하여 생성)만 표시됩니다.

1. 해당 자산을 탭하여 조건에 포함할 자산을 선택한 다음, **[!UICONTROL 완료]**.

   조건 만들기 페이지가 나타나고 추가된 자산을 나열합니다.

   ![createonditionassetadd](assets/createconditionassetsadd.png)

   다음 옵션을 사용하여 조건에 있는 자산을 관리할 수 있습니다.

   ![createonditionscreenassetdeddendannoted](assets/createconditionscreenassetsaddedannotated.png)

   **`[A]`변경 거부.** 이 아이콘을 탭하여 자산의 변경 사항과 조건의 규칙에 대한 변경 사항을 거부합니다.

   **`[B]`변경 수락.** 이 아이콘을 탭하여 조건의 자산 및 규칙에서 수행한 변경 사항을 수락합니다.

   **`[C]`자산이 중복됩니다.** 이 아이콘을 탭하여 조건에 적용된 규칙과 함께 자산의 사본을 만듭니다(있는 경우). 그런 다음 복제된 자산에 대한 규칙 및 자산 편집을 계속할 수 있습니다. 자산을 복제하는 것은 특정 컨텍스트에 따라 대체 자산을 표시하는 유사한 규칙을 만드는 데 유용합니다.

   **`[D]`미리 보기 표시.** 이 아이콘을 탭하여 Create\Edit Condition 페이지 내에 자산의 미리 보기를 표시합니다.

   **`[E]`순서 재지정.** 이 아이콘을 길게 탭하여 자산을 드래그하여 조건 내에서 재정렬할 수 있습니다.

   다음 옵션을 선택하여 조건이 런타임 시 동작하는 방식을 지정할 수 있습니다.

   * **여러 결과 평가를 사용하지 않음\여러 결과 평가 사용**: 이 옵션이 활성화되면(&quot;복수 결과 평가 사용&quot;으로 표시됨) 모든 규칙이 평가되고, 결과는 모든 true 규칙의 합계입니다. 이 옵션이 비활성화되어 있으면(&quot;복수 결과 평가 비활성화&quot;로 표시됨) true로 확인된 첫 번째 규칙만 평가되고, 조건의 출처가 됩니다.
   * **페이지 나누기**: 이 옵션( ![break](assets/break.png))를 클릭하여 조건의 자산 사이에 페이지 나누기를 추가합니다. 이 옵션을 선택하지 않은 경우( ![해제](assets/nobreak.png)). 조건이 인쇄 출력의 다음 페이지로 넘치면 조건이 조건에 있는 자산 간에 페이지를 분할하지 않고 전체 조건이 다음 페이지로 이동합니다.

1. 탭 **[!UICONTROL 규칙 만들기]** 필요에 따라 규칙을 추가하여 자산을 표시하거나 숨깁니다. 규칙에서 변수를 사용하려면 다음을 참조하십시오. [변수 만들기](#variables). 자세한 내용은 [조건에 규칙 추가](#ruleeditor).

   생성된 규칙은 조건 만들기 화면의 RULE 열에 나타납니다.

   ![createonditionscreenrulesaded](assets/createconditionscreenrulesadded.png)

   >[!NOTE]
   >
   >이미 규칙이나 반복이 적용된 조건에 자산을 삽입할 수 있습니다.

1. 탭 **[!UICONTROL 저장]**.

   조건이 만들어집니다. 이제 대화형 커뮤니케이션을 만드는 동안 조건을 빌딩 블록으로 계속 사용할 수 있습니다.

   >[!NOTE]
   >
   >새 조건 또는 편집된 조건을 저장하려면 조건에 추가된 각 자산에 대해 하나 이상의 규칙이 있어야 합니다.

## 조건 편집 {#edit-a-condition}

다음 단계를 사용하여 조건을 편집할 수 있습니다. 팝업 메뉴에서 조각 편집 을 선택하여 Interactive Communication 내에서 조건을 편집할 수도 있습니다.

1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL 문서 조각]**.
1. 조건으로 이동하고 선택합니다.
1. 탭 **[!UICONTROL 편집]**.
1. 조건에서 필요한 변경을 수행합니다. 조건에서 변경할 수 있는 정보에 대한 자세한 내용은 [조건 만들기](#createcondition).
1. 탭 **[!UICONTROL 저장]** 그런 다음 **[!UICONTROL 닫기]**.

## 조건으로 규칙 만들기 {#ruleeditor}

조건에 규칙 편집기를 사용하여 을 기반으로 자산을 표시하거나 숨길 규칙을 만들 수 있습니다 **사전 설정 조건**. 이러한 조건은 다음을 기준으로 작성할 수 있습니다.

* 문자열
* 숫자
* 수학 표현식
* 날짜
* 연결된 양식 데이터 모델의 속성
* 임의 [변수](#variables) 당신이

### 조건으로 규칙 만들기 {#create-rule-in-condition}

1. 조건을 만들거나 편집하는 동안 ![ruleeditoricon](assets/ruleeditoricon.png) (규칙 편집기) 아이콘을 클릭합니다.

   규칙 만들기 대화 상자가 나타납니다. 문자열, 숫자, 수학 표현식 및 날짜 외에도 규칙 편집기에서 규칙의 문을 만들 수도 있습니다.

   * 연결된 양식 데이터 모델의 속성
   * 임의 [변수](#variables) 생성했을 수 있습니다.

   ![createluledialog](assets/createruledialog.png)

   평가할 적절한 옵션을 선택합니다.

   >[!NOTE]
   >
   >자산을 표시하는 규칙을 만드는 데 컬렉션 속성이 지원되지 않습니다.

1. 다음과 같음, 포함 및 다음으로 시작 등의 규칙을 평가할 적절한 연산자를 선택합니다.
1. 평가 표현식, 문자열, 데이터 모델 속성, 변수 또는 날짜를 삽입합니다.

   ![정책 유형이 표준일 때 자산을 표시하는 규칙](assets/ruleincondition.png)

   정책 유형이 표준일 때 자산을 표시하는 규칙

   * 규칙을 만들거나 편집하는 동안, ![icon_resize](assets/icon_resize.png) (크기 조정) 을 클릭하여 규칙 만들기/규칙 편집 대화 상자를 확장합니다. 확장된 전체 창 대화 상자에서는 [변수](#variables) 규칙을 만들려면 다음을 수행하십시오. 다시 크기 조정 을 탭하여 일반 규칙 만들기 대화 상자로 돌아갑니다.
   * 규칙에 여러 조건을 만들 수도 있습니다.

1. 탭 **[!UICONTROL 완료]**.

   규칙이 자산에 적용됩니다.

## 조건에서 변수 만들기 및 사용 {#variables}

조건에서 규칙을 만들거나 편집하는 동안 ![icon_resize](assets/icon_resize.png) (크기 조정) 규칙 만들기\규칙 편집 대화 상자를 확장합니다. 확장된 전체 창 대화 상자에서는 다음 작업을 수행할 수 있습니다.

* 규칙에서 변수 만들기 및 사용
* 양식 데이터 모델의 속성과 변수를 규칙에 드래그하여 놓습니다

[규칙 만들기\규칙 편집] 대화 상자로 돌아가려면 [크기 조정]을 다시 누릅니다.

### 변수 만들기 {#create-variables}

1. 조건에서 규칙을 만들거나 편집하는 동안 ![icon_resize](assets/icon_resize.png) (크기 조정) 을 클릭하여 규칙 만들기/규칙 편집 대화 상자를 확장합니다.

   확장된 전체 창 대화 상자가 나타납니다.

   ![extendedditruledialog](assets/expandededitruledialog.png)

1. 왼쪽 창에서 **[!UICONTROL 변수]**.

   변수 창이 나타납니다.

   ![expandeditruleavables](assets/expandededitrulevariables.png)

1. 탭 **[!UICONTROL 만들기]**.

   변수 만들기 창이 나타납니다.

1. 다음 정보를 입력하고 탭합니다. **[!UICONTROL 만들기]**:

   * **[!UICONTROL 이름*]**: 변수의 이름입니다.
   * **[!UICONTROL 설명]**: 변수에 대한 설명을 입력합니다(선택적).
   * **[!UICONTROL 유형*]**: 변수 유형을 선택합니다. 문자열, 숫자, 부울 또는 날짜입니다.
   * **[!UICONTROL 특정 값만 허용]**: 문자열 및 숫자 변수의 경우 에이전트가 에이전트 UI의 자리 표시자에 대한 특정 값 세트에서 선택하도록 할 수 있습니다. 값 집합을 지정하려면 이 옵션을 선택한 다음, **[!UICONTROL 값*]** 필드.

1. 탭 **[!UICONTROL 만들기]**.

   변수가 만들어지고 변수 창에 나열됩니다.

1. 규칙에 변수를 삽입하려면 변수를 규칙의 옵션 자리 표시자에 드래그하여 놓습니다.
1. 유효한 규칙을 구성한 후 를 누릅니다 **[!UICONTROL 완료]**.

   필요한 경우 조건으로 추가 변경 작업을 수행하고 저장합니다.
