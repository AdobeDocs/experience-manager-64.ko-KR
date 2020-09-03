---
title: AEM 6.4 누적 수정 팩 릴리스 정보
description: Adobe Experience Manager 6.4 누적 수정 팩 관련 릴리스 노트입니다.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 5fefc81e68e64bcaa8df1d9648c4266367a92129
workflow-type: tm+mt
source-wordcount: '3331'
ht-degree: 26%

---


# AEM 6.4 누적 수정 팩 릴리스 정보 {#aem-cumulative-fix-pack-release-notes}

## 릴리스 정보 {#release-information}

| 제품 | **AEM(Adobe Experience Manager) 6.4** |
|---|---|
| 버전 | 6.4.8.2 |
| 유형 | 누적 수정 팩 |
| 날짜 | 2020년 9월 03일 |
| 전제 조건 | [AEM 6.4 서비스 팩 8(6.4.8.0)](sp-release-notes.md) |
| 다운로드 URL | AEM 6.4.8.2 [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-2.0.zip) |

## AEM 6.4.8.2에 포함된 기능 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.2는 2020년 3월 AEM 6.4 서비스 팩 8(6.4.8.0)을 일반적으로 사용할 수 있었던 이후 여러 가지 내부 및 고객 픽스를 포함하는 중요한 업데이트입니다.

AEM 6.4.8.2는 AEM 6.4 서비스 팩 8에 따라 제공되는 CFP(Cumulative Fix Pack)입니다. AEM 6.4 서비스 팩 8을 설치한 후 CFP를 설치합니다.

AEM 6.4.8.2에서는 내장된 저장소(Apache Jackrabbit Oak)가 버전 1.8.22로 업데이트됩니다.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

Adobe Experience Manager 6.4.8.2에서는 다음 문제에 대한 수정 사항을 제공합니다.

### 사이트 {#sites-6482}

* 롤아웃 구성 `RolloutConfigManagerFactoryImpl` 을 로드할 수 없는 경우 누락된 구성을 로드하지 않습니다. 캐시된 구성을 반환합니다(NPR-34091).
* 텍스트 코어 구성 요소에서 소스 HTML 편집 옵션을 사용한 후 태그의 `em` 클래스가 제거됩니다(NPR-34080).
* Experience Manager 6.2에서 Experience Manager 6.5로 업그레이드하는 경우 정적 템플릿의 Parsys 구성 요소가 올바르게 표시되지 않습니다. Parsys 구성 요소의 높이가 0으로 설정되고 이 구성 요소 내에 있는 구성 요소가 표시되지 않습니다(NPR-34044).
* 레이블 정보는 템플릿 편집기 내에서 허용되는 구성 요소에 표시되지 않습니다(NPR-33908).

   ![레이아웃 컨테이너에 레이블 없음](assets/33908_missing_labels.png)

