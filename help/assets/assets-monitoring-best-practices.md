---
title: Assets 모니터링 우수 사례
description: 환경 및 성능 모니터링을 위한 우수 사례 [!DNL Experience Manager] 인스턴스가 배포된 후 인스턴스입니다.
contentOwner: AG
feature: Asset Management
role: Admin,Architect
exl-id: edbb275a-5ead-4ed2-8708-29e766081d75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 1%

---

# Assets 모니터링 우수 사례 {#assets-monitoring-best-practices}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets 관점에서 모니터링에는 다음 프로세스 및 기술에 대한 관찰과 보고가 포함되어야 합니다.

* 시스템 CPU
* 시스템 메모리 사용
* 시스템 디스크 입출력 및 입출력 대기 시간
* 시스템 네트워크 IO
* JMX MBeans 대상:

   * 힙활용률
   * 워크플로우와 같은 비동기 프로세스

* OSGi 콘솔 상태 검사

일반적으로 [!DNL Assets] 라이브 모니터링과 장기 모니터링이라는 두 가지 방법으로 모니터링할 수 있습니다.

## 라이브 모니터링 {#live-monitoring}

개발 중 또는 로드가 많은 상황에서 라이브 모니터링을 수행하여 환경의 성능 특성을 이해해야 합니다. 일반적으로 라이브 모니터링은 도구 세트를 사용하여 수행해야 합니다. 다음은 몇 가지 권장 사항입니다.

