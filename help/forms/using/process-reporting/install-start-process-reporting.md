---
title: 프로세스 보고 시작하기
seo-title: 프로세스 보고 시작하기
description: JEE 프로세스 보고에서 AEM Forms을 시작하기 위해 따라야 하는 절차
seo-description: JEE 프로세스 보고에서 AEM Forms을 시작하기 위해 따라야 하는 절차
uuid: 86ba17da-57e5-4e7a-a864-583d8c0f830e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: process-reporting
discoiquuid: a0f81621-6ccd-46e2-85d7-2eb4ee3cdb91
exl-id: 0af2e992-6670-4e31-9d26-ab74c5b9df8e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 0%

---

# 프로세스 보고 시작하기 {#getting-started-with-process-reporting}

프로세스 보고 를 통해 AEM Forms 사용자는 AEM Forms 구현에서 현재 정의된 AEM Forms 프로세스에 대한 정보를 쿼리할 수 있습니다. 하지만 Process Reporting은 AEM Forms 리포지토리에서 직접 데이터에 액세스하지는 않습니다. 데이터는 ProcessDataPublisher &amp; ProcessDataStorage 서비스&#x200B;*s에 의해 Process Reporting 리포지토리에 처음 게시됩니다.* 그런 다음 Process Reporting의 보고서와 쿼리는 저장소에 게시된 Process Reporting 데이터에서 생성됩니다. 프로세스 보고가 Forms Workflow 모듈의 일부로 설치됩니다.

이 문서에서는 Process Reporting 저장소에 AEM Forms 데이터를 게시할 수 있도록 하는 절차에 대해 자세히 설명합니다. 그런 다음 프로세스 보고를 사용하여 보고서 및 쿼리를 실행할 수 있습니다. 또한 Process Reporting 서비스를 구성하는 데 사용할 수 있는 옵션도 다룹니다.

## 프로세스 보고 사전 요구 사항 {#process-reporting-pre-requisites}

### 불필요한 프로세스 제거 {#purge-non-essential-processes}

현재 Forms Workflow을 사용 중인 경우 AEM Forms 데이터베이스에 상당한 양의 데이터가 포함될 수 있습니다

Process Reporting publishing Services가 현재 데이터베이스에서 사용할 수 있는 모든 AEM Forms 데이터를 게시합니다. 이것은 데이터베이스에 보고서와 쿼리를 실행하지 않으려는 기존 데이터가 포함되어 있는 경우 보고에 필요하지 않더라도 해당 데이터가 모두 리포지토리에 게시된다는 것을 의미합니다. 서비스를 실행하여 데이터를 Process Reporting 저장소에 게시하기 전에 이 데이터를 삭제하는 것이 좋습니다. 이렇게 하면 게시자 서비스와 보고를 위해 데이터를 쿼리하는 서비스의 성능이 모두 향상됩니다.

