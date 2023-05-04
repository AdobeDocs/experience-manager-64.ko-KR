---
title: 에셋 업로드 제한 사항 구성
description: 사용자가 업로드할 수 있는 자산 유형(파일)을 제한하도록 Adobe Experience Manager Assets를 구성하는 방법을 알아봅니다.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 33%

---

# 에셋 업로드 제한 사항 구성 {#configuring-asset-upload-restrictions}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

사용자가 업로드할 수 있는 자산 유형(파일)을 제한하도록 Adobe Experience Manager Assets를 구성할 수 있습니다. 이 기능을 사용하면 사용자가 원치 않는 형식으로 자산을 업로드하거나 악의적인 파일을 업로드할 수 없습니다. 다음 `Day CQ DAM Asset Upload Restriction` 서비스를 사용하면 사용자가 업로드할 수 있는 파일 유형을 제어할 수 있습니다. 기본적으로 [!DNL Experience Manager] 자산을 사용하면 모든 MIME 유형의 자산을 업로드할 수 있습니다. 그러나 특정 MIME 유형의 파일만 업로드하도록 사용자를 제한하도록 서비스를 구성할 수 있습니다.

1. 구성 관리자 웹 콘솔을 열려면 `https://[AEM_server]:[port]/system/console/configMgr`.
1. 를 엽니다. **[!UICONTROL 일 CQ DAM 자산 업로드 제한]** 서비스를 편집 모드로 전환합니다. 기본적으로 **모든 MIME 허용** 옵션을 선택하면 사용자가 모든 MIME 유형의 파일을 업로드할 수 있습니다.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. To restrict users to upload files of certain MIME types only, unselect the **[!UICONTROL llow all MIME]** option and specify allowed MIME types in the **[!UICONTROL Allowed Asset MIMEs (regex)]** fields using regular expressions.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Click/tap **[!UICONTROL Save]** to save the changes. If you specify MIME-strings for allowed MIME types, the upload operation fails for any asset with MIME type that doesn’t match the configured MIME strings in these fields.
