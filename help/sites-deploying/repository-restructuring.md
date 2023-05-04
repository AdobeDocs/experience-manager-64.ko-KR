---
title: AEM 6.4의 저장소 구조 변경
seo-title: Repository Restructuring in AEM 6.4
description: AEM 6.4에서 저장소 구조 변경 이면의 기본 사항과 논리에 대해 알아봅니다
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 2%

---

# AEM 6.4의 저장소 구조 변경{#repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

AEM 6.4 이전에는 업그레이드 시 변경될 수 있는 JCR의 예측할 수 없는 영역에 고객 코드가 배포되었습니다. 이러한 이유로 공식 AEM 릴리스에서 사용자 지정 코드, 구성 또는 컨텐츠를 덮어쓰는 것이 일반적이었습니다. 또한 고객이 변경했을 때 AEM 제품 코드 또는 컨텐츠가 오버라이드되어 제품 기능이 손상되는 경우가 있습니다.

AEM 제품 코드 및 고객 코드에 대한 계층을 명확히 설명함으로써 이러한 충돌을 피할 수 있습니다.

이를 위해 AEM 6.4부터 향후 릴리스에서 컨텐츠를 계속 사용할 수 있도록 다음과 같은 높은 수준의 규칙을 준수하면서 컨텐츠의 위치에 대한 지침과 함께 저장소의 다른 폴더로 컨텐츠가 재구성됩니다.

* AEM 제품 코드는 항상 /libs에 삽입되며, 사용자 지정 코드로 덮어쓰지 않아야 합니다
* 사용자 지정 코드는 /apps, /content 및 /conf에 삽입해야 합니다

## 6.4 업그레이드에 미치는 영향 {#impact-on-upgrades}

AEM 6.4로 업그레이드할 때 /etc 아래에 있는 컨텐츠의 큰 하위 세트가 저장소의 다른 폴더에 복제됩니다. 이러한 새 위치는 컨텐츠를 참조하는 기본 위치입니다. 그러나 AEM 6.4 업그레이드가 /etc 폴더의 이전 위치와 이전 호환되도록 모든 시도가 수행되었으므로 대부분의 경우 변경 사항이 활성 상태가 될 때까지 및 대부분의 경우 수동으로 고객의 애플리케이션에서 수행될 때까지 AEM 코드에서 이전 위치를 계속 참조합니다. 타임라인 관점에서 변경 사항에는 두 가지 카테고리가 있습니다.

* 6.4 업그레이드 포함 - 일부 /etc 재구성 변경 사항은 이전 버전과 호환되지 않으므로 AEM 6.4 업그레이드의 일부로 수정 사항을 계획하고 구현해야 합니다.
* 6.5 업그레이드 전 - 향후 업그레이드 후 어느 시점까지 /etc 재구성 변경 사항 대부분을 지연할 수 있습니다. 이전에 언급했듯이 AEM 6.4 코드는 수정 사항이 고객 릴리스의 일부로 구현될 때까지 이전 위치를 계속 참조합니다. 변경해야 하는 강제 타임라인은 없지만, 향후 기능이 참조되는 새 위치에 따라 사용될 수 있으므로 6.5 업그레이드 전에 수행하는 것이 좋습니다. 또한 주어진 기능에 대한 설명서는 새 위치를 참조하므로 이전 위치가 계속 사용되고 있는 경우 혼동될 수 있습니다.

### 구조 조정 지침 {#restructuring-guidance}

AEM 6.4로 업그레이드를 계획하는 동안 작업 노력을 평가하려면 다음의 솔루션 당 페이지를 참조해야 합니다.

* [모든 AEM 솔루션에 공통으로 사용되는 저장소 구조 변경](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [AEM Sites 저장소 구조 변경](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [AEM Assets 저장소 구조 변경](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html)
* [AEM Assets Dynamic Media 저장소 구조 변경](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [AEM Forms 저장소 구조 변경](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [AEM Communities 저장소 구조 변경](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [AEM Commerce 저장소 구조 변경](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

각 페이지에는 필요한 변경 사항의 긴급성에 해당하는 두 개의 섹션이 있습니다. &quot;6.4 업그레이드 사용&quot; 섹션의 모든 내용은 AEM 6.4 업그레이드 프로젝트의 일부로 태깅해야 합니다. 6.5 이전 업그레이드 아래에 있는 모든 것은 업그레이드 후 까지 선택적으로 지연될 수 있습니다.

페이지의 각 항목에는 &quot;구조 변경 지침&quot; 필드가 포함되어 있습니다. 이 필드는 /etc 폴더 아래에 이전에 있는 컨텐츠에 대해 새 위치를 참조하도록 새 6.4 저장소 모델과 정렬하기 위해 권장되는 기술 전략을 자세히 설명합니다. 추가 &quot;참고&quot; 필드는 유용한 추가 컨텍스트를 제공합니다.
