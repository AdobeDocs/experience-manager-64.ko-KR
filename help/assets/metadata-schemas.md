---
title: 메타데이터 스키마
description: '메타데이터 스키마는 속성에 대해 표시되는 속성 페이지의 레이아웃과 메타데이터 속성을 정의합니다. 사용자 지정 메타데이터 스키마를 만들고, 메타데이터 스키마를 편집하고, 자산에 메타데이터 스키마를 적용하는 방법을 알아보십시오.  '
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 82f42bb3-2c01-407c-a41b-9abe7be4660e
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '2524'
ht-degree: 4%

---

# 메타데이터 스키마 {#metadata-schemas}

[!DNL Experience Manager Assets]에서 메타데이터 스키마는 특정 스키마를 사용하는 자산에 대해 표시되는 속성 페이지 및 메타데이터 속성을 정의합니다. 메타데이터 속성에는 제목, 설명, MIME 유형, 태그 등이 포함됩니다. 메타데이터 스키마 Forms 편집기를 사용하여 기존 스키마를 수정하거나 사용자 지정 메타데이터 스키마를 추가할 수 있습니다.

자산에 대한 속성 페이지를 보고 편집하려면 다음 단계를 수행합니다.

1. 카드 보기의 자산 타일의 빠른 작업에서 **[!UICONTROL 속성 보기]**&#x200B;를 클릭하거나 탭합니다.

   ![chlimage_1-170](assets/chlimage_1-170.png)

   또는 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 속성]** 아이콘을 클릭하거나 탭합니다.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. 사용 가능한 탭 아래에서 다양한 편집 가능한 메타데이터 속성을 편집할 수 있습니다. 하지만 속성 페이지의 [!UICONTROL 기본] 탭에서 자산 [!UICONTROL 유형]을 수정할 수 없습니다.

   ![chlimage_1-172](assets/chlimage_1-172.png)

   자산에 대한 MIME 유형을 수정하려면 사용자 지정 메타데이터 스키마 양식을 사용하거나 기존 양식을 수정합니다. 자세한 내용은 [메타데이터 스키마 편집 Forms](metadata-schemas.md#editing-metadata-schema-forms)을 참조하십시오. 특정 MIME 유형에 대한 메타데이터 스키마를 수정하는 경우 현재 MIME 유형 및 모든 자산 하위 유형이 있는 자산에 대한 속성 페이지 레이아웃이 수정됩니다. 예를 들어 `default/image` 아래에서 `jpeg` 스키마를 수정하면 MIME 유형이 `IMAGE/JPEG`인 자산에 대한 메타데이터 레이아웃(자산 속성)만 수정합니다. 그러나 기본 스키마를 편집하는 경우, 변경 사항은 모든 유형의 자산에 대한 메타데이터 레이아웃을 수정합니다.

## 메타데이터 스키마 양식 {#default-metadata-schema-forms}

양식/템플릿 목록을 보려면 [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.

[!DNL Experience Manager] 은 다음의 메타데이터 스키마 양식 템플릿을 제공합니다.

| 템플릿 |  | 설명 |
|---|---|---|
| [!UICONTROL 기본값] |  | 자산에 대한 기본 메타데이터 스키마 양식입니다. |
|  | 다음 하위 양식은 [!UICONTROL default] 양식의 속성을 상속합니다. |  |
|  | <ul><li> [!UICONTROL dm_video]</li></ul> | Dynamic Media 비디오용 스키마 양식입니다. |
|  | <ul><li> [!UICONTROL 이미지]</li></ul> | MIME 유형이 &quot;이미지&quot;인 자산에 대한 스키마 양식입니다(예: 이미지/jpeg, 이미지/png 등). <br> 이미지   양식에는 다음과 같은 하위 양식 템플릿이 있습니다. <ul><li> [!UICONTROL jpeg]: 하위 유형이 jpeg인 자산에 대한 스키마  [!UICONTROL 양식입니다].</li> <li>[!UICONTROL tiff]: 하위 유형 tiff가 있는 자산에 대한 스키마  [!UICONTROL 양식입니다].</li></ul> |
|  | <ul><li> [!UICONTROL 애플리케이션]</li></ul> | MIME 유형이 &quot;application&quot;인 자산에 대한 스키마 양식입니다(예: application/pdf, application/zip 등). <br>[!UICONTROL pdf]: 하위 유형 pdf가 있는 자산에 대한 스키마 양식입니다. |
|  | <ul><li>[!UICONTROL 비디오]</li></ul> | 비디오/avi, 비디오/mp4 등과 같이 MIME 유형이 &quot;비디오&quot;인 자산에 대한 스키마 양식입니다. |
| [!UICONTROL 컬렉션] |  | 컬렉션에 대한 스키마 양식입니다. |
| [!UICONTROL contentfragment] |  | 컨텐츠 조각에 대한 스키마 양식입니다. |
| [!UICONTROL forms] |  | 이 스키마 양식은 [Adobe Experience Manager Forms](/help/forms/home.md)에 관한 것입니다. |

>[!NOTE]
>
>스키마 양식의 하위 양식을 보려면 스키마 양식 이름을 클릭/탭합니다.

## 메타데이터 스키마 양식 추가 {#adding-a-metadata-schema-form}

1. 사용자 지정 템플릿을 목록에 추가하려면 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >편집되지 않은 템플릿에는 그 앞에 잠금 아이콘이 표시됩니다. 템플릿을 사용자 지정하는 경우 템플릿이 사라지기 전에 잠금 아이콘이 사라집니다.

1. 대화 상자에서 스키마 양식의 제목을 입력하고 **[!UICONTROL 만들기]**&#x200B;를 클릭하여 양식 작성 프로세스를 완료합니다.

   ![chlimage_1-174](assets/chlimage_1-174.png)

## 메타데이터 스키마 양식 편집 {#editing-metadata-schema-forms}

새로 추가되거나 기존 메타데이터 스키마 양식을 편집할 수 있습니다. 메타데이터 스키마 양식은 다음과 같습니다.

* 탭
* 탭 내의 양식 항목.

이러한 양식 항목을 CRX 저장소의 메타데이터 노드 내의 필드에 매핑/구성할 수 있습니다.

새 탭 또는 양식 항목을 메타데이터 스키마 양식에 추가할 수 있습니다. 상위에서 파생된 탭 및 양식 항목은 잠긴 상태입니다. 하위 수준에서 변경할 수 없습니다.

1. **[!UICONTROL 스키마 Forms]** 페이지에서 양식 앞의 확인란을 선택한 다음 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. **[!UICONTROL 메타데이터 스키마 편집기]** 페이지에서 **[!UICONTROL 빌드 양식]** 탭의 구성 요소 유형 목록에서 하나 이상의 구성 요소를 **[!UICONTROL 기본]** 탭으로 드래그하여 자산의 속성 페이지를 사용자 지정합니다.

   ![chlimage_1-176](assets/chlimage_1-176.png)

1. 구성 요소를 구성하려면 구성 요소를 선택하고 **[!UICONTROL 설정]** 탭에서 해당 속성을 수정합니다.

### 양식 작성 탭 내의 구성 요소 {#components-within-the-build-form-tab}

**[!UICONTROL 빌드 양식]** 탭에는 스키마 양식에 사용하는 양식 항목이 나열됩니다. **[!UICONTROL 설정]** 탭은 **[!UICONTROL 양식 작성]** 탭에서 선택하는 각 항목의 속성을 제공합니다. 다음 표에는 **[!UICONTROL 빌드 양식]** 탭에서 사용할 수 있는 양식 항목이 나열되어 있습니다.

| 구성 요소 이름 | 설명 |
|---|---|
| [!UICONTROL 섹션 머리글] | 공통 구성 요소 목록에 대한 섹션 머리글을 추가합니다. |
| [!UICONTROL 한 줄 텍스트] | 단일 행 텍스트 속성을 추가합니다. 문자열로 저장됩니다. |
| [!UICONTROL 다중 값 텍스트] | 다중 값 텍스트 속성을 추가합니다. 문자열 배열로 저장됩니다. |
| [!UICONTROL 번호] | 숫자 구성 요소를 추가합니다. |
| [!UICONTROL 날짜] | 날짜 구성 요소를 추가합니다. |
| [!UICONTROL 드롭다운] | 드롭다운 목록을 추가합니다. |
| [!UICONTROL 표준 태그] | 태그 추가. |
| [!UICONTROL 스마트 태그] | 을(를) 추가하여 메타데이터 태그를 자동으로 추가하여 검색 기능을 보강합니다. |
| [!UICONTROL 숨김 필드] | 숨김 필드를 추가합니다. 자산을 저장할 때 POST 매개 변수로 전송됩니다. |
| [!UICONTROL 자산 참조자] | 이 구성 요소를 추가하여 자산에서 참조하는 자산 목록을 표시합니다. |
| [!UICONTROL 자산 참조] | 를 추가하여 자산을 참조하는 자산 목록을 표시합니다. |
| [!UICONTROL 제품 참조] | 를 추가하여 자산과 연결된 제품 목록을 표시합니다. |
| [!UICONTROL 자산 등급] | 를 추가하여 자산 등급을 매기는 옵션을 표시합니다. |
| [!UICONTROL 상황에 맞는 메타데이터] | 를 추가하여 자산의 속성 페이지에서 다른 메타데이터 탭 표시를 제어합니다. |

### 메타데이터 구성 요소 편집 {#editing-the-metadata-component}

양식에서 메타데이터 구성 요소의 속성을 편집하려면 구성 요소를 클릭하고 **[!UICONTROL 설정]** 탭에서 다음 속성의 하위 집합을 모두 또는 편집하십시오.

**필드 레이블**: 자산의 속성 페이지에 표시되는 메타데이터 속성의 이름입니다.

**속성에 매핑**: 이 속성은 CRX 저장소에 저장되는 자산 노드의 상대 경로/이름을 지정합니다. 경로가 자산의 노드 아래에 있음을 나타내므로 이 경로는 `./`로 시작됩니다.

다음은 이 속성에 유효한 값입니다.

* `./jcr:content/metadata/dc:title`: 자산의 메타데이터 노드에 있는 값을 속성으로  `dc:title`저장합니다.

* `./jcr:created`: 자산의 노드에 JCR 속성을 표시합니다. 보기 속성에서 이러한 속성을 구성하는 경우, 해당 속성이 보호되므로 편집 비활성화로 표시하는 것이 좋습니다. 그렇지 않으면 자산의 속성을 저장할 때 [!UICONTROL 자산 오류가] 결과를 수정하지 못했습니다.

구성 요소가 메타데이터 스키마 양식에 올바르게 표시되는지 확인하려면 속성 경로에 공백이 없어야 합니다.

**자리 표시자**: 이 속성을 사용하여 메타데이터 속성과 관련된 관련 자리 표시자 텍스트를 지정합니다.

**필수**: 이 속성을 사용하여 속성 페이지에서 메타데이터 속성을 필수로 표시합니다.

**편집 비활성화**: 이 속성을 사용하여 속성 페이지에서 메타데이터 속성을 편집할 수 없게 합니다.

**읽기 전용에 빈 필드 표시**: 값이 없는 경우에도 속성 페이지에 메타데이터 속성을 표시하려면 이 속성을 표시합니다. 기본적으로 메타데이터 속성에 값이 없으면 속성 페이지에 나열되지 않습니다.

**순서가 지정된 목록 표시**: 이 속성을 사용하여 선택 항목의 순서가 지정된 목록을 표시합니다

**선택** 사항: 목록에서 선택 사항을 지정하려면 이 속성을 사용하십시오

**설명** : 이 속성을 사용하여 메타데이터 구성 요소에 대한 간단한 설명을 추가합니다.

**클래스**: 속성이 연결된 객체 클래스입니다.

**삭제** 아이콘스키마 양식에서 구성 요소를 삭제하려면 이 아이콘을 클릭합니다.

>[!NOTE]
>
>숨김 필드 구성 요소에는 이러한 속성이 포함되지 않습니다. 대신 속성 이름, 값, 필드 레이블 및 설명과 같은 속성을 포함합니다. 숨김 필드 구성 요소에 대한 값은 자산이 저장될 때마다 POST 매개 변수로 전송됩니다. 자산에 대한 메타데이터로 저장되지 않습니다.

**[!UICONTROL 필수]** 옵션을 선택하면 필수 메타데이터가 없는 자산을 검색할 수 있습니다. **[!UICONTROL 필터]** 패널에서 **[!UICONTROL 메타데이터 유효성 검사]** 설명을 확장하고 **[!UICONTROL 잘못된]** 옵션을 선택합니다. 검색 결과에 스키마 양식을 통해 구성한 필수 메타데이터가 누락된 자산이 표시됩니다.

![chlimage_1-178](assets/chlimage_1-178.png)

컨텍스트 메타데이터 구성 요소를 스키마 양식의 모든 탭에 추가하는 경우 구성 요소는 특정 스키마가 적용되는 자산의 속성 페이지에 목록으로 표시됩니다. 목록에는 상황별 메타데이터 구성 요소를 적용한 탭을 제외한 다른 모든 탭이 포함되어 있습니다. 현재 이 기능은 컨텍스트에 따라 메타데이터 표시를 제어하는 기본 기능을 제공합니다.

![chlimage_1-179](assets/chlimage_1-179.png)

컨텍스트 메타데이터 구성 요소가 적용되는 탭 외에 속성 페이지에 탭을 포함하려면 목록에서 탭을 선택합니다. 탭이 속성 페이지에 추가됩니다.

![chlimage_1-180](assets/chlimage_1-180.png)

### JSON 파일에 속성 지정 {#specifying-properties-in-json-file}

**[!UICONTROL 설정]** 탭에서 옵션에 대한 속성을 지정하는 대신 해당 키-값 쌍을 지정하여 JSON 파일에서 옵션을 정의할 수 있습니다. **[!UICONTROL JSON 경로]** 필드에 JSON 파일의 경로를 지정합니다.

### 스키마 양식에서 탭 추가 또는 삭제 {#adding-deleting-a-tab-in-the-schema-form}

스키마 편집기를 사용하면 탭을 추가하거나 삭제할 수 있습니다. 기본 스키마 양식에는 기본적으로 **[!UICONTROL 기본]**, **[!UICONTROL 고급]**, **[!UICONTROL IPTC]** 및 **[!UICONTROL IPTC 확장]** 탭이 포함됩니다.

![chlimage_1-181](assets/chlimage_1-181.png)

`+` 을 클릭하여 스키마 양식에 새 탭을 추가합니다. 기본적으로 새 탭의 이름은 `Unnamed-1`입니다. **[!UICONTROL 설정]** 탭에서 이름을 수정할 수 있습니다. 탭을 삭제하려면 `X` 을 클릭하십시오.

![chlimage_1-182](assets/chlimage_1-182.png)

## 메타데이터 스키마 양식 삭제 {#deleting-metadata-schema-forms}

[!DNL Experience Manager] 사용자 지정 스키마 양식만 삭제할 수 있습니다. 기본 스키마 양식/템플릿은 삭제할 수 없습니다. 그러나 이러한 양식에서 사용자 지정 변경 사항을 삭제할 수 있습니다.

양식을 삭제하려면 양식을 선택하고 **[!UICONTROL 삭제]** 아이콘을 클릭합니다.

>[!NOTE]
>
>기본 양식에 대한 사용자 지정 변경 사항을 삭제하면 메타데이터 스키마 인터페이스에 잠금 아이콘이 다시 표시되어 양식이 기본 상태로 복귀했음을 나타냅니다.

>[!NOTE]
>
>[!DNL Experience Manager] 자산에서 기본 메타데이터 스키마 양식을 삭제할 수 없습니다.

## MIME 유형에 대한 스키마 양식 {#schema-forms-for-mime-types}

[!DNL Experience Manager] Assets는 즉시 사용 가능한 다양한 MIME 유형에 대한 기본 양식을 제공합니다. 그러나 다양한 MIME 유형의 자산에 사용자 지정 양식을 추가할 수 있습니다.

### MIME 유형에 새 양식 추가 {#adding-new-forms-for-mime-types}

적절한 양식 유형으로 새 양식을 만듭니다. 예를 들어 `image/png` 하위 유형에 새 템플릿을 추가하려면 `image` 양식 아래에 양식을 만듭니다. 스키마 양식의 제목은 하위 유형 이름입니다. 이 경우 제목은 `png`입니다.

### 다양한 MIME 유형에 기존 스키마 템플릿 사용 {#using-an-existing-schema-template-for-various-mime-types}

다른 MIME 유형에 기존 템플릿을 사용할 수 있습니다. 예를 들어 MIME 유형 `image/png`의 자산에 `image/jpeg` 양식을 사용하십시오.

이 경우 CRX 저장소의 `/etc/dam/metadataeditor/mimetypemappings`에 새 노드를 만듭니다. 노드의 이름을 지정하고 다음 속성을 정의합니다.

| 이름 | 설명 | 유형 | 값 |
|---|---|---|---|
| `exposedmimetype` | 매핑할 기존 양식의 이름 | `String` | `image/jpeg` |
| `mimetypes` | `exposedmimetype` 특성에 정의된 양식을 사용하는 MIME 유형 목록입니다 | `String` | `image/png` |

[!DNL Experience Manager] 자산은 다음 MIME 유형 및 스키마 양식을 매핑합니다.

| 스키마 양식 | MIME 유형 |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| 비디오/avi | video/avi, video/msvideo, video/x-msvideo |
| 비디오/wmv | video/x-ms-wmv |
| 비디오/flv | video/x-flv |

## 메타데이터 스키마에 대한 액세스 권한 부여 {#granting-access-to-metadata-schemas}

메타데이터 스키마 기능은 관리자만 사용할 수 있습니다. 그러나 관리자는 `/conf` 폴더에 **[!UICONTROL 만들기]**, **[!UICONTROL 수정]** 및 **[!UICONTROL 삭제]** 권한을 제공하여 관리자가 아닌 사용자에게 액세스 권한을 제공할 수 있습니다.

## 폴더별 메타데이터 적용 {#applying-folder-specific-metadata}

[!DNL Experience Manager] 자산을 사용하면 메타데이터 스키마의 변형을 정의하고 특정 폴더에 적용할 수 있습니다.

예를 들어, 기본 메타데이터 스키마의 변형을 정의하고 폴더에 적용할 수 있습니다. 수정된 스키마를 적용하면 이 스키마가 폴더 내의 자산에 적용되는 원래 기본 메타데이터 스키마를 무시합니다.

이 스키마가 적용되는 폴더에 업로드된 자산만 변형 메타데이터 스키마에 정의된 수정된 메타데이터를 따릅니다.

원래 스키마가 적용되는 다른 폴더의 자산은 원래 스키마에 정의된 메타데이터를 계속 따릅니다.

자산의 메타데이터 상속은 계층 구조의 첫 번째 수준 폴더에 적용되는 스키마를 기반으로 합니다. 즉, 폴더에 하위 폴더가 없는 경우 폴더 내의 자산은 폴더에 적용된 스키마의 메타데이터를 상속합니다.

폴더에 하위 폴더가 있는 경우 하위 폴더 내의 자산은 하위 폴더 수준에서 다른 스키마가 적용되는 경우 하위 폴더 수준에서 적용된 스키마의 메타데이터를 상속합니다. 그러나 하위 폴더 수준에서 스키마 또는 동일한 스키마가 적용되지 않으면 하위 폴더 자산은 상위 폴더 수준에서 적용된 스키마의 메타데이터를 상속합니다.

1. [!DNL Experience Manager] 로고를 클릭한 다음 **[!UICONTROL 도구 > 자산 > 메타데이터 스키마]**&#x200B;로 이동합니다. **[!UICONTROL 메타데이터 스키마 Forms]** 페이지가 표시됩니다.
1. 양식 앞에 확인란을 선택합니다(예: 기본 메타데이터 양식). **[!UICONTROL 복사]** 아이콘을 클릭하거나 탭하고 사용자 지정 양식으로 저장합니다. 양식의 사용자 지정 이름(예: `my_default`)을 지정합니다. 또는 사용자 지정 양식을 만들 수 있습니다.

   ![chlimage_1-184](assets/chlimage_1-184.png)

1. **[!UICONTROL 메타데이터 스키마 Forms]** 페이지에서 `my_default` 양식을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 메타데이터 스키마 편집기]** 페이지에서 스키마 양식에 텍스트 필드를 추가합니다. 예를 들어 레이블이 **[!UICONTROL Category]**&#x200B;인 필드를 추가합니다.

   ![chlimage_1-186](assets/chlimage_1-186.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 수정된 양식은 **[!UICONTROL 메타데이터 스키마 Forms]** 페이지에 나열됩니다.
1. 도구 모음에서 **[!UICONTROL 폴더에 적용]**&#x200B;을 클릭/탭하여 사용자 지정 메타데이터를 폴더에 적용합니다.

   ![chlimage_1-187](assets/chlimage_1-187.png)

1. 수정된 스키마를 적용할 폴더를 선택한 다음 **[!UICONTROL 적용]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. 폴더에 다른 메타데이터 스키마가 적용된 경우 기존 메타데이터 스키마를 덮어쓸 것이라는 메시지가 나타납니다. **[!UICONTROL 덮어쓰기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 확인]**&#x200B;을 클릭하여 성공 메시지를 닫습니다.
1. 수정된 메타데이터 스키마를 적용한 폴더로 이동합니다.

## 필수 메타데이터 정의 {#defining-mandatory-metadata}

폴더 수준에서 필수 필드를 정의할 수 있습니다. 이 필드는 폴더에 업로드된 자산에 적용됩니다. 이전에 정의한 필수 필드에 대해 누락된 메타데이터가 있는 자산을 업로드하면 카드 보기의 자산에 누락된 메타데이터에 대한 시각적 표시가 나타납니다.

>[!NOTE]
>
>메타데이터 필드는 다른 필드의 값을 기준으로 필수로 정의할 수 있습니다. 카드 보기에서는 이러한 필수 메타데이터 필드에 대한 누락된 메타데이터에 대한 경고 메시지가 표시되지 않습니다.[!DNL Experience Manager]

1. [!DNL Experience Manager] 로고를 클릭한 다음 **[!UICONTROL 도구 > 자산 > 메타데이터 스키마]**&#x200B;로 이동합니다. **[!UICONTROL 메타데이터 스키마 Forms]** 페이지가 표시됩니다.
1. 기본 메타데이터 양식을 사용자 지정 양식으로 저장합니다. 예를 들어 `my_default`(으)로 저장합니다.

   ![chlimage_1-189](assets/chlimage_1-189.png)

1. 사용자 지정 양식을 편집합니다. 필수 필드를 추가합니다. 예를 들어 **범주** 필드를 추가하고 필드를 필수로 지정합니다.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 수정된 양식은 **[!UICONTROL 메타데이터 스키마 Forms]** 페이지에 나열됩니다. 사용자 지정 메타데이터를 폴더에 적용하려면 양식을 선택하고 도구 모음에서 **[!UICONTROL 폴더에 적용]**&#x200B;을 클릭/탭합니다.

1. 폴더로 이동하고 사용자 지정 양식에 추가한 필수 필드에 대한 메타데이터가 없는 일부 자산을 업로드합니다. 자산에 대한 카드 보기에는 필수 필드에 대해 누락된 메타데이터에 대한 메시지가 표시됩니다.

   ![chlimage_1-192](assets/chlimage_1-192.png)

1. (선택 사항) `http://[server]:[port]/system/console/components/`에 액세스합니다. 기본적으로 비활성화된 `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` 구성 요소를 구성하고 활성화하십시오. [!DNL Experience Manager] 이 자산에 대한 메타데이터의 유효성을 확인하는 빈도를 설정합니다.
이 구성은 자산의 jcr:content에 `hasValidMetadata` 속성을 추가합니다. 이 속성을 사용하면 [!DNL Experience Manager]이 검색 결과를 필터링할 수 있습니다.

>[!NOTE]
>
>예약된 확인 후 자산이 추가되면, 그 자산은 다음 예약된 확인 때까지 `hasValidMetadata` 로 플래그가 지정되지 않습니다. 자산이 중간 검색 결과에 표시되지 않습니다.

>[!CAUTION]
>
>메타데이터 유효성 검사는 리소스를 많이 사용하므로 시스템 성능에 영향을 줄 수 있습니다. 그에 따라 검사를 예약합니다. [!DNL Experience Manager] 배포에 성능 문제가 있는 경우 이 작업을 비활성화해 보십시오.
