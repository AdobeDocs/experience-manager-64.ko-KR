---
title: 앱 동기화
seo-title: Synchronizing the app
description: 모바일 장치의 AEM Forms 앱을 AEM Forms 서버와 동기화합니다.
seo-description: Synchronize the AEM Forms app on your mobile device with the AEM Forms server.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
exl-id: b5681fe5-69ba-4fc0-95e3-6ffdcdd95382
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# 앱 동기화 {#synchronizing-the-app}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 앱 동기화 {#synchronizing-the-app-1}

앱의 양식은 AEM Forms 서버에서 다운로드됩니다. 양식은 작업 및 Forms 탭에서 다운로드됩니다. 양식에서 만든 초안은 초안 탭에서 다운로드되고 작업에서 생성된 초안은 작업 탭에서 다운로드됩니다. OSGi 서버의 독립형 양식의 경우 양식에서 및 초안이 각각 Forms 및 초안 탭에서 다운로드됩니다.

양식을 작성하여 제출하면 앱이 온라인 상태일 때 양식이 AEM Forms 서버에 즉시 다시 업로드됩니다. 앱이 동기화되면 서버에서 양식을 가져옵니다. 그러나 임시 항목은 앱이 온라인 상태인 경우 서버와 즉시 동기화됩니다.

AEM Forms 서버를 사용하여 온라인 상태이면 기본적으로 앱은 15분마다 동기화됩니다. 그러나 동기화 빈도를 변경할 수 있는 옵션이 있습니다. 또는 언제든지 앱을 수동으로 동기화할 수 있습니다.

**앱을 수동으로 동기화하려면**

동기화 단추를 누릅니다 ![sync-app](assets/sync-app.png) 홈 화면의 오른쪽 아래 모서리에 있습니다.

**동기화 빈도를 변경하려면**

1. 설정 화면으로 이동하려면 홈 화면의 왼쪽 위 모서리에 있는 메뉴 단추를 탭한 다음 탭합니다 **설정**.
1. 설정 화면에서 일반 탭을 탭합니다.

   ![일반 설정 창의 동기화 빈도 설정](assets/gen-settings-1.png)

1. 동기화 빈도 옵션에서 동기화 빈도 오른쪽에 있는 값을 누릅니다.
1. 드롭다운 목록에서 새 동기화 빈도를 선택합니다.

### 기술 사양 {#technical-specifications}

* AEM Forms 서버에 오프라인 앱 데이터를 제출하는 기본 논리는 runtime/offline/util/offline.js에 포함되어 있습니다.
* .js에서 processOfflineSubmittedSavedTasks(...) 함수를 호출하면 저장된 / 제출된 작업이 서버에 전송됩니다. 또한 동기화 프로세스에서 오류나 충돌을 처리합니다. 작업 제출이 실패하면 앱의 작업이 실패로 표시됩니다. 또한 작업은 보낼 편지함에 남아 있습니다.
* syncSubmittedTask() 및 syncSavedTask() 함수는 개별 작업에 대해 작업을 수행합니다.
* 사용자가 오프라인 상태를 서버에 동기화하거나 백그라운드 스레드에 의한 자동 동기화를 선택하면 작업 목록 구성 요소에서 processOfflineSubmittedSavedTasks() 함수 호출이 시작됩니다.
