---
title: ExactTarget과 통합
seo-title: ExactTarget과 통합
description: AEM과 ExactTarget을 통합하는 방법을 살펴보십시오.
seo-description: AEM과 ExactTarget을 통합하는 방법을 살펴보십시오.
uuid: dafa0a1a-2d1e-40fc-a729-f2ce7ebc7807
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: d1cff2bb-9fdf-49cb-a695-d437bba5653d
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# ExactTarget과 통합{#integrating-with-exacttarget}

AEM과 정확한 Target을 통합하면 AEM에서 만든 이메일을 정확한 Target을 통해 관리하고 보낼 수 있습니다. 또한 AEM 페이지에서 AEM 양식을 통해 정확한 Target의 리드 관리 기능을 사용할 수 있습니다.

통합에서는 다음과 같은 기능을 제공합니다.

* AEM에서 이메일을 만들고 배포를 위해 정확한 Target에 게시하는 기능
* AEM 양식의 작업을 설정하여 정확한 Target 구독자를 만드는 기능

ExactTarget이 구성된 후에는 ExactTarget에 뉴스레터 또는 이메일을 게시할 수 있습니다. 이메일 서비스에 [뉴스레터 게시를 참조하십시오](/help/sites-authoring/personalization.md).

## ExactTarget 구성 만들기 {#creating-an-exacttarget-configuration}

ExactTarget 구성은 Cloudservices 또는 도구를 통해 추가할 수 있습니다. 두 방법 모두 이 섹션에 설명되어 있습니다.

### Cloudservices를 통해 ExactTarget 구성 {#configuring-exacttarget-via-cloudservices}

Cloud Services에서 ExactTarget 구성을 만들려면:

1. 시작 페이지에서 **Cloud Services을 클릭합니다**. (Or directly access at `https://<hostname>:<port>/etc/cloudservices.html`.)
1. ExactTarget **을** 클릭한 다음 구성을 **클릭합니다**. ExactTarget 구성 창이 열립니다.

   ![chlimage_1-182](assets/chlimage_1-182.png)

1. Enter a title and optionally, a name and click **Create**. *** ExactTarget 설정** 구성 창이 열립니다.

   ![chlimage_1-31](assets/chlimage_1-31.jpeg)

1. 사용자 이름, 암호를 입력하고 API 끝점을 선택합니다(예: **https://webservice.exacttarget.com/Service.asmx**).
1. ExactTarget에 **연결을 클릭합니다.** 성공적으로 연결되면 성공 대화 상자가 표시됩니다. 확인 **을** 클릭하여 창을 종료합니다.

   ![chlimage_1-32](assets/chlimage_1-32.jpeg)

1. 가능한 경우 계정을 선택합니다. 이 계정은 Enterprise 2.0 고객을 위한 것입니다. **확인**&#x200B;을 클릭합니다.

   ExactTarget이 구성되었습니다. 편집을 클릭하여 구성을 편집할 수 **있습니다**. ExactTarget으로 이동을 클릭하여 ExactTarget **으로 이동할 수 있습니다**.

1. AEM에서 데이터 확장 기능을 제공합니다. ExactTarget 데이터 확장 열을 가져올 수 있습니다. 성공적으로 생성된 ExactTarget 구성 옆에 나타나는 &quot;+&quot; 기호를 클릭하여 구성할 수 있습니다. 드롭다운 목록에서 기존 데이터 확장자를 선택할 수 있습니다. 데이터 확장 구성 방법에 대한 자세한 내용은 [ExactTarget 설명서를 참조하십시오](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships).

   가져온 데이터 확장 열은 나중에 **텍스트 및 개인화 구성 요소를 통해 사용할 수** 있습니다.

   ![chlimage_1-33](assets/chlimage_1-33.jpeg)

### 도구를 통한 ExactTarget 구성 {#configuring-exacttarget-via-tools}

도구에서 ExactTarget 구성을 만들려면:

1. 시작 페이지에서 **도구를 클릭합니다**. 또는 이동 경로를 통해 직접 탐색합니다 `https://<hostname>:<port>/misadmin#/etc`.
1. 도구 **, Cloud Services 구성**, **ExactTarget** 순으로 **선택합니다**.
1. Click **New** to open the **Create Page **window.

   ![chlimage_1-34](assets/chlimage_1-34.jpeg)

1. Enter the **Title** and optionally the **Name**, and click **Create**.
1. 이전 절차의 4단계에서 설명한 대로 구성 정보를 입력합니다. 해당 절차에 따라 ExactTarget 구성을 마칩니다.

### 여러 구성 추가 {#adding-multiple-configurations}

여러 구성을 추가하려면:

1. 시작 페이지에서 **Cloud Services** 을 클릭하고 **ExactTarget을 클릭합니다**. 하나 **이상의 ExactTarget 구성을 사용할 수 있는 경우 표시되는 구성** 표시 단추를 클릭합니다. 사용 가능한 모든 구성이 나열됩니다.
1. 사용 가능한 구성 옆에 있는 **+** 서명을 클릭합니다. 그러면 구성 **만들기** 창이 열립니다. 이전 구성 절차에 따라 새 구성을 만듭니다.

