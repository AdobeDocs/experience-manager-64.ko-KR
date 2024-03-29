---
title: 스페이스 및 엔티티
seo-title: Developing AEM Mobile Content Services
description: 이 페이지는 AEM Mobile 컨텐츠 서비스 개발을 위한 랜딩 페이지를 제공합니다.
seo-description: This page serves a landing page for developing AEM Mobile Content Services.
uuid: eab5a61b-a9e8-4863-90a3-df1f18510cd8
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: ef568577-c74e-4fc2-b66e-eedac2948310
exl-id: d4f29e1a-4d5c-4bdf-b530-7cd51bf709e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 3%

---

# 스페이스 및 엔티티{#spaces-and-entities}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>단일 페이지 애플리케이션 프레임워크 기반 클라이언트측 렌더링(예: React)이 필요한 프로젝트에 SPA 편집기를 사용하는 것이 좋습니다. [자세히 알아보기](/help/sites-developing/spa-overview.md).

스페이스는 Content Services REST API를 통해 노출된 엔티티를 저장하기에 편리한 위치입니다. 앱(또는 모든 채널)은 많은 엔티티와 연결될 수 있으므로 특히 유용합니다. 공간 내에 엔티티를 강제 적용하면 앱의 요구 사항을 그룹화하는 우수 사례가 발생합니다. 선택적으로, AEM의 앱을 적은 수의 공백과 연결할 수 있습니다.

>[!NOTE]
>
>Content Services의 모든 채널에서 사용 가능한 콘텐츠를 만들려면 공간 아래에 있어야 합니다.

## 공간 만들기 {#creating-a-space}

사용자가 여러 콘텐츠 및 자산을 모바일 앱에 노출하려면 AEM Mobile 대시보드를 사용하여 공간을 만듭니다.

Content Services가 공백과 함께 작동하도록 구성되지 않은 처음 사용자의 경우, AEM Mobile 대시보드는 선택 후 앱만 표시합니다 **컨텐츠 서비스**.

>[!CAUTION]
>
>**공백을 추가하기 위한 사전 요구 사항**
>
>을(를) 확인합니다. **AEM 컨텐츠 서비스 활성화** Spaces를 사용하여 작업하고 AEM Mobile 애플리케이션 대시보드에서 활성화하십시오.
>
>자세한 내용은 [콘텐츠 서비스 관리](/help/mobile/developing-content-services.md) 자세한 내용

대시보드에서 스페이스를 구성한 후에는 다음 단계에 따라 공백을 만드십시오.

1. 선택 **Spaces** 컨텐츠 서비스 를 참조하십시오.

   ![chlimage_1-83](assets/chlimage_1-83.png)

1. 선택 **만들기** 스페이스를 만들려면 Enter 키 **제목**, **이름**, 및 **설명** Analytics Mobile Apps 또는 Analytics Premium이 있어야 합니다.

   **만들기**&#x200B;를 클릭합니다.

   ![chlimage_1-84](assets/chlimage_1-84.png)

## 공간 관리 {#managing-a-space}

공간을 만든 후 왼쪽의 를 클릭하여 목록의 공간을 관리합니다.

공간의 속성을 보거나, 공간을 삭제하거나, 스페이스 및 해당 콘텐츠를 AEM 게시 인스턴스에 게시할 수 있습니다.

![chlimage_1-85](assets/chlimage_1-85.png)

**스페이스 속성 보기 및 편집**

1. 목록에서 공백을 선택합니다
1. 선택 **속성** 도구 모음에서
1. 클릭 **닫기** 완료

**스페이스 게시** 스페이스가 게시되면 해당 스페이스의 모든 폴더와 엔티티도 게시됩니다.

1. 스페이스 콘솔 목록에서 해당 아이콘을 클릭하여 공간을 선택합니다
1. 선택 **게시 트리**

>[!NOTE]
>
>다음을 수행할 수 있습니다 **게시 취소** 게시 인스턴스에서 공간을 제거하는 공간입니다.
>
>다음 이미지는 공간을 게시한 후 수행할 수 있는 작업을 보여줍니다.

