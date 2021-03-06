---
title: 이미지 세트
seo-title: Image Sets
description: Dynamic Media에서 이미지 세트를 사용하는 방법을 알아봅니다
seo-description: Learn how to work with image sets in dynamic media
uuid: 16008278-f59f-4fa8-90e9-19c78f132439
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e00e7cc9-b777-4f9e-906d-824bcb2bbd41
exl-id: af3f95aa-a162-4212-a20a-68b5a0e72d6d
feature: Image Sets
role: User
source-git-commit: 77b2643c91092a9a08b67fb5ad06a96a79f4deea
workflow-type: tm+mt
source-wordcount: '2146'
ht-degree: 11%

---

# 이미지 세트 {#image-sets}

이미지 세트는 사용자에게 축소판 이미지를 클릭하여 항목의 다른 보기를 볼 수 있는 통합된 보기 환경을 제공합니다. 이미지 세트를 사용하면 항목의 대체 보기를 표시할 수 있으며 뷰어는 이미지를 자세히 검사할 수 있는 확대/축소 도구를 제공합니다.

이미지 세트는 라는 단어가 포함된 배너에 의해 지정됩니다 **[!UICONTROL 이미지 집합]**. In addition, if the Image Set is published, then the publish date, indicated by the **[!UICONTROL World]** icon is on the banner along with the last modification date, indicated by the **[!UICONTROL Pencil]** icon displays.

![chlimage_1-339](assets/chlimage_1-339.png)

이미지 세트 내에서 이미지 세트를 만들고 축소판을 추가하여 색상 견본을 만들 수도 있습니다.

이 응용 프로그램은 다른 색상, 패턴 또는 마무리로 항목을 표시하려는 경우에 특히 유용합니다. 색상 견본으로 이미지 세트를 만들려면 사용자에게 표시할 각 색상, 패턴 또는 마무리에 대해 하나의 이미지가 필요합니다. 또한 각 색상, 패턴 또는 마무리에 색상, 패턴 또는 마무리 견본이 필요합니다.

예를 들어 서로 다른 색상 BOM이 있는 대문자들의 이미지를 제공한다고 가정합니다. 지폐는 빨간색, 녹색, 파란색이에요. 이 경우 동일한 캡의 샷이 세 개 필요합니다. 하나는 빨간색, 하나는 녹색이고 하나는 파란색 지폐가 있는 한 샷이 필요합니다. 또한 빨간색, 녹색 및 파란색 색상 견본이 필요합니다. 색상 견본은 사용자가 색상 견본 세트 뷰어에서 클릭하여 빨간색으로 청구되거나 녹색으로 청구되거나 파란색으로 청구되는 캡을 보는 축소판 역할을 합니다.

>[!NOTE]
>
>Assets 사용자 인터페이스에 대한 자세한 내용은 [Touch UI를 사용하여 자산 관리](managing-assets-touch-ui.md).

이미지 세트를 생성할 때 Adobe은 다음 우수 사례를 권장하고 다음 제한을 적용합니다.

| 제한 유형 | 우수 사례 | 제한 적용 |
| --- | --- | --- |
| 세트당 중복 자산 수 | 중복 없음 | 20 |
| 설정당 최대 이미지 수 | 세트당 5-10개 이미지 | 1000 |

참조 - [Dynamic Media 제한 사항](/help/assets/limitations.md).

## 빠른 시작: 이미지 세트 {#quick-start-image-sets}

빠르게 시작하고 실행하려면

