---
title: 설명서에 대한 링크 업데이트
seo-title: Updating the link to the documentation
description: AEM Forms 작업 공간에서 Workspace 도움말 링크의 대상을 업데이트하여 사용자 지정 설명서 링크를 가리키는 방법
seo-description: How-to update the destination of Workspace Help link in AEM Forms workspace to point to your custom documentation link.
uuid: 64056d10-1451-44ed-8f25-81a21037dc75
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 788c427f-190f-4580-9efd-6a4c4a008837
exl-id: 68fe3f97-ded8-4223-b4b9-02704077e37e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 7%

---

# 설명서에 대한 링크 업데이트 {#updating-the-link-to-the-documentation}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 작업 공간의 기본 도움말 콘텐츠에 액세스하려면 **도움말 > 작업 공간 도움말**. Adobe 웹 사이트의 온라인 설명서를 가리킵니다. 그러나 다른 URL을 가리키도록 업데이트할 수 있습니다.

기본 도움말 URL을 변경할 수 있는 다음 사용 사례를 고려하십시오.

* 원하는 언어로 현지화된 도움말 제공
* 사용자 지정된 작업 공간에 대한 사용자 지정 도움말 컨텐츠를 제공하는 경우.

온라인 설명서의 URL을 업데이트하려면 [사용자 지정의 일반 단계](/help/forms/using/generic-steps-html-workspace-customization.md) 그리고 다음 단계를 수행합니다.

1. 를 복사합니다. `userinfo.html` 파일 위치 `/libs/ws/js/runtime/templates` to `/apps/ws/js/runtime/templates`.
1. 변경:

   ```
   <ul class="helpmenu">
     <li>            
       <a href="https://www.adobe.com/go/learn_aemforms_documentation_63" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

   끝

   ```
   <ul class="helpmenu">
     <li>            
       <a href="<!--place new help url here-->" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

1. 다음 작업을 수행합니다.

   1. /apps/ws/js/registry.js 을 열어 편집합니다.
   1. 검색 및 바꾸기 `text!/lc/libs/ws/js/runtime/templates/userinfo.html` with `text!/lc/apps/ws/js/runtime/templates/userinfo.html`.
