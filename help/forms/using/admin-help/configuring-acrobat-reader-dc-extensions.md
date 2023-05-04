---
title: 데이터 캡처를 위한 Acrobat Reader DC 확장 구성
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: 데이터 캡처용 Acrobat Reader DC 확장을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 3609ad29-f5b4-4426-8bbc-7c2e38f9b140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# 데이터 캡처를 위한 Acrobat Reader DC 확장 구성 {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 설치 사용자가 Content Services(사용 중지)의 데이터 캡처 기능을 사용하는 경우 이러한 사용자에 대해 읽기 전용 액세스 권한을 가진 역할을 만드는 것이 좋습니다.

***참고**: Adobe® LiveCycle® Content Services ES(사용 중지)는 LiveCycle과 함께 설치된 컨텐츠 관리 시스템입니다. 이를 통해 사용자가 인간 중심 프로세스를 설계, 관리, 모니터링 및 최적화할 수 있습니다. 컨텐츠 서비스(더 이상 사용되지 않음) 지원은 12/31/2014에 종료됩니다.

데이터 캡처에서는 SampleReaderExtensionsCredential에 액세스하기 위해 사용자 역할을 할당해야 합니다. 표준 Trust Administrator 역할을 할당할 수 있지만, 이 역할을 통해 일반 비관리 사용자에게 PKI Trust 설정을 제어하고 PKI Credentials를 관리하는 강력한 관리자 권한이 부여되므로 프로덕션 환경에서 AEM Forms 설치 보안을 손상시킬 수 있습니다. AEM Forms 시스템 관리자는 Trust Store에 대한 읽기 전용 액세스 권한만 부여하는 역할을 만들고 이 새 역할을 데이터 캡처를 사용하는 비관리자 사용자에게 할당하는 것이 좋습니다.

## 데이터 캡처 사용자를 위한 역할 만들기 {#create-a-role-for-data-capture-users}

1. 관리 콘솔에서 설정 > 사용자 관리 > 역할 관리 를 클릭한 다음 새 역할을 클릭합니다.
1. 해당 필드에 역할 이름(예: 데이터 캡처 사용자)과 설명을 입력한 다음 다음을 클릭합니다.
1. 역할 권한 화면에서 권한 찾기를 클릭한 다음 사용 가능한 권한 목록에서 자격 증명 읽기를 선택합니다.
1. 확인을 클릭한 다음 마침을 클릭합니다.

## 데이터 캡처 역할 할당 {#assign-the-data-capture-role}

1. 관리 콘솔에서 설정 > 사용자 관리 > 역할 관리 를 클릭한 다음 찾기를 클릭합니다.
1. 만든 데이터 캡처 사용자 역할을 클릭합니다.
1. 역할 사용자/그룹 탭에서 사용자/그룹 찾기를 클릭합니다.
1. 사용자 및 그룹 찾기 화면에서 찾기를 클릭하고 데이터 캡처 사용자 역할이 필요한 사용자를 선택한 다음 확인을 클릭합니다.
1. 역할 편집 화면에서 저장을 클릭합니다.
