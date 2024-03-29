---
title: AEM Sites 페이지에 적응형 양식 또는 대화형 커뮤니케이션 포함
seo-title: Embed an adaptive form or interactive communication in AEM sites page
description: AEM Sites 페이지에 적응형 양식을 포함할 수 있습니다. 사용자는 사이트 페이지를 종료하지 않고 양식을 작성하고 제출할 수 있습니다.
seo-description: You can embed adaptive forms in AEM sites pages. Users can fill and submit forms without leaving the site pages.
uuid: 59b49e2f-6d95-42e5-b31e-fc40936c42d2
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications, author
discoiquuid: 43362643-69cd-4006-a613-f998c79eeddc
feature: Adaptive Forms
exl-id: ba5d21a4-231c-4e1e-b172-4d700cb9696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 1%

---

# AEM Sites 페이지에 적응형 양식 또는 대화형 커뮤니케이션 포함 {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

AEM Forms을 통해 양식 개발자는 AEM Sites 페이지 또는 AEM 외부에서 호스팅되는 웹 페이지에 적응형 양식 및 대화형 커뮤니케이션을 원활하게 포함할 수 있습니다. 포함된 적응형 양식 및 대화형 커뮤니케이션은 완전히 기능하며 사용자는 페이지를 종료하지 않고 양식을 작성하고 제출할 수 있습니다. 따라서 사용자는 웹 페이지에서 다른 요소의 컨텍스트에 남아 있고 양식 또는 대화형 커뮤니케이션과 동시에 상호 작용할 수 있습니다.

외부 웹 페이지에 적응형 양식 포함에 대한 자세한 내용은 [외부 웹 페이지에 적응형 양식 포함](/help/forms/using/embed-adaptive-form-external-web-page.md).

AEM Sites 페이지에서 다음을 사용하여 적응형 양식 또는 대화형 커뮤니케이션을 추가할 수 있습니다.

