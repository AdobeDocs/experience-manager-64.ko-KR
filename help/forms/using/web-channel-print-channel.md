---
title: 채널 및 웹 채널 인쇄
seo-title: 채널 및 웹 채널 인쇄
description: 인쇄 채널 템플릿 가져오기 및 웹 채널 템플릿 만들기 및 활성화
seo-description: 인쇄 채널 템플릿 가져오기 및 웹 채널 템플릿 만들기 및 활성화
uuid: 19e6ffab-00d2-4084-9ee7-9643b11eb6c6
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 71bba66a-3cac-445b-9941-aa4bcf9b2160
feature: 대화형 통신
exl-id: cb7a8e96-4440-47ec-b506-275d5acc774e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 0%

---

# 채널 및 웹 채널 인쇄 {#print-channel-and-web-channel}

인쇄 채널 템플릿 가져오기 및 웹 채널 템플릿 만들기 및 활성화

대화형 커뮤니케이션은 다음 두 가지 채널을 통해 전달될 수 있습니다.인쇄 및 웹 인쇄 채널은 보험료 지불을 리마인더로 인쇄한 편지와 같은 PDF 및 용지 커뮤니케이션을 만드는 데 사용되는 반면 웹 채널은 웹 사이트의 신용 카드 명세서와 같은 온라인 경험을 전달하는 데 사용됩니다.

Interactive Communication 작성자는 문서 조각이나 이미지와 같은 자산을 재사용하여 Interactive Communication의 인쇄 및 웹 버전을 모두 만들 수 있습니다.

[대화형 통신 만들기](/help/forms/using/create-interactive-communication.md)에 대한 사전 요구 사항 중 하나는 서버에서 인쇄 및/또는 웹 채널을 위한 템플릿을 사용할 수 있도록 하는 것입니다. 템플릿 작성자가 AEM 자체에서 웹 채널 템플릿을 만드는 동안 인쇄 채널 템플릿 XDP는 Adobe Forms 디자이너에서 만들어지고 서버에 업로드됩니다.

## 인쇄 채널 {#printchannel}

대화형 커뮤니케이션의 인쇄 채널은 XFA 양식 서식 파일인 XDP를 사용합니다. XDP는 Adobe Forms 디자이너에 디자인되었습니다. 인쇄 채널 템플릿 만들기에 대한 자세한 내용은 [레이아웃 디자인](/help/forms/using/layout-design-details.md)을 참조하십시오. Interactive Communication에서 인쇄 채널 템플릿을 사용하려면 템플릿을 AEM Forms 서버에 업로드해야 합니다.

### 대화형 통신 인쇄 채널 템플릿 업로드 {#upload-interactive-communication-print-channel-template}

템플릿을 업로드하려면 forms-user 그룹의 구성원이어야 합니다. 다음 단계를 사용하여 인쇄 채널 템플릿(XDP)을 AEM Forms에 업로드합니다.

1. **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;를 선택합니다.

1. **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**&#x200B;를 누릅니다.

   적절한 인쇄 채널 템플릿(XDP)을 탐색하고 선택하고 **[!UICONTROL 열기]**&#x200B;를 누릅니다.

## 웹 채널 {#web-channel}

템플릿 작성자 및 관리자는 웹 템플릿을 만들고, 편집하고, 활성화할 수 있습니다. 다른 사용자가 웹 템플릿을 작성할 수 있도록 하려면 사용자에게 권한을 제공해야 합니다. 자세한 내용은 [사용자, 그룹 및 액세스 권한 관리](/help/sites-administering/user-group-ac-admin.md)를 참조하십시오.

### 웹 채널 템플릿 작성 {#authoring-web-channel-template}

웹 채널 템플릿을 만들려면 먼저 템플릿 폴더를 만들어야 합니다. 템플릿 폴더 내에 웹 템플릿을 만들면 양식 사용자가 템플릿을 기반으로 대화형 커뮤니케이션의 웹 채널을 만들 수 있도록 템플릿을 활성화해야 합니다.

