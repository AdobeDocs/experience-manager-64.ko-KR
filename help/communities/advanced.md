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
role: Administrator
exl-id: c9406aae-288e-4cdf-ac01-cb26b423639e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---

# 고급 점수 및 배지 {#advanced-scoring-and-badges}

## 개요 {#overview}

고급 점수 책정을 통해 회원들을 전문가로 식별할 수 있습니다. 고급 점수는 구성원이 만든 컨텐츠의 수량 *및* 품질에 따라 포인트를 지정하지만, 기본 점수는 생성된 컨텐츠의 수량을 기준으로 포인트를 할당합니다.

이 차이는 점수를 계산하는 데 사용되는 점수 엔진에서 비롯됩니다. 기초채점엔진은 간단한 수학을 적용한다. 고급 점수 엔진은 주제의 자연어 처리(NLP)를 통해 추론된 가치 및 관련 컨텐츠를 제공하는 활성 구성원에게 보상을 제공하는 적응형 알고리즘입니다.

콘텐츠 관련성 외에도 점수 알고리즘에서는 투표 및 답변 비율과 같은 구성원 활동을 고려합니다. 기본 점수가 정량적으로 포함되지만 고급 점수는 알고리즘을 사용합니다.

따라서, 고급 점수 엔진은 분석에 의미 있는 결과를 만들 충분한 데이터를 필요로 한다. 전문가가 되기 위한 성취 임계값은 알고리즘이 계속해서 만들어지는 컨텐츠의 볼륨 및 품질을 조정하므로 지속적으로 재평가됩니다. 구성원의 이전 게시물에 대한 *가치 하락*&#x200B;도 있습니다. 전문가 구성원이 전문가 상태를 얻은 주제 작업에 참여하는 것을 중지하면, 사전 결정된 일부 지점( [점수 엔진 구성](#configurable-scoring-engine) 참조)에서 전문가 로서의 지위를 잃게 됩니다.

고급 점수를 설정하는 것은 기본 점수와 거의 동일합니다.

