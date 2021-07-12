---
title: 이메일 구성
seo-title: 이메일 구성
description: 커뮤니티에 대한 이메일 구성
seo-description: 커뮤니티에 대한 이메일 구성
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 1%

---

# 이메일 구성 {#configuring-email}

AEM Communities에 이메일을 사용

* [커뮤니티 알림](notifications.md)
* [커뮤니티 구독](subscriptions.md)

기본적으로 전자 메일 기능은 SMTP 서버 및 SMTP 사용자의 사양이 필요하므로 작동하지 않습니다.

>[!CAUTION]
>
>알림 및 구독 이메일은 [기본 게시자](deploy-communities.md#primary-publisher)에서만 구성해야 합니다.

## 기본 메일 서비스 구성 {#default-mail-service-configuration}

알림과 구독 모두에 기본 메일 서비스가 필요합니다.

* 기본 게시자에서
* 관리자 권한으로 로그인됨
* [웹 콘솔](../../help/sites-deploying/configuring-osgi.md)에 액세스

   * 예: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* `Day CQ Mail Service` 찾기
* 편집 아이콘을 선택합니다

이것은 [전자 메일 알림 구성](../../help/sites-administering/notification.md)에 대한 설명서를 기반으로 하지만, `"From" address` 필드가&#x200B;*필수가 아닌*&#x200B;이므로 비워 두어야 한다는 점에서 다릅니다.

예를 들어, (예시적인 목적으로만 값으로 채워짐):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL SMTP 서버 호스트 이름]**:  *(필수)* 사용할 SMTP 서버입니다.

* **[!UICONTROL SMTP 서버 포트]** *(필수)*  SMTP 서버 포트는 25 이상이어야 합니다.

* **[!UICONTROL SMTP 사용자]**:  *(필수)* SMTP 사용자입니다.

* **[!UICONTROL SMTP 암호]**:  *(필수)* SMTP 사용자의 암호입니다.

* **[!UICONTROL &quot;보낸 사람&quot; 주소]**: 비워 둡니다.
* **[!UICONTROL SMTP 사용 SSL]**: 이(가) 선택된 경우 보안 이메일을 보냅니다. 포트가 SMTP 서버에 필요한 대로 465로 설정되어 있는지 확인합니다.
* **[!UICONTROL 디버그 전자 메일]**: 이 옵션을 선택하면 SMTP 서버 상호 작용 로깅을 사용합니다.

## AEM Communities 이메일 구성 {#aem-communities-email-configuration}

[기본 메일 서비스](#default-mail-service-configuration)가 구성되면 릴리스에 포함된 `AEM Communities Email Reply Configuration` OSGi 구성의 두 기존 인스턴스가 작동합니다.

전자 메일로 응답을 허용할 때는 구독 인스턴스만 추가로 구성해야 합니다.

1. ` [email](#configuration-for-notifications)` 인스턴스

   회신 이메일을 지원하지 않는 알림의 경우, 변경하지 말아야 합니다.

1. ` [subscriptions-email](#configuration-for-subscriptions)` 인스턴스

   회신 이메일을 통한 게시물 작성을 완전히 활성화할 수 있도록 구성 필요

Communities 이메일 구성 인스턴스에 도달하려면 다음을 수행하십시오.

* 기본 게시자에서
* 관리자 권한으로 로그인됨
* [웹 콘솔](../../help/sites-deploying/configuring-osgi.md)에 액세스

   * 예: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* `AEM Communities Email Reply Configuration` 찾기

![chlimage_1-99](assets/chlimage_1-99.png)

### 알림용 구성 {#configuration-for-notifications}

이름 이메일이 있는 `AEM Communities Email Reply Configuration` OSGi 구성의 인스턴스는 알림 기능을 위한 것입니다. 이 기능에는 이메일 회신이 포함되지 않습니다.

이 구성은 변경하지 마십시오.

* `AEM Communities Email Reply Configuration` 찾기
* 편집 아이콘을 선택합니다
* **이름**&#x200B;이 `email`인지 확인합니다.

* **회신 이메일에서 게시물 만들기**&#x200B;가 `unchecked`인지 확인합니다.

![chlimage_1-100](assets/chlimage_1-100.png)

### 구독 구성 {#configuration-for-subscriptions}

커뮤니티 구독의 경우, 전자 메일에 응답하여 구성원이 컨텐츠를 게시할 수 있는 기능을 활성화하거나 비활성화할 수 있습니다.

* `AEM Communities Email Reply Configuration` 찾기
* 편집 아이콘을 선택합니다
* **이름**&#x200B;이 `subscriptions-email`인지 확인합니다.

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL 이름]** :  *(필수)* `subscriptions-email`. 편집하지 마십시오.

