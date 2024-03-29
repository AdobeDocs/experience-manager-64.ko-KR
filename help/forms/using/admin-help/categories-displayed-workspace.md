---
title: Workspace에 표시되는 카테고리 관리
seo-title: Managing the categories displayed in Workspace
description: Workspace에서 사용자가 시작할 수 있는 프로세스는 왼쪽 탐색 창의 범주로 표시됩니다. Workspace에 표시되는 이러한 카테고리를 관리하는 방법을 알아봅니다.
seo-description: In Workspace, the processes that a user can start are displayed in categories in the left navigation pane. Learn how you can manage these categories displayed in Workspace.
uuid: c2a275f5-872e-467f-9f07-4b130631e8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0d1536a2-10ac-4031-bd7f-264b02d0d75f
exl-id: 5a2bd0ea-2c5e-4e0c-aff1-dba06be6a5b7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 1%

---

# Workspace에 표시되는 카테고리 관리 {#managing-the-categories-displayed-in-workspace}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Workspace에서 사용자가 시작할 수 있는 프로세스는 왼쪽 탐색 창의 범주로 표시됩니다. 관리 콘솔에서 범주를 설정하거나 프로세스 디자이너가 Workbench에서 카테고리를 설정할 수 있습니다. 프로세스 디자이너가 프로세스를 만들 때 해당 프로세스를 카테고리에 할당합니다.

카테고리 이름을 지정할 때 작업 공간 탐색 창에 제대로 나타나도록 카테고리 이름을 만듭니다. 기본적으로 왼쪽 탐색 창의 너비는 210픽셀이며 이는 약 24자입니다. 지정하는 카테고리 이름이 너무 길어 왼쪽 탐색 창의 고정 너비에 맞지 않는 경우 잘립니다. 전체 이름은 마우스 포인터가 마우스 포인터를 위에 두면 나타납니다. 잘릴 카테고리 이름을 사용하지 마십시오. 다음 예는 에 맞는 카테고리 이름과 잘리는 카테고리 이름을 보여줍니다.

**에 맞는 카테고리 이름:** 참석 및 탈퇴

**잘린 카테고리 이름:** 참석 및 휴가(미국)

Workspace에서 카테고리 내의 프로세스는 일반적으로 프로세스 시작 페이지에서 카드로 표시됩니다. 일반적으로, 사용자가 나머지 카드를 보기 위해 스크롤해야 하기 전에 카테고리의 화면에 6개의 카드를 표시할 수 있습니다. 스크롤을 수행하면 프로세스를 찾기가 더 어려워지기 때문에 각 범주를 6개의 프로세스로 제한하거나, 해상도에 따라 화면에 표시할 수 있는 프로세스 수를 스크롤하지 않고도 제한하는 것이 좋습니다.

MySQL을 AEM Forms 데이터베이스로 사용하는 경우 관리 콘솔에서는 확장 문자 사용에만 다른 두 범주 이름을 구별할 수 없습니다. 예를 들어, abcde라는 카테고리와 &quot;bcdcee&quot;라는 카테고리를 만들면 동일한 카테고리로 간주됩니다.

## 카테고리 추가 {#add-a-category}

1. 관리 콘솔에서 서비스 > 애플리케이션 및 서비스 > 카테고리 관리를 클릭합니다.
1. 추가를 클릭합니다. 하위 카테고리를 추가하려면 카테고리를 선택한 다음 추가를 클릭합니다.
1. 이름 상자에 카테고리의 이름을 입력하고 설명 상자에 카테고리의 설명을 입력합니다.
1. 추가를 클릭합니다. 카테고리가 [카테고리 관리] 페이지에 표시됩니다.

   ***참고&#x200B;**: 카테고리를 만들 때 최대 5개의 계층 수준만 추가할 수 있습니다.*

## 카테고리 편집 {#edit-a-category}

1. 관리 콘솔에서 서비스 > 애플리케이션 및 서비스 > 카테고리 관리를 클릭합니다.
1. 편집할 카테고리를 선택하고 편집을 클릭합니다. 또는 편집할 카테고리를 두 번 클릭할 수 있습니다.
1. 이름 상자에서 카테고리의 이름을 편집합니다.

## 카테고리 제거 {#remove-a-category}

사용하지 않는 카테고리만 제거할 수 있습니다.

1. 관리 콘솔에서 서비스 > 애플리케이션 및 서비스 > 카테고리 관리를 클릭합니다.
1. 범주 관리 페이지에서 제거할 범주에 대한 확인란을 선택하고 제거를 누릅니다. 카테고리가 더 이상 표시되지 않습니다.
