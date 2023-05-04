---
title: 코드 함정
seo-title: Code pitfalls
description: AEM용 개발 시 피해야 할 일반적인 코딩 위험
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 9%

---

# 코드 함정{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## Java 코드의 Sling 바인딩 방지 {#avoid-sling-bindings-in-java-code}

Sling Bindings는 90%의 경우에 서비스에 액세스할 수 있는 부적절한 방법입니다. 대신 *@Reference* 또는 *@Inject* 주석.

## Java 코드에서는 Thread.interrupt를 사용하지 마십시오 {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* 잘못된 시간에 호출될 때 Lucene 파일과 영구 캐시 파일을 포함한 파일을 닫을 수 있으므로 위험합니다.

## Java 동기화를 ReadWriteLocks와 혼합하지 마십시오 {#avoid-mixing-java-synchronization-with-readwritelocks}

이 경우 코드가 결국 교착 상태가 될 경합 상태가 될 수 있습니다.
