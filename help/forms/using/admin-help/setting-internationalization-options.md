---
title: 국제화 옵션 설정
seo-title: Setting internationalization options
description: 양식을 렌더링하는 데 사용되는 로케일을 지정하는 방법과 출력 스트림을 인코딩하는 데 사용되는 문자 집합을 지정하는 방법을 알아봅니다.
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 4%

---

# 국제화 옵션 설정{#setting-internationalization-options}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 양식을 렌더링하는 데 사용되는 로케일을 지정합니다 {#specify-the-locale-used-to-render-forms}

PDF 양식을 렌더링할 때 사용되는 로케일을 지정할 수 있습니다. PDF 양식의 필드는 지정된 로케일을 사용하여 데이터를 표시합니다. 예를 들어 로케일이 독일어로 설정된 경우 양식에서 숫자 값에 독일어 소수점 구분 기호를 사용합니다. 로케일은 HTML 변환의 일부로 웹 브라우저와 같은 클라이언트 장치에 유효성 검사 메시지를 전송하는 데에도 사용됩니다.

1. 관리 콘솔에서 서비스 > Forms 를 클릭합니다.
1. 국제화에서 언어 목록에서 양식을 렌더링하는 데 사용되는 로케일을 선택합니다. 기본값은 영어(미국)입니다.
1. 저장을 클릭합니다.

## 출력 스트림을 인코딩하는 데 사용되는 문자 집합을 지정합니다 {#specify-the-character-set-used-to-encode-the-output-stream}

1. 국제화에서 문자 집합 목록에서 문자 집합을 선택합니다. 이 설정은 renderHTMLForm 또는 renderPDFForm에 사용되는 API에 따라 다릅니다. 나열된 문자 세트가 아닌 문자 집합을 지정하려면 [사용자 지정]을 선택하고 표시되는 상자에 인코딩 값을 지정합니다.

   HTML 변환을 위해 AEM Forms에서는 `java.nio.charset` 패키지. sFormPreference가 PDFForm이면 특정 문자 집합만 지원됩니다. 문자 집합은 유효한 정식 이름이어야 합니다. 기본값은 ISO-8859-1입니다.

1. 저장을 클릭합니다.
