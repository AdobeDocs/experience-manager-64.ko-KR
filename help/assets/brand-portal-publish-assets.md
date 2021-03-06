---
title: 폴더를 Brand Portal에 게시
description: Brand Portal에 자산을 게시하고 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 30%

---

# 자산을 Brand Portal에 게시 {#publish-assets-to-brand-portal}

Adobe Experience Manager Assets 관리자는 조직의 [!DNL Experience Manager Assets Brand Portal] 인스턴스에 자산을 게시하거나 게시 워크플로우를 나중 날짜/시간으로 예약할 수 있습니다. 그러나 먼저 [!DNL Assets]을 [!DNL Brand Portal]로 구성해야 합니다. 자세한 내용은 [구성 [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md)을 참조하십시오. [!DNL Assets] 

자산을 게시하면 Brand Portal 사용자가 사용할 수 있습니다.

[!DNL Assets]에서 원래 자산을 이후에 수정하는 경우, 자산을 다시 게시하기 전까지는 변경 사항이 Brand Portal에 반영되지 않습니다. 이 기능은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

복제가 성공하면 자산, 폴더 및 컬렉션을 [!DNL Brand Portal]에 게시할 수 있습니다. Brand Portal에 자산을 게시하려면 다음 단계를 수행합니다.

>[!NOTE]
>
>Adobe은 특히 비스파이크 시간 동안 시차를 두고 게시하는 것이 좋습니다. 따라서 [!DNL Experience Manager] 작성자가 과도한 리소스를 사용하지 않도록 합니다.

1. Assets 콘솔에서 원하는 자산을 마우스로 가리킨 다음 빠른 작업에서 **[!UICONTROL 게시]** 옵션을 선택합니다.

   또는 Brand Portal에 게시할 자산을 선택합니다.

   ![publish2bp-2](assets/publish2bp-2.png)

2. 자산을 Brand Portal에 게시하려면 다음 두 가지 옵션을 사용할 수 있습니다.
   * [자산을 즉시 게시](#publish-now)
   * [나중에 자산 게시](#publish-later)

## 지금 자산 게시 {#publish-now}

선택한 자산을 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

* 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다. 그런 다음 메뉴에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택합니다.

* 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

   1. 그런 다음 **[!UICONTROL 작업]** Brand Portal에 게시&#x200B;]**를 선택하고**[!UICONTROL &#x200B;예약&#x200B;]**에서**[!UICONTROL &#x200B;지금&#x200B;]**을 선택합니다.**[!UICONTROL  **[!UICONTROL 다음].**

   2. **[!UICONTROL 범위]** 내에서 선택 내용을 확인하고 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 탭/클릭합니다.

자산이 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. Brand Portal 인터페이스에 로그인하여 게시된 자산을 확인합니다.

## 나중에 자산 게시 {#publish-later}

나중 날짜 또는 시간에 Brand Portal에 자산을 게시하는 일정을 예약하려면,

1. 게시할 자산/폴더를 선택한 후 맨 위의 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.
2. **[!UICONTROL 게시 관리]** 페이지에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택하고 **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;을 선택합니다.****

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 탭/클릭합니다.
4. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 탭/클릭합니다.
5. **[!UICONTROL 워크플로우]**&#x200B;에서 워크플로우 제목을 지정합니다. **[!UICONTROL 나중에 게시]**&#x200B;를 탭/클릭합니다.

   ![publishworkflow](assets/publishworkflow.png)

이제 Brand Portal에 로그인하여 게시된 자산을 Brand Portal 인터페이스에서 사용할 수 있는지 확인합니다.

![bp_631_landing_page](assets/bp_landing_page.png)
