---
title: 편집기
seo-title: Editor
description: 클래식 UI 편집기로 다시 전환하는 방법을 알아봅니다.
seo-description: Learn how to switch back to the Classic UI Editor.
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
exl-id: 04a9c595-9a73-4a8a-99ae-c2292882338f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 12%

---

# 편집기{#editor}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

기본적으로 편집기에서 클래식 UI로 전환하는 기능이 비활성화됩니다.

![chlimage_1-9](assets/chlimage_1-9.png)

옵션을 다시 활성화하려면 **클래식 UI로 열기** 에서 **페이지 정보** 메뉴에서 다음 단계를 수행합니다.

1. CRXDE Lite을 사용하여 다음 노드를 찾습니다.

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   예

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. 을 사용하여 오버레이 만들기 **오버레이 노드** 옵션; 예:

   * **경로**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **오버레이 위치**: `/apps/`
   * **일치 노드 유형**: 활성(확인란 선택)

1. 겹쳐진 노드에 다음 다중 값 텍스트 속성을 추가합니다.

   `sling:hideProperties = ["granite:hidden"]`

1. 다음 **클래식 UI로 열기** 옵션을 다시 사용할 수 있습니다. **페이지 정보** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-10](assets/chlimage_1-10.png)
