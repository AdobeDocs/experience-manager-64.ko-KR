---
title: 에서 비동기 작업 구성 [!DNL Adobe Experience Manager].
description: 리소스를 많이 사용하는 일부 작업을 비동기식으로 완료하여 성능을 최적화합니다. [!DNL Experience Manager Assets].
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0abdfe87-d932-41dd-b1e6-9f5fa5b924fe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 20%

---

# 비동기 작업 {#asynchronous-operations}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

성능에 대한 부정적인 영향을 줄이려면 [!DNL Adobe Experience Manger Assets] 장시간 실행되는 특정 리소스 집약적인 자산 작업을 비동기식으로 처리합니다. 비동기 처리에는 시스템 리소스의 가용성에 따라 여러 작업을 대기열에 넣고 이를 연속적으로 실행하는 작업이 포함됩니다. 이러한 작업은 다음과 같습니다.

* 여러 자산 삭제.
* 여러 참조가 있는 많은 자산 또는 자산 이동.
* 자산 메타데이터 일괄적으로 내보내기 및 가져오기

에서 비동기 작업의 상태를 볼 수 있습니다 **[!UICONTROL 비동기 작업 상태]** 페이지.

>[!NOTE]
>
>기본적으로 [!DNL Assets] 작업은 동시에 실행됩니다. If `N` CPU 코어 수, `N/2` 작업은 기본적으로 동시에 실행될 수 있습니다. 작업 큐에 대한 사용자 지정 설정을 사용하려면 **[!UICONTROL 비동기 작업 기본 큐]** 구성 [!UICONTROL 웹 콘솔]. 자세한 내용은 [큐 구성](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations)을 참조하십시오.

## 비동기 작업 상태 모니터링 {#monitoring-the-status-of-asynchronous-operations}

항상 [!DNL Assets] 작업을 비동기식으로 처리하면 [!DNL Experience Manager] [받은 편지함](/help/sites-authoring/inbox.md) 및 을 사용할 수 있습니다. 비동기 작업의 상태를 자세히 보려면 **[!UICONTROL 비동기 작업 상태]** 페이지로 이동합니다.

1. 에서 [!DNL Experience Manager] 인터페이스 클릭 **[!UICONTROL 작업]** > **[!UICONTROL 작업]**.

1. **[!UICONTROL 비동기 작업 상태]** 페이지에서 작업 세부 사항을 검토합니다.

   ![비동기 작업의 상태 및 세부 정보](assets/job_status.png)

   작업 진행 상황을 확인하려면 **[!UICONTROL 상태]** 열. 진행 상태에 따라 다음 상태 중 하나가 표시됩니다.

   * **[!UICONTROL 활성]**: 작업을 처리 중입니다..
   * **[!UICONTROL 성공]**: 작업이 완료되었습니다.
   * **[!UICONTROL Fail]** or **[!UICONTROL Error]**: The operation could not be processed.
   * **[!UICONTROL 예약됨]**: 나중에 처리하도록 작업이 예약되었습니다.

1. 활성 작업을 중지하려면 목록에서 해당 작업을 선택하고 **[!UICONTROL 정지]** ![중지 아이콘](assets/do-not-localize/stop_icon.svg) 를 클릭합니다.

1. 설명 및 로그 등 추가 세부 사항을 보려면 작업을 선택하고 **[!UICONTROL 열기]** ![open_icon](assets/do-not-localize/edit_icon.svg) 를 클릭합니다. 작업 세부 사항 페이지가 표시됩니다.

   ![메타데이터 가져오기 작업의 세부 정보](assets/job_details.png)

1. 목록에서 작업을 삭제하려면 도구 모음에서 **[!UICONTROL 삭제]**&#x200B;를 선택합니다. CSV 파일로 세부 사항을 다운로드하려면 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >상태가 활성 또는 큐에 있는 경우 작업을 삭제할 수 없습니다.

## 완료된 작업 제거 {#purge-completed-tasks}

[!DNL Experience Manager Assets] 매일 0100시간에 제거 작업을 실행하여 하루 이상 경과한 완료된 비동기 작업을 삭제합니다.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

삭제 작업에 대한 일정 및 완료된 작업의 세부 사항이 삭제되기 전에 보존 기간을 수정할 수 있습니다. 특정 시점에 세부 사항이 유지되도록 완료된 작업의 최대 수를 구성할 수도 있습니다.

1. 에서 [!DNL Experience Manager] 인터페이스 클릭 **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**.
1. 를 엽니다. **[!UICONTROL Adobe CQ DAM 비동기 작업 제거 예약]** 작업.
1. 완료된 작업을 삭제한 후 임계값 수 및 내역에 세부 사항이 유지되는 최대 작업 수를 지정합니다. 변경 사항을 저장합니다.

   ![비동기 작업 제거를 예약하기 위한 구성](assets/purge_job.png)

## 비동기 삭제 작업에 대한 임계값 구성 {#configure-thresholds-for-asynchronous-delete-operations}

삭제할 자산 또는 폴더의 수가 설정된 임계값 수를 초과하는 경우 삭제 작업이 비동기식으로 수행됩니다.

1. 에서 [!DNL Experience Manager] 인터페이스 클릭 **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**.
1. 에서 [!UICONTROL 웹 콘솔]를 열고 **[!UICONTROL 비동기 삭제 작업 처리]** 구성.
1. 에서 **[!UICONTROL 자산의 임계값 수]** 상자에서 자산, 폴더 또는 참조를 비동기식으로 삭제할 임계값 수를 지정합니다. 변경 사항을 저장합니다.

   ![자산을 삭제할 작업에 대한 임계값 제한 설정](assets/delete_threshold.png)

## 비동기 이동 작업에 대한 임계값 구성 {#configure-thresholds-for-asynchronous-move-operations}

이동할 자산, 폴더 또는 참조 수가 설정된 임계값 수를 초과하는 경우 이동 작업이 비동기식으로 수행됩니다.

1. 에서 [!DNL Experience Manager] 인터페이스, **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**.
1. 에서 [!UICONTROL 웹 콘솔]를 열고 **[!UICONTROL 비동기 이동 작업 처리]** 구성.
1. 에서 **[!UICONTROL 자산/참조의 임계값 수]** 상자에서 자산, 폴더 또는 참조를 비동기식으로 이동할 임계값 수를 지정합니다. 변경 사항을 저장합니다.

   ![작업을 통해 자산을 이동할 임계값 제한 설정](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Experience Manager에서 이메일 구성](/help/sites-administering/notification.md).
>* [자산 메타데이터 일괄적으로 가져오거나 내보냅니다](/help/assets/metadata-import-export.md).

