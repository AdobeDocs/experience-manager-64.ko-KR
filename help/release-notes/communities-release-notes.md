---
title: AEM Communities 릴리스 노트
seo-title: AEM Communities
description: Adobe Experience Manager 6.4 Communities와 관련된 릴리스 노트입니다.
seo-description: Adobe Experience Manager 6.4 Communities와 관련된 릴리스 노트입니다.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 12%

---


# AEM Communities 릴리스 노트 {#aem-communities-release-notes}

이 섹션에서는 6.3 릴리스 이후 AEM Communities의 개선 사항에 대한 정보를 제공합니다. 새로운 기능에 대한 자세한 내용은 AEM 6.4 커뮤니티[의 새로운 기능을 참조하십시오.](/help/communities/whats-new-aem-communities.md)

최신 릴리스를 얻으려면 설명서의 [커뮤니티 배포](/help/communities/deploy-communities.md#latest-releases) 섹션을 참조하십시오.

## 주요 개선 사항 {#main-improvements}

커뮤니티 사이트:

* 커뮤니티 관리자는 이제 다음을 수행할 수 있습니다.

   * 커뮤니티 사이트 영구 삭제
   * 커뮤니티 사이트에 대한 컨텍스트 인식 구성 폴더 선택

커뮤니티 그룹:

* 커뮤니티 관리자는 이제 다음을 수행할 수 있습니다.

   * 영구적으로 커뮤니티 그룹 삭제
   * 여러 언어로 커뮤니티 그룹 만들기
   * 커뮤니티 그룹 내에 활성 카탈로그 및 할당 추가

* 지원 관리자는

   * 커뮤니티 그룹 내에서 리소스 및 학습 경로 만들기 및 할당

파일 라이브러리:

* 이제 커뮤니티 구성원은 정렬 순서, 태그 지정 등과 같이 파일 라이브러리에 대한 여러 개선 사항을 갖습니다.

알림:

* 이제 커뮤니티 구성원은 중재 프로세스를 거친 기여도의 승인 시 알림을 받습니다.

중재:

* 자동 스팸 감지 필터
* 커뮤니티 중재자에게는 추가 중재 필터(예: 답변됨/답변되지 않은 질문)가 있습니다.
* 커뮤니티 중재자는 조정을 책갈피 설정하고 사전 정의된 필터(예: 승인 대기 중인 모든 게시물)에 연결할 수 있습니다.

AEM 6.4의 근본적인 변화와의 전체적인 호환성

참고:이 모든 기능은 AEM 6.3에서도 사용할 수 있습니다. AEM Communities 릴리스 노트에서 [6.3](https://helpx.adobe.com/kr/experience-manager/6-3/release-notes.html)을 확인하십시오.

## 알려진 문제 {#known-issues}

* **중재**  - 벌크 중재 UI에서 단일 삭제 작업으로 상위 게시물을 삭제할 수 없습니다(CQ-4236797).
* **콘솔**  - [사용자 이름 분실] 또는 [암호 분실] 링크가 해당 암호 검색 양식 대신 로그인 페이지로 리디렉션됩니다(CQ-4237682).

## 기능 {#select-features} 선택

전문가 점수(*Powered by Sensei*)는 가치 있는 커뮤니티 행동을 장려하고 보상하는 효과적인 방법으로 게임화를 활성화하는 데 사용됩니다. 추천 또는 마케팅 목적으로 전문가를 식별하는 데에도 사용할 수 있습니다.

## 데모 {#demonstrations}

이러한 모든 기능은 AEM Communities 데모 시나리오를 사용할 때와 새로운 We.Retail 참조 구현 내에서 GitHub.com에서 공개적으로 사용할 수 있는 [AEM 데모 컴퓨터](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki)를 사용하여 입증될 수 있습니다.
