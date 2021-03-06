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
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---

# 그룹 템플릿 {#group-templates}

그룹 템플릿 콘솔은 [사이트 템플릿](sites.md) 콘솔과 매우 유사합니다. 둘 다 미리 연결된 페이지 집합 및 커뮤니티 사이트를 구성하는 기능에 대한 청사진입니다. 차이점은 사이트 템플릿이 기본 커뮤니티에 대한 것이고 그룹 템플릿은 기본 커뮤니티 내에 중첩된 하위 커뮤니티인 커뮤니티 그룹에 대한 것입니다.

커뮤니티 그룹은 [그룹 함수](functions.md#groups-function)(템플릿에서 첫 번째 또는 유일한 함수가 아닐 수 있음)를 포함하여 사이트 템플릿에 통합됩니다.

Communities [기능 팩 1](deploy-communities.md#latestfeaturepack)부터는 그룹 템플릿 내에 그룹 함수를 포함하여 그룹을 중첩할 수 있습니다.

새 커뮤니티 그룹을 만들기 위한 작업이 수행되면 그룹의 템플릿(구조)이 선택됩니다. 선택 사항은 사이트 또는 그룹 템플릿에 추가할 때 그룹 함수가 구성되는 방식에 따라 다릅니다.

>[!NOTE]
>
>[커뮤니티 사이트](sites-console.md), [커뮤니티 사이트 템플릿](sites.md), [커뮤니티 그룹 템플릿](tools-groups.md) 및 [커뮤니티 함수](functions.md)를 만드는 콘솔은 작성 환경에서만 사용할 수 있습니다.

## 그룹 템플릿 콘솔 {#group-templates-console}

작성 환경에서 그룹 템플릿 콘솔에 도달하려면 다음을 수행하십시오

* 전역 탐색에서: **[!UICONTROL 도구 > 커뮤니티 > 그룹 템플릿]**

이 콘솔에는 [커뮤니티 사이트](sites-console.md)를 만들 수 있고 새 그룹 템플릿을 만들 수 있는 템플릿이 표시됩니다.

![그룹 플레이트](assets/groupstemplate.png)

## 그룹 템플릿 만들기 {#create-goup-template}

새 그룹 템플릿 만들기를 시작하려면 **[!UICONTROL 만들기]**&#x200B;를 선택합니다

이렇게 하면 3개의 하위 패널이 포함된 사이트 편집기 패널이 표시됩니다.

### 기본 정보 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

기본 정보 패널에서 이름, 설명 및 템플릿 활성화 또는 비활성화 여부가 구성됩니다.

* **[!UICONTROL 새 그룹 템플릿]**
이름템플릿 이름 ID입니다

* ****
설명템플릿 설명입니다

* **[!UICONTROL 비활성화됨/]**
활성화템플릿 참조 여부를 제어하는 전환 스위치입니다

### 썸네일 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(선택 사항) 커뮤니티 사이트 작성자에게 이름 및 설명과 함께 축소판을 표시하려면 이미지 업로드 아이콘을 선택합니다.

### 구조 {#structure}

>[!CAUTION]
>
>AEM 6.1 Communities FP4 이전 버전에서 작업하는 경우 그룹 함수를 그룹 템플릿에 추가하지 마십시오.
>
>중첩 그룹 기능은 커뮤니티 [FP1](communities.md#latestfeaturepack)에서 사용할 수 있습니다.
>
>여전히 템플릿에서 첫 번째 또는 유일한 함수로 그룹 함수를 추가할 수 없습니다.

![gradtemplate 편집기](assets/grptemplateeditor.png)

커뮤니티 기능을 추가하려면 사이트 메뉴 링크가 표시되어야 하는 순서대로 오른쪽에서 왼쪽으로 드래그합니다. 사이트를 만드는 동안 템플릿에 스타일이 적용됩니다.

예를 들어 포럼을 원하는 경우 라이브러리에서 포럼 함수를 드래그하고 템플릿 빌더 아래에 놓습니다. 포럼 구성 대화 상자가 열립니다. 구성 대화 상자에 대한 자세한 내용은 [함수 콘솔](functions.md)을 참조하십시오.

이 템플릿을 기반으로 하위 커뮤니티 사이트(그룹)에 대해 원하는 다른 커뮤니티 기능을 계속 끌어다 놓습니다.

![드래그 함수](assets/dragfunctions.png)

원하는 함수를 모두 템플릿 빌더 영역으로 끌어다 놓고 구성했으면 오른쪽 상단 모서리에서 **[!UICONTROL 저장]** 을 선택합니다.

## 그룹 템플릿 편집 {#edit-group-template}

기본 [그룹 템플릿 콘솔](#group-templates-console)에서 커뮤니티 그룹을 볼 때 편집할 기존 그룹 템플릿을 선택할 수 있습니다.

그룹 템플릿을 편집해도 템플릿에서 이미 만든 커뮤니티 사이트에는 영향을 주지 않습니다. 대신 [커뮤니티 사이트](sites-console.md#modify-structure)의 구조를 직접 편집할 수 있습니다.

이 프로세스는 그룹 템플릿](#create-goup-template)을 만드는 것과 동일한 패널을 제공합니다.[
