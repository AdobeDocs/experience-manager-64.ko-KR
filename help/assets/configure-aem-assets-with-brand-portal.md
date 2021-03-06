---
title: Brand Portal에서 AEM Assets 구성
description: 'Brand Portal에 자산 및 컬렉션을 게시하기 위해 Brand Portal에서 AEM Assets을 구성하는 방법을 알아봅니다. '
contentOwner: VG
feature: Brand Portal
role: Admin
exl-id: cde35555-259f-4d16-999f-2b93d597b8a5
source-git-commit: a50cd2b50191b86ac27cc228944c6c9e917b08cb
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 81%

---

# Brand Portal에서 AEM Assets 구성 {#configure-integration-64}

Adobe Experience Manager Assets는 다음을 통해 Brand Portal으로 구성됩니다 [!DNL Adobe I/O]: Brand Portal 임차인의 인증을 위해 IMS 토큰을 받습니다.

>[!NOTE]
>
>을 통해 Brand Portal과 AEM Assets 구성 [!DNL Adobe I/O] AEM 6.4.8.0 이상에서 지원됩니다.
>
>이전에는 Brand Portal이 기존 OAuth 게이트웨이를 통해 클래식 UI에 구성되었으며, 이 게이트웨이는 인증을 위해 IMS 액세스 토큰을 가져오는 데 JWT 토큰 교환을 사용합니다.

>[!TIP]
>
>***기존 고객 전용***
>
>기존 OAuth 게이트웨이 구성을 계속 사용하는 것이 좋습니다. 기존 OAuth 게이트웨이 구성 문제가 발생하는 경우 기존 구성을 삭제하고 를 통해 새 구성을 만드십시오 [!DNL Adobe I/O].

이 도움말은 다음 두 가지 사용 사례에 대해 설명합니다.

