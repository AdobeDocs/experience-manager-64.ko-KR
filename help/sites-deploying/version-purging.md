---
title: 버전 제거
seo-title: 버전 제거
description: 이 문서에서는 버전 제거를 위한 사용 가능한 옵션에 대해 설명합니다.
seo-description: 이 문서에서는 버전 제거를 위한 사용 가능한 옵션에 대해 설명합니다.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
translation-type: tm+mt
source-git-commit: 0dced2f56fcebfb03fa6264e98cd686e8e7902c6
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 1%

---


# 버전 제거{#version-purging}

표준 설치 AEM에서는 컨텐츠를 업데이트한 후 페이지를 활성화할 때 페이지 또는 노드의 새 버전을 만듭니다.

>[!NOTE]
>
>컨텐츠가 변경되지 않으면 페이지가 활성화되었으나 새 버전이 만들어지지 않는다는 메시지가 표시됩니다

사이드 킥의 버전 관리 **탭을 사용하여 요청 시** 추가 버전을 만들 수 있습니다. 이러한 버전은 저장소에 저장되며 필요한 경우 복원할 수 있습니다.

이러한 버전은 삭제되지 않으므로 저장소 크기가 시간이 지남에 따라 증가하므로 관리해야 합니다.

AEM에는 저장소 관리에 도움이 되는 다양한 메커니즘이 포함되어 있습니다.

* 버전 [관리자](#version-manager)

   새 버전이 만들어질 때 이전 버전을 제거하도록 구성할 수 있습니다.

* 버전 [제거](/help/sites-deploying/monitoring-and-maintaining.md#version-purging) 도구

   저장소 모니터링 및 유지 관리의 일부로 사용됩니다.

   이 매개 변수를 사용하면 다음 매개 변수에 따라 노드의 이전 버전이나 노드 계층을 제거할 수 있습니다.

   * 저장소에 보관될 최대 버전 수입니다.

      이 수를 초과하면 가장 오래된 버전은 제거됩니다.

   * 저장소에 보관되는 모든 버전의 최대 사용 연령

      버전 사용 기간이 이 값을 초과하면 저장소에서 삭제됩니다.

* 버전 [삭제 유지 관리 작업](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). 버전 삭제 유지 관리 작업을 예약하여 이전 버전을 자동으로 삭제할 수 있습니다. 따라서 버전 제거 도구를 수동으로 사용할 필요가 없습니다.

>[!CAUTION]
>
>저장소 크기를 최적화하려면 버전 삭제 작업을 자주 실행해야 합니다. 제한된 트래픽 양이 있는 경우 업무 시간 이외의 시간에 작업을 예약해야 합니다.

## 버전 관리자 {#version-manager}

제거 도구를 통해 명시적 제거 외에 새 버전이 생성될 때 이전 버전을 제거하도록 버전 관리자를 구성할 수 있습니다.

버전 관리자를 구성하려면 다음을 위한 구성을 만듭니다.

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

다음 옵션을 사용할 수 있습니다.

* `versionmanager.createVersionOnActivation` (부울, 기본값: true)

   페이지를 활성화할 때 버전을 만들지 여부.

   버전 관리자가 부여하는 버전 생성을 억제하도록 복제 에이전트를 구성하지 않으면 버전이 만들어집니다

   버전은 버전 관리자.ivPaths(아래 참조)에 포함된 경로에서 활성화가 발생하는 경우에만 생성됩니다.

* `versionmanager.ivPaths` (문자열[], 기본값: {&quot;/&quot;})

   versionmanager.createVersionOnActivation이 true인 경우 활성화 시 암시적으로 생성되는 경로입니다.

* `versionmanager.purgingEnabled` (부울, 기본값: false)

   새 버전을 만들 때 제거를 사용할지 여부

* `versionmanager.purgePaths` (문자열[], 기본값: {&quot;/content&quot;})

   새 버전을 만들 때 버전을 삭제하는 경로에 대해 설명합니다.

* `versionmanager.maxAgeDays` (int, default: 30)

   제거 시 이 값보다 오래된 버전이 제거됩니다. 이 값이 1보다 작으면 버전 기간을 기준으로 제거를 수행하지 않습니다

* `versionmanager.maxNumberVersions` (int, default 5)

   제거 시 최신 버전보다 오래된 버전이 모두 제거됩니다. 이 값이 1보다 작으면 버전 수를 기준으로 제거를 수행하지 않습니다

* `versionmanager.minNumberVersions` (int, 기본값 0)

   연령에 상관없이 유지할 최소 버전 수 이 값이 1보다 작은 값으로 설정된 경우 최소 버전 수는 유지됩니다.

>[!NOTE]
>
>저장소에 여러 버전을 보관하는 것은 권장되지 않습니다. 따라서 버전 제거 작업을 구성할 때 너무 많은 버전을 삭제에서 제외하지 않도록 주의하십시오. 그렇지 않으면 저장소 크기가 제대로 최적화되지 않습니다. 비즈니스 요구 사항으로 인해 많은 버전을 보유하고 있는 경우 저장소 크기를 최적화하는 다른 방법을 찾으려면 Adobe 지원에 문의하십시오.

### 결합 유지 옵션 {#combining-retention-options}

요구 사항에 따라 어떤 버전을 유지할 것인지( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`) 정의하는 옵션을 결합할 수 있습니다.

예를 들어 유지할 최대 버전 수와 유지할 가장 오래된 버전을 정의할 때 다음을 수행합니다.

* 설정:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* 사용:

   * 지난 60일 이내에 10개 버전 제작
   * 지난 30일 이내에 생성된 버전 3개

* 이것은 다음을 의미합니다.

   * 마지막 3개 버전은 그대로 유지됩니다.

예를 들어 유지할 최대 AND 최소 버전 수와 유지할 가장 오래된 버전을 정의할 때 다음을 수행합니다.

* 설정:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* 사용:

   * 60일 전에 5개 버전 제작

* 이것은 다음을 의미합니다.

   * 3개 버전 유지

## 버전 제거 도구 {#purge-versions-tool}

제거 [버전](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) 도구는 저장소의 노드 버전이나 계층 구조를 제거하기 위한 것입니다. 기본 목적은 노드의 이전 버전을 제거하여 저장소 크기를 줄이는 데 도움이 됩니다.