* **[AEM Forms 컨테이너 구성 요소](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms은 사이트 페이지에 추가할 수 있는 구성 요소를 제공합니다. AEM Forms 컨테이너 구성 요소를 사용하여 적응형 양식 및 대화형 커뮤니케이션을 포함할 수 있습니다.

* **[자산 브라우저](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
사용자가 만드는 모든 양식 및 대화형 커뮤니케이션은 자산 아래에 있습니다. 양식을 페이지에서 자산으로 드래그하여 놓을 수 있습니다.

## 사전 요구 사항 {#prerequisites}

편집 가능한 템플릿을 사용하는 AEM Sites 페이지에 적응형 양식 또는 대화형 커뮤니케이션을 포함하려면 AEM Form 구성 요소가 관련 템플릿에서 허용된 구성 요소로 구성되어 있는지 확인하십시오. 자세한 내용은 **정책 및 속성(레이아웃 컨테이너)** 섹션 [페이지 템플릿 만들기](/help/sites-authoring/templates.md).

정적 템플릿을 사용하는 사이트 페이지의 경우 사이트 페이지의 단락 시스템에서 구성해야 합니다. 자세한 내용은 [디자인 모드에서 구성 요소 구성](/help/sites-authoring/default-components-designmode.md)을 참조하십시오.

## 적응형 양식 또는 대화형 커뮤니케이션 포함 {#af-component}

AEM Forms 컨테이너 구성 요소를 사용하여 적응형 양식 또는 대화형 커뮤니케이션을 포함하려면 다음을 수행하십시오.

1. 적응형 양식 또는 대화형 커뮤니케이션을 포함할 편집 모드에서 AEM Sites 페이지를 엽니다.
1. 구성 요소 브라우저 패널에서 AEM Forms 컨테이너 구성 요소를 페이지에 드래그하여 놓습니다.

   또는 자산 브라우저에서 적응형 양식 또는 대화형 커뮤니케이션을 검색하고 사이트 페이지에 드래그하여 놓을 수 있습니다. AEM Forms 컨테이너에 양식을 포함합니다.

   >[!NOTE]
   >
   >한 페이지의 여러 AEM Forms 컨테이너 구성 요소는 지원되지 않습니다.

1. 사이트 페이지에서 포함된 AEM Forms 컨테이너 구성 요소를 탭한 다음 탭합니다 ![settings_icon](assets/settings_icon.png) 를 클릭합니다. 다음 **[!UICONTROL AEM Forms 컨테이너 편집]** 대화 상자가 열립니다.
1. AEM Forms 컨테이너 편집 대화 상자에서 다음을 지정합니다.

   * **자산 유형:** 포함할 자산 유형을 선택합니다. 옵션은 적응형 양식 및 대화형 커뮤니케이션입니다
   * **자산 경로**: 포함할 적응형 양식 또는 대화형 커뮤니케이션을 찾아 선택합니다. 자산 브라우저에서 삭제한 경우 자동으로 채워집니다.
   * (적응형 양식만 해당) **게시 제출**: 양식 제출 시 트리거할 작업을 선택합니다. 감사 메시지를 표시하거나 감사 인사 페이지를 표시하도록 선택할 수 있습니다.

      * **감사 메시지**: 서식 있는 텍스트 편집기를 사용하여 메시지를 작성하여 양식 제출 시 표시할 수 있습니다. 이 옵션은 감사 메시지를 표시하도록 선택하는 경우에만 사용할 수 있습니다.
      * **감사 인사 페이지**: 양식 제출 시 표시할 페이지를 찾아 선택합니다. 이 옵션은 감사 인사 페이지를 표시하도록 선택하는 경우에만 사용할 수 있습니다.
      * **제출 시 페이지 새로 고침**: 포함된 적응형 양식이 포함된 페이지를 새로 고쳐 감사 인사 페이지를 표시할 수 있도록 합니다. 그렇지 않으면 감사 인사 페이지에서 페이지를 새로 고치지 않고 AEM Forms 컨테이너의 적응형 양식을 대체합니다. 이 옵션은 감사 인사 페이지를 표시하도록 선택하는 경우에만 사용할 수 있습니다.
   * **테마**: 적응형 양식 또는 대화형 커뮤니케이션의 구성 요소에 대한 스타일을 정의하는 테마를 선택합니다. 스타일링에는 글꼴 스타일, 배경색, 치수 및 정렬과 같은 모양 속성이 포함됩니다.
   * **높이**: 컨테이너의 높이를 지정합니다. 컨테이너의 크기를 자동으로 조정하려면 이 필드를 비워 둡니다.
   * **CSS 클라이언트 라이브러리**: CSS 클라이언트 라이브러리의 경로를 지정합니다.


1. 설정을 저장합니다. 적응형 양식 또는 대화형 커뮤니케이션이 이제 페이지에 포함됩니다.

## 포함된 적응형 양식 및 대화형 커뮤니케이션 게시 {#publishing-embedded-adaptive-form-and-interactive-communication}

AEM Sites 페이지에 포함된 자산(적응형 양식 또는 대화형 통신)을 게시하기 위한 다음 시나리오를 생각해 보겠습니다.

* AEM Sites 페이지를 처음으로 게시하고 포함된 적응형 양식 또는 대화형 커뮤니케이션이 포함된 경우 사이트 페이지와 포함된 자산을 게시합니다.
* 게시된 사이트 페이지에서 포함된 적응형 양식 또는 대화형 통신만 수정한 경우 원래 자산을 게시하고 변경 사항이 게시된 사이트 페이지에 반영됩니다. 게시된 사이트 페이지에는 자산에 대한 참조가 포함되어 있으며 페이지를 다시 게시할 필요가 없습니다.
* 사이트 페이지 및 포함된 적응형 양식 또는 대화형 커뮤니케이션을 수정한 경우 사이트 페이지 및 포함된 자산을 다시 게시합니다.

## 포함된 적응형 양식 및 대화형 통신 수정 {#modifying-embedded-adaptive-form-and-interactive-communication}

AEM 사이트 페이지는 AEM Forms 컨테이너에서 적응형 양식 및 대화형 커뮤니케이션에 대한 참조를 유지 관리합니다. 따라서 원본 적응형 양식 및 대화형 커뮤니케이션에 구성된 테마, 스타일 및 제출 작업과 같은 모든 구성 및 속성은 포함된 적응형 양식 및 대화형 커뮤니케이션에 유지됩니다.

포함된 적응형 양식 및 대화형 커뮤니케이션의 구성이나 속성을 수정하려면 다음 중 하나를 수행합니다.

* 각 편집기에서 적응형 양식 또는 대화형 커뮤니케이션으로 원본 양식을 열고 수정합니다.
* 편집 모드에서 사이트 페이지 내에서 적응형 양식 또는 대화형 커뮤니케이션을 탭한 다음 탭합니다 **[!UICONTROL 새 창에서 편집]**. 원본 양식은 수정할 수 있는 편집 모드로 열립니다.

>[!NOTE]
>
>원본 적응형 양식 또는 대화형 커뮤니케이션에서 변경한 내용은 포함된 양식에 자동으로 반영됩니다. 하지만 게시된 페이지의 변경 사항을 반영하도록 적응형 양식, 대화형 통신 또는 사이트 페이지를 다시 게시합니다.

## 고려 사항 및 우수 사례 {#considerations-and-best-practices}

AEM Sites 페이지에 적응형 양식을 포함할 때에는 다음 사항을 염두에 두십시오.

* 원본 양식의 머리글 및 바닥글은 포함된 양식에 포함되지 않습니다.
* 포함된 양식의 사용자 초안 및 제출은 Forms 포털의 초안 및 제출된 Forms 탭에서 지원되고 표시됩니다.
* 원본 양식에 구성된 제출 작업은 포함된 양식으로 유지됩니다.
* 원래 양식에 구성된 경험 타깃팅 및 A/B 테스트가 포함된 양식에서 작동하지 않습니다. 하지만 사이트 페이지에서 경험 타깃팅을 사용하여 사용자 프로필에 따라 다른 양식을 제공할 수 있습니다.
* Adobe Analytics이 원래 양식에 대해 구성된 경우 포함된 양식의 분석 데이터가 Adobe Analytics에 캡처됩니다. 하지만 Forms Analytics 보고서에서는 사용할 수 없습니다.
