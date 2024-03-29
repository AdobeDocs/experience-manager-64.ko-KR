---
title: 컨텐츠 조각 모델
seo-title: Content Fragment Models
description: 컨텐츠 조각 모델은 구조화된 컨텐츠와 함께 컨텐츠 조각을 생성하는 데 사용됩니다.
seo-description: Content Fragment Models are used to create content fragments with structured content.
uuid: 59176a32-1255-4a46-ad00-344bde843ea6
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 45e67357-4524-4d25-b5f1-21182b8e803c
exl-id: 39ed07ec-54a6-4387-8435-e891726c411c
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 87%

---

# 콘텐츠 조각 모델 {#content-fragment-models}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>일부 컨텐츠 조각 기능을 사용하려면 [AEM 6.4 서비스 팩 2(6.4.2.0) 이상](../release-notes/sp-release-notes.md).

컨텐츠 조각 모델은 [컨텐츠 조각](content-fragments.md)에 대한 컨텐츠 구조를 정의합니다.

## 컨텐츠 조각 모델 활성화 {#enable-content-fragment-models}

>[!CAUTION]
>
>활성화하지 않은 경우 **[!UICONTROL 컨텐츠 조각 모델]**, **[!UICONTROL 만들기]** 새 모델을 만드는 데에는 옵션을 사용할 수 없습니다.

컨텐츠 조각 모델을 활성화하려면 필요한 단계가 있습니다.

* 구성 관리자에서 컨텐츠 조각 모델을 사용할 수 있도록 설정
* 자산 폴더에 구성 적용

### 구성 관리자에서 컨텐츠 조각 모델을 사용할 수 있도록 설정 {#enable-content-fragment-models-in-configuration-manager}

