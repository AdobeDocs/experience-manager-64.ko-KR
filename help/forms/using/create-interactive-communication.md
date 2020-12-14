---
title: 대화형 통신 만들기
seo-title: 대화형 통신 만들기
description: '대화형 통신 편집기를 사용하여 대화형 통신을 만듭니다. 드래그 앤 드롭 기능을 사용하여 인터랙티브한 커뮤니케이션을 제작하고 다양한 디바이스 유형의 인쇄 및 웹 출력을 모두 미리 볼 수 있습니다. '
seo-description: '대화형 통신 편집기를 사용하여 대화형 통신을 만듭니다. 드래그 앤 드롭 기능을 사용하여 인터랙티브한 커뮤니케이션을 제작하고 다양한 디바이스 유형의 인쇄 및 웹 출력을 모두 미리 볼 수 있습니다. '
uuid: b98e9a49-cef2-42f2-b484-8765b859895b
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c106aa41-cbc0-4daf-9ac6-6c0d23710010
translation-type: tm+mt
source-git-commit: 73d0dea62c294bea435364fb9c6892d80751d90d
workflow-type: tm+mt
source-wordcount: '3152'
ht-degree: 2%

---


# 대화형 통신 만들기 {#create-an-interactive-communication}

대화형 통신 편집기를 사용하여 대화형 통신을 만듭니다. 드래그 앤 드롭 기능을 사용하여 인터랙티브한 커뮤니케이션을 제작하고 다양한 디바이스 유형의 인쇄 및 웹 출력을 모두 미리 볼 수 있습니다.

## 개요 {#overview}

Interactive Communications는 개인화되고 인터랙티브한 커뮤니케이션의 작성, 조합 및 전달을 중앙에서 관리하고 관리합니다. 인쇄를 웹용 마스터 채널로 활용하면 인터랙티브 커뮤니케이션의 웹 출력을 만들 때 중복 작업을 최소화할 수 있습니다.

### 전제 조건 {#prerequisites}

다음은 대화형 통신을 만들기 위한 사전 요구 사항입니다.

* 테스트 데이터를 포함하거나 Microsoft® Dynamics 인스턴스와 같은 실제 데이터 소스를 사용하여 [양식 데이터 모델](/help/forms/using/data-integration.md)을 설정합니다.
* [문서 조각](/help/forms/using/document-fragments.md)이(가) 있는지 확인합니다.
* 인쇄 및 웹 채널용 [템플릿이 있는지 확인합니다](/help/forms/using/web-channel-print-channel.md).
* 웹 채널에 필요한 [테마](/help/forms/using/themes.md)가 있는지 확인합니다.

## 대화형 통신 만들기 {#createic}

1. AEM 작성자 인스턴스에 로그인하고 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; 문서]**&#x200B;로 이동합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 누르고 **[!UICONTROL 대화형 통신]**&#x200B;을 선택합니다. [대화형 통신 만들기] 페이지가 나타납니다.

   ![인터랙티브한 커뮤니케이션 제작](assets/create-interactive-communication.png)

