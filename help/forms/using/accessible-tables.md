---
title: HTML5 양식에서 액세스 가능한 복잡한 표 만들기
seo-title: Create accessible complex tables in HTML5 forms
description: HTML5 양식에서 액세스 가능한 테이블을 만드는 방법을 알아봅니다.
seo-description: Learn how to create accessible tables in HTML5 forms.
uuid: e52562d2-4dc3-4359-9dbb-c18614921808
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: Mobile Forms
exl-id: a3337bb1-635c-4dc9-b438-3a829d4a9e03
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 2%

---

# HTML5 양식에서 액세스 가능한 복잡한 표 만들기 {#create-accessible-complex-tables-in-html-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

HTML5 Forms에 있는 표의 기본 구현에서는 HTML DIV 요소를 사용하여 테이블을 렌더링합니다. 렌더링에는 액세스 가능성 요구 사항을 충족하기 위해 ARIA 역할을 사용하는 것이 포함됩니다.

데이터 테이블과 함께 사용되는 ARIA 역할을 완전히 지원하지 않는 화면 판독기의 액세스 가능성 문제를 방지하기 위해 Analysis Workspace5 Forms에서 테이블에 대한 대체 변환을 제공합니다. 다음 표는 다음과 같은 기능을 지원하는 디자이너에 도입된 새로운 테이블 형식을 기반으로 합니다.

* 행 머리글
* 행 범위

HTML5 Forms에서 새 형식을 사용하려면 표를 복합적으로 표시합니다. 표를 복잡으로 표시하려면 을 추가합니다 `extras` 태그 내에 있는 하위 폼의 XML 원본은 다음과 같습니다.

```
</extras>
 <text name="complexTable">1</text>
 </extras>
```

로 표시된 테이블 *complexTable* 기본 HTML 변환을 수행하고 특정 화면 판독기에 대해 더 나은 액세스 가능성 지원을 제공합니다.  행 범위를 만들려면 같은 열에서 테이블의 연속 셀을 선택하고 선택 항목을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL 셀 병합]**.

***참고:**행 범위 만들기는 맨 왼쪽 셀에만 작동합니다.*

행을 행 머리글로 표시하려면 행의 모든 셀을 선택하고 선택 항목을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL 마크 헤더]**.

셀을 열 헤더로 표시하려면 열에서 임의의 셀을 선택하고 선택 항목을 마우스 오른쪽 단추로 클릭한 다음 을 클릭합니다 **[!UICONTROL 마크 헤더]**.

새로운 기능의 제한 사항 *AccessibleTable* 형식:

* 테이블에 행 범위를 사용하는 경우 확장 가능한 필드를 지원하지 않습니다
* 중첩된 표(표 셀 내의 표)에 대한 지원이 없습니다
* 행 범위 지원은 헤더 행 및 헤더 셀로 제한됩니다
* 지원은 일반 테이블로 제한됩니다
* 행 범위가 1보다 큰 테이블에서 데이터 미리 채우기를 지원하지 않습니다
