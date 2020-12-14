---
title: 게시된 사이트 경험
seo-title: 게시된 사이트 경험
description: 게시된 사이트 찾아보기
seo-description: 게시된 사이트 찾아보기
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 2%

---


# 게시된 사이트 {#experience-the-published-site} 경험

## 게시 시 {#browse-to-new-site-on-publish} 새 사이트로 이동

새로 만든 커뮤니티 사이트가 게시되었으므로 사이트를 만들 때 표시되는 URL(예: 게시 서버)을 찾습니다.

* 작성자 URL = http://localhost:4502/content/sites/engage/en.html
* 게시 URL = http://localhost:4503/content/sites/engage/en.html

작성자 및 게시에 로그인하는 멤버에 대한 혼동을 최소화하려면 각 인스턴스에 대해 다른 브라우저를 사용하는 것이 좋습니다.

게시된 사이트에 처음 도착할 때 사이트 방문자는 일반적으로 아직 로그인되지 않았으며 익명으로 처리되었습니다.

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## 익명의 사이트 방문자 {#anonymous-site-visitor}

익명의 사이트 방문자는 UI에서 다음을 볼 수 있습니다.

* 사이트의 제목입니다. 시작하기 자습서 소개
* 프로필 링크 없음
* 메시지 링크 없음
* 알림 링크 없음
* 검색 필드
* 로그인 링크
* 브랜드 배너
* 참조 사이트 템플릿에 포함된 구성 요소에 대한 메뉴 링크

다양한 링크를 선택하면 해당 링크가 읽기 전용 모드임을 확인할 수 있습니다.

## JCR {#prevent-anonymous-access-on-jcr}에서 익명 액세스 방지

알려진 제한은 사이트 컨텐츠에 대해 **익명 액세스 허용**&#x200B;이 비활성화되어 있지만 jcr 컨텐츠 및 json을 통해 커뮤니티 사이트 컨텐츠를 익명의 방문자에게 노출합니다. 그러나 이 동작은 해결 방법으로 Sling 제한을 사용하여 제어할 수 있습니다.

jcr 컨텐츠 및 json을 통해 익명의 사용자가 커뮤니티 사이트의 컨텐츠를 액세스로부터 보호하려면 다음 단계를 따르십시오.

1. AEM 작성자 인스턴스에서 https://&lt;호스트>:&lt;포트>/editor.html/content/site/&lt;사이트 이름>.html로 이동합니다.

   >[!NOTE]
   >
   >현지화된 사이트로 이동하지 마십시오.

1. **[!UICONTROL 페이지 속성]**&#x200B;으로 이동합니다.

   ![사이트 인증](assets/site-authentication.png)

1. **[!UICONTROL 고급]** 탭으로 이동합니다.

   ![page-properties](assets/page-properties.png)

1. **[!UICONTROL 인증 요구 사항]**&#x200B;을 활성화합니다.
1. 로그인 페이지의 경로를 추가합니다. 예, `/content/......./GetStarted`.
1. 페이지를 게시합니다.

## 신뢰할 수 있는 커뮤니티 구성원 {#trusted-community-member}

