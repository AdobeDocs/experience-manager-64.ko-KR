---
title: 컨텐츠 처리 필터
seo-title: Content Disposition Filter
description: XSS 공격을 방지하기 위해 컨텐츠 처리 필터를 사용하는 방법을 알아봅니다.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---

# 컨텐츠 처리 필터 {#content-disposition-filter}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

컨텐츠 처리 필터는 SVG 파일에 대한 XSS 공격에 대한 보안 기능입니다.

설치되면 필터가 모든 자산에 대한 액세스를 차단합니다. 예를 들어 온라인에서 PDF을 볼 수 없습니다. 이 섹션에서는 필요에 따라 필터를 구성하는 방법을 설명합니다.

## 컨텐츠 처리 필터 구성 {#configure-content-disposition-filter}

을 볼 수 있습니다 [GitHub의 Apache Sling 컨텐츠 처리 필터.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

컨텐츠 처리 필터 옵션은 다음과 같은 기능을 제공합니다.

* **컨텐츠 처리 경로:** 필터를 적용할 경로 목록 다음에 해당 경로에서 제외할 mime 유형 목록이 옵니다. 이 경로는 절대 경로여야 하며 와일드카드(`*`)를 클릭하여 지정한 경로 접두사와 모든 리소스 경로를 일치시킵니다. 예: `/content/*:image/jpeg,image/svg+xml` 필터를 의 모든 노드에 적용합니다. `/content` jpg 및 svg 이미지 제외

* **제외된 리소스 경로:** 제외된 리소스 목록으로서, 각 리소스 경로는 절대 및 정규화된 경로로 부여되어야 합니다. 접두사 일치/와일드카드는 지원되지 않습니다.

* **모든 리소스 경로에 대해 사용:** 이 플래그는 제외된 리소스 경로에 정의된 제외된 경로를 제외하고 모든 경로에 대해 이 필터를 활성화할지 여부를 제어합니다. 이를 &#39;true&#39;로 설정하면 컨텐츠 처리 경로가 무시됩니다. 구성에 독립적이지 않고 이름이 지정된 속성을 포함하는 리소스 경로만 다룹니다 `jcr:data` 또는
   `jcr:content jcr:data`.
