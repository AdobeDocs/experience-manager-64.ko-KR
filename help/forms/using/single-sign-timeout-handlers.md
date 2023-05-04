---
title: 단일 사인온 및 시간 초과 핸들러
seo-title: Single Sign On and timeout handlers
description: AEM Forms 작업 공간에 대한 세션 시간 초과 값을 설정하는 방법.
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: eb7afdd3-0901-4dfb-b23c-88c46b5a4fb5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 3%

---

# 단일 사인온 및 시간 초과 핸들러 {#single-sign-on-and-timeout-handlers}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 작업 공간이 SSO를 사용하도록 설정되어 있습니다. 사용자가 Forms Manager 또는 PDF 생성기 사용자 인터페이스와 같은 AEM Forms 애플리케이션에 로그인하여 동일한 브라우저 세션에서 AEM Forms 작업 공간에 액세스한 경우, 사용자는 AEM Forms 작업 공간에 로그인하거나 그 반대의 경우도 있습니다.

## AEM Forms 작업 공간의 서버 시간 제한 처리 {#handling-server-timeout-in-nbsp-aem-forms-workspace}

사용자에 대한 세션 시간 초과는 관리 콘솔에서 구성할 수 있습니다.

시간 제한을 설정하려면 다음을 로그인하여 `https://[server]:[port]/adminui`, 다음 위치로 이동합니다. **설정 > 사용자 관리 > 구성 > 고급 시스템 속성 구성**&#x200B;를 누르고 원하는 설정을 만듭니다.

AEM Forms 작업 공간 시간 제한은 다음과 같이 처리됩니다.

* 사용자의 세션 기간은 `initialize` 사용자 세션을 초기화하는 호출.
* 팝업 대화 상자는 세션 만료 15초 전에 세션이 만료된다는 것을 사용자에게 알립니다.

이 팝업 대화 상자에서 다음을 수행합니다.

* 확인 을 클릭하여 사용자 세션을 종료합니다.
* 사용자 세션을 다시 초기화하려면 취소 를 클릭합니다.

>[!NOTE]
>
>작업을 수행하지 않으면 세션 만료 3초 전에 사용자가 AEM Forms 작업 공간에서 자동으로 로그아웃됩니다.
