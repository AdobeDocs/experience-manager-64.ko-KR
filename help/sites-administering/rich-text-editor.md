---
title: 리치 텍스트 편집기 구성
description: AEM 리치 텍스트 편집기를 구성하는 방법에 대해 학습합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7849a3e2d9d8241382652fb1c8e6e302ffd853e0
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 0%

---


# Configure the Rich Text Editor {#configure-the-rich-text-editor}

RTE(Rich Text Editor)는 작성자가 텍스트 컨텐츠를 편집할 수 있는 다양한 기능을 제공합니다. 아이콘, 선택 상자, 도구 모음 및 메뉴는 WYSIWYG 텍스트 편집 환경을 위해 제공됩니다.

작성을 위해 RTE 기능을 사용하는 방법에 대해 알아보려면 [작성에 리치 텍스트 편집기 사용을 참조하십시오](/help/sites-authoring/rich-text-editor.md). 작성 구성 요소에서 사용 가능한 기능을 활성화, 비활성화 및 확장하도록 RTE를 구성할 수 있습니다. 다음 워크플로우는 Experience Manager에서 RTE 구성 작업을 완료하는 권장 순서를 보여줍니다.

![리치 텍스트 편집기를 구성하는 일반적인 워크플로우](assets/rte_workflow_v1.png)

*그림: 리치 텍스트 편집기를 구성하는 일반적인 워크플로우*

## 터치 지원 UI 및 클래식 UI 이해 {#understand-touch-enabled-ui-and-classic-ui}

터치 지원 UI는 AEM의 표준 UI입니다. Adobe은 작성 환경을 위한 [반응형 디자인으로](/help/sites-authoring/responsive-layout.md) Touch UI를 버전 5.6에서 도입했습니다. 터치 UI는 터치 및 데스크톱 장치용으로 설계되었습니다. UI는 원래 클래식 UI와 상당히 다릅니다.

![터치 지원 UI의 리치 텍스트 편집기 도구 모음](assets/chlimage_1-404.png)

*그림: 터치 지원 UI의 리치 텍스트 편집기 도구 모음*

![클래식 UI의 리치 텍스트 편집기 도구 모음](assets/rtedefault.png)

*그림: 클래식 UI의 리치 텍스트 편집기 도구 모음*

