---
title: 양식 관리 소개
seo-title: 양식 관리 소개
description: AEM Forms은 적용형 Forms 및 관련 자산을 관리하는 도구를 제공합니다. 이 문서에서는 주요 양식 관리 기능 및 사용자 인터페이스 요소를 소개합니다.
seo-description: AEM Forms은 적용형 Forms 및 관련 자산을 관리하는 도구를 제공합니다. 이 문서에서는 주요 양식 관리 기능 및 사용자 인터페이스 요소를 소개합니다.
uuid: 8a9fe83a-e9dc-410e-9bae-eca936c6eb8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager, introduction
discoiquuid: 6f9cb26a-ac7f-4218-827f-9d4d55b859b4
exl-id: 08686ad6-85cc-4de5-86d8-05d55acec418
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1605'
ht-degree: 0%

---

# 양식 관리 소개 {#introduction-to-managing-forms}

AEM Forms은 양식, 문서, 테마, 문자, 문서 조각, 데이터 사전 및 관련 자산을 만들고 관리할 수 있는 간단하면서도 강력한 사용자 인터페이스를 제공합니다. 개발자의 데스크탑에서 서비스에 이르기까지 양식, 문서 및 관련 자산의 전체 라이프사이클을 관리하는 데 도움이 됩니다\
최종 사용자를 위한 포털 서버에 게시됩니다. AEM Forms 사용자 인터페이스를 사용하여 다음을 수행할 수 있습니다.

* AEM Forms 구성 요소 액세스
* AEM Forms 구성 액세스

>[!NOTE]
>
>다른 AEM 도구 및 옵션에 대한 자세한 내용은 [작성 환경 사용](/help/sites-authoring/home.md)을 참조하십시오.

## AEM Forms 구성 요소 {#access-aem-forms-components}에 액세스

양식, 문서 및 관련 자산을 만드는 옵션과 함께 AEM에서는 사이트, 자산을 만들고 AEM 인스턴스를 관리하는 등의 옵션을 제공합니다. ![adobeexperiencemanager](assets/adobeexperiencemanager.png) Experience Manager 로고를 클릭하여 사용 가능한 모든 도구로 이동할 수 있습니다. 다른 구성 요소의 콘솔에 대한 링크와 함께, AEM Forms에 대한 링크도 포함되어 있습니다. AEM Forms으로 이동하려면 **Experience Manager 로고** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **탐색** ![나침반](assets/compass.png) > **Forms**&#x200B;를 클릭합니다. 다음 콘솔의 링크가 표시됩니다.

* 양식 및 문서
* 테마
* 편지
* 문서 단편
* 데이터 사전

![aem-forms-console](assets/aem-forms-console.png)

### 양식 및 문서  {#forms-documents}

Forms 및 문서는 대화형 통신, 적응형 양식, 적응형 양식 조각 및 양식 세트를 만드는 옵션을 제공합니다. Forms 및 문서는 JEE의 AEM Forms에만 로컬 저장소에서 파일을 가져오고 AEM Forms 자산을 Workbench와 동기화하는 옵션을 제공합니다.

만들기 버튼은 AEM Forms 자산을 만들거나 업로드하는 프로세스의 시작점입니다. 다음과 같은 만들기 옵션을 제공합니다.

* **대화형 통신**:대화형 커뮤니케이션은 개인화되고, 대화형 및 장치 친화적인 HTML 기반 디지털 서신, 문 또는 문서입니다. 대화형 커뮤니케이션은 자연에 응답하며 사용자 장치 및 설정에 따라 레이아웃 및 디자인을 자동으로 변경합니다. 자세한 내용은 [대화형 통신 개요](/help/forms/using/interactive-communications-overview.md)를 참조하십시오.