1. [여러 보기에 대한 기본 이미지를 업로드합니다.](#uploading-assets-in-image-sets)

   이미지 세트에 대한 이미지를 업로드하여 시작합니다. 사용자가 이미지 세트 뷰어에서 이미지를 확대/축소할 수 있으므로, 이미지를 선택할 때 확대/축소를 고려하십시오. 최적의 확대/축소 세부 사항을 위해 가장 큰 차원에서 이미지가 2000픽셀 이상인지 확인하십시오. Dynamic Media은 각각 최대 25메가픽셀을 렌더링할 수 있습니다. 예를 들어, 5000 x 5000메가픽셀 이미지 또는 최대 25메가픽셀 크기의 다른 크기 조합을 사용할 수 있습니다.

   AEM Assets에서는 많은 이미지 파일 형식을 지원하지만, 무손실 TIFF, PNG 및 EPS 이미지가 좋습니다.

1. [이미지 세트를 만듭니다.](#creating-image-sets)

   이미지 세트에서 사용자는 이미지 세트 뷰어에서 축소판 이미지를 클릭합니다.

   자산에 이미지 세트를 만들려면 **[!UICONTROL 만들기 > 이미지 세트]**. 그런 다음 이미지를 추가하고 탭합니다 **[!UICONTROL 저장]**.

   이미지 세트를 자동으로 만들 수도 있습니다 [일괄처리 집합 사전 설정](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

   **중요 사항** — 일괄 처리 세트는 IPS(이미지 프로덕션 시스템)에 의해 자산 수집의 일부로 만들어지며 Dynamic Media - Scene7 모드에서만 사용할 수 있습니다.

   자세한 내용은 [파일 업로드 및 업로드를 위한 이미지 세트 자산 준비](#uploading-assets-in-image-sets).

   자세한 내용은 [선택기를 사용한 작업.](working-with-selectors.md)

1. 추가 [이미지 집합 뷰어 사전 설정](managing-viewer-presets.md)필요한 경우 ).

   관리자는 이미지를 만들거나 수정할 수 있습니다 **[!UICONTROL 뷰어 사전 설정 설정 설정]**. 뷰어 사전 설정으로 이미지 세트를 보려면 이미지 세트를 선택하고 왼쪽 레일 드롭다운 메뉴에서 을 선택합니다 **[!UICONTROL 뷰어]**.

   자세한 내용은 **[!UICONTROL 도구 > 자산 > 뷰어 사전 설정]** 뷰어 사전 설정을 만들거나 편집하려면 다음을 수행하십시오.

1. (선택 사항) [이미지 세트 보기](image-sets.md#viewing-image-sets) 일괄처리 집합 사전 설정을 사용하여 만들었습니다.
1. [이미지 세트 미리 보기.](previewing-assets.md)

   이미지 세트를 선택하고 미리 볼 수 있습니다. 축소판 아이콘을 눌러 선택한 뷰어에서 이미지 세트를 검사합니다. 에서 다른 뷰어를 선택할 수 있습니다 **[!UICONTROL 뷰어]** 메뉴 아래의 왼쪽 레일 드롭다운 메뉴에서 사용할 수 있습니다.

1. [이미지 세트를 게시합니다.](publishing-dynamicmedia-assets.md)

   이미지 세트를 게시하면 URL 및 포함 문자열이 활성화됩니다. 또한 다음을 수행해야 합니다 [모든 사용자 지정 뷰어 사전 설정 게시](managing-viewer-presets.md) 생성되었습니다. 즉시 사용 가능한 뷰어 사전 설정이 이미 게시되었습니다.

1. [웹 응용 프로그램에 URL 연결](linking-urls-to-yourwebapplication.md) 또는 [비디오 또는 이미지 뷰어 포함](embed-code.md).

   AEM Assets은 이미지 세트에 대한 URL 호출을 생성하고 이미지 세트를 게시한 후 활성화합니다. 자산을 미리 볼 때 이러한 URL을 복사할 수 있습니다. 또는 웹 사이트에 포함할 수 있습니다.

   Select the Image Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   See [Linking an Image Set to a web page](linking-urls-to-yourwebapplication.md) and [Embedding the Video or Image Viewer](embed-code.md).

이미지 세트를 편집하려면 다음을 참조하십시오 [이미지 세트 편집.](#editing-image-sets) 또한 를 보고 편집할 수 있습니다 [이미지 집합 속성](managing-assets-touch-ui.md#editing-properties).

세트를 만드는 데 문제가 있다면 의 이미지 및 세트 를 참조하십시오. [Dynamic Media 문제 해결 - Scene7 모드](troubleshoot-dms7.md#images-and-sets).

## 이미지 세트에서 자산 업로드 {#uploading-assets-in-image-sets}

이미지 세트에 대한 이미지를 업로드하여 시작합니다. 사용자가 이미지 세트 뷰어에서 이미지를 확대/축소할 수 있으므로, 이미지를 선택할 때 확대/축소를 고려하십시오. 가장 큰 차원에서 이미지가 2000픽셀 이상인지 확인합니다. 이미지 세트는 많은 이미지 파일 형식을 지원하지만 무손실 TIFF, PNG 및 EPS 이미지를 사용하는 것이 좋습니다.

이미지 세트에 대한 이미지를 업로드하는 것처럼 할 수 있습니다 [자산에서 다른 자산 업로드](managing-assets-touch-ui.md#uploading-assets).

### 업로드할 이미지 세트 자산 준비 {#preparing-image-set-assets-for-upload}

이미지 세트를 만들기 전에 이미지가 올바른 크기와 형식인지 확인하십시오.

다중 보기 이미지 세트를 만들려면 다른 보기의 항목을 표시하거나 동일한 항목의 다른 측면을 표시하는 이미지가 필요합니다. 목표는 항목의 중요한 기능을 강조 표시하여 보기 또는 동작을 완벽하게 파악할 수 있도록 하는 것입니다.

사용자는 이미지 세트에서 이미지를 확대/축소할 수 있으므로 이미지가 가장 큰 차원에 최소 2000픽셀인지 확인하십시오. 자산은 많은 이미지 파일 형식을 지원하지만 무손실 TIFF, PNG 및 EPS 이미지를 사용하는 것이 좋습니다.

>[!NOTE]
>
>제품 색상 견본을 나타내기 위해 축소판을 사용하는 경우 다음을 수행해야 합니다.
>
>다른 색상, 패턴 또는 마무리로 보여주는 동일한 이미지의 다른 촬영 또는 비네팅이 필요합니다. 또한 색상, 패턴 또는 완료에 해당하는 축소판 파일도 필요합니다. 예를 들어 같은 자켓을 검은색, 갈색 및 녹색으로 표시하는 이미지 세트와 함께 축소판을 표시하려면 다음 작업이 필요합니다.
>
>* 같은 재킷의 검정색, 갈색, 그리고 초록색 샷.
>* 검은색, 갈색 및 녹색 색상의 축소판 그림.
>


## 이미지 세트 만들기 {#creating-image-sets}

사용자 인터페이스 또는 API를 통해 이미지 세트를 만들 수 있습니다. 이 섹션에서는 사용자 인터페이스에서 이미지 세트를 만드는 방법을 설명합니다.

>[!NOTE]
>
>이미지 세트를 자동으로 만들 수도 있습니다 [일괄처리 집합 사전 설정](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**중요 사항:** 배치 세트는 IPS(이미지 프로덕션 시스템)에 의해 자산 수집의 일부로 만들어지며 Dynamic Media - Scene7 모드에서만 사용할 수 있습니다.

세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 자산이 추가된 후 수동으로 자산 순서를 변경하거나 정렬할 수 있습니다.

>[!NOTE]
>
>이미지 세트가 `,` (쉼표)를 포함합니다.

이미지 세트를 생성할 때 Adobe은 다음 우수 사례를 권장하고 다음 제한을 적용합니다.

| 제한 유형 | 우수 사례 | 제한 적용 |
| --- | --- | --- |
| 세트당 중복 자산 수 | 중복 없음 | 20년 |
| 설정당 최대 이미지 수 | 세트당 5-10개 이미지 | 1000년 |

참조 - [Dynamic Media 제한 사항](/help/assets/limitations.md).

**이미지 세트를 만들려면**:

1. in **자산**&#x200B;이미지 세트를 만들 위치로 이동하여 를 누릅니다 **[!UICONTROL 만들기]**, 을(를) 선택하고 을(를) 선택합니다. **[!UICONTROL 이미지 세트]**. You can also create the set from inside a folder that contains your assets.

   ![chlimage_1-340](assets/chlimage_1-340.png)

1. 이미지 세트 편집기 페이지에서 **[!UICONTROL 제목]** 필드에서 이미지 세트의 이름을 입력합니다. 이 이름은 이미지 세트의 배너에 표시됩니다. 설명을 입력합니다(선택적).

   ![chlimage_1-341](assets/chlimage_1-341.png)

   >[!NOTE]
   >
   >When creating the image set, you can change the image set thumbnail or allow AEM to select the thumbnail automatically based on the assets in the image set. 축소판을 선택하려면 **[!UICONTROL 축소판 변경]** 이미지를 선택합니다(다른 폴더로 이동하여 이미지를 찾을 수도 있습니다.). If you have selected a thumbnail and then decide that you want AEM to generate one from the image set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. 다음 중 하나를 수행합니다.

   * 의 왼쪽 위 모서리 근처에 있습니다. **[!UICONTROL 이미지 세트 편집기]** 페이지, 탭 **[!UICONTROL 자산 추가]**.
   * 중간 **[!UICONTROL 이미지 세트 편집기]** 페이지, 탭 **[!UICONTROL 탭하여 자산 선택기 열기]**.

   이미지 세트에 포함할 자산을 탭하여 선택합니다. Selected assets have a checkmark icon over them. 완료되면 페이지의 오른쪽 위 모서리 근처에 있는 를 탭합니다. **[!UICONTROL 선택]**.

   With the Asset Selector, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return]**. You can also apply filters to refine your search results. You can filter by path, collection, file type, and tag. Select the filter and then tap the **[!UICONTROL Filter]** icon on the toolbar. 을 탭하여 보기를 변경합니다. **[!UICONTROL 보기]** 아이콘 및 선택 **[!UICONTROL 열 보기]**, **[!UICONTROL 카드 보기]**, 또는 **[!UICONTROL 목록 보기]**.

   자세한 내용은 [선택기를 사용한 작업.](working-with-selectors.md)

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. 세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 자산을 추가한 후 수동으로 자산 순서를 변경하거나 정렬할 수 있습니다.

   필요한 경우 자산의 **[!UICONTROL 재정렬]** 이미지 순서를 세트 목록의 위나 아래로 조정하려면 자산의 파일 이름 오른쪽에 있는 아이콘을 사용합니다.

   ![spin_set_assets](assets/spin_set_assets.png)

   축소판이나 견본을 변경하려면 **[!UICONTROL 축소판]** 이미지 옆에 있는 아이콘을 클릭하여 원하는 축소판 또는 견본으로 이동합니다. 모든 이미지 선택을 완료하면 탭 **[!UICONTROL 저장]**.

1. (선택 사항) 다음 중 하나를 수행합니다.

   * 이미지를 삭제하려면 이미지를 선택한 다음 를 누릅니다 **[!UICONTROL 자산 삭제]**.
   * 페이지의 오른쪽 위 모서리 근처에 있는 사전 설정을 적용하려면 을(를) 탭합니다 **[!UICONTROL 사전 설정]**&#x200B;를 선택한 다음 사전 설정을 선택하여 모든 자산에 한 번에 적용합니다.

1. 탭 **[!UICONTROL 저장]**. 새로 만든 이미지 세트가 만든 폴더에 나타납니다.

## 이미지 세트 보기 {#viewing-image-sets}

사용자 인터페이스에서 또는 를 사용하여 자동으로 이미지 세트를 만들 수 있습니다 [일괄처리 집합 사전 설정](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**중요 사항** — 배치 세트는 IPS에 의해 만들어집니다 [이미지 프로덕션 시스템] 는 자산 수집의 일부로서 Dynamic Media - Scene7 모드에서만 사용할 수 있습니다.)

그러나 일괄처리 집합 사전 설정을 사용하여 만든 집합에서는 다음을 수행합니다 *not* 사용자 인터페이스에 표시됩니다. 이러한 세트는 세 가지 방법으로 볼 수 있습니다. (사용자 인터페이스에서 이미지 세트를 만들었더라도 이러한 방법을 사용할 수 있습니다.)

* 개별 자산의 속성을 열 때. 속성은 선택한 자산이 (아래에) 멤버인 세트를 나타냅니다 **[!UICONTROL 집합 멤버]**). 세트 이름을 탭하여 전체 세트를 확인합니다.

   ![chlimage_1-343](assets/chlimage_1-343.png)

* From a member image of any set. 을(를) 선택합니다 **[!UICONTROL 세트]** 메뉴 아래의 제품에서 자산이 속하는 세트를 표시합니다.

   ![chlimage_1-344](assets/chlimage_1-344.png)

* 검색에서 **[!UICONTROL 필터]**&#x200B;를 확장한 다음 **[!UICONTROL Dynamic Media]** 을(를) 선택합니다. **[!UICONTROL 세트]**.

   검색은 UI에서 수동으로 만들거나 일괄처리 집합 사전 설정을 통해 자동으로 생성된 일치 세트를 반환합니다. 자동화된 세트의 경우, 검색 쿼리는 &quot;포함&quot; 검색 기준을 사용하는 AEM 검색과 다른 &quot;다음으로 시작&quot; 검색 기준을 사용하여 수행됩니다. 필터를 로 설정 **[!UICONTROL 세트]** 는 자동화된 세트를 검색하는 유일한 방법입니다.

   ![chlimage_1-345](assets/chlimage_1-345.png)

>[!NOTE]
>
>에 설명된 대로 사용자 인터페이스를 통해 세트를 볼 수 있습니다. [이미지 집합 편집](#editing-image-sets).

## 이미지 집합 편집 {#editing-image-sets}

다음과 같이 이미지 세트에서 다양한 편집 작업을 수행할 수 있습니다.

* 이미지 세트에 이미지를 추가합니다.
* 이미지 세트에서 이미지 순서를 변경합니다.
* 이미지 세트에서 자산을 삭제합니다.
* 뷰어 사전 설정을 적용합니다.
* 이미지 세트를 삭제합니다.

**이미지 세트를 편집하려면**:

1. 다음 중 하나를 수행합니다.

   * 이미지 세트 자산을 마우스로 가리킨 다음 탭합니다 **[!UICONTROL 편집]** (연필 아이콘).
   * 이미지 세트 자산을 마우스로 가리킨 다음 탭합니다 **[!UICONTROL 선택]** (확인 표시 아이콘)을 누른 다음 **[!UICONTROL 편집]** 클릭합니다.
   * 이미지 세트 자산을 탭한 다음, **[!UICONTROL 편집]** (연필 아이콘)을 클릭하여 제품에서 사용할 수 있습니다.

1. 이미지 세트에서 이미지를 편집하려면 다음 중 하나를 수행합니다.

   * 자산 순서를 조정하려면 이미지를 새 위치로 드래그합니다(항목을 이동하려면 순서 조정 아이콘을 선택합니다.).
   * 항목을 오름차순이나 내림차순으로 정렬하려면 열 머리글을 누릅니다.
   * 자산을 추가하거나 기존 자산을 업데이트하려면 **[!UICONTROL 자산 추가]**. 자산으로 이동하여 선택한 다음 **[!UICONTROL 선택]** 페이지의 오른쪽 위 모서리 근처에 있습니다.

   >[!NOTE]
   >AEM에서 축소판에 사용하는 이미지를 다른 이미지로 대체하여 삭제하면 원본 자산이 계속 표시됩니다.

   * 자산을 삭제하려면 해당 자산을 선택한 다음 **[!UICONTROL 자산 삭제]**.
   * 페이지의 오른쪽 위 모서리 근처에 있는 사전 설정을 적용하려면 을(를) 탭합니다 **[!UICONTROL 사전 설정]**&#x200B;를 선택한 다음 뷰어 사전 설정을 선택합니다.
   * 축소판을 추가하거나 변경하려면 자산의 오른쪽 옆에 있는 축소판 아이콘을 선택합니다. 새 축소판 그림 또는 견본 자산으로 이동하여 선택한 다음 **[!UICONTROL 선택]**.
   * 전체 이미지 세트를 삭제하려면 이미지 세트로 이동하여 선택한 다음 를 누릅니다 **[!UICONTROL 삭제]**.

   >[!NOTE]
   >
   >You can edit the images in an Image Set by navigating to the set, tap **[!UICONTROL Set Members]** in the left rail, and then tap the Pencil icon on an individual asset to open the editing window.****

1. 탭 **[!UICONTROL 저장]** 편집을 완료하면 됩니다.

## 이미지 세트 미리 보기 {#previewing-image-sets}

자세한 내용은 [자산 미리 보기](previewing-assets.md).

## 이미지 집합 게시 {#publishing-image-sets}

자세한 내용은 [자산 게시](publishing-dynamicmedia-assets.md).
