---
title: 로그 작업
seo-title: 로그 작업
description: 로그 작업을 통해 AEM 문제를 해결하는 방법을 알아봅니다.
seo-description: 로그 작업을 통해 AEM 문제를 해결하는 방법을 알아봅니다.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 3%

---

# 로그 작업{#working-with-logs}

이 섹션에는 문제 해결에 도움이 되는 로그에 대한 자세한 정보가 포함되어 있습니다.

CRX는 세부 로그를 기록합니다. 압축을 풀고 빠른 시작을 시작하면 다음 위치에서 로그를 찾을 수 있습니다.

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## 디버그 로그 수준 {#activating-the-debug-log-level} 활성화

기본 로그 수준은 INFO, 즉 DEBUG 메시지는 기록되지 않습니다.

디버그 로그 수준을 활성화하려면 CRX 탐색기를 사용하여

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

디버그할 속성입니다. 로그를 많이 생성하므로 DEBUG 로그 수준에서 로그를 필요한 기간보다 오래 두지 마십시오.

디버그 파일의 한 줄은 일반적으로 DEBUG로 시작하며 로그 수준, 설치 관리자 작업 및 로그 메시지를 제공합니다. 예:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패하여 설치 프로그램을 계속할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX 일부가 제대로 설치되지 않아 작동하지 않습니다. |
| 2 | 경고 | 작업에 성공했지만 문제가 발생했습니다. CRX가 제대로 작동하지 않을 수 있습니다. |
| 3 | 정보 | 작업이 성공했습니다. |

## 문제 해결에 사용되는 세부 정보 옵션 {#verbose-option-used-for-troubleshooting}

CRX를 시작할 때 다음과 같이 명령줄에 -v (세부 정보) 옵션을 추가할 수 있습니다.&quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

콘솔에 일부 빠른 시작 로그 출력이 표시되므로 문제 해결을 위해 세부 정보 옵션을 사용하십시오.
