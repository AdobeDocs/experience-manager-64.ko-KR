---
title: 기술 요구 사항
seo-title: Technical Requirements
description: AEM에 대해 지원되는 클라이언트 및 서버 플랫폼 목록입니다.
seo-description: A list of the supported client and server platforms for AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
exl-id: 21c10b39-ca37-4085-86f8-063c30a180ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3294'
ht-degree: 1%

---

# 기술 요구 사항{#technical-requirements}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe은 이 문서의 다음 정보에 자세히 설명된 대로 플랫폼에서 Adobe Experience Manager(AEM)을 지원합니다.

플랫폼 자체와 특별히 관련된 문제는 플랫폼 공급업체에 직접 문의하십시오.

>[!NOTE]
>
>AEM을 설치하는 플랫폼에 따라 사용자 관리를 위한 다양한 요구 사항 세트가 있을 수 있습니다.

## 사전 요구 사항 {#prerequisites}

Adobe Experience Manager 설치를 위한 최소 요구 사항:

* 설치된 Java Platform, Standard Edition JDK 또는 기타 지원 [Java 가상 컴퓨터](#java-virtual-machines)
* Experience Manager 빠른 시작 파일(독립 실행형 JAR 또는 웹 애플리케이션 배포 WAR)

### 최소 크기 조정 요구 사항 {#minimum-sizing-requirements}

Adobe Experience Manager 실행을 위한 최소 요구 사항:

* 설치 디렉터리에서 5GB의 사용 가능한 디스크 공간
* 2GB 메모리

>[!NOTE]
>
>* 디지털 자산 사용 사례에는 더 많은 기본 메모리가 필요합니다. 자세한 내용은 [배포 및 유지 관리](/help/sites-deploying/deploy.md#default-local-install) 자세한 내용
>* [AEM Forms 추가 기능 패키지](/help/forms/using/installing-configuring-aem-forms-osgi.md) 15GB의 임시 공간이 필요합니다.
>


자세한 내용은 [하드웨어 크기 조정 지침](/help/managing/hardware-sizing-guidelines.md) 추가 정보.

### 지원 수준 {#support-levels}

이 문서에서는 Adobe Experience Manager에 대해 지원되는 클라이언트 및 서버 플랫폼을 나열합니다. Adobe은 권장 구성 및 기타 구성을 위해 몇 가지 수준의 지원을 제공합니다.

### 지원되는 구성 {#supported-configurations}

Adobe은 이러한 구성을 권장하며 표준 소프트웨어 유지 관리 계약의 일부로 전체 지원을 제공합니다.

<table> 
 <tbody> 
  <tr> 
   <td>지원 수준</td> 
   <td>설명<br />을 따르지 않는 경우입니다 </td> 
  </tr> 
  <tr> 
   <td><strong>A: 지원됨</strong></td> 
   <td>Adobe은 이 구성에 대한 모든 지원 및 유지 관리를 제공합니다. 이 구성은 Adobe의 품질 보증 프로세스에서 다룹니다.</td> 
  </tr> 
  <tr> 
   <td><strong>R: 제한된 지원</strong></td> 
   <td>고객이 프로젝트를 성공적으로 수행할 수 있도록 하기 위해 Adobe은 제한된 지원 프로그램 내에서 특정 조건을 충족해야 합니다. R 수준 지원은 공식 고객 요청과 Adobe 확인을 필요로 합니다. 자세한 내용은 Adobe 고객 지원 센터에 문의하십시오.</td> 
  </tr> 
 </tbody> 
</table>

### 지원되지 않는 구성 {#unsupported-configurations}

| 지원 수준 | 설명 |
|---|---|
| **Z: 지원되지 않음** | 구성이 지원되지 않습니다. Adobe은 구성 작동 여부에 대한 설명을 만들지 않으며 구성을 지원하지 않습니다. |

## 지원되는 플랫폼 {#supported-platforms}

### Java 가상 컴퓨터 {#java-virtual-machines}

이 응용 프로그램을 사용하려면 JDK(Java Development Kit) 배포에서 제공하는 Java Virtual Machine을 실행해야 합니다.

Adobe Experience Manager은 다음 버전의 Java Virtual Machine을 사용하여 작동합니다.

>[!CAUTION]
>
>프로덕션 환경의 안전과 보안을 보장하고 최신 Java 업데이트를 설치하려면 Java 공급업체의 보안 게시판을 추적하는 것이 좋습니다.

<table> 
 <tbody> 
  <tr> 
   <td>Platform</td> 
   <td>지원 수준<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z: 지원되지 않음 </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z: 지원되지 않음 </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z: 지원되지 않음</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK - 64비트</strong></td> 
   <td>A: 지원되는 [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - 빌드 2.9, JRE 1.8.0 [2]</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - 빌드 2.8, JRE 1.8.0 [2]</td> 
   <td>A: 지원됨</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle이 Oracle Java SE 제품에 대한 &quot;장기 지원&quot;(LTS) 모델로 이동되었습니다. Java 9 및 10은 Oracle에 의한 비 LTS 릴리스입니다(참조) [Oracle Java SE 지원 로드맵](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe은 프로덕션에서 AEM을 실행할 Java의 LTS 릴리스만 지원합니다.

1. IBM JRE는 WebSphere Application Server와 함께 만 지원됩니다.
1. 공개 업데이트 종료 이후 LTS 릴리스의 모든 유지 관리 업데이트를 포함하여 Oracle Java SE JDK의 지원 및 배포는 Oracle Java SE 기술을 사용하는 모든 AEM 고객을 위해 Adobe에서 직접 지원합니다. 자세한 내용은 [Adobe Experience Manager Q&amp;A에 대한 Java oracle 지원](assets/adobe-oracle-java-license-agreement.pdf) 추가 정보.

### 스토리지 및 지속성 {#storage-persistence}

Adobe Experience Manager 리포지토리를 배포하는 다양한 옵션이 있습니다. 지원되는 기술 및 스토리지 옵션에 대해서는 다음 목록을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Platform</strong></td> 
   <td><strong>설명</strong></td> 
   <td><strong>지원 수준</strong></td> 
  </tr> 
  <tr> 
   <td><strong>TAR 파일이 있는 파일 시스템 [1]</strong></td> 
   <td>저장소</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td><strong>데이터 저장소 [1]이(가) 있는 파일 시스템</strong></td> 
   <td>바이너리</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>파일 시스템 [1]에서 TAR 파일에 바이너리 저장</td> 
   <td>바이너리</td> 
   <td>Z: 프로덕션에서 지원되지 않음</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>바이너리</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob 저장소</td> 
   <td>바이너리</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>저장소</td> 
   <td>A: 제한 사항 지원</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>저장소</td> 
   <td>A: 제한 사항 지원</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Forms 데이터베이스</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Forms 데이터베이스</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>저장소 및 Forms 데이터베이스</td> 
   <td>R: 제한된 지원(4)</td> 
  </tr> 
  <tr> 
   <td>Oracle 데이터베이스 12c(12.1.x)</td> 
   <td>저장소 및 Forms 데이터베이스</td> 
   <td>R: 제한된 지원</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Forms 데이터베이스</td> 
   <td>Z: 지원되지 않음(4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Forms 데이터베이스</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Forms 데이터베이스</td> 
   <td>R: 제한된 지원(4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene(Quickstart 기본 제공)</strong></td> 
   <td>검색 서비스</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Apache 솔루션</td> 
   <td>검색 서비스</td> 
   <td>A: 지원됨</td> 
  </tr> 
 </tbody> 
</table>

1. &#39;파일 시스템&#39;에는 POSIX 호환 블록 저장소가 포함됩니다. 여기에는 네트워크 스토리지 기술이 포함됩니다. 파일 시스템 성능은 다를 수 있으며 전체 성능에 영향을 줄 수 있습니다. 네트워크/원격 파일 시스템과 함께 테스트 AEM을 로드하는 것이 좋습니다.
1. MongoDB 공유는 AEM에서 지원되지 않습니다.
1. MongoDB Storage Engine WiredTiger만 지원됩니다.
1. AEM Forms에서는 지원되지 않습니다.
1. MongoDB Enterprise 3.6은 AEM 버전 6.4.2.0부터 지원됩니다.
1. MongoDB 3.4에 대한 지원이 EOL(End of Life)에 도달했으며 MongoDB 3.6은 2021년 4월 30일에 EOL에 도달할 예정입니다. Adobe은 앞으로 AEM 제품 관련 문제에 대한 지원만 제공할 예정입니다.

>[!NOTE]
>
>자세한 내용은 [커뮤니티 배포](/help/communities/deploy-communities.md) AEM Communities 기능에 대한 추가 정보입니다.

>[!NOTE]
>
>MongoDB는 타사 소프트웨어이며 AEM 라이선스 패키지에 포함되어 있지 않습니다. 자세한 내용은 [MongoDB 라이선스 정책](https://www.mongodb.org/about/licensing/) 페이지.
>
>MongoDB를 통해 AEM 배포를 최대한 활용하려면 MongoDB Enterprise 버전의 라이센스를 취득하여 전문적인 지원을 받을 것을 권장합니다. 자세한 내용은 [권장 배포](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) 추가 정보.
>
>라이센스에는 작성자나 게시 배포에 사용할 수 있는 하나의 기본 인스턴스와 두 개의 보조 인스턴스로 구성된 표준 복제 세트가 포함되어 있습니다.
>
>MongoDB에서 작성자와 게시를 모두 실행하려면 두 개의 별도 라이센스를 구입해야 합니다.
>
>Adobe 고객 지원 팀은 AEM에서 MongoDB 사용과 관련된 자격 있는 문제를 지원합니다.
>
>자세한 내용은 [Adobe Experience Manager용 MongoDB 페이지](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>위에 나열된 지원되는 관계형 데이터베이스는 타사 소프트웨어이며 AEM 라이선스 패키지에 포함되어 있지 않습니다.
>
>지원되는 관계형 데이터베이스로 AEM 6.4를 실행하려면 데이터베이스 공급업체와의 별도의 지원 계약이 필요합니다. Adobe 고객 지원 팀은 AEM 6.4에서 관계형 데이터베이스 사용과 관련된 자격 있는 문제를 지원합니다.
>
>**대부분의 관계형 데이터베이스는 현재 AEM 6.4의 Level-R 내에서 지원되며, 위의 Level-R 설명에 나와 있는 지원 기준 및 지원 프로그램과 함께 제공됩니다.**

### 서블릿 엔진/애플리케이션 서버 {#servlet-engines-application-servers}

Adobe Experience Manager은 독립형 서버(quickstart JAR 파일)나 타사 애플리케이션 서버(WAR 파일)에서 웹 애플리케이션으로 실행할 수 있습니다.

필요한 최소 서블릿 API 버전은 서블릿 3.1이지만 서블릿 4.0 이하입니다.

| Platform | 지원 수준 |
|---|---|
| **빠른 시작 내장 서블릿 엔진(Jetty 9.3)** | A: 지원됨 |
| Oracle WebLogic Server 12.2(12cR2) | A: 지원됨 |
| IBM WebSphere Application Server Continuous Delivery(LibertyProfile)(웹 프로필 7.0 및 IBM JRE 1.8 포함) | A: 지원됨 |
| IBM WebSphere Application Server 9.0 | A: 지원됨 |
| Apache Tomcat 8.5.x | A: 지원됨 |
| JBoss 애플리케이션 서버를 포함하는 JBoss EAP 7.1.0 | A: 지원(1) |
| JBoss Application Server를 사용하는 JBoss EAP 7.0.0 | A: 지원됨 |

1. AEM Forms에서는 지원되지 않습니다.

### 서버 운영 체제 {#server-operating-systems}

Adobe Experience Manager은 다음 서버 플랫폼에서 작동합니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Platform</strong></td> 
   <td><strong>지원 수준</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Red Hat 배포 기반 Linux</strong></td> 
   <td>A: 지원(1)</td> 
  </tr> 
  <tr> 
   <td>Debian 배포 incl 기반 Linux. 우분투</td> 
   <td>A: 지원됨 (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, SUSE 배포 기반</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>A: 제한 사항 지원(3,5,7)<br /> R: 신규 계약에 대한 제한된 지원</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>A: 제한 사항 지원(2,5,7)<br /> R: 신규 계약에 대한 제한된 지원</td> 
  </tr> 
 </tbody> 
</table>

1. Linux Kernel 2.6, 3.x 및 4.x에는 Red Hat Enterprise Linux, CentOS, Oracle Linux 및 Amazon Linux를 포함한 Red Hat 배포의 파생물이 포함되어 있습니다. AEM Forms 추가 기능 기능은 CentOS 7 및 Red Hat Enterprise Linux 7에서만 지원됩니다.
1. AEM Assets: 섹션을 참조하십시오 [XMP 메타데이터 쓰기 되돌리기 지원](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets: Dynamic Media 이미징은 지원되지 않습니다. Dynamic Media 비디오가 지원됩니다.
1. AEM Forms은 Ubuntu 16.04 LTS에서만 지원됩니다.
1. AEM Assets: 에 대한 지원 없음 [원시 파일 변환](/help/assets/camera-raw.md)
1. AEM Forms: 프로덕션 환경에 대한 지원 없음
1. AEM Assets: 에 대한 지원 없음 [향상된 PDF 래스터라이저](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms: 지원되지 않음

### 가상 및 클라우드 컴퓨팅 환경 {#virtual-cloud-computing-environments}

Adobe Experience Manager은 이 페이지에 나열된 기술 요구 사항 및 Adobe의 표준 지원 약관에 따라 Microsoft Azure 및 Amazon Web Services(AWS)과 같은 클라우드 컴퓨팅 환경의 가상 컴퓨터에서 실행되는 것을 지원합니다.

Adobe은 Adobe Managed Services를 사용하여 Azure 또는 AWS에 AEM을 배포할 것을 권장합니다. Adobe Managed Services는 이러한 클라우드 컴퓨팅 환경에서 AEM을 배포하고 운영하는 경험과 기술을 전문가에게 제공합니다. 저희를 확인하십시오 [Adobe Managed Services에 대한 추가 설명서](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

Azure 또는 AWS에 AEM을 배포하거나 기타 모든 클라우드 컴퓨팅 환경에서 배포하는 다른 모든 경우에는 이 페이지에 나열된 기술 사양을 준수하는 Adobe의 지원이 가상 컴퓨팅 환경에 포함됩니다. 이러한 클라우드 환경에서 실행되는 AEM과 관련하여 보고된 모든 문제는 클라우드 서비스가 이 페이지에 나열된 기술 요구 사항(예: Azure Blob 저장 공간 또는 AWS S3)의 일부로 특별히 지원되지 않는 한 클라우드 컴퓨팅 환경과 관련된 모든 클라우드 서비스와 독립적으로 재현할 수 있어야 합니다.

Adobe Managed Services의 외부에서 Azure 또는 AWS에 AEM을 배포하는 방법에 대한 권장 사항을 제공하려면 원하는 클라우드 환경에서 AEM을 배포하도록 지원하는 클라우드 제공업체 또는 Adobe 파트너와 직접 작업하는 것이 좋습니다. 선택한 클라우드 제공업체 또는 파트너는 특정 성능, 로드, 확장성 및 보안 요구 사항을 충족하기 위해 아키텍처의 크기 조정 사양, 디자인 및 구현을 담당합니다.

### Dispatcher 플랫폼(웹 서버) {#dispatcher-platforms-web-servers}

Dispatcher는 캐싱 및 로드 밸런싱 구성 요소입니다. [최신 Dispatcher 버전을 다운로드합니다](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Experience Manager 6.4를 사용하려면 Dispatcher 버전 4.3.1 이상이 필요합니다.

다음 웹 서버는 Dispatcher 버전 4.3.1에서 사용할 수 있습니다.

| Platform | 지원 수준 |
|---|---|
| **Apache httpd 2.4.x** ( 아래 1,2 참조 ) | A: 지원됨 |
| Microsoft IIS 10(인터넷 정보 서버) | A: 지원됨 |
| Microsoft IIS 8.5(인터넷 정보 서버) | A: 지원됨 |

1. Apache httpd 소스 코드를 기반으로 구축된 웹 서버는 httpd가 기반으로 하는 버전과 동일한 지원 수준을 갖게 됩니다. 확실하지 않은 경우 Adobe에게 각 서버 제품과 관련된 지원 수준을 확인하도록 요청하십시오. 다음과 같은 경우:

   1. HTTP 서버는 공식 Apache 소스 배포만 사용하여 구축되었습니다. 또는
   1. HTTP 서버가 실행 중인 운영 체제의 일부로 전달되었습니다. 예: IBM HTTP Server, Oracle HTTP Server

1. Windows 운영 체제용 Apache 2.4.x에는 Dispatcher를 사용할 수 없습니다.

## 지원되는 클라이언트 플랫폼 {#supported-client-platforms}

### 사용자 인터페이스 작성을 위해 지원되는 브라우저 {#supported-browsers-for-authoring-user-interface}

Adobe Experience Manager 사용자 인터페이스는 다음 클라이언트 플랫폼에서 작동합니다. 모든 브라우저는 기본 플러그인 및 추가 기능으로 테스트됩니다.

AEM 사용자 인터페이스는 더 큰 화면(일반적으로 노트북 및 데스크탑 컴퓨터) 및 태블릿 폼 팩터(예: Apple iPad 또는 Microsoft Surface)에 맞게 최적화되어 있습니다. 휴대폰 폼 팩터는 지원되지 않습니다.

>[!NOTE]
>
>**릴리스 주기가 빠른 브라우저 지원:**
>
>Mozilla Firefox, Google Chrome 및 Microsoft Edge 릴리스는 몇 개월마다 업데이트됩니다. Adobe은 향후 출시될 버전의 이러한 브라우저에서 아래에 명시된 지원 수준을 유지하기 위해 Adobe Experience Manager에 대한 업데이트를 제공하기 위해 노력하고 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>브라우저</strong></td> 
   <td><strong>UI 지원<br /> </strong></td> 
   <td><strong>클래식 UI 지원</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome(Evergreen)</strong></td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge(에버그린)</td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox(Evergreen)</td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox 마지막 ESR [1]</td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>macOS의 Apple Safari 12.x</td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>macOS의 Apple Safari 11.x</td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>macOS의 Apple Safari 10.x</td> 
   <td>A: 지원됨</td> 
   <td>A: 지원됨</td> 
  </tr> 
  <tr> 
   <td>iOS 12.x의 Apple Safari</td> 
   <td>A: 지원되는 [2]</td> 
   <td>Z: 지원되지 않음</td> 
  </tr> 
  <tr> 
   <td>iOS 11.x의 Apple Safari</td> 
   <td>A: 지원되는 [2]</td> 
   <td>Z: 지원되지 않음</td> 
  </tr> 
  <tr> 
   <td>iOS 10.3의 Apple Safari</td> 
   <td>A: 지원되는 [2]</td> 
   <td>Z: 지원되지 않음</td> 
  </tr> 
 </tbody> 
</table>

1. Firefox의 확장 지원 릴리스 [mozilla.org에서 이에 대해 자세히 알아보십시오](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. Apple iPad 지원

### 웹 사이트에 대해 지원되는 브라우저 {#supported-browsers-for-websites}

일반적으로 AEM Sites에서 렌더링하는 웹 사이트에 대한 브라우저 지원은 AEM 페이지 템플릿 구현, 디자인 및 구성 요소 출력에 따라 다르므로 이러한 부분을 구현하는 당사자가 제어합니다.

### WebDAV 클라이언트 {#webdav-clients}

**Microsoft Windows 7+**

Microsoft Windows 7+와 SSL을 사용하여 보안이 설정되지 않은 AEM 인스턴스에 연결하려면 Windows에서 비보안 네트워크에 대한 기본 인증을 사용하도록 설정해야 합니다. WebClient의 Windows 레지스트리를 변경해야 합니다.

1. 레지스트리 하위 키를 찾습니다.

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. 2 이상의 값을 사용하여 이 하위 키에 BasicAuthLevel 레지스트리 항목을 추가합니다.

자세한 내용은 [Microsoft 지원 KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

Windows에서 WebDav 클라이언트의 책임을 개선하려면 다음을 참조하십시오. [Microsoft 지원 KB 2445570](https://support.microsoft.com/kb/2445570)

## 추가 플랫폼 정보 {#additional-platform-notes}

이 섹션에서는 Adobe Experience Manager 및 해당 추가 기능 실행에 대한 특수 노트 및 자세한 정보를 제공합니다.

### IPv4 및 IPv6 {#ipv-and-ipv}

Adobe Experience Manager(인스턴스, Dispatcher)의 모든 요소는 IPv4 및 IPv6 네트워크 모두에 설치할 수 있습니다.

별도의 구성이 필요 없으므로 작업이 원활하게 수행됩니다. 필요한 경우 네트워크 유형에 적합한 형식을 사용하여 IP 주소를 지정할 수 있습니다.

즉, IP 주소를 지정해야 할 경우에는 다음 중에서 선택할 수 있습니다.

* ipV6 주소

   예 `https://[ab12::34c5:6d7:8e90:1234]:4502`

* IPv4 주소

   예 `https://123.1.1.4:4502`

* 서버 이름

   예, `https://www.yourserver.com:4502`

* 기본 사례 `localhost` 은 IPv4 및 IPv6 네트워크 설치에 대해 해석됩니다

   예, `http://localhost:4502`

### AEM Dynamic Media 추가 기능 요구 사항 {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media은 기본적으로 비활성화됩니다. 자세한 내용은 [Dynamic Media 활성화](/help/assets/config-dynamic.md#enabling-dynamic-media).

Dynamic Media이 활성화되면 다음과 같은 추가 시스템 요구 사항이 적용됩니다.
>[!NOTE]
>
>다음 시스템 요구 사항이 적용됩니다 **_전용_** Dynamic Media - 하이브리드 모드를 사용하는 경우; Dynamic Media - 하이브리드 모드에서는 특정 운영 체제에서만 인증되는 내장 이미지 서버가 있습니다.
>
>Dynamic Media - Scene7 모드(즉, **dynamic media_scene7** runmode)를 사용할 경우 추가적인 시스템 요구 사항이 없습니다. AEM과 동일한 시스템 요구 사항만 해당됩니다. Dynamic Media - Scene7 모드 아키텍처는 AEM에 포함된 서비스가 아니라 클라우드 기반 이미지 서비스를 사용합니다.

#### 하드웨어 {#hardware}

다음 하드웨어 요구 사항은 Linux 및 Windows 운영 체제 모두에 적용됩니다.

* 4개 이상의 코어가 있는 Intel Xeon 또는 AMD Opteron CPU
* 최소 16GB RAM

#### Linux {#linux}

Linux에서 Dynamic Media을 사용하려면 다음 전제 조건이 필요합니다.

* RedHat Enterprise 7 또는 CentOS 7 이상(최신 수정 패치 포함)
* 64비트 운영 체제
* 사용 안 함 교환(권장)
* SELinux가 비활성화됨(다음 참고 참조)

>[!NOTE]
>
>LC_CTYPE이 en_US.UTF-8과 같지 않도록 로케일을 설정하면 다이내믹 미디어가 작동하지 않습니다. 해당 값이 무엇인지 확인하려면 명령 프롬프트에서 &quot;locale&quot;을 입력합니다. 설정되지 않은 경우 AEM을 실행하기 전에 &quot;export LC_CTYPE=&quot;를 입력하여 LC_CTYPE 환경 변수를 빈 문자열로 설정하십시오.

>[!NOTE]
>
>**SELinux 비활성화:** 이미지 제공이 SELinux를 켜면 작동하지 않습니다. 이 옵션은 기본적으로 활성화되어 있습니다. 이 문제를 해결하려면 **/etc/selinux/config** 파일 및 SELinux 값을 다음으로 변경합니다.
>
>`SELINUX=enforcing` 끝  `SELINUX=disabled`

>[!NOTE]
>
>**NUMA 아키텍처:** AMD64 및 Intel EM64T을 지원하는 프로세서가 있는 시스템은 일반적으로 NUMA(Non-Uniform Memory Architecture) 플랫폼으로 구성되며, 이는 커널이 단일 메모리 노드를 구성하는 대신 부팅 시 여러 메모리 노드를 구성함을 의미합니다.
>
>다중 노드 구문은 다른 노드가 소진되기 전에 하나 이상의 노드에서 메모리 소진을 일으킬 수 있습니다. 메모리 소모가 발생하면 커널에서 사용 가능한 메모리가 있더라도 프로세스(예: 이미지 서버 또는 플랫폼 서버)를 종료하도록 결정할 수 있습니다.
>
>따라서 Adobe은 이러한 시스템을 실행하는 경우 NUMA를 사용하여 끌 것을 권장합니다 **numa=off** 커널에서 이러한 프로세스를 종료하지 않도록 부팅 옵션을 사용합니다.

>[!NOTE]
>
>**서버의 호스트 이름은 확인할 수 있어야 합니다.** 서버의 호스트 이름이 IP 주소로 확인될 수 있는지 확인하십시오. 불가능한 경우 정규화된 호스트 이름과 IP 주소를 **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* 공간을 실제 메모리(RAM)의 두 배 이상으로 바꿉니다.

Windows에서 Dynamic Media을 사용하려면 x64 및 x86용 Microsoft Visual Studio 2010, 2013 및 2015 재배포용 파일을 설치해야 합니다.

x64

* Microsoft Visual Studio 2010 재배포 가능 여부는 다음 위치에서 찾을 수 있습니다. [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* Microsoft Visual Studio 2013 재배포 가능 여부는 다음 위치에서 찾을 수 있습니다. [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* Microsoft Visual Studio 2015 재배포 가능 여부는 다음 위치에서 찾을 수 있습니다. [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* Microsoft Visual Studio 2010 재배포 가능 여부는 다음 위치에서 찾을 수 있습니다. [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Microsoft Visual Studio 2013 재배포 가능 여부는 다음 위치에서 찾을 수 있습니다. [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft Visual Studio 2015 재배포 가능 여부는 다음 위치에서 찾을 수 있습니다. [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x 이상
* 평가판 및 데모 용으로만 지원됩니다

### AEM Forms PDF 생성기 요구 사항 {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>제품</strong></p> </th> 
   <th><p><strong>PDF으로 변환을 위한 지원되는 형식</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 클래식 트랙</a></p> </td> 
   <td><p>XPS, 이미지 형식(BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF 및 DWF)</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
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
   <td>Corel WordPerfect X7</td> 
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, SXW, SXW, SXD, SXD, XLS, DOC, DOCX, PPT, PPTX, PPTX, 이미지 형식(BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JPX, JPX, JPX2, J2C, JPC, RTF, TXT, RTF, TXT, TXT, RTF, TXT, TXT, TXT, RTF, TXT, RTF, TXT, RTF, TXT, RTF</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, SXW, SXW, SXD, SXD, XLS, DOC, DOCX, PPT, PPTX, PPTX, 이미지 형식(BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPX, JPX, JPX, JPX2, J2C, JPC, RTF, TXT, RTF, TXT, TXT, RTF, TXT, TXT, TXT, RTF, TXT, RTF, TXT, RTF, TXT, RTF</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF 생성기는 지원되는 운영 체제 및 응용 프로그램의 영어, 프랑스어, 독일어 및 일본어 버전만 지원합니다.
>
>또한
>
>* PDF 생성기 필요 [Acrobat 2017 classic track 버전 17.011.30078 이상](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) 변환을 수행합니다.
>* AEM Forms은 지원되는 소프트웨어의 32비트 버전만 지원합니다.
>* OCR PDF(검색 가능한 PDF), Optimize PDF 및 Export PDF 기능은 Microsoft Windows에서만 지원됩니다.
>* HTML2PDF 서비스는 AIX에서 더 이상 사용되지 않습니다.
>* OpenOffice용 PDF 생성기 변환은 Windows, Linux 및 Solaris에서만 지원됩니다.
>* OCR PDF, Optimize PDF 및 Export PDF 기능은 Windows에서만 지원됩니다.
>* Acrobat 버전은 PDF 생성기 기능을 활성화하기 위해 AEM Forms과 번들로 제공됩니다. AEM Forms PDF Generator에서 사용하기 위해 번들로 제공되는 버전은 AEM Forms 라이센스 기간 동안 AEM Forms을 통해서만 프로그래밍 방식으로 액세스할 수 있습니다. 자세한 내용은 배포에 따라 AEM Forms 제품 설명([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) 또는 [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
>


### AEM Forms 디자이너 요구 사항 {#requirements-for-aem-forms-designer}

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

### AEM Assets XMP 메타데이터 쓰기 되돌리기 요구 사항 {#requirements-for-aem-assets-xmp-metadata-write-back}

XMP Write-back은 다음 플랫폼 및 파일 형식에 대해 지원되고 활성화됩니다.

**운영 체제**

* Linux(32비트, 64비트 시스템에서 32비트 애플리케이션 지원 필요) 32비트 클라이언트 라이브러리를 설치하는 단계는 다음을 참조하십시오 [64비트 RedHat Linux에서 XMP 추출 및 쓰기 응답을 활성화하는 방법](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

* Windows Server
* Solaris oracle
* Mac OS X(64비트)

**파일 형식**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### AEM Screens Player 요구 사항 {#requirements-for-aem-screens-player}

AEM Screens Player 버전 3.3.x는 다음 운영 체제를 지원합니다.

* Microsoft Windows 10 Enterprise LTSB
* Google Chrome OS 62+
* Google Android 5.1.1(업데이트된 Android System WebView 버전 52 이상 포함)
* Apple iOS 10.3+
* Apple macOS 10.12+
