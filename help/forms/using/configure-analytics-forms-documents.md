---
title: 분석 및 보고서 구성
seo-title: Configuring analytics and reports
description: 적응형 양식, 적응형 문서 및 HTML5 양식을 사용하는 동안 사용자가 직면하는 상호 작용 패턴 및 문제를 발견하도록 Adobe Analytics을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure Adobe Analytics to discover interaction patterns and problems users face while using adaptive forms, adaptive documents, and HTML5 forms.
uuid: f5671600-e1e2-4fef-9e47-6c8ede027700
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: 6301e0ef-3faa-4e6f-932d-37b049577cec
exl-id: a55999a8-a92b-4750-bf05-ee326d079f65
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 3%

---

# 분석 및 보고서 구성 {#configuring-analytics-and-reports}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms은 게시된 양식 및 문서에 대한 성능 지표를 캡처하고 추적할 수 있도록 Adobe Analytics과 통합됩니다. 이러한 지표를 분석하는 목적은 양식이나 문서를 보다 유용하게 만드는 데 필요한 변경 사항에 대한 데이터를 기반으로 정보에 입각한 결정을 내리는 것입니다.

>[!NOTE]
>
>AEM Forms의 분석 기능은 AEM Forms 추가 기능 패키지의 일부로 사용할 수 있습니다. 추가 기능 패키지 설치에 대한 자세한 내용은 [AEM Forms 설치 및 구성](/help/forms/using/installing-configuring-aem-forms-osgi.md).
>
>추가 기능 패키지 외에 AEM 인스턴스에 대한 Adobe Analytics 계정 및 관리자 권한이 필요합니다. 솔루션에 대한 자세한 내용은 [Adobe Analytics](https://www.adobe.com/solutions/digital-analytics.html).

## 개요 {#overview}

Adobe Analytics을 사용하여 적응형 양식, HTML 5 양식 및 대화형 커뮤니케이션을 사용하는 동안 사용자가 직면하는 상호 작용 패턴 및 문제를 발견할 수 있습니다. 기본적으로 Adobe 분석은 다음 매개 변수에 대한 정보를 추적하고 저장합니다.

* **평균 채우기 시간**: 양식을 채우는 데 걸린 평균 시간입니다.
* **표현물**: 양식을 연 횟수입니다.
* **초안**: 양식을 초안 상태로 저장한 횟수입니다.
* **제출**: 양식을 제출한 횟수입니다.
* **Abort**: 사용자가 양식을 완료하지 않고 나가는 횟수입니다.

Adobe Analytics을 사용자 지정하여 더 많은 매개 변수를 추가/제거할 수 있습니다. 위의 정보와 함께 보고서에는 HTML5 및 적응형 양식의 모든 패널에 대한 다음 정보가 포함되어 있습니다.

* **시간**: 패널 및 패널의 필드에서 보낸 시간.
* **오류**: 패널 및 패널의 필드에서 발생한 오류 수입니다.
* **도움말**: 사용자가 패널의 도움말과 패널의 필드를 여는 횟수입니다.

## 보고서 세트 만들기 {#creating-report-suite}

Analytics 데이터는 보고서 세트라는 고객별 리포지토리에 저장됩니다. 보고서 세트를 만들고 Adobe Analytics을 사용하려면 유효한 Adobe Marketing Cloud 계정이 있어야 합니다. 다음 단계를 수행하기 전에 유효한 Adobe Marketing Cloud 계정이 있는지 확인하십시오.

보고서 세트를 만들려면 다음 단계를 수행하십시오.

1. 에 로그인합니다. [https://sc.omniture.com/login/](https://sc.omniture.com/login/)
1. Marketing Cloud에서 **관리** > **Admin Console** >  **보고서 세트**.
1. 선택 **새로 만들기** > **보고서 세트** 를 입력합니다.

   ![새 보고서 세트 만들기](assets/newreportsuite.png)

   새 보고서 세트 만들기

1. 첫 번째 드롭다운 목록이 **템플릿에서 만들기** 그런 다음 **상거래**.

1. 을(를) 찾습니다 **보고서 세트 ID** 필드를 작성하고 새 보고서 세트 ID를 추가합니다. 예: JJEsquire. 보고서 세트 ID는 보고서 세트 ID 필드 아래에 표시됩니다. 자동 접두사가 포함되어 있으며, 이 접두사는 종종 회사 이름입니다.

1. 새로 추가 **사이트 제목**. 예를 들어 JJEsquire Getting Started Suite. 이 제목은 Analytics UI에서 사용됩니다. 코드에서 보고서 세트 ID를 사용합니다.

1. 선택 **시간대** 드롭다운 이 보고서 세트에 들어오는 모든 데이터는 정의된 시간대를 기반으로 기록됩니다.

1. 을(를) 종료하십시오. **기본 URL** 및 **기본 페이지** 필드가 비어 있습니다. 이 두 값은 Adobe Marketing Cloud 인터페이스에서 웹 사이트에 연결하는 데만 사용됩니다.
1. 을(를) 종료하십시오. **Go Live 날짜** 오늘로 설정합니다. Go Live Date 는 보고서 세트가 활성화되는 날짜를 결정합니다.

1. 에서 **예상 일별 페이지 보기 수** 필드에 100을 입력합니다. 이 필드를 사용하여 일별 웹 사이트에 대해 예상되는 페이지 보기 수를 예측합니다. 이 추정치를 통해 Adobe은 수집하려는 데이터를 처리하기 위해 적절한 양의 하드웨어를 배치할 수 있습니다.

1. 선택 **기본 통화** 드롭다운 이 보고서 세트에 들어오는 모든 통화 데이터는 이 통화 형식으로 변환되어 저장됩니다.

1. 클릭 **보고서 만들기** 세트. 보고서 세트가 성공적으로 만들어졌다는 메시지와 함께 페이지 새로 고침이 표시됩니다.

1. 새로 만든 보고서 세트를 선택합니다. 다음으로 이동 **설정 편집** > **일반** >  **일반 계정 설정**.

   ![일반 계정 설정](assets/geographic_settings.png)
   **그림:** *일반 계정 설정*

1. 일반 계정 설정 화면에서 을 활성화합니다 **지역 보고**&#x200B;를 클릭하고 **저장**.
1. 다음으로 이동 **설정 편집** > **트래픽** > **트래픽 변수**.

1. 보고서 세트에서 다음 트래픽 변수를 구성하고 활성화합니다.

   * **formName**: 적응형 양식의 식별자입니다.
   * **formInstance**: 적응형 양식 인스턴스의 식별자입니다. 이 변수에 대한 경로 보고서 를 활성화합니다.
   * **fieldName**: 적응형 양식 필드의 식별자입니다. 이 변수에 대한 경로 보고서 를 활성화합니다.
   * **panelName**: 적응형 양식 패널의 식별자입니다. 이 변수에 대한 경로 보고서 를 활성화합니다.
   * **formTitle**: 양식의 제목입니다.
   * **fieldTitle**: 양식 필드의 제목입니다.
   * **panelTitle**: 양식 패널의 제목입니다.
   * **analyticsVersion**: 양식 분석 버전입니다.

1. 다음으로 이동 **설정 편집** > **전환** >  **성공 이벤트**. 다음 성공 이벤트를 정의하고 활성화합니다.

   | 성공 이벤트 | 유형 |
   |---|---|
   | 포기 | 카운터 |
   | 렌더링 | 카운터 |
   | panelVisit | 카운터 |
   | fieldVisit | 카운터 |
   | 저장 | 카운터 |
   | 오류 | 카운터 |
   | 도움말 | 카운터 |
   | 제출 | 카운터 |
   | time체류 시간 | 숫자 |

   >[!NOTE]
   >
   >AEM Forms Analytics를 구성하는 데 사용되는 이벤트 번호 및 prop 번호는 에 사용되는 이벤트 번호 및 prop 번호와 달라야 합니다 [AEM analytics](/help/sites-administering/adobeanalytics.md) 구성.

1. Adobe Marketing Cloud 계정에서 로그아웃합니다.

## Cloud Service 구성 만들기 {#creating-cloud-service-configuration}

Cloud Service 구성은 Adobe Analytics 계정에 대한 정보입니다. 이 구성을 통해 Adobe Experience Manager(AEM)이 Adobe Analytics에 연결할 수 있습니다. 사용하는 각 Analytics 계정에 대해 별도의 구성을 만듭니다.

1. 관리자로 AEM 작성자 인스턴스에 로그인합니다.
1. 왼쪽 상단 모서리에서 **Adobe Experience Manager** > **도구** ![도구](assets/tools.png)> **Cloud Services** > **기존 Cloud Services**.
1. 찾기 **Adobe Analytics** 아이콘. 클릭 **구성 표시** 그런 다음 **[+]** 새 구성을 추가하려면

   처음 사용하는 사용자는 **지금 구성**.

1. 새 구성에 제목 을 추가합니다(이름 필드 채우기는 선택 사항). 예: 내 분석 구성. **만들기**&#x200B;를 클릭합니다.

1. 구성 페이지에서 편집 패널이 열리면 다음 필드를 채웁니다.

   * **회사**: Adobe Analytics에서 다루고 있는 회사 이름입니다.

   * **사용자 이름**: Adobe Analytics에 로그인하는 데 사용되는 이름입니다.

   * **암호**: 위의 계정에 대한 Adobe Analytics 암호입니다.

   * **데이터 센터**: Adobe Analytics 계정의 데이터 센터.

1. 클릭 **Analytics에 연결**. 연결에 성공했다는 메시지가 표시된 대화 상자가 나타납니다. **확인**&#x200B;을 클릭합니다.

## Cloud Service 프레임워크 만들기 {#creating-cloud-service-framework}

Adobe Analytics 프레임워크은 Adobe Analytics 변수와 AEM 변수 간의 매핑 세트입니다. 프레임워크를 사용하여 양식에서 Adobe Analytics 보고서에 데이터를 채우는 방법을 구성합니다. 프레임워크는 Adobe Analytics 구성과 관련되어 있습니다. 각 구성에 대해 여러 프레임워크를 만들 수 있습니다.

1. AEM 클라우드 서비스 콘솔에서 을(를) 클릭합니다. **구성 표시**&#x200B;아래에 그룹화됩니다.

1. 을(를) 클릭합니다. **[+]** Analytics 구성 옆에 있는 를 클릭합니다.

   ![Adobe Analytics 구성](assets/adobe-analytics-cloud-services.png)
   **그림:** *Adobe Analytics 구성*

1. 입력 **제목** 및 **이름** 프레임워크에 대해 을(를) 선택합니다. **Adobe Analytics** 프레임워크를 클릭하고 **만들기**. 편집할 프레임워크가 열립니다.

1. 사이드 Pod의 보고서 세트 섹션에서 **항목 추가**&#x200B;그런 다음 드롭다운을 사용하여 프레임워크가 상호 작용하는 보고서 세트 ID(예: JJEsquire)를 선택합니다.

1. 보고서 세트 ID 옆의 보고서 세트에 정보를 전송할 서버 인스턴스를 선택합니다.

   ![information_to_send_to_report_suite](assets/information_to_send_to_report_suite.png)

1. 드래그 **Form Analytics 구성 요소** 에서 **기타** SideKick에서 프레임워크로 카테고리입니다.
1. Analytics 변수를 구성 요소에 정의된 변수와 매핑하려면 AEM Content Finder에서 추적 구성 요소의 필드로 드래그합니다.

   ![AEM 변수와 Adobe Analytics 변수 매핑](assets/analytics.png)

1. 를 사용하여 프레임워크 활성화 **페이지 탭** 사이드킥에서 **프레임워크 활성화**.

## AEM Forms Analytics 구성 서비스 구성 {#configuring-aem-forms-analytics-configuration-service}

1. 작성자 인스턴스에서 https://&lt;*server*>:&lt;*포트*>/system/console/configMgr.
1. AEM Forms Analytics 구성 찾기 및 열기

   ![AEM Forms Analytics 구성 서비스](assets/analytics_configuration.png)
   **그림:** *AEM Forms Analytics 구성 서비스*

1. 다음 필드에 적절한 값을 지정하고 **저장**.

   * **SiteCatalyst 프레임워크**: 추적 프레임워크 설정 섹션에서 정의한 프레임워크/구성을 선택합니다.
   * **필드 시간 추적 기준**: 필드 방문을 추적해야 하는 기간(초)을 지정합니다. 기본값은 0입니다. 값이 0(영)을 초과하면 별도의 두 추적 이벤트가 Adobe Analytics 서버로 전송됩니다. 첫 번째 이벤트는 Analytics 서버에 종료한 필드 추적을 중지하도록 지시합니다. 두 번째 이벤트는 지정된 기간이 지난 후 전송됩니다. 두 번째 이벤트는 Analytics 서버가 방문 필드 추적을 시작하도록 지시합니다. 두 개의 별도 이벤트를 사용하면 한 필드에서 체류한 시간을 정확하게 측정할 수 있습니다. 값이 0(영)이면 단일 추적 이벤트가 Adobe Analytics 서버로 전송됩니다.
   * **Analytics 보고서 동기화 크론**: Adobe Analytics에서 보고서를 가져올 크론 식을 지정합니다. 기본값은 0 0 2 ?
   * **보고서 시간 제한 가져오기:** 서버가 Analytics 보고서에 응답할 때까지 대기하는 기간(초)을 지정합니다. 기본 시간은 120초입니다.

   >[!NOTE]
   >
   >보고서 가져오기 작업을 시간 초과하고 지정된 시간(초)에 대해 최대 10초가 더 걸릴 수 있습니다.

1. 게시 인스턴스에서 1-3단계를 반복하여 분석을 구성합니다.

이제, 양식에 대한 분석을 활성화하고 분석 보고서를 생성할 수 있습니다.

## 양식 또는 문서에 대한 분석 활성화 {#enabling-analytics-for-a-form-or-document}

1. AEM 포털에 로그인합니다. `https://[hostname]:[port]`.
1. 클릭 **Forms > Forms 및 문서**&#x200B;를 클릭하고 폼이나 문서를 선택한 다음 **Analytics 활성화**. 분석 기능이 활성화되어 있습니다.

   ![양식 또는 문서에 대한 분석 활성화](assets/enable-analytics-1.png)
   **그림:** *양식에 대한 분석 활성화*

   **A.** Analytics 활성화 단추 **B.** 선택한 양식

   Forms Analytics 보고서 보기에 대한 자세한 내용은 [AEM Forms 분석 보고서 보기 및 이해](/help/forms/using/view-understand-aem-forms-analytics-reports.md)
