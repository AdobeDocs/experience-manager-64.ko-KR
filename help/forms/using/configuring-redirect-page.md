---
title: 리디렉션 페이지 구성
seo-title: 리디렉션 페이지 구성
description: 적응형 양식을 작성한 후 양식을 만드는 동안 양식 작성자가 구성할 수 있는 웹 페이지로 사용자를 리디렉션할 수 있습니다.
seo-description: 적응형 양식을 작성한 후 양식을 만드는 동안 양식 작성자가 구성할 수 있는 웹 페이지로 사용자를 리디렉션할 수 있습니다.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d

---


# 리디렉션 페이지 구성 {#configuring-redirect-page}

양식 작성자는 양식을 제출한 후 양식 사용자가 리디렉션되는 각 양식에 대한 페이지를 구성할 수 있습니다.

1. 편집 모드에서 구성 요소를 선택한 다음 ![필드 수준](assets/field-level.png) > 적응형 양식 **컨테이너를**&#x200B;클릭한 다음 ![cmppr](assets/cmppr.png)을클릭합니다.

1. 세로 막대에서 [제출]을 **클릭합니다**.

1. 제출 섹션의 감사 페이지 아래에 리디렉션 페이지의 URL을 제공합니다.
1. REST에 제출 끝점 동작의 [작업 제출] 아래에서 리디렉션 페이지에 전달할 매개 변수를 구성할 수 있습니다.

![](assets/thank-you-setting-1.png) 리디렉션 페이지 구성&#x200B;****&#x200B;그림:리디렉션 *페이지 구성*

양식 작성자는 감사 페이지에 전달된 다음 매개 변수를 사용할 수 있습니다. 사용 가능한 모든 제출 작업에 대해 `status` 및 `owner` 매개 변수가 전달됩니다. 이러한 두 매개 변수 외에 다음과 같은 제출 작업에 대한 일부 추가 매개 변수가 전달됩니다.

* **컨텐츠 저장 작업** (더 이상 사용되지 않음):( `contentPath`The path of the node in the repository where submitted data is stored—is passed. is passed.)

* **PDF 저장 동작** (더 이상 사용되지 않음):Of the submitted data and path to the node storing the PDF file in the repository—is passed. `contentPath`

* **양식에 제출 워크플로우**:양식 워크플로우에서 반환된 출력 매개 변수가 전달됩니다.

* **REST 종단점에 제출**:필드 내-매개 변수 매핑에 추가된 매개 변수가 전달됩니다. `status` 및 `owner` 매개 변수는 이 제출 작업에서 전달되지 않습니다. 자세한 내용은 REST에 [제출 끝점 제출 작업](/help/forms/using/configuring-submit-actions.md)구성을 참조하십시오.

