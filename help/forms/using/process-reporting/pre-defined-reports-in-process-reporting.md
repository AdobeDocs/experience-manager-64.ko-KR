---
title: 프로세스 보고의 사전 정의된 보고서
seo-title: Pre-defined reports in Process Reporting
description: JEE의 AEM Forms 프로세스 데이터를 쿼리하여 장기 실행 프로세스, 프로세스 기간 및 워크플로우 볼륨에 대한 보고서를 만듭니다
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 1%

---

# 프로세스 보고의 사전 정의된 보고서 {#pre-defined-reports-in-process-reporting}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 프로세스 보고 기능은 다음과 같이 제공됩니다 *즉시 사용 가능* 보고서:

* **[장기 실행 프로세스](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: 완료하는 데 지정된 시간 이상 걸린 모든 AEM Forms 프로세스에 대한 보고서입니다.

* **[프로세스 기간 차트](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: 기간별로 지정된 AEM Forms 프로세스에 대한 보고서입니다

* **[워크플로우 볼륨](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: 날짜별 지정된 프로세스의 실행 및 완료된 인스턴스에 대한 보고서

## 장기 실행 프로세스 {#long-running-processes}

장기 실행 프로세스 보고서에는 완료하는 데 지정된 시간 이상 걸린 AEM Forms 프로세스가 표시됩니다.

### 장기 실행 프로세스 보고서를 실행하려면 {#to-execute-a-long-running-process-report-br}

1. 프로세스 보고에서 미리 정의된 보고서 목록을 보려면 **프로세스 보고** 트리 보기에서 **보고서** 노드 아래에 있어야 합니다.
1. 을(를) 클릭합니다. **장기 실행 프로세스** 보고서 노드 아래에 그룹화됩니다.

   ![long_running_node](assets/long_running_node.png)

   보고서를 선택하면 **보고서 매개 변수** 패널이 트리 보기 오른쪽에 표시됩니다.

   ![장기 실행 프로세스 보고서 매개 변수 패널](assets/report_parameters_panel.png)

   매개변수:

   * **기간**(*필수*): 지속 시간 및 시간 단위를 지정합니다. 지정된 기간 이상 실행된 모든 AEM Forms 프로세스를 표시합니다.
   * **다음 시기 이후에 시작** (*옵션*): 날짜를 선택합니다. 보고서를 필터링하여 지정된 날짜 이후에 시작된 프로세스 인스턴스를 표시합니다.
   * **시작하기 전** (*옵션*): 날짜를 선택합니다. 보고서를 필터링하여 지정된 날짜 이전에 시작된 프로세스 인스턴스를 표시합니다.

1. 클릭 **이동** 를 눌러 보고서를 실행합니다.

   보고서는 **보고서** 오른쪽 패널 **프로세스 보고** 창을 엽니다.

   ![long_running_processes](assets/long_running_processes.png)

   오른쪽 위 모서리에 있는 옵션을 사용합니다. **보고서** 패널에서 다음 작업을 수행할 수 있습니다.

   * **새로 고침**: 스토리지에 있는 최신 데이터로 보고서를 새로 고칩니다.
   * **범례 색상 변경**: 보고서 범례 색상 선택 및 변경
   * **CSV로 내보내기**: 보고서에서 데이터를 쉼표로 구분된 파일로 내보내고 다운로드합니다

## 프로세스 기간 보고서 {#process-duration-report-br}

프로세스 기간 보고서는 각 인스턴스가 실행한 일별 Forms 프로세스 인스턴스 수를 표시합니다.

### 프로세스 기간 보고서를 실행하려면 {#to-execute-a-process-duration-report-br}

1. 프로세스 보고에서 미리 정의된 보고서를 보려면 **프로세스 보고** 트리 보기에서 **보고서** 노드 아래에 있어야 합니다.
1. 을(를) 클릭합니다. **프로세스 기간** 보고서 노드 아래에 그룹화됩니다.

   ![process_duration_node](assets/process_duration_node.png)

   보고서를 선택하면 **보고서 매개 변수** 패널이 트리 보기 오른쪽에 표시됩니다.

   ![장기 실행 프로세스 보고서 매개 변수 패널](assets/process_duration_params.png)

   매개변수:

   * **프로세스 선택** (*필수*): AEM Forms 프로세스를 선택합니다.

1. 클릭 **이동** 를 눌러 보고서를 실행합니다.

   보고서는 **보고서** Process Reporting 창의 오른쪽에 있는 패널입니다.

   ![process_duration_report](assets/process_duration_report.png)

   오른쪽 위 모서리에 있는 옵션을 사용합니다. **보고서** 패널에서 다음 작업을 수행할 수 있습니다.

   * **새로 고침**: 스토리지에 있는 최신 데이터로 보고서를 새로 고칩니다.
   * **범례 색상 변경**: 보고서 범례 색상 선택 및 변경
   * **CSV로 내보내기**: 보고서에서 데이터를 쉼표로 구분된 파일로 내보내고 다운로드합니다

## 워크플로우 볼륨 보고서 {#workflow-volume-report}

워크플로우 볼륨 보고서는 일별 AEM Forms 프로세스의 현재 실행 및 완료된 인스턴스 수를 표시합니다.

### 워크플로우 볼륨 보고서를 실행하려면 {#to-execute-a-workflow-volume-report-br}

1. 프로세스 보고에서 미리 정의된 보고서를 보려면 **프로세스 보고** 트리 보기에서 **보고서** 노드 아래에 있어야 합니다.
1. 을(를) 클릭합니다. **워크플로우 볼륨** 보고서 노드 아래에 그룹화됩니다.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   보고서를 선택하면 **보고서 매개 변수** 패널이 트리 보기 오른쪽에 표시됩니다.

   ![장기 실행 프로세스 보고서 매개 변수 패널](assets/workflow_volume_params.png)

   매개변수:

   * **프로세스 선택**(*필수*): AEM Forms 프로세스를 선택합니다.
   * **다음 시기 이후에 시작** (*옵션*): 날짜를 선택합니다. 보고서를 필터링하여 지정된 날짜 이후에 시작된 프로세스 인스턴스를 표시합니다.
   * **시작하기 전** (*옵션*): 날짜를 선택합니다. 보고서를 필터링하여 지정된 날짜 이전에 시작된 프로세스 인스턴스를 표시합니다.

1. 클릭 **이동** 를 눌러 보고서를 실행합니다.

   보고서는 **보고서** 오른쪽 패널 **프로세스 보고** 창을 엽니다.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   오른쪽 위 모서리에 있는 옵션을 사용합니다. **보고서** 패널에서 다음 작업을 수행할 수 있습니다.

   * **새로 고침**: 스토리지에 있는 최신 데이터로 보고서를 새로 고칩니다.
   * **범례 색상 변경**: 보고서 범례 색상 선택 및 변경
   * **CSV로 내보내기**: 보고서에서 데이터를 쉼표로 구분된 파일로 내보내고 다운로드합니다
