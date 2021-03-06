---
title: Oak-run.jar 색인 지정 사용 사례
seo-title: Oak-run.jar 색인 지정 사용 사례
description: Oak-run 도구를 사용하여 색인을 생성하기 위한 다양한 사용자 사례에 대해 알아봅니다.
seo-description: Oak-run 도구를 사용하여 색인을 생성하기 위한 다양한 사용자 사례에 대해 알아봅니다.
uuid: 3c50080d-1e0d-4886-8d37-269f06881eb4
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 084075b8-826d-4f27-9342-35f33368f24f
noindex: true
exl-id: 62f1d3e6-b0d2-4d64-b62e-91836b573e8c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Oak-run.jar 색인 지정 사용 사례{#oak-run-jar-indexing-use-cases}

Oak-run은 AEM JMX 콘솔을 통해 이러한 사용 사례 실행을 오케스트레이션하지 않고도 명령줄에서 색인 지정 사용 사례를 지원합니다.

Oak 인덱스를 관리하기 위한 oak-run.jar index 명령 접근 방식을 사용하면 다음과 같은 중요한 이점이 있습니다.

1. Oak-run index 명령은 AEM 6.4에 대한 새 인덱싱 도구 세트를 제공합니다.
1. Oak-run을 사용하면 더 큰 저장소에서 재색인화 시간이 줄어듭니다.
1. Oak-run은 AEM에서 다시 색인화하는 동안 리소스 소비를 줄임으로써 전반적인 시스템 성능을 향상시킵니다.
1. Oak-run은 대역 외 재인덱싱, 프로덕션을 사용할 수 있어야 하는 지원 상황을 제공하며 다시 색인화하는 데 필요한 유지 관리 또는 다운타임을 견딜 수 없습니다.

아래 섹션에서는 샘플 명령을 제공합니다. oak-run index 명령은 모든 NodeStore 및 BlobStore 설정을 지원합니다. 아래 제공된 예는 FileDataStore 및 SegmentNodeStore를 포함하는 설정에 대한 것입니다.

## 사용 사례 1 - 인덱스 일관성 확인 {#usercase1indexconsistencycheck}

인덱스 손상과 관련된 사용 사례입니다. 어떤 인덱스가 손상되었는지 확인할 수 없는 경우도 있습니다. 따라서 Adobe은 다음과 같은 도구를 제공했습니다.

1. 모든 인덱스에 대해 색인 일관성 검사를 수행하고 유효한 인덱스가 유효하지 않은 보고서를 제공합니다.
1. AEM에 액세스할 수 없는 경우에도 도구를 사용할 수 있습니다.
1. 사용하기 쉽습니다.

손상된 인덱스를 확인하는 방법은 `--index-consistency-check` 작업을 통해 수행할 수 있습니다.

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

이렇게 하면 `indexing-result/index-consistency-check-report.txt`에 보고서가 생성됩니다. 샘플 보고서는 아래를 참조하십시오.

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### 이점 {#uc1benefits}

이제 지원 및 시스템 관리자가 이 도구를 사용하여 어떤 인덱스가 손상되었는지 신속하게 확인한 다음 다시 색인화할 수 있습니다.

## 사용 사례 2 - 인덱스 통계 {#usecase2indexstatistics}

쿼리 성능 Adobe에 대한 일부 사례를 진단하려면 기존 인덱스 정의가 필요한 경우가 많습니다. 고객 설정에서 관련 통계를 색인화하십시오. 지금까지 이 정보는 여러 리소스에 분산되었습니다. 문제를 보다 쉽게 해결하기 위해 Adobe은 다음과 같은 도구를 만들었습니다.

1. 시스템에 있는 모든 인덱스 정의를 단일 JSON 파일로 덤프합니다.

1. 기존 인덱스에서 중요한 통계를 덤프합니다.

1. 오프라인 분석을 위해 인덱스 콘텐츠를 덤프합니다.

1. AEM에 액세스할 수 없는 경우에도 사용할 수 있습니다

이제 다음 작업 인덱스 명령을 통해 위의 작업을 수행할 수 있습니다.

* `--index-info` - 인덱스와 관련된 다양한 통계를 수집하고 덤프합니다

* `--index-definitions` - 색인 정의를 수집하고 덤프합니다.

* `--index-dump` - 인덱스 콘텐츠 덤프

명령 작동 방법의 예는 아래 를 참조하십시오.

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

보고서는 `indexing-result/index-info.txt` 및 `indexing-result/index-definitions.json`에 생성됩니다

또한 웹 콘솔을 통해 동일한 세부 정보가 제공되며 구성 덤프 zip에 포함됩니다. 다음 위치에서 액세스할 수 있습니다.

`https://serverhost:serverport/system/console/status-oak-index-defn`

### 이점 {#uc2benefits}

이 도구를 사용하면 색인 지정 또는 쿼리 문제와 관련된 모든 필요한 세부 정보를 빠르게 수집할 수 있으며 이 정보를 추출하는 데 소요되는 시간을 줄일 수 있습니다.

## 사용 사례 3 - 재인덱싱 {#usecase3reindexing}

[시나리오](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing)에 따라 일부 경우에는 재색인화를 수행해야 합니다. 현재 재색인화는 CRXDE를 통해 또는 Index Manager 사용자 인터페이스를 통해 색인 정의 노드에서 `reindex` 플래그를 `true`로 설정하여 수행됩니다. 플래그가 설정되면 재색인화가 비동기식으로 수행됩니다.

재색인화에 대해 주목할 만한 점이 있습니다.

* 재색인화는 `DocumentNodeStore` 설정에서 모든 컨텐츠가 로컬인 `SegmentNodeStore` 설정과 비교하여 훨씬 느립니다.

* 현재 디자인을 사용하면 재색인화가 발생하는 동안 비동기 색인이 차단되고 다른 모든 비동기 인덱스가 부실해지고 색인화 기간 동안 업데이트되지 않습니다. 이로 인해 시스템이 사용 중인 경우 사용자에게 최신 결과가 표시되지 않을 수 있습니다.
* 재색인화에는 AEM 설정에 높은 로드를 배치할 수 있는 전체 리포지토리의 순회 작업이 포함되므로 최종 사용자 환경에 영향을 줍니다.
* `DocumentNodeStore` 재색인화가 상당한 시간이 걸릴 수 있는 설치의 경우 작업 도중에 Mongo 데이터베이스에 대한 연결이 실패하면 색인화를 처음부터 다시 시작해야 합니다.

* 텍스트 추출으로 인해 재색인화하는 데 시간이 오래 걸릴 수 있습니다. 이는 주로 PDF 파일이 많은 설정에 한정되며 텍스트 추출에 소요되는 시간이 인덱싱 시간에 영향을 줄 수 있습니다.

이러한 목표를 달성하기 위해 oak-run 인덱스 도구는 필요에 따라 사용할 수 있는 재색인화를 위한 다른 모드를 지원합니다. oak-run index 명령은 다음과 같은 이점을 제공합니다.

* **대역 외 재인덱싱**  - oak-run 재색인화는 실행 중인 AEM 설정과 별도로 수행할 수 있으므로 사용 중인 AEM 인스턴스에 미치는 영향을 최소화합니다.

* **오프라인 재인덱싱**  - 색인 지정 작업에 영향을 주지 않고 재색인이 수행됩니다. 즉, 비동기 인덱서가 다른 인덱스를 계속 인덱싱할 수 있습니다.

* **DocumentNodeStore 설치에 대한 간소화된 재인덱스**  -  `DocumentNodeStore` 설치의 경우 재색인화를 단일 명령으로 수행할 수 있으므로 가장 적합한 방식으로 재색인화가 수행됩니다.

* **인덱스 정의 업데이트 및 새로운 인덱스 정의 도입 지원**

### 다시 인덱스 - DocumentNodeStore {#reindexdocumentnodestore}

`DocumentNodeStore` 설치 재색인화의 경우 단일 oak-run 명령을 통해 재색인화를 수행할 수 있습니다.

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

다음과 같은 이점이 있습니다

* AEM 인스턴스 실행에 미치는 영향을 최소화합니다. 대부분의 읽기는 보조 서버에서 수행할 수 있으며 AEM 캐시를 실행하는 것은 재색인에 필요한 모든 순회 때문에 영향을 받지 않습니다.
* 또한 사용자는 `--index-definitions-file` 옵션을 통해 새 색인이나 업데이트된 색인의 JSON을 제공할 수 있습니다.

### 다시 인덱스 - SegmentNodeStore {#reindexsegmentnodestore}

`SegmentNodeStore` 설치에 대해 다음 방법 중 하나로 재색인화를 수행할 수 있습니다.

#### 온라인 재인덱스 - SegmentNodeStore {#onlinereindexsegmentnodestore}

`reindex` 플래그 설정을 통해 재색인화가 수행되는 방식을 따릅니다.

#### 온라인 재인덱스 - SegmentNodeStore - AEM 인스턴스가 실행 중입니다. {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

`SegmentNodeStore` 설치의 경우 한 프로세스만 읽기-쓰기 모드에서 세그먼트 파일에 액세스할 수 있습니다. 이러한 oak-run 인덱싱의 일부 작업으로 인해 추가 수동 단계를 수행해야 합니다.

여기에는 다음 항목이 포함됩니다.

1. 단계 텍스트
1. 읽기 전용 모드에서 AEM에서 사용하는 동일한 저장소에 `oak-run`을 연결하고 색인을 수행합니다. 이를 실현하는 방법에 대한 예제:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. 마지막으로, 위의 명령을 실행한 후 oak-run이 인덱싱 파일을 저장한 경로에서 `IndexerMBean#importIndex` 작업을 통해 생성된 인덱스 파일을 가져옵니다.

이 시나리오에서는 AEM 서버를 중지하거나 새 인스턴스를 프로비저닝할 필요가 없습니다. 그러나 색인화에는 전체 리포지토리의 순회 작업이 포함되므로 설치 시 입출력 로드가 증가하여 런타임 성능에 부정적인 영향을 줍니다.

#### 온라인 재인덱스 - SegmentNodeStore - AEM 인스턴스가 종료됨 {#onlinereindexsegmentnodestoreaeminstanceisdown}

`SegmentNodeStore` 설치의 경우 단일 oak-run 명령을 통해 재색인화를 수행할 수 있습니다. 그러나 AEM 인스턴스를 종료해야 합니다.

다음 명령으로 재색인을 트리거할 수 있습니다.

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/ 
```

이 접근 방식과 위에서 설명한 접근 방식의 차이점은 체크포인트 작성과 색인 가져오기가 자동으로 수행된다는 것입니다. 문제는 AEM이 그 과정 중에 다운될 필요가 있다는 것입니다.

#### 대역 외 재인덱스 - SegmentNodeStore {#outofbandreindexsegmentnodestore}

이 사용 사례에서는 복제된 설정에서 재색인화를 수행하여 실행 중인 AEM 인스턴스에 미치는 영향을 최소화할 수 있습니다.

1. JMX 작업을 통해 체크포인트를 만듭니다. 이렇게 하려면 [JMX 콘솔](/help/sites-administering/jmx-console.md)로 이동하여 `CheckpointManager`를 검색할 수 있습니다. 그런 다음 만료에 대한 높은 값(예: **2592000**)을 사용하여 **createCheckpoint(long p1)** 작업을 클릭합니다.
1. `crx-quickstart` 폴더를 새 컴퓨터에 복사합니다.
1. oak-run index 명령을 통해 다시 색인화 수행

1. 생성된 인덱스 파일을 AEM 서버에 복사합니다.

1. JMX를 통해 인덱스 파일을 가져옵니다.

이 사용 사례에서는 `FileDataStore` 이 EBS와 같은 클라우드 기반 스토리지 솔루션에 배치되는 경우 불가능한 다른 인스턴스에서 데이터 스토어에 액세스할 수 있다고 가정합니다. 여기에는 `FileDataStore` 도 복제된 시나리오가 제외됩니다. 인덱스 정의가 전체 텍스트 인덱싱을 수행하지 않으면 `DataStore`에 액세스할 필요가 없습니다.

## 사용 사례 4 - 색인 정의 업데이트 {#usecase4updatingindexdefinitions}

현재 [ACS Confirm Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) 패키지를 통해 인덱스 정의 변경 사항을 전달할 수 있습니다. 따라서 `reindex` 플래그를 `true`로 설정하여 나중에 재색인화를 수행해야 하는 컨텐츠 패키지를 통해 인덱스 정의를 전달할 수 있습니다.

이 기능은 재색인화가 오래 걸리지 않는 작은 설치에 적합합니다. 그러나 매우 큰 저장소의 경우 재색인화는 훨씬 더 많은 시간 내에 수행됩니다. 이러한 경우 이제 oak-run 인덱스 도구 를 사용할 수 있습니다.

이제 Oak-run은 JSON 형식으로 색인 정의를 제공하고 라이브 인스턴스에서 변경 사항이 수행되지 않는 대역 외 모드에서 색인 생성을 지원합니다.

이 사용 사례에 대해 고려해야 하는 프로세스는 다음과 같습니다.

1. 개발자는 로컬 인스턴스의 인덱스 정의를 업데이트한 다음 `--index-definitions` 옵션을 통해 인덱스 정의 JSON 파일을 생성합니다

1. 업데이트된 JSON이 시스템 관리자에게 제공됩니다
1. 시스템 관리자는 대역 외 접근 방식을 따르며 다른 설치 시 인덱스를 준비합니다
1. 이 작업이 완료되면 생성된 인덱스 파일을 실행 중인 AEM 설치 시 가져옵니다.
