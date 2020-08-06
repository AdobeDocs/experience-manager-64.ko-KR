---
title: AEM을 사용하여 자산을 관리하는 모범 사례
description: AEM Assets 배포 및 자산 인제스트 및 처리에 사용되는 기능에 따라, 로드 중인 시스템 안정성과 성능을 향상시키는 모범 사례를 식별하고 준수합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Best practices for AEM Assets {#best-practices-for-assets}

Adobe Experience Manager(AEM) 자산은 콘텐츠 속도를 높여 비즈니스 목표 달성에 기여하는 고품질의 디지털 마케팅 경험을 전달하는 데 중요한 역할을 합니다. AEM Assets 내에서 많은 양의 자산을 사용하여 작업하거나 비디오 및 다이내믹 미디어를 비롯한 다양한 자산을 정기적으로/정기적으로 업로드하는 경우, 시스템 효율성을 위해 디지털 자산 관리 경험을 최적화하는 것이 중요합니다.

조직에 AEM Assets을 배치한 방식과 자산 수집, 변환 생성 및 메타데이터 추출과 관련하여 사용하는 기능에 따라 다양한 영역에서 모범 사례를 찾아 이를 준수함으로써 부하의 시스템 안정성과 성능을 크게 향상시킬 수 있습니다.

다음 가이드를 검토한 후 요구 사항에 맞는 엔터프라이즈 에셋 관리 시스템을 구축하고 관리하는 데 필요한 지식과 툴을 사용할 수 있습니다.

* [자산 성능 조정 가이드](performance-tuning-guidelines.md)는 구현 시 라이브한 후에도 시스템을 최대한 활용할 수 있는 일련의 모범 사례를 포함합니다.
* [자산 크기 조정 가이드](assets-sizing-guide.md)에셋 구현에 대한 견적을 작성할 때 에셋 스토리지, CPU, 메모리, IO 및 네트워크 처리량과 관련하여 사용 가능한 충분한 리소스가 있는지 확인해야 합니다. 이러한 항목 중 많은 항목의 크기를 조정하려면 시스템에 로드되는 자산의 수를 이해해야 합니다. 이 안내서에는 크기 조정 도구는 물론, AEM Assets 배포에 필요한 인프라와 리소스를 측정하기 위한 효율적인 지표를 결정하는 데 도움이 되는 우수 사례가 포함되어 있습니다.
* [자산 마이그레이션 안내서](assets-migration-guide.md)기존 시스템에서 AEM Assets으로 자산을 마이그레이션하려면 마이그레이션 프로세스를 간소화하는 몇 가지 단계를 고려해야 합니다. 마이그레이션 가이드는 단계별로 AEM에 에셋을 가져오기 위해 수행하는 작업에 대한 우수 사례를 포함합니다. 여기에는 메타데이터 적용, 변환 생성 및 배포를 게시할 자산 활성화가 포함됩니다.
* [자산 네트워크 고려 사항](assets-network-considerations.md)AEM 배포를 처리할 때 네트워크 토폴로지를 이해하는 것이 네트워크 성능을 이해하고, 선택 지점을 식별하고, 예상되는 사용자 경험을 설명하는 데 중요합니다. 자산 네트워크 고려 사항 문서에서는 AEM 자산 배포를 디자인할 때 네트워크 고려 사항에 대해 설명합니다.
* [에셋 모니터링 가이드](assets-monitoring-best-practices.md)AEM 배포를 배포한 후에 시스템 무결성을 유지하면서 특정 작업과 시스템을 전반적으로 모니터링해야 합니다. 모니터링 안내서에는 시스템의 다양한 측면을 모니터링하기 위한 모범 사례가 포함되어 있습니다.
* (더 이상 사용되지 않음) [자산 오프로드 안내서](assets-offloading-best-practices.md)에서 대용량 파일 처리 및 실행 워크플로우는 상당한 CPU, 메모리 및 I/O 리소스를 사용할 수 있습니다. 이러한 작업을 오프로딩하면 CPU, 메모리 및 IO 오버헤드가 줄어듭니다. 자산 오프로드 안내서에는 권장되는 사용 사례와 자산 오프로드에 대한 우수 사례가 포함되어 있습니다.
* [AEM 데스크탑 앱 모범 사례](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)AEM 데스크탑 앱은 데스크탑에 디지털 에셋 관리(DAM) 솔루션을 연결하므로 데스크탑에서 바로 AEM 웹 UI에서 사용할 수 있는 파일을 열 수 있습니다. AEM 데스크탑 앱의 편리한 워크플로우는 데스크탑 운영 체제에서 제공하는 네트워크 공유 기술을 사용하여 가능합니다. 이 안내서에서는 주요 기능 및 AEM 데스크탑 앱의 권장 사용에 대해 설명합니다.
* [AEM 및 Creative Cloud 통합 모범 사례](aem-cc-integration-best-practices.md)는 다양한 방법으로 AEM 배포를 Creative Cloud과 통합할 수 있습니다. 통합 및 자산 전송 워크플로우를 간소화하기 위한 몇 가지 모범 사례를 통해 효율성을 극대화할 수 있습니다. 이 안내서에는 AEM Assets과 Adobe Creative Cloud의 통합에 대한 우수 사례가 포함되어 있습니다.
* (더 이상 사용되지 않음) [AEM에서 Creative Cloud 폴더 공유 모범 사례](aem-cc-folder-sharing-best-practices.md)DAM의 사용자가 Creative Cloud(CC) 사용자와 폴더를 공유할 수 있도록 AEM을 구성하여 Creative Cloud 자산 서비스에서 공유 폴더로 사용할 수 있습니다. 이 기능을 사용하여 크리에이티브 팀과 DAM 사용자 간에 파일을 교환할 수 있습니다. 이 안내서에서는 AEM과 Creative Cloud 폴더 공유 기능을 활용하기 위한 모범 사례에 대해 설명합니다.
