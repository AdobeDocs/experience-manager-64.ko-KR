---
title: 어떤 테스트 환경이 필요합니까?
seo-title: Which Test Environments are needed?
description: 몇 가지 환경은 테스트의 일부로 간주되어야 합니다
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 6%

---

# 어떤 테스트 환경이 필요합니까?{#which-test-environments-will-be-needed}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

테스트할 구성을 정의하려면 다음을 고려해야 합니다.

**개발** - 단위 및 특정 통합 테스트의 경우.

**테스트** - 대부분의 테스트에 사용됩니다.

**라이브** - 최종 성능 및 스트레스 테스트 고객과의 수락 테스트도 참조하십시오.

또한 어느 인스턴스가 필요한지 결정해야 합니다(일반적으로 모든 테스트 수준에 대해 각 인스턴스 중 하나 이상).

**작성자** - 이 인스턴스를 사용하여 작성자가 컨텐츠를 입력하고 게시할 수 있습니다.

**게시** - 이 인스턴스는 방문자가 액세스할 수 있도록 게시된 형태로 웹 사이트를 제공합니다.

디스패처와 함께 테스트해야 합니다.

마지막으로 실제 하드웨어는 고려해야 합니다. 최종 라이브 환경에 대한 구성에서 가능한 한 시스템에서 성능 테스트를 수행해야 합니다. 이러한 이유로 프로젝트 론치를 다음으로 분할하는 것이 좋습니다.

**소프트 실행** - 가용성 감소 실제 운영 환경에서 성능 테스트, 조정 및 최적화에 소요되는 시간을 허용합니다.

**하드 론치** - 완벽한 가용성.
