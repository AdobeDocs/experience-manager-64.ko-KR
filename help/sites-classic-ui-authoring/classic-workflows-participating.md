---
title: 워크플로에 참여
seo-title: Participating in Workflows
description: 워크플로는 일반적으로 페이지나 에셋에 대해 사람이 활동을 수행해야 하는 단계를 포함합니다. 워크플로는 활동을 수행할 사용자 또는 그룹을 선택하고 해당 개인 또는 그룹에 작업 항목을 지정합니다.
seo-description: Workflows typically include steps that require a person to perform an activity on a page or asset. The workflow selects a user or group to perform the activity and assigns a work item to that person or group.
uuid: 04dcc8f2-dc11-430f-b0ae-47ef2cb069a2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 1d7a4889-82c5-4096-8567-8f66215a8458
exl-id: a4f0f0c4-3050-4348-8d51-2ca91839208c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 30%

---

# 워크플로에 참여{#participating-in-workflows}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

워크플로는 일반적으로 페이지나 에셋에 대해 사람이 활동을 수행해야 하는 단계를 포함합니다. 워크플로는 활동을 수행할 사용자 또는 그룹을 선택하고 해당 개인 또는 그룹에 작업 항목을 지정합니다.

## 작업 항목 처리 {#processing-your-work-items}

다음 작업을 수행하여 작업 항목을 처리할 수 있습니다.

* **완료**

   워크플로가 다음 단계로 진행될 수 있도록 하는 항목을 완료할 수 있습니다.

* **위임**

   단계가 사용자에게 지정되었지만 어떤 이유로든 작업을 수행할 수 없는 경우, 다른 사용자 또는 그룹에 단계를 위임할 수 있습니다.

   위임에 사용할 수 있는 사용자는 작업 항목이 지정된 사람에 따라 다릅니다.

   * 작업 항목이 그룹에 지정된 경우 그룹 구성원을 사용할 수 있습니다.
   * 작업 항목이 그룹에 할당된 후 사용자에게 위임된 경우 그룹 멤버와 그룹을 사용할 수 있습니다.
   * 작업 항목이 단일 사용자에게 지정된 경우 작업 항목을 위임할 수 없습니다.

* **한 단계 뒤로**

   단계 또는 일련의 단계를 반복해야 하는 경우 한 단계로 돌아갈 수 있습니다. 따라서 워크플로에서 이전에 발생한 단계를 선택하여 다시 처리할 수 있습니다. 워크플로가 사용자가 지정한 단계로 돌아가서 그 단계에서부터 진행됩니다.

## 워크플로우에 참여 {#participating-in-a-workflow}

### 지정된 워크플로우 작업 알림 {#notifications-of-assigned-workflow-actions}

작업 항목이 할당되면(예: **콘텐츠 승인**) 다양한 경고 및/또는 알림이 표시됩니다.

* 다음 **상태** 웹 사이트 콘솔의 열은 페이지가 워크플로우에 있을 때를 나타냅니다.

   ![workflstatus-1](assets/workflowstatus-1.png)

* 사용자나 사용자가 속한 그룹이 워크플로우의 일부로 작업 항목이 지정되면 작업 항목이 AEM Workflow 받은 편지함에 나타납니다.

   ![workflinbox](assets/workflowinbox.png)

### 참가자 단계 완료 {#completing-a-participant-step}

표시된 작업을 수행한 후에는 작업 항목을 완료할 수 있으므로 워크플로우가 계속 진행될 수 있습니다. 다음 절차를 사용하여 작업 항목을 완료합니다.

1. 워크플로우 단계를 선택하고 을(를) 클릭합니다. **완료** 상단 탐색 막대의 단추.
1. 결과 대화 상자에서 **다음 단계**; 즉, 다음으로 실행될 단계입니다. 드롭다운 목록에는 모든 적절한 대상이 표시됩니다. A **댓글** 을 입력할 수도 있습니다.

   ![workflowcomplete](assets/workflowcomplete.png)

   나열된 단계 수는 워크플로우 모델의 디자인에 따라 다릅니다.

1. 클릭 **확인** 를 클릭하여 작업을 확인합니다.

### 참가자 단계 위임 {#delegating-a-participant-step}

다음 절차를 사용하여 작업 항목을 위임하십시오.

1. 을(를) 클릭합니다. **위임** 상단 탐색 막대의 단추.
1. 대화 상자에서 드롭다운 목록을 사용하여 **사용자** 작업 항목을 로 위임하려면 다음을 수행합니다. 을(를) 추가할 수도 있습니다 **댓글**.

   ![workdelegate](assets/workflowdelegate.png)

1. 클릭 **확인** 를 클릭하여 작업을 확인합니다.

### 참가자 단계에서 뒤로 이동 수행 {#performing-step-back-on-a-participant-step}

다음 절차를 사용하여 뒤로 이동하십시오.

1. 맨 위 탐색 막대에서 [뒤로 이동] 단추를 클릭합니다.
1. 결과 대화 상자에서 이전 단계를 선택합니다. 즉, 워크플로우에서 이전에 발생하는 단계이지만 다음 단계를 실행하는 단계입니다. 드롭다운 목록에는 모든 적절한 대상이 표시됩니다.

   ![screen_shot_2018-08-10at155325](assets/screen_shot_2018-08-10at155325.jpg)

1. 확인 을 클릭하여 작업을 확인합니다.
