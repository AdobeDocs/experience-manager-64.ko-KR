---
title: 작성 시의 AEM 문제 해결
seo-title: 작성 시의 AEM 문제 해결
description: AEM을 사용할 때 발생할 수 있는 몇 가지 문제
seo-description: AEM을 사용할 때 발생할 수 있는 몇 가지 문제
uuid: 99af51ea-8628-4811-83f2-ab3f88f0279e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: da0a5644-2e1d-4394-a6aa-11bb41406ba6
exl-id: b0890070-c9e8-4ce4-9149-00c8c38298ce
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 100%

---

# 작성 시의 AEM 문제 해결{#troubleshooting-aem-when-authoring}

다음 섹션에서는 AEM 사용 시 발생할 수 있는 문제들과 이러한 문제의 해결 방법에 대한 제안 사항을 다룹니다.

>[!NOTE]
>
>문제가 발생하는 경우 인스턴스(릴리스 및 서비스 팩)에 대한 [알려진 문제](/help/release-notes/known-issues.md) 목록을 확인하는 것이 유용할 수 있습니다.

>[!NOTE]
>
>관리자 권한이 있는 사용자와 AEM 관련 문제를 해결하려는 사용자는 [AEM 문제 해결(관리자용)](/help/sites-administering/troubleshoot.md)에 설명된 문제 해결 방법을 사용할 수 있습니다. 충분한 권한이 없을 경우에는 시스템 관리자에게 AEM 문제 해결에 대해 문의하십시오.

## 게시된 사이트에 이전 페이지 버전이 여전히 있음 {#old-page-version-still-on-published-site}

* **문제**:

   * 페이지에 변경 작업을 수행하고 이 페이지를 게시 사이트에 복제했지만, 페이지의 *이전* 버전이 여전히 게시 사이트에 표시되고 있습니다.

* **이유**:

   * 이것은 때로 복제 큐 문제일 수 있지만 몇 가지 원인이 있을 수 있고 대개는 캐시 문제일 수 있습니다(로컬 브라우저나 디스패처 중 하나).

* **솔루션**:

   * 다음과 같이 다양한 가능성이 있습니다.
   * 페이지가 올바로 복제되었는지 확인합니다. 페이지 상태를 확인하고, 필요할 경우 복제 큐의 상태도 확인합니다.
   * 로컬 브라우저의 캐시를 지우고 다시 페이지에 액세스합니다.
   * 페이지 URL의 끝에 `?`를 추가합니다. 예:

      * `http://localhost:4502/sites.html/content?`
      * 이렇게 하면 페이지가 AEM에서 바로 요청되고 디스패처가 무시됩니다. 업데이트된 페이지가 표시되면, 이것은 디스패처 캐시를 지우라는 의미입니다.
   * 복제 큐 문제가 있을 경우 시스템 관리자에게 문의하십시오.


## 구성 요소 작업이 도구 모음에 표시되지 않음 {#component-actions-not-visible-on-toolbar}

* **문제**:

   * 적용 가능한 구성 요소 작업의 전체 범위는 작성 환경에서 컨텐츠 페이지를 편집할 때 표시되지 않습니다.

* **이유**:

   * 드문 경우이지만 이전 작업이 도구 모음에 영향을 줄 수 있습니다.

* **솔루션**:

   * 페이지를 새로 고칩니다.
