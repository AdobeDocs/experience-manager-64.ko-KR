---
title: 업그레이드 후 확인 및 문제 해결
seo-title: 업그레이드 후 확인 및 문제 해결
description: 업그레이드 후 발생할 수 있는 문제를 해결하는 방법을 알아봅니다.
seo-description: 업그레이드 후 발생할 수 있는 문제를 해결하는 방법을 알아봅니다.
uuid: 3f83e8fc-1c45-4ef0-b8da-d29ff483d3d5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: bc8c9aa2-f669-41f3-a526-6146ff5cf0cd
feature: 업그레이드
exl-id: edd6e933-59ed-4d7e-8934-7e2ec485cfb9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1888'
ht-degree: 0%

---

# 업그레이드 후 확인 및 문제 해결{#post-upgrade-checks-and-troubleshooting}

## 업그레이드 후 확인 {#post-upgrade-checks}

[즉석 업그레이드](/help/sites-deploying/in-place-upgrade.md) 다음에 나오는 다음 활동을 실행하여 업그레이드를 완료해야 합니다. AEM이 6.4 jar로 시작되었으며 업그레이드된 코드 베이스가 배포되었다고 가정합니다.

* [업그레이드 성공 로그 확인](#verify-logs-for-upgrade-success)

* [OSGi 번들 확인](#verify-osgi-bundles)

* [Oak 버전 확인](#verify-oak-version)

* [사전 업그레이드 백업 폴더의 Inspect](#inspect-preupgradebackup-folder)

* [페이지의 초기 유효성 검사](#initial-validation-of-pages)
* [AEM 서비스 팩 적용](#apply-aem-service-packs)

* [AEM 기능 마이그레이션](#migrate-aem-features)

* [예약된 유지 관리 구성 확인](#verify-scheduled-maintenance-configurations)

* [복제 에이전트 활성화](#enable-replication-agents)

* [사용자 지정 예약된 작업 활성화](#enable-custom-scheduled-jobs)

* [테스트 계획 실행](#execute-test-plan)

### 업그레이드 성공 로그 확인 {#verify-logs-for-upgrade-success}

**upgrade.log**

이전에는 인스턴스의 사후 업그레이드 상태를 검사하기 위해 다양한 로그 파일, 저장소의 일부 및 론치 패드를 신중하게 검사해야 했습니다. 업그레이드 후 보고서를 생성하면 라이브로 전환하기 전에 결함이 있는 업그레이드를 감지하는 데 도움이 됩니다.

이 기능의 주요 목적은 업그레이드의 성공을 평가하는 데 필요한 여러 종단점에서 수동 해석 또는 복잡한 구문 분석 로직의 필요성을 줄이는 것입니다. 이 솔루션은 외부 자동화 시스템에서 업데이트 성공 또는 식별된 실패 시 대응하도록 모호한 정보를 제공하는 것을 목표로 합니다.

특히 다음과 같은 이점을 제공합니다.

* 업그레이드 프레임워크에서 감지한 업그레이드 실패가 단일 업그레이드 보고서에 집중될 수 있습니다.
* 업그레이드 보고서에는 필요한 수동 작업에 대한 표시기가 포함되어 있습니다.

이를 위해 `upgrade.log` 파일에서 로그가 생성되는 방식이 변경되었습니다.

다음은 업그레이드 중에 오류가 표시되지 않는 샘플 보고서입니다.

![1487887443006](assets/1487887443006.png)

다음은 업그레이드 프로세스 중에 설치되지 않은 번들을 보여주는 샘플 보고서입니다.

![1487887532730](assets/1487887532730.png)

**error.log**

target 버전 jar를 사용하여 AEM을 시작하는 동안 및 다음에 error.log를 신중하게 검토해야 합니다. 경고나 오류는 검토해야 합니다. 일반적으로 로그 시작 부분에서 문제를 찾는 것이 가장 좋습니다. 나중에 로그에서 발생하는 오류는 파일 초기에 호출된 근본 원인에 의해 부작용이 될 수 있습니다. 반복된 오류 및 경고가 발생하는 경우 업그레이드](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-upgrade)에 대한 문제 분석에 대해 아래를 참조하십시오.[

### OSGi 번들 확인 {#verify-osgi-bundles}

OSGi 콘솔 `/system/console/bundles`로 이동하여 번들이 시작되지 않았는지 확인합니다. 번들이 설치된 상태에 있는 경우 루트 문제를 확인하려면 `error.log` 을 참조하십시오.

### Oak 버전 확인 {#verify-oak-version}

업그레이드 후에 Oak 버전이 **1.8.2**&#x200B;로 업데이트된 것을 볼 수 있습니다. Oak 버전을 확인하려면 OSGi 콘솔로 이동하고 Oak 번들과 연결된 버전을 확인합니다.Oak Core, Oak Commons, Oak Segment Tar.

### Inspect PreUpgradeBackup 폴더 {#inspect-preupgradebackup-folder}

업그레이드 중에 AEM은 사용자 지정을 백업하고 `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>` 아래에 저장합니다. CRXDE Lite에서 이 폴더를 보려면 [일시적으로 CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md)을 활성화해야 할 수 있습니다.

타임스탬프가 있는 폴더에는 `mergeStatus` 라는 속성(`COMPLETED` 값)이 있어야 합니다. **to-process** 폴더는 비어 있어야 하며 **overwrite** 노드는 업그레이드 중에 덮어쓴 노드를 나타냅니다. **잔류물** 노드 아래의 콘텐츠는 업그레이드 중에 안전하게 병합할 수 없는 콘텐츠를 나타냅니다. 구현이 하위 노드에 종속되어 있는 경우(업그레이드된 코드 패키지로 아직 설치되지 않은 경우) 수동으로 병합해야 합니다.

스테이지 또는 프로덕션 환경에서 이 연습에 따라 CRXDE Lite을 비활성화합니다.

### 페이지 {#initial-validation-of-pages} 의 초기 유효성 검사

AEM의 여러 페이지에 대해 초기 유효성 검사를 수행합니다. 작성 환경을 업그레이드하는 경우 시작 페이지 및 시작 페이지( `/aem/start.html`, `/libs/cq/core/content/welcome.html`)를 엽니다. 작성자 및 게시 환경 모두에서 몇 개의 애플리케이션 페이지를 열고 올바르게 렌더링되는 테스트 연기 테스트를 엽니다. 문제가 발생하면 `error.log` 을 참조하여 문제를 해결하십시오.

### AEM 서비스 팩 적용 {#apply-aem-service-packs}

관련 AEM 6.4 서비스 팩이 릴리스된 경우 적용합니다.

### AEM 기능 마이그레이션 {#migrate-aem-features}

AEM의 몇 가지 기능을 사용하려면 업그레이드 후 추가 단계가 필요합니다. 이러한 기능과 단계를 AEM 6.4에서 마이그레이션하기 위한 전체 목록은 [업그레이드 코드 및 사용자 지정](/help/sites-deploying/upgrading-code-and-customizations.md) 페이지에서 확인할 수 있습니다.

### 예약된 유지 관리 구성 확인 {#verify-scheduled-maintenance-configurations}

#### 데이터 저장소 가비지 수집 활성화 {#enable-data-store-garbage-collection}

파일 데이터 저장소를 사용하는 경우 데이터 저장소 가비지 수집 작업이 활성화되어 주별 유지 관리 목록에 추가되어 있는지 확인합니다. 지침은 [여기](/help/sites-administering/data-store-garbage-collection.md)에 요약되어 있습니다.

>[!NOTE]
>
>S3 사용자 지정 데이터 저장소 설치나 공유 데이터 저장소를 사용하는 경우에는 권장되지 않습니다.

#### 온라인 개정 정리 활성화 {#enable-online-revision-cleanup}

MongoMK 또는 새 TarMK 세그먼트 형식을 사용하는 경우, 개정 정리 작업이 활성화되고 일별 유지 관리 목록에 추가되어야 합니다. 지침 설명 [여기](/help/sites-deploying/revision-cleanup.md)에 나와 있습니다.

### 테스트 계획 실행 {#execute-test-plan}

**테스트 절차** 섹션 아래에 정의된 [업그레이드 코드 및 사용자 지정](/help/sites-deploying/upgrading-code-and-customizations.md)에 대해 자세한 테스트 계획을 실행합니다.

### 복제 에이전트 활성화 {#enable-replication-agents}

게시 환경이 완전히 업그레이드되고 검증되면 작성 환경에서 복제 에이전트를 활성화합니다. 에이전트가 각 게시 인스턴스에 연결할 수 있는지 확인합니다. 이벤트 순서에 대한 자세한 내용은 [업그레이드 프로시저](/help/sites-deploying/upgrade-procedure.md)를 참조하십시오.

### 사용자 지정 예약 작업 활성화 {#enable-custom-scheduled-jobs}

코드 베이스의 일부로 예약된 작업은 이 시점에서 활성화할 수 있습니다.

## 업그레이드 &lt;A0/> 관련 문제 분석{#analyzing-issues-with-upgrade}

이 섹션에는 AEM 6.4로의 업그레이드 절차에 따라 발생할 수 있는 몇 가지 문제 시나리오가 포함되어 있습니다.

이러한 시나리오는 업그레이드와 관련된 문제의 근본 원인을 추적하는 데 도움이 되어야 하며 프로젝트 또는 제품별 문제를 식별하는 데 도움이 되어야 합니다.

### {#dynamic-media-cloud-configuration} 업그레이드 후 Dynamic Media Cloud 구성 다시 만들기

이전 버전에서 AEM 6.4로 업그레이드한 후 이전 설정에서 Dynamic Media Cloud Configuration은 AEM 6.4 TouchUI에서 액세스할 수 없게 될 수 있습니다. 이 문제를 해결하려면 CRXDE Lite을 사용하여 이전 설정을 제거한 다음 새 Dynamic Media 클라우드 구성을 만듭니다. AEM 6.4](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)에서 [Dynamic Media 저장소 구조 조정을 참조하십시오.

### 저장소 마이그레이션 실패 {#repository-migration-failing-}

CRX2에서 Oak로 데이터 마이그레이션은 CQ 5.4를 기반으로 하는 소스 인스턴스로 시작하는 모든 시나리오에 대해 실행 가능한 것이어야 합니다. `repository.xml` 준비를 포함하는 이 문서의 업그레이드 지침을 정확히 따라야 합니다. JAAS를 통해 사용자 지정 사용자 정의 인증자가 시작되지 않도록 하고 마이그레이션을 시작하기 전에 인스턴스가 불일치를 확인했는지 확인하십시오.

마이그레이션이 계속 실패하면 `upgrade.log`을(를) 검사하여 근본 원인이 무엇인지 파악할 수 있습니다. 문제를 아직 알 수 없는 경우 고객 지원 센터에 보고하십시오.

### 업그레이드가 {#the-upgrade-did-not-run}을 실행하지 않았습니다.

준비 단계를 시작하기 전에 java -jar aem-quickstart.jar 명령을 사용하여 먼저 **source** 인스턴스를 실행하여 실행해야 합니다. quickstart.properties 파일이 제대로 생성되었는지 확인하기 위해 필요합니다. 누락된 경우 업그레이드가 작동하지 않습니다. 또는 소스 인스턴스의 설치 폴더에서 `crx-quickstart/conf` 을 확인하여 파일이 있는지 확인할 수 있습니다. 또한 AEM에서 업그레이드를 시작할 때 java -jar aem-quickstart.jar 명령을 사용하여 실행해야 합니다. 시작 스크립트에서 시작하는 것은 업그레이드 모드에서 AEM을 시작하지 않습니다.

### 패키지 및 번들이 {#packages-and-bundles-fail-to-update-} 업데이트에 실패했습니다.

업그레이드 중에 패키지를 설치하지 못할 경우 패키지가 포함하는 번들도 업데이트되지 않습니다. 이 문제 카테고리는 일반적으로 데이터 저장소가 잘못 구성되어 있습니다. 또한 error.log에 **ERROR** 및 **WARN** 메시지로 표시됩니다. 대부분의 경우 기본 로그인이 작동하지 않을 수 있으므로 구성 문제를 검사하고 찾기 위해 CRXDE를 직접 사용할 수 있습니다.

### 일부 AEM 번들이 활성 상태 {#some-aem-bundles-are-not-switching-to-the-active-state}로 전환되지 않습니다.

번들이 시작되지 않는 경우 부족한 종속성을 확인해야 합니다.

이 문제가 있지만 실패한 패키지 설치를 기반으로 하여 번들을 업그레이드하지 않으면 새 버전에 호환되지 않는 것으로 간주됩니다. 이 문제를 해결하는 방법에 대한 자세한 내용은 위의 **패키지 및 번들이 업데이트되지 않음**&#x200B;을 참조하십시오.

업그레이드되지 않은 번들을 감지하려면 새 AEM 6.4 인스턴스의 번들 목록을 업그레이드된 인스턴스와 비교하는 것이 좋습니다. 이렇게 하면 `error.log`에서 검색할 항목의 범위가 더 좁습니다.

### 사용자 지정 번들이 활성 상태 {#custom-bundles-not-switching-to-the-active-state}로 전환되지 않음

사용자 지정 번들이 활성 상태로 전환되지 않는 경우 변경 API를 가져오지 않는 코드가 있을 수 있습니다. 이렇게 되면 대부분 충족되지 않은 종속성이 발생합니다.

제거된 API는 이전 릴리스 중 하나에서 더 이상 사용되지 않는 것으로 표시되어야 합니다. 이 사용 중단 알림에서 코드의 직접 마이그레이션에 대한 지침을 찾을 수 있습니다. Adobe은 버전이 변경 사항을 나타낼 수 있도록 가능한 시맨틱 버전 지정을 목표로 합니다.

문제를 일으킨 변경이 절대적으로 필요한지 확인하고 그렇지 않으면 되돌리는 것이 가장 좋습니다. 또한 엄격한 시맨틱 버전 관리를 통해 패키지 내보내기의 버전 증가가 필요 이상으로 증가했는지 확인하십시오.

### 플랫폼 UI {#malfunctioning-platform-ui}가 작동하지 않음

업그레이드 후 제대로 작동하지 않는 특정 UI 기능의 경우 먼저 인터페이스의 사용자 지정 오버레이를 확인해야 합니다. 일부 구조가 변경되었을 수 있으며 오버레이에 업데이트가 필요하거나 더 이상 사용되지 않을 수 있습니다.

다음으로, 클라이언트 라이브러리에 연결된 사용자 지정 추가 확장으로 추적될 수 있는 Javascript 오류를 확인합니다. AEM 레이아웃에 문제를 일으킬 수 있는 사용자 지정 CSS에도 동일하게 적용할 수 있습니다.

마지막으로 Javascript에서 처리할 수 없을 수 있는 잘못된 구성을 확인합니다. 일반적으로 확장이 잘못 비활성화된 경우가 있습니다.

### 사용자 지정 구성 요소, 템플릿 또는 UI 확장 기능이 작동하지 않음 {#malfunctioning-custom-components-templates-or-ui-extensions}

대부분의 경우 이러한 문제에 대한 근본 원인은 시작되지 않은 번들이나 구성 요소를 처음 사용할 때 발생하는 문제가 발생하는 유일한 차이로 인해 패키지가 설치되지 않은 번들에 대해 동일합니다.

잘못된 사용자 지정 코드를 처리하는 방법은 원인을 확인하기 위해 먼저 연기 테스트를 수행하는 것입니다. 찾으면 이를 수정하는 방법에 대해 이 문서의 [링크] 섹션에 있는 권장 사항을 살펴보십시오.

### 다음 {#missing-customizations-under-etc}에 사용자 지정 항목이 없습니다.

`/apps` 및  `/libs` 는 업그레이드에 의해 잘 처리되지만, 업그레이드  `/etc`   `/var/upgrade/PreUpgradeBackup` 후 의 변경 사항을 수동으로 복원해야 할 수 있습니다. 수동으로 병합해야 하는 모든 내용이 이 위치에 있는지 확인하십시오.

### error.log 및 upgrade.log {#analyzing-the-error-log-and-upgrade-log} 분석

대부분의 경우 문제의 원인을 찾기 위해 로그에 오류가 있는지 확인해야 합니다. 그러나 업그레이드 시 이전 번들이 제대로 업그레이드되지 않을 수 있으므로 종속성 문제를 모니터링해야 합니다.

이 작업을 수행하는 가장 좋은 방법은 현재 직면하고 있는 문제와 관련이 없는 것으로 예상되는 모든 메시지를 제거하여 error.log를 제거하는 것입니다. grep와 같은 도구를 사용하여 다음을 수행할 수 있습니다.

```shell
grep -v UnrelatedErrorString
```

일부 오류 메시지는 즉시 설명되지 않을 수 있습니다. 이 경우 오류가 발생하는 컨텍스트를 보면 오류가 만들어진 위치를 이해하는 데 도움이 됩니다. 다음 아이콘을 사용하여 오류를 분리할 수 있습니다.

* `grep -B` 오류 앞에 줄을 추가하는 경우

또는

* `grep -A` 추가.

이 상태로 이어지는 유효한 사례가 있을 수 있고 응용 프로그램에서 이 오류가 실제 오류인지 확인할 수 없으므로 몇 가지 오류도 WARN 메시지를 찾을 수 있습니다. 이 메시지들도 반드시 참고하세요.

### Adobe 지원 {#contacting-adobe-support}에 연결하는 중

이 페이지의 조언 내용을 완료했지만 여전히 문제가 표시되는 경우 Adobe 지원에 문의하십시오. 지원 엔지니어가 사용 중인 경우 최대한 많은 정보를 제공하려면 업그레이드의 upgrade.log 파일을 포함해야 합니다.
