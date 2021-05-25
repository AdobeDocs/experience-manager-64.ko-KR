---
title: ToDo 목록에 추가 데이터 표시
seo-title: ToDo 목록에 추가 데이터 표시
description: AEM Forms 작업 공간 의 할 일 목록 표시를 사용자 지정하여 기본 정보 외에 자세한 정보를 표시하는 방법
seo-description: AEM Forms 작업 공간 의 할 일 목록 표시를 사용자 지정하여 기본 정보 외에 자세한 정보를 표시하는 방법
uuid: 4c678d9c-7794-4b62-8705-d62c7780c13f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b74a0933-2b96-4a88-9995-6fb21df141aa
exl-id: 42d8472d-0eab-4cf9-a7c3-bf2775ee6bec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# ToDo 목록에 추가 데이터 표시 {#displaying-additional-data-in-todo-list}

기본적으로 AEM Forms 작업 영역 할 일 목록에는 작업 표시 이름과 설명이 표시됩니다. 그러나 만든 날짜, 기한 날짜와 같은 다른 정보를 추가할 수 있습니다. 아이콘을 추가하고 디스플레이 스타일을 변경할 수도 있습니다.

![기본 구성을 보여주는 HTML 작업 공간 할 일 탭 보기](assets/html-todo-list.png)

이 문서에서는 ToDo 목록에 각 작업에 대해 표시할 정보를 추가하는 단계에 대해 자세히 설명합니다.

## {#what-can-be-added}을 추가할 수 있는 항목

서버에서 보낸 `task.json`에 사용 가능한 정보를 추가할 수 있습니다. 정보를 일반 텍스트로 추가하거나 스타일을 사용하여 정보 서식을 지정할 수 있습니다.

JSON 개체 설명에 대한 자세한 내용은 [이](/help/forms/using/html-workspace-json-object-description.md) 문서를 참조하십시오.

## 작업 {#displaying-information-on-a-task}에 정보 표시

1. AEM Forms 작업 공간 사용자 지정에 대한 [일반 절차](/help/forms/using/generic-steps-html-workspace-customization.md)를 따르십시오.
1. 작업에 대한 추가 정보를 표시하려면 `translation.json` 작업 블록 내에 해당 키-값 쌍을 추가해야 합니다.

   예를 들어, 영어 `/apps/ws/locales/en-US/translation.json` 변경:

   ```
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >지원되는 모든 언어에 해당하는 키-값 쌍을 추가합니다.

1. 예를 들어 작업 블록 내에 정보를 추가합니다.

   ```
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## 새 속성 {#defining-css-for-the-new-property}에 대한 CSS 정의

1. 작업에 추가된 정보(속성)에 스타일을 적용할 수 있습니다. 이렇게 하려면 `/apps/ws/css/newStyle.css`에 추가된 새 속성에 대한 스타일 정보를 추가해야 합니다.

   예를 들어 추가:

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## HTML 템플릿에 항목 추가 {#adding-entry-in-the-html-template}

마지막으로 작업에 추가할 각 속성에 대한 개발 패키지에 항목을 포함해야 합니다. 만들려면 AEM Forms 작업 공간 코드 작성 을 참조하십시오.

1. 복사 `task.html`:

   * 시작: `/libs/ws/js/runtime/templates/`
   * 끝: `/apps/ws/js/runtime/templates/`

1. 새 정보를 `/apps/ws/js/runtime/templates/task.html`에 추가합니다.

   예를 들어 `div class="taskProperties"` 아래에 를 추가합니다.

   ```
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```