웹 채널 템플릿을 작성하려면 다음 단계를 완료하십시오.

1. Interactive Communication 웹 템플릿이 아직 없는 경우 해당 템플릿을 유지할 템플릿 폴더를 만듭니다. 자세한 내용은 [페이지 템플릿 - 편집 가능](/help/sites-developing/page-templates-editable.md)에서 템플릿 폴더 를 참조하십시오.

   1. **[!UICONTROL 도구]** ![tools-1](assets/tools-1.png) > **[!UICONTROL 구성 브라우저]**&#x200B;를 탭합니다.
      * 자세한 내용은 [구성 브라우저 설명서](/help/sites-administering/configurations.md)를 참조하십시오.
   1. 구성 브라우저 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 누릅니다.
   1. 구성 만들기 대화 상자에서 폴더의 제목을 지정하고 **[!UICONTROL 편집 가능한 템플릿]**&#x200B;을 선택하고 **[!UICONTROL 만들기]**&#x200B;를 누릅니다.

      폴더가 생성되고 구성 브라우저 페이지에 나열됩니다.

1. 해당 템플릿 폴더로 이동하고 웹 템플릿을 만듭니다.

   1. **[!UICONTROL 도구]** > **[!UICONTROL 템플릿 > 폴더]**&#x200B;를 선택하여 해당 템플릿 폴더로 이동합니다.
   1. **[!UICONTROL 만들기]**&#x200B;를 누릅니다.
   1. **[!UICONTROL 대화형 통신 - 웹 채널]**&#x200B;을 선택하고 **[!UICONTROL 다음]**&#x200B;을 탭합니다.
   1. 템플릿 제목 및 설명을 입력한 다음 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.

      템플릿이 만들어지고 대화 상자가 나타납니다.

   1. **[!UICONTROL 열기]**&#x200B;를 눌러 템플릿 편집기에서 만든 템플릿을 엽니다.

      템플릿 편집기가 나타납니다.

      ![웹 채널 템플릿](assets/webchanneltemplate.png)

      템플릿을 만들거나 편집할 때 템플릿 작성자가 정의할 수 있는 다양한 측면이 있습니다. 템플릿을 만들거나 편집하는 것은 페이지 작성과 유사합니다. 자세한 내용은 [페이지 템플릿 만들기](/help/sites-authoring/templates.md)에서 템플릿 편집 - 템플릿 작성자를 참조하십시오.

1. 대화형 통신 작성을 위해 이 템플릿을 사용하려면 템플릿을 활성화합니다.

   1. **[!UICONTROL 도구]** ![tools-1](assets/tools-1.png) > **[!UICONTROL 템플릿]**&#x200B;을 탭합니다.
   1. 해당 템플릿으로 이동하여 선택한 다음 **[!UICONTROL 활성화]**&#x200B;를 누르고 경고 메시지에서 **[!UICONTROL 활성화]**&#x200B;를 누릅니다.

      템플릿이 활성화되고 해당 상태가 사용으로 표시됩니다. 이제 새로 만든 웹 채널 템플릿을 사용할 수 있는 대화형 통신 만들기를 진행할 수 있습니다.

### 웹 채널 {#print-channel-as-master-for-web-channel}에 대한 마스터로 채널 인쇄

대화형 커뮤니케이션을 작성하는 동안 작성자가 이 옵션을 선택하여 인쇄 채널과 동기화되는 웹 채널을 만들 수 있습니다. 인쇄 채널을 웹 채널용 마스터로 사용하면 웹 채널의 컨텐츠, 상속 및 데이터 바인딩이 인쇄 채널에서 파생되고 인쇄 채널에서 수행된 변경 사항이 웹 채널에 반영될 수 있습니다. 그러나 대화형 통신 작성자는 필요에 따라 웹 채널의 특정 구성 요소에 대한 상속을 중단할 수 있습니다.

![printweb_2-2](assets/printweb_2-2.png)
