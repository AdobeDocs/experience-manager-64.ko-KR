---
title: 자산 성능 조정 가이드
description: 병목 현상을 제거하고 AEM Assets의 성능을 최적화하기 위해 AEM 구성, 하드웨어, 소프트웨어 및 네트워크 구성 요소의 변경 사항에 대한 주요 초점 영역입니다.
contentOwner: AG
feature: 자산 관리
role: Architect,Admin
exl-id: 6c1bff46-f9e0-4638-9374-a9e820d30534
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '3208'
ht-degree: 0%

---

# 자산 성능 조정 가이드 {#assets-performance-tuning-guide}

AEM(Adobe Experience Manager) 자산 설정에는 많은 하드웨어, 소프트웨어 및 네트워크 구성 요소가 포함되어 있습니다. 배포 시나리오에 따라 성능 병목 현상을 제거하기 위해 하드웨어, 소프트웨어 및 네트워크 구성 요소에 대한 특정 구성 변경이 필요할 수 있습니다.

또한 특정 하드웨어 및 소프트웨어 최적화 지침을 식별하고 준수하면 AEM Assets 배포이 성능, 확장성 및 안정성에 대한 기대치를 충족할 수 있는 건전한 기반을 구축할 수 있습니다.

AEM Assets의 낮은 성능은 대화형 성능, 자산 처리, 다운로드 속도 및 기타 영역에 대한 사용자 경험에 영향을 줄 수 있습니다.

실제로 성능 최적화는 모든 프로젝트에 대한 타겟 지표를 설정하기 전에 수행해야 하는 기본적인 작업입니다.

다음은 성능 문제가 사용자에게 영향을 주기 전에 발견하여 해결하는 특정 주요 포커스 영역입니다.

## 플랫폼 {#platform}

AEM은 많은 플랫폼에서 지원되지만 Linux 및 Windows에서 기본 도구에 대한 가장 많은 지원을 제공한다는 사실이 확인되어 최적의 성능과 구현의 편의성에 기여합니다. 가장 좋은 방법은 AEM Assets 배포의 높은 메모리 요구 사항을 충족하기 위해 64비트 운영 체제를 배포하는 것입니다. 모든 AEM 배포과 마찬가지로 TarMK를 가능한 모든 곳에서 구현해야 합니다. TarMK는 단일 작성자 인스턴스를 넘어 확장할 수 없지만 MongoMK보다 성능이 뛰어난 것으로 나타났습니다. TarMK 오프로드 인스턴스를 추가하여 AEM Assets 배포의 워크플로우 처리 능력을 향상시킬 수 있습니다.

### 임시 폴더 {#temp-folder}

자산 업로드 시간을 개선하려면 Java temp 디렉토리에 대한 고성능 저장소를 사용합니다. Linux 및 Windows에서는 RAM 드라이브 또는 SSD를 사용할 수 있습니다. 클라우드 기반 환경에서는 동등한 고속 스토리지 유형을 사용할 수 있습니다. 예를 들어 Amazon EC2에서는 [사용 후 드라이브](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) 드라이브를 임시 폴더에 사용할 수 있습니다.

서버에 충분한 메모리가 있다고 가정할 경우 RAM 드라이브를 구성합니다. Linux에서 다음 명령을 실행하여 8GB RAM 드라이브를 만듭니다.

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Windows OS에서는 RAM 드라이브를 만들거나 SSD와 같은 고성능 스토리지를 사용해야 합니다.

