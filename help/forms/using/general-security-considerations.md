---
title: JEE에서 AEM Forms에 대한 일반 보안 고려 사항
seo-title: General Security Considerations for AEM Forms on JEE
description: JEE 환경에서 AEM Forms 강화 준비 방법을 알아봅니다.
seo-description: Learn how to prepare for hardening your AEM Forms on JEE environment.
uuid: c5f6ffc7-b987-4541-ab60-e97b4ff5b2a4
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 38132225-ecae-4887-8f3d-0b3845059130
role: Admin
exl-id: cde40670-ce9d-4b96-92d3-9e56cb15bdce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 1%

---

# JEE에서 AEM Forms에 대한 일반 보안 고려 사항 {#general-security-considerations-for-aem-forms-on-jee}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

JEE 환경에서 AEM Forms 강화 준비 방법을 알아봅니다.

이 문서에서는 AEM Forms 환경 개선을 준비하는 데 도움이 되는 소개 정보를 제공합니다. 여기에는 JEE의 AEM Forms, 운영 체제, 애플리케이션 서버 및 데이터베이스 보안에 대한 사전 요구 정보가 포함되어 있습니다. 환경을 계속 잠기기 전에 이 정보를 검토하십시오.

## 공급업체 특정 보안 정보 {#vendor-specific-security-information}

이 섹션에는 JEE 솔루션의 AEM Forms에 통합된 운영 체제, 애플리케이션 서버 및 데이터베이스에 대한 보안 관련 정보가 포함되어 있습니다.

이 섹션의 링크를 사용하여 운영 체제, 데이터베이스 및 애플리케이션 서버에 대한 공급업체 특정 보안 정보를 찾을 수 있습니다.

### 운영 체제 보안 정보 {#operating-system-security-information}

운영 체제를 보호할 때 다음 사항을 포함하여 운영 체제 공급업체에서 설명하는 조치를 신중하게 구현하십시오.

* 사용자, 역할 및 권한 정의 및 제어
* 로그 및 감사 추적 모니터링
* 불필요한 서비스 및 응용 프로그램 제거
* 파일 백업

JEE에서 AEM Forms이 지원하는 운영 체제에 대한 보안 정보는 표의 리소스를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th><p>운영 체제</p> </th> 
   <th><p>보안 리소스</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM® AIX® 7.2</p> </td> 
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">IBM AIX 보안 이점</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server® 2012 </p> </td> 
   <td><p><a href="https://blogs.technet.com/b/secguide/archive/2014/08/13/security-baselines-for-windows-8-1-windows-server-2012-r2-and-internet-explorer-11-final.aspx" target="_blank">Windows Server 2012 보안 안내서</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server® 2016 </p> </td> 
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Windows Server 2016 보안 안내서</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® Linux® AP 또는 ES</p> </td> 
   <td><p><a href="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/pdf/security_guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf" target="_blank">Red Hat Enterprise Linux 보안 안내서</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Sun Solaris 11</p> </td> 
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">보안 및 강화 지침</a></p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7 업데이트 3</td> 
   <td><a href="https://docs.oracle.com/cd/E52668_01/E54670/E54670.pdf" target="_blank">릴리스 7에 대한 보안 안내서</a><br /> </td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> </sup></td> 
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">보호 설명서</a></td> 
  </tr> 
 </tbody> 
</table>

### 애플리케이션 서버 보안 정보 {#application-server-security-information}

애플리케이션 서버를 보호할 때 서버 공급업체에서 설명하는 다음 사항을 포함한 측정 방법을 신중하게 구현하십시오.

* 명확하지 않은 관리자 사용자 이름 사용
* 불필요한 서비스를 사용하지 않도록 설정
* 콘솔 관리자 보안
* 보안 쿠키 활성화
* 불필요한 포트를 닫는 중
* IP 주소 또는 도메인으로 클라이언트 제한
* Java™ Security Manager를 사용하여 프로그래밍 방식으로 권한 제한

