---
title: Salesforce와 통합
seo-title: Salesforce와 통합
description: AEM과 Salesforce 통합에 대해 알아봅니다.
seo-description: AEM과 Salesforce 통합에 대해 알아봅니다.
uuid: db3b25f3-b680-4054-a8db-4161d4c86201
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b9752c60-eb26-4840-9163-a99537a58727
exl-id: 4c09699a-c7ae-48ee-9423-87ff35b1e9d9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 3%

---

# Salesforce와 통합{#integrating-with-salesforce}

Salesforce와 AEM을 통합하면 리드 관리 기능이 제공되며 Salesforce에서 제공하는 기존 기능을 활용합니다. Salesforce로 리드를 게시하고 Salesforce에서 직접 데이터에 액세스하는 구성 요소를 만들도록 AEM을 구성할 수 있습니다.

AEM과 Salesforce 간의 양방향 및 확장 가능한 통합을 통해 다음을 수행할 수 있습니다.

* 조직은 데이터를 완벽하게 사용하고 업데이트하여 고객 경험을 향상시킬 수 있습니다.
* 마케팅에서 판매 활동에 대한 참여
* Salesforce 데이터 저장소에서 데이터를 자동으로 전송 및 받을 조직입니다.

이 문서에서는 다음 사항에 대해 설명합니다.

* Salesforce Cloud Services 구성 방법(Salesforce와 통합하도록 AEM 구성)
* Client Context 및 개인화에 Salesforce 리드/연락처 정보를 사용하는 방법
* Salesforce 워크플로우 모델을 사용하여 AEM 사용자를 salesforce에 리드로 게시하는 방법
* Salesforce의 데이터를 표시하는 구성 요소를 만드는 방법

## Salesforce {#configuring-aem-to-integrate-with-salesforce}와 통합하도록 AEM 구성

Salesforce와 통합하도록 AEM을 구성하려면 먼저 Salesforce에서 원격 액세스 애플리케이션을 구성해야 합니다. 그런 다음 이 원격 액세스 응용 프로그램을 가리키도록 salesforce 클라우드 서비스를 구성합니다.

>[!NOTE]
>
>Salesforce에서 무료 개발자 계정을 만들 수 있습니다.

Salesforce와 통합하도록 AEM을 구성하려면:

1. AEM에서 **Cloud Services**&#x200B;로 이동합니다. 타사 서비스에서 **Salesforce**&#x200B;에서 **지금 구성**&#x200B;을 클릭합니다.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. 새 구성을 만듭니다(예: **developer**).

   >[!NOTE]
   >
   >새 구성은 새 페이지로 리디렉션됩니다.**http://localhost:4502/etc/cloudservices/salesforce/developer.html** Salesforce에서 원격 액세스 응용 프로그램을 만드는 동안 콜백 URL에서 지정해야 하는 것과 동일한 값입니다. 이러한 값은 일치해야 합니다.

