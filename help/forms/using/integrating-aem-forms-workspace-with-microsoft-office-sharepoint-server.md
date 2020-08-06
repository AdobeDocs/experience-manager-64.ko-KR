---
title: AEM 양식 작업 영역을 Microsoft Office SharePoint Server와 통합
seo-title: AEM 양식 작업 영역을 Microsoft Office SharePoint Server와 통합
description: 'AEM 양식 작업 영역을 Microsoft Office SharePoint Server와 통합할 수 있습니다. '
seo-description: 'AEM 양식 작업 영역을 Microsoft Office SharePoint Server와 통합할 수 있습니다. '
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---


# AEM 양식 작업 영역을 Microsoft Office SharePoint Server와 통합 {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- 요구 사항**

**사전 요구 사항 지식** SharePoint Server에 AEM Forms 작업 영역을 추가하려면 해당 권한이 있는 SharePoint Server에 액세스할 수 있어야 하며, Workspace에 액세스하려면 URL을 알고 있어야 합니다. 아래 단계에서는 SharePoint Server에 대해 잘 알고 있다고 가정합니다. SharePoint Server의 웹 파트에 대한 자세한 내용은 Windows SharePoint Services의 웹 파트를 참조하십시오.

**사용자 수준**&#x200B;시작

Microsoft Office SharePoint Server(예: Microsoft Office SharePoint Server 2007)에서 AEM Forms 작업 영역을 웹 파트로 사용할 수 있습니다. 사용자는 웹 브라우저를 사용하여 SharePoint Server에 연결하여 AEM Forms 작업 공간에 액세스할 수 있습니다. 이 문서에서는 AEM Forms 작업 영역을 Microsoft Office SharePoint Server의 웹 파트로 표시하는 기본 단계를 알아봅니다. 이 문서에 설명된 단계를 수행하여 SharePoint 서버에 연결하는 사용자가 동일한 포트에서 AEM Forms 작업 공간에 액세스할 수 있도록 통합 환경을 제공할 수 있습니다.

>[!NOTE]
>
>이 문서에 나열된 단계는 특정 Microsoft SharePoint Server 2007입니다. 지원되는 다른 버전의 Microsoft SharePoint로 HTML 작업 영역을 구성할 수도 있습니다.

## Microsoft Office SharePoint Server 2007과 AEM Forms 작업 영역 통합 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

AEM Forms 작업 공간을 웹 파트에 통합하려면 다음 단계를 수행하십시오.

1. 웹 브라우저에서 SharePoint 사이트(https://*[myMOSSserver]:*44299/default.aspx)으로 이동합니다. 여기서 *[myMOSSserver]* 는 Sharepoint 서버의 이름 또는 IP 주소입니다.

   >[!NOTE]
   >
   >44299는 SharePoint 서버의 기본 포트 번호입니다. 포트 번호는 SharePoint Server 설치에 따라 다릅니다.

1. 웹 페이지의 오른쪽 상단에서 **사이트 작업을** 클릭하고 페이지 **편집을 선택합니다**.
1. 웹 파트 **추가 단추를** 클릭합니다.
1. [웹 파트 추가 - 웹 페이지 대화 상자]의 [기타]에서 [ **Page Viewer 웹 파트** ]를 선택한 다음 **추가를 클릭합니다**.
1. [Page Viewer 웹 파트] 상자에서 **편집을** 클릭하고 [공유 웹 파트 **수정]을 선택합니다**.

   >[!NOTE]
   >
   >다음 그림과 같이 3단계에서 클릭한 웹 파트 **추가** 단추 아래에 페이지 뷰어 웹 파트 상자가 나타납니다(그림 1).

   ![Microsoft Office SharePoint 서버의 페이지 뷰어 웹 파트 상자](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **그림:** *Microsoft Office SharePoint 서버의 페이지 뷰어 웹 파트 상자*

1. 페이지 뷰어 페이지에서 다음 작업을 수행합니다.

   1. [링크] 상자에 https://*[AEM_forms_Server]:*8080/lc/ws와 같은 AEM Forms 작업 영역의 URL을 입력합니다. 여기서 *[AEM_forms_Server는 AEM 양식 서버의 IP 또는 이름을]* 나타냅니다.
   1. 모양 **을** 클릭하고 높이, 폭 및 제목을 수정하여 전체 작업 영역 사용자 인터페이스를 볼 수 있습니다. 예를 들어 높이와 너비를 각각 6인치 및 11인치로 설정할 수 있습니다.
   1. 링크 **테스트를 클릭합니다**. 작업 영역이 표시된 새 웹 브라우저 창이 나타납니다.
   1. (선택 사항) **레이아웃** 을 클릭하고 웹 파트에서 작업 영역의 레이아웃을 수정합니다.
   1. (선택 사항) **고급을** 클릭하고 설명과 웹 파트에서 작업 공간을 최소화하거나 닫을 수 있는지 여부와 같은 다른 설정을 수정합니다.

      적용을 **클릭합니다**.

1. 편집 모드 **종료를** 클릭하고 작업 공간에 액세스할 수 있는지 확인합니다.

위의 단계를 완료하면 SharePoint 사이트가 다음 그림과 유사하게 보입니다(그림 2).

![Microsoft Office SharePoint Server와 통합된 AEM Forms 작업 영역](assets/aem-forms-workspace.jpg)

**그림:** *Microsoft Office SharePoint Server와 통합된 AEM Forms 작업 영역*

