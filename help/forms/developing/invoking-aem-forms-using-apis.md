---
title: API를 사용하여 AEM Forms 호출
seo-title: Invoking AEM Forms using APIs
description: Adobe Experience Manager Forms은 공유 인프라 내에서 작동하는 서비스로 구성된 J2EE 기반 엔터프라이즈 소프트웨어입니다. Java API, 웹 서비스, Remoting 및 REST API를 사용하여 클라이언트 애플리케이션을 사용하여 프로그래밍 방식으로 AEM Forms을 호출하는 방법을 알아봅니다.
seo-description: Adobe Experience Manager Forms is J2EE-based enterprise software that consists of services that operate within a shared infrastructure. Learn how to use client applications to invoke AEM Forms programmatically using a Java API, web services, Remoting, and REST API.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
exl-id: 6b60209f-aced-4698-97f1-b1a7782eef46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---

# API를 사용하여 AEM Forms 호출 {#invoking-aem-forms-using-apis}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Forms은 공유 인프라 내에서 작동하는 서비스로 구성된 J2EE 기반 엔터프라이즈 소프트웨어입니다. 서비스 작업은 일반적으로 문서를 사용하거나 생성합니다. AEM Forms을 사용하면 양식 워크플로우를 전자 양식, 문서 보안 및 문서 생성과 결합하여 통합된 서비스 세트에 통합할 수 있습니다. 이러한 서비스는 방화벽 내부 및 외부에서 액세스할 수 있습니다.

클라이언트 응용 프로그램은 Java API, 웹 서비스, 원격 및 REST를 사용하여 프로그래밍 방식으로 AEM Forms 서비스를 호출할 수 있습니다. 관리 콘솔을 사용하여 프로그래밍 방식으로 호출되어 AEM Forms 서비스를 제공할 수 있는 엔드포인트를 표시하도록 서비스를 구성할 수 있습니다. 기본적으로 대부분의 서비스는 원격, Java 및 웹 서비스 끝점을 노출하도록 사전 구성되어 있습니다.

비즈니스 요구 사항에 따라 사용할 호출 방법이 결정됩니다. 예를 들어 Java API를 사용하여 Java Entity 및 Message Bean과 같은 Java 엔터프라이즈 애플리케이션에 AEM Forms 기능을 통합할 수 있습니다. 마찬가지로, 웹 서비스를 사용하여 .NET 프로젝트(또는 웹 서비스 표준을 지원하는 개발 환경으로 개발된 기타 프로젝트)에 AEM Forms 기능을 통합할 수 있습니다.

Enterprise JavaBeans™(EJB)에 J2EE 컨테이너가 필요한 방식과 유사한 서비스 컨테이너를 실행해야 합니다. AEM Forms에는 서비스 컨테이너 구현이 하나만 포함되어 있습니다. 서비스 컨테이너는 서비스 배포를 비롯하여 모든 요청이 올바른 서비스로 전송되도록 하는 등 서비스 수명을 관리합니다. 또한 서비스가 소비하거나 생성하는 문서를 관리합니다.

>[!NOTE]
>
>AEM Forms로 프로그래밍하는 경우에는 감시 폴더 또는 이메일을 사용하여 AEM Forms을 호출하는 방법에 대한 정보가 포함되지 않습니다.
