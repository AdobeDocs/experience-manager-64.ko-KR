---
title: 커뮤니티 기능에 대한 Analytics 구성
seo-title: 커뮤니티 기능에 대한 Analytics 구성
description: 커뮤니티에 대한 분석 구성
seo-description: 커뮤니티에 대한 분석 구성
uuid: 625a253f-b198-40e8-b34c-dff337fb0eff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 36ea97a4-4e13-4e89-866b-495f3c30cb94
role: Admin
exl-id: cb2f61df-73bb-47f7-86ce-feda4772c8d0
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2787'
ht-degree: 4%

---

# 커뮤니티 기능에 대한 Analytics 구성 {#analytics-configuration-for-communities-features}

## 개요 {#overview}

Adobe Analytics과 Adobe Experience Manager(AEM)은 모두 Adobe Marketing Cloud의 솔루션입니다.

Adobe Analytics이 AEM Communities에 대해 구성되어 구성원이 지원되는 커뮤니티 기능과 상호 작용하므로 보고서가 생성되는 Adobe Analytics으로 이벤트가 전송됩니다.

예를 들어 지원 커뮤니티 사이트의 구성원이 할당된 비디오 리소스를 보는 경우 리소스 플레이어는 비디오 하트비트 데이터를 포함하여 이벤트를 Analytics에 보냅니다. 커뮤니티 사이트에서 관리자는 비디오 재생과 관련된 다양한 보고서를 볼 수 있습니다.

또한 다음을 위해 analytics가 필요합니다.

* 게시 환경에서:

   * 커뮤니티 [트렌드 보고](trends.md)
   * 사이트 방문자가 &quot;가장 많이 본&quot;, &quot;가장 활성&quot;, &quot;가장 좋아하는&quot; 순으로 정렬할 수 있습니다
   * UGC 목록에서 카운트 보기

* 작성 환경에서:

   * [구성원 관리 콘솔에서 기여도 데이터 표시](members.md)(보기, 게시물, 다음, 좋아요)
   * 지원 리소스 [reports](reports.md)에 대한 트렌드 요약, 비디오 하트비트 및 비디오 장치

지원되는 커뮤니티 기능은 다음과 같습니다.

* [지원 리소스](resources.md)
* [포럼](forum.md)
* [QnA](working-with-qna.md)
* [블로그](blog-feature.md)
* [파일 라이브러리](file-library.md)
* [달력](calendar.md)

설명서의 이 섹션에서는 Analytics 보고서 세트를 커뮤니티 기능과 연결하는 방법을 설명합니다. 기본 단계는 다음과 같습니다.

