---
title: 컬렉션을 Brand Portal에 게시
description: Brand Portal에 컬렉션을 게시하고 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 22%

---

# 컬렉션을 Brand Portal에 게시 {#publish-collections-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets 관리자는 [!DNL Experience Manager Assets Brand Portal] 조직의 인스턴스. 그러나 먼저 자산을 Brand Portal과 통합해야 합니다. 자세한 내용은 [Brand Portal에서 Assets 구성](configure-aem-assets-with-brand-portal.md)을 참조하십시오.

Assets에서 원래 컬렉션을 차후에 수정하는 경우 컬렉션을 다시 게시하기 전까지는 변경 내용이 Brand Portal에 반영되지 않습니다. 이 특성은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

>[!NOTE]
>
>컨텐츠 조각은 Brand Portal에 게시할 수 없습니다. 따라서 컨텐츠 조각에서 을 선택하는 경우 [!DNL Experience Manager] 작성자, 그런 다음 **[Brand Portal에 게시]** 작업을 사용할 수 없습니다.
>
>컨텐츠 조각이 포함된 컬렉션 게시 위치 [!DNL Experience Manager] 작성자가 Brand Portal으로 이동되면 컨텐츠 조각을 제외한 폴더의 모든 컨텐츠가 Brand Portal 인터페이스에 복제됩니다.

## Brand Portal에 컬렉션 게시 {#publish-a-collection-to-brand-portal}

1. 자산 UI에서 [!DNL Experience Manager] 로고. 그런 다음 **[!UICONTROL 자산 > 컬렉션]** 에서 **[!UICONTROL 탐색]** 페이지.
2. 컬렉션 콘솔에서 Brand Portal에 게시할 컬렉션을 선택합니다.

   ![select_collection](assets/select_collection.png)

3. 도구 모음에서 탭/클릭 **[!UICONTROL Brand Portal에 게시]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. 확인 대화 상자에서 를 탭/클릭합니다 **[!UICONTROL 게시]**.
5. 확인 메시지를 닫습니다.
6. 관리자로 Brand Portal에 로그인합니다. 게시된 컬렉션은 컬렉션 콘솔에서 사용할 수 있습니다.

   ![published_collection](assets/published_collection.png)

## 컬렉션 게시 취소 {#unpublish-collections}

Assets에서 Brand Portal으로 게시하는 컬렉션을 게시 취소할 수 있습니다. 원래 컬렉션을 게시 취소한 후에는 Brand Portal 사용자가 해당 복사본을 더 이상 사용할 수 없습니다.

1. 의 컬렉션 콘솔에서 [!DNL Assets] 인스턴스를 선택하고 게시를 취소하려는 컬렉션을 선택합니다.

   ![select_collection-1](assets/select_collection-1.png)

2. 도구 모음에서 **[!UICONTROL Brand Portal에서 제거]** 아이콘.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. 대화 상자에서 을 탭/클릭합니다. **[!UICONTROL 게시 취소]**.
4. 확인 메시지를 닫습니다. 컬렉션이 Brand Portal 인터페이스에서 제거됩니다.
