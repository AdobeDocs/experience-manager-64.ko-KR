---
title: Query Builder의 사용자 지정 설명 평가기 구현
seo-title: Query Builder의 사용자 지정 설명 평가기 구현
description: Query Builder에서는 컨텐츠 저장소를 쉽게 쿼리하는 방법을 제공합니다
seo-description: Query Builder에서는 컨텐츠 저장소를 쉽게 쿼리하는 방법을 제공합니다
uuid: 5b599b60-a149-4425-b7ac-7fbe7e048bca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 08bdade7-fdad-445d-80fe-8fc06596dace
exl-id: afa7f346-fefa-4faa-bf2d-7480a7e5a5ee
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 3%

---

# Query Builder의 사용자 지정 설명 평가기 구현{#implementing-a-custom-predicate-evaluator-for-the-query-builder}

이 섹션에서는 사용자 지정 설명 평가기를 구현하여 [Query Builder](/help/sites-developing/querybuilder-api.md)를 확장하는 방법을 설명합니다.

## 개요 {#overview}

[Query Builder](/help/sites-developing/querybuilder-api.md)는 컨텐츠 저장소를 쉽게 쿼리하는 방법을 제공합니다. AEM은 데이터를 처리하는 데 도움이 되는 조건자 평가자 세트와 함께 제공됩니다.

그러나 일부 복잡성을 숨기고 더 나은 의미 체계를 보장하는 사용자 지정 설명 평가기를 구현하여 쿼리를 단순화할 수 있습니다.

사용자 지정 조건부는 XPath를 사용하여 직접 수행할 수 없는 다른 작업을 수행할 수도 있습니다. 예를 들면 다음과 같습니다.

* 일부 서비스에서 일부 데이터 보기
* 계산 기반 사용자 지정 필터링

>[!NOTE]
>
>사용자 지정 설명을 구현할 때 성능 문제를 고려해야 합니다.

>[!NOTE]
>
>[쿼리 빌더](/help/sites-developing/querybuilder-api.md) 섹션에서 쿼리 예제를 찾을 수 있습니다.

GITHUB의 코드

GitHub에서 이 페이지의 코드를 찾을 수 있습니다

