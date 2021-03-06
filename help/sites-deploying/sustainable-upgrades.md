---
title: 지속 가능한 업그레이드
seo-title: 지속 가능한 업그레이드
description: AEM 6.4에서 지속 가능한 업그레이드에 대해 알아봅니다.
seo-description: AEM 6.4에서 지속 가능한 업그레이드에 대해 알아봅니다.
uuid: 59d64af5-6ee0-40c8-b24a-c06848f70daa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 5ca8dd7a-4efd-493e-8022-d2f10903b0a2
feature: 업그레이드
exl-id: 765efa8d-1548-4db3-ba87-baa02075eaf6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# 지속 가능한 업그레이드{#sustainable-upgrades}

## 사용자 지정 프레임워크 {#customization-framework}

### 아키텍처(기능/인프라/컨텐츠/애플리케이션) {#architecture-functional-infrastructure-content-application}

Customization Framework 기능은 API와 같은 코드 또는 친숙한 업그레이드 이외의 콘텐츠(예: 오버레이)의 확장 불가능한 영역에서 위반을 줄이는 데 도움이 되도록 설계되었습니다.

사용자 지정 프레임워크에는 두 가지 구성 요소가 있습니다.**API Surface** 및 **컨텐츠 분류**.

#### API 서피스 {#api-surface}

이전 AEM 릴리스에서는 많은 API가 Uber Jar를 통해 노출되었습니다. 이러한 API 중 일부는 고객이 사용하기 위한 것이 아니라 번들 간에 AEM 기능을 지원하도록 노출되었습니다. 앞으로, Java API는 업그레이드 컨텍스트에서 사용할 안전한 API를 고객에게 표시하기 위해 공개 또는 비공개 로 표시됩니다. 기타 세부 사항은 다음과 같습니다.

* `Public`으로 표시된 Java API는 사용자 지정 구현 번들에서 사용 및 참조할 수 있습니다.

* 공용 API는 호환성 패키지 설치와 이전 버전과 호환됩니다.
* 호환성 패키지에는 이전 버전과의 호환성을 보장하기 위해 호환성 Uber JAR가 포함됩니다
* `Private`으로 표시된 Java API는 AEM 내부 번들에서만 사용하기 위한 것으로, 사용자 지정 번들에서는 사용할 수 없습니다.

>[!NOTE]
>
>이 컨텍스트에서 `Private` 및 `Public`의 개념은 공용 및 개인 클래스의 Java 개념과 혼동하면 안 됩니다.

![image2018-2-12_23-52-48](assets/image2018-2-12_23-52-48.png)

#### 컨텐츠 분류 {#content-classifications}

AEM에서는 고객이 AEM 기능을 확장 및 사용자 지정할 수 있도록 오버레이 및 Sling Resource Merger의 주요 기능을 오랫동안 사용해왔습니다. AEM 콘솔 및 UI를 구동하는 사전 정의된 기능은 **/libs**&#x200B;에 저장됩니다. 고객은 **/libs** 아래에 있는 어떤 것도 수정할 수 없지만 **/apps** 아래에 추가 컨텐츠를 추가하여 **/libs**&#x200B;에 정의된 기능을 오버레이하고 확장할 수 있습니다(자세한 내용은 오버레이로 개발 참조). 따라서 **/libs**&#x200B;의 컨텐츠로 AEM을 업그레이드할 때 오버레이 기능이 예기치 않은 방식으로 중단되는 문제가 계속 발생할 수 있습니다. 또한 고객은 `sling:resourceSuperType`을 통해 상속을 통해 AEM 구성 요소를 확장하거나 sling:resourceType을 통해 직접 **/libs**&#x200B;의 구성 요소를 참조할 수도 있습니다. 참조 및 재정의 사용 사례에서 유사한 업그레이드 문제가 발생할 수 있습니다.

고객이 **/libs**&#x200B;의 어떤 영역을 안전하게 사용하고 **/libs**&#x200B;의 컨텐츠를 다음 mixin으로 분류했는지 보다 안전하고 쉽게 이해할 수 있도록 하기 위해.

* **공개(granite:PublicArea)**  - 노드를 오버레이하거나 상속하거나 직접 사용할 수 있도록( `sling:resourceSuperType`) public으로 정의합니다( `sling:resourceType`). Public으로 표시된 /libs 아래의 노드는 호환성 패키지를 추가하여 안전하게 업그레이드할 수 있습니다. 일반적으로 고객은 Public으로 표시된 노드만 활용해야 합니다.

