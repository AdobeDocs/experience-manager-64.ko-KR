---
title: AEM 양식을 위한 백업 및 복구 전략
seo-title: Backup and recovery strategy for AEM forms
description: 데이터를 백업하고 AEM Forms 데이터와 계속 동기화되도록 하는 전략을 구현하는 방법을 알아봅니다.
seo-description: Learn how to implement a strategy to back up data and ensuring that it remains in sync with the AEM forms data.
uuid: 98fc3115-76e5-4e58-aa30-3601866a441f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f192a8a3-1116-4d32-9b57-b53d532c0dbf
exl-id: ee5b0a82-5dd8-4ea6-885c-6154fd41ef4c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 0%

---

# AEM 양식을 위한 백업 및 복구 전략{#backup-and-recovery-strategy-for-aem-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 구현에서 추가 사용자 지정 데이터를 다른 데이터베이스에 저장하는 경우, 이 데이터를 백업하는 전략을 구현하고 AEM Forms 데이터와 계속 동기화되도록 해야 합니다. 또한 추가적인 데이터베이스가 동기화되지 않는 시나리오를 처리할 수 있을 정도로 강력하도록 응용 프로그램을 설계해야 합니다. 일관된 상태를 유지하기 위해 수행되는 모든 데이터베이스 작업은 트랜잭션 컨텍스트에서 수행하는 것이 좋습니다.

AEM Forms 사용 방법을 식별한 후 백업해야 하는 파일, 백업 빈도 및 사용 가능한 백업 기간을 결정합니다.

>[!NOTE]
>
>AEM Forms 구현의 다른 측면과 마찬가지로, 전체 솔루션이 데이터 손실 없이 정상적으로 작동하도록 하려면 프로덕션 환경에서 사용하기 전에 개발 또는 스테이징 환경에서 백업 및 복구 전략을 개발 및 테스트해야 합니다.

Adobe Experience Manager(AEM)은 AEM Forms의 필수적인 부분입니다. 따라서 AEM을 백업하고 AEM Forms Management 솔루션 및 서비스(예: forms manager는 AEM Forms의 AEM 부분에 저장된 데이터를 기반으로 함)와 동기화해야 합니다.데이터 손실을 방지하려면 AEM Forms 특정 데이터를 백업하여 GDS 및 AEM(저장소)이 데이터베이스 참조와 상호 작용하도록 해야 합니다.데이터베이스, GDS, AEM 및 Content Storage Root 디렉터리는 원본과 동일한 DNS 이름을 가진 컴퓨터로 복원해야 합니다.

## 백업 유형 {#types-of-backups}

AEM 양식 백업 전략에는 두 가지 유형의 백업이 포함됩니다.

**시스템 이미지:** 하드 드라이브나 전체 컴퓨터가 작동하지 않을 경우 컴퓨터의 내용을 복원하는 데 사용할 수 있는 전체 시스템 백업입니다. AEM Forms의 프로덕션 배포 전에만 시스템 이미지 백업이 필요합니다. 기업 내부 정책은 시스템 이미지 백업이 필요한 빈도를 나타냅니다.

**AEM Forms 특정 데이터:** 응용 프로그램 데이터는 데이터베이스, GDS(Global Document Storage) 및 AEM 저장소에 있으며 실시간으로 백업해야 합니다. GDS는 프로세스 내에서 사용되는 오래 지속되는 파일을 저장하는 데 사용되는 디렉토리입니다. 이러한 파일에는 PDF, 정책 또는 양식 템플릿이 포함될 수 있습니다.

