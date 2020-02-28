---
title: AEM 6.4 Forms로 업그레이드
seo-title: AEM 6.4 Forms로 업그레이드
description: 'AEM 6.1 양식, AEM 6.2 양식 및 LiveCycle ES4 SP1에서 AEM 6.3 Forms로 직접 업그레이드할 수 있습니다. '
seo-description: 'AEM 6.1 양식, AEM 6.2 양식 및 LiveCycle ES4 SP1에서 AEM 6.3 Forms로 직접 업그레이드할 수 있습니다. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: d2657bc364b7a814fac9228afdec60f96faaf175

---


# JEE에서 AEM 6.4 Forms로 업그레이드 {#upgrade-to-aem-forms-jee}

환경에 적합한 다음 업그레이드 방법 중 하나를 사용하십시오.

## JEE의 AEM 6.2 양식 또는 JEE의 AEM 6.3 양식 > AEM 6.4 양식 {#aem-forms-jee-62-63-to-64}

JEE 또는 AEM 6.3 양식의 기존 AEM 6.2 양식을 JEE의 AEM 6.4 양식으로 업그레이드하려면 다음 절차를 수행하십시오.

1. JEE의 AEM 6.4 양식 설치 프로그램은 Adobe LWS( [Licensing Website)](https://licensing.adobe.com/)에서 다운로드할 수 있습니다. 설치 프로그램을 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
1. 성공적인 [업그레이드를 위해 수행할 확인 사항에 대한 자세한 내용은 업그레이드 확인 목록 및 계획](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) 을 참조하십시오.
1. 서버 다운타임을 [최소화하면서 업그레이드가 제대로](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) 실행되도록 하는 작업을 배우고 수행하려면 AEM Forms로 업그레이드 준비를 참조하십시오.
1. 기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 지침을 따릅니다.

   * [AEM 6.2 또는 AEM 6.3 양식에서 JBoss용 AEM 6.4 Forms로 업그레이드](assets/upgrade-jboss.pdf)
   * [AEM 6.2 또는 AEM 6.3 양식에서 WebLogic용 AEM 6.4 Forms로 업그레이드](assets/upgrade-weblogic.pdf)
   * [AEM 6.2 또는 AEM 6.3 양식에서 WebSphere용 AEM 6.4 Forms로 업그레이드](assets/upgrade-websphere.pdf)
   * [AEM 6.2 또는 AEM 6.3 양식에서 JBoss 턴키용 AEM 6.4 Forms로 업그레이드](assets/upgrade-turnkey.pdf)

## JEE의 AEM 6.0 양식 > JEE의 AEM 6.3 양식 {#aem-forms-jee-60-to-63}

LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms에서 AEM 6.4 Forms로 직접 업그레이드할 수 없습니다. 하나 이상의 LiveCycle 또는 AEM Forms 버전으로 중간 업그레이드한 다음 AEM 6.4 Forms에서 업그레이드할 수 있습니다. 중간 버전 및 해당 업그레이드 지침 목록은 업그레이드 [경로](/help/forms/using/upgrade.md#main-pars-header)선택을 참조하십시오.

## LiveCycle ES4 SP1 > JEE의 AEM 6.4 양식 {#livecycle-es4sp1-forms-jee}

LiveCycle ES4 SP1을 JEE의 AEM 6.4 Forms로 업그레이드하면 에셋 및 데이터를 이전 버전에서 지원되는 애플리케이션 서버, 운영 체제 및 데이터베이스의 최신 인스턴스(새 버전)로 마이그레이션해야 하므로 즉시 업그레이드할 수 있습니다.

다음은 기존 LiveCycle ES4 SP1 서버를 AEM 6.4 Forms로 업그레이드하는 절차의 개요입니다. 자세한 지침은 절차의 끝에 나와 있는 문서를 참조하십시오.

1. 업그레이드 전:

   1. JEE의 AEM 6.4 양식 설치 프로그램은 Adobe LWS( [Licensing Website)](https://licensing.adobe.com/)에서 다운로드할 수 있습니다. 설치 프로그램을 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
   1. 사용할 컨텐츠 저장소(CRX 저장소) 유형을 결정합니다. JEE의 일부 AEM Forms 기능만 컨텐츠 저장소 지속성 기능을 사용하여 컨텐츠 및 자산을 저장합니다. JEE 기능에서 이러한 AEM Forms를 사용하려는 경우에만 컨텐츠 저장소를 설치하고 구성합니다.

      * LiveCycle ES4 SP1에서 Correspondence Management, Forms Portal, HTML Workspace 및 Process Reporting 기능은 Content Repository를 사용합니다. LiveCycle ES4에서 이러한 기능을 사용하지 않고 AEM Forms에서 이러한 기능을 사용하지 않을 계획인 경우 컨텐츠 저장소가 필요하지 않습니다.
      * AEM Forms, 적응형 양식, 통신 관리, HTML5 양식(LiveCycle ES4 SP1의 모바일 양식), Forms Portal, HTML 작업 영역, 프로세스 보고, OSGi의 양식 중심 워크플로우에서는 컨텐츠 저장소를 사용합니다. 이러한 기능에 대해 AEM Forms를 사용하려는 경우 컨텐츠 저장소가 필요합니다.
      * AEM Forms Document Security에 대한 콘텐츠 저장소가 필요하지 않습니다.
      또한 LiveCycle 및 AEM Forms의 저장소 유형은 다릅니다. 사용 가능한 저장소 유형 및 관련 정보는 AEM [Forms 설치에](/help/forms/using/choosing-persistence-type-for-aem-forms.md)대한 지속성 유형 선택을 참조하십시오.

   1. LiveCycle ES4 SP1 컨텐츠 및 데이터의 백업을 만듭니다.

      LiveCycle ES4 SP1 데이터베이스, GDS(Global Data Storage) 및 crx-repository(문서 보안에는 필요 없음)의 백업을 만듭니다. MongoMK 또는 RDBMK 지속성으로 업그레이드하는 경우 LiveCycle ES4 SP1 통신 관리 자산을 .cmp 파일로 내보내고 양식 자산을 AEM 패키지로 내보냅니다.

   1. JEE의 AEM 6.4 양식에 대해 기존 플랫폼(즉, 애플리케이션 서버, 데이터베이스, 운영 체제, Adobe Acrobat, 타사 애플리케이션 및 하드웨어)이 지원되는지 확인합니다. 지원되는 하드웨어 및 소프트웨어에 대한 자세한 내용은 지원되는 플랫폼 [조합 문서를](/help/forms/using/aem-forms-jee-supported-platforms.md) 참조하십시오.

      데이터베이스의 새 인스턴스를 만드는 경우 3단계에서 백업한 데이터를 데이터베이스로 가져옵니다. 데이터를 데이터베이스로 가져오는 방법에 대한 자세한 내용은 해당 데이터베이스 공급업체의 설명서를 참조하십시오.

      >[!NOTE]
      >
      >RDBMK 지속성 형식을 사용하는 경우 JEE의 AEM Forms에서 실행되는 저장소 지속성 및 문서 서비스 모두에 단일 데이터베이스를 사용합니다.


1. 업그레이드 수행:

   1. 설치 프로그램을 실행하여 새 서버의 JEE에 AEM 6.4 양식을 설치합니다. 설치 관리자는 필요한 모든 파일을 하나의 설치 디렉토리 구조 내에 컴퓨터에 저장합니다.
   1. 설치가 완료되면 Configuration Manager를 실행하여 **다양한** AEM Forms 모듈을 구성하고 적절한 구성을 설정합니다. 설정 구성과 함께 GDS(Global Data Storage) 및 crx-repository의 경로를 지정할 수 있습니다.

      >[!NOTE]
      >
      >[업그레이드 작업 선택] 화면에서 Adobe Experience **[!UICONTROL Manager Forms 6.2.0에서 업그레이드]** 옵션을 선택합니다. Adobe **[!UICONTROL Experience Manager Forms 6.2.0에서 업그레이드]** 옵션을 사용하면 구성 관리자가 LiveCycle ES4 SP1에서 AEM 6.4 Forms로 업그레이드할 수 있습니다.

   1. (AEM Forms 문서 보안 모듈에는 필요하지 않음) 컨텐츠를 컨텐츠 저장소(CRX-Repository)로 AEM 6.4 Forms 서버로 가져옵니다.

      >[!NOTE]
      >
      >* crx-repository가 업그레이드되고 컨텐츠가 마이그레이션되면 관리 계정의 암호를 변경합니다. 자세한 지침은 기존 [사용자의 암호 변경을 참조하십시오](/help/sites-administering/granite-user-group-admin.md).


1. 배포 후 작업을 수행하여 로그인 자격 증명을 확인하고, 문서 서비스 구성, 통신 관리, 문서 보안 등을 사용 사례에 따라 수행합니다.
1. 서버가 성공적으로 업그레이드되었는지 확인합니다.

   업그레이드된 AEM Forms 서버에서 몇 가지 루틴 작업을 수행하여 서버가 성공적으로 업그레이드되었는지 확인합니다. 마이그레이션된 몇 개의 양식을 작성 및 제출하거나 문서를 보호하여 성공적으로 업그레이드할 수 있습니다.

   >[!NOTE]
   >
   >AEM 6.4 양식에서 crx-repository의 구조가 변경되었습니다. AEM 6.4 양식으로 업그레이드한 후 새로 만드는 사용자 지정을 위해 변경된 경로를 사용하십시오. 변경된 경로의 전체 목록은 AEM 6.4 [의 양식 리포지토리 재구성을 참조하십시오](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 자세한 지침을 따르십시오.**

* [LiveCycle ES4 SP1에서 JBoss용 AEM 6.4 Forms로 업그레이드](assets/upgrade-jboss-livecycle.pdf)
* [LiveCycle ES4 SP1에서 WebLogic용 AEM 6.4 Forms로 업그레이드](assets/upgrade-weblogic-livecycle.pdf)
* [LiveCycle ES4 SP1에서 WebSphere용 AEM 6.4 Forms로 업그레이드](assets/upgrade-websphere-livecycle.pdf)
* [JBoss 턴키를 사용하여 LiveCycle ES4 SP1에서 AEM 6.4 Forms로 업그레이드](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > JEE의 AEM 6.4 양식 {#livecycle-es3-forms-jee}

LiveCycle ES3를 JEE의 AEM 6.4 Forms로 업그레이드하면 이전 버전에서 지원되는 애플리케이션 서버, 운영 체제 및 데이터베이스의 최신 인스턴스(새 버전)로 자산 및 데이터를 마이그레이션해야 하므로 업그레이드 시 즉시 사용할 수 없습니다.

다음은 기존 LiveCycle ES3 서버를 AEM 6.4 Forms로 업그레이드하는 절차의 개요입니다. 자세한 지침은 절차의 끝에 나와 있는 문서를 참조하십시오.

1. 업그레이드 전:

   1. JEE의 AEM 6.4 양식 설치 프로그램은 Adobe LWS( [Licensing Website)](https://licensing.adobe.com/)에서 다운로드할 수 있습니다. 설치 프로그램을 다운로드하려면 유효한 유지 관리 및 지원 계약이 필요합니다.
   1. 사용할 컨텐츠 저장소(CRX 저장소) 유형을 결정합니다. JEE의 일부 AEM Forms 기능만 컨텐츠 저장소 지속성 기능을 사용하여 컨텐츠 및 자산을 저장합니다. JEE 기능에서 이러한 AEM Forms를 사용하려는 경우에만 컨텐츠 저장소를 설치하고 구성합니다.

      * AEM Forms, 적응형 양식, 통신 관리, HTML5 양식, Forms Portal, HTML Workspace, 프로세스 보고 및 OSGi 기능의 양식 중심 워크플로우에서는 컨텐츠 저장소를 사용합니다. 이러한 기능에 대해 AEM Forms를 사용하려는 경우 컨텐츠 저장소가 필요합니다.
      * AEM Forms Document Security에 대한 콘텐츠 저장소가 필요하지 않습니다.
      또한 LiveCycle 및 AEM Forms의 저장소 유형은 다릅니다. 사용 가능한 저장소 유형 및 관련 정보는 AEM [Forms 설치에](/help/forms/using/choosing-persistence-type-for-aem-forms.md)대한 지속성 유형 선택을 참조하십시오.

   1. LiveCycle ES3 데이터베이스, GDS(Global Data Storage) 및 Content Repository(문서 보안에 필요 없음)의 백업을 만듭니다. MongoMK 또는 RDBMK 지속성으로 업그레이드하는 경우 LiveCycle ES3 통신 관리 에셋을 보관으로 내보냅니다.
   1. JEE의 AEM 6.4 양식에 대해 기존 플랫폼(즉, 애플리케이션 서버, 데이터베이스, 운영 체제, Adobe Acrobat, 타사 애플리케이션 및 하드웨어)이 지원되는지 확인합니다. 지원되는 하드웨어 및 소프트웨어에 대한 자세한 내용은 지원되는 플랫폼 [조합 문서를](/help/forms/using/aem-forms-jee-supported-platforms.md) 참조하십시오.

      데이터베이스의 새 인스턴스를 만드는 경우 3단계에서 백업한 데이터를 데이터베이스로 가져옵니다. 데이터를 데이터베이스로 가져오는 방법에 대한 자세한 내용은 해당 데이터베이스 공급업체의 설명서를 참조하십시오.

      >[!NOTE] RDBMK 지속성 형식을 사용하는 경우 JEE의 AEM Forms에서 실행되는 저장소 지속성 및 문서 서비스 모두에 단일 데이터베이스를 사용합니다.


1. 업그레이드 수행:

   1. 설치 프로그램을 실행하여 새 서버의 JEE에 AEM 6.4 양식을 설치합니다. 설치 관리자는 필요한 모든 파일을 하나의 설치 디렉토리 구조 내에 컴퓨터에 저장합니다.
   1. 설치가 완료되면 Configuration Manager를 실행하여 **다양한** AEM Forms 모듈을 구성하고 적절한 구성을 설정합니다. 설정 구성과 함께 GDS(Global Data Storage) 및 crx-repository의 경로를 지정할 수 있습니다.

      >[!NOTE] [업그레이드 작업 선택] 화면에서 Adobe Experience **[!UICONTROL Manager Forms 6.2.0에서 업그레이드]** 옵션을 선택합니다. Adobe **[!UICONTROL Experience Manager Forms 6.2.0에서 업그레이드]** 옵션을 사용하면 구성 관리자가 LiveCycle ES3에서 AEM 6.4 Forms로 업그레이드할 수 있습니다.

   1. (AEM Forms 문서 보안 모듈에는 필요하지 않음) CRX 저장소를 AEM 6.4 Forms 서버로 업그레이드하여 가져옵니다.

      >[!NOTE] crx-repository가 업그레이드되고 컨텐츠가 마이그레이션되면 관리 계정의 암호를 변경합니다. 자세한 지침은 기존 [사용자의 암호 변경을 참조하십시오](/help/sites-administering/granite-user-group-admin.md).
1. 배포 후 작업을 수행하여 로그인 자격 증명을 확인하고, 문서 서비스 구성, 통신 관리, 문서 보안 등을 사용 사례에 따라 수행합니다.
1. 서버가 성공적으로 업그레이드되었는지 확인합니다.

   업그레이드된 AEM Forms 서버에서 몇 가지 루틴 작업을 수행하여 서버가 성공적으로 업그레이드되었는지 확인합니다. 마이그레이션된 몇 개의 양식을 작성 및 제출하거나 문서를 보호하여 성공적으로 업그레이드할 수 있습니다.

   >[!NOTE] AEM 6.4 양식에서 crx-repository의 구조가 변경되었습니다. AEM 6.4 양식으로 업그레이드한 후 새로 만드는 사용자 지정을 위해 변경된 경로를 사용하십시오. 변경된 경로의 전체 목록은 AEM 6.4 [의 양식 리포지토리 재구성을 참조하십시오](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**기존 환경과 애플리케이션 서버에 따라 다음 문서 중 하나를 선택하고 자세한 지침을 따르십시오.**

* [LiveCycle ES3에서 JBoss용 AEM 6.4 Forms로 업그레이드](assets/upgrade-jboss-livecycle-es3.pdf)
* [LiveCycle ES3에서 WebLogic용 AEM 6.4 Forms로 업그레이드](assets/upgrade-weblogic-livecycle-es3.pdf)
* [LiveCycle ES3에서 WebSphere용 AEM 6.4 Forms로 업그레이드](assets/upgrade-websphere-livecycle-es3.pdf)
* [JBoss 턴키를 사용하여 LiveCycle ES3에서 AEM 6.4 Forms로 업그레이드](assets/upgrade-turnkey-livecycle-es3.pdf)
