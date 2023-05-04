---
title: 다국어 자산
description: 이진, 메타데이터 및 태그를 포함한 자산을 여러 언어로 번역하는 워크플로우를 자동화하는 방법을 알아봅니다.
contentOwner: AG
feature: Asset Management
role: Admin
exl-id: 8e065137-3599-48af-a040-6923b7b5e1d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 5%

---

# 다국어 자산 {#multilingual-assets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM(Adobe Experience Manager) 자산을 사용하면 자산(바이너리, 메타데이터 및 태그 포함)에 대한 번역 워크플로우를 자동화하여 다국어 프로젝트에서 사용할 수 있도록 다른 언어로 자산을 생성할 수 있습니다.

번역 워크플로우를 자동화하기 위해 번역 서비스 공급자를 [!DNL Experience Manager] 자산을 여러 언어로 번역할 프로젝트를 만들 수 있습니다. [!DNL Experience Manager] 은 사람 및 기계 번역 워크플로우를 지원합니다.

인간 번역: 번역된 자산이 반환되고 AEM으로 가져옵니다. 번역 공급자가 AEM과 통합되면 사이에 자산이 자동으로 전송됩니다 [!DNL Experience Manager] 그리고 번역 공급자입니다.

기계 번역: 기계 번역 서비스는 자산의 메타데이터와 태그를 즉시 변환합니다.

자산을 번역하면 다음 사항이 포함됩니다.

1. [연결 중 [!DNL Experience Manager] 번역 서비스 공급자 사용](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [번역 통합 프레임워크 구성 만들기](/help/sites-administering/tc-tic.md)
1. [자산 번역 준비](preparing-assets-for-translation.md)
1. [폴더에 번역 클라우드 서비스 적용](transition-cloud-services.md)
1. [번역 프로젝트 만들기](translation-projects.md)

번역 서비스 공급자가 AEM과 통합할 커넥터를 제공하지 않는 경우 [대체 프로세스](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

또한, [컨텐츠 조각에 대한 번역 프로젝트 만들기](creating-translation-projects-for-content-fragments.md).