JEE에서 AEM Forms이 지원하는 애플리케이션 서버에 대한 보안 정보는 이 표의 리소스를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th><p>응용 프로그램 서버</p> </th> 
   <th><p>보안 리소스</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Oracle WebLogic®</p> </td> 
   <td><p>에서 WebLogic Security 이해 검색 <a href="https://download.oracle.com/docs/">https://download.oracle.com/docs/</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM WebSphere®</p> </td> 
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">애플리케이션 및 환경 보호</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® JBoss®</p> </td> 
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security+subsystem+configuration">보안 하위 시스템 구성</a></p> </td> 
  </tr> 
 </tbody> 
</table>

### 데이터베이스 보안 정보 {#database-security-information}

데이터베이스 보안을 설정할 때 다음을 포함하여 데이터베이스 공급업체에서 설명하는 측정 방법을 구현해 보십시오.

* ACL(액세스 제어 목록)을 사용하여 작업 제한
* 비표준 포트 사용
* 방화벽 뒤에 데이터베이스 숨기기
* 데이터베이스에 기록하기 전에 중요한 데이터를 암호화합니다(데이터베이스 제조업체의 설명서 참조)

JEE에서 AEM Forms이 지원하는 데이터베이스에 대한 보안 정보는 이 표의 리소스를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th><p>데이터베이스</p> </th> 
   <th><p>보안 리소스</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM DB2® 11.1</p> </td> 
   <td><p><a href="https://www-01.ibm.com/software/data/db2/library/">DB2 제품군 라이브러리</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td>웹에서 "SQL Server 2016: 보안"</td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5</p> </td> 
   <td><p><a href="https://dev.mysql.com/doc/refman/5.0/en/security.html">MySQL 5.0 일반 보안 문제</a></p> <p><a href="https://dev.mysql.com/doc/refman/5.1/en/security.html">MySQL 5.1 일반 보안 문제</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle® 12c</p> </td> 
   <td><p>의 보안 장을 참조하십시오. <a href="https://docs.oracle.com/database/121/TDPSG/GUID-6E2F4E53-5D87-4FCD-9C9C-6792217D7014.htm#TDPSG94426" target="_blank">Oracle 12g 설명서</a></p> </td> 
  </tr> 
 </tbody> 
</table>

이 표에서는 JEE에서 AEM Forms 구성 프로세스 중에 열어야 하는 기본 포트를 설명합니다. https를 통해 연결하는 경우 포트 정보와 IP 주소를 적절하게 조정합니다. 포트 구성에 대한 자세한 내용은 *JEE에 AEM Forms 설치 및 배포* 애플리케이션 서버에 대한 문서입니다.

<table> 
 <thead> 
  <tr> 
   <th><p>제품 또는 서비스</p> </th> 
   <th><p>포트 번호</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>JBoss</p> </td> 
   <td><p>8080</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic 관리 서버</p> </td> 
   <td><p>구성 중에 관리자가 설정</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebSphere</p> </td> 
   <td><p>9060에서 전역 보안이 활성화되어 있으면 기본 SSL 포트 값은 9043입니다.</p> <p>9080</p> </td> 
  </tr> 
  <tr> 
   <td><p>BAM 서버</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td><p>8880</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL</p> </td> 
   <td><p>3306</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle</p> </td> 
   <td><p>1521</p> </td> 
  </tr> 
  <tr> 
   <td><p>DB2</p> </td> 
   <td><p>50000</p> </td> 
  </tr> 
  <tr> 
   <td><p>SQL Server</p> </td> 
   <td><p>1433</p> </td> 
  </tr> 
  <tr> 
   <td><p>LDAP</p> </td> 
   <td><p>LDAP 서버가 실행 중인 포트입니다. 기본 포트는 일반적으로 389입니다. 그러나 SSL 옵션을 선택하면 기본 포트는 일반적으로 636입니다. 지정할 포트를 LDAP 관리자에게 확인합니다.</p> </td> 
  </tr> 
 </tbody> 
