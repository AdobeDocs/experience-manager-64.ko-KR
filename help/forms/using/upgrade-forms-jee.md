---
title: AEM 6.4 Forms로 업그레이드
seo-title: AEM 6.4 Forms로 업그레이드
description: 'AEM 6.1 Forms, AEM 6.2 Forms 및 LiveCycle ES4 SP1에서 AEM 6.3 Forms으로 직접 업그레이드할 수 있습니다. '
seo-description: 'AEM 6.1 Forms, AEM 6.2 Forms 및 LiveCycle ES4 SP1에서 AEM 6.3 Forms으로 직접 업그레이드할 수 있습니다. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---

# JEE의 AEM 6.4 Forms으로 업그레이드 {#upgrade-to-aem-forms-jee}

환경에 적합한 다음 업그레이드 경로 중 하나를 사용하십시오.

## JEE의 AEM 6.2 Forms 또는 JEE의 AEM 6.3 Forms > JEE의 AEM 6.4 Forms {#aem-forms-jee-62-63-to-64}

JEE의 기존 AEM 6.2 Forms 또는 JEE의 AEM 6.3 Forms을 JEE의 AEM 6.4 Forms으로 업그레이드하려면 다음 절차를 수행하십시오.

1. [Adobe 라이선스 웹 사이트(LWS)](https://licensing.adobe.com/)에서 JEE의 AEM 6.4 Forms 설치 프로그램을 다운로드합니다. 설치 관리자를 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
1. 성공적인 업그레이드를 위해 수행할 검사에 대해 알려면 [업그레이드 체크리스트 및 planning](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63)을 참조하십시오.
1. 서버 가동 중지 시간을 최소화하면서 업그레이드가 올바르게 실행되도록 하는 작업을 배우고 수행하려면 [AEM Forms으로 업그레이드 준비](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63)를 참조하십시오.
1. 기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 지침을 따릅니다.

   * [AEM 6.2 또는 AEM 6.3 Forms에서 JBoss용 AEM 6.4 Forms으로 업그레이드](assets/upgrade-jboss.pdf)
   * [AEM 6.2 또는 AEM 6.3 Forms에서 WebLogic용 AEM 6.4 Forms으로 업그레이드](assets/upgrade-weblogic.pdf)
   * [AEM 6.2 또는 AEM 6.3 Forms에서 WebSphere용 AEM 6.4 Forms으로 업그레이드](assets/upgrade-websphere.pdf)
   * [AEM 6.2 또는 AEM 6.3 Forms에서 JBoss 턴키용 AEM 6.4 Forms으로 업그레이드](assets/upgrade-turnkey.pdf)

## JEE의 AEM 6.0 Forms > JEE의 AEM 6.3 Forms {#aem-forms-jee-60-to-63}

AEM 6.0 Forms, AEM 6.1 Forms에서 AEM 6.4 Forms으로 직접 업그레이드할 수 없습니다. 하나 이상의 LiveCycle 또는 AEM Forms 버전으로 중간 업그레이드를 수행한 다음, AEM 6.4 Forms에서 업그레이드할 수 있습니다. 중간 버전 및 해당 업그레이드 지침 목록은 [업그레이드 경로 선택](upgrade.md)을 참조하십시오.

## LiveCycle ES4 SP1 > JEE의 AEM 6.4 Forms {#livecycle-es4sp1-forms-jee}

LiveCycle ES4 SP1을 JEE의 AEM 6.4 Forms으로 업그레이드하면 이전 버전에서 지원되는 애플리케이션 서버, 운영 체제 및 데이터베이스의 새로운 인스턴스(새 버전)로 자산 및 데이터를 마이그레이션해야 하므로 즉시 업그레이드할 수 있습니다.

다음은 기존 LiveCycle ES4 SP1 서버를 AEM 6.4 Forms으로 업그레이드하는 절차에 대한 개요입니다. 자세한 지침은 절차 끝에 나열된 문서를 참조하십시오.

1. 업그레이드하기 전에:

   1. [Adobe 라이선스 웹 사이트(LWS)](https://licensing.adobe.com/)에서 JEE의 AEM 6.4 Forms 설치 프로그램을 다운로드합니다. 설치 관리자를 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
   1. 사용할 컨텐츠 저장소(CRX 저장소) 유형을 결정합니다. JEE의 일부 AEM Forms 기능만 컨텐츠 저장소 지속성 을 사용하여 컨텐츠 및 자산을 저장합니다. JEE 기능에서 이러한 AEM Forms을 사용하려는 경우에만 컨텐츠 저장소를 설치 및 구성합니다.

      * LiveCycle ES4 SP1에서는 서신 관리, Forms 포털, HTML 작업 공간 및 프로세스 보고 기능이 컨텐츠 저장소를 사용합니다. LiveCycle ES4에서 이러한 기능을 사용하지 않았고 AEM Forms에서 이러한 기능을 사용하지 않을 계획이라면 Content Repository가 필요하지 않습니다.
      * AEM Forms, 적응형 Forms, 서신 관리, HTML5 Forms(LiveCycle ES4 SP1의 모바일 Forms으로 알려짐), Forms Portal, HTML Workspace, 프로세스 보고, OSGi의 Forms 중심 워크플로우는 컨텐츠 저장소를 사용합니다. 이러한 기능에 AEM Forms을 사용하려는 경우 컨텐츠 저장소가 필요합니다.
      * AEM Forms Document Security에 대한 컨텐츠 리포지토리는 필요하지 않습니다.

      또한 LiveCycle 및 AEM Forms의 저장소 유형이 다릅니다. 사용 가능한 저장소 유형 및 관련 정보는 [AEM Forms 설치](/help/forms/using/choosing-persistence-type-for-aem-forms.md)에 대한 지속성 유형 선택을 참조하십시오.

   1. LiveCycle ES4 SP1 컨텐츠 및 데이터의 백업을 만듭니다.

      LiveCycle ES4 SP1 데이터베이스, GDS(Global Data Storage) 및 crx 저장소 백업을 만듭니다(문서 보안에는 필요 없음). MongoMK 또는 RDBMK 지속성으로 업그레이드하는 경우, .cmp 파일에서 LiveCycle ES4 SP1 서신 관리 자산을 내보내고 Forms 자산을 AEM 패키지로 내보냅니다.

   1. 기존 플랫폼(예: 애플리케이션 서버, 데이터베이스, 운영 체제, Adobe Acrobat, 타사 애플리케이션 및 하드웨어)이 JEE의 AEM 6.4 Forms에 대해 지원되는지 확인합니다. 지원되는 하드웨어 및 소프트웨어에 대한 자세한 내용은 [지원되는 플랫폼 조합](/help/forms/using/aem-forms-jee-supported-platforms.md) 문서를 참조하십시오.

      데이터베이스의 새 인스턴스를 만들면 3단계에서 백업된 데이터를 데이터베이스로 가져옵니다. 데이터를 데이터베이스로 가져오는 방법에 대한 자세한 내용은 해당 데이터베이스 공급업체의 설명서를 참조하십시오.

      >[!NOTE]
      >
      >RDBMK 지속성 형식을 사용하는 경우, JEE에서 AEM Forms에서 실행되는 저장소 지속성 및 문서 서비스 모두에 단일 데이터베이스를 사용합니다.


1. 업그레이드를 수행합니다.

   1. 설치 프로그램을 실행하여 새 서버에 AEM 6.4 Forms을 JEE에 설치합니다. 설치 관리자는 필요한 모든 파일을 하나의 설치 디렉터리 구조 내에 컴퓨터에 저장합니다.
   1. 설치가 완료되면 **구성 관리자**&#x200B;를 실행하여 다양한 AEM Forms 모듈을 구성하고 적절한 구성을 설정합니다. 구성 설정과 함께 GDS(글로벌 데이터 저장소) 및 crx 저장소의 경로를 지정할 수 있습니다.

      >[!NOTE]
      >
      >업그레이드 작업 선택 화면에서 **[!UICONTROL Adobe Experience Manager Forms 6.2.0에서 업그레이드]** 옵션을 선택합니다. **[!UICONTROL Adobe Experience Manager Forms 6.2.0에서 업그레이드]** 옵션을 사용하면 구성 관리자가 LiveCycle ES4 SP1에서 AEM 6.4 Forms으로 업그레이드할 수 있습니다.

   1. (AEM Forms 문서 보안 모듈에 필요하지 않음) 컨텐츠를 컨텐츠 저장소(CRX-Repository)에 AEM 6.4 Forms 서버로 가져옵니다.

      >[!NOTE]
      >
      >* crx-repository가 업그레이드되고 컨텐츠가 마이그레이션되면 관리 계정의 암호를 변경합니다. 자세한 지침은 [기존 사용자의 암호 변경](/help/sites-administering/granite-user-group-admin.md)을 참조하십시오.


1. 배포 후 작업을 수행하여 로그인 자격 증명을 확인하고 문서 서비스, 서신 관리, 문서 보안 등을 구성합니다.
1. 서버가 업그레이드되었는지 확인합니다.

   업그레이드된 AEM Forms 서버에서 몇 가지 일상적인 작업을 수행하여 서버가 성공적으로 업그레이드되었는지 확인합니다. 마이그레이션된 양식 몇 개를 작성 및 제출하거나 문서를 보호하여 업그레이드를 성공적으로 수행할 수 있습니다.

   >[!NOTE]
   >
   >AEM 6.4 Forms에서 crx-repository 구조가 변경되었습니다. AEM 6.4 Forms로 업그레이드한 후 새로 만든 사용자 지정에 변경된 경로를 사용하십시오. 변경된 경로의 전체 목록은 [AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)Forms 저장소 구조 조정을 참조하십시오.

**기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 세부 지침을 따릅니다.**

* [JBoss용 AEM 6.4 Forms으로 LiveCycle ES4 SP1에서 업그레이드](assets/upgrade-jboss-livecycle.pdf)
* [WebLogic용 AEM 6.4 Forms으로 LiveCycle ES4 SP1에서 업그레이드](assets/upgrade-weblogic-livecycle.pdf)
* [LiveCycle ES4 SP1에서 AEM 6.4 Forms for WebSphere로 업그레이드](assets/upgrade-websphere-livecycle.pdf)
* [JBoss 턴키를 사용하여 LiveCycle ES4 SP1에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > JEE의 AEM 6.4 Forms {#livecycle-es3-forms-jee}

LiveCycle ES3를 JEE의 AEM 6.4 Forms으로 업그레이드하면 이전 버전에서 지원되는 애플리케이션 서버, 운영 체제 및 데이터베이스의 새로운 인스턴스(새 버전)로 자산 및 데이터를 마이그레이션하는 작업이 포함되므로 업그레이드 시 즉시 수행됩니다.

다음은 기존 LiveCycle ES3 서버를 AEM 6.4 Forms으로 업그레이드하는 절차에 대한 개요입니다. 자세한 지침은 절차 끝에 나열된 문서를 참조하십시오.

1. 업그레이드하기 전에:

   1. [Adobe 라이선스 웹 사이트(LWS)](https://licensing.adobe.com/)에서 JEE의 AEM 6.4 Forms 설치 프로그램을 다운로드합니다. 설치 관리자를 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
   1. 사용할 컨텐츠 저장소(CRX 저장소) 유형을 결정합니다. JEE의 일부 AEM Forms 기능만 컨텐츠 저장소 지속성 을 사용하여 컨텐츠 및 자산을 저장합니다. JEE 기능에서 이러한 AEM Forms을 사용하려는 경우에만 컨텐츠 저장소를 설치 및 구성합니다.

      * AEM Forms에서 OSGi 기능의 적응형 Forms, 서신 관리, HTML5 Forms, Forms 포털, HTML 작업 공간, 프로세스 보고 및 Forms 중심 워크플로우는 컨텐츠 저장소를 사용합니다. 이러한 기능에 AEM Forms을 사용하려는 경우 컨텐츠 저장소가 필요합니다.
      * AEM Forms Document Security에 대한 컨텐츠 리포지토리는 필요하지 않습니다.

      또한 LiveCycle 및 AEM Forms의 저장소 유형이 다릅니다. 사용 가능한 저장소 유형 및 관련 정보는 [AEM Forms 설치](/help/forms/using/choosing-persistence-type-for-aem-forms.md)에 대한 지속성 유형 선택을 참조하십시오.

   1. LiveCycle ES3 데이터베이스, GDS(Global Data Storage) 및 컨텐츠 리포지토리 백업을 만듭니다(문서 보안에 필요 없음). MongoMK 또는 RDBMK 지속성으로 업그레이드하는 경우, LiveCycle ES3 서신 관리 자산을 아카이브로 내보냅니다.
   1. 기존 플랫폼(예: 애플리케이션 서버, 데이터베이스, 운영 체제, Adobe Acrobat, 타사 애플리케이션 및 하드웨어)이 JEE의 AEM 6.4 Forms에 대해 지원되는지 확인합니다. 지원되는 하드웨어 및 소프트웨어에 대한 자세한 내용은 [지원되는 플랫폼 조합](/help/forms/using/aem-forms-jee-supported-platforms.md) 문서를 참조하십시오.

      데이터베이스의 새 인스턴스를 만들면 3단계에서 백업된 데이터를 데이터베이스로 가져옵니다. 데이터를 데이터베이스로 가져오는 방법에 대한 자세한 내용은 해당 데이터베이스 공급업체의 설명서를 참조하십시오.

      >[!NOTE]
      >
      >RDBMK 지속성 형식을 사용하는 경우, JEE에서 AEM Forms에서 실행되는 저장소 지속성 및 문서 서비스 모두에 단일 데이터베이스를 사용합니다.


1. 업그레이드를 수행합니다.

   1. 설치 프로그램을 실행하여 새 서버에 AEM 6.4 Forms을 JEE에 설치합니다. 설치 관리자는 필요한 모든 파일을 하나의 설치 디렉터리 구조 내에 컴퓨터에 저장합니다.
   1. 설치가 완료되면 **구성 관리자**&#x200B;를 실행하여 다양한 AEM Forms 모듈을 구성하고 적절한 구성을 설정합니다. 구성 설정과 함께 GDS(글로벌 데이터 저장소) 및 crx 저장소의 경로를 지정할 수 있습니다.

      >[!NOTE]
      >
      >업그레이드 작업 선택 화면에서 **[!UICONTROL Adobe Experience Manager Forms 6.2.0에서 업그레이드]** 옵션을 선택합니다. **[!UICONTROL Adobe Experience Manager Forms 6.2.0에서 업그레이드]** 옵션을 사용하면 구성 관리자가 LiveCycle ES3에서 AEM 6.4 Forms으로 업그레이드할 수 있습니다.

   1. (AEM Forms 문서 보안 모듈에 필요하지 않음) CRX 저장소를 업그레이드하고 AEM 6.4 Forms 서버로 가져옵니다.

      >[!NOTE]
      >
      >crx-repository가 업그레이드되고 컨텐츠가 마이그레이션되면 관리 계정의 암호를 변경합니다. 자세한 지침은 [기존 사용자의 암호 변경](/help/sites-administering/granite-user-group-admin.md)을 참조하십시오.
1. 배포 후 작업을 수행하여 로그인 자격 증명을 확인하고 문서 서비스, 서신 관리, 문서 보안 등을 구성합니다.
1. 서버가 업그레이드되었는지 확인합니다.

   업그레이드된 AEM Forms 서버에서 몇 가지 일상적인 작업을 수행하여 서버가 성공적으로 업그레이드되었는지 확인합니다. 마이그레이션된 양식 몇 개를 작성 및 제출하거나 문서를 보호하여 업그레이드를 성공적으로 수행할 수 있습니다.

   >[!NOTE]
   >
   >AEM 6.4 Forms에서 crx-repository 구조가 변경되었습니다. AEM 6.4 Forms로 업그레이드한 후 새로 만든 사용자 지정에 변경된 경로를 사용하십시오. 변경된 경로의 전체 목록은 [AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)Forms 저장소 구조 조정을 참조하십시오.

**기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 세부 지침을 따릅니다.**

* [JBoss용 AEM 6.4 Forms으로 LiveCycle ES3에서 업그레이드](assets/upgrade-jboss-livecycle-es3.pdf)
* [WebLogic용 AEM 6.4 Forms으로 LiveCycle ES3에서 업그레이드](assets/upgrade-weblogic-livecycle-es3.pdf)
* [WebSphere용 AEM 6.4 Forms으로 LiveCycle ES3에서 업그레이드](assets/upgrade-websphere-livecycle-es3.pdf)
* [JBoss 턴키를 사용하여 LiveCycle ES3에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-turnkey-livecycle-es3.pdf)
