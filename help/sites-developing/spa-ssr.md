---
title: SPA 및 서버측 렌더링
seo-title: SPA 및 서버측 렌더링
description: '"SPA 및 서버측 렌더링"'
seo-description: 'null'
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
exl-id: 89e45231-885a-4d35-839b-2b50239503ad
source-git-commit: cc31f2fa2f79154749776260f7621f6631e9db4a
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 1%

---

# SPA 및 서버측 렌더링{#spa-and-server-side-rendering}

>[!NOTE]
>단일 페이지 애플리케이션(SPA) 편집기 기능을 사용하려면 [AEM 6.4 서비스 팩 2](https://helpx.adobe.com/kr/experience-manager/6-4/release-notes/sp-release-notes.html) 이상이 필요합니다.
>
>SPA 편집기는 SPA 프레임워크 기반 클라이언트측 렌더링(예: React 또는 Angular)이 필요한 프로젝트에 권장되는 솔루션입니다.

>[!NOTE]
>
>이 문서에 설명된 대로 SPA 서버측 렌더링 기능을 사용하려면 AEM 6.4.5.0 이상이 필요합니다.

## 개요 {#overview}

SPA(단일 페이지 애플리케이션)은 종종 기본 애플리케이션과 마찬가지로 친숙한 방식으로 반응하고 동작하는 풍부한 동적 경험을 사용자에게 제공할 수 있습니다. [이는 클라이언트가 컨텐츠를 전방으로 로드한 다음, 사용자 인터랙션을 처리하](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) 는 데 크게 의존하여 클라이언트와 서버 사이에 필요한 통신 양을 최소화함으로써, 앱을 보다 반응적으로 만들 수 있다.

그러나 이는 특히 SPA이 크고 해당 컨텐츠가 풍부한 경우 초기 로드 시간이 길어질 수 있습니다. 로드 시간을 최적화하기 위해 일부 컨텐츠를 서버측에서 렌더링할 수 있습니다. SSR(서버 측 렌더링)을 사용하면 페이지의 초기 로드를 가속화한 다음 클라이언트에 추가 렌더링을 전달할 수 있습니다.

## SSR {#when-to-use-ssr} 사용 시기

모든 프로젝트에 SSR이 필요하지 않습니다. AEM은 SPA용 JS SSR을 완전히 지원하지만 Adobe에서는 모든 프로젝트에 대해 체계적으로 구현하는 것은 권장하지 않습니다.

SSR을 구현하려면 먼저 장기적인 유지 관리를 포함하여 SSR이 프로젝트에 대해 어떤 추가 복잡성, 노력, 비용을 추가로 나타내는지 평가해야 합니다. SSR 아키텍처는 추가 값이 예상 비용을 명확하게 초과하는 경우에만 선택해야 합니다.

일반적으로 SSR은 다음 질문 중 하나에 명확한 &quot;예&quot;가 있을 때 일부 값을 제공합니다.

* **SEO:** 트래픽을 발생시키는 검색 엔진에서 사이트를 제대로 인덱싱하려면 SSR이 여전히 필요합니까? 기본 검색 엔진 크롤러가 이제 JS를 평가한다는 것을 잊지 마십시오.
* **페이지 속도:** SSR은 실시간 환경에서 측정 가능한 속도 개선 기능을 제공하고 전체 사용자 경험에 추가합니까?

이 두 질문 중 하나 이상이 프로젝트에 대해 명확한 &quot;예&quot;로 답변되는 경우에만 Adobe에서 SSR 구현을 추천합니다. 다음 섹션에서는 Adobe I/O Runtime을 사용하여 이 작업을 수행하는 방법에 대해 설명합니다.

## Adobe I/O Runtime {#adobe-io-runtime}

프로젝트에 SSR](#when-to-use-ssr)을 구현해야 한다고 확신하는 경우 Adobe의 권장 해결 방법은 Adobe I/O Runtime을 사용하는 것입니다.[

Adobe I/O Runtime에 대한 자세한 내용은

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html)  - 서비스 개요
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html)  - 플랫폼에 대한 자세한 설명서입니다.

