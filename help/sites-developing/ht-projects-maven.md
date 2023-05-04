---
title: Apache Maven을 사용하여 AEM 프로젝트를 작성하는 방법
description: 이 문서에서는 Apache Maven을 기반으로 AEM 프로젝트를 설정하는 방법을 설명합니다
exl-id: 6ae0e387-468b-4cea-9e3f-0816d67b7621
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 21%

---

# Apache Maven을 사용하여 AEM 프로젝트를 작성하는 방법 {#how-to-build-aem-projects-using-apache-maven}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM 6.4는 온프레미스 및 AMS 구현 둘 다에 대해 최신 AEM Project Archetype에서 구현한 패키지 관리 및 프로젝트 구조에 대한 최신 모범 사례를 준수합니다.

>[!TIP]
>
>자세한 내용은 다음을 참조하십시오.
>
>* 다음 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 최신 AEM 프로젝트를 구성하는 방법에 대한 AEM as a Cloud Service 설명서의 문서 입니다.
>* 다음 [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) archetype을 사용하여 새 AEM 프로젝트를 시작하는 방법에 대한 설명서입니다.
>* 다음 [Adobe 컨텐츠 패키지 Maven 플러그인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developer-tools/maven-plugin.html#developer-tools) AEM 애플리케이션을 배포하는 방법에 대한 AEM as a Cloud Service 설명서의 문서 입니다.
>
>세 문서 모두 AEM 6.4에 적용됩니다.
