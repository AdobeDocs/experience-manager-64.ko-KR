---
title: Microsoft SharePoint용 커넥터 구성
seo-title: Configuring Connector for Microsoft SharePoint
description: AEM Forms와 Microsoft SharePoint 간의 통신을 사용하도록 Microsoft SharePoint용 커넥터를 구성합니다.
seo-description: Configure Connector for Microsoft SharePoint to enable communication between AEM forms and Microsoft SharePoint.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
exl-id: 9bd396a3-5da9-4355-ad76-e7132ac8aed8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# Microsoft SharePoint용 커넥터 구성 {#configuring-connector-for-microsoft-sharepoint}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Microsoft SharePoint용 커넥터를 사용하면 AEM Forms와 Microsoft SharePoint 간에 통신할 수 있습니다. 자세한 배경 정보는 의 &quot;Connectors for ECM&quot;을 참조하십시오. [서비스 참조](https://www.adobe.com/go/learn_aemforms_services_63).

1. 관리 콘솔에서 서비스 > Microsoft SharePoint용 커넥터 를 클릭합니다.
1. SharePoint 서버에 대해 다음 설정을 지정합니다.

   **SharePoint 서버 호스트 이름:** SharePoint 서버에 있는 웹 애플리케이션의 호스트 이름 포트 번호(형식) `[hostname]:[port]`.

   **사용자 이름:** SharePoint 서버에 연결하는 데 사용되는 사용자 계정입니다.

   **암호:** SharePoint 서버에 연결하는 데 사용되는 사용자 계정의 암호

   **도메인 이름:** SharePoint 서버가 있는 도메인입니다.

1. 저장을 클릭합니다.

## Microsoft SharePoint 구성 서비스 {#microsoft-sharepoint-configuration-service}

Microsoft SharePoint 구성 서비스 `(MSSharePointConfigService)` 가장 권한이 있는 AEM forms 사용자의 자격 증명을 지정할 수 있도록 해줍니다. 가장 권한에 대한 자세한 내용은 [Microsoft SharePoint용 커넥터 구성](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). 다음 단계에 따라 설정을 지정하십시오. `MSSharePointConfigService`:

1. 관리 콘솔에서 서비스 > 애플리케이션 및 서비스 > 서비스 관리를 클릭합니다.
1. 서비스 목록을 탐색하고 를 클릭합니다. `MSSharePointConfigService`.
1. 구성 페이지에서 다음 설정을 지정합니다.

   * 가장 권한이 있는 사용자의 사용자 이름
   * 위 사용자의 암호

1. 저장을 클릭합니다.
