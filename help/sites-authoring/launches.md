---
title: 론치 개요
seo-title: Launches Overview
description: 론치를 사용하여 향후 릴리스용 콘텐츠를 효율적으로 개발할 수 있습니다. 현재 페이지를 유지하면서 나중에 게시할 수 있도록 변경할 수 있습니다
seo-description: Launches enable you to efficiently develop content for a future release. They allow you to make changes ready for future publication, while maintaining your current pages
uuid: ff6a2898-7a77-4315-bb1f-efa9caa5f3b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: a7ec190d-056e-4fc9-8f2d-f4164273674d
exl-id: a6dca5d7-21b5-4a7f-9e83-b0f5ea77bc88
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 52%

---

# 론치 개요{#launches}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

론치를 사용하여 향후 릴리스용 콘텐츠를 효율적으로 개발할 수 있습니다.

론치가 생성되므로 향후에 게시할 수 있도록 변경할 수 있습니다(현재 페이지를 유지하는 동안). 론치 페이지를 편집하고 업데이트한 후 이를 소스에 다시 홍보한 후 소스 페이지(최상위 레벨)를 활성화합니다. 홍보를 하면 론치 콘텐츠가 소스 페이지에 다시 복제되며, 홍보는 수동 또는 자동으로 수행할 수 있습니다(론치를 생성 및 편집할 때 설정된 필드에 따라 다름).

예를 들어 온라인 상점의 계절별 제품 페이지는 주력 제품이 현재 계절과 일치하도록 분기별로 업데이트합니다. 다음 분기별 업데이트를 준비하기 위해 적절한 웹 페이지의 론치를 만들 수 있습니다. 분기 내내, 론치 사본에 다음 변경 사항이 누적되었습니다.

* 일반 유지 관리 작업의 결과로서 발생하는 소스 페이지 변경 사항입니다. 이러한 변경 사항은 론치 페이지에 자동으로 복제됩니다.
* 다음 분기를 준비하기 위해 론치 페이지에서 직접 수행한 편집.

다음 분기가 되면 소스 페이지(업데이트된 콘텐츠 보관 중)를 게시할 수 있도록 론치 페이지를 홍보합니다. 모든 페이지를 홍보하거나 수정한 페이지만 홍보할 수 있습니다.

론치는 다음 작업도 수행할 수 있습니다.

* 여러 루트 분기를 위해 만들어집니다. 전체 사이트에 대한 론치를 만들 수도 있지만(그리고 거기에서 변경을 수행할 수도 있지만) 전체 사이트를 복사해야 하므로 비현실적일 수 있습니다. 수백 또는 수천 개의 페이지가 관련되어 있는 경우, 시스템 요구 사항과 성능에 복사 작업과 프로모션 작업에 필요한 후속 비교의 영향을 모두 받습니다.
* 중첩(론치 내 론치)하여 기존 론치에서 론치를 만들 수 있는 기능을 제공하므로 작성자는 각 론치에 대해 동일한 변경을 여러 번 수행하지 않고 이미 수행된 변경 사항을 활용할 수 있습니다.

