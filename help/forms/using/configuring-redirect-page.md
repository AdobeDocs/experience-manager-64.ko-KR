---
title: 리디렉션 페이지 구성
seo-title: Configuring redirect page
description: 적응형 양식을 채운 후에는 양식을 만드는 동안 양식 작성자가 구성할 수 있는 웹 페이지로 사용자를 리디렉션할 수 있습니다.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---

# 리디렉션 페이지 구성 {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

양식 작성자는 양식을 제출한 후 양식 사용자가 리디렉션되는 각 양식에 대해 페이지를 구성할 수 있습니다.

1. 편집 모드에서 구성 요소를 선택한 다음 ![필드 수준](assets/field-level.png) > **적응형 양식 컨테이너**&#x200B;를 클릭한 다음 ![cmppr](assets/cmppr.png).

1. 사이드바에서 **제출**.

1. 제출 서류 섹션의 감사 인사 페이지 아래에 리디렉션 페이지의 URL을 입력합니다.
1. 선택적으로, 제출 작업에서 REST에 제출 끝점 작업에 대해 리디렉션 페이지에 전달될 매개 변수를 구성할 수 있습니다.

![페이지 구성 리디렉션](assets/thank-you-setting-1.png)
**그림:** *페이지 구성 리디렉션*

양식 작성자는 감사 인사 페이지에 전달되는 다음 매개 변수를 사용할 수 있습니다. 사용 가능한 모든 제출 작업에 대해, `status` 및 `owner` 매개 변수가 전달됩니다. 이 두 매개 변수 외에 다음 제출 작업에 대한 몇 가지 추가 매개 변수가 전달됩니다.

* **컨텐츠 저장 작업** (사용하지 않음) : `contentPath`- 제출된 데이터가 저장되는 저장소의 노드 경로 가 전달됩니다.

* **PDF 작업 저장** (사용하지 않음) : `contentPath`—저장소에 PDF 파일을 저장하는 노드에 대한 제출된 데이터 및 경로가 전달됩니다.

* **Forms 워크플로우에 제출**: 양식 워크플로우에서 반환된 출력 매개 변수가 전달됩니다.

* **REST 엔드포인트에 제출**: 필드-매개 변수 매핑에 추가된 매개 변수가 전달됩니다. `status` 및 `owner` 이 제출 작업에는 매개 변수가 전달되지 않습니다. 자세한 내용은 [REST에 제출 끝점 제출 작업 구성](/help/forms/using/configuring-submit-actions.md).
