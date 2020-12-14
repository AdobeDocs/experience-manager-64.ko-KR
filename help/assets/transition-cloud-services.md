---
title: 폴더에 번역 클라우드 서비스 적용
description: 폴더에 번역 클라우드 서비스 적용
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 1%

---


# 번역 클라우드 서비스를 {#applying-translation-cloud-services-to-folders} 폴더에 적용

Adobe Experience Manager(AEM)을 사용하면 원하는 번역 제공업체에서 클라우드 기반의 번역 서비스를 활용하여 요구 사항에 따라 에셋을 변환할 수 있습니다.

번역 워크플로우 중에 활용할 수 있도록 번역 클라우드 서비스를 자산 폴더에 직접 적용할 수 있습니다.

## 번역 서비스 적용 중 {#applying-the-translation-services}

번역 클라우드 서비스를 자산 폴더에 직접 적용하면 번역 워크플로우를 만들거나 업데이트할 때 번역 서비스를 구성할 필요가 없습니다.

1. 자산 UI에서 번역 서비스를 적용할 폴더를 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]** 아이콘을 클릭/탭하여 **[!UICONTROL 폴더 속성]** 페이지를 표시합니다.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. **[!UICONTROL Cloud Services]** 탭으로 이동합니다.
1. Cloud Service 구성 목록에서 원하는 번역 공급자를 선택합니다. 예를 들어 Microsoft의 번역 서비스를 사용하려면 **[!UICONTROL Microsoft Translator]**&#x200B;를 선택합니다.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. 변환 공급자에 대한 커넥터를 선택합니다.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. 도구 모음에서 **[!UICONTROL 저장]**&#x200B;을 클릭/탭한 다음 **[!UICONTROL 확인]**&#x200B;을 클릭하여 대화 상자를 닫습니다.번역 서비스가 폴더에 적용됩니다.

## 사용자 정의 번역 커넥터 적용 중 {#applying-custom-translation-connector}

번역 워크플로우에서 사용할 번역 서비스에 대한 사용자 지정 커넥터를 적용하려면 사용자 정의 커넥터를 적용하려면 먼저 패키지 관리자에서 커넥터를 설치합니다. 그런 다음 Cloud Services 콘솔에서 커넥터를 구성합니다. 커넥터를 구성한 후에는 [번역 서비스 적용](transition-cloud-services.md#applying-the-translation-services)에 설명된 Cloud Services 탭의 커넥터 목록에서 커넥터를 사용할 수 있습니다. 사용자 정의 커넥터를 적용하고 번역 워크플로우를 실행하면 번역 프로젝트의 **[!UICONTROL 번역 요약]** 타일에는 **[!UICONTROL 공급자]** 및 **[!UICONTROL 메서드]**&#x200B;의 헤드 아래에 커넥터 세부 정보가 표시됩니다.

1. 패키지 관리자에서 커넥터를 설치합니다.
1. AEM 로고를 클릭/탭하고 **[!UICONTROL 도구 > 배포 > Cloud Services]**&#x200B;로 이동합니다.
1. **[!UICONTROL Cloud Services]** 페이지에서 **[!UICONTROL 제3자 서비스]** 아래에 설치한 커넥터를 찾습니다.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. **[!UICONTROL 지금 구성]** 링크를 클릭/탭하여 **[!UICONTROL 구성 만들기]** 대화 상자를 엽니다.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. 커넥터의 제목과 이름을 지정한 다음 **[!UICONTROL 만들기]**&#x200B;를 클릭/탭합니다. 사용자 지정 커넥터는 [번역 서비스 적용](#applying-the-translation-services)단계 5에 설명된 **[!UICONTROL Cloud Services]** 탭의 커넥터 목록에서 사용할 수 있습니다.
1. 사용자 지정 커넥터를 적용한 후 [번역 프로젝트 만들기](translation-projects.md)에 설명된 변환 워크플로우를 실행합니다. **[!UICONTROL 프로젝트]** 콘솔에서 번역 프로젝트의 **[!UICONTROL 번역 요약]** 타일에 있는 커넥터의 세부 정보를 확인합니다.

   ![chlimage_1-220](assets/chlimage_1-220.png)
