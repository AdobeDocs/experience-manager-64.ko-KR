---
title: 메타데이터 편집 또는 추가 방법
description: 의 자산 메타데이터에 대해 알아봅니다. [!DNL Experience Manager] 자산 및 자산 메타데이터를 편집할 수 있는 다양한 방법을 제공합니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: f0522343-f8a9-4d89-8ce8-b3357ae3fe70
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 9%

---

# 메타데이터 편집 또는 추가 방법 {#how-to-edit-or-add-metadata}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

메타데이터는 검색할 수 있는 자산에 대한 추가 정보입니다. 이미지를 업로드할 때 자동으로 추출됩니다. 기존 메타데이터를 편집하거나 기존 필드에 새 메타데이터 속성을 추가할 수 있습니다(예: 메타데이터 필드가 비어 있는 경우).

회사에서 제어되고 신뢰할 수 있는 메타데이터 어휘를 필요로 하기 때문에 [!DNL Experience Manager] 자산은 새 메타데이터 속성을 임시로 추가할 수 없습니다. 작성자가 자산에 새 메타데이터 필드를 추가할 수 없지만 개발자는 추가할 수 있습니다. 자세한 내용은 [자산에 대한 새 메타데이터 속성 만들기](meta-edit.md#editing-metadata-schema).

## 자산에 대한 메타데이터 편집 {#editing-metadata-for-an-asset}

메타데이터를 편집하려면 다음을 수행하십시오.

1. 다음 중 하나를 수행하십시오.

   * Assets UI에서 자산을 선택하고 **[!UICONTROL 속성 보기]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
   * 자산 축소판에서 **[!UICONTROL 속성 보기]** 빠른 작업.
   * 자산 페이지에서 **[!UICONTROL 속성 보기]** 아이콘 ![정보 아이콘](assets/do-not-localize/info_icon.png) 를 클릭합니다.

   자산 페이지에 자산의 모든 메타데이터가 표시됩니다. 이 메타데이터는 업로드(수집)할 때 자동으로 추출됩니다 [!DNL Experience Manager] 자산.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Make edits to the metadata under the various tabs, as required, and when completed, click/tap **[!UICONTROL Save]** from the toolbar to save your changes. Click/tap **[!UICONTROL Close]** to return to the Assets web interface.

   >[!NOTE]
   >
   >텍스트 필드가 비어 있으면 기존 메타데이터 세트가 없습니다. 필드에 값을 입력하고 저장하여 해당 메타데이터 속성을 추가할 수 있습니다.

자산의 메타데이터에 대한 모든 변경 사항은 XMP 데이터의 일부로서 원래 바이너리에 다시 작성됩니다. 이 작업은 AEM 메타데이터 다시 쓰기 작업 과정을 통해 수행됩니다. 기존 속성(예: `dc:title`)을 덮어쓰고 새로 만든 속성(다음과 같은 사용자 지정 속성 포함) `cq:tags`)가 스키마와 함께 추가됩니다.

XMP Write-back은 다음에 설명된 플랫폼 및 파일 형식에 대해 지원 및 활성화됩니다. [기술 요구 사항.](/help/sites-deploying/technical-requirements.md)

## 메타데이터 스키마 편집 {#editing-metadata-schema}

메타데이터 스키마를 편집하는 방법에 대한 자세한 내용은 [메타데이터 스키마 양식 편집](metadata-schemas.md#editing-metadata-schema-forms).

## 내에서 사용자 지정 네임스페이스 등록 [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

AEM 내에 고유한 네임스페이스를 추가할 수 있습니다. cq, jcr 및 sling과 같이 사전 정의된 네임스페이스가 있는 것처럼 저장소 메타데이터 및 xml 처리를 위한 네임스페이스를 가질 수 있습니다.

1. 노드 유형 관리 페이지로 이동합니다 `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. 클릭 또는 탭 **[!UICONTROL 네임스페이스]** 를 클릭합니다. 네임스페이스 관리 페이지가 창에 표시됩니다.

1. 네임스페이스를 추가하려면 를 클릭하거나 탭합니다 **[!UICONTROL 새로 만들기]** 아래에 있습니다.
1. XML 네임스페이스 규칙에서 사용자 지정 네임스페이스를 지정합니다(URI 형식으로 ID를 지정하고 ID에 연결된 접두어를 지정). **[!UICONTROL 저장]**.

## 팁 및 제한 사항 {#best-practices-limitations}

* Touch-UI를 통한 메타데이터 업데이트에서는 `dc` 네임스페이스. HTTP API를 통해 수행된 모든 업데이트는 `jcr` 네임스페이스. 자세한 내용은 [HTTP API를 사용하여 메타데이터를 업데이트하는 방법](/help/assets/mac-api-assets.md#update-asset-metadata).

>[!MORELIKETHIS]
>
>* [자산의 메타데이터 및 요구 사항 정보](metadata.md)

