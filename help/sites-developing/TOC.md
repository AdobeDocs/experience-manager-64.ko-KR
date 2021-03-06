---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: AEM 6.4 개발 사용 안내서
breadcrumb-title: Developing 안내서
user-guide-description: 이 안내서에서는 AEM 인스턴스를 빌드하는 방법을 다룹니다.
feature: Developing
role: Developer
source-git-commit: 35aea0e087334a1c1e6a708f2182bd9dee799dc0
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 92%

---


# AEM 6.4 개발 사용 안내서 {#developing}

+ [개발 사용 안내서 개요](home.md)
+ 개발자를 위한 소개{#introduction}
   + [AEM Sites 개발 시작하기 - WKND 튜토리얼](getting-started.md)
   + [AEM 코어 개념](the-basics.md)
   + [AEM 터치 지원 UI의 구조](touch-ui-structure.md)
   + [AEM 터치 지원 UI의 개념](touch-ui-concepts.md)
   + [AEM 개발 - 지침 및 우수 사례](dev-guidelines-bestpractices.md)
   + [클라이언트측 라이브러리 사용](clientlibs.md)
   + [개발 및 페이지 비교](pagediff.md)
   + [편집기 제한 사항](editor-limitations.md)
   + [CSRF 보호 프레임워크](csrf-protection.md)
   + [데이터 모델링 - David Nuescheler의 모델](model-data.md)
   + [AEM에 기여](contributing-to-cq.md)
   + [보안](security.md)
   + [참조 자료](reference-materials.md)
   + [모든 기능을 갖춘 웹 사이트 만들기(클래식 UI)](website.md)
   + [디자인과 디자이너(클래식 UI)](designer.md)
+ 플랫폼{#platform}
   + [슬링 치트시트](sling-cheatsheet.md)
   + [Sling 어댑터 사용](sling-adapters.md)
   + [태그 라이브러리](taglib.md)
   + 템플릿{#templates}
      + [템플릿](templates.md)
      + [페이지 템플릿 - 편집 가능 ](page-templates-editable.md)
      + [페이지 템플릿 - 정적](page-templates-static.md)
      + [컨텐츠 조각 템플릿](content-fragment-templates.md)
      + [적응형 템플릿 렌더링](templates-adaptive-rendering.md)
   + [AEM에서 Sling Resource Merger 사용](sling-resource-merger.md)
   + [오버레이](overlays.md)
   + [이름 지정 규칙](naming-conventions.md)
   + [새로운 Granite UI 필드 구성 요소 만들기](granite-ui-component.md)
   + QueryBuilder{#query-builder}
      + [Query Builder의 사용자 지정 설명 평가기 구현](implementing-custom-predicate-evaluator.md)
      + [쿼리 빌더 술어 참조](querybuilder-predicate-reference.md)
      + [쿼리 빌더 API](querybuilder-api.md)
   + 태깅{#tagging}
      + [태깅](tags.md)
      + [AEM 태그 지정 프레임워크](framework.md)
      + [AEM 애플리케이션에 태깅 작성](building.md)
   + [오류 핸들러로 표시된 페이지 사용자 지정](customizing-errorhandler-pages.md)
   + [사용자 지정 노드 유형](custom-nodetypes.md)
   + [그래픽 렌더링용 글꼴 추가](adding-fonts.md)
   + [SQL 데이터베이스에 연결](jdbc.md)
   + [URL 표면화](externalizer.md)
   + [오프로드용 작업 만들기 및 소비](dev-offloading.md)
   + [쿠키 사용 구성](cookie-optout.md)
   + [프로그래밍 방식으로 AEM JCR에 액세스하는 방법](access-jcr.md)
   + [JMX 콘솔과 서비스 통합](jmx-integration.md)
   + [벌크 편집기 개발](dev-bulk-editor.md)
   + [보고서 개발](dev-reports.md)
   + eCommerce{#ecommerce}
      + [eCommerce](ecommerce.md)
      + [개발(일반)](generic.md)
      + [SAP Commerce Cloud를 사용하여 개발](sap-commerce-cloud.md)
+ 구성 요소{#components}
   + [코어 구성 요소](https://docs.adobe.com/content/help/ko/experience-manager-core-components/using/introduction.html)
   + [스타일 시스템](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/siteandpage/style-system.html)
   + [구성 요소 개요](components.md)
   + [AEM 구성 요소 - 기본 사항](components-basics.md)
   + [AEM 구성 요소 개발](developing-components.md)
   + [AEM 구성 요소 개발 - 코드 샘플](developing-components-samples.md)
   + [콘텐츠 서비스에 대한 JSON 내보내기](json-exporter.md)
   + [구성 요소에 대해 JSON 내보내기 활성화](json-exporter-components.md)
   + [이미지 편집기](image-editor.md)
   + [장식 태그](decoration-tag.md)
   + [조건 숨기기 사용](hide-conditions.md)
   + [여러 즉석 편집기 구성](multiple-inplace-editors.md)
   + [개발자 모드](developer-mode.md)
   + [UI 테스트](hobbes.md)
   + [컨텐츠 조각용 구성 요소](components-content-fragments.md)
   + [JSON 형식으로 페이지 정보 얻기](pageinfo.md)
   + 다국어화{#internationalization}
      + [구성 요소 다국어화](i18n.md)
      + [UI 문자열 다국어화](i18n-dev.md)
      + [번역기를 사용하여 사전 관리](i18n-translator.md)
      + [번역할 문자열 추출](i18n-extract.md)
   + 클래식 UI 구성 요소{#classic-ui-components}
      + [AEM 구성 요소 개발(클래식 UI)](developing-components-classic.md)
      + [위젯 사용 및 확장(클래식 UI)](widgets.md)
      + [xtype 사용(클래식 UI)](xtypes.md)
      + [양식 개발(클래식 UI)](developing-forms.md)
+ 헤드리스 환경 관리{#headless}
   + [AEM을 사용한 헤드리스 및 하이브리드](https://business.adobe.com/content/dam/dx/us/en/products/experience-manager/sites/headless-content-management-system/pdfs/aem-hybrid-architecture-wp-1-18-19.pdf)
   + [구성 요소에 대해 JSON 내보내기 활성화](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/json-exporter-components.html)
   + SPA(Single Page Applications){#spas}
      + [SPA 소개 및 워크스루](spa-walkthrough.md)
      + [SPA WKND 튜토리얼](spa-wknd.md)
      + [AEM에서 SPA 시작하기 - React](spa-getting-started-react.md)
      + [AEM에서 SPA 시작하기 - Angular](spa-getting-started-angular.md)
      + [SPA에 대한 React 구성 요소 구현](spa-implementing-react-component.md)
      + [SPA 깊이 들어가기](spa-deep-dives.md)
      + [SPA 편집기 개요](spa-overview.md)
      + [AEM용 SPA 개발](spa-architecture.md)
      + [SPA 블루프린트](spa-blueprint.md)
      + [SPA 페이지 구성 요소](spa-page-component.md)
      + [구성 요소 매핑을 위한 동적 모델 SPA](spa-dynamic-model-to-component-mapping.md)
      + [SPA 모델 라우팅](spa-routing.md)
      + [SPA 및 Adobe Experience Platform Launch 통합](spa-launch.md)
      + [SPA 및 서버측 렌더링](spa-ssr.md)
      + [SPA 참조 자료](spa-reference-materials.md)
   + [HTTP API](https://experienceleague.adobe.com/docs/experience-manager-64/assets/extending/mac-api-assets.html)
   + [컨텐츠 조각](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments.html)
   + [경험 조각](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/authoring/experience-fragments.html)
   + [AEM의 컨텐츠 조각과 컨텐츠 서비스 이해](https://helpx.adobe.com/kr/experience-manager/kt/sites/using/content-fragments-content-services-feature-video-understand.html)
+ 개발 도구{#devtools}
   + [개발 도구](dev-tools.md)
   + [AEM 현대화 도구](modernization-tools.md)
   + [대화 상자 편집기](dialog-editor.md)
   + [대화 상자 변환 도구](dialog-conversion.md)
   + [CRXDE Lite를 사용한 개발](developing-with-crxde-lite.md)
   + [Maven을 사용한 패키지 관리](vlt-mavenplugin.md)
   + [Eclipse를 사용하여 AEM 프로젝트를 개발하는 방법](howto-projects-eclipse.md)
   + [Apache Maven을 사용하여 AEM 프로젝트를 작성하는 방법](ht-projects-maven.md)
   + [IntelliJ IDEA를 사용하여 AEM 프로젝트를 개발하는 방법](ht-intellij.md)
   + [VLT 도구 사용 방법](ht-vlttool.md)
   + [프록시 서버 도구 사용 방법](ht-proxy-server.md)
   + [AEM Brackets 확장](aem-brackets.md)
   + [Eclipse용 AEM 개발자 도구](aem-eclipse.md)
   + [AEM 저장소 도구](aem-repo-tool.md)
+ 개인화{#personlization}
   + [ContextHub](contexthub.md)
   + [ContextHub Javascript API 참조](contexthub-api.md)
   + [ContextHub 확장](ch-extend.md)
   + [페이지에 ContextHub 추가 및 저장소 액세스](ch-adding.md)
   + [샘플 ContextHub 저장소 후보](ch-samplestores.md)
   + [샘플 ContextHub UI 모듈 유형](ch-samplemodules.md)
   + [ContextHub 진단](ch-diagnostics.md)
   + [타깃팅된 컨텐츠를 위한 개발](target.md)
   + Client Context{#client-context}
      + [Client Context 관련 세부 사항](client-context.md)
      + [Client Context Javascript API](ccjsapi.md)
+ AEM 확장{#extending-aem}
   + [페이지 작성 사용자 지정](customizing-page-authoring-touch.md)
   + [콘솔 사용자 지정](customizing-consoles-touch.md)
   + [페이지 속성 보기 사용자 지정](page-properties-views.md)
   + [페이지 속성의 벌크 편집을 위한 페이지 구성](bulk-editing.md)
   + [콘텐츠 조각 맞춤화 및 확장](customizing-content-fragments.md)
   + 워크플로우 확장{#extending-workflows}
      + [워크플로 개발 및 확장](workflows.md)
      + [워크플로 모델 만들기](workflows-models.md)
      + [워크플로 기능 확장](workflows-customizing-extending.md)
      + [프로그래밍 방식으로 워크플로우와 상호 작용](workflows-program-interaction.md)
      + [워크플로 단계 참조](workflows-step-ref.md)
      + [워크플로우 우수 사례](workflows-best-practices.md)
      + [워크플로 프로세스 참조](workflows-process-ref.md)
   + [다중 사이트 관리자 확장](extending-msm.md)
   + 추적 및 분석{#extending-analytics}
      + [이벤트 추적 확장](extending-analytics.md)
      + [구성 요소에 Adobe Analytics 추적 추가](extending-analytics-components.md)
      + [Adobe Analytics 프레임워크 사용자 지정](extending-analytics-framework.md)
      + [Analytics에 대한 서버측 페이지 이름 지정 구현](extending-analytics-pa-naming.md)
   + 클라우드 서비스{#extending-cloud-services}
      + [클라우드 서비스 구성](extending-cloud-config.md)
      + [사용자 지정 클라우드 서비스 만들기](extending-cloud-config-custom-cloud.md)
   + [사용자 지정 확장 프로그램 만들기](extending-campaign-extensions.md)
   + 양식{#extending-forms}
      + [사용자 지정 양식 매핑 만들기](extending-campaign-form-mapping.md)
      + [Adobe Campaign 양식 구성 요소를 사용하여 사용자 지정 AEM 페이지 템플릿 만들기](extending-campaign-custom-template.md)
      + [분석 요청 스크립트](analyze-request.md)
   + [JMX 콘솔과 서비스 통합](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/jmx-integration.html)
   + [벌크 편집기 개발](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-bulk-editor.html)
   + 클래식 UI 확장{#extending-classic-ui}
      + [웹 사이트 콘솔 사용자 지정(클래식 UI)](customizing-siteadmin.md)
      + [시작 콘솔 사용자 지정(클래식 UI)](customizing-the-welcome-console.md)
      + [보고서 개발](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-reports.html)
+ 테스트{#testing}
   + [계획](planning.md)
   + [어떤 테스트 환경이 필요합니까?](test-environments.md)
   + [테스트 사례 정의](test-cases.md)
   + [테스트 - 언제 누구와 함께?](when-who.md)
   + [테스트 계획 컴파일](test-plan.md)
   + [결과 추적 및 피드백 제공](results-and-feedback.md)
   + [테스트 및 추적 도구](tools.md)
   + [수락 및 승인](acceptance-signoff.md)
   + [다음 릴리스...](the-next-release.md)
   + [확인 목록](checklists.md)
   + [Tough Day](tough-day.md)
   + [UI 테스트](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/hobbes.html)
+ 우수 사례{#bestpractices}
   + [우수 사례 개요](best-practices.md)
   + [AEM 개발 지침 및 우수 사례](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/dev-guidelines-bestpractices.html)
   + [개발 우수 사례](development-practices.md)
   + [컨텐츠 아키텍처](content-architecture.md)
   + [소프트웨어 아키텍처](software-architecture.md)
   + We.Retail 참조 구현{#we-retail}
      + [We.Retail 참조 구현](we-retail.md)
      + [We.Retail에서 컨텐츠 조각 시험 사용](we-retail-content-fragments.md)
      + [We.Retail에서 핵심 구성 요소 시험 사용](we-retail-core-components.md)
      + [We.Retail에서 편집 가능한 템플릿 시험 사용](we-retail-editable-templates.md)
      + [We.Retail에서 응답형 레이아웃 시험 사용](we-retail-responsive-layout.md)
      + [We.Retail에서 세계화된 사이트 구조 시험 사용](we-retail-globalized-site-structure.md)
      + [We.Retail에서 경험 조각 시험 사용](we-retail-experience-fragments.md)
   + [코딩 팁](coding-tips.md)
   + [코드 함정](code-pitfalls.md)
   + [OSGI 번들](osgi-bundles.md)
   + [JCR 통합](jcr-integration.md)
   + [코드 샘플](code-samples.md)
   + [느린 쿼리 문제 해결](troubleshooting-slow-queries.md)
+ 모바일 웹{#mobileweb}
   + [모바일 웹](mobile-web.md)
   + [장치 그룹 필터 만들기](groupfilters.md)
   + [웹 페이지를 위한 응답형 디자인](responsive.md)
   + [모바일 장치용 사이트 만들기](mobile.md)
   + [에뮬레이터](emulators.md)
