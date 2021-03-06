---
title: MSM을 사용하여 자산 재사용
description: 상위 자산에서 파생되고 상위 자산에 연결된 여러 페이지/폴더에서 자산을 사용합니다. 자산이 기본 사본과 계속 동기화되며 몇 번의 클릭으로 상위 자산에서 업데이트를 받습니다.
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management,Multi Site Manager
role: User,Admin,Architect
exl-id: a8e9f8de-ca84-4107-8f73-2fc75eeae1f1
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '3159'
ht-degree: 0%

---

# [!DNL Assets]에 MSM을 사용하여 자산 재사용 {#reuse-assets-using-msm-for-assets}

[!DNL Adobe Experience Manager]의 MSM(Multi Site Manager) 기능을 사용하면 한 번 작성되고 여러 웹 위치에서 다시 사용할 수 있습니다. [!DNL Assets] 기능에 대한 MSM과 같은 디지털 자산에 사용할 수 있습니다. [!DNL Assets]에 MSM을 사용하면 다음 작업을 수행할 수 있습니다.

* 자산을 한 번 만든 다음 이러한 자산의 사본을 만들어 사이트의 다른 영역에서 재사용할 수 있습니다.
* 동기화에 여러 사본을 유지하고 원본 기본 복사본을 한 번 업데이트하여 변경 사항을 하위 복사본에 푸시합니다.
* 상위 자산과 하위 자산 간의 연결을 일시적으로 또는 영구적으로 일시 중단하여 로컬 변경을 수행합니다.

## 전제 조건 {#msm-prerequisites}

