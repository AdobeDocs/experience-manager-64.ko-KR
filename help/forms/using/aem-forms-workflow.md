---
title: OSGi의 Forms 중심 워크플로우
seo-title: Rapidly build adaptive forms-based processes, automate document services operations, and use Acrobat Sign with AEM workflows
description: AEM Forms Workflow를 사용하여 검토 및 승인을 자동화하고 신속하게 작성하여 문서 서비스를 시작하고(예를 들어 PDF 문서를 다른 형식으로 변환함), Acrobat Sign 서명 워크플로우와 통합 등을 수행할 수 있습니다.
seo-description: Use AEM Forms Workflow to automate and rapidly build review and approvals, to start document services (For example, to convert a PDF document to another format), integrate with Acrobat Sign signature workflow, and more.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
exl-id: fa39a4e8-ae22-4356-8935-44fdf1f4f609
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2902'
ht-degree: 3%

---

# OSGi의 Forms 중심 워크플로우 {#forms-centric-workflow-on-osgi}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

![](do-not-localize/header.png)

기업은 수백, 수천 개의 양식, 다양한 백엔드 시스템, 온라인 또는 오프라인 데이터 소스에서 데이터를 수집합니다. 또한 동적 사용자 집합을 사용하여 반복적인 검토 및 승인 프로세스를 포함하는 데이터에 대한 결정을 내릴 수 있습니다.

내부 및 외부 대상에 대한 검토 및 승인 워크플로우와 함께 대규모 조직 및 기업에는 반복 작업이 있습니다. 예를 들어 PDF 문서를 다른 형식으로 변환하는 작업이 있습니다. 수동으로 완료하면 이러한 작업에 많은 시간과 리소스가 필요합니다. 또한 기업은 사전 정의된 형식으로 나중에 사용할 수 있도록 문서를 디지털 서명하고 양식 데이터를 아카이브하는 법적 요구 사항을 가지고 있습니다.

## OSGi에서 Forms 중심의 워크플로우 소개 {#introduction-to-forms-centric-workflow-on-osgi}

AEM 워크플로우를 사용하여 적응형 양식 기반 워크플로우를 신속하게 구축할 수 있습니다. 이러한 워크플로우는 검토 및 승인, 비즈니스 프로세스 흐름, 문서 서비스 시작, Acrobat Sign 서명 워크플로우와 통합 및 유사한 작업에 사용할 수 있습니다. 예를 들어, 신용 카드 신청 처리, 직원이 승인 작업 과정을 중단하고 양식을 PDF 문서로 저장합니다. 또한 이러한 워크플로우는 조직 내부 또는 네트워크 방화벽에서 사용할 수 있습니다.

OSGi의 Forms 중심 워크플로우를 사용하면 JEE 스택에 완전한 프로세스 관리 기능을 설치하지 않고도 OSGi 스택에서 다양한 작업에 대한 워크플로우를 신속하게 작성하고 배포할 수 있습니다. 워크플로우의 개발 및 관리에서는 익숙한 AEM 워크플로우 및 AEM 받은 편지함 기능을 사용합니다. 워크플로우는 여러 소프트웨어 시스템, 네트워크, 부서 및 조직에 걸쳐 이루어지는 실제 업무 프로세스를 자동화하는 기초입니다.

설정되면, 사용자가 양식을 제출하거나 또는 [서신 관리](/help/forms/using/cm-overview.md) 편지. 향상된 AEM 워크플로우 기능을 통해 AEM Forms은 서로 다른 두 가지 기능을 제공하면서도 유사한 기능을 제공합니다. 배포 전략의 일부로 사용자에게 적합한 배포 방법을 결정해야 합니다. 다음을 참조하십시오 [비교](/help/forms/using/capabilities-osgi-jee-workflows.md) OSGi 및 JEE의 프로세스 관리에 대한 Forms 중심의 AEM 워크플로우입니다. 또한 배포 토폴로지에 대해서는 다음을 참조하십시오. [AEM Forms을 위한 아키텍처 및 배포 토폴로지](/help/forms/using/aem-forms-architecture-deployment.md).

