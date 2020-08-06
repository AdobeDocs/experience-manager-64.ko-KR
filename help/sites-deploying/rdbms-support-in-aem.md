---
title: AEM 6.4의 RDBMS 지원
seo-title: AEM 6.4의 RDBMS 지원
description: AEM 6.4의 관계형 데이터베이스 지속성 지원 및 사용 가능한 구성 옵션에 대해 알아봅니다.
seo-description: AEM 6.4의 관계형 데이터베이스 지속성 지원 및 사용 가능한 구성 옵션에 대해 알아봅니다.
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
translation-type: tm+mt
source-git-commit: 5513b24953438cc6c1b3f0027ff5535b4a1874d8
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---


# AEM 6.4의 RDBMS 지원{#rdbms-support-in-aem}

## 개요 {#overview}

AEM에서 관계형 데이터베이스 지속성 지원은 문서 마이크로커널을 사용하여 구현됩니다. 문서 마이크로커널은 MongoDB 지속성을 구현하는 데에도 사용되는 기준입니다.

Mongo Java API를 기반으로 하는 Java API로 구성됩니다. BlobStore API의 구현도 제공됩니다. 기본적으로 블로브는 데이터베이스에 저장됩니다.

구현 세부 정보에 대한 자세한 내용은 [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) 및 [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) 설명서를 참조하십시오.

>[!NOTE]
>
>PostgreSQL **9.4에** 대한 지원도 제공되지만 데모 용도로만 제공됩니다. 프로덕션 환경에서는 사용할 수 없습니다.

## 지원되는 데이터베이스 {#supported-databases}

AEM의 관계형 데이터베이스 지원 수준에 대한 자세한 내용은 [기술 요구 사항 페이지를 참조하십시오](/help/sites-deploying/technical-requirements.md).

## 구성 단계 {#configuration-steps}

OSGi 서비스를 구성하여 저장소를 `DocumentNodeStoreService` 만듭니다. MongoDB 외에도 관계형 데이터베이스 지속성을 지원하도록 확장되었습니다.

이를 수행하려면 AEM으로 데이터 소스를 구성해야 합니다. 이 작업은 `org.apache.sling.datasource.DataSourceFactory.config` 파일을 통해 수행됩니다. 로컬 구성 내의 OSGi 번들로 각 데이터베이스의 JDBC 드라이버를 별도로 제공해야 합니다.

JDBC 드라이버용 OSGi 번들을 만드는 단계는 Apache Sling 웹 사이트에서 이 [설명서를](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle) 참조하십시오.

>[!NOTE]
>
>일부 SQL 드라이버는 OSGi 번들로 이미 패키지되어 있습니다.
>
>이 경우 jar 파일을 복사하여 install-path/crx-quickstart/install/9에 넣습니다.

번들이 준비되면 아래 단계에 따라 AEM에 RDB 지속성을 구성합니다.

1. 데이터베이스 데몬이 시작되었고 AEM에서 사용할 활성 데이터베이스가 있는지 확인하십시오.
1. AEM 6.3 jar를 설치 디렉토리로 복사합니다.
1. 설치 디렉토리 `crx-quickstart\install` 에서 호출된 폴더를 만듭니다.
1. 디렉토리에서 다음 이름으로 구성 파일을 생성하여 문서 노드 저장소를 `crx-quickstart\install` 구성합니다.

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. 폴더에 다음 이름으로 다른 구성 파일을 생성하여 데이터 소스 및 JDBC 매개변수를 `crx-quickstart\install` 구성합니다.

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >지원되는 각 데이터베이스의 데이터 소스 구성에 대한 자세한 내용은 [데이터 소스 구성 옵션을 참조하십시오](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. 다음으로 AEM에 사용할 JDBC OSGi 번들을 준비합니다.

   1. https://dev.mysql.com/downloads/connector/j/에서 ZIP 보관 파일 다운로드
      * 버전은 5.1.38보다 커야 합니다.
   1. 보관 파일에서 `mysql-connector-java-version-bin.jar` (번들) 추출
   1. 웹 콘솔을 사용하여 번들 설치 및 시작:
      * http://serveraddress:serverport/system/console/bundles으로 *이동*
      * 설치/ **업데이트 선택**
      * 다운로드한 ZIP 보관에서 추출한 번들 선택
      * Oracle **Corporation의 MySQLcom.mysql.jdbc용 JDBC 드라이버가** 활성 상태인지 확인하고 시작합니다.

1. 마지막으로 AEM을 `crx3` 및 `crx3rdb` 런타임 모드로 시작합니다.

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## 데이터 소스 구성 옵션 {#data-source-configuration-options}

OSGi `org.apache.sling.datasource.DataSourceFactory-oak.config` 구성은 AEM 및 데이터베이스 지속성 계층 간의 통신에 필요한 매개 변수를 구성하는 데 사용됩니다.

다음 구성 옵션을 사용할 수 있습니다.

* `datasource.name:` 데이터 원본 이름입니다. The default is `oak`.

* `url:` JDBC에 사용해야 하는 데이터베이스의 URL 문자열. 각 데이터베이스 유형에는 고유한 URL 문자열 형식이 있습니다. 자세한 내용은 아래 [URL 문자열 형식을](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) 참조하십시오.

* `driverClassName:` JDBC 드라이버 클래스 이름입니다. 사용할 데이터베이스와 그 뒤에 연결되는 드라이버에 따라 다릅니다. 다음은 AEM에서 지원하는 모든 데이터베이스의 클래스 이름입니다.

   * `org.postgresql.Driver` for PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` for DB2;
   * `oracle.jdbc.OracleDriver` for Oracle;
   * `com.mysql.jdbc.Driver` for MySQL and MariaDB (실험적);
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` for Microsoft SQL Server(실험적).

* `username:` 데이터베이스가 실행되는 사용자 이름입니다.

* `password:` 데이터베이스 암호입니다.

### URL 문자열 형식 {#url-string-formats}

사용해야 하는 데이터베이스 유형에 따라 데이터 소스 구성에서 다른 URL 문자열 형식이 사용됩니다. 다음은 AEM에서 현재 지원하는 데이터베이스의 형식 목록입니다.

* `jdbc:postgresql:databasename` for PostgreSQL;

* `jdbc:db2://localhost:port/databasename` for DB2;
* `jdbc:oracle:thin:localhost:port:SID` for Oracle;
* `jdbc:mysql://localhost:3306/databasename` for MySQL and MariaDB (실험적);

* `jdbc:sqlserver://localhost:1453;databaseName=name` for Microsoft SQL Server (실험적).

## 알려진 제한 사항 {#known-limitations}

단일 데이터베이스가 있는 여러 AEM 인스턴스의 동시 사용은 RDBMS 지속성에서 지원되지만 동시 설치는 지원되지 않습니다.

이 문제를 해결하려면 먼저 단일 멤버와 함께 설치를 실행하고 설치를 마친 후 다른 멤버를 추가해야 합니다.

