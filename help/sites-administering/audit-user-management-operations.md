---
title: AEM에서 사용자 관리 작업을 감사하는 방법
seo-title: AEM에서 사용자 관리 작업을 감사하는 방법
description: AEM에서 사용자 관리 작업을 감사하는 방법을 알아봅니다.
feature: 작업
seo-description: AEM에서 사용자 관리 작업을 감사하는 방법을 알아봅니다.
uuid: 4ea704b4-9150-4b5f-b9cb-cdac95cfd70c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 437fa139-2dde-41a0-9649-6bb110039618
exl-id: f987c4f5-64dd-491b-aafe-cb98acf0b1eb
source-git-commit: 40a4e01eea3e20fda6d0b2c8af985f905039e320
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# AEM{#how-to-audit-user-management-operations-in-aem}에서 사용자 관리 작업을 감사하는 방법

## 소개 {#introduction}

AEM에서는 권한 변경 사항을 로그하여 나중에 감사할 수 있도록 하는 기능을 도입했습니다.

개선 사항으로 사용자 권한 및 그룹 지정에 대한 CRUD(만들기, 읽기, 업데이트, 삭제) 작업을 감사할 수 있습니다. 구체적으로 설명하면 다음과 같이 기록됩니다.

* 새 사용자 만들기
* 그룹에 추가되는 사용자
* 기존 사용자 또는 그룹의 권한 변경

기본적으로 항목이 `error.log` 파일에 기록됩니다. 모니터링을 쉽게 하려면 별도의 로그 파일로 리디렉션하는 것이 좋습니다. 아래 단락에서 이 작업을 수행하는 방법에 대한 자세한 정보를 제공합니다.

## 출력을 별도의 로그 파일 {#redirecting-the-output-to-a-separate-log-file}로 리디렉션합니다.

로깅 출력을 별도의 로그 파일로 리디렉션하려면 새 **Apache Sling Logging Logger** 구성을 만들어야 합니다. 아래 예에서 별도의 파일 이름으로 `useraudit.log`을 사용합니다.

1. `https://<serveraddress>:<serverport>/system/console/configMgr`(으)로 이동하여 웹 콘솔로 이동합니다.
1. **Apache Sling Logging Configuration**&#x200B;을 검색합니다. 그런 다음 항목 오른쪽의 &quot;+&quot;를 눌러 새 공장 구성을 만듭니다.
1. 다음 구성을 만듭니다.

   * **로그 수준:** 정보
   * **로그 파일:** logs/useraudit.log
   * **메시지 패턴:** 수준 기본값
   * **로거:** com.adobe.granite.security.user.internal.audit, com.adobe.granite.security.user.internal.servlets.AuthorizableServlet

   **로거** 필드에 두 로거를 모두 입력하려면 첫 번째 이름을 입력한 다음 &quot;+&quot; 버튼을 누르고 두 번째 로거의 이름을 입력하여 다른 필드를 만들어야 합니다.

## 출력 예 {#example-output}

올바르게 구성된 경우 출력은 다음과 같습니다.

```xml
19.05.2017 15:15:08.933 *INFO* [0:0:0:0:0:0:0:1 [1495196108932] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:15:08.934 *INFO* [0:0:0:0:0:0:0:1 [1495196108932] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Group 'group1' was created

19.05.2017 15:16:25.698 *INFO* [0:0:0:0:0:0:0:1 [1495196185696] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create User 'user1' operation initiated by User 'admin' (administrator)
19.05.2017 15:16:25.700 *INFO* [0:0:0:0:0:0:0:1 [1495196185696] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user1' was created

19.05.2017 15:16:25.728 *INFO* [0:0:0:0:0:0:0:1 [1495196185726] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:16:25.729 *INFO* [0:0:0:0:0:0:0:1 [1495196185726] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditGroupAction User 'user1' was added to the group 'group1'

19.05.2017 15:17:29.830 *INFO* [0:0:0:0:0:0:0:1 [1495196249828] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Password Change for User 'user2' operation initiated by User 'admin' (administrator)
19.05.2017 15:17:29.832 *INFO* [0:0:0:0:0:0:0:1 [1495196249828] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Password for User 'user2' was changed

19.05.2017 15:17:54.906 *INFO* [0:0:0:0:0:0:0:1 [1495196274904] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Delete User 'user2' operation initiated by User 'admin' (administrator)
19.05.2017 15:17:54.906 *INFO* [0:0:0:0:0:0:0:1 [1495196274904] POST /home/users/5/5dI6iK4HkZmrfTjcLBoI.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user2' was removed

19.05.2017 15:19:11.050 *INFO* [0:0:0:0:0:0:0:1 [1495196351049] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Create User 'user3' operation initiated by User 'admin' (administrator)
19.05.2017 15:19:11.052 *INFO* [0:0:0:0:0:0:0:1 [1495196351049] POST /libs/granite/security/post/authorizables.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'user3' was created
19.05.2017 15:19:36.899 *INFO* [0:0:0:0:0:0:0:1 [1495196376898] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)

19.05.2017 15:19:36.916 *INFO* [0:0:0:0:0:0:0:1 [1495196376915] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Edit Membership for Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:19:36.917 *INFO* [0:0:0:0:0:0:0:1 [1495196376915] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditGroupAction User 'user1' was removed from the group 'group1'

19.05.2017 15:21:34.419 *INFO* [0:0:0:0:0:0:0:1 [1495196494417] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Delete Group 'group1' operation initiated by User 'admin' (administrator)
19.05.2017 15:21:34.419 *INFO* [0:0:0:0:0:0:0:1 [1495196494417] POST /home/groups/d/dGf7f7vGrZRLs6HS3AK-.rw.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Group 'group1' was removed

19.05.2017 15:44:10.404 *INFO* [0:0:0:0:0:0:0:1 [1495197850401] POST /home/users/3/35XVpVtLRx4a5J9gKrVG.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.servlets.AuthorizableServlet Password Change for User 'john' operation initiated by User 'john' (not administrator)
19.05.2017 15:44:10.405 *INFO* [0:0:0:0:0:0:0:1 [1495197850401] POST /home/users/3/35XVpVtLRx4a5J9gKrVG.rw.userprops.html HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction Password for User 'john' was changed
```

## 클래식 UI

클래식 UI에서 사용자 추가 및 삭제와 관련된 감사 로그에 기록된 CRUD 작업에 대한 정보는 영향을 받는 사용자의 ID와 변경된 사항이 발생한 시기로 제한됩니다.

예:

```
10.05.2019 18:01:09.123 INFO [0:0:0:0:0:0:0:1 [1557491469096] POST /libs/cq/security/authorizables/POST HTTP/1.1] com.adobe.granite.security.user.internal.audit.AuditAuthorizableAction User 'test' was created
```
