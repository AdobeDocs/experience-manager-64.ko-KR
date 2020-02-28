---
title: 컬렉션, 코드 조각 및 코드 조각 템플릿을 위한 멀티 테넌트
description: 고객 조직에 따라 CRX 저장소의 컨텐츠를 분리하여 무단 액세스를 방지합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# 컬렉션, 코드 조각 및 코드 조각 템플릿을 위한 멀티 테넌트 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

멀티 테넌트 기능을 사용하면 조직 접두사 및 조직 ID를 기반으로 CRX의 컨텐츠를 분리하여 다른 조직의 사용자가 무단 액세스로부터 컨텐츠를 보호할 수 있습니다.

AEM(Adobe Experience Manager) 자산은 각 조직의 데이터를 다른 경로로 저장합니다. 각 조직별 경로는 조직 접두사와 조직 ID로 식별됩니다.
다양한 유형의 에셋이 CRX에 저장되는 기존 위치에 포함되어 있습니다.

예를 들어 AEM 자산이라는 폴더를 만드는 경우 `Demo`기본적으로 CRX의 `../content/dam/Demo` 위치에 폴더가 저장됩니다. 다중 테넌트 관리 기능을 활성화하면 데이터를 저장할 수 `../content/dam/<organization prefix>/<organization id>Demo`있습니다.

예를 들어, 조직에 할당된 AEM 자산(주문형)의 Adobe Marketing Cloud 사용자의 경우, `aodpremium` 다중 테넌트 기능을 사용하여 다음 경로를 구성하고 컨텐츠를 분리할 수 `../content/dam/mac/aodpremiumDemo`있습니다. 이 `mac` `aodpremium` 예에서는 조직 접두사이며 조직 ID입니다.

사용자의 조직 및 ID를 기반으로, 이 정규화된 경로는 AEM 자산 인터페이스와 세그먼트 동기화를 실행하기 위한 이동 및 조각 만들기 마법사를 비롯한 다양한 마법사에 표시됩니다.

다중 테넌트 기능 기능을 사용하면 다음 유형의 자산 및 구성 요소를 세그먼트화할 수 있습니다.

* 컬렉션
* 공개 컬렉션
* 카탈로그(페이지 추가/선택 마법사 포함)
* 템플릿
* 코드 조각 템플릿
* Lightbox
