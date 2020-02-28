---
title: GQL 전체 텍스트 검색
description: AEM 자산에서 GQL 전체 텍스트 검색 기능을 살펴보십시오. 제목, 설명 및 작성자 이름과 같은 특정 메타데이터를 기반으로 자산을 검색할 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: adf44677a0ac833a131aad8187529b094aaca9ef

---


# GQL 전체 텍스트 검색 {#gql-full-text-search}

AEM 자산에서 GQL 전체 텍스트 검색 기능을 살펴보십시오. 제목, 설명 및 작성자 이름과 같은 특정 메타데이터를 기반으로 자산을 검색할 수 있습니다.

GQL 전체 텍스트 검색 기능을 사용하면 제목, 설명, 작성자 등과 같은 특정 메타데이터를 기반으로 자산을 검색할 수 있습니다.

제목 등의 메타데이터를 기반으로 자산을 검색하려면 검색 패널에서 메타데이터 키워드 다음에 해당 값을 지정합니다. GQL 전체 텍스트 검색 기능은 사용자가 입력한 값과 메타데이터가 정확히 일치하는 자산만 가져옵니다.

예를 들어 제목이 &quot;Target&quot;인 자산을 검색하려면 다음 단계를 수행하십시오.

## 자산 검색 {#searching-assets}

1. 자산 사용자 인터페이스의 도구 모음에서 검색 **[!UICONTROL 아이콘을 클릭하거나 탭하여]** Omnisearch 상자를 표시합니다.

   ![](assets/do-not-localize/chlimage_1.png)

1. Omnisearch 상자에 커서를 두고 Enter 키를 누릅니다.
1. GlobalNav 아이콘을 클릭하거나 탭하여 필터 **[!UICONTROL 패널을]** 표시합니다.
1. 전체 검색 상자에서 값 &quot;Target&quot;을 지정합니다. 검색을 특정 폴더로 제한하려면 필터 패널에서 찾아보기 아이콘을 클릭하거나 탭하고 폴더를 선택합니다. 이 경우 폴더 및 하위 폴더 내에서만 일치 항목이 검색됩니다.

   >[!NOTE]
   >
   >폴더에서 전체 텍스트 검색을 수행할 수도 있습니다. 이 경우 비어 있지 않은 전체 텍스트 검색어를 지정해야 합니다.

   ![gql_search](assets/gql_search.png)

1. Enter **[!UICONTROL 키를 누릅니다]**. AEM 자산 사용자 인터페이스는 제목이 &quot;Target&quot;과 정확히 일치하는 자산만 표시합니다.

GQL 전체 텍스트 검색 기능을 사용하면 다음을 기반으로 자산을 검색할 수 있습니다.

* And 작업, 여러 메타데이터 필드에 대해 지정한 값(속성)을 결합하여 만들어진 복잡한 쿼리
* 단일 메타데이터 필드에 대한 여러 값
* 하위 문자열 일치

GQL 전체 텍스트 검색 기능을 사용하면 다음 메타데이터 속성을 기반으로 자산을 검색할 수 있습니다. 속성 이름(예: 작성자, 제목 등)과 값은 대/소문자를 구분합니다.

>[!NOTE]
>
>GQL 전체 텍스트 검색은 전체 텍스트 조건자만 사용할 수 있습니다.

| 속성 | 검색 형식(패싯 값) |
|---|---|
| [!UICONTROL 제목] | 제목:John |
| [!UICONTROL 작성자] | creator:John |
| [!UICONTROL 내용 작성자] | contributor:John |
| [!UICONTROL 위치] | 위치:인도 |
| [!UICONTROL 설명] | 설명:&quot;샘플 이미지&quot; |
| [!UICONTROL 작성자 도구] | creatortool:&quot;Adobe Photoshop 7.0&quot; |
| [!UICONTROL 저작권 소유자] | 저작권 소유자:&quot;Adobe Systems&quot; |
| [!UICONTROL 내용 작성자] | contributor:John |
| [!UICONTROL 사용 약관] | usageterms:&quot;CopyRights Reserved&quot; |
| [!UICONTROL 작성됨] | created:YYYY-MM-DDTHH:MM:SS.000+05:30.YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 만료 날짜] | expires:YYYY-MM-DDTHH:MM:SS.000+05:30.YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 정시] | ontime:YYYY-MM-DDTHH:MM:SS.000+05:30.YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 해제 시간] | offtime:YYYY-MM-DDTHH:MM:SS.000+05:30.YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 시간] 범위(만료 날짜 시간, 시간 외) | 패싯 필드:하한...맨 바운드 |
| [!UICONTROL 경로] | /content/dam/&lt;폴더 이름> |
| [!UICONTROL PDF 제목] | pdftitle:&quot;Adobe Document&quot; |
| [!UICONTROL 제목] | 제목:&quot;교육&quot; |
| [!UICONTROL 태그] | 태그:&quot;위치 및 여행&quot; |
| [!UICONTROL 유형] | type:&quot;image\png&quot; |
| [!UICONTROL 이미지 너비] | width:lower bound..맨 바운드 |
| [!UICONTROL 이미지 높이] | height:lower bound.맨 바운드 |
| [!UICONTROL 개인] | 사람:John |

