---
title: 메시징 기능
seo-title: Messaging Feature
description: 메시징 구성 요소 구성
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 2%

---

# 메시징 기능 {#messaging-feature}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

포럼 및 주석에서 발생하는 공개되는 상호 작용 외에도 AEM Communities의 메시징 기능을 사용하면 커뮤니티 멤버가 보다 비공개로 상호 작용할 수 있습니다.

이 기능은 [커뮤니티 사이트](overview.md#communitiessites) 가 만들어집니다.

메시징 기능은 다음과 같은 기능을 제공합니다.

* 하나 이상의 커뮤니티 구성원에게 메시지 보내기
* 커뮤니티 구성원 그룹에 메시지 보내기
* 첨부 파일이 있는 메시지 보내기
* 메시지 전달
* 메시지에 회신
* 메시지 삭제
* 삭제된 메시지 복원

메시징 기능을 활성화하고 수정하려면 다음을 참조하십시오.

* [메시징 구성](messaging.md) 관리자용
* [메시징 핵심 사항](essentials-messaging.md) 개발자용

>[!NOTE]
>
>추가는 지원되지 않습니다 `Compose Message, Message, or Message List` 구성 요소(에 있음) `Communities`구성 요소 그룹)을 작성자 편집 모드의 페이지에 그룹화합니다.

## 메시징 구성 요소 구성 {#configuring-messaging-components}

커뮤니티 사이트에 대해 메시징이 활성화되면 추가 구성 없이 완전히 설정됩니다. 이 정보는 기본 구성을 변경해야 하는 경우 제공됩니다.

### 메시지 목록 구성(메시지 상자) {#configuring-message-list-messagebox}

