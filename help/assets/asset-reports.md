---
title: 디지털 자산 사용 및 공유에 대한 보고서입니다.
description: 의 자산에 대한 보고서 [!DNL Adobe Experience Manager Assets] 디지털 자산의 사용, 활동 및 공유를 이해하는 데 도움이 됩니다.
contentOwner: AG
feature: Asset Reports,Asset Management
role: User,Admin
exl-id: 6f03ee04-d2e2-47e6-892b-50fad3043a28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 10%

---

# 에셋 보고서 {#asset-reports}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

자산 보고를 사용하여 [!DNL Adobe Experience Manager Assets] 배포. 사용 [!DNL Assets], 디지털 자산에 대한 다양한 보고서를 생성할 수 있습니다. 이 보고서는 시스템의 사용, 사용자가 자산과 상호 작용하는 방법, 다운로드 및 공유되는 자산에 대한 유용한 정보를 제공합니다.

보고서에서 정보를 사용하여 주요 성공 지표를 도출하여 [!DNL Assets] 엔터프라이즈 및 고객별

다음 [!DNL Assets] 보고 프레임워크 사용 [!DNL Sling] 주문 방식으로 보고서 요청을 비동기식으로 처리하는 작업입니다. 대형 저장소에 대해 확장 가능합니다. 비동기 보고서 처리는 보고서가 생성되는 효율과 속도를 높입니다.

보고서 관리 인터페이스는 직관적이며, 보관된 보고서에 액세스하고 보고서 실행 상태(성공, 실패 및 큐)를 볼 수 있는 세분화된 옵션과 컨트롤을 제공합니다.

보고서가 생성되면 이메일(선택 사항) 및 받은 편지함 알림을 통해 알림을 받게 됩니다. 이전에 생성한 모든 보고서가 표시되는 보고서 목록 페이지에서 보고서를 보거나, 다운로드하거나, 삭제할 수 있습니다.

## 전제 조건 {#prerequisite-for-reporting}

보고서를 생성하려면 다음을 확인하십시오.

* 활성화 [!UICONTROL 일 CQ DAM 이벤트 레코더] 서비스 대상 **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**.
* 보고할 활동 또는 이벤트를 선택합니다. 예를 들어 다운로드한 자산에 대한 보고서를 생성하려면 를 선택합니다 [!UICONTROL 자산 다운로드(다운로드됨)].

![웹 콘솔에서 자산 보고 활성화](assets/reports-config-day-cq-dam-event-recorder.png)

## 보고서 생성 {#generate-reports}

[!DNL Experience Manager Assets] 는 다음과 같은 표준 보고서를 생성합니다.

* 업로드
* 다운로드
* 만료
* 수정
* 게시
* [!DNL Brand Portal] 페이지를
* 디스크 사용량
* 파일
* 공유 링크

[!DNL Adobe Experience Manager] 관리자는 구현을 위해 이러한 보고서를 쉽게 생성하고 사용자 지정할 수 있습니다. 관리자는 다음 단계에 따라 보고서를 생성할 수 있습니다.

1. in [!DNL Experience Manager] 인터페이스, **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 보고서]**.

   ![자산 보고서를 탐색하는 도구 페이지](assets/navigation.png)

1. 설정 [!UICONTROL 자산 보고서] 페이지를 클릭한 다음 **[!UICONTROL 만들기]** 를 클릭합니다.
1. 에서 **[!UICONTROL 보고서 만들기 페이지]** 페이지에서 만들려는 보고서를 선택하고 **[!UICONTROL 다음]**.

   ![보고서 유형 선택](assets/choose_report.png)

   >[!NOTE]
   >
   >기본적으로 컨텐츠 조각 및 링크 공유는 자산에 포함됩니다 [!UICONTROL 다운로드한 보고서]. 링크 공유 보고서를 만들거나 다운로드 보고서에서 컨텐츠 조각을 제외하려면 적절한 옵션을 선택합니다.

   >[!NOTE]
   >
   >다음 [!UICONTROL 다운로드] 보고서에는 개별적으로 선택하고 빠른 작업을 사용하여 다운로드하거나 다운로드한 자산에만 대한 세부 사항이 표시됩니다. 그러나 다운로드한 폴더 내에 있는 자산의 세부 사항은 포함하지 않습니다.

