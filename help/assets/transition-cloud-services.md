---
title: 폴더에 번역 클라우드 서비스 적용
description: 폴더에 번역 클라우드 서비스 적용
contentOwner: AG
feature: Translation
role: Admin
exl-id: 87883a3f-db95-41f4-b0aa-cdaeb7e6f555
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 53%

---

# 폴더에 번역 클라우드 서비스 적용 {#applying-translation-cloud-services-to-folders}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager을 사용하면 원하는 번역 공급자로부터 클라우드 기반 번역 서비스를 활용하여 요구 사항에 따라 자산을 번역할 수 있습니다.

번역 워크플로우 중에 활용할 수 있도록 번역 클라우드 서비스를 자산 폴더에 직접 적용할 수 있습니다.

## 번역 서비스 적용 {#applying-the-translation-services}

번역 클라우드 서비스를 자산 폴더에 직접 적용하면 번역 워크플로우를 만들거나 업데이트할 때 번역 서비스를 구성할 필요가 없습니다.

1. 자산 UI에서 번역 서비스를 적용할 폴더를 선택합니다.
1. From the toolbar, click/tap the **[!UICONTROL Properties]** icon to display the **[!UICONTROL Folder Properties]** page.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Navigate to the **[!UICONTROL Cloud Services]** tab.
1. Cloud Service 구성 목록에서 원하는 번역 공급자를 선택합니다. 예를 들어, Microsoft에서 번역 서비스를 사용하려면 **[!UICONTROL Microsoft Translator]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. 번역 공급자의 커넥터를 선택합니다.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. From the toolbar, click/tap **[!UICONTROL Save]**, and then click **[!UICONTROL OK]** to close the dialog.The translation service is applied to the folder.

## 사용자 지정 번역 커넥터 적용  {#applying-custom-translation-connector}

If you want to apply a custom connector for the translation services you want to use in translation workflows. To apply a custom connector, first install the connector from Package Manager. Then, configure the connector from the Cloud Services console. After you configure the connector, it is available in the list of connectors in the Cloud Services tab described in [Applying the translation services](transition-cloud-services.md#applying-the-translation-services). After you apply the custom connector and run translation workflows, the **[!UICONTROL Translation Summary]** tile of the translation project displays the connector details under the heads **[!UICONTROL Provider]** and **[!UICONTROL Method]**.

1. 패키지 관리자에서 커넥터를 설치합니다.
1. 클릭/탭하기 [!DNL Experience Manager] 로고로 이동하여 **[!UICONTROL 도구 > 배포 > Cloud Services]**.
1. Locate the connector you installed under **[!UICONTROL Third Party Services]** in the **[!UICONTROL Cloud Services]** page.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. 클릭/탭하기 **[!UICONTROL 지금 구성]** 링크를 클릭하여 열기 **[!UICONTROL 구성 만들기]** 대화 상자.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Specify a title and a name for the connector, and then click/tap **[!UICONTROL Create]**. The custom connector is available in the list of connectors in the **[!UICONTROL Cloud Services]** tab described in step 5 of [Applying the translation services](#applying-the-translation-services).
1. Run any translation workflow described in [Creating Translation Projects](translation-projects.md) after you apply the custom connector. Verify the details of the connector in the **[!UICONTROL Translation Summary]** tile of the translation project in the **[!UICONTROL Projects]** console.

   ![chlimage_1-220](assets/chlimage_1-220.png)