AEM Forms 프로세스 데이터 삭제에 대한 자세한 내용은 [프로세스 데이터 삭제](https://help.adobe.com/en_US/livecycle/11.0/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7cb2.2.html)를 참조하십시오.

>[!NOTE]
>
>Purge Utility에 대한 팁과 트릭은 [프로세스 및 작업 제거](https://www.adobe.com/content/dam/Adobe/en/devnet/livecycle/pdfs/purging_processes_jobs.pdf)에 있는 Adobe Developer Connection 문서를 참조하십시오.

## 프로세스 보고 서비스 구성 {#configuring-process-reporting-services}

### 프로세스 데이터 게시 예약 {#schedule-process-data-publishing}

Process Reporting Services는 예약된 기준에 따라 AEM Forms 데이터베이스의 데이터를 Process Reporting 저장소에 게시합니다.

이 작업은 리소스를 많이 사용할 수 있으며 AEM Forms 서버의 성능에 영향을 줄 수 있습니다. AEM Forms 서버 사용 시간 슬롯 외부에서 예약하는 것이 좋습니다.

기본적으로 데이터 게시는 매일 오전 2시에 실행되도록 예약됩니다.

게시 일정을 변경하려면 다음 단계를 수행하십시오.

>[!NOTE]
>
>클러스터에서 AEM Forms 구현을 실행 중인 경우 클러스터의 각 노드에서 다음 단계를 수행하십시오.

#### JBoss 애플리케이션 서버 {#jboss-application-server}

1. AEM Forms 서버 인스턴스를 중지합니다.
   * (Windows의 경우) 편집기에서 `[*JBoss root*]/bin/run.conf.bat` 파일을 엽니다.
   * (Linux, AIX 및 Solaris의 경우) `[*JBoss root*]/bin/run.conf.sh` 파일이 편집기에 있습니다.

1. JVM 인수 `-Dreporting.publisher.cron = <expression>.` 추가

   예:다음 아이콘 표현식으로 인해 Process Reporting에서 5시간마다 AEM Forms 데이터를 Process Reporting 저장소에 게시합니다.

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. `run.conf.bat` 파일을 저장하고 닫습니다.

1. AEM Forms 서버 인스턴스를 다시 시작합니다.

#### WebSphere 응용 프로그램 서버 {#websphere-application-server}

1. AEM Forms 서버 인스턴스를 중지합니다.
1. WebSphere 관리 콘솔에 로그인합니다. 탐색 트리에서 **Servers** > **Application server**&#x200B;를 클릭한 다음 오른쪽 창에서 서버 이름을 클릭합니다.

1. 서버 인프라에서 **Java 및 프로세스 관리** > **프로세스 정의**&#x200B;를 클릭합니다.

1. 추가 속성에서 **Java 가상 컴퓨터**&#x200B;를 클릭합니다.

   일반 JVM 인수 상자에서 `-Dreporting.publisher.cron = <expression>.` 인수를 추가합니다.

   **예**:다음 아이콘 표현식으로 인해 Process Reporting에서 5시간마다 AEM Forms 데이터를 Process Reporting 저장소에 게시합니다.

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. **적용**&#x200B;을 클릭하고 확인 을 클릭한 다음 **마스터 구성에 직접 저장**&#x200B;을 클릭합니다.

1. AEM Forms 서버 인스턴스를 다시 시작합니다.

#### WebLogic 응용 프로그램 서버 {#weblogic-application-server}

1. AEM Forms 서버 인스턴스를 중지합니다.
1. WebLogic 관리 콘솔에 로그인합니다. WebLogic 관리 콘솔의 기본 주소는 `https://[hostname]:[port]/console`입니다.

1. 변경 센터에서 **잠금 및 편집**&#x200B;을 클릭합니다.

1. 도메인 구조에서 **환경** > **서버**&#x200B;를 클릭하고 오른쪽 창에서 관리 서버 이름을 클릭합니다.

1. 다음 화면에서 **구성** 탭 > **서버 시작** 탭을 클릭합니다.

1. 인수 상자에서 JVM 인수 `-Dreporting.publisher.cron = <expression>`을 추가합니다.

   **예**:다음 아이콘 표현식으로 인해 Process Reporting에서 5시간마다 AEM Forms 데이터를 Process Reporting 저장소에 게시합니다.

   `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. **저장**&#x200B;을 클릭한 다음 **변경 내용 활성화**&#x200B;를 클릭합니다.

1. AEM Forms 서버 인스턴스를 다시 시작합니다.

![processdatapubliserservice](assets/processdatapublisherservice.png)

### ProcessDataStorage 서비스 {#processdatastorage-service}

ProcessDataStorageProvider 서비스는 ProcessDataPublisher 서비스에서 프로세스 데이터를 수신하여 Process Reporting 저장소에 저장합니다.

각 게시 주기에 따라 데이터는 사전 정의된 루트 폴더의 하위 폴더에 저장됩니다.

관리 콘솔을 사용하여 루트(**default**&#x200B;를 구성할 수 있습니다.`/content/reporting/pm`) 위치 및 하위 폴더(**default**:`/yyyy/mm/dd/hh/mi/ss`) 프로세스 데이터가 저장되는 계층 형식입니다.

#### 프로세스 보고 저장소 위치를 구성하려면 {#to-configure-the-process-reporting-repository-locations}

1. 관리자 자격 증명을 사용하여 **관리 콘솔**&#x200B;에 로그인합니다. 관리 콘솔의 기본 URL은 `https://[server]:[port]/adminui`입니다.
1. **홈** > **서비스** > **응용 프로그램 및 서비스** > **서비스 관리**&#x200B;로 이동하여 **ProcessDataStorageProvider** 서비스를 엽니다.

   ![process-data-storage-service](assets/process-data-storage-service.png)

   **루트 폴더**

   보고를 위해 프로세스 데이터를 저장할 CRX 위치입니다.

   `Default`: `/content/reporting/pm`

   **폴더 계층**

   프로세스 생성 시간에 따라 프로세스 데이터가 저장되는 폴더 계층 구조

   `Default`:  `/yyyy/mm/dd/hh/mi/ss`

1. **저장**&#x200B;을 클릭합니다.

### ReportConfiguration 서비스 {#reportconfiguration-service}

ReportConfiguration 서비스는 프로세스 보고 쿼리 서비스를 구성하기 위해 Process Reporting에서 사용합니다.

#### ReportingConfiguration 서비스를 구성하려면 {#to-configure-the-reportingconfiguration-service}

1. CRX 관리자 자격 증명을 사용하여 **구성 관리자**&#x200B;에 로그인합니다. 구성 관리자의 기본 URL은 `https://[*server*]:[*port*]/lc/system/console/configMgr`입니다.
1. **ReportingConfiguration** 서비스를 엽니다.
1. **레코드 수**

   저장소에서 쿼리를 실행할 때 결과에는 많은 수의 레코드가 포함될 수 있습니다. 결과 세트가 큰 경우 쿼리 실행에서 서버 리소스를 사용할 수 있습니다.

   큰 결과 세트를 처리하기 위해 ReportConfiguration 서비스는 쿼리 처리를 레코드 배치로 분할합니다. 이렇게 하면 시스템 로드가 줄어듭니다.

   `Default`:  `1000`

   **CRX 스토리지 경로**

   보고를 위해 프로세스 데이터를 저장할 CRX 위치입니다.

   `Default`:  `/content/reporting/pm`

   >[!NOTE]
   >
   >ProcessDataStorage 구성 옵션 **루트 폴더**&#x200B;에 지정된 위치와 동일합니다.
   >
   >ProcessDataStorage 구성에서 루트 폴더 옵션을 업데이트하는 경우 ReportConfiguration 서비스에서 CRX 저장소 경로 위치를 업데이트해야 합니다.

1. **저장**&#x200B;을 클릭하고 **CQ 구성 관리자**&#x200B;를 닫습니다.

### ProcessDataPublisher 서비스 {#processdatapublisher-service}

ProcessDataPublisher 서비스는 AEM Forms 데이터베이스에서 프로세스 데이터를 가져오고 이 데이터를 저장할 ProcessDataStorageProvider 서비스에 게시합니다.

#### ProcessDataPublisher 서비스를 구성하려면   {#to-configure-processdatapublisher-service-nbsp}

1. 관리자 자격 증명을 사용하여 **관리 콘솔**&#x200B;에 로그인합니다.

   기본 URL은 `https://[server]:port]/adminui/`.

1. **홈** > **서비스** > **응용 프로그램 및 서비스** > **서비스 관리**&#x200B;로 이동하여 **ProcessDataPublisher** 서비스를 엽니다.

![processdatapubliserservice-1](assets/processdatapublisherservice-1.png)

**데이터 게시**

프로세스 데이터 게시를 시작하려면 이 옵션을 활성화합니다. 기본적으로 이 옵션은 비활성화됩니다.

Process Reporting 구성 요소와 관련된 모든 구성이 적절하게 설정된 경우에만 Process Reporting을 활성화합니다.

또는 더 이상 필요하지 않은 프로세스 데이터 게시를 비활성화하려면 이 옵션을 사용합니다.

`Default`:  `Off`

**배치 간격(초)**

ProcessDataPublisher 서비스가 실행될 때마다 서비스가 먼저 배치 간격별로 서비스를 마지막으로 실행한 이후 시간을 분할합니다. 그런 다음 서비스는 AEM Forms 데이터의 각 간격을 별도로 처리합니다.

이렇게 하면 순환 내에서 각 실행(배치)하는 동안 게시자가 처리하는 데이터의 크기를 제어하는 데 도움이 됩니다.

예를 들어 게시자가 매일 실행되는 경우 한 번의 실행으로 하루 전체 데이터를 처리하는 대신 기본적으로 처리를 각각 1시간의 24개의 배치로 분할합니다.

`Default`:  `3600`

`Unit`:  `Seconds`

**잠금 시간 초과(초)**

게시자 서비스는 데이터 처리를 시작할 때 잠금을 획득하여 게시자의 여러 인스턴스가 동시에 실행 및 데이터 처리를 시작하지 않습니다.

잠금을 획득한 게시자 서비스가 잠금 시간 초과 값으로 정의된 시간(초) 동안 유휴 상태인 경우, 다른 게시자 서비스 인스턴스가 처리를 계속할 수 있도록 해당 잠금이 해제됩니다.

`Default`:  `3600`

`Unit`:  `Seconds`

**다음에서 데이터 게시**

AEM Forms 환경에는 환경이 설정된 시간의 데이터가 포함되어 있습니다.

기본적으로 ProcessDataPublisher 서비스는 AEM Forms 데이터베이스에서 모든 데이터를 가져옵니다.

보고 요구 사항에 따라 특정 날짜 및 시간 이후에 데이터에 대한 보고서 및 쿼리를 실행하려는 경우 날짜 및 시간을 지정하는 것이 좋습니다. 그런 다음 게시 서비스는 해당 날짜부터 게시합니다.

`Default`:  `01-01-1970 00:00:00`

`Format`:  `dd-MM-yyyy HH:mm:ss`

## 프로세스 보고 사용자 인터페이스 {#accessing-the-process-reporting-user-interface} 액세스

프로세스 보고를 위한 사용자 인터페이스는 브라우저 기반입니다.

Process Reporting을 설정한 후에는 AEM Forms 설치의 다음 위치에서 Process Reporting 작업을 시작할 수 있습니다.

`https://<server>:<port>/lc/pr`

### 프로세스 보고에 로그인 {#log-in-to-process-reporting}

프로세스 보고 URL(https://&lt;server>:&lt;port>/lc/pr)로 이동하면 로그인 화면이 표시됩니다.

프로세스 보고 모듈에 로그인할 자격 증명을 지정합니다.

>[!NOTE]
>
>Process Reporting 사용자 인터페이스에 로그인하려면 다음 AEM Forms 권한이 필요합니다.
>
>`PERM_PROCESS_REPORTING_USER`

![캡처](assets/capture.png)

프로세스 보고에 로그인하면 **[!UICONTROL 홈]** 화면이 표시됩니다.

### 프로세스 보고 홈 화면 {#process-reporting-home-screen}

![process-reporting-home-screen](assets/process-reporting-home-screen.png)

**프로세스 보고 트리 보기:**  홈 화면의 왼쪽에 있는 트리 보기에는 Process Reporting 모듈에 대한 항목이 포함되어 있습니다.

트리 보기는 다음과 같은 최상위 항목으로 구성됩니다.

**보고서:** 이 항목에는 Process Reporting과 함께 제공되는 기본 보고서가 포함되어 있습니다.

사전 정의된 보고서에 대한 자세한 내용은 [프로세스 보고 중 사전 정의된 보고서](pre-defined-reports-in-process-reporting.md)를 참조하십시오.

**임시 쿼리:**  이 항목에는 프로세스 및 작업에 대한 필터 기반 검색을 수행하는 옵션이 포함되어 있습니다.

임시 쿼리에 대한 자세한 내용은 프로세스 보고 의 [임시 쿼리](adhoc-queries-in-process-reporting.md)를 참조하십시오.

**사용자 지정:** 사용자 지정 노드는 사용자가 만드는 사용자 지정 보고서를 표시합니다.

사용자 지정 보고서를 만들고 표시하는 절차는 [Process Reporting의 사용자 지정 보고서](/help/forms/using/process-reporting/process-reporting-custom-reports.md)를 참조하십시오.

**프로세스 보고 제목 표시줄:**  프로세스 보고 제목 표시줄에는 사용자 인터페이스에서 작업할 때 사용할 수 있는 몇 가지 일반 옵션이 포함되어 있습니다.

**프로세스 보고 제목:**  제목 표시줄의 왼쪽 모서리에 프로세스 보고 제목이 표시됩니다.

언제든지 제목을 클릭하여 홈 화면으로 돌아갑니다.

**마지막 업데이트 시간:**  프로세스 데이터는 AEM Forms 데이터베이스에서 예약된 대로 Process Reporting 저장소에 게시됩니다.

마지막 업데이트 시간은 데이터 업데이트가 Process Reporting 저장소에 푸시된 마지막 날짜 및 시간을 표시합니다.

데이터 게시 서비스 및 이 서비스의 예약 방법에 대한 자세한 내용은 프로세스 보고 시작하기 문서에서 [프로세스 데이터 게시 예약](/help/forms/using/process-reporting/install-start-process-reporting.md#p-schedule-process-data-publishing-p)을 참조하십시오.

**Process Reporting 사용자:** 로그인한 사용자 이름이 마지막 업데이트 시간 오른쪽에 표시됩니다.

**프로세스 보고 제목 표시줄 드롭다운 목록:**  프로세스 보고 제목 표시줄의 오른쪽 모서리에 있는 드롭다운 목록에는 다음 옵션이 있습니다.

* **[!UICONTROL 동기화]**:포함된 Process Reporting 저장소를 AEM Forms 데이터베이스와 동기화합니다.
* **[!UICONTROL 도움말]**:프로세스 보고에 대한 도움말 설명서를 봅니다.
* **[!UICONTROL 로그아웃]**:프로세스 보고 로그아웃
