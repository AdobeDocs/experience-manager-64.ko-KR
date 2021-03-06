---
title: 이름 지정 규칙
seo-title: 이름 지정 규칙
description: 저장소의 노드는 Java 컨텐츠 저장소의 이름 지정 규칙을 따릅니다
seo-description: 저장소의 노드는 Java 컨텐츠 저장소의 이름 지정 규칙을 따릅니다
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
exl-id: 741043c7-2ebb-455d-8163-a246b874a7b3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 21%

---

# 이름 지정 규칙{#naming-conventions}

저장소의 노드는 [Java 컨텐츠 저장소](/help/sites-developing/the-basics.md#java-content-repository)의 이름 지정 규칙을 따릅니다. 그러나 AEM에서는 페이지 노드의 이름에 대한 추가적인 규칙을 적용합니다.

## 페이지 이름 지정 규칙 {#naming-conventions-for-pages}

이러한 이름 지정 규칙은 다음과 같은 다양한 수준에서 구현됩니다.

* JcrUtil:[JCR 유틸리티의 AEM 구현](#jcr-utilities)
* 페이지 관리자:[페이지 관리자](#page-manager)는 페이지 수준 작업에 대한 메서드를 제공합니다.
* 사용되는 UI에 따라:

   * [표준, 터치 지원 UI](#standard-ui)
   * [클래식 UI](#classic-ui)

### JCR 유틸리티 {#jcr-utilities}

[](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) JcrUtilities는 JCR 유틸리티의 AEM 구현을 나열합니다. 이름 유효성 검사에 대한 특정 관심 사항은 이 컨트롤이 제어하는 문자 매핑과 다음 유효성 검사입니다.

* `isValidName`

   * 이름이 비어 있지 않고 올바른 문자만 포함되어 있는지 확인합니다.
   * 제안된 이름이 유효한지 확인하는 데 사용할 수 있습니다.

* `createValidName`

   * 이렇게 하면 임의의 문자열로 유효한 레이블이 만들어집니다.
   * 제목에서 이름을 만드는 데 사용할 수 있습니다.

### 페이지 관리자 {#page-manager}

[](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) PageManager는 JCRUtil [을 기반으로 페이지 수준 작업을 위한 ](#jcr-utilities)메서드를 제공합니다.

### 표준 UI {#standard-ui}

터치 지원 표준 UI:

* 다음 경우 PageManager에서 지정한 제한에 따라 이름을 확인합니다.

   * 노드 이름으로 전환할 페이지 제목이 제공됩니다
   * 명시적 노드 이름이 제공됩니다.

### 클래식 UI {#classic-ui}

클래식 UI에서는 더 엄격한 제한 사항을 적용합니다.

* 다음 중 한 경우에 명시적 노드 이름이 있을 때 이름을 확인합니다.

   * 노드 이름으로 전환할 페이지 제목이 제공됩니다
   * 명시적 노드 이름이 제공됩니다.

* 유효한 문자(`PageManagerImpl` 은 추가 문자를 허용하지만 클래식 UI 내에서 페이지를 만들 때는 이러한 문자만 실제로 유효합니다.):

   * &#39;a&#39; ~ &#39;z&#39;
   * &#39;A&#39; ~ &#39;Z&#39;
   * &#39;0&#39; ~ &#39;9&#39;
   * _(밑줄)
   * `-` (대시/빼기 기호)
