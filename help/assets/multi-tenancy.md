---
title: 컬렉션, 코드 조각 및 코드 조각 템플릿에 대한 다중 임차인
description: 무단 액세스를 방지하기 위해 고객 조직을 기반으로 CRX 저장소의 컨텐츠를 구분합니다.
contentOwner: AG
feature: 컬렉션
role: Architect,Administrator,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 7%

---

# 컬렉션, 코드 조각 및 코드 조각 템플릿에 대한 다중 임차인 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

다중 임차인 기능을 사용하면 조직 접두사와 조직 ID를 기반으로 CRX의 컨텐츠를 구분하여 다른 조직의 사용자가 무단 액세스로부터 컨텐츠를 보호할 수 있습니다.

Adobe Experience Manager (AEM) 자산은 각 조직의 데이터를 다른 경로에 저장합니다. 각 조직별 경로는 조직 접두사와 조직 ID로 식별됩니다.
CRX에 다른 유형의 자산이 저장되는 기존 위치에 포함됩니다.

예를 들어 `Demo` 폴더를 만드는 경우 기본적으로 AEM Assets는 CRX의 `../content/dam/Demo` 위치에 폴더를 저장합니다. 멀티 테넌트 관리 기능을 사용하면 `../content/dam/<organization prefix>/<organization id>Demo`에 데이터를 저장할 수 있습니다.

예를 들어 `aodpremium` 조직에 할당된 AEM Assets(주문형) Adobe Marketing Cloud 사용자의 경우, 다중 임차인 기능을 사용하여 다음 경로를 `../content/dam/mac/aodpremiumDemo`로 구성하고 컨텐츠를 분리할 수 있습니다. 이 예에서 `mac`은 조직 접두사이고 `aodpremium`은 조직 ID입니다.

사용자의 조직 및 ID를 기반으로 이 정규화된 경로는 AEM Assets 인터페이스 및 다양한 마법사에 표시되며 세그먼트 지정을 적용하기 위한 이동 및 코드 조각 만들기 마법사를 포함합니다.

다중 임차인 기능을 사용하면 다음 유형의 자산 및 구성 요소를 세그먼트화할 수 있습니다.

* 컬렉션
* 공용 컬렉션
* 카탈로그(페이지 추가/선택 마법사 포함)
* 템플릿
* 코드 조각 템플릿
* Lightbox
