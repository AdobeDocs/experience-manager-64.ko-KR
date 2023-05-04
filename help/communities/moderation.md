---
title: 중재 콘솔
seo-title: Moderation Console
description: 중재 콘솔에 액세스하는 방법
seo-description: How to access the Moderation console
uuid: 920124b9-af6f-4622-adb6-b8e294c5607d
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6c405543-e339-4916-aa0f-b61d0b798cf3
role: Admin
exl-id: ded38cee-fbce-46cc-974f-38d3a293a55d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1883'
ht-degree: 5%

---

# 중재 콘솔 {#moderation-console}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Communities에서 일괄 [커뮤니티 콘텐츠 조정](moderate-ugc.md) 관리자 및 커뮤니티 중재자(중재자로 지정된 신뢰할 수 있는 커뮤니티 구성원)가 작성 및 게시 환경을 모두 사용할 수 있습니다.

관리자 및 커뮤니티 중재자도 다음 작업을 수행할 수 있습니다 [컨텍스트 내 중재](in-context.md) 를 입력합니다.

모든 기능 [커뮤니티 사이트](sites-console.md) is `Administration`관리자 권한으로 로그인한 사용자가 사용할 수 있는 메뉴 항목입니다. 다음 `Administration`링크를 통해 중재 콘솔에 액세스할 수 있습니다.

중재 콘솔에서 관리자 및 커뮤니티 중재자는 중재할 권한이 있는 모든 사용자 생성 콘텐츠(UGC)에 액세스할 수 있습니다. 여러 사이트를 중재할 수 있는 경우 모든 사이트에서 게시물을 보거나 선택한 커뮤니티 사이트별로 필터링할 수 있습니다.

자세한 내용은 [사용자 및 사용자 그룹 관리](users.md).

중재 콘솔에서는 다음을 지원합니다.
* 일괄 조정 작업 수행
* UGC 검색
* UGC 세부 정보 보기
* UGC 작성자 세부 정보 보기

관리자로 로그인하거나 ` [moderator permissions](in-context.md#identifyingtrustedmembers)`을 사용하면 중재 작업이 수행될 수 있습니다.

## 게시 환경 액세스 {#publish-environment-access}

게시된 커뮤니티 사이트에서 중재 콘솔에 대한 액세스는 커뮤니티 중재자가 로그인하면 나타나는 관리 링크를 통해 수행됩니다.

![publishweretail](assets/publishweretail.png)

관리 링크를 선택하면 관리 콘솔이 나타납니다.

![moderationconsole-publish](assets/moderationconsole-publish.png)

## 작성 환경 액세스 {#author-environment-access}

작성 환경에서 중재 콘솔에 도달하려면

* 전역 탐색에서: **[!UICONTROL 탐색 > 커뮤니티 > 중재]**

관리자로 로그인하거나 ` [moderator permissions](in-context.md#identifyingtrustedmembers)`을 사용하면 중재 작업이 수행될 수 있습니다. 표시된 유일한 커뮤니티 콘텐츠는 로그인한 구성원이 중재할 수 있는 것입니다.

>[!NOTE]
>
>선택한 SRP가 공용 저장소를 구현하는 경우에만 게시 환경의 UGC가 작성자에게만 표시됩니다. 예를 들어 기본적으로 저장소는 작성자 및 게시용 공통 저장소가 아닌 JSRP입니다. 자세한 내용은 [커뮤니티 컨텐츠 저장소](working-with-srp.md).

![moderationconsoleauthor](assets/moderationconsoleauthor.png)

## 중재 콘솔 UI {#moderation-console-ui}

왼쪽 탐색 레일(작성자에는 표시되지만 게시에는 표시되지 않음)을 별도로 설정하면 중재 UI에 다음과 같은 기본 영역이 있습니다.

