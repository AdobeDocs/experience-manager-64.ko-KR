---
title: 작업 관리자 데이터베이스에서 레코드 제거
seo-title: Purge records from the Job Manager database
description: 프로세스 데이터가 크면 AEM Forms 성능이 저하될 수 있습니다. 레코드가 더 이상 필요하지 않은 경우 프로세스 데이터를 삭제하는 것이 좋습니다.
seo-description: Large process data can result in lower AEM forms performance. It is good practice to purge process data when records are no longer necessary.
uuid: cf214498-36e9-4dcc-b4d4-e7c46f80dbab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 69a406f2-4fa8-40bb-b671-7b0f5b6a2c4c
exl-id: be2e2a4b-5aac-4612-81b6-b4bbb3036d77
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 1%

---

# 작업 관리자 데이터베이스에서 레코드 제거 {#purge-records-from-the-job-manager-database}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

장기간 프로세스가 호출될 때 생성되는 프로세스 데이터는 너무 커져서 AEM Forms 성능이 저하되고 불필요한 디스크 공간이 사용될 수 있습니다. 레코드가 더 이상 필요하지 않은 경우 프로세스 데이터를 삭제하는 것이 좋습니다.

관리 콘솔을 사용하여 오래된 레코드를 한 번 지우거나 일반 자동 삭제를 스케줄링할 수 있습니다. 사용되지 않는 레코드를 삭제하는 다른 방법은 [프로세스 데이터 삭제](/help/forms/using/admin-help/purging-process-data.md#purging-process-data).

**작업 제거 스케줄러 페이지에 액세스**

1. 관리 콘솔에서 페이지의 오른쪽 위 모서리에 있는 상태 모니터를 클릭합니다.
1. 작업 제거 스케줄러 탭을 클릭합니다.

현재 예약된 삭제에 대한 정보는 [작업 제거 스케줄러 정보] 상자에 표시됩니다.

>[!NOTE]
>
>[스케줄러 중지]를 클릭하면 나중에 예약된 모든 숙제가 중지되지만 이미 진행 중인 제거 작업은 중지하지 않습니다.

**1회 제거 예약**

1. 한 번만 선택합니다.
1. 완료된 레코드 삭제 필터 영역에서 레코드가 사용되지 않고 삭제할 준비가 된 것으로 간주되는 이후의 일 또는 주 수를 지정합니다.

   >[!NOTE]
   >
   >완료되지 않은 프로세스와 관련된 레코드는 지정된 기간보다 오래된 경우에도 삭제되지 않습니다.

1. 제거 시기를 지정합니다. 현재 날짜 및 시간 사용 확인란을 선택하거나 확인란의 선택을 취소하고 달력 및 시계 아이콘을 클릭하여 비우기 수행 날짜 및 시간을 지정합니다.

   >[!NOTE]
   >
   >과거의 시작 날짜 및 시간을 지정하는 경우 스케줄러 시작 을 클릭하면 즉시 제거가 수행됩니다.

1. 스케줄러 시작 을 클릭합니다. 이전에 예약한 모든 스케줄러 설정은 새 설정으로 대체됩니다.

**자동 제거 일정 구성**

1. 반복 간격 을 선택하고 제거 사이의 일 또는 주 수를 지정합니다.
1. 완료된 레코드 삭제 필터 영역에서 레코드가 사용되지 않고 삭제할 준비가 된 것으로 간주되는 이후의 일 또는 주 수를 지정합니다. 값을 로 설정할 수 없습니다 `0`.

   >[!NOTE]
   >
   >완료되지 않은 프로세스와 관련된 레코드는 지정된 기간보다 오래된 경우에도 삭제되지 않습니다.

1. 제거 시작 시기를 지정합니다. 현재 날짜 및 시간 사용 확인란을 선택하거나 확인란의 선택을 취소하고 달력 및 시계 아이콘을 클릭하여 비우기 수행 날짜 및 시간을 지정합니다.

   >[!NOTE]
   >
   >과거의 시작 날짜 및 시간을 지정하는 경우 AEM Forms는 지정한 날짜를 기준으로 논리 다음 시작 날짜를 계산합니다. 예를 들어, 작업 삭제를 4월 7일에 매주 시작하여 4월 9일이면 첫 번째 제거가 4월 14일에 발생합니다.

1. 스케줄러 시작 을 클릭합니다. 이전에 예약한 모든 스케줄러 설정은 새 설정으로 대체됩니다.
