---
title: Sling 어댑터 사용
seo-title: Using Sling Adapters
description: Sling은 어댑터 패턴을 제공하여 적응형 인터페이스를 구현하는 개체를 간편하게 번역합니다
seo-description: Sling offers an Adapter pattern to conveniently translate objects that implement the Adaptable interface
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 7780d04d-418e-494c-85c3-76bef5f35690
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1753'
ht-degree: 14%

---

# Sling 어댑터 사용{#using-sling-adapters}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

[Sling](https://sling.apache.org) 오퍼 [어댑터 패턴](https://sling.apache.org/site/adapters.html) 구현된 객체를 간편하게 번역하려면 [적응성](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 인터페이스. 이 인터페이스는 일반 을 제공합니다 [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 개체를 인수로 전달되는 클래스 형식으로 변환하는 메서드입니다.

예를 들어 Resource 개체를 해당 Node 개체로 변환하려면 다음을 간단히 수행할 수 있습니다.

```java
Node node = resource.adaptTo(Node.class);
```

## 사용 사례 {#use-cases}

다음과 같은 사용 사례가 있습니다.

* 구현별 개체를 가져옵니다.

   예를 들어, 제네릭의 JCR 기반 구현 [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) 인터페이스는 기본 JCR에 대한 액세스 권한을 제공합니다. [`Node`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* 내부 컨텍스트 개체를 전달해야 하는 개체의 바로 가기 만들기

   예를 들어 JCR 기반 [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) 요청의 [`JCR Session`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html)과 같이 해당 요청 세션을 기반으로 작동하는 많은 개체에 대해 이 작업이 필요합니다. [`PageManager`](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) 또는 [`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* 서비스에 대한 바로 가기.

   드문 사례 - `sling.getService()` 간단합니다.

### Null 반환 값 {#null-return-value}

`adaptTo()` null을 반환할 수 있습니다.

다음과 같은 여러 가지 이유가 있습니다.

* 구현은 target 유형을 지원하지 않습니다
* 이 케이스를 처리하는 어댑터 팩터리가 활성 상태가 아닙니다(예: 서비스 참조가 누락되어)
* 내부 조건이 실패했습니다.
* 서비스를 사용할 수 없습니다.

null 케이스를 적절하게 처리하는 것이 중요합니다. jsp 렌더링의 경우 컨텐츠가 비어 있는 경우 jsp에 오류가 발생할 수 있습니다.

### 캐싱 {#caching}

성능을 개선하기 위해 구현은 자유롭게 `obj.adaptTo()` 호출. 만약 `obj` 는 동일하고 반환된 개체는 동일합니다.

이 캐싱은 모든 경우에 수행됩니다 `AdapterFactory` 기반 사례.

그러나 일반 규칙이 없습니다. 개체가 새 인스턴스이거나 기존 인스턴스일 수 있습니다. 즉, 두 동작에 의존할 수 없습니다. 따라서 그것은 특히 내부에서 중요합니다 `AdapterFactory`로 설정되면 이 시나리오에서는 해당 개체를 다시 사용할 수 있습니다.

### 작동 방법 {#how-it-works}

다음과 같은 다양한 방법이 있습니다 `Adaptable.adaptTo()` 를 구현할 수 있습니다.

* 개체 자체에 의해; 메서드 자체를 구현하고 특정 객체에 매핑합니다.
* 기준 [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)- 임의의 개체를 매핑할 수 있습니다.

   개체는 여전히 `Adaptable` 인터페이스 및 확장 필요 [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (이 `adaptTo` 중앙 어댑터 관리자 호출).

   후크를 사용하여 `adaptTo` 기존 클래스의 메커니즘(예: `Resource`.

* 둘 다 조합입니다.

첫 번째 경우 javadocs에 `adaptTo-targets` 가능합니다. 그러나 JCR 기반 리소스와 같은 특정 하위 클래스의 경우 이 작업이 불가능한 경우가 많습니다. 후자의 경우 `AdapterFactory` 는 일반적으로 번들의 개인 클래스의 일부이며, 따라서 클라이언트 API에 노출되거나 javadocs에 나열되지 않습니다. 이론적으로, 모든 사람들이 `AdapterFactory` 구현에서 [OSGi](/help/sites-deploying/configuring-osgi.md) 서비스 런타임에서 해당 &quot;adapttable&quot;(소스 및 타겟) 구성을 확인하지만 서로 매핑하지 않습니다. 결국, 이것은 문서화되어야 하는 내부 논리에 따라 다릅니다. 따라서 이 참조는

## 참조 {#reference}

### 슬링 {#sling}

[**리소스**](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) 다음 사항에 맞게 조정:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">노드</a></td> 
   <td>JCR 노드 기반 리소스이거나 노드를 참조하는 JCR 속성입니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">속성</a></td> 
   <td>JCR 속성 기반 리소스인 경우.</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">항목</a></td> 
   <td>JCR 기반 리소스(노드 또는 속성)인 경우</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">맵</a></td> 
   <td>JCR 노드 기반 리소스(또는 기타 리소스 지원 값 맵)인 경우 속성 맵을 반환합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>JCR 노드 기반 리소스(또는 기타 리소스 지원 값 맵)인 경우 속성의 사용하기 쉬운 맵을 반환합니다. 를 사용하여 (보다 간단하게) 구현할 수도 있습니다<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (null 케이스 등을 처리합니다).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">상속 값 맵</a></td> 
   <td>확장 <a href="https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> 속성을 찾을 때 리소스 계층 구조를 고려할 수 있도록 해줍니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersisstableValueMap</a></td> 
   <td>JCR 노드 기반 리소스인 경우 사용자는 해당 노드에서 속성을 수정할 수 있는 권한을 갖습니다.<br /> 참고: 여러 지속되는 맵은 해당 값을 공유하지 않습니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">입력 스트림</a></td> 
   <td>"file"의 이진 콘텐츠 반환<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[**ResourceResolver**](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) 다음 사항에 맞게 조정:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Session</a></td> 
   <td>JCR 기반 리소스 확인자(기본값)인 경우 요청의 JCR 세션입니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">디자이너</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>JCR 기반 리소스 확인자인 경우 JCR 세션을 기반으로 합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>JCR 기반 리소스 확인자인 경우 JCR 세션을 기반으로 합니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>JCR 세션을 기반으로 하는 경우, JCR 기반 리소스 확인자이고 사용자에게 UserManager에 액세스할 수 있는 권한이 있는 경우.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">승인 가능 대상</a> </td> 
   <td>현재 사용자입니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">사용자</a><br /> </td> 
   <td>현재 사용자입니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/privileges/PrivilegeManager.html">Privilemanager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/Preferences.html">환경 설정</a></td> 
   <td>현재 사용자의 환경 설정(JCR 기반 리소스 확인자인 경우 JCR 세션 기반).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">기본 설정 서비스</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/auth/pin/PinManager.html">PinManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">외부 도우미</a></td> 
   <td>절대 URL을 표면화하기 위해, 요청 개체가 있더라도 말이다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

[**SlingHttpServletRequest**](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) 다음 사항에 맞게 조정:

대상이 아직 없지만 Adaptable을 구현하고 사용자 지정 AdapterFactory에서 소스로 사용할 수 있습니다.

[**SlingHttpServletResponse**](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) 다음 사항에 맞게 조정:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>sling 재작성기 응답인 경우</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[**페이지**](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) 다음 사항에 맞게 조정:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">리소스</a><br /> </td> 
   <td>페이지의 리소스.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td> 
   <td>레이블이 지정된 리소스(이 ==).</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">노드</a></td> 
   <td>페이지의 노드입니다.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>페이지의 리소스를 조정할 수 있는 모든 것입니다.</td> 
  </tr> 
 </tbody> 
</table>

[**구성 요소**](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) 다음 사항에 맞게 조정:

| [리소스](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 구성 요소의 리소스입니다. |
|---|---|
| [LabeledResource](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | 레이블이 지정된 리소스(이 ==). |
| [노드](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 구성 요소의 노드입니다. |
| ... | 구성 요소의 리소스에 적용할 수 있는 모든 것입니다. |

[**템플릿**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) 다음 사항에 맞게 조정:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">리소스</a><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>템플릿의 리소스입니다.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td> 
   <td>레이블이 지정된 리소스(이 ==).</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">노드</a></td> 
   <td>이 템플릿의 노드입니다.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>템플릿의 리소스를 조정할 수 있는 모든 것입니다.</td> 
  </tr> 
 </tbody> 
</table>

#### 보안 {#security}

[**승인 가능**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html), [**사용자**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) 및 [**그룹**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) 적응:

| [노드](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 사용자/그룹 홈 노드를 반환합니다. |
|---|---|
| [복제 상태](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | 사용자/그룹 홈 노드에 대한 복제 상태를 반환합니다. |

#### DAM {#dam}

[**자산**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) 다음 사항에 맞게 조정:

| [리소스](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 자산의 리소스입니다. |
|---|---|
| [노드](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 자산의 노드입니다. |
| ... | 자산의 리소스를 조정할 수 있는 모든 것입니다. |

#### 태그 지정 {#tagging}

[**태그**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) 다음 사항에 맞게 조정:

| [리소스](https://helpx.adobe.com/kr/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 태그의 리소스. |
|---|---|
| [노드](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 태그의 노드입니다. |
| ... | 태그의 리소스에 적용할 수 있는 모든 것입니다. |

#### 기타 {#other}

또한 Sling / JCR / OCM 은 ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` 사용자 지정 OCM([개체 콘텐츠 매핑](https://jackrabbit.apache.org/object-content-mapping.html)) 내의 아무 곳에나 삽입할 수 있습니다.
