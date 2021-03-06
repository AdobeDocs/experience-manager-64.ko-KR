---
title: 번역 프로젝트 만들기
description: AEM에서 번역 프로젝트를 만드는 방법을 알아봅니다.
contentOwner: AG
feature: Translation
role: Architect,Admin
exl-id: 1b931fef-eed0-4758-993d-cdf8d478fb6f
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '1939'
ht-degree: 6%

---

# 번역 프로젝트 만들기 {#creating-translation-projects}

언어 사본을 만들려면 자산 UI의 참조 레일에서 사용할 수 있는 다음 언어 복사 워크플로우 중 하나를 트리거하십시오.

**작성 및 번역**

이 워크플로우에서 번역할 자산이 번역하려는 언어의 언어 루트에 복사됩니다. 또한 선택한 옵션에 따라 프로젝트 콘솔에서 자산에 대한 번역 프로젝트가 만들어집니다. 설정에 따라 번역 프로젝트를 수동으로 시작하거나 번역 프로젝트를 만드는 즉시 자동으로 실행할 수 있습니다.

**언어 복사 업데이트**

이 워크플로우를 실행하여 추가 자산 그룹을 번역하고 특정 로케일의 언어 복사본에 포함합니다. 이 경우 번역된 자산은 이미 이전에 번역된 자산이 들어 있는 대상 폴더에 추가됩니다.

>[!NOTE]
>
>자산 바이너리는 번역 서비스 공급자가 바이너리 변환을 지원하는 경우에만 변환됩니다.

>[!NOTE]
>
>PDF 및 InDesign 파일과 같은 복잡한 자산에 대한 번역 워크플로우를 실행하는 경우, 해당 하위 자산 또는 표현물(있는 경우)이 번역을 위해 제출되지 않습니다.

## 워크플로우 만들기 및 번역 {#create-and-translate-workflow}

작성 및 번역 워크플로우를 사용하여 처음으로 특정 언어의 언어 사본을 생성할 수 있습니다. 워크플로우는 다음 옵션을 제공합니다.

* 구조만 생성
* 새 번역 프로젝트 만들기
* 기존 번역 프로젝트에 추가

### 구조만 생성 {#create-structure-only}

**구조만 만들기** 옵션을 사용하여 대상 언어 루트 내에서 소스 폴더의 계층 구조와 일치하도록 대상 폴더 계층 구조를 만듭니다. 이 경우 소스 자산이 대상 폴더에 복사됩니다. 그러나 번역 프로젝트는 생성되지 않습니다.

1. Assets UI에서 대상 언어 루트에서 구조를 만들 소스 폴더를 선택합니다.
1. **[!UICONTROL 참조]** 창을 열고 **[!UICONTROL 복사]** 아래에 있는 **[!UICONTROL 언어 사본]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. 맨 아래에서 **[!UICONTROL 만들기 및 번역]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-58](assets/chlimage_1-58.png)

1. **[!UICONTROL Target 언어]** 목록에서 폴더 구조를 만들 언어를 선택합니다.

   ![chlimage_1-59](assets/chlimage_1-59.png)

1. **[!UICONTROL Project]** 목록에서 **[!UICONTROL 구조만 만들기]**&#x200B;를 선택합니다.

   ![chlimage_1-60](assets/chlimage_1-60.png)

1. **[!UICONTROL 만들기]**&#x200B;를 클릭/탭합니다. 대상 언어의 새 구조는 **[!UICONTROL 언어 사본]** 아래에 나열됩니다.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. 목록에서 구조를 클릭/탭한 다음, **[!UICONTROL Assets]**&#x200B;에 표시 를 클릭/탭하여 대상 언어 내의 폴더 구조로 이동합니다.

   ![chlimage_1-62](assets/chlimage_1-62.png)

### 새 번역 프로젝트 만들기 {#create-a-new-translation-project}

이 옵션을 사용하면 변환할 자산이 번역할 언어의 언어 루트에 복사됩니다. 선택한 옵션에 따라 프로젝트 콘솔에서 자산에 대한 번역 프로젝트가 만들어집니다. 설정에 따라 번역 프로젝트를 수동으로 시작하거나 번역 프로젝트를 만드는 즉시 자동으로 실행할 수 있습니다.

1. Assets UI에서 언어 사본을 만들 소스 폴더를 선택합니다.
1. **[!UICONTROL 참조]** 창을 열고 **[!UICONTROL 복사]** 아래에 있는 **[!UICONTROL 언어 사본]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-63](assets/chlimage_1-63.png)