고성능 임시 볼륨이 준비되면 JVM 매개 변수 -Djava.io.tmpdir을 설정합니다. 예를 들어 AEM의 bin/start 스크립트에서 CQ_JVM_OPTS 변수에 아래의 JVM 매개 변수를 추가할 수 있습니다.

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java 구성 {#java-configuration}

### Java 버전 {#java-version}

2015년 4월 현재 Oracle이 Java 7에 대한 업데이트 릴리스를 중단했으므로 Java 8에 AEM Assets을 배포하는 것이 좋습니다. 일부 경우에는 성능이 개선되었습니다.

### JVM 매개 변수 {#jvm-parameters}

다음 JVM 매개 변수를 설정해야 합니다.

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`= 500000
* `-Doak.queryLimitReads`= 100000
* `-Dupdate.limit`= 250000
* `-Doak.fastQuerySize`=true

## 데이터 저장소 및 메모리 구성 {#data-store-and-memory-configuration}

### 파일 데이터 저장소 구성 {#file-data-store-configuration}

모든 AEM Assets 사용자는 세그먼트 저장소에서 데이터 저장소를 분리하는 것이 좋습니다. 또한 `maxCachedBinarySize` 및 `cacheSizeInMB` 매개 변수를 구성하면 성능을 극대화할 수 있습니다. `maxCachedBinarySize` 을 캐시에서 저장할 수 있는 가장 작은 파일 크기로 설정합니다. `cacheSizeInMB` 내의 데이터 저장소에 사용할 메모리 내 캐시의 크기를 지정합니다. Adobe은 이 값을 총 heap 크기의 2-10% 이내로 설정할 것을 권장합니다. 그러나 로드/성능 테스트는 이상적인 설정을 결정하는 데 도움이 될 수 있습니다.

### 버퍼된 이미지 캐시의 최대 크기 구성 {#configure-the-maximum-size-of-the-buffered-image-cache}

많은 양의 자산을 Adobe Experience Manager에 업로드할 때, 메모리 소비에서 예기치 않은 스파이크가 발생하고 JVM이 OutOfMemoryErrors로 실패하지 않도록 버퍼링된 이미지 캐시의 구성된 최대 크기를 줄입니다. 최대 힙이 5GB이고, Oak BlobCache가 1GB로 설정되고, 문서 캐시가 2GB로 설정되는 시스템을 예로 들어 보겠습니다. `Xmx` 이 경우 버퍼링된 캐시는 최대 1.25GB와 메모리가 필요하므로 예기치 않은 스파이크에 대해서는 0.75GB 메모리만 남게 됩니다.

OSGi 웹 콘솔에서 버퍼된 캐시 크기를 구성합니다. `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`에서 `cq.dam.image.cache.max.memory` 속성을 바이트 단위로 설정합니다. 예를 들어 1073741824은 1GB(1024 x 1024 x 1024 = 1GB)입니다.

AEM 6.1 SP1에서 이 속성을 구성하기 위해 `sling:osgiConfig` 노드를 사용하는 경우 데이터 유형을 Long으로 설정해야 합니다. 자세한 내용은 [CQBufferedImageCache가 자산 업로드 중 힙을 사용합니다](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### 공유 데이터 저장소 {#shared-data-stores}

S3 또는 공유 파일 데이터 저장소를 구현하면 디스크 공간을 절약하고 대규모 구현에서 네트워크 처리량을 늘리는 데 도움이 될 수 있습니다. 공유 데이터 저장소 사용의 장단점에 대한 자세한 내용은 [자산 크기 조정 안내서](assets-sizing-guide.md)를 참조하십시오.

### S3 데이터 저장소 {#s-data-store}

다음 S3 데이터 저장소 구성( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`)은 Adobe이 기존 파일 데이터 저장소에서 고객 사이트의 S3 데이터 저장소로 12.8TB의 바이너리 대용량 개체(BLOB)를 추출하는 데 도움이 되었습니다.

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## 네트워크 최적화 {#network-optimization}

Adobe은 많은 회사에 HTTP 트래픽을 감지하는 방화벽이 있어 이 방화벽이 있어 파일 업로드와 손상이 발생할 수 있습니다. 대용량 파일 업로드를 위해서는 WiFi 네트워크가 빠르게 포화되는 것을 방지하기 때문에 사용자가 네트워크에 유선 연결을 가지고 있는지 확인합니다. 네트워크 병목 현상을 식별하는 방법에 대한 지침은 [자산 크기 조정 가이드](assets-sizing-guide.md)를 참조하십시오. 네트워크 토폴로지를 분석하여 네트워크 성능을 평가하려면 [자산 네트워크 고려 사항](assets-network-considerations.md)을 참조하십시오.

주로 네트워크 최적화 전략은 사용 가능한 대역폭 및 AEM 인스턴스의 로드에 따라 다릅니다. 방화벽 또는 프록시를 포함한 일반적인 구성 옵션은 네트워크 성능을 개선하는 데 도움이 될 수 있습니다. 다음은 기억해야 할 몇 가지 주요 사항입니다.

