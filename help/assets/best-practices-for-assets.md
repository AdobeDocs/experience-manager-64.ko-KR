---
title: AEM을 사용하여 자산을 관리하는 우수 사례
description: AEM Assets 배포 및 자산을 수집 및 처리하는 데 사용되는 기능에 따라 로드 중인 시스템 안정성 및 성능을 향상시키는 우수 사례를 식별하고 따릅니다.
contentOwner: AG
feature: 자산 관리
role: Architect,Administrator
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# AEM Assets {#best-practices-for-assets} 우수 사례

Adobe Experience Manager(AEM) Assets는 컨텐츠 속도를 높여 비즈니스 목표 달성에 기여하는 고품질의 디지털 마케팅 경험을 제공하는데 중요한 부분입니다. AEM Assets 내에서 많은 자산을 사용하여 작업하거나 비디오 및 다이내믹 미디어를 포함한 다양한 자산을 정기적으로/정기적으로 업로드하는 경우 시스템 효율성을 위해 디지털 자산 관리 경험을 최적화하는 것이 중요합니다.

조직을 위해 AEM Assets을 배치한 방법과 자산 수집, 표현물 생성 및 메타데이터 추출과 관련하여 사용하는 기능에 따라 다양한 영역에서 우수 사례를 식별하고 준수하면 로드 중인 시스템 안정성 및 성능이 크게 향상됩니다.

다음 안내서를 검토한 후에는 필요에 따라 엔터프라이즈 자산 관리 시스템을 구축하고 관리하는 지식과 도구가 제공됩니다.

* [자산 성능 조정 ](performance-tuning-guidelines.md)
안내서라이브 상태가 된 후에도 구현 중 어느 시점에서 시스템을 최대한 활용할 수 있는 모범 사례 세트가 포함되어 있습니다.
* [자산 크기 ](assets-sizing-guide.md)
조정 안내서자산 구현에 대한 예측을 작성할 때 자산 저장, CPU, 메모리, IO 및 네트워크 처리량 측면에서 사용 가능한 리소스가 충분한지 확인하는 것이 중요합니다. 이러한 항목 중 많은 항목의 크기를 조정하려면 시스템에 로드되는 자산의 수를 이해해야 합니다. 이 안내서에는 크기 조정 도구뿐만 아니라 AEM Assets 배포에 필요한 인프라 및 리소스를 추정하는 효율적인 지표를 결정하는 데 도움이 되는 모범 사례가 포함되어 있습니다.
* [자산 마이그레이션 ](assets-migration-guide.md)
안내서 기존 시스템에서 AEM Assets으로 자산을 마이그레이션하려면 마이그레이션 프로세스를 간소화하는 몇 가지 단계를 고려해야 합니다. 마이그레이션 안내서에는 자산을 단계별로 AEM에 가져오기 위해 수행하는 작업에 대한 모범 사례가 포함되어 있습니다. 여기에는 메타데이터 적용, 변환 생성 및 배포를 게시할 자산 활성화 등이 포함됩니다.
* [자산 네트워크 ](assets-network-considerations.md)
고려 사항 AEM 배포를 처리할 때 네트워크 성능을 이해하고 선택 사항을 식별하며 예상 사용자 경험을 설명하는 데 네트워크 토폴로지를 이해하는 것이 중요합니다. 자산 네트워크 고려 사항 문서에서는 AEM 자산 배포를 디자인할 때 네트워크 고려 사항에 대해 설명합니다.
* [자산 모니터링 ](assets-monitoring-best-practices.md)
안내서AEM 배포이 배포되면 일반적으로 특정 작업 및 시스템을 모니터링하여 시스템의 무결성과 작업 효율성을 확인해야 합니다. 모니터링 안내서에는 시스템의 다양한 측면을 모니터링하기 위한 모범 사례가 포함되어 있습니다.
* (사용하지 않음) [Assets 오프로딩 안내서](assets-offloading-best-practices.md)
대용량 파일을 처리하고 AEM Assets에서 워크플로우를 실행하면 상당한 CPU, 메모리 및 I/O 리소스를 사용할 수 있습니다. 이러한 작업을 업로드하면 CPU, 메모리 및 IO 오버헤드가 줄어들 수 있습니다. Assets 오프로딩 안내서에는 Assets 오프로딩에 대한 권장 사용 사례 및 우수 사례가 포함되어 있습니다.
* [AEM 데스크탑 앱 모범 ](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
사례AEM 데스크탑 앱은 데스크탑에 DAM(디지털 자산 관리) 솔루션을 연결하므로 데스크탑에서 바로 AEM 웹 UI에서 사용할 수 있는 파일을 열 수 있습니다. AEM 데스크탑 앱의 사용하기 쉬운 워크플로우는 데스크탑 운영 체제에서 제공하는 네트워크 공유 기술을 사용하여 활성화됩니다. 이 안내서에서는 주요 기능 및 AEM 데스크탑 앱의 권장 사용에 대해 설명합니다.
* [AEM 및 Creative Cloud 통합 우수 ](aem-cc-integration-best-practices.md)
사례AEM 배포를 여러 가지 방법으로 Creative Cloud과 통합할 수 있습니다. 통합 및 자산 전송 워크플로우를 간소화하는 몇 가지 모범 사례를 따르면 최대 효율성을 달성할 수 있습니다. 이 안내서에는 AEM Assets과 Adobe Creative Cloud의 통합에 대한 모범 사례가 포함되어 있습니다.
* (사용하지 않음) [AEM에서 Creative Cloud 폴더 공유 우수 사례](aem-cc-folder-sharing-best-practices.md)
DAM의 사용자가 Creative Cloud(CC) 사용자와 폴더를 공유할 수 있도록 AEM을 구성하여 Creative Cloud Assets 서비스에서 공유 폴더로 사용할 수 있습니다. 이 기능은 크리에이티브 팀과 DAM 사용자 간에 파일을 교환하는 데 사용할 수 있습니다. 이 안내서에서는 AEM에서 Creative Cloud 폴더 공유 기능을 활용하는 모범 사례에 대해 설명합니다.
