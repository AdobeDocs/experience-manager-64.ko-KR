---
title: 대화형 통신 개요
seo-title: 대화형 통신 개요
description: 이 문서에는 개요, 샘플 사용 사례, 작성 워크플로우, 대화형 커뮤니케이션과 편지 간 차이점이 포함되어 있습니다.
seo-description: 대화형 통신 주요 기능, 샘플 사용 사례, 작성 워크플로우 및 대화형 커뮤니케이션과 서신 관리 간의 차이점
uuid: a06b4ac7-ca20-4d6d-b2b7-87b21e2f5cf9
contentOwner: gtalwar
topic-tags: interactive-communications, introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 67b03098-c58d-4a57-90e0-e4ddd78e5d99
exl-id: 386fc8b2-c92d-4731-8445-1bb6af54fd98
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 5%

---

# 대화형 통신 개요 {#interactive-communications-overview}

이 문서에는 개요, 샘플 사용 사례, 작성 워크플로우, 대화형 커뮤니케이션과 편지 간 차이점이 포함되어 있습니다.

![](do-not-localize/correspondence-management.png)

Interactive Communications는 비즈니스 서신, 문서, 명세서, 혜택 공지, 마케팅 이메일, 청구서 및 환영 키트와 같은 안전하고 개인화된 인터랙티브한 통신의 작성, 수집 및 전달을 중앙 집중화하여 관리합니다.

## 주요 기능 {#key-capabilities}

다음은 Interactive Communications의 주요 기능입니다.

* 양식 데이터 모델과 즉시 통합하여 백엔드 데이터베이스 및 MS® Dynamics 등의 기타 CRM 시스템에 쉽고 간편하게 액세스할 수 있습니다
* 인쇄 채널에서 웹 채널을 자동 생성할 수 있는 기능을 갖춘 인쇄 및 웹 채널을 위한 통합 제작 인터페이스
* 인쇄 및 웹에서 쉽게 이해할 수 있는 시각적 형식으로 정보를 제공하는 차트
* 문서 조각 지원 규칙 편집기 및 양식 데이터 모델
* 에이전트 사용자 인터페이스는 대화형 커뮤니케이션의 인쇄 및 웹 미리 보기를 표시합니다
* 구성 요소를 드래그 앤 드롭하여 인쇄 및 웹 채널을 신속하게 구성

## 샘플 사용 사례 {#sample-use-case}

[신용 카드 고객용 시작 키트](/help/forms/using/finance-reference-site-walkthrough.md#credit-card-application-walkthrough) 샘플 사용 사례는 대화형 커뮤니케이션의 기능을 보여줍니다.

## 대화형 통신 만들기 {#interactive-communication-creation}

![interactive_communication-01](assets/interactive_communication-01.jpg)

### 워크플로우 {#workflow}

대화형 커뮤니케이션을 만들려면 대화형 커뮤니케이션용 [빌딩 블록](#buildingblocks)을 준비하여 다음 단계를 완료하십시오.

1. [대화형 통신 만들기](/help/forms/using/create-interactive-communication.md)를 선택합니다.

1. [양식 데이터 모델](/help/forms/using/data-integration.md), 미리 채우기 서비스 및 [인쇄 및 웹 채널 템플릿](/help/forms/using/web-channel-print-channel.md)을 지정합니다. 인쇄 채널에서 웹 채널을 생성하도록 선택할 수 있습니다.

1. [드래그 앤 드롭 인터페이스](/help/forms/using/introduction-interactive-communication-authoring.md)를 사용하여 필요에 따라 문서 조각, 이미지, 구성 요소를 인쇄 및 대화형 커뮤니케이션의 웹 채널을 추가합니다.
1. 다음과 같이 삽입된 구성 요소의 속성을 구성합니다.

   1. 이미지
   1. [표](/help/forms/using/create-interactive-communication.md#tables) (레이아웃 조각 포함)
   1. [차트](/help/forms/using/chart-component-interactive-communications.md)
   1. [문서 조각](/help/forms/using/create-interactive-communication.md#document-fragment-properties)

1. 인쇄 및 웹 채널을 미리 보고 필요한 경우 대화형 커뮤니케이션을 편집합니다.
1. 에이전트는 에이전트 UI를 사용하여 [대화형 통신](/help/forms/using/prepare-send-interactive-communication.md)을 준비하여 수신자/사후 프로세스에 보냅니다.

### 빌딩 블록 {#buildingblocks}

다음은 대화형 커뮤니케이션을 만드는 데 필요한 기본 구성단위입니다.

* [양식 데이터 모델](/help/forms/using/data-integration.md)
* [인쇄 및 웹 채널 템플릿](/help/forms/using/web-channel-print-channel.md)
* [문서 조각](/help/forms/using/document-fragments.md)
* 이미지
* [](/help/forms/using/themes.md) 웹 채널의 테마

## 대화형 커뮤니케이션과 서신 관리 {#interactive-communications-vs-correspondence-management}

대화형 커뮤니케이션은 고객 커뮤니케이션을 만드는 기본적이고 권장되는 방법입니다. AEM 6.3 Forms 및 AEM 6.2 Forms에서 만드는 문자를 계속 사용하려면 [호환성 패키지](/help/forms/using/compatibility-package.md)를 설치해야 합니다. 다음은 Interactive Communication과 Letter의 기능을 비교한 것입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>기능</strong></td> 
   <td><strong>대화형 통신</strong></td> 
   <td><strong>편지</strong></td> 
  </tr>
  <tr>
   <td>출력</td> 
   <td>인쇄 및 웹</td> 
   <td>인쇄</td> 
  </tr>
  <tr>
   <td>스키마</td> 
   <td>양식 데이터 모델 </td> 
   <td>데이터 사전 </td> 
  </tr>
  <tr>
   <td>로컬라이제이션</td> 
   <td>양식 데이터 모델에서 지원되지 않음</td> 
   <td>데이터 사전에서 지원됨</td> 
  </tr>
  <tr>
   <td>규칙 편집기</td> 
   <td>
    <ul> 
     <li>인라인 조건을 만들기 위한 텍스트 및 조건 지원 규칙 편집기</li> 
     <li>대화형 통신 편집기는 웹 채널의 구성 요소에 대한 규칙 적용을 지원합니다</li> 
    </ul> </td> 
   <td>조건부 표현식 작성을 위한 UI 없음</td> 
  </tr>
  <tr>
   <td>작성</td> 
   <td>인쇄 및 웹 채널 구성을 위한 드래그 앤 드롭 인터페이스</td> 
   <td>드래그 앤 드롭 메커니즘 없음 </td> 
  </tr>
  <tr>
   <td>차트</td> 
   <td>인쇄와 웹 채널에서 지원되는 차트</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>테마</td> 
   <td>테마를 사용하여 웹 채널 스타일 지정</td> 
   <td>테마를 지원하지 않음</td> 
  </tr>
  <tr>
   <td>감사 및 버전 관리</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>초안 및 인스턴스 관리</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>일괄 처리</td> 
   <td>지원됨 </td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>에이전트 서명</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>원격 함수</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
 </tbody>
</table>