* 사용자는 중첩된 구성 요소의 네 번째 수준 이후에 parsys에 구성 요소를 추가하거나 편집할 수 없습니다(NPR-33873).
* 편집 가능한 템플릿의 초기 컨텐츠가 변경된 다음 템플릿이 게시되는 경우, 페이지가 게시되지 않아도 이 템플릿으로 만들어진 새 페이지에는 템플릿의 게시된 날짜가 표시됩니다(NPR-33822).
* 복사본의 `cq:acLinks` 및 `cq:acUUID` [!DNL Adobe Campaign] 속성은 복사 및 붙여넣기 작업 중 제거됩니다(NPR-33793).
* 라이브 [!UICONTROL 사용량] 탭에서 49개의 결과만 표시됩니다. 구성 요소에 대한 모든 사용법은 표시되지 않습니다(NPR-33710).
* 작성하는 동안 URL에 `/` 문자가 포함된 웹 페이지가 응답하지 않습니다. 작성하는 동안 구성 요소가 추가되면 CPU 사용이 증가하고 브라우저가 응답을 중지합니다(NPR-33625).
* 의 인라인 편집 모드에서 이미지 [!DNL RTE]를 드래그하면 텍스트 구성 요소에 사용할 수 없습니다(NPR-33579).
* 페이지 이름과 동일한 이름으로 블루프린트 페이지에 구성 요소를 만들 수 있습니다. 롤아웃 중에 이러한 구성 요소의 이름은 접미어로 변경됩니다 `_msm_moved`. 하지만 구성 요소는 [!UICONTROL 단락 시스템] (NPR-33534)의 끝으로 이동합니다.
* 첫 번째 컨텐츠 루트에서 하위 페이지 [!UICONTROL 포함] 속성이 선택되지 않은 경우 론치 승격은 페이지를 게시하지 않습니다(NPR-33533).
* 앵커 [!DNL Experience Manager] `PageRedirectServlets` 가 있는 페이지로 리디렉션은 URL 조각 또는 앵커 뒤에 쿼리 문자열을 삽입하므로 작성자 인스턴스에서 작동하지 않습니다(NPR-34287).
* `PageRedirectServlet` 링크 실패로 연결되는 Sling 매핑 `.html` 후 추가합니다(NPR-34271).
* 페이지 [!DNL Live Copy] 를 일시 중단할 수 있으며 상속은 편집기 모드에서 보듯이 끊깁니다. 그러나 페이지 속성에서 상속을 나타내는 아이콘은 상속이 존재하며 끊어진 것이 아님을 잘못 나타냅니다(NPR-34096).
* 템플릿 편집 페이지의 허용된 구성 요소 표시 문제(CQ-4297295).
* Chrome 및 Firefox를 업그레이드한 후 팝업 메뉴가 예상대로 작동하지 않습니다. 페이지 속성을 로드할 때 패널에 데이터가 있으면 패널이 표시되지 않습니다(CQ-4292995).

### 자산 {#assets-6482}

* 업로드된 PDF 파일에 대한 텍스트 추출을 사용할 수 없으며 PDF 파일에서 일부 단어를 전체 텍스트로 검색하지 못했습니다(NPR-34165).

   >[!NOTE]
   >이 수정 사항을 적용하려면 서비스 팩 6.4.8.2를 설치한 후 Adobe Experience Manager 인스턴스를 다시 시작하십시오.

* 백슬래시는 이름에 특수 문자가 있는 자산의 검색 제안에서 특수 문자 앞에 추가됩니다(NPR-33833).

* 스마트 컬렉션으로 저장된 사용자 지정 필터가 자산에 올바르게 적용되지 않으므로 검색 결과가 정확하지 않습니다(NPR-33725).

* 순서가 변경된 폴더 내의 자산 타임라인은 자산이 이동되었음을 나타냅니다(NPR-33580).

* 자산에서 자산을 일괄 게시 취소하면 [!DNL Brand Portal] 오류가 `Request-URI Too Long` 발생합니다(NPR-34158).

* 사용자가 자산 세트를 선택한 후 [!UICONTROL 필터] 옵션을 선택한 다음(자산이 선택 해제됨) 이동할 다른 자산 세트를 선택하면 이전에 선택한 자산도 새 위치로 이동됩니다(NPR-34018).

* 스크롤 막대는 페이지에 맞는 많은 자산이 있더라도 목록 보기에 표시되지 않습니다(NPR-34156).

* 자산에 대한 [!UICONTROL 게시] 관리 페이지가 손상되어 해당 옵션이 작동하지 않습니다(CQ-4302509).

**Dynamic Media**

* 이미지 프로필을 여러 종횡비(예: 11)가 있는 폴더에 추가할 때 스마트 자르기 기능이 실패하므로 오류가 발생합니다(NPR-34083).

* Adobe Experience Manager의 이미지 사전 설정 변경 사항은 [!UICONTROL Scene7] Publishing System(NPR-34284, CQ-429713)과 동기화되지 않습니다.

* PANORAMICVIEW [!UICONTROL _AUTOMOTE] 수정자 레이블이 [!UICONTROL 뷰어 사전 설정 편집기] 페이지의 [!UICONTROL 동작] 탭에서 누락되었습니다(CQ-4302043).

