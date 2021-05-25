---
title: Apache Tika를 사용하여 MIME 유형의 디지털 자산을 탐지합니다
description: Apache Tika를 활성화하여 AEM Assets이 파일 확장자 대신 업로드 작업 중에 컨텐츠 스트림에서 MIME 유형의 자산을 검색할 수 있도록 지원합니다.
contentOwner: AG
feature: 메타데이터,개발자 도구,자산 관리
role: Administrator,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Apache Tika를 사용하여 MIME 유형의 디지털 자산 {#detecting-mime-type-of-assets-using-apache-tika}을 검색합니다.

일반적으로 Adobe Experience Manager(AEM) Assets는 파일 확장자에서 업로드하는 MIME 유형의 자산을 감지합니다. Apache Tika를 사용하여 자산을 업로드하는 경우, AEM Assets은 파일 확장자 대신 업로드 작업 중에 컨텐츠 스트림에서 MIME 유형을 감지합니다.

이 기능은 기본적으로 비활성화됩니다. 이 기능을 사용하려면 구성 관리자에서 **일 CQ DAM Mime 유형** 서비스를 구성하십시오.

>[!NOTE]
>
>Apache Tika 라이브러리를 사용하는 MIME 유형 감지는 리소스를 많이 사용하는 작업입니다.

1. `https://[AEM_server]:[port]/system/console/configMgr` 로 이동하여 Configuration Manager 웹 콘솔을 엽니다.
1. 서비스 목록에서 **[!UICONTROL 일 CQ DAM MIME 유형 서비스]**&#x200B;를 찾아 옆에 있는 **[!UICONTROL 편집]** 아이콘을 탭/클릭하여 편집 모드에서 엽니다.

1. 파일 확장자를 무시하면서 업로드된 자산의 구문 분석을 사용하여 MIME 유형을 확인할 수 있도록 하려면 **[!UICONTROL 컨텐츠에서 MIME 감지 옵션을 선택하십시오.]** 기본적으로 이 옵션은 선택되어 있지 않습니다.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. **[!UICONTROL 저장]** 을 클릭/탭하여 변경 내용을 저장합니다.
