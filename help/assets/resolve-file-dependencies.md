---
title: 파일 종속성 해결
seo-title: 파일 종속성 해결
description: 자동 해결에 실패할 때 텍스처 맵 파일과 같은 3D 파일 종속성을 해결하는 방법.
seo-description: 자동 해결에 실패할 때 텍스처 맵 파일과 같은 3D 파일 종속성을 해결하는 방법.
uuid: 49cefabf-147b-4a78-90f3-0f2d6a8e8cae
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 05b7410b-82a1-4267-ac07-2edbc29e9ee8
exl-id: 088d32a8-a47e-4ae6-a171-8d327d3dac64
feature: 3D 자산
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 39%

---

# 파일 종속성 해결 {#resolving-file-dependencies}

텍스처 맵 파일과 같은 기본 3D 모델 파일 종속성은 가능한 경우 자동으로 해결됩니다. 이 기능은 3D 파일에서 찾은 것과 동일한 이름의 파일을 AEM이 가까운 자산 폴더에서 검색하도록 함으로써 수행됩니다. 미리 보기 만들기 처리 단계에서 하나 이상의 종속성을 해결할 수 없는 경우, 자산 카드의 **[!UICONTROL 카드 보기]**&#x200B;에 다음 빨간색 배너 메시지가 표시됩니다.

![chlimage_1-124](assets/chlimage_1-124.png)

**파일 종속성을 해결하려면 다음을 수행하십시오**.

1. **[!UICONTROL 카드 보기]**&#x200B;에서 카드의 **[!UICONTROL 해결되지 않은 종속성]** 배너 메시지 위로 포인터를 가져간 다음 **[!UICONTROL 느낌표]** 아이콘을 탭합니다.

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. **[!UICONTROL 메타데이터 속성]** 페이지에서 **[!UICONTROL 종속성]** 탭을 탭합니다.

   AEM에서 자동으로 확인할 수 없는 파일은 **[!UICONTROL 원래 경로]** 열 아래에 빨간색으로 표시됩니다.

1. 다음 중 하나 이상을 수행하십시오.

   * **종속성을 찾아 선택합니다**. (이 선택 사항은 종속성 파일을 이미 업로드했다고 가정합니다.)

      1. 빨간색 경로의 왼쪽에 있는 **[!UICONTROL 파일 찾아보기]** 아이콘을 누릅니다.
      1. **[!UICONTROL 콘텐트 선택]** 페이지에서 누락된 파일로 이동한 다음 파일의 카드를 눌러 선택합니다.
      1. **[!UICONTROL 콘텐츠 선택]** 페이지의 왼쪽 위 모서리에서 **[!UICONTROL 닫기]**(X 아이콘)를 탭하여 **[!UICONTROL 속성 보기]** 페이지로 돌아갑니다.
   * **종속성을 업로드합니다**. (이 선택 사항은 누락된 파일을 아직 업로드하지 않았다고 가정합니다.)

      1. 누락된 경로 및 파일 이름을 확인합니다.
      1. 속성 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 닫기]**&#x200B;를 탭합니다.

   파일이 업로드되면 **[!UICONTROL 속성 보기 > 종속성]** 페이지로 돌아갑니다. 새로 업로드된 자산이 이제 참조된 자산으로 올바로 나열됩니다.

   * **종속성을 무시합니다**.

      누락된 종속성이 더 이상 필요하지 않은 경우, 누락된 파일의 왼쪽에 있는 텍스트 필드에 **[!UICONTROL 참조된 자산]** 열에서 AEM 3D가 파일을 무시하도록 `n/a`를 입력합니다.



1. **[!UICONTROL 속성 보기]** 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 저장]**&#x200B;을 탭합니다.
1. **[!UICONTROL 닫기]****[!UICONTROL 를 탭하여 [카드 보기]로 돌아갑니다]**.

   자산이 새로 해결된 종속성과 함께 자동으로 다시 처리됩니다.
