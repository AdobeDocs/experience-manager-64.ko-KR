---
title: 폴더를 Brand Portal에 게시
description: Brand Portal에 폴더를 게시 및 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 27%

---

# 폴더를 Brand Portal에 게시 {#publish-folders-to-brand-portal}

Adobe Experience Manager Assets 관리자는 조직의 [!DNL Experience Manager Assets Brand Portal] 인스턴스에 자산 및 폴더를 게시(또는 게시 워크플로우를 나중 날짜/시간으로 예약)할 수 있습니다. 그러나 먼저 [!DNL Experience Manager Assets]을 [!DNL Brand Portal]과 통합해야 합니다. 자세한 내용은 [Brand Portal](configure-aem-assets-with-brand-portal.md)로 구성 [!DNL Experience Manager Assets] 을 참조하십시오.

자산 또는 폴더를 게시하면 Brand Portal 사용자가 사용할 수 있습니다.

[!DNL Assets]에서 원래 자산이나 폴더를 이후에 수정하는 경우, 자산이나 폴더를 다시 게시하기 전까지는 변경 사항이 Brand Portal에 반영되지 않습니다. 이 기능은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

## 폴더를 Brand Portal에 게시 {#publish-folders-to-brand-portal-1}

1. [!DNL Assets] 인터페이스에서 원하는 폴더를 마우스로 가리킨 다음 빠른 작업에서 **[!UICONTROL 게시]** 옵션을 선택합니다.

   또는 원하는 폴더를 선택하고 추가 단계를 수행합니다.

   ![publish2bp](assets/publish2bp.png)

2. **지금 폴더 게시**

   선택한 폴더를 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

   * 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다. 그런 다음 메뉴에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택합니다.
   * 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

3. 그런 다음 **[!UICONTROL 작업]** Brand Portal에 게시&#x200B;]**를 선택하고**[!UICONTROL &#x200B;예약&#x200B;]**에서**[!UICONTROL &#x200B;지금&#x200B;]**을 선택합니다.**[!UICONTROL  **[!UICONTROL Next].**
4. **[!UICONTROL 범위]** 내에서 선택 내용을 확인하고 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 탭합니다.

   폴더가 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. Brand Portal 인터페이스에 로그인하여 게시된 폴더를 확인합니다.

   **나중에 폴더 게시**

   나중 날짜 또는 시간으로 자산 폴더의 Brand Portal에 게시 워크플로우를 예약하려면 다음을 수행하십시오.

   1. 게시할 자산/폴더를 선택한 후 맨 위의 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.
   2. **[!UICONTROL 게시 관리]** 페이지에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택하고 **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;을 선택합니다.****

      ![publishlaterbp](assets/publishlaterbp.png)

   3. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 누릅니다.
   4. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인합니다. **[!UICONTROL 다음]**&#x200B;을 누릅니다.
   5. **[!UICONTROL 워크플로우]**&#x200B;에서 워크플로우 제목을 지정합니다. **[!UICONTROL 나중에 게시]**&#x200B;를 누릅니다.

      ![manageschedulepub](assets/manageschedulepub.png)

## Brand Portal에서 폴더 게시 취소 {#unpublish-folders-from-brand-portal}

[!DNL Experience Manager] 작성자 인스턴스에서 게시를 취소하여 Brand Portal에 게시된 모든 자산 폴더를 제거할 수 있습니다. 원래 폴더를 게시 취소한 후에는 Brand Portal 사용자가 해당 복사본을 더 이상 사용할 수 없습니다.

Brand Portal에서 폴더를 빠르게 게시 취소하거나 나중 날짜 및 시간 동안 예약할 수 있는 옵션이 있습니다. Brand Portal에서 자산 폴더의 게시를 취소하려면,

1. [!DNL Experience Manager] 작성자 인스턴스의 [!DNL Assets] 인터페이스에서 게시를 취소하려는 폴더를 선택합니다.

   ![publish2bp-1](assets/publish2bp-1.png)

2. 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 탭/클릭합니다.

3. **지금 Brand Portal에서 게시 취소**

   Brand Portal에서 원하는 폴더를 빨리 게시 취소하려면,

   1. **[!UICONTROL 게시 관리]** 페이지에서 **[!UICONTROL Action]** Brand Portal ]**에서**[!UICONTROL &#x200B;게시 취소 를 선택하고 **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 지금]**&#x200B;을 선택합니다.
   2. **[!UICONTROL 다음].**
   3. **[!UICONTROL 범위]** 내에서 선택 내용을 확인하고 **[!UICONTROL Brand Portal에서 게시 취소]**&#x200B;를 탭합니다.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **나중에 Brand Portal에서 게시 취소**

   Brand Portal에서 이후 날짜 및 시간으로 폴더 게시를 예약하려면,

   1. **[!UICONTROL 게시 관리]** 페이지에서 **[!UICONTROL Action]** Brand Portal ]**에서**[!UICONTROL &#x200B;게시 취소 를 선택하고 **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]를 선택합니다.**
   2. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 누릅니다.
   3. **[!UICONTROL 범위]** 내에서 선택 내용을 확인하고 **[!UICONTROL 다음]**&#x200B;을 누릅니다.
   4. **[!UICONTROL 워크플로우]**&#x200B;에서 **[!UICONTROL 워크플로우 제목]**&#x200B;을 지정합니다. **[!UICONTROL 나중에 게시 취소]를 누릅니다.**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>Brand Portal에서 자산을 게시/게시 취소하는 절차는 폴더의 해당 절차와 유사합니다.
