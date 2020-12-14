---
title: AEM을 사용하여 자산을 관리하는 모범 사례
description: AEM Assets 배포 및 자산 인제스트 및 처리 기능에 따라 로드 중인 시스템 안정성과 성능을 향상시키는 우수 사례를 식별하고 준수합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# AEM Assets {#best-practices-for-assets}에 대한 우수 사례

Adobe Experience Manager(AEM) 자산은 콘텐츠 속도를 높여 비즈니스 목표 달성에 기여하는 고품질의 디지털 마케팅 경험을 전달하는 데 중요한 역할을 합니다. AEM Assets 내에서 많은 양의 에셋을 사용하여 작업하거나 비디오 및 다이내믹 미디어를 비롯한 다양한 에셋을 정기적으로/정기적으로 업로드하는 경우 시스템 효율성을 높이기 위해 디지털 에셋 관리 경험을 최적화하는 것이 중요합니다.

조직을 위해 AEM Assets을 배치한 방식과 자산 수집, 변환 생성 및 메타데이터 추출에 사용하는 기능에 따라 다양한 영역에서 모범 사례를 식별하고 이를 준수함으로써 로드 중인 시스템 안정성과 성능을 크게 향상시킬 수 있습니다.

다음 가이드를 검토하여 필요에 따라 엔터프라이즈 에셋 관리 시스템을 구축하고 관리하는 데 필요한 지식과 툴을 사용할 수 있습니다.

* [자산 성능 조정 ](performance-tuning-guidelines.md)
안내서실시간 진행 후에도 구현 시 언제든지 따라할 수 있는 최상의 작업 방법을 제공하여 시스템을 최대한 활용할 수 있습니다.
* [자산 크기 ](assets-sizing-guide.md)
조정 안내서자산 구현에 대한 견적을 작성할 때 자산 저장소, CPU, 메모리, IO 및 네트워크 처리량에 대해 사용할 수 있는 충분한 리소스가 있는지 확인하는 것이 중요합니다. 이러한 항목 중 많은 항목의 크기를 조정하려면 시스템에 로드되는 자산 수를 이해해야 합니다. 이 안내서에는 크기 조정 도구는 물론 AEM Assets 배포에 필요한 인프라 및 리소스를 측정하기 위한 효율적인 지표를 결정하는 데 도움이 되는 우수 사례가 포함되어 있습니다.
* [자산 마이그레이션 ](assets-migration-guide.md)
안내서자산을 기존 시스템에서 AEM Assets으로 마이그레이션하려면 마이그레이션 프로세스를 간소화하기 위한 몇 가지 단계를 고려해야 합니다. 마이그레이션 안내서에는 단계별로 AEM으로 에셋을 가져오는 데 수행하는 작업에 대한 우수 사례가 포함되어 있습니다. 여기에는 메타데이터 적용, 변환 생성 및 배포를 게시할 자산 활성화 등이 포함됩니다.
* [자산 네트워크 ](assets-network-considerations.md)
고려 사항AEM 배포를 처리할 때 네트워크 토폴로지를 이해하는 것은 네트워크 성능을 이해하고 선택 지점을 식별하며 예상되는 사용자 경험을 설명하는 데 중요합니다. 자산 네트워크 고려 사항 문서에서는 AEM 자산 배포를 디자인할 때 네트워크 고려 사항을 설명합니다.
* [에셋 모니터링 ](assets-monitoring-best-practices.md)
안내서 AEM 배포를 배포한 후 일반적으로 특정 작업 및 시스템을 모니터링하여 시스템의 무결성과 운영 효율성을 확보해야 합니다. 모니터링 안내서에는 시스템의 다양한 측면을 모니터링하기 위한 모범 사례가 포함되어 있습니다.
* (사용되지 않음) [자산 오프로딩 안내서](assets-offloading-best-practices.md)
AEM Assets에서 대용량 파일 및 실행 워크플로우를 처리할 때 상당한 CPU, 메모리 및 I/O 리소스를 사용할 수 있습니다. 이러한 작업을 오프로딩하면 CPU, 메모리 및 IO 오버헤드가 줄어듭니다. 자산 오프로딩 안내서에는 권장되는 사용 사례와 자산 오프로딩에 대한 우수 사례가 포함되어 있습니다.
* [AEM 데스크탑 앱 모범 ](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
사례AEM 데스크탑 앱은 데스크탑에 디지털 에셋 관리(DAM) 솔루션을 연결하므로 데스크탑에서 바로 AEM 웹 UI에서 사용할 수 있는 파일을 열 수 있습니다. AEM 데스크탑 앱의 사용이 간편한 워크플로우는 데스크탑 운영 체제에서 제공하는 네트워크 공유 기술을 통해 활성화됩니다. 이 안내서에서는 주요 기능 및 AEM 데스크탑 앱의 권장 사용에 대해 설명합니다.
* [AEM 및 Creative Cloud 통합 모범 사례](aem-cc-integration-best-practices.md)
는 다양한 방법으로 AEM 배포를 Creative Cloud과 통합할 수 있습니다. 통합 및 자산 전송 워크플로우를 간소화하기 위한 몇 가지 모범 사례를 통해 효율성을 극대화할 수 있습니다. 이 안내서에는 AEM Assets과 Adobe Creative Cloud 통합에 대한 우수 사례가 포함되어 있습니다.
* (사용되지 않음) [AEM에서 Creative Cloud 폴더 공유 모범 사례](aem-cc-folder-sharing-best-practices.md)
DAM의 사용자가 Creative Cloud(CC) 사용자와 폴더를 공유할 수 있도록 AEM을 구성하여 Creative Cloud 에셋 서비스의 공유 폴더로 사용할 수 있습니다. 이 기능을 사용하여 크리에이티브 팀과 DAM 사용자 간에 파일을 교환할 수 있습니다. 이 안내서에서는 AEM과 Creative Cloud 폴더 공유 기능을 활용하기 위한 모범 사례에 대해 설명합니다.
