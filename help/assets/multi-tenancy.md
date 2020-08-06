---
title: 컬렉션, 코드 조각 및 코드 조각 템플릿에 대한 다중 임차인
description: 인증되지 않은 액세스를 방지하기 위해 고객 조직을 기반으로 CRX 저장소의 컨텐츠를 구분합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---


# 컬렉션, 코드 조각 및 코드 조각 템플릿에 대한 다중 임차인 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

멀티 테넌시 기능을 사용하면 조직 접두사 및 조직 ID를 기반으로 CRX의 컨텐츠를 분리하여 다른 조직의 사용자가 인증되지 않은 액세스로부터 컨텐츠를 보호할 수 있습니다.

Adobe Experience Manager(AEM) 자산은 각 조직의 데이터를 다른 경로로 저장합니다. 각 조직별 경로는 조직 접두사와 조직 ID로 식별됩니다.
다양한 유형의 에셋이 CRX에 저장되는 기존 위치에 포함됩니다.

예를 들어, 이름이 `Demo`있는 폴더를 만들면 기본적으로 AEM 에셋은 CRX의 `../content/dam/Demo` 위치에 폴더를 저장합니다. 멀티 테넌트 기능을 활성화하면 데이터를 저장할 수 있습니다 `../content/dam/<organization prefix>/<organization id>Demo`.

예를 들어, 조직에 할당된 AEM Assets(주문형)의 Adobe Marketing Cloud 사용자의 경우, 다중 테넌시 기능을 사용하여 다음 경로를 구성하고 컨텐츠를 구분하도록 `aodpremium` `../content/dam/mac/aodpremiumDemo`구성할 수 있습니다. 이 예에서 `mac` 는 조직 접두사이며 조직 ID `aodpremium` 입니다.

사용자의 조직 및 ID를 기반으로, 이 정규화된 경로가 AEM Assets 인터페이스와 다양한 마법사(예: 이동 및 코드 조각 생성 마법사)에 표시되어 세그먼트 분류를 적용합니다.

다중 테넌트 기능을 사용하면 다음 유형의 자산 및 구성 요소를 세그먼트화할 수 있습니다.

* 컬렉션
* 공개 컬렉션
* 카탈로그(페이지 추가/선택 마법사 포함)
* 템플릿
* 코드 조각 템플릿
* Lightbox
