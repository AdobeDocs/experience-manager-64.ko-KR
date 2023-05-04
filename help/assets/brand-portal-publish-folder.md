---
title: 폴더를 Brand Portal에 게시
description: Brand Portal에 폴더를 게시 및 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 26%

---

# 폴더를 Brand Portal에 게시 {#publish-folders-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets 관리자는 [!DNL Experience Manager Assets Brand Portal] 조직에 대한 인스턴스(또는 나중에 게시 워크플로우를 날짜/시간으로 예약)를 지정합니다. 그러나 먼저 을 통합해야 합니다 [!DNL Experience Manager Assets] with [!DNL Brand Portal]. 자세한 내용은 [구성 [!DNL Experience Manager Assets] Brand Portal](configure-aem-assets-with-brand-portal.md).

자산 또는 폴더를 게시하면 Brand Portal 사용자가 사용할 수 있습니다.

에서 원래 자산 또는 폴더를 추가로 수정하는 경우 [!DNL Assets]로 지정하는 경우, 자산이나 폴더를 다시 게시하기 전까지는 변경 사항이 Brand Portal에 반영되지 않습니다. 이 기능은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

## 폴더를 Brand Portal에 게시 {#publish-folders-to-brand-portal-1}

1. 에서 [!DNL Assets] 인터페이스, 원하는 폴더 위로 마우스를 가져간 다음 을 선택합니다 **[!UICONTROL 게시]** 옵션을 선택합니다.

   또는 원하는 폴더를 선택하고 추가 단계를 수행합니다.

   ![publish2bp](assets/publish2bp.png)

2. **지금 폴더 게시**

   선택한 폴더를 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

   * 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다. 그런 다음 메뉴에서 **[!UICONTROL Brand Portal에 게시]**.
   * 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

3. 그런 다음 **[!UICONTROL 작업]** 선택 **[!UICONTROL Brand Portal에 게시]**, 및에서 **[!UICONTROL 예약]** 선택 **[!UICONTROL 지금]**. 탭 **[!UICONTROL 다음].**
4. 내 **[!UICONTROL 범위]**, 선택 내용을 확인하고 탭하기 **[!UICONTROL Brand Portal에 게시]**.

   폴더가 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. Brand Portal 인터페이스에 로그인하여 게시된 폴더를 확인합니다.

   **나중에 폴더 게시**

   나중 날짜 또는 시간으로 자산 폴더의 Brand Portal에 게시 워크플로우를 예약하려면 다음을 수행하십시오.

   1. 게시할 자산/폴더를 선택한 후 을 선택합니다. **[!UICONTROL 게시 관리]** 맨 위에 있는 도구 모음에서 를 클릭합니다.
   2. 설정 **[!UICONTROL 게시 관리]** 페이지를 선택하고 **[!UICONTROL Brand Portal에 게시]** 변환 전: **[!UICONTROL 작업]** 을(를) 선택합니다. **[!UICONTROL 나중에]** 변환 전: **[!UICONTROL 예약]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. 탭 **[!UICONTROL 다음]**.
   4. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인합니다. 탭 **[!UICONTROL 다음]**.
   5. **[!UICONTROL 워크플로우]**&#x200B;에서 워크플로우 제목을 지정합니다. 탭 **[!UICONTROL 나중에 게시]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Brand Portal에서 폴더 게시 취소 {#unpublish-folders-from-brand-portal}

Brand Portal에 게시된 모든 자산 폴더를 [!DNL Experience Manager] 작성자 인스턴스. 원래 폴더를 게시 취소한 후에는 Brand Portal 사용자가 해당 복사본을 더 이상 사용할 수 없습니다.

Brand Portal에서 폴더를 빠르게 게시 취소하거나 나중 날짜 및 시간 동안 예약할 수 있는 옵션이 있습니다. Brand Portal에서 자산 폴더의 게시를 취소하려면,

1. 에서 [!DNL Assets] 인터페이스 [!DNL Experience Manager]  작성자 인스턴스에서 게시를 취소하려는 폴더를 선택합니다.

   ![publish2bp-1](assets/publish2bp-1.png)

2. 도구 모음에서 탭/클릭 **[!UICONTROL 게시 관리]**.

3. **지금 Brand Portal에서 게시 취소**

   Brand Portal에서 원하는 폴더를 빨리 게시 취소하려면,

   1. 설정 **[!UICONTROL 게시 관리]** 페이지, **[!UICONTROL 작업]** 선택 **[!UICONTROL Brand Portal에서 게시 취소]** 및 **[!UICONTROL 예약]** 선택 **[!UICONTROL 지금]**.
   2. 탭/클릭 **[!UICONTROL 다음].**
   3. 내 **[!UICONTROL 범위]**, 선택 내용을 확인하고 탭하기 **[!UICONTROL Brand Portal에서 게시 취소]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **나중에 Brand Portal에서 게시 취소**

   Brand Portal에서 이후 날짜 및 시간으로 폴더 게시를 예약하려면,

   1. 설정 **[!UICONTROL 게시 관리]** 페이지, **[!UICONTROL 작업]** 선택 **[!UICONTROL Brand Portal에서 게시 취소]** 및 **[!UICONTROL 예약]** 선택 **[!UICONTROL 나중에].**
   2. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. 탭 **[!UICONTROL 다음]**.
   3. 내 **[!UICONTROL 범위]**, 선택 내용을 확인하고 탭하기 **[!UICONTROL 다음]**.
   4. 을(를) 지정합니다 **[!UICONTROL 워크플로우 제목]** 아래에 **[!UICONTROL 워크플로우]**. 탭 **[!UICONTROL 나중에 게시 취소].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>Brand Portal에서 자산을 게시/게시 취소하는 절차는 폴더의 해당 절차와 유사합니다.
