---
title: Apache Tika를 사용하여 MIME 유형의 디지털 자산을 탐지합니다
description: Apache Tika를 활성화하여 도움말 [!DNL Experience Manager] Assets는 파일 확장명 대신 업로드 작업 중에 컨텐츠 스트림에서 MIME 유형의 자산을 감지합니다.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 6%

---

# Apache Tika를 사용하여 MIME 유형의 디지털 자산을 탐지합니다 {#detecting-mime-type-of-assets-using-apache-tika}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

일반적으로 Adobe Experience Manager Assets는 파일 확장자에서 업로드하는 MIME 유형의 자산을 감지합니다. Apache Tika를 사용하여 자산을 업로드하는 경우, [!DNL Experience Manager] Assets는 파일 확장자 대신 업로드 작업 중에 컨텐츠 스트림에서 해당 MIME 유형을 감지합니다.

이 기능은 기본적으로 비활성화됩니다. 이 기능을 활성화하려면 **일 CQ DAM Mime 유형** 서비스(Configuration Manager)를 통해 제공됩니다.

>[!NOTE]
>
>Apache Tika 라이브러리를 사용하는 MIME 유형 감지는 리소스를 많이 사용하는 작업입니다.

1. 이동 `https://[AEM_server]:[port]/system/console/configMgr` 구성 관리자 웹 콘솔을 열려면 다음을 수행하십시오.
1. 서비스 목록에서 **[!UICONTROL 일 CQ DAM Mime 유형 서비스]** 을(를) 탭/클릭합니다 **[!UICONTROL 편집]** 아이콘 옆에 있는 아이콘을 클릭하여 편집 모드로 엽니다.

1. 을(를) 선택합니다 **[!UICONTROL 콘텐츠에서 MIME 검색]** 파일 확장자를 무시하고 업로드된 자산의 구문 분석을 활성화하여 해당 MIME 유형을 확인하는 옵션입니다. 기본적으로 이 옵션은 선택되어 있지 않습니다.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Click/tap **[!UICONTROL Save]** to save the changes.
