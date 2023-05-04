---
title: 편집할 디지털 자산 체크인 및 체크아웃
description: 편집할 자산을 체크 아웃하고 변경 사항이 완료된 후 다시 체크 인하는 방법을 알아봅니다.
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0c79ed42-0acd-426e-8e14-412bb4117585
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 8%

---

# Assets의 체크인 및 체크아웃 파일 {#check-in-and-check-out-files-in-assets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets를 사용하면 편집할 자산을 체크 아웃하고 변경을 완료한 후 다시 체크 인할 수 있습니다. 자산을 체크 아웃한 후에는 자산을 편집, 주석 달기, 게시, 이동 또는 삭제할 수만 있습니다. 자산을 체크 아웃하면 자산이 잠깁니다. 다른 사용자는 자산을 다시 체크 인할 때까지 자산에서 이러한 작업을 수행할 수 없습니다 [!DNL Experience Manager] 자산. 그러나 잠긴 자산에 대한 메타데이터를 변경할 수 있습니다.

자산을 체크 아웃하거나 체크 인할 수 있으려면 자산에 대해 쓰기 액세스 권한이 필요합니다.

이 기능은 여러 사용자가 여러 팀 간의 워크플로우 편집에서 공동 작업하는 작성자가 변경한 내용을 다른 사용자가 덮어쓰지 않도록 하는 데 도움이 됩니다.

## 자산 체크아웃 {#checking-out-assets}

1. Assets UI에서 체크 아웃할 자산을 선택합니다. 여러 자산을 선택하여 체크아웃할 수도 있습니다.

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. 도구 모음에서 **[!UICONTROL 체크아웃]** 아이콘.

   ![chlimage_1-469](assets/chlimage_1-469.png)

   다음을 확인합니다. **[!UICONTROL 체크아웃]** 아이콘 전환 **[!UICONTROL 체크 인]** 아이콘이 표시됩니다.

   ![chlimage_1-470](assets/chlimage_1-470.png)

   다른 사용자가 체크 아웃한 자산을 편집할 수 있는지 확인하려면 다른 사용자로 로그인합니다. 체크 아웃한 자산의 축소판에 잠금 아이콘이 표시됩니다.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   자산을 선택합니다. 도구 모음에는 자산을 편집, 주석 달기, 게시 또는 삭제할 수 있는 옵션이 표시되지 않습니다.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   그러나 클릭/탭할 수 있습니다 **[!UICONTROL 속성 보기]** 아이콘을 사용하여 잠긴 자산의 메타데이터를 편집합니다.

1. 편집 아이콘을 클릭/탭하여 자산을 편집 모드로 엽니다.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. 자산을 편집하고 변경 사항을 저장합니다. 예를 들어, 이미지를 자르거나 저장합니다.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   자산에 주석을 달거나 게시하도록 선택할 수도 있습니다.

1. Select the edited asset from the Assets UI, and click/tap the **[!UICONTROL Checkin]** icon from the toolbar.

   ![chlimage_1-475](assets/chlimage_1-475.png)

   수정된 자산은에 체크 인됩니다. [!DNL Assets] 및 은 다른 사용자가 편집할 수 있도록 제공됩니다.

## 강제 체크인 {#forced-check-in}

관리자는 다른 사용자가 체크 아웃한 자산을 체크 인할 수 있습니다.

1. 에 로그인합니다. [!DNL Assets] 관리자로.
1. Assets UI에서 다른 사용자가 체크 아웃한 자산을 한 개 이상 선택합니다.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. 도구 모음에서 **[!UICONTROL 잠금 해제]** 아이콘. 자산이 다시 체크 인되고 다른 사용자가 편집할 수 있습니다.

   ![chlimage_1-477](assets/chlimage_1-477.png)
