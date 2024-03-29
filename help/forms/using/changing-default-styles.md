---
title: HTML5 양식의 기본 스타일 변경
seo-title: Changing default styles of HTML5 forms
description: HTML5 양식 스타일은 CSS를 기반으로 합니다. 양식의 기본 스타일을 변경할 수 있습니다.
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Mobile Forms
exl-id: 74e54d96-e418-40aa-9b93-561fbdd6312d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 3%

---

# HTML5 양식의 기본 스타일 변경 {#changing-default-styles-of-html-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

HTML5 양식은 HTML5 기능을 사용하여 렌더링되고 렌더링된 양식의 스타일은 CSS를 사용하여 수행됩니다. HTML5 양식의 기본 모양은 PDF 표현물과 유사합니다. 개발자는 사용자 지정 CSS를 사용하여 HTML 5 양식의 기본 모양을 변경할 수 있습니다.

이 문서에서는 HTML5 양식의 스타일을 변경하는 단계별 정보를 제공하며 [스타일 소개](/help/forms/using/css-styles.md) 이 문서에는 HTML5 양식의 다양한 스타일 측면에 대한 자세한 정보가 포함되어 있습니다. 이 문서에서 언급된 단계를 수행하기 전에 스타일 소개 문서를 읽어야 합니다.

다음 두 이미지는 기본 스타일과 사용자 지정된 스타일 간의 차이를 보여줍니다.

![사진-002-소형](assets/pictures-002-small.png)

## 양식 스타일 지정 {#style-your-forms}

1. **사용자 지정 스타일을 추가할 프로필 선택**

   URL에서 CRX DE 인터페이스에 액세스합니다. **https://&lt;server>:&lt;port>/crx/de** 프로필을 만들거나 기존 프로필을 선택합니다. 프로필을 만드는 방법을 알아보려면 [새 프로필 만들기](/help/forms/using/custom-profile.md)

1. **HTML5 양식의 스타일을 지정할 CSS 스타일 시트 만들기**

   프로필 렌더러를 만든 폴더로 이동하고 CSS 스타일 시트 파일을 만듭니다. 다음 단계를 수행합니다

   1. 폴더를 마우스 오른쪽 단추로 클릭하고 를 선택합니다. **만들기** -> **파일 만들기** 메뉴에서
   HTML5 양식에서 특정 구성 요소에 대해 만들 CSS 클래스를 확인하려면 [스타일 소개](/help/forms/using/css-styles.md).

1. **프로필 렌더러에 스타일 시트 포함**

   CRX DE에서 프로필 렌더러 페이지(jsp 파일)를 열고 XFA 클라이언트 라이브러리 바로 아래에 있는 페이지에 CSS 파일을 포함합니다. 프로필에 CSS 파일을 포함하려면 다음 단계를 수행합니다.

   1. 렌더러 페이지에서 다음 줄을 검색합니다.

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. 스타일 시트를 포함하려면 위의 줄 아래에 다음 내용을 삽입합니다.

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. 파일을 저장합니다.