* 기본 및 고급 점수 및 배지 규칙은 [콘텐츠](implementing-scoring.md#apply-rules-to-content)에 동일하게 적용됩니다
   * 기본 및 고급 점수 및 배지 규칙은 동일한 콘텐츠에 적용할 수 있습니다
* [구성 요소에 대한 ](implementing-scoring.md#enable-badges-for-component) 배지 활성화

점수부여 및 배지 규칙을 설정할 때의 차이점은 다음과 같습니다.

* 구성 가능한 고급 점수 엔진
* 고급 점수 규칙:
   * `scoringType` 고급으로  **[!UICONTROL 설정]**
   * 불용 단어 필요

* 고급 배지 규칙:
   * `badgingType` 고급으로  **[!UICONTROL 설정]**
   * `badgingLevels` 포상을 받을 전문가 레벨 수로 설정
   * 배지에 대한 임계값 배열 매핑 점 대신 `badgingPaths` 배지 배열 필요

>[!NOTE]
>
>고급 점수 및 배지 기능을 사용하려면 [전문가 식별 패키지](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg)를 설치하십시오.

## 구성 가능한 점수 엔진 {#configurable-scoring-engine}

고급 점수 엔진은 고급 점수 알고리즘에 영향을 주는 매개 변수가 포함된 OSGi 구성을 제공합니다.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL 점수]**
가중치항목을 계산할 때 가장 높은 우선 순위를 지정해야 하는 동사를 지정합니다. 하나 이상의 항목을 입력할 수 있지만 항목당 하나의 동사 **로 제한됩니다**. [항목 및 동사](implementing-scoring.md#topics-and-verbs)를 참조하십시오.

   쉼표가 이스케이프 처리된 `topic,verb`으로 입력되었습니다. 예:

   `/social/forum/hbs/social/forum\,ADD`

   기본값은 QnA 및 포럼 구성 요소에 대해 ADD 동사로 설정됩니다.


* **[!UICONTROL 점수 범위]**

   고급 점수의 범위는 이 값(가능한 최대 점수)과 0(가능한 최소 점수)으로 정의됩니다.

   기본값은 100이므로 점수 범위가 0-100입니다.


* **[!UICONTROL 엔티티 감소 시간 간격]**

   이 매개 변수는 모든 엔티티 점수가 지워진 후 시간(시)을 나타냅니다. 커뮤니티 사이트의 점수에 더 이상 이전 콘텐츠를 포함하지 않아야 합니다.

   기본값은 216000 시간(~24년)입니다.


* **[!UICONTROL 점수 증가율]**

   점수를 지정합니다. 0과 채점 범위 사이에, 성장이 둔화되면서 전문가 수가 제한된다.

   기본값은 50입니다.

## 고급 점수 규칙 {#advanced-scoring-rules}

기본 점수에서 배지를 만드는 데 필요한 양이 알려져 있습니다.

고급 채점에서는 시스템 내의 품질 데이터의 양에 따라 필요한 수량이 지속적으로 조정됩니다. 점수는 벨 커브와 유사한 방식으로 계속해서 계산됩니다.

더 이상 활성 상태가 아닌 주제에 대해 전문가 배지를 얻으면 시간이 지남에 따라 부패로 인해 배지를 잃게 될 가능성이 있습니다.

### 점수부여 유형 {#scoringtype}

점수 규칙은 점수 하위 규칙 집합이며 각 규칙에 `scoringType`이 선언됩니다.

고급 점수 엔진을 호출하려면 `scoringType`을 `advanced`(으)로 설정해야 합니다.

[점수 하위 규칙](implementing-scoring.md#scoring-sub-rules)을 참조하십시오.

![chlimage_1-261](assets/chlimage_1-261.png)

### 스토워드 {#stopwords}

고급 점수 패키지는 스톱 단어 파일이 포함된 구성 폴더를 설치합니다.

* `/etc/community/scoring/configuration/stopwords`

고급 점수 책정 알고리즘에서는 stopwords 파일에 포함된 단어 목록을 사용하여 컨텐츠 처리 중에 무시되는 일반적인 영어 단어를 식별합니다.

이 파일을 수정할 가능성은 없습니다.

stopwords 파일이 없으면 고급 점수 엔진이 오류가 발생합니다.

## 고급 배지 규칙 {#advanced-badging-rules}

고급 배지 규칙 속성은 [기본 배지 규칙 속성](implementing-scoring.md#badging-rules)과 다릅니다.

배지 이미지와 포인트를 연관시키는 대신, 허용된 전문가 수와 배지 이미지를 포상할 것인지 식별하기만 하면 됩니다.

![chlimage_1-262](assets/chlimage_1-262.png)

| **속성** | **유형** | **값 설명** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | String[] | (필수) 배지 이미지의 최대 배지 레벨 수입니다. 배지 이미지 경로는 먼저 가장 높은 전문가에게 부여되도록 정렬해야 합니다. 배지 수준이 나타내는 것보다 적은 배지가 있는 경우 배열의 마지막 배지가 나머지 배열에 채워집니다. 예제 항목:/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | 긴 | (선택 사항) 수여할 전문 지식 수준을 지정합니다. 예를 들어 전문가 및 거의 전문가(배지 2개)가 있어야 하는 경우 값을 2로 설정해야 합니다. badgingLevel은 badgingPath 속성에 대해 나열된 전문가 관련 배지 이미지 수와 일치해야 합니다. 기본값은 1입니다. |
| badgingType | 문자열 | (필수) 점수 엔진을 &quot;기본&quot; 또는 &quot;고급&quot;으로 식별합니다. &quot;고급&quot;으로 설정하면 기본값이 &quot;기본&quot;입니다. |
| scoringRules | 문자열[] | (선택 사항) 나열된 점수 규칙으로 식별된 점수 이벤트로 배지 규칙을 제한하는 복수 값 문자열입니다. 예 입력:/etc/community/scoring/rules/adv-comments-scoringDefault는 제한이 없습니다. |

## 포함 규칙 및 배지 {#included-rules-and-badge}

### 포함된 배지 {#included-badge}

이 베타 릴리스에 포함된 리워드 기반 전문가 배지는 다음과 같습니다.

* 전문가

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

활동에 대한 보상으로 전문가 배지가 표시되려면 다음 두 가지 사항이 있어야 합니다.

* `badges` 포럼 또는 QnA 구성 요소와 같은 기능에 대해 활성화되어야 합니다
* 고급 점수 및 배지 규칙은 구성 요소가 배치된 페이지(또는 상위)에 적용되어야 합니다

다음에 대한 기본 정보를 참조하십시오.

* [구성 요소에 대한 배지 활성화](implementing-scoring.md#enable-badges-for-component)
* [규칙 적용](implementing-scoring.md#apply-rules-to-content)

### 점수 규칙 및 하위 규칙 포함 {#included-scoring-rules-and-sub-rules}

베타 릴리스에 포함된 두 가지 고급 점수 규칙은 [포럼 함수](functions.md#forum-function)(포럼 및 포럼 기능의 주석 구성 요소에 대해 각각 하나씩)에 있습니다.

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
* `subRules` 규칙 노드에서 [] String 유형의  `jcr:content` 특성입니다
* `sub-rules` 다양한 점수 규칙 간에 공유할 수 있습니다
* `rules` 모든 사용자에 대해 읽기 권한이 있는 저장소 위치에 있어야 합니다
   * 규칙 이름은 위치에 관계없이 고유해야 합니다

### 배지 규칙 포함 {#included-badging-rules}

릴리스에 포함된 두 가지 고급 배지 규칙은 [고급 포럼 및 댓글 점수 규칙](#included-scoring-rules-and-sub-rules)에 해당합니다.

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**메모:**

* `rules` 노드는 유형입니다.  `cq:Page`
* `rules`모든 사용자에 대해 읽기 권한이 있는 저장소 위치에 있어야 합니다
   * 규칙 이름은 위치에 관계없이 고유해야 합니다
