---
title: AEM Forms 서버의 성능 조정
seo-title: Performance tuning of AEM Forms server
description: AEM Forms이 최적의 성능을 발휘하도록 캐시 설정 및 JVM 매개 변수를 미세 조정할 수 있습니다. 또한 웹 서버를 사용하면 AEM Forms 배포 성능을 향상시킬 수 있습니다.
seo-description: For AEM Forms to perform optimally, you can fine-tune the cache settings and JVM parameters. Also, using a web server can enhance the performance of AEM Forms deployment.
uuid: 77eaeecc-ca52-4d3d-92e6-1ab4d91b9edd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 5d672b56-00c4-46a0-974b-e174fbdf07d6
role: Admin
exl-id: bc750571-08a5-414c-aed5-4e839f6695ae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 2%

---

# AEM Forms 서버의 성능 조정 {#performance-tuning-of-aem-forms-server}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 문서에서는 병목 현상을 줄이고 AEM Forms 배포의 성능을 최적화하기 위해 구현할 수 있는 전략 및 모범 사례에 대해 설명합니다.

## 캐시 설정 {#cache-settings}

를 사용하여 AEM Forms에 대한 캐싱 전략을 구성하고 제어할 수 있습니다. **모바일 Forms 구성** AEM Web Configuration Console의 구성 요소:

* (OSGi의 AEM Forms) `https://[server]:[port]/system/console/configMgr`
* (JEE의 AEM Forms) `https://[server]:[port]/lc/system/console/configMgr`

캐싱에 사용할 수 있는 옵션은 다음과 같습니다.

* **없음**: 아티팩트를 캐시하지 않도록 강제 적용합니다. 따라서 실제로 성능이 저하되고 캐시가 없기 때문에 높은 메모리 가용성이 필요합니다.
* **보수**: 인라인 조각 및 이미지가 포함된 템플릿과 같이 양식을 렌더링하기 전에 생성된 중간 아티팩트만 캐시하도록 지시합니다.
* **공격적**: 강제 적용에서는 Reactive 캐싱 수준의 모든 아티팩트 외에 렌더링된 HTML 컨텐츠를 포함하여 캐싱할 수 있는 거의 모든 항목을 캐싱합니다. 따라서 성능이 가장 뛰어나지만 캐시된 아티팩트를 저장하는 데 더 많은 메모리를 사용합니다. 공격적인 캐싱 전략은 렌더링된 컨텐츠가 캐싱될 때 양식을 렌더링할 때 일관된 시간 성능을 얻음을 의미합니다.

AEM Forms의 기본 캐시 설정이 최적의 성능을 발휘하기에 충분하지 않을 수 있습니다. 따라서 다음 설정을 사용하는 것이 좋습니다.

* **캐시 전략**: 공격적
* **캐시 크기** (양식 개수 기준): 필요에 따라
* **최대 개체 크기**: 필요에 따라

![모바일 Forms 구성](assets/snap.png)

>[!NOTE]
>
>AEM Dispatcher를 사용하여 적응형 양식을 캐시하는 경우 미리 채워진 데이터가 있는 양식이 포함된 적응형 양식도 캐시합니다. 이러한 양식이 AEM Dispatcher 캐시에서 제공되는 경우 미리 채워진 데이터나 오래된 데이터를 사용자에게 제공할 수 있습니다. 따라서 AEM Dispatcher를 사용하여 사전 채워진 데이터를 사용하지 않는 적응형 양식을 캐싱합니다. 또한 디스패처 캐시는 캐시된 조각을 자동으로 무효화하지 않습니다. 따라서 양식 조각을 캐시하는 데 이 필드를 사용하지 마십시오. 이러한 양식 및 조각의 경우 [적응형 양식 캐시](/help/forms/using/configure-adaptive-forms-cache.md).

## JVM 매개 변수 {#jvm-parameters}

최적의 성능을 위해 다음 JVM을 사용하는 것이 좋습니다 `init` 구성할 인수 `Java heap` 및 `PermGen`.

