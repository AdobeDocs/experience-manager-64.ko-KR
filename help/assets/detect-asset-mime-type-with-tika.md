---
title: Apache Tika를 사용하여 디지털 자산의 MIME 유형 감지
description: Apache Tika를 활성화하면 AEM Assets이 파일 확장자 대신 업로드 작업 중에 콘텐츠 스트림에서 MIME 유형의 자산을 검색할 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# Apache Tika를 사용하여 디지털 자산의 MIME 유형 감지 {#detecting-mime-type-of-assets-using-apache-tika}

일반적으로 Adobe Experience Manager(AEM) 자산은 파일 확장자에서 업로드하는 자산의 MIME 유형을 감지합니다. Apache Tika를 사용하여 에셋을 업로드하면 AEM Assets은 업로드 작업 중에 파일 확장자 대신 컨텐츠 스트림에서 MIME 형식을 감지합니다.

이 기능은 기본적으로 비활성화됩니다. 이 기능을 활성화하려면 Configuration Manager에서 **일 CQ DAM Mime 형식** 서비스를 구성합니다.

>[!NOTE]
>
>Apache Tika 라이브러리를 사용하는 MIME 유형 감지는 리소스를 많이 사용하는 작업입니다.

1. 이동 `https://[AEM_server]:[port]/system/console/configMgr` 으로 이동하여 Configuration Manager 웹 콘솔을 엽니다.
1. 서비스 목록에서 **[!UICONTROL Day CQ DAM MIME 유형 서비스를]** 찾아 옆에 있는 **[!UICONTROL 편집]** 아이콘을 탭/클릭하여 편집 모드에서 엽니다.

1. 파일 **[!UICONTROL 확장자를 무시하고 업로드한 자산의 구문 분석을 활성화하여 MIME 형식을 결정하려면 [콘텐츠에서]** MIME 감지] 옵션을 선택합니다. 기본적으로 이 옵션은 선택되지 않습니다.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 저장을 클릭/ **[!UICONTROL 탭하여]** 변경 사항을 저장합니다.
