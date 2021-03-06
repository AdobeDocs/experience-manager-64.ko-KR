---
title: 하나의 서버에서 두 개의 AEM Forms 작업 공간 인스턴스 호스팅
seo-title: 하나의 서버에서 두 개의 AEM Forms 작업 공간 인스턴스 호스팅
description: LC 관리자가 다른 URL을 통해 액세스할 수 있는 단일 서버에서 두 개의 인스턴스를 호스팅하도록 HTML WS를 사용자 지정하는 방법
seo-description: LC 관리자가 다른 URL을 통해 액세스할 수 있는 단일 서버에서 두 개의 인스턴스를 호스팅하도록 HTML WS를 사용자 지정하는 방법
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
exl-id: ef2ad8e1-5007-4587-97ca-cf21070be9a6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 하나의 서버 {#hosting-two-aem-forms-workspace-instances-on-one-server}에서 두 개의 AEM Forms 작업 공간 인스턴스 호스팅

AEM Forms의 기본 설치 및 설정을 사용하면 서버에서 하나의 AEM Forms 작업 영역만 사용할 수 있습니다. 그러나 단일 AEM Forms 서버에 두 개의 서로 다른 AEM Forms 작업 공간 인스턴스를 호스팅해야 할 수 있습니다. 두 인스턴스는 다른 URL에서 액세스할 수 있습니다.

AEM Forms 관리자는 작업 공간을 사용자 지정하여 두 개의 서로 다른 URL을 만들고 두 개의 작업 공간을 동일한 서버에서 사용할 수 있도록 합니다. 이 사용자 지정 문서에서 두 작업 공간은 `https://[server]:[port]/lc/ws` 및 `https://[server]:[port]:/lc/ws2`에서 액세스할 수 있다고 가정합니다.

다음 단계에 따라 AEM Forms 작업 공간을 구성하십시오.

1. 서버에 AEM Forms 작업 공간의 개발 패키지를 설치합니다. 만들기 지침은 [개발 패키지](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p) 를 참조하십시오.
1. `https://[server]:[port]/lc/crx/de/index.jsp`에 액세스하여 관리자로 CRXDE Lite에 로그인합니다.
1. /content에 노드를 복사하여 /content에 붙여넣습니다. 노드 이름을 ws2로 변경합니다. **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다. 이 노드의 속성에서 `sling:resourceType` 값을 ws2로 변경합니다. **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

1. /libs에서 폴더를 복사하여 /apps에 붙여넣습니다. 폴더 이름을 ws2로 변경합니다. **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.
1. `/apps/ws2`의 `GET.jsp`에서 다음 코드를 변경합니다. 다음 내용을 바꿉니다

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" /><html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" />
   ```

   다음 코드와 함께

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. `/apps/ws2/js`에 있는 `registry.js`에서 템플릿의 경로를 `/apps/ws2/js/runtime/templates`에 있는 템플릿을 참조하도록 변경합니다. 다음 코드를 바꿉니다

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/libs/ws/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

   다음 코드와 함께

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/apps/ws2/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

1. `/apps/ws2/js/runtime/models` 및 `/apps/ws2/js/runtime/views`의 `userinfo.js`에서 `/lc/content/ws` 문자열을 `lc/content/ws2` 로 변경합니다.

1. `/apps/ws2/js/runtime/services/service.js`에서 `getLocalizationData` 함수의 경로를 변경하여 `/lc/apps/ws2/Locale.html`를 가리킵니다.

1. 새 작업 영역의 `pdf.html`을 참조하려면 `/apps/ws2/js/runtime/views/forms/pdftaskform.js`에서 `pdf.html`의 경로를 변경합니다.

1. 새 작업 영역의 `pdf.html`을 참조하려면 `startprocess.html`, `taskdetails.html` 및 `processinstancehistory.html`의 경로를 `pdf.html` 및 `WsNextAdapter.swf`에서 변경하십시오(`/apps/ws2/js/runtime/templates`).

1. `/etc/map/ws` 폴더를 복사하여 `/etc/map`에 붙여넣습니다. 새 폴더의 이름을 ws2로 변경합니다. 모두 저장을 클릭합니다.

1. `ws2` 속성에서 `sling:redirect` 값을 `content/ws2` 로 변경합니다.

1. `sling:match` 값을 `^[^/\||]/[^/\||]/ws2$`(으)로 변경합니다.
