---
title: 유지 관리 모드에서 AEM Forms 실행
seo-title: Running AEM forms in maintenance mode
description: 유지 관리 모드는 DSC 패치 작업, AEM 양식 업그레이드 또는 서비스 팩 적용 등의 작업을 수행할 때 유용합니다. 유지 관리 모드에서 AEM Forms를 실행하는 방법에 대해 자세히 알아보십시오.
seo-description: Maintenance mode is useful when performing tasks such as patching a DSC, upgrading AEM forms, or applying a service pack. Learn more about running AEM forms in maintenance mode.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 2%

---

# 유지 관리 모드에서 AEM Forms 실행 {#running-aem-forms-in-maintenance-mode}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

유지 관리 모드는 DSC 패치 작업, AEM 양식 업그레이드 또는 서비스 팩 적용 등의 작업을 수행할 때 유용합니다.

서버가 유지 관리 모드에 있는 동안 프로세스를 호출하지 마십시오. 서버가 유지 관리 모드에 있는 동안 프로세스가 호출되면 다음과 같이 발생합니다.

* 프로세스가 오래되면 작업 데이터베이스에 추가되지만 시작되지 않습니다. 유지 관리 모드를 종료하면 유지 관리 모드 중에 서버가 다시 시작되었더라도 AEM Forms는 큐에서 오래 지속되는 작업을 처리합니다.
* 프로세스가 단기 체류하면 즉시 처리됩니다.

**유지 관리 모드에 AEM 양식 넣기**

1. 웹 브라우저에서 다음을 입력합니다.

   `https://`*[호스트 이름&#x200B;]*`:`*[포트]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[관리자 사용자 이름&#x200B;]*`&password=`*[암호]*

   이제 일시 중지됨 메시지가 브라우저 창에 표시됩니다.

   >[!NOTE]
   >
   >유지 관리 모드 중에 서버를 종료하면 다시 시작할 때 유지 관리 모드가 계속 됩니다. 유지 관리 작업을 마치면 유지 관리 모드를 해제해야 합니다.

**AEM Forms가 유지 관리 모드에서 실행 중인지 확인합니다**

1. 웹 브라우저에서 다음을 입력합니다.

   `https://`*[호스트 이름]:[포트&#x200B;]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[관리자 사용자 이름]* `&password=`*[암호&#x200B;]*

   브라우저 창에 상태가 표시됩니다. 상태가 &quot;true&quot;이면 서버가 유지 관리 모드에서 실행 중이고 &quot;false&quot;는 서버가 유지 관리 모드가 아님을 나타냅니다.

**유지 관리 모드 해제**

1. 웹 브라우저에서 다음을 입력합니다.

   `https://`*[호스트 이름]:[포트&#x200B;]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[관리자 사용자 이름]* `&password=`*[암호&#x200B;]*

   브라우저 창에 &quot;지금 실행 중&quot; 메시지가 표시됩니다.