1. [암호화 키](#replicate-the-crypto-key) 를 복제하여 모든 AEM 인스턴스에서 암호화/암호 해독이 올바르게 수행되도록 합니다
1. Adobe Analytics [보고서 세트 준비](#adobe-analytics-report-suite-for-video-reporting)
1. AEM Analytics [클라우드 서비스](#aem-analytics-cloud-service-configuration) 및 [프레임워크](#aem-analytics-framework-configuration)를 만듭니다
1. [커뮤니티 ](#enable-analytics-for-a-community-site) 사이트에 대한 Analytics 활성화
1. [](#verify-analytics-to-aem-variable-mapping) Analytics에서 AEM으로 변수 매핑 확인
1. [기본 게시자](#primary-publisher) 식별
1. [](#publish-community-site-and-analytics-cloud-service) 커뮤니티 사이트 게시
1. Adobe Analytics에서 커뮤니티 사이트로 보고서 데이터](#obtaining-reports-from-analytics)의 [가져오기를 구성합니다

## 전제 조건 {#prerequisites}

Analytics for Communities 기능을 구성하려면 계정 담당자에게 Adobe Analytics 계정 및 [보고서 세트](#adobe-analytics-report-suite-for-video-reporting)를 설정해야 합니다. 설정하고 나면 다음 정보를 사용할 수 있습니다.

* 회사 이름

   Adobe Analytics 계정과 연결된 회사입니다
* 사용자 이름

   Analytics 계정을 관리할 권한이 있는 사용자의 로그인 사용자 이름입니다

   (웹 서비스 액세스 권한을 포함해야 합니다.)

* 암호

   인증된 사용자의 로그인 암호

* Analytics 데이터 센터

   계정에 대한 Analytics 데이터 센터의 URL입니다

* 보고서 세트

   사용할 Analytics 보고서 세트의 이름입니다

## 비디오 보고를 위한 Adobe Analytics 보고서 세트 {#adobe-analytics-report-suite-for-video-reporting}

Adobe Marketing Cloud의 [보고서 세트 관리자](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html)를 사용하여 커뮤니티 사이트에서 커뮤니티 기능에 대한 보고서를 제공할 수 있도록 Analytics 보고서 세트를 구성할 수 있습니다.

[회사 이름 및 사용자 이름](analytics.md#prerequisites)을 사용하여 [Adobe Marketing Cloud](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/home.html)에 로그인하면 다음과 같은 새 보고서 세트 또는 기존 보고서 세트를 구성할 수 있습니다.

* [11개의 전환 변수](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) (evar)

   * **`evar1`** 사용  **`evar11`** 안 함
   * 기존 evar를 재사용하거나(이름 변경) 새 evar를 만들어 커뮤니티 기능에 사용할 수 있습니다

* [7 성공 이벤트](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/success-events/success-event.html) (이벤트)

   * **`event1`** 사용  **`event7`** 안 함
   * 유형 **`Counter`**

      * 아님 **`Counter (no subrelations)`**
   * 기존 이벤트를 재사용하거나(이름 변경) 새 이벤트를 만들어 커뮤니티 기능에 사용할 수 있습니다


* [비디오 관리](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)

   * 비디오 보고 콘솔

      * 사용 `Video Core`
      * 저장을 선택합니다
   * 비디오 코어 측정 콘솔

      * 선택 `Use Solution Variables`
      * 저장을 선택합니다


**새 보고서 세트를 사용하는 경우 새 보고서 세트에는 4개의 evar와 6개의 이벤트 변수만 있을 수 있고, Communities에는 11개의 evar 및 7개의 이벤트 변수가 필요합니다.**

**기존 보고서 세트**&#x200B;를 사용하는 경우 커뮤니티 사이트에 대한 Analytics 프레임워크를 활성화하기 전에 [변수 매핑](#modifying-analytics-variable-mapping)을 수정해야 할 수 있습니다. 커뮤니티 전용 변수와 관련된 사항은 계정 담당자에게 문의하십시오.

>[!CAUTION]
>
>**내에서 이미 변수를 사용하는 기존 보고서 세트를 사용하는 경우**
>
>* **`evar1`** ~ **`evar11`**
>* **`event1`** ~ **`event7`**

>
>
**그런 다음 커뮤니티 사이트가 게시되기 전에 커뮤니티 사이트에 대해 Analytics가 활성화되었을 때 자동으로 Analytics 변수에 매핑된 AEM 변수를 이동하여 기존 매핑을 복원하는 것이** 중요합니다.
>
>기존 매핑을 복원하고 AEM 변수를 다른 Analytics 변수로 이동하려면 [Analytics 변수 매핑 수정](#modifying-analytics-variable-mapping)의 섹션을 참조하십시오.
>
>이를 실패하면 복구할 수 없는 데이터 손실이 발생할 수 있습니다.

### 비디오 하트비트 분석 {#video-heartbeat-analytics}

비디오 하트비트 Analytics에 라이센스가 있으면 `Marketing Cloud Org Id`이 할당됩니다.

비디오 보고에 대한 Analytics 보고서 세트를 구성 [한 후 비디오 하트비트 보고를 활성화하려면](#adobe-analytics-report-suite-for-video-reporting):

* [Analytics 클라우드 서비스](#aem-analytics-cloud-service-configuration) 만들기
* 커뮤니티 사이트에 대해 [Analytics 활성화](#enable-analytics-for-a-community-site)
* `Marketing Cloud Org Id`을(를) 커뮤니티 사이트와 연결

`Marketing Cloud Org Id`은 [커뮤니티 사이트 생성](sites-console.md#enablement) 시 또는 [커뮤니티 사이트 속성 수정](sites-console.md#modifying-site-properties)에 의해 입력될 수 있습니다. [](#aem-analytics-cloud-service-configuration)

![chlimage_1-264](assets/chlimage_1-264.png)

비디오 하트비트 Analytics가 활성화되면 비디오 플레이어에 대한 JS(Javascript) 코드는 비디오 하트비트 라이브러리 코드(JS에서도)를 인스턴스화합니다. 이 코드는 10초마다(구성할 수 없음) 비디오 상태 업데이트를 Analytics 비디오 추적 서버로 전송하는 모든 논리를 처리하며 결국 비디오 세션의 누적 보고서를 기본 Analytics 서버로 보냅니다.

활성화되지 않은 경우 비디오 하트비트 코드가 인스턴스화되지 않고 비디오 진행 및 위치 추적 다시 시작만 보고를 위해 SRP로 유지됩니다.

## AEM Analytics Cloud 서비스 구성 {#aem-analytics-cloud-service-configuration}

작성자 인스턴스에서 표준 UI를 사용하여 Adobe Analytics과 AEM 커뮤니티 사이트를 통합하는 새 Analytics 통합을 만들려면:

* 전역 탐색에서: **[!UICONTROL 도구 > 배포 > Cloud Services]**
* **[!UICONTROL Adobe Analytics]**&#x200B;로 스크롤합니다.
* **[!UICONTROL 지금 구성]** 또는 **[!UICONTROL 구성 표시]**&#x200B;를 선택합니다.

![chlimage_1-265](assets/chlimage_1-265.png)

### 구성 만들기 대화 상자 {#create-configuration-dialog}

* **[!UICONTROL 사용 가능한 구성]** 옆에 있는 `[+]` 아이콘을 선택하여 새 구성을 만듭니다

구성 만들기 대화 상자에서 입력할 값이 구성을 식별합니다.

![chlimage_1-266](assets/chlimage_1-266.png)

* **[!UICONTROL 제목]**

   (필수) 구성에 대한 표시 제목입니다.

   예를 들어 *지원 커뮤니티 분석*&#x200B;을 입력합니다.

* **[!UICONTROL 이름]**

   (선택 사항) 지정하지 않으면 기본적으로 이름이 제목에서 파생된 올바른 노드 이름으로 설정됩니다.

   예를 들어 *communities*&#x200B;를 입력합니다.


* **[!UICONTROL 템플릿]**

   선택 `Adobe Analytics Configuration`

* **[!UICONTROL 만들기]**&#x200B;를 선택합니다
   * 구성 페이지를 시작하고 `Analytics Settings` 대화 상자를 엽니다.

### Analytics 설정 대화 상자 {#analytics-settings-dialog}

새 Analytics 구성을 처음 만들면 Analytics 설정 항목에 대한 구성 및 새 대화 상자가 표시됩니다. 이 대화 상자를 사용하려면 계정 담당자에게 받은 [전제 조건 계정 정보](#prerequisites)가 필요합니다.

![chlimage_1-267](assets/chlimage_1-267.png)

* **[!UICONTROL 회사]**

   Adobe Analytics 계정과 연결된 회사입니다

* **[!UICONTROL 사용자 이름]**

   Analytics 계정을 관리할 권한이 있는 사용자의 로그인 사용자 이름입니다

* **[!UICONTROL 암호]**

   인증된 사용자의 로그인 암호

* **[!UICONTROL 데이터 센터]**

   보고서 세트를 호스팅하는 Analytics 데이터 센터를 선택합니다

* **[!UICONTROL 페이지에 추적 태그를 추가하지 않음]**

   기본값으로 둡니다(선택 안 함).

* **[!UICONTROL AppMeasurement 사용]**

   기본값으로 둡니다(선택 안 함).

* **[!UICONTROL 페이지 노출을 매일 밤 가져오지 않음(작성자)]**

   기본값으로 둡니다(선택 안 함).

* **[!UICONTROL 페이지 노출을 매일 밤 가져오지 않음(게시)]**

   기본값으로 둡니다(선택됨).

설정을 저장하려면 다음을 수행합니다.


* **[!UICONTROL Analytics에 연결]**&#x200B;을 선택합니다.

   * 성공하지 못하면

      * 항목에 선행 공백 없음 확인
      * 다른 데이터 센터 시도
      * 계정 담당자에게 문의하십시오

* **[!UICONTROL 확인]** 선택


![chlimage_1-268](assets/chlimage_1-268.png)

### 프레임워크 만들기 {#create-framework}

Adobe Analytics에 대한 기본 연결을 성공적으로 구성한 후에는 커뮤니티 사이트에 대한 프레임워크를 만들거나 편집해야 합니다. 이 프레임워크의 목적은 커뮤니티 기능(AEM) 변수를 Analytics(보고서 세트) 변수에 매핑하는 것입니다.

* **[!UICONTROL 사용 가능한 프레임워크]** 옆에 있는 `[+]` 아이콘을 선택하여 새 프레임워크를 만듭니다

![chlimage_1-269](assets/chlimage_1-269.png)

* **[!UICONTROL 제목]**

   (필수) 프레임워크의 표시 제목입니다

   예를 들어 *지원 커뮤니티 프레임워크*&#x200B;를 입력합니다.

* **[!UICONTROL 이름]**

   (선택 사항) 지정하지 않으면 기본적으로 이름이 제목에서 파생된 올바른 노드 이름으로 설정됩니다.

   예를 들어 *communities*&#x200B;를 입력합니다.

* **[!UICONTROL 템플릿]**

   선택 `Adobe Analytics Framework`

* **[!UICONTROL 만들기]**&#x200B;를 선택합니다

Analytics 프레임워크를 만들면 구성에 대한 프레임워크가 열립니다.

## AEM Analytics 프레임워크 구성 {#aem-analytics-framework-configuration}

프레임워크의 목적은 AEM 변수를 Analytics 변수(evar 및 이벤트)에 매핑하는 것입니다. 매핑에 사용할 수 있는 Analytics 변수는 보고서 세트](#adobe-analytics-report-suite-for-video-reporting)에 정의된 [입니다.

![chlimage_1-270](assets/chlimage_1-270.png)

### 보고서 세트 선택 {#select-report-suite}

비디오 보고에 대해 설정된 보고서 세트를 선택합니다.

보고서 세트가 아직 만들어지지 않았거나 제대로 설정되지 않은 경우에는 이전 섹션을 참조하십시오.\
[비디오 보고를 위한 Adobe Analytics 보고서 세트](#adobe-analytics-report-suite-for-video-reporting)

사이드 킥이 필요하지 않으며 보고서 세트 설정에 대한 액세스를 방해하지 않도록 최소화할 수 있습니다.

#### &#39;항목 추가&#39;를 선택하기 전후에 보고서 세트 대화 상자 {#report-suites-dialog-before-and-after-selecting-add-item}

![chlimage_1-271](assets/chlimage_1-271.png)

1. **[!UICONTROL 항목 추가 +]** 드롭다운 상자가 두 개 나타납니다
1. 회사 계정과 연결된 보고서 세트를 선택할 수 있도록 하려면 `Report suite` 을 선택합니다
1. 대화 상자에서 **[!UICONTROL Yes]**&#x200B;를 선택합니다. ```Load default server settings? Do you want to load the default server settings and overwrite current values in the Server section?```
1. `Run Mode` 선택\
   **[!UICONTROL 게시]** 선택

![chlimage_1-272](assets/chlimage_1-272.png)

이제 Analytics 클라우드 서비스 및 프레임워크가 완료되었습니다. 매핑은 이 Analytics 서비스가 활성화된 상태에서 커뮤니티 사이트가 생성되면 정의됩니다.

## 커뮤니티 사이트에 대한 Analytics 활성화 {#enable-analytics-for-a-community-site}

### 새 커뮤니티 사이트에 사용 {#enable-for-new-community-site}

[새 커뮤니티 사이트를 만드는 동안 Analytics 클라우드 서비스를 추가하려면](sites-console.md):


* 3단계에서
* [ANALYTICS 탭](sites-console.md#analytics)에서 다음을 수행합니다.

   * **[!UICONTROL Analytics]** 활성화 확인란을 선택합니다
   * 드롭다운 상자에서 프레임워크를 선택합니다

* 선택적으로 Analytics 프레임워크 구성으로 돌아가 변수 매핑을 조정하십시오.

### 기존 커뮤니티 사이트에 대해 활성화 {#enable-for-existing-community-site}

Analytics 클라우드 서비스를 [기존 커뮤니티 사이트](sites-console.md#modifying-site-properties)에 추가하려면:


* **[!UICONTROL 커뮤니티 > 사이트]** 콘솔로 이동합니다.
* 커뮤니티 사이트의 사이트 편집 아이콘을 선택합니다
* 설정 선택
* Analytics 섹션에서 다음을 수행합니다.

   * **[!UICONTROL Analytics]** 활성화 확인란을 선택합니다
   * 드롭다운 상자에서 프레임워크를 선택합니다


* 선택적으로 Analytics 프레임워크 구성으로 돌아가 변수 매핑을 조정하십시오.

### 사용자 지정된 사이트에 대해 활성화 {#enable-for-customized-sites}

Analytics 추적 및 가져오기가 커뮤니티 사이트에 대해 제대로 작동하려면 `scf-js-site-title` 클래스 및 href 특성이 있는 페이지 요소가 있어야 합니다. 커뮤니티 사이트에 대한 수정되지 않은 `sitepage.hbs` 스크립트에서 그러하듯이 그러한 요소는 페이지에만 있어야 합니다. `siteUrl` 값이 추출되어 *사이트 경로*&#x200B;로 Adobe Analytics에 전송됩니다.

```xml
# present in default sitepage.hbs
# only one scf-js-site-title class should be included
# this example sets it to be hidden as it serves no visual purpose
<div
    class="navbar-brand scf-js-site-title"
    href="{{siteUrl}}.html"
    style="visibility: hidden;"
>
</div>
```

`sitepage.hbs` 스크립트를 오버레이하는 **사용자 지정된 커뮤니티 사이트**&#x200B;의 경우 요소가 있는지 확인하십시오. `siteUrl`변수는 클라이언트에 제공하기 전에 서버에서 렌더링될 때 설정됩니다.

커뮤니티 구성 요소를 포함하지만 [사이트 만들기 마법사](sites-console.md)로 만들어지지 않은 **일반 AEM 사이트**&#x200B;의 경우 요소를 추가해야 합니다. href의 값은 사이트의 경로여야 합니다. 예를 들어 사이트 경로가 `/content/my/company/en`이면 다음을 사용합니다.

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## Analytics for Communities 기능 {#analytics-for-communities-features}

Analytics는 여러 커뮤니티 기능에 자동으로 사용됩니다.

작성 환경의 [OSGi 구성](../../help/sites-deploying/configuring-osgi.md) `AEM Communities Analytics Component Configuration` 은 Analytics용으로 구현된 구성 요소 목록을 제공합니다. 변수의 자동 매핑은 나열된 구성 요소에 의해 결정됩니다.

Analytics용으로 구현된 새 사용자 지정 구성 요소를 만드는 경우 구성된 구성 요소 목록에 추가해야 합니다.

### 구성 요소 구성 {#component-configuration}

![chlimage_1-273](assets/chlimage_1-273.png)

참고: `journal` 구성 요소는 블로그 기능을 구현하는 데 사용됩니다.

### AEM 변수에 Analytics가 매핑됨 {#mapped-analytics-to-aem-variables}

커뮤니티 사이트가 Analytics가 활성화되고 클라우드 구성 프레임워크가 선택된 상태로 저장되면 AEM 변수가 각각 evar1 및 event1로 시작하는 Analytics evar 및 이벤트에 자동으로 매핑되고 1씩 증가합니다.

evar1에서 evar11까지 및 event1에서 event7까지 변수 중 하나를 매핑하는 기존 보고서 세트를 사용하는 경우 [AEM 변수를 다시 매핑하고 원래 매핑을 복원해야 합니다.](#modifying-analytics-variable-mapping)

다음은 [시작하기 자습서](getting-started-enablement.md)를 따르는 후의 기본 매핑의 예입니다.

![chlimage_1-274](assets/chlimage_1-274.png)

#### 각 이벤트와 함께 전송된 eVar 맵 {#map-of-evars-sent-with-each-event}

|  | 사용 리소스 유형 | 사이트 제목 | 함수 유형 | 그룹 제목 | 그룹 경로 | UGC 유형 | UGC 제목 | 사용자(구성원) | UGC 경로 | 사이트 경로 |
|------------------------|------------------------|-----------|--------------|------------|-----------|---------|----------|--------------|---------|----------|
|  | **eVar1** | **eVar2** | **eVar3** | **eVar4** | **eVar5** | **eVar6** | **eVar7** | **eVar8** | **eVar9** | **eVar10** |
| event1리소스 재생 | (관리) | - | - | - | - | - | - | - | 자. | - |
| event2SCFVview | (관리) | 나. | 다. | (d) | (e) | 바. | 사. | (h) | 자. | 차. |
| event3SCFCreate(Post) | - | 나. | 다. | 라. | 마. | 바. | 사. | 아. | 자. | 차. |
| event4SCFFollow | - | 나. | 다. | 라. | 마. | 바. | 사. | 아. | 자. | 차. |
| event5SCFVoteUp | - | 나. | 다. | 라. | 마. | 바. | 사. | 아. | 자. | 차. |
| event6SCFVoteDown | - | 나. | 다. | 라. | 마. | 바. | 사. | 아. | 자. | 차. |
| event7SCFRate | - | 나. | 다. | 라. | 마. | 바. | 사. | 아. | 자. | 차. |

**eVar 값의 예:**

* [MIME 유형](https://www.iana.org/assignments/media-types): video/mp4
* [커뮤니티 사이트 제목](sites-console.md#step13asitetemplate): Geometrixx 커뮤니티
* [커뮤니티 함수 이름](functions.md): 포럼
* [커뮤니티 그룹 이름](creating-groups.md#creating-a-new-group): 하이킹
* 커뮤니티 그룹 컨텐츠에 대한 경로: /content/sites/communities/en/groups/hiking
* [UGC 구성 요소 resourceType](essentials.md): social/forum/components/hbs/topic
* UGC 구성 요소 제목: 하이킹 항목
* 로그인(승인 가능한 Id): aaron.mcdonald@mailinator.com
* UGC에 대한 SRP 경로: /content/usergenerated/asi/.../forum/jmtz-topic3 또는 *다음에 추가할 구성 요소 경로*: /content/sites/communities/en/jcr:content/content/primary/forum
* 커뮤니티 사이트 컨텐츠에 대한 경로: /content/sites/community/en

### Analytics 변수 매핑 수정 {#modifying-analytics-variable-mapping}

커뮤니티 사이트에 대해 Analytics가 활성화되면 AEM 변수에 Analytics evar 및 이벤트 매핑이 프레임워크 구성에서 볼 수 있습니다.

Analytics가 활성화되고 커뮤니티 사이트가 게시되기 전에 왼쪽 레일에서 원하는 Analytics evar 또는 이벤트를 끌어서 매핑 테이블의 관련 행에 놓아 프레임워크에서 매핑을 변경할 수 있습니다.

중복 매핑을 방지하려면 마우스를 해당 행에서 Analytics evar 또는 이벤트 를 제거하고 Analytics 변수 요소의 오른쪽에 표시되는 &quot;X&quot;를 선택하여 행에서 제거해야 합니다.

Communities evar 및 이벤트가 보고서 세트에 이전에 존재했던 매핑을 덮어쓴 경우 데이터 손실을 방지하기 위해 Communities용 AEM 변수를 다른 Analytics evar 및/또는 이벤트에 지정하고 원래 매핑을 복원합니다.

>[!CAUTION]
>
>커뮤니티 사이트가 [published](#publishing-the-community-site)이고 Analytics가 활성화되어 있기 전에 다시 매핑하는 것이 중요합니다. 그렇지 않으면 데이터가 손실될 수 있습니다.

#### 예제 1단계: Analytics evar14를 매핑 테이블로 드래그 {#example-step-dragging-analytics-evar-into-mapping-table}

![chlimage_1-275](assets/chlimage_1-275.png)

#### 예제 2단계: 대체된 evar11을 제거하려면 &#39;x&#39;를 선택합니다. {#example-step-selecting-x-to-remove-replaced-evar}

![chlimage_1-276](assets/chlimage_1-276.png)

#### 예제 3단계: AEM var eventdata.siteId가 Analytics evar14에 다시 매핑됨 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![chlimage_1-277](assets/chlimage_1-277.png)

## 커뮤니티 사이트 게시 {#publishing-the-community-site}

### Analytics에서 AEM로의 변수 매핑 확인 {#verify-analytics-to-aem-variable-mapping}

Analytics 클라우드 서비스 및 프레임워크를 게시하는 커뮤니티 사이트를 게시하기 전에 변수 매핑을 확인하는 것이 좋습니다.

섹션 을 참조하십시오.

* [AEM 변수에 Analytics가 매핑됨](#mapped-analytics-to-aem-variables)
* [Analytics 변수 매핑 수정](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**내에서 이미 변수를 사용하는 기존 보고서 세트를 사용하는 경우**
>
>* **`evar1`** ~ **`evar11`**
>* **`event1`** ~ **`event7`**

>
>
**그런 다음 커뮤니티 사이트가 게시되기 전에 기존 매핑을 복원하고 자동으로 매핑된 Communities AEM 변수(커뮤니티 사이트에 대해 Analytics가 활성화되었을 때)를 다른 Analytics 변수로 이동하는 것이** 중요합니다. 이 다시 매핑은 모든 Communities 구성 요소에서 일관되어야 합니다.
>
>이를 실패하면 복구할 수 없는 데이터 손실이 발생할 수 있습니다.

### 기본 게시자 {#primary-publisher}

선택한 배포가 [게시 팜](topologies.md#tarmk-publish-farm)인 경우, 보고서 데이터를 [SRP](working-with-srp.md)에 쓰기 위해 Adobe Analytics을 폴링하는 기본 게시자로 하나의 AEM 게시 인스턴스를 식별해야 합니다.

기본적으로 `AEM Communities Publisher Configuration` OSGi 구성은 게시 인스턴스를 기본 게시자로 식별하므로 게시 팜의 모든 게시 인스턴스가 주 게시자로 자가 식별됩니다.

따라서 모든 보조 게시 인스턴스의 구성을 편집하여 **기본 게시자** 확인란의 선택을 취소합니다.

특정 지침은 [커뮤니티 배포](deploy-communities.md#primary-publisher)의 기본 게시자 섹션을 참조하십시오.

>[!CAUTION]
>
>여러 게시 인스턴스에서 폴링을 방지하기 위해 기본 게시자를 구성하는 것이 중요합니다.

### 암호화 키 복제 {#replicate-the-crypto-key}

Adobe Analytics 자격 증명이 암호화되어 있습니다. 작성자와 게시자 간에 암호화된 Analytics 자격 증명을 복제하거나 전송하기 쉽도록 하려면 모든 AEM 인스턴스가 동일한 기본 암호화 키를 공유해야 합니다.

이렇게 하려면 [암호화 키 복제](deploy-communities.md#replicate-the-crypto-key)의 지침을 따르십시오.

### 커뮤니티 사이트 및 Analytics Cloud 서비스 게시 {#publish-community-site-and-analytics-cloud-service}

커뮤니티 사이트에 대해 Analytics 클라우드 서비스가 활성화되고, 필요한 경우 Analytics의 [AEM 변수에 대한 매핑이 조정되면 [(re)커뮤니티 사이트](sites-console.md#publishing-the-site)를 게시하여 게시 환경에 구성을 복제해야 합니다.](#mapped-analytics-to-aem-variables)

## Analytics에서 보고서 가져오기 {#obtaining-reports-from-analytics}

### 보고서 관리 {#report-management}

작성자 및 기본 게시자의 [OSGi 구성](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Report Management` 은 Analytics를 쿼리하는 데 사용됩니다.

작성자에서 쿼리는 실시간 보고서에 대한 것입니다.

기본 게시자에서 쿼리는 보고서 임포터의 Analytic 데이터 가져오기를 준비하기 위한 정보를 제공하는 데 사용됩니다.

쿼리 간격의 기본값은 10초입니다.

### 보고서 가져오기 {#report-importer}

Analytics가 활성화된 커뮤니티 사이트가 게시되면 기본 게시자의 [OSGi 구성](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Report Importer`이(가) CRXDE에 개별적으로 구성되지 않은 구성에 대한 기본 폴링 간격을 설정하도록 구성할 수 있습니다.

폴링 간격은 데이터를 [SRP](working-with-srp.md)에 가져오고 저장할 Adobe Analytics에 대한 요청 빈도를 제어합니다.

데이터가 &quot;빅 데이터&quot;로 분류될 수 있는 경우, 더 자주 투표하는 경우 커뮤니티 사이트에 큰 로드를 초래할 수 있습니다.

기본 폴링 **가져오기 간격**&#x200B;이 12시간으로 설정되어 있습니다.

![chlimage_1-278](assets/chlimage_1-278.png)

### 구성 요소 보고서 사용자 지정 {#component-report-customization}

현재, 추적할 지표를 사용자 지정하기 위해 저장소에 해당 지표에 대한 보고서를 생성할 기간을 정의하는 노드가 만들어집니다.

포럼 주제는 현재 이 사용자 지정의 유일한 예입니다.

* 기본 게시자에서
* 관리 권한으로 로그인
* [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)로 이동합니다.

   * 예: [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* 언어 루트의 `jcr:content` 노드 아래에 있습니다

   * 예, `/content/sites/engage/en/jcr:content`

* Analytics 보고에 대해 구성된 구성 요소로 이동합니다

   * 예, `analytics/reportConfigs/social_forum_components_hbs_topic`

* 생성된 기간을 확인합니다

   * `last30Days`
   * `last90Days`
   * `thisYear`

* `total`노드를 확인합니다.

   * `interval` 속성을 수정하면 보고서 가져오기 간격이 재정의됩니다
   * 이 값은 초 단위이며 4시간(14400초)으로 설정됩니다

![chlimage_1-279](assets/chlimage_1-279.png)

## Analytics에서 사용자 데이터 관리 {#manage-user-data-in-analytics}

Adobe Analytics에서는 사용자 데이터에 액세스, 내보내기 및 삭제할 수 있는 API를 제공합니다. 자세한 내용은 [액세스 및 삭제 요청 제출](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html)을 참조하십시오.

## 리소스 {#resources}

* Adobe Marketing Cloud: [Analytics 도움말 및 참조](https://docs.adobe.com/content/help/en/analytics/landing/home.html)
* AEM: [Adobe Analytics과 통합](../../help/sites-administering/adobeanalytics.md)
* AEM: [외부 공급자의 Analytics](../../help/sites-administering/external-providers.md)
