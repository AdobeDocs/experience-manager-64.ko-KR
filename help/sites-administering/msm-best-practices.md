---
title: MSM 우수 사례
seo-title: MSM 우수 사례
description: AEM 다중 사이트 관리자를 시작하고 실행하는 데 도움이 되도록 Adobe 엔지니어링 및 컨설팅 팀이 컴파일한 우수 사례를 찾습니다.
seo-description: AEM 다중 사이트 관리자를 시작하고 실행하는 데 도움이 되도록 Adobe 엔지니어링 및 컨설팅 팀이 컴파일한 우수 사례를 찾습니다.
uuid: cbb598bb-ec8f-4985-97af-7c87f5891c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features, best-practices
content-type: reference
discoiquuid: 04344537-7485-40a9-ad14-804ba448f1e2
feature: 다중 사이트 관리자
exl-id: f23a1c62-0191-4b5b-90be-d66d51e38f83
source-git-commit: 3ee650d0810a03878b4b0a58708ea3600fa28ff2
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 1%

---

# MSM 우수 사례{#msm-best-practices}

## 일반 {#general}

MSM은 콘텐츠 배포를 자동화하기 위한 구성 가능한 프레임워크입니다. 구현에는 종종 웹 사이트의 주요 부분과 조직 및 지역 범위가 포함됩니다. 따라서 웹 사이트를 계획하는 대로 MSM 구현을 신중하게 계획하는 것이 좋습니다.

* 구현을 시작하기 전에 **계획 구조 및 컨텐츠 흐름**&#x200B;을 주의하십시오.
* **필요한 만큼 사용자 지정하되 가능한 한 적게 사용자 지정합니다.** MSM은 높은 수준의 사용자 지정(예: 롤아웃 구성)을 지원하는 반면 웹 사이트의 성능, 안정성 및 업그레이드 가능성에 대한 우수 사례는 사용자 지정을 최소화하는 것입니다.
* **거버넌스** 모델을 일찍 설정하고 그에 따라 사용자를 교육하여 성공을 보장합니다. 거버넌스 관점에서 가장 좋은 방법은 로컬 컨텐츠 제작자가&#x200B;**에서 다른 로컬 사용자 및 해당 Live Copy에 컨텐츠를 할당/연결하는 권한을 최소화하는 것입니다.** 이것은 제어되지 않고 체인화된 상속이 MSM 구조의 복잡성을 크게 증가시키고 성능과 안정성을 손상시킬 수 있기 때문입니다.

* 구조에 대한 계획이 있으면 컨텐츠 흐름, 자동화 및 거버넌스 - **프로토타입을 수행하고 라이브 구현을 시작하기 전에 시스템**&#x200B;을 철저히 테스트하십시오.
* **Adobe 컨설팅 및 선도적인 시스템 통합자**&#x200B;는 MSM을 사용하여 컨텐츠 자동화를 계획하고 구현하는 풍부한 경험을 보유하고 있으므로 MSM 프로젝트를 시작하고 전체 구현 중에 시작할 수 있습니다.

