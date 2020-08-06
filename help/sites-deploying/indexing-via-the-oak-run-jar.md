---
title: Oak-run Jar를 통한 인덱싱
seo-title: Oak-run Jar를 통한 인덱싱
description: Oak-run Jar를 통해 색인 작업을 수행하는 방법을 알아봅니다.
seo-description: Oak-run Jar를 통해 색인 작업을 수행하는 방법을 알아봅니다.
uuid: 09a83ab9-92ec-4b55-8d24-2302f28fc2e4
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: c8a505ab-a075-47da-8007-43645a8c3ce5
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 1%

---


# Oak-run Jar를 통한 인덱싱{#indexing-via-the-oak-run-jar}

Oak-run은 JMX 수준에서 작업할 필요 없이 명령줄에서 모든 인덱싱 사용 사례를 지원합니다. 오크 실행 접근 방식의 이점은 다음과 같습니다.

1. AEM 6.4용 새로운 인덱싱 툴셋입니다.
1. EMC DL 시리즈 / VTL 솔루션 / DL 시리즈 / DL 시리즈(
1. AEM에서 다시 색인화하는 동안 리소스 사용량을 줄여 다른 AEM 활동에 대한 시스템 성능을 향상시킵니다.
1. Oak-run은 다음과 같은 대역 외 지원을 제공합니다. 프로덕션 조건이 프로덕션 인스턴스에 대해 다시 색인 작업을 수행할 수 없는 경우, 복제된 환경을 다시 인덱싱하여 중요한 성능에 영향을 주지 않도록 할 수 있습니다.

아래에서 `oak-run` 도구를 통해 색인 작업을 수행할 때 활용할 수 있는 사용 사례 목록을 확인할 수 있습니다.

## 색인 일관성 검사 {#indexconsistencychecks}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 사용 사례 1 - [인덱스 일관성 확인을 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck).

* `oak-run.jar`lucene oak 색인이 손상되었는지 신속하게 판별합니다.
* 사용 중인 AEM 인스턴스에서 일관성 확인 수준 1 및 2를 실행할 수 있습니다.

![screen_shot_2017-12-14at135758](assets/screen_shot_2017-12-14at135758.png)

## 색인 통계 {#indexstatistics}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 사용 사례 2 - [인덱스 통계를 참조하십시오.](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics)

* `oak-run.jar` 오프라인 분석을 위해 모든 색인 정의, 중요한 색인 통계 및 색인 내용을 덤프합니다.

* 사용 중인 AEM 인스턴스에서 실행되도록 안전합니다.

![image2017-12-19_9-47-40](assets/image2017-12-19_9-47-40.png)

## 다시 인덱싱 접근 방식 결정 트리 {#reindexingapproachdecisiontree}

이 다이어그램은 다양한 다시 색인 접근 방식을 사용할 시기를 결정하는 트리 입니다.

![oak_-_reindexingoak-run](assets/oak_-_reindexingwithoak-run.png)

## MongoMK / RDMBMK 재인덱싱 {#reindexingmongomk}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 사용 사례 3 - [다시 색인화를 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### SegmentNodeStore 및 DocumentNodeStore용 텍스트 사전 추출 {#textpre-extraction}

[텍스트 사전 추출](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) (AEM 6.3과 함께 존재했던 기능)을 사용하여 다시 색인화하는 시간을 줄일 수 있습니다. 텍스트 사전 추출을 모든 재색인 접근 방식과 함께 사용할 수 있습니다.

색인 `oak-run.jar` 지정 방식에 따라 아래 다이어그램의 재색인 실행 단계 양쪽에 다양한 단계가 있습니다.

![4](assets/4.png)

>[!NOTE]
>
>오렌지는 AEM이 유지 관리 창에 있어야 하는 활동을 나타냅니다.

### oak-run.jar를 사용하여 MongoMK 또는 RDBMK에 대한 온라인 재인덱싱 {#onlinere-indexingformongomk}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 Reindex [- DocumentNodeStore를 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

MongoMK(및 RDBMK) AEM 설치를 다시 인덱싱하는 데 권장되는 방법입니다. 다른 방법은 사용하지 마십시오.

이 프로세스는 클러스터의 단일 AEM 인스턴스에만 실행해야 합니다.

![5](assets/5.png)

## TarMK 다시 인덱싱 {#re-indexingtarmk}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 [다시 색인 - SegmentNodeStore를 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **콜드 대기 고려 사항(TarMK)**

   * 콜드스탠바이 에는 특별한 고려사항이 없다. Cold Standby 인스턴스는 변경 사항을 평소대로 동기화합니다.

* **AEM 게시 팜(AE 게시 팜은 항상 TarMK여야 함)**

   * 게시 팜의 경우, 모든 OR에서 단일 게시에서 단계를 실행한 다음 다른 사용자에 대해 설정을 복제해야 합니다(AEM 인스턴스를 복제할 때 일반적인 모든 정밀한 작업 수행). sling.id - 여기에 연결되어 있어야 함)

