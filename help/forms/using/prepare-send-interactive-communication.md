---
title: 에이전트 UI를 사용하여 대화형 통신 준비 및 보내기
seo-title: 에이전트 UI를 사용하여 대화형 통신 준비 및 보내기
description: '에이전트 UI를 사용하면 에이전트가 대화형 통신을 준비하고 게시물 프로세스로 전송할 수 있습니다. 에이전트는 허용된 대로 필요한 수정 사항을 만들고 이메일 또는 인쇄와 같은 게시 프로세스에 대화형 통신을 제출합니다. '
seo-description: 에이전트 UI를 사용하여 대화형 통신 준비 및 보내기
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
translation-type: tm+mt
source-git-commit: 835618e8e0d01905ad7b476b0172dfecec41cf9d
workflow-type: tm+mt
source-wordcount: '1358'
ht-degree: 0%

---


# 에이전트 UI {#prepare-and-send-interactive-communication-using-the-agent-ui}을(를) 사용하여 대화형 통신 준비 및 보내기

에이전트 UI를 사용하면 에이전트가 대화형 통신을 준비하고 게시물 프로세스로 전송할 수 있습니다. 에이전트는 허용된 대로 필요한 수정 사항을 만들고 이메일 또는 인쇄와 같은 게시 프로세스에 대화형 통신을 제출합니다.

## 개요 {#overview}

대화형 통신이 만들어지면 에이전트는 에이전트 UI에서 대화형 통신을 열고 데이터를 입력하고 콘텐트 및 첨부 파일을 관리하여 수신자별 사본을 준비할 수 있습니다. 마지막으로, 에이전트는 대화형 통신을 게시물 프로세스에 제출할 수 있습니다.

에이전트 UI를 사용하여 대화형 통신을 준비하는 동안 에이전트는 에이전트 UI에서 다음 대화형 통신 측면을 관리하고 게시물 프로세스에 제출합니다.

* **데이터**:에이전트 UI의 [데이터] 탭에는 에이전트가 편집 가능한 변수와 잠금 해제된 양식 데이터 모델 속성이 대화형 통신에 표시됩니다. 이러한 변수/속성은 대화형 통신에 포함된 문서 조각을 편집하거나 만드는 동안 만들어집니다. 데이터 탭에는 XDP/인쇄 채널 템플릿에 내장된 모든 필드도 포함되어 있습니다. [데이터] 탭은 에이전트가 편집할 수 있는 [대화형 통신]에 변수, 양식 데이터 모델 속성 또는 필드가 있는 경우에만 나타납니다.
* **컨텐츠**:[콘텐트] 탭에서 에이전트는 대화형 통신에서 문서 조각 및 컨텐츠 변수와 같은 내용을 관리합니다. 에이전트는 문서 조각의 속성에서 대화형 통신을 생성하는 동안 문서 조각에서 허용된 대로 변경할 수 있습니다. 또한 에이전트는 가능한 경우 문서 단편을 재정렬하고, 추가/제거하고 페이지 나누기를 추가할 수 있습니다.
* **첨부 파일**:[첨부 파일] 탭은 대화형 통신에 첨부 파일이 있거나 에이전트에 라이브러리 액세스 권한이 있는 경우에만 에이전트 UI에 나타납니다. 에이전트는 첨부 파일을 변경하거나 편집할 수 없거나 허용되지 않을 수 있습니다.

## 에이전트 UI {#prepare-interactive-communication-using-the-agent-ui}을(를) 사용하여 대화형 통신 준비

1. **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; 문서]**&#x200B;를 선택합니다.
1. 적절한 대화형 통신을 선택하고 **[!UICONTROL 에이전트 UI 열기]**&#x200B;를 누릅니다.

   >[!NOTE]
   >
   >에이전트 UI는 선택한 대화형 통신에 인쇄 채널이 있는 경우에만 작동합니다.

   ![openentui](assets/openagentiui.png)

   Interactive Communication의 컨텐츠 및 속성을 기반으로 에이전트 UI는 다음 3개의 탭을 사용하여 나타납니다.데이터, 컨텐트 및 첨부 파일을 참조하십시오.

   ![agentuitabs](assets/agentuitabs.png)

   데이터 입력, 컨텐츠 관리 및 첨부 파일 관리를 계속합니다.

### 데이터 입력 {#enter-data}

1. 데이터 탭에서 필요에 따라 변수, 양식 데이터 모델 속성 및 인쇄 템플릿(XDP) 필드에 데이터를 입력합니다. 별표(&amp;ast;)가 표시된 모든 필수 필드를 채워 **제출** 단추를 활성화합니다.

   대화형 통신 미리 보기에서 데이터 필드 값을 눌러 [데이터] 탭에서 해당 데이터 필드를 강조 표시하거나 그 반대로 합니다.