1. salesforce 계정에 로그인합니다(또는 계정이 없는 경우 [https://developer.force.com](https://developer.force.com)에서 만듭니다.)
1. Salesforce에서 **Create** > **Apps**&#x200B;로 이동하여 **연결된 앱**&#x200B;에 액세스합니다(이전 버전의 salesforce에서 워크플로우는 **Deploy** > **원격 액세스**).
1. **새로 만들기**&#x200B;를 클릭하여 AEM을 Salesforce와 연결합니다.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. **연결된 앱 이름**, **API 이름** 및 **전자 메일**&#x200B;을 입력합니다. **OAuth 설정 활성화** 확인란을 선택하고 **콜백 URL**&#x200B;을 입력하고 OAuth 범위를 추가합니다(예: 전체 액세스). 콜백 URL은 다음과 유사합니다.`http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   구성과 일치하도록 서버 이름/포트 번호 및 페이지 이름을 변경합니다.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. **저장**&#x200B;을 클릭하여 Salesforce 구성을 저장합니다. Salesforce는 AEM 구성에 필요한 **소비자 키** 및 **소비자 암호**&#x200B;를 만듭니다.

   ![chlimage_1-87](assets/chlimage_1-87.png)

   >[!NOTE]
   >
   >Salesforce의 원격 액세스 애플리케이션이 활성화될 때까지 몇 분(최대 15분)을 기다려야 할 수 있습니다.

1. AEM에서 **Cloud Services**&#x200B;로 이동하여 이전에 만든 Salesforce 구성으로 이동합니다(예: **developer**). **편집**&#x200B;을 클릭하고 salesforce.com에서 고객 키와 고객 암호를 입력합니다.

   ![chlimage_1-23](assets/chlimage_1-23.jpeg)

   | 로그인 URL | Salesforce 인증 끝점입니다. 이 값은 사전 입력되어 대부분의 경우 제공됩니다. |
   |---|---|
   | 고객 키 | salesforce.com의 원격 액세스 응용 프로그램 등록 페이지에서 가져온 값을 입력합니다. |
   | 고객 비밀 | salesforce.com의 원격 액세스 응용 프로그램 등록 페이지에서 가져온 값을 입력합니다. |

1. 연결하려면 **Salesforce에 연결**&#x200B;을 클릭하십시오. Salesforce 요청은 구성이 salesforce에 연결되도록 허용합니다.

   ![chlimage_1-88](assets/chlimage_1-88.png)

   AEM에서 성공적으로 연결되었다는 확인 대화 상자가 열립니다.

1. 웹 사이트의 루트 페이지로 이동하고 **페이지 속성**&#x200B;을 클릭합니다. 그런 다음 **Cloud Services**&#x200B;을 선택하고 **Salesforce**&#x200B;를 추가하고 올바른 구성을 선택합니다(예: **developer**).

   ![chlimage_1-89](assets/chlimage_1-89.png)

   이제 워크플로우 모델을 사용하여 Salesforce에 리드를 게시하고 Salesforce에서 데이터에 액세스하는 구성 요소를 만들 수 있습니다.

## AEM 사용자를 Salesforce 리드로 내보내기 {#exporting-aem-users-as-salesforce-leads}

AEM 사용자를 Salesforce 리드로 내보내려면 리드를 Salesforce에 게시하도록 워크플로우를 구성해야 합니다.

AEM 사용자를 Salesforce 리드로 내보내려면

1. 워크플로우 **Salesforce.com Export**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **시작**&#x200B;을 클릭하여 `http://localhost:4502/workflow`의 Salesforce 워크플로우로 이동합니다.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. 이 워크플로우에 대한 **페이로드**&#x200B;로 리드로 만들 AEM 사용자를 선택합니다(홈 -> 사용자). Salesforce 리드의 **FirstName** 및 **LastName** 필드에 매핑되는 **givenName**, **familyName** 등의 정보가 포함되어 있으므로 사용자의 프로필 노드를 선택해야 합니다.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >이 워크플로우를 시작하기 전에 AEM의 리드 노드가 Salesforce에 게시되기 전에 가져야 하는 특정 필수 필드가 있습니다. **givenName**, **familyName**, **company**&#x200B;및 **email**&#x200B;입니다. AEM 사용자와 Salesforce 리드 간의 전체 매핑 목록을 보려면 AEM 사용자와 Salesforce 리드 간의 매핑 구성 을 참조하십시오.](#mapping-configuration-between-aem-user-and-salesforce-lead)[

1. **확인**&#x200B;을 클릭합니다. 사용자 정보는 salesforce.com으로 내보내집니다. salesforce.com에서 확인할 수 있습니다.

   >[!NOTE]
   >
   >오류 로그에 리드를 가져오는지 여부가 표시됩니다. 자세한 내용은 오류 로그를 확인하십시오.

### Salesforce.com 내보내기 워크플로우 구성 {#configuring-the-salesforce-com-export-workflow}

올바른 Salesforce.com 구성에 일치시키거나 다른 변경 작업을 수행하려면 Salesforce.com 내보내기 워크플로우를 구성해야 할 수 있습니다.

Salesforce.com 내보내기 워크플로우를 구성하려면 다음을 수행합니다.

1. 다음으로 이동 `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![chlimage_1-24](assets/chlimage_1-24.jpeg)

1. Salesforce.com 내보내기 단계를 열고 **인수** 탭을 선택한 다음 올바른 구성을 선택하고 **확인**&#x200B;을 클릭합니다. Salesforce에서 삭제된 리드를 워크플로우에서 다시 만들려면 확인란을 선택합니다.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. **저장**&#x200B;을 클릭하여 변경 내용을 저장합니다.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### AEM 사용자와 Salesforce 리드 간의 구성 매핑 {#mapping-configuration-between-aem-user-and-salesforce-lead}

AEM 사용자와 Salesforce 리드 간의 현재 매핑 구성을 보거나 편집하려면 구성 관리자를 엽니다.`https://<hostname>:<port>/system/console/configMgr` 및 **Salesforce 리드 매핑 구성**&#x200B;을 검색합니다.

1. **웹 콘솔**&#x200B;을 클릭하거나 `https://<hostname>:<port>/system/console/configMgr.`로 직접 이동하여 구성 관리자를 엽니다
1. **Salesforce 리드 매핑 구성**&#x200B;을 검색합니다.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. 필요에 따라 매핑을 변경합니다. 기본 매핑은 ** aemUserAttribute=sfLeadAttribute** 패턴을 따릅니다. **저장**&#x200B;을 클릭하여 변경 내용을 저장합니다.

## Salesforce 클라이언트 컨텍스트 저장소 구성 {#configuring-salesforce-client-context-store}

Salesforce 클라이언트 컨텍스트 저장소는 AEM 내에서 이미 사용할 수 있는 정보보다 현재 로그인한 사용자에 대한 추가 정보를 표시합니다. Salesforce와의 연결에 따라 Salesforce에서 이 추가 정보를 가져옵니다.

이를 수행하려면 다음을 구성해야 합니다.

1. Salesforce 연결 구성 요소를 통해 AEM 사용자를 Salesforce ID에 연결합니다.
1. Salesforce 프로필 데이터 를 Client Context 페이지에 추가하여 보려는 속성을 구성합니다.
1. (선택 사항) Salesforce Client Context Store에서 데이터를 사용하는 세그먼트를 만듭니다.

### AEM 사용자를 Salesforce ID {#linking-an-aem-user-with-a-salesforce-id}에 연결

Client Context에서 로드하려면 AEM 사용자를 Salesforce ID에 매핑해야 합니다. 실제 시나리오에서는 알려진 사용자 데이터를 기반으로 유효성 검사를 통해 연결됩니다. 데모 목적으로 이 절차에서는 **Salesforce Connect** 구성 요소를 사용합니다.

1. AEM에서 웹 사이트로 이동하여 로그인한 다음, 사이드킥에서 **Salesforce Connect** 구성 요소를 드래그하여 놓습니다.

   >[!NOTE]
   >
   >**Salesforce Connect** 구성 요소를 사용할 수 없는 경우 **디자인** 보기로 이동하여 **편집** 보기에서 사용할 수 있도록 선택하십시오.

   ![chlimage_1-25](assets/chlimage_1-25.jpeg)

   구성 요소를 페이지로 끌면 **Link to Salesforce=Off**&#x200B;가 표시됩니다.

   ![chlimage_1-95](assets/chlimage_1-95.png)

   >[!NOTE]
   >
   >이 구성 요소는 데모용으로만 사용됩니다. 실제 시나리오에서는 사용자를 리드와 연결/일치시키는 다른 프로세스가 있습니다.

1. 페이지에서 구성 요소를 드래그한 후 열어서 구성합니다. 구성, 연락처 유형, Salesforce 리드 또는 연락처를 선택하고 **확인**&#x200B;을 클릭합니다.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   AEM은 Salesforce 연락처 또는 리드와 사용자를 연결합니다.

   ![chlimage_1-97](assets/chlimage_1-97.png)

### Salesforce 데이터를 Client Context {#adding-salesforce-data-to-client-context}에 추가

Client Context에서 Salesforce에서 사용자 데이터를 로드하여 개인화에 사용할 수 있습니다.

1. 확장하려는 클라이언트 컨텍스트를 엽니다(예: `http://localhost:4502/etc/clientcontext/default/content.html.`)

   ![chlimage_1-26](assets/chlimage_1-26.jpeg)

1. **Salesforce 프로필 데이터** 구성 요소를 Client Context로 드래그합니다.

   ![chlimage_1-27](assets/chlimage_1-27.jpeg)

1. 구성 요소를 두 번 클릭하여 엽니다. **항목 추가**&#x200B;를 선택하고 드롭다운 목록에서 속성을 선택합니다. 원하는 만큼 속성을 추가하고 **확인**&#x200B;을 선택합니다.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. 이제 Salesforce의 Salesforce 관련 속성이 클라이언트 컨텍스트에 표시됩니다.

   ![chlimage_1-99](assets/chlimage_1-99.png)

### Salesforce Client Context Store {#building-a-segment-using-data-from-salesforce-client-context-store}의 데이터를 사용하여 세그먼트 작성

Salesforce Client Context Store에서 데이터를 사용하는 세그먼트를 만들 수 있습니다. 이를 위해 진행되는 작업:

1. **도구** > **세그먼테이션**&#x200B;으로 이동하거나 [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation)로 이동하여 AEM의 세그멘테이션으로 이동합니다.
1. Salesforce의 데이터를 포함하도록 세그먼트를 만들거나 업데이트합니다. 자세한 내용은 [세그먼테이션](/help/sites-administering/campaign-segmentation.md)을 참조하십시오.

## 리드 검색 {#searching-leads}

AEM은 지정된 기준에 따라 Salesforce에서 리드를 검색하는 샘플 검색 구성 요소와 함께 제공됩니다. 이 구성 요소는 Salesforce REST API를 사용하여 salesforce 개체를 검색하는 방법을 보여줍니다. Salesforce 구성과 페이지를 연결하여 salesforce.com에 호출을 트리거해야 합니다.

>[!NOTE]
>
>Salesforce REST API를 사용하여 Salesforce 개체를 쿼리하는 방법을 보여주는 샘플 구성 요소입니다. 필요에 따라 더 복잡한 구성 요소를 만들려면 예를 사용하십시오.

이 구성 요소를 사용하려면

1. 이 구성을 사용할 페이지로 이동합니다. 페이지 속성을 열고 **Cloud Services을 선택합니다.** 서비스  **추가** 를 클릭하고  **** Salesforce와 적절한 구성을 선택하고  **확인**&#x200B;을 클릭합니다.

   ![chlimage_1-28](assets/chlimage_1-28.jpeg)

1. Salesforce 검색 구성 요소를 페이지로 드래그합니다(활성화되어 있으면). 활성화하려면 디자인 모드로 이동하여 해당 영역에 추가합니다.

   ![chlimage_1-29](assets/chlimage_1-29.jpeg)

1. 검색 구성 요소를 열고 검색 매개 변수를 지정하고 **확인**&#x200B;을 클릭합니다.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM에는 지정된 기준과 일치하는 검색 구성 요소에 지정된 리드가 표시됩니다.

   ![chlimage_1-101](assets/chlimage_1-101.png)