* 인스턴스 유형(작은, 중간, 큰)에 따라 AEM 인스턴스에 충분한 네트워크 대역폭이 있는지 확인하십시오. AEM이 AWS에서 호스팅되는 경우 특히 적절한 대역폭 할당이 중요합니다.
* AEM 인스턴스가 AWS에서 호스팅되는 경우 다양한 스케일링 정책을 통해 이점을 얻을 수 있습니다. 사용자가 높은 로드를 예상하는 경우 인스턴스의 크기를 변경합니다. 중간/낮은 로드를 위해 크기를 줄입니다.
* HTTPS:대부분의 사용자에게는 HTTP 트래픽을 감지하는 방화벽이 있으므로 업로드 작업 중에 파일 업로드나 손상된 파일의 업로드에 부정적인 영향을 줄 수 있습니다.
* 큰 파일 업로드:사용자가 네트워크에 유선 연결을 했는지 확인합니다(WiFi 연결이 빠르게 채워짐).

## 워크플로우 {#workflows}

### 임시 워크플로우 {#transient-workflows}

가능하면 DAM 자산 업데이트 워크플로우를 임시 로 설정합니다. 이 설정은 워크플로우가 일반적인 추적 및 보관 프로세스를 통과하지 않아도 되므로 워크플로우를 처리하는 데 필요한 오버헤드를 크게 줄입니다.

>[!NOTE]
>
>기본적으로 AEM 6.3에서는 DAM 자산 업데이트 워크플로우가 일시로 설정됩니다. 이 경우 다음 절차를 건너뛸 수 있습니다.

1. 구성할 AEM 인스턴스에서 `http://localhost:4502/miscadmin` 을 엽니다.

1. 탐색 트리에서 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]** > **[!UICONTROL dam]**&#x200B;을 확장합니다.
1. **[!UICONTROL DAM 자산 업데이트]**&#x200B;를 두 번 클릭합니다.
1. 부동 도구 패널에서 **[!UICONTROL 페이지]** 탭으로 전환한 다음 **[!UICONTROL 페이지 속성]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 임시 워크플로우]**&#x200B;를 선택하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >일부 기능은 임시 워크플로우를 지원하지 않습니다. AEM Assets 배포에 이러한 기능이 필요한 경우 임시 워크플로우를 구성하지 마십시오.

   임시 워크플로우를 사용할 수 없는 경우 워크플로우 제거를 정기적으로 실행하여 보관된 DAM 자산 업데이트 워크플로우를 삭제하여 시스템 성능이 저하되지 않도록 합니다.

   일반적으로 매주 삭제 워크플로우를 실행해야 합니다. 그러나 대규모 자산 수집 중과 같이 리소스를 많이 사용하는 시나리오에서는 더 자주 실행할 수 있습니다.

   워크플로우 삭제를 구성하려면 OSGi 콘솔을 통해 새 Adobe Granite Workflow 제거 구성을 추가합니다. 그런 다음 워크플로우를 주별 유지 관리 창의 일부로 구성하고 예약합니다.

   퍼징이 너무 오래 실행되면 시간이 초과됩니다. 따라서 많은 수의 워크플로우로 인해 워크플로우 제거를 완료하지 못하는 상황을 방지하려면 작업 제거를 완료해야 합니다.

   예를 들어, 워크플로 인스턴스 노드를 만드는 임시 이외의 다양한 워크플로우를 실행한 후 임시 단위로 [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html)를 실행할 수 있습니다. Granite Workflow 제거 스케줄러가 실행될 때까지 기다리지 않고 중복되고 완료된 워크플로우 인스턴스를 즉시 제거합니다.

### 최대 병렬 작업 수 {#maximum-parallel-jobs}

기본적으로 AEM은 서버의 프로세서 수와 동일한 최대 병렬 작업 수를 실행합니다. 이 설정의 문제는 로드가 많은 동안 모든 프로세서가 DAM 자산 업데이트 워크플로우에 의해 사용되고 UI 응답성이 느려지고 AEM이 서버 성능과 안정성을 보호하는 다른 프로세스를 실행하지 못하도록 한다는 것입니다. 이 값은 다음 단계를 수행하여 서버에서 사용할 수 있는 프로세서의 절반으로 설정하는 것이 좋습니다.

1. AEM 작성기에서 [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent)로 이동합니다.
1. 구현과 관련된 각 워크플로우 큐(예: Granite Transient Workflow Queue)에서 편집 을 클릭합니다.
1. 최대 병렬 작업 값을 변경하고 저장을 누릅니다.

