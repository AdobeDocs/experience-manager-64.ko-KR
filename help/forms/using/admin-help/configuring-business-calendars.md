---
title: 업무 달력 구성
seo-title: 업무 달력 구성
description: 업무 달력은 조직의 업무 및 비업무 일수를 정의합니다. 비즈니스 달력을 구성하는 방법을 알아봅니다.
seo-description: 업무 달력은 조직의 업무 및 비업무 일수를 정의합니다. 비즈니스 달력을 구성하는 방법을 알아봅니다.
uuid: 0ba610b8-72a8-480c-8783-70d98cbe890a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7a85e13d-4800-47c4-812a-5c6e2355298a
exl-id: d29e1b1e-62df-4b0d-aa64-ad98568cf4a6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1934'
ht-degree: 0%

---

# 비즈니스 달력 구성 {#configuring-business-calendars}

*업무* 달력 조직에 대한 업무 및 비업무 일수(예: 법정 휴일, 주말 및 회사 종료 일수)를 정의합니다. 비즈니스 달력을 사용하는 경우 AEM Forms에서는 특정 날짜 계산을 수행할 때 비업무일을 건너뜁니다. Workbench에서 작업 미리 알림, 기한 및 에스컬레이션과 같은 사용자 관련 이벤트나 타이머 이벤트 및 대기 서비스와 같이 사용자와 연관되지 않은 작업에 비즈니스 달력을 사용할지 여부를 지정할 수 있습니다.

예를 들어, 작업 미리 알림은 작업이 사용자에게 지정된 후 3영업일 후에 발생하도록 구성됩니다. 그 일은 목요일에 배정된다. 하지만 금요일은 공휴일, 그 다음 2일은 주말날이어서 다음 3일은 공휴일이 아닙니다. 따라서 다음 주 수요일에 전갈을 보내드립니다.

>[!NOTE]
>
>비즈니스 달력을 사용하여 날짜 및 시간을 계산할 때 AEM Forms는 실행 중인 서버의 날짜 및 시간을 사용하고 시간대 간의 차이에 대해서는 조정하지 않습니다. 예를 들어, London에서 실행 중인 서버에서 오전 10시에 작업 미리 알림이 발생하도록 예약되어 있지만 미리 알림을 받는 사용자가 New York City에 있는 경우 사용자는 현지 시간으로 오전 5시에 미리 알림을 받게 됩니다.

## 기본 비즈니스 달력 사용 {#using-the-default-business-calendar}

AEM Forms에서는 토요일 및 일요일을 비업무일로 지정하는 기본 비즈니스 달력(*기본 달력*)을 제공합니다. 조직의 모든 사용자에게 비업무일이 동일한 경우 조직에 맞게 기본 비즈니스 달력을 업데이트할 수 있습니다. 기본 비즈니스 달력만 사용하는 경우 사용자 관리에서 비즈니스 달력을 활성화하거나 매핑을 제공할 필요가 없습니다. 다른 업무 달력이 정의되지 않은 경우 AEM Forms에서는 기본 업무 달력을 사용합니다.

## 여러 업무 달력 설정 {#setting-up-multiple-business-calendars}

조직의 일부 사용자에게 비업무일이 다른 경우 여러 업무 달력을 정의하고 사용자에 대한 업무 달력의 런타임 해결을 허용하는 매핑을 구성할 수 있습니다.

### 여러 비즈니스 달력 정의 {#define-multiple-business-calendars}

