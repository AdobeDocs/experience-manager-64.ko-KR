---
title: 페이지 내보내기
seo-title: 페이지 내보내기
description: AEM 페이지 내보내기 기능을 사용하는 방법을 알아봅니다.
seo-description: AEM 페이지 내보내기 기능을 사용하는 방법을 알아봅니다.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
translation-type: tm+mt
source-git-commit: aac5026a249e1cb09fec66313cc03b58597663f0
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# 페이지 내보내기{#the-page-exporter}

AEM에서는 이미지, .js 및 .css 파일을 비롯한 전체 웹 페이지로 페이지를 내보낼 수 있습니다.

내보내기가 구성되면 URL에서 `html`을 `export.zip`으로 대체하여 브라우저에 페이지를 요청하기만 하면 렌더링된 페이지와 참조된 에셋이 포함된 zip 파일 다운로드를 받을 수 있습니다. 페이지에 있는 모든 경로(예: 이미지 경로)는 zip 파일에 포함된 파일 또는 서버의 리소스를 가리키도록 다시 작성됩니다.

## 페이지 {#exporting-a-page} 내보내기

다음 단계에서는 페이지를 내보내는 방법을 설명하고 사이트에 대한 내보내기 구성 템플릿이 있다고 가정합니다. 구성 템플릿은 페이지를 내보내는 방법을 정의하며, 사이트에 따라 다릅니다. 구성 템플릿을 만들려면 [사이트](#creating-a-page-exporter-configuration-for-your-site) 섹션에 대한 페이지 내보내기 구성 만들기 섹션을 참조하십시오.

페이지를 내보내려면:

1. 브라우저에서 페이지를 엽니다. 예:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. 페이지 속성 대화 상자를 열고 **고급** 탭을 선택하고 **내보내기** 필드 세트를 확장합니다.

1. 돋보기 아이콘을 클릭하고 구성 템플릿을 선택합니다. Geometrixx 사이트의 기본 템플릿이므로 **geometrixx** 템플릿을 선택합니다. **확인**&#x200B;을 클릭합니다.

1. **확인**&#x200B;을 클릭하여 페이지 속성 대화 상자를 닫습니다.
1. URL에서 `html`을 `export.zip`으로 대체하여 페이지를 요청합니다.

1. 파일 시스템에 `<page-name>.export.zip` 파일을 다운로드합니다.

1. 파일 시스템에서 파일의 압축을 해제합니다.

   * 페이지 html 파일( `<page-name>.html`)은 `<unzip-dir>/<page-path>` 아래에서 사용할 수 있습니다.
   * 다른 리소스(.js 파일, .css 파일, 이미지, ...)는 내보내기 템플릿의 설정에 따라 찾을 수 있습니다. 이 예에서 일부 리소스는 `<unzip-dir>/etc` 아래에 있고 일부는 `<unzip-dir>/<page-path>` 아래에 있습니다.

1. 브라우저에서 페이지 html 파일( `<unzip-dir>/<page-path>.html`)을 열어 렌더링을 확인합니다.

## {#creating-a-page-exporter-configuration-for-your-site} 사이트에 대한 페이지 내보내기 구성 만들기

페이지 내보내기는 컨텐츠 동기화 프레임워크를 기반으로 합니다. 페이지 속성 대화 상자에서 사용할 수 있는 구성은 구성 템플릿입니다. 페이지에 필요한 모든 종속성을 정의합니다. 페이지 내보내기가 트리거되면 구성 템플릿이 사용되고 페이지 경로와 디자인 경로가 구성에 동적으로 적용됩니다. 그런 다음 표준 컨텐츠 동기화 기능을 사용하여 zip 파일을 만듭니다.

AEM에는 다음과 같은 몇 가지 템플릿이 포함되어 있습니다.

* `/etc/contentsync/templates/default`에 있는 기본 설정입니다. 이 템플릿:

   * 저장소에 구성 템플릿이 없을 때 폴백 템플릿입니다.
   * 새 구성 템플릿의 기초로 사용할 수 있습니다.

* `/etc/contentsync/templates/geometrixx`에서 **Geometrixx** 사이트에 대한 전용 사이트입니다. 이 템플릿을 예로 사용하여 새 템플릿을 만들 수 있습니다.

페이지 내보내기 구성 템플릿을 만들려면:

1. **CRXDE Lite**&#x200B;에서 `/etc/contentsync/templates` 아래에 노드를 만듭니다.

   * 이름:예:`mysite`. 페이지 내보내기 템플릿을 선택할 때 페이지 속성 대화 상자에 이름이 나타납니다.
   * 유형: `nt:unstructured`

1. 여기서 `mysite`이라고 하는 템플릿 노드 아래에 아래 설명된 구성 노드를 사용하여 노드 구조를 만듭니다.

### 페이지 내보내기 구성 노드 {#page-exporter-configuration-nodes}

구성 템플릿은 노드 구조로 구성됩니다. 각 노드에는 zip 파일의 작성 프로세스에서 특정 작업을 정의하는 `type` 속성이 있습니다. 유형 속성에 대한 자세한 내용은 Content Sync 프레임워크 페이지의 구성 유형 개요 섹션을 참조하십시오.

다음 노드를 사용하여 내보내기 구성 템플릿을 작성할 수 있습니다.

**페이지** 노드페이지 html을 zip 파일에 복사하는 데 페이지 노드가 사용됩니다. 다음과 같은 특성이 있습니다.

* 필수 노드입니다.
* `/etc/contentsync/templates/<sitename>` 아래에 있습니다.
* 이름은 `page`입니다.
* 해당 노드 유형은 `nt:unstructured`입니다.

`page` 노드에는 다음 속성이 있습니다.

* `pages` 값이 있는 `type` 속성 집합.

* 현재 페이지 경로가 구성에 동적으로 복사되므로 `path` 속성이 없습니다.

* 다른 속성은 Content Sync 프레임워크의 구성 유형 개요 섹션에 설명되어 있습니다.

**다시 작성** 노드다시 작성 노드는 내보낸 페이지에서 링크가 어떻게 재작성되는지 정의합니다. 새로 작성된 링크는 zip 파일에 포함된 파일이나 서버의 리소스를 가리킬 수 있습니다.

`rewrite` 노드에 대한 전체 설명은 컨텐츠 동기화 페이지를 참조하십시오.

**디자인** 노드디자인 노드는 내보낸 페이지에 사용되는 디자인을 복사하는 데 사용됩니다. 다음과 같은 특성이 있습니다.

* 선택 사항입니다.
* `/etc/contentsync/templates/<sitename>` 아래에 있습니다.
* 이름은 `design`입니다.
* 노드 유형은 `nt:unstructured`입니다.

`design` 노드에는 다음 속성이 있습니다.

* `type` 속성이 `copy` 값으로 설정되었습니다.

* 현재 페이지 경로가 구성에 동적으로 복사되므로 `path` 속성이 없습니다.

**범용 노드** 는 clientlibs .js 또는 .css 파일과 같은 리소스를 zip 파일로 복사하는 데 사용됩니다. 다음과 같은 특성이 있습니다.

* 선택 사항입니다.
* `/etc/contentsync/templates/<sitename>` 아래에 있습니다.
* 특정 이름이 없습니다.
* 노드 유형은 `nt:unstructured`입니다.
* Content Sync 프레임워크의 구성 유형 개요 섹션에 정의된 대로 `type` 속성과 `type` 관련 속성이 있습니다.

예를 들어 다음 구성 노드는 geometrixx clientlibs .js 파일을 zip 파일로 복사합니다.

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

**Geometrixx** 페이지 내보내기 구성 템플릿은 페이지 내보내기를 구성하는 방법을 보여줍니다. 브라우저에서 템플릿의 노드 구조를 json 형식으로 보려면 다음 URL을 요청하십시오.

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**사용자 지정 구성 구현**

노드 구조에서 알아보았듯이 **Geometrixx** 페이지 내보내기 구성 템플릿에는 `type` 속성이 `image`로 설정된 `logo` 노드가 있습니다. 이미지 로고를 zip 파일에 복사하도록 만들어진 특수 구성 유형입니다. 특정 요구 사항을 충족하려면 사용자 지정 `type` 속성을 구현해야 할 수 있습니다.이렇게 하려면 콘텐츠 동기화 페이지의 사용자 지정 업데이트 처리기 구현 섹션을 참조하십시오.

## 프로그래밍 방식으로 페이지 {#programmatically-exporting-a-page} 내보내기

페이지를 프로그래밍 방식으로 내보내려면 [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI 서비스를 사용할 수 있습니다. 이 서비스를 통해 다음과 같은 작업을 수행할 수 있습니다.

* 페이지를 내보내고 HTTP 서블릿 응답으로 씁니다.
* 페이지를 내보내고 특정 위치에 zip 파일을 저장합니다.

`export` 선택기에 바인딩되고 `zip` 확장의 서블릿은 PageExporter 서비스를 사용합니다.

## 문제 해결 {#troubleshooting}

zip 파일의 다운로드에 문제가 있는 경우 저장소의 `/var/contentsync` 노드를 삭제하고 내보내기 요청을 다시 보낼 수 있습니다.

