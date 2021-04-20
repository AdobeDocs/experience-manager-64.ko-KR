---
title: 비공개 폴더 공유
description: AEM(Adobe Experience Manager) 자산에서 비공개 폴더를 만들고 다른 사용자와 공유하며 이들에게 다양한 권한을 할당하는 방법을 알아보십시오.
contentOwner: AG
feature: Collaboration
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 4%

---


# 비공개 폴더 공유 {#private-folder-sharing}

귀하에게만 제공되는 Adobe Experience Manager(AEM) 자산 사용자 인터페이스에서 비공개 폴더를 만들 수 있습니다. 이 비공개 폴더를 다른 사용자에게 공유하고, 사용자에게 다양한 권한을 할당할 수 있습니다. 사용자가 지정하는 권한 수준에 따라 폴더 내의 자산을 보거나 자산을 편집하는 등 다양한 작업을 폴더에 수행할 수 있습니다.

1. 자산 콘솔의 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 탭/클릭한 다음 메뉴에서 **[!UICONTROL 폴더]**&#x200B;를 선택합니다.

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. **[!UICONTROL 폴더 추가]** 대화 상자에서 폴더의 제목과 이름(선택 사항)을 입력하고 **[!UICONTROL 비공개]**&#x200B;를 선택합니다.

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. **[!UICONTROL 만들기]**&#x200B;를 탭/클릭합니다. UI에 비공개 폴더가 생성됩니다.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. 다른 사용자와 폴더를 공유하고 다른 사용자에게 할당 권한을 할당하려면 폴더를 선택하고 도구 모음에서 **[!UICONTROL 속성]** 아이콘을 클릭/탭합니다.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >폴더를 공유하기 전에는 다른 사용자가 해당 폴더를 볼 수 없습니다.

1. 폴더 속성 페이지의 **[!UICONTROL 사용자 추가]** 목록에서 사용자를 선택하고 개인 폴더의 사용자에게 역할을 할당하고 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >폴더를 공유하는 사용자에게 편집기, 소유자 또는 뷰어와 같은 다양한 역할을 할당할 수 있습니다. 사용자에게 소유자 역할을 할당하면 폴더에 대한 편집기 권한이 사용자에게 있습니다. 또한 사용자는 다른 사람과 폴더를 공유할 수 있습니다. 편집기 역할을 할당하면 사용자가 비공개 폴더의 자산을 편집할 수 있습니다. 뷰어 역할을 할당하면 사용자는 비공개 폴더의 에셋만 볼 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 사용자가 AEM Assets에 로그인할 때 지정하는 역할에 따라 개인 폴더에 대한 권한 집합이 할당됩니다.
1. 확인 메시지를 닫으려면 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.
1. 폴더를 공유하는 사용자는 공유 알림을 받습니다. 알림을 보려면 사용자의 자격 증명으로 AEM Assets에 로그인합니다.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. 알림 아이콘을 탭/클릭하여 알림 목록을 엽니다.

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. 관리자가 공유한 비공개 폴더의 항목을 클릭/탭하여 폴더를 엽니다.

>[!NOTE]
>
>비공개 폴더를 만들려면 비공개 폴더를 만들 상위 폴더에 대한 ACL 읽기 및 편집 권한이 필요합니다. 관리자가 아닌 경우 기본적으로 */content/dam*&#x200B;에서 이러한 권한이 활성화되어 있지 않습니다. 이 경우 비공개 폴더를 만들거나 폴더 설정을 보기 전에 먼저 사용자 ID/그룹에 대해 이러한 권한을 얻습니다.