1. 적절한 비즈니스 달력을 사용자와 연결하는 방법을 결정합니다. 비즈니스 달력을 사용자와 연결하는 방법에는 두 가지가 있습니다.

   **그룹 멤버십:** 사용자의 그룹 멤버십에 따라 사용자에게 비즈니스 달력을 할당할 수 있습니다. 이 경우 그룹의 각 사용자는 동일한 비즈니스 달력을 사용합니다.

   사용자가 두 개의 다른 그룹의 멤버이고 해당 그룹이 두 개의 서로 다른 비즈니스 달력에 매핑되어 있는 경우 AEM Forms에서는 검색 결과에서 찾은 첫 번째 달력을 사용합니다. 이 경우 비즈니스 달력 키를 사용하여 사용자를 비즈니스 달력과 연결하는 것이 좋습니다.

   **비즈니스 달력 키:** 사용자 관리에 지정된 설정인 비즈니스 달력 키를 기반으로 사용자에게 비즈니스 달력을 할당할 수 있습니다. 그런 다음 Forms Workflow에서 비즈니스 달력 키를 비즈니스 달력에 매핑합니다.

   사용자에게 비즈니스 달력 키를 할당하는 방법은 엔터프라이즈, 로컬 또는 하이브리드 도메인을 사용하는지에 따라 다릅니다. 도메인 설정에 대한 자세한 내용은 [도메인 추가](/help/forms/using/admin-help/adding-domains.md#adding-domains)를 참조하십시오.

   로컬 또는 하이브리드 도메인을 사용하는 경우 사용자 정보는 사용자 관리 데이터베이스에만 저장됩니다. 이러한 사용자에 대한 비즈니스 달력 키를 설정하려면 사용자 관리에서 사용자를 추가하거나 편집할 때 비즈니스 달력 키 필드에 문자열을 입력합니다. ([사용자 추가 및 구성](/help/forms/using/admin-help/adding-configuring-users.md#adding-and-configuring-users) 참조) 그런 다음 비즈니스 달력 키(문자열)를 Forms Workflow의 비즈니스 달력에 매핑합니다. ([사용자와 그룹을 비즈니스 달력에 매핑](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar)을 참조하십시오.)

   엔터프라이즈 도메인을 사용하는 경우 사용자 정보는 사용자 관리 데이터베이스와 동기화되는 LDAP 디렉토리와 같은 타사 스토리지 시스템에 있습니다. 비즈니스 달력 키를 LDAP 디렉토리의 필드에 매핑할 수 있습니다. 예를 들어, 디렉토리에 있는 각 사용자 레코드에 &quot;국가&quot; 필드가 포함되어 있고 사용자가 위치한 국가를 기준으로 업무 달력을 할당하려는 경우 디렉토리에 대한 사용자 설정을 지정할 때 업무 달력 키 필드에 &quot;국가&quot; 필드 이름을 지정합니다. ([디렉토리 구성](/help/forms/using/admin-help/configuring-directories.md#configuring-directories)을 참조하십시오.) 그런 다음 비즈니스 달력 키(LDAP 디렉토리의 &quot;국가&quot; 필드에 정의된 값)를 Forms Workflow의 업무 달력에 매핑할 수 있습니다. ([사용자와 그룹을 비즈니스 달력에 매핑](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar)을 참조하십시오.)

1. Forms 워크플로우에서 동일한 비업무일을 공유하는 각 사용자 집합에 대한 달력을 정의합니다. ( [비즈니스 달력 만들기 또는 업데이트](configuring-business-calendars.md#create-or-update-a-business-calendar)를 참조하십시오.)
1. Forms 워크플로우에서 각 달력에 대한 비즈니스 달력 키 또는 그룹 멤버십을 매핑합니다. ([사용자와 그룹을 비즈니스 달력에 매핑](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar)을 참조하십시오.)
1. Workbench에서 프로세스 개발자는 미리 알림, 기한 및 에스컬레이션에 비즈니스 달력을 사용할지 여부를 선택합니다. ([Workbench 도움말](https://www.adobe.com/go/learn_aemforms_workbench_63) 참조).

   프로세스 개발자가 비즈니스 달력을 사용하도록 선택하는 경우 AEM Forms는 Administration Console에 정의된 사용자 관리 설정과 비즈니스 달력 매핑을 기반으로 해당 비즈니스 달력을 동적으로 선택하거나, 매핑이 없는 경우 기본 달력을 사용합니다.

   프로세스 개발자가 업무 달력을 사용하지 않는 경우 이벤트의 일자 계산은 매일 업무일로 처리합니다. 예를 들어, 작업이 사용자에게 지정된 후 3일 후에 작업 마감일이 발생하도록 구성됩니다. 그 일은 목요일에 배정된다. 마감일은 주말임에도 불구하고 일요일에 발생합니다.

## 비즈니스 달력 {#create-or-update-a-business-calendar} 만들기 또는 업데이트

조직에 비업무일이 다른 여러 사용자 세트가 포함된 경우 여러 업무 달력을 정의할 수 있습니다. AEM Forms와 함께 제공되는 기본 기본 기본 기본 제공 달력을 포함하여 기존 달력을 변경할 수도 있습니다.

>[!NOTE]
>
>새 비즈니스 달력을 만들지 않으면 기본 달력이 사용됩니다.

1. 관리 콘솔에서 서비스 > Forms 워크플로우 > 비즈니스 달력을 클릭합니다.
1. 새 비즈니스 달력을 추가하려면 ![bus_cal_plus](assets/bus_cal_plus.png)을 클릭합니다. *새 달력*&#x200B;이 드롭다운 목록에 나타납니다. 텍스트를 선택하고 달력의 다른 이름을 입력합니다.

   기존 비즈니스 달력을 편집하려면 드롭다운 목록에서 해당 일정을 선택합니다.

1. 비업무일 기본 아래에서 주말 등 비업무일을 주별 선택합니다.
1. [] 선택 사항업무 시간 사용을 선택하고 업무 일수의 시작 및 종료 시간을 지정합니다.

   이 옵션을 선택하면 지정된 시간 범위 전에 발생하는 이벤트가 시간 범위의 시작 시간으로 이동되고 시간 범위 이후에 발생하는 이벤트가 다음 영업일의 시작 시간으로 이동됩니다.

   예를 들어, 사용자에게 화요일 오전 2시에 작업이 할당되고 해당 작업에 대한 미리 알림은 업무일로 2일로 설정되는 상황을 생각해 보겠습니다. 근무 시간이 없으면, 목요일 오전 2시에 상기시켜 드리겠습니다. 근무 시간이 오전 8시에서 오후 5시로 설정되면, 목요일 오전 8시로 미리 알림이 푸시됩니다. 영업 시간이 없으면, 화요일 오후 6시에 미리 알림 이벤트가 생성되면 목요일 영업 시간 이후에 알림 이벤트가 발생할 것입니다. 근무 시간이 오전 8시에서 오후 5시로 설정되어 있으면, 금요일 오전 8시에 알림 메시지가 나타납니다.

1. 왼쪽의 달력에서 휴일과 같은 비영업일을 두 번 클릭합니다. 과거에 일은 선택할 수 없습니다. 선택한 비업무일이 오른쪽 목록에 나타나고 날짜가 한 줄에 두 번 표시됩니다. 왼쪽의 일자를 선택하여 비업무일의 이름 또는 설명을 입력합니다.

   목록에서 비업무일을 제거하려면 그 날 옆에 ![bus_cal_trash](assets/bus_cal_trash.png)를 클릭하십시오.

1. [] 선택 사항이 달력이 기본 달력이 되도록 하려면 기본 달력을 선택합니다. 기본 달력은 사용자 관련 이벤트에 대한 다른 달력 매핑이 없거나 타이머 이벤트 또는 대기 서비스에 대한 비즈니스 달력이 지정되지 않은 경우 사용됩니다. 기본 달력을 삭제할 수 없습니다.
1. 비업무일 정의를 마친 경우 달력 사용 을 선택하여 활성화한 다음 저장을 누릅니다.

   기존 달력을 업데이트하는 경우 새 버전은 즉시 적용되며 이미 실행 중인 작업을 포함하여 모든 비즈니스 달력 계산에 사용됩니다.

   >[!NOTE]
   >
   >달력을 활성화하지 않으면 기본 달력이 사용됩니다.

## 사용자 및 그룹을 비즈니스 달력 {#mapping-users-and-groups-to-a-business-calendar}에 매핑

비즈니스 달력을 사용자와 연결하는 데에는 두 가지 방법을 사용할 수 있습니다. 비즈니스 달력 키 또는 사용자가 속한 디렉토리 그룹을 기준으로 사용자에게 업무 달력을 지정할 수 있습니다. 매핑 탭을 사용하여 AEM Forms에서 사용할 방법을 지정하고, 비즈니스 달력 키 및 그룹을 비즈니스 달력에 매핑합니다. 비즈니스 달력 키를 사용자와 연결하는 방법에 대한 자세한 내용은 [여러 비즈니스 달력 설정](configuring-business-calendars.md#setting-up-multiple-business-calendars)을 참조하십시오.

### 비즈니스 달력 키 {#associate-business-calendars-with-users-based-on-business-calendar-keys}에 따라 비즈니스 달력을 사용자와 연결

1. 관리 콘솔에서 서비스 > 양식 워크플로우 > 비즈니스 달력을 클릭한 다음 매핑 탭을 클릭합니다.
1. 시스템이 사용할 목록(User Manager Business Calendar Key Resolution)을 선택합니다.
1. 사용자 관리자 비즈니스 달력 키 표시를 선택합니다. 사용자 관리에서 정의된 고유한 비즈니스 달력 키 세트가 들어 있는 목록이 표시됩니다.

   로컬 및 하이브리드 도메인의 경우 사용자 관리의 비즈니스 달력 키 필드에 입력한 값이 목록에 표시됩니다. 엔터프라이즈(LDAP) 도메인의 경우 LDAP 도메인 설정에서 구성된 LDAP 필드(예: &quot;국가&quot;)에서 반환되는 고유 세트가 목록에 표시됩니다.

   사용자 관리 관리자가 비즈니스 달력 키를 정의하지 않은 경우 목록이 비어 있습니다.

1. UM 비즈니스 달력 키 목록에서 각 항목에 대해 달력을 선택합니다.
1. 저장을 클릭합니다.

### 디렉터리 서비스 그룹 {#associate-business-calendars-with-users-and-groups-based-on-directory-service-groups}에 따라 비즈니스 일정을 사용자 및 그룹과 연결

1. 관리 콘솔에서 서비스 > 양식 워크플로우 > 비즈니스 달력을 클릭한 다음 매핑 탭을 클릭합니다.
1. 시스템에서 사용할 그룹 목록에서 디렉토리 서버에서 정의한 그룹을 선택합니다.
1. 매핑 탭에서 디렉토리 서비스 그룹 표시를 선택합니다. 사용자 관리에 정의된 그룹이 포함된 목록이 표시됩니다. ([디렉토리 설정](/help/forms/using/admin-help/configuring-directories.md#directory-settings)을 참조하십시오.)

   >[!NOTE]
   >
   >Workbench에서 비즈니스 달력을 사용하도록 사용자 서비스를 구성하고 서비스가 그룹에 지정된 경우 AEM Forms에서는 여기에 지정된 그룹 매핑을 사용하여 그룹에 대한 달력을 확인합니다. AEM Forms에서는 사용자의 달력을 해결하기 위해 비즈니스 달력 키를 사용하는 경우에도 항상 그룹 매핑을 사용하여 그룹의 일정을 확인합니다. 그룹 매핑을 찾을 수 없으면 기본 비즈니스 달력이 사용됩니다.

1. 디렉토리 서비스 그룹 목록의 각 항목에 대해 달력을 선택합니다.
1. 저장을 클릭합니다.

## 비즈니스 달력 내보내기 및 가져오기 {#exporting-and-importing-business-calendars}

AEM Forms를 사용하면 비즈니스 달력을 XML 파일로 내보내고 가져올 수 있습니다. 이 기능을 사용하여 달력을 스테이징 시스템에서 프로덕션 시스템으로 이동할 수 있습니다.

>[!NOTE]
>
>이 기능은 AEM Forms에서 제공하는 기본 비즈니스 달력을 포함하여 정의된 모든 업무 달력을 내보내고 가져옵니다. 기존 일정과 이름이 같은 가져온 비즈니스 달력이 기존 달력을 덮어씁니다.

### 비즈니스 달력 내보내기 {#export-business-calendars}

1. 관리 콘솔에서 서비스 > 양식 워크플로우 > 비즈니스 달력을 클릭합니다.
1. 내보내기 를 클릭하고 XML 파일을 저장합니다.

### 비즈니스 달력 가져오기 {#import-business-calendars}

1. 관리 콘솔에서 서비스 > 양식 워크플로우 > 비즈니스 달력을 클릭합니다.
1. 가져오기를 클릭합니다. 
1. 내보낸 비즈니스 달력을 포함하는 XML 파일을 선택하고 열기를 누릅니다.

## 비즈니스 달력 {#delete-a-business-calendar} 삭제

조직에서 더 이상 필요하지 않은 업무 달력을 제거할 수 있습니다. 여전히 사용자 및 그룹에 매핑된 비즈니스 달력을 삭제하는 경우 기본 달력이 사용됩니다.

1. 관리 콘솔에서 서비스 > Forms 워크플로우 > 비즈니스 달력을 클릭합니다.
1. 달력을 선택합니다.
1. 삭제를 클릭합니다. 