### 플랫폼 {#platform-6482}

* 기본 에이전트(게시) 구성에 대한 **[!UICONTROL 연결 시간]** 제한 **[!UICONTROL 및]** 소켓 시간초과설정에 대한 기본값이 지정되지 않았습니다(NPR-33708).
* 유지 관리 작업 스케줄러는 구성된 것보다 자주 유지 관리 작업을 시작하고 중지합니다(NPR-33520).
* 업그레이드된 Experience Manager 인스턴스에서 진단 도구를 사용하여 로그를 다운로드할 수 없습니다(NPR-34419).

### 통합 {#integrations-6482}

* 마이그레이션된 라이브러리 `library_path` 에 대한 [!DNL Adobe Launch] 라이브러리 URL을 생성할 때 의 값은 고려되지 않습니다 [!DNL Adobe Dynamic Tag Management]. 또한 마이그레이션된 라이브러리는 라이브러리와 다른 접두사를 [!DNL Adobe Launch] 사용합니다. (NPR-34238).
* 클라우드 서비스에서 상속된 속성은 페이지 속성을 업데이트할 때 지속되지 않습니다(NPR-33865).

### 사용자 인터페이스 {#ui-6482}

* 검색 페이지에서 선택한 자산 수의 표시가 잘못되었습니다(NPR-33540).

### 커뮤니티 {#communities-6482}

* 관리 콘솔을 통해 추가된 커뮤니티 그룹의 기존 사용자는 커뮤니티 그룹 콘솔의 수정 사항에 대한 사용자 목록에서 제거됩니다(NPR-34312).

### 양식 {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] 누적 수정 팩에는 수정 사항이 포함되어 있지 않습니다 [!DNL Experience Manager Forms]. 이러한 수정 사항은 별도의 [!DNL Forms] 추가 기능 패키지를 사용하여 전달됩니다. 또한, JEE의 [!DNL Experience Manager Forms]에 대한 수정 사항이 포함된 누적 설치 프로그램이 릴리스됩니다. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

**적응형 양식**

* 응용 양식 조각이 누락된 경우 응용 양식이 렌더링되지 않습니다(NPR-34303).

* 적응형 양식 필드에 대한 도움말 내용 설명에 단락 HTML 태그가 표시됩니다(NPR-34117).

* 페이지에 Forms 컨테이너를 추가하면 페이지에 다음 오류 메시지가 표시되고 새 구성 요소를 추가할 수 없습니다(NPR-33858). [!DNL Experience Manager Sites]

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* [서버에서 **[!UICONTROL 재유효성 검사] 속성을]** 선택하고 여러 첨부 파일을 업로드하면 응용 양식이 제출되지 않습니다(NPR-33701).

* 페이지 언어 **[!UICONTROL 사용]** 및 **[!UICONTROL 양식이 페이지의 구성 요소]** 에서 페이지 [!DNL Experience Manager Forms] 옵션 [!DNL Experience Manager Sites] 의 전체 너비를 덮을 때페이지가 변환되지 않습니다(NPR-33641).

* 페이지에 포함된 분석 지원 응용 양식을 제출하면 분석이 올바르게 작동하지 않습니다(NPR-31359). [!DNL Experience Manager Sites]

* 라이브러리 [!DNL Lodash] 및 [!DNL backbone] 라이브러리에 대한 종속성을 제거했습니다(NPR-33458).

* REST에 **[!UICONTROL 제출 종단점]** 제출 작업은 응용 양식에 대해 작동하지 않습니다(NPR-34513).

* 접근성:필수 필드에 대한 첨부를 업로드하지 않고 적응형 양식을 제출하려고 하면 초점은 자동으로 첨부 필드로 이동하지 않습니다(NPR-34511).

**워크플로우**

* [!DNL Experience Manager] 워크플로우 제거 작업에 실패하고 다음 오류 메시지가 표시됩니다(NPR-33576).

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* 6.4.8.1 [!DNL Experience Manager] 을 설치할 때 항목의 [!UICONTROL To Do] 목록이 링크로 표시되지 않습니다. 할 일 항목 [!UICONTROL 에] 대한 텍스트에는 HTML 태그가 포함됩니다(NPR-34318).