[새 컨텐츠 조각 모델을 생성](#creating-a-content-fragment-model)하려면 먼저 구성 관리자를 사용하여 컨텐츠 조각 모델을 활성화&#x200B;**해야 합니다**.

1. **[!UICONTROL 도구]**, **[!UICONTROL 일반]**&#x200B;으로 이동한 후 **[!UICONTROL Configuration Browser]**&#x200B;를 엽니다.
   * 자세한 내용은 [구성 브라우저 설명서](/help/sites-administering/configurations.md) 추가 정보.
1. 웹 사이트에 적합한 위치를 선택합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 사용하여 대화 상자를 열고 여기에서

   1. **[!UICONTROL 제목]**&#x200B;을 지정합니다.
   1. **[!UICONTROL 컨텐츠 조각 모델]**&#x200B;을 선택하여 사용할 수 있도록 설정합니다.

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 정의를 저장합니다.

### 에셋 폴더에 구성 적용 {#apply-the-configuration-to-your-assets-folder}

컨텐츠 조각 모델에 대해 구성 **[!UICONTROL 전역]** 이 활성화되면 사용자가 만드는 모든 모델을 자산 폴더에서 사용할 수 있습니다.

비교 가능한 자산 폴더와 함께 다른 구성(즉, 전역 제외)을 사용하려면 연결을 정의해야 합니다. 이 작업은 적절한 폴더의 **[!UICONTROL 폴더 속성]**&#x200B;에서 **[!UICONTROL 클라우드 서비스]** 탭에 있는 **[!UICONTROL 구성]**&#x200B;을 사용하여 수행됩니다.

## 콘텐츠 조각 모델 만들기 {#creating-a-content-fragment-model}

1. **[!UICONTROL 도구]**, **[!UICONTROL 자산]**&#x200B;으로 이동한 후 **[!UICONTROL 컨텐츠 조각 모델]**&#x200B;을 엽니다.
1. [구성](#enable-content-fragment-models)에 적절한 폴더로 이동합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 사용하여 마법사를 엽니다.

   >[!CAUTION]
   >
   >[콘텐츠 조각 모델 사용이 활성화되지 않은](#enable-content-fragment-models) 경우 **만들기** 옵션을 사용할 수 없습니다.

1. **[!UICONTROL 모델 제목]**&#x200B;을 지정합니다. 필요한 경우 **[!UICONTROL 설명]**&#x200B;을 추가할 수도 있습니다.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. **[!UICONTROL 만들기]**&#x200B;를 사용하여 빈 모델을 저장합니다. 작업의 성공을 나타내는 메시지가 표시되면 **[!UICONTROL 열기]**&#x200B;를 선택하여 모델을 즉시 편집하거나 **[!UICONTROL 완료]**&#x200B;를 선택하여 콘솔로 돌아갈 수 있습니다.

## 콘텐츠 조각 모델 정의 {#defining-your-content-fragment-model}

컨텐츠 조각 모델은 결과 컨텐츠 조각의 구조를 효과적으로 정의합니다. 모델 편집기를 사용하여 필수 필드를 추가하고 구성할 수 있습니다.

>[!CAUTION]
>
>기존 컨텐츠 조각 모델을 편집하면 종속된 조각이 영향을 받을 수 있습니다.

1. **[!UICONTROL 도구]**, **[!UICONTROL 자산]**&#x200B;으로 이동한 후 **[!UICONTROL 컨텐츠 조각 모델]**&#x200B;을 엽니다.

1. 컨텐츠 조각 모델을 포함하는 폴더로 이동합니다.
1. **[!UICONTROL 편집]**&#x200B;에 필요한 모델을 엽니다. 빠른 작업을 사용하거나, 모델을 선택한 후 도구 모음에서 작업을 선택하십시오.

   모델 편집기를 열면 다음과 같이 표시됩니다.

   * 왼쪽: 이미 정의된 필드
   * 오른쪽: 필드를 만드는 데 사용할 수 있는 **[!UICONTROL 데이터 유형]**(필드가 만들어지면 사용할 **[!UICONTROL 속성]**)

   >[!NOTE]
   >
   >필드가 **필수 여부**, **레이블** 왼쪽 창에 표시된 항목은 별표(**&amp;ast;**).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **필드를 추가하려면**

   * 필수 데이터 유형을 필드에 필요한 위치로 드래그합니다.

   ![cfm-6420-11](assets/cfm-6420-11.png)

   * 모델에 필드가 추가되면 오른쪽 패널에 그 특정 데이터 유형에 대해 정의할 수 있는 **속성**&#x200B;이 표시됩니다. 여기에서 해당 필드에 필요한 사항을 정의할 수 있습니다. 예:

   ![cfm-6420-13](assets/cfm-6420-13.png)

1. **필드를 제거하려면**

   필요한 필드를 선택한 후 휴지통 아이콘을 클릭/탭합니다. 작업을 확인하는 메시지가 나타납니다.

   ![cf-32](assets/cf-32.png)

1. 모든 필수 필드를 추가하고 속성을 정의한 후 **[!UICONTROL 저장]**&#x200B;을 사용하여 정의를 유지합니다. 예:

   ![cfm-6420-14](assets/cfm-6420-14.png)

## 콘텐츠 조각 모델 삭제 {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>콘텐츠 조각 모델을 삭제하면 종속된 조각이 영향을 받을 수 있습니다.

컨텐츠 조각 모델을 삭제하려면

1. **[!UICONTROL 도구]**, **[!UICONTROL 자산]**&#x200B;으로 이동한 후 **[!UICONTROL 컨텐츠 조각 모델]**&#x200B;을 엽니다.

1. 컨텐츠 조각 모델을 포함하는 폴더로 이동합니다.
1. 모델을 선택한 후 도구 모음에서 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >참조되는 모델의 경우 경고가 표시됩니다. 적절하게 조치하십시오.

## 콘텐츠 조각 모델 게시 {#publishing-a-content-fragment-model}

콘텐츠 조각 모델은 종속된 콘텐츠 조각이 게시될 때/게시되기 전에 게시해야 합니다.

컨텐츠 조각 모델을 게시하려면

1. **[!UICONTROL 도구]**, **[!UICONTROL 자산]**&#x200B;으로 이동한 후 **[!UICONTROL 컨텐츠 조각 모델]**&#x200B;을 엽니다.

1. 컨텐츠 조각 모델을 포함하는 폴더로 이동합니다.
1. 모델을 선택한 후 도구 모음에서 **[!UICONTROL 게시]**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >모델이 아직 게시되지 않은 컨텐츠 조각을 게시하는 경우 선택 목록에 이것이 표시되고 모델이 조각과 함께 게시됩니다.
