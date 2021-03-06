---
title: 클러스터 환경에서 백업 및 복원 전략
seo-title: 클러스터 환경에서 백업 및 복원 전략
description: AEM Forms 구현에서 다른 데이터베이스에 추가 사용자 지정 데이터를 저장하는 경우 AEM Forms 데이터와 계속 동기화되도록 이 데이터를 백업하는 전략을 구현해야 합니다.
seo-description: AEM Forms 구현에서 다른 데이터베이스에 추가 사용자 지정 데이터를 저장하는 경우 AEM Forms 데이터와 계속 동기화되도록 이 데이터를 백업하는 전략을 구현해야 합니다.
uuid: c29b989c-30ed-4a8e-bab8-9b7746291a33
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c332985b-4556-4056-961a-fce2356da88d
exl-id: 432221c9-4b78-4d0d-bf22-b56810bf4256
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 0%

---

# 클러스터 환경에서 백업 및 복원 전략 {#strategy-for-backup-and-restore-in-a-clustered-environment}

>[!NOTE]
>
>AEM Forms 구현에서 다른 데이터베이스에 추가 사용자 지정 데이터를 저장하는 경우 AEM Forms 데이터와 계속 동기화되도록 이 데이터를 백업하는 전략을 구현해야 합니다. 또한 추가적인 데이터베이스가 동기화되지 않는 시나리오를 처리할 수 있을 정도로 강력하도록 응용 프로그램을 설계해야 합니다. 일관된 상태를 유지하기 위해 수행되는 모든 데이터베이스 작업은 트랜잭션 컨텍스트에서 수행하는 것이 좋습니다.

오류가 발생한 경우 복구하려면 AEM Forms 시스템의 다음 부분을 백업해야 합니다.

* AEM Forms에서 사용하는 데이터베이스
* 오랫동안 지속되었던 데이터 및 기타 영구 문서를 보유한 GDS
* AEM 데이터베이스(crx-repository)

>[!NOTE]
>
>고객 글꼴, 커넥터 데이터 등과 같이 AEM Forms 설정에서 사용 중인 다른 데이터를 백업해야 합니다.

## 클러스터된 환경 백업 {#back-up-a-clustered-environment}

이 항목에서는 AEM Forms 클러스터형 환경을 백업하기 위한 다음 전략에 대해 설명합니다.

* 다운타임으로 오프라인 백업
* 다운타임이 없는 오프라인 백업(종료 중인 보조 노드의 백업)
* 다운타임이 없고 응답 지연이 있는 온라인 백업
* Bootstrap 속성 파일 백업

### 다운타임이 {#offline-backup-with-downtime}인 오프라인 백업

