---
title: 적응형 양식 현지화를 위한 새 로케일 지원
seo-title: Supporting new locales for adaptive forms localization
description: AEM Forms에서는 적응형 양식을 현지화하기 위해 새 로케일을 추가할 수 있습니다. 기본적으로 지원되는 로케일은 영어, 프랑스어, 독일어 및 일본어입니다.
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. The supported locales by default are English, French, German, and Japanese.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
feature: Adaptive Forms
role: Admin
exl-id: 9f0e7284-ac11-406d-8d8c-7682f1d66fff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 1%

---

# 적응형 양식 현지화를 위한 새 로케일 지원 {#supporting-new-locales-for-adaptive-forms-localization}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 로케일 사전 정보 {#about-locale-dictionaries}

적응형 양식의 현지화는 다음 두 가지 로케일 사전 유형을 사용합니다.

**양식별 사전** 적응형 양식에 사용된 문자열을 포함합니다. 예를 들어 레이블, 필드 이름, 오류 메시지, 도움말 설명 등이 있습니다. 이 파일은 각 로케일에 대한 XLIFF 파일 세트로 관리되며 https://에서 액세스할 수 있습니다`<host>`:`<port>`/libs/cq/i18n/translator.html

**글로벌 사전** AEM 클라이언트 라이브러리에는 JSON 개체로 관리되는 두 개의 글로벌 사전이 있습니다. 이러한 사전은 기본 오류 메시지, 월 이름, 통화 기호, 날짜 및 시간 패턴 등을 포함합니다. 이러한 사전은 CRXDe Lite에서 /libs/fd/xfaforms/clientlibs/I18N에 있습니다. 이러한 위치에는 각 로케일에 대한 별도의 폴더가 포함되어 있습니다. 글로벌 사전은 일반적으로 자주 업데이트되지 않으므로 각 로케일에 대해 별도의 JavaScript 파일을 유지하면 브라우저에서 이를 캐싱하고 동일한 서버에서 다른 적응형 양식에 액세스할 때 네트워크 대역폭 사용을 줄일 수 있습니다.

### 적응형 양식 현지화 작동 방식 {#how-localization-of-adaptive-form-works}

적응형 양식을 렌더링하면 지정된 순서로 다음 매개 변수를 보고 요청된 로케일을 식별합니다.

* 요청 매개 변수 `afAcceptLang`

   사용자의 브라우저 로케일을 재정의하려면 `afAcceptLang` 요청 매개 변수를 사용하여 로케일을 강제 적용합니다. 예를 들어 다음 URL은 일본어 로케일로 양식을 렌더링합니다.

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* 사용자에 대해 설정된 브라우저 로케일입니다. 이 로켈은 `Accept-Language` 헤더.

* AEM에 지정된 사용자의 언어 설정입니다.

로케일이 식별되면 적응형 양식이 양식 특정 사전을 선택합니다. 요청된 로케일에 대한 양식 특정 사전을 찾을 수 없으면 영어(en) 사전이 사용됩니다.

요청된 로캘에 대한 클라이언트 라이브러리가 없는 경우 클라이언트 라이브러리에서 로케일에 있는 언어 코드를 확인합니다. 예를 들어, 요청된 로케일이 `en_ZA` (남아프리카 영어) 및 클라이언트 라이브러리 `en_ZA` 은 존재하지 않으며 적응형 양식에서는 클라이언트 라이브러리를 `en` (영어) 언어입니다. 그러나 이들 중 어느 것도 존재하지 않는 경우에는 적응형 양식에서에 사전을 사용합니다 `en` 로케일.

## 지원되지 않는 로케일에 대한 지역화 지원 추가 {#add-localization-support-for-non-supported-locales}

AEM Forms은 현재 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어(pt-BR, 중국어(zh-CN), 중국어(zh-TW) 및 한국어(ko-KR) 로케일로 적응형 양식 컨텐츠의 지역화를 지원합니다.

적응형 양식 런타임 시 새 로케일에 대한 지원을 추가하려면 다음을 수행합니다.

1. [GuideLocalizationService 서비스에 로케일 추가](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [로케일에 대한 XFA 클라이언트 라이브러리 추가](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [로케일에 대한 적응형 양식 클라이언트 라이브러리 추가](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [사전에 대한 로케일 지원 추가](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [서버 다시 시작](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### 안내서 로컬라이제이션 서비스에 로케일 추가 {#add-a-locale-to-the-guide-localization-service-br}

1. 이동 `https://[server]:[port]/system/console/configMgr`.
1. 을(를) 클릭하여 편집합니다 **Guide Localization Service** 구성 요소.
1. 지원되는 로케일 목록에 추가할 로케일을 추가합니다.

![GuideLocalizationService](assets/configservice.png)

### 로케일에 대한 XFA 클라이언트 라이브러리 추가 {#add-xfa-client-library-for-a-locale-br}

유형의 노드 만들기 `cq:ClientLibraryFolder` 아래에 `etc/<folderHierarchy>`, 카테고리 포함 `xfaforms.I18N.<locale>`를 검색하고 다음 파일을 클라이언트 라이브러리에 추가합니다.

* **I18N.js** 정의 `xfalib.locale.Strings` 대상 `<locale>` 에 정의된 대로 `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt** 다음 포함:

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### 로케일에 대한 적응형 양식 클라이언트 라이브러리 추가 {#add-adaptive-form-client-library-for-a-locale-br}

유형의 노드 만들기 `cq:ClientLibraryFolder` 아래에 `etc/<folderHierarchy>`, 카테고리를 로 사용 `guides.I18N.<locale>` 및 종속 항목을 `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` 및 `guide.common`. &quot;

클라이언트 라이브러리에 다음 파일을 추가합니다.

* **i18n.js** 정의 `guidelib.i18n`, &quot;calendarSymbol&quot; 패턴이 있는 경우 `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` 대상 `<locale>` 에 설명된 대로 [로케일 집합 사양](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf). 또한 의 다른 지원되는 로케일에 대해 정의된 방법을 확인할 수 있습니다 `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.js** 정의 `guidelib.i18n.strings` 및 `guidelib.i18n.LogMessages` 대상 `<locale>` 에 정의된 대로 `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

* **js.txt** 다음 포함:

```
i18n.js
LogMessages.js
```

### 사전에 대한 로케일 지원 추가 {#add-locale-support-for-the-dictionary-br}

다음 경우에만 이 단계를 수행합니다. `<locale>` 을(를) 추가할 때 `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. 만들기 `nt:unstructured` 노드 `languages` 아래에 `etc`: 아직 없는 경우.

1. 여러 값을 갖는 문자열 속성 추가 `languages` 아직 없는 경우 노드에 추가합니다.
1. 추가 `<locale>` 기본 로케일 값 `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`: 아직 없는 경우.

1. 추가 `<locale>` 의 값으로 `languages` 속성 `/etc/languages`.

다음 `<locale>` 에 표시됩니다. `https://[server]:[port]/libs/cq/i18n/translator.html`.

### 서버 다시 시작 {#restart-the-server}

추가된 로케일을 적용하려면 AEM 서버를 다시 시작합니다.

## 스페인어 지원을 추가하기 위한 샘플 라이브러리 {#sample-libraries-for-adding-support-for-spanish}

스페인어 지원을 추가하기 위한 샘플 클라이언트 라이브러리

[파일 가져오기](assets/sample.zip)
