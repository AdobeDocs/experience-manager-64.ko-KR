---
title: 구성 파일 가져오기 및 내보내기
seo-title: 구성 파일 가져오기 및 내보내기
description: 서버 환경 설정을 편집하거나 다른 AEM Forms 제품 인스턴스를 구성하기 위해 구성 파일을 가져오고 내보내는 방법을 알아봅니다.
seo-description: 서버 환경 설정을 편집하거나 다른 AEM Forms 제품 인스턴스를 구성하기 위해 구성 파일을 가져오고 내보내는 방법을 알아봅니다.
uuid: 32e8a709-2d7c-4740-9533-d53aa751bc58
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c1636537-f7dc-48d8-a3f0-9052bcd28b62
exl-id: dbad776a-60fd-4fcc-ba2a-a2f379f5462c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 구성 파일 {#importing-and-exporting-the-configuration-file} 가져오기 및 내보내기

[수동 구성] 페이지에서는 구성 설정의 사본을 XML 형식으로 다운로드할 수 있습니다. 이 파일의 설정은 모든 서버 기본 설정을 제어합니다. 그런 다음 파일을 편집하고 다시 서버에 업로드할 수 있습니다. 파일을 사용하여 다른 AEM Forms 제품 인스턴스를 구성할 수도 있습니다.

보안 위험을 방지하기 위해 디렉토리 서버의 바인딩 암호 값은 내보낸 구성 파일에 포함되지 않습니다. 파일을 새 시스템으로 가져오기 전에 XML 파일의 암호를 업데이트합니다.

>[!NOTE]
>
>구성 파일을 가져오면 파일의 정보를 기반으로 AEM Forms가 다시 구성됩니다. AEM Forms 제품 및 XML에 익숙한 시스템 관리자나 전문 서비스 컨설턴트만 구성 파일 수정을 고려해야 합니다. 예를 들어 손상된 설정을 다시 구성하기 위해 구성 파일을 편집해야 할 수 있습니다.

**구성 정보 내보내기**

1. 관리 콘솔에서 설정 > 사용자 관리 > 구성 > 구성 파일 가져오기 및 내보내기를 클릭합니다.
1. 내보내기를 클릭합니다. Microsoft Internet Explorer를 사용하는 경우 파일을 저장할 위치를 지정하라는 메시지가 표시됩니다. Firefox를 사용하는 경우 해당 파일이 데스크탑에 저장됩니다.

**구성 정보 가져오기**

1. 관리 콘솔에서 설정 > 사용자 관리 > 구성 > 구성 파일 가져오기 및 내보내기를 클릭합니다.
1. 찾아보기 를 클릭하여 구성 파일을 찾고 가져오기를 클릭한 다음 확인을 클릭합니다.
