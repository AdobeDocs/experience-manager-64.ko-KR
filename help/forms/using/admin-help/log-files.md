---
title: 로그 파일
seo-title: Log files
description: 런타임 또는 시작 오류와 같은 이벤트는 모든 텍스트 편집기를 사용하여 열 수 있는 애플리케이션 서버 로그 파일에 기록됩니다.
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 4%

---

# 로그 파일 {#log-files}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

런타임 또는 시작 오류와 같은 이벤트는 애플리케이션 서버 로그 파일에 기록됩니다. 응용 프로그램 서버에 배포하는 데 문제가 있으면 로그 파일을 사용하여 문제를 찾을 수 있습니다. 텍스트 편집기를 사용하여 로그 파일을 열 수 있습니다.

(JBoss) 다음 로그 파일은 `*[appserver root]*/server/*[server]*/log` 디렉토리:

* boot.log
* server.log.*[yyyy-mm-dd]*
* server.log

(WebLogic) 도메인 로그 파일은 *[appserverdomain]* 디렉토리 및 서버 로그 파일은 *[appserverdomain]/servers/[appserver 이름]/logs *디렉토리:

* access.log
* *[appserver 이름]*.log
* *[appserver 이름]*.out *[증분 번호]*

(WebSphere) 다음 로그 파일은 *[appserver 루트]*/profiles/default/logs/*[appserver 이름]* 디렉토리:

* SystemErr.log
* SystemOut.log
* StartServer.log
