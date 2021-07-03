---
title: AEM에서 자산 검색
description: 필터 패널을 사용하여 AEM에서 필요한 자산을 찾는 방법과 검색에 표시되는 자산을 사용하는 방법을 알아봅니다.
contentOwner: AG
feature: 검색,메타데이터
role: User
exl-id: cc1a5946-e13d-4433-a25a-d297fd07e2e4
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 3%

---

# AEM에서 자산 검색 {#search-assets-in-aem}

필터 패널을 사용하여 AEM에서 필요한 자산을 찾는 방법과 검색에 표시되는 자산을 사용하는 방법을 알아봅니다.

필터 패널을 사용하여 자산, 폴더, 태그 및 메타데이터를 검색합니다. 와일드카드 별표를 사용하여 문자열의 일부를 검색할 수 있습니다.

필터 패널에서는 일반 분류 순서가 아니라 여러 가지 방법으로 자산 및 폴더를 검색할 수 있는 다양한 옵션을 제공합니다.

다음 옵션(설명)을 기준으로 검색할 수 있습니다.

* 파일 유형
* 파일 크기
* 필드 이름
* 마지막 수정 날짜
* 상태
* 방향
* 스타일
* 인사이트

<!-- TBD keystroke 65 article and port applicable changes here. This content goes. -->

필터 패널을 사용자 지정하고 [검색 패싯](search-facets.md)을 사용하여 검색 설명을 추가/제거할 수 있습니다. [필터] 패널을 표시하려면 다음 단계를 수행합니다.

1. Assets 사용자 인터페이스의 도구 모음에서 ![search_icon](assets/search_icon.png) 을 탭/클릭하여 Omnisearch 상자를 표시합니다.
1. 검색어를 입력하고 Enter 키를 누릅니다. 또는 검색어를 입력하지 않고 Enter 키를 누르면 됩니다. 검색 기능이 작동하지 않는 선행 공백을 입력하지 마십시오.

1. GlobalNav 아이콘을 탭/클릭합니다. [필터] 패널이 표시됩니다.

   ![filters_panel-1](assets/filters_panel-1.png)

   검색하는 항목의 유형에 따라 검색 결과의 맨 위에 일치하는 항목 수가 표시됩니다.

   ![number_of_searches](assets/number_of_searches.png)

## 파일 형식 검색 {#search-for-file-types}

필터 패널은 검색 경험에 더 많은 세부 사항을 추가하고 검색 기능을 더 다양하게 만들 수 있도록 해줍니다. 원하는 세부 수준으로 쉽게 드릴다운할 수 있습니다.

예를 들어, 이미지를 찾으려면 **[!UICONTROL 파일 유형]** 조건자를 사용하여 비트맵 이미지를 사용할지 아니면 벡터 이미지를 선택할지를 선택합니다.

![image_type](assets/image_type.png)

이미지에 대한 MIME 유형을 지정하여 검색 범위를 더 좁힐 수 있습니다.

![mime_type](assets/mime_type.png)

마찬가지로 문서를 검색할 때 PDF 또는 MS Word와 같은 형식을 지정할 수 있습니다.

![문서](assets/documents.png)

## 파일 크기를 기준으로 검색 {#search-based-on-file-size}

**파일 크기** 조건자를 사용하여 크기를 기준으로 자산을 검색합니다. 검색 범위를 좁히려면 크기 범위의 하한과 상한을 지정할 수 있습니다. KB, MB 등의 측정 단위를 지정할 수도 있습니다.

![unit_of_measure](assets/unit_of_measure.png)

## 자산이 마지막으로 수정된 시기를 기준으로 검색 {#search-based-on-when-assets-are-last-modified}

진행 중인 자산을 관리하거나 검토 워크플로우를 모니터링하는 경우 정확한 타임스탬프를 기반으로 자산이 마지막으로 수정된 시기를 검색할 수 있습니다. 예를 들어, 자산이 수정되기 전이나 후의 날짜를 지정합니다.

![last_modified_date](assets/last_modified_dates.png)

다음 옵션을 사용하여 검색에서 더 높은 수준의 세부기간을 달성할 수도 있습니다.

![timestamp](assets/timestamp.png)

## 상태 기반 검색 {#search-based-on-status}

게시, 승인, 체크아웃 및 만료와 같은 다양한 유형의 상태를 기반으로 자산을 검색하려면 **상태** 조건자를 사용합니다.

![상태](assets/status.png)

예를 들어, 자산 게시를 모니터링할 때 적절한 옵션을 사용하여 게시되는 자산을 검색할 수 있습니다.

![페이지를](assets/publish.png)

자산의 검토 상태를 모니터링할 때 적절한 옵션을 사용하여 승인 중인 자산 또는 승인 보류 중인 자산을 찾습니다.

![승인](assets/approval.png)

## 인사이트 데이터를 기반으로 검색 {#search-based-on-insights-data}

다양한 Creative 앱에서 가져온 사용 통계를 기반으로 자산을 검색하려면 **Insights** 조건자를 사용하십시오. 사용 데이터는 다음 카테고리로 그룹화됩니다.

* 사용 점수
* 노출 횟수
* 클릭 수
* 자산이 표시되는 미디어 채널

![통찰력](assets/insights.png)
