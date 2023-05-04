---
title: 적응형 양식의 구분 기호 구성 요소
seo-title: Separator component in adaptive forms
description: 구분 기호 구성 요소를 사용하여 양식의 섹션을 시각적으로 분리할 수 있습니다.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
exl-id: 7e37401a-8c63-4711-8a33-61e6bd4b419f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 2%

---

# 적응형 양식의 구분 기호 구성 요소 {#separator-component-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

구분 기호 구성 요소를 사용하여 양식의 패널을 시각적으로 분리할 수 있습니다. 구분 기호 구성 요소의 다음 속성을 지정하여 구분 기호 구성 요소의 전체 모양과 스타일을 정의할 수 있습니다.

* **요소 이름:** 구성 요소의 이름을 지정합니다. SOM 표현식은 요소 이름 필드에 지정된 값으로 구성 요소를 해결합니다.
* **두께:** 구분 기호 구성 요소의 두께(픽셀 단위)를 지정합니다.
* **열 범위:** 구분 기호 구성 요소가 속하는 열의 수를 지정합니다.
* **CSS 클래스:** 구분 기호 구성 요소에 대한 사용자 지정 CSS 클래스를 지정합니다
* **인라인 스타일:** 이제 AEM Forms을 사용하여 개별 적응형 양식 구성 요소에 인라인 CSS 스타일을 적용하고 실시간으로 변경 사항을 미리 볼 수 있습니다.

구분 기호 구성 요소의 속성을 지정하려면

1. 구분 기호 구성 요소를 선택하고 탭합니다 ![cmppr](assets/cmppr.png). 속성은 사이드바에서 열립니다.
1. 인라인 CSS 속성 섹션에서 탭을 클릭하여 CSS 속성을 지정합니다. 예: a. 필드 탭에서 **항목 추가**. 필드가 두 개인 행이 추가됩니다.
1. 왼쪽의 첫 번째 필드에서 적용할 CSS3 속성을 지정합니다. 예, **테두리**. 아래쪽 화살표 단추를 클릭하여 속성을 선택할 수도 있습니다. 드롭다운 목록은 완전하지 않으며 이 필드에 지원되는 CSS3 속성 이름을 지정할 수 있습니다.
1. 인접 필드에서 지정된 CSS3 속성에 유효한 값을 지정합니다. 예, **3px 솔리드 블랙**.
1. 클릭 **항목 추가** 다른 속성과 해당 값을 지정합니다.
1. 클릭 **미리 보기** 양식에서 변경 사항을 미리 보려면
1. 클릭 **확인** 변경 사항을 확인하려면 **취소 **를 클릭하여 변경 없이 대화 상자를 종료합니다.
