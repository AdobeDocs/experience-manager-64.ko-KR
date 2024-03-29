---
title: 프로세스 인스턴스 검색
seo-title: Searching for process instances
description: 프로세스 검색 페이지에서 프로세스 인스턴스를 찾기 위한 검색 기준을 입력할 수 있습니다.
seo-description: Use the Process Search page to enter search criteria for finding a process instance.
uuid: 4a9c5b05-add5-4278-9c6f-d1928b6860d2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 88b634bb-8f6c-4830-ad01-821668609615
exl-id: 25a01630-47ec-4823-ad11-9a636697f3dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# 프로세스 인스턴스 검색{#searching-for-process-instances}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

프로세스 검색 페이지에서 프로세스 인스턴스를 찾기 위한 검색 기준을 입력할 수 있습니다. Forms Workflow 페이지나 프로세스 인스턴스 페이지에서 검색을 눌러 프로세스 검색 페이지에 액세스할 수 있습니다.

기본 기준을 입력하여 일반 검색을 수행하거나 특정 속성을 사용하여 세부 검색을 수행하거나 기본 기준 및 특정 속성의 조합을 사용하여 통합 검색을 수행할 수 있습니다.

## 일반 검색 수행 {#perform-a-general-search}

프로세스 인스턴스의 프로세스 ID를 알고 있거나, 관련 프로세스 인스턴스 그룹을 찾고 있거나, 프로세스 인스턴스가 몇 개만 실행 중인 경우, 프로세스에 대한 일반 검색은 가장 적절합니다.

일반 검색을 수행할 기본 기준을 입력합니다. 여러 기준을 입력하면 암시된 AND 조건으로 검색이 수행됩니다.

1. 관리 콘솔에서 서비스 > Forms 워크플로우 > 프로세스 검색 을 클릭합니다.
1. 프로세스 검색 페이지의 일반 검색 아래에서 다음 기준을 제공합니다.

   * **프로세스 ID:** 각 고유한 프로세스 인스턴스를 식별하는 양의 정수입니다.
   * **프로세스 상태:** 목록에서 상태를 선택합니다.
   * **애플리케이션:** 목록에서 응용 프로그램을 선택합니다. 배포된 애플리케이션만 표시됩니다.
   * **프로세스 이름 - 버전:** 메뉴에서 프로세스 이름을 선택합니다. 배포된 프로세스만 표시됩니다.

1. 검색을 클릭합니다. 발견된 인스턴스를 나열하는 프로세스 인스턴스 페이지가 나타납니다.

## 프로세스에 대한 자세한 검색 수행 {#perform-a-detailed-search-for-a-process}

특정 속성을 입력하여 자세한 검색을 수행할 수 있습니다. 실행 중인 프로세스 인스턴스가 많으므로 특정 기준으로 가능한 검색 범위를 좁히는 것이 필요한 경우 세부 검색이 가장 적합합니다.

1. 관리 콘솔에서 서비스 > Forms 워크플로우 > 프로세스 검색 을 클릭합니다.
1. 프로세스 검색 페이지의 상세 검색에서 첫 번째 기준 세트를 지정합니다.

   * 속성 목록에서 속성을 선택합니다.
   * 필터 목록에서 연산자를 선택합니다.
   * 값 상자에 선택한 속성에 적합한 값을 입력합니다.

1. 다른 행을 추가하려면 필터 추가를 선택합니다. 다른 속성, 필터, 값 목록 및 조건 목록이 표시됩니다.
1. Condition에서 AND 또는 OR를 선택합니다. 검색 범위를 더 좁히려면 필요에 따라 1~3단계를 반복합니다.
1. 행을 추가하거나 제거하려면 추가 필터 또는 더 적은 필터를 클릭합니다. 1개~4개 행을 사용할 수 있습니다.
1. 검색을 클릭합니다. 발견된 인스턴스를 나열하는 프로세스 인스턴스 페이지가 나타납니다.

[프로세스 인스턴스 상태 정보](/help/forms/using/admin-help/processes.md#about-process-instance-statuses)

## 프로세스에 대해 통합 검색 수행 {#perform-a-combined-search-for-a-process}

일반 검색과 상세 검색을 모두 기준으로 검색을 생성하려면 해당 영역 사이에 암묵적 AND를 사용하여 프로세스 검색 페이지의 일반 검색 영역과 상세 검색 영역 모두에 검색 기준을 입력합니다.

검색이 너무 좁은 경우에는 인스턴스를 찾을 수 없습니다.
