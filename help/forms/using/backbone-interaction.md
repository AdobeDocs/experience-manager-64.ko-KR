---
title: 백본 상호 작용
seo-title: Backbone interaction
description: AEM Forms 작업 공간에서 백본 JavaScript 모델 사용에 대한 개념 정보입니다.
seo-description: Conceptual information about use of Backbone JavaScript models in AEM Forms workspace.
uuid: c70da848-e514-42bc-a59b-44a7c00aa529
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: d363eec3-172b-413e-9743-ed51804ea1e9
exl-id: f726cb73-732c-4893-bdb5-10ddcf4a340a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 1%

---

# 백본 상호 작용 {#backbone-interaction}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

백본은 웹 응용 프로그램에서 MVC 아키텍처를 만들고 따르는 데 도움이 되는 라이브러리입니다. 백본의 기본 개념은 인터페이스를 논리 뷰로 구성하는 것입니다. 모델을 기반으로 하여 페이지를 다시 그릴 필요 없이 모델을 변경할 때 개별적으로 업데이트할 수 있습니다. 백본에 대한 자세한 내용은 [https://backbonejs.org](https://backbonejs.org/).

몇 가지 주요 개념은 다음과 같습니다.

**백본 모델** 데이터 및 이 데이터와 관련된 대부분의 논리를 포함합니다.

**백본 보기** 해당 모델의 상태를 나타내는 데 사용됩니다. 백본 보기는 실제로 컨트롤러처럼 동작하며, 사용자 클릭과 같은 사용자 인터페이스 이벤트를 수신하거나, 이벤트(예: 변경된 데이터)를 모델링하고, 사용자 인터페이스를 적절하게 수정합니다.

**HTML 템플릿** 모델로 채워진 자리 표시자가 있는 래퍼 템플릿입니다.

**AEM Forms 작업 공간** 여러 개의 개별 구성 요소를 포함합니다. 각 구성 요소:

* 단일 논리 사용자 인터페이스 요소를 나타냅니다.
* 유사한 구성 요소의 컬렉션일 수 있습니다.
* 백본 모델, 백본 보기 및 HTML 템플릿으로 구성됩니다.
* 서비스에 대한 참조를 포함합니다.
* 필수 유틸리티에 대한 참조를 포함합니다.

구성 요소를 초기화하면 다음 개체가 만들어집니다.

* 구성 요소에 대한 백본 모델의 새 인스턴스가 생성됩니다. 모델에 서비스가 삽입됩니다.
* 백본 보기의 새 인스턴스가 만들어집니다.
* 해당 모델, HTML 템플릿 및 유틸리티의 인스턴스가 뷰에 삽입됩니다.

백본 뷰에는 해당 처리기와의 사용자 인터페이스 상호 작용으로 인해 발생할 수 있는 다양한 이벤트를 매핑하는 이벤트 맵이 있습니다. 구성 요소가 초기화되면 이 매핑이 시작됩니다.

보기가 초기화되면 보기에서 해당 모델을 호출하여 서버에서 데이터를 가져옵니다. 보기에 필요한 모든 데이터를 사용할 수 있으면 보기에서 HTML 템플릿에서 지정한 형식으로 데이터를 렌더링합니다. 여러 보기가 커뮤니케이션을 위해 동일한 모델을 공유할 수 있습니다.

![](do-not-localize/aem_forms_workflow.png)

예:

1. 사용자가 작업 목록에서 작업 템플릿을 클릭합니다.
1. 작업 보기는 클릭을 수신하고 작업 모델에서 렌더링 함수를 호출합니다.
1. 작업 모델은 그 후에 AEM Forms 서버와의 모든 통신에 공통점인 서비스를 호출합니다.
1. 서비스 클래스는 ajax를 통해 렌더링 메서드에 대해 AEM Forms REST 끝점을 호출합니다.
1. 이 Ajax 호출에 대한 성공 콜백은 작업 모델에 정의되어 있습니다.
1. 작업 모델은 렌더링 호출이 완료되는 알림으로 백본 이벤트를 발생시킵니다.
1. 다른 보기, 작업 세부 정보 보기는 작업 모델에서 이 이벤트를 수신합니다.
1. 그런 다음 작업 세부 정보 보기를 통해 렌더링된 작업(양식, 세부 정보, 첨부 파일, 노트 등)을 사용자에게 표시하도록 작업 세부 사항 템플릿을 변경합니다.
