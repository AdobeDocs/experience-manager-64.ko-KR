---
title: "DB2 데이터베이스: 매주 프로세스 실행"
seo-title: "DB2 database: Running a process weekly"
description: AEM Forms DB2 데이터베이스의 성능을 향상시키는 방법을 참조하십시오.
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---

# DB2 데이터베이스: 매주 프로세스 실행{#db-database-running-a-process-weekly}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms DB2 데이터베이스가 느리게 실행되면 매주 다음 프로세스를 실행하면 성능이 향상됩니다.

1. DB2 컨트롤 센터 시작:

   (Windows) 시작 > 프로그램 > IBM DB2 > 일반 관리 도구 > 제어 센터를 선택합니다.

   (Linux 및 UNIX) 명령 프롬프트에서 `db2jcc` 명령.

1. DB2 Control Center 객체 트리에서 모든 데이터베이스를 클릭합니다.
1. AEM Forms용으로 만든 데이터베이스를 클릭하고 Tables 폴더를 클릭합니다.
1. 목차 창에서 데이터베이스 테이블을 모두 선택하고 마우스 오른쪽 단추로 누른 다음 통계 실행을 선택합니다.
1. 통계 > 인덱스 통계로 이동합니다.
1. 모든 인덱스에 대한 통계 수집을 선택하고 확장된 세부 통계가 있는 인덱스에 대한 통계 수집을 선택한 다음 확인을 누릅니다.

프로세스가 완료되면 메시지가 나타납니다. 메시지를 닫습니다.
