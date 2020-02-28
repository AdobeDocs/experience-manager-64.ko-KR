---
title: 게시 안 함 간단한 응용 문서 만들기
seo-title: 게시 안 함 간단한 응용 문서 만들기
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 게시 안 함 간단한 응용 문서 만들기 {#do-not-publish-create-your-first-adaptive-document}

## 사용 사례 {#use-case}

Adobe Finance는 금융 서비스 분야의 선도적인 조직으로 다양한 고객 프로파일의 요구 사항에 맞게 포괄적이고 개인화된 금융 솔루션을 제공합니다.

고객의 자동차 보험 증권 중 하나가 만료되고 있으며 갱신 견적서와 함께 인터랙티브한 PDF를 포함하는 알림 메시지를 보냅니다. 또한 충성도 보상, 할인 혜택 등 다른 정보도 포함되어 있습니다.

포털은 Adobe AEM에서 실행됩니다. 웹 및 인쇄 시작 채널 출력은 적응형 문서의 다중 채널 기능을 사용하여 만들어집니다.

자습서 끝에 다음과 유사한 응용 문서가 있습니다.[ ad-1 ![](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)[ ad-2 ![](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)간단한 적응형 문서 자습서 만들기는 단계로 분류됩니다. 각 단계 자체에서 전체 아티클이 됩니다.

<table> 
 <tbody>
  <tr>
   <th>학습은</th> 
   <th>
    <ul> 
     <li>적응형 문서 및 양식 데이터 모델 만들기</li> 
     <li>적응형 문서를 위한 템플릿 및 테마 만들기</li> 
     <li>규칙 편집기를 사용하여 비즈니스 규칙 작성<br /> </li> 
     <li>응용 문서 게시. <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>전제 조건</td> 
   <td>
    <ul> 
     <li>AEM 작성자 인스턴스를 설정합니다. </li> 
     <li>AEM Forms 추가 기능 설치. 자세한 내용은 AEM <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">Forms 설치 및 구성을 참조하십시오</a>.</li> 
     <li>데이터베이스 공급자로부터 JDBC 데이터베이스 드라이버(JAR 파일)를 얻습니다. 자습서의 예는 MySQL 데이터베이스를 기반으로 하며 Oracle의 MySQL JDBC 데이터베이스 드라이버를 사용합니다. </li> 
     <li>고객 데이터가 포함된 데이터베이스를 설정합니다. 데이터베이스는 응용 문서를 만드는 데 필요합니다. 이 자습서에서는 데이터베이스를 사용하여 AEM Forms의 양식 데이터 모델 및 지속성 기능을 표시합니다. </li> 
     <li>인쇄 및 웹 채널용 <a href="/help/forms/using/web-channel-print-channel.md">템플릿 만들기/가져오기 및 활성화</a>.</li> 
     <li>FDM을 <a href="/help/forms/using/document-fragments.md">기반으로 문서 조각이 있는지 확인합니다</a>.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Step 1: Create Form Data Model {#step-create-form-data-model}

양식 데이터 모델을 사용하면 적응형 문서를 서로 다른 데이터 소스에 연결할 수 있습니다. 예: AEM 사용자 프로필, RESTful 웹 서비스, SOAP 기반 웹 서비스, OData 서비스 및 관계형 데이터베이스. 양식 데이터 모델은 연결된 데이터 소스에서 사용할 수 있는 비즈니스 개체 및 서비스의 통합된 데이터 표현 스키마입니다. 응용 문서와 함께 양식 데이터 모델을 사용하여 연결된 데이터 소스에서 데이터를 검색할 수 있습니다. 양식 데이터 모델에 대한 자세한 내용은 AEM Forms [데이터 통합을 참조하십시오](/help/forms/using/data-integration.md).

목표:

* 데이터베이스 인스턴스(Microsoft Dynamics)를 데이터 소스로 구성
* Microsoft Dynamics를 데이터 소스로 사용하여 양식 데이터 모델 만들기
* 양식 데이터 모델에 데이터 모델 개체 추가
* 양식 데이터 모델에 대한 읽기 및 쓰기 서비스 구성
* 테스트 데이터를 사용하여 양식 데이터 모델 및 구성된 서비스 테스트

## 2단계:응용 문서 만들기 {#step-create-an-adaptive-document}

고객 커뮤니케이션은 비즈니스 서신, 편지, 문서, 명세서, 혜택 통지, 자산 관리 설명서, 마케팅 이메일, 청구서 및 환영 키트와 같은 안전하고 개인화된 인터랙티브한 통신의 작성, 조합 및 전달을 중앙 집중화하고 관리합니다.

적응형 문서를 사용하면 매력적이고 응답적이며 다이내믹하고 적응성이 높은 고객 커뮤니케이션을 제작할 수 있습니다. AEM Forms에서는 드래그 앤 드롭 방식의 WYSIWYG 편집기를 사용하여 적응형 문서를 만듭니다.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

목표:

* 양식 데이터 모델을 기반으로 적응형 문서의 인쇄 및 웹 출력을 만들 수 있습니다.
* 고객에게 정보를 표시하는 적응형 양식의 레이아웃 필드
* 양식 데이터 모델에서 적응형 문서로 정보를 검색하고 표시하는 규칙을 만듭니다.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## 3단계:적응형 문서 필드에 규칙 적용(웹 채널만 해당) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

응용 문서는 응용 문서 개체에 대한 규칙을 작성할 수 있는 편집기를 제공합니다. 이러한 규칙은 문서의 사전 설정 조건 및 사용자 작업을 기반으로 문서 객체에 대해 트리거할 동작을 정의합니다. 이 플러그인을 사용하면 적응형 문서의 웹 버전에서 사용자 경험을 정확하게 하고 가속화시킬 수 있습니다. 적응형 문서 규칙 및 규칙 편집기에 대한 자세한 내용은 [규칙 편집기를](/help/forms/using/rule-editor.md)참조하십시오.

목표:

* 적응형 문서의 웹 채널 필드에 규칙 만들기 및 적용
* 규칙을 사용하여 웹 채널에서 문서 데이터 모델 서비스 트리거

## 4단계:응용 문서 스타일 지정(웹 채널만 해당) {#step-style-the-adaptive-document-web-channel-only}

적응형 문서는 적응형 문서 및 인라인 스타일에 대한 테마를 만드는 편집기를 제공합니다. 테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있으며 다른 문서의 웹 채널에서 테마를 재사용할 수 있습니다. 스타일은 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성을 포함합니다. 문서에 테마를 적용하면 지정된 스타일이 문서의 해당 구성 요소에 반영됩니다. 자세한 내용은 테마를 [참조하십시오](/help/forms/using/themes.md).

목표:

* 적응형 문서 웹 채널에 대한 테마 만들기
* 적응형 문서 웹 채널에 테마 적용
* 모바일 디바이스 및 데스크탑에서 적응형 문서 웹 채널의 모습 확인

## 5단계:응용 문서 게시 {#step-publish-the-adaptive-document}

응용 문서 만들기가 완료되면 에이전트가 응용 문서를 사용하여 응용 문서를 기반으로 통신 인스턴스를 만들 수 있는 게시 인스턴스에서 사용할 수 있도록 응용 문서를 게시해야 합니다.

응용 문서를 게시하려면 문서 작성자가 필요한 권한을 가져야 합니다.