1. 맨 아래에서 **[!UICONTROL 만들기 및 번역]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-64](assets/chlimage_1-64.png)

1. **[!UICONTROL Target 언어]** 목록에서 폴더 구조를 만들 언어를 선택합니다.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. **[!UICONTROL Project]** 목록에서 **[!UICONTROL 새 번역 프로젝트 만들기]**&#x200B;를 선택합니다.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. **[!UICONTROL 프로젝트 제목]** 필드에 프로젝트의 제목을 입력합니다.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. **[!UICONTROL 만들기]**&#x200B;를 클릭/탭합니다. 소스 폴더의 자산이 4단계에서 선택한 로케일의 대상 폴더에 복사됩니다.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. 폴더로 이동하려면 언어 사본을 선택하고 **[!UICONTROL 자산에 표시]**&#x200B;를 클릭합니다.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. 프로젝트 콘솔로 이동합니다. 번역 폴더가 프로젝트 콘솔에 복사됩니다.

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. 폴더를 열어 번역 프로젝트를 확인합니다.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. 프로젝트를 클릭/탭하여 세부 사항 페이지를 엽니다.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. 번역 작업의 상태를 보려면 **[!UICONTROL 번역 작업]** 타일의 하단에 있는 줄임표를 클릭합니다.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   작업 상태에 대한 자세한 내용은 [번역 작업의 상태 모니터링](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job)을 참조하십시오.

1. 자산 UI로 이동하고 번역된 각 자산에 대한 속성 페이지를 열어 번역된 메타데이터를 확인합니다.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   >[!NOTE]
   >
   >이 기능은 자산과 폴더에 모두 사용할 수 있습니다. 폴더 대신 자산을 선택하면 언어 루트에 대한 폴더의 전체 계층 구조가 복사되어 자산에 대한 언어 사본을 만듭니다.

### 기존 번역 프로젝트에 추가 {#add-to-existing-translation-project}

이 옵션을 사용하는 경우 이전 번역 워크플로우를 실행한 후 소스 폴더에 추가하는 자산에 대해 번역 워크플로우가 실행됩니다. 새로 추가된 자산만 이전에 번역된 자산이 포함된 대상 폴더에 복사됩니다. 이 경우에는 새 번역 프로젝트가 생성되지 않습니다.

1. 자산 UI에서 번역되지 않은 자산이 포함된 소스 폴더로 이동합니다.
1. 변환할 자산을 선택하고 **[!UICONTROL 참조 창]**&#x200B;을 엽니다. **[!UICONTROL 언어 사본]** 섹션에는 현재 사용 가능한 번역 사본 수가 표시됩니다.
1. **[!UICONTROL 사본]**&#x200B;아래에 있는 **[!UICONTROL 언어 사본]**&#x200B;을 클릭/탭합니다. 사용 가능한 번역 사본 목록이 표시됩니다.
1. 맨 아래에서 **[!UICONTROL 만들기 및 번역]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. **[!UICONTROL Target 언어]** 목록에서 폴더 구조를 만들 언어를 선택합니다.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. **[!UICONTROL Project]** 목록에서 **[!UICONTROL 기존 번역 프로젝트에 추가]**&#x200B;를 선택하여 폴더에서 번역 워크플로우를 실행합니다.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >**[!UICONTROL 기존 번역 프로젝트에 추가]** 옵션을 선택하면 프로젝트 설정이 기존 프로젝트의 설정과 정확히 일치하는 경우에만 번역 프로젝트가 기존 프로젝트에 추가됩니다. 그렇지 않으면 새 프로젝트가 만들어집니다.

1. **[!UICONTROL 기존 번역 프로젝트]** 목록에서 변환할 자산을 추가할 프로젝트를 선택합니다.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. **[!UICONTROL 만들기]**&#x200B;를 클릭/탭합니다. 변환할 자산이 대상 폴더에 추가됩니다. 업데이트된 폴더는 **[!UICONTROL 언어 사본]** 섹션 아래에 나열됩니다.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. 프로젝트 콘솔로 이동하고 추가한 기존 번역 프로젝트를 엽니다.
1. 프로젝트 세부 사항 페이지에서 번역 프로젝트 보기를 클릭/탭합니다.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. 번역 워크플로우에서 자산을 보려면 **번역 작업** 타일의 하단에 있는 생략 부호를 클릭/탭하십시오. 번역 작업 목록에는 자산 메타데이터와 태그에 대한 항목도 표시됩니다. 이 항목들은 자산의 메타데이터와 태그도 번역됨을 나타냅니다.

   >[!NOTE]
   >
   >태그나 메타데이터의 항목을 삭제하는 경우, 자산에 대해 태그나 메타데이터가 번역되지 않습니다.

   >[!NOTE]
   >
   >기계 번역을 사용하는 경우 자산 바이너리가 번역되지 않습니다.

   >[!NOTE]
   >
   >번역 작업에 추가하는 자산에 하위 자산이 포함되어 있는 경우, 하위 자산을 선택하고 번역을 위해 해당 자산을 제거하여 결함 없이 진행합니다.

