---
title: PDF 문서에서 유효하고 만료된 인증서 인식
seo-title: Recognizing valid and expired certificates in PDF documents
description: PDF 문서에서 유효하고 만료된 인증서를 인식하는 방법을 알아봅니다.
seo-description: Learn how to recognize valid and expired certificates in PDF documents.
uuid: ceeff57a-586f-4f7b-852f-2a637f003d7e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4559218a-65ba-4577-ad26-7721e28971bc
exl-id: 6e2c109c-381f-455d-bd1d-b08c37c0bd67
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 3%

---

# PDF 문서에서 유효하고 만료된 인증서 인식 {#recognizing-valid-and-expired-certificates-in-pdf-documents}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Reader 확장에서 적용된 사용 권한이 있는 PDF 문서를 Adobe Reader에서 열면 PDF 문서에서 활성화된 특정 사용 권한을 설명하는 상태 표시줄이 나타납니다.

PDF 문서의 사용 권한을 지정하는 디지털 인증서가 만료되고 PDF 문서가 Adobe Reader에서 열리면 PDF 문서에 사용 권한이 있지만 이러한 권한은 비활성화되어 있음을 사용자에게 알려주는 대화 상자가 나타납니다. PDF 문서가 변경되었거나 훼손되었음을 알리는 메시지가 표시되지만 반드시 이 경우에는 아닙니다. Adobe Reader은 인증서가 만료되거나 문서가 수정되면 이 메시지를 표시합니다. Adobe Reader 7.0.x 이상에서는 현재 어느 사례가 문제인지 확인할 수 없습니다.

대화 상자를 닫으면 Adobe Reader에서 PDF 문서가 열립니다. Acrobat Reader DC 확장을 사용하여 적용된 사용 권한을 예상대로 사용할 수 없습니다. PDF 문서가 대화형 양식인 경우 양식 필드가 잠기고 사용자가 양식 데이터를 변경할 수 없습니다.
