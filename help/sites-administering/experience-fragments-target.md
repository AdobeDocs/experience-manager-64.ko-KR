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
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# 경험 조각과 Target 통합{#target-integration-with-experience-fragments}

>[!NOTE]
>
>이 기능을 사용하려면 [AEM 6.4 서비스 팩 2(6.4.2.0)](/help/release-notes/sp-release-notes.md) 이상을 적용해야 합니다.

Adobe Experience Manager(AEM)에서 만든 [경험 조각](/help/sites-authoring/experience-fragments.md)을 Adobe Target으로 내보낼 수 있습니다. 그런 다음 Target 활동에서 오퍼로 사용하여 경험을 규모에 맞게 테스트 및 개인화할 수 있습니다. 이를 통해 AEM의 편의성과 기능을 강력한 AI(Automated Intelligence) 및 기계 학습(ML) 기능을 Target에 결합할 수 있습니다.

## 전제 조건 {#prerequisites}

다양한 작업이 필요합니다.

1. AEM을 Target과 통합해야 합니다. 자세한 내용은 [Adobe Target과 통합](/help/sites-administering/target.md)을 참조하십시오.
1. 경험 조각은 작성자 인스턴스에서 내보내지므로, 게시 인스턴스에 대해 링크가 외부화되었는지 확인하려면 작성자 인스턴스에서 [링크 외부자](/help/sites-developing/externalizer.md)를 구성해야 합니다.

## 클라우드 구성 추가 {#add-the-cloud-configuration}

조각을 내보내기 전에 **Adobe Target**&#x200B;에 대한 **클라우드 구성**&#x200B;을 조각 또는 폴더에 추가해야 합니다.

1. **경험 조각** 콘솔로 이동합니다.
1. 해당 폴더 또는 조각에 대해 **페이지 속성**&#x200B;을 엽니다.

   >[!NOTE]
   >
   >경험 조각 상위 폴더에 클라우드 구성을 추가하는 경우 구성이 모든 하위 폴더에 의해 상속됩니다.
   >
   >경험 조각 자체에 클라우드 구성을 추가하는 경우, 구성은 모든 변형에서 상속됩니다.

1. **Cloud Services** 탭을 선택합니다.

1. **Cloud Service 구성**&#x200B;의 드롭다운 목록에서 **Adobe Target**&#x200B;을 선택합니다.
1. **Adobe Target**&#x200B;에서 적절한 구성을 선택합니다.

1. **저장 및 닫기**.

## 경험 조각을 Target {#exporting-an-experience-fragment-to-target}으로 내보내기

>[!NOTE]
>
>이미지와 같은 미디어 자산의 경우 참조만 Target에 내보내집니다. 자산 자체는 AEM Assets에 저장된 상태로 유지되며 AEM 게시 인스턴스에서 전달됩니다.
>
>이로 인해 Target으로 내보내기 전에 모든 관련 자산이 있는 경험 조각을 게시해야 합니다.

AEM에서 Target으로 경험 조각을 내보내려면(클라우드 구성을 지정한 후):

1. 경험 조각 콘솔로 이동합니다.
1. target으로 내보낼 경험 조각을 선택합니다.

   >[!NOTE]
   >
   >경험 조각 웹 변형이어야 합니다.

1. **Adobe Target으로 내보내기**&#x200B;를 탭/클릭합니다.

   >[!NOTE]
   >
   >경험 조각을 이미 내보낸 경우 Adobe Target **에서**&#x200B;업데이트 를 선택합니다.

1. 필요에 따라 **내보내기를 게시하지 않고 탭/클릭하거나** 또는 **게시**&#x200B;하십시오.

   >[!NOTE]
   >
   >** 게시**를 선택하면 바로 경험 조각이 게시되어 Target에 전송됩니다.

1. 확인 대화 상자에서 **확인**&#x200B;을 탭/클릭합니다.

   이제 경험 조각이 Target에 있어야 합니다.

>[!NOTE]
>
>또는 [페이지 정보](/help/sites-authoring/author-environment-tools.md#page-information) 메뉴의 비교 명령을 사용하여 페이지 편집기에서 내보내기를 수행할 수 있습니다.

## Target {#using-your-experience-fragments-in-target}에서 경험 조각 사용

이전 작업을 수행하면 경험 조각이 Target의 오퍼 페이지에 표시됩니다. [특정 Target 설명서](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html)를 보고 여기에서 달성할 수 있는 사항을 알아 보십시오.

## 이미 Target {#deleting-an-experience-fragment-already-exported-to-target}(으)로 내보낸 경험 조각을 삭제하는 중

이미 Target으로 내보낸 경험 조각을 삭제하면 Target의 오퍼에서 조각을 이미 사용하고 있는 경우 문제가 발생할 수 있습니다. 조각을 삭제하면 조각 컨텐츠가 AEM에 의해 전달될 때 오퍼를 사용할 수 없게 됩니다.

이러한 상황을 피하려면

* 경험 조각이 현재 활동에서 사용되지 않는 경우 AEM에서는 경고 메시지 없이 조각을 삭제할 수 있습니다.
* 경험 조각이 현재 Target의 활동에서 사용 중인 경우 오류 메시지는 AEM 사용자에게 조각을 삭제하면 활동에 발생할 수 있는 결과에 대해 경고합니다.

   AEM의 오류 메시지에는 사용자가 경험 조각을 삭제할 수 없습니다(강제). 경험 조각이 삭제되는 경우:

   * AEM 경험 조각을 사용한 Target 오퍼에 원치 않는 동작이 표시될 수 있습니다

      * 경험 조각 HTML이 Target에 푸시되었으므로 오퍼가 여전히 렌더링될 수 있습니다
      * 참조된 자산을 AEM에서도 삭제한 경우 경험 조각의 모든 참조가 제대로 작동하지 않을 수 있습니다.
   * 물론 경험 조각이 AEM에 더 이상 존재하지 않으므로 경험 구성요소를 추가로 수정할 수는 없습니다.
