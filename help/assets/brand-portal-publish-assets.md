---
title: 폴더를 Brand Portal에 게시
description: Brand Portal에 자산을 게시하고 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 30%

---

# 자산을 Brand Portal에 게시 {#publish-assets-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets 관리자는 [!DNL Experience Manager Assets Brand Portal] 조직에 대한 인스턴스(또는 나중에 게시 워크플로우를 날짜/시간으로 예약)를 지정합니다. 하지만 먼저 구성해야 합니다 [!DNL Assets] with [!DNL Brand Portal]. 자세한 내용은 [구성 [!DNL Assets] with [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

자산을 게시하면 Brand Portal 사용자가 사용할 수 있습니다.

에서 원래 자산을 추가로 수정하는 경우 [!DNL Assets]를 활성화하면 자산을 다시 게시하기 전까지 변경 사항이 Brand Portal에 반영되지 않습니다. 이 기능은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

복제가 성공하면 자산, 폴더 및 컬렉션을 [!DNL Brand Portal]. Brand Portal에 자산을 게시하려면 다음 단계를 수행합니다.

>[!NOTE]
>
>Adobe은 비스파이크 시간 특히 시차를 두고 게시에 권장하므로 [!DNL Experience Manager] 작성자는 과도한 리소스를 사용하지 않습니다.

1. 자산 콘솔에서 원하는 자산을 마우스로 가리킨 다음 을 선택합니다 **[!UICONTROL 게시]** 옵션을 선택합니다.

   또는 Brand Portal에 게시할 자산을 선택합니다.

   ![publish2bp-2](assets/publish2bp-2.png)

2. 자산을 Brand Portal에 게시하려면 다음 두 가지 옵션을 사용할 수 있습니다.
   * [자산을 즉시 게시](#publish-now)
   * [나중에 자산 게시](#publish-later)

## 지금 자산 게시 {#publish-now}

선택한 자산을 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

* 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다. 그런 다음 메뉴에서 **[!UICONTROL Brand Portal에 게시]**.

* 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

   1. 그런 다음 **[!UICONTROL 작업]** 선택 **[!UICONTROL Brand Portal에 게시]**, 및에서 **[!UICONTROL 예약]** 선택 **[!UICONTROL 지금]**. 탭/클릭 **[!UICONTROL 다음].**

   2. 내 **[!UICONTROL 범위]**, 선택 내용을 확인하고 탭/클릭 **[!UICONTROL Brand Portal에 게시]**.

자산이 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. Brand Portal 인터페이스에 로그인하여 게시된 자산을 확인합니다.

## 나중에 자산 게시 {#publish-later}

나중 날짜 또는 시간에 Brand Portal에 자산을 게시하는 일정을 예약하려면,

1. 게시할 자산/폴더를 선택한 후 을 선택합니다. **[!UICONTROL 게시 관리]** 맨 위에 있는 도구 모음에서 를 클릭합니다.
2. 설정 **[!UICONTROL 게시 관리]** 페이지를 선택하고 **[!UICONTROL Brand Portal에 게시]** 변환 전: **[!UICONTROL 작업]** 을(를) 선택합니다. **[!UICONTROL 나중에]** 변환 전: **[!UICONTROL 예약]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. 탭/클릭 **[!UICONTROL 다음]**.
4. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. 탭/클릭 **[!UICONTROL 다음]**.
5. **[!UICONTROL 워크플로우]**&#x200B;에서 워크플로우 제목을 지정합니다. 탭/클릭 **[!UICONTROL 나중에 게시]**.

   ![publishworkflow](assets/publishworkflow.png)

이제 Brand Portal에 로그인하여 게시된 자산을 Brand Portal 인터페이스에서 사용할 수 있는지 확인합니다.

![bp_631_landing_page](assets/bp_landing_page.png)
