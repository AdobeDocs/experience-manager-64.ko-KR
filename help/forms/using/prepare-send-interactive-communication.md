---
title: 에이전트 UI를 사용하여 대화형 통신 준비 및 보내기
seo-title: Prepare and send Interactive Communication using the Agent UI
description: 에이전트 UI를 사용하여 에이전트가 대화형 커뮤니케이션을 준비하고 사후 프로세스로 전송할 수 있습니다. 에이전트는 필요한 수정 사항을 가능한 한 수행하고 전자 메일 또는 인쇄와 같은 사후 프로세스에 대화형 커뮤니케이션을 제출합니다.
seo-description: Prepare and send Interactive Communication using the Agent UI
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
feature: Interactive Communication
exl-id: 5ec33ef5-1722-4d29-9979-d8da32923e66
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 1%

---

# 에이전트 UI를 사용하여 대화형 통신 준비 및 보내기 {#prepare-and-send-interactive-communication-using-the-agent-ui}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

에이전트 UI를 사용하여 에이전트가 대화형 커뮤니케이션을 준비하고 사후 프로세스로 전송할 수 있습니다. 에이전트는 필요한 수정 사항을 가능한 한 수행하고 전자 메일 또는 인쇄와 같은 사후 프로세스에 대화형 커뮤니케이션을 제출합니다.

## 개요 {#overview}

대화형 커뮤니케이션이 생성되면 에이전트는 에이전트 UI에서 대화형 커뮤니케이션을 열고 데이터를 입력하고 콘텐츠 및 첨부 파일을 관리하여 수신자별 복사본을 준비할 수 있습니다. 마지막으로, 에이전트는 대화형 커뮤니케이션을 사후 프로세스에 제출할 수 있습니다.

에이전트 UI를 사용하여 대화형 커뮤니케이션을 준비하는 동안 에이전트는 Agent UI에서 대화형 커뮤니케이션의 다음 측면을 관리한 후 사후 프로세스에 제출합니다.

* **데이터**: 에이전트 UI의 데이터 탭에는 대화형 커뮤니케이션에서 에이전트 편집 가능한 변수와 잠금 해제된 양식 데이터 모델 속성이 표시됩니다. 이러한 변수/속성은 대화형 커뮤니케이션에 포함된 문서 조각을 편집하거나 만드는 동안 만들어집니다. 데이터 탭에는 XDP/인쇄 채널 템플릿에 빌드된 모든 필드가 포함되어 있습니다. 에이전트가 편집할 수 있는 Interactive Communication에 변수, 양식 데이터 모델 속성 또는 필드가 있는 경우에만 데이터 탭이 나타납니다.
* **컨텐츠**: 컨텐츠 탭에서 에이전트는 대화형 커뮤니케이션의 문서 조각 및 컨텐츠 변수와 같은 컨텐츠를 관리합니다. 에이전트는 문서 조각의 속성에서 대화형 커뮤니케이션을 만드는 동안 문서 조각에서 허용되는 대로 변경할 수 있습니다. 가능하면 에이전트는 문서 조각을 재정렬하거나 추가/제거하고 페이지 나누기를 추가할 수도 있습니다.
* **첨부 파일**: Interactive Communication에 첨부 파일이 있거나 에이전트가 라이브러리 액세스 권한이 있는 경우에만 에이전트 UI에 첨부 파일 탭이 나타납니다. 에이전트가 첨부 파일을 변경하거나 편집할 수 없을 수도 있습니다.

## 에이전트 UI를 사용하여 대화형 통신 준비 {#prepare-interactive-communication-using-the-agent-ui}

1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 적절한 대화형 커뮤니케이션을 선택하고 탭하기 **[!UICONTROL 에이전트 UI 열기]**.

   >[!NOTE]
   >
   >에이전트 UI는 선택한 대화형 커뮤니케이션에 인쇄 채널이 있는 경우에만 작동합니다.

   ![opentiui](assets/openagentiui.png)

   Interactive Communication의 컨텐츠 및 속성을 기반으로 다음 세 개의 탭과 함께 에이전트 UI가 나타납니다. 데이터, 컨텐츠 및 첨부 파일.

   ![에이전트 유틸리티](assets/agentuitabs.png)

   데이터 입력, 컨텐츠 관리 및 첨부 파일 관리를 계속 진행합니다.

### 데이터 입력 {#enter-data}

1. 데이터 탭에서 필요에 따라 변수, 양식 데이터 모델 속성 및 인쇄 템플릿(XDP) 필드에 데이터를 입력합니다. 별표(&amp;ast;)로 표시된 모든 필수 필드를 채워 **제출** 버튼을 클릭합니다.

   대화형 통신 미리 보기에서 데이터 필드 값을 탭하여 데이터 탭에서 해당 데이터 필드를 강조 표시하거나 그 반대의 경우도 마찬가지입니다.

