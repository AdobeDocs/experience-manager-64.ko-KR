---
title: 표현물로 XMP 원본에 쓰기
description: XMP 원본에 쓰기 기능이 자산의 메타데이터 변경 사항을 자산의 모든 또는 특정 표현물에 전달하는 방법을 알아봅니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 5%

---

# 표현물로 XMP 원본에 쓰기 {#xmp-writeback-to-renditions}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

의 이 XMP 원본에 쓰기 기능 [!DNL Adobe Experience Manager Assets] 메타데이터 변경 사항을 원래 자산의 표현물에 복제합니다. 자산 내에서 또는 자산을 업로드하는 동안 자산에 대한 메타데이터를 변경하면 변경 사항이 처음에 자산 계층의 메타데이터 노드에 저장됩니다.

XMP 원본에 쓰기 기능을 사용하여 메타데이터 변경 사항을 자산의 모든 또는 특정 표현물에 전달할 수 있습니다. 이 기능은 를 사용하는 메타데이터 속성만 다시 기록합니다 `jcr` namespace, 즉, 라는 속성 `dc:title` 이름이 지정된 `mytitle` 은 아닙니다.

을 수정하는 시나리오를 고려하십시오 [!UICONTROL 제목] 제목이 있는 자산의 속성 `Classic Leather` to `Nylon`.

![메타데이터](assets/metadata.png)

