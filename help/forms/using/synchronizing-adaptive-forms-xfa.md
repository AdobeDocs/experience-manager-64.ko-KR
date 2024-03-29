---
title: 적응형 Forms과 XFA 양식 템플릿 동기화
seo-title: Synchronizing Adaptive Forms with XFA Form Templates
description: 적응형 양식을 XFA/XDP 파일과 동기화.
seo-description: Synchronizing Adaptive forms with XFA/XDP files.
uuid: 6613a9bf-c862-4c18-a5b5-f574d301e936
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 29c0a78c-53b5-4ce7-a2f3-63e1b089b0d0
feature: Adaptive Forms
exl-id: 014c735e-84f8-4cdb-979e-bfab24b3f666
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1191'
ht-degree: 1%

---

# 적응형 Forms과 XFA 양식 템플릿 동기화 {#synchronizing-adaptive-forms-with-xfa-form-templates}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

XFA 양식 템플릿을 기반으로 적응형 양식을 만들 수 있습니다( `*.XDP` 파일)에 액세스할 수 없습니다. 이러한 재사용을 통해 기존 XFA 양식에 대한 투자를 유지할 수 있습니다. 적응형 양식 작성에 XFA 양식 템플릿을 사용하는 방법에 대한 자세한 내용은 [템플릿을 기반으로 적응형 양식 만들기](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p).

적응형 양식의 XDP 파일의 필드를 다시 사용할 수 있습니다. 이러한 필드를 바인드 필드라고 합니다. 바인딩된 필드(예: 스크립트, 레이블 및 표시 형식)의 속성이 XDP 파일에서 복사됩니다. 이러한 속성 중 일부의 값을 재정의하도록 선택할 수도 있습니다.

AEM Forms에서는 적응형 양식의 필드를 나중에 XDP 파일의 해당 필드에 수행한 변경 사항과 동기화하는 데 도움이 되는 방법을 제공합니다. 이 문서에서는 이 동기화를 활성화하는 방법을 설명합니다.

![XFA 양식에서 적응형 양식으로 필드를 드래그할 수 있습니다](assets/drag-drop-xfa.gif.gif)

AEM Forms 작성 환경에서 필드를 XFA 양식(왼쪽)에서 적응형 양식(오른쪽)으로 드래그할 수 있습니다

## 사전 요구 사항 {#prerequisites}

이 문서의 정보를 사용하려면 다음 영역에 대해 잘 알고 있어야 합니다.

* [적응형 양식 만들기](/help/forms/using/creating-adaptive-form.md)

* XFA(XML Forms 아키텍처)

