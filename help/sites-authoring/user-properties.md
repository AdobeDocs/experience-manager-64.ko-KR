---
title: 계정 환경 구성
seo-title: Configuring your account environment
description: AEM에서는 계정과, 작성 환경의 특정 측면들을 구성하는 기능을 제공합니다.
seo-description: AEM provides you with the capability to configure your account and certain aspects of the author environment
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
exl-id: f620e85e-8c77-41a3-a238-9b93c819909d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 59%

---

# 계정 환경 구성{#configuring-your-account-environment}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서는 계정과, 작성 환경의 특정 측면들을 구성하는 기능을 제공합니다.

Using the [User](/help/sites-authoring/user-properties.md#user-settings) option in the [header](/help/sites-authoring/basic-handling.md#the-header) and the associated [My Preferences](#my-preferences) dialog, you can modify your user options.

## 사용자 설정 {#user-settings}

다음 **사용자** 설정 대화 상자에서는 다음에 액세스할 수 있습니다.

* 가장 대상

   * 사용 [가장 대상](/help/sites-administering/security.md#impersonating-another-user) 사용자가 다른 사용자를 대신하여 작업할 수 있는 기능입니다.

* 프로필

   * 다음 주소로 편리한 링크를 제공합니다. [사용자 설정](/help/sites-administering/security.md))

* [내 환경 설정](/help/sites-authoring/user-properties.md#my-preferences)

   * 사용자에게만 해당하는 다양한 환경 설정을 지정합니다.

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## 내 환경 설정 {#my-preferences}

**내 환경 설정** 대화 상자는 헤더에서 [사용자](/help/sites-authoring/user-properties.md#user-settings) 선택 사항을 통해 액세스합니다.

각 사용자는 자신에 대한 특정 속성을 설정할 수 있습니다.

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **언어**

   작성 환경의 UI에 사용할 언어를 정의합니다. 사용 가능한 목록에서 필요한 언어를 선택합니다.

   이 구성은 클래식 UI에도 사용됩니다.

* **창 관리**

   동작 또는 창 열기를 정의합니다. 다음 중 하나를 선택합니다.

   * **여러 창** (기본값)

      * 페이지가 새 창에 열립니다.
   * **단일 창**

      * 페이지가 현재 창에 열립니다.


* **에셋에 대한 데스크탑 작업 표시**

   이 옵션을 사용하려면 AEM 데스크탑 앱을 사용해야 합니다.

* **주석 색상**

   주석을 작성할 때 사용되는 기본 색상을 정의합니다.

   * 색상 블록을 클릭하여 색상을 선택할 견본 선택기를 엽니다.
   * 또는 필드에 원하는 색상의 16진수 코드를 입력하십시오.

* **상대적 날짜 표시**

   가독성을 높이기 위해 AEM은 최근 7일 이내의 날짜를 상대적 날짜(예: 3일 전)로 렌더링하고 이전 날짜를 정확한 날짜(예: 2017년 3월 20일)로 렌더링합니다.

   이 선택 사항은 시스템 날짜가 표시되는 방법을 정의합니다. 다음 옵션을 사용할 수 있습니다.

   * **항상 정확한 날짜 표시**: 항상 정확한 날짜가 표시됩니다(상대적 날짜가 아님).
   * **1일**: 1일 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **7일(기본값)**: 7일 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **1개월**: 한 달 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **1년**: 1년 이내의 날짜는 상대적 날짜가 표시되고, 그 외에는 정확한 날짜가 표시됩니다.
   * **항상 상대적 날짜 표시**: 정확한 날짜는 표시되지 않고 상대적 날짜만 표시됩니다.

* **단축키 사용**

   AEM은 작성의 효율성을 개선하는 다양한 키보드 단축키를 지원합니다.

   * [페이지 편집을 위한 키보드 단축키](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [콘솔용 키보드 단축키](/help/sites-authoring/keyboard-shortcuts.md)

   이 옵션을 사용하면 키보드 단축키를 사용할 수 있습니다. 기본적으로 활성화되어 있지만, 사용자에게 특정 액세스 가능성 요구 사항이 있는 경우와 같이 비활성화할 수 있습니다.

* **클래식 제작 환경 사용**

   이 옵션을 사용하면 [클래식 UI](/help/sites-classic-ui-authoring/home.md)기반 페이지 작성. 기본적으로 표준 UI가 사용됩니다.

* **에셋 홈페이지 활성화**

   이 선택 사항은 시스템 관리자가 전체 조직에 대해 [에셋 홈페이지] 환경을 활성화한 경우에만 사용할 수 있습니다.
