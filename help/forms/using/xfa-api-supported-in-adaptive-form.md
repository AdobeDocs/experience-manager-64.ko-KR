---
title: XDP 기반 적응형 양식의 XFA 지원
seo-title: XFA support in XDP-based adaptive forms
description: 응용 양식에 지원되는 XFA 이벤트, 속성, 스크립트 및 유효성 검사를 나열합니다.
seo-description: Lists supported XFA events, properties, scripts, and validation in adaptive forms.
uuid: 2f976de3-2cdf-4bbb-acd1-048a498930f0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: eaf60421-097e-4feb-b661-433a512470ab
feature: Adaptive Forms
exl-id: 86596819-8108-409e-af14-4634e8a1959d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 6%

---

# XDP 기반 적응형 양식의 XFA 지원 {#xfa-support-in-xdp-based-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

적응형 양식은 XDP 파일에 정의된 다음과 같은 다양한 XFA 이벤트, 속성, 스크립트 및 유효성 검사를 지원합니다.

* XDP 파일의 이벤트에 정의된 스크립트 실행.
* XDP 파일의 필드에 대한 기본값 및 동작 속성을 캡처합니다.
* XDP 파일에 정의된 유효성 검사 스크립트 실행.

XDP 파일을 기반으로 적응형 양식을 만들면 속성, 이벤트 및 유효성 검사가 양식 작성 UI에서 자동으로 채워집니다. 그러나 양식 작성자는 이러한 요소 중 일부를 재정의하여 대체 경험을 만들 수 있습니다.

이 문서에서는 적응형 양식에 적용된 지원되는 XFA 이벤트, 속성 및 유효성 검사를 나열하고 적응형 양식에서 이러한 이벤트를 재정의하는 방법을 설명합니다.

## 적응형 양식에서 지원되는 XFA 요소 및 해당 매핑 {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### 필드 {#fields}

XDP 파일을 사용하여 적응형 양식을 만들 때 XFA 필드를 적응형 양식으로 드래그 드롭할 수 있습니다. 다음 표에는 XFA 필드가 적응형 양식 필드에 매핑되는 방법이 나와 있습니다.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA 필드 또는 컨테이너</strong></p> </td> 
   <td><p><strong>해당 적응형 양식 구성 요소</strong></p> </td> 
  </tr>
  <tr>
   <td><p>버튼 </p> </td> 
   <td><p>버튼</p> </td> 
  </tr>
  <tr>
   <td><p>체크 상자 </p> </td> 
   <td><p>체크 상자</p> </td> 
  </tr>
  <tr>
   <td><p>목록 상자 </p> </td> 
   <td><p>드롭다운 목록</p> </td> 
  </tr>
  <tr>
   <td><p>날짜/시간 필드 </p> </td> 
   <td><p>날짜 선택기</p> </td> 
  </tr>
  <tr>
   <td><p>서명 스크리블</p> </td> 
   <td><p>낙서 서명</p> </td> 
  </tr>
  <tr>
   <td><p>숫자 필드 </p> </td> 
   <td><p>숫자 상자</p> </td> 
  </tr>
  <tr>
   <td><p>십진수 필드</p> </td> 
   <td><p>숫자 상자</p> </td> 
  </tr>
  <tr>
   <td><p>텍스트 필드 </p> </td> 
   <td><p>텍스트 상자</p> </td> 
  </tr>
  <tr>
   <td><p>암호 필드 </p> </td> 
   <td><p>암호 상자</p> </td> 
  </tr>
  <tr>
   <td><p>이미지</p> </td> 
   <td><p>이미지</p> </td> 
  </tr>
  <tr>
   <td><p>텍스트</p> </td> 
   <td><p>텍스트</p> </td> 
  </tr>
  <tr>
   <td><p>하위 양식 </p> </td> 
   <td><p>패널</p> </td> 
  </tr>
  <tr>
   <td><p>영역(그룹)</p> </td> 
   <td><p>패널</p> </td> 
  </tr>
  <tr>
   <td><p>하위 양식 집합 </p> </td> 
   <td><p>패널</p> </td> 
  </tr>
 </tbody>
</table>

### 속성 {#properties}

