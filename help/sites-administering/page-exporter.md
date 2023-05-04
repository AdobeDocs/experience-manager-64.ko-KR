---
title: 페이지 내보내기
seo-title: The Page Exporter
description: AEM Page Exporter를 사용하는 방법을 알아봅니다.
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# 페이지 내보내기{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서는 이미지, .js 및 .css 파일을 포함하는 전체 웹 페이지로 페이지를 내보낼 수 있습니다.

내보내기가 구성되면 을 대체하여 브라우저에서 페이지를 요청하면 됩니다 `html` with `export.zip` 를 URL로 다운로드하면 html 형식으로 렌더링된 페이지와 참조된 자산이 포함된 zip 파일 다운로드가 제공됩니다. 페이지의 모든 경로(예: 이미지에 대한 경로)는 zip 파일에 포함된 파일 또는 서버의 리소스를 가리키도록 다시 작성됩니다.

## 페이지 내보내기 {#exporting-a-page}

다음 단계에서는 페이지를 내보내는 방법을 설명하고 사이트에 대한 내보내기 구성 템플릿이 있다고 가정합니다. 구성 템플릿은 페이지를 내보내는 방식을 정의하고 사이트에 따라 다릅니다. 구성 템플릿을 만들려면 다음을 참조하십시오. [사이트에 대한 페이지 내보내기 구성 만들기](#creating-a-page-exporter-configuration-for-your-site) 섹션을 참조하십시오.

페이지를 내보내려면:

1. 브라우저에서 페이지를 엽니다. 예:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. 페이지 속성 대화 상자를 열고 **고급** 탭 및 확장 **내보내기** 필드 집합입니다.

1. 돋보기 아이콘을 클릭하고 구성 템플릿을 선택합니다. 을(를) 선택합니다 **geometrixx** 템플릿(Geometrixx 사이트에 대한 기본 템플릿이므로). **확인**&#x200B;을 클릭합니다.

1. 클릭 **확인** 를 클릭하여 페이지 속성 대화 상자를 닫습니다.
1. 을 수정하여 페이지 요청 `html` with `export.zip` 를 입력합니다.

1. 다운로드 `<page-name>.export.zip` 파일을 파일 시스템에 추가합니다.

1. 파일 시스템에서 파일의 압축을 해제합니다.

   * 페이지 html 파일( `<page-name>.html`)는 아래에서 사용할 수 있습니다 `<unzip-dir>/<page-path>`
   * 다른 리소스(.js 파일, .css 파일, 이미지, ...)는 내보내기 템플릿의 설정에 따라 배치됩니다. 이 예제에서 몇 가지 리소스는 다음과 같습니다 `<unzip-dir>/etc`, 아래 `<unzip-dir>/<page-path>`.

1. 페이지 html 파일( `<unzip-dir>/<page-path>.html`)을 클릭하여 렌더링을 확인합니다.

## 사이트에 대한 페이지 내보내기 구성 만들기 {#creating-a-page-exporter-configuration-for-your-site}

페이지 내보내기는 콘텐츠 동기화 프레임워크를 기반으로 합니다. 페이지 속성 대화 상자에서 사용할 수 있는 구성은 구성 템플릿입니다. 페이지에 필요한 모든 종속성을 정의합니다. 페이지 내보내기가 트리거되면 구성 템플릿이 사용되며 페이지 경로와 디자인 경로가 모두 구성에 동적으로 적용됩니다. 그런 다음 표준 컨텐츠 동기화 기능을 사용하여 zip 파일을 만듭니다.

AEM에는 다음을 포함한 몇 가지 템플릿이 포함되어 있습니다.

* 기본 설정 위치 `/etc/contentsync/templates/default`. 이 템플릿:

   * 저장소에 구성 템플릿이 없을 때 대체 템플릿입니다.
   * 새 구성 템플릿의 기반으로 사용할 수 있습니다.

* 전용 **Geometrixx** 사이트, 위치 `/etc/contentsync/templates/geometrixx`. 이 템플릿을 예로 사용하여 새 템플릿을 만들 수 있습니다.

페이지 내보내기 구성 템플릿을 만들려면 다음을 수행하십시오.

1. in **CRXDE Lite**&#x200B;아래에 노드를 만드십시오 `/etc/contentsync/templates`:

   * 이름: 예 `mysite`. 페이지 내보내기 템플릿을 선택하면 페이지 속성 대화 상자에 이름이 표시됩니다.
   * 유형: `nt:unstructured`

1. 여기에 호출된 템플릿 노드 아래에 있습니다. `mysite`아래에 설명된 구성 노드를 사용하여 노드 구조를 만듭니다.

### 페이지 내보내기 구성 노드 {#page-exporter-configuration-nodes}

구성 템플릿은 노드 구조로 구성됩니다. 각 노드에는 `type` zip 파일의 작성 프로세스에서 특정 작업을 정의하는 속성입니다. 유형 속성에 대한 자세한 내용은 컨텐츠 동기화 프레임워크 페이지의 구성 유형 개요 섹션을 참조하십시오.

다음 노드를 사용하여 내보내기 구성 템플릿을 작성할 수 있습니다.

**페이지 노드** 페이지 노드는 페이지 html을 zip 파일에 복사하는 데 사용됩니다. 다음과 같은 특성이 있습니다.

* 는 필수 노드입니다.
* 은 아래에 있습니다 `/etc/contentsync/templates/<sitename>`.
* 이름은 입니다 `page`.
* 노드 유형은 다음과 같습니다. `nt:unstructured`

다음 `page` 노드에는 다음 속성이 있습니다.

* A `type` 값을 사용하여 설정된 속성 `pages`.

* 없습니다 `path` 현재 페이지 경로가 구성에 동적으로 복사됩니다.

* 다른 속성은 Content Sync 프레임워크의 구성 유형 개요 섹션에 설명되어 있습니다.

**재작성 노드** 다시 작성 노드는 내보낸 페이지에서 링크를 다시 작성하는 방법을 정의합니다. 다시 작성된 링크는 zip 파일에 포함된 파일 또는 서버의 리소스를 가리킬 수 있습니다.

자세한 내용은 컨텐츠 동기화 페이지 를 참조하십시오 `rewrite` 노드 아래에 있어야 합니다.

**디자인 노드** 디자인 노드는 내보낸 페이지에 사용되는 디자인을 복사하는 데 사용됩니다. 다음과 같은 특성이 있습니다.

* 는 선택 사항입니다.
* 은 아래에 있습니다 `/etc/contentsync/templates/<sitename>`.
* 이름은 입니다 `design`.
* 노드 유형은 다음과 같습니다. `nt:unstructured`.

다음 `design` 노드에는 다음 속성이 있습니다.

* A `type` 값으로 설정된 속성 `copy`.

* 없습니다 `path` 현재 페이지 경로가 구성에 동적으로 복사됩니다.

**범용 노드** 일반 노드는 clientlibs .js 또는 .css 파일과 같은 리소스를 zip 파일에 복사하는 데 사용됩니다. 다음과 같은 특성이 있습니다.

* 는 선택 사항입니다.
* 은 아래에 있습니다 `/etc/contentsync/templates/<sitename>`.
* 특정 이름이 없습니다.
* 노드 유형은 다음과 같습니다. `nt:unstructured`.
* 다음 포함 `type` 및 모든 `type` 관련 속성은 Content Sync 프레임워크의 구성 유형 개요 섹션에 정의되어 있습니다.

예를 들어 다음 구성 노드는 geometrixx clientlibs .js 파일을 zip 파일로 복사합니다.

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

다음 **Geometrixx** 페이지 내보내기 구성 템플릿은 페이지 내보내기를 구성하는 방법을 보여줍니다. 브라우저에서 템플릿의 노드 구조를 json 형식으로 보려면 다음 URL을 요청하십시오.

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**사용자 지정 구성 구현**

노드 구조에서는 **Geometrixx** 페이지 내보내기 구성 템플릿에 `logo` 노드 `type` 속성 설정 `image`. 이미지 로고를 zip 파일에 복사하기 위해 만든 특별한 구성 유형입니다. 일부 특정 요구 사항을 충족하기 위해 사용자 지정을 구현해야 할 수 있습니다 `type` 속성: 이렇게 하려면 콘텐츠 동기화 페이지에서 사용자 지정 업데이트 처리기 구현 섹션을 참조하십시오.

## 프로그래밍 방식으로 페이지 내보내기 {#programmatically-exporting-a-page}

페이지를 프로그래밍 방식으로 내보내려면 [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI 서비스. 이 서비스를 통해 다음을 수행할 수 있습니다.

* 페이지를 내보내고 HTTP 서블릿 응답에 작성합니다.
* 페이지를 내보내고 특정 위치에 zip 파일을 저장합니다.

에 바인딩된 서블릿 `export` 선택기 및 `zip` 확장은 PageExporter 서비스를 사용합니다.

## 문제 해결 {#troubleshooting}

zip 파일의 다운로드에 문제가 있는 경우, `/var/contentsync` 노드에 대한 정보를 생성하여 내보내기 요청을 다시 전송합니다.
