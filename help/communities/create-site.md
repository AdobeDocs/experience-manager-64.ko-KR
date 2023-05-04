---
title: 새 커뮤니티 사이트 작성
seo-title: Author a New Community Site
description: 새 AEM Communities 사이트를 작성하는 방법
seo-description: How to author a new AEM Communities site
uuid: b8557416-cae4-489e-ab3b-e94d56686b7a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: bf182bb7-e305-45be-aadb-d71efd70f8cb
exl-id: 5d58f9c5-3210-48ef-94a3-805a1a57e3af
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 2%

---

# 새 커뮤니티 사이트 작성 {#author-a-new-community-site}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 새 커뮤니티 사이트 만들기 {#create-a-new-community-site}

작성자 인스턴스를 사용하여 새 커뮤니티 사이트 만들기

* 관리자 권한으로 로그인
* 전역 탐색에서: **[!UICONTROL 탐색 > 커뮤니티 > 사이트]**

커뮤니티 사이트 콘솔은 커뮤니티 사이트를 만드는 단계를 안내하는 마법사를 제공합니다. 앞으로 이동할 수 있습니다 `Next`단계 또는 `Back`를 클릭하여 마지막 단계에서 사이트를 커밋하기 전에 이전 단계로 이동합니다.

새 커뮤니티 사이트 만들기를 시작하려면 다음을 수행하십시오.

* 을(를) 선택합니다 `Create` 버튼

![createcommunitysite](assets/createcommunitysite.png)

### 1단계: 사이트 템플릿 {#step-site-template}

![createsitetemplate63](assets/createsitetemplate63.png)

설정 [사이트 템플릿 단계](sites-console.md#step2013asitetemplate), 제목, 설명, URL의 이름을 입력하고 커뮤니티 사이트 템플릿을 선택합니다. 예를 들면 다음과 같습니다.

* **[!UICONTROL 커뮤니티 사이트 제목]**: `Getting Started Tutorial`

* **[!UICONTROL 커뮤니티 사이트 설명]**: `A site for engaging with the community.`

* **[!UICONTROL 커뮤니티 사이트 루트]**: 기본 루트에 대해 비워 둡니다. `/content/sites`)