이 섹션에서는 생성, 편집 및 홍보(필요한 경우)를 하는 방법에 대해 설명합니다 [delete](/help/sites-authoring/launches-creating.md#deleting-a-launch))를 클릭하여 사이트 콘솔 또는 [론치 콘솔](#the-launches-console):

* [론치 만들기](/help/sites-authoring/launches-creating.md)
* [론치 편집](/help/sites-authoring/launches-editing.md)
* [론치 홍보](/help/sites-authoring/launches-promoting.md)

## 론치 - 이벤트 순서 {#launches-the-order-of-events}

론치를 사용하면 하나 이상의 활성화된 웹 페이지에 대한 향후 릴리스를 위해 콘텐츠를 효율적으로 개발할 수 있습니다.

론치를 사용하면 다음 작업을 수행할 수 있습니다.

* Create a copy of your source pages:

   * The copy is your launch.
   * The top-level source pages are known as **Production**.

      * 소스 페이지는 여러(별도의) 분기에서 가져올 수 있습니다.
   >[!CAUTION]
   >
   >클래식 UI에서는 론치에 대한 여러 소스 분기를 사용할 수 없습니다.

   ![chlimage_1-233](assets/chlimage_1-233.png)

* 론치 구성을 편집합니다.

   * 론치에 페이지 및/또는 분기를 추가 또는 제거합니다.
   * **제목**, **론치 날짜**, **프로덕션 준비** 플래그와 같은 론치 속성을 편집합니다.

* 콘텐츠의 수동 또는 자동 홍보 및 게시

   * 수동:

      * 론치 콘텐츠를 게시할 준비가 되면 다시 **타겟**(소스 페이지)으로 홍보합니다.
      * 소스(다시 홍보 후) 페이지의 콘텐츠를 게시합니다.
      * 모든 페이지를 홍보하거나 수정된 페이지만 홍보합니다.
   * 자동 - 다음 내용이 포함됩니다.

      * **론치**(**라이브**) **날짜** 필드: 론치를 만들거나 편집할 때 설정할 수 있습니다.
      * 다음 **프로덕션 준비** 플래그: 론치를 편집할 때만 설정할 수 있습니다.
      * **프로덕션 준비** 플래그를 설정하면 론치가 지정된 **론치**(**라이브**) **날짜**&#x200B;의 프로덕션 페이지로 자동 홍보됩니다. 홍보 이후 프로덕션 페이지는 자동으로 게시됩니다.

         날짜를 설정하지 않았다면 플래그가 적용되지 않습니다.


* 소스 페이지와 론치 페이지 동시 업데이트:

   * 소스 페이지 변경 내용은 론치 사본(상속을 통해, 즉 라이브 카피로 설정된 경우)에서 자동으로 구현됩니다.
   * 론치 사본에 대한 변경은 이 자동 업데이트 또는 소스 페이지를 중단하지 않고 수행할 수 있습니다.

   ![chlimage_1-234](assets/chlimage_1-234.png)

* [중첩 론치 만들기](/help/sites-authoring/launches-creating.md#creating-a-nested-launch) - 론치 내 론치:

   * 소스는 기존 론치입니다.
   * 다음을 수행할 수 있습니다 [중첩 론치 홍보](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch) 모든 타겟에 상위 론치나 최상위 소스 페이지(프로덕션)일 수 있습니다.

   ![chlimage_1-235](assets/chlimage_1-235.png)

   >[!CAUTION]
   >
   >론치를 삭제하면 론치 자체 및 모든 하위 중첩 론치가 제거됩니다.

>[!NOTE]
>
>론치를 만들고 편집하려면 기본 그룹 `content-authors`에서와 같이 `/content/launches`에 대한 액세스 권한이 필요합니다.
>
>문제가 발생하면 시스템 관리자에게 문의하십시오.

### 론치 콘솔 {#the-launches-console}

론치 콘솔에서는 론치에 대한 개요를 제공하며, 나열된 론치에 대해 작업을 수행할 수 있습니다. 이 콘솔은 다음 방법으로 액세스할 수 있습니다.

* **도구** 콘솔: **도구**, **사이트**, **론치**

* 또는 [http://localhost:4502/libs/launches/content/launches.html](http://localhost:4502/libs/launches/content/launches.html)

## 참조의 론치 (Sites 콘솔) {#launches-in-references-sites-console}

1. **Sites** 콘솔에서 론치의 소스로 이동합니다.
1. 를 엽니다. **참조** 레일을 실행하고 소스 페이지를 선택합니다.
1. 선택 **론치**, 기존 론치가 나열됩니다.

   ![chlimage_1-236](assets/chlimage_1-236.png)

1. 적절한 론치를 탭/클릭합니다. 가능한 작업 목록이 표시됩니다.

   ![chlimage_1-237](assets/chlimage_1-237.png)