다음 섹션에서는 Adobe I/O Runtime을 사용하여 두 개의 다른 모델에서 SPA용 SSR을 구현하는 방법에 대해 자세히 설명합니다.

* [AEM 기반 통신 흐름](#aem-driven-communication-flow)
* [Adobe I/O 기반 통신 흐름](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>Adobe은 환경(스테이지, 제품, 테스트 등)별로 별도의 Adobe I/O Runtime 작업 공간을 권장합니다. 이렇게 하면 다른 환경에 배포된 단일 애플리케이션의 다른 버전을 사용하는 일반적인 SDLC(시스템 개발 수명 주기) 패턴을 사용할 수 있습니다. 자세한 내용은 Project Firefly 응용 프로그램용 [CI/CD](https://www.adobe.io/apis/experienceplatform/project-firefly/docs.html#!AdobeDocs/project-firefly/master/guides/ci_cd_for_firefly_apps.md) 문서를 참조하십시오.
>
>인스턴스 유형별 런타임 구현에 차이가 없으면 인스턴스(작성자, 게시)당 별도의 작업 공간이 필요하지 않습니다.

## 원격 콘텐츠 렌더러 구성 {#remote-content-renderer-configuration}

AEM에서는 원격 렌더링된 컨텐츠를 검색할 수 있는 위치를 알고 있어야 합니다. SSR](#adobe-io-runtime)에 대해 구현하도록 선택한 모델에 관계없이 AEM에 이 원격 렌더링 서비스에 액세스하는 방법을 지정해야 합니다.[

이 작업은 **RemoteContentRenderer - Configuration Factory** OSGi 서비스를 통해 수행됩니다. `http://<host>:<port>/system/console/configMgr`의 웹 콘솔 구성 콘솔에서 문자열 &quot;RemoteContentRenderer&quot;를 검색합니다.

![](assets/rendererconfig.png)

구성에 대해 다음 필드를 사용할 수 있습니다.

* **컨텐츠 경로 패턴**  - 필요한 경우 컨텐츠의 일부를 일치시키기 위한 정규 표현식
* **원격 끝점 URL**  - 콘텐츠 생성을 담당하는 끝점의 URL입니다
   * 로컬 네트워크에 없는 경우 보안 HTTPS 프로토콜을 사용합니다.
* **추가 요청 헤더**  - 원격 끝점으로 전송된 요청에 추가할 추가 헤더입니다.
   * 패턴:`key=value`
* **요청 시간 제한**  - 원격 호스트 요청 시간 제한(밀리초)

>[!NOTE]
>
>[AEM 기반 통신 흐름](#aem-driven-communication-flow) 또는 [Adobe I/O Runtime 기반 흐름](#adobe-io-driven-communication-flow)을 구현하도록 선택하는지에 관계없이 원격 콘텐츠 렌더러 구성을 정의해야 합니다.
>
>[사용자 지정 Node.js 서버](#using-node-js)를 사용하도록 선택하는 경우에도 이 구성을 정의해야 합니다.

>[!NOTE]
>
>이 구성은 사용 가능한 추가 확장 및 사용자 지정 옵션이 있는 [원격 콘텐츠 렌더러](#remote-content-renderer)를 사용합니다.

## AEM 기반 통신 흐름 {#aem-driven-communication-flow}

SSR을 사용할 때 AEM에서 SPA의 [구성 요소 상호 작용 워크플로우](/help/sites-developing/spa-overview.md#workflow)에는 Adobe I/O Runtime에서 앱의 초기 컨텐츠가 생성되는 단계가 포함됩니다.

1. 브라우저가 AEM에서 SSR 컨텐츠를 요청합니다.
1. AEM은 모델을 Adobe I/O Runtime에 게시합니다.
1. Adobe I/O Runtime에서 생성된 컨텐츠를 반환합니다
1. AEM은 백엔드 페이지 구성 요소의 HTL 템플릿을 통해 Adobe I/O Runtime에서 반환되는 HTML을 제공합니다.

![server-side-rendering-cms-drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Adobe I/O Runtime 기반 통신 흐름 {#adobe-io-driven-communication-flow}

[AEM 기반 통신 흐름](#aem-driven-communication-flow) 섹션에서는 AEM에서 컨텐츠의 부트스트래핑 및 서비스를 수행하는 SPA에 대한 서버 측 렌더링의 표준 및 권장 구현에 대해 설명합니다.

또는 Adobe I/O Runtime이 부트스트랩을 담당하도록 SSR을 구현하여 커뮤니케이션 흐름을 효과적으로 취소할 수 있습니다.

두 모델 모두 유효하며 AEM에서 지원합니다. 하지만, 특정 모델을 구현하기 전에 각각의 장단점을 고려해야 합니다.

| 부트스트랩 | 장점 | 단점 |
|---|---|---|
| AEM | AEM은 필요한 경우 라이브러리 삽입 작업을 관리합니다.<br>리소스는 AEM에서만 유지 관리하면 됩니다 | SPA 개발자에 익숙하지 않을 수 있음 |
| Adobe I/O Runtime | SPA 개발자에게 더 익숙합니다 | CSS 및 JavaScript와 같은 응용 프로그램에 필요한 Clientlib 리소스는 [`allowProxy` 속성](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br>리소스를 AEM과 Adobe I/O Runtime<br>간에 동기화해야 함 SPA을 작성할 수 있도록 하려면 Adobe I/O Runtime용 프록시 서버가 필요할 수 있습니다 |

## SSR {#planning-for-ssr} 계획

일반적으로 응용 프로그램의 일부만 서버 측에서 렌더링해야 합니다. 일반적인 예는 페이지의 초기 로드 시 접힌 부분 위에 표시되는 컨텐츠를 서버 측에서 렌더링해야 하는 컨텐트입니다. 이렇게 하면 이미 렌더링된 클라이언트에게 콘텐츠를 전달하여 시간을 절약할 수 있습니다. 사용자가 SPA과 상호 작용하면 클라이언트가 추가 컨텐츠를 렌더링합니다.

SPA에 대한 서버 측 렌더링을 구현하는 것을 고려하므로 SSR이 필요한 앱의 부분을 검토해야 합니다.

## SSR {#developing-an-spa-using-ssr}을 사용하여 SPA 개발

SPA 구성 요소는 클라이언트(브라우저) 또는 서버 측에서 렌더링할 수 있습니다. 서버측을 렌더링할 때 창 크기 및 위치와 같은 브라우저 속성이 없습니다. 따라서 SPA 구성 요소는 렌더링될 위치에 대해 가정하지 않고 압축되어야 합니다.

SSR을 활용하려면 서버 측 렌더링을 담당하는 Adobe I/O Runtime뿐만 아니라 AEM에 코드를 배포해야 합니다. 대부분의 코드는 동일하지만 서버별 작업은 다릅니다.

## AEM {#ssr-for-spas-in-aem}의 SPA용 SSR

AEM의 SPA용 SSR에는 앱 콘텐츠 서버 측 렌더링을 위해 호출되는 Adobe I/O Runtime이 필요합니다. 앱의 HTL 내에서 컨텐츠를 렌더링하기 위해 Adobe I/O Runtime의 리소스가 호출됩니다.

AEM이 Angular 및 React SPA 프레임워크을 기본적으로 지원하는 것처럼 Angular 및 React 앱에도 서버 측 렌더링이 지원됩니다. 자세한 내용은 두 프레임워크에 대한 NPM 설명서 를 참조하십시오.

* 반응:[https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular:[https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

간단한 예를 보려면 [We.Retail 저널 앱](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)을 참조하십시오. 전체 애플리케이션 서버 측에서 렌더링됩니다. 이 예는 실제 예는 아니지만 SSR을 구현하는 데 필요한 사항을 보여줍니다.

>[!CAUTION]
>[We.Retail 저널 앱](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)은 데모용으로만 사용되며, 따라서 권장되는 Adobe I/O Runtime 대신 간단한 예로 Node.js를 사용합니다. 이 예는 프로젝트 작업에 사용해서는 안 됩니다.

>[!NOTE]
>모든 AEM 프로젝트는 React 또는 Angular을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 [AEM Project Archetype](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)을 활용해야 합니다.

## Node.js {#using-node-js} 사용

Adobe I/O Runtime은 AEM에서 SSR for SPA을 구현하는 권장 솔루션입니다.

온-프레미스 AEM 인스턴스의 경우, 위에 설명된 것과 같은 방식으로 사용자 지정 Node.js 인스턴스를 사용하여 SSR을 구현할 수도 있습니다. 이 기능은 Adobe에서 지원되지만 권장되지 않습니다.

Node.js는 Adobe 호스팅 AEM 인스턴스에 대해 지원되지 않습니다.

>[!NOTE]
>
>Node.js를 통해 SSR을 구현해야 하는 경우, Adobe은 모든 AEM 환경(작성자, 게시, 스테이지 등)에 대해 별도의 Node.js 인스턴스를 권장합니다.

## 원격 콘텐츠 렌더러 {#remote-content-renderer}

AEM에서 SPA과 함께 SSR을 사용하는 데 필요한 [원격 컨텐츠 렌더러 구성](#remote-content-renderer-configuration)은(는) 사용자의 요구 사항에 맞게 확장 및 사용자 지정할 수 있는 보다 일반화된 렌더링 서비스로 탭을 설정합니다.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` 는 Adobe I/O에서 렌더링되는 등의 원격 서버에 렌더링된 컨텐츠를 검색하기 위한 OSGi 서비스입니다.원격 서버로 전송된 콘텐츠는 전달된 요청 매개 변수를 기반으로 합니다.

`RemoteContentRenderingService` 추가 컨텐츠 조작이 필요할 때 사용자 지정 Sling 모델 또는 서블릿에 종속성 전환으로 삽입할 수 있습니다.

이 서비스는 [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet)에서 내부적으로 사용됩니다.

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

`RemoteContentRendererRequestHandlerServlet` 은 요청 구성을 프로그래밍 방식으로 설정하는 데 사용할 수 있습니다. `DefaultRemoteContentRendererRequestHandlerImpl`제공된 기본 요청 처리기 구현을 통해 콘텐츠 구조의 위치를 원격 엔드포인트에 매핑하기 위해 여러 OSGi 구성을 만들 수 있습니다.

사용자 지정 요청 핸들러를 추가하려면 `RemoteContentRendererRequestHandler` 인터페이스를 구현합니다. `Constants.SERVICE_RANKING` 구성 요소 속성을 `DefaultRemoteContentRendererRequestHandlerImpl` 의 등급인 100보다 큰 정수로 설정해야 합니다.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### 기본 처리기 {#configure-default-handler}의 OSGi 구성 구성

기본 처리기의 구성은 [원격 콘텐츠 렌더러 구성](#remote-content-renderer-configuration) 섹션에 설명된 대로 구성해야 합니다.

###  원격 콘텐츠 렌더러 사용 {#usage}

서블릿을 가져와서 페이지에 삽입할 수 있는 일부 컨텐츠를 반환하려면 다음을 수행하십시오.

1. 원격 서버에 액세스할 수 있는지 확인합니다.
1. 다음 코드 조각 중 하나를 AEM 구성 요소의 HTL 템플릿에 추가합니다.
1. 선택적으로 OSGi 구성을 만들거나 수정합니다.
1. 사이트의 컨텐츠를 찾아봅니다

일반적으로 페이지 구성 요소의 HTL 템플릿은 이러한 기능의 주요 수신자입니다.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### 요구 사항 {#requirements}

서블릿은 Sling 모델 익스포터를 활용하여 구성 요소 데이터를 serialize합니다. 기본적으로 `com.adobe.cq.export.json.ContainerExporter` 및 `com.adobe.cq.export.json.ComponentExporter` 모두 Sling 모델 어댑터로 지원됩니다. 필요한 경우 `RemoteContentRendererServlet`을 사용하고 `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`을 구현하기 위해 요청을 수정해야 하는 클래스를 추가할 수 있습니다. 추가 클래스는 `ComponentExporter`을 확장해야 합니다.
