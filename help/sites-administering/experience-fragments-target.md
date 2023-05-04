---
title: 경험 조각과 Target 통합
seo-title: Target Integration with Experience Fragments
description: 경험 조각과 Target 통합
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 76%

---

# 경험 조각과 Target 통합{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>이 기능을 사용하려면 [AEM 6.4 서비스 팩 2(6.4.2.0)](/help/release-notes/sp-release-notes.md) 또는 나중에 사용합니다.

내보낼 수 있습니다 [경험 조각](/help/sites-authoring/experience-fragments.md), Adobe Experience Manager (AEM)에서 생성된 를 Adobe Target으로 이동합니다. 그런 다음 Target 활동의 오퍼로 사용하여 경험을 대규모로 테스트하고 개인화할 수 있습니다. 이를 통해 AEM의 편의성과 기능을 강력한 AI(Automated Intelligence) 및 기계 학습(ML) 기능을 Target에 결합할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

다음과 같은 다양한 작업을 수행해야 합니다.

1. AEM을 Target과 통합해야 합니다. 자세한 내용은 [Adobe Target과 통합](/help/sites-administering/target.md) 추가 정보.
1. 경험 조각은 작성 인스턴스에서 내보내지므로 다음 작업을 수행해야 합니다 [Link Externalizer 구성](/help/sites-developing/externalizer.md) 작성자 인스턴스에서 게시 인스턴스에 대해 링크가 외부화되었는지 확인합니다.

## 클라우드 구성 추가 {#add-the-cloud-configuration}

조각을 내보내기 전에 **Adobe Target**&#x200B;용 **클라우드 구성**&#x200B;을 조각 또는 폴더에 추가해야 합니다:

1. **경험 조각** 콘솔로 이동합니다.
1. 적절한 폴더 또는 조각에 대한 **페이지 속성**&#x200B;을 엽니다.

   >[!NOTE]
   >
   >클라우드 구성을 경험 조각 상위 폴더에 추가하면 해당 구성은 모든 하위 폴더에 상속됩니다.
   >
   >클라우드 구성을 경험 조각에 추가하면 해당 구성은 모든 변형에 상속됩니다.

1. **클라우드 서비스** 탭을 선택합니다.

1. 아래 **Cloud Service 구성**, 선택 **Adobe Target** 드롭다운 목록에서 을 선택합니다.
1. 아래 **Adobe Target**&#x200B;에서 적절한 구성을 선택합니다.

1. **저장 및 닫기**.

##  Target으로 경험 조각 내보내기 {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>이미지와 같은 미디어 에셋의 경우 하나의 참조만 Target으로 가져올 수 있습니다. 에셋 자체는 AEM Assets 내에 저장되며 AEM 게시 인스턴스에서 전달됩니다.
>
>이로 인해 경험 조각 및 관련된 모든 에셋은 Target으로 내보내기 전에 게시되어야 합니다.

AEM에서 Target으로 경험 조각을 내보내려면(클라우드 구성 지정 이후):

1. 경험 조각 콘솔로 이동합니다.
1. Target으로 내보내고자 하는 경험 조각을 선택합니다.

   >[!NOTE]
   >
   >이는 경험 조각 웹 변형이어야 합니다.

1. **Adobe Target으로 내보내기**&#x200B;를 탭/클릭합니다.

   >[!NOTE]
   >
   >경험 조각을 이미 내보낸 경우 **Adobe Target에서 업데이트**&#x200B;를 선택합니다.

1. 필요에 따라 **게시하지 않고 내보내기** 또는 **게시**&#x200B;를 탭/클릭합니다.

   >[!NOTE]
   >
   >** 게시**를 선택하면 바로 경험 조각이 게시되어 Target에 전송됩니다.

1. 확인 대화 상자에서 **확인**&#x200B;을 탭/클릭합니다.

   이제 경험 조각은 Target에 있게 됩니다.

>[!NOTE]
>
>또는 [페이지 정보](/help/sites-authoring/author-environment-tools.md#page-information) 메뉴의 비슷한 명령을 사용하여 페이지 편집기에서 내보내기를 수행할 수 있습니다.

##  Target에서 경험 조각 사용 {#using-your-experience-fragments-in-target}

이전 작업을 수행하면 경험 조각이 Target의 오퍼 페이지에 표시됩니다. 여기에서 수행할 수 있는 작업에 대해 알아보려면 [관련 Target 설명서](https://experiencecloud.adobe.com/resources/help/ko_KR/target/target/aem-experience-fragments.html)를 살펴보십시오.

## 이미 Target으로 내보낸 경험 조각 삭제 {#deleting-an-experience-fragment-already-exported-to-target}

이미 Target으로 내보낸 경험 조각을 삭제하면 Target의 오퍼에서 해당 조각을 사용 중인 경우 문제가 발생할 수 있습니다. AEM에서 조각 콘텐츠를 전달 중이므로 조각을 삭제하면 오퍼를 사용할 수 없습니다.

이러한 상황을 방지하는 방법:

* 경험 조각이 현재 활동에서 사용되고 있지 않은 경우, 사용자는 AEM을 통해 경고 메시지 없이 조각을 삭제할 수 있습니다.
* 경험 조각이 현재 활동에서 사용되고 있는 경우, 조각 삭제가 활동에 미칠 수 있는 결과를 나타내는 경고 메시지가 AEM 사용자에게 표시됩니다.

   AEM에 오류 메시지가 표시되어도 사용자는 경험 조각을 삭제할 수 있습니다. 경험 조각을 삭제하면 다음과 같은 결과가 발생합니다.

   * AEM 경험 조각 및 Target 오퍼가 원하지 않은 동작을 수행할 수 있습니다.

      * 경험 조각 HTML이 Target으로 푸시되었으므로 해당 오퍼는 여전히 렌더링될 수 있습니다.
      * AEM에서 참조된 에셋을 삭제해도 경험 조각의 참조가 올바르게 작동하지 않을 수 있습니다.
   * 물론, AEM에 경험 조각이 더 이상 존재하지 않으므로 이후에 경험 조각을 수정할 수 없습니다.
