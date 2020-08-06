---
title: 에서 비동기 작업을 [!DNL Adobe Experience Manager]구성합니다.
description: 리소스를 많이 사용하는 작업을 비동기적으로 완료하여 성능을 최적화할 수 [!DNL Experience Manager Assets]있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f6aa1ab2c7a0ddeda1504e95ce4bd57fe74a65fd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 18%

---


# 비동기 작업 {#asynchronous-operations}

성능에 대한 부정적인 영향을 줄이기 위해 장시간 실행되는 특정 리소스 중심 자산 작업을 비동기적으로 [!DNL Adobe Experience Manger Assets] 처리합니다. 비동기 처리에는 여러 작업을 대기열에 넣고 시스템 리소스의 가용성에 따라 여러 작업을 연속으로 실행하는 작업이 포함됩니다. 이러한 작업은 다음과 같습니다.

* 여러 자산 삭제.
* 여러 참조가 있는 많은 자산 또는 자산 이동.
* 에셋 메타데이터를 일괄적으로 내보내기 및 가져오기

비동기 작업 상태 **** 페이지에서 비동기 작업의 상태를 볼 수 있습니다.

>[!NOTE]
>
>기본적으로 [!DNL Assets] 작업은 동시에 실행됩니다. If `N` is the number of CPU cores, `N/2` tasks can execute in parallel, by default. 작업 큐에 대한 사용자 지정 설정을 사용하려면 **[!UICONTROL 웹 콘솔에서]** 비동기 작업 기본 큐 [!UICONTROL 구성을]수정하십시오. 자세한 내용은 [큐 구성](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations)을 참조하십시오.

## Monitor the status of asynchronous operations {#monitoring-the-status-of-asynchronous-operations}

Whenever [!DNL Assets] processes an operation asynchronously, you receive a notification in your [!DNL Experience Manager] [Inbox](/help/sites-authoring/inbox.md) and via an email. 비동기 작업의 상태를 자세히 보려면 **[!UICONTROL 비동기 작업 상태]** 페이지로 이동합니다.

1. In the [!DNL Experience Manager] interface click **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. **[!UICONTROL 비동기 작업 상태]** 페이지에서 작업 세부 사항을 검토합니다.

   ![비동기 작업의 상태 및 세부 정보](assets/job_status.png)

   작업 진행 상태를 확인하려면 상태 **[!UICONTROL 열을]** 참조하십시오. 진행 상태에 따라 다음 상태 중 하나가 표시됩니다.

   * **[!UICONTROL 활성]**: 작업을 처리 중입니다..
   * **[!UICONTROL 성공]**: 작업이 완료되었습니다.
   * **[!UICONTROL 실패]** 또는 **[!UICONTROL 오류]**: 작업을 처리할 수 없습니다.
   * **[!UICONTROL 예약됨]**: 작업은 나중에 처리하도록 예약되어 있습니다.

1. To stop an active operation, select it from the list and click **[!UICONTROL Stop]** ![stop icon](assets/do-not-localize/stop_icon.svg) from the toolbar.

1. To view extra details, for example description and logs, select the operation and click **[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg) from the toolbar. 작업 세부 사항 페이지가 표시됩니다.

   ![메타데이터 가져오기 작업 세부 사항](assets/job_details.png)

1. 목록에서 작업을 삭제하려면 도구 모음에서 **[!UICONTROL 삭제]**&#x200B;를 선택합니다. CSV 파일로 세부 사항을 다운로드하려면 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >상태가 활성 또는 큐에 있는 경우 작업을 삭제할 수 없습니다.

## 완료된 작업 제거 {#purge-completed-tasks}

[!DNL Experience Manager Assets] 하루 100시간에 매일 제거 작업을 실행하여 하루 이상 오래된 완료된 비동기 작업을 삭제합니다.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

삭제 작업에 대한 일정 및 완료된 작업의 세부 사항이 삭제되기 전에 보존되는 기간을 수정할 수 있습니다. 특정 시점에 세부 사항이 유지되도록 완료된 작업의 최대 수를 구성할 수도 있습니다.

1. 인터페이스에서 [!DNL Experience Manager] 도구 **[!UICONTROL > 작업]** > **[!UICONTROL 웹 콘솔]** 을 클릭합니다 ****.
1. [ **[!UICONTROL Adobe CQ DAM 비동기 작업 제거 예약된]** 작업]을 엽니다.
1. 완료된 작업을 삭제한 후 남은 기간(일)과 작업 내역에 세부 사항이 유지되는 최대 작업 수를 지정합니다. 변경 사항을 저장합니다.

   ![비동기 작업의 제거를 예약하기 위한 구성](assets/purge_job.png)

## 비동기 삭제 작업에 대한 임계값 구성 {#configure-thresholds-for-asynchronous-delete-operations}

삭제할 자산 또는 폴더의 수가 설정된 임계값 수를 초과하는 경우 삭제 작업이 비동기적으로 수행됩니다.

1. 인터페이스에서 [!DNL Experience Manager] 도구 **[!UICONTROL > 작업]** > **[!UICONTROL 웹 콘솔]** 을 클릭합니다 ****.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Delete Operation Job Processing]** configuration.
1. [자산 **[!UICONTROL 임계값]** ] 상자에서 자산, 폴더 또는 참조를 비동기적으로 삭제할 임계값 수를 지정합니다. 변경 사항을 저장합니다.

   ![에셋을 삭제하도록 작업의 한도 설정](assets/delete_threshold.png)

## 비동기 이동 작업의 임계값 구성 {#configure-thresholds-for-asynchronous-move-operations}

이동할 자산, 폴더 또는 참조 수가 설정된 임계값 수를 초과하는 경우 이동 작업이 비동기식으로 수행됩니다.

1. 인터페이스에서 [!DNL Experience Manager] 도구 **[!UICONTROL > 작업]** > **[!UICONTROL 웹 콘솔]** 을 클릭합니다 ****.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Move Operation Job Processing]** configuration.
1. 자산/참조 **[!UICONTROL 임계값]** 상자에서 자산, 폴더 또는 참조를 비동기적으로 이동할 임계값 수를 지정합니다. 변경 사항을 저장합니다.

   ![자산을 이동할 작업의 임계값 제한 설정](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Experience Manager에서 이메일을 구성합니다](/help/sites-administering/notification.md).
>* [자산 메타데이터 일괄적으로 가져오거나 내보냅니다](/help/assets/metadata-import-export.md).

