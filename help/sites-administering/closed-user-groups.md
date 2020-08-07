---
title: AEM에서 닫힌 사용자 그룹
seo-title: AEM에서 닫힌 사용자 그룹
description: AEM의 닫힌 사용자 그룹에 대해 알아봅니다.
seo-description: AEM의 닫힌 사용자 그룹에 대해 알아봅니다.
uuid: a65ed163-fdec-45f3-adf9-984d36f4eb73
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: a2bd7045-970f-4245-ad5d-a272a654df0a
translation-type: tm+mt
source-git-commit: 7dc90299b7a0e5166c30702323f1678353fe39b3
workflow-type: tm+mt
source-wordcount: '6889'
ht-degree: 0%

---


# AEM에서 닫힌 사용자 그룹{#closed-user-groups-in-aem}

## 소개 {#introduction}

AEM 6.3 이후 기존 구현과 관련된 성능, 확장성 및 보안 문제를 해결하기 위한 새로운 폐쇄 사용자 그룹 구현이 있습니다.

>[!NOTE]
>
>단순성을 위해 이 설명서 전체에서 CUG 약어가 사용됩니다.

새로운 구현의 목표는 기존 버전의 문제와 디자인 제한 사항을 해결하는 동시에 필요한 기존 기능을 해결하는 것입니다. 그 결과 다음과 같은 특성을 갖는 새로운 CUG 디자인이 생성됩니다.

* 개별적으로 또는 함께 사용할 수 있는 인증 및 인증 요소의 명확한 분리
* 다른 액세스 제어 설정 및 권한 요구 사항에 영향을 주지 않고 구성된 CUG 트리에서 제한된 읽기 액세스를 반영하는 전용 인증 모델
* 일반적으로 작성 인스턴스에 필요한 제한된 읽기 액세스 제어 설정과 일반적으로 게시 시에만 필요한 권한 평가 간의 분리;
* 권한 에스컬레이션 없이 제한된 읽기 액세스 편집
* 인증 요구 사항을 표시하는 전용 노드 유형 확장
* 인증 요구 사항과 연관된 선택적 로그인 경로.

### 새 사용자 지정 사용자 그룹 구현 {#the-new-custom-user-group-implementation}

AEM 컨텍스트에서 알려진 CUG는 다음 단계로 구성됩니다.

* 보호되어야 하는 트리에서 읽기 액세스를 제한하고 주어진 CUG 인스턴스로 나열되거나 CUG 평가에서 모두 제외된 주체를 읽기 전용으로 허용합니다. 이를 **인증** 요소라고 합니다.
* 지정된 트리에 인증을 적용하고 선택적으로 이후에 제외되는 해당 트리에 대한 전용 로그인 페이지를 지정합니다. 이를 **인증** 요소라고 합니다.

새로운 구현은 인증과 인증 요소 사이에 선을 긋도록 설계되었습니다. AEM 6.3에서는 인증 요구 사항을 명시적으로 추가하지 않고 읽기 액세스를 제한할 수 있습니다. 예를 들어, 지정된 인스턴스에 인증이 모두 필요하거나 지정된 트리가 이미 인증이 필요한 하위 트리에 있는 경우

또한, 유효한 권한 설정을 변경하지 않고 지정된 트리를 인증 요구 사항으로 표시할 수 있습니다. 조합 및 결과는 CUG 정책 [결합 및 인증 요구 사항 섹션에](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) 나열되어 있습니다.

## 개요 {#overview}

### 인증:읽기 액세스 제한 {#authorization-restricting-read-access}

CUG의 주요 기능은 선택한 주도자를 제외한 모든 사용자에 대해 컨텐츠 저장소의 지정된 트리에서 읽기 액세스를 제한하는 것입니다. 새로운 구현은 기본 액세스 제어 컨텐츠를 신속하게 조작하는 대신 CUG를 나타내는 전용 유형의 액세스 제어 정책을 정의하여 다른 접근 방식을 취합니다.

#### CUG에 대한 액세스 제어 정책 {#access-control-policy-for-cug}

이 새로운 유형의 정책은 다음과 같은 특성을 갖고 있습니다.

* org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy(Apache Jackrabbit API에 의해 정의됨)의 액세스 제어 정책;
* PrincipalSetPolicy는 주도자 집합을 수정할 수 있는 권한을 부여합니다.
* 부여된 권한 및 정책의 범위는 구현 세부 사항입니다.

CUG를 나타내는 데 사용되는 PrincipalSetPolicy 구현은 다음을 정의합니다.

* CUG 정책은 일반 JCR 항목에 대한 읽기 액세스 권한만 부여합니다(예: 액세스 제어 컨텐츠는 제외됨).
* 범위는 CUG 정책을 포함하는 액세스 제어 노드에 의해 정의됩니다.
* CUG 정책은 중첩될 수 있고, 중첩된 CUG는 &#39;parent&#39; CUG의 기본 집합을 상속하지 않고 새 CUG를 시작합니다.
* 평가가 활성화된 경우 정책의 효과는 전체 하위 트리에서 다음 중첩 CUG로 상속됩니다.

