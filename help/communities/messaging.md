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
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---


# 메시징 구성 {#configuring-messaging}

## 개요 {#overview}

AEM Communities에 대한 메시징 기능은 로그인 사이트 방문자(구성원)가 사이트에 로그인할 때 액세스할 수 있는 서로 메시지를 보내는 기능을 제공합니다.

커뮤니티 사이트를 만드는 동안 상자를 선택하면 커뮤니티 사이트에 대한 [메시징이 활성화됩니다](sites-console.md).

이 페이지에서는 기본 구성 및 가능한 조정에 대한 정보를 제공합니다.

개발자를 위한 자세한 내용은 [메시지 요점을 참조하십시오](essentials-messaging.md).

## 메시징 작업 서비스 {#messaging-operations-service}

AEM Communities 메시징 작업 서비스는 메시징 관련 요청을 처리하는 종단점, 서비스가 메시지를 저장하는 데 사용해야 하는 폴더, 메시지에 첨부 파일이 포함되어 있을 수 있는 경우 허용되는 파일 유형을 식별합니다 [](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) .

커뮤니티 사이트 콘솔을 사용하여 만든 [커뮤니티 사이트의 경우](sites-console.md), 받은 편지함이 설정된 서비스 인스턴스가 이미 있습니다 `/mail/community/inbox`.

### 커뮤니티 메시징 작업 서비스 {#community-messaging-operations-service}

아래와 같이 [사이트 만들기 마법사로 만든 사이트에 대한 서비스 구성이 있습니다](sites-console.md). 구성 옆에 있는 연필 아이콘을 선택하여 구성을 보거나 편집할 수 있습니다.

![chlimage_1-63](assets/chlimage_1-63.png)

### 새 구성 {#new-configuration}

새 구성을 추가하려면 서비스 이름 옆에 있는 더하기&#x200B;**&#39;**+s&#39; 아이콘을 선택합니다.

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 메시지 필드 허용 목록]**&#x200B;메시지 작성 구성 요소를 사용자가 편집하고 유지할 수 있는 속성을 지정합니다. 새로운 양식 요소가 추가된 경우 SRP에 저장하려면 요소 ID를 추가해야 합니다. 기본값은 두 개의 항목입니다. *제목* 및 *컨텐츠*.
**[!UICONTROL 메시지 상자 크기 제한]**&#x200B;각 사용자의 메시지 상자에 있는 최대 바이트 수입니다. 기본값은 *1073741824* (1GB)입니다.**

* **[!UICONTROL 메시지 수 제한]**&#x200B;사용자당 허용되는 총 메시지 수입니다. 값이 -1이면 메시지 상자 크기 제한에 따라 허용되는 메시지 수가 무제한임을 나타냅니다. 기본값은 *10000* (10k)입니다.
**[!UICONTROL 배달 오류]**&#x200B;알림 이 확인란을 선택하면 일부 받는 사람에게 메시지 배달이 실패할 경우 보낸 사람에게 알립니다. 기본값은 *선택되었습니다*.*

* **[!UICONTROL 배달 실패 보낸 사람 id]**&#x200B;배달 실패 메시지에 표시되는 보낸 사람의 이름입니다. 기본값은 *failureNotifier입니다*.
**[!UICONTROL 실패 메시지 템플릿 경로]**&#x200B;배달 실패 메시지 템플릿 루트 절대 경로입니다. 기본값은 */etc/notification/messaging/default입니다*.*

* **[!UICONTROL maxRetries.name]**&#x200B;배달되지 못한 메시지를 다시 보내는 데 필요한 횟수입니다. 기본값은 *3입니다*.
**[!UICONTROL minWaitBetweenRetries.name]**&#x200B;메시지 전송 실패 시 메시지를 다시 보내는 시도 간 대기할 시간(초)입니다. 기본값은 *100 *(초)입니다.*

