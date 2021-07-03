---
title: 타임라인의 활동 스트림
description: '이 문서에서는 타임라인에 자산에 대한 활동 로그를 표시하는 방법에 대해 설명합니다. '
contentOwner: AG
feature: 자산 관리
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 6%

---

# 타임라인의 활동 스트림 {#activity-stream-in-timeline}

이 기능은 타임라인에 자산에 대한 활동 로그를 표시합니다. Adobe Experience Manager (AEM) Assets에서 다음 자산 관련 작업을 수행하는 경우 활동 스트림 기능이 활동을 반영하도록 타임라인을 업데이트합니다.

다음 작업이 활동 스트림에 기록됩니다.

* 만들기
* 삭제
* 다운로드(표현물 포함)
* 게시
* 게시 취소
* 승인
* 거부
* 이동

타임라인에 표시할 활동 로그는 로그 파일이 저장된 CRX의 `/var/audit/com.day.cq.dam/content/dam` 위치에서 가져옵니다.

또한 타임라인 활동은 새 자산이 업로드되거나 기존 자산이 수정되어 [Adobe 자산 링크](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) 또는 [AEM 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)을 통해 AEM에 체크 인될 때 기록됩니다.

>[!NOTE]
>
>이러한 워크플로우에 대한 내역 정보가 저장되지 않으므로 임시 워크플로우는 타임라인에 표시되지 않습니다.

활동 스트림을 보려면 자산에서 하나 이상의 작업을 수행하고 자산을 선택한 다음 GlobalNav 목록에서 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다.

![타임라인-3](assets/timeline-3.png)

타임라인에는 자산에서 수행하는 작업에 대한 활동 스트림이 표시됩니다.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>**게시** 및 **게시 취소** 작업의 기본 로그 저장소 위치는 `/var/audit/com.day.cq.replication/content`입니다. **Move** 작업의 경우 기본 위치는 `/var/audit/com.day.cq.wcm.core.page`입니다.
