---
title: 타임라인의 활동 스트림
description: 이 문서에서는 타임라인에 자산에 대한 활동 로그를 표시하는 방법에 대해 설명합니다.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 27%

---

# 타임라인의 활동 스트림 {#activity-stream-in-timeline}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 기능은 타임라인에 자산에 대한 활동 로그를 표시합니다. 에서 다음 자산 관련 작업을 수행하는 경우 [!DNL Adobe Experience Manager Assets], 활동 스트림 기능은 활동을 반영하도록 타임라인을 업데이트합니다.

다음 작업이 활동 스트림에 기록됩니다.

* 만들기
* 삭제
* 다운로드(표현물 포함)
* 게시
* 게시 취소
* 승인
* 거부
* 이동

The activity logs to be displayed in the timeline are fetched from the location `/var/audit/com.day.cq.dam/content/dam` in CRX, where log files are stored.

또한 새 자산을 업로드하거나 기존 자산을 수정하여 Experience Manager에 체크 인할 때 타임라인 활동이 기록됩니다 [Adobe 자산 링크](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) 또는 [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).

>[!NOTE]
>
>이러한 워크플로우에 대한 내역 정보가 저장되지 않으므로 임시 워크플로우는 타임라인에 표시되지 않습니다.

활동 스트림을 보려면 자산에서 하나 이상의 작업을 수행하고 자산을 선택한 다음 선택합니다 **[!UICONTROL 타임라인]** GlobalNav 목록에서 삭제할 수 있습니다.

![타임라인-3](assets/timeline-3.png)

타임라인에는 자산에서 수행하는 작업에 대한 활동 스트림이 표시됩니다.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>The default log storage location for **Publish** and **Unpublish** tasks is `/var/audit/com.day.cq.replication/content`. For **Move** tasks, the default location is `/var/audit/com.day.cq.wcm.core.page`.
