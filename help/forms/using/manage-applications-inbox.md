---
title: AEM 받은 편지함에서 Forms 애플리케이션 및 작업 관리
seo-title: Manage Forms applications and tasks in AEM Inbox
description: AEM 받은 편지함을 사용하면 애플리케이션 제출 및 작업 관리를 통해 Forms 중심의 워크플로우를 시작할 수 있습니다.
seo-description: AEM Inbox allows you to launch Forms-centric workflows through submitting applications and manage tasks.
uuid: 5173558a-542a-4130-8bb6-5ac555ecc507
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: document_services, publish
discoiquuid: c1515c58-7d9a-4a36-9390-f6d6b980b801
exl-id: 7076807a-40ad-4f3b-beb0-70c1577a8ee7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 2%

---

# AEM 받은 편지함에서 Forms 애플리케이션 및 작업 관리 {#manage-forms-applications-and-tasks-in-aem-inbox}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Forms 중심 워크플로우를 시작하거나 트리거하는 여러 방법 중 하나는 AEM 받은 편지함의 애플리케이션을 통해 입니다. Forms 워크플로우를 받은 편지함에서 애플리케이션으로 사용할 수 있게 하려면 워크플로우 애플리케이션을 만들어야 합니다. 워크플로우 애플리케이션 및 Forms 워크플로우를 시작하는 기타 방법에 대한 자세한 내용은 [OSGi에서 Forms 중심의 워크플로우 시작](/help/forms/using/aem-forms-workflow.md#launch).

또한 AEM 받은 편지함 에서는 Forms 워크플로우를 비롯한 다양한 AEM 구성 요소의 알림과 작업을 통합합니다. 작업 할당 단계를 포함하는 양식 워크플로우가 트리거되면 연관된 응용 프로그램이 할당자의 받은 편지함에서 작업으로 나열됩니다. 할당자가 그룹인 경우 개별 요청이나 위임을 받을 때까지 모든 그룹 구성원의 받은 편지함에 작업이 나타납니다.

받은 편지함 사용자 인터페이스에서는 작업을 볼 수 있는 목록 및 달력 보기를 제공합니다. 보기 설정을 구성할 수도 있습니다. 다양한 매개 변수를 기반으로 작업을 필터링할 수 있습니다. 보기 및 필터에 대한 자세한 내용은 [받은 편지함](/help/sites-authoring/inbox.md).

요약하면 받은 편지함에서 새 응용 프로그램을 만들고 할당된 작업을 관리할 수 있습니다.

>[!NOTE]
>
>AEM 받은 편지함을 사용하려면 workflow-users 그룹의 구성원이어야 합니다.

## 애플리케이션 만들기 {#create-application}

1. 의 AEM 받은 편지함으로 이동합니다. `https://[server]:[port]/aem/inbox`.
1. 받은 편지함 UI에서 **[!UICONTROL 만들기 > 애플리케이션]**. [응용 프로그램 선택] 페이지가 나타납니다.
1. 응용 프로그램을 선택하고 **[!UICONTROL 만들기]**. 응용 프로그램과 연결된 응용 양식이 열립니다. 양식을 작성하고 탭 **[!UICONTROL 제출]**. 연결된 워크플로우를 시작하고 할당자의 받은 편지함에서 작업을 만듭니다.

## 작업 관리 {#manage-tasks}

Forms 워크플로우가 트리거되고 사용자가 할당자 또는 할당자 그룹의 일부인 경우 작업이 받은 편지함에 나타납니다. 받은 편지함 내에서 작업 세부 사항을 보고 작업에 사용 가능한 작업을 수행할 수 있습니다.

### 청구 또는 위임 작업 {#claim-or-delegate-tasks}

그룹에 할당된 작업은 모든 그룹 구성원의 받은 편지함에 나타납니다. 모든 그룹 구성원이 해당 작업을 요청하거나 다른 그룹 구성원에게 위임할 수 있습니다. 방법은 다음과 같습니다.

1. 을 눌러 작업 축소판을 선택합니다. 작업을 열거나 위임하는 옵션이 맨 위에 나타납니다.

   ![select-task](assets/select-task.png)

1. 다음 중 하나를 수행하십시오.

   * 작업을 위임하려면 **[!UICONTROL 위임]**. [항목 위임] 대화 상자가 열립니다. 사용자를 선택하고 필요에 따라 주석을 추가한 다음 **[!UICONTROL 확인]**.

   ![위임](assets/delegate.png)

   * 작업을 요청하려면 **[!UICONTROL 열기]**. 자체 할당 대화 상자가 열립니다. 탭 **[!UICONTROL 계속]** 작업 요청 요청된 작업이 받은 편지함에 할당자로 나타납니다.

   ![청구](assets/claim.png)

### 세부 사항 보기 및 작업에 대한 작업 수행 {#view-details-and-perform-actions-on-tasks}

