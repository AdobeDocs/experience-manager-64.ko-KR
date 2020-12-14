---
title: Apache Tika를 사용하여 디지털 에셋의 MIME 유형 감지
description: Apache Tika를 활성화하여 AEM Assets이 파일 확장명이 아닌 업로드 작업 중에 콘텐츠 스트림에서 MIME 유형의 자산을 검색하는 데 도움이 됩니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# Apache Tika를 사용하여 디지털 자산 {#detecting-mime-type-of-assets-using-apache-tika} MIME 유형 감지

일반적으로 Adobe Experience Manager(AEM) 자산은 파일 확장자에서 업로드하는 자산의 MIME 유형을 감지합니다. Apache Tika를 사용하여 에셋을 업로드하는 경우 AEM Assets은 업로드 작업 중에 파일 확장명 대신 컨텐츠 스트림에서 MIME 유형을 감지합니다.

이 기능은 기본적으로 비활성화됩니다. 이 기능을 활성화하려면 구성 관리자에서 **일 CQ DAM MIME 유형** 서비스를 구성합니다.

>[!NOTE]
>
>Apache Tika 라이브러리를 사용하는 MIME 유형 감지는 리소스를 많이 사용하는 작업입니다.

1. `https://[AEM_server]:[port]/system/console/configMgr`으로 이동하여 Configuration Manager 웹 콘솔을 엽니다.
1. 서비스 목록에서 **[!UICONTROL Day CQ DAM MIME 유형 서비스]**&#x200B;를 찾아 옆에 있는 **[!UICONTROL 편집]** 아이콘을 탭/클릭하여 편집 모드에서 엽니다.

1. **[!UICONTROL 콘텐트]**&#x200B;에서 MIME 감지 옵션을 선택하여 업로드된 에셋의 구문 분석을 활성화하여 파일 확장자를 무시하고 MIME 유형을 결정합니다. 기본적으로 이 옵션은 선택되어 있지 않습니다.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭/탭하여 변경 내용을 저장합니다.
