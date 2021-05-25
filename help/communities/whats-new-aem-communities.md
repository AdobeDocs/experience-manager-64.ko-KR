---
title: AEM 6.4 Communities의 새로운 기능
description: AEM Communities은 파트너, 고객 및 직원 간에 협업하기 위한 비즈니스를 위한 프레임워크를 제공합니다.
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
source-git-commit: 1a7ecec2f3c2618bb6d0280a8f9a66754cd8a1a3
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# AEM 6.4 Communities {#what-s-new-in-aem-communities}의 새로운 기능

AEM Communities은 파트너, 고객 및 직원 간에 협업하기 위한 비즈니스를 위한 프레임워크를 제공합니다. 웹 사이트 구조에 소셜 기능을 부여하고 기업이 이해 당사자들에게 지식을 주고 전달하여 자신의 브랜드 가치를 높일 수 있도록 지원합니다.

AEM 6.4 Communities는 커뮤니티 사용자의 경험을 개선하고 커뮤니티 관리자, 중재자 및 관리자의 일상적인 작업을 간소화하기 위해 기능을 제공합니다.

새로운 기능 및 개선 사항에 대한 빠른 소개는 자세히 알아보십시오. 또한 AEM 6.4 Communities [릴리스 노트](../release-notes/communities-release-notes.md)를 참조하십시오. AEM 6.4 Communities 설명서는 [AEM 6.4 Communities 사용 안내서](home.md)를 참조하십시오.

## 하위 커뮤니티 또는 커뮤니티 그룹 관리 {#managing-sub-communities-or-community-groups}

AEM Communities을 사용하면 커뮤니티 관리자가 사전 정의된 템플릿을 사용하여 커뮤니티 사이트 내에서 그룹 및 하위 그룹을 작성 환경에서 만들 수 있습니다. 이러한 그룹은 하위 커뮤니티 역할을 하며 상위 사이트에서 테마 및 스타일링 등 많은 구성을 상속할 수 있습니다. 하지만 이러한 그룹은 상위 사이트와 다를 수 있습니다. 예를 들어 그룹 중재자 세트가 다르거나 보안 수준에서 다를 수 있습니다. 이러한 그룹은 다음과 같은 개선 사항에 의해 권한을 부여받는 독립적인 완전한 미니 커뮤니티로 작동합니다.

### 단일 단계 {#create-multi-locale-groups-in-single-step}에서 다중 로케일 그룹 만들기

커뮤니티 사이트의 일부로, 단일 작업으로 다국어 그룹을 만들 수 있습니다. **[!UICONTROL 커뮤니티 그룹 템플릿 페이지의 추가 사용 가능한 커뮤니티 그룹 언어]** 필드 **[!UICONTROL 에서]** 는 커뮤니티 사이트 내에서  [새 커뮤니티 ](groups.md) 그룹을 만드는 동안 사용할 수 있으므로 이 작업이 가능합니다.

![multilinoalgroup-1](assets/multilingualgroup-1.png)