* **abstract(granite:AbstractArea)**  - 노드를 추상 노드로 정의합니다. 노드를 오버레이하거나 상속할 수 있습니다( `sling:resourceSupertype`). 그러나 직접 사용해서는 안 됩니다( `sling:resourceType`).

* **최종(granite:FinalArea)**  - 노드를 최종본으로 정의합니다. 최종으로 분류된 노드는 오버레이하거나 상속할 수 없습니다. 최종 노드는 `sling:resourceType`을 통해 직접 사용할 수 있습니다. 최종 노드 아래의 하위 노드는 기본적으로 내부로 간주됩니다

* **내부(granite:InternalArea)**  - 노드를 내부로 정의합니다. 내부로 분류된 노드는 오버레이, 상속 또는 직접 사용할 수 없습니다. 이러한 노드는 AEM의 내부 기능만을 위한 것입니다

* **주석 없음**  - 노드는 트리 계층 구조를 기반으로 분류를 상속합니다. / 루트는 기본적으로 공개입니다. **Internal 또는 Final으로 분류된 상위가 있는 노드도 Internal로 처리됩니다.**

>[!NOTE]
>
>이러한 정책은 Sling 검색 경로 기반 메커니즘에만 적용됩니다. 클라이언트측 라이브러리와 같은 **/libs**&#x200B;의 다른 영역은 `Internal` 로 표시될 수 있지만, 여전히 표준 clientlib 포함과 함께 사용할 수 있습니다. 고객은 이러한 경우에 내부 분류를 계속 존중해야 합니다.

#### CRXDE Lite 컨텐츠 유형 표시기 {#crxde-lite-content-type-indicators}

CRXDE Lite에 적용된 Mixin은 `INTERNAL`으로 표시된 컨텐츠 노드와 트리를 회색으로 표시합니다. `FINAL`의 경우 아이콘만 회색으로 표시됩니다. 이러한 노드의 하위 노드도 회색으로 표시됩니다. 이 두 경우 모두 오버레이 노드 기능이 비활성화됩니다.

**공용**

![image2018-2-8_23-34-5](assets/image2018-2-8_23-34-5.png)

**최종**

![image2018-2-8_23-34-56](assets/image2018-2-8_23-34-56.png)

**내부**

![image2018-2-8_23-38-23](assets/image2018-2-8_23-38-23.png)

**콘텐츠 상태 확인**

AEM 6.4는 컨텐츠 분류와 일치하지 않는 방식으로 오버레이되거나 참조된 컨텐츠를 사용하는 경우 고객에게 경고하기 위한 상태 확인과 함께 제공됩니다.

**Sling/Granite Content Access Check**&#x200B;는 고객 코드가 AEM에서 보호된 노드에 잘못 액세스하고 있는지 확인하기 위해 저장소를 모니터링하는 새로운 상태 확인입니다.

이 작업은 **/apps**&#x200B;을 스캔하고 일반적으로 완료하는 데 몇 초 걸립니다.

이 새 상태 확인에 액세스하려면 다음을 수행해야 합니다.

1. AEM 홈 화면에서 **도구 > 작업 > 상태 보고서**&#x200B;로 이동합니다.
1. 아래 표시된 대로 **Sling/Granite Content Access Check**&#x200B;를 클릭합니다.

   ![screen_shot_2017-12-14at55648pm](assets/screen_shot_2017-12-14at55648pm.png)

검사가 완료되면, 잘못된 참조 중인 보호된 노드의 최종 사용자에게 경고 목록이 표시됩니다.

![스크린샷-2018-2-5healthreports](assets/screenshot-2018-2-5healthreports.png)

위반을 수정한 후 녹색 상태로 돌아갑니다.

![스크린샷-2018-2-5healthreports-violations](assets/screenshot-2018-2-5healthreports-violations.png)

상태 확인은 모든 Sling 검색 경로에서 오버레이 또는 리소스 유형이 사용될 때마다 비동기적으로 확인하는 백그라운드 서비스에서 수집한 정보를 표시합니다. 컨텐츠 혼합을 잘못 사용하면 위반을 보고합니다.