[!DNL Assets]에 MSM을 사용하려면 [!DNL Experience Manager] 6.4 서비스 팩 5 이상을 설치하십시오. 자세한 내용은 최신 서비스 팩](/help/release-notes/sp-release-notes.md)의 릴리스 노트 [를 참조하십시오.

## 이점 및 개념 이해 {#understand-benefits-concepts}

### 작동 방법 및 이점 {#how-it-works-the-benefits}

여러 웹 위치에서 동일한 콘텐츠(텍스트 및 자산)를 재사용하는 사용 시나리오를 이해하려면 [가능한 MSM 시나리오](/help/sites-administering/msm.md)를 참조하십시오. [!DNL Experience Manager] 는 LC(Live Copy)라고 하는 원래 자산과 연결된 사본 사이의 링크를 유지합니다. 유지 관리되는 링크를 사용하면 중앙 집중식 변경 사항을 여러 Live Copy에 푸시할 수 있습니다. 따라서 중복 복제본 관리 제한 사항을 그대로 유지하면서 더욱 신속하게 업데이트할 수 있습니다. 변경 사항의 전달은 오류가 없고 중앙 집중화입니다. 기능을 사용하면 선택한 Live Copy로 제한되는 업데이트를 수행할 수 있습니다. 사용자는 상속이 중단되는 연결을 분리하고, 다음에 기본 복사본을 업데이트하고 변경 사항을 롤아웃할 때 덮어쓰지 않는 로컬 편집 작업을 수행할 수 있습니다. 몇 개의 선택한 메타데이터 필드나 전체 자산에 대해 분리를 수행할 수 있습니다. 이를 통해 원래 기본 복사본에서 상속된 자산을 로컬로 업데이트할 수 있습니다.

MSM은 소스 자산과 Live Copy 간의 라이브 관계를 유지하여 다음과 같습니다.

* 소스 자산 변경 사항은 Live Copy에도 적용(롤아웃)되며, Live Copy는 소스와 동기화됩니다.

* 라이브 관계를 일시 중단하거나 일부 제한된 필드에 대한 상속을 제거하여 Live Copy를 업데이트할 수 있습니다. 소스 수정 사항은 더 이상 Live Copy에 적용되지 않습니다.

### MSM for Assets 용어 {#glossary-msm-for-assets}

* **소스:** 원래 자산 또는 폴더입니다. Live Copy가 파생되는 기본 복사본.

* **Live Copy:** 소스와 동기화 중인 소스 자산/폴더의 사본입니다. Live Copy는 추가적인 Live Copy의 소스가 될 수 있습니다. [LC를 만드는 방법](#create-live-copy-asset)을 참조하십시오.

* **상속:** Live Copy 자산/폴더와 시스템에서 업데이트를 보낼 위치를 기억하기 위해 사용하는 소스 간의 링크/참조입니다. 상속은 메타데이터 필드의 세부 수준에 있습니다. 소스와 라이브 카피 간의 라이브 관계를 유지하면서 선택적 메타데이터 필드에 대한 상속을 제거할 수 있습니다.

* **롤아웃**: Live Copy로 소스 다운스트림에 수행된 수정 사항을 푸시하는 작업입니다. 롤아웃 작업을 사용하여 한 번에 하나 이상의 Live Copy를 업데이트할 수 있습니다. [롤아웃](#rollout-action)을 참조하십시오.

* **롤아웃 구성:** 동기화되는 속성, 방법 및 시기를 결정하는 규칙입니다. 이러한 구성은 Live Copy를 만들 때 적용됩니다. 나중에 편집할 수 있습니다. 하위 자산이 상위 자산에서 롤아웃 구성을 상속할 수 있습니다. [!DNL Assets]에 대한 MSM의 경우 표준 롤아웃 구성만 사용하십시오. 다른 롤아웃 구성은 [!DNL Assets]에 대해 MSM에 사용할 수 없습니다.

* **동기화:** 롤아웃 외에 소스에서 Live Copy로 업데이트를 전송하여 소스와 Live Copy 간에 패리티를 제공하는 또 다른 작업입니다. 특정 Live Copy에 대한 동기화가 시작되고 작업이 소스에서 변경 사항을 가져옵니다. 이 작업을 사용하면 Live Copy 중 하나만 업데이트할 수 있습니다. [동기화 작업](#about-synchronize-action)을 참조하십시오.

* **일시 중단:** Live Copy와 소스 자산/폴더 간의 라이브 관계를 일시적으로 제거합니다. 관계를 재개할 수 있습니다. [일시 중단 작업](#suspend-and-resume-relationship)을 참조하십시오.

* **다시 시작:**  Live Copy가 소스에서 업데이트를 다시 수신하도록 Live Relationship을 다시 시작합니다. [작업 다시 시작](#suspend-and-resume-relationship)을 참조하십시오.

* **재설정:** 재설정 작업을 수행하면 로컬 변경 내용을 덮어써서 Live Copy를 다시 소스의 복제본으로 만듭니다. 또한 상속 취소를 제거하고 모든 메타데이터 필드에 대한 상속을 재설정합니다. 나중에 로컬 수정 작업을 수행하려면 특정 필드의 상속을 다시 취소해야 합니다. [LC](#make-local-modifications-to-live-copy)의 로컬 수정 내용을 참조하십시오.

* **분리:** Live Copy 자산/폴더의 Live Relationship을 완전히 제거할 수 있습니다. 작업을 분리하면 Live Copy가 소스에서 업데이트를 받지 못하고 Live Copy가 되지 않습니다. [관계 제거](#remove-live-relationship)를 참조하십시오.

## 자산의 Live Copy 만들기 {#create-live-copy-asset}

하나 이상의 소스 자산 또는 폴더에서 Live Copy를 생성하려면 다음 중 하나를 수행합니다.

* **방법 1**: 소스 자산을 선택하고 맨 위 **[!UICONTROL 에 있는 만들기]**  >  **[!UICONTROL 라이브]** 카피온 도구 모음을 클릭합니다.
* **방법 2**: 사용자  [!DNL Experience Manager] 인터페이스에서  **[!UICONTROL 만들기 > 인터페이스]** 의 오른쪽 위 모서리에서 라이브 카피피 를 클릭합니다.

자산 또는 폴더의 Live Copy를 한 번에 하나씩 만들 수 있습니다. 자산 또는 Live Copy 자체인 폴더에서 파생된 Live Copy를 만들 수 있습니다.

컨텐츠 조각(CF)은 사용 사례에 대해 지원되지 않습니다. Live Copy를 만들려고 하면 CF가 관계 없이 그대로 복사됩니다. 복사된 CF는 시간 내에 스냅샷이며 원래 CF가 업데이트될 때 업데이트되지 않습니다.

첫 번째 방법을 사용하여 Live Copy를 만들려면 다음 단계를 수행합니다.

1. 소스 자산 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 만들기 > Live Copy]**를 클릭합니다.
   ![인터페이스에서 Live Copy  [!DNL Experience Manager] 만들기](assets/lc_create1.png)
1. 소스 자산 또는 폴더를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 제목과 이름을 입력합니다. 자산에 자식이 없습니다. 폴더의 Live Copy를 만들 때 하위 항목을 포함하거나 제외하도록 선택할 수 있습니다.
1. 롤아웃 구성을 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

두 번째 방법을 사용하여 Live Copy를 만들려면 다음 단계를 수행합니다.

1. [!DNL Experience Manager] 인터페이스의 오른쪽 위 모서리에서 **[!UICONTROL 만들기 > Live Copy]**를 클릭합니다.
   ![인터페이스에서 Live Copy  [!DNL Experience Manager] 만들기](assets/lc_create2.png)
1. 소스 자산 또는 폴더를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 대상 폴더를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 제목과 이름을 입력합니다. 자산에 자식이 없습니다. 폴더의 Live Copy를 만들 때 하위 항목을 포함하거나 제외하도록 선택할 수 있습니다.
1. 롤아웃 구성을 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

>[!NOTE]
>
>소스 또는 Live Copy가 이동되면 관계가 유지됩니다. Live Copy가 삭제되면 관계가 제거됩니다.

## 소스 및 Live Copy의 다양한 속성 및 상태 보기 {#view-properties-statuses-source-and-lc}

관계, 동기화, 롤아웃 등과 같은 Live Copy의 정보 및 MSM 관련 상태를 [!DNL Experience Manager] 사용자 인터페이스의 다양한 영역에서 볼 수 있습니다. 자산 및 폴더에 대해 다음 두 가지 방법이 작동합니다.

* Live Copy 자산을 선택하고 **[!UICONTROL 속성]** 페이지에서 정보를 찾습니다.
* 소스 폴더를 선택하고 **[!UICONTROL Live Copy 콘솔]**&#x200B;에서 각 Live Copy의 세부 정보를 찾습니다.

>[!TIP]
>
>몇 개의 개별 라이브 카피의 상태를 확인하려면 첫 번째 메서드를 사용하여 **[!UICONTROL 속성]** 페이지를 확인합니다. 많은 Live Copy의 상태를 확인하려면 두 번째 메서드를 사용하여 **[!UICONTROL 관계 상태]** 페이지를 확인합니다.

### Live Copy의 정보 및 상태 {#information-status-of-one-lc}

Live Copy 자산 또는 폴더의 정보 및 상태를 확인하려면 다음 단계를 수행합니다.

1. Live Copy 자산 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p` 를 사용합니다.
1. **[!UICONTROL Live Copy]**를 클릭합니다. 소스의 경로, 일시 중단 상태, 동기화 상태, 마지막 롤아웃 날짜 및 마지막 롤아웃을 수행한 사용자를 확인할 수 있습니다.
   ![Live Copy 정보 및 상태가 속성의 콘솔에 표시됩니다](assets/lc_folder_properties.png)
1. 하위 자산이 Live Copy 구성을 빌리는 경우 활성화하거나 비활성화할 수 있습니다.
1. Live Copy에 대한 옵션을 선택하여 상위 항목에서 롤아웃 구성을 상속하거나 구성을 변경할 수 있습니다.

### 폴더의 모든 Live Copy에 대한 정보 및 상태 {#information-status-of-all-lcs-of-folder}

[!DNL Experience Manager] 소스 폴더의 모든 라이브 카피의 동상을 확인하는 콘솔을 제공합니다. 이 콘솔에는 모든 하위 자산의 상태가 표시됩니다.

1. 소스 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p` 를 사용합니다.
1. **[!UICONTROL Live Copy 소스]**&#x200B;를 클릭합니다. 콘솔을 열려면 **[!UICONTROL Live Copy 개요]**를 클릭합니다. 이 대시보드는 모든 하위 자산의 최상위 수준 상태를 제공합니다.
   ![소스의 Live Copy 콘솔에서 Live Copy 상태 보기](assets/lc_statuses.png)
1. Live Copy 폴더의 각 자산에 대한 세부 정보를 보려면 자산을 선택하고 도구 모음에서 **[!UICONTROL 관계 상태]**를 클릭합니다.
   ![폴더에 있는 Live Copy 하위 자산의 세부 정보 및 상태](assets/lc_relationship_status.png)

>[!TIP]
>
>너무 많이 탐색하지 않아도 다른 폴더의 Live Copy 상태를 빠르게 볼 수 있습니다. **[!UICONTROL Live Copy 개요]** 인터페이스의 위쪽 부분에서 폴더를 변경합니다.

### 소스에 대한 참조 레일의 빠른 작업 {#quick-actions-from-references-rail-for-source}

소스 자산 또는 폴더의 경우 다음 정보를 확인하고 참조 레일에서 바로 다음 작업을 수행할 수 있습니다.

* Live Copy 경로를 참조하십시오.
* [!DNL Experience Manager] 사용자 인터페이스에서 특정 Live Copy를 열거나 표시합니다.
* 업데이트를 특정 Live Copy에 동기화합니다.
* 특정 Live Copy에 대한 관계를 일시 중단하거나 롤아웃 구성을 변경합니다.
* Live Copy 개요 콘솔에 액세스합니다.

소스 자산 또는 폴더를 선택하고 왼쪽 레일을 열고 **[!UICONTROL 참조]**&#x200B;를 클릭합니다. 또는 자산 또는 폴더를 선택하고 키보드 단축키 `Alt + 4`을 사용합니다.

![선택한 소스의 참조 레일에서 사용할 수 있는 작업 및 정보](assets/lc_referencerail_source.png)

특정 Live Copy의 경우 **[!UICONTROL Edit Live Copy]**&#x200B;를 클릭하여 관계를 일시 중단하거나 롤아웃 구성을 변경합니다.

![특정 Live Copy의 경우, 소스 자산을 선택하면 참조 레일에서 관계 일시 중단 또는 롤아웃 구성 변경 옵션에 액세스할 수 있습니다](assets/lc_edit_referencerail.png)

### Live Copy에 대한 참조 레일의 빠른 작업 {#quick-actions-from-references-rail-for-live-copy}

Live Copy 자산 또는 폴더의 경우 다음 정보를 확인하고 참조 레일에서 바로 다음 작업을 수행할 수 있습니다.

* 소스 경로를 참조하십시오.
* [!DNL Experience Manager] 사용자 인터페이스에서 특정 Live Copy를 열거나 표시합니다.
* 업데이트를 롤아웃합니다.

Live Copy 자산 또는 폴더를 선택하고 왼쪽 레일을 열고 **[!UICONTROL 참조]**&#x200B;를 클릭합니다. 또는 자산 또는 폴더를 선택하고 키보드 단축키 `Alt + 4`을 사용합니다.

![선택한 Live Copy에 대한 참조 레일에서 사용할 수 있는 작업](assets/lc_referencerail.png)

## 소스에서 Live Copy로 수정 사항 전달 {#propagate-modifications-from-source-to-live-copies}

소스가 수정되면 동기화 작업 또는 롤아웃 작업을 사용하여 변경 사항을 Live Copy에 전파할 수 있습니다. 두 작업 간의 차이점을 이해하려면 [용어집](#glossary-msm-for-assets)을 참조하십시오.

### 롤아웃 작업 {#rollout-action}

소스 자산에서 롤아웃 작업을 시작하고 전체 또는 일부 선택 Live Copy를 업데이트할 수 있습니다.

1. Live Copy 자산 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p` 를 사용합니다.
1. **[!UICONTROL Live Copy 소스]**&#x200B;를 클릭합니다. 도구 모음에서 **[!UICONTROL 롤아웃]**&#x200B;을 클릭합니다.
1. 업데이트할 Live Copy를 선택합니다. **[!UICONTROL 롤아웃]**&#x200B;을 클릭합니다.
1. 하위 자산에 대한 업데이트를 롤아웃하려면 **[!UICONTROL 롤아웃 소스 와 모든 하위]**를 선택합니다.
   ![소스 수정 사항을 일부 또는 모든 Live Copy에 롤아웃합니다.](assets/lc_rollout_page.png)

>[!NOTE]
>
>소스 자산에서 수정한 사항은 직접 관련된 Live Copy에만 롤아웃됩니다. Live Copy가 다른 Live Copy에서 파생된 경우 수정 사항이 파생된 Live Copy로 롤아웃되지 않습니다.

또는 특정 Live Copy를 선택한 후 [!UICONTROL 참조] 레일에서 롤아웃 작업을 시작할 수 있습니다. 자세한 내용은 Live Copy](#quick-actions-from-references-rail-for-live-copy)에 대한 참조 레일의 빠른 작업 [을 참조하십시오. 이 롤아웃 방법에서는 선택한 Live Copy 및 선택적으로 해당 하위 만 업데이트됩니다.

![소스 수정 사항을 선택한 Live Copy에 롤아웃합니다.](assets/lc_rollout_dialog.png)

### 동기화 작업 기본 정보 {#about-synchronize-action}

동기화 작업은 소스 수정 사항만 선택한 Live Copy로 가져옵니다. 동기화 작업은 상속을 취소한 후 수행된 로컬 수정 사항을 준수하며 유지 관리합니다. 로컬 수정 내용을 덮어쓰지 않고 취소된 상속이 다시 설정되지 않습니다. 세 가지 방법으로 동기화 작업을 시작할 수 있습니다.

| [!DNL Experience Manager] 인터페이스에서 위치 | 사용 시기 및 이유 | 사용 방법 |
|---|---|---|
|  참조:레일 | 소스를 이미 선택한 경우 신속하게 동기화합니다. | 소스](#quick-actions-from-references-rail-for-source)에 대한 참조 레일의 빠른 작업 을 참조하십시오.[ |
| [!UICONTROL 속성] 페이지의 도구 모음 | Live Copy 속성이 이미 열려 있으면 동기화를 시작합니다. | [Live Copy 동기화](#synchronize-live-copy)를 참조하십시오 |
| [!UICONTROL Live Copy ] 개요 콘솔 | 소스 폴더가 선택되거나 [!UICONTROL Live Copy 개요] 콘솔이 이미 열려 있는 경우 여러 자산을 빠르게 동기화(반드시 필요한 것은 아님)합니다. 한 번에 한 자산에 대해 동기화 작업이 시작되지만 한 번에 여러 자산에 대해 동기화하는 것이 더 빠릅니다. | Live Copy 폴더에 있는 많은 자산에 대한 작업 [을 참조하십시오](#take-actions-on-many-assets-in-lcfolder) |

### Live Copy 동기화 {#synchronize-live-copy}

동기화 작업을 시작하려면 Live Copy의 **[!UICONTROL 속성]** 페이지를 열고 **[!UICONTROL Live Copy]** 를 클릭하고 도구 모음에서 원하는 작업을 클릭합니다.

동기화 작업과 관련된 상태 및 정보를 보려면 폴더](#information-status-of-all-lcs-of-folder)모든 Live Copy의 정보 및 상태 를 참조하십시오.[

![동기화 작업은 소스에 대한 변경 내용을 가져옵니다.](assets/lc_sync.png)

>[!NOTE]
>
>관계가 일시 중단된 경우 도구 모음에서 동기화 작업을 사용할 수 없습니다. 동기화 작업은 [!UICONTROL 참조] 레일에서 사용할 수 있지만 성공적인 롤아웃 시에도 수정 사항은 전파되지 않습니다.

## 관계 일시 중단 및 다시 시작 {#suspend-and-resume-relationship}

Live Copy가 소스 자산 또는 폴더의 수정 사항을 받지 않도록 일시적으로 관계를 일시 중단할 수 있습니다. Live Copy에서 소스로부터 수정 사항을 수신하기 위해 관계를 다시 시작할 수도 있습니다.

일시 중단하거나 다시 시작하려면 Live Copy의 **[!UICONTROL 속성]** 페이지를 열고 **[!UICONTROL Live Copy]** 를 클릭하고 도구 모음에서 원하는 작업을 클릭합니다.

또는 **[!UICONTROL Live Copy 개요]** 콘솔에서 Live Copy 폴더에 있는 여러 자산의 관계를 빠르게 일시 중단하거나 다시 시작할 수 있습니다. [Live Copy 폴더에 있는 많은 자산에 대한 작업 수행](#take-actions-on-many-assets-in-lcfolder)을 참조하십시오.

## Live Copy에 로컬 수정 {#make-local-modifications-to-live-copy}

Live Copy는 생성될 때 원본 소스의 복제본입니다. Live Copy의 메타데이터 값은 소스에서 상속됩니다. 메타데이터 필드는 소스 자산의 각 필드와 함께 상속을 개별적으로 유지 관리합니다.

그러나 몇 가지 선택 속성을 변경하기 위해 Live Copy에 로컬 수정 작업을 수행할 수 있는 유연성이 있습니다. 로컬 수정 작업을 수행하려면 원하는 속성의 상속을 취소합니다. 하나 이상의 메타데이터 필드의 상속이 취소되면 자산의 라이브 관계와 다른 메타데이터 필드의 상속이 유지됩니다. 모든 동기화 또는 롤아웃은 로컬 수정 사항을 덮어쓰지 않습니다. 이렇게 하려면 Live Copy 자산의 **[!UICONTROL 속성]** 페이지를 열고 메타데이터 필드 옆에 있는 **[!UICONTROL 상속 취소]** 옵션을 클릭합니다.

모든 로컬 수정 사항을 실행 취소하고 자산을 소스의 상태로 되돌릴 수 있습니다. 재설정 작업은 취소할 수 없으며 모든 로컬 수정 사항을 즉시 재정의하고 모든 메타데이터 필드에 상속을 재설정합니다. 되돌리려면 Live Copy 자산의 **[!UICONTROL 속성]** 페이지에서 도구 모음에서 **[!UICONTROL 재설정]**&#x200B;을 클릭합니다.

![재설정 작업은 로컬 편집 내용을 덮어쓰고, Live Copy의 일부를 해당 소스로 가져옵니다](assets/lc_reset.png)

## 라이브 관계 제거 {#remove-live-relationship}

분리 작업을 사용하여 소스와 Live Copy 간의 관계를 완전히 제거할 수 있습니다. Live Copy가 분리된 후 독립형 자산 또는 폴더가 됩니다. 분리한 직후 [!DNL Experience Manager] 인터페이스에 새 자산으로 표시됩니다. 소스에서 Live Copy를 분리하려면 다음 단계를 수행합니다.

1. Live Copy 자산 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 `p` 를 사용합니다.
1. **[!UICONTROL Live Copy]**&#x200B;를 클릭합니다. 도구 모음에서 **[!UICONTROL 분리]**&#x200B;를 클릭합니다. 표시된 대화 상자에서 **[!UICONTROL 분리]**를 클릭합니다.
   ![분리 작업은 소스와 Live Copy 간의 관계를 완전히 제거합니다](assets/lc_detach.png)

>[!CAUTION]
>
>대화 상자에서 [!UICONTROL 분리]를 클릭하면 관계가 즉시 제거됩니다. 속성 페이지에서 [!UICONTROL 취소]를 클릭하여 실행 취소할 수 없습니다.

또는 **[!UICONTROL Live Copy 개요]** 콘솔에서 Live Copy 폴더에 있는 여러 자산을 빠르게 분리할 수 있습니다. [Live Copy 폴더에 있는 많은 자산에 대한 작업 수행](#take-actions-on-many-assets-in-lcfolder)을 참조하십시오.

## Live Copy 폴더에 있는 많은 자산에 대한 작업 수행 {#take-actions-on-many-assets-in-lcfolder}

Live Copy 폴더에 여러 개의 자산이 있는 경우 각 자산에 대해 작업을 시작하는 것은 지루할 수 있습니다. Live Copy 콘솔에서 많은 자산에 대한 기본 작업을 빠르게 시작할 수 있습니다. 위의 방법은 개별 자산에 대해 계속 작동합니다.

1. 소스 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭합니다. 또는 키보드 단축키 p를 사용합니다.
1. Live Copy 소스를 클릭합니다. 콘솔을 열려면 **[!UICONTROL Live Copy 개요]**&#x200B;를 클릭합니다.
1. 이 대시보드에서 Live Copy 폴더에서 Live Copy 자산을 선택합니다. 도구 모음에서 원하는 작업을 클릭합니다. 사용 가능한 작업은 **[!UICONTROL 편집]**, **[!UICONTROL 동기화]**, **[!UICONTROL 재설정]**, **[!UICONTROL 일시 중단]** 및 **[!UICONTROL 분리]**입니다. 선택한 소스 폴더와 라이브 관계가 있는 임의의 Live Copy 폴더의 모든 자산에서 이러한 작업을 빠르게 시작할 수 있습니다.
   ![Live Copy 개요 콘솔에서 Live Copy 폴더의 많은 자산을 쉽게 업데이트할 수 있습니다](assets/lc_console_update_assets.png)

## 자산에 대한 MSM 확장 {#extend-msm-for-assets}

[!DNL Experience Manager] msm Java API를 사용하여 기능을 확장할 수 있습니다. Assets의 경우 확장은 Site용 MSM에서 작동하는 것과 동일하게 작동합니다. 특정 작업에 대한 자세한 내용은 [MSM](../sites-developing/extending-msm.md) 확장 및 다음 섹션을 참조하십시오.

* [API 개요](../sites-developing/extending-msm.md#overview-of-the-java-api)
* [새 동기화 작업 만들기](../sites-developing/extending-msm.md#creating-a-new-synchronization-action)
* [새 롤아웃 구성 만들기](../sites-developing/extending-msm.md#creating-a-new-rollout-configuration)
* [간단한 LiveActionFactory 클래스를 만들고 사용합니다](../sites-developing/extending-msm.md#creating-and-using-a-simple-liveactionfactory-class)

>[!NOTE]
>
>* MSM for Site의 블루프린트를 Assets용 MSM의 Live Copy 소스라고 합니다.
>* MSM for Assets에서는 사이트 만들기 마법사의 장 단계를 제거할 수 없습니다.
>* MSM for Assets에서는 페이지 속성(터치 지원 UI)에서 MSM 잠금 구성이 지원되지 않습니다.


## 자산 관리 작업이 Live Copy에 미치는 영향 {#impact-of-asset-management-tasks-on-live-copies}

Live Copy 및 소스는 디지털 자산으로서 어느 정도 관리할 수 있는 자산 또는 폴더입니다. [!DNL Experience Manager]의 일부 자산 관리 작업은 Live Copy에 특정 영향을 줍니다.

* Live Copy를 복사하면 첫 번째 Live Copy와 동일한 소스를 사용하는 Live Copy 자산이 만들어집니다.
* 소스 또는 해당 Live Copy를 이동하면 Live Relationship이 유지됩니다.
* Live Copy 자산에 대해 편집 작업이 작동하지 않습니다.
* Live Copy 자산에 체크 아웃 작업을 사용할 수 없습니다.
* 소스 폴더의 경우 검토 작업을 만드는 옵션을 사용할 수 있습니다.
* 목록 보기 및 열 보기에서 자산 목록을 볼 때 Live Copy 자산 또는 폴더에 대해 &#39;live copy&#39;가 표시됩니다. 이렇게 하면 폴더에서 Live Copy를 쉽게 식별할 수 있습니다.

## 자산 및 사이트에 대한 MSM 비교 {#compare-msm-for-assets-and-sites}

더 많은 시나리오에서 자산에 대한 MSM은 사이트 기능에 대한 MSM의 동작과 일치합니다. 참고 사항의 몇 가지 주요 차이점은 다음과 같습니다.

* Sites에서 블루프린트 및 Live Copy를 비교할 수 있지만 Assets에서 소스를 Live Copy와 비교할 수는 없습니다.
* 사이트에는 일반적으로 1차 하위 구성요소가 있지만 Assets는 이를 포함하지 않습니다. 개별 자산의 라이브 카피를 만들 때 하위 항목을 포함하거나 제외하는 옵션이 없습니다.
* MSM for Assets에서는 사이트 만들기 마법사의 장 단계를 제거할 수 없습니다.
* MSM for Assets에서는 페이지 속성(터치 지원 UI)에서 MSM 잠금 구성이 지원되지 않습니다.
* Assets용 MSM의 경우 표준 롤아웃 구성만 사용합니다. 자산에 대한 MSM에 다른 롤아웃 구성을 사용할 수 없습니다.

## 자산에 대한 MSM의 제한 사항 {#limitations-of-msm-for-assets}

다음은 자산에 대한 MSM의 제한 사항입니다.

* 컨텐츠 조각(CF)은 사용 사례에 대해 지원되지 않습니다. Live Copy를 만들려고 하면 CF가 관계 없이 그대로 복사됩니다. 복사된 CF는 시간 내에 스냅샷이며 원래 CF가 업데이트될 때 업데이트되지 않습니다.

* MSM이 메타데이터 원본에 쓰기 기능을 사용하도록 설정되어 있지 않습니다. 원본에 쓰기 시작하면 상속이 중단됩니다.
