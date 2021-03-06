---
title: 리디렉션 페이지 구성
seo-title: 리디렉션 페이지 구성
description: 적응형 양식을 채운 후에는 양식을 만드는 동안 양식 작성자가 구성할 수 있는 웹 페이지로 사용자를 리디렉션할 수 있습니다.
seo-description: 적응형 양식을 채운 후에는 양식을 만드는 동안 양식 작성자가 구성할 수 있는 웹 페이지로 사용자를 리디렉션할 수 있습니다.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: 적응형 양식
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 리디렉션 페이지 {#configuring-redirect-page} 구성

양식 작성자는 양식을 제출한 후 양식 사용자가 리디렉션되는 각 양식에 대해 페이지를 구성할 수 있습니다.

1. 편집 모드에서 구성 요소를 선택한 다음 ![필드 수준](assets/field-level.png) > **적응형 양식 컨테이너**&#x200B;를 클릭한 다음 ![cmppr](assets/cmppr.png)를 클릭합니다.

1. 사이드바에서 **제출**&#x200B;을 클릭합니다.

1. 제출 서류 섹션의 감사 인사 페이지 아래에 리디렉션 페이지의 URL을 입력합니다.
1. 선택적으로, 제출 작업에서 REST에 제출 끝점 작업에 대해 리디렉션 페이지에 전달될 매개 변수를 구성할 수 있습니다.

![리디렉션 페이지 ](assets/thank-you-setting-1.png)
**구성그림:** *리디렉션 페이지 구성*

양식 작성자는 감사 인사 페이지에 전달되는 다음 매개 변수를 사용할 수 있습니다. 사용 가능한 모든 제출 작업에 대해 `status` 및 `owner` 매개 변수가 전달됩니다. 이 두 매개 변수 외에 다음 제출 작업에 대한 몇 가지 추가 매개 변수가 전달됩니다.

* **컨텐츠 저장 작업** (더 이상 사용되지 않음) : `contentPath`- 제출된 데이터가 저장되는 저장소의 노드 경로 가 전달됩니다.

* **PDF 저장 작업** (더 이상 사용되지 않음) : `contentPath`—저장소에 PDF 파일을 저장하는 노드에 대한 제출된 데이터 및 경로가 전달됩니다.

* **Forms 워크플로우에 제출**:양식 워크플로우에서 반환된 출력 매개 변수가 전달됩니다.

* **REST 엔드포인트에 제출**:필드-매개 변수 매핑에 추가된 매개 변수가 전달됩니다. `status` 및  `owner` 매개 변수는 이 제출 작업에서 전달되지 않습니다. 자세한 내용은 [REST에 제출 끝점 구성 제출 작업](/help/forms/using/configuring-submit-actions.md)을 참조하십시오.
