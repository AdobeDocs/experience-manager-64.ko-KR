---
title: AEM Forms 참조 사이트 설정 및 구성
seo-title: Set up and configure AEM Forms reference sites
description: AEM Forms 참조 사이트에서는 AEM Forms을 사용하여 조직에서 종단 간 워크플로우를 구현하는 방법을 소개합니다.
seo-description: AEM Forms reference sites showcase how you can use AEM Forms to implement end-to-end workflow in an organization.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '2911'
ht-degree: 2%

---

# AEM Forms 참조 사이트 설정 및 구성 {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms은 AEM Forms이 금융 서비스 업계 및 정부 기관에서 복잡한 트랜잭션을 언제 어디서나 간편하고 매력적인 디지털 경험으로 변환하는 데 어떻게 도움이 되는지를 보여 주는 참조 사이트 구현을 제공합니다.

We.Finance 및 We.Gov 참조 사이트에서는 기존 및 잠재 고객과 교류하기 위한 실제 사용 사례를 도출하여 첫 번째 터치 시점부터 개인화되고 비용 효율적인 방식으로 서신 및 거래 관리에 이르기까지,

참조 사이트를 통해 AEM Forms의 다음과 같은 주요 기능을 살펴보고 소개하는 데 도움이 됩니다.

* 매력적인 반응형 적응형 양식 및 대화형 커뮤니케이션의 작성 환경이 간소화되었습니다.
* 인터랙티브한 커뮤니케이션을 통해 장치 설정 및 레이아웃에 맞는 인터랙티브하고 개인화된 반응형 고객 커뮤니케이션을 만들 수 있습니다.
* 서로 다른 데이터 소스에 연결하여 양식 데이터 모델을 통해 양식 데이터를 미리 작성하고 제출할 수 있는 데이터 통합.
* 비즈니스 프로세스 및 워크플로우를 자동화하는 Forms 워크플로우
* 고급 사용자 데이터 관리 및 처리 기능.
* Adobe Sign과 통합하여 적응형 양식에 안전하게 서명하고 제출할 수 있습니다.
* Adobe Target과 통합하여 타깃팅된 추천을 제공하고 A/B 테스트를 수행하여 양식에서 ROI를 극대화할 수 있습니다.
* Adobe Analytics과 통합하여 양식 또는 캠페인의 성과를 측정하고 현명한 결정을 내릴 수 있습니다.
* 향상된 양식 채우기 경험.

참조 사이트는 템플릿으로 사용하여 고유한 자산을 만들 수 있는 재사용 가능한 자산을 제공합니다.

* Adobe Sign과 통합하여 적응형 양식에 안전하게 서명하고 제출할 수 있습니다.

* Adobe Sign과 통합하여 적응형 양식에 안전하게 서명하고 제출할 수 있습니다.

## 참조 사이트를 설정하는 사전 요구 사항 및 단계입니다 {#prerequisites-and-steps-to-set-up-reference-sites}

참조 사이트를 설정하기 전에 다음 사항이 있는지 확인하십시오.

