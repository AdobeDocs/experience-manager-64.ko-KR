---
title: MSM 롤아웃 충돌
seo-title: MSM 롤아웃 충돌
description: 다중 사이트 관리자 롤아웃 충돌을 처리하는 방법을 알아봅니다.
seo-description: 다중 사이트 관리자 롤아웃 충돌을 처리하는 방법을 알아봅니다.
uuid: 7a640905-aae2-498e-b95c-2c73008fa1cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 16db5334-604f-44e2-9993-10d683dee5bb
feature: 다중 사이트 관리자
exl-id: 636b28aa-0806-4250-ad3b-a72be704af1f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# MSM 롤아웃 충돌{#msm-rollout-conflicts}

블루프린트 분기와 종속 Live Copy 분기 모두에서 페이지 이름이 동일한 새 페이지를 만들면 충돌이 발생할 수 있습니다.

이러한 충돌은 롤아웃 시 처리하고 해결해야 합니다.

## 충돌 처리 {#conflict-handling}

페이지가 충돌하는 경우(블루프린트 및 Live Copy 분기에) MSM을 사용하여 페이지를 처리하는 방법을 정의할 수 있습니다(또는 있더라도).

롤아웃이 차단되지 않도록 하기 위해 가능한 정의는 다음과 같습니다.

* 롤아웃 중에 우선 순위가 있는 페이지(블루프린트 또는 live copy)
* 어떤 페이지의 이름을 바꿀(및 방법),
* 게시된 모든 컨텐츠에 미치는 영향

   AEM(즉시 사용 가능)의 기본 동작은 게시된 컨텐츠는 영향을 받지 않습니다. 따라서 Live Copy 분기에서 수동으로 만든 페이지가 게시되었더라도 충돌 처리 및 롤아웃 후에도 해당 컨텐츠가 계속 게시됩니다.

표준 기능 외에 사용자 지정된 충돌 처리기를 추가하여 다른 규칙을 구현할 수 있습니다. 작업을 개별 프로세스로 게시할 수도 있습니다.

### 예제 시나리오 {#example-scenario}

다음 섹션에서는 블루프린트와 Live Copy 분기(수동으로 생성됨)에서 만들어진 새 페이지 `b`의 예를 사용하여 다양한 충돌 해결 방법을 보여줍니다.

* 블루프린트:`/b`

   마스터 페이지하위 페이지 1개, bp-level-1 사용.

* live copy:`/b`

   Live Copy 분기에서 수동으로 만든 페이지입니다.1개의 하위 페이지가 있는 경우 `lc-level-1`

   * 하위 페이지와 함께 `/b` 게시 시 활성화됩니다.

**롤아웃 전**

<table> 
 <tbody> 
  <tr> 
   <td><strong>롤아웃 전 블루프린트</strong></td> 
   <td><strong>롤아웃 전 live copy</strong></td> 
   <td><strong>롤아웃 전 게시</strong></td> 
  </tr> 
  <tr> 
   <td><code>b</code> <br /> (블루프린트 분기에 만들어짐, 롤아웃 준비)<br /> </td> 
   <td><code>b</code> <br /> (live copy 분기에 수동으로 생성됨)<br /> </td> 
   <td><code>b</code> <br /> (live copy 분기에 수동으로 만든 페이지 b의 컨텐츠가 포함되어 있습니다.)</td> 
  </tr> 
  <tr> 
   <td><code> /bp-level-1</code></td> 
   <td><code> /lc-level-1</code> <br /> (live copy 분기에 수동으로 생성됨)<br /> </td> 
   <td><code> /lc-level-1</code> <br /> (live copy 분기에 수동으로 만든 페이지<br /> 하위 수준-1의 컨텐츠가 포함되어 있습니다.)</td> 
  </tr> 
 </tbody> 
</table>

## 롤아웃 관리자 및 충돌 처리 {#rollout-manager-and-conflict-handling}

롤아웃 관리자를 사용하여 충돌 관리를 활성화하거나 비활성화할 수 있습니다.

이 작업은 **일 CQ WCM 롤아웃 관리자**&#x200B;의 [OSGi 구성](/help/sites-deploying/configuring-osgi.md)을 사용하여 수행됩니다.

* **수동으로 만든 페이지와 충돌 처리**:

   ( `rolloutmgr.conflicthandling.enabled`)

   롤아웃 관리자가 블루프린트에 있는 이름으로 Live Copy에서 만든 페이지의 충돌을 처리해야 하는 경우 true로 설정합니다.