1. 다음 정보를 입력합니다. :

   * **[!UICONTROL 제목]**:대화형 통신 제목을 입력합니다.
   * **[!UICONTROL 이름*]**:대화형 통신 이름은 입력한 제목에서 파생됩니다. 필요한 경우 편집합니다.
   * **[!UICONTROL 설명]**:대화형 통신에 대한 설명을 입력합니다.
   * **[!UICONTROL 양식 데이터 모델*]**:양식 데이터 모델을 찾아 선택합니다. 양식 데이터 모델에 대한 자세한 내용은 [AEM Forms 데이터 통합](/help/forms/using/data-integration.md)을 참조하십시오.
   * **[!UICONTROL 자동 완성 서비스]**:데이터를 검색하고 대화형 통신을 미리 입력할 자동 채우기 서비스를 선택합니다.
   * **[!UICONTROL 게시 프로세스 유형]**:대화형 통신이 전송될 때 트리거할 AEM 또는 Forms 워크플로우를 선택할 수 있습니다. 트리거할 워크플로우의 유형을 선택합니다.
   * **[!UICONTROL 게시 프로세스]**:트리거할 워크플로우의 이름을 선택합니다. AEM 워크플로우를 선택하면 첨부 파일 경로, 레이아웃 경로, PDF 경로, 인쇄 데이터 경로 및 웹 데이터 경로를 제공합니다.
   * **[!UICONTROL 태그]**:대화형 통신에 적용할 태그를 선택합니다. 새/사용자 지정 태그 이름을 입력하고 Enter 키를 눌러 작성할 수도 있습니다.
   * **[!UICONTROL 작성자]**: 작성자 이름은 로그인한 사용자의 사용자 이름에서 자동으로 가져옵니다.
   * **[!UICONTROL 게시 날짜:]** 대화형 통신을 게시할 날짜를 입력합니다.
   * **[!UICONTROL 게시 취소 날짜]**:대화형 통신을 게시 취소할 날짜를 입력합니다.