다음은 복잡한 쿼리에 대한 검색 형식의 예입니다.

* 여러 패싯 필드가 있는 모든 자산을 표시하려면(예:title=John Doe 및 creator 도구 = Adobe Photoshop):

tiltle:&quot;John Doe&quot; creatortool :Adobe&amp;ast;

* 패싯 값이 단일 단어가 아닌 문장일 때 모든 자산을 표시하려면(예:title=Scott Reynolds)

title:&quot;Scott Reynolds&quot;

* 단일 속성의 여러 값이 있는 자산을 표시하려면(예:title=Scott Reynolds 또는 John Doe)

title: &quot;Scott Reynolds&quot; OR &quot;John Doe&quot;

* 특정 문자열로 시작하는 속성 값이 있는 자산을 표시하려면(예:제목은 스콧 레이놀즈)

title:&quot;Scott&quot;

* 속성 값이 특정 문자열로 끝나는 자산을 표시하려면(예:제목은 스콧 레이놀즈)

title:&quot;Reynolds&quot;

* 특정 문자열이 포함된 속성 값을 사용하여 자산을 표시하려면(예:title = 바젤 회의실)

title:&quot;회의&quot;;

* 특정 문자열이 들어 있고 특정 속성 값이 있는 자산을 표시하려면(예:title=John Doe가 있는 자산에서 문자열 Adobe 검색)

&amp;ast;Adobe&amp;ast;title:&quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>속성 경로, 제한, 크기 및 orderby는 다른 속성과 함께 OR을 사용할 수 없습니다.
>
>사용자 생성 속성의 키워드는 속성 편집기에서 필드 레이블로, 공백이 제거되었습니다.


>[!NOTE]
>
>JCR 쿼리를 작성하여 하위 자산만 검색할 경우 일치하는 하위 자산과 함께 참조된 일치하는 자산도 표시됩니다.

전체 텍스트 검색도 -,^ 등과 같은 연산자를 지원합니다. 이러한 문자를 문자열 리터럴로 검색하려면 검색 표현식을 큰 따옴표로 묶습니다. 예를 들어 노트북 - Beauty 대신 &quot;Notebook - Beauty&quot;를 사용합니다.

## 검색 향상 {#boosting-search}

특정 자산에 대한 키워드의 관련성을 개선하여 키워드를 기반으로 검색을 강화할 수 있습니다. 즉, 특정 키워드를 홍보하는 이미지가 이러한 키워드를 기준으로 검색할 때 검색 결과 상단에 표시됩니다.

1. 자산 UI에서 키워드를 홍보할 자산의 속성 페이지를 엽니다.
1. 고급 **[!UICONTROL 탭으로 전환하고]** 검색 키워드의 **** 권한 **[!UICONTROL 상승에서]**&#x200B;추가를 클릭/탭합니다.

   ![eleving_for_search](assets/elevate_for_search.png)

1. [ **[!UICONTROL 홍보 검색]** ] 상자에서 이미지 검색을 강화할 키워드를 지정한 다음 추가를 클릭/ **[!UICONTROL 탭합니다]**. 필요한 경우 동일한 방법으로 여러 키워드를 지정합니다.

   ![add_search_word](assets/add_search_word.png)

1. 저장 및 **[!UICONTROL 닫기를 클릭/탭합니다]**.
1. Omnisearch 상자를 사용하여 키워드를 검색합니다. 이 키워드를 승격시킨 자산이 상위 검색 결과 내에 나타납니다.