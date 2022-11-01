---
title: AEM 6.4 Forms로 업그레이드
seo-title: Upgrade to AEM 6.4 Forms
description: AEM 6.1 Forms, AEM 6.2 Forms 및 LiveCycle ES4 SP1에서 AEM 6.3 Forms으로 직접 업그레이드할 수 있습니다.
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 11%

---

# OSGi에서 AEM 6.4 Forms으로 업그레이드 {#upgrade-to-aem-forms-osgi}

환경에 적합한 다음 업그레이드 경로 중 하나를 사용하십시오.

## AEM 6.2 Forms 또는 AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

AEM 6.2 Forms 또는 AEM 6.3 Forms에서 AEM 6.4 Forms으로 직접 업그레이드할 수 있습니다. 다음을 수행합니다.

1. 기존 AEM 인스턴스를 AEM 6.4로 업그레이드하십시오. 단계는 아래에 나와 있습니다.

   1. AEM 6.2 Forms 또는 AEM 6.3 Forms용 최신 서비스 팩 및 패치를 설치합니다. 자세한 내용은 다음을 참조하십시오.

      * [AEM 6.2 릴리스 정보](https://helpx.adobe.com/kr/experience-manager/6-2/release-notes.html)
      * [AEM 6.3 릴리스 노트](https://helpx.adobe.com/kr/experience-manager/6-3/release-notes.html)
      * [AEM 지속성 허브](https://helpx.adobe.com/kr/experience-manager/aem-releases-updates.html)
   1. 업그레이드할 소스 인스턴스를 준비합니다. 자세한 단계는 [AEM 6.4로 업그레이드](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. 다운로드 [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Unix/Linux 기반 설치만 해당)** UNIX 또는 Linux를 기본 운영 체제로 사용하는 경우 터미널 창을 열고 crx-quickstart가 포함된 폴더로 이동한 다음 명령을 실행합니다.

      `chmod -R 755 ../crx-quickstart`

   1. AEM 인스턴스를 AEM 6.3으로 업그레이드합니다. 단계별 지침은 [AEM 6.4로 업그레이드](/help/sites-deploying/upgrade.md).

      다음 단계를 계속 진행하기 전에 ServiceEvent REGISTERED 및 ServiceEvent UNREGISTERED 메시지가 &lt;crx-repository>/error.log 파일을 참조하십시오.

      >[!NOTE]
      >
      >서버가 실행되고 나면 일부 AEM Forms 번들이 설치 상태로 유지됩니다. 설치 시마다 번들 수가 다를 수 있습니다. 이러한 번들의 상태를 무시해도 됩니다. 번들은 다음 위치에 나열됩니다. `https://[server]:[port]/system/console/`.


1. AEM Forms 추가 기능 패키지 설치. 단계는 아래에 나열되어 있습니다.

   1. [소프트웨어 배포](https://experience.adobe.com/downloads)를 엽니다. 소프트웨어 배포에 로그인하려면 Adobe ID가 필요합니다.
   1. 헤더 메뉴에 제공된 **[!UICONTROL Adobe Experience Manager]**&#x200B;를 누릅니다.
   1. 에서 **[!UICONTROL 필터]** 섹션:
      1. 선택 **[!UICONTROL Forms]** 에서 **[!UICONTROL 솔루션]** 드롭다운 목록.
      1. 패키지의 버전 및 유형을 선택합니다. 를 사용할 수도 있습니다 **[!UICONTROL 다운로드 검색]** 결과를 필터링하는 옵션.
   1. 운영 체제에 해당하는 패키지 이름을 탭하고 **[!UICONTROL EULA 약관 동의]**, 탭 **[!UICONTROL 다운로드]**.
   1. [패키지 관리자](https://docs.adobe.com/content/help/ko-KR/experience-manager-65/administering/contentmanagement/package-manager.html)를 열고 **[!UICONTROL 패키지 업로드]**&#x200B;를 클릭하여 패키지를 업로드합니다.
   1. 패키지를 선택하고 **[!UICONTROL 설치]**&#x200B;를 클릭합니다.

      에 나열된 직접 링크를 사용하여 패키지를 다운로드할 수도 있습니다. [AEM Forms 릴리스](https://helpx.adobe.com/kr/aem-forms/kb/aem-forms-releases.html) 문서.

      >[!NOTE]
      >
      >패키지가 설치되면 AEM 인스턴스를 다시 시작하라는 메시지가 표시됩니다. **서버를 즉시 중지하지 마십시오.** AEM Forms 서버를 중지하기 전에 ServiceEvent REGISTERED 및 ServiceEvent UNREGISTERED 메시지가 &lt;crx-repository>/error.log 파일 및 로그는 안정합니다. 또한 일부 패키지는 설치 상태로 남아 있을 수 있습니다. 이 패키지의 상태를 무시해도 됩니다.

   1. AEM 인스턴스를 중지하고 다음 파일을 삭제합니다.

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. AEM 인스턴스를 시작합니다.


1. 설치 후 활동을 수행합니다.

   * **마이그레이션 유틸리티 실행**

      마이그레이션 유틸리티를 사용하면 AEM 6.4 Forms와 호환되는 이전 버전의 적응형 양식 및 서신 관리 자산을 만들 수 있습니다. AEM Software Distribution에서 유틸리티를 다운로드할 수 있습니다. 마이그레이션 유틸리티를 구성 및 사용하기 위한 단계별 정보는 [마이그레이션 유틸리티](/help/forms/using/migration-utility.md).

      사용 중인 경우 [초안 및 제출 구성 요소 통합을 위한 샘플](integrate-draft-submission-database.md) 데이터베이스를 사용하여 이전 버전에서 업그레이드한 다음 업그레이드를 수행한 후 다음 SQL 쿼리를 실행합니다.

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

   * **(AEM 6.2 Forms 또는 이전 버전에서만 업그레이드하는 경우) Acrobat Sign 다시 구성**

      이전 버전의 AEM Forms에서 Acrobat Sign을 구성한 경우 AEM 클라우드 서비스에서 Acrobat Sign을 다시 구성합니다. 자세한 내용은 [Acrobat Sign과 AEM Forms 통합](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(AEM 6.2 Forms 또는 이전 버전에서만 업그레이드하는 경우) Analytics 및 보고서를 다시 구성합니다**

      AEM 6.4 Forms에서 노출에 대한 소스 및 성공 이벤트에 대한 트래픽 변수를 사용할 수 없습니다. 따라서 AEM 6.2 Forms 또는 이전 버전에서 업그레이드하는 경우 AEM Forms에서 Adobe Analytics 서버로 데이터 전송을 중단하며 적응형 양식에 대한 analytics 보고서를 사용할 수 없습니다. 또한 AEM 6.4 Forms에서는 한 필드에서 체류한 시간에 대한 양식 분석 및 성공 이벤트 버전에 대한 트래픽 변수를 도입합니다. 따라서 AEM Forms 환경에 대한 분석 및 보고서를 다시 구성합니다. 자세한 단계는 [분석 및 보고서 구성](/help/forms/using/configure-analytics-forms-documents.md).

1. 서버가 업그레이드되었는지, 모든 데이터도 마이그레이션되고 정상적으로 작동할 수 있는지 확인하십시오.

   * **번들 상태를 확인합니다.** 모든 번들이 활성 상태인지 확인합니다.
   * **복제 및 역복제 확인:** 마이그레이션된 몇 개의 양식을 게시, 채우기 및 제출합니다. 제출된 데이터도 확인합니다.
   * **관리자 및 개발자 사용자 인터페이스에 대한 액세스 권한 확인:** 관리 계정에서 AEM 인스턴스에 로그인하고 다음 URL에 액세스할 수 있는지 확인하십시오.

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   AEM 6.4 Forms에서 crx-repository 구조가 변경되었습니다. AEM 6.4 Forms로 업그레이드한 후 새로 만든 사용자 지정에 변경된 경로를 사용하십시오. 변경된 경로의 전체 목록은 [AEM 6.4에서 Forms 저장소 구조 변경](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms 및 AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

에서 직접 업그레이드 경로 **AEM 6.0 Forms** 및 **AEM 6.1 Forms** AEM 6.4 Forms으로 이동할 수 없습니다. 중간 작업 수행 [AEM 6.2로 업그레이드 Forms](/help/forms/using/upgrade.md) 또는 [AEM 6.3 Forms으로 업그레이드](/help/forms/using/upgrade.md) 그런 다음 AEM 6.2 Forms 또는 AEM 6.3 Forms에서 AEM 6.4 Forms으로 업그레이드합니다.