* **[!UICONTROL 클라우드 구성]**: (클라우드 구성이 지정되지 않은 경우 비워 둡니다.) 지정된 클라우드 구성에 경로를 제공합니다.
* **[!UICONTROL 커뮤니티 사이트 기본 언어]**: (단일 언어에 대해 그대로 유지) 영어) 풀다운 메뉴를 사용하여 하나를 선택합니다 *이상* 사용 가능한 언어의 기본 언어(독일어, 이탈리아어, 프랑스어, 일본어, 스페인어, 포르투갈어(브라질), 중국어(번체) 및 중국어(간체)입니다. 추가된 각 언어에 대해 하나의 커뮤니티 사이트가 만들어지고 다음에 설명된 우수 사례 후 동일한 사이트 폴더 내에 있게 됩니다 [다국어 사이트의 컨텐츠 번역](../../help/sites-administering/translation.md). 각 사이트의 루트 페이지에는 선택한 언어 중 하나의 언어 코드로 이름이 지정된 하위 페이지가 포함됩니다(예: 영어의 경우 &#39;en&#39;, 프랑스어의 경우 &#39;fr&#39;).

* **[!UICONTROL 커뮤니티 사이트 이름]**: 참여

   * 사이트를 만든 후 쉽게 변경되지 않으므로 이름을 다시 확인하십시오
   * 초기 URL이 커뮤니티 사이트 이름 아래에 표시됩니다
   * 올바른 URL의 경우 기본 언어 코드 + &quot;.html&quot;을 추가합니다
   * *예*, http://localhost:4502/content/sites/ `engage/en.html`

* **[!UICONTROL 템플릿]**: 선택하려면 아래로 이동하십시오. `Reference Site`

**[!UICONTROL 다음]**&#x200B;을 선택합니다

### 2단계: 디자인 {#step-design}

디자인 단계는 테마 및 브랜딩 배너를 선택하는 두 개의 섹션에 나와 있습니다.

#### 커뮤니티 사이트 테마 {#community-site-theme}

템플릿에 적용할 원하는 스타일을 선택합니다. 선택한 경우 테마에 확인 표시가 오버레이됩니다.

![사이트테마](assets/sitetheme.png)

#### 커뮤니티 사이트 브랜딩 {#community-site-branding}

(선택 사항) 사이트 페이지에 표시할 배너 이미지를 업로드합니다. 배너는 커뮤니티 사이트 헤더와 메뉴(탐색 링크) 사이에서 브라우저의 왼쪽 가장자리에 고정됩니다. 배너 높이는 120픽셀로 잘립니다. 브라우저의 너비와 120픽셀 높이에 맞게 배너의 크기를 조정할 수 없습니다.

![chlimage_1-353](assets/chlimage_1-353.png) ![chlimage_1-354](assets/chlimage_1-354.png)

**[!UICONTROL 다음]**&#x200B;을 선택합니다.

### 3단계: 설정 {#step-settings}

설정 단계에서 선택하기 전에 `Next`에는 사용자 관리, 태깅, 조정, 그룹 관리, analytics, 번역 및 활성화와 관련된 구성에 대한 액세스를 제공하는 7개의 섹션이 있습니다.

다음 방문 [AEM Communities for Enablement 시작하기](getting-started-enablement.md) 사용 기능 작업을 경험하는 자습서.

#### 사용자 관리 {#user-management}

의 모든 확인란을 선택합니다. [사용자 관리](sites-console.md#user-management)

* 사이트 방문자가 자체 등록하도록 허용하려면
* 사이트 방문자가 로그인하지 않고 사이트를 볼 수 있도록 하려면 다음을 수행하십시오
* 구성원이 다른 커뮤니티 구성원의 메시지를 보내고 받을 수 있도록 허용
* 프로필 등록 및 생성 대신 Facebook으로 로그인 허용
* 프로필을 등록하고 만드는 대신 Twitter으로 로그인을 허용하려면

>[!NOTE]
>
>프로덕션 환경의 경우 사용자 지정 Facebook 및 Twitter 애플리케이션을 만들어야 합니다. 자세한 내용은 [facebook 및 Twitter을 사용하여 소셜 로그인](social-login.md).

![createsettings](assets/createsitesettings.png)

#### 태깅 {#tagging}

커뮤니티 컨텐츠에 적용할 수 있는 태그는 [태깅 콘솔](../../help/sites-administering/tags.md#tagging-console) (예: [튜토리얼 네임스페이스](setup.md#create-tutorial-tags)).

자동 완성 검색을 사용하면 네임스페이스를 쉽게 찾을 수 있습니다. 예를 들어

* &#39;tut&#39;을 입력합니다.
* 선택 `Tutorial`

![chlimage_1-355](assets/chlimage_1-355.png)

#### 역할 {#roles}

[커뮤니티 구성원 역할](users.md) 역할 섹션의 설정을 통해 할당됩니다.

커뮤니티 구성원(또는 구성원 그룹)이 사이트를 커뮤니티 관리자로 경험하도록 하려면 자동 완성 검색을 사용하고 드롭다운의 옵션에서 구성원 또는 그룹 이름을 선택합니다.

예를 들어

* &quot;q&quot;를 입력합니다.
* 선택 [퀸 하퍼](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[터널 서비스](https://helpx.adobe.com/experience-manager/6-3/communities/using/deploy-communities.html#tunnel-service-on-author) 게시 환경에만 있는 구성원 및 그룹을 선택할 수 있습니다.

![community_roles-1](assets/community_roles-1.png)

#### 중재 {#moderation}

에 대한 기본 전역 설정을 적용합니다. [중재](sites-console.md#moderation) UGC(사용자 생성 콘텐츠).

![chlimage_1-356](assets/chlimage_1-356.png)

#### ANALYTICS {#analytics}

Adobe Analytics 라이센스가 있고 Analytics 클라우드 서비스 및 프레임워크가 구성된 경우 Analytics를 활성화하고 프레임워크를 선택할 수 있습니다.

자세한 내용은 [커뮤니티 기능에 대한 Analytics 구성](analytics.md).

![chlimage_1-357](assets/chlimage_1-357.png)

#### 번역 {#translation}

다음 [번역 설정](sites-console.md#translation) UGC를 번역할지 여부 및 번역할지 여부(있는 경우)와 사이트의 기본 언어를 지정합니다.

* 확인 **[!UICONTROL 기계 번역 허용]**
* 기본 기계 번역 서비스에서 번역용으로 선택한 기본 언어를 그대로 둡니다
* 기본 번역 공급자 및 구성 남기기
* 언어 사본이 없기 때문에 글로벌 스토어를 할 필요가 없습니다
* 선택 **[!UICONTROL 전체 페이지 번역]**
* 기본 지속성 선택 사항을 그대로 둡니다.

![chlimage_1-358](assets/chlimage_1-358.png)

#### 활성화 {#enablement}

참여 커뮤니티를 만들 때는 비워 둡니다.

를 빠르게 만들기 위한 유사한 자습서의 경우 [지원 커뮤니티](overview.md#enablement-community)를 참조하십시오. [AEM Communities for Enablement 시작하기](getting-started-enablement.md).

**[!UICONTROL 다음]**&#x200B;을 선택합니다.

### 4단계: 커뮤니티 사이트 만들기 {#step-create-communities-site}

**[!UICONTROL 만들기]**&#x200B;를 선택합니다.

![chlimage_1-359](assets/chlimage_1-359.png)

프로세스가 완료되면 새 사이트의 폴더가 커뮤니티 - 사이트 콘솔에 표시됩니다.

![communityEssitesconsole](assets/communitiessitesconsole.png)

## 새 커뮤니티 사이트 게시 {#publish-the-new-community-site}

만들어진 사이트는 새 사이트를 만들 수 있는 동일한 콘솔인 Communities - Sites 콘솔에서 관리해야 합니다.

커뮤니티 사이트의 폴더를 선택하여 연 후에는 다음 네 개의 작업 아이콘이 표시되도록 사이트 아이콘을 마우스로 가리킵니다.

![siteactionicons-1](assets/siteactionicons-1.png)

네 번째 줄임표 아이콘(추가 작업)을 선택할 때 사이트 내보내기 및 사이트 삭제 옵션이 표시됩니다.

![siteactionsnew-1](assets/siteactionsnew-1.png)

왼쪽부터 오른쪽까지입니다.

* **사이트 열기**
연필 아이콘을 선택하여 작성 편집 모드에서 커뮤니티 사이트를 열고 페이지 구성 요소를 추가 및/또는 구성합니다

* **사이트 편집**
속성 아이콘을 선택하여 제목과 같은 속성을 수정할 커뮤니티 사이트를 열거나 테마를 변경할 수 있습니다

* **사이트 게시**
커뮤니티 사이트를 게시하려면 월드 아이콘을 선택합니다(예를 들어 게시 서버가 로컬 컴퓨터에서 실행 중인 경우 기본적으로 localhost:4503으로 게시).

* **사이트 내보내기**
내보내기 아이콘을 선택하여 두 사이트에 모두 저장된 커뮤니티 사이트의 패키지를 만듭니다 [패키지 관리자](../../help/sites-administering/package-manager.md) 다운로드.

   UGC는 사이트 패키지에 포함되어 있지 않습니다.

* **사이트 삭제**

   내에서 커뮤니티 사이트를 삭제하려면 삭제 아이콘을 선택합니다 **[!UICONTROL 커뮤니티 > 사이트 콘솔]**. 이 작업은 UGC, 사용자 그룹, 자산 및 데이터베이스 레코드와 같은 사이트와 연관된 모든 항목을 제거합니다.

![siteactions-1](assets/siteactions-1.png)

>[!NOTE]
>
>게시 인스턴스에 기본 포트 4503을 사용하지 않는 경우 기본 복제 에이전트를 편집하여 포트 번호를 올바른 값으로 설정합니다.
>
>작성자 인스턴스의 주 메뉴에서
>
>1. 다음으로 이동 **[!UICONTROL 도구 > 작업 > 복제]** 메뉴
>1. 선택 **[!UICONTROL 작성자의 에이전트]**
>1. 선택 **[!UICONTROL 기본 에이전트(게시)]**
>1. 다음 **[!UICONTROL 설정]** 선택 **[!UICONTROL 편집]**
>1. 에이전트 설정에 대한 팝업 대화 상자에서 전송 탭을 선택합니다
>1. URI에서 포트 번호 4503을 원하는 포트 번호로 변경합니다

>
>예를 들어 포트 6103을 사용하려면 `http://localhost:6103/bin/receive?sling:authRequestLogin=1`
>
>1. 선택 **[!UICONTROL 확인]**
>1. (선택 사항) 선택 `Clear` 또는 `Force Retry` 복제 큐를 재설정하려면


### 게시 선택 {#select-publish}

게시 서버가 실행 중인지 확인한 후 전역 아이콘을 선택하여 커뮤니티 사이트를 게시합니다.

![chlimage_1-360](assets/chlimage_1-360.png)

커뮤니티 사이트가 성공적으로 게시되면 다음과 같은 메시지가 짧게 나타납니다.

![chlimage_1-361](assets/chlimage_1-361.png)

### 새 커뮤니티 사용자 그룹에 알림 {#notice-new-community-user-groups}

새 커뮤니티 사이트와 함께 다양한 관리 기능에 적절한 권한이 설정된 새 사용자 그룹이 생성됩니다. 자세한 내용은 [커뮤니티 사이트에 대한 사용자 그룹](users.md#usergroupsforcommunitysites).

이 새 커뮤니티 사이트의 경우 1단계에서 사이트 이름이 &quot;engage&quot;인 경우 4개의 새 사용자 그룹이 [그룹 콘솔](members.md) (전역 탐색: 커뮤니티, 그룹):

* Community Engage Compmunitymanager
* 커뮤니티 참여 그룹 관리자
* 커뮤니티 참여 구성원
* 커뮤니티 참여 중재자
* 커뮤니티 참여 권한 있는 구성원
* 커뮤니티 참여 Siteontentmanager

주의 사항 [아론 맥도날드](tutorials.md#demo-users) 의 구성원임

* Community Engage Compmunitymanager
* 커뮤니티 참여 중재자
* 커뮤니티 참여 구성원(간접적으로 중재자 그룹의 구성원으로서)

![chlimage_1-362](assets/chlimage_1-362.png)

#### http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-363](assets/chlimage_1-363.png)

## 인증 오류에 대한 구성 {#configure-for-authentication-error}

사이트가 구성되고 게시로 푸시되면, [로그인 매핑 구성](sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) 내의 아무 곳에나 삽입할 수 있습니다. 로그인 자격 증명을 올바르게 입력하지 않으면 인증 오류가 커뮤니티 사이트의 로그인 페이지를 오류 메시지와 함께 다시 표시하는 이점이 있습니다.

추가 `Login Page Mapping` 로서의

* /content/sites/engage/en/signin:/content/sites/engage/en

## 옵션 단계 {#optional-steps}

### 기본 홈 페이지 변경 {#change-the-default-home-page}

데모용으로 게시 사이트를 사용할 때 기본 홈 페이지를 새 사이트로 변경하는 것이 유용할 수 있습니다.

이렇게 하려면 을 사용해야 합니다. [CRXDE](http://localhost:4503/crx/de) Lite를 사용하여 [리소스 매핑](../../help/sites-deploying/resource-mapping.md) 게시할 표.

시작하려면 다음을 수행하십시오.

1. 게시 시 관리자 권한으로 로그인합니다
1. 찾아보기 [http://localhost:4503/crx/de](http://localhost:4503/crx/de)
1. 프로젝트 브라우저에서 `/etc/map`
1. 을(를) 선택합니다 `http` 노드

   * 선택 **[!UICONTROL 노드 만들기]**

      * **이름** localhost.4503

         (do) *not* 사용 `:`)

      * **유형** [sling:Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. 새로 만든 `localhost.4503` 노드 선택

   * 속성 추가

      * **이름** sling:match
      * **유형** 문자열
      * **값** localhost.4503/\$

         ( &#39;$&#39; 문자로 끝나야 함)
   * 속성 추가

      * **이름** sling:internalRedirect
      * **유형** 문자열
      * **값** /content/sites/engage/en.html


1. 선택 **[!UICONTROL 모두 저장]**
1. (선택 사항) 검색 기록을 삭제합니다
1. http://localhost:4503/ 로 이동합니다.

   * http://localhost:4503/content/sites/engage/en.html에 도착합니다.

>[!NOTE]
>
>비활성화하려면 을(를) `sling:match` &#39;x&#39;가 있는 속성 값 - `xlocalhost.4503/$` - 및 **[!UICONTROL 모두 저장]**.

![chlimage_1-364](assets/chlimage_1-364.png)

#### 문제 해결: 맵을 저장하는 동안 오류가 발생했습니다. {#troubleshooting-error-saving-map}

변경 사항을 저장할 수 없는 경우 노드 이름이 `localhost.4503`, &#39;점&#39; 구분 기호 사용, 그리고 아님 `localhost:4503` &#39;콜론&#39; 구분 기호 사용, `localhost`는 올바른 네임스페이스 접두사가 아닙니다.

![chlimage_1-365](assets/chlimage_1-365.png)

#### 문제 해결: 리디렉션 실패 {#troubleshooting-fail-to-redirect}

&#39;**$**&#39;(정규 표현식 끝) `sling:match`문자열은 매우 중요하므로 `http://localhost:4503/` 가 매핑되면 리디렉션 값이 URL의 server:port 뒤에 있을 수 있는 모든 경로에 추가됩니다. 따라서 AEM에서 로그인 페이지로 리디렉션하려고 하면 실패합니다.

### 사이트 수정 {#modify-the-site}

사이트가 처음 만들어지면 작성자가 [사이트 열기 아이콘](sites-console.md#authoring-site-content) 표준 AEM 작성 활동을 수행하려면 다음을 수행하십시오.

또한 관리자는 [사이트 편집 아이콘](sites-console.md#modifying-site-properties) 제목 등 사이트의 속성을 수정하려면

수정 후 다음 사항을 기억하십시오 **저장** 및 **다시 게시** 사이트입니다.

>[!NOTE]
>
>AEM에 익숙하지 않은 경우 다음 문서를 참조하십시오. [기본 처리](../../help/sites-authoring/basic-handling.md) 그리고 [페이지 작성에 대한 빠른 안내](../../help/sites-authoring/qg-page-authoring.md).
