---
title: Forms 포털 구성 요소 활성화
seo-title: Enabling forms portal components
description: 곧바로 사용할 수 있는 Forms Portal 구성 요소는 비활성화됩니다. Document Services 및 Document Services 설명 그룹 을 활성화하여 Forms Portal 구성 요소를 활성화합니다.
seo-description: Out of the box, Forms Portal components are disabled. Enable Document Services and Document Services Predicates groups to enable Forms Portal components.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Forms Portal
exl-id: 01c5eb6b-b097-4354-84b2-8bee7b7626f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 2%

---

# Forms 포털 구성 요소 활성화 {#enabling-forms-portal-components}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

기본적으로 forms 포털 구성 요소는 사용할 수 없습니다. 구성 요소가 AEM 사이드 킥에서 사용 가능한 구성 요소 목록에 나타나도록 하려면 다음 단계를 수행하십시오.

1. 웹 사이트의 작성자 인스턴스에 로그인하고 AEM Sites 페이지를 엽니다.

1. 정적 템플릿을 사용하는 페이지의 경우 다음 단계를 수행하십시오.

   1. 페이지 헤더에서 ![캔버스 드롭다운](assets/canvas-drop-down.png) > **디자인** 페이지를 디자인 모드에서 엽니다.
   1. 파란색 테두리로 구성 요소를 탭한 다음 탭합니다. ![필드 수준](assets/field-level.png) 현재 구성 요소가 포함된 단락 시스템을 선택하려면 다음을 수행하십시오.
   1. 단락 시스템에서 ![settings_icon](assets/settings_icon.png) 단락 시스템의 편집 대화 상자를 엽니다.
   1. 목록 **[!UICONTROL 허용된 구성 요소]**, 확인란을 활성화합니다. **[!UICONTROL 문서 서비스]** 및 **[!UICONTROL 문서 서비스 설명]** 구성 요소. 탭 **[!UICONTROL 확인]**.

1. 동적 템플릿을 사용하는 페이지의 경우 다음 단계를 수행하십시오.

   1. 페이지 헤더에서 ![속성](assets/properties.png) > **템플릿 편집** 페이지의 템플릿을 엽니다.
   1. 탭 **레이아웃 컨테이너** 탭 ![FeedManagement](assets/FeedManagement.png). 에서 **허용된 구성 요소** 탭에서 을 활성화합니다 **문서 서비스 및 문서 서비스 설명** 옵션 및 탭 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>구성 요소를 선택하여 이러한 카테고리에서 특정 구성 요소를 활성화할 수도 있습니다. 구성 요소 및 해당 사용법에 대한 자세한 내용은 [양식 포털 페이지 만들기](/help/forms/using/creating-form-portal-page.md) 및 [페이지에 링크 구성 요소 포함](/help/forms/using/embedding-link-component-page.md).

이제 문서 서비스 및 문서 서비스 설명 구성 요소 범주는 구성 요소 브라우저에서 사용할 수 있습니다. 동일한 템플릿을 사용하는 모든 페이지에 대해 구성 요소가 활성화됩니다.

## 관련 문서

* [Forms 포털 구성 요소 활성화](/help/forms/using/enabling-forms-portal-components.md)
* [Forms 포털 만들기 페이지](/help/forms/using/creating-form-portal-page.md)
* [API를 사용하여 웹 페이지의 양식 나열](/help/forms/using/listing-forms-webpage-using-apis.md)
* [초안 및 제출 구성 요소 사용](/help/forms/using/draft-submission-component.md)
* [초안 및 제출된 양식의 저장 공간 사용자 정의](/help/forms/using/draft-submission-component.md)
* [초안 및 제출 구성 요소와 데이터베이스를 통합하기 위한 샘플](/help/forms/using/integrate-draft-submission-database.md)
* [Forms 포털 구성 요소에 대한 템플릿 사용자 지정](/help/forms/using/customizing-templates-forms-portal-components.md)
* [포털에서 양식 게시 소개](/help/forms/using/introduction-publishing-forms.md)