1. 자산에 대한 번역을 시작하려면 **[!UICONTROL 번역 작업]** 타일의 화살표를 클릭/탭하고 목록에서 **[!UICONTROL 시작]**&#x200B;을 선택합니다.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   번역 작업 시작을 알리는 메시지가 나타납니다.

   ![chlimage_1-82](assets/chlimage_1-82.png)

1. 번역 작업의 상태를 보려면 **[!UICONTROL 번역 작업]** 타일의 하단에 있는 생략 부호를 클릭/탭합니다.

   ![chlimage_1-83](assets/chlimage_1-83.png)

   자세한 내용은 [번역 작업의 상태 모니터링](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job)을 참조하십시오.

1. 번역이 완료되면 상태가 검토 준비로 변경됩니다. 자산 UI로 이동하고 번역된 각 자산에 대한 속성 페이지를 열어 번역된 메타데이터를 확인합니다.

## 언어 복사 업데이트 {#update-language-copies}

이 워크플로우를 실행하여 추가 자산 세트를 번역하고 특정 로케일의 언어 복사본에 포함합니다. 이 경우 번역된 자산은 이미 이전에 번역된 자산이 들어 있는 대상 폴더에 추가됩니다. 옵션 선택에 따라 번역 프로젝트가 만들어지거나 새 자산에 대해 기존 번역 프로젝트가 업데이트됩니다. 언어 사본 업데이트 워크플로우에는 다음 옵션이 포함됩니다.

* 새 번역 프로젝트 만들기
* 기존 번역 프로젝트에 추가

### 새 번역 프로젝트 만들기 {#create-a-new-translation-project-1}

이 옵션을 사용하는 경우 언어 사본을 업데이트할 자산 세트에 대해 번역 프로젝트가 만들어집니다.

1. Assets UI에서 자산을 추가한 소스 폴더를 선택합니다.
1. **[!UICONTROL 참조]** 창을 열고 **[!UICONTROL 복사]** 아래에 있는 **[!UICONTROL 언어 사본]**&#x200B;을 클릭/탭하여 언어 사본 목록을 표시합니다.
1. **[!UICONTROL 언어 사본]** 앞에 확인란을 선택한 다음 해당 로케일에 해당하는 대상 폴더를 선택합니다.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. 맨 아래에서 **[!UICONTROL 언어 사본 업데이트]**&#x200B;를 클릭/탭합니다.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. **[!UICONTROL Project]** 목록에서 **[!UICONTROL 새 번역 프로젝트 만들기]**&#x200B;를 선택합니다.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. **[!UICONTROL 프로젝트 제목]** 필드에 프로젝트의 제목을 입력합니다.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. **[!UICONTROL 시작]**&#x200B;을 클릭/탭합니다.
1. 프로젝트 콘솔로 이동합니다. 번역 폴더가 프로젝트 콘솔에 복사됩니다.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. 폴더를 열어 번역 프로젝트를 확인합니다.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. 프로젝트를 클릭/탭하여 세부 사항 페이지를 엽니다.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. 자산에 대한 번역을 시작하려면 **[!UICONTROL 번역 작업]** 타일의 화살표를 클릭하고 목록에서 **[!UICONTROL 시작]**&#x200B;을 선택합니다.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   번역 작업 시작을 알리는 메시지가 나타납니다.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. 번역 작업의 상태를 보려면 **[!UICONTROL 번역 작업]** 타일의 하단에 있는 생략 부호를 클릭/탭합니다.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   작업 상태에 대한 자세한 내용은 [번역 작업의 상태 모니터링](../sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job)을 참조하십시오.

1. 자산 UI로 이동하고 번역된 각 자산에 대한 속성 페이지를 열어 번역된 메타데이터를 확인합니다.

