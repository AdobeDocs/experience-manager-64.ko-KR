---
title: Dynamic Media 이미지 사전 설정 적용
seo-title: Applying Dynamic Media image presets
description: Dynamic Media에서 이미지 사전 설정을 적용하는 방법 알아보기
seo-description: Learn how to apply image presets in Dynamic Media
uuid: 8bafcbd0-6df0-4d5b-b2f7-116ddb4ec060
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5c1f60ac-3741-4002-9c5d-c128f118342b
exl-id: 07a4f315-a60e-456b-b02d-035b3f6ad9ad
feature: Image Presets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 20%

---

# Dynamic Media 이미지 사전 설정 적용 {#applying-image-presets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이미지 사전 설정을 사용하면 자산에서 서로 다른 크기, 다른 형식 또는 동적으로 생성된 다른 이미지 속성이 있는 이미지를 동적으로 전달할 수 있습니다. 이미지를 내보낼 때 사전 설정을 선택할 수 있으며, 이 경우 관리자가 지정한 사양에 맞게 이미지를 재포맷할 수도 있습니다.

또한 응답형(에 의해 지정됨)인 이미지 사전 설정을 선택할 수 있습니다 **[!UICONTROL RESS]** 버튼 선택 후).

이 섹션에서는 이미지 사전 설정을 사용하는 방법을 설명합니다. [관리자는 이미지 사전 설정을 만들고 구성할 수 있습니다](managing-image-presets.md).

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정에서 작동하며 마지막 전달 순간에 인텔리전스를 사용하여 브라우저 또는 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다. 자세한 내용은 [스마트 이미징](imaging-faq.md) 추가 정보.

미리 볼 때 언제든지 이미지에 이미지 사전 설정을 적용할 수 있습니다.

**Dynamic Media 이미지 사전 설정을 적용하려면**:

1. 자산을 열고 왼쪽 레일에서 드롭다운 메뉴를 탭한 다음, **[!UICONTROL 표현물]**.

   >[!NOTE]
   >
   >* 정적 표현물은 창의 맨 위에 나타납니다. 동적 표현물은 하단에 나타납니다. 동적 변환만 사용하면 URL을 사용하여 이미지를 표시할 수 있습니다. 다음 **[!UICONTROL URL]** 단추는 동적 변환을 선택하는 경우에만 나타납니다. 다음 **[!UICONTROL RESS]** 단추는 응답형 이미지 사전 설정을 선택하는 경우에만 나타납니다.
   >
   >* 선택하면 시스템에 다양한 표현물이 표시됩니다 **[!UICONTROL 표현물]** 를 입력합니다. You can increase the number of presets seen. 자세한 내용은 [표시되는 이미지 사전 설정 수 증가](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display).


   ![chlimage_1-208](assets/chlimage_1-208.png)

1. 다음 중 하나를 수행합니다.

   * 이미지 사전 설정을 미리 볼 동적 변환을 선택합니다.
   * 탭 **[!UICONTROL URL]**, **[!UICONTROL 포함]**, 또는 **[!UICONTROL RESS]** 팝업을 표시하려면 다음을 수행하십시오.

   >[!NOTE]
   >
   >If the asset *and* the image preset are not yet published, the **[!UICONTROL URL]** button (or **[!UICONTROL URL]** and **[!UICONTROL RESS]** buttons, if applicable) are not available.
   >
   >또한 이미지 사전 설정은 Dynamic Media 서버에 자동으로 게시됩니다.
