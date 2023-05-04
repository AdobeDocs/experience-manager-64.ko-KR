---
title: 컬렉션, 코드 조각 및 코드 조각 템플릿에 대한 다중 임차인
description: 무단 액세스를 방지하기 위해 고객 조직을 기반으로 CRX 저장소의 컨텐츠를 구분합니다.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 9%

---

# 컬렉션, 코드 조각 및 코드 조각 템플릿에 대한 다중 임차인 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다중 임차인 기능을 사용하면 조직 접두사와 조직 ID를 기반으로 CRX의 컨텐츠를 구분하여 다른 조직의 사용자가 무단 액세스로부터 컨텐츠를 보호할 수 있습니다.

Adobe Experience Manager (AEM) 자산은 각 조직의 데이터를 다른 경로에 저장합니다. 각 조직별 경로는 조직 접두사와 조직 ID로 식별됩니다.
CRX에 다른 유형의 자산이 저장되는 기존 위치에 포함됩니다.

예를 들어, `Demo`, AEM assets는 기본적으로 폴더를 `../content/dam/Demo` 위치(CRX)를 참조하십시오. 멀티 테넌트 관리 기능을 활성화한 상태에서 데이터를 `../content/dam/<organization prefix>/<organization id>Demo`.

예를 들어에 할당된 AEM Assets(주문형)의 Adobe Marketing Cloud 사용자의 경우 `aodpremium` 조직에서는 다중 임차인 기능을 사용하여 다음 경로를 구성할 수 있습니다 `../content/dam/mac/aodpremiumDemo`를 구분하는 것이 좋습니다. 이 예에서 `mac` 는 조직 접두사이고, `aodpremium` 는 조직 ID입니다.

사용자의 조직 및 ID를 기반으로 이 정규화된 경로는 AEM Assets 인터페이스 및 다양한 마법사에 표시되며 세그먼트 지정을 적용하기 위한 이동 및 코드 조각 만들기 마법사를 포함합니다.

다중 임차인 기능을 사용하면 다음 유형의 자산 및 구성 요소를 세그먼트화할 수 있습니다.

* 컬렉션
* 공용 컬렉션
* 카탈로그(페이지 추가/선택 마법사 포함)
* 템플릿
* 코드 조각 템플릿
* Lightbox
