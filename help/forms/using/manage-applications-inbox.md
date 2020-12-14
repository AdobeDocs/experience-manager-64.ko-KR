---
title: AEM 받은 편지함에서 Forms 애플리케이션 및 작업 관리
seo-title: AEM 받은 편지함에서 Forms 애플리케이션 및 작업 관리
description: AEM 받은 편지함을 통해 애플리케이션을 제출하고 작업을 관리하여 Forms 중심의 워크플로우를 실행할 수 있습니다.
seo-description: AEM 받은 편지함을 통해 애플리케이션을 제출하고 작업을 관리하여 Forms 중심의 워크플로우를 실행할 수 있습니다.
uuid: 5173558a-542a-4130-8bb6-5ac555ecc507
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: document_services, publish
discoiquuid: c1515c58-7d9a-4a36-9390-f6d6b980b801
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 1%

---


# AEM 받은 편지함에서 Forms 응용 프로그램 및 작업 관리 {#manage-forms-applications-and-tasks-in-aem-inbox}

AEM Inbox의 애플리케이션을 통해 Forms 중심의 워크플로우를 시작하거나 트리거하는 다양한 방법 중 하나를 사용할 수 있습니다. 받은 편지함에서 Forms 워크플로우를 애플리케이션으로 사용하려면 워크플로우 애플리케이션을 만들어야 합니다. 워크플로우 응용 프로그램 및 기타 Forms 워크플로우 실행 방법에 대한 자세한 내용은 [OSGi](/help/forms/using/aem-forms-workflow.md#launch)에서 Forms 중심의 워크플로우 시작을 참조하십시오.

또한 AEM Inbox는 Forms 워크플로우를 비롯한 다양한 AEM 구성 요소의 알림 및 작업을 통합합니다. 할당 작업 단계가 포함된 양식 워크플로우가 트리거되면 연결된 애플리케이션이 할당자의 받은 편지함에 작업으로 나열됩니다. 할당자가 그룹인 경우 개별 요청이나 위임이 있을 때까지 해당 작업은 모든 그룹 구성원의 받은 편지함에 나타납니다.

받은 편지함 사용자 인터페이스는 작업을 볼 수 있는 목록 및 달력 보기를 제공합니다. 보기 설정을 구성할 수도 있습니다. 다양한 매개 변수를 기반으로 작업을 필터링할 수 있습니다. 보기 및 필터에 대한 자세한 내용은 [받은 편지함](/help/sites-authoring/inbox.md)을 참조하십시오.

요약하면 받은 편지함을 사용하여 새 응용 프로그램을 만들고 할당된 작업을 관리할 수 있습니다.

>[!NOTE]
>
>AEM 받은 편지함을 사용할 수 있으려면 Workflow-users 그룹의 구성원이어야 합니다.

## 응용 프로그램 {#create-application} 만들기

1. `https://[server]:[port]/aem/inbox`의 AEM 받은 편지함으로 이동합니다.
1. 받은 편지함 UI에서 **[!UICONTROL 만들기 > 응용 프로그램]**&#x200B;을 탭합니다. 애플리케이션 선택 페이지가 나타납니다.
1. 응용 프로그램을 선택하고 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 응용 프로그램과 연결된 응용 양식이 열립니다. 양식을 채우고 **[!UICONTROL 제출]**&#x200B;을 누릅니다. 연결된 워크플로우를 실행하고 할당자의 받은 편지함에 작업을 만듭니다.

## 작업 관리 {#manage-tasks}

Forms 워크플로우가 트리거되고 사용자가 할당자 그룹의 할당자 또는 일부일 경우 작업이 받은 편지함에 나타납니다. 받은 편지함 내에서 작업 세부 사항을 보고 작업에 사용 가능한 작업을 수행할 수 있습니다.

### 작업 {#claim-or-delegate-tasks} 요청 또는 위임

그룹에 할당된 작업은 모든 그룹 구성원의 받은 편지함에 나타납니다. 모든 그룹 구성원은 해당 작업을 요청하거나 다른 그룹 구성원에게 위임할 수 있습니다. 이렇게 하려면 다음을 수행하십시오.

1. 을 눌러 작업 축소판을 선택합니다. 작업을 열거나 위임하는 옵션이 맨 위에 표시됩니다.

   ![select-task](assets/select-task.png)

1. 다음 중 하나를 수행하십시오.

   * 작업을 위임하려면 **[!UICONTROL 위임]**&#x200B;을 탭합니다. 위임 항목 대화 상자가 열립니다. 사용자를 선택하고 필요에 따라 주석을 추가한 다음 **[!UICONTROL OK]**&#x200B;을 누릅니다.

   ![위임](assets/delegate.png)

   * 작업을 요청하려면 **[!UICONTROL 열기]**&#x200B;를 누릅니다. 자체 할당 대화 상자가 열립니다. 작업을 요청하려면 **[!UICONTROL 계속]**&#x200B;을 누릅니다. 요청된 작업이 받은 편지함에 할당자로 표시됩니다.

   ![청구](assets/claim.png)

### 세부 사항 보기 및 작업 수행 {#view-details-and-perform-actions-on-tasks}

작업을 열면 작업 세부 사항을 보고 사용 가능한 작업을 수행할 수 있습니다. 작업에 사용할 수 있는 작업은 연결된 Forms 워크플로우의 [할당] 작업 단계에서 정의됩니다.

1. 을 눌러 작업 축소판을 선택합니다. 선택한 작업을 열거나 위임하는 옵션이 맨 위에 표시됩니다.
1. **[!UICONTROL 열기]**&#x200B;를 눌러 작업 세부 사항을 보고 작업을 수행합니다. 세부 작업 보기가 열립니다. 이 보기에서 작업 세부 사항을 보고 작업에 대해 작업을 수행할 수 있습니다.

   >[!NOTE]
   >
   >작업이 그룹에 할당된 경우 세부 보기에서 해당 작업을 열 수 있도록 요청해야 합니다.

![작업 세부 사항](assets/task-details.png)

세부 작업 보기는 다음 섹션으로 구성됩니다.

* 작업 세부 사항
* 양식
* 워크플로우 세부 정보
* 작업 도구 모음

#### 작업 세부 정보 {#task-details}

작업 세부 사항 섹션에는 작업에 대한 정보가 표시됩니다. 표시되는 정보는 워크플로우에서 [할당 작업 단계](/help/sites-developing/workflows-step-ref.md)의 구성 설정에 따라 다릅니다. 위의 예는 작업에 사용된 설명, 상태, 시작 날짜 및 워크플로우를 표시합니다. 또한 작업에 파일을 첨부할 수도 있습니다.

#### 양식 {#form}

기본 컨텐츠 영역의 양식 탭에는 제출된 양식과 필드 수준 첨부 파일이 있을 경우 해당 파일이 표시됩니다.

#### 워크플로우 세부 정보 {#workflow-details}

맨 위의 [워크플로우 세부 사항] 탭에는 워크플로우의 다양한 단계를 통한 작업의 진행 상태가 표시됩니다. 작업에 대한 완료, 현재 및 보류 중인 단계가 표시됩니다. 워크플로우의 단계는 연관된 워크플로우의 [작업 지정 단계](/help/sites-developing/workflows-step-ref.md)에 정의됩니다.

또한 워크플로우에서 완료된 각 단계에 대한 작업 내역도 표시됩니다. 완료된 스테이지에 대해 **[!UICONTROL 세부 사항 보기]**&#x200B;를 탭하여 해당 스테이지에 대한 세부 사항을 알 수 있습니다. 작업에 대한 주석, 양식 및 작업 첨부 파일, 상태, 시작 및 종료 날짜 등이 표시됩니다.

![workflow details](assets/workflow-details.png)

#### 작업 도구 모음 {#actions-toolbar}

작업 도구 모음에는 작업에 사용할 수 있는 모든 옵션이 표시됩니다. 저장, 재설정 및 위임은 기본 작업이지만 다른 사용 가능한 작업은 [할당 작업 단계](/help/sites-developing/workflows-step-ref.md)에서 구성됩니다. 위의 예에서, 승인 및 거부는 워크플로우에 구성됩니다.

작업에 대해 조치를 취하면 워크플로우에서 계속 진행합니다.

### 완료된 작업 보기 {#view-completed-tasks}

AEM 받은 편지함은 활성 작업만 표시합니다. 완료된 작업은 목록에 표시되지 않습니다. 그러나 받은 편지함 필터를 사용하여 작업 유형, 상태, 시작 날짜 및 종료 날짜 등과 같은 여러 매개 변수를 기준으로 작업을 필터링할 수 있습니다. 완료된 작업을 보려면

1. AEM 받은 편지함에서 ![toggle-side-panel1](assets/toggle-side-panel1.png)을 눌러 필터 선택기를 엽니다.
1. **[!UICONTROL 작업 상태]** 아코디언을 누르고 **[!UICONTROL 완료]**&#x200B;를 선택합니다. 완료된 모든 작업이 표시됩니다.

   ![filter-1](assets/filter-1.png)

1. 을 눌러 작업을 선택하고 **[!UICONTROL 열기]**&#x200B;를 클릭합니다.

작업이 열리고 작업과 연관된 문서 또는 적응형 양식이 표시됩니다. 적응형 양식의 경우 [작업 할당 워크플로우 단계](/help/sites-developing/workflows-step-ref.md)의 양식/문서 탭에 구성된 대로 읽기 전용 적응형 양식 또는 해당 PDF 레코드 문서가 표시됩니다.

작업 세부 사항 섹션에는 수행한 작업, 작업 상태, 시작 날짜 및 종료 날짜와 같은 정보가 표시됩니다.

![완료된 작업](assets/completed-task.png)

**[!UICONTROL 워크플로우 세부 사항]** 탭에는 워크플로우의 각 단계가 표시됩니다. 자세한 내용을 보려면 **[!UICONTROL 세부 사항 보기]**&#x200B;를 누릅니다.

![completed-task-workflow](assets/completed-task-workflow.png)

