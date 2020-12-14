---
title: 고급 점수 및 배지
seo-title: 고급 점수 및 배지
description: 고급 점수 설정
seo-description: 고급 점수 설정
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
translation-type: tm+mt
source-git-commit: ddf92a270835259998aa28f5960abcf55f56d1fc
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---


# 고급 점수 및 배지 {#advanced-scoring-and-badges}

## 개요 {#overview}

고급 득점에서는 참가자를 전문가로 식별할 수 있도록 배지 수여가 가능합니다. 고급 채점에서는 회원이 만든 컨텐츠의 수량 *및* 품질을 기반으로 점수를 할당하는 반면, 기본 채점에서는 생성된 컨텐츠의 양을 기반으로 포인트를 할당합니다.

이러한 차이는 점수를 계산하는 데 사용된 점수 엔진 때문입니다. 기본 점수 엔진은 간단한 수학을 적용합니다. 고급 채점 엔진은 주제의 자연 언어 처리(NLP)를 통해 추론된 개념으로, 가치가 높은 관련 컨텐츠를 제공하는 활성 회원에게 보상을 주는 적응형 알고리즘입니다.

점수 알고리즘은 컨텐츠 연관성 외에도 투표 및 대답 비율과 같은 멤버 활동을 고려합니다. 기본 점수에는 양적인 기준이 포함되지만 고급 점수에서는 알고리즘을 사용합니다.

따라서 고급 채점 엔진은 분석을 의미 있게 할 수 있는 충분한 데이터가 필요합니다. 전문가가 되기 위한 성취 임계값은 알고리즘이 계속해서 생성되는 컨텐츠의 양과 품질을 조정하므로 지속적으로 재평가됩니다. 회원의 이전 게시물에 대한 *감소*&#x200B;의 개념도 있습니다. 전문가 멤버가 전문가 상태를 얻은 해당 항목에 더 이상 참여하지 않을 경우 사전 결정된 일부 지점([채점 엔진 구성](#configurable-scoring-engine) 참조)에 전문가 신분을 잃게 됩니다.

고급 채점 설정은 기본 채점과 거의 동일합니다.