* **[!UICONTROL 카운트 업데이트 풀 크기]**&#x200B;카운트 업데이트에 사용되는 동시 스레드 수입니다. 기본값은 *10입니다*.
**[!UICONTROL inbox.path.name]**(*필수*) 사용자 노드(/home/users/*username*)를 기준으로 **`inbox`** 폴더에 사용할 경로입니다. 경로는 후행 슬래시 &#39;/&#39;로 끝나야 합니다. 기본값은 */mail/inbox입니다* .*

* **[!UICONTROL sentiems.path.name]**(*필수*) 사용자 노드(/home/users/*username*)에 상대적인 **`senditems`** 경로 경로는 후행 슬래시 &#39;/&#39;로 끝나야 합니다. 기본값은 */mail/sentims입니다* .
**[!UICONTROL supportAttachments.name]**&#x200B;이 확인란을 선택하면 사용자가 메시지에 첨부 파일을 추가할 수 있습니다. 기본값은 *선택되었습니다*.*

* **[!UICONTROL batchSize.name]**&#x200B;여러 받는 사람에게 보낼 때 함께 일괄 처리할 메시지 수입니다. 기본값은 *100입니다*.
**[!UICONTROL maxTotalAttachmentSize.name]** supportAttachments가 선택된 경우 이 값은 모든 첨부 파일의 허용되는 최대 총 크기(바이트)를 지정합니다. 기본값은 *104857600* (100MB)입니다.*

* **[!UICONTROL attachmentTypeAllowlist.name]**&#x200B;파일 확장자의 블록 목록으로, &#39;와(과) 함께 접두사가 추가되었습니다&#x200B;**.**&#39;, 시스템에 의해 거부됩니다. 차단되지 않으면 확장이 허용됩니다. &#39;**+**&#39; 및 &#39;**-**&#39; 아이콘을 사용하여 익스텐션을 추가하거나 제거할 수있습니다. 기본값은 *DEFAULT입니다*.

* **[!UICONTROL allowedAttachmentTypes.name]**

**(*작업 필요*)** 블록 목록의 반대쪽에 있는 파일 확장자의 허용 목록입니다. 나열된 파일 확장자를 제외한 모든 파일 확장자를 허용하려면 &#39;**-**&#39; 아이콘을 사용하여 빈 항목 하나를 제거합니다.

* **[!UICONTROL serviceSelector.name]**(*필수*) 서비스가 호출되는 절대 경로(끝점)입니다(가상 리소스). 선택한 경로의 루트는 OSGi 구성의 *실행 경로* 구성 설정 [ 에 포함되어야 `Apache Sling Servlet/Script Resolver and Error Handler`[#$tu39]합니다(예: `/bin/`, `/apps/`및 `/services/`). 사이트의 메시징 기능에 대해 이 구성을 선택하려면 이 끝점이 해당 **`Service selector`** 의 값으로 `Message List and Compose Message components` 제공됩니다( [메시지 기능](configure-messaging.md)참조). 기본값은 */bin/messaging입니다* .


* 


* 


* 


* 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeAllowlist.name]**
A blocklist of file extensions, prefixed with &#39;
**.**&#39;, that will be rejected by the system. If not blocklisted, then the extension is allowed. Extensions may be added or removed using the &#39;**+**&#39; and &#39;**-**&#39; icons. Default is *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Action Required*)** An allowlist of file extensions, the opposite of the blocklist. To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to remove the single empty entry.

* **[!UICONTROL serviceSelector.name]**
(*Required*) An absolute path (endpoint) through which the service is invoked (a virtual resource). The root of the path chosen must be one included in the *Execution Paths* configuration setting of OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`-ERR:REF-NOT-FOUND-, such as `/bin/`, `/apps/`, and `/services/`. To select this configuration for a site&#39;s messaging feature, this endpoint is provided as the **`Service selector`** value for the `Message List and Compose Message components` (see [Message Feature](configure-messaging.md)). The default is */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Use 
**Message Fields Allowlist**.

>[!CAUTION]
>
>Each time a `Messaging Operations Service` configuration is opened for edit, if `allowedAttachmentTypes.name` had been removed, an empty entry is re-added to make the property configurable. A single empty entry effectively disables file attachments.
>
>To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to (again) remove the single empty entry before clicking **[!UICONTROL Save]**.

## Troubleshooting {#troubleshooting}

One way to troubleshoot problems is to enable [debugging messages in the log.](../../help/sites-administering/troubleshooting.md)

See also [Loggers and Writers for Individual Services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

The package to monitor is `com.adobe.cq.social.messaging`.
