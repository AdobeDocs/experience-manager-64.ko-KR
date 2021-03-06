---
title: '적응형 양식 스타일 지정 '
seo-title: '적응형 양식 스타일 지정 '
description: '사용자 정의 테마를 만들고, 개별 구성 요소를 스타일을 지정하고, 테마에 웹 글꼴을 사용하는 방법을 알아봅니다 '
seo-description: '사용자 정의 테마를 만들고, 개별 구성 요소를 스타일을 지정하고, 테마에 웹 글꼴을 사용하는 방법을 알아봅니다 '
page-status-flag: de-activated
uuid: ffb2cc22-baaf-4525-a2e3-29f39271c670
topic-tags: introduction
discoiquuid: 655303a4-99bb-4ba3-9d50-a178f5edcf85
feature: 적응형 양식
exl-id: 0ccf43eb-f0c6-4204-8325-f891caa8f5af
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2071'
ht-degree: 8%

---

# 적응형 양식 {#do-not-publish-style-your-adaptive-form} 스타일 지정

사용자 정의 테마를 만들고, 개별 구성 요소를 스타일을 지정하고, 테마에 웹 글꼴을 사용하는 방법을 알아봅니다

![](do-not-localize/08-style_your_adaptiveformmain.png)

이 자습서는 [첫 번째 적응형 양식 만들기](create-your-first-adaptive-form.md) 시리즈의 단계입니다. 전체 자습서 사용 사례를 이해하고, 수행하고, 시연하기 위해 시리즈를 시간 순서대로 따르는 것이 좋습니다.

## 자습서 {#about-the-tutorial} 정보

테마를 사용하여 적응형 양식에 고유한 모양 및 스타일을 제공할 수 있습니다. 적응형 양식 편집기와 함께 제공되는 기본 테마를 적용하거나 고유한 사용자 지정 테마를 만들 수 있습니다. AEM Forms은 사용자 지정 테마를 만들기 위해 [테마 편집기](themes.md)를 제공합니다. 단일 테마는 모바일, 태블릿 또는 데스크톱에서 연 동일한 적응형 양식에 다른 모양을 제공할 수 있습니다. CSS 또는 LESS에 대한 이전 지식은 테마 편집기를 사용할 필요가 없지만 원하는 것입니다.

자습서를 마치면 다음을 배울 수 있습니다.

* 즉시 사용 가능한 테마를 적응형 양식에 적용
* 테마 편집기를 사용하여 적응형 양식의 테마 만들기
* 개별 구성 요소 스타일 지정
* 보너스 섹션:사용자 정의 테마에 웹 글꼴 사용

이 양식은 자습서를 완료한 후 다음과 비슷합니다.

![사용자 지정 테마가 있는 양식](assets/styled-adaptive-form.png)

## {#before-you-start} 시작 전에

로컬 시스템에서 헤더 스타일 및 로고 이미지를 다운로드합니다. `shipping-address-add-update-form` 적응형 양식의 헤더는 머리글 스타일 및 로고 이미지를 사용합니다. 헤더 스타일 이미지가 헤더의 오른쪽에 나타납니다.

[파일 가져오기](assets/header-style.png)

[파일 가져오기](assets/logo-1.png)

## 1단계:적응형 양식 {#step-apply-a-theme-to-your-adaptive-form}에 테마 적용

적응형 양식 편집기는 다양한 기본 테마를 제공합니다. 적응형 양식에 사용자 지정 스타일을 사용하지 않을 경우에는 즉시 사용 가능한 테마로 적응형 양식을 게시할 수도 있습니다. 테마는 적응형 양식과 독립적입니다. 여러 적응형 양식에 동일한 테마를 적용할 수 있습니다. 적응형 양식에 테마를 적용하려면:

1. 편집할 적응형 양식을 엽니다.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. **적응형 양식 컨테이너**&#x200B;의 속성을 엽니다. 속성 브라우저에서 **기본** > **적응형 양식 테마**&#x200B;로 이동합니다. **적응형 양식 테마** 필드에는 모든 기본 제공 및 사용자 지정 테마가 나열됩니다. 기본적으로 캔버스 테마가 적용됩니다.
1. **적응형 양식 테마** 필드에서 테마를 선택합니다. 예: **설문 조사 테마** ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 탭하여 선택한 테마를 적용합니다.

![기본 테마가 있는 적응형 양식](assets/default-adaptive-form.png)

**그림:** *기본 테마가 있는 적응형 양식*

![설문 조사 테마를 사용한 적응형 양식](assets/adaptive-form-with-survey-theme.png)

**그림:** *설문 조사 테마를 사용한 적응형 양식*

## 2단계:적응형 양식 {#step-update-your-adaptive-form} 업데이트

위에 표시된 디자인에는 기존의 적응형 양식의 자리 표시자 텍스트와 로고를 변경해야 합니다. 다음 단계를 수행하여 필요한 변경 작업을 수행합니다.

1. 헤더의 기존 로고와 텍스트를 변경합니다. 로고를 제거하려면

   1. 양식 편집기에서 양식을 엽니다.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. 헤더 구성 요소에서 로고 이미지를 탭하고 ![cmppr](assets/cmppr.png) 속성을 탭합니다. 이미지 속성에서 X를 눌러 기존 로고 이미지를 제거합니다.
   1. 업로드를 탭하고 logo.png를 선택한 다음, ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 탭하여 변경 내용을 저장합니다. [시작하기 전에](/help/forms/using/style-your-adaptive-form.md#before-you-start) 섹션에서 이미지를 다운로드했습니다.
   1. 헤더 텍스트 `We.Retail`를 탭하고 ![aem_6_3_edit](assets/aem_6_3_edit.png) **편집**&#x200B;을 탭합니다. 헤더 텍스트를 `we retail`로 변경합니다. `we retail`의 `we`에만 굵은 서식만 적용합니다.

   ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. 제목을 제거하고 자리 표시자 텍스트를 추가합니다.

   1. 고객 ID 필드를 탭하고 ![cmppr](assets/cmppr.png) 속성을 탭합니다.
   1. **제목** 필드의 내용을 **자리 표시자 텍스트** 필드에 복사합니다.
   1. **제목** 필드의 콘텐츠를 삭제하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 탭합니다.
   1. 양식의 모든 텍스트 상자, 숫자 상자 및 이메일 필드에 대해 이전 3단계를 반복합니다.

   ![업데이트된 적응형 양식](assets/updated-adaptive-form.png)

## 3단계:적응형 양식 {#step-create-a-custom-theme-for-your-adaptive-form} 사용자 지정 테마를 만듭니다.

[테마 편집기](/help/forms/using/themes.md)를 사용하여 사용자 지정 테마를 만들 수 있습니다. 테마 편집기는 강력한 WYSIWYG 편집기입니다. 적응형 양식의 다양한 구성 요소에 CSS를 적용하는 시각적 방법입니다. 적응형 양식의 구성 요소와 패널에 대한 스타일을 보다 세밀하게 제어할 수 있습니다.

테마는 적응형 양식과 같은 별도의 엔티티입니다. 여기에는 적응형 양식의 구성 요소 및 패널에 대한 스타일(CSS)이 포함되어 있습니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 CSS 속성이 포함됩니다. 테마를 적용하면 지정된 스타일이 적응형 양식의 해당 구성 요소에 적용됩니다.

이 자습서에서는 머리글 및 바닥글, 텍스트 및 숫자 구성 요소, 첨부 파일 구성 요소 및 단추의 스타일을 지정합니다. 먼저 테마 만들기를 시작하십시오.

### 테마 {#create-a-theme} 만들기

1. AEM 작성자 인스턴스에 로그인하고 **Adobe Experience Manager** > **Forms** > **테마**&#x200B;로 이동합니다. 기본 URL은 [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes)입니다.
1. **[!UICONTROL 만들기]**&#x200B;를 누르고 **[!UICONTROL 테마]**&#x200B;를 선택합니다. 테마를 만드는 데 필요한 필드가 있는 테마 만들기 페이지가 나타납니다. 제목 및 이름 필드는 필수입니다.

   * **제목:** 테마의 제목을 지정합니다. 예: **글로벌 테마.** 제목은 테마 목록에서 테마를 식별하는 데 도움이 됩니다.
   * **이름:** 테마 이름을 지정합니다. 예: **전역-테마.** 지정된 이름의 노드가 저장소에 생성됩니다. 제목을 입력을 시작하면 이름 필드의 값이 자동으로 생성됩니다. 제안된 값을 변경할 수 있습니다. 이름 필드에는 영숫자, 하이픈 및 밑줄만 포함할 수 있습니다. 잘못된 입력은 모두 하이픈으로 대체됩니다.

1. **만들기**&#x200B;를 누릅니다. 테마가 만들어지고 편집할 양식을 여는 대화 상자가 나타납니다. **열기**&#x200B;를 눌러 새 탭에서 새로 만든 테마를 엽니다. 테마가 테마 편집기에서 열립니다. 스타일링을 위해 테마 편집기에서는 AEM Forms과 함께 제공되는 기본 적응형 양식을 사용합니다.

   테마 편집기 UI 사용에 대한 자세한 내용은 [테마 편집기 정보](/help/forms/using/themes.md#aboutthethemeeditor)를 참조하십시오.

1. **테마 옵션** ![테마 옵션](assets/theme-options.png) > **구성**&#x200B;을 탭합니다. **양식 미리 보기** 필드에서 **shipping-address-add-update-form** 적응형 양식을 선택하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 탭하고 **저장**&#x200B;을 탭합니다. 이제 테마 편집기는 기본 적응형 양식 대신 고유한 적응형 양식을 사용하도록 구성됩니다. **취소**&#x200B;를 눌러 테마 편집기로 돌아갑니다.

   ![사용자 정의 테마](assets/custom-theme.png)

   **그림:** *shipping-address-add-update-form 적응형 양식이 있는 테마 편집기*

   ![테마 만들기](assets/create-a-theme.png)

   **그림:** *기본 양식이 있는 적응형 양식*

### 스타일 머리글 및 바닥글 {#style-header-and-footer}

머리글과 바닥글은 적응형 양식의 일관적이고 독특한 모양을 제공합니다. 일반적으로 머리글에는 조직의 로고와 이름이 포함되어 있으며 바닥글에는 저작권 정보가 포함되어 있으며 이러한 정보는 조직의 여러 양식에서 동일하게 유지됩니다. shipping-address-add-update-form 적응형 양식의 머리글 및 바닥글에 스타일을 지정하려면 다음을 수행합니다.

1. 선택기 패널에서 **헤더** > **텍스트** 옵션을 탐색합니다. 선택기 패널은 테마 편집기 왼쪽에 있습니다. 패널이 표시되지 않으면 ![사이드 패널 전환](assets/toggle-side-panel.png) 사이드 패널 전환 을 탭합니다.

1. **Text** 아코디언에서 다음 속성을 설정하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 탭합니다.

   | 속성 | 값 |
   |---|---|
   | 글꼴 모음 | Arial |
   | 글꼴 색상 | FFFFFF |
   | 글꼴 크기 | 54px |

1. 헤더 위젯을 탭하고 **Header**&#x200B;을(를) 탭합니다. 헤더 위젯의 스타일을 지정하는 옵션이 왼쪽에 나타납니다. **Dimension 및 위치** 아코디언을 확장하고 **높이**&#x200B;를 `120px`로 설정하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 탭합니다.
1. 헤더 위젯의 배경 아코디언을 확장하고 **배경색**&#x200B;을 `F6921E.`로 설정합니다.

   **이미지 및 그라데이션** > **+ 추가**&#x200B;를 마우스로 가리킨 다음 **이미지**&#x200B;를 탭합니다. 다음 속성을 설정하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 누릅니다.

   | 속성 | 값 |
   |---|---|
   | 이미지 | header-style.png를 업로드합니다. [시작하기 전에](/help/forms/using/style-your-adaptive-form.md#before-you-start) 섹션에서 이미지를 다운로드했습니다. |
   | 위치 | 오른쪽 단추 |
   | 바둑판식으로 배열 | 반복 안 함 |

1. 테마 편집기에서 헤더에서 로고를 탭하고 **헤더 로고**&#x200B;를 누릅니다. Dimension 및 위치 아코디언을 확장하고 다음 속성을 설정하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 누릅니다.

<table> 
 <tbody> 
  <tr> 
   <td>여백</td> 
   <td>값</td> 
  </tr> 
  <tr> 
   <td>여백</td> 
   <td> 
    <ul> 
     <li>상단:1.5rem</li> 
     <li>아래쪽:-35px</li> 
     <li>왼쪽:1rem<strong><br /> </strong></li> 
    </ul> <p><strong>팁: </strong>  <img src="assets/link.png"> 링크 아이콘을 탭하여 각 필드에 다른 값을 제공합니다.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>높이</td> 
   <td>4.75rem</td> 
  </tr> 
 </tbody> 
</table>

1. 바닥글 위젯을 탭하고 **바닥글**&#x200B;을 탭합니다. **배경** 아코디언을 확장하고 **배경색**&#x200B;을 `F6921E`로 설정하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 탭합니다.

### 데이터 캡처 구성 요소의 스타일을 지정하고 배경을 적응형 양식 {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}에 적용합니다

적응형 양식에 여러 구성 요소를 사용하여 데이터를 캡처할 수 있습니다. 예를 들어, 텍스트 상자 및 숫자 상자가 있습니다. 모든 데이터 캡처 구성 요소와 동일한 스타일을 제공하거나 각 구성 요소에 대해 별도의 스타일을 제공할 수 있습니다. 이 자습서에서는 동일한 스타일이 숫자 상자(고객 ID, 우편 번호) 및 텍스트 상자(고객 ID, 이름, 배송 주소, 상태, 이메일)에 적용됩니다. 데이터 캡처 구성 요소의 스타일을 지정하려면 다음을 수행합니다.

1. 고객 ID 필드를 탭하고 **필드 위젯** 옵션을 탭합니다. 다음 속성을 설정하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 누릅니다.

<table> 
 <tbody> 
  <tr> 
   <td>어코디언</td> 
   <td>속성</td> 
   <td>값</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 색상</td> 
   <td>A7A9AC</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 반지름 </td> 
   <td> 
    <ul> 
     <li>상단:7px<br /> </li> 
     <li>오른쪽:7px<br /> </li> 
     <li>아래쪽:7px<br /> </li> 
     <li>왼쪽:7px<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 모음</td> 
   <td>굴림</td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 색상</td> 
   <td>939598<br /> </td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 크기</td> 
   <td>18px</td> 
  </tr> 
  <tr> 
   <td>Dimension 및 위치</td> 
   <td>너비</td> 
   <td>60%</td> 
  </tr> 
  <tr> 
   <td>Dimension 및 위치</td> 
   <td>여백</td> 
   <td> 
    <ul> 
     <li>왼쪽:10rem</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

1. 고객 ID 필드 위의 빈 영역을 탭하고 **응답형 패널 컨테이너**&#x200B;를 탭합니다. **배경** > **배경색**&#x200B;을 F1F2F2로 설정합니다. ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 누릅니다.

   ![](do-not-localize/responsive-panel-container.png)

### {#style-the-buttons} 단추의 스타일을 지정합니다.

사용자 지정 테마를 사용하여 적응형 양식의 모든 단추와 동일한 스타일을 적용하고 [인라인 스타일](/help/forms/using/inline-style-adaptive-forms.md)을 사용하여 특정 단추에 스타일을 적용할 수 있습니다. 단추의 스타일을 지정하려면 다음을 수행합니다.

1. **Submit** 단추를 탭하고 **Button** 옵션을 탭합니다. 다음 속성을 설정하고 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)를 누릅니다.

<table> 
 <tbody> 
  <tr> 
   <td>어코디언</td> 
   <td>속성</td> 
   <td>값</td> 
  </tr> 
  <tr> 
   <td>배경</td> 
   <td>배경색</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>테두리<br /> </td> 
   <td>테두리 색상</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 반지름 </td> 
   <td> 
    <ul> 
     <li>상단:7px<br /> </li> 
     <li>오른쪽:7px<br /> </li> 
     <li>아래쪽:7px<br /> </li> 
     <li>왼쪽:7px</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>텍스트<br /> </td> 
   <td>글꼴 모음</td> 
   <td>굴림</td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 색상</td> 
   <td>FFFF</td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 크기</td> 
   <td>18px</td> 
  </tr> 
 </tbody> 
</table>

1. [사용자 지정 테마](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form), 전역 테마를 적응형 양식에 적용합니다. 스타일이 적응형 양식에 반영되지 않으면 브라우저 캐시를 지우고 다시 시도하십시오.

   ![style-data-capture-components](assets/style-data-capture-components.png)

## 4단계:개별 구성 요소 스타일 지정 {#step-style-individual-components}

일부 스타일은 특정 구성 요소에만 적용됩니다. 이러한 구성 요소는 적응형 양식 편집기에서 스타일이 지정됩니다.

1. 편집할 적응형 양식을 엽니다. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. 상단 막대에서 **스타일** 옵션을 선택합니다.

   ![style-option](assets/style-option.png)

1. **첨부** 단추를 탭하고 ![aem_6_3_edit](assets/aem_6_3_edit.png)아이콘을 탭합니다. **Dimension 및 위치** 아코디언에서 다음 속성을 설정합니다.

   | 속성 | 값 |
   |---|---|
   | 부동 | 왼쪽 |
   | 너비 | 10% |

1. **정부 승인 주소 증명** 옵션을 탭하고 ![aem_6_3_edit](assets/aem_6_3_edit.png)아이콘을 탭합니다. 다음 속성을 설정합니다.

<table> 
 <tbody> 
  <tr> 
   <td>어코디언</td> 
   <td>속성</td> 
   <td>값</td> 
  </tr> 
  <tr> 
   <td>치수 및 위치</td> 
   <td>부동</td> 
   <td>왼쪽</td> 
  </tr> 
  <tr> 
   <td>치수 및 위치</td> 
   <td>너비</td> 
   <td>73%</td> 
  </tr> 
  <tr> 
   <td>치수 및 위치</td> 
   <td>사진 간격</td> 
   <td> 
    <ul> 
     <li>왼쪽:10px</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>치수 및 위치</td> 
   <td>높이</td> 
   <td>40px</td> 
  </tr> 
  <tr> 
   <td>치수 및 위치<br /> </td> 
   <td>여백</td> 
   <td><br /> 
    <ul> 
     <li>오른쪽:2rem</li> 
     <li>왼쪽:10rem </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>배경</td> 
   <td>배경색</td> 
   <td>FFFF</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 너비</td> 
   <td>1px</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 스타일</td> 
   <td>단색</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 색상</td> 
   <td>A7A9AC</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 반지름</td> 
   <td>7px</td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 모음</td> 
   <td>굴림</td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 색상</td> 
   <td>BCBEC0</td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>글꼴 크기</td> 
   <td>18px</td> 
  </tr> 
  <tr> 
   <td>텍스트</td> 
   <td>선 높이</td> 
   <td>2</td> 
  </tr> 
 </tbody> 
</table>

1. **Submit** 단추를 탭하고 ![aem_6_3_edit](assets/aem_6_3_edit.png) 아이콘을 탭합니다. 다음 속성을 설정합니다.

<table> 
 <tbody> 
  <tr> 
   <td>어코디언</td> 
   <td>속성</td> 
   <td>값</td> 
  </tr> 
  <tr> 
   <td>Dimension 및 위치</td> 
   <td>부동</td> 
   <td>오른쪽</td> 
  </tr> 
  <tr> 
   <td>Dimension 및 위치</td> 
   <td>여백</td> 
   <td> 
    <ul> 
     <li>상단:5rem</li> 
     <li>오른쪽:14rem</li> 
     <li>아래쪽:20px</li> 
     <li>왼쪽:20px<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>배경</td> 
   <td>배경색</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>테두리</td> 
   <td>테두리 색상</td> 
   <td>F6921E</td> 
  </tr> 
 </tbody> 
</table>

![styled-adaptive-form-1](assets/styled-adaptive-form-1.png)

## 5단계:보너스 섹션:사용자 지정 테마에서 웹 글꼴 사용 {#step-bonus-section-using-web-fonts-in-a-custom-theme}

다양한 글꼴을 사용하여 적응형 양식을 디자인할 수 있습니다. 적응형 양식을 본 모든 장치에는 적응형 양식을 디자인하는 데 사용되는 글꼴이 없을 수 있습니다. 웹 글꼴 서비스를 사용하여 필요한 글꼴을 대상 장치에 제공할 수 있습니다.

Adobe Typekit은 웹 글꼴 서비스입니다. 적응형 양식과 함께 서비스를 구성하고 사용할 수 있습니다. 적응형 양식에서 Adobe Typekit을 사용하려면:

>[!NOTE]
>
>![typekit-to-adobe-](assets/typekit-to-adobe-fonts.png) fontsTypekit은 이제 Adobe Fonts라고 하며 Creative Cloud 및 기타 구독에 포함되어 있습니다. [추가 정보](https://fonts.adobe.com/).

1. [Adobe Typekit](https://typekit.com/) 계정을 만들고, 키트를 만들고, Font Myriad Pro를 키트에 추가하고, 키트를 게시하고, 키트 ID를 얻습니다. 적응형 양식에서 Adobe Typekit 글꼴(웹 글꼴)을 사용해야 합니다.
1. AEM Forms 서버에서 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **Adobe Experience Manager** > **도구** ![햄머](assets/hammer.png) > **배포** > **Cloud Services**&#x200B;로 이동합니다. Cloud Services 페이지에서 **타사 서비스** > **Typekit**&#x200B;로 이동한 다음 Typekit 아래에서 **구성**&#x200B;지금 을 클릭합니다. 구성을 이미 사용할 수 있는 경우 + 버튼을 클릭하여 새 인스턴스를 만듭니다.

   구성 만들기 대화 상자에서 구성에 대한 **제목**&#x200B;을 지정하고 **만들기**&#x200B;를 클릭합니다. 구성 페이지로 리디렉션됩니다. 표시되는 구성 요소 편집 대화 상자에서 **키트 ID**&#x200B;를 제공하고 **확인**&#x200B;을 클릭합니다.

1. TypeKit 구성을 사용하도록 테마를 구성합니다. 작성자 인스턴스에서 테마 편집기에서 **전역 테마**&#x200B;를 엽니다. 테마 편집기에서 테마 옵션 ![테마 옵션](assets/theme-options.png) > 구성으로 이동합니다. **Typekit Configuration** 필드에서 키트를 선택하고 **Save**&#x200B;를 클릭합니다.

   Typekit에 추가된 글꼴은 모든 구성 요소의 **Text** 아코디언 중에서 선택할 수 있습니다.