* **[위쪽 탐색 모음](#top-navigation-bar)**
* **[도구 모음](#toolbar)**
* **[콘텐츠 영역](#content-area)**

### 위쪽 탐색 모음 {#top-navigation-bar}

상단 탐색 막대는 모든 콘솔에 대해 일정합니다. 자세한 내용은 [기본 처리](../../help/sites-authoring/basic-handling.md).

### 도구 모음 {#toolbar}

위쪽 탐색 모음 아래에 있는 도구 모음은 왼쪽에서 다음 전환 스위치를 제공합니다.

* [필터 레일](moderation.md#filter-rail) 컨텐츠를 필터링할 속성을 선택할 수 있는 레일을 엽니다.

위쪽 탐색 모음 아래에 있는 도구 모음은 왼쪽에서 다음 전환 스위치를 제공합니다.

![전환점](assets/toggleswitch.png)

[필터 레일](moderation.md#filter-rail)\
검색을 선택하여 컨텐츠를 필터링할 속성을 선택할 수 있는 레일을 엽니다.

![필경](assets/filterrail.png)

### 컨텐츠 영역 {#content-area}

컨텐츠 영역에는 게시된 UGC에 대한 정보가 포함되어 있습니다.

* UGC가 게시됨
* 멤버 이름
* 멤버 아바타
* 게시물의 위치
* 게시되었을 때
* 게시물에 대한 회신 수
* [감정](moderate-ugc.md#sentiment) 게시물과 연결됨
* 승인되면 확인 표시가 표시됩니다
* 첨부 파일이 있으면 페이퍼클립이 표시됩니다

>[!NOTE]
>
>컨텐츠 영역에는 *무한 스크롤*&#x200B;즉, 컨텐츠의 끝에 도달할 때까지 계속 스크롤할 수 있습니다. 도구 모음은 스크롤하는 동안에도 컨텐츠 영역 위에 고정된 표시된 위치에 유지됩니다.

### 필터 레일 {#filter-rail}

![chlimage_1-472](assets/chlimage_1-472.png)

사이드 패널 아이콘이 필터 레일을 엽니다. 컨텐츠 영역의 왼쪽에 표시되는 필터 레일은 다른 필터를 제공하며, 각 필터는 컨텐츠 영역에 나타나는 참조된 UGC에 즉시 영향을 줍니다.

각 카테고리 내의 필터는 다음과 같습니다 **또는**&#x200B;함께 사용할 수 있으며 다른 카테고리의 필터는 **및**&#x200B;함께

예를 들어, **질문** 및 **답변**&#x200B;과 같은 역할을 하는 **질문** *또는* an **답변**.

하지만, **질문** 및 **보류 중**&#x200B;인 컨텐츠만 표시됩니다 **질문** 및 **보류 중**.

>[!NOTE]
>
>커뮤니티 중재자는 중재 콘솔 UI에 사전 정의된 필터를 책갈피로 지정할 수 있습니다. 이러한 필터가 URL의 끝(쿼리 문자열 매개 변수)에 추가되므로 중재자는 나중에 책갈피가 지정된 필터로 다시 돌아가 이러한 링크를 공유할 수도 있습니다.

![searchicon](assets/searchicon.png)

필터 레일이 열리면 검색 아이콘을 사용하여 사이드 패널을 닫습니다. 하지만 필터 레일을 닫고 사용자가 생성한 컨텐츠만 표시하려면 검색 아이콘을 클릭하고 컨텐츠 전용 옵션을 선택합니다.

#### 컨텐츠 경로 {#content-path}

컨텐츠 경로는 지정된 컨텐츠 저장소에 배치된 게시물에 표시되는 참조 UGC를 제한합니다.

![content-path](assets/content-path.png)

#### 텍스트 검색 {#text-search}

텍스트 검색은 입력한 텍스트가 포함된 게시물에 표시되는 참조된 UGC를 제한합니다.

![chlimage_1-473](assets/chlimage_1-473.png)

#### Site {#site}

사이트에서 선택한 커뮤니티 사이트에 대한 게시물에 표시된 참조된 UGC를 제한합니다. 선택한 사이트가 없으면 UGC에 대한 모든 참조가 표시됩니다.

![chlimage_1-474](assets/chlimage_1-474.png)

>[!NOTE]
>
>관리자가 벌크 중재 콘솔에 액세스하면, [사이트 만들기 마법사](sites-console.md)예: Geometrixx 샘플.
>
>신뢰할 수 있는 커뮤니티 구성원이 게시 시 벌크 중재 콘솔에 액세스하면 구성원이 중재 권한을 가진 커뮤니티 사이트에 대해 작성된 UGC 참조만 표시되고 사이트 필터로 필터링할 수 있습니다.

#### 콘텐츠 유형 {#content-type}

컨텐츠 유형은 선택한 리소스 유형의 게시물에 표시되는 참조된 UGC를 제한합니다. 다음 유형 중 하나 이상을 선택할 수 있습니다. 아무 것도 선택하지 않으면 모든 유형이 표시됩니다.

* **설명**
* **포럼 주제**
* **포럼 답글**
* **QnA 질문**
* **QnA 답변**
* **블로그 항목**
* **블로그 댓글**
* **달력 이벤트**
* **달력 댓글**
* **파일 라이브러리 폴더**
* **파일 라이브러리 문서**
* **아이디어**
* **관념화 댓글**

![컨텐츠 유형](assets/content-types.png)

#### 추가 컨텐츠 유형 {#additional-content-types}

필터링할 리소스를 더 추가하려면:

* 작성자 인스턴스에서
* 관리자로 로그인
* 열기 [웹 콘솔](http://localhost:4502/system/console/configMgr)
* 찾기 `AEM Communities Moderation Dashboard Filters`
* 편집 모드에서 열 구성을 선택합니다
* 필터링할 구성 요소의 ResourceType을 입력합니다
   * 예를 들어 포함된 투표 구성 요소를 필터링하려면 다음을 입력합니다.\
      `Voting=social/tally/components/hbs/voting`

![chlimage_1-475](assets/chlimage_1-475.png)

* 저장을 선택합니다
* 커뮤니티 - 중재 콘솔 새로 고침

그 결과, 선택할 수 있는 새로운 필터가 `Voting`아래에 `Content Type` 필터 그룹.

해당 필터를 선택하면 대시보드의 콘텐츠에 입력한 ResourceTypes와 일치하는 UGC가 표시됩니다.

#### 상태 {#status}

상태는 선택된 상태의 게시물에 표시된 참조된 UGC를 제한합니다. 이 게시물은 보류 중, 승인됨, 거부됨 또는 마감됨, 블로그 문서에 대한 초안 또는 예약됨, QnA 질문에 대해 답변됨 또는 답변되지 않음 중 하나 이상이 될 수 있습니다. 아무 것도 선택하지 않으면 모두 표시됩니다.

>[!NOTE]
>
>답변되지 않음 상태만 선택하면 중재자는 응답된 질문을 제외한 모든 컨텐츠 유형(모든 컨텐츠 유형)을 볼 수 있습니다. 답변되지 않은 질문 및 포럼 주제, 블로그 기사 또는 댓글과 같은 기타 컨텐츠의 경우 답변된 질문에 대한 책임이 있는 속성이 존재하지 않기 때문입니다.

![상태](assets/statuses.png)

#### 플래그 지정 {#flagging}

플래그 지정은 플래그 지정되거나 숨겨진 게시물에 표시되는 참조된 UGC를 제한합니다.

한 내용에 플래그가 지정되면 해당 컨텐츠를 선택하여 플래그를 해제할 때까지 플래그가 지정된 상태로 유지됩니다 **[!UICONTROL 플래그]** 다시 단추를 누릅니다. 중요 또는 후속 단계와 같은 플래그 지정 수준은 없습니다.

![chlimage_1-476](assets/chlimage_1-476.png)

#### 구성원 {#members}

멤버는 입력한 멤버 이름으로 게시된 UGC로 표시된 참조된 UGC를 제한합니다.

![chlimage_1-477](assets/chlimage_1-477.png)

#### 마지막에 게시된 항목 {#posted-in-the-last}

게시한 마지막 시간 제한은 참조된 UGC가 마지막 시간, 일, 주, 월 또는 연도의 게시물에 표시되는 것을 제한합니다.

![chlimage_1-478](assets/chlimage_1-478.png)

#### 감정 {#sentiment}

[감정](moderate-ugc.md#sentiment) 양수, 음수 또는 중립적인 감정 값이 있는 게시물에 표시되는 참조된 UGC를 제한합니다.

![chlimage_1-479](assets/chlimage_1-479.png)

## 중재 작업 {#moderation-actions}

[중재 작업](moderate-ugc.md#moderation-actions) 컨텐츠 영역에서 하나 이상의 선택 항목을 선택하거나 컨텐츠 세부 사항을 볼 때 선택할 수 있습니다.

게시물을 벌크-중재하려면 컨텐츠 영역에서 선택 ( ![선택](assets/selecticon.png))을 클릭하여 게시물을 가리키면 마우스(데스크탑)를 사용하거나 게시물(모바일)에서 손가락을 길게 눌러 나타납니다. 이렇게 하면 다중 선택 모드로 전환되고 이제 을 클릭하기만 하면 후속 게시물이 대량으로 중재될 수 있습니다. 도구 모음에 표시되는 단추를 사용하여 선택한 게시물에 대해 중재 작업을 수행합니다. 모든 작업이 확인 메시지를 표시합니다.

컨텐츠 영역에서 단일 게시물을 중재하려면 마우스(데스크탑)를 사용하여 해당 게시물을 마우스로 가리키거나 게시물(모바일)에서 손가락을 누른 채 게시물에 버튼이 표시되도록 합니다. 단일 컨텐츠 세부 사항으로 작업하는 경우 삭제 작업만 확인을 묻는 메시지를 표시합니다.

### 여러 게시물 중재 {#moderating-multiple-posts}

다음을 클릭하여 벌크 선택 모드로 들어갑니다 `Select` 게시물의 아이콘:

![select-icon](assets/select-icon.png)

벌크 선택 모드를 종료하려면 도구 모음에서 취소 (x) 아이콘을 선택합니다.

여러 게시물에 대해 수행할 수 있는 중재 작업은 다음과 같습니다.

* 거부
* 삭제
* 게시물 닫기/다시 열기

이러한 작업을 허용하는 아이콘은 여러 게시물을 선택한 경우에만 도구 모음에 표시됩니다.

![불순물](assets/bulkmoderate.png)

### 단일 게시물 중재 {#moderating-a-single-post}

단일 선택 모드에서 다음을 수행할 수 있습니다

* 사용자 이름을 선택하여 사용자 세부 사항을 봅니다
* 게시물에 대한 링크를 선택하여 게시물 컨텍스트 내 게시물 보기
* [답글](#reply)
* [허용](#allow)
* [거부](#deny)
* [삭제](#delete)
* [닫기](#close)
* 보기 [중재 내역](#moderation-history)
* [세부 정보 보기](#viewdetails)

중재 작업 아이콘 위에 있는 카드 보기에 있는 것은 게시물의 텍스트이고 아래는 다음 데이터를 나타냅니다

* 에 답글이 있는 경우 그 앞에 답글 수가 옵니다
* 플래그가 지정된 경우
* 가 승인된 경우
* UGC가 게시되었을 때

![단일 문자 모드](assets/singleselectmode.png)

#### 답글 {#reply}

![chlimage_1-480](assets/chlimage_1-480.png)

단일 게시물로 작업할 때 UGC 유형이 응답을 지원하고 응답을 허용하도록 구성된 경우 회신 아이콘이 표시됩니다.

#### 허용 {#allow}

![chlimage_1-481](assets/chlimage_1-481.png)

단일 게시물로 작업하는 경우, 게시물이 플래그가 지정되거나 거부되면 허용 아이콘이 표시됩니다. 플래그가 지정된 경우 [허용]을 선택하면 모든 플래그가 지워집니다.

#### 거부 {#deny}

![chlimage_1-482](assets/chlimage_1-482.png)

다음 **거부** 중재 작업은 중재되는 컨텐츠에만 사용할 수 있으며, 다중 선택 모드를 제외한 중재되지 않은 컨텐츠에는 나타나지 않습니다.

중재되지 않은 컨텐츠는 항상 승인됩니다.

중재된 컨텐츠는 처음에 보류 중 상태로 전환되며 나중에 수정되어 승인되거나 거부될 수 있습니다.

보류 중인 상태를 유지하는 컨텐츠는 보류 중인 상태로 되돌릴 수 없습니다. 승인됨 또는 거부로 표시된 컨텐츠는 언제든지 다른 상태로 변경할 수 있습니다.

#### 삭제 {#delete}

![chlimage_1-483](assets/chlimage_1-483.png)

단일 선택 모드나 벌크 모드에서 항목을 선택하고 삭제할 수 있습니다. 삭제 작업을 수행하면 확인 대화 상자가 표시됩니다. 삭제된 항목은 콘텐츠 영역에서 바로 사라집니다. **UGC가 삭제되면 저장소에서 영구적으로 제거되며 나중에 검색할 수 없습니다.**

#### 닫기 {#close}

![chlimage_1-484](assets/chlimage_1-484.png)

단일 게시물로 작업할 때 UGC 유형이 해당 리소스에 대한 추가적인 게시물을 방지하는 기능을 지원하는 경우 닫기 아이콘이 표시됩니다.

#### 관리 내역 {#moderation-history}

![chlimage_1-485](assets/chlimage_1-485.png)

단일 게시물로 작업할 경우 마우스로 가리키면 중재 내역 아이콘이 표시됩니다. 아이콘을 선택하면 UGC 게시물에 대한 작업 내역이 포함된 창이 표시됩니다.

여러 UGC 게시물의 컨텐츠 영역 표시로 돌아가려면 보기 세부 정보 창의 오른쪽 상단 모서리에서 X 를 선택합니다.

예:

![chlimage_1-486](assets/chlimage_1-486.png)

#### 세부 사항 보기 {#view-detail}

![chlimage_1-487](assets/chlimage_1-487.png)

단일 게시물로 작업하는 경우 세부 사항 모드에서 UGC를 열어 더 많은 세부 사항을 볼 수 있습니다.

이렇게 하려면 게시물 위로 마우스를 가져가면 게시물이 표시됩니다 `View Detail` 아이콘을 클릭하고 선택하여 게시물의 자세한 내용이 포함된 패널을 표시합니다.

여러 UGC 게시물의 컨텐츠 영역 표시로 돌아가려면 보기 세부 정보 창의 오른쪽 상단 모서리에서 X 를 선택합니다.

예:

![chlimage_1-488](assets/chlimage_1-488.png)
