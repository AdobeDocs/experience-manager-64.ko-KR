---
title: JEE에서 AEM Forms에 대해 지원되는 플랫폼
seo-title: JEE에서 AEM Forms에 대해 지원되는 플랫폼
description: JEE에 AEM Forms 설치를 위해 필수 및 지원되는 인프라 구성 요소 목록
seo-description: JEE에 AEM Forms 설치를 위해 필수 및 지원되는 인프라 구성 요소 목록
uuid: 22f05fd4-f9fc-423e-8a86-1e75df4b2b44
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 1b9f8d98-e7e8-4b9b-a0df-52ccba324da3
role: Administrator
exl-id: 6609c625-0591-42fd-910b-c7c65d52c5f1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3316'
ht-degree: 1%

---

# JEE에서 AEM Forms에 대해 지원되는 플랫폼 {#supported-platforms-for-aem-forms-on-jee}

## 지원되는 플랫폼 {#supported-platforms}

### 지원 수준 {#support-levels}

JEE 서버의 AEM Forms은 지원되는 운영 체제, 애플리케이션 서버, 데이터베이스, 데이터베이스 드라이버, JDK, LDAP 서버 및 이메일 서버의 조합을 사용하여 설정할 수 있습니다.

이 문서에서는 JEE에서 AEM Forms에 대해 지원되는 클라이언트 및 서버 플랫폼을 나열합니다. Adobe은 권장 구성과 기타 구성에 대해 여러 수준의 지원을 제공합니다. 또한 이 문서에서는 지원되는 다른 소프트웨어 및 해당 버전, 예외, 패치 정의 및 타사 소프트웨어 패치 지원 정책을 나열합니다.

