---
title: 비공개 폴더 공유
description: Adobe Experience Manager Assets에서 비공개 폴더를 만들고 다른 사용자와 공유하고, 이들에게 다양한 권한을 할당하는 방법을 알아보십시오.
contentOwner: AG
feature: Collaboration
role: User
exl-id: b6aa3cba-4085-47ac-a249-7461baee2a00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 10%

---

# 비공개 폴더 공유 {#private-folder-sharing}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

배타적으로 사용할 수 있는 Adobe Experience Manager Assets 사용자 인터페이스에서 비공개 폴더를 만들 수 있습니다. 이 비공개 폴더를 다른 사용자에게 공유하고 다양한 권한을 할당할 수 있습니다. 사용자가 지정하는 권한 수준에 따라 폴더에서 다양한 작업을 수행할 수 있습니다. 예를 들어 폴더 내의 자산을 보거나 자산을 편집할 수 있습니다.

1. 자산 콘솔에서 을 탭/클릭합니다 **[!UICONTROL 만들기]** 도구 모음에서 를 선택한 다음 **[!UICONTROL 폴더]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 에서 **[!UICONTROL 폴더 추가]** 대화 상자에서 폴더의 제목과 이름(선택 사항)을 입력하고 **[!UICONTROL 비공개]**.

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. **[!UICONTROL 만들기]**&#x200B;를 탭/클릭합니다. 개인 폴더는 UI에 만들어집니다.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. To share the folder with other users and the assign privileges to them, select the folder, and click/tap the **[!UICONTROL Properties]** icon from the toolbar.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >폴더는 공유하기 전까지 다른 사용자에게 표시되지 않습니다.

1. 폴더 속성 페이지의 **[!UICONTROL 사용자 추가]** 목록에 추가하고, 개인 폴더의 사용자에게 역할을 지정한 다음 **[!UICONTROL 추가]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >폴더를 공유하는 사용자에게 편집기, 소유자 또는 뷰어와 같은 다양한 역할을 할당할 수 있습니다. 사용자에게 소유자 역할을 할당하는 경우 사용자에게 폴더에 대한 편집기 권한이 있습니다. 또한 사용자는 다른 사용자와 폴더를 공유할 수 있습니다. 편집기 역할을 할당하는 경우 사용자는 개인 폴더에서 자산을 편집할 수 있습니다. 뷰어 역할을 할당하는 경우 사용자는 비공개 폴더의 자산만 볼 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 지정한 역할에 따라 사용자가 로그인하는 경우 사용자에게 개인 폴더에 대한 권한 세트가 할당됩니다 [!DNL Experience Manager] 자산.
1. 클릭 **[!UICONTROL 확인]** 확인 메시지를 닫습니다.
1. 폴더를 공유하는 사용자는 공유 알림을 받습니다. 에 로그인합니다. [!DNL Experience Manager] 알림을 볼 사용자의 자격 증명이 있는 자산.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. 알림 아이콘을 탭/클릭하여 알림 목록을 엽니다.

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. 관리자가 공유하는 비공개 폴더의 항목을 클릭/탭하여 폴더를 엽니다.

>[!NOTE]
>
>비공개 폴더를 만들려면 개인 폴더를 만들 상위 폴더에 대한 ACL 읽기 및 편집 권한이 필요합니다. 관리자가 아닌 경우 기본적으로 이 권한은 활성화되지 않습니다 */content/dam*. 이 경우, 개인 폴더를 만들거나 폴더 설정을 보기 전에 먼저 사용자 ID/그룹에 대해 이러한 권한을 얻습니다.
