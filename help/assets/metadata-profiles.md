---
title: 메타데이터 프로필을 사용하여 폴더의 모든 자산에 기본 메타데이터를 적용합니다
description: 자산의 메타데이터 프로필에 대해 알아봅니다. 메타데이터 프로필을 만들어 폴더 자산에 적용하는 방법을 알아봅니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: a7b0f1d6-7deb-4565-8c7f-27cad7cd6bf8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 17%

---

# 메타데이터 프로필 {#metadata-profiles}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

메타데이터 프로필을 사용하면 폴더 내의 자산에 기본 메타데이터를 적용할 수 있습니다. 메타데이터 프로필을 만들어 폴더에 적용합니다. 이후에 폴더에 업로드하는 모든 자산은 메타데이터 프로필에서 구성한 기본 메타데이터를 상속합니다.

## 메타데이터 프로필 추가 {#adding-a-metadata-profile}

1. 을(를) 탭하거나 클릭합니다 [!DNL Experience Manager] 로고 및 탐색 **[!UICONTROL 도구 > 자산 > 메타데이터 프로필]**&#x200B;를 누른 다음 탭합니다. **[!UICONTROL 만들기]**.
1. 메타데이터 프로필의 제목(예: 샘플 메타데이터)을 입력하고 **[!UICONTROL 제출]**. 다음 **[!UICONTROL 양식 편집]** 을 참조하십시오.

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. 구성 요소를 클릭하고 해당 속성을 **[!UICONTROL 설정]** 탭. 예를 들어 **[!UICONTROL 설명]** 구성 요소를 만들고 해당 속성을 편집합니다.

   ![chlimage_1-481](assets/chlimage_1-481.png)

   에 대해 다음 속성을 편집합니다 **[!UICONTROL 설명]** 구성 요소:

   * **[!UICONTROL 필드 레이블]**: 메타데이터 속성의 표시 이름입니다. 사용자 참조용입니다.
   * **[!UICONTROL 속성에 매핑]**: 이 속성의 값은 저장소에 저장되는 자산 노드에 대한 상대 경로/이름을 제공합니다. 값은 항상 `./` 경로가 자산의 노드 아래에 있음을 나타냅니다.

   ![chlimage_1-482](assets/chlimage_1-482.png)

   지정한 값 **[!UICONTROL 속성에 매핑]** 는 자산의 메타데이터 노드 아래에 속성으로 저장됩니다. For example, if you specify . `/jcr:content/metadata/dc:desc` 의 이름으로 **[!UICONTROL 속성에 매핑]**, [!DNL Experience Manager] 자산은 값을 저장합니다 `dc:desc` at the asset&#39;s metadata node.

   * **[!UICONTROL 기본값]**: 이 속성을 사용하여 메타데이터 구성 요소에 대한 기본값을 추가합니다. 예를 들어 &quot;My description&quot;을 지정하면 이 값이 속성에 할당됩니다 `dc:desc` at the asset&#39;s metadata node.

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >새 메타데이터 속성에 기본값을 추가합니다( 에는 이미 존재하지 않음). `/jcr:content/metadata` node)가 자산의 속성에 대한 속성 및 해당 값을 표시하지 않습니다 **[!UICONTROL 속성]** 기본적으로 페이지를 표시합니다. 에서 새 속성을 보려면 [!UICONTROL 속성] 자산의 페이지에서 해당 스키마 양식을 수정합니다.

1. (선택 사항) 구성 요소를 **[!UICONTROL 양식 편집]** 에서 **[!UICONTROL 양식 작성]** 탭에서 속성을 구성하고 **[!UICONTROL 설정]** 탭. The following properties are available from the **[!UICONTROL Build Form]** tab:

| 구성 요소 | 속성 |
|---|---|
| [!UICONTROL 섹션 머리글] | 필드 레이블, <br> 설명 |
| [!UICONTROL 한 줄 텍스트] | 필드 레이블, <br> 속성에 매핑, <br> 기본값 |
| [!UICONTROL 다중 값 텍스트] | 필드 레이블, <br> 속성에 매핑, <br> 기본값 |
| [!UICONTROL 숫자] | 필드 레이블, <br> 속성에 매핑, <br> 기본값 |
| [!UICONTROL 날짜] | 필드 레이블, <br> 속성에 매핑, <br> 기본값 |
| [!UICONTROL 표준 태그] | 필드 레이블, <br> 속성에 매핑, <br> 기본값, <br> 설명 |

![chlimage_1-484](assets/chlimage_1-484.png)

1. 클릭 **[!UICONTROL 완료]**. 메타데이터 프로필은 의 프로필 목록에 추가됩니다 **[!UICONTROL 메타데이터 프로필]** 페이지.

   ![chlimage_1-485](assets/chlimage_1-485.png)

## 메타데이터 프로필 복사 {#copying-a-metadata-profile}

1. 에서 **[!UICONTROL 메타데이터 프로필]** 페이지에서 프로필을 선택하여 복사본을 만듭니다.

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. 클릭 **[!UICONTROL 복사]** 를 클릭합니다.
1. 에서 **[!UICONTROL 메타데이터 프로필 복사]** 대화 상자에서 프로필의 새 사본의 제목을 입력합니다.
1. 클릭 **[!UICONTROL 복사]**. 프로필의 사본이 **[!UICONTROL 메타데이터 프로필]** 페이지.

   ![chlimage_1-487](assets/chlimage_1-487.png)

## 메타데이터 프로필 삭제 {#deleting-a-metadata-profile}