이 경험에서는 [Aaron McDonald](tutorials.md#demo-users)이 [커뮤니티 관리자 및 중재자](create-site.md#roles)의 역할을 할당받았다고 가정합니다. 그렇지 않은 경우 작성 환경으로 돌아가서 [사이트 설정](sites-console.md#modifying-site-properties)을 수정하고 커뮤니티 관리자 및 중재자로 Aaron McDonald를 선택합니다.

오른쪽 상단 모서리에서 `Log in`을 선택하고 사용자 이름 &quot;aaron.mcdonald@mailinator.com&quot; 및 암호 &quot;password&quot;로 로그인합니다. Twitter 또는 Facebook 자격 증명으로 로그인하는 기능을 확인합니다.

![chlimage_1-312](assets/chlimage_1-312.png)

로그인하면 새 메뉴 항목인 `Administration`이(가) 있는데, 이는 멤버가 중재자 역할을 했기 때문입니다. 이제 다양한 링크를 선택하는 것이 더 흥미롭습니다.

![chlimage_1-313](assets/chlimage_1-313.png)

선택한 참조 사이트 템플릿에 달력 함수가 먼저 포함되고, 그 다음에 활동 스트림 함수, 포럼 함수 등이 포함되기 때문에 달력 페이지는 홈 페이지입니다. 이 구조는 [사이트 템플릿](sites.md#edit-site-template) 콘솔에서 또는 작성 환경에서 사이트 속성을 수정할 때 표시됩니다.

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>커뮤니티 구성 요소 및 기능에 대한 자세한 내용은 을 참조하십시오.
>
>* [커뮤니티 구성 요소](author-communities.md) (작성자용)
>* [구성 요소, 기능 및 Feature Essentials](essentials.md) (개발자용)

>



## 포럼 링크 {#forum-link}

포럼 링크를 선택하여 기본 포럼 기능을 봅니다.

구성원은 새 주제를 게시하거나 항목을 따를 수 있습니다.

사이트 방문자는 게시물을 보고 다양한 방법으로 정렬할 수 있습니다.

![chlimage_1-315](assets/chlimage_1-315.png)

## 그룹 링크 {#groups-link}

Aaron은 그룹 관리이므로 그룹 링크를 선택하면 Aaron이 그룹 템플릿, 이미지, 해당 그룹이 열려 있는지 아니면 비밀인지를 선택하고 구성원을 초대함으로써 새 커뮤니티 그룹을 만들 수 있습니다.

게시 환경에서 그룹이 생성되는 예입니다.

작성 환경에서도 그룹을 만들고 작성 환경의 커뮤니티 사이트 내에서 관리할 수 있습니다([커뮤니티 그룹 콘솔](groups.md)). 이 튜토리얼에서는 [작성자](nested-groups.md)에 그룹을 만드는 경험이 그 다음에 있습니다.

![chlimage_1-316](assets/chlimage_1-316.png)

참조 그룹 만들기:

1. **[!UICONTROL 새 그룹]**&#x200B;을 선택합니다.
1. **[!UICONTROL 설정 탭]**
   * 그룹 이름: `Sports`
   * 설명: `A parent group for various sporting groups`
   * 그룹 URL 이름: `sports`
   * `Open Group` 선택(모든 커뮤니티 구성원이 참여하도록 허용)
1. **[!UICONTROL 템플릿 탭]**
   * `Reference Group` 선택(중첩된 그룹을 허용하기 위해 해당 구조에 그룹 함수가 들어 있음)
1. **[!UICONTROL 그룹 만들기]**&#x200B;를 선택합니다.

![chlimage_1-317](assets/chlimage_1-317.png)

새 그룹이 만들어지면, **새 스포츠 그룹**&#x200B;을 선택하여 이 그룹 내에 두 개의 그룹(중첩된)을 만듭니다. 사이트 구조는 그룹 함수로 시작할 수 없으므로 스포츠 그룹을 연 후에는 그룹 링크를 선택해야 합니다.

![chlimage_1-318](assets/chlimage_1-318.png)

`Blog`으로 시작하는 두 번째 링크 집합은 현재 선택된 그룹인 `Sports`그룹에 속합니다. Sports&#39; `Groups` 링크를 선택하면 두 그룹을 Sports 그룹 내에 중첩할 수 있습니다.

예를 들어 `ew groups.`에 두 개를 추가합니다.

* 이름 `Baseball`
   * `Open Group`(필수 멤버십)으로 설정된 상태로 둡니다.
   * 템플릿 탭에서 `Conversational Group`
* 이름 `Gymnastics`
   * 설정을 `Member Only Group`(제한된 멤버십)으로 변경
   * 템플릿 탭에서 `Conversational Group`

**알림**:

* 두 그룹이 모두 표시되기 전에 페이지를 새로 고쳐야 할 수 있습니다.
* 이 템플릿에는 그룹 기능이 포함되어 있지 *않으므로 그룹을 더 이상 중첩할 수 없습니다.
* 작성자의 경우 [그룹 콘솔](groups.md)은(는) `Public Group`(옵션 멤버십)의 세 번째 선택 사항을 제공합니다.

두 그룹이 모두 만들어지면, 야구 그룹과 열린 그룹을 선택하고 해당 링크를 확인합니다.`Discussions` `What's New` `Members`
그룹의 링크는 기본 사이트의 링크 아래에 표시되고, 그 결과는 다음과 같습니다.

![chlimage_1-319](assets/chlimage_1-319.png)

작성자 - 관리 권한이 있는 경우 [커뮤니티 그룹 콘솔](members.md)로 이동하고 Weston McCall을 `Community Engage Gymnastics <uid> Members` 그룹에 추가합니다.

계속 게시하고 Aaron McDonald로 로그아웃하고 스포츠 그룹의 그룹을 익명의 사이트 방문자로 봅니다.

* 홈 페이지에서
* `Groups`링크 선택
* `Sports`링크 선택
* 스포츠&#39; `Groups`링크를 선택합니다.

야구 그룹만 표시됩니다.

Weston McCall(weston.mccall@dodgit.com / 암호)로 로그인하고 동일한 위치로 이동합니다. Weston은 `Join` 열린 `Baseball` 그룹과 `enter or Leave` 비공개 `Gymnastics` 그룹을 만들 수 있습니다.

![chlimage_1-320](assets/chlimage_1-320.png)

## 웹 페이지 링크 {#web-page-link}

웹 페이지 링크를 선택하여 사이트에 포함된 기본 웹 페이지를 봅니다. 표준 AEM 작성 도구를 사용하여 작성 환경에서 이 페이지에 컨텐츠를 추가할 수 있습니다.

예를 들어 **작성자** 인스턴스로 이동하여 [커뮤니티 사이트 콘솔](sites-console.md)에서 `engage` 폴더를 열고 **사이트 열기** 아이콘을 선택하여 작성 편집 모드로 전환합니다. 그런 다음 미리 보기 모드를 선택하여 `Web Page` 링크를 선택한 다음 편집 모드를 선택하여 제목 및 텍스트 구성 요소를 추가합니다. 마지막으로, 페이지나 전체 사이트를 다시 게시합니다.

![chlimage_1-321](assets/chlimage_1-321.png)

## 관리 링크 {#administration-link}

커뮤니티 구성원에게 중재 권한이 있는 경우 관리 링크가 표시되고 이 링크를 선택하면 게시된 커뮤니티 컨텐츠가 표시되고 작성 환경의 [중재 콘솔](moderation.md)과 유사한 방식으로 [중재된](moderate-ugc.md)이(가) 되도록 허용할 수 있습니다.

브라우저의 뒤로 단추를 사용하여 게시된 사이트로 돌아갑니다. 대부분의 콘솔은 게시 환경의 전역 탐색에서 액세스할 수 없습니다.

![chlimage_1-322](assets/chlimage_1-322.png)

## 자체 등록 {#self-registration}

로그아웃한 후 새 사용자 등록을 만들 수 있습니다.

* 선택 `Log In`
* 선택 `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

기본적으로 이메일 주소는 로그인 ID입니다. 이 확인란을 선택하지 않으면 방문자가 자신의 로그인 ID(사용자 이름)를 입력할 수 있습니다. 사용자 이름은 게시 환경에서 고유해야 합니다.

사용자의 이름, 이메일 및 암호를 지정한 후 `Sign Up`을 선택하면 사용자가 만들어지고 사용자가 서명할 수 있게 됩니다.

로그인하면 표시된 첫 번째 페이지가 자신의 `Profile`페이지이며, 이를 통해 개인화할 수 있습니다.

![chlimage_1-325](assets/chlimage_1-325.png)

회원이 로그인 ID를 잊은 경우 이메일 주소를 사용하여 복구할 수 있습니다.

![chlimage_1-326](assets/chlimage_1-326.png)
