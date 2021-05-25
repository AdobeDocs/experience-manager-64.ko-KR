---
title: 자산과 활동 스트림 통합
description: AEM의 기록 기능과 특정 이벤트를 기록하도록 AEM을 구성하는 방법에 대해 설명합니다.
contentOwner: AG
feature: 자산 관리
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 자산과 활동 스트림 통합 {#integrating-assets-with-activity-stream}

Adobe Experience Manager (AEM) Assets 사용자는 자산 만들기, 업로드 및 삭제와 같은 많은 작업을 수행합니다. 이러한 작업을 기록할 수 있으므로 사용자가 수행한 작업 내역을 제공할 수 있습니다. 이 섹션에서는 AEM의 기록 기능과 특정 이벤트를 기록하도록 AEM을 구성하는 방법에 대해 설명합니다.

## 성능 고려 사항 및 기본 동작 {#performance-considerations-and-default-behavior}

대량 가져오기를 수행하는 경우와 같이 이 통합은 CPU 및 디스크 공간을 많이 사용하는 것일 수 있습니다. 이러한 이유로 활동 스트림과의 AEM Assets 통합이 기본적으로 비활성화되어 있습니다.

## 지원되는 작업 이벤트 {#supported-action-events}

다음 이벤트를 기록하도록 구성할 수 있습니다.

* 라이센스 수락(수락됨)
* 생성된 자산(ASSET_CREATED)
* 이동된 자산(ASSET_MOVED)
* 자산이 제거됨(ASSET_REMOVED)
* 라이센스가 거부됨(거부됨)
* 자산 다운로드(다운로드됨)
* 자산 버전이 지정됨(버전이 지정됨)
* 자산 버전이 복원됨(복원됨)
* 자산 메타데이터가 업데이트됨(METADATA_UPDATED)
* 외부 시스템에 게시된 자산(PUBLISHED_EXTERNAL)
* 자산의 원래 업데이트(ORIGINAL_UPDATED)
* 자산 표현물 업데이트(RENDITION_UPDATED)
* 자산 표현물이 제거됨(RENDITION_REMOVED)
* 하위 자산이 업데이트됨(SUBASSET_UPDATED)
* 하위 자산이 제거됨(SUBASSET_REMOVED)

## AEM Assets 이벤트 기록 구성 {#configuring-aem-assets-events-recording}

[웹 콘솔](/help/sites-deploying/configuring-osgi.md)에서는 AEM Assets 이벤트 레코더 조정에 액세스할 수 있습니다. AEM Assets 이벤트 레코더를 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL 웹 콘솔]**&#x200B;로 이동합니다.

1. **[!UICONTROL 구성]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 일 CQ DAM 이벤트 레코더]**&#x200B;를 두 번 클릭합니다.

1. **[!UICONTROL 이 서비스를 사용하도록 설정합니다]**.

1. 사용자 활동 스트림에 기록할 **[!UICONTROL 이벤트 유형]**&#x200B;을 선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## 기록된 이벤트 읽기 {#reading-recorded-events}

기록된 이벤트는 활동으로 저장됩니다. [ActivityManager API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html)를 사용하여 프로그래밍 방식으로 읽을 수 있습니다.