>[!NOTE]
>
>Content Services(사용되지 않음)가 설치되어 있으면 컨텐츠 저장소 루트 디렉토리도 백업합니다. 자세한 내용은 [컨텐츠 저장소 루트 디렉토리(Content Services만 해당)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

데이터베이스는 GDS 파일에 대한 양식 객체, 서비스 구성, 프로세스 상태 및 데이터베이스 참조를 저장하는 데 사용됩니다. 데이터베이스에서 문서 저장소를 활성화하면 GDS의 영구 데이터와 문서도 데이터베이스에 저장됩니다. 다음 방법을 사용하여 데이터베이스를 백업 및 복구할 수 있습니다.

* **스냅샷 백업** 모드 는 AEM Forms 시스템이 무기한 또는 지정된 시간 동안 백업 모드를 사용하지 않도록 설정한 후 백업 모드에 있음을 나타냅니다. 스냅샷 백업 모드를 시작하거나 종료하려면 다음 옵션 중 하나를 사용할 수 있습니다. 복구 시나리오 후에는 스냅샷 백업 모드를 사용할 수 없습니다.

   * [관리 콘솔]에서 [백업 설정] 페이지를 사용합니다. 스냅샷 모드를 시작하려면 안전 백업 모드에서 작업 확인란을 선택합니다. 스냅샷 모드를 종료하려면 확인란을 선택 취소합니다.
   * LCBackupMode 스크립트 사용( [데이터베이스, GDS 및 Content Storage Root 디렉토리 백업](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). 스냅샷 백업 모드를 종료하려면 스크립트 인수에서 `continuousCoverage` 매개 변수 대상 `false` 또는 `leaveContinuousCoverage` 선택 사항입니다.
   * 제공된 백업/복구 API를 사용합니다. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **순환 백업** 모드 는 시스템이 항상 백업 모드이며 이전 세션이 해제되는 즉시 새 백업 모드 세션이 시작됨을 나타냅니다. 롤링 백업 모드와 관련된 시간이 없습니다. 롤링 백업 모드를 종료하기 위해 LCBackupMode 스크립트 또는 API가 호출되면 새 롤링 백업 모드 세션이 시작됩니다. 이 모드는 연속 백업을 지원하는 데 유용하지만 오래된 문서와 필요 없는 문서를 GDS 디렉토리에서 지울 수 있습니다. 백업 및 복구 페이지를 통해 롤링 백업 모드가 지원되지 않습니다. 복구 시나리오 후에도 순환 백업 모드가 계속 활성화됩니다. LCBackupMode 스크립트를 `leaveContinuousCoverage` 선택 사항입니다.

>[!NOTE]
>
>롤링 백업 모드를 즉시 종료하면 새 백업 모드 세션이 시작됩니다. 롤링 백업 모드를 완전히 비활성화하려면 `leaveContinuousCoverage` 스크립트의 옵션입니다. 이 옵션은 기존 롤링 백업 세션을 덮어씁니다. 스냅샷 백업 모드에서는 일반적으로 백업 모드를 종료할 수 있습니다.

데이터 손실을 방지하려면 GDS 및 Content Storage Root 디렉토리 문서가 데이터베이스 참조와 상호 연관되도록 AEM Forms 특정 데이터를 백업해야 합니다.

>[!NOTE]
>
>GDS가 데이터베이스가 아닌 파일 시스템에 저장되면 GDS 백업 전에 데이터베이스 백업을 수행합니다.

## 백업 및 복구에 대한 특별한 고려 사항 {#special-considerations-for-backup-and-recovery}

다음 변경 사항으로 인해 AEM Forms를 다른 환경으로 복구해야 하는 경우 다음 지침을 사용하십시오.

* AEM Forms 서버의 IP 주소, 호스트 이름 또는 포트 변경
* 드라이브 문자 또는 디렉터리 경로에서 변경
* 다른 데이터베이스 호스트, 포트 또는 이름으로 변경

일반적으로 이러한 복구 시나리오는 응용 프로그램 서버, 데이터베이스 서버 또는 Forms 서버를 호스팅하는 서버의 하드웨어 오류로 인해 발생합니다. 이 섹션에 설명된 AEM Forms 관련 구성 외에도 AEM Forms 서버의 호스트 이름 또는 IP 주소가 변경되는 경우 로드 밸런서 및 방화벽과 같은 AEM Forms 배포의 다른 부분에 필요한 변경을 수행해야 합니다.

### 변경할 수 없는 사항 {#what-cannot-be-changed}

데이터베이스 서버와 다른 많은 매개 변수를 변경할 수 있지만 백업에서 AEM Forms를 복구할 때는 애플리케이션 서버 유형이나 데이터베이스 유형을 변경할 수 없습니다. 예를 들어 AEM Forms 백업을 복구하는 경우에는 응용 프로그램 서버를 JBoss에서 WebLogic으로 또는 데이터베이스를 Oracle에서 DB2로 변경할 수 없습니다. 또한 복구된 AEM Forms는 fonts 디렉토리와 같은 동일한 파일 시스템 경로를 사용해야 합니다.

### 복구 후 다시 시작 {#restarting-after-a-recovery}

복구 후 Forms 서버를 다시 시작하기 전에 다음을 수행하십시오.

1. 유지 관리 모드에서 시스템을 시작합니다.
1. 유지 관리 모드에서 Form Manager가 AEM Forms와 동기화되도록 하려면 다음을 수행하십시오.

   1. https://&lt;*server*>:&lt;*포트*>/lc/fm을 클릭하고 관리자/암호 자격 증명을 사용하여 로그인합니다.
   1. 오른쪽 상단 모서리에서 사용자 이름(이 경우 수퍼 관리자)을 클릭합니다.
   1. 클릭 **관리 옵션**.
   1. 클릭 **시작** 저장소에서 자산을 동기화하려면 다음을 수행하십시오.

1. 클러스터형 환경에서는 보조 노드 앞에 기본 노드(AEM에 대해)가 있어야 합니다.
1. 시스템의 정상 작업이 검증될 때까지 웹, SOAP 또는 EJB 프로세스 이니시에이터와 같은 내부 또는 외부 소스에서 시작된 프로세스가 없는지 확인합니다.

기본 AEM Forms 데이터베이스를 이동하거나 변경하는 경우 AEM Forms 데이터 소스 IDP_DS 및 EDC_DS에 대한 데이터베이스 연결 정보를 업데이트하는 방법에 대한 자세한 내용은 애플리케이션 서버와 관련된 설치 안내서를 검토하십시오.

### AEM 양식 호스트 이름 또는 IP 주소 변경 {#changing-the-aem-forms-hostname-or-ip-address}

클러스터에서 UDP 대신 TCP 캐싱을 사용하는 경우 캐시 로케이터 구성을 업데이트해야 합니다. 애플리케이션 서버와 관련된 구성 안내서에서 &quot;TCP만 사용하여 캐싱 로케이터 구성&quot;을 참조하십시오.

### AEM Forms 노드 파일 시스템 경로 변경 {#changing-the-aem-forms-node-file-system-paths}

독립 실행형 노드의 파일 시스템 경로를 변경하는 경우 환경 설정, 기타 시스템 구성, 사용자 정의 애플리케이션 및 배포된 AEM Forms 애플리케이션에서 적절한 참조를 업데이트해야 합니다. 반면 클러스터의 경우 모든 노드에서 동일한 파일 시스템 경로 구성을 사용해야 합니다. GDS(Global Document Storage) 루트 디렉토리를 설정하고 복구된 데이터베이스와 동기화 중인 복구된 GDS의 사본을 가리키도록 해야 합니다. GDS 경로 설정은 GDS에 애플리케이션 서버를 다시 시작할 때 유지하려는 데이터가 포함될 수 있으므로 중요합니다.

클러스터형 환경에서는 백업 전과 복구 후에 저장소의 파일 시스템 경로 구성이 모든 클러스터 노드에 대해 동일해야 합니다.

를 사용하십시오 `LCSetGDS`스크립트에서 `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` 폴더 - 파일 시스템 경로를 변경한 후 GDS 경로를 설정합니다. 자세한 내용은 `ReadMe.txt` 같은 폴더에 있는 파일을 참조하십시오. 이전 GDS 디렉토리 경로를 사용할 수 없으면 `LCSetGDS` AEM Forms를 시작하기 전에 스크립트를 사용하여 새 경로를 GDS에 설정해야 합니다.

>[!NOTE]
>
>이 환경은 이 스크립트를 사용하여 GDS 위치를 변경해야 하는 유일한 환경입니다. AEM Forms가 실행되는 동안 GDS 위치를 변경하려면 관리 콘솔을 사용하십시오. (자세한 내용은 [일반 AEM 양식 설정 구성](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*

GDS 경로를 설정한 후 유지 관리 모드에서 Forms 서버를 시작하고 관리 콘솔을 사용하여 새 노드의 나머지 파일 시스템 경로를 업데이트합니다. 필요한 모든 구성이 업데이트되었는지 확인한 후 AEM Forms를 다시 시작하고 테스트합니다.