1. **[!UICONTROL 다음]**&#x200B;을 누릅니다. 인쇄 및 웹 채널 세부 사항을 지정하는 화면이 나타납니다.
1. 다음을 입력합니다.

   * **[!UICONTROL 인쇄]**:대화형 통신 인쇄 채널을 생성하려면 이 옵션을 선택합니다.
   * **[!UICONTROL 인쇄 템플릿*:]** XDP를 찾아 인쇄 템플릿으로 선택합니다.
   * **[!UICONTROL 웹 기본 채널에 대해 다른 이름으로 인쇄 사용:]** 인쇄 채널과 동기화된 웹 채널을 만들려면 이 옵션을 선택합니다. 웹 채널의 마스터로 인쇄 채널을 사용하면 웹 채널의 컨텐츠 및 데이터 바인딩이 인쇄 채널에서 파생되고 동기화를 누를 때 인쇄 채널의 변경 사항이 웹 채널에 반영됩니다. 그러나 작성자는 필요에 따라 웹 채널의 특정 구성 요소에 대한 상속을 중단할 수 있습니다. 자세한 내용은 [웹 채널을 인쇄 채널과 동기화](/help/forms/using/create-interactive-communication.md#synchronize)를 참조하십시오.
   * **[!UICONTROL 웹:]** 이 옵션을 선택하여 웹 채널 또는 대화형 통신의 응답형 출력을 생성합니다.
   * **[!UICONTROL 대화형 통신 웹 템플릿*:]** 웹 템플릿을 찾아 선택합니다.
   * **[!UICONTROL 테마]** 및  **[!UICONTROL 테마 선택*]**:인터랙티브 커뮤니케이션의 웹 채널의 스타일을 지정할 테마를 찾아보고 선택합니다. 자세한 내용은 AEM Forms](/help/forms/using/themes.md)의 [테마를 참조하십시오.

   인쇄 채널 및 웹 채널에 대한 자세한 내용은 [인쇄 채널 및 웹 채널](/help/forms/using/web-channel-print-channel.md)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;를 누릅니다. [대화형 통신]이 생성되고 경고 상자가 나타납니다. [Add contents using Interactive Communication authoring user interface](#step2)에 설명된 대로 **[!UICONTROL 편집]**&#x200B;을 눌러 대화형 커뮤니케이션의 컨텐츠를 작성하기 시작합니다. 또는 **[!UICONTROL 완료]**&#x200B;를 탭하고 나중에 대화형 통신을 편집하도록 선택할 수 있습니다.

## 대화형 통신 {#step2}에 콘텐트 추가

대화형 통신을 만든 후 대화형 통신 제작 인터페이스를 사용하여 내용을 구성할 수 있습니다.

대화형 통신 제작 인터페이스에 대한 자세한 내용은 [대화형 통신 제작 소개](/help/forms/using/introduction-interactive-communication-authoring.md)를 참조하십시오.

1. [대화형 통신 만들기](#createic)에 언급된 대로 편집을 탭하면 대화형 통신 제작 인터페이스가 시작됩니다. 또는 AEM의 기존 대화형 통신 자산으로 이동하여 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 눌러 대화형 통신 작성 인터페이스를 시작할 수 있습니다.

   대화형 통신이 웹 채널 전용인 경우를 제외하고 기본적으로 대화형 통신의 인쇄 채널이 표시됩니다. 선택한 XDP/인쇄 채널 템플릿에서 사용할 수 있는 대화형 커뮤니케이션의 인쇄 채널에는 대상 영역이 표시됩니다. 이러한 대상 영역 및 필드에서 구성 요소나 자산을 추가할 수 있습니다.

1. 인쇄 채널을 선택한 상태에서 **[!UICONTROL 구성 요소]** 탭을 선택합니다. 다음 구성 요소는 인쇄 채널에서 사용할 수 있습니다.

   | **구성 요소** | **기능** |
   |---|---|
   | Chart | 양식 데이터 모델 컬렉션에서 검색된 2차원 데이터를 시각적으로 표시하기 위해 대화형 커뮤니케이션에서 사용할 수 있는 차트를 추가합니다. 자세한 내용은 [Interactive Communications에서 차트 사용](/help/forms/using/chart-component-interactive-communications.md)을 참조하십시오. |
   | 문서 단편 | 텍스트, 목록 또는 조건 등의 재사용 가능한 구성 요소를 대화형 통신에 추가할 수 있습니다. 추가된 구성 요소는 양식 데이터 모델 기반이거나 양식 데이터 모델이 없을 수 있습니다. |
   | 이미지 | 이미지를 삽입할 수 있습니다. |

   구성 요소를 대화형 통신에 드래그하여 놓고 필요에 따라 구성합니다.

1. 인쇄 채널이 선택된 상태에서 **[!UICONTROL 자산]** 탭으로 이동하여 보려는 자산만 표시하도록 필터를 적용합니다.

   자산 브라우저를 사용하여 대화형 통신 대상 영역에 자산을 직접 드래그하여 놓을 수도 있습니다.

   ![assets-docfragments](assets/assets-docfragments.png)

1. 문서 조각을 대화형 통신에 드래그하여 놓습니다. 다음은 대화형 통신 인쇄 채널에서 사용할 수 있는 문서 조각 유형입니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>문서 단편 유형</strong></td> 
   <td><strong>목적 예</strong></td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">텍스트</a></td> 
   <td>문자의 주소, 수신자 이메일 및 본문 텍스트를 추가하는 텍스트 </td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">조건</a></td> 
   <td>정책 유형에 따라 커뮤니케이션에 적절한 헤더 이미지를 추가하는 조건:Standard 또는 Premium.<br /> </td> 
  </tr> 
  <tr> 
   <td>목록</td> 
   <td>텍스트, 조건, 기타 목록 및 이미지를 비롯한 문서 조각 그룹입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

문서 조각에 대한 자세한 내용은 [문서 조각](/help/forms/using/document-fragments.md)을 참조하십시오.

1. 변수의 바인딩을 설정하려면 변수를 누르고 ![configure_icon](assets/configure_icon.png)(구성)을 선택한 다음 세로 막대의 속성 패널에서 바인딩 속성을 설정합니다.

   * **[!UICONTROL 없음]**:에이전트가 변수의 값을 채웁니다.
   * **[!UICONTROL 텍스트 조각]**:이 옵션을 선택하면 컨텐츠를 필드에 렌더링하는 텍스트 문서 조각을 찾아 선택할 수 있습니다. 이러한 텍스트 문서 조각만 안에 변수가 없는 변수에 바인딩할 수 있습니다.
   * **[!UICONTROL 데이터 모델 개체]**:필드에 값이 채워지는 양식 데이터 모델 속성을 선택합니다.

   관련 텍스트 문서 조각을 구성하도록 선택할 수도 있습니다. 속성 패널에는 텍스트 문서 조각에 있는 변수 목록이 표시됩니다. 변수 이름 옆에 있는 ![편집](assets/edit.png)(편집)을 탭하여 해당 변수의 편집 설정을 표시할 수 있습니다.

1. 표를 추가하려면 인쇄 채널이 선택된 상태로 **[!UICONTROL 자산]** 탭에서 필터를 적용하여 레이아웃 조각만 표시합니다. 필요한 레이아웃 조각을 대화형 통신에 드래그하여 놓습니다. 레이아웃 조각은 XDP를 기반으로 하며 동적 데이터로 채워진 대화형 커뮤니케이션에서 그래픽 레이아웃 또는 정적 및 동적 표를 만드는 데 사용할 수 있습니다.

   예:이전 및 새로운 정책에 대한 총보험료, 충성도 할인 % 및 긴급 노변 지원을 표시할 수 있는 레이아웃 표입니다.

   레이아웃 조각에 대한 자세한 내용은 [문서 조각](/help/forms/using/document-fragments.md)을 참조하십시오.

1. 인쇄 채널이 선택된 상태에서 **[!UICONTROL 자산]** 탭에서 필터를 표시 이미지에 적용합니다. 필요한 이미지를 회사 로고 등 인터랙티브 커뮤니케이션에 드래그하여 놓습니다.

   또한 대화형 통신에서 다음을 관리합니다.

   * [차트 추가 및 구성](/help/forms/using/chart-component-interactive-communications.md)
   * [웹 채널을 인쇄 채널과 동기화](/help/forms/using/create-interactive-communication.md#synchronize)

      * 자동 동기화
      * 상속 취소
      * 상속 다시 활성화
      * 동기화
   * [첨부 파일 및 라이브러리 액세스](/help/forms/using/create-interactive-communication.md#attachmentslibrary)
   * [XDP/레이아웃 필드 속성](/help/forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [구성 요소에 규칙 추가](/help/forms/using/create-interactive-communication.md#rules)


1. **[!UICONTROL 웹 채널]**&#x200B;으로 전환합니다. 웹 채널이 대화형 통신 편집기에 나타납니다. 인쇄 채널에서 웹 채널로 처음으로 전환하는 경우 자동 동기화가 발생합니다. 자세한 내용은 인쇄 채널에서 [웹 채널 동기화를 참조하십시오](/help/forms/using/create-interactive-communication.md#synchronize).

   이 예에서는 웹용 마스터로 인쇄를 사용하고 있으므로 인쇄 채널 자리 표시자, 콘텐츠 및 데이터 바인딩이 웹 채널에 동기화됩니다. 그러나 필요에 따라 웹 채널의 특정 컨텐츠를 변경하고 사용자 지정할 수 있습니다.

   ![웹 채널에셋](assets/webchannelassets.png)

1. 웹 채널을 선택하고 웹 채널에 구성 요소를 추가하려면 **[!UICONTROL 구성 요소]**&#x200B;를 누릅니다. 필요에 따라 대화형 커뮤니케이션의 웹 채널에서 구성 요소를 드래그하여 놓고 구성한 다음 계속 진행합니다.

   | 구성 요소 | 기능 |
   |---|---|
   | 차트 | 양식 데이터 모델 컬렉션에서 검색된 2차원 데이터를 시각적으로 표시하기 위해 대화형 커뮤니케이션에서 사용할 수 있는 차트를 추가합니다. 자세한 내용은 [차트 구성 요소 사용](/help/forms/using/chart-component-interactive-communications.md)을 참조하십시오. |
   | 문서 단편 | 재사용 가능한 구성 요소, 텍스트, 목록 또는 조건을 대화형 통신에 추가할 수 있습니다. 대화형 통신에 추가하는 재사용 가능한 구성 요소는 양식 데이터 모델 기반 또는 양식 데이터 모델 없이 구성할 수 있습니다. |
   | 이미지 | 이미지를 삽입할 수 있습니다. |
   | 패널 | 패널 구성 요소는 다른 구성 요소를 함께 그룹화하기 위한 자리 표시자이며, 아코디언 및 탭과 같은 구성 요소 그룹이 대화형 통신에 어떻게 배치되는지 제어합니다. 또한 패널 구성 요소를 사용하면 교육 자격 증명을 채우는 데 필요한 여러 항목을 포함하여 최종 사용자를 위해 반복 가능한 구성 요소 그룹을 만들 수 있습니다. |
   | 표 | 행 및 열에 데이터를 구성할 수 있는 표를 추가합니다. |
   | 대상 영역 | 웹 채널에서 대상 영역을 삽입하여 웹 채널별 구성 요소를 구성합니다. Target 영역은 웹 채널 특정 구성 요소를 그룹화할 수 있는 일반 컨테이너입니다. |
   | 텍스트 | 대화형 커뮤니케이션의 웹 채널에 리치 텍스트를 추가합니다. 또한 텍스트는 양식 데이터 모델 개체를 사용하여 내용을 동적으로 만들 수도 있습니다. |

1. 필요에 따라 웹 채널에 에셋을 삽입합니다.

   [대화형 통신](#previewic)을 미리 보고 대화형 통신의 인쇄 및 웹 출력이 어떻게 표시되는지 확인하고 필요에 따라 계속 변경할 수 있습니다.

## 대화형 통신 미리 보기 {#previewic}

**[!UICONTROL 미리 보기]** 옵션을 사용하여 대화형 통신 모양을 평가할 수 있습니다. 또한 인터랙티브 커뮤니케이션의 웹 채널은 다양한 디바이스에 대한 인터랙티브 커뮤니케이션의 경험을 에뮬레이션하는 옵션을 제공합니다. 예: iPhone, iPad 및 Desktop. **[!UICONTROL 미리 보기]** 및 **[!UICONTROL 에뮬레이터]** ![눈금자](assets/ruler.png) 옵션을 모두 함께 사용하여 서로 다른 화면 크기의 장치에 대한 웹 출력을 미리 볼 수 있습니다. 미리 보기의 샘플 데이터는 지정된 양식 데이터 모델에서 채워집니다.

1. 미리 보기를 미리 보고 탭할(인쇄 또는 웹) 채널을 선택합니다. [대화형 통신]이 나타납니다.

   >[!NOTE]
   >
   >미리 보기는 지정된 양식 데이터 모델의 샘플 데이터로 채워집니다. 다른 데이터와 대화형 통신을 미리 보거나 프리플라이트 서비스를 사용하는 방법에 대한 자세한 내용은 [양식 데이터 모델 사용](/help/forms/using/using-form-data-model.md) 및 [양식 데이터 모델 사용](/help/forms/using/work-with-form-data-model.md)을 참조하십시오.

1. 웹 채널의 경우 ![눈금자](assets/ruler.png)를 사용하여 다양한 장치에서 대화형 통신이 어떻게 보이는지 확인합니다.

   ![웹 채널 미리 보기](assets/webchannelpreview.png)

또한 에이전트 UI](/help/forms/using/prepare-send-interactive-communication.md)를 사용하여 [대화형 통신을 준비하고 전송할 수 있습니다.

## 대화형 통신에서 속성 구성 {#configuring-properties-in-interactive-communication}

### 첨부 파일 및 라이브러리 액세스 {#attachmentslibrary}

인쇄 채널에서 에이전트가 대화형 통신용 에이전트 UI의 첨부 파일을 관리하도록 첨부 파일 및 라이브러리 액세스를 구성할 수 있습니다.

1. 인쇄 채널에서 문서 컨테이너를 선택하고 **[!UICONTROL 속성]**&#x200B;을 누릅니다.

   ![documenterproperties](assets/documentcontainerproperties.png)

   [속성] 패널이 사이드바에 나타납니다.

   ![속성첨부 파일](assets/propertiesattachments.png)

1. **[!UICONTROL 첨부 파일]**&#x200B;을 확장하고 다음 속성을 지정합니다.

   * **[!UICONTROL 라이브러리 액세스 허용]**:에이전트 UI에서 에이전트에 대한 라이브러리 액세스를 활성화하려면 선택합니다. 활성화된 경우 에이전트는 대화형 통신을 준비하는 동안 라이브러리에서 파일을 추가할 수 있습니다.
   * **[!UICONTROL 첨부 파일 순서 재지정 허용]**:Interactive Communication을 사용하여 첨부 파일의 순서를 재지정할 수 있도록 하려면 선택합니다.
   * **[!UICONTROL 허용되는 최대 첨부 파일 수]**:대화형 통신에서 허용되는 최대 첨부 파일 수를 지정합니다.
   * **[!UICONTROL 첨부할]** 파일:추가 **** 를 눌러 첨부할 파일을 선택하고 다음을 지정합니다.

      * **[!UICONTROL 기본적으로 이 파일을 문서에 첨부합니다]**.첨부 파일만 필수가 아닌 경우 이 옵션을 변경할 수 있습니다.
      * **[!UICONTROL 필수:]** 에이전트가 에이전트 UI에서 첨부 파일을 제거할 수 없습니다.

   ![첨부 파일](assets/attachfiles.png)

1. **[!UICONTROL Done]**&#x200B;을 누릅니다.

### XDP/레이아웃 필드 속성 {#xdplayoutfieldproperties}

1. 대화형 통신의 인쇄 채널을 편집하는 동안 인쇄 채널 템플릿에 내장된 필드를 마우스로 가리키고 ![configure_icon](assets/configure_icon.png) (구성)을 선택합니다.

   세로 막대에 [속성] 대화 상자가 나타납니다.

   ![xdpfieldproperties](assets/xdpfieldproperties.png)

1. 다음을 지정합니다.

   * **[!UICONTROL 이름]**:JCR 노드 이름입니다.
   * **[!UICONTROL 제목]**:에이전트 UI와 문서 컨테이너 트리에서 에이전트가 볼 수 있는 제목을 입력합니다.
   * **[!UICONTROL 바인딩 유형]**:필드에 대해 다음 바인딩 유형 중 하나를 선택합니다.

      * 없음:에이전트가 속성 값을 채웁니다.
      * 텍스트 조각:이 옵션을 선택한 경우 필드에서 컨텐츠가 렌더링되는 텍스트 문서 조각을 찾아 선택할 수 있습니다.
      * 데이터 모델 개체:필드에 값이 채워지는 양식 데이터 모델 속성을 선택합니다.
   * **[!UICONTROL 기본값]**:기본값을 사용하면 지정된 데이터 모델 개체 또는 텍스트 조각에서 제공하는 값이 없을 때 필드가 비어 있지 않습니다. 데이터 바인딩 유형이 none이면 필드에 기본값이 미리 채워집니다.
   * **[!UICONTROL 에이전트가 편집 가능]**:에이전트가 에이전트 UI의 필드에 값을 편집할 수 있도록 허용하려면 선택합니다. 바인딩 유형이 텍스트 조각인 경우에는 이 설정을 적용할 수 없습니다.
   * **[!UICONTROL 레이블]**:에이전트 UI에서 에이전트에 필드에 표시되는 텍스트 문자열을 지정합니다. 바인딩 유형이 텍스트 조각인 경우에는 이 설정을 적용할 수 없습니다.
   * **[!UICONTROL 도구 설명]**:에이전트 UI에서 마우스로 에이전트 위에 표시할 텍스트 문자열을 입력합니다. 바인딩 유형이 텍스트 조각인 경우에는 이 설정을 적용할 수 없습니다.
   * **[!UICONTROL 필수]**:에이전트를 위해 필드를 필수 항목으로 지정하려면 선택합니다. 바인딩 유형이 텍스트 조각인 경우에는 이 설정을 적용할 수 없습니다.
   * **[!UICONTROL 여러 줄 허용]**:여러 줄의 텍스트를 필드에 입력하도록 허용하려면 이 필드를 선택합니다. 바인딩 유형이 텍스트 조각인 경우에는 이 설정을 적용할 수 없습니다.


1. ![done_icon](assets/done_icon.png)을 누릅니다.

## 대화형 통신 구성 요소에 규칙 적용 {#rules}

대화형 커뮤니티에서 구성 요소 또는 컨텐트를 조건화하려면 구성 요소/컨텐트를 누르고 ![createruleicon](assets/createruleicon.png)(규칙 만들기)을 선택하여 규칙 편집기를 실행합니다.

자세한 내용은 다음을 참조하십시오.

* [규칙 편집기](/help/forms/using/rule-editor.md)
* [인터랙티브 커뮤니케이션 제작 소개](/help/forms/using/introduction-interactive-communication-authoring.md)

## {#tables} 테이블 사용

### 대화형 통신 {#dynamic-tables-in-interactive-communication}의 동적 표

레이아웃 조각을 사용하여 대화형 통신에 동적 표를 추가할 수 있습니다. 다음 단계에서는 신용카드 명세서의 예를 사용하여 대화형 커뮤니케이션에서 동적 테이블을 생성하기 위해 레이아웃 조각을 사용하는 방법을 보여 줍니다.

1. 표를 만드는 데 필요한 레이아웃 조각을 AEM에서 사용할 수 있는지 확인합니다.
1. 대화형 커뮤니케이션의 인쇄 채널에서 자산 브라우저의 Target 영역에 있는 레이아웃 조각(다중 열 테이블 포함)을 드래그하여 놓습니다.

   ![lf_dragdrop](assets/lf_dragdrop.png)

   [대화형 통신] 레이아웃 영역에 표가 나타납니다.

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. 표의 각 셀에 대한 데이터 바인딩을 지정합니다. 반복 가능한 행을 만들려면 공통 컬렉션 속성에 속하는 행에 양식 데이터 모델 속성을 삽입합니다.

   1. 테이블의 셀을 누르고 ![configure_icon](assets/configure_icon.png) (구성)을 선택합니다.

      세로 막대에 [속성] 대화 상자가 나타납니다.

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. 속성을 구성합니다.

      * **[!UICONTROL 이름]**:JCR 노드 이름입니다.
      * **[!UICONTROL 제목]**:대화형 통신 편집기에서 볼 제목을 입력합니다.
      * **[!UICONTROL 바인딩 유형]**(&amp;A):필드에 대해 다음 바인딩 유형 중 하나를 선택합니다.

         * **[!UICONTROL 없음]**
         * **[!UICONTROL 데이터 모델 개체]**:양식 데이터 모델 속성의 값이 필드에 채워집니다.
      * **[!UICONTROL 데이터 모델 개체]**:필드에 값이 채워지는 양식 데이터 모델 속성입니다.
      * **[!UICONTROL 기본값]**:기본값을 사용하면 지정된 데이터 모델 개체에 의해 제공된 값이 없을 때 필드가 비어 있지 않습니다. 기본값은 필드에 미리 채워집니다.
      * **[!UICONTROL 에이전트가 편집 가능]**:에이전트가 에이전트 UI의 필드에 값을 편집할 수 있도록 허용하려면 선택합니다.
   1. ![done_icon](assets/done_icon.png)을 누릅니다.



1. 데이터를 사용하여 렌더링된 표를 보려면 대화형 통신을 미리 봅니다.

   ![lf_preview](assets/lf_preview.png)

### 웹 채널 전용 테이블 {#web-channel-only-tables}

유형 컬렉션의 데이터 모델 속성을 사용하여 대화형 통신에 웹 채널 전용 동적 테이블을 만들 수 있습니다. 이러한 표는 컬렉션 속성의 자식 속성을 나타냅니다. 표에 있는 다양한 셀의 서식 속성만 편집할 수 있습니다.

1. 웹 채널로 전환한 다음 Data Sources 브라우저를 표시하도록 선택합니다.
1. 컬렉션 속성을 하위 폼으로 드래그하여 놓습니다.

   하위 폼에서 표가 만들어집니다.

1. 대화형 통신의 웹 미리 보기에서 표를 미리 봅니다.

## 웹 채널을 인쇄 채널 {#synchronize}과 동기화

대화형 통신을 만들 때 기본 웹 채널용으로 인쇄를 선택하면 웹 채널이 인쇄 채널과 동기화되고 웹 채널의 컨텐츠 및 데이터 바인딩이 인쇄 채널에서 파생되며, 동기화를 탭하면 인쇄 채널에서 수행된 변경 사항이 웹 채널에 반영됩니다.

그러나 작성자는 필요에 따라 웹 채널의 구성 요소에 대한 상속을 중단할 수 있습니다.
![printweb_2-3](assets/printweb_2-3.png)
[클릭하여 확대](assets/printweb_2-3.png)

![인터랙티브 커뮤니케이션 편집기에서 인쇄 및 웹 채널](assets/printweb_2-1.png)

### 자동 동기화 {#auto-sync}

인쇄 채널을 웹 채널의 마스터로 사용하고 인쇄 채널에서 웹 채널로 전환하는 경우 자동 동기화가 발생합니다. 자동 동기화는 자리 표시자, 콘텐트 및 데이터 바인딩을 인쇄 채널에서 웹 채널에 가져옵니다. 인터랙티브 커뮤니케이션의 복잡성과 내용에 따라 자동 동기화를 수행하는 데 시간이 걸릴 수 있습니다.

>[!NOTE]
>
>채널을 동기화하면 문서 조각, 이미지, 조건, 목록 및 레이아웃 조각만 인쇄 채널의 웹 채널에 동기화됩니다. 이러한 요소를 포함하는 하위 양식 또는 상위 노드는 동기화되지 않습니다.

### 상속 취소 {#cancel-inheritance}

웹 채널에서 구성 요소는 대상 영역에 포함됩니다.

웹 채널에서 관련 대상 영역 위로 마우스를 가져간 후 ![cancele상속](assets/cancelinheritance.png)(상속 취소)을 선택한 다음 상속 취소 대화 상자에서 **[!UICONTROL Yes]**&#x200B;를 탭합니다.

대상 영역 내의 구성 요소 상속이 취소되고 이제 필요에 따라 편집할 수 있습니다.

### 상속 다시 사용 {#re-enable-inheritance}

웹 채널에서 구성 요소의 상속을 취소한 경우 다시 활성화할 수 있습니다. 상속을 다시 활성화하려면 구성 요소를 포함하는 관련 대상 영역의 경계를 가리키고 ![reenableinheritance](assets/reenableinheritance.png)을 탭합니다.

상속 되돌리기 대화 상자가 나타납니다.

![반향 상속](assets/revertinheritance.png)

필요한 경우 **[!UICONTROL 상속을 되돌린 후 페이지 동기화]**&#x200B;를 선택합니다. 전체 대화형 통신을 동기화하려면 이 옵션을 선택합니다. 이 옵션을 선택하지 않으면 상속을 재활성화할 때 관련 대상 영역만 동기화됩니다.

**[!UICONTROL Yes]**&#x200B;을 누릅니다.

### 동기화 {#synchronize-1}

웹 채널용으로 인쇄기본을 사용하고 인쇄 채널을 변경하는 경우 동기화를 눌러 새로 변경한 내용을 웹 채널에 가져올 수 있습니다.

1. 웹 채널을 인쇄 채널과 동기화하려면 **[!UICONTROL 동기화]**&#x200B;를 누릅니다.

   [채널에서 콘텐트 기본 동기화] 대화 상자가 나타납니다.

   ![synchronizecontentfrommasterchannel](assets/synchronizecontentfrommasterchannel.png)

1. 다음 중 하나를 누릅니다.

   * **[!UICONTROL 변경 내용 취소]**:웹 채널에서 수행한 변경 내용에 관계없이 웹 채널에 수행된 모든 변경 사항을 삭제합니다.
   * **[!UICONTROL 변경 내용 유지]**:상속이 취소되지 않은 대상 영역에만 컨텐츠를 동기화합니다.

