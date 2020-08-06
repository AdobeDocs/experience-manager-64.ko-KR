---
title: AEM의 서비스 사용자
seo-title: AEM의 서비스 사용자
description: AEM의 서비스 사용자에 대해 알아봅니다.
seo-description: AEM의 서비스 사용자에 대해 알아봅니다.
uuid: 4efab5fb-ba11-4922-bd68-43ccde4eb355
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 9cfe5f11-8a0e-4a27-9681-a8d50835c864
translation-type: tm+mt
source-git-commit: dda8156729aa46dd6cfd779bca120b165ccc980b
workflow-type: tm+mt
source-wordcount: '1788'
ht-degree: 0%

---


# AEM의 서비스 사용자{#service-users-in-aem}

## 개요 {#overview}

AEM에서 관리 세션이나 리소스 확인자를 가져오는 주된 방법은 Sling에서 제공하는 `SlingRepository.loginAdministrative()` 및 `ResourceResolverFactory.getAdministrativeResourceResolver()` 메서드를 사용하는 것입니다.

그러나 이러한 방법 중 어느 것도 최소한의 [권한](https://en.wikipedia.org/wiki/Principle_of_least_privilege) 원칙에 따라 설계되지 않았으며 개발자가 초기에 컨텐츠에 적합한 구조와 해당 ACL(Access Control Levels)을 계획하지 않아도 됩니다. 이러한 서비스에 취약점이 있는 경우 코드 자체에 `admin` 대한 관리 권한이 필요하지 않더라도 사용자에게 권한 에스컬레이션이 발생할 수 있습니다.

## 관리자 세션 위상 종료 방법 {#how-to-phase-out-admin-sessions}

### 우선 순위 0: 이 기능은 활성 상태입니까/필수 입니까/방치입니까? {#priority-is-the-feature-active-needed-derelict}

관리 세션이 사용되지 않거나 기능이 완전히 비활성화되어 있을 수 있습니다. 구현의 경우 기능을 완전히 제거하거나 [NOP 코드에 맞아야 합니다](https://en.wikipedia.org/wiki/NOP).

### 우선 순위 1: 요청 세션 사용 {#priority-use-the-request-session}

가능한 한 해당 인증된 요청 세션을 컨텐츠 읽기 또는 쓰기에 사용할 수 있도록 기능을 리팩터링할 수 있습니다. 이렇게 할 수 없는 경우 아래 우선 순위를 적용하여 얻을 수 있습니다.

### 우선 순위 2: 컨텐츠 재구성 {#priority-restructure-content}

콘텐츠를 재조정하면 많은 문제가 해결된다. 구조 조정을 수행할 때 다음과 같은 간단한 규칙을 염두에 두십시오.

* **액세스 제어 변경**

   * 액세스 권한이 정말로 필요한 사용자나 그룹이 실제로 액세스 권한을 가지고 있는지 확인하십시오.

* **콘텐츠 구조 조정**

   * 액세스 제어가 사용 가능한 요청 세션과 일치하는 경우 등 다른 위치로 이동합니다.
   * 컨텐츠 세부기간 변경;

* **코드를 적절한 서비스로 재지정**

   * JSP 코드에서 서비스로 비즈니스 로직을 이동합니다. 이를 통해 다양한 컨텐츠 모델링을 수행할 수 있습니다.

또한 다음과 같은 원칙을 준수하는 새로운 기능을 개발할 수 있습니다.

* **보안 요구 사항은 컨텐츠 구조를 주도해야 합니다.**

   * 액세스 제어 관리 시 자연스러워
   * 액세스 제어는 애플리케이션이 아니라 보관소에서 적용해야 합니다

* **노데티프 사용**

   * 설정할 수 있는 속성 집합 제한

* **개인 정보 설정 준수**

   * 비공개 프로필의 경우, 한 가지 예는 비공개 `/profile` 노드에 있는 프로필 사진, 이메일 또는 전체 이름을 노출하지 않는 것입니다.

## 엄격한 액세스 제어 {#strict-access-control}

컨텐츠를 재구성할 때 액세스 제어를 적용하거나 새 서비스 사용자를 위해 수행하는 경우, 가능한 엄격한 ACL을 적용해야 합니다. 가능한 모든 액세스 제어 기능 사용:

* 예를 들어, on `jcr:read` 을 사용하는 대신 `/apps``/apps/*/components/*/analytics`

* Use [restrictions](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html)

* 노드 유형에 ACL 적용
* 권한 제한

   * 예를 들어 속성을 쓸 필요가 있을 때만 권한을 부여하지 `jcr:write` 마십시오. 대신 `jcr:modifyProperties` 사용

## 서비스 사용자 및 매핑 {#service-users-and-mappings}

상기에 오류가 발생하면 Sling 7은 번들-사용자 매핑 및 두 개의 해당 API 방법을 구성할 수 있는 서비스 사용자 매핑 서비스를 제공합니다. ` [SlingRepository.loginService()](https://sling.apache.org/apidocs/sling7/org/apache/sling/jcr/api/SlingRepository.html#loginService-java.lang.String-java.lang.String-)` 구성된 사용자만의 권한을 가진 세션/리소스 확인자를 ` [ResourceResolverFactory.getServiceResourceResolver()](https://sling.apache.org/apidocs/sling7/org/apache/sling/api/resource/ResourceResolverFactory.html#getServiceResourceResolver-java.util.Map-)` 반환합니다. 이러한 메서드에는 다음과 같은 특성이 있습니다.

* 사용자에게 매핑 서비스를 허용합니다.
* 하위 서비스 사용자를 정의할 수 있습니다.
* 중앙 구성 지점은 다음과 같습니다. `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl`
* `service-id` = `service-name` [ &quot;:&quot; 하위 서비스 이름 ] 

* `service-id` is mapped to resource resolver and/or JCR repository user ID for authentication
* `service-name` 서비스를 제공하는 번들의 상징적인 이름입니다.

## 기타 Recommendations {#other-recommendations}

### admin-session을 서비스-사용자로 대체 {#replacing-the-admin-session-with-a-service-user}

서비스 사용자는 암호를 설정하지 않은 JCR 사용자이며 특정 작업을 수행하는 데 필요한 최소한의 권한 집합입니다. 암호를 설정하지 않으면 서비스 사용자와 로그인할 수 없습니다.

관리 세션을 사용하지 않는 방법은 서비스 사용자 세션으로 바꾸는 것입니다. 필요한 경우 여러 하위 서비스 사용자로 대체될 수도 있습니다.

관리 세션을 서비스 사용자로 교체하려면 다음 단계를 수행해야 합니다.

1. 최소 권한 원칙을 고려하여 서비스에 필요한 권한을 식별합니다.
1. 필요한 권한 설정으로 사용할 수 있는 사용자가 이미 있는지 확인합니다. 기존 사용자가 요구 사항에 맞지 않을 경우 새 시스템 서비스 사용자를 만듭니다. 새 서비스 사용자를 만들려면 RTC가 필요합니다. 경우에 따라 여러 하위 서비스 사용자(예: 쓰기 사용자 및 읽기 사용자)를 만들어 액세스를 구분하는 것이 적절합니다.
1. 사용자의 ACE를 설정하고 테스트합니다.
1. 서비스에 대한 `service-user` 매핑 및 `user/sub-users`

1. 번들에서 서비스 사용자 슬링 기능을 사용할 수 있도록 하십시오. 최신 버전으로 업데이트할 수 있습니다 `org.apache.sling.api`.

1. 코드 `admin-session` 의 코드를 `loginService` 또는 `getServiceResourceResolver` API로 바꿉니다.

## 새 서비스 사용자 만들기 {#creating-a-new-service-user}

AEM 서비스 사용자 목록의 사용자가 사용 사례에 적용할 수 없고 해당 RTC 문제가 승인되었음을 확인한 후 기본 컨텐츠에 새 사용자를 추가할 수 있습니다.

권장 방법은 https://&lt;server>:&lt;port>/crx/explorer/index.jsp에서 저장소 탐색기를 사용할 서비스 사용자를 만드는 *것입니다.*

목표는 컨텐츠 패키지 설치를 통해 사용자를 만들려면 필수 `jcr:uuid` 속성을 가져오는 것입니다.

다음 방법을 통해 서비스 사용자를 만들 수 있습니다.

1. https://&lt;서버>:&lt;포트>/crx/explorer/index.jsp의 저장소 탐색기 *로 이동*
1. 화면의 왼쪽 상단에 있는 **로그인** 링크를 눌러 관리자로 로그인합니다.
1. 그런 다음 시스템 사용자를 만들고 이름을 지정합니다. 사용자를 시스템 개체로 만들려면 중간 경로를 로 설정하고 필요 `system` 에 따라 선택적 하위 폴더를 추가하십시오.

   ![chlimage_1-102](assets/chlimage_1-102.png)

1. 시스템 사용자 노드가 다음과 같이 표시되는지 확인합니다.

   ![chlimage_1-103](assets/chlimage_1-103.png)

   >[!NOTE]
   >
   >서비스 사용자와 연관된 혼합 유형은 없습니다. 이는 시스템 사용자에 대한 액세스 제어 정책이 없음을 의미합니다.

번들의 컨텐츠에 해당 .content.xml을 추가할 때 를 설정한 `rep:authorizableId` 후 기본 유형이 올바른지 확인하십시오 `rep:SystemUser`. 다음과 같이 표시됩니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:rep="internal"
    jcr:primaryType="rep:SystemUser"
    jcr:uuid="4917dd68-a0c1-3021-b5b7-435d0044b0dd"
    rep:principalName="authentication-service"
    rep:authorizableId="authentication-service"/>
```

## ServiceUserMapper 구성에 구성 수정 추가 {#adding-a-configuration-amendment-to-the-serviceusermapper-configuration}

서비스의 매핑을 해당 시스템 사용자에게 추가하려면 서비스의 출하 시 구성을 생성해야 ` [ServiceUserMapper](https://sling.apache.org/apidocs/sling7/org/apache/sling/serviceusermapping/ServiceUserMapper.html)` 합니다. 이러한 모듈식 구성을 유지하려면 Sling [수정 메커니즘을 사용하여 제공할 수 있습니다](https://issues.apache.org/jira/browse/SLING-3578). 이러한 구성을 번들과 함께 설치하는 데 권장되는 방법은 Sling [Initial Content Loading을 사용하는 것입니다](https://sling.apache.org/documentation/bundles/content-loading-jcr-contentloader.html).

1. 번들의 src/main/resources 폴더 아래에 하위 폴더 SLING-INF/content 만들기
1. 이 폴더에서 org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.re정한-&lt;공장 구성에 대한 일부 고유한 이름>.xml 파일을 만듭니다(모든 하위 서비스 사용자 매핑 포함). 예:

1. 번들의 폴더 아래에 `SLING-INF/content` 폴더를 `src/main/resources` 만듭니다.
1. 이 폴더에서 모든 하위 서비스 사용자 매핑을 포함하여 공장 구성 `named org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-<a unique name for your factory configuration>.xml` 의 콘텐트가 포함된 파일을 만듭니다.

   일러스트레이션을 위해 다음 파일을 사용합니다 `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-com.adobe.granite.auth.saml.xml`.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <node>
       <primaryNodeType>sling:OsgiConfig</primaryNodeType>
       <property>
           <name>user.default</name>
           <value></value>
       </property>
       <property>
           <name>user.mapping</name>
           <values>
               <value>com.adobe.granite.auth.saml=authentication-service</value>
           </values>
       </property>
   </node>
   ```

1. 번들의 구성에 있는 Sling 초기 컨텐츠 `maven-bundle-plugin` 를 `pom.xml` 참조하십시오. 예:

   ```xml
   <Sling-Initial-Content>
      SLING-INF/content;path:=/libs/system/config;overwrite:=true;
   </Sling-Initial-Content>
   ```

1. 번들을 설치하고 공장 구성이 설치되어 있는지 확인합니다. 다음을 통해 이 작업을 수행할 수 있습니다.

   * 웹 콘솔(https://serverhost:serveraddress/system/console/configMgr)으로 *이동*
   * Apache **Sling Service User Mapper 서비스 개정안 검색**
   * 링크를 클릭하여 적절한 구성이 적절한지 확인합니다.

## 서비스에서 공유 세션 처리 {#dealing-with-shared-sessions-in-services}

호출은 종종 공유 세션과 함께 `loginAdministrative()` 나타납니다. 이러한 세션은 서비스 활성화에서 획득되며 서비스가 중단된 후에만 로그아웃됩니다. 이 방법은 일반적인 방법이지만 두 가지 문제로 이어집니다.

* **보안:** 이러한 관리 세션은 공유 세션에 바인딩되는 리소스 또는 기타 개체를 캐시하고 반환하는 데 사용됩니다. 나중에 호출 스택에서 이러한 개체는 더 높은 권한을 가진 세션이나 리소스 해결자에 맞게 조정될 수 있으며, 호출자에게 사용 중인 관리 세션이라는 것은 확실하지 않은 경우가 많습니다.
* **성능:** Oak 공유 세션에서 성능 문제가 발생할 수 있으며 현재 이 문제를 사용하지 않는 것이 좋습니다.

보안 위험에 대한 가장 확실한 해결책은 단순히 권한을 제한된 사용자 `loginAdministrative()` 에게 전화를 `loginService()` 대체하는 것입니다. 그러나 이는 잠재적인 성능 저하에 영향을 주지 않습니다. 세션과 연결되지 않은 개체에 요청된 모든 정보를 둘러싸는 것이 완화 가능입니다. 그런 다음 세션을 On-Demand로 생성(또는 제거)합니다.

권장되는 방법은 서비스의 API를 리팩터링하여 호출자가 세션의 생성/삭제를 제어하는 것입니다.

## JSP의 관리 세션 {#administrative-sessions-in-jsps}

연관된 서비스가 없으므로 JSP는 사용할 수 `loginService()`없습니다. 그러나 JSP의 관리 세션은 일반적으로 MVC 패러다임 위반의 신호입니다.

이 문제는 다음 두 가지 방법으로 수정할 수 있습니다.

1. 사용자 세션에 맞게 컨텐츠를 조작할 수 있도록 컨텐츠를 재구성합니다.
1. JSP에서 사용할 수 있는 API를 제공하는 서비스에 로직을 추출합니다.

첫 번째 방법이 선호된다.

## 처리 이벤트, 복제 프리프로세서 및 작업 {#processing-events-replication-preprocessors-and-jobs}

이벤트나 작업을 처리할 때, 그리고 일부 워크플로우에서는 이벤트를 트리거한 해당 세션이 대개 손실됩니다. 이로 인해 이벤트 핸들러와 작업 프로세서가 관리 세션을 사용하여 작업을 수행할 수 있습니다. 이 문제를 해결하기 위한 다양한 접근 방법이 있으며, 각각 장점과 단점을 가지고 있습니다.

1. 이벤트 페이로드에서 `user-id` 를 전달하고 가장을 사용합니다.

   **장점:** 간편한 사용

   **단점:** 여전히 `loginAdministrative()`사용 이미 인증된 요청을 다시 인증합니다.

1. 데이터에 액세스할 수 있는 서비스 사용자를 만들거나 재사용합니다.

   **장점:** 최신 디자인과 일관되게 최소한의 변화가 필요합니다.

   **단점:** 매우 강력한 서비스 사용자가 유연해야 하며 권한 에스컬레이션을 쉽게 야기할 수 있습니다. 보안 모델을 우회합니다.

1. 이벤트 페이로드에서 이벤트 일련화 `Subject` 를 전달하고 해당 주제를 `ResourceResolver` 기반으로 만듭니다. 한 가지 예는 JAAS를 `doAsPrivileged` 에 사용하는 `ResourceResolverFactory`것입니다.

   **장점:** 보안 측면에서 구현이 수월합니다. 재인증을 피하고 원래 권한으로 작동합니다. 관련 코드는 이벤트 소비자에게 투명하게 표시됩니다.

   **단점:** 리팩토링해야 합니다. 이벤트 소비자에게 관련된 보안 관련 코드가 투명하게 처리되면 문제가 발생할 수 있습니다.

세 번째 방법은 현재 기본 처리 방법입니다.

## 워크플로우 프로세스 {#workflow-processes}

워크플로우 프로세스 내에서 워크플로우를 트리거한 해당 사용자 세션이 일반적으로 손실됩니다. 이로 인해 작업을 수행하기 위해 관리 세션을 사용하는 워크플로우 프로세스가 발생합니다.

이러한 문제를 해결하기 위해 [처리 이벤트, 복제 프리프로세서 및 작업에](/help/sites-administering/security-service-users.md#processing-events-replication-preprocessors-and-jobs) 언급된 것과 동일한 접근 방식을 사용하는 것이 좋습니다.

## 슬링 POST 프로세서 및 삭제된 페이지 {#sling-post-processors-and-deleted-pages}

슬링 POST 프로세서 구현에 사용되는 관리 세션은 몇 가지입니다. 일반적으로 관리 세션은 처리 중인 POST 내에서 삭제 보류 중인 노드에 액세스하는 데 사용됩니다. 따라서 요청 세션을 통해 더 이상 사용할 수 없습니다. 삭제 대기 중인 노드는 액세스할 수 없는 메타데이터를 공개하기 위해 액세스할 수 있습니다.
