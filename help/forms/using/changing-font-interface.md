---
title: 인터페이스에서 글꼴 변경
seo-title: 인터페이스에서 글꼴 변경
description: 사용자 인터페이스에서 선택적으로 글꼴을 변경하는 방법입니다.
seo-description: 사용자 인터페이스에서 선택적으로 글꼴을 변경하는 방법입니다.
uuid: d079f656-76f8-4908-9989-dde79e215eb2
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 487e3966-443a-408e-b5af-899fcba6fca6
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 1%

---


# {#changing-the-font-on-the-interface} 인터페이스의 글꼴 변경

AEM Forms 작업 영역에 표시되는 글꼴을 변경할 수 있습니다. 사용자 인터페이스의 특정 섹션에 사용되는 글꼴은 스타일 시트의 해당 섹션에 정의됩니다. 사용자 인터페이스에서 선택적으로 글꼴을 변경할 수 있습니다.

AEM Forms 작업 영역 사용자 지정을 위한 [일반 단계를 따르고 요구 사항에 따라 CSS, HTML 또는 둘 다를 사용자 정의하는 단계를 따릅니다.](/help/forms/using/generic-steps-html-workspace-customization.md)

1. 기존 스타일로 글꼴 모음을 변경하거나 추가합니다.
1. HTML 요소에 대한 글꼴 모음 인라인을 변경하거나 추가합니다.
1. 스타일을 추가하고 HTML 요소에 사용합니다.

예를 들어 위쪽 내비게이션 막대 앵커 텍스트의 글꼴을 Courier New로 변경하려면 다음 단계를 따르십시오.

1. `https://[server]:[port]/lc/crx/de/index.jsp`에 액세스하여 CRXDE Lite에 로그인합니다.
1. 다음 중 하나를 수행하십시오.

   1. 기존 스타일에서 글꼴 모음을 변경하려면 /apps/ws/css의 newStyle.css 파일에 다음 내용을 추가합니다.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. HTML 요소에 대한 글꼴 모음 인라인을 추가하려면 `/libs/ws/js/runtime/templates/appnavigation.html` 파일을 `/apps/ws/js/runtime/templates/appnavigation.html`에 복사합니다.

      다음과 같이 /apps/ws/js/runtime/templates/appnavigation.html 파일을 업데이트합니다.

      ```
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      편집할 /apps/ws/js/registry.js 파일을 열고 `text!/lc/libs/ws/js/runtime/templates/appnavigation.html`을(를) `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`(으)로 바꿉니다.

   1. font-family를 정의하는 스타일을 추가하려면 /apps/ws/css의 newStyle.css 파일에 다음을 추가하십시오.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      HTML 요소에 대한 글꼴 모음 인라인을 추가하려면 /apps/ws/js/runtime/templates의 appnavigation.html 파일에 다음 내용을 추가하십시오.

      ```css
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. 작업 영역을 다시 실행하고 변경 사항이 표시되도록 브라우저 캐시를 지웁니다.

![change_font_](assets/change_font_before.png)
**beforeFigure:** *글꼴 사용자 정의 전 위쪽 내비게이션 막대*

![change_font_](assets/change_font_after.png)
**afterFigure:** *첫 번째 탭의 글꼴 사용자 정의 후 위쪽 내비게이션 막대*