다음 표는 XDP 파일에 정의된 다양한 XFA 스크립트가 적응형 양식에서 작동하는 방식을 캡처합니다.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA 구성 요소 속성</strong></p> </td> 
   <td><p><strong>적응형 양식의 해당 동작</strong></p> </td> 
  </tr>
  <tr>
   <td><p>somExpression </p> </td> 
   <td><p>적응형 양식의 Bind 참조(bindRef) 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>존재 </p> </td> 
   <td><p>적응형 양식의 표시되는 속성에 매핑됩니다. 가시성 표현식을 사용하여 이를 재정의할 수 있습니다.</p> </td> 
  </tr>
  <tr>
   <td><p>액세스 </p> </td> 
   <td><p>적응형 양식의 활성화된 속성에 매핑됩니다. Access 표현식을 사용하여 재정의할 수 있습니다.</p> </td> 
  </tr>
  <tr>
   <td><p>액세스 가능성: 역할 </p> </td> 
   <td><p>적응형 양식의 역할 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>액세스 가능성: speakPriority </p> </td> 
   <td><p>적응형 양식의 speakPriority 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>액세스 가능성: speakText</p> </td> 
   <td><p>적응형 양식의 사용자 지정 액세서빌러티 텍스트에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>액세스 가능성: toolTip </p> </td> 
   <td><p>적응형 양식의 짧은 설명 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>캡션<em> (모든 필드 유형)</em></p> </td> 
   <td><p>적응형 양식의 제목 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>displayFormat<em> (모든 필드 유형)</em></p> </td> 
   <td><p>적응형 양식의 표시 패턴에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>rawValue<em> (모든 필드 유형)</em></p> </td> 
   <td><p>적응형 양식의 값 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>항목<em> (목록 상자, 확인란)</em></p> </td> 
   <td><p>적응형 양식의 옵션 속성에 매핑됩니다. 옵션 표현식을 사용하여 재정의할 수 있습니다.</p> </td> 
  </tr>
  <tr>
   <td><p>maxChar<em> (텍스트 필드)</em></p> </td> 
   <td><p>적응형 양식의 허용되는 최대 문자 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>여러 줄<em> (텍스트 필드)</em></p> </td> 
   <td><p>적응형 양식의 여러 줄 허용 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>frcDigit<em> (숫자 필드, 십진수 필드)</em></p> </td> 
   <td><p>적응형 양식의 프레임 자릿수 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>leadDigit<em> (숫자 필드, 십진수 필드)</em></p> </td> 
   <td><p>적응형 양식의 리드 자릿수 속성에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>multiSelect<em> (목록 상자)</em></p> </td> 
   <td><p>적응형 양식의 여러 선택 속성 허용에 매핑됩니다.</p> </td> 
  </tr>
 </tbody>
</table>

### 스크립트 {#scripts}

다음 표는 XDP 파일에 정의된 다양한 XFA 스크립트가 적응형 양식에서 작동하는 방식을 캡처합니다.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA 스크립트 이벤트</strong></p> </td> 
   <td><p><strong>적응형 양식의 해당 동작</strong></p> </td> 
  </tr>
  <tr>
   <td><p>초기화 </p> </td> 
   <td><p>이 스크립트는 런타임에 실행되며 적응형 양식으로 재정의할 수 없습니다.</p> </td> 
  </tr>
  <tr>
   <td><p>계산</p> </td> 
   <td><p>적응형 양식의 계산 표현식에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>유효성 검사 </p> </td> 
   <td><p>적응형 양식의 유효성 검사 표현식에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>validationState </p> </td> 
   <td><p>이 스크립트는 런타임에 실행되며 적응형 양식으로 재정의할 수 없습니다.<br /> </p> </td> 
  </tr>
  <tr>
   <td><p>종료 </p> </td> 
   <td><p>이 스크립트는 런타임에 실행되며 적응형 양식으로 재정의할 수 없습니다.</p> </td> 
  </tr>
  <tr>
   <td><p>클릭(단추 필드)</p> </td> 
   <td><p>단추의 Click 표현식에 매핑됩니다.</p> </td> 
  </tr>
  <tr>
   <td><p>서버측 스크립트 지원</p> </td> 
   <td><p>이 스크립트는 런타임에 실행되며 적응형 양식으로 재정의할 수 없습니다.</p> </td> 
  </tr>
  <tr>
   <td><p>웹 서비스 지원</p> </td> 
   <td><p>이 스크립트는 런타임에 실행되며 적응형 양식으로 재정의할 수 없습니다.</p> </td> 
  </tr>
  <tr>
   <td><p>변경(스크리블 필드, 라디오 단추, 확인란)</p> </td> 
   <td><p>이 스크립트는 런타임에 실행되며 적응형 양식으로 재정의할 수 없습니다.</p> </td> 
  </tr>
 </tbody>
</table>

### 유효성 검사 {#validations}

다음 표는 XFA 유효성 검사가 적응형 양식의 유효성 검사에 매핑되는 방법을 캡처합니다.

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA 유효성 검사</strong></p> </td> 
   <td><p><strong>적응형 양식의 해당 유효성 검사</strong></p> </td> 
  </tr>
  <tr>
   <td><p>유효성 검사 패턴(formatTest)</p> </td> 
   <td><p>validatePictureClause</p> </td> 
  </tr>
  <tr>
   <td><p>유효성 검사 패턴 메시지(formatTestMessage)</p> </td> 
   <td><p>validatePictureMessage</p> </td> 
  </tr>
  <tr>
   <td><p>필수(nullTest)</p> </td> 
   <td><p>필수 </p> </td> 
  </tr>
  <tr>
   <td><p>빈 메시지(nullTestMessage) </p> </td> 
   <td><p>mandatoryMessage</p> </td> 
  </tr>
  <tr>
   <td><p>스크립트 유효성 검사(scriptTest)</p> </td> 
   <td><p>validateExp</p> </td> 
  </tr>
  <tr>
   <td><p>유효성 검사 스크립트 메시지(scriptTestMessage)</p> </td> 
   <td><p>validateMessage</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>적응형 양식 라디오 단추와 XFA 확인 단추에 바인딩된 확인란 그룹에 대한 필수 속성은 재정의할 수 없습니다.
