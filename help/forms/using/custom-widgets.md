---
title: HTML5 양식에서 사용자 정의 모양 만들기
seo-title: Create custom appearances in HTML5 forms
description: 사용자 지정 위젯을 모바일 Forms에 연결할 수 있습니다. 기존 jQuery 위젯을 확장하거나 사용자 지정 위젯을 개발할 수 있습니다.
seo-description: You can plug in custom widgets to a Mobile Forms. You can extend existing jQuery Widgets or develop your own custom widgets.
uuid: afb16f42-e404-478b-82dd-4b5b59c4f184
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 5d860f05-3257-4cf7-93dd-77d226d59b39
feature: Mobile Forms
exl-id: e9e53b6d-6403-4d37-bac1-efaff0317f34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---

# HTML5 양식에서 사용자 정의 모양 만들기 {#create-custom-appearances-in-html-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

사용자 지정 위젯을 모바일 Forms에 연결할 수 있습니다. 기존 jQuery 위젯을 확장하거나 모양 프레임워크를 사용하여 고유한 사용자 지정 위젯을 개발할 수 있습니다. XFA 엔진은 다양한 위젯을 사용합니다. 자세한 내용은 [적응형 및 HTML5 양식의 모양 프레임워크](/help/forms/using/introduction-widgets.md) 자세한 정보

![기본 및 사용자 지정 위젯의 예](assets/custom-widgets.jpg)
**그림:** *기본 및 사용자 지정 위젯의 예*

## 사용자 지정 위젯과 HTML 5 양식 통합 {#integrating-custom-widgets-with-html-forms}

### 프로필 만들기  {#create-a-profile-nbsp}

프로필을 만들거나 기존 프로필을 선택하여 사용자 지정 위젯을 추가할 수 있습니다. 프로필 만들기에 대한 자세한 내용은 [사용자 지정 프로필 만들기](/help/forms/using/custom-profile.md).

### 위젯 만들기 {#create-a-widget}

HTML5 양식은 새 위젯을 만들기 위해 확장할 수 있는 위젯 프레임워크의 구현을 제공합니다. 구현은 jQuery 위젯입니다 *abstractWidget* 새 위젯을 작성하기 위해 확장할 수 있습니다. 새 위젯은 아래에 언급된 함수를 확장/재정의해야만 작동할 수 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td>함수/클래스</td> 
   <td>설명</td> 
  </tr> 
  <tr> 
   <td>렌더링</td> 
   <td>render 함수는 위젯의 기본 HTML 요소에 대한 jQuery 개체를 반환합니다. 기본 HTML 요소는 포커스가 있는 유형이어야 합니다. 예, &lt;a&gt;, &lt;input&gt;, 및 &lt;li&gt;. 반환된 요소는 $userControl로 사용됩니다. $userControl이 위의 제약 조건을 지정하는 경우 AbstractWidget 클래스의 함수는 예상대로 작동하며, 그렇지 않으면 일반적인 API(focus, click) 중 일부는 변경해야 합니다. </td> 
  </tr> 
  <tr> 
   <td>getEventMap</td> 
   <td>HTML 이벤트를 XFA 이벤트로 변환하는 맵을 반환합니다. <br /> {<br /> 흐림 효과: XFA_EXIT_EVENT,<br /> }<br /> 이 예는 흐림 효과가 HTML 이벤트이고 XFA_EXIT_EVENT가 해당 XFA 이벤트임을 보여줍니다. </td> 
  </tr> 
  <tr> 
   <td>getOptionsMap</td> 
   <td>옵션 변경 시 수행할 작업을 자세히 제공하는 맵을 반환합니다. 키는 위젯에 제공되는 옵션이며 값은 해당 옵션이 변경될 때마다 호출되는 함수입니다. 위젯은 값 및 displayValue를 제외한 모든 공통 옵션에 대한 핸들러를 제공합니다</td> 
  </tr> 
  <tr> 
   <td>getCommitValue</td> 
   <td>위젯 프레임워크는 위젯의 값이 XFAModel(예: textField의 종료 이벤트)에 저장될 때마다 함수를 로드합니다. 구현은 위젯에 저장된 값을 반환해야 합니다. 처리기에 옵션에 대한 새 값이 제공됩니다.</td> 
  </tr> 
  <tr> 
   <td>showValue</td> 
   <td>기본적으로 Enter 이벤트 시 XFA에 필드의 rawValue가 표시됩니다. 이 함수는 사용자에게 rawValue를 표시하기 위해 호출됩니다. </td> 
  </tr> 
  <tr> 
   <td>showDisplayValue</td> 
   <td>기본적으로 종료 이벤트 시 XFA에 필드의 formatValue가 표시됩니다. 이 함수는 형식이 지정된 Value를 사용자에게 표시하도록 호출됩니다. </td> 
  </tr> 
 </tbody> 
</table>

위젯을 직접 만들려면, 위에서 만든 프로필에 재정의된 함수와 새로 추가된 함수를 포함하는 JavaScript 파일의 참조를 포함합니다. 예: *sliderNumericFieldWidget* 는 숫자 필드에 대한 위젯입니다. 헤더 섹션에서 프로필에서 위젯을 사용하려면 다음 줄을 포함하십시오.

```
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### XFA 스크립팅 엔진에 사용자 지정 위젯 등록  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

사용자 지정 위젯 코드가 준비되면 을 사용하여 위젯을 스크립팅 엔진에 등록합니다 `registerConfig`용 API [양식 브리지](/help/forms/using/form-bridge-apis.md). widgetConfigObject 를 입력으로 가져옵니다.

```
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

위젯 구성은 키가 필드를 식별하고 값이 해당 필드에 사용할 위젯을 나타내는 JSON 개체(키 값 쌍의 컬렉션)로 제공됩니다. 샘플 구성은 다음과 같습니다.

```
*{*

*“identifier1” : “customwidgetname”,  
“identifier2” : “customwidgetname2”,  
..  
}*
```

여기서 &quot;identifier&quot;는 특정 필드, 특정 유형의 필드 집합 또는 모든 필드를 나타내는 jQuery CSS 선택기입니다. 다음은 ID의 값 목록에따라 달라집니다.

| 식별자 유형 | 식별자 | 설명 |
|---|---|---|
| 이름 fieldname이 있는 특정 필드 | 식별자: &quot;div.fieldname&quot; | 이름이 &#39;fieldname&#39;인 모든 필드가 위젯을 사용하여 렌더링됩니다. |
| &#39;type&#39; 유형의 모든 필드(여기서 type은 NumericField, DateField 등)가: | 식별자: &quot;div.type&quot; | Timefield 및 DateTimeField의 경우 이 필드는 지원되지 않으므로 텍스트 필드입니다. |
| 모든 필드 | 식별자: &quot;div.field&quot; |  |
