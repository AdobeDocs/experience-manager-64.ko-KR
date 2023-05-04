---
title: 메시징 구성
seo-title: Configuring Messaging
description: 커뮤니티 메시징
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 2%

---

# 메시징 구성 {#configuring-messaging}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

AEM Communities의 메시징 기능은 로그인한 사이트 방문자(구성원)가 사이트에 로그인할 때 액세스할 수 있는 서로 다른 사람에게 메시지를 전송하는 기능을 제공합니다.

커뮤니티 사이트에 대해 [커뮤니티 사이트 만들기](sites-console.md).

이 페이지에서는 기본 구성 및 가능한 조정에 대한 정보를 제공합니다.

개발자를 위한 자세한 내용은 [메시징 핵심 사항](essentials-messaging.md).

## 메시징 작업 서비스 {#messaging-operations-service}

다음 [AEM Communities 메시징 작업 서비스](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) 메시징 관련 요청을 처리하는 종단점, 서비스를 사용하여 메시지를 저장하는 데 사용해야 하는 폴더, 메시지에 파일 첨부 파일이 포함될 수 있는 경우 허용되는 파일 유형을 식별합니다.

를 사용하여 만든 커뮤니티 사이트의 경우 [커뮤니티 사이트 콘솔](sites-console.md)로 설정되어 있는 경우 서비스의 인스턴스가 이미 존재하며, `/mail/community/inbox`.

### 커뮤니티 메시징 작업 서비스 {#community-messaging-operations-service}

아래 표시된 것처럼 과 함께 만들어진 사이트에 대한 서비스 구성이 있습니다 [사이트 만들기 마법사](sites-console.md). 구성 옆에 있는 연필 아이콘을 선택하여 구성을 보거나 편집할 수 있습니다.

![chlimage_1-63](assets/chlimage_1-63.png)

### 새 구성 {#new-configuration}

새 구성을 추가하려면 더하기 &#39; 를 선택합니다&#x200B;**+**&#39; 서비스 이름 옆에 있는 아이콘을 클릭합니다.

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 메시지 허용 목록에 추가하다 필드]**
사용자가 편집하고 유지할 수 있는 메시지 작성 구성 요소의 속성을 지정합니다. 새 양식 요소를 추가하는 경우 SRP에 저장하려면 요소 ID를 추가해야 합니다. 기본값은 두 개의 항목입니다. 
*주제* 및 *콘텐츠*.

* **[!UICONTROL 메시지 상자 크기 제한]**
각 사용자의 메시지 상자에 있는 최대 바이트 수입니다. 기본값은 입니다. 
*1073741824* (1GB).

* **[!UICONTROL 메시지 수 제한]**
사용자당 허용되는 총 메시지 수입니다. 값이 -1이면 메시지 상자 크기 제한에 따라 메시지 수를 무제한으로 지정할 수 있습니다. 기본값은 입니다. 
*10000* (10k).

* **[!UICONTROL 게재 실패 알림]**
이 옵션을 선택하면 일부 수신자에게 메시지 배달이 실패하면 발신자에게 알립니다. 기본값은 입니다. 
*선택함*.

* **[!UICONTROL 게재 발신자 ID 실패]**
게재 실패 메시지에 나타나는 발신자의 이름입니다. 기본값은 입니다. 
*failureNotifier*.

* **[!UICONTROL 실패 메시지 템플릿 경로]**
게재 실패 메시지 템플릿 루트의 절대 경로입니다. 기본값은 입니다. 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
배달되지 않은 메시지를 다시 보내는 데 필요한 횟수입니다. 기본값은 입니다. 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
전송 실패 시 메시지 재전송을 시도하는 동안 대기할 시간(초)입니다. 기본값은 *100 *(초)입니다.

* **[!UICONTROL 업데이트 풀 크기 수]**
카운트 업데이트에 사용되는 동시 스레드 수입니다. 기본값은 입니다. 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*필수 여부*) 사용자의 노드(/home/users/)에 상대적인 경로입니다.*사용자 이름*)에 대해 사용할 수 있습니다. **`inbox`** 폴더를 입력합니다. 경로는 후행 슬래시 &#39;/&#39;로 끝나야 합니다. 기본값은 입니다. */mail/inbox* .

* **[!UICONTROL sentiems.path.name]**
(
*필수 여부*) 사용자의 노드(/home/users/)에 상대적인 경로입니다.*사용자 이름*)에 대해 사용할 수 있습니다. **`senditems`** 폴더를 입력합니다. 경로는 후행 슬래시 &#39;/&#39;로 끝나야 합니다. 기본값은 입니다. */mail/sentims* .

* **[!UICONTROL supportAttachments.name]**
이 확인란을 선택하면 사용자가 메시지에 첨부 파일을 추가할 수 있습니다. 기본값은 입니다. 
*선택함*.

* **[!UICONTROL batchSize.name]**
대규모 수신자 그룹에 보낼 때 전송을 위해 함께 일괄 처리할 메시지 수입니다. 기본값은 입니다. 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
supportAttachments를 선택하면 이 값은 모든 첨부 파일의 최대 허용 전체 크기(바이트)를 지정합니다. 기본값은 입니다. 
*104857600* (100MB).

* **[!UICONTROL attachmentTypeBlocklist.name]**
&#39; 접두사가 있는 차단 목록에 추가하다 파일 확장자 한 파일 확장자입니다.
**.**&#x200B;시스템에서 거부됩니다. 차단 목록에 추가된이 아닌 경우 확장이 허용됩니다. 확장은 &#39;**+**&#39; 및 &#39;**-**&#39; 아이콘입니다. 기본값은 입니다. *기본값*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*필요한 작업*)** 파일 확장자허용 목록에 추가하다와 파일의 차단 목록에 추가하다 반대입니다. 차단 목록에 추가된을 제외한 모든 파일 확장자를 허용하려면 &#39;**-**&#39; 아이콘을 사용하여 빈 단일 항목을 제거합니다.

* **[!UICONTROL serviceSelector.name]**
(*필수 여부*) 서비스를 호출하는 절대 경로(끝점)입니다(가상 리소스). 선택한 경로의 루트는 *실행 경로* OSGi 구성의 구성 설정 [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), 예 `/bin/`, `/apps/`, 및 `/services/`. 사이트의 메시징 기능에 대해 이 구성을 선택하려면 이 엔드포인트가 **`Service selector`** 값 `Message List and Compose Message components` 자세한 내용은 [메시지 기능](configure-messaging.md)). 기본값은 입니다. */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
사용 
**메시지 허용 목록에 추가하다 필드**.

>[!CAUTION]
>
>매번 `Messaging Operations Service` 편집을 위해 구성이 열려 있는 경우 `allowedAttachmentTypes.name` 가 제거되면 빈 항목이 다시 추가되어 속성을 구성할 수 있습니다. 빈 항목 하나가 있으면 파일 첨부 파일이 효과적으로 비활성화됩니다.
>
>차단 목록에 추가된을 제외한 모든 파일 확장자를 허용하려면 &#39;**-**&#39; 아이콘 - (다시) 단일 빈 항목을 제거한 후에 를 클릭합니다. **[!UICONTROL 저장]**.

## 문제 해결 {#troubleshooting}

문제를 해결하는 한 가지 방법은 다음과 같습니다 [로그에 메시지를 디버깅합니다.](../../help/sites-administering/troubleshooting.md)

참조 - [개인 서비스를 위한 로거 및 작가](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

모니터링할 패키지 `com.adobe.cq.social.messaging`.
