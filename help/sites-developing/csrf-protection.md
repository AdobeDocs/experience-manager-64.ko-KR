---
title: CSRF 보호 프레임워크
seo-title: CSRF 보호 프레임워크
description: 프레임워크는 토큰을 사용하여 클라이언트 요청이 합법적임을 보장합니다
seo-description: 프레임워크는 토큰을 사용하여 클라이언트 요청이 합법적임을 보장합니다
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: 533c348e-517f-4d70-a89c-bfc87f71a633
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 6%

---

# CSRF 보호 프레임워크{#the-csrf-protection-framework}

Apache Sling Referrer Filter 외에도 Adobe은 이러한 유형의 공격으로부터 보호하기 위한 새로운 CSRF 보호 프레임워크를 제공합니다.

프레임워크는 토큰을 사용하여 클라이언트 요청이 합법적임을 보장합니다. 토큰은 양식이 클라이언트에 전송될 때 생성되며 양식이 서버에 다시 전송될 때 유효성이 확인됩니다.

>[!NOTE]
>
>익명 사용자에 대한 게시 인스턴스에는 토큰이 없습니다.

## 요구 사항 {#requirements}

### 종속성 {#dependencies}

`granite.jquery` 종속성을 사용하는 모든 구성 요소는 CSRF 보호 프레임워크를 자동으로 활용할 수 있습니다. 이 경우 구성 요소에 대해 해당되지 않는 경우 프레임워크를 사용하려면 먼저 `granite.csrf.standalone`에 대한 종속성을 선언해야 합니다.

### 암호화 키 {#replicating-crypto-keys} 복제

토큰을 사용하려면 `/etc/keys/hmac` 바이너리를 배포의 모든 인스턴스에 복제해야 합니다. HMAC 키를 모든 인스턴스에 복사하는 편리한 방법은 키가 포함된 패키지를 만들어 모든 인스턴스에 패키지 관리자를 통해 설치하는 것입니다.

>[!NOTE]
>
>CSRF 보호 프레임워크를 사용하려면 필요한 [Dispatcher 구성을 변경](https://helpx.adobe.com/kr/experience-manager/dispatcher/user-guide.html)해야 합니다.

>[!NOTE]
>
>웹 응용 프로그램에서 매니페스트 캐시를 사용하는 경우 토큰이 CSRF 토큰 생성 호출을 오프라인으로 사용하지 않도록 하려면 매니페스트에 &quot;**&amp;ast;**&quot;를 추가해야 합니다. 자세한 내용은 이 [링크](https://www.w3.org/TR/offline-webapps/)를 참조하십시오.
>
>CSRF 공격 및 이를 완화하는 방법에 대한 자세한 내용은 [사이트 간 요청 위조 OWASP 페이지](https://owasp.org/www-community/attacks/csrf)를 참조하십시오.
