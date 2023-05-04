---
title: 문자 세트 변경
seo-title: Change the character set
description: 출력 스트림을 인코딩하는 데 사용되는 문자 세트를 지정할 수 있습니다. 문자 집합을 변경하는 방법을 알아봅니다.
seo-description: You can specify the character set used to encode the output stream. Learn how you can change the character set.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
exl-id: 7961efc6-4b11-423a-871d-7b37e3f36781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 6%

---

# 문자 세트 변경 {#change-the-character-set}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

출력 스트림을 인코딩하는 데 사용되는 문자 세트를 지정할 수 있습니다.

1. 관리 콘솔에서 **[!UICONTROL 서비스 > 출력]**.
1. 국제화에서 문자 집합 목록에서 문자 집합을 선택합니다. 이 설정은 `TransformationFormat` 및 `PrintFormat` API를 통해 지정됩니다. 나열된 문자 세트가 아닌 문자 집합을 지정하려면 [사용자 지정]을 선택하고 표시되는 상자에 인코딩 값을 지정합니다.

   If `TransformationFormat` 은 PDF 및 PDF/A 또는 입니다. `PrintFormat` 는 PCL, PostScript, Zebra 레이블, IPL, DPL, TPCL, GenericColorPCL 또는 GenericPSLevel3인 경우 특정 문자 집합만 지원됩니다.

   문자 집합은 유효한 정식 이름이어야 합니다. 기본값은 ISO-8859-1입니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