![chlimage_1-86](assets/chlimage_1-86.png)

## 스페이스에서 폴더 사용 {#working-with-folders-in-a-space}

스페이스의 컨텐츠 및 자산을 추가로 구성하는 데 도움이 되도록 폴더에 폴더를 포함할 수 있습니다. 사용자는 공백 아래에서 고유한 계층 구조를 만들 수 있습니다.

### 폴더 만들기 {#creating-a-folder}

1. 스페이스 콘솔 목록에서 스페이스를 클릭하고 **폴더 만들기**

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. 을(를) 입력합니다. **제목**, **이름,** 및 **설명** 폴더

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. 클릭 **만들기** 스페이스에서 폴더를 만들려면

## 언어 복사 {#language-copy}

>[!CAUTION]
>
>언어 사본이 이 릴리스에서 제대로 작동하지 않습니다. 구조만 설정합니다.

다음 **언어 사본** 작성자는 이 기능을 사용하여 마스터 언어 사본을 복사한 다음 프로젝트 및 워크플로우를 만들어 컨텐츠를 자동으로 번역할 수 있습니다. 언어 복사본은 올바른 구조를 만듭니다. 스페이스에 폴더를 추가하면 스페이스에 언어 사본 을 추가할 수 있습니다.

>[!NOTE]
>
>번역될 수 있는 모든 컨텐츠는 언어 사본 노드 아래에 배치하는 것이 좋습니다.

### 언어 사본 추가 {#adding-language-copy}

1. 공간을 만들고 나면 해당 공간을 클릭하여 언어 사본을 만듭니다.

   클릭 **만들기** 및 **언어 사본**.

   ![chlimage_1-89](assets/chlimage_1-89.png)

   >[!NOTE]
   >
   >언어 복사 노드는 스페이스의 직접 하위 노드로만 존재할 수 있습니다.

1. 선택 **컨텐츠 패키지 언어(&amp;A);** 을 입력하고 **제목&amp;ast;** in **언어 사본 만들기** 대화 상자.

   **만들기**&#x200B;를 클릭합니다.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. 언어 사본 을 만들면 사용자의 공간에 표시됩니다 **언어 마스터**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >선택 **언어 마스터** 언어 복사 폴더를 보려면

### 스페이스에서 폴더 제거 {#removing-a-folder-from-the-space}

1. 스페이스 컨텐트 목록에서 폴더를 선택합니다
1. 클릭 **삭제** 도구 모음에서

   >[!NOTE]
   >
   >폴더로 이동하여 해당 콘텐츠를 보거나 하위 폴더나 엔티티를 추가하려면 스페이스 콘텐츠 목록에서 폴더 제목을 클릭합니다.

## 공간에서 엔티티 작업 {#working-with-entities-in-a-space}

엔티티는 웹 서비스 종단점을 통해 노출되는 콘텐츠를 나타냅니다. 엔티티는 공간에 저장되므로 쉽게 찾을 수 있고 관련 컨텐츠가 들어 있는 AEM 저장소 구조와는 독립적으로 유지됩니다.

일부 논리 수집에서 엔티티를 함께 그룹화할 수도 있습니다. 원하는 수만큼 폴더를 만들 수 있습니다.

다른 엔티티인 엔티티 하위가 데이터 모델링을 위해 수집되는 경우 개발자 사용자는 즉시 제공되는 &quot;엔티티 그룹&quot; 모델 유형에서 특정 &quot;그룹 모델&quot;을 생성할 수 있습니다.

>[!NOTE]
>
>엔티티는 항상 스페이스와 연결되므로 대부분의 엔티티 사용자 인터페이스는 스페이스 콘솔을 통해 액세스됩니다.

### 엔티티 만들기 {#creating-an-entity}