1. 보고서가 저장되는 CRX 저장소에서 제목, 설명, 축소판 및 폴더 경로와 같은 보고서 세부 정보를 구성합니다. 기본적으로 폴더 경로는 다음과 같습니다 `/content/dam`. 다른 경로를 지정할 수 있습니다.

   ![보고서 세부 사항을 추가하는 페이지](assets/report_configuration.png)

   보고서의 날짜 범위를 선택합니다.

   지금 또는 미래 날짜 및 시간에 보고서를 생성하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >나중에 보고서를 예약하도록 선택하는 경우 날짜 및 시간 필드에 날짜와 시간을 지정해야 합니다. 값을 지정하지 않으면 보고서 엔진은 값을 즉시 생성할 보고서로 처리합니다.

   구성 필드는 만드는 보고서 유형에 따라 다를 수 있습니다. 예: **[!UICONTROL 디스크 사용]** 보고서는 자산에 사용되는 디스크 공간을 계산할 때 자산 표현물을 포함하는 옵션을 제공합니다. 디스크 사용 계산을 위해 하위 폴더에 자산을 포함하거나 제외하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >The **[!UICONTROL Disk Usage]** report does not include date range fields because it indicates current disk space usage only.

   ![디스크 사용량 보고서 세부 정보 페이지](assets/disk_usage_configuration.png)

   를 만들 때 **[!UICONTROL 파일]** 보고서에서 하위 폴더를 포함/제외할 수 있습니다. 그러나 이 보고서에 대한 자산 표현물은 포함할 수 없습니다.

   ![파일 보고서의 세부 정보 페이지](assets/files_report.png)

   The **[!UICONTROL Link Share]** report displays URLs to assets that are shared with external users from within [!DNL Assets]. It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. The columns are not customizable.

   다음 **[!UICONTROL 링크 공유]** 보고서에는 아래에 표시되는 공유 URL만 게시하므로 하위 폴더 및 표현물에 대한 옵션이 포함되지 않습니다 `/var/dam/share`.

   ![링크 공유 보고서의 세부 사항 페이지](assets/link_share.png)

1. 클릭 **[!UICONTROL 다음]** 를 클릭합니다.

1. 에서 **[!UICONTROL 열 구성]** 페이지, 기본적으로 보고서에 일부 열이 나타나도록 선택됩니다. 열을 더 선택할 수 있습니다. 선택한 열을 선택 취소하여 보고서에서 제외합니다.

   ![보고서 열 선택 또는 선택 취소](assets/configure_columns.png)

   사용자 지정 열 이름 또는 속성 경로를 표시하려면 `jcr:content` 노드 아래에 있어야 합니다. 또는 속성 경로 선택기를 통해 추가합니다.

   ![보고서 열 선택 또는 선택 취소](assets/custom_columns.png)

1. 클릭 **[!UICONTROL 만들기]** 를 클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.
1. 설정 [!UICONTROL 자산 보고서] 페이지, 보고서 생성 상태는 보고서 작업의 현재 상태를 기반으로 합니다(예: ) [!UICONTROL 성공], [!UICONTROL 실패], [!UICONTROL 큐에 있음], 또는 [!UICONTROL 예약됨]. 알림 받은 편지함에 동일한 상태가 표시됩니다.보고서 페이지를 보려면 보고서 링크를 클릭하십시오. 또는 보고서를 선택하고 을(를) 클릭합니다 **[!UICONTROL 보기]** 를 클릭합니다.

   ![생성된 보고서](assets/report_page.png)

   클릭 **[!UICONTROL 다운로드]** 를 클릭하여 보고서를 CSV 형식으로 다운로드합니다.

## 사용자 지정 열 추가 {#add-custom-columns}

다음 보고서에 사용자 지정 열을 추가하여 사용자 지정 요구 사항에 대한 더 많은 데이터를 표시할 수 있습니다.

* 업로드
* 다운로드
* 만료
* 수정
* 게시
* [!DNL Brand Portal] 페이지를
* 파일

이러한 보고서에 사용자 지정 열을 추가하려면 다음 단계를 수행합니다.

1. 에서 [!DNL Manager interface]를 클릭합니다. **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 보고서]**.
1. 설정 [!UICONTROL 자산 보고서] 페이지를 클릭한 다음 **[!UICONTROL 만들기]** 를 클릭합니다.

1. 에서 **[!UICONTROL 보고서 만들기]** 페이지에서 만들려는 보고서를 선택하고 **[!UICONTROL 다음]**.
1. 제목, 설명, 축소판, 폴더 경로 및 날짜 범위와 같은 보고서 세부 정보를 해당하는 대로 구성합니다.

1. To display a custom column, specify the name of the column in under **[!UICONTROL Custom Columns]**.

   ![보고서의 사용자 지정 열에 대한 이름을 지정합니다](assets/custom_columns-1.png)

1. 아래에 속성 경로를 추가합니다. `jcr:content` property path 선택기를 사용하여 CRXDE에 노드를 추가합니다. 또는 속성 경로 필드에 경로를 입력합니다.

   ![jcr:content의 경로에서 속성 경로를 매핑합니다](assets/property_picker.png)

   또는 속성 경로 필드에 경로를 입력합니다.

   ![property_path](assets/property_path.png)

   사용자 지정 열을 추가하려면 **[!UICONTROL 추가]** 5~6단계를 반복합니다.

1. 클릭 **[!UICONTROL 만들기]** 를 클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.

## 제거 서비스 구성 {#configure-purging-service}

더 이상 필요하지 않은 보고서를 제거하려면 웹 콘솔에서 DAM 보고서 삭제 서비스를 구성하여 수량 및 나이에 따라 기존 보고서를 삭제합니다.

1. 다음에서 웹 콘솔(구성 관리자)에 액세스 `https://[aem_server]:[port]/system/console/configMgr`.
1. 를 엽니다. **[!UICONTROL DAM 보고서 제거 서비스]** 구성.
1. 제거 서비스의 빈도(시간 간격)를 `scheduler.expression.name` 필드. 보고서에 대한 연령 및 수량 임계값을 구성할 수도 있습니다.
1. 변경 사항을 저장합니다.
