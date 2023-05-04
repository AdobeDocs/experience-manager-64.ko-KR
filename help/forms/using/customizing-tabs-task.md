---
title: 작업에 대한 탭 사용자 정의
seo-title: Customizing tabs for a task
description: AEM Forms 작업 영역에서 작업 탭 이름을 사용자 지정하는 방법
seo-description: How-to customize the names of the tabs for your tasks, in LiveCycle AEM Forms workspace.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
exl-id: 42671435-e0f0-41db-af83-182b01742954
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 5%

---

# 작업에 대한 탭 사용자 정의 {#customizing-tabs-for-a-task}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

에 대한 탭 이름을 사용자 지정할 수 있습니다 `Start Process` 의 구성 요소 `Start Process` Uber 보기 및 `Task Details` 의 구성 요소 `ToDo` Uber 보기.

1. 다음을 수행합니다 [AEM Forms 작업 공간 사용자 지정을 위한 일반 단계](/help/forms/using/generic-steps-html-workspace-customization.md).
1. 값 변경 `tabname`에서 `translation.json` 파일.

   예를 들어, `/apps/ws/locales/en-US/translation.json` 를 사용하여 다음을 수행할 수 있습니다.

   * 시작 프로세스에서 시작된 작업의 경우, `"startprocess" : {}` 차단.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * To-do의 작업에 대해서는 `"todo" : {}` 차단.

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >지원되는 모든 언어에 해당하는 키-값 쌍을 추가합니다.