</table>

### 기본이 아닌 HTTP 포트를 사용하도록 JBoss 구성 {#configuring-jboss-to-use-a-non-default-http-port}

JBoss Application Server는 기본 HTTP 포트로 8080을 사용합니다. 또한 JBoss에는 jboss-service.xml 파일에 주석 처리된 사전 구성된 포트 8180, 8280 및 8380도 있습니다. 컴퓨터에 이미 이 포트를 사용하는 애플리케이션이 있는 경우 다음 단계에 따라 JEE에서 AEM Forms이 사용하는 포트를 변경합니다.

1. 편집할 다음 파일을 엽니다.

   단일 서버 설치: [JBoss 루트]/standalone/configuration/standalone.xml

   클러스터 설치: [JBoss 루트]/domain/configuration/domain.xml

1. 값 변경 **포트** 의 속성 **&lt;socket-binding>** 태그로 지정합니다. 예를 들어, 다음은 포트 8090을 사용합니다.

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot;/>

1. 파일을 저장하고 닫습니다.
1. JBoss 애플리케이션 서버를 다시 시작합니다.

## JEE의 AEM Forms 보안 고려 사항 {#aem-forms-on-jee-security-considerations}

이 섹션에서는 사용자가 알고 있어야 하는 JEE 관련 보안 문제에 대한 일부 AEM Forms에 대해 설명합니다.

### 데이터베이스에서 전자 메일 자격 증명이 암호화되지 않음 {#email-credentials-not-encrypted-in-database}

애플리케이션이 저장하는 이메일 자격 증명은 JEE 데이터베이스의 AEM Forms에 저장되기 전에 암호화되지 않습니다. 전자 메일을 사용하도록 서비스 종단점을 구성할 때 해당 종단점 구성의 일부로 사용되는 모든 암호 정보는 데이터베이스에 저장될 때 암호화되지 않습니다.

### 데이터베이스의 Rights Management에 대한 중요한 콘텐츠 {#sensitive-content-for-rights-management-in-the-database}

AEM Forms on JEE는 JEE 데이터베이스의 AEM Forms을 사용하여 정책 문서에 사용되는 중요한 문서 키 정보와 기타 암호화 자료를 저장합니다. 침입으로부터 데이터베이스를 보호하는 것은 이러한 중요한 정보를 보호하는 데 도움이 됩니다.

### 일반 텍스트 양식의 암호 {#password-in-clear-text-format-in-adobe-ds-xml}

JEE에서 AEM Forms을 실행하는 데 사용되는 애플리케이션 서버에는 애플리케이션 서버에 구성된 데이터 소스를 통해 데이터베이스에 액세스할 수 있는 자체 구성이 필요합니다. 응용 프로그램 서버가 해당 데이터 소스 구성 파일의 일반 텍스트로 데이터베이스 암호를 표시하지 않는지 확인합니다.

lc_[데이터베이스].xml 파일에는 암호를 일반 텍스트 형식으로 포함할 수 없습니다. 애플리케이션 서버의 이러한 암호를 암호화하는 방법은 애플리케이션 서버 공급업체에 문의하십시오.

>[!NOTE]
>
>JEE JBoss 턴키 설치 프로그램의 AEM Forms은 데이터베이스 암호를 암호화합니다.

IBM WebSphere Application Server 및 WebLogic Server는 기본적으로 데이터 소스 암호를 암호화할 수 있습니다. 그러나 애플리케이션 서버 설명서에서 이 문제가 발생하는지 확인합니다.

### Trust Store에 저장된 개인 키 보호 {#protecting-the-private-key-stored-in-trust-store}

Trust Store에 가져온 개인 키 또는 자격 증명은 JEE 데이터베이스의 AEM Forms에 저장됩니다. 데이터베이스를 안전하게 보호하고 지정된 관리자에게만 액세스를 제한하는 데 적절한 조치를 취하십시오.
