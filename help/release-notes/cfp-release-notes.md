---
title: AEM 6.4 누적 수정 팩 릴리스 노트
description: Adobe Experience Manager 6.4 누적 수정 팩에 대한 릴리스 노트입니다.
contentOwner: AK
mini-toc-levels: 1
exl-id: a63e77a3-da48-4072-bc75-c4c41a2f62a3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '4680'
ht-degree: 22%

---

# AEM 6.4 누적 수정 팩 릴리스 노트 {#aem-cumulative-fix-pack-release-notes}

## 릴리스 정보 {#release-information}

<!-- TBD: Update the SD URL. -->

| 제품 | **AEM(Adobe Experience Manager) 6.4** |
|---|---|
| 버전 | 6.4.8.4 |
| 유형 | 누적 수정 팩 |
| 날짜 | 2021년 2월 25일 |
| 전제 조건 | [AEM 6.4 서비스 팩 8(6.4.8.0)](sp-release-notes.md) |
| 다운로드 URL | [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## AEM 6.4.8.4에 포함된 기능 {#what-s-included-in-aem}

AEM 누적 수정 팩 6.4.8.4은 2020년 3월, AEM 6.4 서비스 팩 8(6.4.8.0)의 일반 출시 이후 다수의 내부 및 고객 수정 사항을 포함한 중요한 업데이트입니다.

AEM 6.4.8.4는 AEM 6.4 서비스 팩 8에 종속된 CFP(Cumulative Fix Pack)입니다. AEM 6.4 서비스 팩 8을 설치한 후 CFP를 설치합니다.

[!DNL Adobe Experience Manager] 6.4.8.4에 도입된 주요 기능 및 개선 사항은 다음과 같습니다.

* PDFG 변환을 수행할 때 [!DNL Experience Manager Forms] 레지스트리 변경 사항을 활성화하거나 비활성화할 수 있습니다.

* 양식 데이터 모델에서 SOAP 기반 웹 서비스를 위한 X-509 인증서 기반 인증.

* 내장된 저장소(Apache Jackrabbit Oak)가 버전 1.8.24으로 업데이트되었습니다.

CFP 및 기타 릴리스 유형에 대한 자세한 내용은 [AEM Update 릴리스 차량 정의](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html?lang=en) 를 참조하십시오.

Adobe Experience Manager 6.4.8.4에서는 다음 문제에 대한 수정 사항을 제공합니다.

### 사이트 {#sites-6484}

* Experience Manager 서비스 팩 6.4.8.2를 설치한 후에는 컨텐츠 조각 모델을 편집할 수 없으며 다음 오류가 표시됩니다.

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* 사용자가 로그아웃 단추를 클릭하면 사용자가 패키지 관리자에서 로그아웃되지 않습니다. (NPR-35161)
* Experience Manager 6.4.x에서 Experience Manager 6.4.8.3으로 업그레이드한 후 사용자는 게시 관리 를 통해 페이지를 게시할 수 없습니다. (CQ-4312511)
* 블루프린트 하위 페이지를 원래 위치로 다시 이동하면 cq:liveSyncConfig 구성이 Live Copy 하위 페이지에서 제거되지 않습니다. (NPR-35900)
* Live Copy가 있는 블루프린트를 앞뒤로 이동하면 첫 번째 이동만 작동한 다음 실패하며 오류 메시지가 표시되지 않습니다. (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` 스마트  `OutOfMemoryError` 태깅 기능이 큰 지표  `/oak:index/lucene` 및 인덱스를 만들므로  `/oak:index/ntBaseLucene` 오류가 발생합니다(NPR-35650).
* 사용자가 [!DNL Adobe InDesign]에서 자산을 편집한 후 자산을 체크 인할 수 없으며 권한 부족에 대한 오류가 표시됩니다(NPR-35340).
* 이름 지정 충돌을 해결한 후 기존 자산의 새 버전을 만들면 원래 자산의 메타데이터를 덮어씁니다(NPR-35939).
* 자동 생성된 비공개 폴더 그룹은 폴더를 삭제할 때 또는 [!UICONTROL 개인 폴더 제한 제거] 옵션이 설정된 폴더를 업데이트할 때 유지 관리되지 않고 제거되지 않습니다(NPR-35625).

#### [!DNL Dynamic Media] {#dynamic-media}

* 일시적인 ImageServer 오류로 인해 [!DNL Experience Manager]의 몇 가지 기능에 대한 403 응답이 발생합니다. (CQ-4308565)

### 통합 {#integrations-6484}

* 6.4.8.3으로 업그레이드한 후 페이지의 속성을 열면 콘솔에 JavaScript 오류가 표시됩니다(NPR-35649).

### 양식 {#forms-6484}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 는 예정된  [!DNL Experience Manager] 누적 수정 팩 릴리스 날짜로부터 1주일 후에 추가 기능 패키지를 출시합니다.

**서신 관리**

* 편지를 편집할 때 조건이 있는 모듈을 로드하는 데 시간이 오래 걸립니다(NPR-35326).

* 편지를 편집할 때 콘텐츠 및 데이터 바인딩이 사용자 인터페이스에 표시되지 않습니다(CQ-4312905).

**문서 서비스**

* [!DNL JAVA] 을 [!DNL JDK1.8.0_261](으)로 업그레이드한 후 PDF를 어셈블할 수 없습니다(NPR-35761, NPR-35848).

**Foundation JEE**

* [!DNL Forms] 워크플로우에서 작업 알림을 편집하면 저장할 수 없습니다(CQ-4315055).

보안 업데이트에 대한 자세한 내용은 [Experience Manager 보안 게시판 페이지](https://helpx.adobe.com/security/products/experience-manager.html)를 참조하십시오.

## 이전 누적 수정 팩에 포함된 핫픽스 및 기능 팩 {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM 누적 수정 팩 6.4.8.3은 2020년 3월, AEM 6.4 서비스 팩 8(6.4.8.0)의 일반 출시 이후 다수의 내부 및 고객 수정 사항을 포함한 중요한 업데이트입니다.

AEM 6.4.8.3은 AEM 6.4 서비스 팩 8에 종속된 CFP(Cumulative Fix Pack)입니다. AEM 6.4 서비스 팩 8을 설치한 후 CFP를 설치합니다.

AEM 6.4.8.3에서 내장된 저장소(Apache Jackrabbit Oak)가 버전 1.8.23으로 업데이트되었습니다.

CFP 및 기타 릴리스 유형에 대한 자세한 내용은 [AEM Update 릴리스 차량 정의](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html) 를 참조하십시오.

Adobe Experience Manager 6.4.8.3은 다음 문제에 대한 수정 사항을 제공합니다.

#### 사이트 {#sites-6483}

* 컨텐츠 조각의 변형 텍스트를 업데이트하면 변형 대신 마스터 컨텐츠 조각의 컨텐츠가 업데이트됩니다(NPR-35080).

* 구성 요소의 문자열 유형 레이블 속성에 대한 숫자 값을 설정하고, 구성 요소를 삭제하고, 실행 취소 옵션을 사용하여 다시 가져오면 레이블 속성의 유형이 String에서 Long으로 자동으로 변경됩니다(NPR-34738).

* 다중 필드에 파일 업로드 구성 요소를 추가하면 이미지 경로가 다중 필드 노드 대신 구성 요소 노드에 저장됩니다(NPR-34423).

* 대상을 선택하지 않은 경우에도 페이지 이동 마법사에서 다음 단추가 활성화된 상태로 유지됩니다(NPR-34460).

* 상위 구성 요소에 `cq:isContainer` 속성이 포함되어 있으면 상속된 구성 요소에 속성이 자동으로 포함되지 않습니다(CQ-4308409).

* `calc()` 함수를 사용하여 CSS 축소를 사용하는 경우 `+` 기호 주위의 빈 공백이 제거됩니다(NPR-34991).

* AEM 인스턴스를 시작하면 `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` 및 `com.adobe.granite.maintenance.impl.TaskScheduler` 구성 요소가 `Active` 상태에 표시되지 않습니다(NPR-34952).

#### [!DNL Assets] {#assets-6483}

* 기존 자산의 버전을 만들 때 메타데이터 프로필이 폴더에 적용되는 경우 메타데이터에 대한 사용자 업데이트가 지속되지 않습니다(NPR-34833).
* [!DNL Adobe InDesign]과 함께 [!DNL Adobe Asset Link]을 사용하는 경우 검색 결과에 폴더와 컬렉션이 포함되지 않고 자산만 포함됩니다(NPR-34700).
* 폴더에서 자산을 드래그하여 이동할 때 사용자 인터페이스에는 [!UICONTROL Lightbox] 및 [!UICONTROL Drop in Collection]에도 옵션이 표시됩니다. 이동 작업이 취소되더라도 사용자 인터페이스에 나머지 두 옵션이 계속 표시됩니다(NPR-34525).
* 게시 관리 인터페이스가 열리면 게시 옵션을 사용할 수 없으며 게시 취소 옵션을 선택하면 범위 페이지가 비어 있습니다(CQ-4302509).

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* 이미지 사전 설정 설정에서 [!UICONTROL JPG 색차 다운샘플링 활성화] 옵션이 [!DNL Experience Manager]에서 선택 취소되면 변경 사항이 [!DNL Dynamic Media]과 동기화되지 않습니다(NPR-34284).
* [!UICONTROL 뷰어 사전 설정 편집기]에서 [!UICONTROL PanasonicImage/PanoricImage_VR] 사전 설정을 편집할 때 `PanoramicView` 구성 요소에서 `PANORAMICVIEW_AUTOROTATE` 수정자 레이블을 사용할 수 없습니다(CQ-4302043).
* [!DNL Experience Manager]에서 비디오를 게시 취소해도 구성된 Dynamic Media Classic에 응용 비디오 세트가 게시 취소되지 않습니다. (CQ-4304405).

#### 플랫폼 {#platform-6483}

* `emitUseStrict` 플래그가 GCC(Google Closure Compiler) 프로세서 함수 `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`에 추가됩니다. 플래그는 `use strict` 명령의 출력을 억제합니다(NPR-34830).
* 일별 또는 주별 유지 관리 작업을 시작할 때 `NullPointerException`이 반환됩니다(NPR-34702).
* [!DNL Apache Sling Health Check] 도구는 더 이상 사용되지 않습니다. 대신 [패턴 탐지기](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) 를 사용하여 콘텐츠 위반을 감지하십시오(NPR-33929).

#### 통합 {#integrations-6483}

* [!UICONTROL 만들기] 단추가 폴더에서 [!UICONTROL 대상] 페이지로 이동할 때 [!UICONTROL 대상] 페이지에 표시됩니다(NPR-35152).

#### 사용자 인터페이스 {#ui-6483}

* [!UICONTROL Omnisearch] 사용자 인터페이스의 [!UICONTROL 필터] 검색 패널도 검색이 실행되는 위치 이외의 위치에서 결과를 반환합니다(NPR-34877).
* [!UICONTROL Omnisearch] 사용자 인터페이스에서 [!UICONTROL 필터] 패널을 닫을 때 왼쪽 레일이 [!UICONTROL 콘텐츠] 선택 항목으로 재설정되지 않으므로 [!UICONTROL 필터] 패널을 다시 열 수 없습니다(NPR-34483).
* 페이지 속성에 액세스할 때 `NullPointerException`이 반환됩니다(NPR-34509).

#### 커뮤니티 {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* 제품의 불공정한 용어 인스턴스는 모두 수락된 동산으로 대체됩니다(NPR-34506).

#### 상거래 {#commerce-6483}

* 컬렉션에 15개 이상의 제품이 있는 경우 컬렉션에 처음 15개의 제품만 표시됩니다(NPR-34494).

#### 양식 {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 는 예정된  [!DNL Experience Manager] 누적 수정 팩 릴리스 날짜로부터 1주일 후에 추가 기능 패키지를 출시합니다.

>[!NOTE]
>
>[!DNL Experience Manager] 누적 수정 팩에는 수정 사항이 포함되어 있지 않습니다 [!DNL Experience Manager Forms]. 이러한 수정 사항은 별도의 [!DNL Forms] 추가 기능 패키지를 사용하여 전달됩니다. 또한, JEE의 [!DNL Experience Manager Forms]에 대한 수정 사항이 포함된 누적 설치 프로그램이 릴리스됩니다. 자세한 내용은 [AEM Forms 추가 기능 패키지 설치](#install-aem-forms-add-on-package) 및 [AEM Forms JEE 설치 프로그램 설치](#install-aem-forms-jee-installer) 를 참조하십시오.

**적응형 양식**

* [!DNL Experience Manager] 누적 수정 팩을 적용한 후 클래식 UI를 사용하여 적응형 양식을 편집할 수 없습니다(NPR-35127).

* 캐시 무효화로 인해 조각을 로드하는 데 시간이 오래 걸립니다(NPR-34655).

* 액세스 가능성:적응형 양식의 화면 판독기에 탭 탐색 기능이 제대로 작동하지 않습니다(NPR-34550).

**서신 관리**

* ES3에서 자산을 마이그레이션할 때 자산에는 편집할 수 없는 두 가지 기본 조건이 포함됩니다(NPR-34971).

**Foundation JEE**

* [!DNL AEM Forms] 사용자를 Flash에서 HTML로 마이그레이션합니다(CQ-4304075).

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM 누적 수정 팩 6.4.8.2은 2020년 3월, AEM 6.4 서비스 팩 8(6.4.8.0)의 일반 출시 이후 다수의 내부 및 고객 수정 사항을 포함한 중요한 업데이트입니다.

AEM 6.4.8.2는 AEM 6.4 서비스 팩 8에 종속된 CFP(Cumulative Fix Pack)입니다. AEM 6.4 서비스 팩 8을 설치한 후 CFP를 설치합니다.

AEM 6.4.8.2에서 내장된 저장소(Apache Jackrabbit Oak)가 버전 1.8.22으로 업데이트되었습니다.

CFP 및 기타 릴리스 유형에 대한 자세한 내용은 [AEM Update 릴리스 차량 정의](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html) 를 참조하십시오.

Adobe Experience Manager 6.4.8.2는 다음 문제에 대한 수정 사항을 제공합니다.

#### 사이트 {#sites-6482}

* `RolloutConfigManagerFactoryImpl`에서 롤아웃 구성을 로드할 수 없는 경우 누락된 구성을 로드하지 않습니다. 캐시된 구성을 반환합니다(NPR-34091).
* 텍스트 코어 구성 요소에서 소스 HTML 편집 옵션을 사용한 후 `em` 태그의 클래스가 제거됩니다(NPR-34080).
* Experience Manager 6.2에서 Experience Manager 6.5로 업그레이드하는 경우 정적 템플릿의 Parsys 구성 요소가 올바르게 표시되지 않습니다. Parsys 구성 요소의 높이가 0으로 설정되고 이 구성 요소 내에 있는 구성 요소가 표시되지 않습니다(NPR-34044).
* 템플릿 편집기 내에 허용된 구성 요소에 대한 레이블 정보가 표시되지 않습니다(NPR-33908).

   ![레이아웃 컨테이너에 레이블이 없음](assets/33908_missing_labels.png)

* 중첩된 구성 요소의 네 번째 수준 다음에 parsys에 구성 요소를 추가하거나 편집할 수 없습니다(NPR-33873).
* 편집 가능한 템플릿의 초기 컨텐츠가 변경된 다음 템플릿이 게시되면 페이지가 게시되지 않아도 이 템플릿으로 만든 새 페이지에 템플릿의 게시된 날짜가 표시됩니다(NPR-33822).
* 복사에서 [!DNL Adobe Campaign]에 대한 `cq:acLinks` 및 `cq:acUUID` 속성은 복사 및 붙여넣기 작업 중에 제거됩니다(NPR-33793).
* [!UICONTROL 라이브 사용량] 탭에는 49개의 결과만 표시됩니다. 구성 요소에 대한 일부 사용량이 표시되지 않습니다(NPR-33710).
* 작성하는 동안 URL에 `/` 문자가 있는 웹 페이지가 응답하지 않습니다. 작성하는 동안 구성 요소를 추가하면 CPU 사용량이 증가하고 브라우저가 응답을 중지합니다(NPR-33625).
* [!DNL RTE]의 인라인 편집 모드에서 텍스트 구성 요소에 대해 이미지를 드래그하면 작동하지 않습니다(NPR-33579).
* 페이지 이름과 동일한 이름으로 블루프린트 페이지에서 구성 요소를 만들 수 있습니다. 롤아웃 중에 이러한 구성 요소의 이름은 접미사 `_msm_moved`로 변경됩니다. 하지만 구성 요소는 [!UICONTROL 단락 시스템] 의 끝으로 이동됩니다(NPR-33534).
* 첫 번째 컨텐츠 루트에서 [!UICONTROL 하위 페이지 포함] 속성을 선택하지 않은 경우 Launch 프로모션이 페이지를 게시하지 않습니다(NPR-33533).
* `PageRedirectServlets` 은 URL 조각 또는 앵커 뒤에 쿼리 문자열을 하므로 앵커를 사용하는 [!DNL Experience Manager] 페이지로 리디렉션하지 작성자 인스턴스에서 작동하지 않습니다(NPR-34287).
* `PageRedirectServlet` 링크 오류로  `.html` 이어지는 Sling 매핑 후에 을 추가합니다(NPR-34271).
* 페이지의 [!DNL Live Copy]을 일시 중단할 수 있으며 상속이 편집기 모드에서 보듯이 중단됩니다. 그러나 페이지 속성에서 상속을 나타내는 아이콘이 상속이 존재하며 끊기지 않음을 잘못 나타냅니다(NPR-34096).
* 템플릿 편집 페이지에서 허용되는 구성 요소를 표시하는 문제(CQ-4297295).
* Chrome 및 Firefox를 업그레이드한 후 팝업 메뉴가 예상대로 작동하지 않습니다. 페이지 속성을 로드할 때 데이터가 있으면 패널이 표시되지 않습니다(CQ-4292995).
* [!DNL Experience Manager Sites] 구성 요소의 여러 교차 사이트 스크립팅 인스턴스(NPR-33926).
* 클라이언트에게 정보를 전송할 때 다양한 구성 요소에 대해 사용자 입력이 적절히 인코딩되지 않습니다(NPR-33696).
* `childrenlist.html` 로 끝나는 URL은 404 응답 대신 HTML 페이지를 표시합니다. 이러한 URL은 교차 사이트 스크립팅에 취약합니다(NPR-33441).

#### 에셋 {#assets-6482}

* 업로드된 PDF 파일에 대한 텍스트 추출이 작동하지 않고 PDF 파일에서 일부 단어를 전체 텍스트 검색에서 해당 PDF 파일을 가져오지 못했습니다(NPR-34165).

   >[!NOTE]
   >이 수정 사항을 적용하려면 서비스 팩 6.4.8.2를 설치한 후 Adobe Experience Manager 인스턴스를 다시 시작하십시오.

* 이름에 특수 문자가 있는 자산의 검색 제안에 특수 문자 앞에 백슬래시가 추가됩니다(NPR-33833).

* 스마트 컬렉션으로 저장된 사용자 지정 필터는 자산에 올바르게 적용되지 않으므로 검색 결과가 정확하지 않습니다   (NPR-33725).

* 순서가 변경된 폴더 내의 자산의 타임라인은 자산이 이동되었음을 나타냅니다(NPR-33580).

* [!DNL Brand Portal]에서 자산을 벌크로 게시하지 않으면 `Request-URI Too Long` 오류가 발생합니다(NPR-34158).

* 사용자가 자산 세트를 선택한 후 [!UICONTROL 필터] 옵션을 선택한 다음(자산이 선택 취소됨) 이동할 다른 자산 세트를 선택한 경우 열 보기에서 이전에 선택한 자산도 새 위치로 이동되는 경우(NPR-34018).

* 페이지에 맞출 자산이 많아도 목록 보기에 스크롤 막대가 표시되지 않습니다(NPR-34156).

* 자산에 대한 [!UICONTROL 게시 관리] 페이지가 중단되고 그 옵션이 작동하지 않습니다(CQ-4302509).

**Dynamic Media**

* 이미지 프로필이 여러 종횡비를 갖는 폴더(예: 11)에 추가되는 경우 오류가 발생하여 스마트 자르기 기능이 실패합니다(NPR-34083).

* [!UICONTROL Adobe Experience Manager]에서 이미지 사전 설정에 대한 변경 사항이 Dynamic Media Classic에 동기화되지 않습니다(NPR-34284, CQ-4299713).

* [!UICONTROL PANORAMICVIEW_AUTOROTATE] 수정자 레이블이 [!UICONTROL 뷰어 사전 설정 편집기] 페이지의 [!UICONTROL 동작] 탭에 없습니다(CQ-4302043).

#### 플랫폼 {#platform-6482}

* 기본 에이전트(게시) 구성에 대한 **[!UICONTROL 연결 시간 초과]** 및 **[!UICONTROL 소켓 시간 초과]** 설정에 대한 기본값이 지정되지 않았습니다(NPR-33708).
* 유지 관리 작업 스케줄러가 구성된 것보다 너무 자주 유지 관리 작업을 시작하고 중지합니다(NPR-33520).
* 업그레이드된 Experience Manager 인스턴스에서 진단 도구를 사용하여 로그를 다운로드할 수 없습니다(NPR-34419).

#### 통합 {#integrations-6482}

* [!DNL Adobe Dynamic Tag Management]에서 마이그레이션된 라이브러리에 대한 [!DNL Adobe Launch] 라이브러리 URL을 생성할 때 `library_path` 값은 고려되지 않습니다. 또한 마이그레이션된 라이브러리는 [!DNL Adobe Launch] 라이브러리와 다른 접두사를 사용합니다. (NPR-34238).
* 클라우드 서비스에서 상속된 속성은 페이지 속성을 업데이트할 때 지속되지 않습니다(NPR-33865).

#### 사용자 인터페이스 {#ui-6482}

* 검색 페이지에 선택한 자산 수가 잘못 표시됩니다(NPR-33540).

#### 커뮤니티 {#communities-6482}

* Admin Console을 통해 추가된 커뮤니티 그룹의 기존 사용자는 커뮤니티 그룹 콘솔에서 수정된 내용에 대한 사용자 목록에서 제거됩니다(NPR-34312).

#### 양식 {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] 누적 수정 팩에는 수정 사항이 포함되어 있지 않습니다 [!DNL Experience Manager Forms]. 이러한 수정 사항은 별도의 [!DNL Forms] 추가 기능 패키지를 사용하여 전달됩니다. 또한, JEE의 [!DNL Experience Manager Forms]에 대한 수정 사항이 포함된 누적 설치 프로그램이 릴리스됩니다. 자세한 내용은 [AEM Forms 추가 기능 패키지 설치](#install-aem-forms-add-on-package) 및 [AEM Forms JEE 설치 프로그램 설치](#install-aem-forms-jee-installer) 를 참조하십시오.

**적응형 양식**

* 누락된 적응형 양식 조각이 있는 경우 적응형 양식이 렌더링되지 않습니다(NPR-34303).

* 적응형 양식 필드에 대한 도움말 컨텐츠 설명에 단락 HTML 태그가 표시됩니다(NPR-34117).

* [!DNL Experience Manager Sites] 페이지에서 Forms 컨테이너를 추가하면 페이지에 다음 오류 메시지가 표시되고 새 구성 요소를 추가할 수 없습니다(NPR-33858).

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* **[!UICONTROL Server]** 속성에서 재유효성 검사 속성을 선택하고 여러 첨부 파일을 업로드하면 적응형 양식이 제출되지 않습니다(NPR-33701).

* [!DNL Experience Manager Sites] 페이지에서 **[!UICONTROL 페이지 언어 사용]** 및 **[!UICONTROL Form에서 [!DNL Experience Manager Forms] 구성 요소에 있는 Page]** 옵션의 전체 너비를 선택하면 페이지가 번역되지 않습니다(NPR-33641).

* [!DNL Experience Manager Sites] 페이지에 포함된 Analytics 지원 적응형 양식을 제출하면 Analytics가 제대로 작동하지 않습니다(NPR-31359).

* [!DNL Lodash] 및 [!DNL backbone] 라이브러리에 대한 종속성을 제거했습니다(NPR-33458).

* **[!UICONTROL REST 엔드포인트에 제출]** 제출 작업이 적응형 양식에 대해 작동하지 않습니다(NPR-34513).

* 액세스 가능성:필수 필드에 대한 첨부 파일을 업로드하지 않고 적응형 양식을 제출하려고 하면 포커스가 첨부 파일 필드로 자동 이동하지 않습니다(NPR-34511).

* 사용자 입력은 클라이언트에 정보를 보낼 때 [!DNL Forms] 구성 요소에 대해 적절히 인코딩되지 않습니다(NPR-33611).

**워크플로우**

* [!DNL Experience Manager] 워크플로우 삭제 작업이 실패하고 다음 오류 메시지가 표시됩니다(NPR-33576).

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* [!DNL Experience Manager] 6.4.8.1을 설치하면 항목 [!UICONTROL 완료] 목록이 링크로 표시되지 않습니다. [!UICONTROL To Do] 항목의 텍스트에 HTML 태그가 포함됩니다(NPR-34318).

**백엔드 통합**

* AWS에서 호스팅되는 [!DNL Experience Manager Forms Linux] 환경에서 양식 데이터 모델을 구성할 수 없습니다(NPR-33617).

**디자이너**

* [!DNL Experience Manager] Forms 서버에 [!DNL Acrobat DC]이(가) 설치된 경우 [!DNL Experience Manager Designer] 버전 6.x에서는 **[!UICONTROL 양식 배포]** 옵션을 사용할 수 없습니다(NPR-34325).

**문서 보안**

* [!DNL Experience Manager] 6.4.8.0을 설치한 후 PDF 파일에 HSM 기반 인증서로 서명 작업을 실행할 수 없습니다(NPR-34309).

**업그레이드**

* [!DNL Linux] 환경에서 문서 보안을 사용하여 [!DNL Experience Manager Forms]에 대해 [!DNL JBoss] 버전을 7.0.9로 업그레이드하면 오류가 발생합니다(CQ-4300546).

보안 업데이트에 대한 자세한 내용은 [Experience Manager 보안 게시판 페이지](https://helpx.adobe.com/security/products/experience-manager.html)를 참조하십시오.

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM 누적 수정 팩 6.4.8.1은 2020년 3월, AEM 6.4 서비스 팩 8(6.4.8.0)의 일반 출시 이후 다수의 내부 및 고객 수정 사항을 포함한 중요한 업데이트입니다.

AEM 누적 수정 팩 6.4.8.1는 AEM 6.4 서비스 팩 8에 종속됩니다. 따라서 AEM 6.4 서비스 팩 8을 설치한 후 AEM 누적 수정 팩 6.4.8.1 패키지를 설치해야 합니다.

AEM 6.4.8.1의 주요 특징 중 일부는 다음과 같습니다.

* 보안을 강화하기 위해 CRXDE Lite에 대한 익명 액세스가 허용되지 않습니다. 대신 사용자에게 로그인 화면이 표시됩니다. [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)로 개발을 참조하십시오.
* Adobe Experience Manager와 패키지 공유 통합이 제거되었습니다.
* 내장된 저장소(Apache Jackrabbit Oak)가 버전 1.8.21으로 업데이트되었습니다.

CFP 및 기타 릴리스 유형에 대한 자세한 내용은 [AEM Update 릴리스 차량 정의](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html) 를 참조하십시오.

Adobe Experience Manager 6.4.8.1은 다음 문제에 대한 수정 사항을 제공합니다.

#### 사이트 {#sites-6481}

* 익명의 사용자는 CRX DE Lite 기능에 액세스할 수 있습니다(NPR-33522).
* LiveCopy의 로컬 구성 요소의 이름이 블루프린트에서 구성 요소의 이름과 동일하고 이 구성 요소가 블루프린트에서 롤아웃되면, _msm_moved 용어가 로컬 구성 요소의 이름에 추가되지 않습니다(NPR-33207).
* 원래 요청에 추가된 매개 변수는 리디렉션 URL에 포함되지 않습니다(NPR-33174).
* Coral.Select 옵션이 emptyOption=true를 설정하거나 값이 &quot;&quot;인 기본 항목을 포함하는 경우 dropdownshowhide.js 파일에 오류가 발생합니다.처리할 수 없는 유형 오류:component.getValue가 함수가 아닙니다(NPR-33163).
* 구성 요소에 data-sly-resource로 다른 구성 요소가 포함되어 있으면 상위 컨테이너 구성 요소 자리 표시자가 내부 구성 요소 자리 표시자로 대체됩니다(NPR-33119).
* 스키마에 컨텐츠 조각을 기반으로 하고 필수 텍스트 영역 또는 경로 필드를 포함하는 경우 컨텐츠 조각이 저장되지 않습니다(NPR-33007)
* 기본 경험 조각 구성 요소를 사용하여 사용자 지정 구성 요소를 만들고 AEM Sites 페이지에서 사용하면 AEM에 사용자 지정 구성 요소에 대한 참조(사용량)를 표시하지 않습니다(NPR-32852).
* AEM Sites 페이지가 여러 Live Copy가 있는 큰 컨텐츠 세트의 일부인 경우 페이지 버전 기록 미리 보기가 로드되지 않습니다(NPR-32772).
* 론치를 승격하면 론치에 추가된 모든 구성 요소에 &quot;cq:LiveRelationship&quot; mixin이 추가됩니다. 소스 페이지의 라이브 데이터 상속 — 옵션을 선택하지 않은 상태에서 론치가 생성되는지 여부에 관계없이 모든 론치에 영향을 줍니다(NPR-32664).
* 페이지 매김이 시작되면 경험 조각 선택기가 일부 항목을 로드하지 않습니다(NPR-32605).
* AEM Sites 페이지에 대한 론치를 만들 수 없습니다. 론치를 만들 때 오류가 발생합니다(NPR-32544).
* 게시 관리 는 활성화 요청 워크플로우에 참조된 자산을 포함하지 않습니다(NPR-32463).
* Dispatcher 상태 확인은 로그 파일에 `Invalid cookie header` 경고 메시지를 표시합니다(NPR-33630).
* Salesforce 통합은 SSRF에 취약합니다(NPR-32671).
* PreferencesServlet에 XSS가 반영되었습니다(NPR-33439).

#### 에셋 {#assets-6481}

* 목록 보기에서 선택 내용의 변경에 따라 자산 수가 변경되지 않습니다(NPR-33285).

* 다음 단추는 상위 노드(단일 하위 폴더가 표시되는 경우)를 선택한 다음 하위 폴더를 선택할 때 활성화되지 않습니다(NPR-33284).

* DMS7 또는 하이브리드 모드가 활성화된 경우 저장소 루트에 대한 읽기 액세스 권한이 없는 사용자에 대해 Touch UI가 렌더링되지(오류 있음) 않습니다(NPR-33175).

* 폴더 및 자산 이름에 발생하는 GB18030 문자가 다운로드한 zip 파일에서 공백으로 변경됩니다(NPR-33150).

* 이름에 점 `.` 문자가 있는 상위 폴더의 자산을 스마트 자르기하면 추가 폴더가 만들어집니다(NPR-32755).

* 지연 로드는 트리거되지 않으며 알림 받은 편지함에서 작업을 검토하도록 선택할 때 100개 이하의 자산이 표시됩니다(NPR-32749).

* coral-info의 변경으로 인해 공유 컬렉션에 대한 링크 페이지가 손상되었습니다(NPR-32510).

* 벌크 업로드 중 자산 처리가 보류됩니다(CQ-4293916).

* Experience Manager의 SSRF 취약성(NPR-33437).

#### 플랫폼 {#platform-6481}

* `sling:match` 맵 항목이 `/etc/maps`에 작성되지 않으면 [!DNL Sling] 필터가 호출되지 않습니다(NPR-33308).
* 페이지 비활성화 시 모든 플러시 에이전트가 트리거됩니다(NPR-32941).
* `ScriptProcessor` API를 사용하여 JavaScript 라이브러리를 축소하면 로그 파일에 JavaScript 코드가 엄격한 모드에 준하지 않음을 나타내는 오류 메시지가 표시됩니다. API는 엄격한 모드를 활성화하거나 비활성화하는 옵션을 제공하지 않습니다. (NPR-32746).
* SQL 쿼리가 더 오래 실행되면(예: 7시간) AEM이 응답하지 않습니다(NPR-33043).

#### 사용자 인터페이스 {#ui-6481}

* 선택 대화 상자를 사용하여 경로를 검색하거나 찾아보면 선택 대화 상자에 이미지만 표시하는 대신 선택한 JCR 노드의 모든 컨텐츠가 표시됩니다(NPR-32712).

#### 번역 프로젝트 {#tranlation-6481}

* 번역 작업 실행 시 로그에 `NullPointerException` 오류가 표시됩니다(NPR-32220).

#### 통합 {#integrations-6481}

* JSON에 대한 교차 사이트 스크립팅(NPR-32745).

#### 커뮤니티 {#communities-6481}

* 작성자는 새 그룹을 만든 후 [!DNL Internet Explorer] 11의 [!UICONTROL 커뮤니티 그룹] 섹션으로 리디렉션되지 않습니다(NPR-33202).
* [!UICONTROL 활동 스트림] 페이지 액세스 시 오류가 발생합니다(NPR-33152).
* [!DNL Communities] 그룹을 편집하고 썸네일 이미지를 변경해도 그룹 썸네일 이미지가 업데이트되지 않습니다(NPR-32603). 
* UGC(사용자 생성 컨텐츠)의 알림 및 구독 버전을 만드는 동안 소스 페이지의 잘못된 ID가 저장됩니다(, CQ-4289703).
* 크로스 사이트 스크립팅 문제(NPR-33212).

#### 워크플로 {#workflow-6481}

* 일부 구성 요소는 사용자가 [!UICONTROL 대화 상자 참가자 단계]를 포함하는 워크플로우를 완료할 때 나타나는 대화 상자에 표시되지 않습니다(NPR-32989).

* 왼쪽 레일의 [!UICONTROL 타임라인] 옵션을 로드하는 데 예상보다 시간이 더 걸립니다(NPR-32850).

#### 양식 {#forms-6481}

>[!NOTE]
>
>AEM 누적 수정 팩에는 AEM Forms 수정 사항이 포함되어 있지 않습니다. 이러한 수정 사항은 별도의 Forms 추가 기능 패키지를 사용하여 전달됩니다. 또한, JEE의 AEM Forms에 대한 수정 사항이 포함된 누적 설치 프로그램이 릴리스됩니다. 자세한 내용은 [AEM Forms 추가 기능 패키지 설치](#install-aem-forms-add-on-package) 및 [AEM Forms JEE 설치 프로그램 설치](#install-aem-forms-jee-installer) 를 참조하십시오.

* 서신 관리:사용자가 [!DNL Word] 문서의 컨텐츠를 붙여넣으면 텍스트 문서 조각은 서식을 유지하지 않습니다(NPR-33213).
* 적응형 양식: 적응형 양식 사전의 문자열에 새 줄이 있으면 사전에 `&#xa;` 문자가 추가됩니다(NPR-33265).
* 적응형 양식: 사용자가 둘 이상의 첨부 파일이 있는 적응형 양식을 저장할 수 없습니다(NPR-33214).
* 응용 Forms:인스턴스 관리자 클래스에 대한 `AddInstance` 및 `RemoveInstance` 메서드는 [!DNL Internet Explorer 11]에서 지연 로드 조각에 대한 동적 인스턴스 수를 추가하지 않습니다(NPR-33201).
* 응용 Forms:[!DNL Sites] 페이지에 포함된 적응형 양식에 활성화된 Analytics는 제출 및 중단 이벤트에 대한 데이터를 기록하지 않습니다(NPR-31359).
* 응용 Forms:사용자가 [!DNL Word] 문서의 컨텐츠를 적응형 양식에 붙여넣고 제출하면 제출된 적응형 양식에 유니코드 문자가 포함됩니다. 또한 유니코드 문자로 인해 PDF를 PDF/A로 변환할 수 없습니다(NPR-33348).
* 백엔드 통합: 잘못된 비활성 상태로 인해 새로 고침 토큰이 만료되므로 양식 데이터 모델 요청이 실패합니다(NPR-33168).
* 문서 서비스:[!DNL Linux] 서버에서 [!DNL WebLogic]에 대한 깁슨 jar이 누락되어 PDF 변환 서비스가 PostScript로 변환되지 못했습니다(NPR-33515, CQ-4292239).
* 문서 서비스:사용자가 텍스트 파일을 PDF로 변환하면 일본어 문자가 올바르게 렌더링되지 않습니다(NPR-33239).
* GuideSOMProviderServlet과 함께 저장된 XSS(NPR-32701).

## 6.4.8.4 설치 {#install}

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
>AEM 6.4에 기능 팩이 설치된 고객의 경우. Adobe에서 제공하는 선택적 기능 팩은 릴리스 버전 및 서비스 팩에 종속되어 있습니다. 기능 팩이 설치되어 있는 경우 AEM 고객 지원팀에 문의하여 해당 기능 팩과 AEM 6.4용 누적 수정 팩의 호환성을 확인하십시오.

* AEM 6.4.8.4를 사용하려면 AEM 6.4.8.0이 필요합니다. 세부 지침은 [업그레이드 설명서](../sites-deploying/upgrade.md)를 참조하십시오.
* MongoDB 및 여러 인스턴스가 포함된 배포에서 패키지 관리자를 사용하여 작성자 인스턴스 중 하나에 AEM 6.4.8.4을 설치합니다.
* 누적 수정 팩을 설치하기 전에 AEM 인스턴스의 스냅샷 또는 새 백업이 있는지 확인하십시오.
* 설치하기 전에 인스턴스를 다시 시작합니다. 이 작업은 인스턴스가 업데이트 모드 상태에서만 필요하지만 이전 버전에서 인스턴스가 방금 업데이트된 경우입니다. 일반적으로 인스턴스가 오랫동안 실행 중인 경우 권장됩니다.

>[!NOTE]
>
>AEM 6.4.8.4 패키지를 삭제하거나 제거하지 않는 것이 좋습니다.

### 누적 수정 팩 {#install-cumulative-fix-pack} 설치

기존 AEM 6.4.8.0 인스턴스에 누적 수정 팩을 설치하려면 다음 단계를 수행하십시오.

1. [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) 링크를 클릭하여 패키지를 다운로드합니다.

1. [패키지 관리자](http://localhost:4502/crx/packmgr/index.jsp)를 열고 **[!UICONTROL 패키지 업로드]**&#x200B;를 클릭하여 패키지를 업로드합니다.

1. 패키지 이름을 선택하고 **[!UICONTROL 설치]**&#x200B;를 클릭합니다.

>[!NOTE]
>
>**패키지 관리자 UI의 대화 상자가 6.4.8.4 설치 중에 종료되는 경우가 있습니다.**
>
>따라서 인스턴스에 액세스하기 전에 오류 로그가 안정화될 때까지 기다리는 것이 좋습니다. 사용자는 Updater 번들 제거와 관련된 특정 로그가 생성된 후에 설치가 성공적으로 수행되었는지 확인해야 합니다. 일반적으로 Safari에서 발생하지만, 브라우저에서는 간헐적으로 발생할 수 있습니다.

### 자동 설치 {#auto-installation}

실행 중인 인스턴스에 AEM 6.4.8.4을 자동으로 설치하는 두 가지 방법이 있습니다.

A. 서버가 실행되는 동안 패키지를 ..*/crx-quickstart/install* 폴더에 배치합니다. 패키지가 자동으로 설치됩니다.

B. 패키지 관리자에서 [HTTP API](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) 를 사용하여 `cmd=install&recursive=true` 를 사용하는지 확인합니다. 이 경우 중첩된 패키지가 설치됩니다.

>[!NOTE]
>
>AEM 6.4.8.4은 부트스트랩 설치를 지원하지 않습니다.

### 설치 확인 {#validate-install}

1. 제품 정보 페이지(*/system/console/productinfo*)에 설치된 제품 아래에 업데이트된 버전 문자열 &quot;Adobe Experience Manager, 버전 6.4.8.4&quot;가 표시됩니다.
1. 모든 OSGI 번들은 OSGi 콘솔에서 ACTIVE이거나 FRAGMENT입니다(웹 콘솔 사용: /system/console/bundles).
1. OSGI 번들 org.apache.jackrabbit.oak-core는 버전 1.8.17 이상에 있습니다(웹 콘솔 사용: /system/console/bundles).

이 버전의 AEM Sites 및 Assets에서 실행할 인증된 플랫폼을 확인하려면 [기술 요구 사항](../sites-deploying/technical-requirements.md) 을 참조하십시오.

>[!NOTE]
>패키지를 성공적으로 설치하면 컨텐츠 패키지가 성공적으로 설치되었음을 나타내는 정보 메시지가 표시됩니다. (예: **&quot;Content Package AEM-6.4-Service-Pack-8이 성공적으로 설치되었습니다.&quot;**)

### Dynamic Media 뷰어 업데이트(5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.4에는 이미지 사전 설정 페이지에서 중복 이름을 확인할 수 있는 Dynamic Media 뷰어(5.10.1)의 새 버전이 포함되어 있습니다. Dynamic Media 고객은 box 뷰어 사전 설정을 최신 상태로 전환하려면 다음 명령을 실행하는 것이 좋습니다.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

새 뷰어 사전 설정을 /conf 위치에 복사합니다.

### AEM Forms 추가 기능 패키지 설치 {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 는 예정된  [!DNL Experience Manager] 누적 수정 팩 릴리스 날짜로부터 1주일 후에 추가 기능 패키지를 출시합니다.

>[!NOTE]
>
>AEM Forms를 사용하지 않는 경우 건너뜁니다. AEM Forms의 수정 사항은 별도의 추가 기능 패키지를 통해 전달됩니다.

1. AEM 누적 수정 팩을 설치했는지 확인합니다.
1. 운영 체제에 대해 [AEM Forms 릴리스](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#forms-updates)에 나열된 해당 양식 추가 기능 패키지를 다운로드합니다.
1. [AEM Forms 추가 기능 패키지 설치](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package)에 설명된 대로 양식 추가 기능 패키지를 설치합니다.

### AEM Forms JEE 설치 프로그램 {#install-aem-forms-jee-installer} 설치

>[!NOTE]
>
>JEE에서 AEM Forms를 사용하지 않는 경우 건너뜁니다. 별도의 설치 관리자를 통해 AEM Forms JEE의 수정 사항이 전달됩니다.

AEM Forms JEE용 누적 설치 프로그램 설치 및 배포 후 구성에 대한 자세한 내용은 [AEM Forms JEE 패치 설치 프로그램](jee-patch-installer-64.md) 을 참조하십시오.

>[!NOTE]
>
>JEE의 Forms Experience Manager용 누적 설치 프로그램을 설치한 후 최신 Forms 추가 기능 패키지를 설치하고 `crx-repository\install` 폴더에서 Forms 추가 기능 패키지를 삭제한 다음 서버를 다시 시작합니다.

### Uber Jar {#uber-jar}

AEM 6.4.8.4용 Uber Jar는 [Maven Central 저장소](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/)에서 사용할 수 있습니다.

Maven 프로젝트에서 Uber Jar를 사용하려면 문서 [Uber jar 사용 방법](../sites-developing/ht-projects-maven.md)을 참조하여 프로젝트 POM에 다음 종속성을 포함하십시오.

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar 및 기타 관련 가공물은 Public Maven 저장소(repo.adobe.com) 대신 Maven 중앙 저장소에서 사용할 수 있습니다. 기본 UberJar 파일의 이름이 `uber-jar-<version>.jar`로 변경되었습니다. 따라서 `dependency` 태그에 대해 `apis` 값이 있는 `classifier`이 없습니다.

## 제거된/더 이상 사용되지 않는 기능 {#removed-deprecated-features}

이 섹션에는 AEM 6.4에서 제거되었거나 이제 사용되지 않는 기능이 나와 있습니다.

| 영역 | 기능 | 대체 | 버전 |
|---|---|---|---|
| 자산 | 하위 자산에 대한 태그 작업 관리 | 교체 없음 | AEM 6.4.2.0 |
| Assets과 Adobe Creative Cloud 통합 | [AEM과 Creative Cloud 폴더 공유](https://docs.adobe.com/content/help/ko-KR/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html)는 Creative 사용자에게 AEM의 자산에 대한 액세스 권한을 제공하는 방법으로 AEM 6.2에 도입되었습니다. Creative Cloud 애플리케이션에서 새롭게 출시된 기능인 Adobe Asset Link는 Photoshop, InDesign 및 Illustrator에서 직접 AEM 자산에 액세스할 수 있는 강력한 권한과 함께 우수한 사용자 경험을 제공합니다. Adobe는 폴더 공유 기능에 대한 추가 개선을 하지 않습니다. 이 기능은 AEM에 포함되어 있지만 고객은 교체 서비스를 사용하는 것이 좋습니다. | Adobe 자산 링크 또는 데스크탑 앱. 자세한 내용은 [AEM Creative Cloud 통합](/help/assets/aem-cc-integration-best-practices.md) 문서를 참조하십시오. | AEM 6.4.4.0 |

## 알려진 문제 {#known-issues}

* [!DNL Experience Manager] 6.4에서 [!DNL Experience Manager] 6.5로 업그레이드하는 경우 일부 번들이 상태를 `Active` 로 표시하지 않을 수 있습니다. 문제를 해결하려면 최신 [!DNL Experience Manager] 6.5 서비스 팩을 설치하십시오.

AEM 6.4.8.0 서비스 팩의 알려진 문제에 대한 자세한 내용은 [AEM 6.4.8.0 서비스 팩 릴리스 노트](sp-release-notes.md)를 참조하십시오.

## OSGi 번들 및 컨텐츠 패키지가 포함됨 {#osgi-bundles-and-content-packages-included}

다음 텍스트 문서에는 AEM 6.4.8.4에 포함된 OSGi 번들 및 컨텐츠 패키지 목록이 나와 있습니다.

AEM 6.4.8.4에 포함된 OSGi 번들 목록

[파일 가져오기](assets/6.4.8.4_osgi_bundles.txt)

AEM 6.4.8.4에 포함된 컨텐츠 패키지 목록

[파일 가져오기](assets/6.4.8.4_content_packages.txt)

## 유용한 리소스 {#helpful-resources}

* [AEM 6.4 릴리스 노트](../release-notes/release-notes.md)
* [AEM 제품 페이지](https://www.adobe.com/kr/solutions/web-experience-management.html)
* [AEM 6.4 설명서](https://helpx.adobe.com/kr/support/experience-manager/6-4.html)
* [Adobe 우선 순위 제품 업데이트](https://www.adobe.com/subscription/priority-product-update.html) 구독

## 제한된 사이트 {#restricted-sites-new}

다음 사이트는 고객만 사용할 수 있습니다. 액세스가 필요한 고객의 경우 Adobe 계정 관리자에게 문의하십시오.

* [licensing.adobe.com에서 제품 다운로드](https://licensing.adobe.com/)
* [고객 지원 팀에 문의](https://docs.adobe.com/content/help/ko-KR/customer-one/using/home.html)
