---
title: 폴더를 Brand Portal에 게시
description: 브랜드 포털에 자산을 게시하고 게시 취소하는 방법을 알아봅니다.
contentOwner: VG
feature: Brand Portal
role: 비즈니스 전문가
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 39%

---


# 자산을 Brand Portal에 게시 {#publish-assets-to-brand-portal}

Adobe Experience Manager(AEM) 자산 관리자는 조직에 대해 AEM Assets 브랜드 포털 인스턴스에 자산을 게시할 수 있습니다(또는 게시 워크플로우를 최신 날짜/시간으로 예약할 수 있습니다). 그러나 먼저 브랜드 포털로 AEM Assets을 구성해야 합니다. 자세한 내용은 [Brand Portal에서 AEM Assets 구성](configure-aem-assets-with-brand-portal.md)을 참조하십시오.

자산을 게시한 후 브랜드 포털의 사용자가 사용할 수 있습니다.

AEM Assets에서 원래 에셋을 나중에 수정하는 경우 에셋을 다시 게시하기 전까지 변경 사항이 브랜드 포털에 반영되지 않습니다. 이 기능은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

복제가 성공하면 자산, 폴더 및 컬렉션을 Brand Portal에 게시할 수 있습니다. 자산을 브랜드 포털에 게시하려면 다음 단계를 수행합니다.

>[!NOTE]
>
>AEM 작성자가 초과 리소스를 차지하지 않도록 가급적이면 피크가 아닌 시간에, 시차 게시를 수행하는 것이 좋습니다.

1. 자산 콘솔에서 원하는 자산을 마우스로 가리키고 빠른 작업 중에서 **[!UICONTROL 게시]** 옵션을 선택합니다.

   또는 브랜드 포털에 게시할 자산을 선택합니다.

   ![publish2bp-2](assets/publish2bp-2.png)

2. 자산을 브랜드 포털에 게시하려면 다음 두 가지 옵션을 사용할 수 있습니다.
   * [즉시 에셋 게시](#publish-now)
   * [나중에 자산 게시](#publish-later)

## 지금 자산 게시 {#publish-now}

선택한 자산을 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

* 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다. 그런 다음 메뉴에서 **[!UICONTROL 브랜드 포털에 게시]**&#x200B;를 선택합니다.

* 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

   1. 그런 다음 **[!UICONTROL Action]**&#x200B;브랜드 포털에 게시&#x200B;]**를 선택하고**[!UICONTROL &#x200B;예약&#x200B;]**에서**[!UICONTROL &#x200B;지금&#x200B;]**을 선택합니다.**[!UICONTROL  **[!UICONTROL 다음]을 탭/ 클릭합니다.**

   2. **[!UICONTROL 범위]** 내에서 선택을 확인하고 **[!UICONTROL 브랜드 포털에 게시]**&#x200B;를 탭/클릭합니다.

자산이 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. 브랜드 포털 인터페이스에 로그인하여 게시된 자산을 확인합니다.

## 나중에 자산 게시 {#publish-later}

나중 날짜 또는 시간에 Brand Portal에 자산을 게시하는 일정을 예약하려면,

1. 게시할 자산/폴더를 선택한 후에는 맨 위의 도구 모음에서 **[!UICONTROL 발행물 관리]**&#x200B;를 선택합니다.
2. **[!UICONTROL 발행물 관리]** 페이지에서 **[!UICONTROL Action]**&#x200B;에서 **[!UICONTROL 브랜드 포털에 게시]**&#x200B;를 선택하고 **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;을 선택합니다.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 탭/클릭합니다.
4. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 탭/클릭합니다.
5. **[!UICONTROL 워크플로우]**&#x200B;에서 워크플로우 제목을 지정합니다. **[!UICONTROL 나중에 게시]**&#x200B;를 탭/클릭합니다.

   ![publishworkflow](assets/publishworkflow.png)

이제 브랜드 포털에 로그인하여 게시된 자산을 브랜드 포털 인터페이스에서 사용할 수 있는지 확인합니다.

![bp_631_landing_page](assets/bp_landing_page.png)