**백엔드 통합**

* AWS 호스팅 [!DNL Experience Manager Forms Linux] 환경에서 양식 데이터 모델을 구성할 수 없습니다(NPR-33617).

**디자이너**

* Forms 서버 [!DNL Acrobat DC] 에 설치되어 있는 경우 [!DNL Experience Manager] 양식 **[!UICONTROL 배포 옵션은]** 버전 6.x(NPR-34325)에서 사용할 수 없습니다 [!DNL Experience Manager Designer] .

**문서 보안**

* 6.4.8.0을 설치한 후 PDF 파일에 HSM 기반 인증서로 서명 작업을 실행할 수 없습니다(NPR-34309). [!DNL Experience Manager]

**업그레이드**

* 환경에서 Document Security [!DNL JBoss] 에 대해 [!DNL Experience Manager Forms] [!DNL Linux] 7.0.9로 버전을 업그레이드하면 오류가 발생합니다(CQ-4300546).

보안 업데이트에 대한 자세한 내용은 [Experience Manager 보안 게시판 페이지를 참조하십시오](https://helpx.adobe.com/security/products/experience-manager.html).

## 이전 누적 수정 팩에 포함된 핫픽스 및 기능 팩 {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1은 2020년 3월 AEM 6.4 서비스 팩 8(6.4.8.0)의 일반 출시 이후 여러 가지 내부 및 고객 픽스를 포함하는 중요한 업데이트입니다.

AEM 누적 수정 팩 6.4.8.1은 AEM 6.4 서비스 팩 8에 따라 다릅니다. 따라서 AEM 6.4 서비스 팩 8을 설치한 후 AEM Cumulative Fix Pack 6.4.8.1 패키지를 설치해야 합니다.

AEM 6.4.8.1의 주요 특징 중 일부는 다음과 같습니다.

* Adobe Experience Manager와 패키지 공유 통합이 제거되었습니다.
* 내장된 저장소(Apache Jackrabbit Oak)가 버전 1.8.21으로 업데이트되었습니다.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

Adobe Experience Manager 6.4.8.1에서는 다음 문제에 대한 수정 사항을 제공합니다.

#### 사이트 {#sites-6481}

* LiveCopy의 로컬 구성 요소의 이름이 설계도에 있는 구성 요소의 이름과 동일하며 구성 요소가 블루프린트에서 롤아웃되는 경우, _msm_moved 용어는 로컬 구성 요소의 이름에 추가되지 않습니다(NPR-33207).
* 원래 요청에 추가된 매개 변수는 리디렉션 URL에 포함되지 않습니다(NPR-33174).
* Coral.Select 옵션이 emptyOption=true를 설정하거나 값이 &quot;&quot;인 기본 항목을 포함할 경우 dropdownshowide.js 파일에 오류가 발생합니다.처리할 수 없는 유형 오류:component.getValue가 함수가 아닙니다(NPR-33163).
* 구성 요소에 다른 구성 요소가 데이터-슬라이리소스로서 포함되어 있으면 상위 컨테이너 구성 요소 자리 표시자는 내부 구성 요소 자리 표시자(NPR-33119)로 대체됩니다.
* 스키마에 컨텐츠 조각을 기반으로 하고 필수 텍스트 영역 또는 경로 필드를 포함하는 경우 컨텐츠 조각이 저장되지 않습니다(NPR-33007)
* 기본 경험 조각 구성 요소를 사용하여 사용자 지정 구성 요소를 만들고 AEM Sites 페이지에서 사용하면 AEM에 사용자 지정 구성 요소에 대한 참조(사용량)를 표시하지 않습니다(NPR-32852).
* AEM Sites 페이지가 여러 Live Copy가 있는 큰 컨텐츠 세트의 일부인 경우 페이지 버전 기록 미리 보기가 로드되지 않습니다(NPR-32772).
* 론치를 승격하면 론치에 추가된 모든 구성 요소에 &quot;cq:LiveRelationship&quot; 믹스가 추가됩니다. 소스 페이지 라이브 데이터 상속 — 옵션(NPR-32664)을 선택하지 않고 론치가 작성되었는지 여부에 관계없이 모든 론치에 영향을 줍니다.
* 페이지 매김이 시작되면 경험 조각 선택기가 일부 항목을 로드하지 않습니다(NPR-32605).
* AEM Sites 페이지에 대한 론치를 만들 수 없습니다. 론치를 만들면 오류가 발생합니다(NPR-32544).
* 게시 관리에는 활성화 요청 워크플로에 참조된 자산이 포함되지 않습니다(NPR-32463).
* Dispatcher 상태 확인은 로그 파일에 `Invalid cookie header` 경고 메시지를 표시합니다(NPR-33630).
* Salesforce 통합은 SSRF에 취약합니다(NPR-32671).
* PreferencesServlet에 반영된 XSS(NPR-33439).

#### 자산 {#assets-6481}

* 목록 보기에서 선택 사항의 변경에 따라 자산 개수가 변경되지 않습니다(NPR-33285).

* 상위 노드(단일 하위 폴더가 표시되는 곳)를 선택한 다음 하위 폴더(NPR-33284)를 선택하면 다음 단추가 활성화되지 않습니다.

* DMS7 또는 하이브리드 모드가 활성화된 경우(NPR-33175) 저장소 루트에서 읽기 권한이 없는 사용자에 대해 터치 UI가 렌더링되지(오류 포함) 않습니다.

* 폴더 및 자산 이름에 발생하는 GB18030자가 다운로드된 zip 파일에서 공백으로 변경됩니다(NPR-33150).

* Extra folder is created on smart-cropping an asset that is inside a parent folder with dot `.` character in its name (NPR-32755).

* 알림 받은 편지함에서 작업을 검토하도록 선택할 때 지연 로딩이 트리거되지 않고 100개 이하의 자산이 표시됩니다(NPR-32749).

* 산호 정보(NPR-32510)의 변경으로 컬렉션이 공유되는 링크 페이지가 끊어졌습니다.

* 벌크 업로드가 중단되는 동안 자산 처리가 중단되었습니다(CQ-4293916).

* Experience Manager의 SSRF 취약성(NPR-33437).

#### 플랫폼 {#platform-6481}

* `sling:match` 맵 항목이 `/etc/maps`에 작성되지 않으면 [!DNL Sling] 필터가 호출되지 않습니다(NPR-33308).
* 모든 플러쉬 에이전트는 페이지 비활성화 시 트리거됩니다(NPR-32941).
* API를 사용하여 `ScriptProcessor` JavaScript 라이브러리를 축소하면 로그 파일에 JavaScript 코드가 엄격한 모드를 준수하지 않음을 나타내는 오류 메시지가 표시됩니다. API는 엄격 모드를 활성화하거나 비활성화할 수 있는 옵션을 제공하지 않습니다. (NPR-32746).
* SQL 쿼리가 더 오래 실행되면(예: 7시간) AEM이 응답하지 않습니다(NPR-33043).

#### 사용자 인터페이스 {#ui-6481}

* 선택 대화 상자를 사용하여 경로를 검색하거나 검색할 때 선택 대화 상자에 이미지만 표시하지 않고 선택한 JCR 노드의 모든 내용이 표시됩니다(NPR-32712).

#### 번역 프로젝트 {#tranlation-6481}

* 번역 작업 실행 시 로그에 `NullPointerException` 오류가 표시됩니다(NPR-32220).

#### 통합 {#integrations-6481}

* JSON용 크로스 사이트 스크립팅(NPR-32745).

#### 커뮤니티 {#communities-6481}

* 작성자는 새 그룹을 만든 후 [!DNL Internet Explorer] 11의 [!UICONTROL 커뮤니티 그룹] 섹션으로 리디렉션되지 않습니다(NPR-33202).
* [!UICONTROL 활동 스트림] 페이지 액세스 시 오류가 발생합니다(NPR-33152).
* [!DNL Communities] 그룹을 편집하고 썸네일 이미지를 변경해도 그룹 썸네일 이미지가 업데이트되지 않습니다(NPR-32603). 
* UGC(사용자 생성 컨텐츠)의 알림 및 구독 버전을 만드는 동안 소스 페이지의 잘못된 ID가 저장됩니다(, CQ-4289703).
* 사이트 간 스크립팅 문제(NPR-33212).

#### 워크플로우 {#workflow-6481}

* 일부 구성 요소는 사용자가 대화 상자 참가자 단계를  포함하는 워크플로우를 완료하면 표시되는 대화 상자에 표시되지 않습니다(NPR-32989).

* 왼쪽 레일의 [!UICONTROL 타임라인] 옵션을 로드하는 데 예상보다 시간이 더 걸립니다(NPR-32850).

#### 양식 {#forms-6481}

>[!NOTE]
>
>AEM 누적 수정 팩에는 AEM Forms에 대한 수정 사항이 포함되어 있지 않습니다. 이러한 수정 사항은 별도의 Forms 추가 기능 패키지를 사용하여 전달됩니다. 또한, JEE의 AEM Forms에 대한 수정 사항이 포함된 누적 설치 프로그램이 릴리스됩니다. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* 통신 관리:사용자가 [!DNL Word] 문서의 컨텐츠를 붙여넣을 때 텍스트 문서 조각은 서식을 유지하지 않습니다(NPR-33213).
* 적응형 양식: 적응형 양식 사전의 문자열에 새 줄이 있으면 사전에 `&#xa;` 문자가 추가됩니다(NPR-33265).
* 적응형 양식: 사용자가 둘 이상의 첨부 파일이 있는 적응형 양식을 저장할 수 없습니다(NPR-33214).
* 적응형 Forms: `AddInstance` 및 인스턴스 관리자 클래스의 `RemoveInstance` 메서드는 레이지 로드 조각에 대한 동적 인스턴스 수를 추가하지 않습니다( [!DNL Internet Explorer 11] NPR-33201).
* 적응형 Forms:페이지에 포함된 응용 양식에 활성화된 분석은 제출 및 포기 이벤트에 대한 데이터를 기록하지 않습니다(NPR-31359). [!DNL Sites]
* 적응형 Forms:사용자가 문서의 컨텐츠를 응용 양식 [!DNL Word] 에 붙여넣고 제출하면 제출된 응용 양식에 유니코드 문자가 포함됩니다. 또한 유니코드 문자로 인해 PDF를 PDF/A로 변환할 수 없습니다(NPR-3348).
* 백엔드 통합: 잘못된 비활성 상태로 인해 새로 고침 토큰이 만료되므로 양식 데이터 모델 요청이 실패합니다(NPR-33168).
* 문서 서비스:서버에 대한 깁슨 병들이 누락되어 PDF 문서를 PostScript로 변환하지 못하는 경우(NPR-33515, CQ-4292239). [!DNL WebLogic] [!DNL Linux]
* 문서 서비스:사용자가 텍스트 파일을 PDF로 변환하면 일본어 문자가 올바르게 렌더링되지 않습니다(NPR-33239).
* GuideSOMProviderServlet과 함께 XSS를 저장함(NPR-32701).

## 6.4.8.2 설치 {#install}

### 설치 요구 사항 {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>AEM 6.4에 기능 팩을 설치한 고객의 경우. Adobe에서 제공하는 옵션 기능 팩은 릴리스 버전 및 서비스 팩에 종속됩니다. Feature Pack이 설치되어 있는 경우 AEM 고객 지원 센터에 문의하여 AEM 6.4용 누적 수정 팩과 해당 기능 팩의 호환성을 확인하십시오.

* AEM 6.4.8.2 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* MongoDB 및 여러 인스턴스가 포함된 배포에서 패키지 관리자를 사용하여 작성자 인스턴스 중 하나에 AEM 6.4.8.2을 설치합니다.
* 누적 수정 팩을 설치하기 전에 AEM 인스턴스의 스냅샷 또는 새 백업을 보유해야 합니다.
* 설치하기 전에 인스턴스를 다시 시작합니다. 인스턴스가 업데이트 모드에 있는 경우에만 필요하지만(이전 버전에서 인스턴스가 방금 업데이트되었을 때의 경우임), 인스턴스가 더 긴 시간 동안 실행 중이면 권장됩니다.

>[!NOTE]
>
>AEM 6.4.8.2 패키지를 삭제하거나 제거하지 않는 것이 좋습니다.

### 누적 수정 팩 설치 {#install-cumulative-fix-pack}

기존 AEM 6.4.8.0 인스턴스에 누적 수정 팩을 설치하려면 다음 단계를 수행하십시오.

1. Software Distribution [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-2.0.zip) 링크를 클릭하여 패키지를 다운로드합니다.

1. [패키지 관리자](http://localhost:4502/crx/packmgr/index.jsp)를 열고 **[!UICONTROL 패키지 업로드]**&#x200B;를 클릭하여 패키지를 업로드합니다.

1. 패키지 이름을 선택하고 **[!UICONTROL 설치]**&#x200B;를 클릭합니다.

>[!NOTE]
>
>**패키지 관리자 UI의 대화 상자가 6.4.8.2 설치 중에 종료되는 경우가 있습니다.**
>
>따라서 인스턴스에 액세스하기 전에 오류 로그가 안정화될 때까지 기다리는 것이 좋습니다. 설치 성공 여부를 확인하려면 업데이트 번들 제거와 관련된 특정 로그를 기다려야 합니다. 일반적으로 Safari에서 발생하지만, 브라우저에서는 간헐적으로 발생할 수 있습니다.

### 자동 설치 {#auto-installation}

실행 중인 인스턴스에 AEM 6.4.8.2을 자동으로 설치하는 두 가지 방법이 있습니다.

A. 서버가 실행되는 동안 패키지를 ..*/crx-quickstart/install* 폴더에 배치합니다. 패키지가 자동으로 설치됩니다.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.2은 부트스트랩 설치를 지원하지 않습니다.

### 설치 확인 {#validate-install}

1. 이제 제품 정보 페이지(*/system/console/productinfo*)에 설치된 제품 아래에 업데이트된 버전 문자열 &quot;Adobe Experience Manager, 버전 6.4.8.2&quot;가 표시됩니다.
1. 모든 OSGI 번들은 OSGi 콘솔에서 ACTIVE이거나 FRAGMENT입니다(웹 콘솔 사용: /system/console/bundles).
1. OSGI 번들 org.apache.jackrabbit.oak-core는 버전 1.8.17 이상에 있습니다(웹 콘솔 사용: /system/console/bundles).

이번 AEM Sites 및 자산 릴리스에서 실행할 수 있는 인증된 플랫폼을 결정하려면 [기술 요구 사항을 참조하십시오](../sites-deploying/technical-requirements.md).

>[!NOTE]
>On successful installation of the package, an informational message appears indicating that the content package has installed successfully, such as **&quot;Content Package AEM-6.4-Service-Pack-8 installed successfully.&quot;**

### 다이내믹 미디어 뷰어 업데이트(5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.2에는 이미지 사전 설정 페이지에서 중복 이름을 확인할 수 있는 새로운 버전의 Dynamic Media 뷰어(5.10.1)가 포함되어 있습니다. Dynamic Media 고객은 박스 뷰어 사전 설정에서 최신 상태로 전환하려면 다음 명령을 실행해야 합니다.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

새 뷰어 사전 설정을 /conf 위치에 복사합니다.

### AEM Forms 추가 기능 패키지 설치 {#install-aem-forms-add-on-package}

>[!NOTE]
>
>AEM Forms를 사용하지 않는 경우 건너뜁니다. AEM Forms의 수정 사항은 별도의 추가 기능 패키지를 통해 전달됩니다.

1. AEM 누적 수정 팩을 설치했는지 확인합니다.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/kr/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Install AEM Forms JEE installer {#install-aem-forms-jee-installer}

>[!NOTE]
>
>JEE에서 AEM Forms를 사용하지 않는 경우 건너뜁니다. 별도의 설치 프로그램을 통해 AEM Forms JEE의 수정 사항이 전달됩니다.

For information about installing the cumulative installer for AEM Forms JEE and post-deployment configuration, see [AEM Forms JEE Patch Installer 0019](jee-patch-installer-64.md).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.2 is available in the [Adobe Public Maven repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.2/uber-jar-6.4.8.2.jar).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.2</version>  
      <scope>provided</scope>
</dependency>
```

## 제거된/더 이상 사용되지 않는 기능 {#removed-deprecated-features}

이 섹션에는 AEM 6.4에서 제거되었거나 이제 사용되지 않는 기능이 나와 있습니다.

| 영역 | 기능 | 대체 | 버전 |
|---|---|---|---|
| 자산 | 하위 자산에 대한 태그 작업 관리 | 교체 없음 | AEM 6.4.2.0 |
| Assets과 Adobe Creative Cloud 통합 | [AEM-Creative Cloud 폴더 공유](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) 기능은 크리에이티브 사용자가 AEM의 에셋에 액세스할 수 있도록 하는 방법으로 AEM 6.2에서 도입되었습니다. Creative Cloud 애플리케이션에서 새롭게 출시된 기능인 Adobe Asset Link는 Photoshop, InDesign 및 Illustrator에서 직접 AEM 자산에 액세스할 수 있는 강력한 권한과 함께 우수한 사용자 경험을 제공합니다. Adobe는 폴더 공유 기능에 대한 추가 개선을 하지 않습니다. 이 기능은 AEM에 포함되어 있지만, 고객은 이 교체 기능을 사용하는 것이 좋습니다. | Adobe 자산 링크 또는 데스크탑 앱. 자세한 내용은 [AEM Creative Cloud 통합](/help/assets/aem-cc-integration-best-practices.md) 문서를 참조하십시오. | AEM 6.4.4.0 |

## 알려진 문제 {#known-issues}

* Experience Manager 6.4.8.2에서 Experience Manager 6.5로 업그레이드하는 경우 일부 번들에 상태가 로 표시되지 않을 수 있습니다 `Active`. 최신 Experience Manager 6.5 서비스 팩 6를 설치하여 문제를 해결하십시오.

AEM 6.4.8.0 서비스 팩 알려진 문제에 대한 자세한 내용은 [AEM 6.4.8.0 서비스 팩 릴리스 정보를 참조하십시오](sp-release-notes.md).

## OSGi 번들 및 컨텐츠 패키지가 설치됨 {#osgi-bundles-and-content-packages-included}

다음 텍스트 문서에는 AEM 6.4.8.2에 포함된 OSGi 번들 및 컨텐츠 패키지가 나와 있습니다.

AEM 6.4.8.2에 포함된 OSGi 번들 목록

[파일 가져오기](assets/6.4.8.2_osgi_bundles.txt)

AEM 6.4.8.2에 포함된 콘텐츠 패키지 목록

[파일 가져오기](assets/6.4.8.2_content_packages.txt)

## 유용한 리소스 {#helpful-resources}

* [AEM 6.4 릴리스 노트](../release-notes/release-notes.md)
* [AEM 제품 페이지](https://www.adobe.com/kr/solutions/web-experience-management.html)
* [AEM 6.4 설명서](https://helpx.adobe.com/kr/support/experience-manager/6-4.html)
* [Adobe 우선 순위 제품 업데이트](https://www.adobe.com/subscription/priority-product-update.html) 구독

## 제한된 사이트 {#restricted-sites-new}

다음 사이트는 고객만 사용할 수 있습니다. 액세스가 필요한 고객의 경우 Adobe 계정 관리자에게 문의하십시오.

* [licensing.adobe.com에서 제품 다운로드](https://licensing.adobe.com/)
* [고객 지원 팀에 문의](https://docs.adobe.com/content/help/ko-KR/customer-one/using/home.html)
