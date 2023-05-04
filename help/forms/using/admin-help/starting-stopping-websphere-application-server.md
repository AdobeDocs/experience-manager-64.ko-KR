---
title: WebSphere Application Server 시작 및 중지
seo-title: Starting and stopping WebSphere Application Server
description: AEM Forms 제품을 배포하려는 WebSphere 인스턴스를 중지하거나 시작해야 하는 몇 가지 절차가 있습니다. 이 문서에서는 WebSphere Application Server를 시작하고 정지하는 방법을 설명합니다.
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 8e3bb77f-b187-42c8-a90e-fe0fee50dc34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 3%

---

# WebSphere Application Server 시작 및 중지 {#starting-and-stopping-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 제품을 배포하려는 WebSphere 인스턴스를 중지하거나 시작해야 하는 몇 가지 절차가 있습니다. 응용 프로그램 서버가 시작되었는지 확실하지 않은 경우 먼저 WebSphere 응용 프로그램 서버의 상태를 볼 수 있습니다.

## WebSphere 응용 프로그램 서버의 상태 보기 {#view-the-status-of-websphere-application-server}

1. 명령 프롬프트에서 *[appserver 루트]*/bin 디렉토리.
1. 다음 명령을 입력하고 *server_name* WebSphere Application Server의 이름을 사용하여 다음을 수행합니다.

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux, UNIX) 를 참조하십시오./ `serverStatus.sh`*server_name*

## WebSphere 응용 프로그램 서버 시작 {#start-websphere-application-server}

1. 명령 프롬프트에서 *[appserver 루트]*/bin 디렉토리.
1. 다음 명령을 입력하고 *server_name* WebSphere Application Server의 이름을 사용하여 다음을 수행합니다.

   * (Windows) `startServer.bat`*server_name*
   * (Linux, UNIX) 를 참조하십시오./ `startServer.sh`*server_name*

## WebSphere 응용 프로그램 서버 중지 {#stop-websphere-application-server}

1. 명령 프롬프트에서 *[appserver 루트]*/bin 디렉토리.
1. 다음 명령을 입력하고 *server_name* WebSphere Application Server의 이름을 사용하여 다음을 수행합니다.

   * (Windows) `stopServer.bat`*server_name*
   * (Linux, UNIX) 를 참조하십시오./ `stopServer.sh`*server_name*
