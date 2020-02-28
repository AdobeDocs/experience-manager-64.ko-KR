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


# OSGi에서 AEM 6.4 Forms로 업그레이드 {#upgrade-to-aem-forms-osgi}

환경에 적합한 다음 업그레이드 방법 중 하나를 사용하십시오.

## AEM 6.2 양식 또는 AEM 6.3 양식 > AEM 6.4 양식 {#upgrade-aem-forms-62-63-to-64}

AEM 6.2 양식 또는 AEM 6.3 양식에서 AEM 6.4 양식으로 직접 업그레이드할 수 있습니다. 다음을 수행합니다.

1. 기존 AEM 인스턴스를 AEM 6.4로 업그레이드합니다.다음 단계는 다음과 같습니다.

   1. AEM 6.2 양식 또는 AEM 6.3 양식에 대한 최신 서비스 팩 및 패치를 설치합니다. 자세한 내용은 다음을 참조하십시오.

      * [AEM 6.2 릴리스 노트](https://helpx.adobe.com/experience-manager/6-2/release-notes.html)
      * [AEM 6.3 릴리스 노트](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
      * [AEM 지속 허브](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)
   1. 업그레이드할 소스 인스턴스를 준비합니다. 자세한 단계는 AEM [6.4로 업그레이드를 참조하십시오](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. AEM 6. [4 QuickStart를 다운로드합니다](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Unix/Linux 기반 설치만 해당)** UNIX 또는 Linux를 기본 운영 체제로 사용하는 경우 터미널 창을 열고 crx-quickstart가 포함된 폴더로 이동한 다음 다음 다음 다음 명령을 실행합니다.

      `chmod -R 755 ../crx-quickstart`

   1. AEM 인스턴스를 AEM 6.3으로 업그레이드합니다.단계별 지침은 AEM [6.4로 업그레이드를 참조하십시오](/help/sites-deploying/upgrade.md).

      다음 단계를 계속하기 전에 &lt;crx-repository>/error.log 파일에 ServiceEvent REGISTERED 및 ServiceEvent UNREGISTERED 메시지가 나타날 때까지 기다립니다.

      >[!NOTE]
      >
      >서버가 실행되고 나면 몇 개의 AEM Forms 번들이 설치 상태로 유지됩니다. 번들 수는 설치 시 다를 수 있습니다. 이러한 번들의 상태를 무시해도 됩니다. 번들은 에 나와 `https://[server]:[port]/system/console/`있습니다.


1. AEM Forms 추가 기능 패키지를 설치합니다. 다음 단계는 다음과 같습니다.

   1. AEM 서버에 관리자로 로그인하고 패키지 공유를 엽니다. 패키지 공유의 기본 URL은 입니다 `https://[server]:[port]/crx/packageshare`.
   1. 패키지 공유에서 **[!UICONTROL AEM 6.4 양식 추가 기능 패키지를]**&#x200B;검색하고 운영 체제에 해당하는 패키지를 클릭한 다음 다운로드를 **[!UICONTROL 클릭합니다]**. 라이센스 계약을 읽고 동의한 다음 확인을 **[!UICONTROL 클릭합니다]**. 다운로드가 시작됩니다. 다운로드하면 패키지 **[!UICONTROL 옆에]** 다운로드된 단어가 나타납니다.

      또는 AEM Forms 릴리스에 나열된 하이퍼링크를 [사용하여](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 패키지를 수동으로 다운로드할 수도 있습니다.

   1. 다운로드가 완료되면 [다운로드됨]을 **[!UICONTROL 클릭합니다]**. 패키지 관리자로 리디렉션됩니다. 패키지 관리자에서 다운로드한 패키지를 검색하고 설치를 **[!UICONTROL 클릭합니다]**.

      AEM Forms 릴리스에 [나열된 직접 링크를 사용하여 패키지를 수동으로 다운로드하는 경우 AEM Package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)Manager를 **[!UICONTROL 열고 패키지 업로드를]**&#x200B;클릭한다음 다운로드한 패키지를 선택하고 업로드를 클릭합니다. 패키지가 업로드된 후 패키지 이름을 클릭하고 설치를 **[!UICONTROL 클릭합니다]**.

      >[!NOTE]
      >
      >패키지가 설치되면 AEM 인스턴스를 다시 시작하라는 메시지가 표시됩니다. **서버를 즉시 중지하지 마십시오.** AEM Forms 서버를 중지하기 전에 &lt;crx-repository>/error.log 파일에 ServiceEvent REGISTERED 및 ServiceEvent UNREGISTERED 메시지가 나타나지 않고 로그가 안정될 때까지 기다립니다. 또한 일부 패키지는 설치된 상태로 유지될 수 있습니다. 이러한 패키지의 상태를 무시해도 됩니다.

   1. AEM 인스턴스를 중지하고 다음 파일을 삭제합니다.

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. AEM 인스턴스를 시작합니다.


1. 설치 후 작업을 수행합니다.

   * **마이그레이션 유틸리티 실행**

      마이그레이션 유틸리티를 사용하면 AEM 6.4 양식과 호환되는 이전 버전의 응용 양식 및 통신 관리 에셋을 만들 수 있습니다. AEM 패키지 공유에서 유틸리티를 다운로드할 수 있습니다. 마이그레이션 유틸리티를 구성하고 사용하기 위한 단계별 정보는 [마이그레이션 유틸리티를](/help/forms/using/migration-utility.md)참조하십시오.

      초안 및 제출 [구성 요소를](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) 데이터베이스와 통합하고 이전 버전에서 업그레이드하는 데 Sample을 사용하는 경우 업그레이드를 수행한 후 다음 SQL 쿼리를 실행합니다.

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(AEM 6.2 양식 또는 이전 버전에서만 업그레이드하는 경우) Adobe Sign을 다시 구성하십시오.**

      이전 버전의 AEM Forms에서 Adobe Sign을 구성한 경우 AEM Cloud 서비스에서 Adobe Sign을 다시 구성하십시오. 자세한 내용은 AEM Forms [와 Adobe Sign 통합을 참조하십시오](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(AEM 6.2 Forms 또는 이전 버전에서만 업그레이드하는 경우) 분석 및 보고서를 다시 구성합니다.**

      AEM 6.4 Forms에서는 소스나 임프레션에 대한 성공 이벤트에 대한 트래픽 변수를 사용할 수 없습니다. 따라서 AEM 6.2 양식 또는 이전 버전에서 업그레이드하면 AEM Forms가 Adobe Analytics 서버로 데이터 전송을 중단하고 적응형 양식에 대한 분석 보고서를 사용할 수 없습니다. 또한 AEM 6.4 양식에서는 한 필드에 보낸 시간에 대한 양식 분석 및 성공 이벤트 버전에 대한 트래픽 변수를 제공합니다. 따라서 AEM Forms 환경에 대한 분석 및 보고서를 다시 구성합니다. 자세한 내용은 분석 [및 보고서](/help/forms/using/configure-analytics-forms-documents.md)구성을 참조하십시오.

1. 서버가 성공적으로 업그레이드되고 모든 데이터도 성공적으로 마이그레이션되며 정상적으로 작동하는지 확인합니다.

   * **** 번들의 상태를 확인합니다.모든 번들이 활성 상태인지 확인합니다.
   * **** 복제 및 역 복제 확인:마이그레이션된 몇 가지 양식을 게시, 채우기 및 제출합니다. 제출된 데이터도 확인합니다.
   * **** 관리자 및 개발자 사용자 인터페이스에 대한 액세스 확인:관리 계정에서 AEM 인스턴스에 로그인하고 다음 URL에 대한 액세스 권한이 있는지 확인합니다.

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`
   >[!NOTE]
   AEM 6.4 양식에서 crx-repository의 구조가 변경되었습니다. AEM 6.4 양식으로 업그레이드한 후 새로 만드는 사용자 지정을 위해 변경된 경로를 사용하십시오. 변경된 경로의 전체 목록은 AEM 6.4 [의 양식 리포지토리 재구성을 참조하십시오](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 양식 및 AEM 6.1 양식 > AEM 6.4 양식 {#upgrade-aem-forms-60-61-to-64}

AEM 6.0 양식 **및 AEM** 6.1 **양식에서** AEM 6.4 양식으로의 직접 업그레이드 경로는 사용할 수 없습니다. AEM 6.2 Forms로 중간 [업그레이드하거나](/help/forms/using/upgrade.md) AEM 6.3 Forms로 [업그레이드한](/help/forms/using/upgrade.md) 다음 AEM 6.2 Forms 또는 AEM 6.3 Forms에서 AEM 6.4 Forms로 업그레이드하십시오.
