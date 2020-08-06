---
title: 컬렉션을 Brand Portal에 게시
description: 컬렉션을 브랜드 포털에 게시하고 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 21%

---


# 컬렉션을 Brand Portal에 게시 {#publish-collections-to-brand-portal}

Adobe Experience Manager(AEM) 자산 관리자는 조직의 AEM Assets 브랜드 포털 인스턴스에 컬렉션을 게시할 수 있습니다. 그러나 먼저 AEM Assets을 브랜드 포털과 통합해야 합니다. 자세한 내용은 [Brand Portal에서 AEM Assets 구성](configure-aem-assets-with-brand-portal.md)을 참조하십시오.

AEM Assets에서 원래 컬렉션을 나중에 수정하는 경우 컬렉션을 다시 게시하기 전까지 변경 사항이 브랜드 포털에 반영되지 않습니다. 이러한 특성을 통해 브랜드 포털에서는 진행 중인 변경 작업을 사용할 수 없습니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

>[!NOTE]
>
>컨텐츠 조각은 Brand Portal에 게시할 수 없습니다. Therefore, if you select content fragment(s) on AEM Author, then **[Publish to Brand Portal]** action is not available.
>
>콘텐츠 조각이 포함된 컬렉션이 AEM Author에서 브랜드 포털로 게시되면 콘텐츠 조각을 제외한 폴더의 모든 콘텐츠가 브랜드 포털 인터페이스에 복제됩니다.

## 브랜드 포털에 컬렉션 게시 {#publish-a-collection-to-brand-portal}

1. AEM Assets UI에서 AEM 로고를 탭/클릭합니다. 그런 다음 탐색 **[!UICONTROL 페이지에서]** 자산 > 컬렉션 **[!UICONTROL 으로]** 이동합니다.
2. 컬렉션 콘솔에서 브랜드 포털에 게시할 컬렉션을 선택합니다.

   ![select_collection](assets/select_collection.png)

3. From the toolbar, tap/click **[!UICONTROL Publish to Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. In the confirmation dialog, tap/click **[!UICONTROL Publish]**.
5. 확인 메시지를 닫습니다.
6. 관리자로 브랜드 포털에 로그인합니다. 게시된 컬렉션은 컬렉션 콘솔에서 사용할 수 있습니다.

   ![published_collection](assets/published_collection.png)

## 컬렉션 게시 취소 {#unpublish-collections}

AEM Assets에서 브랜드 포털에 게시하는 컬렉션의 게시를 취소할 수 있습니다. 원본 컬렉션의 게시를 취소하면 더 이상 해당 복사본을 브랜드 포털 사용자가 사용할 수 없습니다.

1. AEM Assets 인스턴스의 컬렉션 콘솔에서 게시 취소할 컬렉션을 선택합니다.

   ![select_collection-1](assets/select_collection-1.png)

2. From the toolbar, tap/click the **[!UICONTROL Remove from Brand Portal]** icon.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. In the dialog, tap/click **[!UICONTROL Unpublish]**.
4. 확인 메시지를 닫습니다. 컬렉션이 Brand Portal 인터페이스에서 제거됩니다.
