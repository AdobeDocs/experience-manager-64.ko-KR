---
title: 디지털 자산에 워터마크 추가
description: 워터마크 기능을 사용하여 자산에 디지털 워터마크를 추가하는 방법을 알아봅니다.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 5%

---

# 디지털 자산에 워터마크 지정 {#watermarking}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] 에서는 사용자가 자산의 정품 여부 및 저작권 소유권을 확인하는 데 도움이 되는 자산에 디지털 워터마크를 추가할 수 있습니다. [!DNL Experience Manager Assets] 에서는 PNG 및 JPEG 파일에서 워터마크로 사용할 텍스트를 지원합니다.

Adobe Experience Manager Assets를 사용하면 사용자가 자산의 정품 인증 및 저작권 소유권을 확인하는 데 도움이 되는 이미지에 디지털 워터마크를 추가할 수 있습니다. [!DNL Experience Manager] 자산은 PNG 및 JPEG 파일에서 워터마크로 사용할 텍스트를 지원합니다.

자산에 워터마크를 적용하려면 [!UICONTROL DAM 자산 업데이트] 워크플로우.

1. 액세스 권한 [!DNL Experience Manager] 사용자 인터페이스를 사용하여 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]**.
1. 워크플로우 모델 페이지에서 **[!UICONTROL DAM 자산 업데이트]** 워크플로우 및 **[!UICONTROL 편집]**.

1. 사이드 패널에서 **[!UICONTROL 워터마크 추가]** 한 단계 후에 [!UICONTROL DAM 자산 업데이트] 워크플로우.

   ![DAM 자산 업데이트 워크플로우에서 워터마크 추가 단계를 드래그합니다.](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >배치 [!UICONTROL 워터마크 추가] 이전 단계 [!UICONTROL 프로세스 축소판] 단계.

1. 를 엽니다. **[!UICONTROL 워터마크 추가]** 속성을 표시하는 단계입니다.
1. 에서 **[!UICONTROL 인수]** 탭에서 텍스트, 글꼴 유형, 크기, 색상, 위치, 방향 등 다양한 필드에 유효한 값을 지정합니다. 변경 사항을 확인하려면 **[!UICONTROL 완료]**.

   ![자산의 워터마크 추가 단계에서 인수를 제공합니다](assets/arguments_add_watermark_aem_assets.png)

1. Save the **[!UICONTROL DAM Update Asset]** workflow with the Watermark step.
1. 에서 [!DNL Experience Manager] 사용자 인터페이스에서 샘플 자산을 업로드합니다. 워터마크는 위의 단계에서 구성한 위치에 글꼴 크기, 색상 등으로 나타납니다.

프로그래밍 방식으로 또는 동적 정보로 PDF 문서를 워터마킹하려면 다음을 사용하는 것이 좋습니다 [[!DNL Experience Manager] 문서 서비스](/help/forms/using/overview-aem-document-services.md) 제공

## 팁 및 제한 사항 {#tips-limitations}

* 텍스트 기반 워터마크만 지원됩니다. 이미지를 만들 때 이미지를 업로드할 수 있어도 이미지가 워터마크로 사용되지 않습니다 [!UICONTROL 워터마크 프로세스 추가].
* 워터마크 지정 기능은 PNG 및 JPEG 파일만 지원합니다. 다른 자산 형식은 워터마크가 되지 않습니다.