* [시각적 VM](https://visualvm.github.io/): Visual VM을 사용하면 CPU 사용, Java 메모리 사용 등 자세한 Java VM 정보를 볼 수 있습니다. 또한 인스턴스에서 실행되는 코드를 샘플링하고 평가할 수 있습니다.
* [상단](https://man7.org/linux/man-pages/man1/top.1.html): Top은 CPU, 메모리 및 IO 사용을 포함한 사용 통계를 표시하는 대시보드를 여는 Linux 명령입니다. 인스턴스에서 발생하는 상황에 대한 높은 수준의 개요를 제공합니다.
* [상단](https://hisham.hm/htop/): 상단 은 대화형 프로세스 뷰어입니다. Top이 제공할 수 있는 기능 외에도 자세한 CPU 및 메모리 사용을 제공합니다. Top은 `yum install htop` 또는 `apt-get install htop`.

* [Iotop](https://guichaz.free.fr/iotop/): Iotop은 디스크 입출력 사용을 위한 세부 대시보드입니다. 여기에는 디스크 입출력(I/O)을 사용하는 프로세스와 사용 양을 나타내는 바와 미터(M)가 표시됩니다. Iotop은 `yum install iotop` 또는 `apt-get install iotop`.

* [Iftop](https://www.ex-parrot.com/pdw/iftop/): Iftop은 이더넷/네트워크 사용에 대한 자세한 정보를 표시합니다. 이더넷을 사용하는 엔티티의 통신 채널 통계당 정보를 표시하는 경우 사용하는 대역폭과 대역폭이 표시됩니다. Iftop은 `yum install iftop` 또는 `apt-get install iftop`.

* Java 비행 기록(JFR): 비프로덕션 환경에서 자유롭게 사용할 수 있는 Oracle의 상업적 도구입니다. 자세한 내용은 [Java Flight Recorder를 사용하여 CQ 런타임 문제를 진단하는 방법](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq).
* [!DNL Experience Manager] error.log 파일: 당신은 [!DNL Experience Manager] error.log 파일에서 시스템에 기록된 오류의 세부 정보를 확인하십시오. 명령 사용 `tail -F quickstart/logs/error.log` 오류를 식별하려면 조사해야 합니다.
* [워크플로우 콘솔](../sites-administering/workflows.md): 워크플로우 콘솔을 활용하여 지연 또는 문제가 발생하는 워크플로우를 모니터링합니다.

일반적으로 이러한 도구를 함께 사용하여 성능에 대한 포괄적인 아이디어를 얻을 수 있습니다 [!DNL Experience Manager] 인스턴스.

>[!NOTE]
>
>이러한 도구는 표준 도구이며 Adobe에서 직접 지원하지 않습니다. 추가 라이센스가 필요하지 않습니다.

![chlimage_1-142](assets/chlimage_1-142.png) ![chlimage_1-143](assets/chlimage_1-143.png)

## 장기 모니터링 {#long-term-monitoring}

장기 모니터링 [!DNL Experience Manager] 인스턴스에는 모니터되는 동일한 부분을 더 오래 동안 실시간으로 모니터링하는 작업이 포함됩니다. 또한 환경에 따른 경고를 정의하는 작업도 포함됩니다.

### 로그 집계 및 보고 {#log-aggregation-and-reporting}

로그를 집계하는 데 사용할 수 있는 몇 가지 도구(예: Splunk(TM) 및 Elastic Search/Logstash/Kabana(ELK)가 있습니다. 작동 시간을 평가하려면 [!DNL Experience Manager] 예를 들어 시스템에 관련된 로그 이벤트를 이해하고 이를 기반으로 경고를 만드는 것이 중요합니다. 개발 및 운영 방침에 대한 좋은 지식이 있으면 로그 수집 프로세스를 튜닝하여 중요한 경고를 생성하는 방법을 더 잘 이해할 수 있습니다.

### 환경 모니터링 {#environment-monitoring}

환경 모니터링에는 다음 모니터링이 포함됩니다.

* 네트워크 처리량
* 디스크 IO
* 메모리
* CPU 사용률
* JMX MBeans
* 외부 웹 사이트

각 항목을 모니터링하려면 NewRelic(TM) 및 AppDynamics(TM)와 같은 외부 도구가 필요합니다. 이러한 도구를 사용하여 시스템에 대한 경고를 정의할 수 있습니다. 예를 들어 높은 시스템 사용률, 워크플로우 백업, 상태 확인 실패 또는 웹 사이트에 대한 인증되지 않은 액세스 등이 있습니다. Adobe은 다른 도구에 비해 특정 도구를 권장하지 않습니다. 자신에게 적합한 도구를 찾고 이를 활용하여 설명된 항목을 모니터링합니다.

#### 내부 애플리케이션 모니터링 {#internal-application-monitoring}

내부 애플리케이션 모니터링에는 [!DNL Experience Manager] JVM, 컨텐츠 저장소, 플랫폼에 구축된 사용자 정의 응용 프로그램 코드를 통한 모니터링 등 스택을 포함합니다. 일반적으로 SolarWinds(TM), HP OpenView(TM), Hyperic(TM), Javbix(TM) 등과 같이 널리 사용되는 다양한 모니터링 솔루션에서 직접 모니터링할 수 있는 JMX Mbeans를 통해 수행됩니다. JMX에 대한 직접 연결을 지원하지 않는 시스템의 경우 셸 스크립트를 작성하여 JMX 데이터를 추출하고 해당 데이터를 기본적으로 이해하는 형식으로 이러한 시스템에 표시할 수 있습니다.

JMX Mbeans에 대한 원격 액세스는 기본적으로 활성화되지 않습니다. JMX를 통한 모니터링에 대한 자세한 내용은 [JMX 기술을 사용한 모니터링 및 관리](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

대부분의 경우 통계를 효과적으로 모니터링하려면 기준선이 필요합니다. 기준선을 만들려면 미리 설정된 기간 동안의 일반 작업 조건에서 시스템을 관찰한 다음 일반 지표를 식별합니다.

**JVM 모니터링**

Java 기반 애플리케이션 스택과 마찬가지로 [!DNL Experience Manager] 은 기본 Java Virtual Machine을 통해 제공된 리소스에 따라 다릅니다. JVM에 의해 노출된 플랫폼 MXBeans를 통해 이러한 리소스의 상태를 모니터링할 수 있습니다. MXBeans에 대한 자세한 내용은 [플랫폼 MBean 서버 및 플랫폼 MXBeans 사용](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

다음은 JVM에 대해 모니터링할 수 있는 몇 가지 기준 매개 변수입니다.

메모리

* `MBean: lava.lang:type=Memory`
* URL: */system/console/jmx/java.lang:type=Memory*
* 인스턴스: 모든 서버
* 경보 임계값: heap 또는 비heap 메모리 사용률이 해당 최대 메모리의 75%를 초과하는 경우
* 경고 정의: 시스템 메모리가 부족하거나 코드에 메모리 누수가 있습니다. 정의에 도달할 스레드 덤프를 분석합니다.

**참고**: 이 콩에서 제공하는 정보는 바이트 단위로 표시됩니다.

스레드

* MBean: `java.lang:type=Threading`
* URL: */system/console/jmx/java.lang:type=Threading*
* 인스턴스: 모든 서버
* 경보 임계값: 스레드 수가 기준 요소의 150%보다 큰 경우
* 경고 정의: 능동적으로 도망가는 과정이 있거나, 비효율적인 운영으로 많은 양의 자원이 소비되고 있다. 정의에 도달할 스레드 덤프를 분석합니다.

**[!DNL Experience Manager]모니터링**

[!DNL Experience Manager] 또한 JMX를 통해 통계 및 작업 세트를 노출합니다. 이러한 기능은 시스템 상태를 평가하고 사용자에게 영향을 주기 전에 잠재적인 문제를 식별하는 데 도움이 될 수 있습니다. 자세한 내용은 [설명서](/help/sites-administering/jmx-console.md) on [!DNL Experience Manager] JMX MBeans입니다.

다음은 모니터링할 수 있는 몇 가지 기준 매개 변수입니다 [!DNL Experience Manager]:

복제 에이전트

* MBean: `com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>”`
* URL: */system/console/jmx/com.adobe.granite.replication:type=agent,id=&quot;&lt;agent_name>&quot;*
* 인스턴스: 작성자 및 모든 게시 인스턴스 1개(플러시 에이전트)
* 경보 임계값: 값이 `QueueBlocked` 는 true 또는 의 값입니다. `QueueNumEntries` 은 기준선의 150%보다 큽니다.

* 경고 정의: 시스템에서 차단된 큐가 존재하여 복제 대상이 다운되었거나 접근할 수 없음을 나타냅니다. 네트워크 또는 인프라 문제로 인해 과도한 항목이 큐에 올라가 시스템 성능에 부정적인 영향을 줄 수 있습니다.

**참고**: MBean 및 URL 매개 변수의 경우 을 `<AGENT_NAME>` 모니터링할 복제 에이전트의 이름으로 구성됩니다.

세션 카운터

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.jackrabbit.oak:id=7,name=&quot;OakRepository Statistics&quot;,type*=&quot;RepositoryStats&quot;
* 인스턴스: 모든 서버
* 경보 임계값: 열려 있는 세션이 기준 요소를 50% 이상 초과하는 경우
* 경고 정의: 세션은 코드 조각을 통해 열 수 있으며 닫히지 않습니다. 이것은 시간이 지남에 따라 천천히 일어날 수 있고 결국 시스템에서 메모리 누수를 일으킬 수 있다. 시스템에서 세션 수가 변동해야 하지만 지속적으로 증가해서는 안 됩니다.

상태 검사

에서 사용할 수 있는 상태 검사 [작업 대시보드](/help/sites-administering/operations-dashboard.md#health-reports) 모니터링하기 위한 해당 JMX MBeans가 있습니다. 그러나 사용자 정의 상태 검사를 작성하여 추가 시스템 통계를 표시할 수 있습니다.

다음은 모니터링에 유용한 몇 가지 기본 상태 확인입니다.

* 시스템 확인

   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck*
   * 인스턴스: 작성자 1명, 모든 게시 서버
   * 경보 임계값: 상태가 좋지 않으면
   * 경고 정의: 지표 중 하나의 상태는 WARN 또는 CRITICAL입니다. 문제의 원인에 대한 자세한 내용은 로그 속성을 확인하십시오.

* 복제 큐

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck*
   * 인스턴스: 작성자 1명, 모든 게시 서버
   * 경보 임계값: 상태가 좋지 않으면
   * 경고 정의: 지표 중 하나의 상태는 WARN 또는 CRITICAL입니다. 문제를 일으킨 큐에 대한 자세한 내용은 로그 속성을 확인하십시오.

* 응답 성능

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck*
   * 인스턴스: 모든 서버
   * 경보 기간: 상태가 좋지 않으면
   * 경고 정의: 지표 중 하나의 상태는 경고 또는 위기 상태입니다. 문제를 일으킨 큐에 대한 자세한 내용은 로그 속성을 확인하십시오.

* 쿼리 성능

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name= queryStatus,type=HealthCheck*
   * 인스턴스: 작성자 1명, 모든 게시 서버
   * 경보 임계값: 상태가 좋지 않으면
   * 경고 정의: 시스템에서 하나 이상의 쿼리가 느리게 실행됩니다. 문제를 일으킨 쿼리에 대한 자세한 내용은 로그 속성을 확인하십시오.

* 활성 상태 번들

   * MBean: org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck*
   * 인스턴스: 모든 서버
   * 경보 임계값: 상태가 좋지 않으면
   * 경고 정의: 시스템에 비활성 또는 확인되지 않은 OSGi 번들이 있습니다. 문제를 일으킨 번들에 대한 자세한 내용은 로그 속성을 확인하십시오.

* 오류 로그

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck*
   * 인스턴스: 모든 서버
   * 경보 임계값: 상태가 좋지 않으면
   * 경고 정의: 로그 파일에 오류가 있습니다. 문제의 원인에 대한 자세한 내용은 로그 속성을 확인하십시오.

## 일반적인 문제 및 해결 방법  {#common-issues-and-resolutions}

모니터링 과정에서 문제가 발생하면 다음과 같은 몇 가지 문제 해결 작업을 수행하여 [!DNL Experience Manager] 인스턴스:

* TarMK를 사용하는 경우 Tar 압축을 자주 실행합니다. 자세한 내용은 [저장소 유지 관리](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
* 확인 `OutOfMemoryError` 로그. 자세한 내용은 [메모리 문제 분석](https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html).
* 색인화되지 않은 쿼리, 트리 순회 또는 인덱스 순번에 대한 참조가 로그에 있는지 확인합니다. 색인화되지 않은 쿼리 또는 제대로 인덱싱되지 않은 쿼리를 나타냅니다. 쿼리 및 색인 지정 성능 최적화에 대한 우수 사례가 필요하면 를 참조하십시오 [쿼리 및 색인 생성에 대한 우수 사례](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* 워크플로우 콘솔을 사용하여 워크플로우가 예상대로 작동하는지 확인합니다. 가능하면 여러 워크플로우를 하나의 워크플로우로 압축합니다.
* 라이브 모니터링을 재방문하여 특정 리소스의 병목 현상이나 높은 소비자에 대해 살펴봅니다.
* 클라이언트 네트워크에서 송신 지점을 조사하고 수신 포인트는 [!DNL Experience Manager] 인스턴스 네트워크(디스패처 포함). 주로 병목영역입니다. 자세한 내용은 [자산 네트워크 고려사항](assets-network-considerations.md).
* 업그레이드 [!DNL Experience Manager] server. 당신의 사이즈가 적당하지 않을 수도 있습니다 [!DNL Experience Manager] 인스턴스. Adobe 고객 지원 을 통해 서버의 크기가 더 작은지 확인할 수 있습니다.
* 를 검사합니다. `access.log` 및 `error.log` 특정 시간 동안의 항목 파일이 잘못되었습니다. 사용자 지정 코드 예외 항목을 나타낼 수 있는 패턴을 찾습니다. 모니터링하는 이벤트 목록에 추가합니다.
