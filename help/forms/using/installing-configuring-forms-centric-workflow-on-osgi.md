---
title: OSGi에 Forms 중심의 워크플로우 설치 및 구성
seo-title: Installing and Configuring Forms-centric workflow on OSGi
description: 비즈니스 서신, 문서, 명세서, 혜택 공지, 마케팅 이메일, 청구서 및 환영 키트를 만들도록 AEM Forms Interactive Communications를 설치 및 구성합니다.
seo-description: Install and configure AEM Forms Interactive Communications to create business correspondences, documents, statements, benefit notices, marketing mails, bills, and welcome kits.
uuid: 847c3351-dc46-4e60-a023-0f4e9e057c7c
topic-tags: installing
discoiquuid: 7333641e-8c8c-4b52-a7da-a2976c88592c
role: Admin
exl-id: 308b106f-4c5a-49d6-a7f6-c1e8a0bf62e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1645'
ht-degree: 8%

---

# OSGi에 Forms 중심의 워크플로우 설치 및 구성 {#installing-and-configuring-forms-centric-workflow-on-osgi}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

기업은 여러 양식, 백엔드 시스템 및 기타 데이터 소스에서 데이터를 수집하고 처리합니다. 데이터 처리에는 검토 및 승인 절차, 반복 작업, 데이터 아카이빙이 포함됩니다. 예를 들어 양식을 검토하고 PDF 문서로 변환합니다. 수동 작업을 수행하면 반복 작업에 많은 시간과 리소스가 소요될 수 있습니다.

다음을 사용할 수 있습니다 [OSGi의 Forms 중심 워크플로우](/help/forms/using/aem-forms-workflow.md) 적응형 양식 기반 워크플로우를 신속하게 구축할 수 있습니다. 이러한 워크플로우를 통해 검토 및 승인 워크플로우, 비즈니스 프로세스 워크플로우 및 기타 반복 작업을 자동화할 수 있습니다. 또한 이러한 워크플로우는 문서 처리(PDF 문서 작성, 조합, 배포 및 보관, 문서 액세스를 제한하는 디지털 서명 추가, 바코드 양식 디코딩 등)와 양식 및 문서에서 Acrobat Sign 서명 워크플로우를 사용하는 데 도움이 됩니다.

설정되면 사용자가 양식 또는 대화형 커뮤니케이션을 제출할 때 이러한 워크플로우를 수동으로 트리거하여 정의된 프로세스를 완료하거나 프로그래밍 방식으로 실행할 수 있습니다. 이 기능은 AEM Forms 추가 기능 패키지에 포함되어 있습니다.

AEM Forms은 강력한 엔터프라이즈급 플랫폼입니다. OSGi의 Forms 중심의 워크플로우는 AEM Forms의 기능 중 하나입니다. 전체 기능 목록에 대해서는 다음을 참조하십시오 [AEM Forms 소개](/help/forms/using/introduction-aem-forms.md).

>[!NOTE]
>
>OSGi의 Forms 중심 워크플로우를 사용하면 JEE 스택에 완전한 프로세스 관리 기능을 설치하지 않고도 OSGi 스택에서 다양한 작업에 대한 워크플로우를 신속하게 작성하고 배포할 수 있습니다. 다음을 참조하십시오 [비교](/help/forms/using/capabilities-osgi-jee-workflows.md) OSGi 및 JEE의 Process Management에 대한 Forms 중심의 AEM Workflows의 차이점과 유사성을 살펴봅니다.
>
>비교 후 JEE 스택에 프로세스 관리 기능을 설치하도록 선택한 경우 다음을 참조하십시오. [JEE에서 AEM Forms 설치 또는 업그레이드](/help/forms/home.md) jee 스택 설치 및 구성 및 프로세스 관리 기능에 대한 자세한 내용은 를 참조하십시오.

## 배포 토폴로지 {#deployment-topology}

AEM Forms 추가 기능 패키지는 AEM에 배포된 애플리케이션입니다. OSGi 기능에서 Forms 중심의 워크플로우를 실행하려면 최소 1개의 AEM 작성자 또는 처리 인스턴스(프로덕션 작성자)만 필요합니다. 처리 인스턴스는 [경화된 AEM 작성자](/help/forms/using/hardening-securing-aem-forms-environment.md) 인스턴스. 프로덕션 작성자에서 워크플로우 또는 적응형 양식 만들기와 같은 실제 작성을 수행하지 마십시오.

