---
title: 그룹 템플릿
seo-title: 그룹 템플릿
description: 그룹 템플릿 콘솔에 액세스하는 방법
seo-description: 그룹 템플릿 콘솔에 액세스하는 방법
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---


# 그룹 템플릿 {#group-templates}

그룹 템플릿 콘솔은 [사이트 템플릿 콘솔과](sites.md) 매우 유사합니다. 이 두 가지 모두 미리 연결된 페이지 세트를 위한 청사진이며 커뮤니티 사이트를 형성합니다. 차이점은 사이트 템플릿은 기본 커뮤니티를 위한 것이고 그룹 템플릿은 기본 커뮤니티 내에 중첩된 하위 커뮤니티를 위한 것입니다.

커뮤니티 그룹은 [그룹 기능](functions.md#groups-function) (템플릿에서 첫 번째 또는 유일한 기능은 아닐 수 있음)을 포함하여 사이트 템플릿에 통합됩니다.

커뮤니티 [기능 팩 1](deploy-communities.md#latestfeaturepack)의 경우 그룹 기능을 그룹 템플릿 내에 포함하여 그룹을 중첩할 수 있습니다.

새 커뮤니티 그룹을 만들기 위해 작업이 수행되면 그룹의 템플릿(구조)이 선택됩니다. 선택 사항은 사이트 또는 그룹 템플릿에 추가할 때 그룹 함수가 어떻게 구성되었는지에 따라 다릅니다.

>[!NOTE]
>
>작성 환경에서만 사용할 수 있는 [커뮤니티 사이트](sites-console.md), [커뮤니티 사이트 템플릿](sites.md), [커뮤니티 그룹 템플릿](tools-groups.md) 및 [커뮤니티 기능](functions.md) 의 콘솔입니다.

## 그룹 템플릿 콘솔 {#group-templates-console}

작성 환경에서 그룹 템플릿 콘솔에 도달하려면

* 전역 탐색에서: **[!UICONTROL 도구 > 커뮤니티 > 그룹 템플릿]**

이 콘솔에는 [커뮤니티 사이트를](sites-console.md) 만들 수 있는 템플릿이 표시되며 새 그룹 템플릿을 만들 수 있습니다.

![그룹템플릿](assets/groupstemplate.png)

## 그룹 템플릿 만들기 {#create-goup-template}

새 그룹 템플릿을 만들려면 만들기를 **[!UICONTROL 선택합니다]**

그러면 3개의 하위 패널이 포함된 사이트 편집기 패널이 표시됩니다.

### 기본 정보 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

기본 정보 패널에서 이름, 설명 및 템플릿 활성화 또는 비활성화 여부를 구성합니다.

* **[!UICONTROL 새 그룹 템플릿 이름]**&#x200B;템플릿 이름 ID

* **[!UICONTROL 설명]**&#x200B;템플릿 설명

* **[!UICONTROL 비활성화/]**&#x200B;활성화템플릿 참조 여부를 제어하는 전환 스위치입니다.

### 썸네일 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(선택 사항) 커뮤니티 사이트 작성자에게 이름 및 설명과 함께 축소판을 표시하려면 이미지 업로드 아이콘을 선택합니다.

### 구조 {#structure}

>[!CAUTION]
>
>AEM 6.1 Communities FP4 이전 버전에서 작업하는 경우 그룹 기능을 그룹 템플릿에 추가하지 마십시오.
>
>중첩 그룹 기능은 Communities [FP1에서 사용할 수 있습니다](communities.md#latestfeaturepack).
>
>템플릿의 첫 번째 또는 유일한 함수로 Groups 함수를 추가할 수 없습니다.

![grptemplateeditor](assets/grptemplateeditor.png)

커뮤니티 기능을 추가하려면 사이트 메뉴 링크가 표시되어야 하는 순서대로 오른쪽에서 왼쪽으로 드래그합니다. 사이트를 만드는 동안 스타일이 템플릿에 적용됩니다.

예를 들어 포럼을 원하는 경우 라이브러리에서 포럼 함수를 드래그하여 템플릿 빌더 아래에 놓습니다. 그러면 포럼 구성 대화 상자가 열립니다. 구성 대화 상자에 대한 자세한 내용은 [함수 콘솔을](functions.md) 참조하십시오.

이 템플릿을 기반으로 하는 하위 커뮤니티 사이트(그룹)에 대해 원하는 다른 커뮤니티 기능을 계속 드래그 앤 드롭합니다.

![드래그 함수](assets/dragfunctions.png)

원하는 기능을 모두 템플릿 빌더 영역에 놓고 구성한 후에는 오른쪽 **[!UICONTROL 상단 모서리에서 저장을]** 선택합니다.

## 그룹 템플릿 편집{#edit-group-template}

기본 [그룹 템플릿 콘솔에서](#group-templates-console)커뮤니티 그룹을 볼 때 편집할 기존 그룹 템플릿을 선택할 수 있습니다.

그룹 템플릿을 편집해도 템플릿에서 이미 만든 커뮤니티 사이트에는 영향을 주지 않습니다. 대신 커뮤니티 사이트 [구조를 직접](sites-console.md#modify-structure)편집할 수 있습니다.

이 프로세스에서는 그룹 템플릿 [을 만드는 것과 동일한 패널을 제공합니다](#create-goup-template).