작업을 열면 작업 세부 사항을 보고 사용 가능한 작업을 수행할 수 있습니다. 작업에 사용할 수 있는 작업은 연결된 Forms 워크플로우의 지정 작업 단계에서 정의됩니다.

1. 을 눌러 작업 축소판을 선택합니다. 선택한 작업을 열거나 위임하는 옵션이 맨 위에 나타납니다.
1. 탭 **[!UICONTROL 열기]** 작업 세부 사항을 보고 작업을 수행하십시오. 세부 작업 보기가 열립니다. 이 보기에서 작업 세부 사항을 보고 작업에 대해 작업을 수행할 수 있습니다.

   >[!NOTE]
   >
   >작업이 그룹에 할당되어 있는 경우 해당 작업을 세부 보기에서 열 수 있도록 요청해야 합니다.

![작업 세부 사항](assets/task-details.png)

세부 작업 보기는 다음 섹션으로 구성됩니다.

* 작업 세부 정보
* 양식
* 워크플로우 세부 정보
* 작업 도구 모음

#### 작업 세부 정보 {#task-details}

작업 세부 정보 섹션에는 작업에 대한 정보가 표시됩니다. 표시되는 정보는 [작업 단계 할당](/help/sites-developing/workflows-step-ref.md) 을 입력합니다. 위의 예에는 작업에 사용된 설명, 상태, 시작 날짜 및 워크플로우가 표시됩니다. 또한 작업에 파일을 첨부할 수도 있습니다.

#### 양식 {#form}

기본 컨텐츠 영역의 양식 탭에는 제출된 양식과 필드 수준 첨부 파일이 있는 경우 표시됩니다.

#### 워크플로우 세부 정보 {#workflow-details}

맨 위에 있는 워크플로우 세부 정보 탭에는 워크플로우의 다양한 단계를 통한 작업 진행 상태가 표시됩니다. 작업에 대한 완료, 현재 및 보류 중인 단계가 표시됩니다. 워크플로우의 단계는 [작업 단계 할당](/help/sites-developing/workflows-step-ref.md) 연결된 워크플로우에 대한 것입니다.

또한 탭에는 워크플로우의 완료된 각 단계에 대한 작업 기록이 표시됩니다. 탭할 수 있습니다 **[!UICONTROL 세부 사항 보기]** 해당 단계에 대한 세부 사항을 알기 위한 단계를 완료했습니다. 작업에 대한 설명, 양식 및 작업 첨부 파일, 상태, 시작 및 종료 날짜 등이 표시됩니다.

![workflow details](assets/workflow-details.png)

#### 작업 도구 모음 {#actions-toolbar}

작업 도구 모음에는 작업에 사용 가능한 모든 옵션이 표시됩니다. 저장, 재설정 및 위임은 기본 작업이지만 사용 가능한 다른 작업은 [작업 단계 할당](/help/sites-developing/workflows-step-ref.md). 위의 예에서 승인 및 거부는 워크플로우에 구성됩니다.

작업에 대해 작업을 수행하면 워크플로우에서 더 진행됩니다.

### 완료된 작업 보기 {#view-completed-tasks}

AEM 받은 편지함은 활성 작업만 표시합니다. 완료된 작업이 목록에 표시되지 않습니다. 그러나 받은 편지함 필터를 사용하여 작업 유형, 상태, 시작 및 종료 날짜 등의 여러 매개 변수를 기반으로 작업을 필터링할 수 있습니다. 완료된 작업을 보려면

1. AEM 받은 편지함에서 ![toggle-side-panel1](assets/toggle-side-panel1.png) 을 눌러 필터 선택기를 엽니다.
1. 탭 **[!UICONTROL 작업 상태]** 아코디언을 선택하고 **[!UICONTROL 완료]**. 완료된 작업이 모두 나타납니다.

   ![filter-1](assets/filter-1.png)

1. 작업을 선택하려면 탭하고 를 클릭합니다 **[!UICONTROL 열기]**.

작업이 열리고 작업과 연관된 적응형 양식이 표시됩니다. 적응형 양식의 경우 창의 양식/문서 탭에 구성된 대로 읽기 전용 적응형 양식 또는 해당 레코드 PDF 문서를 표시합니다 [작업 워크플로우 지정 단계](/help/sites-developing/workflows-step-ref.md).

작업 세부 정보 섹션에는 수행한 작업, 작업 상태, 시작 날짜 및 종료 날짜 등의 정보가 표시됩니다.

![완료 작업](assets/completed-task.png)

다음 **[!UICONTROL 워크플로우 세부 사항]** 탭에는 워크플로우의 각 단계가 표시됩니다. 탭 **[!UICONTROL 세부 사항 보기]** 을 참조하십시오.

![completed-task-workflow](assets/completed-task-workflow.png)