### 기존 번역 프로젝트에 추가 {#add-to-existing-translation-project-1}

이 옵션을 사용하는 경우 자산 세트가 기존 번역 프로젝트에 추가되어 선택한 로케일의 언어 사본을 업데이트합니다.

1. 자산 UI에서 자산 폴더를 추가한 소스 폴더를 선택합니다.
1. **[!UICONTROL 참조 창]**&#x200B;을 열고 **[!UICONTROL 복사]** 아래에 있는 **[!UICONTROL 언어 사본]**&#x200B;을 클릭/탭하여 언어 사본 목록을 표시합니다.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. 모든 언어 사본을 선택하는 **[!UICONTROL 언어 사본]** 앞에 확인란을 선택합니다. 번역할 로케일에 해당하는 언어 사본(복사)을 제외한 다른 복사본을 선택 취소합니다.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. 맨 아래에서 **[!UICONTROL 언어 사본 업데이트]**&#x200B;를 클릭/탭합니다.

   ![chlimage_1-96](assets/chlimage_1-96.png)

1. **[!UICONTROL Project]** 목록에서 **[!UICONTROL 기존 번역 프로젝트에 추가]**&#x200B;를 선택합니다.

   ![chlimage_1-97](assets/chlimage_1-97.png)

1. **[!UICONTROL 기존 번역 프로젝트]** 목록에서 변환할 자산을 추가할 프로젝트를 선택합니다.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. **[!UICONTROL 시작]**&#x200B;을 클릭/탭합니다.
1. 나머지 절차를 완료하려면 [기존 번역 프로젝트에 추가](translation-projects.md#add-to-existing-translation-project)의 9-14단계를 참조하십시오.

## 임시 언어 사본 만들기 {#creating-temporary-language-copies}

번역 워크플로우를 실행하여 편집된 원래 자산의 버전으로 언어 사본을 업데이트하면 번역된 자산을 승인할 때까지 기존 언어 사본이 유지됩니다. [!DNL Experience Manager] Assets는 새로 번역된 자산을 임시 위치에 저장하고, 명시적으로 자산을 승인한 후 기존 언어 사본을 업데이트합니다. 자산을 거부하면 언어 사본은 변경되지 않은 상태로 유지됩니다.

1. 언어 사본을 이미 만든 **[!UICONTROL 언어 사본]** 아래의 소스 루트 폴더를 클릭/탭한 다음, **[!UICONTROL 자산]**&#x200B;에 표시 를 클릭/탭하여 [!DNL Experience Manager] 자산에서 폴더를 엽니다.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Assets UI에서 이미 번역한 자산을 선택하고 도구 모음에서 **[!UICONTROL 편집]** 아이콘을 클릭/탭하여 편집 모드에서 자산을 엽니다.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. 자산을 편집한 다음 변경 사항을 저장합니다.
1. [기존 번역 프로젝트에 추가](#add-to-existing-translation-project) 절차의 2-14단계를 수행하여 언어 사본을 업데이트합니다.
1. **[!UICONTROL 번역 작업]** 타일의 하단에 있는 생략 부호를 클릭/탭합니다. **[!UICONTROL 번역 작업]** 페이지의 자산 목록에서 번역된 버전의 자산이 저장되는 임시 위치를 명확하게 볼 수 있습니다.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. **[!UICONTROL 제목]** 옆의 확인란을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 번역 수락]**&#x200B;을 클릭/탭한 다음, 대화 상자에서 **[!UICONTROL 수락]**&#x200B;을 클릭/탭하여 대상 폴더의 번역된 자산을 편집된 자산의 번역된 버전으로 덮어씁니다.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   >[!NOTE]
   >
   >번역 워크플로우에서 대상 자산을 업데이트하도록 하려면 자산과 메타데이터를 모두 수락합니다.

   **[!UICONTROL 번역 거부]**&#x200B;를 클릭/탭하여 원래 번역된 버전의 자산을 대상 로케일 루트에서 유지하고 편집된 버전을 거부합니다.

   ![chlimage_1-103](assets/chlimage_1-103.png)

1. 자산 콘솔로 이동하고 번역된 각 자산에 대한 속성 페이지를 열어 번역된 메타데이터를 확인합니다.

자산에 대한 메타데이터를 효율적으로 번역하는 방법에 대한 팁은 메타데이터](https://web.archive.org/web/20181217033517/https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/)을 효율적으로 변환하는 5단계 중 [5단계에 대해 보관된 이 페이지를 참조하십시오.
