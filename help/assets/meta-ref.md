---
title: 메타데이터 스키마 참조
description: 'Dublin Core, IPTC 및 기타 메타데이터 스키마를 포함하여 자산 메타데이터를 설명하는 표준 규칙에 대해 알아봅니다. '
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 2%

---

# 메타데이터 스키마 참조 {#metadata-schemata-reference}

다음 참조에는 특정 메타데이터 스키마(알파벳 순서로)에 대한 정보와 속성 및 해당 정의 목록이 포함되어 있습니다.

## 더블린 코어 {#dublin-core}

더블린 코어 메타데이터는 자산을 쉽게 찾을 수 있도록 자산을 설명하는 표준화된 규칙 세트를 제공합니다. [!DNL Experience Manager] 자산에서 Dublin Core는 비디오, 사운드, 이미지 및 문서를 포함한 디지털 자산을 설명합니다.

단순 DCMES(Dublin Core Metadata Element Set)에는 다음 표에 나열된 15개의 메타데이터 요소가 포함되어 있습니다. 각 더블린 코어 요소는 선택 사항이며 반복될 수 있습니다. 미디어 유형별 메타데이터에서처럼 더블린 코어 메타데이터 정보를 추가하거나 삭제할 수 있습니다.

DCMES 외에도 Dublin Core Initiative에서 만든 다른 메타데이터 요소가 있습니다. 자세한 내용은 [Dublin Core Initiative](https://dublincore.org/)를 참조하십시오.

| 속성 | 설명 |
|---|---|
| 참여자 | 컨텐츠에 기여할 책임이 있는 개인 또는 회사입니다. |
| 범위 | 자산이 적용되는 지리적 위치 또는 기간입니다. |
| 작성자 | 컨텐츠 작성을 담당하는 사람 또는 회사입니다. |
| 날짜 | 자산과 연관된 날짜 또는 기간. |
| 설명 | 자산에 대한 자세한 정보입니다. |
| 포맷 | 자산의 파일 형식, 실제 미디어 또는 차원입니다. [!DNL Experience Manager] dc:format을 사용하여 자산의 mime 유형을 나타냅니다. |
| 식별자 | 자산에 대한 고유한 참조. |
| 언어 | 자산의 언어(예: 영어)입니다. |
| 게시자 | 자산을 사용할 수 있도록 하는 담당자 또는 회사입니다. |
| 관계 | 관련 자산. |
| 권한 | 이 자산에 대한 권한이 있는 사람에 대한 정보입니다. |
| source | 자산이 파생되는 관련 자산. |
| 주제 | 자산의 주제입니다. |
| 제목 | 자산의 이름입니다. |
| 유형 | 자산의 특성 또는 장르입니다. |

## IPTC {#iptc}

국제통신협회(IPTC)는 전 세계 언론사의 컨소시엄으로 기술 표준을 개발하고 유지하는 것이 목표다. IPTC는 사진작가들 사이에서 거의 보편적으로 받아들여지는 이미지에 대한 일련의 사진 메타데이터 표준을 정의했다. 이러한 메타데이터 표준은 1990년대에 만들어진 IIM(IPTC Information Interchange Model)으로 알려진 광범위한 표준의 일부입니다.

IPTC 헤더 정보는 대부분 XMP으로 대체되었지만, XMP에 대해 IPTC 핵심 스키마 및 확장 스키마를 사용할 수 있습니다. 이미지 프로그램에서 XMP 및 IPTC 속성이 모두 동기화됩니다.
