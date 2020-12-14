---
title: 적응형 양식에서 양식 데이터 모델 서비스를 호출하는 API
seo-title: 적응형 양식에서 양식 데이터 모델 서비스를 호출하는 API
description: '적응형 양식 필드 내에서 WSDL로 작성된 웹 서비스를 호출하는 데 사용할 수 있는 invokeWebServices API에 대해 설명합니다. '
seo-description: '적응형 양식 필드 내에서 WSDL로 작성된 웹 서비스를 호출하는 데 사용할 수 있는 invokeWebServices API에 대해 설명합니다. '
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 1%

---


# 적응형 양식 {#api-to-invoke-form-data-model-service-from-adaptive-forms}에서 양식 데이터 모델 서비스를 호출하는 API

## 개요 {#overview}

AEM Forms을 사용하면 양식 작성자가 적응형 양식 필드 내에서 양식 데이터 모델에 구성된 서비스를 호출함으로써 양식 채우기 환경을 보다 간소화하고 향상시킬 수 있습니다. 데이터 모델 서비스를 호출하려면 시각적인 편집기에서 규칙을 만들거나 [규칙 편집기](/help/forms/using/rule-editor.md)의 코드 편집기에서 `guidelib.dataIntegrationUtils.executeOperation` API를 사용하여 JavaScript를 지정할 수 있습니다.

이 문서에서는 `guidelib.dataIntegrationUtils.executeOperation` API를 사용하여 서비스를 호출하는 JavaScript를 작성하는 데 중점을 둡니다.

## API {#using-the-api} 사용

`guidelib.dataIntegrationUtils.executeOperation` API는 적응형 양식 필드 내에서 서비스를 호출합니다. API 구문은 다음과 같습니다.

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

API에는 다음 매개 변수가 필요합니다.

| 매개 변수 | 설명 |
|---|---|
| `operationInfo` | 양식 데이터 모델 식별자, 작업 제목 및 작업 이름을 지정하는 구조 |
| `inputs` | 서비스 작업에 값을 입력하는 양식 객체를 지정하는 구조 |
| `outputs` | 서비스 작업에서 반환한 값으로 채울 양식 객체를 지정하는 구조 |

`guidelib.dataIntegrationUtils.executeOperation` API의 구조는 서비스 작업에 대한 세부 정보를 지정합니다. 구조의 구문은 다음과 같습니다.

```
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

API 구조는 서비스 작업에 대해 다음과 같은 세부 정보를 지정합니다.

<table> 
 <tbody> 
  <tr> 
   <th>매개 변수</th> 
   <th>설명</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>양식 데이터 모델의 이름을 포함하는 저장소 경로를 지정합니다.</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>실행할 서비스 작업의 이름을 지정합니다.</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>하나 이상의 양식 개체를 서비스 작업의 입력 인수에 매핑</td> 
  </tr> 
  <tr> 
   <td>출력</td> 
   <td>하나 이상의 양식 객체를 서비스 작업의 출력 값에 매핑하여 양식 필드 채우기<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 서비스 {#sample-script-to-invoke-a-service}을 호출하는 샘플 스크립트

다음 샘플 스크립트는 `guidelib.dataIntegrationUtils.executeOperation` API를 사용하여 `employeeAccount` 양식 데이터 모델에 구성된 `getAccountById` 서비스 작업을 호출합니다.

`getAccountById` 작업은 `employeeID` 양식 필드의 값을 `empId` 인수에 대한 입력으로 사용하고 해당 직원의 직원 이름, 계정 번호 및 계정 잔액을 반환합니다. 출력 값은 지정된 양식 필드에 채워집니다. 예를 들어 `name` 인수의 값은 `fullName` 양식 요소에 채워지고 `account` 양식 요소의 `accountNumber` 인수에 대한 값이 채워집니다.

```
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```

