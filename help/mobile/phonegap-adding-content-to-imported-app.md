---
title: 하이브리드 앱을 AEM Mobile에 사용할 준비가 되었습니까?
seo-title: Is your hybrid app ready for AEM Mobile?
description: 하이브리드 앱에 대해 알려면 이 페이지를 따르십시오. AEM의 앱은 일반적으로 두 부분으로 나누어집니다. 'shell'과 'content' 및 이 페이지는 이러한 주제에 대한 더 많은 통찰력을 제공합니다.
seo-description: Follow this page to learn about hrybrid apps. An app in AEM is commonly divided into two parts. The 'shell' and 'content' and this page provides more insight on these topics.
uuid: cbcce3fa-9100-46ea-9f24-931b42666709
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: b7fd7954-f2a5-402d-b259-e18b5a618be9
pagetitle: Is your hybrid app ready for AEM Mobile?
exl-id: 79eafdb5-8b83-466a-8d06-da1a655a0619
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 1%

---

# 하이브리드 앱을 AEM Mobile에 사용할 준비가 되었습니까?{#is-your-hybrid-app-ready-for-aem-mobile}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>단일 페이지 애플리케이션 프레임워크 기반 클라이언트측 렌더링(예: React)이 필요한 프로젝트에 SPA 편집기를 사용하는 것이 좋습니다. [자세히 알아보기](/help/sites-developing/spa-overview.md).

Hybrid PhoneGap 또는 Cordova 앱을 AEM으로 가져온 것은 무엇입니까? 앱에 작성 가능한 컨텐츠를 추가할 가능성이 있습니다. 이 작업을 수행하려면 AEM 앱의 구조를 전체적으로 이해해야 합니다. AEM의 앱은 일반적으로 두 부분으로 나누어집니다. &#39;shell&#39;과 &#39;content&#39;입니다. 쉘은 앱의 정적 부분으로 구성됩니다. PhoneGap 구성 파일, 앱 프레임워크 및 탐색 컨트롤과 같은 작업을 할 수 있습니다. 가져온 아카이브의 컨텐츠는 쉘의 일부로 저장됩니다. 이 문서의 컨텍스트에서 셸은 앱 개발자가 만든 AEM이 아닌 Hybrid PhoneGap 앱의 모든 컨텐츠입니다.

컨텐츠는 AEM 개발자가 작성한 AEM에서 작성된 구성 요소, 템플릿 및 작성된 페이지를 나타냅니다. 콘텐츠는 개발자 콘텐츠 또는 작성된 콘텐츠로 분류됩니다. 구성 요소, 디자인 및 페이지 템플릿은 개발자가 빌드하므로 개발 콘텐츠로 간주됩니다. 작성자 컨텐츠는 구성 요소 및 템플릿을 사용하여 작성된 페이지입니다. 이러한 작업은 일반적으로 디자이너 또는 마케터가 수행합니다.

Hybrid 앱에 작성된 AEM 페이지를 추가하려면 앱 개발자와 AEM 개발자 간의 조정이 필요합니다. 작성된 컨텐츠를 추가하려는 앱의 모든 위치에서 앱 개발자는 AEM에서 오버레이할 수 있는 구조로 이러한 페이지를 구성해야 합니다. 앱 개발자는 AEM에서 컨텐츠를 추가할 작성 위치에 대한 경로를 AEM 개발자에게 제공한 다음 AEM 개발자가 페이지 컨텐츠를 작성한 후 대체될 Hybrid 앱에서 자리 표시자 페이지를 제공할 수 있어야 합니다.

설명을 더 쉽게 따르도록 하기 위해 AEM Marketing Cloud을 사용합니다. AEM Mobile 하이브리드 참조 를 참조하십시오. 하이브리드 참조 앱은 사이드 메뉴가 있는 홈 페이지로 구성됩니다.

![chlimage_1-76](assets/chlimage_1-76.png)

이 예제에서는 애플리케이션의 시작 페이지를 작성하겠습니다. 소스 확인 [https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75). 앱 개발자가 시작 페이지를 정의하고 앱으로 렌더링되는 페이지에 대한 템플릿을 제공했음을 알 수 있습니다. 여기에서 앱 개발자와 AEM 개발자가 조정해야 합니다. 하이브리드 참조 앱의 시작 페이지 템플릿에 대한 경로는 &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot;로 정의됩니다. AEM 개발자가 동일한 경로를 사용하여 AEM 저장소에서 시작 페이지를 작성하므로 이 경로가 매우 중요합니다.

![chlimage_1-77](assets/chlimage_1-77.png)

하이브리드 앱에 새 페이지를 추가하기 위해 컨텐츠 동기화를 사용하여 컨텐츠를 오버레이하는 기능에 의존하므로 AEM에서 작성한 컨텐츠와 동일한 경로를 사용하는 것이 중요합니다. 가져오기 프로세스의 일부로 하이브리드 앱을 AEM으로 가져오는 경우 컨텐츠 동기화 구성이 설정됩니다.

![chlimage_1-78](assets/chlimage_1-78.png)

앱 대시보드에서 &#39;소스 다운로드&#39;를 사용하면 ContentSync 스크립트를 실행하여 하이브리드 앱의 아카이브를 어셈블합니다.

![chlimage_1-79](assets/chlimage_1-79.png)

ContentSync는 먼저 앱의 &#39;shell&#39;을 가져옵니다. 이 앱에서는 모든 앱에서 개발한 Hybrid 앱의 컨텐츠가 저장되어 앱의 &#39;content&#39;를 가져옵니다. 이제 &#39;content&#39;에 있는 경로와 동일한 경로가 &#39;shell&#39;에 있는 페이지가 있으면 &#39;shell&#39; 아래의 페이지가 &#39;content&#39; 아래의 페이지로 (대체됨)됩니다. 다시 말해, AEM에서 ContentSync를 실행할 때 &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot;과 동일한 경로를 갖는 페이지를 만들면 Hybrid 참조 앱의 일부인 페이지를 해당 위치에 있는 AEM에 있는 모든 페이지로 오버레이합니다. 오버레이는 ContentSync에서 처리되므로 앱을 사용하는 사용자의 경우 AEM에서 제작한 콘텐츠가 있는 앱에 대한 업데이트가 원활하게 표시되며 앱을 다시 빌드할 필요가 없습니다. 따라서 앱을 실행할 때 시작 페이지가 다음과 같이 나타납니다.

![chlimage_1-80](assets/chlimage_1-80.png)
