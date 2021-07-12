---
title: 컬렉션을 Brand Portal에 게시
description: Brand Portal에 컬렉션을 게시하고 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 21%

---

# 컬렉션을 Brand Portal에 게시 {#publish-collections-to-brand-portal}

AEM(Adobe Experience Manager) Assets 관리자는 조직의 AEM Assets Brand Portal 인스턴스에 컬렉션을 게시할 수 있습니다. 그러나 먼저 AEM Assets을 Brand Portal과 통합해야 합니다. 자세한 내용은 [Brand Portal에서 AEM Assets 구성](configure-aem-assets-with-brand-portal.md)을 참조하십시오.

AEM Assets에서 원래 컬렉션을 차후에 수정하는 경우 컬렉션을 다시 게시하기 전까지는 변경 내용이 Brand Portal에 반영되지 않습니다. 이 특성은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

>[!NOTE]
>
>컨텐츠 조각은 Brand Portal에 게시할 수 없습니다. 따라서 AEM 작성자에서 컨텐츠 조각을 선택하는 경우 **[Brand Portal에 게시]** 작업을 사용할 수 없습니다.
>
>컨텐츠 조각이 포함된 컬렉션이 AEM 작성자에서 Brand Portal으로 게시되면 컨텐츠 조각을 제외한 폴더의 모든 컨텐츠가 Brand Portal 인터페이스에 복제됩니다.

## Brand Portal에 컬렉션 게시 {#publish-a-collection-to-brand-portal}

1. AEM Assets UI에서 AEM 로고를 탭/클릭합니다. 그런 다음 **[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL 자산 > 컬렉션]** 로 이동합니다.
2. 컬렉션 콘솔에서 Brand Portal에 게시할 컬렉션을 선택합니다.

   ![select_collection](assets/select_collection.png)

3. 도구 모음에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 탭/클릭합니다.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. 확인 대화 상자에서 **[!UICONTROL 게시]**&#x200B;를 탭/클릭합니다.
5. 확인 메시지를 닫습니다.
6. 관리자로 Brand Portal에 로그인합니다. 게시된 컬렉션은 컬렉션 콘솔에서 사용할 수 있습니다.

   ![published_collection](assets/published_collection.png)

## 컬렉션 게시 취소 {#unpublish-collections}

AEM Assets에서 Brand Portal으로 게시하는 컬렉션을 게시 취소할 수 있습니다. 원래 컬렉션을 게시 취소한 후에는 Brand Portal 사용자가 해당 복사본을 더 이상 사용할 수 없습니다.

1. AEM Assets 인스턴스의 컬렉션 콘솔에서 게시를 취소하려는 컬렉션을 선택합니다.

   ![select_collection-1](assets/select_collection-1.png)

2. 도구 모음에서 **[!UICONTROL Brand Portal에서 제거]** 아이콘을 탭/클릭합니다.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. 대화 상자에서 **[!UICONTROL 게시 취소]**&#x200B;를 탭/클릭합니다.
4. 확인 메시지를 닫습니다. 컬렉션이 Brand Portal 인터페이스에서 제거됩니다.