* **[!UICONTROL 회신 이메일에서 게시물 만들기]**: 이 확인란을 선택하면 구독 이메일의 수신자가 응답을 보내 콘텐츠를 게시할 수 있습니다. 기본값이 선택되어 있습니다.
* **[!UICONTROL 헤더에 추적된 ID 추가]**: 기본값은  `Reply-To`입니다.

* **[!UICONTROL 최대 제목 길이]**: 추적기 ID를 제목 줄에 추가하면 추적된 ID를 제외하고 제목 최대 길이로 트리밍됩니다. 추적된 ID 정보가 손실되지 않도록 하려면 가능한 한 작게 표시해야 합니다. 기본값은 200입니다.
* **[!UICONTROL 이메일 &quot;보낸 사람&quot; 주소]**:  *(필수)* 알림 이메일을 배달할 주소입니다. [기본 메일 서비스](#configuredefaultmailservice)에 대해 지정된 동일한 **SMTP 사용자**&#x200B;일 수 있습니다. 기본값은 `no-reply@example.com`입니다.

* **[!UICONTROL 회신 구분 기호]**: 추적기 ID가 회신 헤더에 추가되면 이 구분 기호가 사용됩니다. 기본값은 `+`(더하기 기호)입니다.

* **[!UICONTROL 주체의 추적기 Id 접두사]**: 추적기 ID를 제목 줄에 추가하면 이 접두사가 사용됩니다. 기본값은 `post#`입니다.

* **[!UICONTROL 메시지 본문의 추적기 ID 접두사]**: 추적기 ID를 메시지 본문에 추가하면 이 접두사가 사용됩니다. 기본값은 `Please do not remove this:`입니다.

* **[!UICONTROL 이메일(HTML]**): 이 확인란을 선택하면 콘텐츠 유형의 이메일이 로 설정됩니다 `"text/html;charset=utf-8"`. 기본값이 선택되어 있습니다.

* **[!UICONTROL 기본 사용자 이름]**: 이 이름은 이름 사용자가 없을 때 사용됩니다. 기본값은 `no-reply@example.com`입니다.

* **[!UICONTROL 템플릿 루트 경로]**: 이메일은 이 루트 경로에 저장된 템플릿을 사용하여 작성됩니다. 기본값은 `/etc/community/templates/subscriptions-email`입니다.

## 폴링 가져오기 구성 {#configure-polling-importer}

전자 메일을 저장소로 가져오려면 폴링 가져오기를 구성하고 리포지토리에서 해당 속성을 수동으로 구성해야 합니다.

### 새 폴링 가져오기 추가 {#add-new-polling-importer}

* 기본 게시자에서
* 관리자 권한으로 로그인됨
* 폴링 가져오기 콘솔로 이동합니다.
예: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* **[!UICONTROL 추가]** 선택

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL 유형]**:  *(필수)* 선택하려면 아래로 당기십시오  `POP3 (over SSL).`

* **[!UICONTROL URL]**:  *(필수)* 아웃바운드 메일 서버입니다. 예, `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL 경로]** 가져오기(&amp;A):  *(필수)* 을  `/content/usergenerated/mailFolder/postEmails`
찾아보고 로 설정합니다. 
`postEmails`폴더를 만들고  **확인 을 선택합니다.**

* **[!UICONTROL 업데이트 간격(초)]**:  *(선택 사항)* 기본 메일 서비스에 대해 구성된 메일 서버에는 업데이트 간격 값에 대한 요구 사항이 있을 수 있습니다. 예를 들어 Gmail에는 `300` 간격이 필요할 수 있습니다.

* **[!UICONTROL 로그인]**:  *(선택 사항)*

* **[!UICONTROL 암호]**:  *(선택 사항)*

* **[!UICONTROL 확인]** 선택

### 새 폴링 가져오기에 대한 프로토콜 조정 {#adjust-protocol-for-new-polling-importer}

새 폴링 구성이 저장되면 프로토콜을 `POP3`에서 `emailreply`(으)로 변경하려면 구독 전자 메일 가져오기의 속성을 추가로 수정해야 합니다

[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) 사용:

* 기본 게시자에서
* 관리자 권한으로 로그인됨
* [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importers/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)로 이동합니다.
* 새로 만든 구성을 선택합니다
* 다음 속성을 수정합니다

   * **feedType**: 다음으로  `pop3s` 바꾸기  **`emailreply`**
   * **소스**: 원본 프로토콜 `pop3s://` 을  **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

빨간색 삼각형은 수정된 속성을 나타냅니다. 변경 사항을 저장해야 합니다.

* **[!UICONTROL 모두 저장]** 선택
