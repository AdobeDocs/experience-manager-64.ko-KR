---
title: 스크리블 서명을 사용하여 양식에 전자 서명 적용
seo-title: Apply electronic signatures to a form using scribble signatures
description: 스크리블을 사용한 서명 양식
seo-description: Signing forms using scribble
uuid: e807d0de-6d5f-458e-be3e-273ed7a521c0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 6a806727-28c5-430e-9a83-b43e0e9d9e1c
feature: Adaptive Forms
exl-id: a870c4b7-4040-4bd8-b477-286ebe6a4b01
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 1%

---

# 스크리블 서명을 사용하여 양식에 전자 서명 적용 {#apply-electronic-signatures-to-a-form-using-scribble-signatures}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

를 사용할 수 있습니다 **스크리블 서명** 구성 요소 및 **서명 단계** 적응형 양식에 서명을 그릴 구성 요소(스크리블) 서명 단계 구성 요소는 적응형 양식의 PDF 버전을 표시합니다. 서명 단계 구성 요소를 사용하려면 레코드 문서 옵션을 활성화하거나 양식 템플릿 기반의 적응형 양식을 사용해야 합니다.

두 구성 요소 모두 아래에 표시된 대로 양식에 서명할 창을 제공합니다. 지리적 위치 아이콘을 클릭할 수도 있습니다 ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) 서명에 지리적 위치를 추가하려면

![스크리블 기호 대화 상자](assets/scribble-signature.png)

## 스크리블 서명을 사용하도록 적응형 양식 구성 {#configure-an-adaptive-form-to-use-scribble-signature}

1. 레코드 문서 만들기 옵션을 활성화하거나 양식 서식 파일이 적응형 양식을 기반으로 합니다. 단계별 정보는 [적응형 양식 만들기](/help/forms/using/creating-adaptive-form.md).
1. 드래그 앤 드롭 **스크리블 서명** 구성 요소를 구성 요소 브라우저에서 적응형 양식으로 전환
1. 탭하기 **구성** ![구성](assets/configure.png) 아이콘. 속성 브라우저를 열고 스크리블 서명 구성 요소의 속성을 표시합니다. 스크리블 서명 구성 요소의 속성을 구성합니다.
1. 구성 요소 브라우저에서 적응형 양식으로 서명 단계 구성 요소를 드래그하여 놓습니다.

   >[!NOTE]
   >
   >서명 단계 구성 요소는 양식에 사용할 수 있는 전체 너비를 높입니다. 서명 단계 구성 요소가 포함된 섹션에는 다른 구성 요소가 없는 것이 좋습니다.

1. 콘텐츠 브라우저에서 **양식 컨테이너**&#x200B;를 누르고 를 누릅니다 **구성** ![구성](assets/configure.png) 아이콘. 속성 브라우저를 열고 적응형 양식 컨테이너 속성을 표시합니다. 다음으로 이동 **적응형 양식 컨테이너** > **전자 서명** 선택 취소 **Acrobat Sign 활성화** 선택 사항입니다. 완료 를 누릅니다 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) 아이콘을 클릭하여 변경 사항을 저장합니다.

   >[!NOTE]
   >
   >적응형 양식에 서명 단계 구성 요소를 추가하면 Acrobat Sign 활성화 옵션이 자동으로 선택됩니다.

1. 탭하기 **구성** ![구성](assets/configure.png) 아이콘. 속성 브라우저를 열고 서명 단계 속성을 표시합니다. 다음 속성을 구성합니다.

   * **요소 이름**: 구성 요소의 이름을 지정합니다.
   * **제목:** 구성 요소의 고유한 제목을 지정합니다.
   * **템플릿 메시지:** 서명 PDF을 로드하는 동안 표시할 메시지를 지정합니다. Acrobat Sign 서비스는 서명 PDF을 준비하고 로드하는 데 시간이 오래 걸립니다.
   * **서명 서비스:** 을(를) 선택합니다 **스크리블 서명** 선택 사항입니다.
   * **CSS 클래스**: 클라이언트 라이브러리의 CSS 클래스(있는 경우)를 지정합니다. 을 사용하는 것이 좋습니다 [테마](/help/forms/using/themes.md) 및 [인라인 스타일](/help/forms/using/inline-style-adaptive-forms.md) CSS 클래스 대신 사용할 수 있습니다.

   완료 를 누릅니다 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) 아이콘을 클릭하여 변경 사항을 저장합니다. 서명이 성공적으로 구성되었습니다.

   이제 양식을 채울 때 적응형 양식의 PDF 버전이 표시되고 PDF 문서에 서명할 옵션이 제공됩니다. 자세한 내용은 [스크리블 서명을 사용하여 적응형 양식에 서명](/help/forms/using/signing-forms-using-scribble.md#p-sign-an-adaptive-form-using-scribble-signature-p).

## 스크리블 서명을 사용하여 적응형 양식에 서명 {#sign-an-adaptive-form-using-scribble-signature}

1. 적응형 양식을 작성하고 서명 단계 페이지에 도달하면 서명 화면이 표시됩니다.

   ![EchoSign 페이지의 서명 화면](assets/esignscribblesign.jpg)

1. 클릭 **[!UICONTROL Sign]**. 스크리블 기호 대화 상자가 나타납니다. 양식에 서명하고 완료를 클릭합니다. ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) 아이콘을 클릭하여 서명을 저장합니다.

   ![스크리블 기호 대화 상자](assets/scribblewidget.jpg)

1. 완료 를 클릭하여 서명 프로세스를 완료합니다.

   ![서명 프로세스 완료](assets/scribblecomplete.jpg)

서명은 양식에 추가되고 양식 컨트롤이 다음 패널로 이동합니다.