>[!NOTE]
>
>* 지원되는 서버 플랫폼에 대한 전체 예외 목록은 [지원되는 서버 플랫폼에 대한 예외](#exceptions-to-supported-server-platforms)를 참조하십시오.
>* AEM Forms on JEE는 지원되는 운영 체제 및 응용 프로그램의 영어, 프랑스어, 독일어 및 일본어 버전만 지원합니다.

>



### 권장 구성 {#recommendedconfigurations}

Adobe은 이러한 구성을 권장하며 표준 소프트웨어 유지 관리 계약의 일부로 전체 또는 제한된 지원을 제공합니다.

<table> 
 <tbody> 
  <tr> 
   <th>지원 수준</th> 
   <th>설명</th> 
  </tr> 
  <tr> 
   <td>A:지원됨<br /> </td> 
   <td>Adobe은 이 구성에 대한 모든 지원 및 유지 관리를 제공합니다. 이 구성은 Adobe의 품질 보증 프로세스에서 다룹니다.</td> 
  </tr> 
  <tr> 
   <td>R:제한된 지원</td> 
   <td>Adobe은 특정 사전 요구 사항을 충족한 후 이 구성에 대한 모든 지원을 제공합니다. 사전 요구 사항에 대해 알아보고 지원 요청을 제기하려면 Adobe 엔터프라이즈 지원에 문의하십시오.</td> 
  </tr> 
  <tr> 
   <td>L:제한된 지원</td> 
   <td>Adobe은 특정 사전 요구 사항을 충족한 후 이 구성에 대한 모든 지원 및 유지 관리를 제공합니다. 일부 기능은 구성에서 사용할 수 없습니다. 전제 조건에 대한 자세한 내용을 알고 지원을 요청하려면 Adobe 엔터프라이즈 지원에 문의하십시오.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 지원되지 않는 구성 {#unsupported-configurations}

| 지원 수준 | 설명 |
|---|---|
| E:작동해야 함 | 구성이 작동될 것으로 예상되며, 반대의 보고는 없습니다. |
| Z:지원되지 않음 | 구성이 지원되지 않습니다. Adobe은 구성 작동 여부에 대한 설명을 만들지 않으며 구성을 지원하지 않습니다. |

### Java Virtual Machine(JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms을 사용하려면 JDK(Java Development Kit) 배포에서 제공하는 Java Virtual Machine을 실행해야 합니다. Adobe Experience Manager은 다음 버전의 Java Virtual Machine을 사용하여 작동합니다.

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>플랫폼</strong></p> </th> 
   <th><p><strong>지원 수준</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Oracle Java™ SE 8(64비트)</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>사소한 릴리스 및 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® J9 가상 컴퓨터(빌드 2.8, JRE 1.8.0)</td> 
   <td>A:지원됨</td> 
   <td>사소한 릴리스 및 업데이트</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* AEM Forms on JEE는 프로덕션 환경에서 64비트 JVM만 지원합니다.
>* 프로덕션 환경의 안전과 보안을 유지하고 최신 Java 업데이트를 설치하려면 Java 공급업체에서 제공하는 보안 게시판을 추적하는 것이 좋습니다.

>



### 데이터베이스 및 CRX 지속성 {#databases-and-crx-persistence}

#### AEM 지속성 지원 {#aem-persistence-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>플랫폼</strong></p> </td> 
   <td><p><strong> 설명</strong></p> </td> 
   <td><p><strong>지원 수준</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>파일 시스템</p> </td> 
   <td><p>저장소 마이크로커널(TAR MK 파일)</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr> 
  <tr> 
   <td><p>MongoDB Enterprise 3.4</p> </td> 
   <td><p>저장소 마이크로커널</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>저장소 마이크로커널</td> 
   <td>지원됨</td> 
  </tr> 
  <tr> 
   <td><p>Oracle 데이터베이스 12c 릴리스 1</p> </td> 
   <td><p>저장소 마이크로커널</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>저장소 마이크로커널</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr> 
 </tbody> 
</table>

* MongoDB는 타사 소프트웨어이며 AEM 라이선스 패키지에 포함되어 있지 않습니다. 자세한 내용은 [MongoDB 라이선스 정책](https://www.mongodb.org/about/licensing/) 페이지를 참조하십시오.

* AEM을 최대한 활용하려면 MongoDB Enterprise 버전의 라이센스를 취득하여 전문 지원을 받는 것이 좋습니다.
* Adobe 고객 지원 팀은 AEM에서 MongoDB 사용과 관련된 자격 있는 문제를 지원합니다. 자세한 내용은 [Adobe Experience Manager용 MongoDB 페이지](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)를 참조하십시오.
* &#39;파일 시스템&#39;에는 POSIX 호환 블록 저장소가 포함됩니다. 여기에는 네트워크 스토리지 기술이 포함됩니다. 파일 시스템 성능은 다를 수 있으며 전체 성능에 영향을 줄 수 있습니다. 네트워크/원격 파일 시스템과 함께 테스트 AEM을 로드하는 것이 좋습니다.
* MongoDB 스토리지 엔진 WiredTiger만 지원됩니다.
* MongoDB 공유는 AEM에서 지원되지 않습니다.
* JEE의 AEM Forms은 RDBMK 지속성에 대한 MySQL을 지원하지 않습니다.
* 문서 보안 모듈은 콘텐츠 저장소를 사용하지 않습니다. 즉, 문서 보안만 사용하고 HTML 작업 공간, HTML5 양식 또는 적응형 양식을 사용할 계획이 없는 경우 컨텐츠 저장소를 설치하지 마십시오.
* JEE의 AEM Forms은 Oracle 다중 임차인 아키텍처를 지원합니다.

#### 데이터베이스 지원 {#database-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>플랫폼</strong></p> </td> 
   <td><p><strong> 설명</strong></p> </td> 
   <td><p><strong>지원 수준 AEM 6.4</strong></p> </td> 
   <td><p><strong>JEE에서 지원 수준 AEM Forms 6.4</strong></p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>저장소 마이크로커널</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr> 
  <tr> 
   <td><p>Oracle 데이터베이스 12c 릴리스 1</p> </td> 
   <td><p>저장소 마이크로커널</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5.7.19<br /> </p> </td> 
   <td><p>저장소 마이크로커널</p> </td> 
   <td><p>작동해야 함</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>저장소 마이크로커널</p> </td> 
   <td><p>작동해야 함</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr> 
 </tbody> 
</table>

### 데이터베이스 드라이버 {#database-drivers}

<table> 
 <tbody> 
  <tr> 
   <th>데이터베이스 </th> 
   <th><p><strong>플랫폼</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td>MySQL</td> 
   <td><p>MySQL Connector/J 5.7</p> <p>mysql-connector-java-5.1.30-bin.jar(버전 5.1.30)</p> </td> 
   <td><p>JEE 설치 시 AEM Forms과 함께 제공됨</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Microsoft® SQL Server JDBC 드라이버 6.2.1.0<br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>JEE 설치 시 AEM Forms과 함께 제공됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle</td> 
   <td><p>Oracle 데이터베이스 12.1.0.2.0 JDBC 드라이버</p> <p>ojdbc7.jar(버전 12.1.0.2.0)<br /> </p> </td> 
   <td><p>JEE 설치 시 AEM Forms과 함께 제공됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2</td> 
   <td><p>IBM® DB2 Universal JDBC 드라이버 4.16.53 (db2jcc4.jar)</p> </td> 
   <td><p><a href="https://www-01.ibm.com/support/docview.wss?uid=swg21363866" target="_blank">IBM 웹 사이트</a>에서 드라이버를 다운로드합니다.</p> </td> 
  </tr> 
 </tbody> 
</table>

### 응용 프로그램 서버 {#application-servers}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> 플랫폼</strong></p> </td> 
   <td><p><strong>지원 수준</strong></p> </td> 
   <td><p><strong>지원되는 패치 정의</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle WebLogic Server 12.2.1(12c R2) <sup>[1] [2] [4] [8]</sup></p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>서비스 팩 및 중요 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® WebSphere® Application Server 9.0 <sup>[2] [6]</sup><br /> </td> 
   <td>A:지원됨</td> 
   <td>서비스 팩 및 중요 업데이트</td> 
  </tr> 
  <tr> 
   <td><p>JBoss® EAP(엔터프라이즈 응용 프로그램 플랫폼) 7.0.6 <sup>[1] [4] [5] [7] [8][11]</sup></p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>지원되는 EAP 버전에 대한 패치 및 누적 패치<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>IBM® WebSphere® 클러스터는 Network Deployment Edition에서만 지원됩니다.

### 서버 운영 체제 {#server-operating-systems}

#### 프로덕션 환경 {#production-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong> 플랫폼</strong></p> </th> 
   <th><p><strong>지원 수준</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A:지원됨</td> 
   <td>서비스 팩 및 중요 업데이트</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server 2012 R2 V6.3</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>서비스 팩 및 중요 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle Solaris™ 11 - V5.11<sup> [3] [10]</sup></p> </td> 
   <td><p>L:제한적</p> </td> 
   <td><p>업데이트 및 패치</p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat Enterprise Linux 7(커널 3.x)</br><b>참고:</b> <a href="https://access.redhat.com/articles/4665701">Red Hat Enterprise Linux 6</a>은 유지 관리 종료 단계에 도달하고, 2020년 11월 30일에 확장 수명 주기 지원 단계로 전환합니다. Adobe은 업그레이드 및 새 설치에 Red Hat Enterprise Linux 7을 권장합니다. 기존 설치에서는 Extended Life Cycle Support 단계 동안 Red Hat Enterprise Linux 6을 사용할 수 있습니다.</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>사소한 릴리스, 누적 업데이트 및 중요 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td><p>SUSE® Linux® Enterprise Server 12</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>서비스 팩, 누적 패치 및 중요 보안 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7 업데이트 3</td> 
   <td>A:지원됨</td> 
   <td>서비스 팩, 누적 패치 및 중요 보안 업데이트</td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> [9]</sup></td> 
   <td>A:지원됨</td> 
   <td>서비스 팩, 누적 패치 및 중요 보안 업데이트</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2 [10]</td> 
   <td>A:제한된 지원</td> 
   <td>서비스 팩, 누적 패치 및 중요 보안 업데이트</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>JEE의 AEM Forms은 64비트 운영 체제만 지원합니다.

#### 가상화 환경 {#virtualized-environment}

물리적 컴퓨터 또는 가상 환경에서 JEE에서 AEM Forms을 실행할 수 있습니다. 그러나 가상 환경에서 AEM Forms에 문제가 발생하면 실제 컴퓨터에서 해당 문제를 복제해 보십시오. 실제 컴퓨터에서 문제가 계속 발생하면 Adobe 지원 센터에 문의하여 해결 방법을 확인하십시오. 물리적 시스템에서 복제되지 않는 문제는 가상 환경 공급업체에 문의하십시오.

#### 개발 환경 {#development-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>플랫폼(기본 버전)</strong></p> </th> 
   <th>지원 수준</th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> </td> 
   <td>E:작동해야 함</td> 
   <td><p>서비스 팩 및 중요 업데이트</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* JEE의 AEM Forms은 64비트 운영 체제만 지원합니다.
>* PDF Generator 서비스는 Windows 10에서 지원되지 않습니다.

>



### 지원되는 서버 플랫폼에 대한 예외 {#exceptions-to-supported-server-platforms}

JEE 서버에서 AEM Forms을 설정할 플랫폼을 선택하는 동안 다음 예외를 고려하십시오.

1. JEE의 AEM Forms은 IBM® AIX®에서 Oracle WebLogic 및 JBoss®를 지원하지 않습니다.
1. JEE의 AEM Forms은 MySQL이 포함된 Oracle WebLogic 및 IBM® WebSphere®를 지원하지 않습니다.
1. JEE의 AEM Forms은 인텔® 아키텍처가 있는 Oracle Solaris™을 지원하지 않습니다(SPARC®만 지원됨).
1. JEE의 AEM Forms은 SUSE Linux Enterprise Server 12의 Oracle WebLogic 및 JBoss를 지원하지 않습니다. SUSE Linux Enterprise Server 12에서는 IBM WebSphere만 지원됩니다.
1. JEE의 AEM Forms은 Oracle Java™ SE 이외의 JBoss®를 사용하는 JDK를 지원하지 않습니다.
1. JEE의 AEM Forms은 IBM® JDK 이외의 IBM® WebSphere®를 사용하는 JDK를 지원하지 않습니다.
1. JEE의 AEM Forms은 JBoss®를 사용하는 IBM® DB2를 지원하지 않습니다.
1. CRX 리포지토리는 TarMK, MongoDB 및 관계형 데이터베이스(RDBMK)의 지속성을 지원합니다. 애플리케이션 서버와 CRX 저장소 간에 두 개의 다른 데이터베이스 시스템을 가질 수 없습니다. 그러나 JEE 환경의 AEM Forms에서는 CRX 리포지토리와 함께 MongoMK 및 애플리케이션 서버와 함께 지원되는 관계형 데이터베이스를 사용할 수 있습니다.
1. JEE의 AEM Forms은 CentOS의 WebSphere 애플리케이션 서버를 지원하지 않습니다.
1. AIX 및 Solaris 운영 체제는 업그레이드 고객에게만 제공됩니다.
1. JEE의 AEM Forms은 RBAC(JBoss 역할 기반 액세스 제어)를 지원하지 않습니다.

또한 JEE 배포에서 AEM Forms Adobe 소프트웨어를 선택할 때 다음 사항을 고려하십시오.

* JEE의 AEM Forms은 지원되는 주요 버전 및 부 버전의 소프트웨어 위에 있는 업데이트, 패치 및 수정 팩을 지원합니다. 그러나 다음 주요 버전 또는 부 버전으로 업데이트는 명시하지 않는 한 지원되지 않습니다.
* 클러스터 기반 설치에서는 TarMK 지속성을 지원하지 않습니다. 지원되는 지속성에 대한 자세한 내용은 [AEM Forms 설치에 대한 지속성 유형 선택](/help/forms/using/choosing-persistence-type-for-aem-forms.md)을 참조하십시오.
* JEE의 AEM Forms은 [타사 소프트웨어 지원 정책](#third-party-patch-support-policy)에 따라 다양한 타사 소프트웨어를 지원합니다.
* JEE의 AEM Forms은 타사 공급업체가 제공하는 지원에 따라 플랫폼을 지원합니다. 일부 조합은 타사 공급업체에서 허용하지 않을 수 있습니다. 예를 들어, 많은 공급업체가 IBM® DB2를 사용하여 애플리케이션 서버를 인증하지 않았습니다. 따라서 JEE의 AEM Forms도 이러한 조합을 지원하지 않습니다. 지원되는 소프트웨어 버전을 선택하려면 타사 공급업체의 지원 매트릭스도 확인하십시오.
* JEE의 AEM Forms은 TarMK Cold Standby를 지원하지 않습니다.
* JEE의 AEM Forms은 수직 클러스터링을 지원하지 않습니다.
* JEE의 AEM Forms은 클러스터된 환경에서 MySQL 데이터베이스를 지원하지 않습니다.
* 패키지 JDBC 모듈이 Weblogic에 구성되어 있으면 RDBMK가 DB2, MYSQL, MS SQL 및 Oracle 데이터베이스에서 작동하지 않습니다.

### LDAP 서버(선택 사항) {#ldap-servers-optional}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>제품(기본 버전)</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Oracle UD(Unified Directory) 11g 릴리스 2</td> 
   <td>서비스 팩</td> 
  </tr> 
  <tr> 
   <td>Microsoft Active Directory 2016</td> 
   <td>유지 관리 릴리스 및 수정 팩</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Active Directory 2012</p> </td> 
   <td><p>운영 체제와 함께 제공된 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Active Directory LDS(Lightweight Directory Services) 2012</p> </td> 
   <td><p>운영 체제와 함께 제공된 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td> 
   <td><p>기능 팩 및 임시 수정 사항</p> </td> 
  </tr> 
  <tr> 
   <td>IBM Lotus Domino 8.5.0</td> 
   <td>유지 관리 릴리스 및 수정 팩</td> 
  </tr> 
  <tr> 
   <td>Novell eDirectory 8.8.7</td> 
   <td>제품 업데이트</td> 
  </tr> 
 </tbody> 
</table>

### 전자 메일 서버(선택 사항) {#email-servers-optional}

* IBM Lotus Domino 9.0
* Microsoft Exchange 2013
* Microsoft Office 365

### 컨텐츠 관리자 및 해당 커넥터 {#content-managers-and-corresponding-connectors}

<table> 
 <tbody> 
  <tr> 
   <td><strong>제품<br /> </strong></td> 
   <td><strong>버전</strong></td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager Server</td> 
   <td>8.5 수정 팩 2<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager 클라이언트</td> 
   <td><p>버전 8.5<strong> </strong>이 지원됩니다</p> </td> 
  </tr> 
  <tr> 
   <td>EMC Documentum</td> 
   <td>7.0 및 7.3</td> 
  </tr> 
  <tr> 
   <td>IBM Filenet</td> 
   <td>5.2</td> 
  </tr> 
  <tr> 
   <td>Microsoft Sharepoint</td> 
   <td>2013년 및 2016년<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Cordova {#support-for-cordova} 지원

AEM Forms 앱은 이제 Apache Cordova를 지원합니다. 다음은 지원되는 Cordova 플랫폼별 버전입니다.

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### PDF Generator에 대한 소프트웨어 지원 {#software-support-for-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>제품</strong></p> </th> 
   <th><p><strong>PDF로 변환할 수 있는 지원되는 형식</strong></p> </th> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 클래식 트랙</a></td> 
   <td>XPS, 이미지 형식(BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF 및 DWF</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF 및 TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF 및 TXT</td> 
  </tr> 
  <tr> 
   <td>WordPerfect X7</td> 
   <td>WP, WPD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2013</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2013</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2013</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, SXW, SXW, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, IMAGE 형식(BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JPF, J2K, J2C, RTF, HTML, HTML, RTF, HTML, HTML, HTML, HTML, JTXC, HTML, XC, HTML, RTF 및 TXT</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 3.4</td> 
   <td>ODT, ODP, ODS, ODG, SXW, SXW, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, IMAGE 형식(BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JPF, J2K, J2C, RTF, HTML, HTML, RTF, HTML, HTML, HTML, HTML, JTXC, HTML, XC, HTML, RTF 및 TXT</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator는 지원되는 운영 체제 및 응용 프로그램의 영어, 프랑스어, 독일어 및 일본어 버전만 지원합니다.
>
>또한
>
>* PDF Generator를 사용하려면 전환을 수행하려면 32비트 버전의 [Acrobat 2017 Classic 트랙 버전 17.011.30078 이상](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html)이 필요합니다.
>* PDF Generator는 변환에 필요한 32비트 Retail 버전의 Microsoft Office Professional Plus와 기타 소프트웨어만 지원합니다.
>* PDF Generator는 Microsoft Office 365를 지원하지 않습니다.
>* OpenOffice용 PDF Generator 변환은 Windows, Linux 및 Solaris에서만 지원됩니다.
>* HTML2PDF 서비스는 AIX에서 더 이상 사용되지 않습니다.
>* OCR PDF, Optimize PDF 및 Export PDF 기능은 Windows에서만 지원됩니다.
>* Acrobat 버전은 PDF Generator 기능을 활성화하기 위해 AEM Forms과 번들로 제공됩니다. AEM Forms PDF Generator에서 사용할 수 있도록 번들로 제공되는 버전은 AEM Forms 라이센스 기간 동안 AEM Forms을 통해서만 프로그래밍 방식으로 액세스할 수 있습니다. 자세한 내용은 배포에 대한 AEM Forms 제품 설명([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) 또는 [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;을 참조하십시오

>



### 액세스 가능성 지원 예외 {#exceptions-to-accessibility-support}

AEM Forms의 다음 하위 시스템은 [508](https://www.section508.gov/) 규격이 아닙니다.

* 적응형 Forms 작성 UI
* Forms Manager 작성 UI
* 서신 관리 작성 UI
* 관리 UI(관리 콘솔 UI)

## JEE의 AEM Forms 시스템 요구 사항 {#system-requirements-for-aem-forms-on-jee}

### 최소 하드웨어 요구 사항 {#minimum-hardware-requirements}

<table> 
 <tbody> 
  <tr> 
   <td>플랫폼</td> 
   <td>최소 하드웨어 요구 사항</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server</td> 
   <td>Intel® Xeon® E5-2680, 2.4GHz 프로세서 또는 동급<br /> VMWare ESX 5.1 이상<br /> RAM:6GB(64비트 JVM이 있는 64비트 OS)<br /> 사용 가능한 디스크 공간:15GB의 임시 공간 + JEE의 AEM Forms용 22GB<br /></td> 
  </tr> 
  <tr> 
   <td>Sun Solaris</td> 
   <td>UltraSPARC® IIIi, 1.5GHz 프로세서<br /> Solaris 컨테이너(영역) 분할<br /> RAM:6GB(64비트 JVM이 있는 64비트 OS)<br /> 사용 가능한 디스크 공간:6GB의 임시 공간 + JEE의 AEM Forms용 22GB<br /></td> 
  </tr> 
  <tr> 
   <td>IBM AIX</td> 
   <td>P6 p시리즈 520(모델 52A) 9131-52A, 1.8GHz 프로세서<br /> LPAR 분할<br /> RAM:6GB(64비트 JVM이 있는 64비트 OS)<br /> 사용 가능한 디스크 공간:6GB의 임시 공간 + JEE의 AEM Forms용 22GB<br /></td> 
  </tr> 
  <tr> 
   <td>SUSE Linux Enterprise Server</td> 
   <td>Intel Xeon E5-2670v2, 1vCPU, 2.5GHz 프로세서<br /> AWS m3.medium(3ECU)<br /> RAM:6GB(64비트 JVM이 있는 64비트 OS)<br /> 사용 가능한 디스크 공간:6GB의 임시 공간 + JEE의 AEM Forms용 22GB<br /></td> 
  </tr> 
  <tr> 
   <td>Red Hat Enterprise Linux</td> 
   <td>Intel Xeon E5-2670v2, 1vCPU, 2.5GHz 프로세서<br /> AWS m3.medium(3ECU)<br /> RAM:6GB(64비트 JVM이 있는 64비트 OS)<br /> 사용 가능한 디스크 공간:6GB의 임시 공간 + JEE의 AEM Forms용 22GB<br /><br /> </td> 
  </tr> 
  <tr> 
   <td>소규모 운영 환경을 위한 하드웨어 요구 사항</td> 
   <td> 
    <ul> 
     <li><strong>인텔 기반 환경</strong>:Intel® Xeon® E5-2680, 2.4GHz 이상 듀얼 코어 프로세서를 사용하면 성능이 더욱 향상됩니다</li> 
     <li><strong>Sun SPARC 기반 환경: </strong> UltraSPARC V 이상</li> 
     <li><strong>IBM AIX 기반 환경: </strong> Power6 이상<br /> </li> 
     <li><strong>메모리: </strong>4GB  <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

추가 요구 사항은 다음을 참조하십시오.

* [JEE 배포에서 단일 서버 AEM Forms을 위한 시스템 요구 사항](https://www.adobe.com/go/learn_aemforms_sysreq_single_64)
* [JEE 배포에서 클러스터된 AEM Forms에 대한 시스템 요구 사항](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_64)

## JEE에서 AEM Forms에 대해 지원되는 클라이언트 {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

>[!NOTE]
>
>32비트 및 64비트 운영 체제가 모두 지원됩니다.

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>플랫폼</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> <p>(Enterprise, Pro, Basic)</p> </td> 
   <td>서비스 팩 및 중요 업데이트</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Windows® 2012 Server R2</td> 
   <td>서비스 팩 및 중요 업데이트</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Windows® 2016 Server</td> 
   <td>서비스 팩 및 중요 업데이트</td> 
  </tr> 
 </tbody> 
</table>

* 설치 디스크 공간:Workbench 전용 1.7GB, Workbench, Designer 및 Windows 임시 설치 디렉토리의 경우 샘플 어셈블리 400MB - 사용자 temp 디렉토리에 200MB, Windows 임시 디렉토리에 200MB - 단일 드라이브에 2.7GB

>[!NOTE]
>
>이러한 모든 위치가 단일 드라이브에 있는 경우 설치 중에 1.5GB의 공간이 있어야 합니다. 설치가 완료되면 임시 디렉토리에 복사된 파일이 삭제됩니다.

* Workbench를 실행하는 메모리:2GB RAM
* 하드웨어 요구 사항:Intel® Pentium® 4 또는 AMD 동급 프로세서, 1GHz 프로세서
* 최소 1024 X 768픽셀 이상(16비트 색상 이상) 모니터 해상도
* JEE 서버의 AEM Forms에 대한 TCP/IPv4 또는 TCP/IPv6 네트워크 연결

>[!NOTE]
>
>Windows에 Workbench를 설치하려면 관리 권한이 있어야 합니다. 관리자가 아닌 계정을 사용하여 설치하는 경우 설치 관리자에서 적절한 계정에 대한 자격 증명을 입력하라는 메시지를 표시합니다.

### 디자이너 {#designer}

* Microsoft® Windows® 2012 Server R2, Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10
* PAE, NX 및 SSE2를 지원하는 1GHz 이상의 프로세서
* 64비트 OS용 32비트 또는 2GB RAM의 경우 1GB
* 32비트 또는 64비트 OS용 20GB 디스크 공간의 경우 16GB 디스크 공간
* 그래픽 메모리 - 128MB GPU(256MB 권장)
* 2.35GB의 사용 가능한 하드 디스크 공간
* 1024 X 768픽셀 이상의 모니터 해상도
* 비디오 하드웨어 가속(옵션)
* Acrobat Pro DC, Acrobat Standard DC 또는 Adobe Acrobat Reader DC
* 디자이너를 설치할 관리 권한

### Adobe Acrobat 및 Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Acrobat 및 Adobe Reader(기본)</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Acrobat 2017(클래식 트랙)</td> 
   <td>버전 17.011.30078 이상<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Acrobat DC 제품군에서는 기본적으로 다른 제품인 Acrobat과 Reader 모두에 대한 두 가지 트랙을 소개합니다.&quot;Classic&quot; 및 &quot;Continuous.&quot; 두 트랙에 대한 자세한 내용과 비교는 [https://www.adobe.com/go/acrobatdctracks.](https://www.adobe.com/go/acrobatdctracks)

### 브라우저 {#browsers}

#### 데스크톱 {#desktops}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>브라우저(기본)</strong></p> </th> 
   <th><p><strong>지원 수준</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft Edge</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>서비스 팩 및 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox 4.5.x</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>모든 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome 46+</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>모든 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x</td> 
   <td>A:지원됨</td> 
   <td>모든 업데이트</td> 
  </tr> 
  <tr> 
   <td><p>MAC OS X의 Google Chrome 및 Firefox</p> </td> 
   <td><p>A:지원됨</p> </td> 
   <td><p>모든 업데이트</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>데스크탑에 대한 일부 브라우저 관련 예외는 다음과 같습니다.
>
>* 대부분의 최신 브라우저는 더 이상 NPAPI 기반 플러그인을 지원하지 않습니다. AEM Forms 애플리케이션 및 워크플로우에 영향을 주는 방법에 대한 자세한 내용은 [NPAPI 브라우저 플러그인의 중단 및 그 영향](https://helpx.adobe.com/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html)을 참조하십시오.
>* Safari는 Macintosh OS X에서만 지원됩니다.


#### 모바일 클라이언트 {#mobile-clients}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>브라우저(기본)</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Android™ 4.1.2 이상의 Chrome</p> </td> 
   <td><p>모든 업데이트</p> </td> 
  </tr> 
  <tr> 
   <td>iOS 11.0 이상의 Safari</td> 
   <td>모든 업데이트</td> 
  </tr> 
  <tr> 
   <td>Windows 10의 Internet Explorer</td> 
   <td>모든 업데이트</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge<br /> </td> 
   <td>모든 업데이트<br /> </td> 
  </tr> 
  <tr> 
   <td>Android™ 4.4 이상의 기본 Android 브라우저</td> 
   <td>모든 업데이트</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Forms Portal은 iPad의 Safari에서만 지원됩니다.

>



### AEM Forms 앱 {#aem-forms-workspace-app}

#### 모바일 장치 지원 {#mobile-device-support}

AEM Forms 앱은 다음 플랫폼에서 사용할 수 있습니다.

| **플랫폼** | **지원되는 장치** |
|---|---|
| Apple iOS | iOS 11 이상을 실행하는 Apple iPhone, iPad, iPad Air, iPad mini. |
| Google Android | Android 4.4(Andoird Kit Kat) 및 *[API Level 19 이상]*. AEM Forms 앱은 7, 10인치 삼성 갤럭시 태블릿과 7인치 구글 넥서스, 인기 스마트폰으로 인증됐다. |
| Microsoft Windows | Microsoft Windows 10 운영 체제를 실행하는 Microsoft Surface 장치, 태블릿, 노트북 및 데스크톱 |

### Adobe Flash Player {#adobe-flash-player}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Flash Player(기본)</strong></p> </th> 
   <th><p><strong>지원되는 패치 정의</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>최신 버전 Flash Player</p> </td> 
   <td><p>부 버전 및 업데이트</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Adobe은 [2020년 말에 Flash Player 업데이트 및 배포를 중지합니다](https://theblog.adobe.com/adobe-flash-update/).

### Microsoft Office용 Adobe 문서 보안 확장 {#adobe-rights-management-extension-for-microsoft-office}

Microsoft® Office용 문서 보안 확장 Adobe에 대한 시스템 요구 사항을 보려면 [여기](https://www.adobe.com/products/livecycle/rightsmanagement/extension/downloads.html)를 클릭하십시오.

### 클라이언트 지원 예외 {#exceptions-to-client-support}

Microsoft® Windows® 2012는 Reader 및 Acrobat을 제외하고 지정된 모든 클라이언트 측 소프트웨어에 대해 지원되지 않습니다.

또한, JEE의 AEM Forms은 지원되는 주요 버전 및 부 버전의 소프트웨어 위에 있는 업데이트, 패치 및 수정 팩을 지원합니다. 그러나 다음 주요 버전 또는 부 버전으로 업데이트는 명시하지 않는 한 지원되지 않습니다.

## 타사 패치 지원 정책 {#third-party-patch-support-policy}

JEE의 AEM Forms에 대한 타사 소프트웨어 요구 사항은 해당 제품 문서의 &quot;시스템 요구 사항&quot; 섹션에 설명되어 있습니다. 모든 설명서는 [https://adobe.com/go/learn_aemforms_documentation_64](https://adobe.com/go/learn_aemforms_documentation_64)에서 액세스할 수 있습니다.

JEE의 타사 참조 플랫폼에 있는 AEM Forms은 JEE에서 AEM Forms을 개발 및 릴리스하는 동안 최신 상태인 타사 인프라의 특정 패치 수준과 JEE에서 해당 버전의 AEM Forms에서 지원하는 인프라의 최소 패치/서비스 팩 수준에서 명시합니다.

Adobe은 타사 공급업체가 AEM Forms on JEE에서 지원하는 버전과의 이전 호환성을 보장한다고 가정할 경우, 해당 릴리스 시 타사 공급업체가 발행한 긴급 또는 권장 패치를 지원합니다. Adobe은 JEE 설명서의 AEM Forms에 명시된 최소 패치 수준 이후에 릴리스된 패치만 지원합니다.

경우에 따라 Adobe은 주요 기능을 변경하는 타사 업데이트를 지원하지 않으므로 전체 이전 버전과의 호환성을 지원하지 않습니다. 지원되는 업데이트에 대한 자세한 내용은 특정 공급업체 제품 및 패치 유형 Adobe이 지원하는 경우 [지원되는 패치 정의](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html)를 참조하십시오.

Adobe의 제어 이외의 상황에서 이전 버전과의 호환성을 주장하는 타사 패치는 Adobe 제품이나 고객 환경에 부정적인 영향을 줄 수 있습니다. 이러한 경우, Adobe은 고객이 중요한 시스템에 적용하기 전에 타사에서 제공한 긴급 패치가 미치는 영향을 평가할 것을 권장합니다. Adobe은 일반적인 Adobe 지원 프로그램을 통해 또는 제3자가 패치의 문제를 수정함으로써 이러한 문제를 해결하기 위한 합리적인 비즈니스 노력을 이용하여 타사와 협력합니다. 이는 Adobe에서 지원하는 새로 릴리스된 타사 패치가 공급업체가 설명한 대로 또는 JEE의 AEM Forms에서 작동하는 것을 보장하지 않습니다.

Adobe은 JEE 릴리스에서 AEM Forms이 지원하는 타사 참조 플랫폼 및 지원되는 패치 정의를 지정된 시점에서 변경할 수 있는 권한을 갖습니다.

타사 패치에 대한 추가 정보는 Adobe 엔터프라이즈 지원 사이트에서 제품과 관련된 기술 자료를 검색하여 찾을 수도 있습니다.

[**지원 문의**](https://www.adobe.com/kr/account/sign-in.supportportal.html)
