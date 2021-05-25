---
title: Adobe Analytics와 통합
seo-title: Adobe Analytics와 통합
description: AEM을 Adobe Analytics과 통합하는 방법을 알아봅니다.
seo-description: AEM을 Adobe Analytics과 통합하는 방법을 알아봅니다.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 5%

---

# Adobe Analytics와 통합{#integrating-with-adobe-analytics}

Adobe Analytics과 AEM을 통합하여 웹 페이지 활동을 추적할 수 있습니다.

* Adobe Analytics 구성을 사용하면 AEM에서 Adobe Analytics을 인증할 수 있습니다.
* 프레임워크는 Adobe Analytics 보고서 세트로 전송되는 데이터를 식별합니다.

이 데이터에는 페이지 및 사용자 데이터가 포함됩니다.예:

* AEM 구성 요소가 수집하는 데이터
* 링크 클릭 수
* 비디오 사용 정보
* Adobe Analytics에서 페이지 방문 횟수

다음 페이지는 통합을 구성하는 데 도움이 됩니다.

* [Adobe Analytics 연결 및 프레임워크 생성](/help/sites-administering/adobeanalytics-connect.md)
* [Adobe Analytics에 대한 링크 추적 구성](/help/sites-administering/adobeanalytics-link.md)
* [구성 요소 데이터를 Adobe Analytics 속성과 매핑](/help/sites-administering/adobeanalytics-mapping.md)
* [Adobe Analytics에 대한 비디오 추적 구성](/help/sites-administering/adobeanalytics-video.md)

[옵트인 마법사](/help/sites-administering/opt-in.md)를 사용하여 통합을 쉽게 수행할 수도 있습니다.

>[!NOTE]
>
>방법 문서를 참조하십시오.[DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html)을 사용하여 AEM과 Adobe Target 및 Adobe Analytics 통합

## 추가 정보 {#further-information}

다음을 참조하십시오.

* [Adobe Analytics ](/help/sites-developing/extending-analytics.md) 통합 확장 을 참조하십시오.
* Adobe Analytics 통합 문제 해결에 대한 자세한 내용은 기술 자료 문서 [Adobe Analytics 통합 - 문제 해결](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html) 을 참조하십시오.

>[!NOTE]
>
>사용자 지정 프록시 구성과 함께 Adobe Analytics을 사용하는 경우 [Apache HTTP Client **프록시 구성에 필요한 두 개의 OSGi 번들](/help/sites-deploying/configuring-osgi.md)(예: 웹 콘솔 사용)을 구성해야 합니다.** AEM의 일부 기능에서는 3.x API를 사용하는 반면, 다른 기능에서는 4.x API를 사용하기 때문에 두 가지 모두 필요합니다. 구성:
>
>* **3.x API를 구성하기 위한 Day Commons HTTP Client 3.1** \
   >  예: [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **4.x API를** 구성하기 위한 Apache HTTP 구성 요소 프록시 구성
>
>  
예: [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
