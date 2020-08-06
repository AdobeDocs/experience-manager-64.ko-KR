---
title: 메시징 구성
seo-title: 메시징 구성
description: 커뮤니티 메시지
seo-description: 커뮤니티 메시지
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 9fa89ca34843d41a5ab5711c1090fcc7a1077760
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 1%

---


# 메시징 구성 {#configuring-messaging}

## 개요 {#overview}

AEM Communities의 메시징 기능은 로그인 사이트 방문자(구성원)가 사이트에 로그인할 때 액세스할 수 있는 다른 사람에게 메시지를 보내는 기능을 제공합니다.

커뮤니티 사이트를 만드는 동안 상자를 선택하면 커뮤니티 사이트에 대한 [메시징이 활성화됩니다](sites-console.md).

이 페이지에서는 기본 구성 및 가능한 조정에 대한 정보를 제공합니다.

개발자를 위한 자세한 내용은 [메시지 요점을 참조하십시오](essentials-messaging.md).

## 메시징 작업 서비스 {#messaging-operations-service}

The [AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) is identify the endpoint that handles messaging related requests, the service should use for storing messages, and if 메시지에 첨부 파일이 포함되어 있을 수 있는 경우 허용되는 파일 형식을 식별합니다.

커뮤니티 사이트 콘솔을 사용하여 만든 [커뮤니티 사이트의 경우](sites-console.md), 받은 편지함이 설정된 서비스 인스턴스가 이미 있습니다 `/mail/community/inbox`.

### 커뮤니티 메시징 작업 서비스 {#community-messaging-operations-service}

아래와 같이 [사이트 만들기 마법사로 만든 사이트에 대한 서비스 구성이 있습니다](sites-console.md). 구성 옆에 있는 연필 아이콘을 선택하여 구성을 보거나 편집할 수 있습니다.

![chlimage_1-63](assets/chlimage_1-63.png)

### 새 구성 {#new-configuration}

새 구성을 추가하려면 서비스 이름 옆에 있는 더하기&#x200B;**&#39;**+s&#39; 아이콘을 선택합니다.

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 메시지 허용 목록에 추가하다 필드]**&#x200B;메시지 작성 구성 요소를 사용자가 편집하고 유지할 수 있는 속성을 지정합니다. 새로운 양식 요소가 추가된 경우 SRP에 저장하려면 요소 ID를 추가해야 합니다. 기본값은 두 개의 항목입니다. 
*제목* 및 *컨텐츠*.

* **[!UICONTROL 메시지 상자 크기 제한]**&#x200B;각 사용자의 메시지 상자에 있는 최대 바이트 수입니다. 기본값은 
*1073741824* (1GB).

* **[!UICONTROL 메시지 수 제한]**&#x200B;사용자당 허용되는 총 메시지 수입니다. 값이 -1이면 메시지 상자 크기 제한에 따라 허용되는 메시지 수가 무제한임을 나타냅니다. 기본값은 
*10000* (10k).

* **[!UICONTROL 배달 오류]**&#x200B;알림 이 확인란을 선택하면 일부 받는 사람에게 메시지 배달이 실패할 경우 보낸 사람에게 알립니다. 기본값은 
*선택함*.

* **[!UICONTROL 배달 실패 보낸 사람 id]**&#x200B;배달 실패 메시지에 표시되는 보낸 사람의 이름입니다. 기본값은 
*failureNotifier*.

* **[!UICONTROL 실패 메시지 템플릿 경로]**&#x200B;배달 실패 메시지 템플릿 루트 절대 경로입니다. 기본값은 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**&#x200B;배달되지 못한 메시지를 다시 보내는 데 필요한 횟수입니다. 기본값은 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**&#x200B;메시지 전송 실패 시 메시지를 다시 보내는 시도 간 대기할 시간(초)입니다. 기본값은 *100 *(초)입니다.

* **[!UICONTROL 카운트 업데이트 풀 크기]**&#x200B;카운트 업데이트에 사용되는 동시 스레드 수입니다. 기본값은 
*10*.

* **[!UICONTROL inbox.path.name]**(
*필수*)*폴더에 사용할 경로(사용자의 노드(/home/users/* username **`inbox`** )입니다. 경로는 후행 슬래시 &#39;/&#39;로 끝나야 합니다. 기본값은 */mail/inbox입니다* .

* **[!UICONTROL sentiems.path.name]**(
*필수*)*폴더에 사용할 경로(사용자의 노드(/home/users/* username **`senditems`** )입니다. 경로는 후행 슬래시 &#39;/&#39;로 끝나야 합니다. 기본값은 */mail/sentims입니다* .

* **[!UICONTROL supportAttachments.name]**&#x200B;이 확인란을 선택하면 사용자가 메시지에 첨부 파일을 추가할 수 있습니다. 기본값은 
*선택함*.

* **[!UICONTROL batchSize.name]**&#x200B;여러 받는 사람에게 보낼 때 함께 일괄 처리할 메시지 수입니다. 기본값은 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]** supportAttachments가 선택된 경우 이 값은 모든 첨부 파일의 허용되는 최대 총 크기(바이트)를 지정합니다. 기본값은 
*104857600* (100MB).

* **[!UICONTROL attachmentTypeBlocklist.name]**&#x200B;파일 확장자차단 목록에 추가하다의(&#39;
**.**&#39;, 시스템에 의해 거부됩니다. 그렇지 차단 목록에 추가된 않으면 확장이 허용됩니다. &#39;**+**&#39; 및 &#39;**-**&#39; 아이콘을 사용하여 익스텐션을 추가하거나 제거할 수있습니다. 기본값은 *DEFAULT입니다*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*작업 필요*** )파일 확장자의 허용 목록에 추가하다차단 목록에 추가하다입니다. 파일 확장자를 제외한 모든 파일 확장자를 허용하려면 &#39;**-**&#39; 아이콘을 사용하여 빈 항목 하나를 제거합니다.

* **[!UICONTROL serviceSelector.name]**(*필수*) 서비스가 호출되는 절대 경로(끝점)입니다(가상 리소스). 선택한 경로의 루트는 OSGi 구성의 *실행 경로* 구성 설정 [ 에 포함되어야 `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)합니다(예: `/bin/`, `/apps/`및 `/services/`). 사이트의 메시징 기능에 대해 이 구성을 선택하려면 이 끝점이 해당 **`Service selector`** 의 값으로 `Message List and Compose Message components` 제공됩니다( [메시지 기능](configure-messaging.md)참조). 기본값은 */bin/messaging입니다* .

* **[!UICONTROL fieldAllowlist.name]**&#x200B;사용 
**메시지 필드 허용 목록에 추가하다**.

>[!CAUTION]
>
>편집을 위해 `Messaging Operations Service` `allowedAttachmentTypes.name` 구성을 열 때마다, 제거된 경우 빈 항목이 다시 추가되어 속성을 구성할 수 있습니다. 비어 있는 단일 항목은 파일 첨부 파일을 효과적으로 비활성화합니다.
>
>파일 확장자를 제외한 모든 파일 확장자를 허용하려면 &#39;**-**&#39; 아이콘을 사용하여 **[!UICONTROL 저장]**&#x200B;을 클릭하기 전에 비어 있는 항목 하나를 제거합니다.

## 문제 해결 {#troubleshooting}

문제를 해결하는 한 가지 방법은 로그에서 [디버깅 메시지를 활성화하는 것입니다.](../../help/sites-administering/troubleshooting.md)

로거 [및 개인 정보 서비스 작가도 참조하십시오](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

모니터링할 패키지 `com.adobe.cq.social.messaging`가 있습니다.
