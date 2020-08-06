---
title: 폴더를 Brand Portal에 게시
description: 브랜드 포털에 폴더를 게시하고 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 27%

---


# 폴더를 Brand Portal에 게시 {#publish-folders-to-brand-portal}

Adobe Experience Manager(AEM) 자산 관리자는 자산 및 폴더를 AEM Assets 브랜드 포털 인스턴스에 게시(또는 게시 워크플로우를 최신 날짜/시간으로 예약)할 수 있습니다. 그러나 먼저 AEM Assets을 브랜드 포털과 통합해야 합니다. 자세한 내용은 [Brand Portal에서 AEM Assets 구성](configure-aem-assets-with-brand-portal.md)을 참조하십시오.

자산 또는 폴더를 게시한 후 브랜드 포털에서 사용자가 사용할 수 있습니다.

AEM Assets에서 원래 자산 또는 폴더를 이후에 수정하는 경우, 자산 또는 폴더를 다시 게시하기 전까지 변경 사항이 브랜드 포털에 반영되지 않습니다. 이 기능은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

## 폴더를 Brand Portal에 게시 {#publish-folders-to-brand-portal-1}

1. AEM Assets 인터페이스에서 원하는 폴더 위로 마우스를 가져간 다음 빠른 작업 **[!UICONTROL 에서 게시]** 옵션을 선택합니다.

   또는 원하는 폴더를 선택하고 추가 단계를 따릅니다.

   ![publish2bp](assets/publish2bp.png)

2. **지금 폴더 게시**

   선택한 폴더를 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

   * 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.
   * 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

3. 그런 다음 작업 **[!UICONTROL 에서]** 브랜드 포털 **[!UICONTROL 에 게시]**&#x200B;를 **[!UICONTROL 선택하고]** 예약 **[!UICONTROL 에서]**&#x200B;지금을선택합니다. 다음을 **[!UICONTROL 누릅니다].**
4. 범위 내 **[!UICONTROL 에서]**&#x200B;선택을 확인하고 브랜드 포털 **[!UICONTROL 에 게시를 탭합니다]**.

   폴더가 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. 게시된 폴더를 보려면 브랜드 포털 인터페이스에 로그인합니다.

   **나중에 폴더 게시**

   자산 폴더의 브랜드 포털 게시 워크플로우를 나중 날짜 또는 시간으로 예약하려면:

   1. 게시할 자산/폴더를 선택한 경우 **[!UICONTROL 맨]** 위의 도구 모음에서 게시 관리를 선택합니다.
   2. [ **[!UICONTROL 발행물]** ] 페이지에서 **[!UICONTROL 작업]** 에서 **[!UICONTROL 브랜드 포털에]** 게시 **[!UICONTROL 를 선택하고 Facebook에서]** **** LaterScheduling을 선택합니다.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. 다음을 **[!UICONTROL 누릅니다]**.
   4. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인합니다. 다음을 **[!UICONTROL 누릅니다]**.
   5. **[!UICONTROL 워크플로우]**&#x200B;에서 워크플로우 제목을 지정합니다. 나중에 **[!UICONTROL 게시를 누릅니다]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Brand Portal에서 폴더 게시 취소 {#unpublish-folders-from-brand-portal}

AEM 작성자 인스턴스에서 게시를 취소하여 브랜드 포털에 게시된 자산 폴더를 제거할 수 있습니다. 원래 폴더를 게시 취소한 후에는 Brand Portal 사용자가 해당 복사본을 더 이상 사용할 수 없습니다.

브랜드 포털에서 폴더를 신속하게 게시 취소하거나 나중 날짜 및 시간으로 예약하는 옵션이 있습니다. Brand Portal에서 자산 폴더의 게시를 취소하려면,

1. AEM 작성자 인스턴스의 AEM Assets 인터페이스에서 게시 취소할 폴더를 선택합니다.

   ![publish2bp-1](assets/publish2bp-1.png)

2. 도구 모음에서 게시 **[!UICONTROL 관리를 탭/클릭합니다]**.

3. **지금 브랜드 포털에서 게시 취소**

   브랜드 포털에서 원하는 폴더를 빠르게 게시 취소하려면 다음을 수행하십시오.

   1. 게시 **[!UICONTROL 관리]** 페이지의 **[!UICONTROL 경우, 브랜드 포털]****[!UICONTROL 에서 게시 취소를 선택하고 Scheduling]** **** ****&#x200B;에서 게시 취소를 선택합니다.
   2. Tap/ click **[!UICONTROL Next].**
   3. 범위 내에서 **[!UICONTROL 선택]**&#x200B;사항을 확인하고 브랜드 포털에서 **[!UICONTROL 게시 취소를 탭합니다]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **나중에 브랜드 포털에서 게시 취소**

   Brand Portal에서 이후 날짜 및 시간으로 폴더 게시를 예약하려면:

   1. 게시 **[!UICONTROL 관리]** 페이지의 **[!UICONTROL 경우, 브랜드 포털]****[!UICONTROL 에서 게시 취소를]** 선택하고 Scheduling **** **에서 게시 취소를 선택합니다.**
   2. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. 다음을 **[!UICONTROL 누릅니다]**.
   3. 범위 내 **[!UICONTROL 에서]**&#x200B;선택을 확인하고 **[!UICONTROL 다음을 누릅니다]**.
   4. Specify a **[!UICONTROL Workflow title]** under **[!UICONTROL Workflows]**. 나중에 **[!UICONTROL 게시 취소를 누릅니다].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>자산을 브랜드 포털에 게시/게시 취소하는 절차는 폴더에 대한 해당 절차와 유사합니다.