AEM에는 충돌 관리가 비활성화되었을 때 [사전 정의된 동작이 있습니다](#behavior-when-conflict-handling-deactivated).

## 충돌 처리기 {#conflict-handlers}

AEM에서는 충돌 핸들러를 사용하여 블루프린트에서 Live Copy로 컨텐츠를 롤아웃할 때 존재하는 페이지 충돌을 해결합니다. 페이지 이름 바꾸기는 이러한 충돌을 해결하는 단일 방법입니다. 두 개 이상의 충돌 처리기를 작동하여 다양한 동작을 선택할 수 있습니다.

AEM은 다음을 제공합니다.

* [기본 충돌 처리기](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* [사용자 지정된 처리기](#customized-handlers)를 구현할 수 있습니다.
* 각 개별 처리기의 우선 순위를 설정할 수 있는 서비스 등급 메커니즘입니다. 순위가 가장 높은 서비스가 사용됩니다.

### 기본 충돌 처리기 {#default-conflict-handler}

기본 충돌 처리기:

* 를 `ResourceNameRolloutConflictHandler`이라고 합니다.

* 이 핸들러를 사용하면 블루프린트 페이지에 우선 순위가 지정됩니다.
* 이 처리기의 서비스 등급이 낮습니다(&quot;예:사용자 지정된 처리기에 더 높은 등급이 필요하다는 가정 하에 `service.ranking` 속성의 기본값 아래에 표시됩니다. 그러나 필요할 때 등급을 유연하게 사용하기 위한 절대 최소는 아닙니다.

이 충돌 처리기가 블루프린트에 우선합니다. Live Copy 페이지 `/b`이(가) Live Copy 분기 내에서 `/b_msm_moved`(으)로 이동되었습니다.

* live copy:`/b`

   가 `/b_msm_moved`(Live Copy 내)로 이동됩니다. 이렇게 하면 백업 기능이 수행되며 컨텐츠가 손실되지 않습니다.

   * `lc-level-1` 가 이동되지 않습니다.

* 블루프린트:`/b`

   Live Copy 페이지 `/b`에 롤아웃됩니다.

   * `bp-level-1` 가 livecopy로 롤아웃됩니다.

**롤아웃 후**

<table> 
 <tbody> 
  <tr> 
   <td><strong>롤아웃 후 블루프린트</strong></td> 
   <td><strong>롤아웃 후 live copy</strong><br /> </td> 
   <td></td>
   <td><strong>롤아웃 후 live copy</strong><br /> <br /> <br /> </td> 
   <td><strong>롤아웃 후 게시</strong><br /> <br /> </td> 
  </tr> 
  <tr> 
   <td><code>b</code></td> 
   <td><code>b</code> <br /> (롤아웃된 블루프린트 페이지 b의 컨텐츠가 있음)<br /> </td> 
   <td></td>
   <td><code>b_msm_moved</code> <br /> (live copy 분기에서 수동으로 만든 페이지 b의 컨텐츠가 있음)</td> 
   <td><code>b</code> <br /> 변경 금지는 live copy 분기에서 수동으로 만들어졌고 이제 b_msm_moved)인 원래 페이지 b의 컨텐츠를 포함합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td><code> /bp-level-1</code></td> 
   <td><code class="code"> /bp-level-1</code></td> 
   <td><code> /lc-level-1</code> <br /> (변경 없음)</td> 
   <td><code> </code></td> 
   <td><code> /lc-level-1</code> <br /> (변경 없음)</td> 
  </tr> 
 </tbody> 
</table>

### 사용자 지정된 처리기 {#customized-handlers}

사용자 지정된 충돌 처리기를 통해 고유한 규칙을 구현할 수 있습니다. 서비스 등급 메커니즘을 사용하여 다른 핸들러와 상호 작용하는 방법을 정의할 수도 있습니다.

사용자 지정된 충돌 처리기는 다음 작업을 수행할 수 있습니다.

* 필요에 따라 이름을 지정합니다. &quot;
* 필요에 따라 개발/구성예를 들어 live copy 페이지에 우선순위가 지정되도록 핸들러를 개발할 수 있습니다.
* [OSGi 구성](/help/sites-deploying/configuring-osgi.md);특히

   * **서비스 등급**:

      다른 충돌 핸들러( `service.ranking`)와 관련된 순서를 정의합니다.

      기본값은 0입니다.

### 충돌이 비활성화된 {#behavior-when-conflict-handling-deactivated} 처리 시 동작

수동으로 [충돌 처리 비활성화](#rollout-manager-and-conflict-handling)를 수행하면 AEM에서 충돌하는 페이지에 대해 작업을 수행하지 않습니다(충돌하지 않은 페이지는 예상대로 롤아웃됩니다.).

>[!CAUTION]
>
>AEM에서는 이 동작을 명시적으로 구성해야 하므로 충돌이 무시되고 있음을 표시하지 않으므로 이 동작이 필수 동작이라고 가정합니다.

이 경우 Live Copy가 효과적으로 우선합니다. 블루프린트 페이지 `/b`은 복사되지 않고 Live Copy 페이지 `/b`은(는) 그대로 유지됩니다.

* 블루프린트:`/b`

   은 전혀 복사되지 않지만 무시됩니다.

* live copy:`/b`

   계속 똑같아

<table> 
 <caption>
   롤아웃 후 
 </caption> 
 <tbody> 
  <tr> 
   <td><strong>롤아웃 후 블루프린트</strong></td> 
   <td><strong>롤아웃 후 live copy</strong><br /> <br /> <br /> </td> 
   <td><strong>롤아웃 후 게시</strong><br /> <br /> </td> 
  </tr> 
  <tr> 
   <td><code>b</code></td> 
   <td><code>b</code> <br /> 변경 금지에는 live copy 분기에서 수동으로 만든 페이지 b의 컨텐츠가 있습니다.</td> 
   <td><code>b</code> <br /> 변경 금지live copy 분기에 수동으로 만든 페이지 b의 컨텐츠를 포함합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td><code> /bp-level-1</code> </td> 
   <td><code> /lc-level-1</code> <br /> (변경 없음)</td> 
   <td><code> /lc-level-1</code> <br /> (변경 없음)</td> 
  </tr> 
 </tbody> 
</table>

### 서비스 등급 {#service-rankings}

[OSGi](https://www.osgi.org/) 서비스 등급을 사용하여 개별 충돌 처리기의 우선순위를 정의할 수 있습니다.
