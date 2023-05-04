---
title: 자산 테스트에 대한 이름 지정 규칙
seo-title: Naming conventions for assets
description: 저장소의 노드는 Java 컨텐츠 저장소의 이름 지정 규칙을 따릅니다. 그러나 Adobe Experience Manager은 자산 노드의 이름에 대한 추가적인 규칙을 적용합니다.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 6%

---

# 자산 테스트에 대한 이름 지정 규칙{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

저장소의 노드는 [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). 그러나 Adobe Experience Manager은 자산 노드의 이름에 대한 추가적인 규칙을 적용합니다.

## 클래식 UI {#classic-ui}

클래식 UI에서는 더 엄격한 제한을 적용합니다.

* 다음 중 한 경우 명시적 노드 이름이 있을 때 자산 이름을 확인합니다.

   * 노드 이름으로 변환할 자산 제목이 제공됩니다
   * 명시적 노드 이름이 제공됩니다

* 유효한 문자(클래식 UI 내에서 자산이 만들어지는 경우 이러한 문자만 실제로 유효합니다.):

   * &#39;a&#39;~&#39;z&#39;
   * &#39;A&#39;~&#39;Z&#39;
   * &#39;0&#39;~&#39;9&#39;
   * _(밑줄)
   * `-` (대시/빼기)