* [새 구성](#configure-new-integration-64): 새 Brand Portal 사용자이고 Brand Portal으로 AEM Assets 작성자 인스턴스를 구성하려는 경우 [!DNL Adobe I/O].
* [구성 업그레이드](#upgrade-integration-64): 기존 OAuth 게이트웨이에 Brand Portal으로 구성된 AEM Assets 작성자 인스턴스를 사용하는 기존 Brand Portal 사용자인 경우 기존 구성을 삭제하고 새 구성을 만드는 것이 좋습니다. [!DNL Adobe I/O].

제공된 정보는 이 도움말을 읽는 사람이 다음 기술을 잘 알고 있다는 가정을 기반으로 합니다.

* Adobe Experience Manager 및 AEM 패키지 설치, 구성 및 관리

* Linux 및 Microsoft Windows 운영 체제 사용

## 전제 조건 {#prerequisites}

Brand Portal에 AEM Assets을 구성하려면 다음이 필요합니다.

* 최신 서비스 팩으로 실행 중인 AEM Assets 작성자 인스턴스.
* Brand Portal 임차인 URL.
* Brand Portal 테넌트의 IMS 조직에 대한 시스템 관리자 권한이 있는 사용자

[AEM 6.4 다운로드 및 설치](#aemquickstart)

[최신 AEM 서비스 팩 다운로드 및 설치](#servicepack)

### AEM 6.4 다운로드 및 설치 {#aemquickstart}

AEM 작성자 인스턴스를 설정하려면 AEM 6.4가 있어야 합니다. AEM을 실행하지 않은 경우 다음 위치에서 다운로드하십시오.

* 기존 AEM 고객의 경우 [Adobe 라이선스 웹 사이트](http://licensing.adobe.com)에서 AEM 6.4를 다운로드합니다.

* Adobe 파트너인 경우 [Adobe 파트너 교육 프로그램](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q)을 사용하여 AEM 6.4를 요청합니다.

AEM을 다운로드한 후 AEM 작성자 인스턴스를 설정하는 방법은 [배포 및 유지 관리](https://helpx.adobe.com/kr/experience-manager/6-4/sites/deploying/using/deploy.html#defaultlocalinstall)를 참조하십시오.

### AEM 최신 서비스 팩 다운로드 및 설치 {#servicepack}

세부 지침은 다음을 참조하십시오.

* [AEM 6.4 서비스 팩 릴리스 노트](https://helpx.adobe.com/kr/experience-manager/6-4/release-notes/sp-release-notes.html)

**고객 지원에 문의** 최신 AEM 패키지 또는 서비스 팩을 찾을 수 없는 경우

## 구성 만들기 {#configure-new-integration-64}

Brand Portal에 AEM Assets을 처음 구성하는 경우 단계를 나열된 순서로 수행합니다.

1. [공개 인증서 받기](#public-certificate)
1. [만들기 [!DNL Adobe I/O] 통합](#createnewintegration)
1. [IMS 계정 구성 만들기](#create-ims-account-configuration)
1. [클라우드 서비스 구성](#configure-the-cloud-service)
1. [구성 테스트](#test-integration)

>[!NOTE]
>
>AEM Assets 작성자 인스턴스는 하나의 Brand Portal 테넌트로 구성해야 합니다.

### IMS 구성 만들기 {#create-ims-configuration}

IMS 구성은 AEM Assets 작성자 인스턴스를 사용하여 Brand Portal 테넌트를 인증합니다.

IMS 구성에는 두 단계가 포함됩니다.

* [공개 인증서 받기](#public-certificate)
* [IMS 계정 구성 만들기](#create-ims-account-configuration)

### 공개 인증서 받기 {#public-certificate}

공개 인증서를 사용하면 프로필을 인증할 수 있습니다 [!DNL Adobe I/O].

1. AEM Assets 작성자 인스턴스에 로그인
기본 URL: http:// localhost:4502/aem/start.html
1. **도구** ![도구](assets/tools.png) 패널에서 **[!UICONTROL 보안]** >> **[!UICONTROL Adobe IMS 구성]**&#x200B;으로 이동합니다.

   ![Adobe IMS 계정 구성 UI](assets/ims-config1.png)

1. Adobe IMS 구성 페이지가 열립니다.

   **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   **[!UICONTROL Adobe IMS 기술 계정 구성]** 페이지가 표시됩니다.

1. 기본적으로 **인증서** 탭이 열립니다.

   **클라우드 솔루션**&#x200B;에서 **[!UICONTROL Adobe Brand Portal]**&#x200B;을 선택합니다.

1. **[!UICONTROL 새 인증서 만들기]** 확인란을 선택하고 인증서 **별칭**&#x200B;을 지정합니다. 별칭은 대화 상자의 이름으로 사용됩니다.

1. **[!UICONTROL 인증서 만들기]**&#x200B;를 클릭합니다. 대화 상자가 나타납니다. 공개 인증서를 생성하려면 **[!UICONTROL 확인]**&#x200B;을 클릭하십시오.

   ![인증서 만들기](assets/ims-config2.png)

1. **[!UICONTROL 공개 키 다운로드]**&#x200B;를 클릭하고 *AEM-Adobe-IMS.crt* 인증서 파일을 컴퓨터에 저장합니다. 인증서 파일은 [만들기 [!DNL Adobe I/O] 통합](#createnewintegration).

   ![인증서 다운로드](assets/ims-config3.png)

1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   **계정** 탭에서 Adobe IMS 계정을 만듭니다. 하지만 이를 위해서는 통합에 대한 세부 사항이 필요합니다. 우선은 이 페이지를 열어 두십시오.

   새 탭을 열고 [만들기 [!DNL Adobe I/O] 통합](#createnewintegration) ims 계정 구성에 대한 통합 세부 사항을 가져오는 방법 을 참조하십시오.

### 만들기 [!DNL Adobe I/O] 통합 {#createnewintegration}

[!DNL Adobe I/O] 통합은 IMS 계정 구성을 설정하는 데 필요한 API 키, 클라이언트 암호 및 페이로드(JWT)를 생성합니다.

1. 에 로그인합니다. [!DNL Adobe I/O] Brand Portal 테넌트의 IMS 조직에 대한 시스템 관리자 권한이 있는 콘솔입니다.

   기본 URL: [https://console.adobe.io/](https://console.adobe.io/)

1. **[!UICONTROL 통합 만들기]**&#x200B;를 클릭합니다.

1. **[!UICONTROL API에 액세스]**&#x200B;를 선택하고, **[!UICONTROL 계속]**&#x200B;을 클릭합니다.

   ![새 통합 만들기](assets/create-new-integration1.png)

1. 새 통합 만들기 페이지가 열립니다.

   드롭다운 목록에서 자신이 속한 조직을 선택합니다.

   **[!UICONTROL Experience Cloud]**&#x200B;에서 **[!UICONTROL AEM Brand Portal]**&#x200B;을 선택하고 **[!UICONTROL 계속]**&#x200B;을 클릭합니다.

   Brand Portal 옵션이 비활성화되어 있다면 **[!UICONTROL Adobe 서비스]** 옵션 위의 드롭다운 상자에서 올바른 조직을 선택했는지 확인하십시오. 조직을 모르는 경우에는 관리자에게 문의하십시오.

   ![통합 만들기](assets/create-new-integration2.png)

1. 통합에 사용할 이름과 설명을 지정합니다. **[!UICONTROL 컴퓨터에서 파일 선택]**&#x200B;을 클릭하고 [공개 인증서 받기](#public-certificate) 섹션에서 다운로드한 `AEM-Adobe-IMS.crt` 파일을 업로드하십시오.

1. 조직의 프로필을 선택합니다.

   또는 기본 프로필 **[!UICONTROL Assets Brand Portal]**&#x200B;을 선택하고 **[!UICONTROL 통합 만들기]**&#x200B;를 클릭하십시오. 통합이 생성됩니다.

1. **[!UICONTROL 통합 세부 사항으로 계속]**&#x200B;을 클릭하여 통합 정보를 확인합니다.

   **[!UICONTROL API 키]**&#x200B;를 복사합니다.

   **[!UICONTROL 클라이언트 암호 검색]**&#x200B;을 클릭하고 클라이언트 암호 키를 복사합니다.

   ![통합의 API 키, 클라이언트 암호 및 페이로드 정보](assets/create-new-integration3.png)

1. **[!UICONTROL JWT]** 탭으로 이동하여 **[!UICONTROL JWT 페이로드]**&#x200B;를 복사합니다.

   API 키, 클라이언트 암호 키 및 JWT 페이로드 정보는 IMS 계정 구성을 만드는 데 사용됩니다.

### IMS 계정 구성 만들기 {#create-ims-account-configuration}

다음 절차를 수행했는지 확인하십시오.

* [공개 인증서 받기](#public-certificate)
* [만들기 [!DNL Adobe I/O] 통합](#createnewintegration)

**IMS 계정 구성을 만드는 절차:**

1. IMS 구성 페이지, **[!UICONTROL 계정]** 탭을 엽니다. [공개 인증서 받기](#public-certificate) 섹션의 끝에서 페이지를 열어 두었습니다.

1. IMS 계정에 대한 **[!UICONTROL 제목]**&#x200B;을 지정합니다.

   **[!UICONTROL 인증 서버]**&#x200B;에서 URL [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)을 입력하십시오.

   끝에 복사한 API 키, 클라이언트 암호 및 JWT 페이로드를 붙여 넣습니다. [만들기 [!DNL Adobe I/O] 통합](#createnewintegration).

   **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   통합이 생성됩니다.

   ![IMS 계정 구성](assets/create-new-integration6.png)

1. IMS 구성을 선택하고 **[!UICONTROL 상태 확인]**&#x200B;을 클릭합니다. 대화 상자가 나타납니다.

   **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 연결에 성공하면 *토큰이 검색되었습니다*&#x200B;라는 메시지가 나타납니다.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>IMS 구성은 하나만 있어야 합니다. IMS 구성을 여러 개 만들지 마십시오.
>
>IMS 구성이 상태 검사를 통과하는지 확인합니다. 구성이 상태 검사를 통과하지 않으면 구성이 잘못된 것입니다. 이 구성을 삭제하고 유효한 새 구성을 만들어야 합니다.

### 클라우드 서비스 구성 {#configure-the-cloud-service}

Brand Portal 클라우드 서비스 구성을 만들려면 다음 단계를 수행하십시오.

1. AEM Assets 작성자 인스턴스에 로그인합니다.

   기본 URL: http:// localhost:4502/aem/start.html
1. **도구** ![도구](assets/tools.png) 패널에서 **[!UICONTROL 클라우드 서비스 >> AEM Brand Portal]**&#x200B;로 이동합니다.

   Brand Portal 구성 페이지가 열립니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

1. 구성에 대한 **[!UICONTROL 제목]**&#x200B;을 지정합니다.

   [IMS 계정 구성 만들기](#create-ims-account-configuration) 단계에서 만든 IMS 구성을 선택하십시오.

   **[!UICONTROL 서비스 URL]**&#x200B;에서 Brand Portal 테넌트 URL을 입력합니다.

   ![](assets/create-cloud-service.png)

1. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 클라우드 구성이 생성됩니다. 이제 AEM Assets 작성자 인스턴스가 Brand Portal 임차인과 통합됩니다.

### 구성 테스트 {#test-integration}

1. AEM Assets 작성자 인스턴스에 로그인합니다.

   기본 URL: http:// localhost:4502/aem/start.html

1. **도구** ![도구](assets/tools.png) 패널에서 **[!UICONTROL 배포 >> 복제]**&#x200B;로 이동합니다.

   ![](assets/test-integration1.png)

1. 복제 페이지가 열립니다.

   **[!UICONTROL 작성자의 에이전트]**&#x200B;를 클릭합니다.

   ![](assets/test-integration2.png)

1. 각 임차인에 대해 4개의 복제 에이전트가 작성됩니다.

   Brand Portal 임차인의 복제 에이전트를 찾습니다.

   복제 에이전트 URL을 클릭합니다.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >복제 에이전트가 동시에 작동하여 작업 분포를 동일하게 공유하므로 게시 속도가 원래 속도보다 4배 더 빨라집니다. 클라우드 서비스가 구성된 후에는 여러 자산의 병렬 게시를 활성화하기 위해 기본적으로 활성화된 복제 에이전트를 활성화하는 데 추가 구성이 필요하지 않습니다.

1. AEM Assets 작성자와 Brand Portal 간의 연결을 확인하려면 **[!UICONTROL 연결 테스트]**&#x200B;를 클릭합니다.

   ![](assets/test-integration4.png)

1. 테스트 결과 맨 아래에서 복제가 성공했는지 확인합니다.

   ![](assets/test-integration5.png)


1. 4개의 복제 에이전트 모두에 대한 테스트 결과를 하나씩 확인합니다.

   >[!NOTE]
   >
   >일부 자산의 복제가 실패할 수 있으므로 복제 에이전트를 비활성화하지 마십시오.
   >
   >시간 초과 오류를 방지하기 위해 4개의 복제 에이전트가 모두 구성되었는지 확인합니다. 자세한 내용은 [Brand Portal에 동시 게시 문제 해결](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html#connection-timeout).

Brand Portal이 AEM Assets 작성자 인스턴스로 구성되었습니다. 이제 다음을 수행할 수 있습니다.

* [AEM Assets의 자산을 Brand Portal에 게시](../assets/brand-portal-publish-assets.md)
* [AEM Assets의 폴더를 Brand Portal에 게시](../assets/brand-portal-publish-folder.md)
* [AEM Assets에서 Brand Portal에 컬렉션 게시](../assets/brand-portal-publish-collection.md)
* Brand Portal 사용자가 AEM Assets에 자산을 제공하고 게시할 수 있도록 [자산 소싱](https://docs.adobe.com/content/help/ko-KR/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html)을 구성합니다.

## 구성 업그레이드 {#upgrade-integration-64}

다음 단계를 나열된 순서로 수행하여 기존 구성을 업그레이드합니다.

1. [실행 중인 작업 확인](#verify-jobs)
1. [기존 구성 삭제](#delete-existing-configuration)
1. [구성 만들기](#configure-new-integration-64)

### 실행 중인 작업 확인 {#verify-jobs}

수정하기 전에 AEM Assets 작성자 인스턴스에서 게시 작업이 실행되고 있지 않은지 확인합니다. 이러한 경우 4개의 복제 에이전트를 모두 확인하고 큐가 유휴 상태인지/비어 있는지 확인할 수 있습니다.

1. AEM Assets 작성자 인스턴스에 로그인합니다.

   기본 URL: http:// localhost:4502/aem/start.html

1. **도구** ![도구](assets/tools.png) 패널에서 **[!UICONTROL 배포 >> 복제]**&#x200B;로 이동합니다.

1. 복제 페이지가 열립니다.

   **[!UICONTROL 작성자의 에이전트]**&#x200B;를 클릭합니다.

   ![](assets/test-integration2.png)

1. Brand Portal 임차인의 복제 에이전트를 찾습니다.

   모든 복제 에이전트에 대해 **큐가 유휴 상태**&#x200B;인지, 활성 상태인 게시 작업이 없는지 확인합니다.

   ![](assets/test-integration3.png)

### 기존 구성 삭제 {#delete-existing-configuration}

기존 구성을 삭제하는 동안 다음 확인 목록을 실행해야 합니다.

* 4개의 복제 에이전트 모두 삭제
* 클라우드 서비스 삭제
* MAC 사용자 삭제

기존 구성을 삭제하려면 다음 단계를 수행하십시오.

1. AEM Assets 작성자 인스턴스에 로그인하고 CRX Lite를 관리자로 엽니다.

   기본 URL: http:// localhost:4502/crx/de/index.jsp

1. `/etc/replications/agents.author`로 이동하고 Brand Portal 임차인의 4개 복제 에이전트를 모두 삭제합니다.

   ![](assets/delete-replication-agent.png)

1. `/etc/cloudservices/mediaportal`로 이동하여 **클라우드 서비스 구성**&#x200B;을 삭제합니다.

   ![](assets/delete-cloud-service.png)

1. `/home/users/mac`로 이동하고 Brand Portal 임차인의 **MAC 사용자**&#x200B;를 삭제합니다.

   ![](assets/delete-mac-user.png)


이제 다음을 수행할 수 있습니다 [구성 만들기](#configure-new-integration-64) AEM 6.4 작성자 인스턴스에서 [!DNL Adobe I/O].



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

복제가 성공하면 자산, 폴더 및 컬렉션을 Brand Portal에 게시할 수 있습니다. 자세한 내용은 다음을 참조하십시오.

* [자산을 Brand Portal에 게시](brand-portal-publish-assets.md)
* [Brand Portal에 자산 및 폴더 게시](brand-portal-publish-folder.md)
* [컬렉션을 Brand Portal에 게시](brand-portal-publish-collection.md)