1. 스페이스 콘솔을 열고 스페이스 제목을 클릭합니다.

   선택적으로, 목록에서 폴더 제목을 클릭하여 폴더로 이동할 수 있습니다.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. 엔티티에 대한 모델을 선택합니다. 만들려는 엔티티 유형입니다. 다음을 클릭합니다.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   >[!NOTE]
   >
   >선택할 수 있는 옵션이 있습니다 **자산 모델**, **페이지 모델**&#x200B;또는 이전에 만든 엔티티 유형의 모델입니다.
   >
   >자세한 내용은 [모델 생성](/help/mobile/administer-mobile-apps.md)를 입력하여 사용자 지정 엔티티를 생성합니다.

1. 을(를) 입력합니다. **제목**, **이름**, **설명**, 및 **태그** 없습니다. **만들기**&#x200B;를 클릭합니다.

   ![chlimage_1-94](assets/chlimage_1-94.png)

   완료되면 엔티티가 스페이스 하위 항목에 나타납니다.

### 엔티티 편집 {#editing-an-entity}

1. 엔티티를 만든 후 폴더 또는 스페이스로 이동하고 편집할 스페이스 콘솔에서 엔티티를 선택합니다.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. 편집할 엔티티를 선택하고 를 클릭합니다 **편집**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   >[!CAUTION]
   >
   >엔티티를 생성하도록 선택한 템플릿에 따라, UI는 엔티티의 속성을 편집 및 보는 것에 대해 달라집니다. 자세한 내용은 아래 단계를 참조하십시오.

   ***엔티티를 자산 모델로 만들 템플릿을 선택하는 경우***, 클릭 **편집** 아래 그림과 같이 자산을 추가할 수 있습니다.

   ![chlimage_1-97](assets/chlimage_1-97.png)

   또는 을(를) 클릭합니다 **미리 보기** 를 클릭하여 json 링크를 확인합니다.

   ![chlimage_1-98](assets/chlimage_1-98.png)

   ***엔티티를 페이지 모델로 생성할 템플릿을 선택하는 경우***, 클릭 **편집** 아래 그림과 같이 자산을 추가할 수 있습니다.

   ![chlimage_1-99](assets/chlimage_1-99.png)

   에서 아이콘을 클릭합니다. **경로** 자산을 추가하려면

   ![chlimage_1-100](assets/chlimage_1-100.png)

   >[!NOTE]
   >
   >엔티티를 추가한 후에는 미리 보기 링크가 작동되도록 저장해야 합니다. 미리 보기를 보려면 **저장**. 을(를) 클릭합니다. **미리 보기** 아래 그림과 같이 추가된 자산의 json을 표시합니다.

   ![chlimage_1-101](assets/chlimage_1-101.png)

   >[!NOTE]
   >
   >엔티티에 자산을 추가했으면 다음 중 하나를 선택할 수 있습니다 **저장** 변경 내용을 저장하려면 **저장 및 닫기** 엔티티를 정의한 스페이스 콘솔 목록으로 저장하고 리디렉션하려면

   또한 스페이스 콘솔 목록에서 엔티티를 선택하고 을 클릭합니다 **속성** 정의된 엔티티의 등록 정보를 보고 편집하려면

   ![chlimage_1-102](assets/chlimage_1-102.png)

   제목, 설명, 태그를 편집하고 엔티티에 자산을 추가할 수 있습니다.

   ![chlimage_1-103](assets/chlimage_1-103.png)

### 엔티티 제거 {#removing-an-entity}

1. 스페이스 컨텐트 목록에서 엔티티를 선택합니다

   ![chlimage_1-104](assets/chlimage_1-104.png)

1. 클릭 **삭제** 도구 모음에서 특정 엔티티를 스페이스에서 제거하려면

### 엔티티 게시 {#publishing-an-entity}

선택할 수 있습니다 **게시 트리** 또는 **빠른 게시** 엔티티를 게시하려면 다음을 수행하십시오.

1. 스페이스 콘솔 목록에서 엔티티를 선택하고 **트리 게시**를 클릭하여 해당 엔티티와 해당 하위 엔티티를 게시합니다.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   **또는**,

   클릭 **빠른 게시** 특정 엔티티를 게시하려면 다음을 수행하십시오.