>[!MORELIKETHIS]
>
>* [UI 추천](/help/sites-deploying/ui-recommendations.md)
>* 클래식 UI 사용 중단에 대해서는 [AEM 6.4 릴리스 노트를 참조하십시오.](/help/release-notes/deprecated-removed-features.md)
>* UI의 차이는 [터치 UI와 클래식 UI를 참조하십시오](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
>* 터치 지원 UI에 대해 자세히 알아보려면 AEM 터치 UI [의 개념을 참조하십시오.](/help/sites-developing/touch-ui-concepts.md)


## 다양한 편집 모드 {#editingmodes}

작성자는 다양한 구성 요소 모드를 사용하여 AEM에서 텍스트 컨텐츠를 만들고 편집할 수 있습니다. 컨텐츠 작성 및 서식 지정을 위한 툴바 옵션과 다양한 편집 모드에서 RTE 지원 구성 요소의 사용자 환경은 RTE 구성에 따라 다릅니다.

| 편집 모드 | 편집 영역 | 활성화할 기능 권장 | 터치 UI | 클래식 UI |
|--- |--- |--- |--- |--- |
| 인라인 | 간단한 편집을 위한 즉석 편집, 대화 상자를 열지 않고 서식 지정 | 최소 RTE 기능 | Y | Y |
| RTE 전체 화면 | 전체 페이지 | 모든 필수 RTE 기능 | Y | N |
| 대화 상자 | 페이지 컨텐츠 맨 위에 있는 대화 상자지만 전체 페이지를 포함하지 않음 | 클래식 UI에서 필요한 모든 RTE 기능; 터치 UI의 기능 활용 | Y | Y |
| 대화 상자 전체 화면 | 전체 화면 모드와 동일; RTE와 함께 대화 상자의 필드 포함 | 모든 필수 RTE 기능 | Y | N |

>[!NOTE]
>
>소스 편집 기능은 터치 지원 UI의 인라인 편집 모드에서 사용할 수 없습니다. 전체 화면 모드에서는 이미지를 드래그할 수 없습니다. 다른 모든 기능은 모든 모드에서 작동합니다.

### 인라인 편집 {#inline-editing}

페이지를 열 때(느린 두 번 탭/클릭) 페이지 내에서 컨텐츠를 편집할 수 있습니다. 기본 옵션이 있는 작은 도구 모음이 표시됩니다.

![터치 지원 UI의 기본 툴바를 사용한 인라인 편집](assets/chlimage_1-405.png)

*그림: 터치 지원 UI의 기본 툴바를 사용한 인라인 편집*

클래식 UI에서 구성 요소를 느리게 두 번 클릭하면 인라인 편집이 가능하며 주황색 윤곽선이 내용을 강조 표시합니다. Content Finder가 열려 있으면 창 맨 위에 사용 가능한 RTE 서식 지정 옵션이 있는 도구 모음이 표시됩니다. 컨텐츠 파인더가 열려 있지 않으면 서식 옵션이 표시되지 않고 기본 텍스트 편집만 수행할 수 있습니다.

### Full screen editing {#full-screen-editing}

AEM 구성 요소는 페이지 컨텐츠를 숨기고 사용 가능한 화면을 차지하는 전체 화면 보기에서 열 수 있습니다. 대부분의 편집 옵션을 제공하므로 인라인 편집의 자세한 버전을 전체 화면으로 편집하는 것이 좋습니다. 인라인 편집 모드를 사용할 때 작은 도구 모음에서 ![rte_fullscreen](assets/rte_fullscreen.png)을 클릭하여 열 수 있습니다.

대화 상자 전체 화면 모드에서는 세부 RTE 도구 모음, 대화 상자 모드에서 사용할 수 있는 옵션 및 구성 요소가 제공됩니다. 다른 구성 요소와 함께 RTE가 포함된 대화상자에만 적용됩니다.

![터치 활성화 UI의 전체 화면 모드에서 편집할 때 자세한 RTE 도구 모음](assets/chlimage_1-406.png)

*그림: 터치 활성화 UI의 전체 화면 모드에서 편집할 때 자세한 RTE 도구 모음*

### 대화 상자 편집 {#dialog-editing}

클래식 UI에서 구성 요소를 두 번 클릭하면 컨텐츠를 편집할 수 있는 대화 상자가 열립니다. 대화 상자가 기존 페이지 상단에 열립니다. 일부 특정 시나리오에서 대화 상자가 팝업 창으로 열립니다. 예를 들어 텍스트 구성 요소가 다중 열 페이지 레이아웃의 열에 포함되어 있고 대화 상자에 사용할 수 있는 영역이 더 적은 경우

![터치가 활성화된 UI의 대화 상자 편집 모드](assets/dialog_editing_modetouchui.png)

*그림: 터치가 활성화된 UI의 대화 상자 편집 모드*

![편집에 대한 세부 도구 모음이 포함된 클래식 UI의 대화 상자](assets/chlimage_1-407.png)

*그림: 편집에 대한 세부 도구 모음이 포함된 클래식 UI의 대화 상자*

## RTE 플러그인 및 관련 기능 정보 {#aboutplugins}

이 기능은 다음과 같이 일련의 플러그인을 통해 사용할 수 있습니다.

* 속성 `features` :

   * 이 플러그인은 해당 플러그인의 기본 기능을 활성화하거나 비활성화하는 데 사용됩니다.
   * 표준화된 절차를 사용하여 구성할 수 있습니다.

* 적절한 경우, 보다 많은 속성과 옵션을 참조하십시오.

해당 플러그인과 관련된 노드의 `features` 속성 값에 따라 RTE의 기본 기능이 활성화되거나 비활성화됩니다.

다음 표에는 현재 플러그인이 표시되어 있습니다.

* API 설명서에 대한 링크가 있는 플러그인 ID. 플러그인을 [활성화할 때 ID가 노드 이름으로 사용됩니다](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).
* 속성에 허용된 `features` 값.
* 플러그인에서 제공하는 기능에 대한 설명입니다.

| 플러그인 ID | features | 설명 |
|--- |--- |--- |
| 편집 | cut copy paste-default paste-plaintext paste-wordhtml | [잘라내기, 복사 및 3가지 붙여넣기 모드](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles). |
| [칠드플레이스](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | 찾기 바꾸기 | 찾기 및 바꾸기 |
| [format](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | 굵은 기울임꼴 밑줄 | [기본 텍스트 서식](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles). |
| [이미지](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | 이미지 | 기본 이미지 지원(컨텐츠 또는 컨텐츠 파인더에서 드래그) 브라우저에 따라 작성자에 대한 지원 동작이 다릅니다 |
| [keys](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | 이 값을 정의하려면 [탭 크기를 참조하십시오](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tabsize). |
| [justice](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justfyleft justifycenter justifyright | 단락 정렬. |
| [링크](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modifylink 연결 해제 | [하이퍼링크 및 앵커](/help/sites-administering/configure-rich-text-editor-plug-ins.md#linkstyles). |
| [lists](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | 순서가 없는 들여쓰기 내어쓰기 | 이 플러그인은 들여쓰기 및 목록 [을 모두 제어합니다](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indentmargin). 중첩된 목록 포함. |
| [misctools](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specialchars sourceedit | 기타 도구를 사용하면 작성자가 [특수 문자를](/help/sites-administering/configure-rich-text-editor-plug-ins.md#spchar) 입력하거나 HTML 소스를 편집할 수 있습니다. 또한 목록을 정의하려는 경우 전체 [범위의 특수 문자를](/help/sites-administering/configure-rich-text-editor-plug-ins.md#definerangechar) 추가할 수도 있습니다. |
| Paraformat | paraformat | 기본 단락 형식은 Paragraph, Heading 1, Heading 2 및 Heading 3(`<p>`, `<h1>`및 `<h2>`and `<h3>`)입니다. 단락 서식 [을](/help/sites-administering/configure-rich-text-editor-plug-ins.md#paraformats) 더 추가하거나 목록을 확장할 수 있습니다. |
| spellcheck | checktext | [언어 인식 맞춤법 검사기입니다](/help/sites-administering/configure-rich-text-editor-plug-ins.md#adddict). |
| styles | styles | CSS 클래스를 사용한 스타일 지정 지원. [텍스트에 사용할 고유한 스타일을 추가(또는 확장)하려면 새로운 텍스트 스타일을](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles) 추가합니다. |
| 아래 첨자 | 아래 첨자 | 기본 포맷의 익스텐션, 하위 및 수퍼 스크립트 추가 |
| 표 | 표 제거 가능한 삽입방법 제거삽입열 제거열 제거cellprop셀 분할셀 선택열 | 전체 표 또는 개별 셀에 고유한 스타일을 추가하려는 경우 표 스타일 [](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles)구성을 참조하십시오. |
| 실행 취소 | 실행 취소 재실행 | 실행 [취소 및 재실행 작업의 기록](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undohistory) 크기입니다. |

>[!NOTE]
>
>대화 상자 모드에서는 전체 화면 플러그인이 지원되지 않습니다. 전체 화면 모드 `dialogFullScreen` 에 대한 도구 모음을 구성하는 설정을 사용합니다.

## 구성 경로 및 위치 이해 {#understand-the-configuration-paths-and-locations}

작성자에게 제공하는 RTE [편집 모드(및 UI)](#editingmodes) 는 RTE 플러그인을 활성화할 때 구성 세부 사항 [의 위치를 결정합니다](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).

| 편집 모드 | 터치 UI 위치 | 클래식 UI 위치 |
|---|---|---|
| 인라인 | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| 전체 화면 | `cq:editConfig/cq:inplaceEditing` | 해당 사항 없음 |
| 대화 상자 | `cq:dialog` | `dialog` |
| 전체 화면 대화 상자 | `cq:dialog` | 해당 사항 없음 |

>[!NOTE]
>
>노드 이름을 다음으로 지정하지 `cq:inplaceEditing` 마십시오 `config`. 노드에서 `cq:inplaceEditing` 다음 속성을 정의합니다.
>
>* **이름**: `configPath`
>* **유형**: `String`
>* **값**: 실제 구성을 포함하는 노드의 경로

>
>
RTE 구성 노드의 이름을 다음으로 지정하지 마십시오 `config`. 그렇지 않으면 RTE 구성은 관리자만 적용되고 그룹의 사용자에 대해서는 적용되지 않습니다 `content-author`.

Touch UI의 대화 상자 편집 모드에 적용되는 다음 속성을 구성합니다.

* `useFixedInlineToolbar`: RTE 노드(sling:resourceType=)에 정의된 이 부울 속성 `cq/gui/components/authoring/dialog/richtext`을 설정하여 `True`부동 대신 RTE 도구 모음을 고정합니다.

   이 속성이 true이면 Richtext 편집은 기본적으로 &quot;foundation-contentloaded&quot; 이벤트에서 시작됩니다.

   이를 방지하려면 속성을 설정하여 &#39;rte-start&#39; 이벤트 `customStart` 를 트리거하여 RTE `True`편집을 시작합니다. 이 속성이 &#39;true&#39;인 경우 기본 동작인 &#39;클릭 시 시작&#39;이 작동하지 않습니다.

* `customStart`: 이벤트를 트리거하여 RTE를 시작할 시기를 제어하려면 RTE 노드에 정의된 이 부울 속성 `True`을 로 설정합니다 `rte-start`.

* `rte-start`: RTE의 편집 `contenteditable-div` 을 시작할 때 이 이벤트를 트리거합니다. 이 기능은 true로 설정된 경우에만 `customStart` 작동합니다.

터치 지원 대화 상자에서 RTE를 사용하는 경우 문제를 방지하기 위해 속성을 true `useFixedInlineToolbar` 로 설정해야 합니다.

## 즉석 편집 사용자 정의 {#customizing-in-place-editing}

다음 속성을 구성하여 텍스트 편집기가 시작하는 HTML 선택기를 정의할 수 있습니다.

* **`editElementQuery`** - 정의됨 `cq:InplaceEditingConfig`으로, 이 속성은 텍스트 구성 요소에 대한 인라인 편집을 시작할 HTML 요소의 선택기를 지정하는 데 사용됩니다. 지정하지 않으면 텍스트 구성 요소 HTML에서 바로 인라인 편집이 시작됩니다.
* **`textPropertyName`** - 에 정의됨 `cq:InplaceEditingConfig`으로, 이 속성은 텍스트 구성 요소의 HTML 값이 인라인 편집 후에 지속될 컨텐트 노드에 저장될 속성 이름을 지정하는 데 사용됩니다.

대화 상자에 해당하는 속성은 입니다 `name`.

## 플러그인을 활성화하여 RTE 기능 활성화 {#enable-rte-functionalities-by-activating-plug-ins}

RTE 기능은 기능 속성이 있는 일련의 플러그인을 통해 제공됩니다. 각 플러그인의 다양한 기능을 활성화하거나 비활성화하도록 기능 속성을 구성할 수 있습니다.

RTE 플러그인의 자세한 구성에 대해서는 RTE 플러그인을 활성화하고 구성하는 [방법을 참조하십시오](/help/sites-administering/configure-rich-text-editor-plug-ins.md).

이 샘플 구성을 다운로드하여 RTE를 구성하는 방법을 이해합니다. 이 패키지에서 모든 기능이 활성화됩니다.

[파일 가져오기](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
>
>템플릿 편집자는 [핵심 구성 요소 텍스트 구성 요소를](https://helpx.adobe.com/experience-manager/core-components/using/text.html) 사용하여 사용자 인터페이스에 있는 많은 RTE 플러그인을 컨텐츠 정책으로 구성할 수 있으므로 기술 구성 없이도 컨텐츠 정책은 설명된 대로 RTE 사용자 인터페이스 구성에서 작동할 수 있습니다. 자세한 내용은 [RTE 사용자 인터페이스 설정 및 컨텐츠 정책](/help/sites-administering/rich-text-editor.md#rtecontentpolicies), 페이지 템플릿 [만들기](/help/sites-authoring/templates.md)및 [핵심 구성 요소 개발자 설명서를 참조하십시오](https://helpx.adobe.com/experience-manager/core-components/using/developing.html).

>[!NOTE]
>
>참조용으로 기본 텍스트 구성 요소(표준 설치의 일부로 제공)는 다음 위치에서 찾을 수 있습니다.
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`

>
>
자체 텍스트 구성 요소를 만들려면 이러한 구성 요소를 편집하는 대신 위의 구성 요소를 복사하십시오.

## RTE 도구 모음 구성 {#dialogfullscreen}

AEM에서는 다양한 편집 모드에 대해 리치 텍스트 편집기의 UI를 다르게 구성할 수 있습니다. 기본 설정은 아래에 제공됩니다. 요구 사항에 따라 이러한 기본값을 무시할 수 있습니다.

최상의 작성 경험을 위해:

* 부동 대화 상자에서 부동 대화 상자의 크기가 작으므로 팝업이 없는 플러그인만 활성화합니다.
* 전체 화면 대화 상자에서 모든 필수 플러그인을 사용할 수 있고 플러그인과 같이 더 큰 팝업이 있는 플러그인을 사용할 수 `Paste` 있습니다. 아래 설명된 `dialogFullScreen` 구성을 사용하십시오.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

인라인 모드 및 전체 화면 모드에 서로 다른 UI 설정이 사용됩니다. 도구 모음 속성은 도구 모음의 단추를 지정하는 데 사용됩니다. 예를 들어 단추 자체가 피쳐(예: `Bold`)인 경우, `PluginName#FeatureName` (예: `links#modifylink`)로 지정됩니다. 단추가 팝업인 경우(예: 플러그인 일부 기능 포함), 로 `#PluginName` 지정됩니다 `#format`. 구분자( | )를 &#39;-&#39;로 단추 그룹 사이에 지정할 수 있습니다.

인라인 또는 전체 화면 모드 아래의 팝업 노드에는 사용 중인 팝오버 목록이 포함되어 있습니다. 노드 아래의 각 하위 노드는 `popovers` 플러그인(예: `format`) 이름을 따릅니다. 플러그인 기능 목록 `items` (예: `format#bold`)이 들어 있는 속성이 있습니다.

## RTE 사용자 인터페이스 설정 및 컨텐츠 정책 {#rtecontentpolicies}

관리자는 위에서 설명한 대로 구성을 수행하는 대신 컨텐츠 정책을 사용하여 RTE 옵션을 제어할 수 있습니다. 컨텐츠 정책은 [편집 가능한 템플릿의 일부로 사용될 경우 구성 요소의 디자인 속성을 정의합니다](../sites-authoring/templates.md). 예를 들어 RTE를 사용하는 텍스트 구성 요소를 편집 가능한 템플릿과 함께 사용하는 경우 컨텐츠 정책은 굵게 표시된 옵션을 사용할 수 있고 몇 가지 단락 서식 지정 옵션을 사용할 수 있음을 정의할 수 있습니다. 컨텐츠 정책은 다시 사용할 수 있으며 여러 템플릿에 적용할 수 있습니다.

AEM 6.4 서비스 팩 3부터 사용자 인터페이스 구성에서 컨텐츠 정책으로 이어지는 RTE 흐름 다운스트림의 사용 가능한 옵션

* 사용자 인터페이스 구성 설정은 콘텐츠 정책에 사용할 수 있는 옵션을 정의합니다.
* RTE의 사용자 인터페이스 구성이 제거되었거나 항목을 활성화하지 않으면 콘텐츠 정책이 해당 항목을 구성할 수 없습니다.
* 작성자는 사용자 인터페이스 구성 및 컨텐츠 정책에 의해 사용 가능한 기능에만 액세스할 수 있습니다.

예를 들어 [텍스트 코어 구성 요소 설명서를 볼 수 있습니다](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor).

## 도구 모음 아이콘과 명령 간의 매핑 사용자 정의 {#iconstoolbar}

RTE 도구 모음에 표시된 Coral 아이콘과 사용 가능한 명령 간의 매핑을 사용자 정의할 수 있습니다. Coral 아이콘 외에는 다른 아이콘을 사용할 수 없습니다.

1. under라는 노드 `icons` 를 만듭니다 `uiSettings/cui`.

1. 아래에 개별 아이콘에 대한 노드를 만듭니다.
1. 각 개별 아이콘 노드에서 Coral 아이콘과 아이콘에 매핑할 명령을 지정합니다.

아래는 Bold 명령을 Coral 아이콘에 매핑하는 샘플 조각입니다 `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true"> 
    <rtePlugins jcr:primaryType="nt:unstructured"> 
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/> 
    </rtePlugins> 
    <uiSettings jcr:primaryType="nt:unstructured"> 
        <cui jcr:primaryType="nt:unstructured"> 
            <inline jcr:primaryType="nt:unstructured" 
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]"> 
            </inline> 
            <icons jcr:primaryType="nt:unstructured"> 
                <bold jcr:primaryType="nt:unstructured" 
                    command="format#bold" 
                    icon="textItalic"/> 
            </icons> 
        </cui> 
    </uiSettings> 
</text>
```

## CoralUI 2 리치 텍스트 편집기로 전환 {#switch-to-coralui-rich-text-editor}

페이지에서 CoralUI 2 RTE clientlib 또는 CoralUI 3 RTE clientlib을 포함할 수 있습니다. 기본적으로 리치 텍스트 편집기에는 CoralUI 3 RTE clientlib이 포함됩니다. CoralUI 2 RTE로 전환하려면 다음 단계를 수행하십시오.

>[!NOTE]
>
>Adobe에서는 전환을 최상의 방법으로 권장하지 않습니다. 마지막 수단으로 CoralUI 2 RTE로 전환합니다. CoralUI 2 RTE용 사용자 정의 플러그인은 플러그인이 클래스와 같은 RTE 내부 시스템에 의존하지 않는 경우 CoralUI 3 RTE와 함께 작동합니다. CoralUI 3 RTE용 사용자 정의 플러그인을 사용하는 경우 `rte.coralui3` 라이브러리를 사용하십시오.

1. 노드를 아래 `/libs/cq/gui/components/authoring/editors/clientlibs/core` 에 오버레이하고 `/apps`다음을 수행합니다.

   * Replace `rte.coralui3` with `rte.coralui2` for the dependencies property.
   * Replace `cq.authoring.editor.core.inlineediting.rte.coralui3` with `cq.authoring.editor.core.inlineediting.rte.coralui2` for the embed property.
   * Replace `cq.authoring.rte.coralui3` with `cq.authoring.rte.coralui2` for the embed property.

1. 노드 `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` 와 `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` 아래에 노드를 `/apps`오버레이합니다.

   카테고리 `cq.authoring.dialog` 를 `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` 제거하고 에 추가합니다 `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`.

1. 페이지에 포함되는 다른 종속성을 `rte.coralui3` 다음으로 변경합니다 `rte.coralui2`. 예를 들어 아래 노드를 오버레이한 후 `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` 에 대한 `/apps`종속성을 에서 (으)로 `rte.coralui3` 변경합니다 `rte.coralui2`.

1. 노드를 아래 `cq/ui/widgets` 에 `/apps`오버레이합니다. 노드의 종속성을 다음으로 `cq.rte` 바꿉니다 `/apps/cq/ui/widgets` `cq.coralui2.rte`.

>[!NOTE]
>
>CoralUI 2 RTE는 플러그인 대화 상자에 handlebars 템플릿을 사용합니다. 따라서 CoralUI 2 RTE clientlib은 handlebars clientlib에 대한 종속성을 갖습니다. CoralUI 3 RTE는 handlebars 템플릿을 사용하지 않으며 연관된 종속성이 없습니다. 사용자 지정 플러그인이 handlebars 템플릿을 사용하는 경우 웹 페이지에 handlebars clientlib을 포함시키십시오.

## 추가 정보 {#further-information}

RTE 구성에 대한 자세한 내용은 [AEM Widget API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) 참조를 참조하십시오.

특히, 사용 가능한 플러그인 및 관련 옵션을 보려면:

* CQ. [form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText) 구성 요소는 스타일이 지정된 텍스트 정보(리치 텍스트)를 편집하기 위한 양식 필드를 제공합니다. 리치 텍스트 양식에 사용할 수 있는 모든 매개 변수를 알고 싶으면 구성 옵션을 참조하십시오.
* RichText 구성 요소는 [CQ.form.rte.plugins.Plugin 아래에 나열된 플러그인을 사용하여 다양한 기능을 제공합니다](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin). 각 플러그인의 경우:

   * 활성화(또는 비활성화)할 수 있는 기능에 대한 자세한 내용은 기능을 참조하십시오.
   * 해당 플러그인의 세부 구성에 대해 사용할 수 있는 모든 매개 변수에 대한 구성 옵션을 참조하십시오.

* 링크에 대한 HTML 규칙에 대한 자세한 정보도 사용할 수 있습니다.

위의 옵션을 사용하여 고유한 RTE를 확장하고 사용자 정의할 수 있습니다. 예를 들어 링크를 만들 때 페이지에서 사용할 수 있는 앵커를 나열하려면 페이지의 고유한 구현을 제공할 수 있습니다 `LinkPlugin`.

## 알려진 제한 사항 {#known-limitations}

AEM RTE 기능에는 다음과 같은 제한 사항이 있습니다.

* RTE 기능은 AEM 구성 요소 대화 상자에서만 지원됩니다. RTE는 마법사 또는 터치가 활성화된 UI의 [페이지 속성](/help/sites-developing/page-properties-views.md) 및 [스캐폴딩](/help/sites-authoring/scaffolding.md) 같은 Foundation양식에서는 지원되지 않습니다.

* AEM은 [하이브리드 장치에서 작동하지 않습니다](/help/release-notes/known-issues.md).

* RTE 구성 노드의 이름을 지정하지 마십시오 `config`. 그렇지 않으면 RTE 구성은 관리자에게만 적용되고 그룹의 사용자에 대해서는 적용되지 않습니다 `content-author`.

* RTE는 컨텐츠를 포함할 인라인 프레임 또는 iframe을 지원하지 않습니다.

>[!MORELIKETHIS]
>
>* [RTE 플러그인 구성](configure-rich-text-editor-plug-ins.md)
>* [작성에 리치 텍스트 편집기 사용](../sites-authoring/rich-text-editor.md)
>* [액세스 가능한 사이트에 대한 RTE 구성](rte-accessible-content.md)
>* [터치 UI 및 클래식 UI 기능 패리티](../release-notes/touch-ui-features-status.md)
>* [복합 다중 필드 구성 요소를 만들기 위한 자습서 샘플](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

