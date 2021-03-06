---
title: AEM 6.4로 업그레이드
seo-title: AEM 6.4로 업그레이드
description: 이전 AEM 설치를 AEM 6.4로 업그레이드하는 기본 사항에 대해 알아봅니다.
seo-description: 이전 AEM 설치를 AEM 6.4로 업그레이드하는 기본 사항에 대해 알아봅니다.
uuid: aa878528-5161-4df3-9fed-cc779fb6bdbe
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 81ceb91d-039e-45f0-9b0c-b8233901dea8
targetaudience: target-audience upgrader
feature: 업그레이드
exl-id: 791da16c-bf2c-47a9-86a4-0a601a1b017e
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 3%

---

# AEM 6.4로 업그레이드{#upgrading-to-aem}

이 섹션에서는 AEM 설치를 AEM 6.4로 업그레이드하는 내용을 다룹니다.

* [업그레이드 계획](/help/sites-deploying/upgrade-planning.md)
* [패턴 탐지기를 사용한 업그레이드 복잡성 평가](/help/sites-deploying/pattern-detector.md)
* [AEM 6.4의 이전 버전과의 호환성](/help/sites-deploying/backward-compatibility.md)
* [업그레이드 프로시저](/help/sites-deploying/upgrade-procedure.md)
* [코드 및 사용자 지정 업그레이드](/help/sites-deploying/upgrading-code-and-customizations.md)
* [업그레이드 전 유지 관리 작업](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [즉석 업그레이드 수행](/help/sites-deploying/in-place-upgrade.md)
* [업그레이드 후 확인 및 문제 해결](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [지속 가능한 업그레이드](/help/sites-deploying/sustainable-upgrades.md)
* [레이지 컨텐츠 마이그레이션](/help/sites-deploying/lazy-content-migration.md)
* [AEM 6.4의 저장소 구조 변경](/help/sites-deploying/repository-restructuring.md)

이러한 절차에 포함된 AEM 인스턴스를 보다 쉽게 참조할 수 있도록 이 문서 전체에서 다음 용어가 사용됩니다.

* *source* 인스턴스는 업그레이드할 AEM 인스턴스입니다.
* *target* 인스턴스는 업그레이드할 인스턴스입니다.

>[!NOTE]
>
>업그레이드의 신뢰성을 향상시키기 위한 노력의 일환으로 AEM 6.4는 포괄적인 저장소 재구성을 완료했습니다. 새 구조와 정렬하는 방법에 대한 자세한 내용은 AEM 6.4의 저장소 구조 변경](/help/sites-deploying/repository-restructuring.md)을 참조하십시오[

## 변경 사항{#what-has-changed}

다음은 AEM의 최근 여러 릴리스에 대한 참고 사항의 주요 변경 사항입니다.

AEM 6.0에서는 새로운 Jackrabbit Oak 저장소를 도입했습니다. 지속성 관리자는 [Micro Kernels](/help/sites-deploying/recommended-deploys.md)로 대체되었습니다. 버전 6.1부터 CRX2는 더 이상 지원되지 않습니다. CRX2 리포지토리를 5.6.1 인스턴스에서 마이그레이션하려면 crx2oak라는 마이그레이션 도구를 실행해야 합니다. 자세한 내용은 [CRX2OAK 마이그레이션 도구 사용](/help/sites-deploying/using-crx2oak.md)을 참조하십시오.

Assets Insights를 사용하고 AEM 6.2 이전 버전에서 업그레이드하는 경우 자산을 마이그레이션하고 JMX Bean을 통해 생성된 ID를 가져야 합니다. 내부 테스트에서는 TarMK 환경의 125K 자산이 한 시간 후에 마이그레이션되었지만 결과는 다를 수 있습니다.

AEM 6.3에서는 TarMK 구현의 기반인 `SegmentNodeStore`에 대한 새 형식을 도입했습니다. AEM 6.3 이전 버전에서 업그레이드하는 경우 시스템 다운타임을 포함하여 업그레이드의 일부로 저장소 마이그레이션이 필요합니다.

Adobe 엔지니어링 팀은 이것을 약 20분 정도 예상하고 있습니다. 재색인화는 필요하지 않습니다. 또한 새 저장소 형식과 함께 작동하도록 crx2oak 도구의 새 버전이 릴리스되었습니다.

**AEM 6.3에서 AEM 6.4로 업그레이드하는 경우 이 마이그레이션이 필요하지 않습니다.**

업그레이드 전 유지 관리 작업은 자동화를 지원하도록 최적화되었습니다.

crx2oak 도구 명령줄 사용 옵션이 자동화 친화적이며 더 많은 업그레이드 경로를 지원하도록 변경되었습니다.

업그레이드 후 확인 작업도 자동화되었습니다.

이제 주기적으로 수정 버전 및 데이터 저장소 가비지 수집을 수집하여 정기적으로 수행해야 하는 일상적인 유지 관리 작업입니다. AEM 6.3의 도입으로 Adobe은 온라인 개정 정리를 지원하고 권장합니다. 이러한 작업을 구성하는 방법에 대한 자세한 내용은 [개정 정리](/help/sites-deploying/revision-cleanup.md) 를 참조하십시오.

**AEM 6.4** 에서는 업그레이드  [계획](/help/sites-deploying/pattern-detector.md) 을 시작할 때 업그레이드의 복잡도를 평가하기 위한 패턴 탐지기를 소개합니다. 6.4는 기능의 [이전 버전과의 호환성](/help/sites-deploying/backward-compatibility.md)에 중점을 둡니다. 마지막으로, [지속 가능한 업그레이드](/help/sites-deploying/sustainable-upgrades.md)에 대한 우수 사례가 추가되었습니다.

최신 AEM 버전에서 변경된 내용에 대한 자세한 내용은 전체 릴리스 노트를 참조하십시오.

* [https://helpx.adobe.com/kr/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/kr/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/kr/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/kr/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/kr/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/kr/experience-manager/6-4/release-notes.html)

## 업그레이드 개요 {#upgrade-overview}

AEM 업그레이드는 여러 단계로, 때로는 여러 달에 걸쳐 수행됩니다. 업그레이드 프로젝트에 포함된 내용과 이 설명서에 포함된 콘텐츠에 대한 개요로 다음 요약이 제공되었습니다.

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## 6.4 업그레이드 개선 사항이 있는 업그레이드 흐름 {#upgrade-overview-1}

아래 다이어그램은 업그레이드 방법을 강조 표시하는 전체 권장 흐름을 캡처합니다. 우리가 도입한 새로운 기능들을 참고하세요. 업그레이드는 생성된 보고서의 패턴을 기반으로 AEM 6.4와의 호환성을 위해 수행할 경로를 결정할 수 있도록 해야 하는 패턴 탐지기([패턴 탐지기 업그레이드 복잡성 평가](/help/sites-deploying/pattern-detector.md) 참조)로 시작해야 합니다.

6.4에는 모든 새로운 기능을 이전 버전과 호환하는 데 큰 중점을 두었지만, 일부 이전 버전과의 호환성 문제가 여전히 표시되는 경우 호환성 모드를 통해 사용자 지정 코드를 6.4와 준수하도록 개발을 일시적으로 연기할 수 있습니다. 이 접근 방식을 사용하면 업그레이드 직후 개발 노력을 방지할 수 있습니다(AEM 6.4](/help/sites-deploying/backward-compatibility.md)이전 버전과의 호환성 참조).[

마지막으로, 6.4 개발 주기에서 지속 가능 업그레이드([지속 가능 업그레이드](/help/sites-deploying/sustainable-upgrades.md) 참조)에 도입된 기능을 사용하면 Best Practice를 통해 향후 업그레이드를 보다 효율적이고 원활하게 수행할 수 있습니다.

![6_4_upgrade_overviewflows-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)
