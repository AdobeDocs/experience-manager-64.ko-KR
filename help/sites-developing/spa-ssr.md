---
title: SPA 및 서버측 렌더링
seo-title: SPA 및 서버측 렌더링
description: 'null'
seo-description: 'null'
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
translation-type: tm+mt
source-git-commit: 0e7f4a78f63808bea2aa7a5abbb31e7e5b9d21b3
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 1%

---


# SPA 및 서버측 렌더링{#spa-and-server-side-rendering}

>[!NOTE]
>단일 페이지 애플리케이션(SPA) 편집기 기능을 사용하려면 [AEM 6.4 서비스 팩 2](https://helpx.adobe.com/kr/experience-manager/6-4/release-notes/sp-release-notes.html) 이상이 필요합니다.
>
>SPA 편집기는 SPA 프레임워크 기반의 클라이언트측 렌더링(예: 반응 또는 각도)이 필요한 프로젝트에 권장되는 솔루션입니다.

>[!NOTE]
>
>이 문서에 설명된 대로 SPA 서버측 렌더링 기능을 사용하려면 AEM 6.4.5.0 이상이 필요합니다.

## 개요 {#overview}

단일 페이지 애플리케이션(SPA)을 통해 사용자는 종종 기본 애플리케이션과 마찬가지로 익숙한 방식으로 반응하고 작동하는 풍부한 동적 경험을 제공할 수 있습니다. [이는 클라이언트에 의존하여 콘텐츠를 맨 앞에 로드한 다음 사용자 상호](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) 작용을 처리하는 까다로운 작업을 수행하여 클라이언트와 서버 사이에 필요한 통신 양을 최소화하여 앱을 보다 재활성화할 수 있도록 함으로써 이루어집니다.

그러나 SPA가 크고 컨텐츠가 풍부한 경우 초기 로드 시간이 길어질 수 있습니다. 로드 시간을 최적화하기 위해 일부 컨텐츠는 서버측에서 렌더링될 수 있습니다. SSR(서버측 렌더링)을 사용하면 페이지의 초기 로드를 가속화한 다음 클라이언트에게 추가 렌더링을 전달할 수 있습니다.

## SSR 사용 시기 {#when-to-use-ssr}

SSR이 모든 프로젝트에 필요하지 않습니다. AEM은 SPA용 JS SSR을 완벽하게 지원하지만 Adobe은 모든 프로젝트에 대해 체계적으로 구현하지 않는 것이 좋습니다.

SSR을 구현하기로 결정할 때 먼저 SSR을 현실적으로 추가함으로써 장기적인 유지 관리를 포함하여 프로젝트에 어떤 추가 복잡성, 노력, 비용이 있는지를 평가해야 합니다. SSR 아키텍처는 추가된 값이 예상 비용을 명확하게 초과하는 경우에만 선택해야 합니다.

일반적으로 SSR은 다음 질문 중 하나에 대해 명확한 &quot;예&quot;가 있을 때 약간의 값을 제공합니다.

* **SEO:** 실제로 트래픽을 발생시키는 검색 엔진으로 사이트를 올바로 인덱싱하려면 SSR이 여전히 필요합니까? 이제 주 검색 엔진 크롤러가 JS를 평가한다는 점을 염두에 두십시오.
* **페이지 속도:** SSR은 실제 환경에서 측정 가능한 속도 향상을 제공하고 전반적인 사용자 경험을 제공합니까?

이 두 질문 중 하나 이상의 질문에 대해 프로젝트에 대해 명확한 &quot;예&quot;를 대답하는 경우에만 Adobe에서 SSR 구현을 권장합니다. 다음 섹션에서는 Adobe I/O Runtime을 사용하여 이 작업을 수행하는 방법에 대해 설명합니다.

## Adobe I/O Runtime {#adobe-io-runtime}

프로젝트에서 SSR을 구현해야 한다고 [확신하는 경우 Adobe](#when-to-use-ssr)는 Adobe I/O Runtime을 사용하는 것이 좋습니다.

Adobe I/O Runtime에 대한 자세한 내용은

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - 서비스 개요
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - 플랫폼에 대한 자세한 설명서

다음 섹션에서는 두 가지 서로 다른 모델에서 SSR for your SPA를 구현하는 데 Adobe I/O Runtime을 사용할 수 있는 방법에 대해 자세히 설명합니다.

* [AEM 기반의 커뮤니케이션 흐름](#aem-driven-communication-flow)
* [Adobe I/O-런타임 기반의 커뮤니케이션 흐름](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>Adobe은 모든 AEM 환경(작성자, 게시, 단계 등)에 대해 별도의 Adobe I/O Runtime 인스턴스를 권장합니다.

## 원격 컨텐츠 렌더러 구성 {#remote-content-renderer-configuration}

AEM은 원격으로 렌더링된 내용을 검색할 수 있는 위치를 알고 있어야 합니다. SSR용으로 구현하려는 모델 [에](#adobe-io-runtime)관계없이 이 원격 렌더링 서비스에 액세스하는 방법을 AEM에 지정해야 합니다.

이 작업은 **RemoteContentRenderer - Configuration Factory** OSGi 서비스를 통해 수행됩니다. 의 웹 콘솔 구성 콘솔에서 &quot;RemoteContentRenderer&quot; 문자열을 검색합니다 `http://<host>:<port>/system/console/configMgr`.

![](assets/rendererconfig.png)

구성에 대해 다음 필드를 사용할 수 있습니다.

* **컨텐츠 경로 패턴** - 필요한 경우 컨텐츠의 일부를 일치시키기 위한 정규 표현식
* **원격 끝점 URL** - 콘텐츠 생성을 담당하는 끝점의 URL
   * 로컬 네트워크에 있지 않은 경우 보안 HTTPS 프로토콜을 사용하십시오.
* **추가 요청 헤더** - 원격 끝점으로 전송된 요청에 추가할 추가 헤더
   * 패턴: `key=value`
* **요청 시간 초과** - 원격 호스트 요청 시간 초과(밀리초)

>[!NOTE]
>
>[AEM 기반 통신 흐름](#aem-driven-communication-flow) 또는 [Adobe I/O Runtime 중심 흐름을](#adobe-io-driven-communication-flow)구현하도록 선택하더라도 원격 컨텐츠 렌더러 구성을 정의해야 합니다.
>
>사용자 지정 Node.js 서버를 [사용하도록 선택하는 경우에도 이 구성을 정의해야 합니다](#using-node-js).

>[!NOTE]
>
>이 구성은 추가 확장 및 사용자 정의 옵션이 있는 [원격](#remote-content-renderer)컨텐츠 렌더러를 활용합니다.

## AEM 기반의 커뮤니케이션 흐름 {#aem-driven-communication-flow}

SSR을 사용할 때 AEM에서 SPA의 [구성 요소 상호 작용 작업](/help/sites-developing/spa-overview.md#workflow) 과정에는 앱의 초기 컨텐츠가 Adobe I/O Runtime에서 생성되는 단계가 포함됩니다.

1. 브라우저가 AEM에서 SSR 컨텐츠를 요청합니다.
1. AEM은 모델을 Adobe I/O Runtime에 게시합니다.
1. Adobe I/O Runtime은 생성된 컨텐트를 반환합니다.
1. AEM은 백엔드 페이지 구성 요소의 HTL 템플릿을 통해 Adobe I/O Runtime이 반환하는 HTML을 제공합니다.

![server-side-rendering-cms-drivenemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Adobe I/O Runtime 중심 커뮤니케이션 흐름 {#adobe-io-driven-communication-flow}

AEM 기반 [커뮤니케이션 흐름](#aem-driven-communication-flow) 섹션에서는 AEM의 SPA와 관련하여 서버측 렌더링의 표준 및 권장 구현에 대해 설명합니다. 여기서 AEM은 부트스트래핑 및 컨텐트 제공을 수행합니다.

또는 SSR을 구현하여 Adobe I/O Runtime이 부트스트랩을 책임지도록 하고 통신 흐름을 효과적으로 반대로 할 수 있습니다.

두 모델 모두 유효하며 AEM에서 지원됩니다. 그러나 특정 모델을 구현하기 전에 각 솔루션의 장단점을 고려해야 합니다.

| 부트스트랩 | 장점 | 단점 |
|---|---|---|
| AEM | AEM은<br>필요한 경우 삽입된 라이브러리를 관리하며, 리소스는 AEM에서만 유지 관리해야 합니다. | SPA 개발자에게 익숙하지 않은 경우 |
| Adobe I/O Runtime | SPA 개발자에게 더 친숙한 기능 | CSS 및 JavaScript와 같은 응용 프로그램에 필요한 Clientlib 리소스는 AEM 개발자가 [`allowProxy` 속성을 통해 사용할 수 있도록 해야 합니다.](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br>리소스는 AEM과 Adobe I/O 런타임 사이에 동기화되어야<br>합니다.SPA를 제작하려면 Adobe I/O Runtime용 프록시 서버가 필요할 수 있습니다 |

## SSR 계획 {#planning-for-ssr}

일반적으로 응용 프로그램의 일부만을 서버측에서 렌더링해야 합니다. 일반적인 예는 페이지의 초기 로드 시 접힌 항목 위에 표시되는 컨텐츠를 서버측에서 렌더링해야 하는 것입니다. 이렇게 하면 이미 렌더링된 컨텐츠를 클라이언트에 전달함으로써 시간을 절약할 수 있습니다. 사용자가 SPA와 상호 작용하면 추가 컨텐츠가 클라이언트에 의해 렌더링됩니다.

SPA에 대한 서버측 렌더링을 구현하려는 경우 SSR이 필요한 앱의 일부를 검토해야 합니다.

## SSR을 사용한 SPA 개발 {#developing-an-spa-using-ssr}

SPA 구성 요소는 클라이언트(브라우저) 또는 서버측에서 렌더링할 수 있습니다. 서버측에서 렌더링하면 창 크기 및 위치와 같은 브라우저 속성이 없습니다. 따라서 SPA 구성 요소는 렌더링될 위치를 예측할 수 없도록 그래픽이 되어야 합니다.

SSR을 활용하려면 서버측 렌더링을 담당하는 Adobe I/O Runtime과 AEM에 코드를 배포해야 합니다. 대부분의 코드는 동일하지만 서버별 작업은 다릅니다.

## AEM의 SSR for SPA {#ssr-for-spas-in-aem}

AEM의 SSR for SPA에는 앱 컨텐츠 서버측 렌더링을 위해 호출되는 Adobe I/O Runtime이 필요합니다. 앱의 HTL 내에서 컨텐츠를 렌더링하기 위해 Adobe I/O Runtime의 리소스가 호출됩니다.

AEM이 즉시 사용 가능한 Angular and Responsive SPA 프레임워크를 지원하는 것처럼 Angular 및 Reimate 앱에도 서버측 렌더링이 지원됩니다. 자세한 내용은 두 프레임워크에 대한 NPM 설명서를 참조하십시오.

* 반응: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* 각진: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

간단한 예를 보려면 [We.Retail 저널 앱을 참조하십시오](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). 전체 애플리케이션 서버를 렌더링합니다. 실제 사례는 아니지만 SSR을 구현하는 데 필요한 사항을 설명해줍니다.

>[!CAUTION]
>We. [Retail Journal 앱은](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) 데모 용도로만 사용되며 권장 Adobe I/O Runtime 대신 Node.js를 간단한 예로 사용합니다. 이 예제는 프로젝트 작업에 사용할 수 없습니다.

>[!NOTE]
>모든 AEM 프로젝트는 [AEM 프로젝트 원형](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)(React or Angular)을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 프로젝트 전형(Pretype)을 활용해야 합니다.

## Node.js 사용 {#using-node-js}

AEM에서 SSR for SPA를 구현할 수 있는 권장 솔루션인 Adobe I/O Runtime

사전 설정 AEM 인스턴스의 경우 위에서 설명한 것과 동일한 방식으로 사용자 지정 Node.js 인스턴스를 사용하여 SSR을 구현할 수도 있습니다. 이 기능은 Adobe에서 지원되지만 권장되지 않습니다.

Node.js는 Adobe 호스팅 AEM 인스턴스에 대해 지원되지 않습니다.

>[!NOTE]
>
>SSR을 Node.js를 통해 구현해야 하는 경우, Adobe은 모든 AEM 환경(작성자, 게시, 스테이지 등)에 대해 별도의 Node.js 인스턴스를 권장합니다.

## 원격 컨텐츠 렌더러 {#remote-content-renderer}

AEM에서 SSR을 SPA와 함께 사용하는 데 필요한 [원격 컨텐츠 렌더러 구성](#remote-content-renderer-configuration) (Remote Content Renderer Configuration)은 보다 일반화된 렌더링 서비스로, 필요에 따라 확장 및 사용자 정의할 수 있습니다.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` 는 Adobe I/O와 같이 원격 서버에서 렌더링된 내용을 검색하는 OSGi 서비스입니다. 원격 서버로 보낸 내용은 전달된 요청 매개 변수를 기반으로 합니다.

`RemoteContentRenderingService` 추가 컨텐츠 조작이 필요할 때 종속성 전환을 통해 사용자 지정 Sling 모델 또는 서블릿에 삽입할 수 있습니다.

이 서비스는 [RemoteContentRendererRequestHandlerServlet에서 내부적으로 사용됩니다](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

요청 구성을 프로그래밍 방식으로 설정하는 데 사용할 `RemoteContentRendererRequestHandlerServlet` 수 있습니다. `DefaultRemoteContentRendererRequestHandlerImpl`, 제공된 기본 요청 처리기 구현에서는 컨텐츠 구조의 위치를 원격 끝점에 매핑하기 위해 여러 OSGi 구성을 만들 수 있습니다.

사용자 지정 요청 핸들러를 추가하려면 `RemoteContentRendererRequestHandler` 인터페이스를 구현합니다. 구성 요소 `Constants.SERVICE_RANKING` 속성은 해당 속성의 등급인 100보다 높은 정수로 설정해야 `DefaultRemoteContentRendererRequestHandlerImpl`합니다.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### 기본 핸들러의 OSGi 구성 {#configure-default-handler}

기본 핸들러의 구성은 원격 컨텐츠 렌더러 구성 섹션에 설명된 대로 [구성해야 합니다](#remote-content-renderer-configuration).

###  원격 컨텐츠 렌더러 사용 {#usage}

서블릿을 가져와 페이지에 삽입할 수 있는 일부 컨텐츠를 반환하려면:

1. 원격 서버에 액세스할 수 있는지 확인합니다.
1. AEM 구성 요소의 HTL 템플릿에 다음 코드 조각 중 하나를 추가합니다.
1. OSGi 구성을 만들거나 수정할 수도 있습니다.
1. 사이트 컨텐츠 찾아보기

일반적으로 페이지 구성 요소의 HTL 템플릿은 이러한 기능의 기본 수신자입니다.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### 요구 사항 {#requirements}

이 서블릿은 Sling Model Exporter를 활용하여 구성 요소 데이터의 일련화를 수행합니다. 기본적으로 `com.adobe.cq.export.json.ContainerExporter` 및 `com.adobe.cq.export.json.ComponentExporter` 는 모두 슬링 모델 어댑터로 지원됩니다. 필요한 경우, 요청을 사용하고 구현에 맞게 조정해야 하는 클래스를 추가할 수 `RemoteContentRendererServlet` 있습니다 `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. 추가 클래스는 해당 클래스를 확장해야 합니다 `ComponentExporter`.
