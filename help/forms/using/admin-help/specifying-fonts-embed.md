---
title: 포함할 글꼴 지정
seo-title: Specifying fonts to embed
description: 포함할 글꼴을 지정하는 방법을 알아봅니다.
seo-description: Learn how to specify fonts to embed.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
exl-id: 0bde7192-9d21-40b4-9164-314c9a30153b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 3%

---

# 포함할 글꼴 지정 {#specifying-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Forms 서비스에서 생성하는 양식과 함께 항상 포함되거나 포함되지 않는 글꼴을 지정할 수 있습니다. 글꼴을 포함하면 양식의 파일 크기가 늘어납니다. 사용자가 시스템에 거의 사용하지 않는 비정상적인 글꼴을 포함합니다. 일반적으로 설치한 일반 글꼴은 포함하지 마십시오.

>[!NOTE]
>
>Forms에 대해 사용자 지정 XCI 파일을 지정한 경우 XCI 파일의 포함 글꼴 옵션이 이러한 설정을 무시합니다. (자세한 내용은 [Forms 위치 구성](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms))

1. 관리 콘솔에서 **[!UICONTROL 서비스 > Forms]**.
1. 아래 **[!UICONTROL 글꼴 포함 설정]**&#x200B;에서 **[!UICONTROL 항상 글꼴 포함]** 상자에 포함할 글꼴의 이름을 쉼표로 구분하여 입력합니다. 지정하는 글꼴은 양식에서 사용하는 경우에만 생성된 양식에 포함됩니다. 서비스에 전달된 XCI 파일에서 포함 글꼴 옵션을 설정한 경우 PDF에 사용된 모든 글꼴이 항상 포함되므로 이 설정은 무시됩니다.
1. 에서 **[!UICONTROL 글꼴 포함 안 함]** 상자에 포함할 글꼴의 이름을 쉼표로 구분하여 입력합니다. 지정한 글꼴은 생성된 PDF에서 사용되더라도 PDF에 포함되지 않습니다. 서비스에 전달된 XCI 파일에서 포함 글꼴 옵션이 꺼져 있는 경우 PDF에 사용된 글꼴이 포함되지 않으므로 이 설정은 무시됩니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