이러한 CUG 정책은 oak-authorization-cug라는 별도의 인증 모듈을 통해 AEM 인스턴스에 배포됩니다. 이 모듈에는 자체 액세스 제어 관리 및 권한 평가가 포함되어 있습니다. 즉, 기본 AEM 설정은 여러 인증 메커니즘을 결합하는 Oak 컨텐츠 저장소 구성을 제공합니다. 자세한 내용은 Apache Oak 설명서 [의 이 페이지를 참조하십시오](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

이 복합 설정에서 새 CUG는 대상 노드에 첨부된 기존 액세스 제어 컨텐츠를 대체하지 않지만, 원래 액세스 제어에 영향을 주지 않고 나중에 제거할 수 있는 보완책으로 설계되었습니다. 기본적으로 AEM에서는 액세스 제어 목록이 됩니다.

이전 구현과 달리 새로운 CUG 정책은 항상 액세스 제어 컨텐츠로 인식되고 처리됩니다. 이는 JCR 액세스 제어 관리 API를 사용하여 만들고 편집함을 의미합니다. 자세한 내용은 CUG 정책 [관리](#managing-cug-policies) 섹션을 참조하십시오.

#### CUG 정책의 허가평가 {#permission-evaluation-of-cug-policies}

CUG에 대한 전용 액세스 제어 관리 외에 새로운 인증 모델은 정책에 대한 허용 평가를 조건부로 허용할 수 있도록 합니다. 이렇게 하면 스테이징 환경에서 CUG 정책을 설정할 수 있으며 프로덕션 환경에 복제한 후에는 효과적인 권한을 평가만 할 수 있습니다.

CUG 정책에 대한 권한 평가 및 기본 또는 추가 인증 모델과의 상호 작용은 Apache Jackrabbit Oak에서 다중 인증 메커니즘을 위해 설계된 패턴을 따릅니다.모든 모델에서 액세스 권한을 부여하는 경우에만 주어진 권한 세트가 부여됩니다. 자세한 내용은 [이 페이지를](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) 참조하십시오.

CUG 정책을 처리 및 평가하기 위해 설계된 인증 모델과 연관된 권한 평가에 다음 특성이 적용됩니다.

* 일반 노드 및 속성에 대한 읽기 권한만 처리하지만 액세스 제어 컨텐츠를 읽지 않습니다.
* 보호된 JCR 컨텐츠를 수정하는 데 필요한 쓰기 권한이나 권한(액세스 제어, 노드 유형 정보, 버전 관리, 잠금 또는 사용자 관리)은 처리되지 않습니다.이러한 권한은 CUG 정책에 영향을 받지 않으며 관련 인증 모델로 평가되지 않습니다. 이러한 권한 부여 여부는 보안 설정에 구성된 다른 모델에 따라 달라집니다.

단일 CUG 정책이 권한 평가에 미치는 영향은 다음과 같이 요약될 수 있습니다.

* 정책에 명시된 제외된 주도자나 주도자를 포함하는 항목을 제외한 모든 사용자에 대해 읽기 액세스가 거부됩니다.
* 정책은 정책 및 해당 속성을 포함하는 액세스 제어 노드에 적용됩니다.
* 이 효과는 추가적으로 계층 아래로 상속됩니다. 즉, 액세스 제어 노드에 의해 정의된 항목 트리
* 그러나 액세스 제어 노드의 형제나 조상은 영향을 받지 않습니다.
* 지정된 CUG의 상속은 중첩된 CUG에서 중지됩니다.

#### 우수 사례 {#best-practices}

CUG를 통해 제한된 읽기 액세스를 정의하기 위한 다음 우수 사례를 고려해야 합니다.

* CUG의 요구 사항이 읽기 액세스 또는 인증 요구 사항을 제한하는지 여부를 신중하게 결정할 수 있습니다. 후자의 경우 또는 둘 다 필요할 경우, 인증 요구 사항에 대한 자세한 내용은 우수 사례 섹션을 참조하십시오
* 위협 경계를 식별하고 인증된 액세스와 관련된 데이터 및 역할의 민감도를 명확하게 파악하기 위해 보호해야 하는 데이터 또는 컨텐츠에 대한 위협 모델을 생성합니다.
* 일반적인 인증 관련 측면과 모범 사례를 고려하여 저장소 컨텐츠와 CUG를 모델링합니다.

   * 주어진 주체가 주어진 저장소 항목을 읽을 수 있도록 허용하는 설정 허여에 배포된 다른 모듈의 평가 및 CUG가 부여된 경우에만 읽기 권한이 부여됩니다
   * 다른 인증 모듈로 읽기 액세스가 이미 제한된 중복 CUG를 만들지 마십시오
   * 중첩된 CUG가 과도하게 필요한 경우 컨텐츠 디자인에서 문제를 잠재적으로 강조 표시할 수 있습니다
   * CUG에 대한 매우 과도한 요구(예: 모든 단일 페이지)는 애플리케이션과 컨텐츠의 특정 보안 요구 사항에 맞게 잠재적으로 더 적합한 사용자 정의 인증 모델이 필요하다는 것을 나타낼 수 있습니다.

* 최적화된 성능을 위해 CUG 정책에 지원되는 경로를 저장소의 일부 트리로 제한합니다. 예를 들어 AEM 6.3 이후 기본값으로 제공된 /content 노드 아래의 CUG만 허용합니다.
* CUG 정책은 소규모 주도자에게 읽기 권한을 부여하도록 고안되었습니다. 수많은 주도자의 필요성이 컨텐츠 또는 애플리케이션 디자인의 문제점을 강조할 수 있으므로 재고려해야 합니다.

### 인증:인증 요구 사항 정의 {#authentication-defining-the-auth-requirement}

CUG 기능의 인증 관련 부분을 사용하면 인증이 필요한 트리를 표시하고 선택적으로 전용 로그인 페이지를 지정할 수 있습니다. 이전 버전에 따라 새 구현에서는 컨텐츠 저장소에서 인증이 필요한 트리를 표시할 수 있으며, 요구 사항을 최종적으로 적용하고 로그인 리소스로 리디렉션할 `Sling org.apache.sling.api.auth.Authenticator`책임이 있는 사람과의 동기화를 조건부로 활성화할 수 있습니다.

이러한 요구 사항은 등록 속성을 제공하는 OSGi 서비스를 통해 인증자에게 `sling.auth.requirements` 등록됩니다. 그런 다음 이러한 속성을 사용하여 인증 요구 사항을 동적으로 확장합니다. 자세한 내용은 Sling 설명서를 [참조하십시오](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS).

#### 전용 혼합 유형으로 인증 요구 사항 정의 {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

보안상의 이유로 새 구현은 잔존 JCR 속성의 사용을 로그인 경로에 대해 STRING 유형의 단일 선택적 속성을 정의하는 전용 mixin 유형 `granite:AuthenticationRequired`으로 대체합니다 `granite:loginPath`. 이 혼합 유형과 관련된 컨텐츠 변경 사항만 Apache Sling Authenticator에 등록된 요구 사항을 업데이트합니다. 수정은 일시적 수정을 지속 시 추적하므로 `javax.jcr.Session.save()` 호출이 유효해야 합니다.

속성에 대해서도 `granite:loginPath` 마찬가지입니다. 인증 요구 사항 관련 믹싱 유형으로 정의된 경우에만 적용됩니다. 구조화되지 않은 JCR 노드에서 이 이름을 가진 잔여속성을 추가하면 원하는 효과가 나타나지 않으며 OSGi 등록을 업데이트하는 핸들러에 의해 속성이 무시됩니다.

>[!NOTE]
>
>로그인 경로 속성 설정은 선택 사항이며, 인증이 필요한 트리가 기본값으로 되돌아갈 수 없거나 상속된 로그인 페이지로 돌아올 수 없는 경우에만 필요합니다. 아래의 [로그인 경로 평가를](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path) 참조하십시오.

#### Sling 인증자를 사용하여 인증 요구 사항 및 로그인 경로 등록 {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

이러한 유형의 인증 요구 사항은 특정 실행 모드 및 컨텐츠 저장소 내의 작은 트리 하위 세트로 제한되어야 하므로 요구 사항 혼합 유형과 로그인 경로 속성을 추적하는 것은 조건적이며 지원되는 경로를 정의하는 해당 구성에 바인딩됩니다(아래 구성 옵션 참조). 따라서 지원되는 경로 범위 내의 변경 사항만 OSGi 등록으로 업데이트되며, 다른 부분에서는 혼합 유형과 속성이 모두 무시됩니다.

이제 기본 AEM 설정은 작성자 실행 모드에서 믹스를 설정할 수 있도록 허용하여 이 구성을 사용합니다. 그러나 게시 인스턴스에 복제하는 경우에만 이 구성을 적용할 수 있습니다. Sling이 인증 요구 사항을 실행하는 방법에 대한 자세한 내용은 [이 페이지를](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) 참조하십시오.

구성된 지원 경로 내에 `granite:AuthenticationRequired` mixin 유형을 추가하면 해당 속성이 포함된 새로운 추가 항목이 포함된 책임 처리기의 OSGi 등록이 `sling.auth.requirements` 업데이트됩니다. 지정된 인증 요구 사항이 선택적 `granite:loginPath` 속성을 지정하는 경우 인증 요구 사항에서 제외되기 위해 값은 인증자에게 &#39;-&#39; 접두사를 추가하여 추가됩니다.

#### 인증 요구 사항 평가 및 상속 {#evaluation-and-inheritance-of-the-authentication-requirement}

Apache Sling 인증 요구 사항은 페이지 또는 노드 계층 구조를 통해 상속됩니다. 순위 및 우선 순위와 같은 인증 요구 사항에 대한 상속 및 평가에 대한 자세한 내용은 구현 세부 사항으로 간주되며 이 문서에 문서화되지 않습니다.

#### 로그인 경로 평가 {#evaluation-of-login-path}

로그인 경로 평가 및 인증 시 해당 리소스로 리디렉션되는 리디렉션은 현재 기본적으로 AEM으로 구성된 Apache Sling AuthenticationHandler인 Adobe의 구현 세부 정보입니다. `com.day.cq.auth.impl.LoginSelectorHandler`

이 핸들러를 호출하면 사용자가 리디렉션될 매핑 로그인 페이지를 확인할 수 있습니다. `AuthenticationHandler.requestCredentials` 여기에는 다음 단계가 포함됩니다.

* 리디렉션의 이유로 만료된 암호와 일반 로그인의 필요성을 구별합니다.
* 정기적으로 로그인하는 경우 다음 순서로 로그인 경로를 얻을 수 있는지 테스트합니다.

   * LoginPathProvider에서 새 `com.adobe.granite.auth.requirement.impl.RequirementService`
   * 오래된 CUG 구현에서,
   * 로그인 페이지 매핑에서 `LoginSelectorHandler`
   * 마지막으로, 에 정의된 기본 로그인 페이지로 폴백합니다 `LoginSelectorHandler`.

* 위에 나열된 호출을 통해 유효한 로그인 경로를 가져오면 사용자의 요청이 해당 페이지로 리디렉션됩니다.

이 문서의 대상은 내부 `LoginPathProvider` 인터페이스에 표시된 로그인 경로 평가입니다. AEM 6.3부터 제공된 구현은 다음과 같이 작동합니다.

* 로그인 경로 등록은 만료된 암호 구분과 리디렉션의 이유로 정기적인 로그인이 필요한 경우에 따라 다릅니다
* 정기적으로 로그인하는 경우 다음 순서로 로그인 경로를 얻을 수 있는지 테스트합니다.

   * 새 `LoginPathProvider` 에 의해 구현된 `com.adobe.granite.auth.requirement.impl.RequirementService`대로
   * 오래된 CUG 구현에서,
   * 을 사용하여 정의된 로그인 페이지 매핑에서 `LoginSelectorHandler`,
   * 마지막으로 에 정의된 기본 로그인 페이지로 폴백합니다 `LoginSelectorHandler`.

* 위에 나열된 호출을 통해 유효한 로그인 경로를 가져오면 사용자의 요청이 해당 페이지로 리디렉션됩니다.

[ `LoginPathProvider` MOCK] The new auth-requirement support in Granite(화강암)의 새 인증 요구 사항이 구현되면 속성이 정의한 대로 로그인 경로를 노출하고 위에서 설명한 대로 `granite:loginPath` 혼합 유형으로 정의됩니다. 로그인 경로 및 속성 값 자체를 포함하는 리소스 경로 매핑은 메모리에 저장되며 계층 구조의 다른 노드에 적합한 로그인 경로를 찾기 위해 평가됩니다.

>[!NOTE]
>
>평가는 구성된 지원 경로에 있는 리소스와 연결된 요청에 대해서만 수행됩니다. 다른 요청의 경우 로그인 경로를 결정하는 다른 방법이 평가됩니다.

#### 우수 사례 {#best-practices-1}

인증 요구 사항을 정의할 때는 다음 우수 사례를 고려해야 합니다.

* 중첩 인증 요구 사항 방지:트리 시작 시 단일 인증 요구 사항 마커를 배치해도 충분하며 대상 노드에서 정의한 전체 하위 트리에 상속됩니다. 해당 트리 내의 추가 인증 요구 사항은 중복으로 간주되어야 하며 Apache Sling 내의 인증 요구 사항을 평가하는 동안 성능 문제가 발생할 수 있습니다. 인증 및 인증 관련 CUG 영역이 분리되어 있으면 전체 트리에 대한 인증을 적용하는 동시에 CUG 또는 기타 정책 유형의 읽기 액세스를 제한할 수 있습니다.
* 인증 요구 사항이 중첩된 하위 트리를 다시 제외하지 않아도 전체 트리에 적용되는 것과 같은 모델 리포지토리 컨텐츠.
* 중복 로그인 경로를 지정하고 이후에 등록하지 않으려면:

   * 상속을 사용하고 중첩된 로그인 경로를 정의하지 마십시오.
   * 선택적 로그인 경로를 기본값 또는 상속된 값에 해당하는 값으로 설정하지 마십시오.
   * 응용 프로그램 개발자는 응용 프로그램과 연관된 전역 로그인 경로 구성(기본 및 매핑 모두)에서 구성해야 하는 로그인 경로를 식별해야 합니다 `LoginSelectorHandler`.

## 저장소의 표현 {#representation-in-the-repository}

### 저장소의 CUG 정책 표현 {#cug-policy-representation-in-the-repository}

Oak 설명서는 새로운 CUG 정책이 저장소 컨텐츠에 어떻게 반영되는지 설명합니다. 자세한 내용은 [이 페이지를 참조하십시오](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository).

### 저장소의 인증 요구 사항 {#authentication-requirement-in-the-repository}

별도의 인증 요구 사항에 대한 필요는 대상 노드에 전용 혼합 노드 유형을 배치하여 저장소 컨텐츠에 반영됩니다. mixin 유형은 대상 노드에 의해 정의된 트리의 전용 로그인 페이지를 지정하는 선택적 속성을 정의합니다.

로그인 경로와 연관된 페이지는 해당 트리 내부 또는 외부에 있을 수 있습니다. 인증 요구 사항에서 제외됩니다.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## CUG 정책 및 인증 요구 사항 관리 {#managing-cug-policies-and-authentication-requirement}

### CUG 정책 관리 {#managing-cug-policies}

CUG에 대한 읽기 액세스를 제한하는 새로운 유형의 액세스 제어 정책은 JCR 액세스 제어 관리 API를 사용하여 관리되며 [JCR 2.0 사양에 설명된 메커니즘을 따릅니다](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html).

#### 새 CUG 정책 설정 {#set-a-new-cug-policy}

이전에 CUG가 설정되지 않은 노드에서 새 CUG 정책을 적용하는 코드 이전에 `getApplicablePolicies` 설정되지 않은 새 정책만 반환됩니다. 결국 정책을 다시 기록해야 하고 변경 사항을 유지해야 한다.

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

AccessControlPolicyIterator it = acMgr.getApplicablePolicies(path);
while (it.hasNext()) {
        AccessControlPolicy policy = it.nextAccessControlPolicy();
        if (policy instanceof PrincipalSetPolicy) {
           cugPolicy = (PrincipalSetPolicy) policy;
           break;
        }
}

if (cugPolicy == null) {
   log.debug("no applicable policy"); // path not supported or no applicable policy (e.g.
                                                   // the policy was set before)
   return;
}

cugPolicy.addPrincipals(toAdd1, toAdd2);
cugPolicy.removePrincipals(toRemove));

acMgr.setPolicy(path, cugPolicy); // as of this step the policy can be edited/removed
session.save();
```

#### 기존 CUG 정책 편집 {#edit-an-existing-cug-policy}

기존 CUG 정책을 편집하려면 다음 단계가 필요합니다. 수정된 정책은 다시 작성해야 하며 변경 사항은 계속 사용해야 합니다 `javax.jcr.Session.save()`.

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
     if (policy instanceof PrincipalSetPolicy) {
        cugPolicy = (PrincipalSetPolicy) policy;
        break;
     }
}

if (cugPolicy == null) {
   log.debug("no policy to edit"); // path not supported or policy not set before
   return;
}

if (cugPolicy.addPrincipals(toAdd1, toAdd2) || cugPolicy.removePrincipals(toRemove)) {
   acMgr.setPolicy(path, cugPolicy);
   session.save();
} else {
     log.debug("cug policy not modified");
}
```

### 효과적인 CUG 정책 검색 {#retrieve-effective-cug-policies}

JCR 액세스 제어 관리는 지정된 경로에서 적용되는 정책을 검색하기 위한 최상의 작업 방법을 정의합니다. CUG 정책 평가는 조건적이며 활성화될 해당 구성에 따라 달라지기 때문에 주어진 CUG 정책이 특정 설치 환경에서 효과를 발휘하는지 확인하는 편리한 전화 `getEffectivePolicies` 를 사용하면 됩니다.

>[!NOTE]
>
>해당 경로가 이미 기존 CUG의 일부인지 확인하기 위해 계층 `getEffectivePolicies` 을 따라 표시되는 및 다음 코드 예제 간의 차이점을 참고하십시오.

```java
String path = [...] // needs to be a supported, absolute path

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

// log an debug message of all CUG policies that take effect at the given path
// there could be zero, one or many (creating nested CUGs is possible)
for (AccessControlPolicy policy : acMgr.getEffectivePolicies(path) {
     if (policy instanceof PrincipalSetPolicy) {
        String policyPath = "-";
        if (policy instanceof JackrabbitAccessControlPolicy) {
           policyPath = ((JackrabbitAccessControlPolicy) policy).getPath();
        }
        log.debug("Found effective CUG for path '{}' at '{}', path, policyPath);
     }
}
```

#### 상속된 CUG 정책 검색 {#retrieve-inherited-cug-policies}

적용 여부에 관계없이 지정된 경로에 정의된 모든 중첩 CUG를 찾습니다. 자세한 내용은 구성 옵션 [섹션을](/help/sites-administering/closed-user-groups.md#configuration-options) 참조하십시오.

```java
String path = [...]

List<AccessControlPolicy> cugPolicies = new ArrayList<AccessControlPolicy>();
while (isSupportedPath(path)) {
     for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
         if (policy instanceof PrincipalSetPolicy) {
            cugPolicies.add(policy);
         }
      }
      path = (PathUtils.denotesRoot(path)) ? null : PathUtils.getAncestorPath(path, 1);
}
```

#### Pincipal별 CUG 정책 관리 {#managing-cug-policies-by-pincipal}

주체별 액세스 제어 정책을 편집할 수 `JackrabbitAccessControlManager` 있도록 정의된 확장 기능은 CUG 정책에 의해 항상 모든 주도자에게 영향을 주듯이 CUG 액세스 제어 관리를 통해 구현되지 않습니다.해당 목록에 `PrincipalSetPolicy` 나열된 모든 주체가 대상 노드에 의해 정의된 트리의 컨텐츠를 읽을 수 없는 반면 다른 모든 주체는 읽기 액세스가 부여됩니다.

해당 메서드는 항상 빈 정책 배열을 반환하지만 예외를 throw하지 않습니다.

### 인증 요구 사항 관리 {#managing-the-authentication-requirement}

대상 노드의 유효한 노드 유형을 변경하여 새로운 인증 요구 사항을 생성, 수정 또는 제거할 수 있습니다. 그런 다음 일반 JCR API를 사용하여 선택적 로그인 경로 속성을 작성할 수 있습니다.

>[!NOTE]
>
>위에 언급된 특정 대상 노드에 대한 수정 사항은 Apache Sling Authenticator에 반영됩니다. 단, 대상 `RequirementHandler` 이 구성되어 있고 지원되는 경로에 의해 정의된 트리에 포함됩니다(구성 옵션 섹션 참조).
>
>자세한 내용은 [Mixin 노드 유형 지정](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3 Mixin Node Types) 및 노드 [추가 및 속성 설정](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.4 노드 추가 및 속성 설정)을 참조하십시오.

#### 새 인증 요구 사항 추가 {#adding-a-new-auth-requirement}

새 인증 요구 사항을 만드는 단계는 아래에 자세히 설명되어 있습니다. 대상 노드를 포함하는 트리에 대해 요구 사항이 구성된 경우에만 Apache Sling Authenticator `RequirementHandler` 에 등록됩니다.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### 로그인 경로를 사용하여 새 인증 요구 사항 추가 {#add-a-new-auth-requirement-with-login-path}

로그인 경로를 포함하여 새 인증 요구 사항을 만드는 절차. 대상 노드가 들어 있는 트리에 대해 구성된 경우 로그인 경로에 대한 요구 사항 및 제외는 Apache Sling Authenticator에만 `RequirementHandler` 등록됩니다.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### 기존 로그인 경로 수정 {#modify-an-existing-login-path}

기존 로그인 경로를 변경하는 단계는 아래에 자세히 설명되어 있습니다. 수정 사항은 대상 노드를 포함하는 트리에 대해 구성된 경우에만 Apache Sling Authenticator `RequirementHandler` 에 등록됩니다. 이전 로그인 경로 값이 등록에서 제거됩니다. 대상 노드와 연관된 인증 요구 사항은 이 수정으로 영향을 받지 않습니다.

```java
Node targetNode = [...]
String newLoginPath = [...] // STRING property

if (targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", newLoginPath);
   session.save();
} else {
     log.debug("cannot modify login path property; mixin type missing");
}
```

#### 기존 로그인 경로 제거 {#remove-an-existing-login-path}

기존 로그인 경로를 제거하는 절차. 대상 노드가 들어 있는 트리에 대해 로그인 경로 항목이 구성된 경우 Apache Sling Authenticator에서 `RequirementHandler` 로그인 경로 항목이 등록되지 않습니다. 대상 노드와 연관된 인증 요구 사항은 영향을 받지 않습니다.

```java
Node targetNode = [...]

if (targetNode.hasProperty("granite:loginPath") &&
   targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", null);
   session.save();
} else {
     log.debug("cannot remove login path property; mixin type missing");
}
```

또는 아래 방법을 사용하여 동일한 목적을 달성할 수 있습니다.

```java
String path = [...] // absolute path to target node

String propertyPath = PathUtils.concat(path, "granite:loginPath");
if (session.propertyExists(propertyPath)) {
    session.getProperty(propertyPath).remove();
    // or: session.removeItem(propertyPath);
    session.save();
}
```

#### 인증 요구 사항 제거 {#remove-an-auth-requirement}

기존 인증 요구 사항을 제거하는 절차 대상 노드가 들어 있는 트리에 대해 구성된 경우에만 Apache Sling Authenticator에서 요구 사항 `RequirementHandler` 이 등록되지 않습니다.

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### 유효 인증 요구 사항 검색 {#retrieve-effective-auth-requirements}

Apache Sling Authenticator에 등록된 모든 효과적인 인증 요구 사항을 읽을 수 있는 전용 공개 API는 없습니다. 하지만 이 목록은 &quot; `https://<serveraddress>:<serverport>/system/console/slingauth` 인증 요구 사항 구성&#x200B;**&quot; 섹션**&#x200B;아래의 시스템 콘솔에표시됩니다.

다음 이미지는 데모 컨텐츠가 있는 AEM 게시 인스턴스의 인증 요구 사항을 보여줍니다. 커뮤니티 페이지의 강조 표시된 경로는 이 문서에 설명된 구현에 의해 추가된 요구 사항이 Apache Sling 인증자에 어떻게 반영되는지 보여줍니다.

>[!NOTE]
>
>이 예에서 선택적 로그인 경로 속성이 설정되지 않았습니다. 따라서 인증자에게 두 번째 항목이 등록되지 않았습니다.

![chlimage_1-62](assets/chlimage_1-62.jpeg)

#### 유효 로그인 경로 검색 {#retrieve-the-effective-login-path}

현재 인증이 필요한 리소스에 익명으로 액세스하는 경우 적용되는 로그인 경로를 검색할 공개 API가 없습니다. 로그인 경로가 검색되는 방식에 대한 구현 세부 사항은 로그인 경로 평가 섹션을 참조하십시오.

그러나 이 기능에 정의된 로그인 경로 외에도 로그인으로 리디렉션되는 방법을 지정하는 다른 방법이 있습니다. 이 방법은 컨텐츠 모델 및 지정된 AEM 설치의 인증 요구 사항을 고려해야 합니다.

#### 상속된 인증 요구 사항 검색 {#retrieve-the-inherited-auth-requirement}

로그인 경로와 마찬가지로 컨텐츠에 정의된 상속된 인증 요구 사항을 검색할 공개 API도 없습니다. 다음 샘플에서는 해당 계층에 정의된 모든 인증 요구 사항을 적용 여부와 관계없이 나열하는 방법을 보여 줍니다. 자세한 내용은 구성 [옵션을 참조하십시오](/help/sites-administering/closed-user-groups.md#configuration-options).

>[!NOTE]
>
>인증 요구 사항과 로그인 경로에 상속 메커니즘에 의존하여 중첩된 인증 요구 사항을 만들지 않는 것이 좋습니다.
>
>자세한 내용은 인증 요구 사항 [의 평가 및 상속, 로그인 경로](#evaluation-and-inheritance-of-the-authentication-requirement)평가 및 [우수 사례](#evaluation-of-login-path) 를 [참조하십시오](#best-practices).

```java
String path = [...]
Node node = session.getNode(path);

Map<String, String> authRequirements = new ArrayList<String, String>();
while (isSupported(node)) {
     if (node.isNodeType("granite:AuthenticationRequired")) {
         String loginPath = (node.hasProperty("granite:loginPath") ?
                                     node.getProperty("granite:loginPath").getString() :
                                     "";
        authRequirements.put(node.getPath(), loginPath);
        node = node.getParent();
     }
}
```

### CUG 정책과 인증 요구 사항 결합 {#combining-cug-policies-and-the-authentication-requirement}

다음 표에는 구성을 통해 두 모듈을 모두 활성화한 AEM 인스턴스의 유효한 CUG 정책 조합과 인증 요구 사항이 나와 있습니다.

| **인증 필요** | **로그인 경로** | **제한된 읽기 액세스** | **예상 효과** |
|---|---|---|---|
| 예 | 예 | 예 | 유효한 권한 평가가 액세스 권한을 부여하는 경우에만 CUG 정책에 표시된 하위 트리를 볼 수 있습니다. 인증되지 않은 사용자는 지정된 로그인 페이지로 리디렉션됩니다. |
| 예 | 아니오 | 예 | 유효한 권한 평가가 액세스 권한을 부여하는 경우에만 CUG 정책에 표시된 하위 트리를 볼 수 있습니다. 인증되지 않은 사용자는 상속된 기본 로그인 페이지로 리디렉션됩니다. |
| 예 | 예 | 아니오 | 인증되지 않은 사용자는 지정된 로그인 페이지로 리디렉션됩니다. 인증 요구 사항으로 표시된 트리를 볼 수 있는지 여부는 해당 하위 트리에 포함된 개별 항목의 유효 권한에 따라 다릅니다. 읽기 액세스를 제한하는 전용 CUG가 없습니다. |
| 예 | 아니오 | 아니오 | 인증되지 않은 사용자는 상속된 기본 로그인 페이지로 리디렉션됩니다. 인증 요구 사항으로 표시된 트리를 볼 수 있는지 여부는 해당 하위 트리에 포함된 개별 항목의 유효 권한에 따라 다릅니다. 읽기 액세스를 제한하는 전용 CUG가 없습니다. |
| 아니오 | 아니오 | 예 | 인증된 지정된 사용자 또는 인증되지 않은 사용자는 효과적인 권한 평가를 통해 액세스 권한을 부여하는 경우에만 CUG 정책에 표시된 하위 트리를 볼 수 있습니다. 인증되지 않은 사용자는 동일하게 취급되고 로그인으로 리디렉션되지 않습니다. |

>[!NOTE]
>
>&#39;Authentication Requirement&#39; = No 및 &#39;Login Path&#39; = Yes의 조합이 위에 표시되지 않습니다. &#39;Login Path&#39;는 Auth-Requirement와 연결된 선택적 속성입니다. 정의된 mixin 유형을 추가하지 않고 해당 이름으로 JCR 속성을 지정하면 아무런 효과가 없으며 해당 처리기에서 무시됩니다.

## OSGi 구성 요소 및 구성 {#osgi-components-and-configuration}

이 섹션에서는 OSGi 구성 요소 및 새로운 CUG 구현과 함께 도입된 개별 구성 옵션에 대한 개요를 제공합니다.

이전 및 새 구현 간의 구성 옵션에 대한 포괄적인 매핑은 CUG 매핑 설명서를 참조하십시오.

### 인증:설정 및 구성 {#authorization-setup-and-configuration}

새로운 인증 관련 부분은 AEM 기본 설치의 일부인 **Oak CUG 인증** 번들( `org.apache.jackrabbit.oak-authorization-cug`)에 포함되어 있습니다. 번들은 읽기 액세스를 관리하는 추가 방법으로 배포하려는 분리된 인증 모델을 정의합니다.

#### CUG 인증 설정 {#setting-up-cug-authorization}

CUG 인증 설정은 [관련 Apache 설명서에 자세히 설명되어 있습니다](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability). 기본적으로 AEM에는 모든 실행 모드에 배포되는 CUG 인증이 있습니다. 단계별 지침은 다른 인증 설정이 필요한 설치에서 CUG 인증을 비활성화하는 데 사용할 수도 있습니다.

#### 레퍼러 필터 구성 {#configuring-the-referrer-filter}

또한 AEM에 액세스하는 데 [사용될 수 있는 모든 호스트 이름으로 Sling Referrer](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) 필터를 구성해야 합니다.예를 들어, CDN, 부하 균형 조정기 등을 통해 제공됩니다.

레퍼러 필터가 구성되지 않은 경우 사용자가 CUG 사이트에 로그인을 시도하면 다음과 유사한 오류가 표시됩니다.

```shell
31.01.2017 13:49:42.321 *INFO* [qtp1263731568-346] org.apache.sling.security.impl.ReferrerFilter Rejected referrer header for POST request to /libs/granite/core/content/login.html/j_security_check : https://hostname/libs/granite/core/content/login.html?resource=%2Fcontent%2Fgeometrixx%2Fen%2Ftest-site%2Ftest-page.html&$$login$$=%24%24login%24%24&j_reason=unknown&j_reason_code=unknown
```

#### OSGi 컴포넌트의 특성 {#characteristics-of-osgi-components}

인증 요구 사항을 정의하고 전용 로그인 경로를 지정하기 위해 다음 두 개의 OSGi 구성 요소가 도입되었습니다.

* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration`
* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl`

**org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration**

<table> 
 <tbody> 
  <tr> 
   <td>레이블</td> 
   <td>Apache Jackrabbit Oak CUG 구성</td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>CUG 권한 설정 및 평가를 위한 인증 구성</td> 
  </tr> 
  <tr> 
   <td>구성 속성</td> 
   <td> 
    <ul> 
     <li><code>cugSupportedPaths</code></li> 
     <li><code>cugEnabled</code></li> 
     <li><code>configurationRanking</code></li> 
    </ul> <p>또한 아래의 <a href="/help/sites-administering/closed-user-groups.md#configuration-options" target="_blank">구성 옵션을</a> 참조하십시오.</p> </td> 
  </tr> 
  <tr> 
   <td>구성 정책</td> 
   <td><code>ConfigurationPolicy.REQUIRE</code></td> 
  </tr> 
  <tr> 
   <td>참조</td> 
   <td><code>CugExclude (ReferenceCardinality.OPTIONAL_UNARY)</code></td> 
  </tr> 
 </tbody> 
</table>

**org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl**

<table> 
 <tbody> 
  <tr> 
   <td>레이블</td> 
   <td>Apache Jackrabbit Oak CUG Exclude List</td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>CUG 평가에서 혼동된 이름이 있는 주체를 제외할 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>구성 속성</td> 
   <td> 
    <ul> 
     <li><code>principalNames</code></li> 
    </ul> <p>아래의 구성 옵션을 참조하십시오.</p> </td> 
  </tr> 
  <tr> 
   <td>구성 정책</td> 
   <td><code>ConfigurationPolicy.REQUIRE</code></td> 
  </tr> 
  <tr> 
   <td>참조</td> 
   <td>NA</td> 
  </tr> 
 </tbody> 
</table>

#### Configuration Options {#configuration-options}

주요 구성 옵션은 다음과 같습니다.

* `cugSupportedPaths`:CUG를 포함할 수 있는 하위 트리를 지정합니다. 기본값이 설정되지 않음
* `cugEnabled`:구성 옵션을 사용하여 현재 CUG 정책에 대한 권한 평가를 활성화합니다.

CUG-authorization 모듈과 관련된 사용 가능한 구성 옵션이 [Apache Oak 문서에서 자세히 설명되어 있습니다](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#configuration).

#### CUG 평가에서 주도자 제외 {#excluding-principals-from-cug-evaluation}

개별 주도자를 CUG 평가에서 제외시키는 것이 이전 구현에서 채택되었습니다. 새로운 CUG 인증에서는 CugExclude라는 전용 인터페이스를 통해 이러한 문제를 다룹니다. Apache Jackrabbit Oak 1.4는 개별 주체 이름을 구성할 수 있는 확장 구현 및 고정된 주도자 집합을 제외하는 기본 구현을 제공합니다. 후자는 AEM 게시 인스턴스에 구성됩니다.

AEM 6.3에서는 다음 주체가 CUG 정책에 영향을 받지 않도록 하기 때문에 기본값이 됩니다.

* 관리자 주체(관리자 사용자, 관리자 그룹)
* 서비스 사용자 관리자
* 저장소 내부 시스템 주체

자세한 내용은 아래 AEM 6.3 이후의 [기본 구성](#default-configuration-since-aem) 섹션에 있는 표를 참조하십시오.

&#39;관리자&#39; 그룹의 제외는 **Apache Jackrabbit Oak CUG 제외 목록의 구성 섹션에 있는 시스템 콘솔에서 변경하거나 확장할 수 있습니다**.

또는 CugExclude 인터페이스의 사용자 지정 구현을 제공 및 배포하여 특별한 필요가 있을 경우 제외된 주도자 집합을 조정할 수 있습니다. 자세한 내용 및 예제 구현은 [CUG 플러그인에](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) 대한 설명서를 참조하십시오.

### 인증:설정 및 구성 {#authentication-setup-and-configuration}

새로운 인증 관련 부분은 **Adobe Granite Authentication Handler** 번들( `com.adobe.granite.auth.authhandler` 버전 5.6.48)에 포함되어 있습니다. 이 번들은 AEM 기본 설치의 일부입니다.

사용되지 않는 CUG 지원에 대한 인증 요구 사항 교체를 설정하려면 특정 AEM 설치 시 일부 OSGi 구성 요소가 있어야 하며 활성화되어 있어야 합니다. 자세한 내용은 **아래의 OSGi 구성 요소의 특성을** 참조하십시오.

>[!NOTE]
>
>RequirementHandler가 있는 필수 구성 옵션으로 인해 인증 관련 부분은 지원되는 경로 집합을 지정하여 기능이 활성화된 경우에만 활성화됩니다. 표준 AEM 설치에서는 작성 실행 모드에서 기능이 비활성화되고 게시 실행 모드에서 /content에 대해 활성화됩니다.

**OSGi 컴포넌트의 특성**

다음 2개의 OSGi 구성 요소가 인증 요구 사항을 정의하고 전용 로그인 경로를 지정하는 데 도입되었습니다.

* `com.adobe.granite.auth.requirement.impl.RequirementService`
* `com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler`

**com.adobe.granite.auth.requirement.impl.RequirementService**

<table> 
 <tbody> 
  <tr> 
   <td>레이블</td> 
   <td>-</td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>인증 요구 사항(믹싱 유형을 통해)에 영향을 주는 컨텐츠 변경에 대해 옵저버를 등록한 인증 요구 사항을 위한 전용 OSGi 서비스 및 로그인 경로가 <code>granite:AuthenticationRequirement</code> 에 노출됩니다 <code>LoginSelectorHandler</code>. </td> 
  </tr> 
  <tr> 
   <td>구성 속성</td> 
   <td>-</td> 
  </tr> 
  <tr> 
   <td>구성 정책</td> 
   <td><code>ConfigurationPolicy.OPTIONAL</code></td> 
  </tr> 
  <tr> 
   <td>참조</td> 
   <td> 
    <ul> 
     <li><code>RequirementHandler (ReferenceCardinality.MANDATORY_UNARY)</code></li> 
     <li><code>Executor (ReferenceCardinality.MANDATORY_UNARY)</code></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler**

| 레이블 | Adobe [MOCK]Granite Authentication Requirements and Login Path Handler |
|---|---|
| 설명 | `RequirementHandler` 구현을 참조하십시오. |
| 구성 속성 | `supportedPaths` |
| 구성 정책 | `ConfigurationPolicy.REQUIRE` |
| 참조 | NA |

#### Configuration Options {#configuration-options-1}

CUG 다시 작성의 인증 관련 부분은 [Adobe]의 [화강암 인증 요구 사항] 및 [로그인 경로 처리기]와 연결된 단일 구성 옵션만 사용합니다.

**&quot;인증 요구 사항 및 로그인 경로 처리기&quot;**

<table> 
 <tbody> 
  <tr> 
   <td>속성</td> 
   <td>유형</td> 
   <td>기본 값</td> 
   <td>설명</td> 
  </tr> 
  <tr> 
   <td><p>Label = 지원되는 경로</p> <p>이름 = 'supportedPaths'</p> </td> 
   <td>&lt;문자열&gt; 설정</td> 
   <td>-</td> 
   <td>이 처리기에서 인증 요구 사항이 적용될 경로입니다. Leave this configuration unset if you want to add the mixin type to nodes without having them forced (for example, on author instances). <code>granite:AuthenticationRequirement</code> 없는 경우 이 기능은 비활성화됩니다. </td> 
  </tr> 
 </tbody> 
</table>

## AEM 6.3 이후의 기본 구성 {#default-configuration-since-aem}

AEM의 새로운 설치에서는 기본적으로 CUG 기능의 인증 및 인증 관련 부분에 모두 새로운 구현을 사용합니다. 이전 구현 &quot;Adobe CUG(Granite Closed User Group) Support&quot;는 더 이상 사용되지 않으며, 모든 AEM 설치에서 기본적으로 비활성화됩니다. 대신 새 구현이 다음과 같이 활성화됩니다.

### 작성자 인스턴스 {#author-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **설명** |
|---|---|
| 지원되는 경로 `/content` | CUG 정책에 대한 액세스 제어 관리가 활성화되어 있습니다. |
| CUG 평가 활성화 FALSE | 권한 평가를 사용할 수 없습니다. CUG 정책은 아무런 효과가 없습니다. |
| 등급 | 200 | Oak 설명서를 참조하십시오. |

>[!NOTE]
>
>기본 작성 인스턴스에 **Apache Jackrabbit Oak CUG Exclude List** 및 **Adobe Granite Authentication Requirements 및 Login Path Handler** 에 대한 구성이 없습니다.

### 게시 인스턴스 {#publish-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **설명** |
|---|---|
| 지원되는 경로 `/content` | CUG 정책에 대한 액세스 제어 관리가 구성된 경로 아래에서 활성화됩니다. |
| CUG 평가 활성화 TRUE | 권한 평가는 구성된 경로 아래에서 활성화됩니다. CUG 정책은 발효됩니다 `Session.save()`. |
| 등급 | 200 | Oak 설명서를 참조하십시오. |

| **&quot;Apache Jackrabbit Oak CUG Exclude List&quot;** | **설명** |
|---|---|
| 주체 이름 관리자 | CUG 평가에서 관리자 주도자를 제외합니다. |

| **&quot;Adobe [Granite Authentication Requirements and Login Path Handler&quot;** | **설명** |
|---|---|
| 지원되는 경로  `/content` | 저장소에 정의된 혼합 유형의 인증 요구 사항은 아래에 `granite:AuthenticationRequired` 적용됩니다 `/content` `Session.save()`. Sling Authenticator가 업데이트됩니다. 지원되는 경로 외부에 혼합 유형을 추가하는 것은 무시됩니다. |

## CUG 인증 및 인증 요구 사항 비활성화 {#disabling-cug-authorization-and-authentication-requirement}

특정 설치에서 CUG를 사용하지 않거나 인증 및 인증에 다른 방법을 사용하는 경우 새로운 구현을 모두 사용할 수 없습니다.

### CUG 인증 비활성화 {#disable-cug-authorization}

복합 권한 부여 설정에서 [CUG 권한](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) 모델을 제거하는 방법에 대한 자세한 내용은 CUG 플러그인 설명서를 참조하십시오.

### 인증 요구 사항 비활성화 {#disable-the-authentication-requirement}

모듈에서 제공한 인증 요구 사항에 대한 지원을 비활성화하려면 [ `granite.auth.authhandler` Adobe [화강암 인증 요구 사항] 및 [로그인 경로 처리기]와 연결된 구성을 제거하는 데 충분합니다 ****.

>[!NOTE]
>
>그러나 구성을 제거하면 영향을 받지 않고 노드에 적용할 수 있는 혼합 유형이 등록 취소되지 않습니다.

## 다른 모듈과의 상호 작용 {#interaction-with-other-modules}

### Apache Jackrabbit API {#apache-jackrabbit-api}

CUG 인증 모델에서 사용되는 새로운 유형의 액세스 제어 정책을 반영하기 위해 Apache Jackrabbit가 정의한 API가 확장되었습니다. 모듈 버전 2.11.0부터 `jackrabbit-api` 모듈 `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`은 확장되는 새로운 인터페이스를 정의합니다 `javax.jcr.security.AccessControlPolicy`.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Apache Jackrabbit FileVault의 가져오기 메커니즘은 유형의 액세스 제어 정책을 처리하도록 조정되었습니다 `PrincipalSetPolicy`.

### Apache Sling Content Distribution {#apache-sling-content-distribution}

위의 [Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault) 섹션을 참조하십시오.

### Adobe [MOCK]Granite Replication {#adobe-granite-replication}

다른 AEM 인스턴스 간에 CUG 정책을 복제할 수 있도록 복제 모듈이 약간 조정되었습니다.

* `DurboImportConfiguration.isImportAcl()` 문자 그대로 해석되며 구현 시 액세스 제어 정책에만 영향을 미칩니다. `javax.jcr.security.AccessControlList`

* `DurboImportTransformer` true ACL에 대해서만 이 구성을 준수합니다.
* CUG 인증 모델에서 생성된 `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy` 인스턴스와 같은 다른 정책은 항상 복제되며 구성 옵션() `DurboImportConfiguration.isImportAcl`은 무시됩니다.

CUG 정책을 복제하는 한 가지 제한 사항이 있습니다. 해당 믹싱 노드 유형을 제거하지 않고 지정된 CUG 정책 `rep:CugMixin,` 이 제거되면 제거가 복제 시 반영되지 않습니다. 이는 정책 제거 시 항상 혼합을 제거함으로써 해결되었습니다. 그러나 mixin 유형이 수동으로 추가되는 경우 제한이 나타날 수 있습니다.

### Adobe GRANITE 인증 처리기 {#adobe-granite-authentication-handler}

번들과 함께 제공된 인증 처리기 **Adobe [Granite HTTP Header Authentication Handler** ]는 `com.adobe.granite.auth.authhandler` 동일한 모듈에 의해 정의된 `CugSupport` 인터페이스에 대한 참조를 보유합니다. 특정 상황에서 &#39;영역&#39;을 계산하는 데 사용되며 처리기로 구성된 영역으로 돌아갑니다.

이 설정은 사용되지 않는 구현을 다시 활성화하려는 경우 이전 버전과의 호환성을 최대한 보장하기 위해 선택적 참조를 `CugSupport` 사용하도록 조정되었습니다. 구현을 사용한 설치는 더 이상 CUG 구현에서 추출된 영역을 가져오지 않지만 [ **Adobe [Granite HTTP Header Authentication Handler]로 정의된 영역에 항상 표시됩니다**.

>[!NOTE]
>
>기본적으로 [ **Adobe [화강암 HTTP 헤더 인증 처리기** ]는 [로그인 페이지 비활성화]() 옵션을 활성화한 상태로 게시 실행 모드에서만 `auth.http.nologin`구성됩니다.

### AEM LiveCopy {#aem-livecopy}

LiveCopy와 함께 CUG를 구성하는 방법은 다음과 같이 추가 노드 1개와 추가 속성 1개를 추가하여 저장소에 표시됩니다.

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

이 두 요소 모두 를 통해 만들어집니다 `cq:Page`. 현재 디자인에서 MSM은 `cq:PageContent` (`jcr:content`) 노드 아래에 있는 노드와 속성만 처리합니다.

따라서 CUG 그룹을 블루프린트에서 Live Copy로 롤백할 수 없습니다. Live Copy를 설정할 때 이에 따라 계획을 설정하십시오.

## 새로운 CUG 구현의 변경 사항 {#changes-with-the-new-cug-implementation}

이 섹션의 목표는 CUG 기능에 대한 변경 사항에 대한 개요와 이전 구현과 새 구현 간의 비교를 제공하는 것입니다. 여기에는 CUG 지원 구성 방식에 영향을 주는 변경 사항이 나열되며 저장소 컨텐츠에서 CUG를 관리하는 방법과 사용자에 대해 설명합니다.

### CUG 설정 및 구성 차이점 {#diferences-in-cug-setup-and-configuration}

사용되지 않는 OSGi 구성 요소 **Adobe CUG(Granite Closed User Group) 지원** `com.day.cq.auth.impl.cug.CugSupportImpl`()이 이전 CUG 기능의 인증 및 인증 관련 부분을 별도로 처리할 수 있도록 새 구성 요소로 대체되었습니다.

## 저장소 컨텐츠에서 CUG 관리의 차이점 {#differences-in-managing-cugs-in-the-repository-content}

다음 섹션에서는 기존 구현과 새 구현과 구현 및 보안 관점에서 차이가 나는 것을 설명합니다. 새로운 구현은 동일한 기능을 제공하기 위한 것이지만 새로운 CUG를 사용할 때 알아야 할 미묘한 차이가 있습니다.

### 인증과 관련된 차이점 {#diferences-with-regards-to-authorization}

권한 부여 관점의 기본 차이는 아래 목록에 요약됩니다.

**CUG를 위한 전용 액세스 제어 컨텐츠**

이전 구현에서는 기본 인증 모델을 사용하여 게시 시 액세스 제어 목록 정책을 조작하고 CUG에서 지정한 설정에 따라 기존 ACE를 교체했습니다. 이는 게시에 해석된 정규 잔존 JCR 속성을 작성하여 트리거되었습니다.

새로운 구현을 통해 기본 인증 모델의 액세스 제어 설정은 작성, 수정 또는 제거되는 CUG로 인해 영향을 받지 않습니다. 대신 호출된 새로운 유형의 정책 `PrincipalSetPolicy` 이 대상 노드에 대한 추가 액세스 제어 컨텐츠로 적용됩니다. 이 추가 정책은 대상 노드의 자식으로 위치하며, 있을 경우 기본 정책 노드의 동위가 됩니다.

**액세스 제어 관리에서 CUG 정책 편집**

잔존 JCR 속성에서 전용 액세스 제어 정책으로 전환하면 CUG 기능의 인증 부분을 생성하거나 수정하는 데 필요한 권한에 영향을 줍니다. 제어 컨텐츠에 액세스하기 위한 수정 사항으로 간주되므로 보관소에 쓰기 `jcr:readAccessControl` 를 위해서는 `jcr:modifyAccessControl` 권한과 권한이 필요합니다. 따라서 페이지의 액세스 제어 컨텐츠를 수정할 권한이 있는 컨텐츠 작성자만 이 컨텐츠를 설정하거나 수정할 수 있습니다. 이는 일반 JCR 속성을 작성할 수 있는 기능이 충분하여 권한 에스컬레이션 문제가 발생하는 이전 구현과 대비됩니다.

**정책으로 정의된 Target 노드**

CUG 정책은 제한된 읽기 액세스 권한이 적용될 하위 트리를 정의하는 JCR 노드에서 작성되어야 합니다. 트리 전체에 CUG가 예상될 경우 AEM 페이지가 될 수 있습니다.

CUG 정책을 지정된 페이지 아래에 있는 jcr:content 노드에만 배치하면 지정된 페이지의 컨텐츠에 대한 액세스만 제한되며, 형제 페이지 또는 하위 페이지에는 적용되지 않습니다. 유효한 사용 사례일 수 있으며, 세분화된 액세스 컨텐츠 컨텐츠를 적용할 수 있는 저장소 편집기를 사용할 수 있습니다. 하지만, 이것은 jcr:content 노드에 cq:cugEnabled 속성을 삽입하는 이전 구현이 내부적으로 페이지 노드에 다시 매핑되었던 것과 대비됩니다. 이 매핑은 더 이상 수행되지 않습니다.

**CUG 정책을 사용한 권한 평가**

이전 CUG 지원에서 추가 인증 모델로 이동하면 효과적인 읽기 권한이 평가되는 방식이 변경됩니다. Jackrabbit 설명서에 [설명된 대로, Oak 저장소에서 구성한 모든 모델의 권한 평가가 읽기 액세스 권한을 부여하는 경우에만 볼 수](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html)`CUGcontent` 있는 지정된 주체가 읽기 액세스 권한을 부여하게 됩니다.

즉, 효과적인 사용 권한을 평가하기 위해 CUG 컨텐츠에 대한 `CUGPolicy` 및 기본 액세스 제어 항목을 모두 검토하고 두 가지 유형의 정책에 의해 부여된 경우에만 CUG 컨텐츠에 대한 읽기 액세스 권한이 부여됩니다. 전체 트리에 대한 읽기 액세스 권한이 모든 사람에게 부여된 기본 AEM 게시 설치에서는 CUG `/content` 정책의 효과는 이전 구현과 동일합니다.

**주문형 평가**

CUG 인증 모델을 사용하면 액세스 제어 관리 및 권한 평가를 개별적으로 설정할 수 있습니다.

* CUG를 만들 수 있는 지원되는 경로가 하나 이상 있는 경우 액세스 제어 관리가 활성화됩니다
* 권한 평가는 옵션 **CUG 평가 활성화가 추가로 선택된 경우에만** 활성화됩니다.

CUG 정책의 새로운 AEM 기본 설정 평가에서는 &#39;게시&#39; 실행 모드에서만 활성화됩니다. 자세한 내용은 AEM 6.3 이후의 [기본 구성에](#default-configuration-since-aem) 대한 세부 사항을 참조하십시오. 지정된 경로에 대한 효과적인 정책을 컨텐츠에 저장된 정책과 비교하여 확인할 수 있습니다. 유효한 정책은 CUG에 대한 권한 평가가 활성화된 경우에만 표시됩니다.

위에서 설명한 대로 CUG 액세스 제어 정책은 항상 컨텐츠에 저장되지만, 이러한 정책으로 인한 효과적인 사용 권한에 대한 평가는 Apache Jackrabbit Oak **CUG Configuration의 시스템 콘솔에서** CUG 평가 사용 **기능이 설정되어 있는 경우에만 적용됩니다.** 기본적으로 &#39;게시&#39; 실행 모드에서만 활성화됩니다.

### 인증과 관련된 차이점 {#differences-with-regards-to-authentication}

인증에 대한 기본 설정은 아래에 설명되어 있습니다.

#### 인증 요구 사항을 위한 전용 믹싱 유형 {#dedicated-mixin-type-for-authentication-requirement}

이전 구현에서 CUG의 인증 및 인증 양상은 단일 JCR 속성( `cq:cugEnabled`)에 의해 트리거되었습니다. 인증에 관한 한 Apache Sling Authenticator 구현에 저장된 인증 요구 사항 목록이 업데이트되었습니다. 새 구현을 사용하면 대상 노드를 전용 믹싱 유형()으로 표시함으로써 동일한 결과를 얻을 수 `granite:AuthenticationRequired`있습니다.

#### 로그인 경로를 제외하기 위한 속성 {#property-for-excluding-login-path}

mixin 유형은 기본적으로 속성에 해당하는 단일 선택적 속성 `granite:loginPath`을 `cq:cugLoginPage` 정의합니다. 이전 구현과 달리 로그인 경로 속성은 선언 노드 유형이 언급된 mixin인 경우에만 적용됩니다. 혼합 유형을 설정하지 않고 해당 이름의 속성을 추가하면 아무런 효과가 없으며, 새로운 요구 사항이나 로그인 경로에 대한 제외가 인증자에게 보고되지 않습니다.

#### 인증 요구 사항에 대한 권한 {#privilege-for-authentication-requirement}

혼합 유형을 추가하거나 제거하려면 권한이 `jcr:nodeTypeManagement` 부여되어야 합니다. 이전 구현에서는 `jcr:modifyProperties` 권한이 남아 있는 속성을 편집하는 데 사용됩니다.

속성을 추가 `granite:loginPath` , 수정 또는 제거하려면 동일한 권한이 필요합니다.

#### 혼합 유형에 의해 정의된 Target 노드 {#target-node-defined-by-mixin-type}

인증 요구 사항은 강제 로그인에 적용할 하위 트리를 정의하는 JCR 노드에서 작성되어야 합니다. 이는 CUG가 전체 트리에 영향을 줄 것으로 예상되며 새 구현에 대한 UI가 결과적으로 페이지 노드에 인증 요구 사항 믹싱 유형을 추가하는 경우에 대비해 AEM 페이지일 수 있습니다.

CUG 정책을 지정된 페이지 아래에 있는 jcr:content 노드에만 배치하면 컨텐츠에 대한 액세스만 제한되며, 페이지 노드 자체나 하위 페이지에서는 적용되지 않습니다.

이는 유효한 시나리오로, 모든 노드에 믹싱을 배치할 수 있는 저장소 편집기를 사용할 수 있습니다. 하지만, 이 동작은 이전 구현과 대비됩니다. 여기서 jcr:content 노드에 cq:cugEnabled 또는 cq:cugLoginPage 속성을 삽입하면 궁극적으로 페이지 노드에 내부적으로 다시 매핑됩니다. 이 매핑은 더 이상 수행되지 않습니다.

#### 구성된 지원 경로 {#configured-supported-paths}

mixin `granite:AuthenticationRequired` type과 granite:loginPath 속성은 Adobe [GRANITE 인증 요구 사항] 및 [로그인 경로 처리기]와 함께 있는 **지원되는 경로** 구성 옵션 집합으로 정의된 범위 내에서만 **적용됩니다**. 경로를 지정하지 않으면 인증 요구 사항 기능이 모두 비활성화됩니다. 이 경우 지정된 JCR 노드에 추가하거나 설정할 때 혼합 유형 또는 속성이 적용됩니다.

### JCR 컨텐트, OSGi 서비스 및 구성 매핑 {#mapping-of-jcr-content-osgi-services-and-configurations}

아래 문서는 이전 및 새 구현 간에 OSGi 서비스, 구성 및 저장소 컨텐츠에 대한 포괄적인 매핑을 제공합니다.

AEM 6.3 이후 CUG 매핑

[파일 가져오기](assets/cug-mapping.pdf)

## 업그레이드 CUG {#upgrade-cug}

### 더 이상 사용되지 않는 CUG를 사용한 기존 설치 {#existing-installations-using-the-deprecated-cug}

이전 CUG 지원 구현은 더 이상 사용되지 않으며 향후 버전에 대해 제거됩니다. AEM 6.3보다 이전 버전에서 업그레이드할 때에는 새 구현으로 이동하는 것이 좋습니다.

업그레이드된 AEM 설치의 경우 하나의 CUG 구현만 활성화되어 있는지 확인해야 합니다. 새로워진 CUG와 사용되지 않는 이전 CUG 지원을 조합하여 테스트되지 않고 불필요한 비헤이비어가 발생할 수 있습니다.

* 인증 요구 사항과 관련된 Sling Authenticator 충돌
* 이전 CUG와 연결된 ACL 설정이 새로운 CUG 정책과 충돌할 때 읽기 액세스가 거부되었습니다.

### 기존 CUG 컨텐츠 마이그레이션 {#migrating-existing-cug-content}

Adobe은 새 CUG 구현으로 마이그레이션하는 도구를 제공합니다. 사용하려면 다음 단계를 수행하십시오.

1. 툴 `https://<serveraddress>:<serverport>/system/console/cug-migration` 로 이동합니다.
1. CUG를 확인할 루트 경로를 입력하고 Perform dry run **버튼을** 누릅니다. 이렇게 하면 선택한 위치에서 전환될 수 있는 CUG가 검색됩니다.
1. 결과를 검토한 후 마이그레이션 **수행** 단추를 눌러 새 구현으로 마이그레이션합니다.

>[!NOTE]
>
>문제가 발생하는 경우 마이그레이션 툴의 출력을 받기 위해 **DEBUG** 수준에서 특정 로거 `com.day.cq.auth.impl.cug` 를 설정할 수 있습니다. 이 [방법에 대한 자세한 내용은](/help/sites-deploying/configure-logging.md) 로깅을 참조하십시오.