* **적응형 양식:** 적응형 양식은 매력적인 반응형 양식입니다. 사용자 응답, 장치 또는 작업 환경에 따라 양식 섹션을 추가하거나 제거하여 사용자 입력에 동적으로 적응하는 적응형 양식을 작성할 수 있습니다. [적응형 양식 작성 소개](/help/forms/using/introduction-forms-authoring.md) 문서에서는 적응형 양식에 대한 자세한 정보를 제공합니다.

* **적응형 양식 조각:** 모든 양식은 특정 용도로 디자인되지만, 이름 및 주소, 가족 세부 사항, 소득 세부 사항 등과 같은 개인 세부 사항을 제공하는 등 대부분의 양식에는 몇 가지 공통 세그먼트가 있습니다. 이러한 섹션에 대해 개별 자산을 생성할 수 있습니다. 이러한 재사용 가능한 독립 실행형 세그먼트를 적응형 양식 조각이라고 합니다. 자세한 내용은 [적응형 양식 조각](/help/forms/using/adaptive-form-fragments.md) 문서를 참조하십시오.

* **양식 세트:**  양식 세트는 함께 그룹화되어 최종 사용자에게 단일 양식 세트로 제공되는 HTML5 양식의 컬렉션입니다. 최종 사용자가 양식 세트에 입력을 시작하면 양식은 한 양식에서 다른 양식으로 원활하게 전환됩니다. 결국 사용자는 한 번의 클릭으로 모든 양식을 단일 엔티티로 제출할 수 있습니다. 자세한 내용은 AEM Forms](/help/forms/using/formset-in-aem-forms.md)에서 양식 세트 [를 참조하십시오.

* **폴더:** AEM Forms 사용자 인터페이스는 폴더를 사용하여 자산을 정렬합니다. 두 가지 유형의 폴더를 지원합니다.

   * **일반 폴더:**  이 폴더는 AEM Forms 사용자 인터페이스 내에서 만든 자산에 사용됩니다. 이러한 폴더에는 엄격한 폴더 구조가 없습니다. 이러한 폴더에 적응형 양식, 대화형 통신, 적응형 양식 조각, 양식 템플릿(XDP), PDF forms, 문서 및 관련 자산의 이름을 변경하고, 하위 폴더를 만들고 저장할 수 있습니다.
   * **Forms Workflow 폴더:** Forms 워크플로우 폴더는 Workbench 프로세스(LiveCycle 아카이브)가 마이그레이션되고 AEM Forms 사용자 인터페이스와 동기화될 때 생성됩니다. 이름 변경, 하위 폴더 만들기, 대화형 통신, 응용 양식 조각 또는 대화형 커뮤니케이션을 만들 수 없습니다. 버전 폴더를 삭제하거나 적응형 양식, 적응형 양식 조각 또는 대화형 커뮤니케이션을 버전 폴더와 동시에 만들고 업로드할 수도 없습니다.

![폴더](assets/folders.png)

**A.** 일반 폴더  **B.** Forms Workflow 폴더

Forms 및 문서 패널에서는 다음 작업도 수행할 수 있습니다.

* **로컬 저장소에서 파일 가져오기:**  PDF forms 및 문서, 양식 템플릿(XFA 양식) 및 기타 리소스(XSD의 이미지 및 XML 스키마)를 가져올 수 있습니다. 단계별 지침은 [AEM Forms으로 자산 가져오기 및 내보내기](/help/forms/using/import-export-forms-templates.md)를 참조하십시오.

* **AEM Forms 자산을 Workbench와 동기화:** Workbench의 파일 옵션을 사용하여 AEM Forms 사용자 인터페이스와 Workbench 간에 자산을 동기화할 수 있습니다. 이렇게 하면 AEM Forms 사용자 인터페이스와 Workbench의 crx-repository assets 선택 시 모든 자산을 사용할 수 있습니다.

### 테마  {#themes}

테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있습니다. 테마는 독립적인 정체성을 가지고 있다. 따라서 여러 적응형 양식에서 테마를 다시 사용할 수 있습니다. 구성 요소에 대한 스타일을 지정하거나 양식에서 사용되는 다양한 구성 요소의 CSS 속성을 수정할 수 있습니다. 스타일에는 배경색, 상태 색상, 투명도 및 크기와 같은 속성이 포함됩니다. 사용자 지정 내용을 테마로 저장하고 양식의 구성 요소에 사전 설정으로 포팅할 수 있습니다. 양식에 테마를 추가하면 지정된 스타일이 양식의 해당 구성 요소에 반영됩니다. AEM 6.2 Forms을 사용하여 테마를 만들고 양식에 적용할 수 있습니다.

테마 만들기 및 사용에 대한 자세한 내용은 [AEM Forms의 테마](/help/forms/using/themes.md)를 참조하십시오.

### 편지  {#letters}

AEM Forms Letter는 안전하고 개인화된 대화형 커뮤니케이션입니다. AEM Forms을 사용하여 사전 승인된 컨텐츠와 사용자 정의 작성 컨텐츠 모두에서 간소화된 프로세스를 통해 편지(해당라고도 함)를 신속하게 어셈블할 수 있습니다.

문자 만들기 및 사용에 대한 자세한 내용은 [편지 만들기](/help/forms/using/create-letter.md)를 참조하십시오.

### 문서 단편 {#document-fragments}

문서 조각은 편지를 작성할 수 있는 서신의 재사용 가능한 부분 또는 구성 요소입니다. 문서 조각은 텍스트, 목록, 조건 및 레이아웃 조각 유형입니다. 문서 조각 만들기 및 사용에 대한 자세한 내용은 [문서 조각 만들기](/help/forms/using/document-fragments.md)를 참조하십시오.

### 데이터 사전 {#data-dictionaries}

일반적으로 비즈니스 사용자는 XSD(XML 스키마) 및 Java 클래스와 같은 메타데이터 표현에 대한 지식이 필요하지 않습니다. 그러나 일반적으로 솔루션을 구축하려면 이러한 데이터 구조 및 속성에 액세스해야 합니다. AEM Forms은 데이터 사전을 사용하여 비즈니스 사용자가 기본 데이터 모델에 대한 기술 세부 사항을 알지 않고도 백엔드 데이터 소스의 정보를 사용할 수 있습니다.

데이터 사전 만들기 및 사용에 대한 자세한 내용은 [데이터 사전 문서](/help/forms/using/data-dictionary.md) 만들기를 참조하십시오

## AEM Forms 구성 액세스 {#accessing-aem-forms-configurations}

AEM 도구 패널에는 다양한 구성 요소를 위한 도구가 포함되어 있습니다. AEM Forms 관련 도구로 탐색하려면 **Experience Manager 로고** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **도구** ![햄머](assets/hammer.png) > **Forms**&#x200B;를 클릭합니다. 다음 기능을 수행하는 도구가 표시됩니다.

* **감시 폴더 구성:** 관리자가 감시 폴더에 파일(예: PDF 파일)을 배치할 때 사전 구성된 작업이 시작되고 파일을 조작하도록 감시 폴더라는 네트워크 폴더를 구성할 수 있습니다.  <!-- Fix broken link For detailed information, see Create and Configure a watched folder. -->

* **Forms App Offline Service 구성:** AEM Forms 앱 오프라인 서비스는 양식에 사용된 리소스의 경로 또는 URL을 캐시합니다. 양식에 사용되는 리소스의 경로나 URL을 캐싱하면 서버측 성능이 향상됩니다. AEM Forms 앱의 서버측 오프라인 구성 요소를 구성하려면 [오프라인 모드에서 작업](/help/forms/using/work-offline-mode.md)을 참조하십시오.

![aem-forms-tools](assets/aem-forms-tools.png)

* **PDF 생성기 구성:**  관리자는 AEM Forms PDF 생성기 설정을 구성하고, 사용자 계정을 추가하고, PDF 생성기에 구성을 가져오거나 내보낼 수 있습니다.
* **서신 관리 자산 게시:**  AEM Forms을 사용하면 작성자 인스턴스의 모든 편지, 문서 조각 및 데이터 사전 및 관련 종속성을 한 번에 게시할 수 있습니다. 게시된 자산에는 모든 서신 관리 자산 및 관련 종속성이 포함됩니다. 자세한 내용은 [양식 및 문서 게시 및 게시 취소](/help/forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets)를 참조하십시오.
* **서신 관리 자산 내보내기:** 모든 서신 관리 자산 및 관련 종속성을 AEM Forms 인스턴스에서 패키지로 다운로드할 수 있습니다. 자세한 단계는 [AEM Forms으로 자산 가져오기 및 내보내기](/help/forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)를 참조하십시오

## 사용자 인터페이스의 공통 요소 {#commonelements}

* **왼쪽 레일:** 왼쪽 레일 아이콘 레일  ![](assets/railleftpng.png) 레일 아이콘을 클릭하여 AEM Forms의 타임라인 및 참조 기능을 표시할 수 있습니다.

   * **타임라인:**  타임라인에서 검토할 수 있는 자산에 주석을 추가하고 볼 수 있습니다. 자세한 지침은 [양식에 있는 자산에 대한 검토 만들기 및 관리](/help/forms/using/create-reviews-forms.md)를 참조하십시오.
   * **참조:** AEM Forms 자산은 여러 AEM Forms 자산에서 사용할 수 있습니다. 예를 들어 문서 조각은 여러 편지에서 사용할 수 있습니다. 참조 는 선택한 자산이 사용되는 자산(다른 양식 또는 리소스) 목록과 선택한 자산이 사용하는 다른 자산 목록입니다.

* **탐색 표시:**  이동 경로는 현재 콘솔 또는 폴더의 제목을 나타냅니다. 탐색 표시 옵션을 클릭하여 계층 구조에서 높은 폴더 수준 간을 탐색할 수 있습니다.
* **전환기 보기:** 전환기 보기 아이콘  ![](assets/viewlist.png) 뷰목록이나  ![](assets/viewcard.png) 뷰카드 를 클릭하여 목록과 카드 보기 간에 빠르게 전환할 수 있습니다. 일반적인 사용자 인터페이스 구성 요소에 대한 자세한 내용은 [작성 환경 사용](/help/sites-authoring/basic-handling.md)을 참조하십시오.
* **검색:** 검색  ![](assets/search.png) 옵션은 필요한 컨텐츠 및 도구를 빠르게 찾고 이동할 수 있는 기능을 제공합니다. 컨텐츠 또는 제품 기능의 이름을 입력하고 제안에서 선택합니다. 예를 들어, &quot;Documents&quot;를 입력하여 Forms 및 문서 또는 문서 조각 콘솔을 빠르게 찾고 이동합니다. 검색에 대한 자세한 내용은 AEM 6.2 [search](/help/sites-authoring/search.md) 문서를 참조하십시오
* **작업 도구 모음**:자산을 선택할 때 자산 목록 위에 작업 도구 모음이 표시됩니다. 여기에는 선택한 자산에 대한 모든 관리 도구가 포함되어 있습니다. 도구 아이콘 위로 마우스를 가져가면 기능을 설명하는 도구 설명을 볼 수 있습니다

>[!NOTE]
>
>사용자가 Forms 및 문서의 콘솔을 검색할 때 레일에는 **필터 및 옵션**&#x200B;만 포함됩니다. 필터 및 옵션 을 사용하여 고급 검색을 수행할 수 있습니다.

* **작업 도구 모음**:자산을 선택할 때 자산 목록 위에 작업 도구 모음이 표시됩니다. 여기에는 선택한 자산에 대한 모든 관리 도구가 포함되어 있습니다. 도구 아이콘 위로 마우스를 가져가면 기능을 설명하는 도구 설명을 볼 수 있습니다

![적응형 양식에 대한 작업 도구 모음](assets/action-tool-bar.png)
