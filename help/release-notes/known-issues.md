---
title: AEM 6.4의 알려진 문제
seo-title: AEM 6.4의 알려진 문제
description: Adobe Experience Manager 6.4의 알려진 문제
seo-description: Adobe Experience Manager 6.4의 알려진 문제.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 5%

---


# 알려진 문제 {#known-issues}

이 페이지는 2018년 4월에 릴리스된 Adobe Experience Manager 6.4의 알려진 문제 목록을 유지합니다. 알려진 문제에 대한 자세한 내용은 지원 센터[에 문의하십시오.](https://helpx.adobe.com/kr/support/experience-manager.html)

## 하이브리드 장치 {#hybrid-devices}

하이브리드 장치는 지원되지 않습니다. 이러한 장치를 사용할 때 다양한 문제가 발생할 수 있습니다. 다음 제안된 절차는 많은 문제를 해결하는 데 도움이 됩니다.

Google Chrome을 브라우저로 사용하는 경우:

* 주소 표시줄에 `chrome://flags/`을 입력하고 Enter 키를 누릅니다.
* 터치 이벤트 활성화 > 비활성화됨을 클릭합니다.
* 브라우저를 다시 시작합니다(모든 탭 및 창).

Mozilla Firefox를 브라우저로 사용하는 경우:

* 주소 표시줄에 `about:config`을 입력하고 Enter 키를 누릅니다.
* 설정을 `dom.w3c`으로 필터링합니다.
* 설정이 `0` 및 `false`인지 확인합니다.
* 브라우저를 다시 시작합니다.

Microsoft Edge를 브라우저로 사용하는 경우:

* 주소 표시줄에 `about:flags`을 입력하고 Return 키를 누릅니다.
* 시험 기능으로 스크롤한 다음 **[!UICONTROL 터치]**&#x200B;로 스크롤합니다.
* **[!UICONTROL 터치 이벤트 활성화]**&#x200B;를 클릭합니다.
* **[!UICONTROL 항상 해제]**&#x200B;를 선택합니다.
* 브라우저를 다시 시작합니다.

## 플랫폼 {#platform}

* **작업 대시보드:** 백업 파일에 .zip 확장명이 없는 경우 진행률 표시줄이 표시되지 않습니다. (GRANITE-10713)
* **HTL:** Java Use 객체가 패키지 선언에서 후행 공백이 있으면 SightlyJavaCompilerService가 정지됩니다(GRANITE-20836).
* **configuration.delete()(** GRANITE-20618) 후에도 Apache Felix/Sling:Config 파일이 저장소에 계속 있습니다.
* **클라우드 설정:** 구성 컨테이너 편집 후 콘솔 연결이 끊깁니다(GRANITE-20726).
* **보안:** IMS 통합이 사용자 지정 컨텍스트 경로(GRANITE-20639)와 실패했습니다.
* **보안:** SSO, 외부 및 기본 로그인 모듈의 기본 JAAS 등급 개선(GRANITE-20590)
* **도구 - CRX DE Lite:** 속성 보기의 리지 상태가 계속 위로 이동합니다(GRANITE-12040).
* **도구 - CRX DE Lite: 속성 이름을 두 번 클릭하지 않으면 &quot;긴&quot; 값 유형에 대한 변경 내용을 저장할** 수 없습니다(GRANITE-12351).

* **도구 - CRX DE Lite:열린 텍스트 파일에서** ctrl+F 검색은 RegExp 검색에 고정됩니다(GRANITE-5996).

* **도구 - 노드 이름 변경 후 CRX DE Lite:** Node 속성이 표시되지 않음(GRANITE-7160)
* **UI:** &quot;자세히..&quot; 풀다운 IE 및 Firefox의 팝업 요소에서 열 때 모든 요소가 표시되지 않음(GRANITE-16326)
* **UI:** 2개의 나란히 열을 사용하는 고정 열 레이아웃을 사용할 때 정보 도구 설명이 숨겨집니다(GRANITE-16869).
* **UI:** 존재하지 않는 사용자로 가장하는 경우 처리되지 않은 오류가 발생했습니다(GRANITE-23228). 오류 메시지를 사용자 지정하기 위해 [오류 핸들러](/help/sites-developing/customizing-errorhandler-pages.md)를 구현하는 방법에 대한 해결책

* **Omnisearch:** 백슬래시 원인 예외 검색(GRANITE-11769)
* **Omnisearch:목록 보기에서** &quot;보기 설정&quot;을 열면 검색 필터가 변경됩니다(GRANITE-16524).
* **Omnisearch:** 사이트에서 자산 검색을 수행할 때 표시되는 열 구성의 잘못된 목록(GRANITE-16527)

* **Omnisearch:** 왼쪽 레일 예측자가 Omnisearch 서버 요청(GRANITE-20524)과 함께 진행 중입니다.
* **Omnisearch:** Omnisearch는 컨텍스트 경로를 지원하지 않습니다(GRANITE-16044).

## 자산 {#assets}

* **검색**:검색 문자열이 공백 OAK-4786으로 시작하는 경우 검색 결과 [는 반환되지 않습니다.](https://issues.apache.org/jira/browse/OAK-4786)

* **검색**:클래식 UI에서 태그는 검색에 표시되지 않습니다(CQ-4235239).

* **UI**:복사-붙여넣기 및 모두 선택(CQ-4236142) 후 자산 UI가 응답하지 않습니다.

* **UI**:지연 로드 후 자산을 이동할 수 없습니다(CQ-4236134).

* **보고서**:자산 수정 보고서 생성 오류(CQ-4239744)

* **보고서**:예약된 일반 자산 보고서 생성에 일관성 없이 실패함(일부 보고서는 큐에 있음) (CQ-4239089)

* **메타데이터**:자산 스키마에 다중 값 텍스트 필드를 추가하면 필수 필드 계단식 규칙이 작동하지 않습니다(CQ-4239333).

* **BrandPortal**:BrandPortal에 게시가 컬렉션에 대해 작동하지 않습니다(CQ-4238731).

* **업로드**:파일 이름에 특수 문자가 포함된 에셋을 업로드할 때 허용되지 않는 문자에 대한 유효성 검사 오류 메시지가 각 에셋에 대해 표시되지 않습니다. 첫 번째 에셋에 대해서만 표시되지만, 인터페이스는 제공된 에셋의 파일 이름이 허용되지 않음을 사용자에게 분명히 나타냅니다. (CQ-4256876)

## 커뮤니티 {#communities}

* **중재**  - 벌크 중재 UI에서 단일 삭제 작업으로 상위 게시물을 삭제할 수 없습니다(CQ-4236797).

* **콘솔**  - [사용자 이름 분실] 또는 [암호 분실] 링크가 해당 암호 검색 양식 대신 로그인 페이지로 리디렉션됩니다(CQ-4237682).

## 양식 {#forms}

### 설치 및 배포

* (AEM Forms JEE에만 해당) Configuration Manager를 실행하는 동안 JBoss 응용 프로그램 서버를 부트스트래핑하면 EJB 호출 및 부트스트랩 오류 오류가 반환됩니다. 하지만, 여러분은 그것들을 무시할 수 있습니다. (Ref# CQ-4229793)
* AEM Forms가 시작되면 `SAX Security Manager could not be setup`라는 경고가 나타납니다. (CQ-4297403)

### 대화형 통신

* 에이전트 UI는 차트 또는 이미지 요소를 포함하는 대화형 통신을 로드하는 데 시간이 걸립니다. (CQ-4236630)
* 인쇄 미리 보기의 데이터 표시 형식은 dd-mm-yyyy이지만 웹 미리 보기는 `dd-mmm-yy`(CQ-4237045)입니다.
* Interactive Communication Web 채널은 순차 목록과 비순차 목록만 지원합니다. 목록 문서 조각에서 복합 목록 및 들여쓰기는 대화형 통신 웹 채널에 대해 지원되지 않습니다. (CQ-4233672)
* 웹 채널이 인쇄 채널과 동기화할 때 다음 문제가 관찰됩니다.

   * 인쇄 채널에서 처음 전환하는 경우 웹 채널을 동기화하려면 시간이 걸립니다.
   * 인쇄 채널에 구성되지 않은 차트 구성 요소가 포함된 경우 웹 채널이 동기화되지 않습니다. 문제를 해결하려면 차트 구성 요소를 삭제하고 다시 동기화하십시오.
   * 동기화하면 &quot;Live Copy를 동기화하는 동안 오류가 발생했습니다.&quot; 오류가 발생하는 경우가 있습니다. 문제를 해결하려면 페이지를 새로 고칩니다.
   * 표의 첫 번째 열이 인쇄 채널 템플릿의 머리글 열일 때 레이아웃 조각의 정적 텍스트는 표 셀 이름으로 바뀝니다.
   * 웹 채널 통신 하단의 다른 위치에 구성 요소나 자산을 추가할 수 없습니다. 다른 위치에 배치하려면 웹 채널 하단에 패널을 추가하고 컨텐츠 트리를 사용하여 순서를 변경합니다.
   * Live Copy 상속을 제거하지 않고도 컨텐츠를 웹 채널의 상속된 대상 영역으로 이동할 수 있습니다.

(CQ-4239780)

### 데이터 통합

* SOAP 기반 웹 서비스에 대한 인증 구성이 보이지 않으므로 클라우드 서비스에서 구성할 수 없습니다. 문제를 해결하려면 다음을 수행하십시오.

   1. CRXDE Lite 콘솔에서 다음 노드로 이동합니다.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. value 속성 값을 text 속성 값과 동일하게 업데이트합니다.
   1. 모두 저장을 클릭하여 구성을 저장합니다.

(CQ-4238462)

### Adobe Sign 통합

* Adobe Sign 스케줄러는 간헐적으로 작업을 중단하므로 대기 중인 양식은 제출로 이동하지 않습니다. 이 문제를 해결하려면 https://[*server*]:[*port*]/system/console/bundle의 AEM 웹 콘솔에서 **Apache Sling 스케줄러 지원** 번들을 다시 시작하십시오.

### 적응형 Forms 저작

* 적응형 양식의 차트 구성 요소는 일반적으로 사용하는 것보다 더 많은 공간을 차지합니다.
* Forms Manager UI에서 적응형 양식, 적응형 양식 단편 또는 인터랙티브한 커뮤니케이션에 대한 속성을 저장할 때 예외가 반환됩니다.
* 적응형 양식 텍스트 상자에 지정된 최대 문자 수가 Android 6.0 Samsung 장치에 적용되지 않습니다. (Ref# CQ-4235205)
