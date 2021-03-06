---
title: 디자이너에서 페이지 제로 콘텐츠 변경
seo-title: 디자이너에서 페이지 제로 콘텐츠 변경
description: Adobe PDF이 아닌 뷰어에서 XFA PDF를 볼 때 XFA PDF의 페이지 0에 표시되는 메시지를 어떻게 변경할 수 있는지 알고 있습니까?
seo-description: Adobe PDF이 아닌 뷰어에서 XFA PDF를 볼 때 XFA PDF의 페이지 0에 표시되는 메시지를 어떻게 변경할 수 있는지 알고 있습니까?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: 적응형 양식
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%

---

# 디자이너의 페이지 제로 콘텐츠 변경 {#changing-page-zero-content-in-designer}

Chrome 또는 Firefox의 기본 PDF 뷰어와 같이 Adobe PDF이 아닌 뷰어가 PDF/XFA 양식의 컨텐츠를 읽을 수 없을 때 기본적으로 페이지 제로(Page Zero) 컨텐츠가 표시됩니다. 기본 페이지 제로 메시지는 아래에 표시되어 있습니다.

![defaultpage0message](assets/defaultpage0message.png)

AEM Forms 기능 팩 1 버전의 Designer를 사용하면 페이지 0에 표시되는 메시지를 변경할 수 있습니다. 페이지 제로 메시지를 변경하려면 다음 단계를 수행하십시오.

1. AEM Forms 기능 팩 1 버전의 Designer가 설치되어 있는지 확인합니다. 디자이너의 정보 화면에서 버전을 확인할 수 있습니다.

1. 페이지 제로 컨텐츠를 변경할 양식을 엽니다.

1. **파일 > 양식 속성**&#x200B;을 클릭합니다.

1. 양식 속성 대화 상자에서 ![plus](assets/plus.png) (더하기 아이콘)를 클릭하여 사용자 지정 속성을 추가합니다.

1. **_pagezerocontent** 를 속성의 이름으로 지정합니다.
1. 새 페이지 제로 메시지를 리치 텍스트 형식으로 값으로 추가합니다. 예:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. 양식을 PDF로 저장합니다.

1. 브라우저에서 PDF 양식을 보고 메시지가 업데이트되었는지 확인합니다. 위의 예제 값은 다음과 같이 나타납니다.

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>양식을 다시 열면 방금 만든 사용자 지정 속성이 양식 속성 대화 상자에 제대로 표시되지 않을 수 있습니다. 하지만 제대로 작동하며 업데이트된 페이지 제로 메시지가 양식에 표시됩니다.