### 컨텐츠 관리 {#manage-content}

컨텐츠 탭에서 대화형 커뮤니케이션의 문서 조각 및 컨텐츠 변수와 같은 컨텐츠를 관리합니다.

1. **[!UICONTROL 컨텐트]**&#x200B;를 선택합니다. [대화형 통신]의 [콘텐트] 탭이 나타납니다.

   ![agentuicontenttab](assets/agentuicontenttab.png)

1. 필요에 따라 [콘텐트] 탭에서 문서 조각을 편집합니다. 컨텐츠 계층 구조의 관련 단편에 초점을 맞추기 위해 Interactive Communication 미리 보기에서 관련 라인 또는 단락을 탭하거나 컨텐츠 계층 구조에서 직접 조각을 탭할 수 있습니다.

   예를 들어 &quot;지금 결제를 온라인으로 만들기..&quot;라는 라인이 있는 문서 조각은 아래 그래픽의 미리 보기에서 선택되고 컨텐츠 탭에서 동일한 문서 조각이 선택됩니다.

   ![contentmodulefocus](assets/contentmodulefocus.png)

   컨텐츠 또는 데이터 탭에서 미리 보기의 왼쪽 상단에 있는 컨텐츠 내 선택한 모듈 강조 표시( ![highlightselectedmodulesincontentcr](assets/highlightselectedmodulesincontentccr.png))를 탭하여 미리 보기에서 관련 텍스트, 단락 또는 데이터 필드를 탭/선택한 경우 문서 조각으로 이동할 수 있는 기능을 비활성화하거나 활성화할 수 있습니다.

   대화형 통신을 만드는 동안 에이전트가 편집할 수 있도록 허용된 조각에는 [선택한 내용 편집]( ![iconeditselectedcontent](assets/iconeditselectedcontent.png)) 아이콘이 있습니다. 선택한 컨텐츠 편집 아이콘을 눌러 편집 모드에서 조각을 실행하고 변경합니다. 텍스트 서식 지정 및 관리에 다음 옵션을 사용합니다.

   * [서식 옵션](#formattingtext)

      * [다른 응용 프로그램에서 서식이 지정된 텍스트 복사](#pasteformattedtext)
      * [텍스트 부분 강조 표시](#highlightemphasize)
   * [특수 문자](#specialcharacters)
   * [키보드 단축키](/help/forms/using/keyboard-shortcuts.md)

   에이전트 사용자 인터페이스의 다양한 문서 조각에 사용할 수 있는 작업에 대한 자세한 내용은 [에이전트 사용자 인터페이스](#actionsagentui)에서 사용할 수 있는 작업 및 정보를 참조하십시오.

1. 대화형 통신 인쇄 출력에 페이지 나누기를 추가하려면 페이지 나누기를 삽입할 위치에 커서를 놓고 [페이지 나누기 이전 또는 다음 페이지 나누기]를 선택합니다( ![pagebreakebefore](assets/pagebreakbeforeafter.png)).

   명확한 페이지 나누기 자리 표시자가 대화형 통신에 삽입됩니다. 명확한 페이지 나누기가 대화형 통신에 미치는 영향을 보려면 인쇄 미리 보기를 참조하십시오.

   ![explicitpagebreak](assets/explicitpagebreak.png)

   대화형 통신 첨부 파일을 계속 관리합니다.

### 첨부 파일 관리 {#manage-attachments}

1. **[!UICONTROL 첨부 파일]**&#x200B;을 선택합니다. 에이전트 UI는 대화형 통신을 만드는 동안 설정된 대로 사용 가능한 첨부 파일을 표시합니다.

   보기 아이콘을 눌러 Interactive Communication과 함께 첨부를 제출하지 않도록 선택할 수 있으며, 첨부의 십자가를 눌러 Interactive Communication에서 첨부를 삭제(에이전트가 첨부를 삭제하거나 숨길 수 있는 경우)할 수 있습니다. 대화형 통신을 만드는 동안 필수로 지정된 첨부 파일의 경우 보기 및 삭제 아이콘이 비활성화됩니다.

   ![attachmentsagentui](assets/attachmentsagentui.png)

1. 라이브러리 액세스( ![라이브러리 액세스](assets/libraryaccess.png)) 아이콘을 눌러 콘텐츠 라이브러리에 액세스하여 DAM 에셋을 첨부 파일로 삽입합니다.

   >[!NOTE]
   >
   >[라이브러리 액세스] 아이콘은 [인쇄] 채널의 [문서 컨테이너] 속성에서 대화형 통신을 만드는 동안 라이브러리 액세스가 활성화된 경우에만 사용할 수 있습니다.

1. Interactive Communication을 생성하는 동안 첨부 파일의 순서가 잠기지 않은 경우 첨부 파일을 선택하고 아래 및 위쪽 화살표를 눌러 첨부 파일의 순서를 변경할 수 있습니다.
1. [웹 미리 보기] 및 [인쇄 미리 보기]를 사용하여 요구 사항에 따라 두 출력이 같은지 확인합니다.

   만족할 만한 미리 보기를 찾은 경우 **[!UICONTROL 제출]**&#x200B;을 눌러 Interactive Communication을 게시 프로세스에 제출/보냅니다. 또는 변경 내용을 적용하려면 미리 보기를 종료하여 변경 사항으로 돌아갑니다.

## 텍스트 서식 지정 {#formattingtext}

에이전트 UI에서 텍스트 부분을 편집하는 동안 도구 모음은 선택한 편집 유형에 따라 변경됩니다.글꼴, 단락 또는 목록:

![](assets/typeofformattingtoolbar.png) ![typeoformatting toolbar글꼴 도구 모음](do-not-localize/fonttoolbar.png)

글꼴 툴바

![단락 도구 모음](do-not-localize/paragraphtoolbar.png)

단락 도구 모음

![목록 도구 모음](do-not-localize/listtoolbar.png)

목록 도구 모음

### 텍스트 {#highlightemphasize} 부분 강조/강조

편집 가능한 부분에 있는 텍스트의 일부를\n강조하려면 텍스트를 선택하고 강조 색상을 누릅니다.

![highlighttextagentui](assets/highlighttextagentui.png)

### 서식이 지정된 텍스트 {#pasteformattedtext} 붙여넣기

![텍스트](assets/pastedtext.png)

### 텍스트 {#specialcharacters}에 특수 문자 삽입

에이전트 UI는 210개의 특수 문자를 지원합니다. 관리자는 [사용자 정의 특수 문자에 대한 지원을 사용자 정의](/help/forms/using/custom-special-characters.md)로 추가할 수 있습니다.

#### 첨부 전송 {#attachmentdelivery}

* 서버측 API를 대화형 또는 비대화형 PDF로 사용하여 대화형 통신을 렌더링하면 렌더링된 PDF에 첨부 파일이 PDF 첨부 파일로 포함됩니다.
* 대화형 통신과 관련된 사후 프로세스가 에이전트 UI를 사용하여 제출 문서의 일부로 로드되면 첨부 파일은 List&lt;com.adobe.idp.Document> inAttachmentDocs 매개 변수로 전달됩니다.
* 전자 메일 및 인쇄와 같은 전달 메커니즘 작업 과정에서도 PDF 버전의 대화형 통신과 함께 첨부 파일을 제공합니다.

## 에이전트 사용자 인터페이스 {#actionsagentui}에서 사용할 수 있는 동작 및 정보

### 문서 조각 {#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **위쪽/아래쪽 화살표**:대화형 통신에서 문서 부분을 위 또는 아래로 이동하는 화살표입니다.
* **삭제**:허용되는 경우 대화형 통신에서 문서 부분을 삭제합니다.
* **이전**  페이지 나누기(대상 영역의 하위 부분에 적용 가능):문서 부분 앞에 페이지 나누기를 삽입합니다.
* **들여쓰기**:문서 부분의 들여쓰기를 늘리거나 줄입니다.
* **페이지 나누기 이후** (대상 영역의 하위 부분에 적용 가능):문서 부분 뒤에 페이지 나누기를 삽입합니다.

![dofragoptions](assets/docfragoptions.png)

* 편집(텍스트 부분만 해당):텍스트 문서 부분을 편집하기 위해 서식 있는 텍스트 편집기를 엽니다. 자세한 내용은 [텍스트 서식 지정](#formattingtext)을 참조하십시오.

* 선택(눈 모양 아이콘):대화형 통신에서 문서 부분을 포함\제외합니다.
* 채워지지 않은 값(정보):문서 부분의 칠이 없는 변수 수를 나타냅니다.

### 문서 부분 목록 {#list-document-fragments}

![목록 옵션](assets/listoptions.png)

* 빈 줄 삽입:새 빈 행을 삽입합니다.
* 선택(눈 모양 아이콘):대화형 통신에서 문서 부분을 포함\제외합니다.
* 글머리 기호/번호 매기기 건너뛰기:목록 문서 부분의 글머리 기호/번호 매기기를 건너뛰려면 활성화합니다.
* 채워지지 않은 값(정보):문서 부분의 칠이 없는 변수 수를 나타냅니다.