### TarMK의 온라인 재인덱싱 {#onlinere-indexingfortarmk}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 [온라인 재색인 - SegmentNodeStore를 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

이것은 oak-run.jar의 새로운 인덱싱 기능을 사용하기 전에 사용되는 방법입니다. Oak 색인에 `reindex=true` 속성을 설정하여 수행할 수 있습니다.

시간 및 성능 효과를 고객이 색인에 적용할 수 있는 경우 이 방법을 사용할 수 있습니다. 보통 중소규모의 AEM 설치 경우입니다.

![6](assets/6.png)

### oak-run.jar를 사용하는 온라인 TarMK 다시 인덱싱 {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 [온라인 재인덱스 - SegmentNodeStore - AEM 인스턴스가 실행 중임을 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

TarMK의 온라인 재색인은 위에서 설명한 온라인 TarkMK의 재색인화보다 더 빠릅니다. 하지만 유지 관리 기간 동안 창이 짧아지는 방법을 사용하여 실행해야 하며 다시 색인화를 수행하려면 더 많은 단계가 필요합니다.

>[!NOTE]
>
>오렌지는 유지 관리 기간 동안 AEM이 수행되어야 하는 작업을 나타냅니다.

![7](assets/7.png)

### oak-run.jar를 사용하여 TarMK를 오프라인 재인덱싱 {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 [온라인 재인덱스 - SegmentNodeStore - AEM 인스턴스가 종료됨을 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

Offline re-indexing of TarMK는 단일 `oak-run.jar` 주석이 필요하므로 TarMK를 위한 가장 간단한 `oak-run.jar` 기반 재인덱싱 접근 방식입니다. 그러나 AEM 인스턴스를 종료해야 합니다.

>[!NOTE]
>
>빨간색은 AEM을 종료해야 하는 작업을 나타냅니다.

![8](assets/8.png)

### oak-run.jar를 사용하는 아웃오브 밴드 TarMK 다시 인덱싱  {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 대역 외 [재색인 - SegmentNodeStore를 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

대역외 재인덱싱을 사용하면 사용 중인 AEM 인스턴스에 대해 다시 인덱싱할 수 있는 영향을 최소화할 수 있습니다.

>[!NOTE]
>
>빨간색은 AEM이 종료될 수 있는 작업을 나타냅니다.

![9](assets/9.png)

## 색인 정의 업데이트 {#updatingindexingdefinitions}

>[!NOTE]
>
>이 시나리오에 대한 자세한 내용은 사용 사례 4 - [색인 정의 업데이트를 참조하십시오](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions).

### ACS Ensure Index를 사용하여 TarMK에서 색인 정의 만들기 및 업데이트 {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS Ensure Index는 커뮤니티에서 지원하는 프로젝트이며 Adobe 지원에서 지원되지 않습니다.

이를 통해 컨텐츠 패키지를 통해 배송 색인 정의를 수행할 수 있으므로 나중에 다시 색인 플래그를 로 설정하여 다시 색인화할 수 있습니다 `true`. 이렇게 하면 색인 재작성에 시간이 오래 걸리지 않는 작은 설정에 적용됩니다.

자세한 내용은 [ACS 색인 확인 설명서를](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) 참조하십시오.

### oak-run.jar를 사용하여 TarMK에서 색인 정의 만들기 및 업데이트 {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

비 `oak-run.jar` 메서드를 사용하여 다시 인덱싱할 때 시간 또는 성능이 너무 높을 경우 다음 `oak-run.jar` 기반 방법을 사용하여 TarMK 기반 AEM 설치 환경에서 Lucene 색인 정의를 가져오고 다시 인덱싱할 수 있습니다.

![10](assets/10.png)

### oak-run.jar를 사용하여 MonogMK에서 색인 정의 생성 및 업데이트 {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

비 `oak-run.jar` 메서드를 사용하여 다시 인덱싱할 때 시간 또는 성능에 미치는 영향이 너무 높은 경우 다음 `oak-run.jar` 기반 방법을 사용하여 MongoMK 기반 AEM 설치의 Lucene 색인 정의를 가져오고 다시 인덱싱할 수 있습니다.

![11](assets/11.png)