대기열을 사용 가능한 프로세서의 절반으로 설정하는 것은 시작할 수 있는 솔루션입니다. 그러나 최대 처리량을 달성하고 환경에 따라 조정하려면 이 수를 늘리거나 줄여야 할 수도 있습니다. 외부 워크플로우와 같은 다른 프로세스뿐만 아니라 임시 및 임시 워크플로우에 대한 별도의 큐가 있습니다. 프로세서가 50%로 설정된 여러 개의 큐가 동시에 활성화되면 시스템이 빠르게 오버로드될 수 있습니다. 많이 사용되는 큐는 사용자 구현마다 매우 다릅니다. 따라서 서버 안정성을 손상시키지 않고 최대 효율성을 위해 신중하게 구성해야 할 수 있습니다.

### 오프로딩 {#offloading}

비디오 코드 변환과 같이 리소스를 많이 사용하는 워크플로우나 워크플로우의 경우 DAM 자산 업데이트 워크플로우를 두 번째 작성자 인스턴스로 오프로드할 수 있습니다. 종종 오프로딩 시 문제는 워크플로우 처리를 오프로드하여 저장된 모든 로드는 인스턴스 간에 컨텐츠를 전후 재생하는 비용으로 오프셋됩니다.

AEM 6.2부터 AEM 6.1용 기능 팩으로 바이너리 없는 복제 기능을 사용하여 오프로드를 수행할 수 있습니다. 이 모델에서 작성자 인스턴스는 공통 데이터 저장소를 공유하고 순방향 복제만 통해 메타데이터를 앞뒤로 보냅니다. 이 접근 방식이 공유 파일 데이터 저장소에서 잘 작동하지만 S3 데이터 저장소에 문제가 있을 수 있습니다. 백그라운드 쓰기 스레드는 지연을 유도할 수 있으므로 오프로딩 작업이 시작되기 전에 자산이 데이터 저장소에 기록되지 않았을 수 있습니다.

### DAM 자산 구성 업데이트 {#dam-update-asset-configuration}

DAM 자산 업데이트 워크플로우에는 Dynamic Media Classic PTIFF 생성 및 InDesign Server 통합과 같은 작업에 대해 구성된 전체 단계 세트가 포함되어 있습니다. 그러나 대부분의 사용자는 이러한 단계 중 일부가 필요하지 않을 수 있습니다. Adobe은 DAM 자산 업데이트 워크플로우 모델의 사용자 지정 복사본을 만들고 불필요한 단계를 제거하는 것을 권장합니다. 이 경우 새 모델을 가리키도록 DAM 자산 업데이트 용 런처를 업데이트합니다.

>[!NOTE]
>
>DAM 자산 업데이트 워크플로우를 집중적으로 실행하면 파일 데이터베이스 크기가 크게 늘어날 수 있습니다. Adobe에서 수행한 실험 결과에 따르면 약 5500 워크플로우가 8시간 내에 수행되는 경우 데이터 저장소 크기가 약 400GB까지 증가할 수 있습니다.
>
>데이터 저장소 가비지 수집 작업을 실행한 후 데이터 저장소가 원래 크기로 복원됩니다.
>
>일반적으로 데이터 저장소 가비지 수집 작업은 다른 예약된 유지 관리 작업과 함께 매주 실행됩니다.
>
>디스크 공간이 제한되어 있고 DAM 자산 업데이트 워크플로우를 집중적으로 실행하는 경우 가비지 수집 작업 예약을 더 자주 고려하십시오.

#### 런타임 변환 생성 {#runtime-rendition-generation}

고객은 웹 사이트에서 다양한 크기와 형식의 이미지를 사용하거나 비즈니스 파트너에게 배포할 수 있습니다. 각 표현물이 리포지토리에서 자산의 풋프린트에 추가되므로, 이 기능을 신중하게 사용하는 것이 좋습니다. 이미지를 처리하고 저장하는 데 필요한 리소스의 양을 줄이기 위해 이러한 이미지를 섭취 중 변환보다는 런타임 시 생성할 수 있습니다.

많은 Sites 고객은 요청 시 이미지의 크기를 조정하고 자르기를 수행하는 이미지 서블릿을 구현하여 게시 인스턴스에 추가 로드를 부과합니다. 그러나 이러한 이미지를 캐시하는 한 이러한 문제를 완화할 수 있습니다.