### 컨텐츠 관리 {#manage-content}

콘텐츠 탭에서 대화형 커뮤니케이션에서 문서 조각 및 콘텐츠 변수와 같은 콘텐츠를 관리합니다.

1. 선택 **[!UICONTROL 컨텐츠]**. 대화형 커뮤니케이션의 콘텐츠 탭이 나타납니다.

   ![aguicontenttab](assets/agentuicontenttab.png)

1. 필요에 따라 컨텐츠 탭에서 문서 조각을 편집합니다. 컨텐츠 계층 구조에서 관련 조각에 초점을 맞추기 위해 Interactive Communication 미리 보기에서 관련 라인 또는 단락을 탭하거나 컨텐츠 계층 구조에서 직접 조각을 탭할 수 있습니다.

   예를 들어, 아래 그래픽의 미리 보기에서 &quot;지금 결제...&quot; 라인이 있는 문서 조각이 선택되고 컨텐츠 탭에서 동일한 문서 조각이 선택되었습니다.

   ![contentmodulefocus](assets/contentmodulefocus.png)

   컨텐츠 또는 데이터 탭에서 컨텐츠( ![highlightselectedmoulesincontentcr](assets/highlightselectedmodulesincontentccr.png)) 미리 보기 왼쪽 위에서 관련 텍스트, 단락 또는 데이터 필드를 미리 보기에서 탭/선택하면 문서 조각으로 이동하는 기능을 비활성화하거나 활성화할 수 있습니다.

   대화형 커뮤니케이션을 만드는 동안 에이전트가 편집할 수 있는 조각에는 선택한 컨텐츠 편집( ![iconeditselectedcontent](assets/iconeditselectedcontent.png)) 아이콘을 클릭합니다. 선택한 컨텐츠 편집 아이콘을 탭하여 편집 모드에서 조각을 실행하고 변경합니다. 텍스트 서식 지정 및 관리에 다음 옵션을 사용합니다.

   * [서식 옵션](#formattingtext)

      * [다른 응용 프로그램에서 서식이 지정된 텍스트를 복사하여 붙여넣습니다](#pasteformattedtext)
      * [텍스트 부분 강조 표시](#highlightemphasize)
   * [특수 문자](#specialcharacters)
   * [키보드 단축키](/help/forms/using/keyboard-shortcuts.md)

   에이전트 사용자 인터페이스의 다양한 문서 조각에 사용할 수 있는 작업에 대한 자세한 내용은 [에이전트 사용자 인터페이스에서 사용할 수 있는 작업 및 정보](#actionsagentui).

1. Interactive Communication의 인쇄 출력에 페이지 나누기를 추가하려면 페이지 나누기를 삽입할 위치에 커서를 놓고 다음 페이지 나누기 전에 또는 다음 페이지 나누기를 선택합니다( ![pagebreveforeafter](assets/pagebreakbeforeafter.png)).

   대화형 커뮤니케이션에 명시적 페이지 브레이크 자리 표시자가 삽입됩니다. 명시적 페이지 나누기가 대화형 커뮤니케이션에 미치는 영향을 보려면 인쇄 미리 보기를 참조하십시오.

   ![experiicpagebreak](assets/explicitpagebreak.png)

   Interactive Communication의 첨부 파일 관리를 계속합니다.

### 첨부 파일 관리 {#manage-attachments}

1. 선택 **[!UICONTROL 첨부 파일]**. Agent UI는 Interactive Communication을 생성하는 동안 설정된 대로 사용 가능한 첨부 파일을 표시합니다.

   보기 아이콘을 탭하여 Interactive Communication과 함께 첨부 파일을 제출하지 않도록 선택할 수 있으며, 첨부 파일에서 십자를 탭하여 Interactive Communication에서 해당 첨부 파일을 삭제할 수 있습니다(에이전트가 첨부 파일을 삭제하거나 숨길 수 있는 경우). 대화형 커뮤니케이션을 만드는 동안 필수로 지정된 첨부 파일의 경우 보기 및 삭제 아이콘이 비활성화됩니다.

   ![attachmentsagentui](assets/attachmentsagentui.png)

1. 라이브러리 액세스( ![libraryaccess](assets/libraryaccess.png)) 아이콘을 사용하여 컨텐츠 라이브러리에 액세스하여 DAM 자산을 첨부 파일로 삽입합니다.

   >[!NOTE]
   >
   >라이브러리 액세스 아이콘은 대화형 커뮤니케이션을 만드는 동안 라이브러리 액세스가 활성화된 경우에만 사용할 수 있습니다(인쇄 채널의 문서 컨테이너 속성에서).

1. Interactive Communication을 생성하는 동안 첨부 파일의 순서가 잠겨 있지 않은 경우 첨부 파일을 선택하고 아래쪽 및 위쪽 화살표를 탭하여 첨부 파일의 순서를 변경할 수 있습니다.
1. Web Preview 및 Print Preview를 사용하여 두 출력이 요구 사항에 해당하는지 확인합니다.

   미리 보기가 만족스러우면 을 누릅니다 **[!UICONTROL 제출]** 인터랙티브한 커뮤니케이션을 게시물 프로세스에 제출/전송합니다. 또는 변경을 수행하려면 미리 보기를 종료하여 변경 사항으로 돌아갑니다.

## 텍스트 서식 지정 {#formattingtext}

에이전트 UI에서 텍스트 조각을 편집하는 동안 도구 모음은 사용자가 선택한 편집 유형에 따라 변경됩니다. 글꼴, 단락 또는 목록:

![typoformingtoolbar](assets/typeofformattingtoolbar.png) ![글꼴 도구 모음](do-not-localize/fonttoolbar.png)

글꼴 도구 모음

![단락 도구 모음](do-not-localize/paragraphtoolbar.png)

단락 도구 모음

![목록 도구 모음](do-not-localize/listtoolbar.png)

목록 도구 모음

### 텍스트 부분 강조/강조 표시 {#highlightemphasize}

편집 가능한 조각에서 텍스트의 일부를 강조 표시하려면 텍스트를 선택하고 강조 색상 을 탭합니다.

![highlighttextagentui](assets/highlighttextagentui.png)

### 서식이 지정된 텍스트 붙여넣기 {#pasteformattedtext}

![텍스트 붙여넣기](assets/pastedtext.png)

### 텍스트에 특수 문자 삽입 {#specialcharacters}

에이전트 UI가 210개의 특수 문자를 지원합니다. 관리자는 다음을 수행할 수 있습니다 [사용자 지정별 추가/사용자 지정 특수 문자 지원 추가](/help/forms/using/custom-special-characters.md).

#### 첨부 파일 게재 {#attachmentdelivery}

* 서버측 API를 대화형 또는 비대화형 PDF으로 사용하여 대화형 커뮤니케이션을 렌더링하면 렌더링된 PDF에 첨부 파일이 PDF 첨부 파일로 포함됩니다.
* Interactive Communication과 연관된 사후 프로세스가 에이전트 UI를 사용하여 제출 의 일부로 로드되면 첨부 파일이 목록으로 전달됩니다&lt;com.adobe.idp.document> inAttachmentDocs 매개 변수.
* 전자 메일 및 인쇄와 같은 게재 메커니즘 워크플로우도 Interactive Communication PDF 버전과 함께 첨부 파일을 제공합니다.

## 에이전트 사용자 인터페이스에서 사용할 수 있는 작업 및 정보 {#actionsagentui}

### 문서 조각 {#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **위쪽/아래쪽 화살표**: 대화형 커뮤니케이션에서 문서 조각을 위 또는 아래로 이동하는 화살표
* **삭제**: 허용되는 경우 Interactive Communication에서 문서 조각을 삭제합니다.
* **앞에 페이지 나누기** (대상 영역의 하위 조각에 적용 가능): 문서 조각 앞에 페이지 나누기를 삽입합니다.
* **들여쓰기**: 문서 조각의 들여쓰기를 늘리거나 줄입니다.
* **다음 이후 페이지 나누기** (대상 영역의 하위 조각에 적용 가능): 문서 조각 뒤에 페이지 나누기를 삽입합니다.

![docfragoptions](assets/docfragoptions.png)

* 편집(텍스트 조각만): 텍스트 문서 조각을 편집할 리치 텍스트 편집기를 엽니다. 자세한 내용은 [텍스트 서식 지정](#formattingtext).

* 선택(눈 모양 아이콘): 대화형 커뮤니케이션에서 문서 조각을 포함\제외합니다.
* 입력되지 않은 값(정보): 문서 조각에서 채워지지 않은 변수의 수를 나타냅니다.

### 문서 조각 나열 {#list-document-fragments}

![listoptions](assets/listoptions.png)

* 빈 행 삽입: 새 빈 행을 삽입합니다.
* 선택(눈 모양 아이콘): 대화형 커뮤니케이션에서 문서 조각을 포함\제외합니다.
* 글머리 기호/번호 건너뛰기: 목록 문서 조각에서 글머리 기호/번호 매기기를 건너뛸 수 있도록 설정합니다.
* 입력되지 않은 값(정보): 문서 조각에서 채워지지 않은 변수의 수를 나타냅니다.
