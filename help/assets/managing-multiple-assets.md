---
title: 여러 자산 및 컬렉션의 메타데이터 일괄 편집
description: 여러 자산 및 컬렉션의 메타데이터를 동시에 편집하여 일반적인 메타데이터 변경 사항을 신속하게 전파하는 방법을 살펴봅니다.
contentOwner: AG
feature: 자산 관리,메타데이터,컬렉션
role: 비즈니스 전문가
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 2%

---


# 여러 자산 및 컬렉션 관리 {#managing-multiple-assets-and-collections}

여러 자산 및 컬렉션의 메타데이터를 동시에 편집하여 일반적인 메타데이터 변경 사항을 신속하게 전파하는 방법을 살펴봅니다.

AEM(Adobe Enterprise Manager) 자산은 여러 자산의 메타데이터를 동시에 편집할 수 있으므로 일반적인 메타데이터 변경 사항을 자산에 일괄적으로 신속하게 적용할 수 있습니다. 여러 컬렉션의 메타데이터를 일괄적으로 편집할 수도 있습니다.

속성 페이지를 사용하여 여러 자산 또는 컬렉션에서 메타데이터 변경을 수행합니다.

* 메타데이터 속성을 공통 값으로 변경
* 태그 추가 또는 수정

메타데이터 속성 추가, 수정, 삭제를 포함하여 메타데이터 속성 페이지를 사용자 정의하려면 스키마 편집기를 사용합니다.

>[!NOTE]
>
>벌크 편집 방법은 폴더 또는 컬렉션에서 사용할 수 있는 자산에 대해 작동합니다. 여러 폴더에서 사용할 수 있거나 일반적인 기준과 일치하는 자산의 경우 자산 검색 결과에서 메타데이터를 일괄 업데이트할 수 있습니다.

## 여러 자산 {#editing-metadata-properties-of-multiple-assets}의 메타데이터 속성 편집

1. 자산 사용자 인터페이스에서 편집할 자산의 위치로 이동합니다.
1. 공통 속성을 편집할 자산을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭하여 선택한 자산에 대한 속성 페이지를 엽니다.
1. 다양한 탭에서 선택한 자산에 대한 메타데이터 속성을 수정합니다.
1. 특정 자산의 메타데이터를 보려면 목록에서 나머지 자산의 선택을 취소합니다. [!UICONTROL 속성] 페이지에서 일부 자산의 선택을 취소하면 해당 자산의 메타데이터가 업데이트되지 않습니다.
1. 자산에 대해 다른 메타데이터 스키마를 선택하려면 도구 모음에서 **[!UICONTROL 설정]**&#x200B;을 클릭하고 스키마를 선택합니다. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다.
1. 여러 값이 포함된 필드에 기존 메타데이터와 함께 새 메타데이터를 추가하려면 **[!UICONTROL 추가 모드]**&#x200B;를 선택합니다. 이 옵션을 선택하지 않으면 새 메타데이터가 필드에 있는 기존 메타데이터를 대체합니다. **[!UICONTROL 제출]**&#x200B;을 클릭합니다.

![메타데이터 스키마 벌크가 여러 자산에 적용됩니다.](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>단일 값 필드의 경우 **[!UICONTROL 추가 모드]**&#x200B;를 선택하더라도 새 메타데이터는 필드의 기존 값에 추가되지 않습니다.

## 벌크 메타데이터 업데이트 {#configure-limit-for-bulk-metadata-update}에 대한 제한 구성

AEM은 DOS와 같은 상황을 방지하기 위해 Sling 요청에서 지원되는 매개 변수의 수를 제한합니다. 한 번에 많은 자산의 메타데이터를 업데이트할 때 한도에 도달해도 메타데이터가 더 많은 자산에 대해 업데이트되지 않습니다. AEM은 로그에 다음 경고를 생성합니다.

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

제한을 변경하려면 [!UICONTROL Apache Sling 요청 매개 변수 처리] OSGi 구성에서 **[!UICONTROL 도구 > 작업 > 웹 콘솔]**&#x200B;에 액세스하고 [!UICONTROL 최대 POST 매개 변수]의 값을 변경합니다.

>[!MORELIKETHIS]
>
>* [여러 컬렉션의 메타데이터를 일괄 편집](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)