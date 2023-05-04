---
title: AEM을 사용하여 자산을 관리하는 우수 사례
description: 로드 중인 시스템 안정성 및 성능을 향상시키는 우수 사례를 식별하고 준수합니다 [!DNL Experience Manager] 자산을 수집 및 처리하는 데 사용되는 자산 배포 및 기능입니다.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# 우수 사례 [!DNL Experience Manager] 자산 {#best-practices-for-assets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets는 컨텐츠 속도를 높여 비즈니스 목표 달성에 기여하는 고품질 디지털 마케팅 경험을 제공하는데 중요한 부분입니다. 내에서 자산이 많은 경우 [!DNL Assets] 비디오 및 다이내믹 미디어를 포함한 다양한 자산을 정기적으로/정기적으로 업로드하려면 시스템 효율성을 위해 디지털 자산 관리 경험을 최적화해야 합니다.

위치 방법에 따라 [!DNL Assets] 조직 및 자산 수집, 표현물 생성 및 메타데이터 추출과 관련하여 사용하는 기능에 대해, 다양한 영역에서 우수 사례를 식별하고 준수하면 로드 중인 시스템 안정성 및 성능이 크게 향상됩니다.

다음 안내서를 검토한 후에는 필요에 따라 엔터프라이즈 자산 관리 시스템을 구축하고 관리하는 지식과 도구가 제공됩니다.

* [자산 성능 조정 가이드](performance-tuning-guidelines.md)
를 라이브로 전환한 후에도 구현 중 어느 시점에서 따를 수 있는 모범 사례 세트가 포함되어 있어 시스템을 최대한 활용할 수 있습니다.
* [자산 크기 조정 가이드](assets-sizing-guide.md)
Assets 구현에 대한 견적을 작성할 때 자산 저장, CPU, 메모리, IO 및 네트워크 처리량 측면에서 사용 가능한 리소스가 충분한지 확인하는 것이 중요합니다. 이러한 항목 중 많은 항목의 크기를 조정하려면 시스템에 로드되는 자산의 수를 이해해야 합니다. 이 안내서에는 배포에 필요한 인프라 및 리소스를 추정하는 효율적인 지표를 결정하는 데 도움이 되는 모범 사례가 포함되어 있습니다 [!DNL Experience Manager] 자산 및 크기 조정 도구.
* [자산 마이그레이션 안내서](assets-migration-guide.md)
자산을 이전 시스템에서 로 마이그레이션하려면 [!DNL Experience Manager] 자산 마이그레이션 프로세스를 간소화하기 위해 몇 가지 단계를 고려해야 합니다. 마이그레이션 안내서에는 자산을 로 가져오기 위해 수행하는 작업에 대한 모범 사례가 포함되어 있습니다 [!DNL Experience Manager] 위상적으로. 여기에는 메타데이터 적용, 변환 생성 및 배포를 게시할 자산 활성화 등이 포함됩니다.
* [자산 네트워크 고려사항](assets-network-considerations.md)
처리 시 [!DNL Experience Manager] 배포, 네트워크 토폴로지를 이해하는 것은 네트워크 성능을 이해하고, 선택 지점을 식별하고, 예상되는 사용자 경험을 설명하는 데 중요합니다. 자산 네트워크 고려 사항 문서에서는 [!DNL Experience Manager] 자산 배포.
* [자산 모니터링 안내서](assets-monitoring-best-practices.md)
이후 [!DNL Experience Manager] 배포가 배포되면 시스템 무결성 및 작업 효율성을 보장하기 위해 특정 작업과 시스템을 일반적으로 모니터링해야 합니다. 모니터링 안내서에는 시스템의 다양한 측면을 모니터링하기 위한 모범 사례가 포함되어 있습니다.
* (더 이상 사용되지 않음) [Assets 오프로딩 안내서](assets-offloading-best-practices.md)
대용량 파일 처리 및 [!DNL Experience Manager] 자산은 상당한 CPU, 메모리 및 I/O 리소스를 사용할 수 있습니다. 이러한 작업을 업로드하면 CPU, 메모리 및 IO 오버헤드가 줄어들 수 있습니다. Assets 오프로딩 안내서에는 Assets 오프로딩에 대한 권장 사용 사례 및 우수 사례가 포함되어 있습니다.
* [[!DNL Experience Manager] 데스크탑 앱 모범 사례](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] 데스크탑 앱에서는 DAM(디지털 자산 관리) 솔루션을 데스크탑에 연결하여 [!DNL Experience Manager] 데스크탑에서 직접 웹 UI 사용 [!DNL Experience Manager] 데스크탑 앱의 사용하기 쉬운 워크플로우는 데스크탑 운영 체제에서 제공하는 네트워크 공유 기술을 사용하여 활성화됩니다. 이 안내서에서는 주요 기능 및 [!DNL Experience Manager] 데스크탑 앱.
* [[!DNL Experience Manager] 및 Creative Cloud 통합 우수 사례](aem-cc-integration-best-practices.md)
을(를) 통합할 수 있습니다 [!DNL Experience Manager] 여러 가지 방법으로 Creative Cloud을 사용한 배포. 통합 및 자산 전송 워크플로우를 간소화하는 몇 가지 모범 사례를 따르면 최대 효율성을 달성할 수 있습니다. 이 안내서에는 통합에 대한 모범 사례가 포함되어 있습니다 [!DNL Experience Manager] Adobe Creative Cloud이 있는 자산.
* (더 이상 사용되지 않음) [[!DNL Experience Manager] 폴더 공유 우수 사례 Creative Cloud](aem-cc-folder-sharing-best-practices.md)
다음을 구성할 수 있습니다 [!DNL Experience Manager] DAM의 사용자가 Creative Cloud 사용자와 폴더를 공유할 수 있도록 Creative Cloud 자산 서비스에서 공유 폴더로 사용할 수 있습니다. 이 기능은 크리에이티브 팀과 DAM 사용자 간에 파일을 교환하는 데 사용할 수 있습니다. 이 안내서에서는 를 활용하기 위한 모범 사례를 설명합니다 [!DNL Experience Manager] 폴더 공유 기능 Creative Cloud
