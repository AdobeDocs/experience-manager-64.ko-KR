---
title: Adobe Analytics와 통합
seo-title: Integrating with Adobe Analytics
description: AEM을 Adobe Analytics과 통합하는 방법을 알아봅니다.
seo-description: Learn how to integrate AEM with Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 62%

---

# Adobe Analytics와 통합{#integrating-with-adobe-analytics}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Analytics과 AEM을 통합하여 웹 페이지 활동을 추적할 수 있습니다.

* Adobe Analytics 구성을 사용하면 AEM에서 Adobe Analytics를 인증할 수 있습니다.
* 프레임워크는 Adobe Analytics 보고서 세트로 전송되는 데이터를 식별합니다.

이 데이터에는 페이지 및 사용자 데이터가 포함됩니다. 예:

* AEM 구성 요소가 수집하는 데이터
* 링크 클릭
* 비디오 사용 정보
* Adobe Analytics에서의 페이지 방문 횟수

다음 페이지는 통합을 구성하는 데 도움이 됩니다.

* [Adobe Analytics 연결 및 프레임워크 생성](/help/sites-administering/adobeanalytics-connect.md)
* [Adobe Analytics를 위한 링크 추적 구성](/help/sites-administering/adobeanalytics-link.md)
* [Adobe Analytics 속성을 사용하여 구성 요소 데이터 매핑](/help/sites-administering/adobeanalytics-mapping.md)
* [Adobe Analytics를 위한 비디오 추적 구성](/help/sites-administering/adobeanalytics-video.md)

를 사용할 수도 있습니다 [옵트인 마법사](/help/sites-administering/opt-in.md) 통합을 쉽게 수행할 수 있습니다.

>[!NOTE]
>
>방법 문서를 참조하십시오. [DTM을 사용하여 AEM과 Adobe Target 및 Adobe Analytics 통합](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## 추가 정보 {#further-information}

다음을 참조하십시오.

* [Adobe Analytics 통합 확장](/help/sites-developing/extending-analytics.md)을 참조하여 사용자 데이터를 수집하는 구성 요소 개발 및 Adobe Analytics 프레임워크 맞춤화에 대한 자세한 내용을 알아보십시오.
* 지식 기반 문서인 [Adobe Analytics 통합 - 문제 해결](https://helpx.adobe.com/kr/experience-manager/kb/sitecatalystintegrationtroubleshooting.html)을 참조하여 Adobe Analytics 통합 관련 문제를 해결하는 방법에 대해 알아보십시오.

>[!NOTE]
>
>If you are using Adobe Analytics with a custom proxy configuration, you need to [configure two OSGi bundles](/help/sites-deploying/configuring-osgi.md) (for example, with the Web console) required for the **Apache HTTP Client** proxy configurations. Both are required as some functionalities of AEM use the 3.x APIs, while others use the 4.x APIs. 다음을 구성하십시오.
>
>* 3.x API 구성을 위한 **Day Commons HTTP 클라이언트 3.1**\
   >  예 [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* 4.x API 구성을 위한 **Apache HTTP 구성 요소 프록시 구성**
>
>  예 [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
