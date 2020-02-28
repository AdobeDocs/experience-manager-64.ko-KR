---
title: 자산 선택기
description: 자산 선택기를 사용하여 AEM(Adobe Experience Manager) 자산 내에서 자산에 대한 메타데이터를 검색, 필터링, 검색 및 페치하는 방법을 알아봅니다. 자산 선택기 인터페이스를 사용자 지정하는 방법도 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Asset Selector {#asset-selector}

>[!NOTE]
>
>이전 버전의 AEM에서 자산 [선택기의](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) 이름이 자산 선택기로 지정되었습니다.

자산 선택기를 사용하면 AEM(Adobe Experience Manager) 자산 내에서 자산을 검색, 필터링 및 검색할 수 있습니다. 자산 선택기를 사용하여 선택한 자산의 메타데이터를 가져올 수도 있습니다. 자산 선택기 인터페이스를 사용자 정의하려면 지원되는 요청 매개 변수로 시작할 수 있습니다. 이러한 매개 변수는 특정 시나리오에 대한 자산 선택기 컨텍스트를 설정합니다.

현재, 요청 매개 변수(이미지/비디오/텍스트 `Asset Type` )와&#x200B;*(*&#x200B;단일 `Selection mode` /다중&#x200B;**)를 자산 선택기에 대한 컨텍스트 정보로 전달할 수 있습니다. 이 정보는 선택 항목 전체에서 그대로 유지됩니다.

자산 선택기는 HTML5 **Window.postMessage** 메시지를 사용하여 선택한 자산에 대한 데이터를 수신자에게 보냅니다.

자산 선택기는 Granite의 기본 피커 어휘를 기반으로 합니다. 기본적으로 자산 선택기는 찾아보기 모드에서 작동합니다. 그러나 Omnisearch 경험을 사용하여 필터를 적용하여 특정 자산에 대한 검색을 조정할 수 있습니다.

CQ 컨테이너의 일부인지 여부에 관계없이 모든 웹 페이지를 자산 선택기(`https://[AEM_server]:[port]/aem/assetpicker.html`)와 통합할 수 있습니다.

## 컨텍스트 매개 변수 {#contextual-parameters}

URL에 다음 요청 매개 변수를 전달하여 특정 컨텍스트에서 자산 선택기를 시작할 수 있습니다.

| 이름 | 값 | 예 | 목적 |
|---|---|---|---|
| 리소스 접미사(B) | URL에서 리소스 접미어로 폴더 경로:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | 특정 폴더를 선택한 상태로 자산 선택기를 실행하려면(예: 폴더를 `/content/dam/we-retail/en/activities` 선택한 경우) URL은 다음과 같은 형식이어야 합니다. `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | 자산 선택기를 시작할 때 특정 폴더를 선택해야 하는 경우 리소스 접미어로 전달합니다. |
| mode | 단일, 다중 | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | 여러 모드에서 자산 선택기를 사용하여 여러 자산을 동시에 선택할 수 있습니다. |
| mimetype | 자산의 MIMETYPE(`/jcr:content/metadata/dc:format`와일드카드도 지원됨) | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation&mimetype=*png`</li></ul> | MIME 유형을 기반으로 자산을 필터링하는 데 사용합니다. |
| 문제가 발생합니다 | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | 이러한 매개 변수를 사용하여 자산 선택기를 [화강암 대화 상자]로 엽니다. 이 옵션은 [granite Path Field]를 통해 자산 선택기를 실행하고 이를 pickerSrc URL로 구성할 때만 적용됩니다. |
| assettype(S) | 이미지, 문서, 멀티미디어, 보관 | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=archives`</li> | 전달된 값을 기준으로 자산 유형을 필터링하려면 이 옵션을 사용합니다. |
| 루트 | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | 자산 선택기의 루트 폴더를 지정하려면 이 옵션을 사용합니다. 이 경우 자산 선택기를 사용하면 루트 폴더 아래에서 하위 자산(직접/간접)만 선택할 수 있습니다. |

## 자산 선택기 사용 {#using-the-asset-selector}

1. 자산 선택기 인터페이스에 액세스하려면 로 `https://[AEM_server]:[port]/aem/assetpicker`이동합니다.
1. 원하는 폴더로 이동하고 하나 이상의 자산을 선택합니다.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   또는 OmniSearch 상자에서 원하는 자산을 검색한 다음 선택할 수 있습니다.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   OmniSearch 상자를 사용하여 자산을 검색하는 경우 필터 창에서 다양한 필터를 선택하여 **[!UICONTROL 검색을]** 조정할 수 있습니다.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. 도구 모음에서 **[!UICONTROL 선택을]** 탭/클릭합니다.
