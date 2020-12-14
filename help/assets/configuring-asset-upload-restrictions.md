---
title: 자산 업로드 제한 사항 구성
description: AEM(Adobe Experience Manager) 자산을 구성하여 사용자가 업로드할 수 있는 자산(파일)의 유형을 제한하는 방법을 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# 자산 업로드 제한 사항 구성 {#configuring-asset-upload-restrictions}

AEM(Adobe Experience Manager) 자산을 구성하여 사용자가 업로드할 수 있는 자산(파일) 유형을 제한할 수 있습니다. 이 기능을 사용하면 사용자가 원치 않는 형식으로 에셋을 업로드하거나 악의적인 파일을 업로드할 가능성을 없앨 수 있습니다. `Day CQ DAM Asset Upload Restriction` 서비스를 사용하면 사용자가 업로드할 수 있는 파일 유형을 제어할 수 있습니다. 기본적으로 AEM Assets에서는 사용자가 모든 MIME 유형의 자산을 업로드할 수 있습니다. 그러나 특정 MIME 유형의 파일만 업로드하도록 사용자가 제한하도록 서비스를 구성할 수 있습니다.

1. 구성 관리자 웹 콘솔을 열려면 `https://[AEM_server]:[port]/system/console/configMgr`에 액세스하십시오.
1. 편집 모드에서 **[!UICONTROL 일 CQ DAM 자산 업로드 제한]** 서비스를 엽니다. 기본적으로 **모든 MIME** 허용 옵션이 선택되어 있어 사용자가 모든 MIME 유형의 파일을 업로드할 수 있습니다.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. 사용자가 특정 MIME 유형의 파일만 업로드하도록 제한하려면 **[!UICONTROL 모든 MIME]** 옵션을 선택 취소하고 정규 표현식을 사용하여 **[!UICONTROL 허용되는 자산 MIME(regex)]** 필드에 허용되는 MIME 유형을 지정합니다.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭/탭하여 변경 내용을 저장합니다. 허용되는 MIME 유형에 대해 MIME 문자열을 지정하는 경우 MIME 유형의 자산에 대해 업로드 작업이 실패합니다. 이 필드는 구성된 MIME 문자열과 일치하지 않습니다.
