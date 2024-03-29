---
title: AEM Communities의 사용자 및 UGC 관리 서비스
seo-title: User and UGC Management Service in AEM Communities
description: API를 사용하여 사용자 생성 컨텐츠를 벌크 삭제 및 대량 내보내고 사용자 계정을 비활성화할 수 있습니다.
seo-description: Use APIs to bulk delete and bulk export user generated content, and disable user account.
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
role: Admin
exl-id: f4adc53d-6809-4d89-a3dd-5d783e938a63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 8%

---

# AEM Communities의 사용자 및 UGC 관리 서비스 {#user-and-ugc-management-service-in-aem-communities}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!IMPORTANT]
>
>아래 섹션에서는 GDPR이 예로 사용되지만, 포함된 세부 사항은 GDPR, CCPA 등 모든 데이터 보호 및 개인 정보 보호 규정에 적용됩니다.

AEM Communities은 사용자 프로필을 관리하고 사용자 생성 콘텐츠(UGC)를 벌크 관리하기 위해 즉시 사용 가능한 API를 표시합니다. 활성화되면, **UserUgcManagement** 권한 있는 사용자(커뮤니티 관리자 및 중재자)는 사용자 프로필을 비활성화하고 특정 사용자에 대해 UGC를 벌크 삭제 또는 대량 내보낼 수 있습니다. 또한 이러한 API를 통해 고객 데이터의 제어자와 프로세서는 유럽 연합의 GDPR(General Data Protection Regulation) 및 기타 GDPR에서 권장하는 개인 정보 보호 규정을 준수할 수 있습니다.

자세한 내용은 [Adobe 개인 정보 보호 센터의 GDPR 페이지](https://www.adobe.com/privacy/general-data-protection-regulation.html)를 참조하십시오.

>[!NOTE]
>
>구성한 경우 [AEM Communities의 Adobe Analytics](analytics.md) 사이트에서 캡처된 사용자 데이터는 Adobe Analytics 서버로 전송됩니다. Adobe Analytics은 사용자 데이터에 액세스, 내보내기 및 삭제하고 GDPR을 준수하는 데 사용할 수 있는 API를 제공합니다. 자세한 내용은 [액세스 및 삭제 요청 제출](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

이러한 API를 사용하려면 `/services/social/ugcmanagement` UserUgcManagement 서비스를 활성화하여 끝점입니다. 이 서비스를 활성화하려면 [샘플 서블릿](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) 사용 가능 [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). 그런 다음 다음과 같이 http 요청을 사용하여 적절한 매개 변수를 사용하여 커뮤니티 사이트의 게시 인스턴스에 있는 엔드포인트를 히트합니다.

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

그러나 UI(사용자 인터페이스)를 작성하여 시스템에서 사용자 프로필과 사용자 생성 컨텐츠를 관리할 수도 있습니다.

이러한 API를 사용하면 다음 기능을 수행할 수 있습니다.

## 사용자의 UGC 검색 {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` 은 시스템에서 사용자의 모든 UGC를 내보내는 데 도움이 됩니다.

* **사용자**: 사용자의 작성 가능한 ID.
* **outputStream**: 결과는 사용자가 생성한 컨텐츠(json 파일)와 첨부 파일(사용자가 업로드한 이미지 또는 비디오 포함)을 포함하는 zip 파일인 출력 스트림으로 반환됩니다.

예를 들어, weston.mccall@dodgit.com을 작성 가능한 ID로 사용하여 커뮤니티 사이트에 로그인하는 Weston McCall이라는 사용자의 UGC를 내보내려면 다음과 유사한 http GET 요청을 보낼 수 있습니다.

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## 사용자의 UGC 삭제 {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** 은 시스템에서 사용자의 모든 UGC를 삭제하는 데 도움이 됩니다.

* **사용자**: 사용자의 작성 가능한 ID.

예를 들어 http-POST 요청을 통해 작성 가능한 ID가 weston.mccall@dodgit.com 있는 사용자의 UGC를 삭제하려면 다음 매개 변수를 사용하십시오.

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Adobe Analytics에서 UGC 삭제 {#delete-ugc-from-analytics}

Adobe Analytics에서 사용자 데이터를 삭제하려면 GDPR Analytics 워크플로우를 따릅니다. api는 Adobe Analytics에서 사용자 데이터를 삭제하지 않습니다.

AEM Communities에서 사용하는 Adobe Analytics 변수 매핑에 대해서는 다음 이미지를 참조하십시오.

![Adobe Analytics에 대한 AEM 커뮤니티 변수 매핑](assets/Analytics-Communities-Mapping.png)

## 사용자 계정 비활성화 {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** 은 사용자 계정을 비활성화하는 데 도움이 됩니다.

* **사용자**: 사용자의 작성 가능한 ID.

>[!NOTE]
>
>사용자를 비활성화하면 사용자가 서버에 가지고 있는 모든 사용자 생성 컨텐츠가 삭제됩니다.

예를 들어 http-POST 요청을 통해 ID weston.mccall@dodgit.com을 갖는 사용자의 프로필을 삭제하려면 다음 매개 변수를 사용하십시오.

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>deleteUserAccount() API는 시스템에서 사용자 프로필만 비활성화하고 UGC를 제거합니다. 그러나 시스템에서 사용자 프로필을 삭제하려면 **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de)를 눌러 사용자 노드를 찾아 삭제합니다.