* 기본 및 고급 점수 지정 및 배지 규칙은 [동일한 방식으로 콘텐츠에 적용됨](implementing-scoring.md#apply-rules-to-content)
   * 동일한 컨텐츠에 기본 및 고급 채점 및 배지 규칙을 적용할 수 있습니다.
* [구성 요소 ](implementing-scoring.md#enable-badges-for-component) 제네릭 배지 활성화

점수 지정 및 배지 규칙 설정의 차이점은 다음과 같습니다.

* 구성 가능한 고급 채점 엔진
* 고급 채점 규칙:
   * `scoringType` [ **[!UICONTROL 고급]으로 설정]**
   * 중지 단어 필요

* 고급 배지 규칙:
   * `badgingType` [ **[!UICONTROL 고급]으로 설정]**
   * `badgingLevels` 상을 받을 전문가 수준 수 설정
   * 임계값에 대한 배열 매핑 지점 대신 배지의 `badgingPaths` 배지가 필요합니다.

>[!NOTE]
>
>고급 점수 지정 및 배지 기능을 사용하려면 [전문가 식별 패키지](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg)를 설치합니다.

## 구성 가능한 점수 엔진 {#configurable-scoring-engine}

고급 점수 지정 엔진은 고급 점수 지정 알고리즘에 영향을 주는 매개 변수를 사용하여 OSGi 구성을 제공합니다.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL 점수]**
가중치주제에 대해 점수를 계산할 때 가장 높은 우선 순위를 주어야 하는 동사를 지정합니다. 하나 이상의 주제를 입력할 수 있지만 주제당 동사 **1개**&#x200B;로 제한됩니다. [항목 및 동사](implementing-scoring.md#topics-and-verbs)를 참조하십시오.

   쉼표를 이스케이프한 `topic,verb`으로 입력했습니다. 예:

   `/social/forum/hbs/social/forum\,ADD`

   기본값은 QnA 및 포럼 구성 요소에 대한 ADD 동사로 설정됩니다.


* **[!UICONTROL 점수 범위]**

   고급 점수의 범위는 이 값(가능한 최대 점수) 및 0(가능한 최저 점수)으로 정의됩니다.

   기본값은 100이므로 점수 범위는 0-100입니다.


* **[!UICONTROL 개체 감소 시간 간격]**

   이 매개 변수는 모든 엔티티 점수가 지워지는 이후의 시간 수를 나타냅니다. 커뮤니티 사이트의 점수에 더 이상 이전 컨텐츠를 포함하지 않아야 합니다.

   기본값은 21,6000시간(24년)입니다.


* **[!UICONTROL 채점 증가 비율]**

   점수를 지정합니다. 0 - 채점 범위 사이에서 성장 속도가 느려져서 전문가 수를 제한할 수 있습니다.

   기본값은 50입니다.

## 고급 점수 지정 규칙 {#advanced-scoring-rules}

기초채점에선 배지 달기 물량이 알려져 있다.

고급 채점에서는 시스템 내 품질 데이터의 양에 따라 필요한 양을 지속적으로 조정할 수 있습니다. 채점은 벨 곡선과 유사한 방식으로 지속적으로 계산됩니다.

더 이상 활성 상태가 아닌 주제에 대해 전문가 배지를 획득한 경우 시간이 지남에 따라 부패로 인해 배지를 잃게 될 가능성이 있습니다.

### 점수 지정 유형 {#scoringtype}

점수 지정 규칙은 점수 지정 하위 규칙 집합이며 각 규칙이 `scoringType`을 선언합니다.

고급 점수 지정 엔진을 호출하려면 `scoringType`을 `advanced`로 설정해야 합니다.

[채점 하위 규칙](implementing-scoring.md#scoring-sub-rules)을 참조하십시오.

![chlimage_1-261](assets/chlimage_1-261.png)

### 중지 단어 {#stopwords}

고급 채점 패키지는 초점 파일이 포함된 구성 폴더를 설치합니다.

* `/etc/community/scoring/configuration/stopwords`

고급 점수 지정 알고리즘은 초점 파일에 포함된 단어 목록을 사용하여 컨텐츠 처리 중에 무시되는 일반적인 영어 단어를 식별합니다.

이 파일이 수정될 가능성은 없습니다.

stopwords 파일이 없으면 고급 점수 지정 엔진에서 오류가 발생합니다.

## 고급 배지 규칙 {#advanced-badging-rules}

고급 배지 규칙 속성은 [기본 배지 규칙 속성](implementing-scoring.md#badging-rules)과 다릅니다.

배지 이미지에 포인트를 연결하는 대신 허용되는 전문가 수와 배지 이미지를 식별하기만 하면 됩니다.

![chlimage_1-262](assets/chlimage_1-262.png)

| **속성** | **유형** | **값 설명** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | String[] | (필수) 배지 수준 수에 이르기까지 배지 이미지의 다중 값 문자열입니다. 배지 이미지 경로는 순서대로 정렬해야 첫 번째 배지는 가장 높은 전문가에게 부여됩니다. 배지(badgingLevels)에 지정된 배지가 적은 경우 배열의 마지막 배지가 나머지 배열에 채워집니다. 시작 예:/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | 긴 | (선택 사항) 받을 전문 지식 수준을 지정합니다. 예를 들어 전문가 및 거의 전문가(배지 2개)가 있어야 하는 경우 값을 2로 설정해야 합니다. badgingLevel은 badgingPath 속성에 나열된 전문가 관련 배지 이미지 수와 일치해야 합니다. 기본값은 1입니다. |
| badgingType | 문자열 | (필수) 채점 엔진을 &quot;기본&quot; 또는 &quot;고급&quot;으로 식별합니다. &quot;advanced&quot;로 설정되어 있거나, 기본값은 &quot;basic&quot;입니다. |
| scoringRules | 문자열[] | (선택 사항) 나열되는 점수 지정 규칙에 의해 식별된 점수부여 이벤트에 대한 배지 규칙을 제한하는 복수 값 문자열. 예 입력:/etc/community/scoring/rules/adv-comments-scoring기본값은 제한이 없습니다. |

## 포함된 규칙 및 배지 {#included-rules-and-badge}

### 포함된 배지 {#included-badge}

이 베타 릴리스에 포함된 제품:

* 전문가

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

활동상의 보상으로 전문가 배지가 나타나려면 두 가지 사항이 필요합니다.

* `badges` 포럼 또는 QnA 구성 요소와 같은 기능에 대해 활성화되어야 합니다.
* 고급 채점 및 배지 규칙은 구성 요소가 배치된 페이지(또는 상위 페이지)에 적용되어야 합니다.

다음에 대한 기본 정보를 참조하십시오.

* [구성 요소에 대한 배지 활성화](implementing-scoring.md#enable-badges-for-component)
* [규칙 적용](implementing-scoring.md#apply-rules-to-content)

### 포함 점수 규칙 및 하위 규칙 {#included-scoring-rules-and-sub-rules}

베타 릴리스에 포함된 2개의 포럼 함수[에 대한 2개의 고급 채점 규칙은 포럼과 포럼 기능의 주석 구성 요소에 각각 하나씩 있습니다.](functions.md#forum-function)

1. /etc/community/scoring/rules/adv-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-voting-rule-owner

      /etc/community/scoring/rules/sub-rules/adv-voting-rule

2. /etc/community/scoring/rules/adv-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-forums-rule

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-voting-rule-owner

**메모:**

* `rules`과 `sub-rules` 노드 모두 `cq:Page` 유형입니다.
* `subRules` 은 규칙의 노드에서 [] Stringing 유형의  `jcr:content` 특성입니다.
* `sub-rules` 다양한 채점 규칙 간에 공유될 수 있습니다.
* `rules` 저장소 위치에 모든 사용자에 대한 읽기 권한이 있어야 합니다.
   * 규칙 이름은 위치에 관계없이 고유해야 합니다.

### 배지 규칙 포함 {#included-badging-rules}

이 릴리스에는 [고급 포럼 및 댓글 점수 지정 규칙](#included-scoring-rules-and-sub-rules)에 해당하는 2개의 고급 배지 규칙이 포함되어 있습니다.

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**메모:**

* `rules` node are type  `cq:Page`
* `rules`저장소 위치에 모든 사용자에 대한 읽기 권한이 있어야 합니다.
   * 규칙 이름은 위치에 관계없이 고유해야 합니다.
