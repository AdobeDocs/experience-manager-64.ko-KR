---
title: 배포 및 유지 관리
seo-title: Deploying and Maintaining
description: AEM 설치를 시작하는 방법을 알아봅니다.
seo-description: Learn how to get started with the AEM installation.
uuid: 552a41a1-a8b3-4c5a-bfb3-718bcb612752
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 6696c325-d188-41c8-a39f-c8ae7f339fe8
exl-id: 9a779cde-dfdf-4d70-a452-5e7d12bf3f28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1855'
ht-degree: 3%

---

# 배포 및 유지 관리{#deploying-and-maintaining}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 페이지에서는 다음 항목을 확인할 수 있습니다.

* [기본 개념](#basic-concepts)

   * [AEM이란?](#what-is-aem)
   * [일반적인 배포](#typical-deployment-scenarios)

      * [On-premise](#on-premise)
      * [Cloud Manager를 사용한 Managed Services](#managed-services-using-cloud-manager)

* [시작하기](#getting-started)

   * [사전 요구 사항](#prerequisites)
   * [소프트웨어 가져오기](#getting-the-software)
   * [기본 로컬 설치](#default-local-install)
   * [작성 및 게시 설치](#author-and-publish-installs)
   * [설치 디렉토리 압축 해제](#unpacked-install-directory)
   * [시작 및 중지](#starting-and-stopping)

이러한 기본 사항을 숙지하고 나면 다음 하위 페이지에서 보다 고급 및 세부 정보를 찾을 수 있습니다.

* [기술 요구 사항](/help/sites-deploying/technical-requirements.md)
* [권장 배포](/help/sites-deploying/recommended-deploys.md)
* [사용자 지정 독립형 설치](/help/sites-deploying/custom-standalone-install.md)
* [응용 프로그램 서버 설치](/help/sites-deploying/application-server-install.md)
* [문제 해결](/help/sites-deploying/troubleshooting.md)
* [명령줄 시작 및 중지](/help/sites-deploying/command-line-start-and-stop.md)
* [구성](/help/sites-deploying/configuring.md)
* [AEM 6.4로 업그레이드](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/sites-deploying/ecommerce.md)
* [구성 방법 문서](/help/sites-deploying/ht-deploy.md)
* [웹 콘솔](/help/sites-deploying/web-console.md)
* [복제 문제 해결](/help/sites-deploying/troubleshoot-rep.md)
* [모범 사례](/help/sites-deploying/best-practices.md)
* [커뮤니티 배포](/help/communities/deploy-communities.md)
* [AEM Platform 소개](/help/sites-deploying/platform.md)
* [성능 지침](/help/sites-deploying/performance-guidelines.md)
* [AEM Mobile 시작하기](/help/mobile/getting-started-aem-mobile.md)
* [AEM Screens 소개](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html)

## 기본 개념 {#basic-concepts}

### AEM이란? {#what-is-aem}

Adobe Experience Manager은 상업용 웹 사이트 및 관련 서비스를 제작, 관리 및 배포하는 웹 기반 클라이언트 서버 시스템입니다. 다양한 인프라 수준 및 애플리케이션 수준 기능을 하나의 통합 패키지로 결합합니다.

인프라 수준에서 AEM은 다음을 제공합니다.

* **웹 응용 프로그램 서버**: AEM은 독립형 모드(통합 Jetty 웹 서버 포함)나 타사 애플리케이션 서버(WebLogic, WebSphere 등)에서 웹 애플리케이션으로 배포할 수 있습니다.
* **웹 응용 프로그램 프레임워크**: AEM에는 RESTful 컨텐츠 지향 웹 애플리케이션의 작성을 간소화하는 Sling 웹 애플리케이션 프레임워크가 포함되어 있습니다.
* **컨텐츠 저장소**: AEM에는 비정형 및 반구조화된 데이터를 위해 특별히 설계된 계층적 데이터베이스 유형인 JCR(Java Content Repository)이 포함되어 있습니다. 저장소는 사용자 대상 컨텐츠뿐만 아니라 애플리케이션에서 사용하는 모든 코드, 템플릿 및 내부 데이터도 저장합니다.

이 베이스를 기반으로 구축된 AEM에서는 다음을 관리할 수 있는 다양한 애플리케이션 수준 기능도 제공합니다.

* **웹 사이트**
* **모바일 애플리케이션**
* **디지털 발행물**
* **양식**
* **디지털 자산**
* **커뮤니티**
* **온라인 상거래**

마지막으로, 고객은 이러한 인프라 및 애플리케이션 수준의 기본 구성 요소를 사용하여 자체 애플리케이션을 구축함으로써 맞춤형 솔루션을 만들 수 있습니다.

AEM 서버가 **Java 기반** 해당 플랫폼을 지원하는 대부분의 운영 체제에서 실행됩니다. AEM과의 모든 클라이언트 상호 작용은 **웹 브라우저**.

### 일반적인 배포 시나리오 {#typical-deployment-scenarios}

AEM 용어에서 &quot;인스턴스&quot;는 서버에서 실행되는 AEM의 사본입니다. AEM 설치에는 일반적으로 두 개 이상의 인스턴스가 포함되며, 일반적으로 별도의 시스템에서 실행됩니다.

* **작성자**: 컨텐츠를 생성, 업로드 및 편집하고 웹 사이트를 관리하는 데 사용되는 AEM 인스턴스. 컨텐츠가 라이브로 전환될 준비가 되면 게시 인스턴스에 복제됩니다.
* **게시**: 게시된 컨텐츠를 대중에게 제공하는 AEM 인스턴스입니다.

이러한 인스턴스는 설치된 소프트웨어의 측면에서 동일합니다. 구성 요소로만 구별됩니다. 또한 대부분의 설치에서 디스패처를 사용합니다.

* **Dispatcher**: 정적 웹 서버(Apache httpd, Microsoft IIS 등) 증강으로 AEM dispatcher 모듈을 사용합니다. 게시 인스턴스에서 생성된 웹 페이지를 캐시하여 성능을 개선합니다.

이 설정에는 많은 고급 옵션과 정교함이 있지만 작성, 게시 및 디스패처의 기본 패턴은 대부분의 배포의 핵심입니다. 우리는 비교적 간단한 설정에 초점을 맞추는 것으로 시작할 것입니다. 고급 배포 옵션에 대한 토론이 따릅니다.

다음 섹션에서는 두 시나리오에 대해 설명합니다.

* **On-premise**: AEM은 기업 환경에서 구축 및 관리됩니다.

* **Managed Services - Adobe Experience Manager용 Cloud Manager**: Adobe Managed Services에서 배포 및 관리하는 AEM.

### On-premise {#on-premise}

회사 환경의 서버에 AEM을 설치할 수 있습니다. 일반적인 설치 인스턴스는 다음과 같습니다. 개발, 테스트 및 게시 환경. 자세한 내용은 [시작하기](/help/sites-deploying/deploy.md#getting-started) 섹션을 참조하십시오.

일반적인 온프레미스 배포에 대한 자세한 내용은 [권장 배포](/help/sites-deploying/recommended-deploys.md).

### Cloud Manager를 사용한 Managed Services {#managed-services-using-cloud-manager}

AEM Managed Services은 디지털 경험 관리를 위한 완벽한 솔루션입니다. 온-프레미스 배포의 모든 제어, 보안 및 사용자 지정 이점을 유지하면서 클라우드에서 경험 전달 솔루션의 이점을 제공합니다. AEM Managed Services을 사용하면 클라우드에 배포하고 Adobe의 우수 사례 및 지원을 통해 고객이 보다 신속하게 시작할 수 있습니다. 조직 및 비즈니스 사용자는 IT에 대한 부담을 줄이면서 짧은 시간에 고객의 참여를 유도하고 시장 점유율을 높이며 혁신적인 마케팅 캠페인을 만드는 데 집중할 수 있습니다.

AEM Managed Services 고객은 다음과 같은 이점을 누릴 수 있습니다.

**시장 출시 시간 단축:** Adobe Managed Services의 유연한 클라우드 인프라를 통해 조직은 성공적인 디지털 경험을 신속하게 계획, 실행 및 최적화할 수 있습니다. Adobe은 추가적인 자본, 하드웨어 또는 소프트웨어 필요 없이 클라우드 아키텍처를 관리하며 Adobe의 고객 성공 엔지니어와 백엔드 앱에 연결하기 위한 AEM 아키텍처, 프로비저닝, 사용자 지정 및 go-live 우수 사례를 지원합니다.

**높은 성능:** 99.5%, 99.9%, 99.95%, 99.99% 및 99.99%의 서비스 가용성 옵션을 통해 비즈니스에 안정적인 디지털 경험을 제공합니다. 또한 자동 백업 및 다중 모드 재해 복구 모델을 통해 신뢰성 및 우발적 관리를 보장할 수 있습니다.

**IT 비용 최적화:** 사전 예방 지침 및 전문 기술은 조직이 최신 버전의 AEM을 계속 사용할 수 있도록 지원합니다. Adobe Platinum 유지 관리 및 지원은 AMS Enterprise/Basic의 새로운 배포에 자동으로 포함되며 조직에서 미션 크리티컬 애플리케이션을 유지할 수 있도록 기술 전문 지식과 운영 경험을 제공합니다. 무료 기본 Analytics 또는 Target 기능은 특히 분석 및 개인화에 대한 요구 사항이 제한된 중간 규모 조직의 경우 추가적인 가치를 제공합니다.

**최고 보안:** 방화벽 시스템 후방 또는 가상 사설 클라우드 내에서 고객 애플리케이션을 제한된 액세스 시설에 호스팅하여 엔터프라이즈급 물리적, 네트워크 및 데이터 보안을 보장합니다. 여기에는 강력한 데이터 저장 암호화, 안티바이러스 및 데이터 격리 기능을 갖춘 단일 임차인 가상 시스템이 포함됩니다.

**Cloud Manager**: Adobe Experience Manager Managed Services 서비스의 일부인 Cloud Manager는 조직에서 클라우드에서 Adobe Experience Manager을 자체 관리할 수 있도록 해주는 셀프서비스 포털입니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 최신 CI/CD(지속적 통합 및 지속적 배포) 파이프라인이 포함되어 있습니다. Cloud Manager는 Adobe Managed Service 고객만 사용할 수 있습니다.

Cloud Manager 및 해당 리소스에 대한 자세한 내용은 [**Cloud Manager 사용 안내서**](https://helpx.adobe.com/experience-manager/cloud-manager/user-guide.html).

## 시작하기 {#getting-started}

### 사전 요구 사항 {#prerequisites}

프로덕션 인스턴스는 일반적으로 공식적으로 지원되는 OS를 실행하는 전용 시스템에서 실행됩니다( [기술 요구 사항](/help/sites-deploying/technical-requirements.md))로 설정되면 Experience Manager 서버는 을 지원하는 모든 시스템에서 실제로 실행됩니다 [**Java Standard Edition 8**](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

숙지하고 AEM에서 개발하는 데 사용하기 위해 Apple OS X 또는 Microsoft Windows 또는 Linux의 데스크탑 버전을 실행하는 로컬 시스템에 설치된 인스턴스를 사용하는 것이 일반적입니다.

클라이언트측에서 AEM은 모든 최신 브라우저(**Microsoft Edge**, **Internet Explorer** 11, **Chrome** 51+ , **Firefox** 47+, **Safari** 8+) 데스크탑 및 태블릿 운영 체제에서 모두 사용할 수 있습니다. 자세한 내용은 [지원되는 클라이언트 플랫폼](/help/sites-deploying/technical-requirements.md#supported-client-platforms) 자세한 내용

### 소프트웨어 가져오기 {#getting-the-software}

유효한 유지 관리 및 지원 계약을 보유한 고객은 코드가 포함된 메일 알림을 수신하여 [**Adobe 라이선스 웹 사이트**](https://licensing.adobe.com/). 비즈니스 파트너는 [**spphelp@adobe.com**](mailto:spphelp@adobe.com).

AEM 소프트웨어 패키지는 다음 두 가지 방법으로 사용할 수 있습니다.

* **cq-quickstart-6.4.0.jar:** 독립형 실행 파일 *jar* 파일을 설정하고 실행하는 데 필요한 모든 것이 포함된 파일입니다.

* **cq-quickstart-6.4.0.war:** A *전쟁* 타사 애플리케이션 서버에 배포할 파일입니다.

다음 섹션에서는 **독립형 설치**. 애플리케이션 서버에 AEM 설치에 대한 자세한 내용은 [응용 프로그램 서버 설치](/help/sites-deploying/application-server-install.md).

### 기본 로컬 설치 {#default-local-install}

1. 로컬 컴퓨터에 설치 디렉터리를 만듭니다. 예:

   UNIX 설치 위치: **/opt/aem**

   Windows 설치 위치: **`C:\Program Files\aem`**

   마찬가지로 데스크탑의 폴더에 샘플 인스턴스를 설치하는 것이 일반적입니다. 어떤 경우든 이 위치는 일반적으로 다음과 같이 표시됩니다.

   `<aem-install>`

   *파일 디렉토리의 경로는 US ASCII 문자로만 구성되어야 합니다.*

1. 배치 **jar** 및 **라이선스** 이 디렉터리에 있는 파일:

   ```shell
   <aem-install>/
       cq-quickstart-6.4.0.jar
       license.properties
   ```

   를 제공하지 않는 경우 `license.properties` 파일에서, AEM은 브라우저를 **시작** 시작 시 화면에 라이센스 키를 입력할 수 있습니다. 아직 라이센스 키가 없는 경우 Adobe에서 유효한 라이센스 키를 요청해야 합니다.

1. GUI 환경에서 인스턴스를 시작하려면 **`cq-quickstart-6.4.0.jar`** 파일.

   또는 명령줄에서 AEM을 시작할 수 있습니다. 32비트 Java VM의 경우 다음을 입력합니다.

   ```shell
       java -Xmx1024M -jar cq-quickstart-6.4.0.jar
   ```

   64비트 VM의 경우 다음을 입력합니다.

   ```shell
       java -XX:MaxPermSize=256m -Xmx1024M -jar cq-quickstart-6.4.0.jar
   ```

AEM에서 jar 파일의 압축을 풀고 자체적으로 설치한 다음 시작하는 데 몇 분이 걸립니다. 위의 절차는 다음과 같습니다.

* an **AEM 작성자** 인스턴스
* 실행 **localhost**
* 포트 **4502년**

인스턴스에 액세스하려면 브라우저가 다음 위치로 이동하십시오.

**`http://localhost:4502`**

작성자 인스턴스의 결과는 **게시 인스턴스** on **`localhost:4503`**.

### 작성 및 게시 설치 {#author-and-publish-installs}

기본 설치(A) **작성자** 인스턴스 **`localhost:4502`**)은 단순히 이름을 바꾸면 변경할 수 있습니다 `jar` 파일을 먼저 시작하기 전에 먼저 파일을 작성합니다. 이름 지정 패턴은 다음과 같습니다.

**`cq-<instance-type>-p<port-number>.jar`**

예를 들어 파일 이름을

**`cq-author-p4502.jar`**

를 실행하면 작성자 인스턴스가에 실행됩니다. **`localhost:4502`**.

마찬가지로 파일 이름 바꾸기 및 실행

**`cq-publish-p4503.jar`**

이 실행되면 게시 인스턴스가 **`localhost:4503`**.

예를 들어에 이러한 두 인스턴스를 설치합니다

`<aem-install>/author`및

**`<aem-install>/publish`**

설치 사용자 지정에 대한 자세한 내용은 다음을 참조하십시오.

* [사용자 지정 독립형 설치](/help/sites-deploying/custom-standalone-install.md)
* [실행 모드](/help/sites-deploying/configure-runmodes.md)

### 설치 디렉토리 압축 해제 {#unpacked-install-directory}

quickstart jar를 처음 실행하면 라는 새 하위 디렉토리 아래에 있는 동일한 디렉토리에 바로 그 자체의 압축을 해제합니다 `crx-quickstart`. 다음을 완료해야 합니다.

```xml
<aem-install>/
    license.properties
    cq-quickstart-6.4.0.jar
    crx-quickstart/
        app/
        bin/
        conf/
        launchpad/
        logs/
        metrics/        
        monitoring/
        opt/
        repository/
        threaddumps/
        eula-de_DE.html
        eula-en_US.html
        eula-fr_FR.html
        eula-ja_JP.html
        readme.txt
```

인스턴스가 GUI에서 설치된 경우 브라우저 창이 자동으로 열리고 인스턴스의 호스트 및 포트와 온/오프 스위치를 표시하는 데스크톱 응용 프로그램 창도 열립니다.

![screen_shot_2018-04-05at91504am1](assets/screen_shot_2018-04-05at91504am1.png)

>[!NOTE]
>
>symlink를 사용하는 경우 [symlink 관련 문제](https://helpx.adobe.com/experience-manager/kb/changing-symlink.html).

### 시작 및 중지 {#starting-and-stopping}

AEM이 압축을 풀고 처음 시작하면 설치 디렉터리에서 jar 파일을 두 번 클릭하면 인스턴스가 시작되지만 다시 설치되지 않습니다.

GUI에서 인스턴스를 중지하려면 **설정/해제** 데스크탑 응용 프로그램 창에서 전환합니다.

명령줄에서 AEM을 중지하거나 시작할 수도 있습니다. 처음으로 인스턴스를 이미 설치했다고 가정할 경우 **명령줄 스크립트** 는 다음 위치에 있습니다.

**`<aem-install>/crx-quickstart/bin/`**

이 폴더에는 다음 Unix bash 셸 스크립트가 포함되어 있습니다.

* **`start`**: 인스턴스를 시작합니다
* `stop`: 인스턴스를 중지합니다
* **`status`**: 인스턴스의 상태를 보고합니다
* **`quickstart`**: 필요한 경우 시작 정보를 구성하는 데 사용됩니다.

동등한 것도 있습니다 **`bat`** Windows용 파일 자세한 내용은 다음을 참조하십시오.

* [명령줄 시작 및 중지](/help/sites-deploying/command-line-start-and-stop.md)

AEM이 시작되고 웹 브라우저를 적절한 페이지(일반적으로 로그인 페이지)로 자동 리디렉션합니다. 예:

`http://localhost:4502/`

![screen_shot_2018-04-03at15317pm1](assets/screen_shot_2018-04-03at15317pm1.png)

로그인하면 AEM에 액세스할 수 있습니다. 자세한 내용은 역할에 따라 다음을 참조하십시오.

* [작성](/help/sites-authoring/home.md)
* [관리](/help/sites-administering/home.md)
* [개발](/help/sites-developing/home.md)
* [관리](/help/managing/best-practices.md)

## 고급 배포 {#advanced-deployment}

위의 섹션에서는 AEM 설치의 기본 사항을 잘 이해할 수 있습니다. 그러나 AEM의 전체 프로덕션 시스템을 설치하려면 훨씬 더 복잡한 작업이 필요할 수 있습니다. 고급 설치에 대한 전체 내용은 다음 하위 페이지를 참조하십시오.

* [기술 요구 사항](/help/sites-deploying/technical-requirements.md)
* [권장 배포](/help/sites-deploying/recommended-deploys.md)
* [사용자 지정 독립형 설치](/help/sites-deploying/custom-standalone-install.md)
* [응용 프로그램 서버 설치](/help/sites-deploying/application-server-install.md)
* [문제 해결](/help/sites-deploying/troubleshooting.md)
* [명령줄 시작 및 중지](/help/sites-deploying/command-line-start-and-stop.md)
* [구성](/help/sites-deploying/configuring.md)
* [AEM 6.4로 업그레이드](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/sites-deploying/ecommerce.md)
* [구성 방법 문서](/help/sites-deploying/ht-deploy.md)
* [웹 콘솔](/help/sites-deploying/web-console.md)
* [복제 문제 해결](/help/sites-deploying/troubleshoot-rep.md)
* [모범 사례](/help/sites-deploying/best-practices.md)
* [커뮤니티 배포](/help/communities/deploy-communities.md)
* [AEM Platform 소개](/help/sites-deploying/platform.md)
* [성능 지침](/help/sites-deploying/performance-guidelines.md)
* [AEM Mobile 시작하기](/help/mobile/getting-started-aem-mobile.md)
* [AEM Screens 소개](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html)