또 다른 방법은 Dynamic Media Classic 기술을 사용하여 이미지 조작을 완전히 제거하는 것입니다. 또한 AEM 인프라에서 렌디션 생성 책임을 인계할 뿐만 아니라 전체 게시 계층도 넘겨받는 Brand Portal을 배포할 수 있습니다.

#### ImageMagick {#imagemagick}

ImageMagick를 사용하여 렌디션을 생성하기 위해 DAM 자산 업데이트 워크플로우를 사용자 지정하는 경우 */etc/ImageMagick/*&#x200B;에서 policy.xml 파일을 수정하는 것이 좋습니다. 기본적으로 ImageMagick는 OS 볼륨의 사용 가능한 전체 디스크 공간과 사용 가능한 메모리를 사용합니다. policy.xml의 `policymap` 섹션 내에서 다음 구성을 변경하여 이러한 리소스를 제한합니다.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

또한 *configure.xml* 파일에서 ImageMagick의 임시 폴더의 경로를 충분한 공간 및 IOPS가 있는 디스크 파티션으로 설정합니다(또는 환경 변수 `MAGIC_TEMPORARY_PATH`).

>[!CAUTION]
>
>ImageMagick가 사용 가능한 모든 디스크 공간을 사용하는 경우 구성이 잘못되면 서버가 불안정해질 수 있습니다. ImageMagick를 사용하여 큰 파일을 처리하는 데 필요한 정책 변경 사항은 AEM 성능에 영향을 줄 수 있습니다. 자세한 내용은 [ImageMagick](best-practices-for-imagemagick.md) 설치 및 구성 을 참조하십시오.

>[!NOTE]
>
>ImageMagick `policy.xml` 및 `configure.xml` 파일은 `/etc/ImageMagick/` 대신 `/usr/lib64/ImageMagick-*/config/` 아래에 있습니다. 구성 파일 위치에 대한 자세한 내용은 [ImageMagick 설명서](https://www.imagemagick.org/script/resources.php)를 참조하십시오.

AMS(Adobe Managed Services)에서 AEM을 사용하는 경우 대용량 PSD 또는 PSB 파일을 많이 처리할 계획이면 Adobe 고객 지원 센터에 문의하십시오. Experience Manager은 30000 x 23000 픽셀 이상의 고해상도 PSB 파일을 처리하지 못할 수 있습니다.

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### XMP 원본에 쓰기 {#xmp-writeback}

XMP 원본에 쓰기 기능은 AEM에서 메타데이터가 수정될 때마다 원래 자산을 업데이트하므로, 다음과 같은 결과가 발생합니다.

* 자산 자체가 수정됨
* 자산의 버전이 만들어집니다
* 자산에 대해 DAM 자산 업데이트 가 실행됩니다

나열된 결과는 상당한 자원을 소모한다. 따라서 Adobe은 필요하지 않은 경우 [XMP 원본에 쓰기](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html)를 사용하지 않도록 설정하는 것이 좋습니다.

워크플로우 실행 플래그를 선택하면 대량의 메타데이터를 가져오면 리소스 집약적인 XMP 원본에 쓰기 활동이 발생할 수 있습니다. 다른 사용자의 성능에 영향을 주지 않도록 서버 사용 공간을 적게 사용하는 동안 이러한 가져오기를 계획합니다.

## 복제 {#replication}

자산을 많은 수의 게시 인스턴스로 복제할 때(예: 사이트 구현에서) Adobe은 체인 복제를 사용하는 것을 권장합니다. 이 경우 작성자 인스턴스는 단일 게시 인스턴스로 복제되고, 이렇게 되면 다른 게시 인스턴스로 복제되어 작성자 인스턴스를 늘립니다.

### 체인 복제 구성 {#configure-chain-replication}

1. 복제 체인에 사용할 게시 인스턴스를 선택합니다
1. 해당 게시 인스턴스에서 다른 게시 인스턴스를 가리키는 복제 에이전트를 추가합니다
1. 이러한 각 복제 에이전트에서 **[!UICONTROL Triggers]** 탭에서 **[!UICONTROL On Receive]**&#x200B;를 활성화합니다

>[!NOTE]
>
>Adobe에서는 자산을 자동 활성화하지 않는 것이 좋습니다. 그러나 필요한 경우 Adobe에서 이를 워크플로우의 마지막 단계로 수행하는 것이 좋습니다(일반적으로 DAM 자산 업데이트).

## 인덱스 검색 {#search-indexes}

시스템 인덱스에 대한 업데이트가 자주 포함되므로 최신 서비스 팩 및 성능 관련 핫픽스를 구현하십시오. [성능 조정 팁 을 참조하십시오 | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) 사용 중인 AEM 버전에 따라 적용할 수 있는 일부 색인 최적화의 경우

자주 실행하는 쿼리에 대한 사용자 지정 인덱스를 만듭니다. 자세한 내용은 [느린 쿼리 분석 방법](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) 및 [사용자 지정 인덱스 작성](/help/sites-deploying/queries-and-indexing.md)을 참조하십시오. 쿼리 및 색인 우수 사례에 대한 추가 인사이트를 보려면 [쿼리 및 색인 생성에 대한 우수 사례](/help/sites-deploying/best-practices-for-queries-and-indexing.md)를 참조하십시오.

### Lucene 인덱스 구성 {#lucene-index-configurations}

AEM Assets 성능을 향상시키는 데 도움이 되는 Oak 색인 구성에서 일부 최적화를 수행할 수 있습니다.

LuceneIndexProvider 구성을 업데이트합니다.

1. /system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService로 이동합니다.
1. AEM 6.2 이전 버전에서 **[!UICONTROL CopyOnRead , CopyOnWrite 및 미리 가져오기 인덱스 파일]**&#x200B;을 활성화합니다. 이러한 값은 AEM 6.2 이상 버전에서 기본적으로 활성화됩니다.

색인 구성을 업데이트하여 다시 인덱싱 시간을 개선합니다.

1. CRXDe /crx/de/index.jsp 를 열고 관리 사용자로 로그인합니다
1. /oak:index/lucene으로 이동합니다.
1. 값이 &quot;/var&quot;, &quot;/etc/workflow/instances&quot; 및 &quot;/etc/replication&quot;인 **[!UICONTROL excludedPaths]**&#x200B;라는 String[] 속성을 추가합니다
1. /oak:index/damAssetLucene으로 이동합니다.
1. **[!UICONTROL includedPaths]**&#x200B;라는 String[] 속성을 한 값 &quot;/content/dam&quot;과 함께 추가합니다
1. 저장

(AEM6.1 및 6.2만 해당) ntBaseLucene 인덱스를 업데이트하여 자산 삭제 및 이동 성능을 개선합니다.

1. */oak:index/ntBaseLucene/indexRules/nt:base/properties* 로 이동합니다.
1. */oak:index/ntBaseLucene/indexRules/nt:base/properties* 아래에 두 개의 nt:un구조화되지 않은 노드 **[!UICONTROL slingResource]** 및 **[!UICONTROL damResolvedPath]** 추가
1. 노드에서 아래 속성을 설정합니다. 여기서 ordered 및 propertyIndex 속성은 *Boolean* 형식입니다.

   slingResource

   name=&quot;sling:resource&quot;

   ordered=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvedPath&quot;

   ordered=false

   propertyIndex=true

   type=&quot;String&quot;

1. /oak:index/ntBaseLucene 노드에서 `reindex=true` 속성을 설정합니다.
1. **[!UICONTROL 모두 저장]** 클릭
1. 색인화가 완료될 때 error.log를 모니터링합니다.

   인덱스에 대한 재색인화가 완료되었습니다.[/oak:index/ntBaseLucene]

1. 또한 reindex 속성이 false로 돌아가므로 CRXDe에서 /oak:index/ntBaseLucene 노드를 새로 고쳐서 색인이 완료되는 것을 확인할 수 있습니다
1. 색인화가 완료되면 CRXDe로 돌아가서 이러한 두 인덱스에 대해 **[!UICONTROL type]** 속성을 비활성화로 설정합니다

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. **[!UICONTROL 모두 저장]** 클릭

Lucene 텍스트 추출 비활성화:

사용자가 PDF 문서에 포함된 텍스트를 검색하는 등 자산의 내용을 검색할 필요가 없는 경우, 이 기능을 비활성화하여 색인 성능을 향상시킬 수 있습니다.

1. AEM 패키지 관리자 /crx/packmgr/index.jsp 로 이동합니다.
1. 아래 패키지를 업로드하고 설치합니다

[파일 가져오기](assets/disable_indexingbinarytextextraction-10.zip)

### Guess Total {#guess-total}

큰 결과 세트를 생성하는 쿼리를 만들 때 `guessTotal` 매개 변수를 사용하여 실행할 때 메모리 사용량이 많은 것을 방지합니다.

## 알려진 문제 {#known-issues}

### 큰 파일 {#large-files}

AEM에는 대형 파일과 관련된 것으로 알려진 두 가지 주요 문제가 있습니다. 파일이 2GB보다 큰 크기에 도달하면 콜드 대기 동기화가 메모리 부족 상태로 발생할 수 있습니다. 대기 동기화가 실행되지 않는 경우도 있습니다. 다른 경우에는 기본 인스턴스가 충돌합니다. 이 시나리오는 컨텐츠 패키지를 포함하여 2GB보다 큰 AEM의 모든 파일에 적용됩니다.

마찬가지로, 공유 S3 데이터 저장소를 사용하는 동안 파일의 크기가 2GB에 도달하면 파일이 캐시에서 파일 시스템으로 완전히 지속되는 데 시간이 걸릴 수 있습니다. 따라서 바이너리 없는 복제를 사용할 때 복제가 완료되기 전에 바이너리 데이터가 지속되지 않았을 수 있습니다. 이러한 경우 특히 오프로딩 시나리오와 같이 데이터 가용성이 중요한 경우 문제가 발생할 수 있습니다.

## 성능 테스트 {#performance-testing}

모든 AEM 배포에 대해 병목 현상을 신속하게 식별하고 해결할 수 있는 성능 테스트 시스템을 구축하십시오. 여기에 초점을 맞출 몇 가지 주요 영역들이 있습니다.

### 네트워크 테스트 {#network-testing}

고객의 모든 네트워크 성능 문제에 대해 다음 작업을 수행하십시오.

* 고객 네트워크 내에서 네트워크 성능 테스트
* Adobe 네트워크 내에서 네트워크 성능을 테스트합니다. AMS 고객의 경우 CSE와 협력하여 Adobe 네트워크에서 테스트합니다.
* 다른 액세스 포인트에서 네트워크 성능 테스트
* 네트워크 벤치마크 도구 사용
* 디스패처에 대해 테스트

### AEM 인스턴스 테스트 {#aem-instance-testing}

효율적인 CPU 사용률 및 로드 공유를 통해 지연을 최소화하고 높은 처리량을 얻으려면 AEM 인스턴스의 성능을 정기적으로 모니터링합니다. 특히

* AEM 인스턴스에 대해 로드 테스트 실행
* 업로드 성능 및 UI 응답성 모니터링

## AEM Assets 성능 검사 목록 {#aem-assets-performance-checklist}

* HTTPS를 활성화하여 기업의 HTTP 트래픽 스니퍼들을 파악합니다.
* 자산 업로드를 위해 유선 연결을 사용합니다.
* 최적의 JVM 매개 변수를 설정합니다.
* 파일 시스템 DataStore 또는 S3 DataStore를 구성합니다.
* 하위 자산 생성을 비활성화합니다. 활성화되어 있으면 AEM 워크플로우는 다중 페이지 자산의 각 페이지에 대해 별도의 자산을 만듭니다. 이러한 각 페이지는 추가 디스크 공간을 사용하고, 버전 관리를 필요로 하며, 추가 워크플로우 처리를 필요로 하는 개별 자산입니다. 별도의 페이지가 필요하지 않으면 하위 자산 생성 및 페이지 추출 활동을 비활성화합니다.
* 임시 워크플로우를 활성화합니다.
* Granite 워크플로우 큐를 조정하여 동시 작업을 제한합니다.
* 리소스 소비를 제한하도록 ImageMagick를 구성합니다.
* DAM 자산 업데이트 워크플로우에서 불필요한 단계를 제거합니다.
* 워크플로우 및 버전 제거를 구성합니다.
* Lucene 인덱스 구성을 최적화합니다.
* 최신 서비스 팩 및 핫픽스로 인덱스를 최적화합니다. 사용할 수 있는 추가 인덱스 최적화에 대해서는 Adobe 고객 지원 센터에 문의하십시오.
* `guessTotal` 을 사용하여 쿼리 성능을 최적화합니다.
* 파일 컨텐츠에서 파일 유형을 검색하도록 AEM을 구성하는 경우([!UICONTROL AEM Web Console]에서 [!UICONTROL Day CQ DAM Mime 유형 서비스]를 구성), 작업이 리소스를 많이 소모하므로 비스파이크 시간 동안 많은 파일을 대량으로 업로드하십시오.