1. 전체 클러스터 및 관련 서비스를 종료합니다. ( [서비스 시작 및 중지 참조](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. 모든 노드에서 데이터베이스, GDS 및 커넥터를 백업합니다. ([백업 및 복구할 파일 참조](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. AEM 리포지토리를 오프라인으로 백업하려면 다음 단계를 수행하십시오.

   1. 각 클러스터 노드에 대해 클러스터 노드 ID가 포함된 파일을 백업합니다.
   1. 하위 디렉토리를 포함하여 보조 클러스터 노드의 모든 파일을 백업합니다.
   1. 각 클러스터 노드의 저장소/시스템 ID를 별도로 백업합니다.

   자세한 단계는 [백업 및 복원](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)을 참조하십시오.

1. 고객 글꼴과 같은 다른 데이터를 백업합니다.
1. 클러스터를 다시 시작합니다.

### 다운타임이 없는 오프라인 백업 {#offline-backup-with-no-downtime}

1. 순환 백업 모드를 시작합니다. ( [백업 모드 입력](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes) 참조)

   복구 후 롤링 백업 모드를 종료해야 합니다.

1. AEM과 관련하여 클러스터의 보조 노드를 모두 종료합니다. ( [서비스 시작 및 중지 참조](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. 모든 노드에서 데이터베이스, GDS 및 커넥터를 백업합니다. ([백업 및 복구할 파일 참조](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. AEM 리포지토리를 오프라인으로 백업하려면 다음 단계를 수행하십시오.

   1. 각 클러스터 노드에 대해 클러스터 노드 ID가 포함된 파일을 백업합니다.
   1. 하위 디렉토리를 포함하여 보조 클러스터 노드의 모든 파일을 백업합니다.
   1. 각 클러스터 노드의 repository/system.id을 별도로 백업합니다.

   자세한 단계는 [백업 및 복원](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)을 참조하십시오.

1. 고객 글꼴과 같은 다른 데이터를 백업합니다.
1. 클러스터를 다시 시작합니다.

### 다운타임이 없고 응답 {#online-backup-with-no-downtime-but-delay-in-response} 지연이 있는 온라인 백업

1. 순환 백업 모드를 시작합니다. ( [백업 모드 입력](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes) 참조)

   복구 후 롤링 백업 모드를 종료해야 합니다.

1. AEM과 관련하여 클러스터의 보조 노드를 모두 종료합니다. ( [서비스 시작 및 중지 참조](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. 모든 노드에서 데이터베이스, GDS 및 커넥터를 백업합니다. ([백업 및 복구할 파일 참조](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. 다음 단계를 수행하여 AEM 리포지토리를 온라인으로 백업합니다.

   1. 각 클러스터 노드에 대해 cluster_node.id가 포함된 파일을 백업합니다.
   1. 각 클러스터 노드의 repository/system.id을 별도로 백업합니다.
   1. 보조 노드에서 리포지토리의 온라인 백업을 수행하여 자세한 단계는 온라인 백업을 참조하십시오.

1. 고객 글꼴과 같은 다른 데이터를 백업합니다.
1. 클러스터를 다시 시작합니다.

### Bootstrap 속성 파일 {#back-up-the-bootstrap-properties-file} 백업

AEM 클러스터를 생성하면 모든 보조 노드에 대한 속성 파일이 애플리케이션 서버에 생성됩니다. Bootstrap 속성 파일을 백업하는 것이 좋습니다. 이 파일은 애플리케이션 서버의 다음 위치에서 찾을 수 있습니다.

* JBoss:BIN 디렉토리에
* WebLogic:도메인 디렉토리
* WebSphere:프로필 디렉토리

AEM 보조 노드의 재해 복구 시나리오를 위해 파일을 백업하고 복원된 경우 애플리케이션 서버의 지정된 위치에서 교체해야 합니다.

## 클러스터된 환경에서 복구 {#recovery-in-a-clustered-environment}

전체 클러스터 또는 단일 노드가 실패할 경우 백업을 사용하여 복원해야 합니다.

단일 노드 복구를 위해 단일 노드를 종료하고 단일 노드 복구 절차를 실행해야 합니다.

데이터베이스 충돌과 같은 오류로 인해 전체 클러스터가 실패하는 경우 다음 단계를 수행해야 합니다. 복원은 사용된 백업 방법에 따라 다릅니다.

### 단일 노드 {#restoring-a-single-node} 복원

1. 손상된 노드를 중지합니다.

   >[!NOTE]
   >
   >손상된 노드가 AEM 주 노드인 경우 전체 클러스터 노드를 종료합니다.

1. 시스템 이미지에서 물리적 시스템을 다시 생성합니다.
1. 이미지가 만들어진 이후에 적용된 AEM Forms에 패치 또는 업데이트를 적용합니다. 이 정보는 백업 절차 중에 기록됩니다. AEM Forms는 시스템을 백업할 때와 동일한 패치 수준으로 복구해야 합니다.
1. (*선택 사항*) 다른 모든 노드가 제대로 작동하는 경우 AEM 저장소가 또한 손상되었을 수 있습니다. 이 경우 AEM 저장소의 error.log 파일에 저장소 동기화 해제 메시지가 표시됩니다.

   저장소를 복원하려면 다음 단계를 수행합니다.

   >[!NOTE]
   >
   >압축된 crx-repository 백업을 온라인 상태로 전환한 경우 임의의 위치에서 압축을 풀고 오프라인 복원 프로세스를 따릅니다.

   1. 노드의 clusterNode 디렉토리에서 저장소, 공유, 버전 및 작업 공간 디렉토리를 삭제합니다.
   1. 클러스터 노드(하위 디렉토리 포함)의 백업을 노드에 복원합니다.
   1. 노드에서 clusterNode/revision.log 파일을 삭제합니다.
   1. 있는 경우 노드에서 .lock을 삭제합니다.
   1. 있는 경우 노드에서 repository/system.id 을 삭제합니다.
   1. 있는 경우 노드에서 파일 &amp;ast;&amp;ast;/listener.properties을 삭제합니다.
   1. 개별 클러스터 노드의 경우 repository/cluster_node.id을 복원합니다.

>[!NOTE]
>
>다음 사항을 고려하십시오.

* 실패한 노드가 AEM 기본 노드인 경우 보조 저장소 폴더(crx-repository\crx.000(0000은 임의의 자릿수)의 모든 컨텐츠를 crx-repository\ 저장소 폴더로 복사하고 보조 저장소 폴더를 삭제합니다.
* 클러스터 노드를 다시 시작하기 전에 주 노드에서 저장소 /clustered.txt을 삭제해야 합니다.
* 기본 노드가 먼저 시작되고 완전히 시작되면 다른 노드를 시작합니다.

### 전체 클러스터 {#restoring-the-entire-cluster} 복원

1. 모든 클러스터 노드를 중지합니다.
1. 시스템 이미지에서 물리적 시스템을 다시 생성합니다.
1. 이미지가 만들어진 이후에 적용된 AEM FormsAEM 양식에 패치 또는 업데이트를 적용합니다. 이 정보는 백업 절차의 1단계에서 기록되었습니다. AEM Forms는 시스템을 백업할 때와 동일한 패치 수준으로 복구해야 합니다.
1. 데이터베이스, GDS 및 커넥터를 복원합니다.
1. AEM 저장소를 오프라인으로 복구하려면 다음을 수행하십시오.

   >[!NOTE]
   >
   >압축된 crx-repository 백업을 온라인 상태로 전환한 경우 임의의 위치에서 압축을 풀고 오프라인 복원 프로세스를 따릅니다.

   1. 모든 클러스터 노드에서 clusterNode 디렉토리의 저장소, 공유, 버전 및 작업 공간 디렉토리를 삭제합니다.
   1. 공유 디렉터리에서 모든 파일 및 디렉터리를 삭제합니다.
   1. 클러스터 노드(하위 디렉토리 포함)의 백업을 하나의 클러스터 노드로 복원합니다.
   1. 복원된 클러스터 노드의 모든 파일을 다른 모든 클러스터 노드에 복사합니다. 완료되면 각 클러스터 노드에 동일한 데이터가 포함됩니다.
   1. 모든 클러스터 노드에서 clusterNode/revision.log 파일을 삭제합니다.
   1. 있는 경우 모든 클러스터 노드에서 .lock을 삭제합니다.
   1. 있는 경우 repository/system.id 모든 클러스터 노드를 삭제합니다.
   1. 모든 클러스터 노드에서 파일 &amp;ast;&amp;ast;/listener.properties을 삭제합니다(있는 경우).
   1. 개별 클러스터 노드의 경우 repository/cluster_node.id을 복원합니다.

>[!NOTE]
>
>다음 사항을 고려하십시오.

* 실패한 노드가 AEM 기본 노드인 경우 보조 저장소 폴더의 모든 컨텐츠를 복사합니다(crx-repository\crx.0000(여기서 0000은 임의의 자릿수가 될 수 있음). crx-repository\ repository 폴더에 복사합니다.
* 클러스터 노드를 다시 시작하기 전에 주 노드에서 저장소 /clustered.txt을 삭제해야 합니다.
* 기본 노드가 먼저 시작되고 완전히 시작되면 다른 노드를 시작합니다.

## 서신 관리 솔루션 게시 노드 {#back-up-and-restore-correspondence-management-solution-publish-node} 백업 및 복원

게시자 노드는 클러스터된 환경에서 1차-2차 관계가 없습니다. [백업 및 복원](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)을 수행하여 게시자 노드의 백업을 수행할 수 있습니다.

### 단일 게시자 노드 {#recover-a-single-publisher-node} 복구

1. 복구해야 하는 노드를 종료하고 노드가 다시 작동될 때까지 게시 활동을 수행하지 않습니다.
1. [백업] 복원(https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html#Restoring the Backup)을 사용하여 게시 노드를 복원합니다.

### 클러스터 복구 {#recover-a-cluster}

1. 클러스터를 종료합니다.
1. [백업] 복원(https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html#Restoring the Backup)을 사용하여 게시 노드를 복원합니다.
1. 기본 노드를 시작하고 작성 클러스터의 보조 노드를 시작합니다.