* [GitHub에서 aem-search-custom-predicate-evaluator 프로젝트를 엽니다.](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
* 프로젝트를 [ZIP 파일](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)로 다운로드합니다

## 설명 평가기 세부 사항 {#predicate-evaluator-in-detail}

조건자 평가기는 쿼리의 제약 조건을 정의하는 특정 조건자에 대한 평가를 처리합니다.

상위 수준 검색 제한(&quot;너비 > 200&quot; 등)을 실제 컨텐츠 모델에 맞는 특정 JCR 쿼리(예: 메타데이터/@width > 200)에 매핑합니다. 또는 노드를 수동으로 필터링하고 해당 제약 조건을 확인할 수 있습니다.

>[!NOTE]
>
>`PredicateEvaluator` 및 `com.day.cq.search` 패키지에 대한 자세한 내용은 [Java 설명서](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/search/package-summary.html)를 참조하십시오.

## 복제 메타데이터에 대한 사용자 지정 설명 평가기 구현 {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

예를 들어 이 섹션에서는 복제 메타데이터를 기반으로 데이터를 제공하는 사용자 지정 설명 평가기를 만드는 방법을 설명합니다.

* `cq:lastReplicated` 마지막 복제 작업의 날짜를 저장합니다.

* `cq:lastReplicatedBy` 마지막 복제 작업을 트리거한 사용자의 id를 저장합니다

* `cq:lastReplicationAction` 마지막 복제 작업(예: 활성화, 비활성화)을 저장하는 스토리지

### 기본 설명 평가자를 사용하여 복제 메타데이터 쿼리 {#querying-replication-metadata-with-default-predicate-evaluators}

다음 쿼리는 연도 시작 이후 `admin`에 의해 활성화된 `/content` 분기의 노드 목록을 가져옵니다.

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

이 쿼리는 유효하지만 읽기 어려우며 세 복제 속성 간의 관계를 강조 표시하지 않습니다. 사용자 지정 설명 평가기를 구현하면 복잡성을 줄이고 이 쿼리의 의미 체계를 개선합니다.

### 목표 {#objectives}

`ReplicationPredicateEvaluator`의 목표는 다음 구문을 사용하여 위의 쿼리를 지원하는 것입니다.

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

사용자 지정 설명 평가기로 복제 메타데이터 설명을 그룹화하면 의미 있는 쿼리를 만들 수 있습니다.

### Maven 종속성 업데이트 중 {#updating-maven-dependencies}

>[!NOTE]
>
>maven을 사용하는 새 AEM 프로젝트 설정은 [Apache Maven](/help/sites-developing/ht-projects-maven.md)을 사용하여 AEM 프로젝트를 작성하는 방법에 의해 문서화되었습니다.

먼저 프로젝트의 Maven 종속성을 업데이트해야 합니다. `PredicateEvaluator`은 `cq-search` 아티팩트의 일부이므로 Maven pom 파일에 추가해야 합니다.

>[!NOTE]
>
>`OSGi` 컨테이너에 의해 `cq-search`가 제공되므로 `cq-search` 종속성의 범위가 `provided`로 설정됩니다.

pom.xml

다음 코드 조각은 [통합 비교 형식](https://en.wikipedia.org/wiki/Diff#Unified_format)의 차이점을 보여 줍니다

```
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

[aem-search-custom-조건자-평가기](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator) -  [pom.xml](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/7aed6b35b4c8dd3655296e1b10cf40c0dd1eaa61/pom.xml)

### ReplicationDe조건자 평가기를 쓰는 중 {#writing-the-replicationpredicateevaluator}

`cq-search` 프로젝트에 `AbstractPredicateEvaluator` 추상 클래스가 포함되어 있습니다. 사용자 지정 설명 평가기 `(PredicateEvaluator`)를 구현하는 몇 가지 단계로 확장할 수 있습니다.

>[!NOTE]
>
>다음 절차에서는 데이터를 필터링하기 위해 `Xpath` 표현식을 작성하는 방법에 대해 설명합니다. 행을 기준으로 데이터를 선택하는 `includes` 메서드를 구현하는 방법도 있습니다. 자세한 내용은 [Java 설명서](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html#includes28comdaycqsearchpredicatejavaxjcrqueryrowcomdaycqsearchevalevaluationcontext29)를 참조하십시오.

1. `com.day.cq.search.eval.AbstractPredicateEvaluator`을 확장하는 새 Java 클래스를 만듭니다.
1. 다음과 같이 `@Component` 을 사용하여 클래스에 주석을 답니다

   src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

   다음 코드 조각은 [통합 비교 형식](https://en.wikipedia.org/wiki/Diff#Unified_format)의 차이점을 보여 줍니다


```
@@ -19,8 +19,11 @@
  */
 package com.adobe.aem.docs.search;
+import org.apache.felix.scr.annotations.Component;
+import com.day.cq.search.eval.AbstractPredicateEvaluator;
+@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
 public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

  }
```

[aem-search-custom-조건자-평가기](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator) -  [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/ec70fac35fbd0d132e00c6066a204804e9cbe70f/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)

>[!NOTE]
>
>`factory`은 `com.day.cq.search.eval.PredicateEvaluator/`로 시작하고 사용자 지정 `PredicateEvaluator`의 이름으로 끝나는 고유한 문자열이어야 합니다.

>[!NOTE]
>
>`PredicateEvaluator` 이름은 쿼리를 작성할 때 사용되는 조건자 이름입니다.

1. 오버라이드:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   override 메서드에서 인수에 지정된 `Predicate`에 따라 `Xpath` 표현식을 만듭니다.

### 복제 메타데이터 {#example-of-a-custom-predicate-evalutor-for-replication-metadata}에 대한 사용자 지정 설명 평가자의 예

이 `PredicateEvaluator`의 전체 구현은 다음 클래스와 유사할 수 있습니다.

src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

```
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;

import org.slf4j.Logger;

import org.slf4j.LoggerFactory;

 
import com.day.cq.search.Predicate;

import com.day.cq.search.eval.AbstractPredicateEvaluator;

import com.day.cq.search.eval.EvaluationContext;

 
@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";

    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";

    static final String PN_LAST_REPLICATED = "cq:lastReplicated";

    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";

    static final String PREDICATE_SINCE = "since";

    static final String PREDICATE_SINCE_OP = " >= ";

    static final String PREDICATE_ACTION = "action";
 

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,

            EvaluationContext context) {

        log.debug("predicate {}", predicate);


        String date = predicate.get(PREDICATE_SINCE);

        String user = predicate.get(PREDICATE_BY);

        String action = predicate.get(PREDICATE_ACTION);


        StringBuilder sb = new StringBuilder();


        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);

            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);

            sb.append(PN_LAST_REPLICATED_BY);

            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);

            sb.append(PN_LAST_REPLICATED_ACTION);

            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```

[aem-search-custom-조건자-평가기](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)  -  [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/blob/master/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)
