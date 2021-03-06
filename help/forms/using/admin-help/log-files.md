---
title: 로그 파일
seo-title: 로그 파일
description: 런타임 또는 시작 오류와 같은 이벤트는 모든 텍스트 편집기를 사용하여 열 수 있는 애플리케이션 서버 로그 파일에 기록됩니다.
seo-description: 런타임 또는 시작 오류와 같은 이벤트는 모든 텍스트 편집기를 사용하여 열 수 있는 애플리케이션 서버 로그 파일에 기록됩니다.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 로그 파일 {#log-files}

런타임 또는 시작 오류와 같은 이벤트는 애플리케이션 서버 로그 파일에 기록됩니다. 응용 프로그램 서버에 배포하는 데 문제가 있으면 로그 파일을 사용하여 문제를 찾을 수 있습니다. 텍스트 편집기를 사용하여 로그 파일을 열 수 있습니다.

(JBoss) 다음 로그 파일은 `*[appserver root]*/server/*[server]*/log` 디렉토리에 있습니다.

* boot.log
* server.log.*[yyyy-mm-dd]*
* server.log

(WebLogic) 도메인 로그 파일은 *[appserverdomain]* 디렉터리에 있고 서버 로그 파일은 *[appserverdomain]/servers/[appserver name]/logs *디렉터리에 있습니다.

* access.log
* *[appserver name]*.log
* *[appserver 이름]*.out.*[증분 번호]*

(WebSphere) 다음 로그 파일은 *[appserver root]*/profiles/default/logs/*[appserver name]* 디렉토리에 있습니다.

* SystemErr.log
* SystemOut.log
* StartServer.log
