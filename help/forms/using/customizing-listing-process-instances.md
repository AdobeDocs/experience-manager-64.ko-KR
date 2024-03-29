---
title: 프로세스 인스턴스 목록 사용자 정의
seo-title: Customizing the listing of process instances
description: AEM Forms 작업 공간의 프로세스 인스턴스에 표시되는 속성을 사용자 지정하는 방법
seo-description: How-to customize the properties displayed in process instance in AEM Forms workspace.
uuid: 3b55d9b9-7f73-46dd-9eb6-42be218440a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 40d7d43f-ee0a-4e34-ae93-20c9c940f76b
exl-id: e7b8206c-bac2-48a6-b353-d06bc73b29f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 5%

---

# 프로세스 인스턴스 목록 사용자 정의 {#customizing-the-listing-of-process-instances}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

프로세스 인스턴스 목록이 AEM Forms 작업 공간의 추적 탭에 표시됩니다.

프로세스 인스턴스 목록에서 각 프로세스 인스턴스에 대해 AEM Forms 작업 공간에 해당 인스턴스의 일부 속성이 표시됩니다. 각 프로세스 인스턴스에 대해 다음 속성을 사용할 수 있습니다. 이러한 속성은 프로세스 인스턴스 구성 요소 모델에 속성으로 저장되며 해당 보기 및 템플릿에서 사용할 수 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>속성</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>프로세스 인스턴스에 대한 설명입니다.</td> 
  </tr> 
  <tr> 
   <td>개시자</td> 
   <td>프로세스 인스턴스의 개시자의 이름입니다.</td> 
  </tr> 
  <tr> 
   <td>initiatorId</td> 
   <td>프로세스 인스턴스의 개시자의 ID입니다.</td> 
  </tr> 
  <tr> 
   <td>processCompleteTime</td> 
   <td>프로세스가 완료되면 타임스탬프를 지정합니다.</td> 
  </tr> 
  <tr> 
   <td>processInstanceId</td> 
   <td>프로세스 인스턴스의 ID입니다.</td> 
  </tr> 
  <tr> 
   <td>processInstanceStatus</td> 
   <td>0 = 시작됨<br /> 1 = 실행 중<br /> 2 = 완료<br /> 3 = 완료<br /> 4 = 종료됨<br /> 5 = 종료 중<br /> 6 = 일시 중단됨<br /> 7 = 일시 중단<br /> 8 = 일시 중단 해제</td> 
  </tr> 
  <tr> 
   <td>processName</td> 
   <td>프로세스의 이름입니다.</td> 
  </tr> 
  <tr> 
   <td>processStartTime</td> 
   <td>프로세스가 시작될 때의 타임스탬프입니다.</td> 
  </tr> 
  <tr> 
   <td>processVariables</td> 
   <td>프로세스 변수의 개체 배열입니다. 각 프로세스 변수 개체에는 다음이 포함됩니다 <strong>이름</strong> (프로세스 변수의 이름), <strong>value</strong> (프로세스 변수 값) 및<strong> 유형</strong> (프로세스 변수 유형)</td> 
  </tr> 
 </tbody> 
</table>

**예:**

를 표시하려면 `description` 프로세스 인스턴스 카드에서 프로세스 인스턴스의 등록 정보를 수행하려면 다음 단계를 수행하십시오.

1. 다음을 수행합니다 [AEM Forms 작업 공간 사용자 지정을 위한 일반 단계](/help/forms/using/generic-steps-html-workspace-customization.md).
1. 다음 작업을 수행합니다.

   1. /libs/ws/js/runtime/templates/processinstance.html 가 없는 경우 이 파일을 /apps/ws/js/runtime/templates/에 복사합니다. 클릭 **모두 저장**.
   1. class = &#39;processDescription&#39;인 프로세스 설명 div를 추가합니다. inprocessinstance.html

   ```
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. 다음 작업을 수행합니다.

   1. /apps/ws/js/registry.js 을 열어 편집합니다.
   1. 검색 및 바꾸기 `text!/lc/libs/ws/js/runtime/templates/processinstance.html`with `text!/lc/`**앱**/ws/js/runtime/templates/processinstance.html

1. 위의 변경 사항에서는 다음과 같은 방법으로 스타일 시트 /apps/ws/css/newStyle.css에 항목을 추가하여 CSS 파일을 업데이트해야 할 수 있습니다.

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement as well as user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
