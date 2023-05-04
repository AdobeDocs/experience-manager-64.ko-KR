---
title: 전자 메일 알림 구성
seo-title: Configuring Email Notification
description: AEM에서 이메일 알림을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure Email Notification in AEM.
uuid: 6cbdc312-860b-4a69-8bbe-2feb32204a27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6466d7b8-e308-43c5-acdc-dec15f796f64
exl-id: ea12035c-09b6-4197-ab23-c27fe71e7432
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 2%

---

# 전자 메일 알림 구성{#configuring-email-notification}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서 다음과 같은 사용자에게 이메일 알림을 보냅니다.

* 수정 또는 복제와 같은 페이지 이벤트에 가입했습니다. 다음 [알림 받은 편지함](/help/sites-classic-ui-authoring/author-env-inbox.md#subscribing-to-notifications) 섹션에서 해당 이벤트에 가입하는 방법을 설명합니다.

* 포럼 이벤트를 구독했습니다.
* 워크플로우에서 단계를 수행해야 합니다. 다음 [참가자 단계](/help/sites-developing/workflows-step-ref.md#participant-step) 섹션에서 워크플로우에서 이메일 알림을 트리거하는 방법을 설명합니다.

전제 조건:

* 사용자의 프로필에 유효한 이메일 주소가 정의되어 있어야 합니다.
* 다음 **일 CQ 메일 서비스** 를 올바르게 구성해야 합니다.

사용자에게 알림이 전송되면 프로필에 정의된 언어로 이메일을 받게 됩니다. 각 언어에는 사용자 지정할 수 있는 자체 템플릿이 있습니다. 새 언어에 대한 새 이메일 템플릿을 추가할 수 있습니다.

>[!NOTE]
>
>AEM을 사용하여 작업하는 경우 이러한 서비스에 대한 구성 설정을 관리하는 방법에는 몇 가지가 있습니다. 참조 [OSGi 구성](/help/sites-deploying/configuring-osgi.md) 자세한 내용 및 권장 지침

## 메일 서비스 구성 {#configuring-the-mail-service}

AEM에서 이메일을 보내려면 **일 CQ 메일 서비스** 를 올바르게 구성해야 합니다. 웹 콘솔에서 구성을 볼 수 있습니다. AEM을 사용하여 작업하는 경우 이러한 서비스에 대한 구성 설정을 관리하는 방법에는 몇 가지가 있습니다. 참조 [OSGi 구성](/help/sites-deploying/configuring-osgi.md) 자세한 내용 및 권장 지침

다음 제한 사항이 적용됩니다.

* 다음 **SMTP 서버 포트** 는 25 이상이어야 합니다.

* 다음 **SMTP 서버 호스트 이름** 비워 둘 수 없습니다.
* 다음 **&quot;보낸 사람&quot; 주소** 비워 둘 수 없습니다.

을 사용하여 문제를 디버깅하는 데 도움이 되도록 **일 CQ 메일 서비스**, 서비스 로그를 볼 수 있습니다.

`com.day.cq.mailer.DefaultMailService`

구성은 웹 콘솔에서 다음과 같습니다.

![chlimage_1-276](assets/chlimage_1-276.png)

## 이메일 알림 채널 구성 {#configuring-the-email-notification-channel}

페이지 또는 포럼 이벤트 알림에 구독하면 보낸 메일 주소가 `no-reply@acme.com` 기본적으로 사용됩니다. 이 값은 **알림 이메일 채널** 서비스를 클릭합니다.

이메일 주소를 구성하려면 `sling:OsgiConfig` 노드에 대한 섹션을 참조하십시오. CRXDE Lite을 사용하여 노드를 직접 추가하려면 다음 절차를 따르십시오.

1. CRXDE Lite에서 `config` 아래의 애플리케이션 폴더를 참조하십시오.
1. 구성 폴더에서 다음 노드를 추가합니다.

   `com.day.cq.wcm.notification.email.impl.EmailChannel` 유형 `sling:OsgiConfig`

1. 추가 `String` 이름이 지정된 노드에 대한 속성 `email.from`. 값에 사용할 이메일 주소를 지정합니다.

1. 클릭 **모두 저장**.

다음 절차를 사용하여 컨텐츠 패키지 소스 폴더에서 노드를 정의합니다.

1. 사용자 `jcr_root/apps/*app_name*/config folder`로 명명된 파일을 만듭니다. `com.day.cq.wcm.notification.email.impl.EmailChannel.xml`

1. 노드를 나타내려면 다음 XML을 추가하십시오.

   `<?xml version="1.0" encoding="UTF-8"?> <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig" email.from="name@server.com"/>`
1. 의 값 바꾸기 `email.from` 특성( `name@server.com`)에 사용할 수 있습니다.

1. 파일을 저장합니다.

## 워크플로우 이메일 알림 서비스 구성 {#configuring-the-workflow-email-notification-service}

워크플로우 이메일 알림을 받으면 보낸 사람 이메일 주소와 호스트 URL 접두사가 모두 기본값으로 설정됩니다. 이러한 값은 **Day CQ Workflow Email Notification Service** 참조하십시오. 이 경우 리포지토리에서 변경 사항을 유지하는 것이 좋습니다.

기본 구성은 웹 콘솔에서 다음과 같습니다.

![chlimage_1-277](assets/chlimage_1-277.png)

### 페이지 알림용 이메일 템플릿 {#email-templates-for-page-notification}

페이지 알림용 이메일 템플릿은 아래에 있습니다.

`/libs/settings/notification-templates/com.day.cq.wcm.core.page`

기본 영어 템플릿( `en.txt`)은 다음과 같이 정의됩니다.

```xml
subject=[CQ Page Event Notification]: Page Event

header=-------------------------------------------------------------------------------------\n \
Time: ${time}\n \
User: ${userFullName} (${userId})\n \
-------------------------------------------------------------------------------------\n\n

message=The following pages were affected by the event: \n \
 \n \
${modifications} \n \
 \n\n
footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### 페이지 알림에 대한 이메일 템플릿 사용자 정의 {#customizing-email-templates-for-page-notification}

페이지 알림에 대한 영어 이메일 템플릿을 사용자 지정하는 방법은 다음과 같습니다.

1. CRXDE에서 파일을 엽니다.

   `/libs/settings/notification-templates/com.day.cq.wcm.core.page/en.txt`

1. 필요에 따라 파일을 수정합니다.
1. 변경 사항을 저장합니다.

템플릿에는 다음 형식이 있어야 합니다.

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

위치 &lt;text_x> 정적 텍스트와 동적 문자열 변수를 혼합하여 사용할 수 있습니다. 페이지 알림의 이메일 템플릿 내에서 다음 변수를 사용할 수 있습니다.

* `${time}`, 이벤트 날짜 및 시간을 지정합니다.

* `${userFullName}`: 이벤트를 트리거한 사용자의 전체 이름입니다.

* `${userId}`: 이벤트를 트리거한 사용자의 ID입니다.
* `${modifications}`에서는 페이지 이벤트 유형 및 페이지 경로를 형식으로 설명합니다.

   &lt;page event=&quot;&quot; type=&quot;&quot;> => &lt;page path=&quot;&quot;>

   예:

   PageModified => /content/geometrixx/en/products

### 포럼 알림용 이메일 템플릿 {#email-templates-for-forum-notification}

포럼 알림용 이메일 템플릿은 다음 위치에 있습니다.

`/etc/notification/email/default/com.day.cq.collab.forum`

기본 영어 템플릿( `en.txt`)은 다음과 같이 정의됩니다.

```xml
subject=[CQ Forum Notification]

header=-------------------------------------------------------------------------------------\n \
Time: Time: ${time}\n \
Forum Page Path: ${forum.path}\n \
-------------------------------------------------------------------------------------\n\n

message=Page: ${host.prefix}${forum.path}.html\n

footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### 포럼 알림용 이메일 템플릿 사용자 정의 {#customizing-email-templates-for-forum-notification}

포럼 알림에 대한 영어 이메일 템플릿을 사용자 지정하려면 다음을 수행하십시오.

1. CRXDE에서 파일을 엽니다.

   `/etc/notification/email/default/com.day.cq.collab.forum/en.txt`

1. 필요에 따라 파일을 수정합니다.
1. 변경 사항을 저장합니다.

템플릿에는 다음 형식이 있어야 합니다.

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

위치 `<text_x>` 정적 텍스트와 동적 문자열 변수를 혼합하여 사용할 수 있습니다.

포럼 알림에 대해 이메일 템플릿 내에서 다음 변수를 사용할 수 있습니다.

* `${time}`, 이벤트 날짜 및 시간을 지정합니다.

* `${forum.path}`를 채울 수 있습니다.

### 워크플로우 알림용 이메일 템플릿 {#email-templates-for-workflow-notification}

워크플로우 알림에 대한 이메일 템플릿(영어)은 다음 위치에 있습니다.

`/libs/settings/workflow/notification/email/default/en.txt`

다음과 같이 정의됩니다.

```xml
subject=Workflow notification: ${event.EventType}

header=-------------------------------------------------------------------------------------\n \
Time: ${event.TimeStamp}\n \
Step: ${item.node.title}\n \
User: ${participant.name} (${participant.id})\n \
Workflow: ${model.title}\n \
-------------------------------------------------------------------------------------\n\n

message=Content: ${host.prefix}${payload.path.open}\n

footer=\n \
-------------------------------------------------------------------------------------\n \
View the overview in your ${host.prefix}/aem/inbox\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### 워크플로우 알림에 대한 이메일 템플릿 사용자 정의 {#customizing-email-templates-for-workflow-notification}

워크플로우 이벤트 알림에 대한 영어 이메일 템플릿을 사용자 정의하려면

1. CRXDE에서 파일을 엽니다.

   `/libs/settings/workflow/notification/email/default/en.txt`

1. 필요에 따라 파일을 수정합니다.
1. 변경 사항을 저장합니다.

템플릿에는 다음 형식이 있어야 합니다.

```
subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

>[!NOTE]
>
>위치 `<text_x>` 정적 텍스트와 동적 문자열 변수를 혼합하여 사용할 수 있습니다. 각 행 `<text_x>` 항목은 백슬래시로 끝나야 합니다. `\`). 마지막 인스턴스를 제외하고, 백슬래시가 없으면 `<text_x>` 문자열 변수를 채우는 방법을 설명합니다.
>
>템플릿 형식에 대한 자세한 내용은 [Properties.load()의 javadocs](https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.InputStream-) 메서드를 사용합니다.

메서드 `${payload.path.open}` 작업 항목의 페이로드에 대한 경로를 표시합니다. 예를 들어 Sites의 페이지에 대해 다음 작업을 수행합니다 `payload.path.open` 과 비슷합니다 `/bin/wcmcommand?cmd=open&path=…`.; 서버 이름이 없으므로 템플릿 접두사가 `${host.prefix}`.

이메일 템플릿 내에서 다음 변수를 사용할 수 있습니다.

* `${event.EventType}`, 이벤트 유형
* `${event.TimeStamp}`, 이벤트 날짜 및 시간
* `${event.User}`, 이벤트를 트리거한 사용자
* `${initiator.home}`, 개시자 노드 경로

* `${initiator.name}`, 이니시에이터 이름

* `${initiator.email}`, 개시자의 이메일 주소
* `${item.id}`, 작업 항목의 id
* `${item.node.id}`, 이 작업 항목과 연결된 워크플로우 모델의 노드 id
* `${item.node.title}`, 작업 항목의 제목
* `${participant.email}`, 참가자의 이메일 주소
* `${participant.name}`, 참여자의 이름
* `${participant.familyName}`, 참여자의 가족명
* `${participant.id}`, 참여자의 id
* `${participant.language}`, 참가자 언어
* `${instance.id}`, 워크플로우 id
* `${instance.state}`, 워크플로우 상태
* `${model.title}`, 워크플로우 모델의 제목
* `${model.id}`, 워크플로우 모델의 id

* `${model.version}`, 워크플로우 모델의 버전
* `${payload.data}`, 페이로드

* `${payload.type}`, 페이로드 유형
* `${payload.path}`, 페이로드 경로
* `${host.prefix}`, 호스트 접두사, 예: http://localhost:4502

### 새 언어용 이메일 템플릿 추가 {#adding-an-email-template-for-a-new-language}

새 언어의 템플릿을 추가하려면 다음을 수행합니다.

1. CRXDE에서 파일을 추가합니다 `<language-code>.txt` 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래 아래

   * `/libs/settings/notification-templates/com.day.cq.wcm.core.page` : 페이지 알림용
   * `/etc/notification/email/default/com.day.cq.collab.forum` : 포럼 알림용
   * `/libs/settings/workflow/notification/email/default` : 워크플로우 알림용

1. 언어에 맞게 파일을 조정합니다.
1. 변경 사항을 저장합니다.

>[!NOTE]
>
>다음 `<language-code>` 전자 메일 템플릿의 파일 이름으로 사용되는 경우 AEM에서 인식하는 두 글자 하위 언어 코드가 있어야 합니다. 언어 코드의 경우 AEM은 ISO-639-1을 사용합니다.

## AEM Assets 이메일 알림 구성 {#assetsconfig}

AEM Assets의 컬렉션이 공유되거나 공유되지 않으면 사용자는 AEM에서 이메일 알림을 받을 수 있습니다. 이메일 알림을 구성하려면 다음 단계를 수행합니다.

1. 위에 설명된 대로 이메일 서비스를 구성합니다. [메일 서비스 구성](/help/sites-administering/notification.md#configuring-the-mail-service).
1. 관리자로 AEM에 로그인합니다. 클릭 **도구** >  **작업** >  **웹 콘솔** 웹 콘솔 구성을 엽니다.
1. 편집 **일 CQ DAM 리소스 수집 서블릿**. 선택 **전자 메일 보내기**. **저장**&#x200B;을 클릭합니다.