문서에서 예제에 대해 제공하는 자산을 사용하려면 다음 섹션에 설명된 대로 샘플 패키지를 다운로드합니다. [샘플 패키지](/help/forms/using/synchronizing-adaptive-forms-xfa.md#p-sample-package-p).

## 샘플 패키지 {#sample-package}

이 문서에서는 예제를 사용하여 적응형 양식을 업데이트된 XFA 양식 템플릿과 동기화하는 방법을 보여줍니다. 이 예제에서 사용되는 자산은 패키지에서 다운로드할 수 있습니다. [다운로드](/help/forms/using/synchronizing-adaptive-forms-xfa.md#p-downloads-p) 섹션에 자세히 설명되어 있습니다.

패키지를 업로드한 후 AEM Forms UI에서 이러한 자산을 볼 수 있습니다.

패키지 관리자를 사용하여 패키지를 설치합니다. `https://<server>:<port>/crx/packmgr/index.jsp`

패키지에는 다음 자산이 들어 있습니다.

1. `sample-form.xdp`: 예로서 사용되는 XFA 양식 템플릿입니다

1. `sample-xfa-af`: sample-form.xdp 파일을 기반으로 하는 적응형 양식입니다. 그러나 이 적응형 양식에는 필드가 포함되지 않습니다. 다음 단계에서는 이 적응형 양식에 콘텐츠를 추가합니다.

### 적응형 양식에 콘텐츠 추가 {#add-content-to-adaptive-form-br}

1. https://으로 이동합니다.&lt;server>:&lt;port>/aem/forms.html 묻는 경우 자격 증명을 입력합니다.
1. 작성자 모드에서 편집할 샘플-af-xfa를 엽니다.
1. 사이드바의 컨텐츠 브라우저에서 데이터 모델 객체 탭을 선택합니다. NumericField1 및 TextField1을 적응형 양식으로 드래그합니다.
1. NumericField1의 제목을 **숫자 필드** to **AF 숫자 필드.**

>[!NOTE]
>
>앞의 단계에서 XDP 파일에 있는 필드의 속성을 덮어씁니다. 따라서 XDP 파일의 해당 속성을 나중에 수정하는 경우 이 속성은 동기화되지 않습니다.

## XDP 파일에서 변경 내용 감지 {#detecting-changes-in-xdp-file}

XDP 파일 또는 조각이 변경될 때마다 AEM Forms UI는 XDP 파일 또는 조각을 기반으로 하는 모든 적응형 양식에 플래그를 지정합니다.

XDP 파일을 업데이트한 후 변경 사항에 플래그를 지정하려면 AEM Forms UI에서 다시 업로드해야 합니다.

예를 들어 `sample-form.xdp` 다음 단계를 사용하여 파일을 작성합니다.

1. 다음으로 이동 `https://<server>:<port>/projects.html.` 메시지가 표시되면 자격 증명을 입력합니다.
1. 왼쪽의 Forms 탭을 클릭합니다.
1. 다운로드 `sample-form.xdp` 파일을 로컬 컴퓨터에 저장합니다. XDP 파일은 `.zip` 파일 압축 해제 유틸리티를 사용하여 추출할 수 있는 파일입니다.

1. 를 엽니다. `sample-form.xdp` 파일에서 TextField1 필드의 제목을 **텍스트 필드** to **내 텍스트 필드**.

1. 업로드 `sample-form.xdp` 파일을 다시 AEM Forms UI에 넣습니다.

XDP 파일이 업데이트되면 XDP 파일을 기반으로 적응형 양식을 편집할 때 편집기에 아이콘이 표시됩니다. 이 아이콘은 적응형 양식이 XDP 파일과 동기화되지 않았음을 나타냅니다. 다음 이미지에서 사이드바의 옆에 있는 아이콘을 참조하십시오.

![아이콘: 적응형 양식이 XDP 파일과 동기화되지 않았음을 표시합니다](assets/sync-af-xfa.png)

## 적응형 양식을 최신 XDP 파일과 동기화 {#synchronizing-adaptive-forms-with-the-latest-xdp-file}

다음에 작성을 위해 XDP 파일과 동기화되지 않은 적응형 양식을 열면 다음 메시지가 표시됩니다.
**적응형 양식에 대한 스키마/양식 템플릿이 업데이트되었습니다. `Click Here` 를 새로운 버전으로 재구성합니다.**

메시지를 클릭하면 적응형 양식의 필드가 XDP 파일의 해당 필드와 동기화됩니다.

이 문서에 사용된 예제를 보려면 `sample-xfa-af` 작성 모드. 메시지가 적응형 양식의 맨 아래에 표시됩니다.

![적응형 양식을 XDP 파일과 동기화하라는 메시지가 표시됩니다](assets/sync-af-xfa-1.png)

### 속성 업데이트 {#updating-the-properties}

XDP 파일에서 적응형 양식으로 복사된 모든 속성은 작성자가 적응형 양식(구성 요소 대화 상자에서)에서 명시적으로 재정의된 속성을 제외하고 업데이트됩니다. 업데이트된 속성 목록은 서버 로그에서 사용할 수 있습니다.

예제 적응형 양식의 속성을 업데이트하려면 링크(레이블이 지정됨)를 클릭하십시오 `"Click Here"`)을 클릭하여 제품에서 사용할 수 있습니다. TextField1의 제목이 **텍스트 필드** to **내 텍스트 필드**.

![update-property](assets/update-property.png)

>[!NOTE]
>
>에 설명된 대로 구성 요소 속성 대화 상자에서 이 속성을 재정의했기 때문에 AF 숫자 필드 레이블이 변경되지 않았습니다. [적응형 양식에 콘텐츠 추가](#p-add-content-to-adaptive-form-br-p).

### XDP 파일의 새 필드를 적응형 양식에 추가   {#adding-new-fields-from-xdp-file-to-adaptive-form-nbsp}

나중에 원래 XDP 파일에 추가된 모든 필드는 양식 계층 탭에 나타나며 이러한 새 필드를 적응형 양식으로 드래그할 수 있습니다.

양식 계층 탭의 필드를 업데이트하려면 오류 메시지의 링크를 클릭할 필요가 없습니다.

### XDP 파일에서 필드가 삭제됨 {#deleted-fields-in-xdp-file}

적응형 양식에 이전에 복사한 필드를 XDP 파일에서 삭제하면 해당 필드가 XDP 파일에 없다는 오류 메시지가 작성 모드에 표시됩니다. 이러한 경우 적응형 양식에서 필드를 수동으로 삭제하거나 `bindRef` 속성 을 클릭합니다.

다음 단계는 이 문서에 사용된 예에서 자산에 대한 이 사용 흐름을 보여줍니다.

1. 업데이트 `sample-form.xdp` 파일에서 NumericField1을 삭제합니다.
1. 업로드 `sample-form.xdp` AEM Forms UI의 파일
1. 를 엽니다. `sample-xfa-af` 작성을 위한 적응형 양식입니다. 다음 오류 메시지가 표시됩니다. 적응형 양식에 대한 스키마/양식 템플릿이 업데이트되었습니다. `Click Here` 를 새로운 버전으로 재구성합니다.

1. 링크를 클릭합니다(레이블이 &quot; `Click Here`&quot;)을 입력하여 메시지를 표시할 수 있습니다. XDP 파일에 더 이상 필드가 없다는 오류 메시지가 표시됩니다.

![XDP 파일에서 요소를 삭제할 때 표시되는 오류](assets/no-element-xdp.png)

삭제된 필드는 필드에 오류를 나타내는 아이콘도 표시됩니다.

![필드의 오류 아이콘](assets/error-field.png)

>[!NOTE]
>
>적응형 양식의 필드에 잘못된 바인딩이 있습니다(잘못된 필드) `bindRef` 편집 대화 상자의 값)도 삭제된 필드로 간주됩니다. 작성자가 이러한 오류를 수정하고 적응형 양식을 게시하지 않는 경우 필드는 일반적인 바인딩되지 않은 적응형 양식 필드로 처리되며 출력 XML 파일의 바인딩되지 않은 섹션에 포함됩니다.

## 다운로드 {#downloads}

이 문서의 예제에 대한 컨텐츠 패키지

[파일 가져오기](assets/sample-xfa-af-sync-1.0.zip)
