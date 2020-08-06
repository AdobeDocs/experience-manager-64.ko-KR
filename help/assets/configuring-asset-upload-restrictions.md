---
title: 자산 업로드 제한 구성
description: 사용자가 업로드할 수 있는 자산(파일)의 유형을 제한하도록 Adobe Experience Manager(AEM) 자산을 구성하는 방법을 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# 자산 업로드 제한 구성 {#configuring-asset-upload-restrictions}

사용자가 업로드할 수 있는 자산(파일)의 유형을 제한하도록 Adobe Experience Manager(AEM) 자산을 구성할 수 있습니다. 이 기능을 사용하면 사용자가 원치 않는 형식으로 에셋을 업로드하거나 악의적인 파일을 업로드할 가능성을 없앨 수 있습니다. 이 `Day CQ DAM Asset Upload Restriction` 서비스를 사용하면 사용자가 업로드할 수 있는 파일 유형을 제어할 수 있습니다. 기본적으로 AEM Assets에서는 사용자가 모든 MIME 유형의 자산을 업로드할 수 있습니다. 그러나 특정 MIME 형식의 파일만 업로드하도록 사용자가 제한하도록 서비스를 구성할 수 있습니다.

1. Configuration Manager 웹 콘솔을 열려면 액세스합니다 `https://[AEM_server]:[port]/system/console/configMgr`.
1. 편집 모드에서 **[!UICONTROL 요일 CQ DAM 자산 업로드 제한]** 서비스를 엽니다. 기본적으로 모든 MIME **허용** 옵션이 선택되어 있어 사용자가 모든 MIME 유형의 파일을 업로드할 수 있습니다.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. 사용자가 특정 MIME 형식의 파일만 업로드하도록 제한하려면 모든 MIME **** 옵션 제한을 해제하고 일반 표현식을 사용하여 허용된 자산 MIME(regex) 필드에 허용된 MIME 형식을 **[!UICONTROL 지정합니다]** .

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. 저장을 클릭/ **[!UICONTROL 탭하여]** 변경 사항을 저장합니다. 허용되는 MIME 유형에 대해 MIME 문자열을 지정하는 경우 MIME 형식의 모든 자산에 대해 업로드 작업이 실패합니다. 이 필드는 구성된 MIME 문자열과 일치하지 않습니다.