OSGi에서 Forms 중심의 워크플로우 확장 [AEM 받은 편지함](/help/sites-authoring/inbox.md) 및 은 AEM Forms 중심의 워크플로우에 대한 지원을 추가하기 위해 AEM 워크플로우 편집기에 대한 추가 구성 요소(단계)를 제공합니다. 확장된 AEM 받은 편지함에는 다음과 유사한 기능이 있습니다 [AEM Forms 작업 공간](/help/forms/using/introduction-html-workspace.md). 인간 중심 워크플로우 관리(승인, 검토 등)와 함께 AEM 워크플로우를 사용하여 자동화할 수 있습니다 [문서 서비스](/help/sites-developing/workflows-step-ref.md)-관련 작업(예: PDF 생성) 및 전자 서명(Acrobat Sign) 문서.

다음 다이어그램은 OSGi에서 Forms 중심의 워크플로우를 작성, 실행 및 모니터링하는 종단 간 절차를 설명합니다.

![aem-forms-workflow 소개](assets/introduction-to-aem-forms-workflow.jpg)

## 시작하기 전 {#before-you-start}

* 워크플로우는 실제 비즈니스 프로세스를 나타냅니다. 실제 비즈니스 프로세스와 비즈니스 프로세스 참가자 목록을 준비하십시오. 또한 워크플로우를 만들기 전에 자료(적응형 양식, PDF 문서 등)를 준비할 수 있습니다.
* 워크플로우에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시되며 워크플로우의 진행 상황을 보고하는 데 도움이 됩니다. 비즈니스 프로세스를 논리적 단계로 나눕니다.
* AEM Workflows의 작업 할당 단계를 구성하여 사용자 또는 담당자에게 이메일 알림을 전송할 수 있습니다. 그래서 [이메일 알림 활성화](#configure-email-service).
* 워크플로우는 디지털 서명에 Acrobat Sign을 사용할 수도 있습니다. 워크플로우에서 Acrobat Sign을 사용하려는 경우, [AEM Forms용 Acrobat Sign 구성](/help/forms/using/adobe-sign-integration-adaptive-forms.md) 워크플로우에서 사용하기 전에

## 워크플로우 모델 만들기 {#create-a-workflow-model}

워크플로우 모델은 비즈니스 프로세스의 로직과 흐름으로 구성됩니다. 일련의 단계로 구성되어 있습니다. 이러한 단계는 AEM 구성 요소입니다. 필요에 따라 매개 변수 및 스크립트로 워크플로우 단계를 확장하여 더 많은 기능과 제어를 제공할 수 있습니다. AEM Forms에서는 즉시 사용 가능한 AEM 단계과 몇 가지 단계를 제공합니다. AEM 및 AEM Forms 단계의 세부 목록에 대해서는 다음을 참조하십시오 [AEM 워크플로우 단계 참조](/help/sites-developing/workflows-step-ref.md) 및 [OSGi의 Forms 중심 워크플로우 - 단계 참조](/help/forms/using/aem-forms-workflow.md).

AEM은 제공된 워크플로우 단계를 사용하여 워크플로우 모델을 만드는 직관적인 사용자 인터페이스를 제공합니다. 워크플로우 모델을 만드는 단계별 지침은 [워크플로우 모델 만들기](/help/sites-developing/workflows-models.md). 다음 예제에서는 승인 및 검토 작업 과정에 대한 워크플로우 모델을 만드는 단계별 지침을 제공합니다.

>[!NOTE]
>
>워크플로우 모델을 만들거나 편집하려면 워크플로우 편집기 그룹의 구성원이어야 합니다.

### 승인 및 검토 작업 과정에 대한 모델 만들기 {#create-a-model-for-an-approval-and-review-workflow}

승인 및 검토 작업 과정은 사람의 개입이 필요한 작업을 위한 것입니다. 다음 예제에서는 프론트 오피스 뱅킹 에이전트가 채울 대출 신청 워크플로우 모델을 생성합니다. 신청서를 작성하면 승인을 위해 전송됩니다. 나중에 승인된 신청은 Acrobat Sign을 사용하여 전자 서명을 신청한 사람에게 전송됩니다.

이 예는 아래에 첨부된 패키지로 사용할 수 있습니다. 패키지 관리자를 사용하여 예제를 가져오고 설치합니다. 다음 단계를 수행하여 애플리케이션에 대한 워크플로우 모델을 수동으로 만들 수도 있습니다.

이 예제에서는 프런트오피스 뱅킹 에이전트가 채울 모기지 응용 프로그램을 워크플로 모델을 만듭니다. 신청서를 작성하면 승인을 위해 전송됩니다. 나중에 승인된 애플리케이션은 Acrobat Sign을 사용하여 고객에게 전자 서명을 위해 전송됩니다. 패키지 관리자를 사용하여 예제를 가져오고 설치할 수 있습니다.

[파일 가져오기](assets/example-mortgage-loan-application.zip)

1. 워크플로우 모델 콘솔을 엽니다. 기본 URL은 `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. 선택 **[!UICONTROL 만들기]**, 그런 다음 **[!UICONTROL 모델 만들기]**. 워크플로우 모델 추가 대화 상자가 나타납니다.
1. 을(를) 입력합니다. **[!UICONTROL 제목]** 및 **[!UICONTROL 이름]** (선택 사항). 예를 들어, 담보 대출 신청입니다. 탭 **[!UICONTROL 완료]**.
1. 새로 만든 워크플로우 모델을 선택하고 탭합니다 **편집.** 이제 워크플로우 단계를 추가하여 비즈니스 논리를 작성할 수 있습니다. 워크플로우 모델을 처음 만들면 다음과 같은 내용이 포함됩니다.

   * 단계: 흐름 시작 및 흐름 종료. 이러한 단계는 워크플로우의 시작과 끝을 나타냅니다. 이러한 단계는 필수 사항이며 편집하거나 제거할 수 없습니다.
   * 단계 1이라는 참가자 단계의 예입니다. 이 단계는 관리자 사용자에게 작업 항목을 할당하도록 구성되어 있습니다. 이 단계를 제거합니다.

1. 이메일 알림을 활성화합니다. OSGi에서 Forms 중심의 워크플로우를 구성하여 사용자 또는 담당자에게 이메일 알림을 보낼 수 있습니다. 이메일 알림을 활성화하려면 다음 구성을 수행하십시오.

   1. 의 AEM 구성 관리자로 이동합니다. `https://[server]:[port]/system/console/configMgr`.
   1. 를 엽니다. **[!UICONTROL 일 CQ 메일 서비스]** 구성. 에 사용할 값을 지정합니다. **[!UICONTROL SMTP 서버 호스트 이름]**, **[!UICONTROL SMTP 서버 포트,]** 및 **[!UICONTROL &quot;보낸 사람&quot; 주소]** 필드. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
   1. 를 엽니다. **[!UICONTROL Day CQ Link Externalizer]** 구성. 에서 **[!UICONTROL 도메인]** 필드에서 로컬, 작성자 및 게시 인스턴스에 대한 실제 호스트 이름/IP 주소 및 포트 번호를 지정합니다. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

1. 워크플로우 단계를 만듭니다. 워크플로우에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시되며 워크플로우의 진행 상태를 보고합니다.

   스테이지를 정의하려면 ![info-circle](assets/info-circle.png) 아이콘 을 클릭하여 워크플로우 모델 속성을 열고 **[!UICONTROL 단계]** 탭하고 워크플로우 모델의 단계를 추가하고 탭합니다 **[!UICONTROL 저장 및 닫기]**. 예를 들어 담보 대출 애플리케이션의 경우 단계를 생성합니다. 대출 요청, 대출 요청 상태, 서명 문서 및 서명된 대출 문서

1. 드래그 앤 드롭 **[!UICONTROL 작업 할당]** 워크플로우 모델에 대한 단계 브라우저. 모델의 첫 번째 단계로 만듭니다.

   작업 할당 구성 요소는 워크플로우로 만든 작업을 사용자 또는 그룹에 할당합니다. 작업 할당과 함께 구성 요소를 사용하여 작업에 적응형 양식 또는 비대화형 PDF을 지정할 수 있습니다. 적응형 양식은 사용자의 입력을 수용하기 위해 필요하며 비대화형 PDF 또는 읽기 전용 적응형 양식은 검토 전용 워크플로우에 사용됩니다.

   이 단계를 사용하여 작업의 동작을 제어할 수도 있습니다. 예를 들어, 자동 레코드 문서를 만들고, 특정 사용자 또는 그룹에 작업을 할당하고, 제출된 데이터의 경로, 미리 채울 데이터 경로 및 기본 작업을 지정할 수 있습니다. 작업 할당 단계의 옵션에 대한 자세한 내용은 [OSGi의 Forms 중심 워크플로우 - 단계 참조](/help/forms/using/aem-forms-workflow.md) 문서.

   ![workflow-editor](assets/workflow-editor.png)

   모기지 애플리케이션 예제의 경우 작업이 완료되면 읽기 전용 적응형 양식을 사용하도록 지정 작업 단계를 구성하고 PDF 문서를 표시합니다. 또한, 대출 요청을 승인할 수 있는 사용자 그룹으로 을 선택합니다. 설정 **[!UICONTROL 작업]** 탭에서 비활성화하십시오 **[!UICONTROL 제출]** 선택 사항입니다. 을(를) 지정합니다 **[!UICONTROL 경로 변수]**. 예: actionTake. 또한 승인 및 거부 경로를 추가합니다. 경로는 AEM 받은 편지함에 별도의 작업(단추)으로 표시됩니다. 워크플로우는 사용자가 누르는 작업(단추)을 기반으로 분기를 선택합니다.

   예제 패키지를 가져올 수 있습니다. 이 패키지는 섹션의 시작 부분에서 다운로드할 수 있습니다. 여기에는 담보 대출 응용 프로그램과 같이 구성된 작업 단계의 모든 필드의 전체 값 세트가 포함됩니다.

1. OR 분할 구성 요소를 단계 브라우저에서 워크플로우 모델로 끌어다 놓습니다. OR 분할은 워크플로우에서 분할을 만들며, 그 뒤에는 하나의 분기만 활성화됩니다. 이 단계를 통해 워크플로우에 조건부 처리 경로를 도입할 수 있습니다. 필요에 따라 각 분기에 워크플로우 단계를 추가합니다.

   OR 분할의 속성을 열고 다음 코드 조각을 Branch1 및 Branch2에 추가합니다. 이러한 코드 조각은 AEM Inbox의 사용자 작업을 기반으로 분기를 선택하는 데 도움이 됩니다.

   **분기 1용 코드 조각**

   사용자가 탭할 때 **[!UICONTROL 승인]** AEM 받은 편지함에서 분기 1이 활성화됩니다.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **분기 2용 코드 조각**

   사용자가 탭할 때 **[!UICONTROL 거부]** AEM 받은 편지함에서 분기 2가 활성화됩니다.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. 다른 워크플로우 단계를 추가하여 비즈니스 논리를 작성합니다.

   담보 대출 예제의 경우, 아래 이미지에 표시된 대로 레코드의 생성 문서, 두 개의 지정 작업 단계 및 서명 문서 단계를 모델의 분기 1에 추가합니다. 작업 지정 단계 하나는 표시 및 전송입니다 **지원자에게 대출 서류에 서명하다** 그리고 다른 할당 작업 구성 요소 **서명된 문서를 표시합니다.**. 또한 2분기에 작업 구성 요소 할당을 추가합니다. 사용자가 AEM 받은 편지함에서 거부 를 탭하면 활성화됩니다.

   할당 작업 단계, 레코드 단계 문서 및 담보 대상 응용 프로그램과 같이 구성된 서명 문서 단계의 모든 필드의 전체 값 세트에 대해 이 섹션의 시작 부분에서 다운로드할 수 있는 예제 패키지를 가져옵니다.

   워크플로우 모델이 준비되었습니다. 다양한 방법을 통해 워크플로우를 시작할 수 있습니다. 자세한 내용은 [OSGi에서 Forms 중심의 워크플로우 시작](#launch).

   ![workflow editor-auditor](assets/workflow-editor-mortgage.png)

## Forms 중심의 워크플로우 애플리케이션 만들기 {#create-a-forms-centric-workflow-application}

애플리케이션이 워크플로우와 연관된 적응형 양식입니다. 받은 편지함을 통해 애플리케이션을 제출하면 연관된 워크플로우가 시작됩니다. AEM 받은 편지함 및 AEM Forms 앱에서 Forms 워크플로우를 응용 프로그램으로 사용할 수 있도록 하려면 다음을 수행하여 워크플로우 애플리케이션을 만듭니다.

>[!NOTE]
>
>워크플로 응용 프로그램을 만들고 관리하려면 fd-administrator 그룹의 구성원이어야 합니다.

1. AEM 작성자 인스턴스에서 ![도구](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL 워크플로우 애플리케이션 관리]** 및 탭 **[!UICONTROL 만들기]**.
1. 워크플로우 응용 프로그램 만들기 창에서 다음 필드에 대한 입력을 제공하고 **[!UICONTROL 만들기]**. 새 응용 프로그램이 만들어지고 워크플로 응용 프로그램 화면에 나열됩니다.

<table> 
 <tbody> 
  <tr> 
   <td>필드</td> 
   <td>설명</td> 
  </tr> 
  <tr> 
   <td>제목</td> 
   <td>제목은 AEM 받은 편지함에 표시되며 사용자가 애플리케이션을 선택하는 데 도움이 됩니다. 설명적으로 보관하세요. 예를 들어, 저축 계정 개설 애플리케이션이 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>이름 </td> 
   <td>응용 프로그램의 이름을 지정합니다. 알파벳, 숫자, 하이픈 및 밑줄을 제외한 모든 문자는 하이픈으로 바뀝니다. </td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>설명은 AEM 받은 편지함에 표시됩니다. 설명 필드에 응용 프로그램에 대한 자세한 정보를 제공합니다. 예를 들어 응용 프로그램의 목적입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>적응형 양식</td> 
   <td><p>적응형 양식의 경로를 지정합니다. 사용자가 애플리케이션을 시작하면 지정된 적응형 양식이 표시됩니다.</p> <p><strong>참고</strong>: 워크플로우 애플리케이션은 한 페이지 이상이거나 Apple iPad에서 스크롤해야 하는 양식 및 PDF 문서를 지원하지 않습니다. 애플리케이션이 Apple iPad에서 열리고 적응형 양식 또는 PDF 문서가 페이지보다 긴 경우 두 번째 페이지의 양식 필드와 컨텐츠가 유실됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td>그룹 액세스</td> 
   <td><p>그룹을 선택합니다. 선택한 그룹의 구성원에게만 AEM 받은 편지함에 응용 프로그램이 표시됩니다. 액세스 그룹 옵션을 사용하면 워크플로 사용자 그룹의 모든 그룹을 선택할 수 있습니다. </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>미리 채우기 서비스</td> 
   <td>선택 <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">미리 채우기 서비스</a> 적응형 양식에 사용할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>워크플로우 모델</td> 
   <td>선택 <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">워크플로우 모델</a> 참조하십시오. 워크플로우 모델은 비즈니스 프로세스의 로직과 흐름으로 구성됩니다. </td> 
  </tr> 
  <tr> 
   <td>데이터 파일 경로</td> 
   <td>crx-repository에서 데이터 파일의 경로를 지정합니다. 이 경로는 적응형 양식 페이로드를 기준으로 하며 데이터 파일의 이름을 포함합니다. 해당되는 경우 항상 확장자를 포함한 파일의 전체 이름을 포함하십시오. 예: [payload]/data.xml </td> 
  </tr> 
  <tr> 
   <td>첨부 파일 경로</td> 
   <td>crx-repository에서 첨부 파일 폴더의 경로를 지정합니다. 첨부 파일 경로는 페이로드 위치에 상대적입니다. 예: [payload]/data.xml </td> 
  </tr> 
  <tr> 
   <td>기록 문서 경로</td> 
   <td>crx-repository에 있는 레코드 문서 파일의 경로를 지정합니다. 경로는 적응형 양식 페이로드 위치에 상대적입니다. 해당되는 경우 항상 확장자를 포함한 파일의 전체 이름을 포함하십시오. 예: [payload]/DOR/creditcard.pdf</td> 
  </tr> 
 </tbody> 
</table>

## OSGi에서 Forms 중심의 워크플로우 시작 {#launch}

다음을 통해 Forms 중심의 워크플로우를 시작하거나 트리거할 수 있습니다.

* [AEM 받은 편지함에서 애플리케이션 제출](#inbox)
* [AEM Forms 앱에서 애플리케이션 제출](#afa)

* [적응형 양식 제출](#af)
* [감시 폴더 사용](#watched)

* [대화형 통신 또는 편지 제출](#letter)

### AEM 받은 편지함에서 애플리케이션 제출 {#inbox}

만든 워크플로 응용 프로그램은 받은 편지함에서 응용 프로그램으로 사용할 수 있습니다. 워크플로우 사용자 그룹의 구성원인 사용자는 관련 워크플로우를 트리거하는 애플리케이션을 작성하고 제출할 수 있습니다. AEM 받은 편지함을 사용하여 응용 프로그램을 제출하고 작업을 관리하는 방법에 대한 자세한 내용은 [AEM 받은 편지함에서 Forms 애플리케이션 및 작업 관리](/help/forms/using/manage-applications-inbox.md).

### AEM Forms 앱에서 애플리케이션 제출 {#afa}

AEM Forms 앱은 AEM Forms 서버와 동기화되며 계정에서 양식 데이터, 작업, 워크플로우 애플리케이션 및 저장된 정보(초안/템플릿)를 변경할 수 있습니다. 자세한 내용은 [AEM Forms 앱](/help/forms/using/aem-forms-app.md) 및 관련 문서.

### 적응형 양식 제출 {#af}

적응형 양식 제출 시 워크플로우를 시작하도록 적응형 양식의 제출 작업을 구성할 수 있습니다. 적응형 양식은 다음을 제공합니다. **[!UICONTROL AEM 워크플로우 호출]** 작업을 제출하여 적응형 양식 제출 시 워크플로우를 시작합니다. 제출 작업에 대한 자세한 내용은 [제출 작업 구성](/help/forms/using/configuring-submit-actions.md). AEM Forms 앱을 통해 적응형 양식을 제출하려면 적응형 양식 속성에서 AEM Forms 앱과 동기화 를 활성화합니다.

AEM Forms 앱에서 워크플로우를 동기화, 제출 및 트리거하도록 적응형 양식을 구성할 수 있습니다. 자세한 내용은 [양식 작업](/help/forms/using/working-with-form.md).

### 감시 폴더 사용 {#watched}

관리자(fd-administrators 그룹의 구성원)는 사용자가 폴더에 파일(예: PDF 파일)을 배치할 때 미리 구성된 워크플로우를 실행하도록 네트워크 폴더를 구성할 수 있습니다. 워크플로우가 완료되면 결과 파일을 지정된 출력 폴더에 저장할 수 있습니다. 이러한 폴더를 [감시 폴더](/help/forms/using/watched-folder-in-aem-forms.md). 워크플로우를 시작할 감시 폴더를 구성하려면 다음 절차를 수행하십시오.

1. AEM 작성자 인스턴스에서 ![도구](assets/tools.png) **[!UICONTROL Forms > 감시 폴더 구성]**. 이미 구성된 감시 폴더 목록이 표시됩니다.
1. 탭 **[!UICONTROL 새로 만들기]**. 필드 목록이 표시됩니다. 워크플로우에 대한 감시 폴더를 구성할 다음 필드에 값을 지정합니다.

<table> 
 <tbody> 
  <tr> 
   <td>필드</td> 
   <td>설명</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">이름</span></td> 
   <td>감시 폴더의 이름을 지정합니다. 이 필드는 영숫자만 지원합니다.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">경로</span></td> 
   <td>감시 폴더의 실제 위치를 지정합니다. 클러스터형 환경에서는 AEM 클러스터 노드에서 액세스할 수 있는 공유 네트워크 폴더를 사용합니다.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">사용 중인 파일 처리</span></td> 
   <td>을(를) 선택합니다 <span class="uicontrol">워크플로우 </span>선택 사항입니다. </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">워크플로우 모델</span></td> 
   <td>워크플로우 모델을 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">출력 파일 패턴</span></td> 
   <td>출력 파일 및 디렉토리의 디렉토리 구조를 지정합니다. 을(를) 지정할 수도 있습니다 <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">출력 파일 및 디렉토리의 패턴</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. 탭 **[!UICONTROL 고급]**. 다음 필드에 값을 지정하고 **[!UICONTROL 만들기]**. 감시 폴더는 워크플로우를 시작하도록 구성되어 있습니다. 이제 감시 폴더의 입력 디렉토리에 파일이 배치될 때마다 지정된 워크플로우가 트리거됩니다.

   | 필드 | 설명 |
   |---|---|
   | 페이로드 매퍼 필터  | 감시 폴더를 만들면 crx-repository에 폴더 구조가 만들어집니다. 폴더 구조는 워크플로우에 대한 페이로드 역할을 할 수 있습니다. AEM Workflow를 매핑하여 감시 폴더 구조의 입력을 허용하는 스크립트를 작성할 수 있습니다. 즉시 구현할 수 있으며 페이로드 매퍼 필터에 나열됩니다. 사용자 지정 구현이 없는 경우 기본 구현을 선택합니다. |

   고급 탭에는 더 많은 필드가 포함되어 있습니다. 이러한 필드 대부분은 기본값을 포함합니다. 모든 필드에 대해 알아보려면 [감시 폴더 만들기 또는 구성](/help/forms/using/creating-configure-watched-folder.md) 문서.

### 대화형 통신 또는 편지 제출 {#letter}

대화형 통신 또는 편지를 제출할 때 OSGi에서 Forms 중심의 워크플로우를 연결 및 실행할 수 있습니다. 서신 관리 워크플로우에서는 사후 처리 대화형 커뮤니케이션 및 편지에 사용됩니다. 예를 들어, 최종 문자를 전자 메일, 인쇄, 팩스 또는 아카이빙할 수 있습니다. 자세한 단계는 [인터랙티브 통신 및 문자 사후 처리](/help/forms/using/submit-letter-topostprocess.md).

## 추가 구성 {#additional-configurations}

### 이메일 서비스 구성 {#configure-email-service}

AEM Workflows의 작업 할당 및 이메일 보내기 단계를 사용하여 이메일을 보낼 수 있습니다. 전자 메일을 보내는 데 필요한 전자 메일 서버 및 기타 구성을 지정하려면 다음 단계를 수행하십시오.

1. 의 AEM 구성 관리자로 이동합니다. `https://[server]:[port]/system/console/configMgr`.
1. 를 엽니다. **[!UICONTROL 일 CQ 메일 서비스]** 구성. 에 사용할 값을 지정합니다. **[!UICONTROL SMTP 서버 호스트 이름]**, **[!UICONTROL SMTP 서버 포트,]** 및 **[!UICONTROL &quot;보낸 사람&quot; 주소]** 필드. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 를 엽니다. **[!UICONTROL Day CQ Link Externalizer]** 구성. 에서 **[!UICONTROL 도메인]** 필드에서 로컬, 작성자 및 게시 인스턴스에 대한 실제 호스트 이름/IP 주소 및 포트 번호를 지정합니다. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

### 워크플로우 인스턴스 제거 {#purge-workflow-instances}

워크플로 인스턴스 수를 최소화하면 워크플로 엔진의 성능이 향상되므로 완료되었거나 실행 중인 워크플로 인스턴스를 저장소에서 정기적으로 제거할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [워크플로우 인스턴스 일반 삭제](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).
