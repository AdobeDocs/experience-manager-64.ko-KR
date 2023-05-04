---
title: 메시징 핵심 사항
seo-title: Messaging Essentials
description: 메시징 구성 요소 개요
seo-description: Messaging component overview
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
exl-id: c6ad3c2b-8776-4ec4-99da-ab73ecc61153
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 3%

---

# 메시징 핵심 사항 {#messaging-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 페이지에서는 메시징 구성 요소를 사용하여 웹 사이트에 메시징 기능을 포함하는 작업에 대한 세부 사항을 설명합니다.

## 클라이언트측 핵심 사항 {#essentials-for-client-side}

**메시지 작성**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/composemessage</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>템플릿</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td> 
  </tr> 
  <tr> 
   <td><strong>속성</strong></td> 
   <td>참조 <a href="configure-messaging.md">메시징 구성</a></td> 
  </tr> 
  <tr> 
   <td><strong>관리 구성</strong></td> 
   <td><a href="messaging.md">메시징 구성</a></td> 
  </tr> 
 </tbody> 
</table>

**메시지 목록** (받은 편지함, 전송 및 휴지통의 경우)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>템플릿</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td><strong>속성</strong></td> 
   <td>자세한 내용은 <a href="configure-messaging.md">메시징 구성</a></td> 
  </tr> 
  <tr> 
   <td><strong>관리 구성</strong></td> 
   <td><a href="messaging.md">메시징 구성</a></td> 
  </tr> 
 </tbody> 
</table>

참조 - [클라이언트측 사용자 지정](client-customize.md)

## 서버측 핵심 사항 {#essentials-for-server-side}

* [메시징 구성](configure-messaging.md)

* [메시징 클라이언트 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) SCF 구성 요소용

* [메시징 API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) 서비스

* [메시징 끝점](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [서버측 사용자 지정](server-customize.md)

>[!CAUTION]
>
>String 매개 변수는 다음 MessageBuilder 메서드에 대해 후행 슬래시 &quot;/&quot;를 포함하지 *않아야 합니다.
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>예:
>
>
```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### 커뮤니티 사이트 {#community-site}

마법사를 사용하여 만든 커뮤니티 사이트 구조에는 선택한 경우 메시징 기능이 포함됩니다. 자세한 내용은 `User Management` 설정 [커뮤니티 사이트 콘솔](sites-console.md#user-management).

### 샘플 코드: 메시지 수신 알림 {#sample-code-message-received-notification}

예를 들어 소셜 메시징 기능에서는 작업에 대한 이벤트가 발생합니다 `send`, `marking read`, `marking delete`. 이러한 이벤트를 포착하고 이벤트에 포함된 데이터에 대한 작업을 수행할 수 있습니다.

다음 예제에서는 `message sent` 이벤트 및 는 `Day CQ Mail Service`.

서버측 샘플 스크립트를 시도하려면 개발 환경과 OSGi 번들을 빌드하는 기능이 필요합니다.

1. 관리자로 다음 위치에 로그인합니다. ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. 만들기 `bundle node`in `/apps/engage/install` 과 같은 임의 이름 사용

   * **[!UICONTROL 기호 이름]**: com.engage.media.social.messaging.MessagingNotification
   * **[!UICONTROL 이름]**: 시작하기 자습서 메시지 알림
   * **[!UICONTROL 설명]**: 사용자가 메시지를 받을 때 사용자에게 이메일 알림을 전송하는 샘플 서비스
   * **[!UICONTROL 패키지]**: `com.engage.media.social.messaging.notification`

1. 다음으로 이동 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. 삭제 `Activator.java` 클래스 자동 생성
   1. 클래스 만들기 `MessageEventHandler.java`
   1. 아래 코드를 `MessageEventHandler.java`

1. 클릭 **[!UICONTROL 모두 저장]**
1. 다음으로 이동 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` 및에 작성된 대로 모든 가져오기 구문을 추가합니다. `MessageEventHandler.java` 코드가 있어야 합니다.
1. 번들 빌드
1. 확인 `Day CQ Mail Service`OSGi 서비스가 구성되었습니다
1. 한 데모 사용자로 로그인하여 다른 데모 사용자로 이메일 보내기
1. 수신자는 새 메시지에 대한 이메일을 수신해야 합니다

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site, 
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
