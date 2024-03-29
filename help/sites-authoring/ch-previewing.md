---
title: ContextHub 데이터를 사용하여 페이지 미리보기
seo-title: Previewing Pages Using ContextHub Data
description: ContextHub 도구 모음은 ContextHub 저장소의 데이터를 표시하고 저장소 데이터를 변경할 수 있도록 해 주며 콘텐츠를 미리 보는 데 유용합니다.
seo-description: The ContextHub toolbar displays data from ContextHub stores and enables you to change store data and  is useful for previewing content
uuid: 0150555a-0a92-4692-a706-bbe59fd34d6a
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f281ef8c-0831-470c-acb7-189f20452a50
exl-id: 24f94dd5-62a4-4ac3-9a1b-a8e189da9958
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 50%

---

# ContextHub 데이터를 사용하여 페이지 미리보기{#previewing-pages-using-contexthub-data}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다음 [ContextHub](/help/sites-developing/contexthub.md) 도구 모음은 ContextHub 저장소의 데이터를 표시하고 저장소 데이터를 변경할 수 있도록 해줍니다. ContextHub 도구 모음은 ContextHub 저장소의 데이터로 판별되는 콘텐츠를 미리 보는 데 유용합니다.

도구 모음은 하나 이상의 UI 모듈이 포함된 일련의 UI 모드로 구성됩니다.

* UI 모드는 도구 모음의 왼쪽에 표시되는 아이콘입니다. 아이콘을 클릭하거나 탭하면 포함된 UI 모듈이 도구 모음에 표시됩니다.
* UI 모듈은 하나 이상의 ContextHub 저장소의 데이터를 표시합니다. 일부 UI 모듈에서는 저장소 데이터를 조작할 수도 있습니다.

ContextHub는 몇 가지 UI 모드와 UI 모듈을 설치합니다. 관리자가 [구성된 ContextHub](/help/sites-administering/contexthub-config.md) 다른 항목을 표시합니다.

![screen_shot_2018-03-23at093446](assets/screen_shot_2018-03-23at093446.png)

## ContextHub 도구 모음 표시 {#revealing-the-contexthub-toolbar}

ContextHub 도구 모음은 미리보기 모드에서 사용할 수 있습니다. 도구 모음은 작성자 인스턴스에서만, 그리고 관리자가 활성화한 경우에만 사용할 수 있습니다.

![screen_shot_2018-03-23at093730](assets/screen_shot_2018-03-23at093730.png)

1. 편집할 수 있도록 페이지가 열린 상태에서 도구 모음의 [미리보기]를 클릭하거나 탭합니다.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. 도구 모음을 표시하려면 ContextHub 아이콘을 클릭하거나 탭합니다.

   ![](do-not-localize/screen_shot_2018-03-23at093621.png)

## UI 모듈 기능 {#ui-module-features}

각 UI 모듈은 서로 다른 기능 세트를 제공하지만, 다음과 같은 유형의 기능은 일반적입니다. UI 모듈은 확장 가능하므로 개발자는 필요에 따라 다른 기능을 구현할 수 있습니다.

### 도구 모음 콘텐츠 {#toolbar-content}

UI 모듈은 도구 모음에 있는 하나 이상의 ContextHub 저장소에서 가져온 데이터를 표시할 수 있습니다. UI 모듈은 아이콘 및 제목을 사용하여 자신을 식별합니다.

![screen_shot_2018-03-23at093936](assets/screen_shot_2018-03-23at093936.png)

### 팝업 콘텐츠 {#popup-content}

일부 UI 모듈은 클릭하거나 탭하면 팝업을 오버레이로 표시합니다. 일반적으로 팝업은 도구 모음에 표시되는 내용 이외의 추가 정보를 포함합니다.

![screen_shot_2018-03-23at094003](assets/screen_shot_2018-03-23at094003.png)

### 팝업 Forms {#popup-forms}

모듈의 팝업 오버레이에는 ContextHub 저장소에서 데이터를 변경할 수 있는 양식 요소가 포함될 수 있습니다. 페이지 콘텐츠가 저장소 데이터에 의해 판별되는 경우 양식을 사용하고 페이지 콘텐츠에 대한 변경 사항을 관찰할 수 있습니다.

### 전체 화면 모드 {#fullscreen-mode}

팝업 오버레이는 클릭하거나 탭하여 전체 브라우저 창이나 화면을 덮도록 팝업 콘텐츠를 확장하는 아이콘을 포함할 수 있습니다.

![](do-not-localize/chlimage_1-18.png)
