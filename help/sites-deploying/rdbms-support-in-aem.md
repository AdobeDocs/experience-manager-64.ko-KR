---
title: AEM 6.4의 RDBMS 지원
seo-title: RDBMS Support in AEM 6.4
description: AEM 6.4의 관계형 데이터베이스 지속성 지원 및 사용 가능한 구성 옵션에 대해 알아봅니다.
seo-description: Learn about the relational database persistence support in AEM 6.4 and the available configuration options.
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
feature: Configuring
exl-id: 89523bb4-e4c4-469c-802b-6fe27c816a2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 1%

---

# AEM 6.4의 RDBMS 지원{#rdbms-support-in-aem}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

AEM의 관계형 데이터베이스 지속성 지원은 문서 마이크로커널을 사용하여 구현됩니다. 문서 마이크로커널은 MongoDB 지속성 구현에도 사용되는 기반입니다.

Mongo Java API를 기반으로 하는 Java API로 구성됩니다. BlobStore API의 구현도 제공됩니다. 기본적으로 blob은 데이터베이스에 저장됩니다.

구현 세부 사항에 대한 자세한 내용은 [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) 및 [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) 설명서.

>[!NOTE]
>
>지원 대상 **PostgreSQL 9.4** 도 제공되지만, 데모용으로만 제공됩니다. 프로덕션 환경에는 사용할 수 없습니다.

## 지원되는 데이터베이스 {#supported-databases}

AEM의 관계형 데이터베이스 지원 수준에 대한 자세한 내용은 [기술 요구 사항 페이지](/help/sites-deploying/technical-requirements.md).

## 구성 단계 {#configuration-steps}

저장소는 `DocumentNodeStoreService` OSGi 서비스. MongoDB 외에 관계형 데이터베이스 지속성을 지원하도록 확장되었습니다.

이를 수행하려면 AEM으로 데이터 소스를 구성해야 합니다. 이 작업은 를 통해 수행됩니다 `org.apache.sling.datasource.DataSourceFactory.config` 파일. 각 데이터베이스에 대한 JDBC 드라이버는 로컬 구성 내의 OSGi 번들로 별도로 제공해야 합니다.

JDBC 드라이버용 OSGi 번들을 생성하는 단계는 다음을 참조하십시오 [설명서](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle) 를 클릭합니다.

>[!NOTE]
>
>일부 SQL 드라이버는 이미 OSGi 번들로 패키지되어 있습니다.
>
>이 경우 jar 파일을 install-path/crx-quickstart/install/9에 복사하면 됩니다.

번들이 준비되면 아래 절차에 따라 RDB 지속성을 사용하여 AEM을 구성하십시오.

1. 데이터베이스 데몬이 시작되고 AEM에 사용할 활성 데이터베이스가 있는지 확인하십시오.
1. AEM 6.3 jar를 설치 디렉토리에 복사합니다.
1. 라는 폴더를 만듭니다. `crx-quickstart\install` 를 클릭합니다.
1. 에서 다음 이름으로 구성 파일을 만들어 문서 노드 저장소를 구성합니다. `crx-quickstart\install` 디렉토리:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. 에서 다음 이름으로 다른 구성 파일을 생성하여 데이터 소스 및 JDBC 매개 변수를 구성합니다 `crx-quickstart\install` 폴더:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >지원되는 각 데이터베이스에 대한 데이터 소스 구성에 대한 자세한 내용은 [데이터 소스 구성 옵션](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. 다음으로 AEM에서 사용할 JDBC OSGi 번들을 준비합니다.

   1. https://dev.mysql.com/downloads/connector/j/에서 ZIP 아카이브를 다운로드합니다.
      * 버전은 >= 5.1.38이어야 합니다.
   1. 추출 `mysql-connector-java-version-bin.jar` 보관 파일의 (번들)
   1. 웹 콘솔을 사용하여 번들을 설치하고 시작합니다.
      * 이동 *http://serveraddress:serverport/system/console/bundles*
      * 선택 **설치/업데이트**
      * 다운로드한 ZIP 아카이브에서 추출한 번들을 찾아 선택합니다
      * 확인 **Oracle Corporation의 MySQLcom.mysql.jdbc용 JDBC 드라이버** 활성 상태이고 시작합니다.

1. 마지막으로 AEM을 `crx3` 및 `crx3rdb` 런타임 모드:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## 데이터 소스 구성 옵션 {#data-source-configuration-options}

다음 `org.apache.sling.datasource.DataSourceFactory-oak.config` OSGi 구성은 AEM과 데이터베이스 지속성 계층 간의 통신에 필요한 매개 변수를 구성하는 데 사용됩니다.

다음 구성 옵션을 사용할 수 있습니다.

* `datasource.name:` 데이터 소스 이름입니다. 기본값은 `oak`입니다.

* `url:` JDBC와 함께 사용해야 하는 데이터베이스의 URL 문자열입니다. 각 데이터베이스 유형에는 자체 URL 문자열 형식이 있습니다. 자세한 내용은 [URL 문자열 형식](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) 아래의 제품에서 사용할 수 있습니다.

* `driverClassName:` JDBC 드라이버 클래스 이름입니다. 사용할 데이터베이스에 따라, 다음에 연결하는 데 필요한 드라이버에 따라 다릅니다. 다음은 AEM에서 지원하는 모든 데이터베이스의 클래스 이름입니다.

   * `org.postgresql.Driver` PostgreSQL용
   * `com.ibm.db2.jcc.DB2Driver` DB2용
   * `oracle.jdbc.OracleDriver` oracle
   * `com.mysql.jdbc.Driver` MySQL 및 MariaDB(실험)
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` Microsoft SQL Server용(실험).

* `username:` 데이터베이스가 실행되는 사용자 이름입니다.

* `password:` 데이터베이스 암호입니다.

### URL 문자열 형식 {#url-string-formats}

사용해야 하는 데이터베이스 유형에 따라 데이터 소스 구성에서 다른 URL 문자열 형식이 사용됩니다. 다음은 AEM에서 현재 지원하는 데이터베이스의 형식 목록입니다.

* `jdbc:postgresql:databasename` PostgreSQL용

* `jdbc:db2://localhost:port/databasename` DB2용
* `jdbc:oracle:thin:localhost:port:SID` oracle
* `jdbc:mysql://localhost:3306/databasename` MySQL 및 MariaDB(실험)

* `jdbc:sqlserver://localhost:1453;databaseName=name` Microsoft SQL Server용(실험).

## 알려진 제한 사항 {#known-limitations}

단일 데이터베이스와 함께 여러 AEM 인스턴스를 동시에 사용하는 것은 RDBMS 지속성에서 지원되지만 동시 설치는 지원되지 않습니다.

이 문제를 해결하려면 먼저 단일 멤버로 설치를 실행하고 설치가 완료된 후 다른 멤버를 추가합니다.
