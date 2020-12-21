---
title: AEM 6.4 Forms으로 업그레이드
seo-title: AEM 6.4 Forms으로 업그레이드
description: 'AEM 6.1 Forms, AEM 6.2 Forms 및 LiveCycle ES4 SP1에서 AEM 6.3 Forms으로 직접 업그레이드할 수 있습니다. '
seo-description: 'AEM 6.1 Forms, AEM 6.2 Forms 및 LiveCycle ES4 SP1에서 AEM 6.3 Forms으로 직접 업그레이드할 수 있습니다. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: ffa45c8fa98e1ebadd656ea58e4657b669ddd830
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---


# JEE {#upgrade-to-aem-forms-jee}에서 AEM 6.4 Forms으로 업그레이드

환경에 적합한 다음 업그레이드 방법 중 하나를 사용하십시오.

## JEE의 AEM 6.2 Forms 또는 JEE의 AEM 6.3 Forms > AEM 6.4 Forms on JEE {#aem-forms-jee-62-63-to-64}

다음 절차를 수행하여 JEE의 기존 AEM 6.2 Forms 또는 JEE의 AEM 6.3 Forms을 AEM 6.4 Forms on JEE로 업그레이드하십시오.

1. [LWS(Adobe Licensing Website)](https://licensing.adobe.com/)에서 JEE 설치 관리자의 AEM 6.4 Forms을 다운로드합니다. 설치 프로그램을 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
1. 성공적으로 업그레이드하기 위해 수행할 검사에 대해 알려면 [업그레이드 확인 목록 및 ](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) 계획을 참조하십시오.
1. 서버 다운타임을 최소화하면서 업그레이드가 제대로 실행되도록 하는 작업을 배우고 수행하려면 [AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63)로 업그레이드 준비를 참조하십시오.
1. 기존 환경과 응용 프로그램 서버에 따라 다음 문서 중 하나를 선택하고 지침을 따릅니다.

   * [AEM 6.2 또는 AEM 6.3 Forms에서 JBoss용 AEM 6.4 Forms으로 업그레이드](assets/upgrade-jboss.pdf)
   * [WebLogic용 AEM 6.2 또는 AEM 6.3 Forms에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-weblogic.pdf)
   * [AEM 6.2 또는 AEM 6.3 Forms에서 WebSphere용 AEM 6.4 Forms으로 업그레이드](assets/upgrade-websphere.pdf)
   * [JBoss 턴키용 AEM 6.2 또는 AEM 6.3 Forms에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-turnkey.pdf)

## JEE의 AEM 6.0 Forms > JEE의 AEM 6.3 Forms {#aem-forms-jee-60-to-63}

LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms에서 AEM 6.4 Forms으로 직접 업그레이드할 수 없습니다. 하나 이상의 LiveCycle 또는 AEM Forms 버전으로 중간 업그레이드한 다음 AEM 6.4 Forms에서 업그레이드할 수 있습니다. 중간 버전의 목록과 해당 업그레이드 지침에 대해서는 [업그레이드 경로 선택](upgrade.md)을 참조하십시오.

## LiveCycle ES4 SP1 > AEM 6.4 Forms on JEE {#livecycle-es4sp1-forms-jee}

JEE에서 LiveCycle ES4 SP1을 AEM 6.4 Forms으로 업그레이드하면 이전 버전에서 지원되는 애플리케이션 서버, 운영 체제 및 데이터베이스의 최신 인스턴스(새 버전)로 자산 및 데이터를 마이그레이션해야 하므로 즉시 업그레이드할 수 있습니다.

다음은 기존 LiveCycle ES4 SP1 서버를 AEM 6.4 Forms으로 업그레이드하는 절차의 개요입니다. 자세한 지침은 절차의 끝 부분에 나열된 문서를 참조하십시오.

1. 업그레이드 전:

   1. [LWS(Adobe Licensing Website)](https://licensing.adobe.com/)에서 JEE 설치 관리자의 AEM 6.4 Forms을 다운로드합니다. 설치 프로그램을 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
   1. 사용할 컨텐트 저장소(CRX 저장소) 유형을 결정합니다. JEE 기반의 일부 AEM Forms 기능만 컨텐츠 저장소 지속성 기능을 사용하여 컨텐츠와 에셋을 저장할 수 있습니다. JEE 기능에 이러한 AEM Forms을 사용하려는 경우에만 컨텐츠 저장소를 설치하고 구성합니다.

      * LiveCycle ES4 SP1에서는 통신 관리, Forms Portal, HTML Workspace 및 프로세스 보고 기능이 컨텐츠 저장소를 사용합니다. LiveCycle ES4에서 이러한 기능을 사용하지 않고 AEM Forms에서 이러한 기능을 사용하지 않을 계획인 경우, 컨텐츠 저장소가 필요하지 않습니다.
      * AEM Forms에서 적응 Forms, 통신 관리, HTML5 Forms(LiveCycle ES4 SP1의 모바일 Forms으로 알려져 있음), Forms Portal, HTML Workspace, 프로세스 보고, OSGi의 Forms 중심 워크플로우, 기능은 컨텐츠 저장소를 사용합니다. 이러한 기능에 AEM Forms을 사용하려는 경우 컨텐츠 저장소가 필요합니다.
      * AEM Forms Document Security에 대한 콘텐츠 리포지토리는 필요하지 않습니다.

      또한 LiveCycle과 AEM Forms의 저장소 유형은 다릅니다. 사용 가능한 저장소 유형 및 관련 정보는 [AEM Forms 설치에 대한 지속성 유형 선택](/help/forms/using/choosing-persistence-type-for-aem-forms.md)을 참조하십시오.

   1. LiveCycle ES4 SP1 컨텐츠 및 데이터의 백업을 만듭니다.

      LiveCycle ES4 SP1 데이터베이스, GDS(Global Data Storage) 및 crx-repository의 백업을 만듭니다(문서 보안에 필요하지 않음). MongoMK 또는 RDBMK 지속성으로 업그레이드하는 경우 LiveCycle ES4 SP1 메일 관리 에셋을 .cmp 파일로 내보내고 양식 에셋을 AEM 패키지로 내보냅니다.

   1. JEE의 AEM 6.4 Forms에서 기존 플랫폼(즉, 애플리케이션 서버, 데이터베이스, 운영 체제, Adobe Acrobat, 타사 애플리케이션 및 하드웨어)이 지원되는지 확인하십시오. 지원되는 하드웨어 및 소프트웨어에 대한 자세한 내용은 [지원되는 플랫폼 조합](/help/forms/using/aem-forms-jee-supported-platforms.md) 문서를 참조하십시오.

      데이터베이스의 새 인스턴스를 만드는 경우 3단계에서 백업된 데이터를 데이터베이스로 가져옵니다. 데이터를 데이터베이스로 가져오는 방법에 대한 자세한 내용은 해당 데이터베이스 공급업체의 설명서를 참조하십시오.

      >[!NOTE]
      >
      >RDBMK 지속성 형식을 사용하는 경우 JEE의 AEM Forms에서 실행되는 저장소 지속성 및 문서 서비스 모두에 단일 데이터베이스를 사용합니다.


1. 업그레이드 수행:

   1. 설치 프로그램을 실행하여 새 서버의 JEE에 AEM 6.4 Forms을 설치합니다. 설치 프로그램은 필요한 모든 파일을 하나의 설치 디렉토리 구조 내에 컴퓨터에 저장합니다.
   1. 설치가 완료되면 **구성 관리자**&#x200B;를 실행하여 다양한 AEM Forms 모듈을 구성하고 적절한 구성을 설정합니다. 설정 구성과 함께 GDS(Global Data Storage) 및 crx-repository의 경로를 지정할 수 있습니다.

      >[!NOTE]
      >
      >[업그레이드 작업 선택] 화면에서 **[!UICONTROL Adobe Experience Manager Forms 6.2.0]**&#x200B;에서 업그레이드 옵션을 선택합니다. **[!UICONTROL Adobe Experience Manager Forms 6.2.0]**&#x200B;에서 업그레이드 옵션을 사용하면 구성 관리자가 LiveCycle ES4 SP1에서 AEM 6.4 Forms으로 업그레이드할 수 있습니다.

   1. (AEM Forms 문서 보안 모듈의 경우 필요 없음) 컨텐츠를 컨텐츠 저장소(CRX-Repository)로 AEM 6.4 Forms 서버로 가져옵니다.

      >[!NOTE]
      >
      >* crx-repository가 업그레이드되고 컨텐츠가 마이그레이션되면 관리 계정의 암호를 변경합니다. 자세한 내용은 [기존 사용자의 암호 변경](/help/sites-administering/granite-user-group-admin.md)을 참조하십시오.


1. 배포 후 작업을 수행하여 사용 사례에 따라 로그인 자격 증명을 확인하고, 문서 서비스, 통신 관리, 문서 보안 등을 구성합니다.
1. 서버가 성공적으로 업그레이드되었는지 확인합니다.

   서버가 성공적으로 업그레이드되었는지 확인하기 위해 업그레이드된 AEM Forms 서버에서 몇 가지 루틴 작업을 수행합니다. 마이그레이션된 몇 개의 양식을 작성하여 제출하거나 문서를 보호하여 업그레이드를 성공적으로 수행할 수 있습니다.

   >[!NOTE]
   >
   >AEM 6.4 Forms에서 crx-repository의 구조가 변경되었습니다. AEM 6.4 양식으로 업그레이드한 후 새로 만드는 사용자 지정을 위해 변경된 경로를 사용합니다. 변경된 경로의 전체 목록은 AEM 6.4[Forms 리포지토리 재구조화를 참조하십시오.](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)

**기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 자세한 지침을 따릅니다.**

* [LiveCycle ES4 SP1에서 JBoss용 AEM 6.4 Forms으로 업그레이드](assets/upgrade-jboss-livecycle.pdf)
* [WebLogic용 LiveCycle ES4 SP1에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-weblogic-livecycle.pdf)
* [WebSphere용 AEM 6.4 Forms으로 LiveCycle ES4 SP1에서 업그레이드](assets/upgrade-websphere-livecycle.pdf)
* [JBoss 턴키를 사용하여 LiveCycle ES4 SP1에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms on JEE {#livecycle-es3-forms-jee}

JEE에서 AEM 6.4 Forms으로 LiveCycle ES3를 업그레이드하는 것은 지원되는 애플리케이션 서버, 운영 체제 및 데이터베이스의 최신 인스턴스(새 버전)로 에셋 및 데이터를 마이그레이션하는 작업이 필요하므로 즉시 업그레이드됩니다.

다음은 기존 LiveCycle ES3 서버를 AEM 6.4 Forms으로 업그레이드하는 절차의 개요입니다. 자세한 지침은 절차의 끝 부분에 나열된 문서를 참조하십시오.

1. 업그레이드 전:

   1. [LWS(Adobe Licensing Website)](https://licensing.adobe.com/)에서 JEE 설치 관리자의 AEM 6.4 Forms을 다운로드합니다. 설치 프로그램을 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
   1. 사용할 컨텐트 저장소(CRX 저장소) 유형을 결정합니다. JEE 기반의 일부 AEM Forms 기능만 컨텐츠 저장소 지속성 기능을 사용하여 컨텐츠와 에셋을 저장할 수 있습니다. JEE 기능에 이러한 AEM Forms을 사용하려는 경우에만 컨텐츠 저장소를 설치하고 구성합니다.

      * AEM Forms의 OSGi 기능에서 적응형 Forms, 통신 관리, HTML5 Forms, Forms Portal, HTML Workspace, 프로세스 보고 및 Forms 중심 워크플로우는 컨텐츠 저장소를 사용합니다. 이러한 기능에 AEM Forms을 사용하려는 경우 컨텐츠 저장소가 필요합니다.
      * AEM Forms Document Security에 대한 콘텐츠 리포지토리는 필요하지 않습니다.

      또한 LiveCycle과 AEM Forms의 저장소 유형은 다릅니다. 사용 가능한 저장소 유형 및 관련 정보는 [AEM Forms 설치에 대한 지속성 유형 선택](/help/forms/using/choosing-persistence-type-for-aem-forms.md)을 참조하십시오.

   1. LiveCycle ES3 데이터베이스, GDS(Global Data Storage) 및 컨텐츠 저장소의 백업을 만듭니다(문서 보안에 필요하지 않음). MongoMK 또는 RDBMK 지속성으로 업그레이드하는 경우 LiveCycle ES3 메일 관리 에셋을 보관으로 내보냅니다.
   1. JEE의 AEM 6.4 Forms에서 기존 플랫폼(즉, 애플리케이션 서버, 데이터베이스, 운영 체제, Adobe Acrobat, 타사 애플리케이션 및 하드웨어)이 지원되는지 확인하십시오. 지원되는 하드웨어 및 소프트웨어에 대한 자세한 내용은 [지원되는 플랫폼 조합](/help/forms/using/aem-forms-jee-supported-platforms.md) 문서를 참조하십시오.

      데이터베이스의 새 인스턴스를 만드는 경우 3단계에서 백업된 데이터를 데이터베이스로 가져옵니다. 데이터를 데이터베이스로 가져오는 방법에 대한 자세한 내용은 해당 데이터베이스 공급업체의 설명서를 참조하십시오.

      >[!NOTE]
      >
      >RDBMK 지속성 형식을 사용하는 경우 JEE의 AEM Forms에서 실행되는 저장소 지속성 및 문서 서비스 모두에 단일 데이터베이스를 사용합니다.


1. 업그레이드 수행:

   1. 설치 프로그램을 실행하여 새 서버의 JEE에 AEM 6.4 Forms을 설치합니다. 설치 프로그램은 필요한 모든 파일을 하나의 설치 디렉토리 구조 내에 컴퓨터에 저장합니다.
   1. 설치가 완료되면 **구성 관리자**&#x200B;를 실행하여 다양한 AEM Forms 모듈을 구성하고 적절한 구성을 설정합니다. 설정 구성과 함께 GDS(Global Data Storage) 및 crx-repository의 경로를 지정할 수 있습니다.

      >[!NOTE]
      >
      >[업그레이드 작업 선택] 화면에서 **[!UICONTROL Adobe Experience Manager Forms 6.2.0]**&#x200B;에서 업그레이드 옵션을 선택합니다. **[!UICONTROL Adobe Experience Manager Forms 6.2.0]**&#x200B;에서 업그레이드 옵션을 사용하면 구성 관리자가 LiveCycle ES3에서 AEM 6.4 Forms으로 업그레이드할 수 있습니다.

   1. (AEM Forms 문서 보안 모듈의 경우 필요 없음) CRX 저장소를 AEM 6.4 Forms 서버로 업그레이드하여 가져옵니다.

      >[!NOTE]
      >
      >crx-repository가 업그레이드되고 컨텐츠가 마이그레이션되면 관리 계정의 암호를 변경합니다. 자세한 내용은 [기존 사용자의 암호 변경](/help/sites-administering/granite-user-group-admin.md)을 참조하십시오.
1. 배포 후 작업을 수행하여 사용 사례에 따라 로그인 자격 증명을 확인하고, 문서 서비스, 통신 관리, 문서 보안 등을 구성합니다.
1. 서버가 성공적으로 업그레이드되었는지 확인합니다.

   서버가 성공적으로 업그레이드되었는지 확인하기 위해 업그레이드된 AEM Forms 서버에서 몇 가지 루틴 작업을 수행합니다. 마이그레이션된 몇 개의 양식을 작성하여 제출하거나 문서를 보호하여 업그레이드를 성공적으로 수행할 수 있습니다.

   >[!NOTE]
   >
   >AEM 6.4 Forms에서 crx-repository의 구조가 변경되었습니다. AEM 6.4 양식으로 업그레이드한 후 새로 만드는 사용자 지정을 위해 변경된 경로를 사용합니다. 변경된 경로의 전체 목록은 AEM 6.4[Forms 리포지토리 재구조화를 참조하십시오.](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)

**기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 자세한 지침을 따릅니다.**

* [JBoss용 LiveCycle ES3에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-jboss-livecycle-es3.pdf)
* [WebLogic용 LiveCycle ES3에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-weblogic-livecycle-es3.pdf)
* [WebSphere용 AEM 6.4 Forms으로 LiveCycle ES3에서 업그레이드](assets/upgrade-websphere-livecycle-es3.pdf)
* [JBoss 턴키를 사용하여 LiveCycle ES3에서 AEM 6.4 Forms으로 업그레이드](assets/upgrade-turnkey-livecycle-es3.pdf)
