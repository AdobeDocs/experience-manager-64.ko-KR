---
title: 게시 안 함 첫 번째 적응형 문서 만들기
seo-title: 게시 안 함 첫 번째 적응형 문서 만들기
description: 게시 안 함
seo-description: 게시 안 함
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
source-git-commit: 7ec0cd95417c015565fa6e07c753c4ac6df35cdb
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---


# 게시 안 함 첫 번째 적응형 문서 {#do-not-publish-create-your-first-adaptive-document} 만들기

## 사용 사례 {#use-case}

Adobe Finance는 금융 서비스 도메인의 선도적인 조직으로, 다양한 고객 프로필의 요구 사항에 맞게 포괄적이고 개인화된 금융 솔루션을 제공합니다.

고객의 자동 보험 증권 중 하나가 만료되며 갱신 견적서와 함께 대화형 PDF를 포함하는 리마인더를 고객에게 보냅니다. 또한 충성도 보상, 할인 제공 등의 기타 정보도 포함됩니다.

포털은 Adobe AEM에서 실행됩니다. 응용 문서의 다중 채널 기능을 사용하여 웹 및 인쇄 시작 채널 출력을 만듭니다.

자습서가 끝나면 다음과 유사한 적응형 문서가 제공됩니다.
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)첫 번째 적응형 문서 자습서를 만드는 방법은 단계로 분류됩니다. 각 단계 자체가 완전한 문서입니다.

<table> 
 <tbody>
  <tr>
   <th>배울 수 있습니다</th> 
   <th>
    <ul> 
     <li>적응형 문서 및 양식 데이터 모델 만들기</li> 
     <li>적응형 문서를 위한 템플릿 및 테마 만들기</li> 
     <li>규칙 편집기를 사용하여 비즈니스 규칙을 만듭니다.<br /> </li> 
     <li>응용 문서를 게시합니다.<br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>전제 조건</td> 
   <td>
    <ul> 
     <li>AEM 작성자 인스턴스를 설정합니다. </li> 
     <li>AEM Forms 추가 기능 설치. 자세한 내용은 <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">AEM Forms 설치 및 구성</a>을 참조하십시오.</li> 
     <li>데이터베이스 공급자에서 JDBC 데이터베이스 드라이버(JAR 파일)를 가져옵니다. 자습서의 예제는 MySQL 데이터베이스를 기반으로 하며 Oracle의 MySQL JDBC 데이터베이스 드라이버를 사용합니다. </li> 
     <li>고객 데이터가 포함된 데이터베이스를 설정합니다. 적응형 문서를 만들려면 데이터베이스가 필요합니다. 이 자습서에서는 데이터베이스를 사용하여 AEM Forms의 양식 데이터 모델 및 지속성 기능을 표시합니다. </li> 
     <li><a href="/help/forms/using/web-channel-print-channel.md">인쇄 및 웹 채널용 템플릿</a>을 생성/가져오고 활성화합니다.</li> 
     <li>FDM</a>을 기반으로 하는 <a href="/help/forms/using/document-fragments.md">문서 조각이 있는지 확인합니다.</a></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## 1단계:양식 데이터 모델 만들기 {#step-create-form-data-model}

양식 데이터 모델을 사용하면 적응형 문서를 서로 다른 데이터 소스에 연결할 수 있습니다. 예를 들어 AEM 사용자 프로필, RESTful 웹 서비스, SOAP 기반 웹 서비스, OData 서비스 및 관계형 데이터베이스가 있습니다. 양식 데이터 모델은 연결된 데이터 소스에서 사용할 수 있는 비즈니스 엔티티 및 서비스의 통합 데이터 표현 스키마입니다. 적응형 문서와 함께 양식 데이터 모델을 사용하여 연결된 데이터 소스에서 데이터를 검색할 수 있습니다. 양식 데이터 모델에 대한 자세한 내용은 [AEM Forms 데이터 통합](/help/forms/using/data-integration.md)을 참조하십시오.

목표:

* 데이터베이스 인스턴스(Microsoft Dynamics)를 데이터 소스로 구성
* Microsoft Dynamics를 데이터 소스로 사용하여 양식 데이터 모델 만들기
* 양식 데이터 모델에 데이터 모델 개체 추가
* 양식 데이터 모델에 대한 읽기 및 쓰기 서비스 구성
* 테스트 데이터로 양식 데이터 모델 및 구성된 서비스 테스트

## 2단계:응용 문서 {#step-create-an-adaptive-document} 만들기

고객 커뮤니케이션은 비즈니스 서신, 편지, 문서, 명세서, 혜택 공지, 재산 관리 설명서, 마케팅 이메일, 청구서 및 환영 키트와 같은 안전하고 개인화된 인터랙티브한 통신의 작성, 수집 및 전달을 중앙 집중화하여 관리합니다.

적응형 문서를 사용하면 매력적인 반응형, 동적 및 적응형 고객 커뮤니케이션을 만들 수 있습니다. AEM Forms은 적응형 문서를 만들기 위해 드래그 앤 드롭 WYSIWYG 편집기를 제공합니다.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

목표:

* 양식 데이터 모델을 기반으로 적응형 문서의 인쇄 및 웹 출력을 만들 수 있습니다.
* 고객에게 정보를 표시하는 적응형 양식의 레이아웃 필드
* 양식 데이터 모델에서 적응형 문서로 정보를 검색하고 표시하는 규칙을 만듭니다.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## 3단계:적응형 문서 필드에 규칙 적용(웹 채널만 해당) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

적응형 문서는 적응형 문서 객체에 대한 규칙을 작성하는 편집기를 제공합니다. 이러한 규칙은 문서의 사전 설정된 조건 및 사용자 작업을 기반으로 문서 객체에 대해 트리거할 작업을 정의합니다. 응용 문서의 웹 버전에서 정확성을 보장하고 사용자 경험을 빠르게 하는 데 도움이 됩니다. 적응형 문서 규칙 및 규칙 편집기에 대한 자세한 내용은 [규칙 편집기](/help/forms/using/rule-editor.md)를 참조하십시오.

목표:

* 적응형 문서의 웹 채널 필드에 규칙을 만들고 적용합니다
* 규칙을 사용하여 웹 채널에서 문서 데이터 모델 서비스를 트리거합니다.

## 4단계:응용 문서 스타일 지정(웹 채널만 해당) {#step-style-the-adaptive-document-web-channel-only}

응용 문서는 응용 문서 및 인라인 스타일링을 위한 테마를 만드는 편집기를 제공합니다. 테마에 구성 요소 및 패널에 대한 스타일 지정 세부 사항이 포함되어 있으며 다른 문서의 웹 채널에서 테마를 다시 사용할 수 있습니다. 스타일은 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성을 포함합니다. 문서에 테마를 적용하면 지정된 스타일이 문서의 해당 구성 요소에 반영됩니다. 자세한 내용은 [테마](/help/forms/using/themes.md)를 참조하십시오.

목표:

* 응용 문서 웹 채널에 대한 테마 만들기
* 응용 문서 웹 채널에 테마 적용
* 모바일 장치 및 데스크탑에서 응용 문서 웹 채널의 모양을 확인합니다

## 5단계:응용 문서 {#step-publish-the-adaptive-document} 게시

응용 문서 작성을 마쳤으면 에이전트가 응용 문서를 사용하여 응용 문서를 기반으로 통신 인스턴스를 만들 수 있는 게시 인스턴스에서 응용 문서를 사용할 수 있도록 하려면 해당 문서를 게시해야 합니다.

응용 문서를 게시하려면 문서 작성자에게 필요한 권한이 있어야 합니다.
