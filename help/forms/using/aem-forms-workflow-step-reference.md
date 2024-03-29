---
title: OSGi의 Forms 중심 워크플로우 - 단계 참조
seo-title: Forms-centric workflow on OSGi - Step Reference
description: OSGi 단계를 기반으로 하는 Forms 중심의 워크플로우를 통해 적응형 양식 기반 워크플로우를 신속하게 구축할 수 있습니다.
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: AEM Docs
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
exl-id: f8e25989-6ed3-4b35-95e5-fbfd7c51d622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4673'
ht-degree: 0%

---

# OSGi의 Forms 중심 워크플로우 - 단계 참조 {#forms-centric-workflow-on-osgi-step-reference}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## Forms Workflow 단계 {#forms-workflow-steps}

Forms 워크플로우 단계는 AEM 워크플로우에서 AEM Forms 관련 작업을 수행합니다. 이러한 단계를 통해 OSGi에서 Forms 중심의 워크플로우를 기반으로 적응형 양식을 신속하게 작성할 수 있습니다. 이러한 워크플로우는 기본 검토 및 승인 작업 과정, 내부 및 방화벽 비즈니스 프로세스를 개발하는 데 사용할 수 있습니다. Forms Workflow 단계를 사용하여 문서 서비스를 시작하고, Acrobat Sign 서명 워크플로우와 통합하고, 기타 AEM Forms 작업을 수행할 수도 있습니다. 필요한 경우 [AEM Forms 추가 기능](https://www.adobe.com/go/learn_aemforms_documentation_63) 워크플로우에서 이러한 단계를 사용하려면

## 작업 단계 할당 {#assign-task-step}

작업 할당 단계에서는 작업을 만들어 사용자 또는 그룹에 지정합니다. 작업 할당과 함께 구성 요소는 작업에 대한 적응형 양식 또는 비대화형 PDF도 지정합니다. 적응형 양식은 사용자의 입력을 수용하기 위해 필요하며 비대화형 PDF 또는 읽기 전용 적응형 양식은 검토 전용 워크플로우에 사용됩니다.

구성 요소를 사용하여 작업의 동작을 제어할 수도 있습니다. 예를 들어, 자동 레코드 문서를 만들고, 특정 사용자 또는 그룹에 작업을 할당하고, 제출된 데이터의 경로를 지정하고, 미리 채울 데이터의 경로를 지정하고, 기본 작업을 지정할 수 있습니다. 작업 할당 단계에는 다음 속성이 있습니다.

* **제목:** 작업의 제목입니다. 제목이 AEM 받은 편지함에 표시됩니다.
* **설명:** 작업에서 수행 중인 작업에 대한 설명입니다. 이 정보는 공유 개발 환경에서 작업할 때 다른 프로세스 개발자에게 유용합니다.

* **축소판 그림 경로:** 작업 축소판의 경로입니다. 경로를 지정하지 않으면 적응형 양식 기본 축소판이 표시되고 기록 문서에 대해 기본 아이콘이 표시됩니다.
* **워크플로우 단계:** 워크플로우에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시됩니다. 모델의 속성(사이드 킥과 페이지 > 페이지 속성 > 단계)에서 이러한 단계를 정의할 수 있습니다.
* **우선 순위:** 선택한 우선순위가 AEM 받은 편지함에 표시됩니다. 사용 가능한 옵션은 높음, 중간, 낮음입니다. 기본값은 보통입니다.
* **기한:** 작업 지연으로 표시된 후 일 또는 시간 수를 지정합니다. 선택하는 경우 **해제**&#x200B;을 지정하면 작업이 지연으로 표시되지 않습니다. 작업 기한이 지난 후 특정 작업을 수행할 시간 초과 처리기를 지정할 수도 있습니다.

* **일:** 작업을 완료하기 전 일 수입니다. 작업이 사용자에게 지정된 후 일 수가 계산됩니다. 작업이 완료되지 않고 일 필드에 지정된 일 수를 교차하는 경우, 이 옵션을 선택하면 기한 후 시간 초과 처리기가 트리거됩니다.
* **시간:** 작업을 완료하기 전 시간 작업이 사용자에게 지정된 후 시간 수가 계산됩니다. 작업이 완료되지 않고 시간 필드에 지정된 시간 수를 교차하는 경우, 이 옵션을 선택하면 시간 초과 처리기가 기한 후 트리거됩니다.
* **기한 후 시간 초과:** 시간 초과 처리기 선택 필드를 사용하려면 이 옵션을 선택합니다.
* **시간 제한 처리기:** 작업 할당 단계가 기한 일자를 넘을 때 실행할 스크립트를 선택합니다. 다음 위치의 CRX 저장소에 배치된 스크립트 [앱]/fd/dashboard/scripts/timeoutHandler 를 선택할 수 있습니다. 지정된 경로가 crx-repository에 없습니다. 관리자는 이 경로를 사용하기 전에 만듭니다.
* **작업 세부 정보의 마지막 작업에서 작업 및 설명을 강조 표시합니다.** 작업의 작업 세부 사항 섹션에서 마지막으로 수행한 작업과 받은 설명을 표시하려면 이 옵션을 선택합니다.
* **유형:** 워크플로우를 시작할 때 채울 문서 유형을 선택합니다. 적응형 양식, 읽기 전용 적응형 양식 또는 비대화형 PDF 문서를 선택할 수 있습니다.
* **적응형 양식 사용:** 입력 적응형 양식을 찾을 방법을 지정합니다. 절대 경로에서 사용할 수 있는 적응형 양식을 사용하거나, 워크플로우에 페이로드로 제출하거나, 변수를 사용하여 계산된 경로에서 사용할 수 있습니다. 문자열 유형의 변수를 사용하여 경로를 지정할 수 있습니다.
* **적응형 양식 경로**: 적응형 양식의 경로를 지정합니다. 적응형 양식 필드 사용 의 절대 경로 옵션과 함께 유형 필드의 적응형 양식 또는 읽기 전용 적응형 양식 옵션을 사용할 때 필드를 사용할 수 있습니다.
* **PDF 경로:** 비대화형 PDF 문서의 경로를 지정합니다. 유형 필드에서 비대화형 PDF 문서를 선택하면 필드를 사용할 수 있습니다. 경로는 항상 페이로드를 기준으로 합니다. 예, [Payload_Directory]/Workflow/PDF/credit-card.pdf 경로가 crx-repository에 없습니다. 관리자는 이 경로를 사용하기 전에 만듭니다. PDF 경로 옵션을 사용하려면 레코드 문서 옵션을 활성화하거나 양식 서식 파일을 기반으로 적응형 양식을 사용해야 합니다.
* **완료된 작업의 경우 적응형 양식을 다음으로 렌더링합니다.**: 작업이 완료됨으로 표시되면 적응형 양식을 읽기 전용 적응형 양식 또는 PDF 문서로 렌더링할 수 있습니다. 적응형 양식을 기록 문서로 렌더링하려면 기록 문서 옵션을 활성화하거나 양식 서식 파일을 기반으로 하는 적응형 양식이 필요합니다.
* **미리 채울 정보:** 아래 나열된 다음 필드는 작업에 대한 입력으로 사용됩니다.

   * **데이터 파일 경로:** 입력 데이터 파일(.json 또는 .xml)의 경로입니다. 경로는 항상 페이로드를 기준으로 합니다. 예를 들어 파일에는 AEM 받은 편지함 애플리케이션을 통해 양식에 대해 제출된 데이터가 포함되어 있습니다. 경로의 예는 다음과 같습니다 [Payload_Directory]/workflow/data.
   * **첨부 경로:** 위치에서 사용할 수 있는 첨부 파일은 작업과 관련된 양식에 첨부됩니다. 경로는 항상 페이로드를 기준으로 합니다. 경로의 예는 다음과 같습니다 [Payload_Directory]/attachments/

* **제출된 정보:** 아래 나열된 다음 필드는 작업의 출력 위치로 사용됩니다.

   * **데이터 파일 경로:** 데이터 파일(.json 또는 .xml)의 경로입니다. 데이터 파일에는 관련 양식을 통해 제출된 정보가 들어 있습니다. 경로는 항상 페이로드를 기준으로 합니다. 예, [Payload_Directory]/Workflow/data. 여기서 데이터는 파일입니다.
   * **첨부 경로:** 작업에서 양식 첨부 파일을 저장할 경로를 제공합니다.
   * **레코드 경로 문서:** 레코드 문서를 저장하는 경로입니다. 예, [Payload_Directory]/DocumentofRecord/credit-card.pdf 경로 필드가 비어 있는 경우 기록 문서가 생성되지 않습니다. 경로는 항상 페이로드를 기준으로 합니다.

* **할당 옵션:** 사용자에게 작업을 할당할 방법을 지정합니다. 참가자 선택기 스크립트를 사용하여 사용자 또는 그룹에 작업을 동적으로 할당하거나 특정 AEM 사용자 또는 그룹에 작업을 지정할 수 있습니다.
* **참가자 선택기:** 이 옵션은 **동적으로 사용자 또는 그룹에 추가** 옵션 지정 필드에서 옵션이 선택되어 있습니다. ECMAScript 또는 서비스를 사용하여 사용자나 그룹을 동적으로 선택할 수 있습니다. 자세한 내용은 [사용자에게 워크플로우를 동적으로 할당](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) 및 [사용자 지정 Adobe Experience Manager 동적 참가자 단계 만들기](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **참가자:** 이 필드는 **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantSelector]** 참가자 선택기 필드에서 옵션이 선택됩니다. 필드에서는 RandomParticipantSelector 옵션의 사용자 또는 그룹을 선택할 수 있습니다.

* **인수:** 이 필드는 참가자 선택기 필드에서 RandomParticipantChoose 스크립트 이외의 스크립트를 선택한 경우 사용할 수 있습니다. 필드에서는 참가자 선택기 필드에서 선택한 스크립트에 대해 쉼표로 구분된 인수 목록을 제공할 수 있습니다.

* **사용자 또는 그룹:** 작업이 선택한 사용자 또는 그룹에 할당됩니다. 이 옵션은 **특정 사용자 또는 그룹 옵션** 옵션 지정 필드에서 이 선택되어 있습니다. 이 필드에는 workflow-users 그룹의 모든 사용자와 그룹이 나열됩니다.

* **할당자에게 전자 메일로 알림:** 할당자에게 전자 메일 알림을 전송하려면 이 옵션을 선택합니다. 이러한 알림은 작업이 사용자에게 할당되면 전송됩니다. 옵션을 사용하기 전에 AEM 웹 콘솔에서 알림을 활성화하십시오. 단계별 지침은 [할당 작업 단계에 대한 이메일 알림 구성](/help/forms/using/aem-forms-workflow.md)

* **HTML 이메일 템플릿**: 알림 이메일에 사용할 이메일 템플릿을 선택합니다. 템플릿을 편집하려면 crx-repository에서 /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt에 있는 파일을 수정합니다.
* **위임 허용 대상:** AEM 받은 편지함은 로그인한 사용자에게 할당된 워크플로우를 다른 사용자에게 위임하는 옵션을 제공합니다. 동일한 그룹 내에서 또는 다른 그룹의 워크플로우 사용자에게 위임할 수 있습니다. 작업이 단일 사용자 및 **할당자 그룹의 구성원에게 위임 허용** 옵션을 선택한 경우 작업을 다른 사용자 또는 그룹에 위임할 수 없습니다.

* **기본 작업:** 즉시 제출, 저장 및 재설정 작업을 사용할 수 있습니다. 기본적으로 모든 기본 작업이 활성화됩니다.
* **경로 변수:** 경로 변수의 이름입니다. 경로 변수는 사용자가 AEM 받은 편지함에서 선택하는 사용자 지정 작업을 캡처합니다.
* **경로:** 작업은 다른 경로에 분기될 수 있습니다. AEM 받은 편지함에서 선택하면 경로에는 값이 반환되고 선택한 경로를 기준으로 워크플로우 분기가 반환됩니다.
* **제목**: 경로의 제목을 지정합니다. AEM 받은 편지함에 표시됩니다.
* **Coral 아이콘**: coral 아이콘의 HTML 속성을 지정합니다. Adobe CoreUI 라이브러리는 방대한 터치 첫 번째 아이콘 세트를 제공합니다. 라우트의 아이콘을 선택하여 사용할 수 있습니다. AEM 받은 편지함에 제목과 함께 표시됩니다.
* **할당자가 댓글을 추가할 수 있도록 허용**: 작업에 대한 설명을 활성화하려면 이 옵션을 선택합니다. 할당자는 작업 제출 시 AEM 받은 편지함 내에서 주석을 추가할 수 있습니다.
* **할당자가 작업에 첨부 파일 추가 허용**: 작업에 대한 첨부 파일을 사용하려면 이 옵션을 선택합니다. 할당자는 작업 제출 시 AEM 받은 편지함 내에서 첨부 파일을 추가할 수 있습니다.
* **작업 첨부 파일의 출력 경로**: 첨부 파일의 위치를 지정합니다. 위치는 페이로드를 기준으로 합니다.
* **사용자 지정 메타데이터 사용:** 사용자 지정 메타데이터 필드를 활성화하려면 이 옵션을 선택합니다. 사용자 지정 메타데이터는 이메일 템플릿에 사용됩니다.
* **사용자 지정 메타데이터:** 이메일 템플릿에 대한 사용자 지정 메타데이터를 선택합니다. 사용자 지정 메타데이터는 apps/fd/dashboard/scripts/metadataScripts의 crx 저장소에서 사용할 수 있습니다. 지정된 경로가 crx-repository에 없습니다. 관리자는 이 경로를 사용하기 전에 만듭니다. 사용자 지정 메타데이터에 서비스를 사용할 수도 있습니다. 또한 `WorkitemUserMetadataService` 사용자 지정 메타데이터를 제공하는 인터페이스입니다.

* **이전 단계의 데이터 표시**: 이 옵션을 선택하면 담당자에게 이전 담당자, 작업에 이미 수행한 작업, 작업에 추가된 댓글, 완료된 작업의 기록 문서를 볼 수 있습니다(가능한 경우).
* **후속 단계의 데이터 표시:** 현재 할당자가 후속 할당자가 작업에 추가한 작업과 설명을 보려면 이 옵션을 선택합니다. 또한 현재 할당자는 필요한 경우 완료된 작업의 기록 문서를 볼 수 있습니다.
* **데이터 유형의 가시성:** 기본적으로 할당자는 이전 및 이후 할당자가 추가한 기록 문서, 담당자, 조치 및 설명을 볼 수 있습니다. 할당자에게 표시되는 데이터 유형을 제한하려면 데이터 유형 표시 옵션을 사용합니다.

## 이메일 전송 단계 {#send-email-step}

전자 메일 단계를 사용하여 문서, 적응형 양식 링크, 대화형 통신 링크 또는 첨부된 PDF 문서가 있는 전자 메일 등을 보낼 수 있습니다. 이메일 전송 단계에서 지원 [HTML 이메일](https://en.wikipedia.org/wiki/HTML_email). HTML 이메일은 응답형이며 수신자의 이메일 클라이언트 및 화면 크기에 맞게 조정됩니다. HTML 이메일 템플릿을 사용하여 이메일의 모양, 색상 구성표 및 동작을 정의할 수 있습니다.

이메일 단계에서는 Day CQ Mail Service를 사용하여 이메일을 전송합니다. 이메일 단계를 사용하기 전에 [이메일 서비스](/help/forms/using/aem-forms-workflow.md) 가 구성되어 있습니다. 이메일 단계에는 다음 속성이 있습니다.

**제목:** 단계의 제목은 워크플로우 편집기에서 단계를 식별하는 데 도움이 됩니다.

**설명:** 설명은 공유 개발 환경에서 작업할 때 다른 프로세스 개발자에게 유용합니다.

**이메일 제목:** 제목은 워크플로우 메타데이터에서 검색하거나 수동으로 지정할 수 있습니다. 을(를) 선택합니다 **리터럴** 수동으로 제목을 지정하거나 **워크플로우 메타데이터에서 검색** 메타데이터 속성에서 제목을 검색하는 옵션입니다.

**HTML 이메일 템플릿**: 이메일에 대한 HTML 템플릿입니다. 이메일 템플릿에 변수를 지정할 수 있습니다. 이메일 단계에서 입력을 위해 템플릿에 포함된 모든 변수를 추출하고 표시합니다.

**전자 메일 템플릿 메타데이터:** 이메일 템플릿 변수 값은 사용자가 지정하는 값, 작성자 또는 게시 서버의 자산 경로, 이미지 또는 워크플로우 메타데이터 속성일 수 있습니다.

* **리터럴:** 지정할 정확한 값을 알고 있는 경우 옵션을 사용합니다. 예, [example@example.com](mailto:example@example.com).

* **워크플로우 메타데이터:** 사용할 값이 워크플로우 메타데이터 속성에 저장되면 옵션을 사용합니다. 옵션을 선택한 후 워크플로우 메타데이터 옵션 아래의 빈 텍스트 상자에 메타데이터 속성 이름을 입력합니다. 예를 들어 emailAddress가 있습니다.
* **자산 URL:** 대화형 커뮤니케이션의 웹 링크를 전자 메일에 포함하려면 옵션을 사용합니다. 옵션을 선택한 후 포함할 대화형 커뮤니케이션을 찾아 선택합니다. 자산은 작성자 또는 게시 서버에 있을 수 있습니다.
* **이미지:** 이메일에 이미지를 포함하려면 옵션을 사용합니다. 옵션을 선택한 후 이미지를 찾아 선택합니다. 이미지 옵션은 이메일 템플릿에서 사용할 수 있는 이미지 태그(&lt;img src=&quot;&amp;ast;&quot; />)에만 사용할 수 있습니다.

**보낸 사람 / 받는 사람의 이메일 주소:** 을(를) 선택합니다 **리터럴** 이메일 주소를 수동으로 지정하거나 선택하는 옵션 **워크플로우 메타데이터에서 검색** 메타데이터 속성에서 이메일 주소를 검색하는 옵션입니다. 에 대한 메타데이터 속성 배열 목록을 지정할 수도 있습니다 **워크플로우 메타데이터에서 검색** 선택 사항입니다.

**파일 첨부 경로:** 지정된 위치에서 사용할 수 있는 자산이 전자 메일에 첨부됩니다. 자산의 경로는 페이로드 또는 절대 경로를 기준으로 할 수 있습니다. 경로의 예는 다음과 같습니다 [Payload_Directory]/attachments/

**파일 이름:** 전자 메일 첨부 파일의 이름입니다. 이메일 단계에서 첨부 파일의 원래 파일 이름을 지정된 파일 이름으로 변경합니다. 이름은 워크플로우 메타데이터 속성에서 수동으로 지정하거나 검색할 수 있습니다. 를 사용하십시오 **리터럴** 지정할 정확한 값을 알고 있는 경우 옵션을 선택합니다. 를 사용하십시오 **워크플로우 메타데이터에서 검색** 사용할 값이 워크플로우 메타데이터 속성에 저장되면 선택합니다.

## 레코드 문서 생성 단계 {#generate-document-of-record-step}

양식을 채우거나 제출하면 양식의 레코드를 인쇄나 문서 형식으로 유지할 수 있습니다. 이를 기록 문서(DoR)라고 합니다. [레코드 문서 생성] 단계를 사용하여 적응형 양식의 읽기 전용 또는 대화형 PDF 버전을 만들 수 있습니다. PDF 버전에는 적응형 양식의 레이아웃과 함께 양식에 입력된 정보가 포함되어 있습니다.

레코드 문서 단계에는 다음 속성이 있습니다.

**적응형 양식 사용**: 입력 적응형 양식을 찾을 방법을 지정합니다. 절대 경로에서 사용할 수 있는 적응형 양식을 사용하거나, 워크플로우에 페이로드로 제출하거나, 변수를 사용하여 계산된 경로에서 사용할 수 있습니다. 문자열 유형의 변수를 사용하여 경로를 지정할 수 있습니다.

**적응형 양식 경로**: 적응형 양식의 경로를 지정합니다. 적응형 양식 필드 사용 의 절대 경로 옵션과 함께 유형 필드의 적응형 양식 또는 읽기 전용 적응형 양식 옵션을 사용할 때 필드를 사용할 수 있습니다.

**입력 데이터 경로:** 적응형 양식에 대한 입력 데이터의 경로입니다. 데이터를 페이로드를 기준으로 한 위치에 유지하거나 데이터의 절대 경로를 지정할 수 있습니다. 입력 데이터는 적응형 양식과 병합되어 레코드 문서를 만듭니다.

**입력 첨부 경로:** 입력 첨부 경로: 첨부 파일의 경로입니다. 이러한 첨부 파일은 기록 문서에 포함됩니다. 첨부 파일을 페이로드에 대해 위치에 유지하거나 첨부 파일의 절대 경로를 지정할 수 있습니다.

첨부 파일 등의 폴더 경로를 지정하면 폴더에서 직접 사용할 수 있는 모든 파일이 레코드 문서에 첨부됩니다. 지정한 첨부 경로에서 직접 사용할 수 있는 폴더에서 사용할 수 있는 파일이 있으면 첨부 파일로 기록 문서에 포함됩니다. 직접 사용 가능한 폴더에 폴더가 있으면 건너뜁니다.

**생성된 레코드 경로 문서:** 레코드 파일의 문서를 보관할 위치를 지정합니다. 페이로드 폴더를 덮어쓰거나 레코드 문서를 페이로드 디렉토리 내의 위치에 배치하도록 선택할 수 있습니다.

**로케일**: 레코드 문서의 언어를 지정합니다.

## 양식 데이터 모델 서비스 단계 호출 {#invoke-form-data-model-service-step}

다음을 사용할 수 있습니다 [AEM Forms 데이터 통합](/help/forms/using/data-integration.md) 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 이러한 데이터 소스는 데이터베이스, 웹 서비스, REST 서비스, OData 서비스 및 CRM 솔루션일 수 있습니다. AEM Forms 데이터 통합을 사용하면 구성된 데이터베이스에서 데이터 검색, 추가, 업데이트 작업을 수행하기 위해 다양한 서비스를 포함하는 양식 데이터 모델을 만들 수 있습니다. 를 사용할 수 있습니다 **데이터 모델 서비스 단계 호출** FDM(양식 데이터 모델)을 선택하고 FDM의 서비스를 사용하여 서로 다른 데이터 소스에 데이터를 검색, 업데이트 또는 추가할 수 있습니다.

단계의 필드에 대한 입력을 설명하기 위해 다음 데이터베이스 테이블 및 JSON 파일이 예로 사용됩니다.

**샘플 CustomerDetails 테이블**

<table> 
 <tbody> 
  <tr> 
   <td>속성</td> 
   <td>값<br /> </td> 
  </tr> 
  <tr> 
   <td>이름<br /> </td> 
   <td>사라<br /> </td> 
  </tr> 
  <tr> 
   <td>성</td> 
   <td>로즈</td> 
  </tr> 
  <tr> 
   <td>고객 ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>이메일 주소<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**샘플 JSON 파일**

```
{ 
  customer: { 
   firstName: "Sarah", 
   lastName:"Rose", 
   customerId: "1", 
   emailAddress:"srose@we.info" 
 }, 
  insurance: {
   customerId: "1", 
  policyType: "Premium,
  policyNumber: "Premium-521499",
  customerDetails: { 
   firstName: "Sarah",
   lastName: "Rose",
   customerId: "1",
   emailAddress: "srose@we.info" 
  }
 }
}
```

양식 데이터 모델 서비스 호출 단계에는 양식 데이터 모델 작업을 용이하게 하기 위해 다음과 같은 필드가 나열되어 있습니다.

* **제목:** 단계의 제목입니다. 워크플로우 편집기에서 단계를 식별하는 데 도움이 됩니다.
* **설명:** 공유 개발 환경에서 작업하는 경우 다른 프로세스 개발자에게 유용한 설명입니다.

* **양식 데이터 모델 경로**: 서버에 있는 양식 데이터 모델을 찾아 선택합니다.

* **서비스**: 선택한 양식 데이터 모델에서 제공하는 서비스 목록입니다.
* **서비스 입력 > 리터럴, 워크플로우 메타데이터 및 JSON 파일을 사용하여 입력 데이터 제공**: 서비스에는 여러 개의 인수가 있을 수 있습니다. 옵션을 선택하여 워크플로우 메타데이터 속성, JSON 개체에서 서비스 인수 값을 얻거나 제공된 텍스트 상자에 값을 직접 입력합니다.

   * **리터럴:** 지정할 정확한 값을 알고 있는 경우 옵션을 사용합니다. 예: srose@we.info
   * **워크플로우 메타데이터에서 검색:** 사용할 값이 워크플로우 메타데이터 속성에 저장되면 옵션을 사용합니다. 예를 들어 emailAddress가 있습니다.
   * **JSON 점 표기법:** 사용할 값이 JSON 파일에 있을 때 옵션을 사용합니다. 예를 들어, insurance.customerDetails.emailAddress.JSON 점 표기법 옵션은 입력 JSON에서 입력 필드 매핑 옵션을 선택한 경우에만 사용할 수 있습니다.
   * **입력 JSON에서 입력 필드 매핑:** JSON 파일에서 일부 서비스 인수의 입력 값을 가져올 JSON 파일의 경로를 지정합니다. JSON 파일의 경로는 페이로드 또는 절대 경로를 기준으로 할 수 있습니다.

* **서비스 입력 > JSON 파일을 사용하여 입력 데이터 제공:** JSON 파일에서 모든 인수에 대한 값을 가져오려면 옵션을 선택합니다.
* **입력 JSON 파일 경로**: 모든 서비스 인수에 대한 값이 포함된 JSON 파일의 경로입니다. JSON 파일의 경로는 다음과 같습니다 **페이로드에 대해 상대** 또는 **절대 경로**.

* **JSON 점 표기법:** 지정된 JSON 파일의 모든 개체를 서비스 인수에 대한 입력으로 사용하려면 필드를 비워 둡니다. 지정된 JSON 파일에서 특정 JSON 개체를 서비스 인수에 대한 입력으로 읽으려면 JSON 개체에 점 표기법을 지정합니다. 예를 들어, 섹션 시작 부분에 나열된 JSON과 유사한 JSON이 있는 경우 insurance.customerDetails를 지정하여 서비스에 대한 입력으로 고객의 모든 세부 정보를 제공합니다.
* **서비스 출력 > 메타데이터에 출력 값 매핑 및 쓰기:** 출력 값을 crx-repository에 있는 워크플로우 인스턴스 메타데이터 노드의 속성으로 저장하는 옵션을 선택합니다. 메타데이터 속성의 이름을 지정하고 메타데이터 속성과 매핑할 해당 서비스 출력 속성을 선택합니다. 예를 들어 출력 서비스에서 반환한 phone_number 속성을 워크플로우 메타데이터의 phone_number 속성에 매핑합니다.
* **서비스 출력 > 출력을 JSON으로 저장:** 옵션을 선택하여 출력 값을 JSON 파일에 저장합니다.
* **출력 JSON 파일 경로:** 출력 JSON 파일을 저장하는 경로입니다. 출력 JSON 파일의 경로는 페이로드 또는 절대 경로를 기준으로 할 수 있습니다.

## 문서 서명 단계 {#sign-document-step}

문서 서명 단계에서는 Acrobat Sign을 사용하여 문서에 서명할 수 있습니다. 문서 서명 단계에는 다음 속성이 있습니다.

* **계약 이름:** 계약의 제목을 지정합니다. 계약 이름은 서명자에게 보내는 전자 메일의 제목 및 본문 텍스트의 일부가 됩니다.
* **로케일:** 전자 메일 및 확인 옵션에 대한 언어를 지정합니다.
* **Acrobat Sign Cloud 구성**: Acrobat Sign 클라우드 구성을 선택합니다. AEM Forms용 Acrobat Sign을 구성하지 않은 경우 [Acrobat Sign과 AEM Forms 통합](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **서명할 문서:** 페이로드를 기준으로 한 위치에서 문서를 선택하거나, 페이로드를 문서로 사용하거나, 문서의 절대 경로를 지정할 수 있습니다.
* **입력 첨부 경로:** 첨부 파일을 선택합니다. 이러한 첨부 파일은 서명 문서에 포함되어 있습니다. 첨부 파일을 페이로드에 대해 위치에 유지하거나 첨부 파일의 절대 경로를 지정할 수 있습니다.

   첨부 파일 등의 폴더 경로를 지정하면 폴더에서 직접 사용할 수 있는 모든 파일이 레코드 문서에 첨부됩니다. 지정된 첨부 경로에서 직접 사용할 수 있는 폴더에서 사용할 수 있는 파일이 있으면 해당 파일은 첨부 파일로 문서에 포함됩니다. 직접 사용 가능한 폴더에 폴더가 있으면 건너뜁니다.
* **마감일까지 일수:** 작업에서 지정한 일 수 동안 작업이 없으면 문서가 기한(전달된 기간)으로 표시됩니다. **마감일까지 일수** 필드. 문서화된 항목이 서명을 위해 사용자에게 지정된 후 일 수가 계산됩니다.

* **미리 알림 전자 메일 빈도:** 매일 또는 주별 간격으로 미리 알림 이메일을 보낼 수 있습니다. 이 주는 서명을 위해 사용자에게 문서화된 항목이 지정된 날짜부터 계산됩니다.
* **서명 프로세스:** 순차 또는 병렬 순서로 문서에 서명하도록 선택할 수 있습니다. 순차적으로, 한 서명자가 서명할 때 문서를 수신합니다. 첫 번째 서명자가 문서 서명을 완료하면 문서가 두 번째 서명자에게 보내지는 등의 작업을 수행합니다. 동시에 여러 서명자가 한 번에 문서에 서명할 수 있습니다.

* **리디렉션 URL:** 리디렉션 URL을 지정합니다. 문서가 서명되면 할당자를 URL로 리디렉션할 수 있습니다. 일반적으로 이 URL에는 감사 메시지나 추가 지침이 포함되어 있습니다.
* **워크플로우 단계:** 워크플로우에는 여러 단계가 있을 수 있습니다. 이러한 단계는 AEM 받은 편지함에 표시됩니다. 모델의 속성(사이드 킥과 페이지 > 페이지 속성 > 단계)에서 이러한 단계를 정의할 수 있습니다.
* **서명자 선택:** 문서의 서명자를 선택하는 방법을 지정합니다. 워크플로우를 사용자나 그룹에 동적으로 할당하거나 서명자의 세부 사항을 수동으로 추가할 수 있습니다.
* **서명자를 선택하는 스크립트 또는 서비스:** 이 옵션은 서명자 선택 필드에서 동적으로 옵션을 선택한 경우에만 사용할 수 있습니다. ECMAScript 또는 서비스를 지정하여 문서에 대한 서명자 및 확인 옵션을 선택할 수 있습니다.

* **서명자 세부 정보:** 서명자 선택 필드에서 수동 옵션을 선택한 경우에만 옵션을 사용할 수 있습니다. 이메일 주소를 지정하고 선택적 확인 메커니즘을 선택합니다. 2단계 확인 메커니즘을 선택하기 전에 구성된 Acrobat Sign 계정에 대해 해당 확인 옵션이 활성화되어 있는지 확인하십시오.
* **상태 변수:** Acrobat Sign이 활성화된 문서는 문서의 서명 상태를 변수에 저장합니다. 상태 변수의 이름을 지정합니다(adobeSignStatus). 인스턴스의 상태 변수는 /etc/workflow/instances/ 의 CRXDE에서 사용할 수 있습니다.&lt;server>/&lt;date-time>/&lt;instance of=&quot;&quot; workflow=&quot;&quot; model=&quot;&quot;>/workItems/&lt;node>/metaData에 변수의 상태가 포함되어 있습니다.
* **서명된 문서 경로:** 서명된 문서를 보관할 위치를 지정합니다. 페이로드 파일을 덮어쓰거나 서명된 문서를 페이로드 디렉토리 내의 위치에 배치할 수 있습니다.

## 문서 서비스 단계 {#document-services-steps}

AEM 문서 서비스는 PDF 문서를 작성, 조립 및 보호하기 위한 서비스 세트입니다. AEM Forms은 각 문서 서비스에 대해 별도의 AEM 워크플로우 단계를 제공합니다.

### 문서 타임스탬프 적용 단계 {#apply-document-time-stamp-step}

문서에 타임스탬프를 추가합니다. 입력 문서 경로, 입력 문서 이름, 내보낸 데이터를 저장할 위치 등의 문서 세부 정보를 제공합니다. 기존 페이로드 파일을 덮어쓰거나 다른 파일 이름을 선택하여 페이로드 폴더 아래의 다른 파일에 데이터를 저장할 수 있습니다.

### 이미지로 변환 단계 {#convert-to-image-step}

PDF 문서를 이미지 파일로 변환합니다. 지원되는 이미지 형식은 JPEG, JPEG2000, PNG 및 TIFF입니다. 다음 정보는 TIFF 이미지에 대한 전환에 적용됩니다.

* 다중 페이지 TIFF 파일이 생성됩니다.
* 일부 주석은 TIFF 이미지에 포함되지 않습니다. Acrobat에서 모양을 생성해야 하는 주석은 포함되지 않습니다.

### PDF/A 단계로 변환 {#convert-to-pdf-a-step}

제공된 옵션을 사용하여 PDF 문서를 PDF/A 형식으로 변환합니다. Portable Document Format(PDF)의 PDF/A 버전은 문서의 보관 및 장기 보관을 위해 전문화되어 있습니다.

### PS로 변환 단계 {#convert-to-ps-step}

PDF 문서를 PostScript로 변환합니다. PostScript로 변환할 때 변환 작업을 사용하여 소스 문서와 PostScript 수준 2 또는 3으로 변환할지 여부를 지정할 수 있습니다. PostScript 파일로 변환하는 PDF 문서는 비대화형 문서여야 합니다.

### 지정된 유형 단계에서 PDF 만들기 {#create-pdf-from-specified-type-step}

입력 파일에서 PDF 문서를 생성합니다. 입력 문서는 페이로드를 기준으로 하거나, 절대 경로를 사용하거나, 페이로드 자체일 수 있습니다.

### URL/HTML/ZIP 단계에서 PDF 만들기 {#create-pdf-from-url-html-zip-step}

제공된 URL, HTML 및 ZIP 파일에서 PDF 문서를 생성합니다.

### 데이터 내보내기 단계 {#export-data-step}

PDF forms 또는 XDP 파일에서 데이터를 내보냅니다. 입력 문서의 파일 경로와 데이터 내보내기 형식을 입력해야 합니다. 데이터 형식 내보내기 옵션은 자동, XDP 및 XmlData입니다.

### 지정된 유형 단계로 Export PDF {#export-pdf-to-specified-type-step}

PDF 문서를 선택한 형식으로 변환합니다.

### 비대화형 PDF 단계 생성 {#generate-non-interactive-pdf-step}

비대화형 PDF 생성. 다양한 사용자 지정 옵션을 제공합니다.

### 데이터 가져오기 단계 {#import-data-step}

양식 데이터를 PDF 양식에 병합합니다. 양식 데이터를 PDF 양식으로 가져올 수 있습니다.

### DDX 단계 호출 {#invoke-ddx-step}

지정된 입력 문서 맵에서 DDX 파일을 실행하고 조작된 PDF 문서를 반환합니다.

### Optimize PDF 단계 {#optimize-pdf-step}

크기를 줄여 PDF 파일을 최적화합니다. 이렇게 변환하면 원래 버전보다 작을 수 있는 PDF 파일이 생성됩니다. 또한 이 작업은 PDF 문서를 최적화 매개 변수에 지정된 PDF 버전으로 변환합니다.

최적화 설정은 파일의 최적화 방법을 지정합니다. 다음은 설정 예입니다.

* Target PDF 버전
* JavaScript 작업 및 포함된 페이지 축소판과 같은 개체 삭제
* 주석 및 파일 첨부 파일과 같은 사용자 데이터 삭제
* 잘못되었거나 사용하지 않은 설정을 삭제하는 중입니다.
* 압축되지 않은 데이터 압축 또는 보다 효율적인 압축 알고리즘 사용
* 포함된 글꼴 제거
* 투명도 값 설정

### 렌더링 PDF 양식 단계 {#render-pdf-form-step}

XDP(양식 디자이너)에서 만든 양식을 PDF 양식으로 렌더링합니다.

### 보안 문서 단계 {#secure-document-step}

문서 암호화, 서명 및 인증 AEM Forms은 암호 기반 암호와 인증서 기반 암호화를 모두 지원합니다. 문서 서명을 위한 다양한 알고리즘 중에서 선택할 수도 있습니다. 예를 들어 SHA-256 및 SH-512입니다. 워크플로우 단계를 사용하여 PDF 문서를 읽을 수도 있습니다. 워크플로우 단계에서는 바코드 디코딩, 디지털 서명, PDF 데이터 가져오기 및 내보내기 및 기타 옵션을 사용할 수 있는 옵션을 제공합니다.

### 프린터로 보내기 단계 {#send-to-printer-step}

프린터로 직접 문서를 보냅니다. 다음과 같은 인쇄 액세스 메커니즘을 지원합니다.

* **직접 액세스 가능한 프린터**: 동일한 컴퓨터에 설치된 프린터를 직접 액세스 가능한 프린터라고 하며, 컴퓨터의 이름을 프린터 호스트라고 합니다. 이 유형의 프린터는 컴퓨터에 직접 연결된 로컬 프린터일 수 있습니다.
* **간접 액세스 가능한 프린터**: 인쇄 서버에 설치된 프린터는 다른 컴퓨터에서 액세스할 수 있습니다. UNIX® 인쇄 시스템(CUMPS) 및 LPD(Line Printer Daemon) 프로토콜과 같은 기술은 네트워크 프린터에 연결할 수 있습니다. 간접 액세스 가능한 프린터에 액세스하려면 인쇄 서버의 IP 또는 호스트 이름을 지정합니다. 이 메커니즘을 사용하면 네트워크에 LPD가 실행 중인 경우 LPD URI로 문서를 보낼 수 있습니다. 이 메커니즘을 사용하면 LPD가 실행 중인 네트워크에 연결된 프린터로 문서를 라우팅할 수 있습니다.