이 경우 [!DNL Experience Manager] Assets는 변경 내용을 **[!UICONTROL 제목]** 속성( `dc:title` 자산 계층에 저장된 자산 메타데이터의 매개 변수입니다.

![metadata_stored](assets/metadata_stored.png)

하지만, [!DNL Experience Manager Assets] 은 자산의 표현물에 메타데이터 변경 사항을 자동으로 전파하지 않습니다. 자세한 내용은 [XMP 원본에 쓰기 사용 방법](#enabling-xmp-writeback).

## XMP 원본에 쓰기 활성화 {#enabling-xmp-writeback}

메타데이터 변경 사항을 업로드할 때 자산의 표현물에 전파할 수 있도록 하려면 를 수정합니다 **Adobe CQ DAM Rendition Maker** 구성 관리자에서 구성합니다.

1. 구성 관리자를 여는 위치 `https://[aem_server]:[port]/system/console/configMgr`.
1. 를 엽니다. **[!UICONTROL Adobe CQ DAM Rendition Maker]** 구성.
1. 을(를) 선택합니다 **[!UICONTROL XMP 전파]** 옵션을 선택한 다음 변경 사항을 저장합니다.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## 특정 표현물에 대해 XMP 원본에 쓰기 활성화 {#enabling-xmp-writeback-for-specific-renditions}

XMP 원본에 쓰기 기능이 메타데이터 변경 사항을 전파하여 표현물을 선택하려면 이러한 표현물을 DAM 메타데이터 쓰기 되돌리기 워크플로우의 XMP 쓰기 처리 워크플로우 단계에 지정합니다. 기본적으로 이 단계는 원래 표현물로 구성됩니다.

변환 축소판 140.100.png 및 319.319.png에 메타데이터를 전파하는 XMP 원본에 쓰기 기능의 경우 다음 단계를 수행합니다.

1. Experience Manager에서 **[!UICONTROL 도구 > 워크플로우 > 모델]**.
1. 에서 [!UICONTROL 모델] 페이지를 열고 **[!UICONTROL DAM 메타데이터 원본에 쓰기]** 워크플로우 모델.
1. In the **[!UICONTROL DAM Metadata Writeback]** properties page, open the **[!UICONTROL XMP Writeback Process]** step.
1. In the **[!UICONTROL Step Properties]** dialog box, tap/click the **[!UICONTROL Process]** tab.
1. 에서 **[!UICONTROL 인수]** 상자, 추가 `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. 탭/클릭 **[!UICONTROL 확인]**.

   ![step_properties](assets/step_properties.png)

1. 새 속성을 사용하여 Dynamic Media 이미지에 대한 피라미드 TIFF 표현물을 재생성하려면 를 추가합니다. **[!UICONTROL Dynamic Media 처리 이미지 자산]** dam 메타데이터 원본에 쓰기 워크플로우로 이동합니다.
PTIFF 표현물은 Dynamic Media 하이브리드 모드에서만 로컬로 만들어지고 저장됩니다. 워크플로우를 저장합니다.

메타데이터 변경 사항이 변환에 전파됩니다 `thumbnail.140.100.png` 및 `thumbnail.319.319.png` 다른 자산이 아니라 자산입니다.

>[!NOTE]
>
>64비트 Linux의 XMP 원본에 쓰기 문제에 대해서는 다음을 참조하십시오 [64비트 RedHat Linux에서 XMP 쓰기 되돌리기 사용 방법](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>지원되는 플랫폼에 대한 자세한 내용은 [XMP 메타데이터 쓰기 되돌리기 사전 요구 사항](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## XMP 메타데이터 필터링 {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] 에서는 자산을 수집할 때 자산 바이너리에서 읽히고 JCR에 저장된 XMP 메타데이터에 대한 속성/노드의 차단 목록 및 허용 목록 필터링을 모두 지원합니다.

차단 목록을 사용하여 필터링하면 제외에 지정된 속성을 제외한 모든 XMP 메타데이터 속성을 가져올 수 있습니다. 그러나 대량의 XMP 메타데이터가 있는 INDD 파일(예: 10,000개의 속성이 있는 노드 1000개)과 같은 자산 유형의 경우 필터링할 노드의 이름을 항상 미리 알려지는 것은 아닙니다. 차단 목록을 사용하여 필터링하면 많은 XMP 메타데이터가 있는 자산을 가져올 수 있는 경우, [!DNL Experience Manager] 인스턴스 또는 클러스터에는 안정성 문제가 발생할 수 있습니다. 예를 들어 중단된 관찰 큐 등이 있습니다.

허용 목록을 통해 XMP 메타데이터를 필터링하면 가져올 XMP 속성을 정의할 수 있으므로 이 문제가 해결됩니다. 이렇게 하면 다른 모든 또는 알 수 없는 XMP 속성이 무시됩니다. 이전 버전과의 호환성을 위해 차단 목록을 사용하는 필터에 이러한 속성 중 일부를 추가할 수 있습니다.

>[!NOTE]
>
>필터링은 자산 바이너리의 XMP 소스에서 파생된 속성에만 작동합니다. EXIF 및 IPTC 형식과 같이 비 XMP 소스에서 파생된 속성의 경우 필터링이 작동하지 않습니다. 예를 들어, 자산 생성 날짜는 라는 속성에 저장됩니다 `CreateDate` EXIF TIFF에서 참조할 수 있습니다. [!DNL Experience Manager] 이 값을 라는 메타데이터 필드에 저장합니다. `exif:DateTimeOriginal`. 소스가 XMP이 아닌 소스이므로 이 속성은 필터링이 작동하지 않습니다.

1. 구성 관리자를 여는 위치 `https://[aem_server]:[port]/system/console/configMgr`.
1. 를 엽니다. **[!UICONTROL Adobe CQ DAM XmpFilter]** 구성.
1. 허용 목록을 통해 필터링을 적용하려면 **[!UICONTROL XMP 허용 목록에 추가하다 속성에 적용]**&#x200B;및에서 가져올 속성을 지정합니다. **[!UICONTROL XMP 필터링에 허용되는 XML 이름]** 상자.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. 허용 목록을 통해 필터링을 적용한 후 차단된 XMP 속성을 필터링하려면 **[!UICONTROL XMP 필터링을 위한 차단된 XML 이름]** 상자. 변경 사항을 저장합니다.

   >[!NOTE]
   >
   >다음 **[!UICONTROL XMP 차단 목록에 추가하다 속성에 적용]** 옵션이 기본적으로 선택됩니다. 즉, 차단 목록을 사용하여 필터링하는 것은 기본적으로 활성화되어 있습니다. 이러한 필터링을 비활성화하려면 **[!UICONTROL XMP 차단 목록에 추가하다 속성에 적용]** 선택 사항입니다.