>[!NOTE]
>
>MSM 작업에 대한 자세한 내용은 기술 자료 문서를 참조하십시오.
>
>* [MSM FAQ](https://helpx.adobe.com/experience-manager/kb/index/msm_faq.html)
>* [MSM 문제 해결](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-msm-issues.html)

>



>[!NOTE]
>
>[참조 구성 요소](/help/sites-authoring/default-components-foundation.md#reference)를 사용하여 단일 페이지나 단락을 다시 사용할 수도 있습니다. 그러나 다음 사항에 주의하십시오.
>
>* MSM은 보다 유연하며, 동기화 내용과 시기를 미세 제어할 수 있습니다.
>* [이제 ](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html) 핵심 구성 요소가 기초 구성 요소보다 권장됩니다.

>



## Live Copy 소스 및 블루프린트 구성 {#live-copy-sources-and-blueprint-configurations}

Live Copy는 [일반 페이지](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) 또는 [블루프린트 구성](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)을 사용하여 만들 수 있습니다. 둘 다 유효한 사용 사례입니다.

블루프린트 구성을 사용하면 다음과 같은 이점이 있습니다.

* 작성자가 블루프린트에서 이 블루프린트에서 상속되는 Live Copy에 수정 사항을 푸시하기 위해 **롤아웃** 옵션을 사용할 수 있도록 허용합니다.
* 작성자가 **사이트 만들기**;를 사용하도록 허용언어를 쉽게 선택하고 live copy 구조를 구성할 수 있습니다.
* 블루프린트와 관계가 있는 Live Copy에 대한 기본 롤아웃 구성을 정의합니다.

블루프린트 구성을 참조하지 않는 경우 Live Copy 자체에서만 롤아웃을 시작할 수 있으므로 기본적으로 소스에서 컨텐츠를 가져옵니다.

Live Copy를 사용하여 새 사이트를 만들 때 전체 MSM 기능 세트의 가용성을 보장하기 위해 블루프린트 구성을 만드는 것이 좋습니다.

>[!NOTE]
>
>CUG 그룹을 Blueprint의 Live Copy로 롤아웃할 수 없습니다. Live Copy를 구성할 때 이를 계획하십시오.

## 구성 요소 및 컨테이너 동기화 {#components-and-container-synchronization}

일반적으로 구성 요소 동기화에 대한 MSM의 롤아웃 규칙은 다음과 같습니다.

* 구성 요소는 블루프린트에 포함된 모든 리소스 동기화를 롤아웃합니다.
* 컨테이너는 현재 리소스만 동기화합니다.

즉, 구성 요소가 합계로 처리되고 롤아웃 시 구성 요소 자체가 사용되고 모든 해당 하위 구성 요소가 블루프린트의 합계로 대체됩니다. 즉, 리소스가 이러한 구성 요소에 로컬로 추가되는 경우 롤아웃 시 블루프린트의 콘텐츠로 손실됩니다.

로컬에 추가된 구성 요소가 롤아웃에서 유지 관리되도록 구성 요소 중첩을 지원하려면 구성 요소를 컨테이너로 선언해야 합니다. 예를 들어, 기본 parsys는 컨테이너로 선언되므로 로컬에서 추가한 컨텐츠를 지원할 수 있습니다.

>[!NOTE]
>
>구성 요소에 속성 `cq:isContainer`을 추가하여 컨테이너로 지정합니다.

## 사이트 만들기 {#create-site}

AEM에는 Live Copy를 만드는 두 가지 주요 접근 방식이 있습니다.

* [Live Copy 생성](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   이 방법은 모든 페이지에서 Live Copy를 생성할 수 있도록 보다 일반적인 방법으로 간주할 수 있습니다. Live Copy의 컨텐츠 구조가 소스와 정확히 일치합니다.

* [사이트 만들기](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)

   이는 주로 다국어 구조로 웹 사이트를 제작하는 데 사용되는 보다 전문적인 접근 방법입니다.

다음은 사이트를 만들 때 고려해야 할 몇 가지 고려 사항입니다.

* 새 사이트를 만들려면 [블루프린트 구성](/help/sites-administering/msm-livecopy.md#managing-blueprint-configurations)이 필요합니다.
* 새 사이트에서 만들 언어 경로를 선택하려면 해당 언어 루트가 블루프린트(소스)에 있어야 합니다.
* [새 사이트가 Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)(**Create**&#x200B;을 사용한 다음 **사이트**)로 만들어지면 이 Live Copy의 처음 두 수준은 *얕은*&#x200B;입니다. 페이지의 하위 페이지는 라이브 관계에 속하지 않지만 트리거와 일치하는 라이브 관계가 발견되면 롤아웃이 계속 내려옵니다.

   이 방법은 다음을 방지할 수 있습니다.

   * 블루프린트에서 수동으로 언어 추가(첫 번째 수준 아래)
   * 언어 루트 바로 아래에 컨텐츠를 수동으로 추가,
   * 롤아웃 시 이 새 컨텐츠를 Live Copy로 자동으로 전달하지 않습니다.

## MSM 및 다국어 웹 사이트 {#msm-and-multilingual-websites}

MSM은 다음과 같은 두 가지 방법으로 다국어 웹 사이트를 만들 수 있습니다.

* 언어 마스터를 만들 때

   * MSM 자체 **는 컨텐츠 번역**&#x200B;을 제공하지 않지만, 기능을 수행하는 타사 번역 커넥터와 통합할 수 있습니다. 참고 사항:

      * MSM을 사용하면 페이지 및/또는 구성 요소 수준에서 상속을 취소할 수 있습니다. 이렇게 하면 다음 롤아웃 시 번역된 컨텐츠(Live Copy에서 블루프린트에서 아직 번역되지 않은 컨텐츠로)를 덮어쓰는 것을 방지할 수 있습니다.
      * 일부 타사 번역 커넥터는 MSM 상속을 자동화합니다.

         자세한 내용은 번역 서비스 공급자에게 문의하십시오.

      * 언어 마스터를 만들고 번역할 수 있는 또 다른 방법은 AEM 기본 제공 번역 통합 프레임워크와 함께 언어 사본을 사용하는 것입니다.

* 언어 마스터에서 컨텐츠를 롤아웃할 때.

   * 예를 들어, 프랑스어 마스터 부터 프랑스/프랑스어, 캐나다/프랑스어, 스위스/프랑스어 등 국가별 사이트에 이르기까지 다양한 국가에서 사용할 수 있습니다.

자세한 내용은 [다국어 사이트에 대한 콘텐츠 번역](/help/sites-administering/translation.md) 및 [번역 우수 사례](/help/sites-administering/tc-bp.md)를 참조하십시오.

## 구조 변경 및 롤아웃 {#structure-changes-and-rollouts}

블루프린트/소스 트리의 컨텐츠 구조에 대한 수정 사항은 Live Copy에 다르게 반영됩니다. 이것은 수정 유형에 따라 달라집니다.

* **** 블루프린트에서 새 페이지를 만들면 표준 롤아웃 구성을 사용하여 롤아웃 후 해당 페이지가 Live Copy에서 생성됩니다.

* **** 블루프린트에서 페이지를 삭제하면 표준 롤아웃 구성을 사용하여 롤아웃 후 Live Copy에서 해당 페이지가 삭제됩니다.

* **** 블루프린트에서 페이지를 이동해도  **** 표준 롤아웃 구성을 사용하여 롤아웃 후 Live Copy에서 해당 페이지가 이동되지 않습니다.

   * 이 동작의 이유는 페이지 이동이 암시적으로 페이지 삭제를 포함하기 때문입니다. 이로 인해 작성자가 페이지를 삭제하면 게시 시 해당 컨텐츠가 자동으로 비활성화되므로 게시 시 예기치 않은 동작이 발생할 수 있습니다. 링크, 책갈피 및 기타 항목과 같은 관련 항목에 노크 효과가 있을 수도 있습니다.
   * 각 Live Copy 페이지의 컨텐츠 상속은 블루프린트에서 해당 소스의 새 위치를 반영하도록 업데이트됩니다.
   * 블루프린트에서 Live Copy로 페이지 이동을 완전히 실현하려면 다음 우수 사례를 고려하십시오.

>[!NOTE]
>
>이 작업은 [롤아웃 시 트리거](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/msm-sync.html#rollout-triggers)에서만 작동합니다.

* 사용자 지정 롤아웃 구성을 만듭니다.

   * 이 새 구성에는 작업이 포함되어야 합니다.

      `PageMoveAction`

      이 구성에 다른 작업을 추가하지 마십시오.

* 새 구성을 배치합니다.

   * Live Copy에서 이전 위치에서 각 페이지를 삭제하는 동안 페이지 이동을 완전히 롤아웃하려면:

      * 표준 롤아웃 구성 전에 새로 만든 구성을 배치합니다.

         표준 롤아웃 구성에서는 이전 위치에서 페이지를 삭제하는 작업이 수행됩니다.
   * 각 페이지를 Live Copy에서 이전 위치에 유지한 채 페이지 이동을 롤아웃하려면(기본적으로 컨텐츠가 복제됨):

      * 표준 롤아웃 구성 뒤에 새로 만든 구성을 배치합니다.

         이렇게 하면 Live Copy에서 컨텐츠가 삭제되거나 게시에서 비활성화되지 않습니다.


## 역할 사용자 지정 {#customizing-rollouts}

MSM 롤아웃 구성은 사용자 지정이 매우 가능합니다. 롤아웃 자동화는 매우 큰 결과를 초래할 수 있습니다. 가장 좋은 방법으로서, 다음 예와 같이 전에 *매우*&#x200B;을 신중하게 계획해야 합니다.

* 롤아웃 자동화예를 들어, [onModify 트리거인](#onmodify)에서는
* 사용자 지정 [노드 유형/속성](#node-types-properties),
* 후속 워크플로우 시작
* 롤아웃의 일부로 컨텐츠 및/또는 활성화.

### onModify {#onmodify}

[롤아웃 트리거](/help/sites-administering/msm-sync.md#rollout-triggers) `onModify`를 사용할 때는 다음 사항을 고려해야 합니다.

* `onModify` 트리거로 롤아웃을 자동화하면 *모든* 페이지 수정 후 롤아웃을 트리거하므로 작성 성능에 부정적인 영향을 줄 수 있습니다.

* 롤아웃 결과는 다음과 같이 예상되는 결과와 다를 수 있습니다.

   * 결과 수정 이벤트의 순서를 지정할 수 없습니다.
   * 이벤트 기반 아키텍처는 롤아웃 관리자에 전달된 이벤트의 시퀀스를 보장할 수 없습니다.

* 이러한 롤아웃 구성을 사용하면 동일한 리소스의 동시 업데이트가 발생하는 경우 커밋 충돌이 발생할 수 있습니다.

따라서 자동 롤아웃 시작의 이점이 잠재적인 성능 문제를 능가하는 경우 *만*&#x200B;을 사용하는 것이 좋습니다.`onModify`

### 노드 유형/속성 {#node-types-properties}

다음 사항을 기억하십시오.

* MSM을 사용하면 롤아웃 작업을 사용자 정의할 수 있을 뿐만 아니라 롤아웃되는 노드 속성을 사용자 지정할 수도 있습니다. [MSM OSGi 구성을 사용하면 노드 유형](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization)이 소스에서 Live Copy로 복사되지 않도록 제외할 수 있습니다.

## 추가 정보 {#further-information}

이 페이지와 다음 페이지에서는 관련 문제를 다룹니다.

* [Live Copy 생성 및 동기화](/help/sites-administering/msm-livecopy.md)
* [Live Copy 개요 콘솔](/help/sites-administering/msm-livecopy-overview.md)
* [Live Copy 동기화 구성](/help/sites-administering/msm-sync.md)
* [MSM 롤아웃 충돌](/help/sites-administering/msm-rollout-conflicts.md)
