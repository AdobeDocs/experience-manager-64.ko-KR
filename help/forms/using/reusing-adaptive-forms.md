---
title: 적응형 양식 재사용
seo-title: Reusing adaptive forms
description: 기존 적응형 양식을 다시 사용하여 새 적응형 양식을 만들 수 있습니다.
seo-description: You can reuse an existing adaptive form to create new adaptive forms.
uuid: f1d0fb70-e255-4dd9-8e6d-fd65eaf2e81a
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ef564750-f107-41cb-887e-fc6d22b7d32e
feature: Adaptive Forms
exl-id: 9393fe94-002a-497b-9579-d6ad3bb3973e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 1%

---

# 적응형 양식 재사용 {#reusing-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

기존 적응형 양식의 속성 중 일부를 사용하여 새 양식을 만들려면 복사-붙여넣기 기능을 사용하면 됩니다. 또한 원하는 폴더 경로에 새 적응형 양식을 붙여넣을 수 있습니다. 모든 메타데이터 속성이 복제되고 XFA 및 XSD 기반 적응형 양식의 XFA 및 XSD도 복사됩니다.

>[!NOTE]
>
>상태 및 검토 세부 정보는 복사되지 않습니다. 예를 들어 적응형 양식이 게시되어 있는 경우 붙여넣은 적응형 양식이 게시 취소 상태입니다. 마찬가지로, 복사된 자산이 검토 중인 경우 붙여넣은 자산은 동일한 검토 아래에 있지 않습니다.

### 적응형 양식 복사 {#copy-an-adaptive-form}

다음 방법 중 하나를 사용하여 적응형 양식을 복사합니다.

1. 복사 를 클릭합니다 ![aem6forms_copy](assets/aem6forms_copy.png) 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.

   >[!NOTE]
   >
   >빠른 작업은 마우스로 가리키면 축소판 위에 표시되는 작업 항목입니다.

1. 적응형 양식을 선택합니다. 선택 프로세스는 서로 다른 보기에 대해 다릅니다.

   카드 보기인 경우 선택 항목을 클릭하여 선택 모드로 이동합니다 ![aem6forms_check-circle](assets/aem6forms_check-circle.png) 아이콘을 클릭하고 복사할 모든 적응형 양식을 클릭합니다.

   목록 보기에 있는 경우 모든 적응형 양식의 확인란을 클릭하여 선택합니다.

   >[!NOTE]
   >
   >복사-붙여넣기 기능은 적응형 양식에만 지원되며 선택한 모든 자산이 동일한 폴더에 있어야 하므로 선택한 모든 자산은 적응형 양식이어야 합니다.

   자산을 선택한 후 복사를 클릭합니다 ![aem6forms_copy](assets/aem6forms_copy.png) 도구 모음에 있는 아이콘을 사용하여 선택한 적응형 양식을 복사합니다.

### 적응형 양식 붙여넣기 {#paste-an-adaptive-form}

복사 작업을 클릭하면 선택 모드가 자동으로 종료되고 붙여넣기가 수행됩니다 ![aem6forms_paste](assets/aem6forms_paste.png) 아이콘 표시 이제 원하는 폴더 경로로 이동하고 붙여넣기를 클릭합니다 ![aem6forms_paste](assets/aem6forms_paste.png) 아이콘을 클릭하여 복사한 적응형 양식을 붙여넣습니다.

동일한 폴더 또는 동일한 노드 이름(CRX 저장소에 저장됨)을 사용하는 다른 파일을 이 대상 폴더에 붙여 넣는 경우 1이 접미사에 추가됩니다(예: myaf1이 myaf1이 되고 myaf1이 같은 위치에 있으면 myaf2가 됩니다.) 다른 모든 속성은 원래의 적응형 양식과 동일하게 유지됩니다.

붙여넣기를 클릭한 후 ![aem6forms_paste](assets/aem6forms_paste.png) 아이콘, 다시 숨겨집니다. 한 번에 한 번만 붙여넣을 수 있습니다. 동일한 자산의 사본을 다시 만들려면 다시 복사합니다.

### 새로운 적응형 양식의 내용 변경 {#change-contents-of-new-adaptive-form}

붙여넣은 적응형 양식의 콘텐츠는 다음 방법을 사용하여 변경하여 복사한 양식과 다르게 만들 수 있습니다.

1. **메타데이터 속성 변경:**

   적응형 양식의 메타데이터 속성(예: 제목 및 설명)을 변경할 수 있습니다. 메타데이터 속성 및 메타데이터 속성을 변경하는 방법에 대한 자세한 내용은 [양식 메타데이터 관리](/help/forms/using/manage-form-metadata.md)

1. **XFA/XSD 기반 응용 Forms에 대한 XFA/XSD 변경:**

   적응형 양식에 사용되는 XFA/XSD를 변경할 수 있습니다. 이러한 적응형 양식을 변경하는 방법을 알려면 다음을 참조하십시오 [양식 메타데이터 관리](/help/forms/using/manage-form-metadata.md)

1. **재게시:**

   붙여넣은 자산은 복사한 자산과 다릅니다. 새 자산으로 게시하여 최종 사용자가 사용할 수 있도록 할 수 있습니다. 자산을 게시하는 방법에 대한 자세한 내용은 [양식 게시 및 게시 취소](/help/forms/using/publishing-unpublishing-forms.md)
