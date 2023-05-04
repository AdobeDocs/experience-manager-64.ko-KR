---
title: AEM Forms 작업 공간 사용자 지정을 위한 일반 단계
seo-title: Generic steps for AEM Forms workspace customization
description: AEM Forms 작업 공간 사용자 인터페이스 사용자 지정을 시작하는 방법.
seo-description: How to get started customizing AEM Forms workspace user interface.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
exl-id: 2c0dab68-d77e-46fb-832d-90edea510750
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 4%

---

# AEM Forms 작업 공간 사용자 지정을 위한 일반 단계 {#generic-steps-for-aem-forms-workspace-customization}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

사용자 지정을 수행하는 일반적인 단계는 다음과 같습니다.

1. 에 액세스하여 CRXDE Lite에 로그인합니다. `https://[server]:[port]/lc/crx/de/index.jsp`.
1. 이름이 인 폴더 만들기 `ws`at `/apps`존재하지 않는 경우 해당됩니다. 클릭 **[!UICONTROL 모두 저장]**.
1. 찾아보기 `/apps/ws`로 이동하고 **[!UICONTROL 액세스 제어]** 탭.
1. 에서 **[!UICONTROL 액세스 제어]** 목록, **[!UICONTROL +]** 새 항목을 추가하려면 클릭 **[!UICONTROL +]** 다시 한 번
1. 을(를) 검색하고 선택합니다 **[!UICONTROL PERM_WORKSPACE_USER]** 교장.

   ![Analysis Workspace를 사용자 지정하는 일반 단계의 일부로 PERM_WORKSPACE_USER 주도자를 선택합니다](assets/perm_workspace_user.png)

1. 제공 `jcr:read` Privacy to Principal.
1. 클릭 **[!UICONTROL 모두 저장]**.
1. 를 복사합니다. `GET.jsp` 및 `html.jsp`파일의 `/libs/ws`폴더 `/apps/ws` 폴더를 입력합니다.
1. 를 복사합니다. `/libs/ws/locales` 폴더의 `/apps/ws` 폴더를 입력합니다. 클릭 **[!UICONTROL 모두 저장]**.
1. 에서 참조 및 상대 경로를 업데이트합니다 `GET.jsp` 파일, 아래와 같이 를 클릭하고 **[!UICONTROL 모두 저장]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. CSS 사용자 지정에 대해서는 다음을 수행합니다.

   1. 로 이동합니다 `/apps/ws` 폴더 및 이름이 지정된 새 폴더 만들기 `css`.
   1. 에서 `css`폴더 폴더, 이름이 인 새 파일 만들기 `newStyle.css`.
   1. 열기 `/apps/ws/html`.jsp 및

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   끝

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >위에 표시된 대로 newStyle.css 항목 뒤에 사용자 정의 CSS 파일의 항목을 배치합니다.

1. /apps/ws/html.jsp 파일에서

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   끝

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. 다음 작업을 수행합니다.

   1. 이름이 인 폴더 만들기 `js`at `/apps/ws`. 클릭 **[!UICONTROL 모두 저장]**.
   1. 이름이 인 폴더 만들기 `libs`at `/apps/ws/js`. 클릭 **[!UICONTROL 모두 저장]**.
   1. 이름이 인 폴더 만들기 `jqueryui`at `/apps/ws/js/libs`. 클릭 **[!UICONTROL 모두 저장]**.
   1. 복사 `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` to `/apps/ws/js/libs/jqueryui`. 클릭 **[!UICONTROL 모두 저장]**.

1. HTML 사용자 정의에 대해서는 다음을 수행합니다.

   1. 아래 `/apps/ws/js`, 라는 폴더를 만듭니다. `runtime`. 클릭 **[!UICONTROL 모두 저장]**.
   1. 아래 `/apps/ws/js/runtime`, 라는 폴더를 만듭니다. `templates`. 클릭 **[!UICONTROL 모두 저장]**.
   1. 복사 `/libs/ws/js/main.js` to `/apps/ws/js/main.js`.
   1. /libs/ws/js/registry.js에 복사 `/apps/ws/js/registry.js`.

1. 클릭 **[!UICONTROL 모두 저장]**, 캐시 지우기 및 AEM Forms 작업 공간 새로 고침.

   URL에 액세스 `https://[server]:[port]/lc/ws` 관리자/암호 자격 증명으로 로그인합니다. 브라우저가 로 리디렉션됩니다. `https://[server]:[port]/lc/apps/ws/index.html`.
