---
title: 편집자
seo-title: 편집자
description: 클래식 UI 편집기로 다시 전환하는 방법을 알아봅니다.
seo-description: 클래식 UI 편집기로 다시 전환하는 방법을 알아봅니다.
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
exl-id: 04a9c595-9a73-4a8a-99ae-c2292882338f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 8%

---

# 편집자{#editor}

기본적으로 편집기에서 클래식 UI로 전환하는 기능이 비활성화됩니다.

![chlimage_1-9](assets/chlimage_1-9.png)

**페이지 정보** 메뉴에서 **클래식 UI에서 열기** 옵션을 다시 활성화하려면 다음 단계를 수행합니다.

1. CRXDE Lite을 사용하여 다음 노드를 찾습니다.

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   예

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. **오버레이 노드** 옵션을 사용하여 오버레이를 만듭니다.예:

   * **경로**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **오버레이 위치**: `/apps/`
   * **일치 노드 유형**:활성(확인란 선택)

1. 겹쳐진 노드에 다음 다중 값 텍스트 속성을 추가합니다.

   `sling:hideProperties = ["granite:hidden"]`

1. 페이지를 편집할 때 **클래식 UI에서 열기** 옵션은 **페이지 정보** 메뉴에서 다시 사용할 수 있습니다.

   ![chlimage_1-10](assets/chlimage_1-10.png)
