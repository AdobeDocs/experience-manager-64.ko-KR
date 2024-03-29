---
title: 양식 출력 구성
seo-title: Configuring form output
description: 양식 출력을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure form output.
uuid: 70aad14e-c845-4ef3-a751-ad8860d5d505
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 17c9b69a-3c6f-47e3-a828-841bb90eba8b
exl-id: b19cae88-a549-41ba-b4a6-4b065a995296
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 4%

---

# 양식 출력 구성{#configuring-form-output}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 웹 브라우저에 반환된 HTML 출력 유형을 지정합니다 {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. 관리 콘솔에서 서비스 > 양식을 클릭합니다.
1. 양식 출력의 출력 유형 목록에서 다음 옵션 중 하나를 선택합니다.

   **전체 HTML:** 전체 HTML 태그 내에 양식을 렌더링하려면(전체 HTML 페이지). 이 값이 기본값입니다.

   **양식 본문:** 내에서 양식을 렌더링하려면 `<BODY>` 태그 (전체 HTML 페이지가 아님).

1. 저장을 클릭합니다.

## PDF 컨텐츠가 렌더링되는 위치를 지정합니다 {#specify-the-location-where-pdf-content-is-rendered}

1. [양식 출력]의 [렌더링 위치] 목록에서 다음 옵션 중 하나를 선택합니다.

   **클라이언트:** Adobe Acrobat 또는 Adobe Reader 내에서 PDF forms을 렌더링하려면 클라이언트측 렌더링은 AEM Forms의 성능을 향상시키고 PDFForm 변환에만 적용됩니다.

   **서버:** 응용 프로그램 서버에서 PDF forms을 렌더링하려면 다음을 수행하십시오.

   **자동:** PDF 양식을 `dynamicRender` xdp 파일의 구성 값입니다. 이 값이 기본값입니다.

1. 저장을 클릭합니다.

## 양식 제출 전에 사용자 지정 스크립트 호출 구성 {#configuring-invocation-of-custom-scripts-before-form-submit}

다음 단계를 수행하여 기능을 활성화합니다.

1. 관리 콘솔에 로그인합니다.
1. 이동 **서비스** > **forms**.
1. 출력 유형을 양식 본문으로 지정합니다.
1. 설정을 저장합니다.
1. HTML 코드의 head 섹션에서 JavaScript 변수 __CUSTOM_SCRIPTS_VERSION을 선언하고 해당 값을 1로 설정합니다.

   >[!NOTE]
   >
   >*이 기능을 비활성화하려면 JavaScript 변수를 제거하거나 값을 0으로 설정할 수 있습니다.*