1. 에서 **[!UICONTROL 메타데이터 프로필]** 페이지에서 삭제할 프로필을 선택합니다.

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. 클릭 **[!UICONTROL 메타데이터 프로필 삭제]** 클릭합니다.
1. 대화 상자에서 **[!UICONTROL 삭제]** 삭제 작업을 확인합니다. 메타데이터 프로필이 목록에서 삭제됩니다.

## 폴더에 메타데이터 프로필 적용 {#applying-a-metadata-profile-to-folders}

메타데이터 프로필을 폴더에 할당하면 모든 하위 폴더는 해당 상위 폴더에서 프로필을 자동으로 상속합니다. 즉, 폴더에 하나의 메타데이터 프로필만 할당할 수 있습니다. 따라서 자산을 업로드, 저장, 사용 및 보관하는 의 폴더 구조를 신중하게 고려하십시오.

폴더에 다른 메타데이터 프로필을 할당한 경우 새 프로필이 이전 프로필을 무시합니다. 이전에 기존 폴더 자산은 변경되지 않은 상태로 유지됩니다. 새 프로필은 나중에 폴더에 추가된 자산에 적용됩니다.

프로필이 할당된 폴더는 카드 이름에 표시되는 프로필의 이름으로 사용자 인터페이스에 표시됩니다.

![chlimage_1-489](assets/chlimage_1-489.png)

특정 폴더에 메타데이터 프로필을 적용하거나 모든 자산에 전체적으로 적용할 수 있습니다.

### 특정 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-specific-folders}

You can apply a metadata profile to a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from **[!UICONTROL Properties]**. This section describes how to apply metadata profiles to folders both ways.

Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

#### 프로필 사용자 인터페이스의 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. 탭하기 [!DNL Experience Manager] 로고 및 탐색 **[!UICONTROL 도구 > 자산 > 메타데이터 프로필]**.
1. 폴더 또는 여러 폴더에 적용할 메타데이터 프로필을 선택합니다.

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. 탭 **[!UICONTROL 폴더에 메타데이터 프로필 적용]** 새로 업로드한 자산을 받는 데 사용할 폴더 또는 여러 폴더를 선택하고 탭합니다 **[!UICONTROL 완료]**. Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

#### 속성의 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-folders-from-properties}

1. 왼쪽 레일에서 **[!UICONTROL 자산]** 그런 다음 메타데이터 프로필을 적용할 폴더로 이동합니다.
1. 폴더에서 확인 표시를 눌러 선택한 다음 탭합니다  **[!UICONTROL 속성]**.

1. 을(를) 선택합니다 **[!UICONTROL 메타데이터 프로필]** 탭을 클릭하고 드롭다운 메뉴에서 프로필을 선택한 다음 를 클릭합니다 **[!UICONTROL 저장]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

### 메타데이터 프로필을 전체적으로 적용 {#applying-a-metadata-profile-globally}

폴더에 프로필을 적용하는 것 외에도 폴더에 업로드된 모든 컨텐츠가 전역적으로 적용되도록 프로필을 적용할 수 있습니다 [!DNL Experience Manager] 폴더의 자산에는 선택한 프로필이 적용됩니다. 메타데이터 프로필을 전체적으로 적용하려면 다음 단계를 수행합니다.

1. 다음 중 하나를 수행하십시오.

   * 다음으로 이동 `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` 해당 프로필을 적용하고 을 탭하거나 클릭합니다 **[!UICONTROL 저장]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * 다음 노드로 CRXDE Lite으로 이동합니다. `/content/dam/jcr:content`. 속성 추가 `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` 탭 **[!UICONTROL 모두 저장]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## 폴더에서 메타데이터 프로필 제거 {#removing-a-metadata-profile-from-folders}

폴더에서 메타데이터 프로필을 제거하면 모든 하위 폴더는 해당 상위 폴더에서 프로필을 자동으로 상속받게 됩니다. 그러나 폴더 내에서 발생한 파일의 모든 처리가 그대로 유지됩니다.

You can remove a metadata profile from a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from the **[!UICONTROL Properties]**. This section describes how to remove metadata profiles from folders both ways.

### 프로필 사용자 인터페이스를 통해 폴더에서 메타데이터 프로필 제거 {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

프로필 사용자 인터페이스를 통해 폴더에서 메타데이터 프로필을 제거하려면 다음 단계를 수행합니다.

1. 탭하기 [!DNL Experience Manager] 로고 및 탐색 **[!UICONTROL 도구 > 자산 > 메타데이터 프로필]**.
1. 폴더 또는 여러 폴더에서 제거할 메타데이터 프로필을 선택합니다.
1. 탭 **[!UICONTROL 폴더에서 메타데이터 프로필 제거]** 프로필을 제거할 폴더 또는 여러 폴더를 선택한 다음 **[!UICONTROL 완료]**.

   이름이 더 이상 폴더 이름 아래에 표시되지 않으므로 메타데이터 프로필이 더 이상 폴더에 적용되지 않았는지 확인할 수 있습니다.

### 속성을 통해 폴더에서 메타데이터 프로필 제거 {#removing-metadata-profiles-from-folders-via-properties}

1. 탭하기 [!DNL Experience Manager] 로고 및 탐색 **[!UICONTROL 자산]** 을 클릭하여 메타데이터 프로필을 제거할 폴더로 이동합니다.
1. 폴더에서 확인 표시를 눌러 선택한 다음 탭합니다 **[!UICONTROL 속성]**.
1. 을(를) 선택합니다 **[!UICONTROL 메타데이터 프로필]** 탭을 선택하고 **[!UICONTROL 없음]** 를 클릭합니다. 탭 **[!UICONTROL 저장]**.

Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.
