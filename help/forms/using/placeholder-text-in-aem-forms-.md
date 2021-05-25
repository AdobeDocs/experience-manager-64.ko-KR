---
title: 'AEM Forms의 자리 표시자 텍스트 '
seo-title: 'AEM Forms의 자리 표시자 텍스트 '
description: 자리 표시자 텍스트는 컨트롤에 값이 없을 때 사용자에게 데이터 항목을 제공하기 위한 것입니다. 샘플 값이거나 예상 형식에 대한 간단한 설명일 수 있습니다.
seo-description: 자리 표시자 텍스트는 컨트롤에 값이 없을 때 사용자에게 데이터 항목을 제공하기 위한 것입니다. 샘플 값이거나 예상 형식에 대한 간단한 설명일 수 있습니다.
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: 적응형 양식
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 1%

---

# AEM Forms {#placeholder-text-in-aem-forms}의 자리 표시자 텍스트

자리 표시자 텍스트는 단어 또는 짧은 구를 나타냅니다. 컨트롤에 값이 없을 때 사용자에게 데이터 항목을 지원하기 위한 것입니다. 자리 표시자 텍스트는 샘플 값이거나 예상 형식에 대한 간단한 설명일 수 있습니다. 사용자가 값을 입력하기 전에 자리 표시자 텍스트가 표시되며, 사용자가 값을 입력하거나 선택하면 제거됩니다.

>[!NOTE]
>
>지정되는 경우 자리 표시자 텍스트에는 새 줄 문자가 포함되지 않은 값이 있어야 합니다.

![자리 표시자 텍스트가 있는 날짜 구성 요소 및 없는 날짜](assets/dat-picker-place-holder-text.png)

**자리 표시자 텍스트** B. **** 자리 표시자 텍스트가 없는 날짜 구성 요소

AEM Forms에서는 암호 상자, 날짜 선택기, 숫자 상자 및 텍스트 상자 필드에 대한 자리 표시자 텍스트를 지원합니다.\
자리 표시자 텍스트는 기본 HTML5 날짜 위젯에 대해 지원되지 않습니다. 자리 표시자 텍스트를 지정하려면

1. 자리 표시자 텍스트를 지원하는 구성 요소를 마우스 오른쪽 단추로 클릭하고 **편집**&#x200B;을 클릭합니다. 구성 요소 편집 대화 상자가 나타납니다.

1. **제목 및 텍스트** 탭을 엽니다.
1. **자리 표시자 텍스트 상자**&#x200B;에 단어나 짧은 구를 지정합니다. **확인**&#x200B;을 클릭합니다.

>[!NOTE]
>
>자리 표시자 텍스트는 Microsoft Internet Explorer 9에서 지원되지 않습니다.