다음 토폴로지는 OSGi 기능에서 AEM Forms Interactive Communications, Correspondence Management, AEM Forms 데이터 캡처 및 Forms 중심의 워크플로우를 실행하기 위한 토폴로지를 나타냅니다. 토폴로지에 대한 자세한 내용은 [AEM Forms을 위한 아키텍처 및 배포 토폴로지](/help/forms/using/aem-forms-architecture-deployment.md).

![권장 토폴로지](assets/recommended-topology.png)

OSGi의 AEM Forms Forms 중심 워크플로우는 AEM Forms의 작성자 인스턴스에서 AEM 받은 편지함 및 AEM 워크플로우 모델 작성 UI를 실행합니다.

## 시스템 요구 사항 {#system-requirements}

>[!NOTE]
>
>로 이동 [다음 단계](#next-steps) 의 설명에 따라 OSGi에 AEM Forms을 이미 설치한 경우 문서의 섹션 [데이터 캡처 기능 설치 및 구성](/help/forms/using/installing-configuring-aem-forms-osgi.md) 문서.

OSGi에서 Forms 중심의 워크플로우를 설치 및 구성하기 전에 다음을 확인합니다.

* 하드웨어 및 소프트웨어 인프라가 제대로 구축되어 있습니다. 지원되는 하드웨어 및 소프트웨어에 대한 자세한 내용은 [기술 요구 사항](/help/sites-deploying/technical-requirements.md).

* AEM 인스턴스의 설치 경로에 공백이 들어 있지 않습니다.
* AEM 인스턴스가 실행 중입니다. AEM 용어에서 &quot;인스턴스&quot;는 작성자 또는 게시 모드에서 서버에서 실행되는 AEM의 사본입니다. OSGi에서 Forms 중심의 워크플로우를 실행하려면 하나 이상의 AEM 인스턴스(작성자 또는 처리)가 필요합니다.

   * **작성자**: 컨텐츠를 작성, 업로드 및 편집하고 웹 사이트를 관리하는 데 사용되는 AEM 인스턴스입니다. 컨텐츠가 라이브로 전환될 준비가 되면 게시 인스턴스에 복제됩니다.
   * **처리 중:** 처리 인스턴스는 [경화된 AEM 작성자](/help/forms/using/hardening-securing-aem-forms-environment.md) 인스턴스. 설치를 수행한 후 작성자 인스턴스를 설정하고 이를 취소할 수 있습니다.
   * **게시**: 인터넷 또는 내부 네트워크를 통해 대중에게 게시된 컨텐츠를 제공하는 AEM 인스턴스입니다.

* 메모리 요구 사항이 충족되었습니다. AEM Forms 추가 기능 패키지에는 다음이 필요합니다.

   * Microsoft Windows 기반 설치를 위한 15GB의 임시 공간.
   * UNIX 기반 설치를 위한 6GB의 임시 공간.

* UNIX 기반 시스템에 대한 추가 요구 사항: UNIX 기반 운영 체제를 사용하는 경우 각 운영 체제의 설치 미디어에서 다음 패키지를 설치합니다.

<table> 
 <tbody>
  <tr>
   <td>expand</td> 
   <td>libxcb</td> 
   <td>freetype</td> 
   <td>libXau</td> 
  </tr>
  <tr>
   <td>libSM</td> 
   <td>zlib</td> 
   <td>libICE</td> 
   <td>libuuid</td> 
  </tr>
  <tr>
   <td>글라이치</td> 
   <td>libXext</td> 
   <td><p>nss-softokn-freebl</p> </td> 
   <td>fontconfig</td> 
  </tr>
  <tr>
   <td>libX11</td> 
   <td>libXrender</td> 
   <td>libXrandr</td> 
   <td>libXinerama</td> 
  </tr>
 </tbody>
</table>

## AEM Forms 추가 기능 패키지 설치 {#install-aem-forms-add-on-package}

AEM Forms 추가 기능 패키지는 AEM에 배포된 애플리케이션입니다. 이 패키지에는 OSGi 및 기타 기능에 대한 Forms 중심의 워크플로우가 포함되어 있습니다. 추가 기능 패키지를 설치하려면 다음 단계를 수행하십시오.

1. [소프트웨어 배포](https://experience.adobe.com/downloads)를 엽니다. 소프트웨어 배포에 로그인하려면 Adobe ID가 필요합니다.
1. 헤더 메뉴에 제공된 **[!UICONTROL Adobe Experience Manager]**&#x200B;를 누릅니다.
1. 에서 **[!UICONTROL 필터]** 섹션:
   1. 선택 **[!UICONTROL Forms]** 에서 **[!UICONTROL 솔루션]** 드롭다운 목록.
   2. 패키지의 버전 및 유형을 선택합니다. 를 사용할 수도 있습니다 **[!UICONTROL 다운로드 검색]** 결과를 필터링하는 옵션.
1. 운영 체제에 해당하는 패키지 이름을 탭하고 **[!UICONTROL EULA 약관 동의]**, 탭 **[!UICONTROL 다운로드]**.
1. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)를 열고 **[!UICONTROL 패키지 업로드]**&#x200B;를 클릭하여 패키지를 업로드합니다.
1. 패키지를 선택하고 **[!UICONTROL 설치]**&#x200B;를 클릭합니다.

   에 나열된 직접 링크를 통해 패키지를 다운로드할 수도 있습니다 [AEM Forms 릴리스](https://helpx.adobe.com/kr/aem-forms/kb/aem-forms-releases.html) 문서.

1. 패키지가 설치되면 AEM 인스턴스를 다시 시작하라는 메시지가 표시됩니다. **서버를 즉시 다시 시작하지 마십시오.** AEM Forms 서버를 중지하기 전에 ServiceEvent REGISTERED 및 ServiceEvent UNREGISTERED 메시지가 [AEM-Installation-Directory]/crx-quickstart/logs/error.log 파일 및 로그는 안정합니다.
1. 모든 작성자 및 게시 인스턴스에 대해 1-7단계를 반복합니다.

## 설치 후 구성 {#post-installation-configurations}

AEM Forms에는 몇 가지 필수 및 선택적 구성이 있습니다. 필수 구성에는 BoundcyCastle 라이브러리 및 직렬화 에이전트 구성이 포함됩니다. 선택적 구성에는 Dispatcher 및 Adobe Target 구성이 포함됩니다.

### 필수 설치 후 구성 {#mandatory-post-installation-configurations}

#### RSA 및 BouncyCastle 라이브러리 구성  {#configure-rsa-and-bouncycastle-libraries}

라이브러리를 부팅하려면 모든 작성자 및 게시 인스턴스에서 다음 단계를 수행하십시오.

1. 기본 AEM 인스턴스를 중지합니다.
1. 를 엽니다. [AEM 설치 디렉토리]\crx-quickstart\conf\sling.properties 파일을 편집할 수 있습니다.

   만약 [AEM 설치 디렉토리]\crx-quickstart\bin\start.bat에서 AEM을 시작한 다음, 다음에 있는 sling.properties를 편집합니다 [AEM_root]\crx-quickstart\.

1. sling.properties 파일에 다음 속성을 추가합니다.

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (AIX만 해당) sling.properties 파일에 다음 속성을 추가합니다.

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. 파일을 저장하고 닫고 AEM 인스턴스를 시작합니다.
1. 모든 작성자 및 게시 인스턴스에 대해 1-4단계를 반복합니다.

#### 직렬화 에이전트 구성 {#configure-the-serialization-agent}

모든 작성자 및 게시 인스턴스에서 다음 단계를 수행하여 패키지를 페이지에 허용 목록에 추가하다 추가합니다.

1. 브라우저 창에서 AEM 구성 관리자를 엽니다. 기본 URL은 `https://[server]:[port]/system/console/configMgr`.
1. 검색 및 열기 **Deserialization 방화벽 구성**.
1. 추가 **sun.util.calendar** 패키지 **허용 목록에 추가하다** 필드. 저장을 클릭합니다.
1. 모든 작성자 및 게시 인스턴스에 대해 1-3단계를 반복합니다.

### 설치 후 구성 옵션 {#optional-post-installation-configurations}

#### Dispatcher 구성 {#configure-dispatcher}

Dispatcher가 AEM에 대해 캐싱 및 로드 밸런싱 도구를 제공합니다. AEM Dispatcher는 또한 AEM 서버를 공격으로부터 보호합니다. Dispatcher를 엔터프라이즈급 웹 서버와 함께 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다. 만약 [Dispatcher](https://helpx.adobe.com/kr/experience-manager/dispatcher/using/dispatcher-configuration.html)그런 다음 AEM Forms에 대해 다음 구성을 수행합니다.

1. AEM Forms에 대한 액세스 구성:

   편집할 dispatcher.any 파일을 엽니다. 필터 섹션으로 이동하고 필터 섹션에 다음 필터를 추가합니다.

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   파일을 저장하고 닫습니다. 필터에 대한 자세한 내용은 [Dispatcher 설명서](https://helpx.adobe.com/kr/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. 레퍼러 필터 서비스를 구성합니다.

   관리자로 Apache Felix 구성 관리자에 로그인합니다. 구성 관리자의 기본 URL은 `https://[server]:[port_number]/system/console/configMgr`. 에서 **구성** 메뉴에서 **Apache Sling 레퍼러 필터** 선택 사항입니다. 호스트 허용 필드에 디스패처의 호스트 이름을 입력하여 레퍼러로 허용하고 를 클릭합니다. **저장**. 항목의 형식은 다음과 같습니다 `https://[server]:[port]`.

#### 캐시 구성 {#configure-cache}

캐싱은 데이터 액세스 시간을 단축하고, 지연을 줄이고, 입출력(I/O) 속도를 향상시키는 메커니즘입니다. 적응형 양식 캐시는 사전 채워진 데이터를 저장하지 않고 적응형 양식의 HTML 콘텐츠과 JSON 구조만 저장합니다. 적응형 양식을 렌더링하는 데 필요한 시간을 줄이는 데 도움이 됩니다.

* 적응형 양식 캐시를 사용하는 경우 [AEM Dispatcher](https://helpx.adobe.com/kr/experience-manager/dispatcher/using/dispatcher-configuration.html) 를 눌러 적응형 양식의 클라이언트 라이브러리(CSS 및 JavaScript)를 캐시합니다.
* 사용자 지정 구성 요소를 개발하는 동안 개발에 사용되는 서버에서 적응형 양식 캐시를 사용하지 않도록 설정하십시오.

적응형 양식 캐시를 구성하려면 다음 단계를 수행하십시오.

1. 의 AEM 웹 콘솔 구성 관리자로 이동합니다. `https://[server]:[port]/system/console/configMgr`.
1. 클릭 **[!UICONTROL 적응형 양식 및 대화형 통신 웹 채널 구성]** 구성 값을 편집하려면 다음을 수행하십시오. 구성 값 편집 대화 상자에서 AEM Forms 서버의 인스턴스가 캐싱할 수 있는 최대 양식 또는 문서 수를 **적응형 Forms 수** 필드. 기본값은 100입니다. **저장**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >캐시를 비활성화하려면 [적응형 Forms 수] 필드의 값을 **0**. 캐시 구성을 비활성화하거나 변경하면 캐시가 재설정되고 모든 양식 및 문서가 캐시에서 제거됩니다.

#### Acrobat Sign 구성 {#configure-adobe-sign}

Acrobat Sign을 사용하면 적응형 양식에 전자 서명 워크플로우를 사용할 수 있습니다. 전자 서명은 법무, 판매, 임금, 인적 자원 관리 등의 다양한 분야에서 문서를 처리하는 워크플로를 개선합니다.

OSGi 시나리오의 일반적인 Acrobat Sign 및 Forms 중심의 워크플로우에서 사용자는 적응형 양식을 작성하여 서비스에 적용합니다. 신용 카드 신청 양식과 시민 혜택 양식을 예로 들 수 있습니다. 사용자가 애플리케이션 양식을 작성, 제출 및 서명하면 승인/거부 워크플로우가 시작됩니다. 서비스 제공업체는 AEM 받은 편지함에서 애플리케이션을 검토하고 Acrobat Sign을 사용하여 애플리케이션에 전자적으로 서명합니다. 유사한 전자 서명 워크플로우를 활성화하기 위해 Acrobat Sign을 AEM Forms과 통합할 수 있습니다.

AEM Forms과 함께 Acrobat Sign을 사용하려면, [Acrobat Sign과 AEM Forms 통합](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

## 다음 단계 {#next-steps}

OSGi 기능에서 Forms 중심의 워크플로우를 사용할 환경을 구성했습니다. 이제 기능을 사용하기 위한 단계는 다음과 같습니다.

* [OSGi에서 Forms 중심의 워크플로우 사용](/help/forms/using/aem-forms-workflow.md)
* [워크플로 단계 참조](/help/sites-developing/workflows-step-ref.md)
* [편지 및 대화형 커뮤니케이션의 사후 처리](/help/forms/using/submit-letter-topostprocess.md)
