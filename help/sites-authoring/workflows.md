---
title: 워크플로우 작업
seo-title: 워크플로우 작업
description: AEM의 워크플로우에서는 페이지나 자산에서 수행되는 일련의 단계들을 자동화할 수 있습니다.
seo-description: AEM의 워크플로우에서는 페이지나 자산에서 수행되는 일련의 단계들을 자동화할 수 있습니다.
uuid: c4442d2a-c6b0-49d4-a1ce-384017c45bf0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 7cb99618-d903-4cfb-b0d9-b23d189f6e78
exl-id: 8d318fd5-3d8f-4144-95c8-d90685378a91
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 100%

---

# 워크플로우 작업{#working-with-workflows}

AEM 워크플로우에서는 (하나 이상의) 페이지 및/또는 자산에서 수행되는 일련의 단계들을 자동화할 수 있습니다.

예를 들어, 편집자는 게시할 때 사이트 관리자가 페이지를 활성화하기 전에 컨텐츠를 검토해야 합니다. 이 예제를 자동화하는 워크플로우는 필요한 작업을 수행할 때가 되면 각 참가자에게 알립니다:

1. 작성자는 페이지에 이 워크플로우를 적용합니다.
1. 편집자는 페이지 컨텐츠를 검토해야 함을 나타내는 작업 항목을 수신합니다. 완료되면 작업 항목이 완료되었음을 나타냅니다.
1. 그러면 사이트 관리자는 페이지 활성화를 요청하는 작업 항목을 수신합니다. 완료되면 작업 항목이 완료되었음을 나타냅니다.

일반적으로 다음이 진행됩니다.

* 컨텐츠 작성자는 워크플로우에 참여할 뿐만 아니라 페이지에 워크플로우를 적용합니다.
* 사용하는 워크플로우는 조직의 비즈니스 프로세스마다 고유합니다.

다음 페이지에 이 내용이 나와 있습니다.

* [페이지에 워크플로우 적용](/help/sites-authoring/workflows-applying.md)
* [워크플로우에 참여](/help/sites-authoring/workflows-participating.md)
