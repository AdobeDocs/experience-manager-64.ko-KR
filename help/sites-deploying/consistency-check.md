---
title: 일관성 및 순회 검사
seo-title: Consistency and Traversal Checks
description: 일관성 및 순회 검사를 수행하는 방법을 알아봅니다.
seo-description: Learn how to perform consistency and traversal checks.
uuid: 0304e378-7c60-4bf5-9052-d01149d2a6df
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: af9a3e9d-194a-42e5-be28-b238e0c1e55e
feature: Configuring
exl-id: 67dfa0f7-24ac-41ae-83c9-3bb1a8656502
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# 일관성 및 순회 검사{#consistency-and-traversal-checks}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

업그레이드할 때 작업 영역이 일치하지 않아 문제가 발생할 수 있습니다. 테스트 업그레이드를 실행하여 문제가 되는지 확인하거나 일관성 검사를 예방 작업으로 실행할 수 있습니다.

작업 공간 불일치로 인해 실패하는 테스트 업그레이드를 실행하는 경우 crx-quickstart/logs/crx/error.log에 다음과 유사한 항목이 표시됩니다.

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## 일관성 검사 수행 {#perform-a-consistency-check}

일관성 검사를 수행하려면 JMX Mbean** com.adobe.granite(저장소)의 관리 페이지로 **. AEM 기본 화면에서 다음 위치로 이동합니다.

**도구 > 웹 콘솔 > 기본(메뉴 막대) > JMX > com.adobe.granite(저장소)**

기본 설치에서 찾을 수 있는 항목은 다음과 같습니다.  **[|나를 표시|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

에서 **작업** 페이지의 섹션에서 두 가지 방법을 확인할 수 있습니다. **`traversalCheck`** 및 **`consistencyCheck`**. 검사를 실행하려면 작업을 클릭하고 원하는 매개 변수를 입력합니다.

![chlimage_1-117](assets/chlimage_1-117.png)
