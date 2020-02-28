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
source-git-commit: 9b6c1efe1f6281892648c7b41820856d2e3fcac1

---


# 알려진 문제 {#known-issues}

이 페이지에는 2018년 4월에 릴리스된 Adobe Experience Manager 6.4의 알려진 문제 목록이 표시됩니다. 알려진 문제에 대한 자세한 내용은 지원 [센터에 문의하십시오](https://helpx.adobe.com/support/experience-manager.html).

## 하이브리드 장치 {#hybrid-devices}

하이브리드 장치는 지원되지 않습니다. 이러한 장치를 사용할 때 다양한 문제가 발생할 수 있습니다. 다음의 제안된 절차는 많은 문제를 해결하는 데 도움이 됩니다.

Google Chrome을 브라우저로 사용하는 경우:
* 주소 `chrome://flags/` 표시줄에 입력하고 Enter 키를 누릅니다.
* 터치 이벤트 활성화 > 비활성화를 클릭합니다.
* 브라우저를 다시 시작합니다(모든 탭 및 창).

Mozilla Firefox를 브라우저로 사용하는 경우:
* 주소 `about:config` 표시줄에 입력하고 Enter 키를 누릅니다.
* 설정을 필터링합니다 `dom.w3c`.
* 설정이 `0` 및 `false`인지 확인합니다.
* 브라우저를 다시 시작합니다.

Microsoft Edge를 브라우저로 사용하는 경우:

* 주소 `about:flags` 표시줄에 입력하고 Return 키를 누릅니다.
* 시험적 기능으로 스크롤 후 터치를 **[!UICONTROL 선택합니다]**.
* 터치 **[!UICONTROL 이벤트]**&#x200B;활성화를 클릭합니다.
* [항상 **[!UICONTROL 끄기]를 선택합니다]**.
* 브라우저를 다시 시작합니다.

## 플랫폼 {#platform}

* **** 작업 대시보드:백업 파일에 .zip 확장명이 없는 경우 진행률 표시줄이 표시되지 않습니다. (GRANITE-10713)
* **** HTL:패키지 선언에서 후행 공백이 있는 Java Use 개체가 SightlyJavaCompilerService를 중지합니다(GRANITE-20836)
* **** Apache Felix/Sling:configuration.delete()(GRANITE-20618) 후에도 구성 파일이 저장소에 여전히 있습니다.
* **** 클라우드 설정:구성 컨테이너 편집 후 콘솔이 끊어집니다(GRANITE-20726).
* **** 보안:IMS 통합이 사용자 지정 컨텍스트 경로와 실패했습니다(GRANITE-20639).
* **** 보안:SSO, 외부 및 기본 로그인 모듈의 기본 JAAS 등급 개선(GRANITE-20590)
* **** 도구 - CRX DE Lite:속성 보기의 리지(GRANITE-12040)
* **** 도구 - CRX DE Lite:속성 이름을 두 번 클릭하지 않으면 &quot;Long&quot; 값 형식에 대한 변경 내용을 저장할 수 없습니다(GRANITE-12351).

* **** 도구 - CRX DE Lite:RegExp 검색 시 Ctrl+F 검색(GRANITE-5996)

* **** 도구 - CRX DE Lite:노드 이름을 바꾼 후 노드 속성이 표시되지 않음(GRANITE-7160)
* **** UI:풀다운 &quot;자세히...&quot; ie 및 Firefox의 팝업 요소에서 열 때 일부 요소가 표시되지 않음(GRANITE-16326)
* **** UI:두 개의 나란히 열이 있는 고정 열 레이아웃을 사용할 때 정보 툴팁이 숨겨집니다(GRANITE-16869).
* **** UI:존재하지 않는 사용자로 가장할 때 처리되지 않은 오류가 발생했습니다(GRANITE 파섹-23228). 오류 메시지를 사용자 지정하기 위해 오류 처리기를 [](/help/sites-developing/customizing-errorhandler-pages.md) 구현하여 해결했습니다.

* **** Omnisearch:백슬래시 원인 예외를 사용한 검색(GRANITE-11769)
* **** Omnisearch:검색 필터가 변경되는 목록 보기에서 &quot;설정 보기&quot;를 엽니다(GRANITE-16524).
* **** Omnisearch:사이트에서 자산 검색을 수행할 때 표시되는 열 구성 목록이 잘못되었습니다(GRANITE-16527).

* **** Omnisearch:왼쪽 레일 예측자가 Omnisearch 서버 요청을 수행하고 있습니다(GRANITE-20524).
* **** Omnisearch:Omnisearch는 컨텍스트 경로를 지원하지 않습니다(GRANITE-16044).

## 자산 {#assets}

* **검색**:검색 문자열이 공백으로 시작하는 경우 검색에서 결과가 반환되지 [않습니다. OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **검색**:클래식 UI에서 태그는 검색에 표시되지 않습니다(CQ-4235239).

* **UI**:복사-붙여넣기 및 전체 선택 후 자산 UI가 응답하지 않음(CQ-4236142)

* **UI**:레이지 로드 후 자산을 이동할 수 없습니다(CQ-4236134).

* **보고서**:자산 수정 보고서 생성 오류(CQ-4239744)

* **보고서**:예약된 일반 자산 보고서 생성이 일관되게 실패합니다(일부 보고서는 큐에 있음)(CQ-4239089).

* **메타데이터**:자산 스키마에 다중 값 텍스트 필드를 추가하면 필수 필드 계단식 규칙이 작동하지 않습니다(CQ-4239333).

* **브랜드 포털**:BrandPortal에 게시가 컬렉션에서 작동하지 않습니다(CQ-4238731).

* **업로드**:파일 이름에 특수 문자가 포함된 에셋을 업로드할 때 허용되지 않은 문자에 대한 유효성 검사 오류 메시지가 각 에셋에 대해 표시되지 않습니다. 첫 번째 에셋에 대해서만 표시되지만 제공된 에셋의 파일 이름이 허용되지 않는다는 것을 인터페이스가 명확하게 나타냅니다. (CQ-4256876)

## 커뮤니티 {#communities}

* **중재** - 벌크 중재 UI에서 상위 게시물을 단일 삭제 작업으로 삭제할 수 없음(CQ 파섹-4236797)

* **콘솔** - [사용자 이름 분실] 또는 [암호 분실] 링크가 해당 암호 검색 양식 대신 로그인 페이지로 리디렉션되고 있습니다(CQ-4237682).

## 양식 {#forms}

### 설치 및 배포

* (AEM Forms JEE만 해당) Configuration Manager를 실행하는 동안 JBoss 응용 프로그램 서버를 부트스트랩할 때 EJB 호출 및 부트스트랩 실패 오류가 반환됩니다. 하지만 무시해도 됩니다. (Ref# CQ-4229793)

### 대화형 통신

* 에이전트 UI는 차트나 이미지 요소를 포함하는 대화형 통신을 로드하는 데 시간이 오래 걸립니다. (CQ-4236630)
* 인쇄 미리 보기의 데이터 표시 형식은 dd-mm-yyyy이지만 웹 미리 보기는 `dd-mmm-yy` (CQ-4237045)
* Interactive Communication Web 채널은 순차 목록과 비순차 목록만 지원합니다. 목록 문서 조각에서 복합 목록 및 들여쓰기는 대화형 통신의 웹 채널에서 지원되지 않습니다. (CQ-4233672)
* 웹 채널이 인쇄 채널과 동기화할 때 다음 문제가 관찰됩니다.

   * 인쇄 채널에서 처음 전환할 때 웹 채널을 동기화하려면 시간이 오래 걸립니다.
   * 인쇄 채널에 구성되지 않은 차트 구성 요소가 포함된 경우 웹 채널이 동기화되지 않습니다. 문제를 해결하려면 차트 구성 요소를 삭제하고 다시 동기화하십시오.
   * &quot;Live Copy 동기화 중 오류가 발생했습니다&quot; 오류로 인해 동기화가 실패하는 경우가 있습니다. 문제를 해결하려면 페이지를 새로 고칩니다.
   * 표의 첫 번째 열이 인쇄 채널 템플릿의 머리글 열이면 레이아웃 조각의 정적 텍스트가 표 셀 이름으로 바뀝니다.
   * 웹 채널 통신 하단의 다른 위치에 구성 요소나 자산을 추가할 수 없습니다. 다른 위치에 배치하려면 웹 채널 하단에 패널을 추가하고 컨텐츠 트리를 사용하여 순서를 변경합니다.
   * Live Copy 상속을 제거하지 않고 컨텐츠를 웹 채널의 상속된 타겟 영역으로 이동할 수 있습니다.

(CQ-4239780)

### 데이터 통합

* SOAP 기반 웹 서비스에 대한 인증 구성이 보이지 않으므로 클라우드 서비스에서 구성할 수 없습니다. 문제를 해결하려면 다음을 수행하십시오.

   1. CRXDE Lite 콘솔에서 다음 노드로 이동합니다.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. 값 속성 값을 text 속성 값과 동일하게 업데이트합니다.
   1. 모두 저장을 클릭하여 구성을 저장합니다.

(CQ-4238462)

### Adobe Sign 통합

* Adobe Sign 스케줄러는 간헐적으로 작업을 중단하므로 양식 대기 중인 서명이 제출로 이동하지 않습니다. 이 문제를 해결하려면 https://의 AEM **웹 콘솔에서** Apache Sling [*Scheduler Support*]&#x200B;번들을&#x200B;[**]&#x200B;다시 시작하십시오.port/system/console/bundles.

### 적응형 양식 작성

* 적응형 양식의 차트 구성 요소는 일반적으로 사용하는 것보다 더 많은 공간을 차지합니다.
* 적응형 양식, 적응형 양식 조각 또는 Forms Manager UI의 대화형 통신에 대한 속성을 저장할 때 예외가 반환됩니다.
* 적응형 양식 텍스트 상자에 지정된 최대 문자 수가 Android 6.0 Samsung 장치에 적용되지 않습니다. (Ref# CQ-4235205)
