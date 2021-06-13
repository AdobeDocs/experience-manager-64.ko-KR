---
title: 스마트 컨텐츠 서비스 릴리스 노트
seo-title: 스마트 컨텐츠 서비스 릴리스 노트
description: 스마트 컨텐츠 서비스 개요 및 서비스 관련 알려진 문제입니다.
seo-description: 스마트 컨텐츠 서비스 개요 및 서비스 관련 알려진 문제입니다.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
exl-id: 6e7ac9d2-7181-48bb-82c4-61a90e594ff5
source-git-commit: a842c45f0a0597f4c7f143974a550874258e5382
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 12%

---

# 스마트 컨텐츠 서비스 릴리스 노트 {#smart-content-service-release-notes}

스마트 컨텐츠 서비스 개요 및 서비스 관련 알려진 문제입니다.

조직은 직원, 파트너 및 고객이 디지털 자산을 참조하고 검색하는 데 사용하는 분류법에 따라 디지털 자산에 태그를 지정해야 합니다. 일반 태그와 비교하여 비즈니스 분류법을 기반으로 태그가 지정된 자산은 태그 기반 검색으로 더 쉽게 식별 및 검색됩니다.

스마트 컨텐츠 서비스는 AEM Assets의 비즈니스 분류법을 사용하여 디지털 자산에 자동으로 태그를 지정하므로 가장 관련성이 높은 자산이 검색에 표시됩니다.

비즈니스 분류법을 인식하려면 조정된 AEM 자산 및 태그 세트에 대해 스마트 컨텐츠 서비스를 교육해야 합니다. 훈련이 끝나면 서비스는 유사한 자산 세트에 이러한 태그를 적용할 수 있습니다.

Smart Content Service는 비즈니스 분류에 대한 이미지 인식 알고리즘을 교육할 수 있는 Adobe Sensei 플랫폼을 기반으로 합니다. 그런 다음 이 컨텐츠 인텔리전스를 사용하여 유사한 자산에 관련 태그를 적용하는 데 사용됩니다.

## 주요 개선 사항 {#key-improvements}

스마트 컨텐츠 서비스에는 다음과 같은 주요 개선 사항이 포함되어 있습니다.

* 모델 정밀도, 회수 값 향상을 위한 알고리즘 최적화
* 테넌트 수준에서 모든 태그에 대한 모델 교육 재설정 지원
* 충돌을 방지하기 위해 향상된 스마트 태그 네임스페이스를 지원합니다
* 재교육으로 인해 발생하는 손상을 방지하기 위한 새로운 모델 교체 정책
* 서비스 사용에 대한 임차인 기반 모니터링
* 서비스 견고성을 향상시키는 클러스터링 및 연결 관련 문제에 대한 수정 사항

## 해결된 문제 {#fixed-issues}

이 릴리스에서는 다음 문제가 해결되었습니다.

* MySQL 서버에 연결할 수 없는 경우 태깅 및 교육 워크플로우에 대한 작업자 프로세스가 종료됩니다. CQ-4242886

* 정밀도 편중 점수가 제대로 계산되지 않습니다. CQ-4241797

* 모델에 대한 PR 계산이 잘못되었습니다. CQ-4241381

* 교육 워크플로우는 큐에서 처리할 때 예제 자산을 누락합니다. CQ-4240901

* 정밀회수 개선. CQ-4239895

* 모델 교체 정책. CQ-4239886

* 남성용 셔츠에 여성용 재킷에 태그가 지정되어 있다. CQ-4239650

* 단계 배포에서 교육 예가 누락되었습니다. CQ-4239483

* 교육 작업의 유효성 검사는 교육을 위해 제출된 자산 집합에서 수행해야 합니다. CQ-4238834

* 태그에 최소 긍정/음수 기능이 있어도 모델 생성이 실패합니다. CQ-4240741

* 트레이너 로그에 잘못된 정보가 있습니다. CQ-4240738

* 교육을 위해 제출된 태그가 서로 임의의 네거티브인 경우 최초 교육 문제가 발생합니다. CQ-4240118

* 즉흥 로그를 사용하여 테넌트당 서비스 사용을 모니터링합니다. CQ-4239781

## 언어 {#languages}

스마트 컨텐츠 서비스는 다음 로케일에 사용할 수 있습니다.

* 영어
* 독일어
* 프랑스어
* 스페인어
* 이탈리아어
* 포르투갈어
* 일본어
* 중국어 간체
* 한국어

## 링크 {#links}

* [adobe.com의 Adobe Experience Manager 제품 페이지](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [향상된 스마트 태그 설명서](/help/assets/enhanced-smart-tags.md)

## 제품 액세스 및 지원(제한된 사이트) {#product-access-and-support-restricted-sites}

다음 사이트는 고객만 사용할 수 있습니다. 고객이고 액세스 권한이 필요한 경우 Adobe 계정 관리자에게 문의하십시오.

* [제품 액세스](https://login.experiencecloud.adobe.com/exc-content/login.html)
* [licensing.adobe.com에서 제품 다운로드](https://licensing.adobe.com/).
* [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에 추가 기능을 위한 제품 업데이트, 패치 및 패키지.
* [Admin Console ](https://adminconsole.adobe.com/)를 통한 고객 지원. 자세한 내용은 [새 Adobe 고객 지원 경험](https://docs.adobe.com/content/help/ko-KR/customer-one/using/home.html)을 참조하십시오.
