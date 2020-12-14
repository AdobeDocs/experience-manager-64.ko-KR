---
title: 경험 조각과 Target 통합
seo-title: 경험 조각과 Target 통합
description: 경험 조각과 Target 통합
seo-description: 경험 조각과 Target 통합
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# 경험 조각과의 Target 통합{#target-integration-with-experience-fragments}

>[!NOTE]
>
>이 기능을 사용하려면 [AEM 6.4 서비스 팩 2(6.4.2.0)](/help/release-notes/sp-release-notes.md) 이상을 사용해야 합니다.

Adobe Experience Manager(AEM)에서 만든 [경험 조각](/help/sites-authoring/experience-fragments.md)을 Adobe Target으로 내보낼 수 있습니다. 그런 다음 Target 활동에서 오퍼로 사용하여 경험을 규모에 맞게 테스트하고 개인화할 수 있습니다. AEM의 사용 편의성과 강력한 기능을 Target의 강력한 AI(Automated Intelligence) 및 ML(Machine Learning) 기능과 결합할 수 있습니다.

## 전제 조건 {#prerequisites}

다양한 작업이 필요합니다.

1. AEM과 Target을 통합해야 합니다. 자세한 내용은 [Adobe Target](/help/sites-administering/target.md)과 통합을 참조하십시오.
1. 경험 조각은 작성 인스턴스에서 내보내기되므로 작성 인스턴스에서 [링크 외부라이저](/help/sites-developing/externalizer.md)를 구성하여 게시 인스턴스에 대한 링크가 외부화되도록 해야 합니다.

## 클라우드 구성 {#add-the-cloud-configuration} 추가

조각을 내보내기 전에 **Adobe Target**&#x200B;에 대한 **클라우드 구성**&#x200B;을 조각 또는 폴더에 추가해야 합니다.

1. **경험 조각** 콘솔로 이동합니다.
1. 해당 폴더 또는 조각에 대해 **페이지 속성**&#x200B;을 엽니다.

   >[!NOTE]
   >
   >클라우드 구성을 경험 조각 상위 폴더에 추가하는 경우 모든 하위 폴더에 의해 구성이 상속됩니다.
   >
   >클라우드 구성을 경험 조각 자체에 추가하는 경우, 구성은 모든 변수에서 상속됩니다.

1. **Cloud Services** 탭을 선택합니다.

1. **Cloud Service 구성**&#x200B;의 드롭다운 목록에서 **Adobe Target**&#x200B;을 선택합니다.
1. **Adobe Target**&#x200B;에서 적절한 구성을 선택합니다.

1. **저장 및 닫기**.

## 경험 조각을 Target {#exporting-an-experience-fragment-to-target}으로 내보내기

>[!NOTE]
>
>이미지와 같은 미디어 에셋의 경우 참조만 Target으로 내보내집니다. 자산 자체는 AEM Assets에 저장되어 AEM 게시 인스턴스에서 전달됩니다.
>
>이 때문에 Target으로 내보내기 전에 모든 관련 자산이 있는 경험 조각을 게시해야 합니다.

경험 조각을 AEM에서 Target으로 내보내려면(클라우드 구성을 지정한 후):

1. 경험 조각 콘솔로 이동합니다.
1. 타겟으로 내보낼 경험 조각을 선택합니다.

   >[!NOTE]
   >
   >경험 조각 웹 변형이어야 합니다.

1. **Adobe Target**&#x200B;로 내보내기를 탭/클릭합니다.

   >[!NOTE]
   >
   >경험 조각을 이미 내보낸 경우 Adobe Target **에서**&#x200B;업데이트를 선택합니다.

1. 필요에 따라 **또는**&#x200B;게시&#x200B;**를 게시하지 않고**&#x200B;내보내기를 탭/클릭합니다.

   >[!NOTE]
   >
   >게시**를 선택하면 즉시 경험 조각을 게시하고 Target에 보냅니다.

1. 확인 대화 상자에서 **확인**&#x200B;을 탭/클릭합니다.

   이제 경험 조각이 Target 내에 있어야 합니다.

>[!NOTE]
>
>또는 [페이지 정보](/help/sites-authoring/author-environment-tools.md#page-information) 메뉴의 비교 명령을 사용하여 페이지 편집기에서 내보내기를 수행할 수 있습니다.

## Target {#using-your-experience-fragments-in-target}에서 경험 조각 사용

이전 작업을 수행한 후 경험 조각은 Target의 오퍼 페이지에 표시됩니다. 여기에서 얻을 수 있는 사항에 대해 알아보려면 [특정 Target 설명서](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html)를 살펴보십시오.

## 경험 조각을 삭제하여 Target {#deleting-an-experience-fragment-already-exported-to-target}에 이미 내보내었습니다.

이미 Target으로 내보낸 경험 조각을 삭제하면 해당 단편이 Target의 오퍼에서 이미 사용되고 있는 경우 문제가 발생할 수 있습니다. 조각을 삭제하면 조각 컨텐츠가 AEM에 의해 배달되므로 오퍼를 사용할 수 없게 됩니다.

이러한 상황을 피하려면

* 경험 단편이 현재 활동에 사용되지 않는 경우 AEM에서는 경고 메시지 없이 단편을 삭제할 수 있습니다.
* Target의 활동에서 경험 조각을 현재 사용 중인 경우, 조각을 삭제하면 활동에 발생할 수 있는 결과에 대해 AEM 사용자에게 오류 메시지가 표시됩니다.

   AEM의 오류 메시지로 인해 사용자가 경험 조각을 삭제할 수 없습니다(강제-). 경험 조각이 삭제된 경우:

   * AEM 경험 조각의 Target 오퍼에 원하지 않는 동작이 표시될 수 있습니다.

      * 경험 조각 HTML이 Target으로 푸시되었기 때문에 오퍼는 여전히 렌더링됩니다
      * 참조된 자산이 AEM에서도 삭제된 경우 경험 조각의 모든 참조가 제대로 작동하지 않을 수 있습니다.
   * 물론 경험 조각은 AEM에 더 이상 존재하지 않으므로 경험 조각에 대한 추가 수정은 불가능합니다.


