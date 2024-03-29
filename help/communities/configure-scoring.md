---
title: 점수 책정 및 배지 핵심 사항
seo-title: Scoring and Badges Essentials
description: 점수 및 배지 기능 개요
seo-description: Scoring and Badges feature overview
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
exl-id: 84aa46d5-4ca4-4f6e-b0b9-fc9907be00a5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 2%

---

# 점수 책정 및 배지 핵심 사항 {#scoring-and-badges-essentials}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Communities 점수 및 배지 기능은 커뮤니티 구성원을 식별하고 포상하는 기능을 제공합니다.

기능 설정에 대한 자세한 내용은

* [커뮤니티 점수 및 배지](implementing-scoring.md)

이 페이지에는 추가적인 기술 세부 정보가 포함되어 있습니다.

* 방법 [배지 표시](#displaying-badges) 이미지 또는 텍스트
* 광범위한 기능 사용 방법 [디버그 로깅](#debug-log-for-scoring-and-badging)
* 방법 [UGC 액세스](#ugc-for-scoring-and-badging) 점수 및 배지 관련

>[!CAUTION]
>
>CRXDE Lite에 표시되는 구현 구조는 변경될 수 있습니다.

## 배지 표시 {#displaying-badges}

배지가 텍스트로 표시되는지 아니면 이미지가 HBS 템플릿의 클라이언트 측에서 제어되는지 여부를 나타냅니다.

예를 들어 `this.isAssigned` in `/libs/social/forum/components/hbs/topic/list-item.hbs`,:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

true인 경우 isAssigned 는 역할에 대해 배지가 할당되었음을 나타내고 배지는 텍스트로 표시되어야 합니다.

false인 경우, 할당됨은 획득한 배지가 이미지로 표시되어야 함을 나타냅니다.

이 동작에 대한 모든 변경 사항은 사용자 지정된 스크립트(재정의 또는 오버레이)로 수행해야 합니다. 자세한 내용은 [클라이언트측 사용자 지정](client-customize.md).

## 점수 및 배지 디버그 로그 {#debug-log-for-scoring-and-badging}

점수부여 및 배지 디버깅에 도움이 되도록 사용자 지정 로그 파일을 설정할 수 있습니다. 이 기능에 문제가 발생하는 경우 이 로그 파일의 내용을 고객 지원에 제공할 수 있습니다.

자세한 지침은 [사용자 지정 로그 파일 만들기](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

슬링로그 파일을 빠르게 설정하려면 다음을 수행합니다.

1. 액세스 권한 **[!UICONTROL Adobe Experience Manager 웹 콘솔 로그 지원]**, 예

   * http://localhost:4502/system/console/slinglog

1. 선택 **[!UICONTROL 새 로거 추가]**

   1. 선택 `DEBUG` 대상 **[!UICONTROL 로그 수준]**
   1. 이름 입력 **[!UICONTROL 로그 파일]**, 예

      * logs/scoring-debug.log
   1. 두 개 입력 **[!UICONTROL 로거]** (클래스) 항목(사용) `+` 아이콘)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. **[!UICONTROL 저장]**&#x200B;을 선택합니다



![chlimage_1-248](assets/chlimage_1-248.png)

로그 항목을 보려면

* 웹 콘솔에서

   * 아래에 **[!UICONTROL 상태]** 메뉴
   * 선택 **[!UICONTROL 로그 파일]**
   * 로그 파일 이름(예: )을 검색합니다. `scoring-debug`

* 서버의 로컬 디스크

   * 로그 파일이 &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log
   * 예, `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## 점수 및 배지 UGC {#ugc-for-scoring-and-badging}

선택한 SRP가 JSRP 또는 MSRP이지만 ASRP가 아닌 경우 점수 및 배지 지정과 관련된 UGC를 볼 수 있습니다. (이러한 용어에 익숙하지 않은 경우 [커뮤니티 컨텐츠 저장소](working-with-srp.md) 및 [저장소 리소스 공급자 개요](srp.md))

UGC를 사용하여 쉽게 액세스할 수 있으므로 점수 및 배지 데이터에 액세스하기 위한 설명은 JSRP를 사용합니다 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

**작성자의 JSRP**: 작성 환경에서 테스트하면 작성 환경에서만 표시되는 UGC가 만들어집니다.

**게시할 때의 JSRP**: 마찬가지로, 게시 환경에서 테스트하는 경우 게시 인스턴스에 대한 관리 권한이 있는 CRXDE Lite에 액세스해야 합니다. 게시 인스턴스가에서 실행 중인 경우 [프로덕션 모드](../../help/sites-administering/production-ready.md) (nosamplecontent runmode) [CRXDE Lite 활성화](../../help/sites-administering/enabling-crxde-lite.md).

JSRP에 대한 UGC의 기본 위치는 다음과 같습니다 `/content/usergenerated/asi/jcr/`.

### 점수 및 배지 API {#scoring-and-badging-apis}

다음 API를 사용할 수 있습니다.

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

설치된 의 최신 Javadocs [릴리스](deploy-communities.md#LatestReleases) Adobe 리포지토리에서 개발자가 사용할 수 있습니다. 자세한 내용은 [커뮤니티에 Maven 사용: Javadocs](maven.md#javadocs).

**저장소에서 UGC의 위치와 형식은 경고 없이 변경될 수 있습니다**.

### 설정 예 {#example-setup}

저장소 데이터의 스크린샷은 두 개의 서로 다른 AEM 사이트에서 포럼에 대한 점수 및 배지 설정으로부터 나옵니다.

1. 고유 ID를 사용하는 AEM 사이트(마법사를 사용하여 만든 커뮤니티 사이트):

   * 에서 만든 시작 자습서(참여) 사이트 사용 [시작하기 자습서](getting-started.md)
   * 포럼 페이지 노드를 찾습니다.

      * `/content/sites/engage/en/forum/jcr:content`
   * 점수 및 배지 속성 추가

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * 포럼 구성 요소 노드를 찾습니다.

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * 속성을 추가하여 배지 표시

      * `allowBadges = true`
   * 사용자가 로그인하고 포럼 주제를 만들며 청동 배지를 받습니다





1. AEM 사이트 *사용 안 함* 고유 id:

   * 사용 [커뮤니티 구성 요소 안내서](components-guide.md)
   * 포럼 페이지 노드를 찾습니다.

      * `/content/community-components/en/forum/jcr:content`
   * 점수 및 배지 속성 추가

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * 포럼 구성 요소 노드를 찾습니다.

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * 속성을 추가하여 배지 표시

      * `allowBadges = true`
   * 사용자가 로그인하고 포럼 주제를 만들며 청동 배지를 받습니다




1. 사용자에게 cURL을 사용하여 중재자 배지가 지정됩니다.

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

사용자가 청동 배지 두 개를 획득하고 중재자 배지 수여를 받았으므로 사용자가 다음과 같이 포럼 항목과 함께 표시됩니다.

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>이 예는 다음 우수 사례를 따르지 않습니다.
>
>* 점수 규칙 이름은 전체적으로 고유해야 합니다. 같은 이름으로 끝나면 안 됩니다.\
   >  예 *not* 다음을 수행합니다.\
   >  /etc/community/scoring/rules/site1/forums-scoring\
   >  /etc/community/scoring/rules/site2/forums-scoring
>
>* 다른 AEM 사이트에 대한 고유한 배지 이미지 만들기
>


### 액세스 점수 UGC {#access-scoring-ugc}

의 사용 [API](#scoring-and-badging-apis) 이 선호됩니다.

조사 목적으로 예제에 JSRP를 사용하면 점수가 포함된 기본 폴더는 다음과 같습니다

* `/content/usergenerated/asi/jcr/scoring`

의 하위 노드 `scoring`은 점수 규칙 이름입니다. 따라서 서버의 점수 규칙 이름을 전역적으로 고유하도록 지정하는 것이 가장 좋습니다.

Geometrixx 참여 사이트의 경우 사용자 및 해당 점수는 점수 규칙 이름, 커뮤니티 사이트의 사이트 ID( )로 구성된 경로에 있습니다 `engage-ba81p`) 내의 고유한 id 및 사용자 id를 반환합니다.

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

커뮤니티 구성 요소 안내서 사이트의 경우 사용자 및 해당 점수는 점수 규칙 이름, 기본 ID( )로 구성된 경로에 있습니다 `default-site`) 내의 고유한 id 및 사용자 id를 반환합니다.

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

점수는 속성에 저장됩니다 `scoreValue_tl` 직접 값을 포함할 수도 있고 간접적으로 atomicCounter를 참조할 수도 있습니다.

![chlimage_1-251](assets/chlimage_1-251.png)

### 배지 UGC 액세스 {#access-badging-ugc}

의 사용 [API](#scoring-and-badging-apis) 이 선호됩니다.

예를 들어 JSRP를 사용하여 조사 목적으로 지정된 배지에 대한 정보가 포함된 기본 폴더는 다음과 같습니다

* /content/usergenerated/asi/jcr

뒤에 사용자 프로필에 대한 경로가 차례로 표시되고 다음과 같은 배지 폴더로 끝납니다.

* /home/users/community/w271Up2Z4DjnOQrviv/profile/badge

#### 수상 배지 {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### 지정된 배지 {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## 추가 정보 {#additional-information}

점을 기준으로 정렬된 멤버 목록을 표시하려면 다음을 수행합니다.

* [리드 보드 기능](functions.md#leaderboard-function) 커뮤니티 사이트 또는 그룹 템플릿에 포함하기 위해
* [리드 보드 구성 요소](enabling-leaderboard.md): 페이지 작성을 위한 리드 보드 함수의 주요 구성 요소입니다.