메시지 목록 구성을 수정하려면 **받은 편지함**, **보낸 항목**, 및 **휴지통** 메시징 기능 페이지에서 다음 위치에서 사이트를 엽니다. [편집 모드 작성](sites-console.md#authoring-site-content).

in `Preview` 모드를 선택하고 **[!UICONTROL 메시지]** 링크를 클릭하여 기본 메시징 페이지를 엽니다. 그런 다음 **[!UICONTROL 받은 편지함, 보낸 항목 또는 휴지통]** 를 입력하여 해당 메시지 목록에 대한 구성 요소를 구성할 수 있습니다.

in `Edit` 모드 페이지에서 구성 요소를 선택합니다.

구성 대화 상자에 액세스하려면 을(를) 선택하여 상속을 취소해야 합니다. `link`아이콘.

구성이 완료되면 을(를) 선택하여 상속을 복원해야 합니다. `broken link` 아이콘.

![chlimage_1-396](assets/chlimage_1-396.png)

상속이 취소되면 상속을 선택할 수 있습니다 `configure` 아이콘을 클릭하여 구성 대화 상자를 엽니다.

![chlimage_1-397](assets/chlimage_1-397.png)

#### 기본 탭 {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL 서비스 선택기]**
(*필수 여부*) 속성 값으로 설정합니다 `serviceSelector.name` 에서 [AEM Communities 메시징 작업 서비스](messaging.md#messaging-operations-service).

* **[!UICONTROL 작성 페이지]**
(*필수 여부*) 구성원이 를 클릭할 때 열 페이지입니다 `Reply` 버튼을 클릭합니다. 대상 페이지에는 가 포함되어야 합니다 **[!UICONTROL 메시지 작성]** 양식.

* **[!UICONTROL 리소스로 회신/보기]**
이 확인란을 선택하면 회신 URL 및 보기 URL이 리소스를 참조하고, 그렇지 않은 데이터는 URL에서 쿼리 매개 변수로 전달됩니다.

* **[!UICONTROL 프로필 표시 양식]**
보낸 사람 프로필을 표시하는 데 사용할 프로필 양식입니다.

* **[!UICONTROL 휴지통 폴더]**
이 옵션을 선택하면 이 메시지 목록 구성 요소는 삭제됨으로 플래그가 지정된 메시지(휴지통)만 표시합니다.

* **[!UICONTROL 폴더 경로]**
(*필수 여부*) `inbox.path.name` 및 `sentitems.path.name` 에서 [AEM Communities 메시징 작업 서비스](messaging.md#messaging-operations-service). 을 구성할 때 `Inbox`를 채울 때 다음 값을 사용하여 항목을 하나 추가합니다 `inbox.path.name`. 을 구성할 때 `Outbox`를 채울 때 다음 값을 사용하여 항목을 하나 추가합니다 `sentitems.path.name`. 을 구성할 때 `Trash`두 값을 모두 사용하여 두 항목을 추가합니다.

#### 표시 탭 {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL 읽기 단추 표시]**
이 옵션을 선택하면 
`Read`메시지를 읽음으로 표시할 수 있는 단추입니다.

* **[!UICONTROL 읽지 않은 상태로 표시 단추]**
이 옵션을 선택하면 
`Mark Unread` 메시지를 읽음으로 표시할 수 있는 단추입니다.

* **[!UICONTROL 삭제 단추]**
이 옵션을 선택하면 
`Delete`메시지를 읽음으로 표시할 수 있는 단추입니다. 다음의 경우 삭제 기능을 복제합니다 **`Message Options`** 도 선택되어 있습니다.

* **[!UICONTROL 메시지 옵션]**
선택된 경우 이 표시됩니다 
**`Reply`**, **`Reply All`**, **`Forward`** 및 **`Delete`** 메시지를 다시 전송하거나 삭제할 수 있는 단추입니다. 다음의 경우 삭제 기능을 복제합니다 **`Delete Button`** 도 선택되어 있습니다.

* **[!UICONTROL 페이지당 메시지 수]**
지정된 수는 페이지 매김 구성표에 페이지당 표시되는 최대 메시지 수입니다. 번호를 지정하지 않은 경우(비워 두면) 모든 메시지가 표시되고 페이지 매김이 없습니다.

* **[!UICONTROL 타임스탬프 패턴]**
하나 이상의 언어에 대한 타임스탬프 패턴을 제공합니다. 기본값은 en, de, fr, es, ja, zh_CN, ko_KR입니다.

* **[!UICONTROL 사용자 표시]**
다음 중 하나를 선택합니다 
**`Sender`** 또는 **`Recipients`** 을 입력하여 보낸 사람 또는 받는 사람을 표시할지 여부를 결정합니다.

### 작성 메시지 구성 {#configuring-compose-message}

메시지 작성 페이지의 구성을 수정하려면 [편집 모드 작성](sites-console.md#authoring-site-content).

in `Preview`모드를 선택하고 **[!UICONTROL 메시지]** 링크를 클릭하여 기본 메시징 페이지를 엽니다. 그런 다음 새 메시지 단추를 선택하여 `Compose Message` 페이지..

in `Edit` 모드에서 메시지 본문을 포함하는 페이지에서 기본 구성 요소를 선택합니다.

구성 대화 상자에 액세스하려면 을(를) 선택하여 상속을 취소해야 합니다. `link`아이콘.

구성이 완료되면 을(를) 선택하여 상속을 복원해야 합니다. `broken link` 아이콘.

![chlimage_1-400](assets/chlimage_1-400.png)

상속이 취소되면 상속을 선택할 수 있습니다 `configure` 아이콘을 클릭하여 구성 대화 상자를 엽니다.

![chlimage_1-401](assets/chlimage_1-401.png)

#### 기본 탭 {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL 리디렉션 URL]**
메시지를 보낸 후 표시되는 페이지의 URL을 입력합니다. 예를 들어 
`../messaging.html`.

* **[!UICONTROL URL 취소]**
보낸 사람이 메시지를 취소할 경우 표시되는 페이지의 URL을 입력합니다. 예를 들어 
`../messaging.html`.

* **[!UICONTROL 메시지 주체의 최대 길이]**
제목 필드에 허용되는 최대 문자 수입니다. 예를 들면 500입니다. 기본값은 제한이 없습니다.

* **[!UICONTROL 메시지 본문의 최대 길이]**
컨텐츠 필드에 허용되는 최대 문자 수입니다. 예: 10000. 기본값은 제한이 없습니다.

* **[!UICONTROL 서비스 선택기]**
(*필수 여부*) 속성 값으로 설정합니다 **`serviceSelector.name`** 에서 [AEM Communities 메시징 작업 서비스](messaging.md#messaging-operations-service).

#### 표시 탭 {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL 제목 필드 표시]**
이 옵션을 선택하면 
`Subject` 필드를 설정하고 메시지에 제목을 추가할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 제목 레이블]**
옆에 표시할 텍스트를 입력합니다. 
`Subject` 필드. 기본값은 입니다. `Subject`.

* **[!UICONTROL 파일 첨부 필드 표시]**
이 옵션을 선택하면 
`Attachment` 필드를 작성하고 메시지에 첨부 파일을 추가할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 파일 레이블 첨부]**
옆에 표시할 텍스트를 입력합니다. 
`Attachment` 필드. 기본값은 입니다. **`Attach File`**.

* **[!UICONTROL 컨텐츠 필드 표시]**
이 옵션을 선택하면 
`Content` 필드를 설정하고 메시지 본문을 추가할 수 있습니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 컨텐츠 레이블]**
옆에 표시할 텍스트를 입력합니다. 
`Content` 필드. 기본값은 입니다. **`Body`**.

* **[!UICONTROL 리치 텍스트 편집기 사용]**
이 확인란을 선택하면 자체 리치 텍스트 편집기가 있는 사용자 지정 컨텐츠 텍스트 상자의 사용을 나타냅니다. 기본값은 선택되어 있지 않습니다.

* **[!UICONTROL 타임스탬프 패턴]**
하나 이상의 언어에 대한 타임스탬프 패턴을 제공합니다. 기본값은 en, de, fr, es, ja, zh_CN, ko_KR입니다.