이러한 그룹을 만들려면 사이트 콘솔에서 원하는 커뮤니티 사이트의 그룹 컬렉션으로 이동할 수 있습니다. 그룹을 만들고 **[!UICONTROL 추가 사용 가능한 커뮤니티 그룹 언어**[!UICONTROL &#x200B;커뮤니티 그룹 템플릿&#x200B;]**페이지의]** 필드에서 원하는 언어를 지정합니다.

### 그룹 콘솔에서 커뮤니티 그룹 삭제 {#delete-community-groups-from-groups-console}

AEM 6.4 Communities에서는 커뮤니티 사이트 콘솔 내의 커뮤니티 그룹 컬렉션에서 기존 커뮤니티 그룹에 있는 그룹 삭제 아이콘을 제공합니다. 따라서 그룹과 연관된 모든 항목(예: 컨텐츠 및 사용자 멤버십)의 삭제와 함께 [그룹 삭제](groups.md#deleting-the-group)을 한 번의 클릭으로 사용할 수 있습니다.

![deletegrp](assets/deletegrp.png)

### 그룹 {#create-and-assign-enablement-resources-within-groups} 내에 활성 리소스를 만들고 할당합니다.

이제 타깃팅된 특정 커뮤니티 구성원에 대해 학습 컨텐츠를 작성, 관리 및 게시할 수 있습니다. 커뮤니티 그룹(전체 커뮤니티 사이트뿐만 아니라)에 대한 카탈로그 및 할당 기능의 가용성으로 인해 지원 관리자는 [지원 리소스](resource.md)와 작은 사용자 집합에 대한 학습 경로를 할당할 수 있습니다.

![할당 카탈로그](assets/assignmentcatalog.png)

## 사용자 생성 콘텐츠 중재 {#moderating-user-generated-content}

AEM 6.4 Communities에서는 조정에 대한 개선 사항이 거의 없으며 이는 커뮤니티 중재자의 일상적 생활을 간소화하는 데 중요합니다.

### 자동 스팸 감지 {#automatic-spam-detection}

새로운 스팸 감지 엔진은 커뮤니티 사이트 또는 그룹에서 원치 않는 사용자 생성 컨텐츠를 필터링하는 데 도움이 됩니다. 이 기능을 활성화하면 사전 정의된 스팸 단어 세트를 기반으로 사용자가 생성한 컨텐츠를 스팸 또는 스팸 아님 으로 표시할 수 있습니다. 중재자는 컨텐츠에 따라 게시 인스턴스에 거부 또는 표시되도록 허용할 수 있습니다. 이러한 중재 작업은 인라인 또는 벌크 중재 콘솔을 통해 수행할 수 있습니다.

![spamdetection-1](assets/spamdetection-1.png)

[스팸 ](moderate-ugc.md#spam-detection) 감지기는 90% 정확도로 지정된 사용자가 생성한 컨텐츠를 찾아 플래그를 지정합니다. 그러나 이 기능은 기본적으로 활성화되어 있지 않습니다. 이를 활성화하려면 커뮤니티 관리자가 시스템/콘솔에서 configMgr로 이동하여 스팸 프로세스를 추가해야 합니다.

![spamprocess-1](assets/spamprocess-1.png)

### QnA {#new-answered-unanswered-filters-for-qna}에 대한 새로운 (응답 없음) 필터

AEM 6.4는 일괄 중재 콘솔에 두 개의 [새 필터](moderation.md#filter-rail)QnA 질문에 대해 응답됨 및 답변되지 않음 을 추가합니다. 이러한 필터는 필터 레일의 상태 아래에서 사용할 수 있습니다.

![상태](assets/statuses.png)

답변됨 상태를 선택하면 응답된 모든 질문이 컨텐츠 영역의 중재자에게 표시됩니다. 반면에, 답변되지 않음 상태만 선택한 경우, 답변되지 않은 질문 및 포럼 주제, 블로그 기사 또는 댓글과 같은 기타 컨텐츠에 답변되지 않은 질문에 대해 답변된 질문을 제외한 모든 컨텐츠 유형에 대해 조정자가 모든 컨텐츠(모든 컨텐츠 유형)를 볼 수 있습니다.

### 책갈피 중재 필터 {#bookmark-moderation-filters}

AEM Communities은 중재 콘솔에서 사전 정의된 중재 필터](moderation.md#filter-rail)에 책갈피를 지정하는 기능을 제공합니다. [ 이렇게 저장된 책갈피는 나중에 다시 방문하여 다른 사용자와 공유할 수 있습니다.

사용자는 중재 콘솔의 필터 레일에서 원하는 필터를 선택하고 필터링된 UGC를 보고 브라우저에서 필터를 책갈피로 지정해야 합니다. 이러한 필터는 URL 문자열의 끝 부분에 추가되므로 나중에 공유, 재사용 및 다시 방문할 수 있습니다.

## 커뮤니티 사이트 관리 {#managing-community-sites}

AEM 6.4 Communities에서는 사이트 관리자가 서로 다른 언어의 많은 커뮤니티 사이트를 쉽게 만들고, 관리하고 삭제할 수 있도록 해주는 사이트 관리 개선 사항을 제공합니다.

### 한 단계에서 다중 로케일 커뮤니티 사이트 만들기 {#create-multi-locale-community-sites-in-one-step}

AEM Communities에서는 단일 작업으로 [다국어 커뮤니티 사이트](create-site.md)를 만들 수 있습니다. 사이트 콘솔에서 새 커뮤니티 사이트를 만드는 동안 **[!UICONTROL 사이트 템플릿]** 페이지의 **[!UICONTROL 커뮤니티 사이트 기본 언어]** 필드에서 선택할 수 있는 여러 언어가 사용 가능하므로 이 작업이 가능합니다.

![multilocalesite](assets/multilocalesite.png)

사용자는 이러한 모든 사이트에 대해 구성 폴더, 브랜딩 및 기타 많은 구성을 한 번에 선택할 수 있습니다.

### 사이트 콘솔에서 커뮤니티 사이트 삭제 {#delete-community-sites-from-sites-console}

AEM 6.4 Communities에서는 커뮤니티 사이트 콘솔에서 기존 커뮤니티 사이트에서 사이트 삭제 아이콘을 제공합니다. 이렇게 하면 한 번의 클릭으로 사이트](create-site.md)와 관련 항목을 [삭제할 수 있습니다.

![사이트 작업](assets/siteactions.png)

## UGC 및 사용자 프로필 관리 {#managing-ugc-and-user-profiles}

사용자 데이터 보호를 커뮤니티 환경의 중심으로 유지하면 AEM Communities은 [API를 기본](user-ugc-management-service.md) 및 [샘플 서블릿](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet)을 표시합니다. 이러한 API는 사용자가 생성한 컨텐츠를 벌크 관리(벌크 삭제 및 대량 내보내기)하고 사용자 프로필을 삭제하는 데 도움이 되며 EU GDPR 준수 요청을 처리하는 데 중요합니다.

## 변경 사항 {#what-s-changed}

* 새 커뮤니티 사이트를 만드는 동안 AEM 6.4 Communities에서 Captcha 확인을 더 이상 기본적으로 사용할 수 없습니다. 그러나 보안 강화를 위해 [Google 구성 요소 reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html)를 포함하도록 커뮤니티 사이트를 사용자 지정할 수 있습니다.
* 사용자 지정 CSS 업로드 옵션이 커뮤니티 사이트 및 그룹 테마에서 제거되었습니다.
* 벌크 중재 UI의 필터 레일에 컨텐츠 전용 및 검색 아이콘이 추가되었습니다.
* 콘텐츠 경로 필터가 대량 중재 UI의 필터 레일에 추가되었습니다.
* 벌크 모드로 전환하고 벌크 모드 종료가 벌크 중재 UI에서 제거되었습니다. 다중 선택 모드로 전환하려면 마우스(데스크탑)를 사용하여 마우스를 가리키거나 게시물(모바일)에서 손가락을 누르고 있는 게시물에 나타나는 선택 ( ![선택 아이콘](assets/selecticon.png)) 아이콘을 클릭합니다.