* **AEM Essentials**

   AEM QuickStart, AEM Forms 추가 기능 패키지 및 참조 사이트 패키지. 추가 기능 및 참조 사이트 패키지 세부 정보는 [AEM Forms 릴리스](https://helpx.adobe.com/kr/aem-forms/kb/aem-forms-releases.html) 를 참조하십시오.

* **SMTP**
서비스모든 SMTP 서비스를 사용할 수 있습니다.

* **Adobe Sign 개발자 계정 및 Adobe Sign API 애플리케이션**

   디지털 서명 기능을 사용하려면 Adobe Sign 개발자 계정이 필요합니다. [Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)을 참조하십시오.

* AEM Forms과 통합하기 위해 실행 중인 Microsoft Dynamics 365 인스턴스입니다. 참조 사이트를 실행하려면 샘플 데이터를 Microsoft Dynamics 인스턴스로 가져와서 참조 사이트에서 사용되는 대화형 커뮤니케이션을 미리 채웁니다.
* Forms 추가 기능 패키지가 있는 AEM 6.4의 실행 중인 인스턴스. 자세한 내용은 [AEM Forms 설치 및 구성](installing-configuring-aem-forms-osgi.md)을 참조하십시오.

권장 시퀀스에서 다음 단계를 수행하여 참조 사이트를 설정하고 구성합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>단계</strong></th> 
   <th><strong>구성</strong></th> 
   <th><strong>메모</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">AEM Forms 설치 및 구성</a></td> 
   <td>작성자 및 게시</td> 
   <td>AEM Forms 작성자 및 게시 인스턴스를 설치하고 구성합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">SSL 구성</a></td> 
   <td>작성자 및 게시<br /> </td> 
   <td>Adobe Sign과의 보안 통신을 위해 SSL을 통해 HTTP를 활성화합니다.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">일 CQ Link Externalizer 구성 구성 구성</a></p> </td> 
   <td>작성자 및 게시<br /> </td> 
   <td><p>참조 사이트 사용 사례에서는 다양한 트랜잭션에 대한 이메일을 제공합니다. 이 설정은 이메일을 통한 뉴스레터 게재에 필요합니다. URL 및 이미지가 게시 인스턴스를 가리키도록 합니다. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">일 CQ 메일 서비스 구성</a></td> 
   <td>작성자 및 게시</td> 
   <td>이메일 통신에 필요합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">기본 XSS 구성 무시</a></td> 
   <td>게시</td> 
   <td>xss 보안에 의해 차단된 $, { 및 } 문자를 무시하는 데 사용됩니다.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">AEM DS 설정 구성</a></td> 
   <td>작성</td> 
   <td>게시 인스턴스에서 양식 제출 및 작성자 인스턴스의 처리 워크플로우에 대한 AEM DS를 구성합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">참조 사이트 패키지 배포</a></td> 
   <td>작성</td> 
   <td>AEM Forms 작성자 인스턴스에 참조 사이트 패키지를 배포합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">샘플 데이터를 Microsoft Dynamics로 가져오기</a></td> 
   <td>작성자 및 게시</td> 
   <td>신용 카드 신청, 주택 담보 대출 신청 및 주택 보험 신청 연습에 대한 샘플 데이터 가져오기</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Microsoft Dynamics용 OAuth 클라우드 서비스 구성</a></td> 
   <td>작성자 및 게시</td> 
   <td>AEM Forms과 Microsoft Dynamics 간의 통신을 사용하도록 AEM Forms에서 OAuth 클라우드 서비스를 구성합니다. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Adobe Sign 스케줄러 구성</a></td> 
   <td>작성자 및 게시<br /> </td> 
   <td>2분마다 상태를 확인하도록 스케줄러 구성을 변경합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">참조 사이트 Adobe Sign Cloud Service 구성</a></td> 
   <td>작성자 및 게시<br /> </td> 
   <td>참조 사이트 패키지와 함께 제공되는 구성이며 유효한 자격 증명으로 재구성해야 합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">익명 사용자에 대한 Forms 일반 구성 서비스 구성</a></td> 
   <td>게시</td> 
   <td>이 구성에서는 익명 사용자에 대해 레코드 제출, 서명 및 문서를 생성할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">양식 데이터 모델의 Rest 서비스 Swagger 파일 수정</a></td> 
   <td>작성자 및 게시<br /> </td> 
   <td>환경에 대한 서비스를 수정합니다.</td> 
  </tr> 
 </tbody> 
</table>

## AEM Forms 설치 및 구성 {#install-and-configure-aem-forms}

[OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md)에 설명된 대로 AEM Forms을 설치하고 배포합니다.

>[!NOTE]
>
>다른 시스템에 둘 이상의 게시 인스턴스 또는 작성자 및 게시 인스턴스가 있는 경우 복제 및 역방향 복제 에이전트를 구성합니다.

## SSL 구성 {#ssl}

Adobe Sign 서버와 통신하려면 SSL 구성이 필요합니다. 자세한 단계는 [SSL을 통해 HTTP 활성화](/help/sites-administering/ssl-by-default.md)를 참조하십시오.

>[!CAUTION]
>
>`/etc/map` 폴더에 강제 SSL을 구성하지 마십시오.

## 일 CQ Link Externalizer 구성 구성 구성 {#externalizer}

AEM에서 **Externalizer**&#x200B;는 사전 구성된 DNS로 경로를 접두사로 사용하여 리소스 경로(예: /path/to/my/page)를 프로그래밍 방식으로 외부 및 절대 URL(예: https://www.mycompany.com/path/to/my/page)으로 변환할 수 있는 OSGI 서비스입니다. [URL 표면화](/help/sites-developing/externalizer.md)를 참조하십시오.

>[!CAUTION]
>
>SSL에 자체 서명된 인증서를 사용하는 경우 HTTPS URL을 외부화하지 마십시오.
>
>또한 로컬 서버의 호스트 이름 대신 localhost를 사용하십시오.

작성자 및 게시 인스턴스 모두에서 다음 단계를 수행하십시오.

1. https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr의 OSGi 구성으로 이동합니다.
1. **[!UICONTROL Day CQ Link Externalizer]** 구성을 찾아 탭합니다.

   Day CQ Link Externalizer 대화 상자가 열려 구성을 편집합니다.

1. 일 CQ Link Externalizer 대화 상자의 도메인 필드에서

   * 작성자 인스턴스에서 외부 시스템에서 액세스할 수 있는 게시 URL을 지정합니다. 예를 들어 호스트 이름 또는 게시 웹 서버가 있습니다.
   * 게시 인스턴스에서 작성자 및 게시 URL을 모두 지정합니다.

1. 작성자와 게시 인스턴스 모두에서 로컬 서버 URL이 도메인 필드에 지정되어 있는지 확인합니다.
1. **[!UICONTROL 저장]**&#x200B;을 누릅니다. 모든 서비스가 다시 시작될 때까지 잠시 기다립니다.

## 일 CQ 메일 서비스 구성 {#cqmail}

참조 사이트 구현에서는 양식을 작성하고 제출할 때 샘플 사용자에게 이메일을 보내야 합니다. Day CQ Mail Service를 구성하면 자동화된 이메일을 고객에게 보낼 SMTP 서비스 세부 사항을 제공할 수 있습니다. [이메일 알림 구성](/help/sites-administering/notification.md)을 참조하십시오.

게시 인스턴스에서 메일 서비스를 구성하려면 다음 단계를 수행하십시오.

1. https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr의 OSGi 구성으로 이동합니다.
1. **[!UICONTROL Day CQ Mail Service]**&#x200B;를 찾아 탭하여 구성할 수 있도록 엽니다.
1. SMTP 서버 호스트 이름 및 포트 값을 제공합니다.
1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

>[!NOTE]
>
>회사 SMTP 서비스나 Gmail과 같은 공용 서비스를 사용할 수 있습니다. SMTP 서비스 구성에 대해서는 SMTP 서비스 설명서를 참조하십시오.

## 기본 XSS 구성 무시 {#xss}

We.Finance 참조 사이트에 대한 이메일 템플릿에는 이메일에 개인화된 링크가 포함되어 있습니다. 이러한 링크에는 자리 표시자가 `${placeholder}`입니다. 이러한 자리 표시자는 이메일을 보내기 전에 실제 값으로 대체됩니다. AEM에 대한 기본 XSS 보호 구성에서는 HTML 콘텐츠의 URL에서 중괄호(**{ }**)를 허용하지 않습니다. 그러나 게시 인스턴스에서 다음 단계를 수행하여 기본 구성을 재정의할 수 있습니다.

1. `/libs/cq/xssprotection/config.xml`을 `/apps/cq/xssprotection/config.xml`에 복사합니다.
1. 열기 `/apps/cq/xssprotection/config.xml`.
1. `common-regexps` 섹션에서 `onsiteURL` 항목을 다음과 같이 수정하고 파일을 저장합니다.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>중괄호(**{ }**)는 HTML 콘텐츠의 URL에서 허용되는 문자로 포함됩니다.

SMTP 서버를 구성한 후 Sarah Rose 가상 사용자를 사용하여 양식을 작성하고 초안으로 저장해 보십시오. 초안으로 저장하면 이메일을 사용하여 초안을 받을 수 있는 옵션이 제공됩니다. **이메일 보내기** 단추를 탭할 때 응용 프로그램 초안으로 연결되는 링크가 있는 이메일을 받으면 이메일 구성이 성공했습니다. 초안을 보려면 Sarah의 자격 증명을 사용하여 로그인해야 합니다.

## AEM DS 설정 구성 {#aemds}

참조 사이트 사용 사례에서 전자 메일 통신을 위해 게시 인스턴스에 AEM DS 서비스 설정이 필요합니다. 게시 인스턴스에서 AEM DS 서비스 설정을 구성하는 자세한 단계는 [AEM DS 설정 구성](/help/forms/using/configuring-the-processing-server-url-.md)을 참조하십시오.

AEM Forms 참조 사이트의 경우 AEM DS 설정 서비스에서 처리 서버의 URL 대신 게시 서버의 URL을 지정합니다.

>[!CAUTION]
>
>AEM Forms OSGi에 대해 를 구성하는 경우 처리 서버 URL에 `/lc`을 추가하지 마십시오.

## 참조 사이트 패키지 배포 {#refsite}

소프트웨어 배포를 사용하여 다음 참조 사이트 패키지를 설치합니다.

* [AEM-FORMS.-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS.6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

패키지 사용 방법에 대한 자세한 내용은 [패키지 사용 방법](/help/sites-administering/package-manager.md)을 참조하십시오.

패키지를 설치하고 작성자 및 게시 인스턴스를 시작했으면 브라우저의 다음 URL을 참조하십시오.

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

설치가 성공하면 We.Gov 및 We.Finance 참조 사이트 랜딩 페이지에 액세스할 수 있습니다.

## (선택 사항) 샘플 데이터를 Microsoft Dynamics로 가져옵니다 {#optional-import-sample-data-into-microsoft-dynamics}

홈 모기지 응용 프로그램 및 자동 보험 응용 프로그램 참조 사이트는 Microsoft Dynamics의 레코드를 사용하도록 구성되어 있습니다. 참조 사이트 패키지는 참조 사이트를 실행하기 위해 Microsoft Dynamics에 가져올 수 있는 사용자 지정 엔터티 및 샘플 레코드를 설치합니다. 다음 단계를 수행하여 샘플 데이터를 마이그레이션하고 설정합니다.

자동 보험 적용을 위한 사용자 정의 엔티티를 가져오려면 다음을 수행하십시오.

1. AEM 작성자 인스턴스의 `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip`WeFinanceAutoInsurance_1_0.zip **솔루션 패키지를 다운로드합니다.**
1. Microsoft Dynamics 인스턴스에서 **[!UICONTROL 설정]** 메뉴의 **[!UICONTROL 솔루션]**&#x200B;으로 이동한 다음 **[!UICONTROL 가져오기]**&#x200B;를 클릭합니다. 패키지를 선택하고 가져옵니다.

자동 보험 적용을 위한 사용자 정의 엔티티를 가져오려면 다음을 수행하십시오.

1. https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip에서 **AEMFormsFSIRefsite_1_0.zip** 패키지를 다운로드합니다. 패키지를 선택하고 가져옵니다.

1. Microsoft Dynamics 인스턴스에서 **[!UICONTROL 설정]** 메뉴의 **[!UICONTROL 솔루션]**&#x200B;으로 이동한 다음 **[!UICONTROL 가져오기]**&#x200B;를 클릭합니다. 패키지를 선택하고 가져옵니다.

고객 및 보험 정책 레코드를 임포트하려면

1. AEM 작성자 인스턴스의 다음 위치에서 **We.Finance Customers.csv, We.Finance 자동 보험 갱신.csv** 및 **홈 모기지** 데이터 파일을 다운로드합니다.

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Microsoft Dynamics 인스턴스에서 다음을 수행합니다.

   * **[!UICONTROL Sales > We.Finance 고객]**&#x200B;으로 이동하여 **[!UICONTROL 가져오기]**&#x200B;를 클릭합니다.
   * **[!UICONTROL Sales > We.Finance 자동 보험]**&#x200B;으로 이동하여 **[!UICONTROL 가져오기]**&#x200B;를 클릭합니다.
   * **[!UICONTROL Sales > We.Finance Home Moderation]**&#x200B;로 이동하여 **[!UICONTROL Import]**&#x200B;를 클릭합니다.

## Microsoft Dynamics용 OAuth 클라우드 서비스 구성 {#configure-oauth-cloud-service-for-microsoft-dynamics}

AEM Forms과 Microsoft Dynamics 간의 통신을 사용하도록 AEM Forms에서 OAuth 클라우드 서비스를 구성합니다. AEM 작성자 및 게시 인스턴스에서 OAuth Cloud Service을 구성하려면 다음 단계를 수행합니다.

1. AEM 작성자 인스턴스에서 **[!UICONTROL 도구 > Cloud Services > Data Sources > global]**&#x200B;로 이동합니다. **[!UICONTROL Refsite Dynamics 통합]** 아이콘을 탭하고 **[!UICONTROL 속성]**&#x200B;을 탭합니다.
1. Microsoft Azure Active Directory 계정으로 이동합니다. 등록된 애플리케이션의 **[!UICONTROL 회신 URL]** 설정에 복사된 클라우드 서비스 구성 URL을 추가합니다. 구성을 저장합니다.
1. 인증 설정 탭에서 Microsoft Dynamics 인스턴스에 대해 **[!UICONTROL 서비스 루트]**, **[!UICONTROL 클라이언트 Id]**, **[!UICONTROL 클라이언트 암호]** 및 **[!UICONTROL 리소스 URL]**&#x200B;을 지정합니다. Microsoft Dynamics 로그인 페이지로 리디렉션하는 **[!UICONTROL OAuth]**&#x200B;연결을 클릭합니다.
1. 로그인 자격 증명을 제공합니다. 로그인하면 AEM Forms 클라우드 서비스 구성 페이지로 리디렉션됩니다. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 클라우드 서비스 구성이 저장됩니다.
1. **[!UICONTROL Forms > 데이터 통합 > We.Finance]**&#x200B;로 이동합니다. 자동 보험(Dynamics)을 선택하고 편집을 클릭합니다. Microsoft Dynamics 엔티티는 데이터 소스 탭 아래에 나열됩니다. 모든 엔터티를 Microsoft Dynamics에서 가져오고 데이터 소스 탭 아래에 나열할 때까지 기다립니다.
1. **[!UICONTROL AutoInsuranceRenewal 엔티티]**&#x200B;를 선택하고 **[!UICONTROL 테스트 모델 개체]**&#x200B;를 클릭합니다. 입력 요청 섹션에서 고객 ID에 대한 값을 &quot;900001&quot;으로 지정하고 **[!UICONTROL 테스트]**&#x200B;를 클릭합니다. 출력 섹션에는 고객 ID 900001에 대해 Microsoft Dynamics에서 가져온 레코드가 표시됩니다.
1. 입력 요청 섹션에서 고객 ID에 대한 값을 &quot;900001&quot;으로 지정하고 **[!UICONTROL 테스트]**&#x200B;를 클릭합니다. 출력 섹션에는 고객 ID 900001에 대해 Microsoft Dynamics에서 가져온 레코드가 표시됩니다.
1. 게시 인스턴스에서 1-6단계를 반복합니다.

## Adobe Sign 스케줄러 구성 {#scheduler}

작성자 및 게시 인스턴스 둘 다에서 다음을 수행합니다.

1. `https://[server]:[host]/system/console/configMgr`의 AEM 웹 구성 콘솔로 이동합니다.
1. **[!UICONTROL Adobe Sign 구성 서비스]**&#x200B;를 찾아 탭하여 구성용으로 엽니다.
1. **[!UICONTROL 상태 업데이트 스케줄러 표현식]**&#x200B;을 **0/2 &amp;ast;로 구성합니다. amp;ast; amp;ast; ?**

   >[!NOTE]
   >
   >위의 스케줄러 구성은 2분마다 Adobe Sign 서비스의 상태를 확인합니다.

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

## 참조 사이트 Adobe Sign 클라우드 서비스 구성 {#sign-service}

작성자 및 게시 인스턴스 둘 다에서 다음을 수행합니다.

1. **[!UICONTROL 도구 > Cloud Services > Adobe Sign > global]**&#x200B;로 이동합니다. **[!UICONTROL AEM Forms 참조 사이트 기호]**&#x200B;를 선택하고 **[!UICONTROL 속성]**&#x200B;을 탭합니다.

   >[!CAUTION]
   >
   >https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html URL이 Adobe Sign API 애플리케이션의 리디렉션 URL 목록에 추가되는지 확인합니다.

1. Adobe Sign 애플리케이션 OAuth 구성의 클라이언트 ID와 암호를 지정합니다.
1. (선택 사항) **[!UICONTROL Adobe Sign for attachments도 활성화]** 옵션을 선택하고 **[!UICONTROL Adobe Sign에 연결]**&#x200B;을 탭합니다. 적응형 양식에 첨부된 파일을 서명을 위해 전송된 해당 Adobe Sign 문서에 추가합니다.
1. **[!UICONTROL Adobe Sign에 연결]**&#x200B;을 탭하고 Adobe Sign 자격 증명으로 로그인합니다.

## Forms 일반 구성 서비스 구성 {#anonymous}

익명 사용자에 대한 액세스를 허용하려면 게시 인스턴스에서 다음을 수행합니다.

1. `https://[server]:[port]/system/console/configMgr`의 AEM 웹 구성 콘솔로 이동합니다.
1. **[!UICONTROL Forms Common Configuration Service]**&#x200B;를 찾아 탭하여 구성용으로 엽니다.
1. **[!UICONTROL 모든 사용자]**&#x200B;에 대한 **[!UICONTROL Allow]** 필드를 구성합니다.
1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

## 양식 데이터 모델에 대한 Rest 서비스 수정 {#fdm}

작성자 및 게시 인스턴스 둘 다에서 다음을 수행합니다.

1. `https://[server]:[port]/crx/de/index.jsp`에 있는 CRXDE로 이동합니다.
1. **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** 로 이동하여 swagger 파일을 엽니다.
1. 환경에 따라 호스트 및 포트 설정을 업데이트합니다.
1. 설정을 저장합니다.
1. (**작성자 인스턴스만**) **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL 데이터 소스]** > **[!UICONTROL 전역]**&#x200B;로 이동합니다. **[!UICONTROL roi-rest]**&#x200B;를 선택하고 **[!UICONTROL 속성]**&#x200B;을 탭합니다. **[!UICONTROL 인증 설정]**&#x200B;을 탭하고 **[!UICONTROL 인증 유형]**&#x200B;기본 인증&#x200B;]**으로 설정합니다.**[!UICONTROL  서비스에 액세스할 사용자 이름/암호로 `admin`/ `admin`을 지정합니다. **[!UICONTROL 저장 및 닫기]**&#x200B;를 누릅니다.

## Marketing Cloud과 통합 {#integrate-with-marketing-cloud}

AEM Forms을 Adobe Analytics 및 Adobe Target과 통합할 수 있습니다. Adobe Analytics을 사용하면 보고서를 생성하고 적응형 양식의 성능을 분석할 수 있지만 Adobe Target은 개인화된 경험을 제공하고 적응형 양식에 대해 A/B 테스트를 수행하는 데 도움이 됩니다.

AEM Forms에서 Adobe Analytics 및 Adobe Target을 구성하려면 다음을 수행하십시오.

### Adobe Analytics 구성 {#configure-adobe-analytics}

AEM Forms과 Adobe Analytics 통합을 통해 고객이 양식 및 문서와 상호 작용하는 방법을 모니터링하고 분석할 수 있습니다. 문제 영역을 식별하고 수정하고 전환율을 높이는 데 도움이 됩니다.

참조 사이트에서 이 기능을 경험하려면 [분석 및 보고서 구성](/help/forms/using/configure-analytics-forms-documents.md)에 설명된 대로 Analytics 계정을 구성합니다.

보고서를 생성하기 위해 시드 데이터는 참조 사이트와 번들로 제공됩니다. 시드 데이터를 사용하기 전에 다음을 수행하십시오.

1. AEM 클라우드 서비스에서 We.Finance 및 We.Gov 분석 구성을 사용할 수 있는지 확인합니다. 다음 방법 중 하나로 클라우드 서비스를 찾을 수 있습니다.

   * **[!UICONTROL Cloud Services>기존 Cloud Services]**&#x200B;로 이동하거나 https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html으로 이동합니다.
   * **[!UICONTROL Cloud Services]** 페이지의 **[!UICONTROL Adobe Analytics]** 섹션에서 `Show Configurations`를 클릭합니다. We.Finance 및 We.Gov 구성을 사용할 수 있습니다. 구성을 열려면 를 클릭합니다. 구성 페이지에서 **[!UICONTROL 편집]**&#x200B;을 클릭합니다. 유효한 회사, 사용자 이름, 공유 암호(암호) 및 데이터 센터를 제공하고 **[!UICONTROL Analytics에 연결]**&#x200B;을 클릭합니다. 연결 성공 대화 상자가 표시되면 구성 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 클릭합니다. [Analytics 및 Reports 구성](/help/forms/using/configure-analytics-forms-documents.md)에 설명된 대로 Analytics 구성에서 프레임워크를 구성합니다.

1. https://&lt;*host*:&lt;*port*/system/console/configMgr 로 이동하여 다음을 수행합니다.

   * **[!UICONTROL 웹 콘솔 구성]** 페이지에서 **[!UICONTROL AEM Forms Analytics 구성]**&#x200B;을(를) 찾아 클릭합니다.
   * AEM Forms Analytics 구성 대화 상자의 **[!UICONTROL SiteCatalyst 프레임워크]** 필드에서 we-finance(we-finance) 또는 we-gov(we-gov)를 선택합니다.
   * **[!UICONTROL 저장]**&#x200B;을 클릭하고 페이지를 새로 고치도록 하십시오.

1. https://&lt;host>:&lt;port>/aem/forms에서 양식 관리자로 이동하여 다음을 수행합니다.

   * We.Finance 또는 We.Gov 폴더를 열고 보고서를 볼 양식을 선택합니다.
   * 작업 도구 모음에서 Analytics 활성화 를 클릭합니다. 양식에 대한 분석 기능을 활성화한 후 Analytics 보고서 를 클릭합니다. 빈 보고서가 생성되는 것을 볼 수 있습니다. 빈 보고서가 생성된 후에는 데모 목적으로 분석 보고서를 생성하려면 참조 사이트 패키지와 함께 제공된 시드 데이터를 제공해야 합니다.

   참조 사이트는 신용 카드, 주택 담보 및 아동 지원 사용 사례에 대한 시드 데이터를 분석 보고에 제공합니다. 시드 데이터 구성은 [We.Finance 참조 사이트 안내](/help/forms/using/finance-reference-site-walkthrough.md) 및 [We.Gov 참조 사이트 안내](/help/forms/using/gov-reference-site-walkthrough.md)를 참조하십시오.

### Target 구성 {#configure-target}

참조 사이트에서는 적응형 문서에 타깃팅되고 개인화된 컨텐츠를 포함할 수 있는 Adobe Target과 AEM Forms의 통합을 소개합니다. 또한 적응형 양식에 대한 A/B 테스트를 만들 수도 있습니다.

참조 사이트에서 통합을 경험하려면 다음을 수행하여 AEM에서 Target을 구성합니다.

1. 서버에서 A/B 테스트를 활성화하려면 jvm 인수 `-Dabtesting.enabled=true`으로 작성자 빠른 시작을 시작합니다.

   **참고**: 턴키 설치에서 서비스로 시작된 JBoss에서 AEM 인스턴스가 실행 중인 경우, 파일의 다음 항목 `-Dabtesting.enabled=true` 에 매개 변수를  `jboss\bin\standalone.conf.bat` 추가합니다.

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. https://&lt;*hostname*:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html에 액세스합니다.

1. **[!UICONTROL Adobe Target]** 섹션에서 **[!UICONTROL 구성 표시]**&#x200B;를 클릭합니다. 사용 가능한 We.Finance Target 구성을 볼 수 있습니다. 구성을 열려면 를 클릭합니다. 구성 페이지에서 **[!UICONTROL 편집]**&#x200B;을 클릭합니다. 구성에 대한 **[!UICONTROL 구성 요소 편집]** 대화 상자가 열립니다.

1. Target 계정과 연결된 클라이언트 코드, 이메일 및 암호를 지정합니다. API 유형을 **[!UICONTROL REST]**&#x200B;로 선택합니다.
1. **[!UICONTROL Adobe 대상에 연결]**&#x200B;을 클릭합니다. Target 계정이 성공적으로 구성되면 **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 패키지된 구성에 Target 프레임워크이 있음을 확인할 수 있습니다.

1. https://&lt;*hostname*>:&lt;*port*/system/console/configMgr 로 이동합니다.

1. **[!UICONTROL AEM Forms Target 구성]**&#x200B;을 클릭합니다.
1. Target 프레임워크을 선택합니다.
1. **[!UICONTROL Target URL]** 필드에서 AEM Forms에 대한 URL을 지정합니다. 예: https://&lt;*hostname*:&lt;*port*>.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

신용 카드 애플리케이션 및 주택 담보 대출 신청 사용 사례는 A/B 테스트를 수행하고 데모 목적으로 보고서를 소개하는 방법을 보여줍니다. 연습은 [We.Finance 참조 사이트 안내](/help/forms/using/finance-reference-site-walkthrough.md)를 참조하십시오.

## 다음 단계 {#next-step}

이제 모두 참조 사이트를 탐색하도록 설정되어 있습니다. 참조 사이트 워크플로우 및 단계에 대한 자세한 내용은 다음을 참조하십시오.

* [We.Finance 참조 사이트 안내](/help/forms/using/finance-reference-site-walkthrough.md)
* [We.Gov 참조 사이트 안내](/help/forms/using/gov-reference-site-walkthrough.md)

* [직원 셀프 서비스 참조 사이트 안내](/help/forms/using/employee-self-service-reference-site.md)