```java
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>권장되는 설정은 Windows 2008 R2 8 Core 및 Oracle HotSpot 1.7(64비트) JDK이며 시스템 구성에 따라 확대하거나 축소할 수 있습니다.

## 웹 서버 사용 {#using-a-web-server}

적응형 양식 및 HTML5 양식은 HTML5 형식으로 렌더링됩니다. 결과 출력은 양식 크기 및 양식 이미지와 같은 요소에 따라 클 수 있습니다. 데이터 전송을 최적화하기 위해 권장되는 방법은 요청을 제공하는 웹 서버를 사용하여 HTML 응답을 압축하는 것입니다. 이 접근 방식은 응답 크기, 네트워크 트래픽, 서버와 클라이언트 시스템 간의 데이터를 스트리밍하는 데 필요한 시간을 줄입니다.

예를 들어, JBoss를 사용하여 Apache Web Server 2.0 32비트에서 압축을 활성화하려면 다음 단계를 수행하십시오.

>[!NOTE]
>
>다음 지침은 Apache Web Server 2.0 32비트 이외의 서버에는 적용되지 않습니다. 다른 서버와 관련된 단계는 해당 제품 설명서를 참조하십시오.

다음 단계에서는 Apache 웹 서버를 사용하여 압축을 활성화하는 데 필요한 변경 사항을 보여줍니다

**운영 체제에 적용할 수 있는 Apache 웹 서버 소프트웨어를 얻습니다.**

* Windows: apache HTTP Server Project 사이트에서 Apache 웹 서버를 다운로드합니다.
* Solaris 64비트: solaris용 Sunfreeware 웹 사이트에서 Apache 웹 서버를 다운로드합니다.
* Linux: apache 웹 서버는 Linux 시스템에 미리 설치됩니다.

Apache는 HTTP 프로토콜을 사용하여 CRX와 통신할 수 있습니다. 구성은 HTTP를 사용하여 최적화를 위한 것입니다.

1. 에서 다음 모듈 구성의 주석 처리를 취소합니다. `APACHE_HOME/conf/httpd.conf` 파일.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Linux의 경우 기본값입니다 `APACHE_HOME` is `/etc/httpd/`.

1. crx의 포트 4502에서 프록시를 구성합니다.

   에 다음 구성 추가 `APACHE_HOME/conf/httpd.conf` 구성 파일.

   ```java
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. 압축을 활성화합니다. 에 다음 구성 추가 `APACHE_HOME/conf/httpd.conf` 구성 파일.

   **HTML5 양식의 경우**

   ```java
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **적응형 양식의 경우**

   ```java
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   crx 서버에 액세스하려면 `https://[server]:80`, 위치 `server` 는 Apache 서버가 실행 중인 서버의 이름입니다.

## AEM Forms을 실행하는 서버에서 안티바이러스 사용 {#using-an-antivirus-on-server-running-aem-forms}

바이러스 백신 소프트웨어를 실행하는 서버에서 성능이 저하될 수 있습니다. 항상 안티바이러스(On-Access Scanning) 소프트웨어가 시스템의 모든 파일을 검색합니다. 이렇게 하면 서버 속도가 느려질 수 있고 AEM Forms의 성능이 영향을 받습니다.

성능을 향상시키기 위해 안티바이러스 소프트웨어에서 다음 AEM Forms 파일 및 폴더를 항상 설정(On-Access) 검사에서 제외하도록 지시할 수 있습니다.

* AEM 설치 디렉토리. 전체 디렉터리를 제외할 수 없는 경우 다음을 제외합니다.

   * [AEM 설치 디렉토리]\crx-repository\temp
   * [AEM 설치 디렉토리]\crx-repository\repository
   * [AEM 설치 디렉토리]\crx-repository\launchpad

* 응용 프로그램 서버 임시 디렉터리입니다. 기본 위치는 다음과 같습니다.

   * (Jboss) [AEM 설치 디렉토리]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(JEE의 AEM Forms만 해당)** GDS(전역 문서 저장소) 디렉터리입니다. 기본 위치는 다음과 같습니다.

   * (JBoss) `[appserver root]/server/[server]/svcnative/DocumentStorage`
   * (WebLogic) `[appserverdomain]/[server]/adobe/LiveCycleServer/DocumentStorage`
   * (WebSphere) `[appserver root]/installedApps/adobe/[server]/DocumentStorage`

* **(JEE의 AEM Forms만 해당)** AEM Forms 서버 로그 및 임시 디렉토리. 기본 위치는 다음과 같습니다.

   * 서버 로그 - `[AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs`
   * 임시 디렉터리 - [AEM Forms 설치 디렉토리]\temp

>[!NOTE]
>
>* GDS 및 임시 디렉토리에 대해 다른 위치를 사용하는 경우 AdminUI를에서 엽니다. `https://[server]:[port]/adminui)`, 다음 위치로 이동합니다. **홈 > 설정 > 핵심 시스템 설정 > 핵심 구성** 를 클릭하여 사용 중인 위치를 확인합니다.
* AEM Forms 서버가 제안된 디렉터리를 제외한 후에도 느리게 수행하는 경우 Java 실행 파일(java.exe)도 제외합니다.
>

