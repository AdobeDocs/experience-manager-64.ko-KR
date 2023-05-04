---
title: HTML5 양식에 대한 첨부 파일 활성화
seo-title: Enabling attachments for an HTML5 form
description: 기본적으로 HTML5 양식에 대한 첨부 파일 지원은 비활성화됩니다.
seo-description: By default, the attachment support for HTML5 forms is disabled.
uuid: 2c62ac3e-4b27-46c7-a61d-a805fb5d26fb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: Mobile Forms
exl-id: 82a843c4-5cb2-4f5e-ad4d-cf2e9ea6cdb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 2%

---

# HTML5 양식에 대한 첨부 파일 활성화 {#enabling-attachments-for-an-html-form}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

HTML5 양식을 사용하여 첨부 파일을 업로드, 미리 보기 및 제출할 수 있습니다. 기본적으로 첨부 파일 지원은 비활성화됩니다. 첨부 지원을 사용하려면

1. 만들기 [사용자 지정 프로필](/help/forms/using/custom-profile.md) 다중 선택 문자열 속성 사용 `mfAttachmentOptions`.
1. 사용자 지정 프로필에서 속성을 지정합니다 `fileSizeLimit`, `multiSelect`, 및 `buttonTex`첨부 파일 위젯의 옵션을 구성하려면 다음을 수행합니다. 필요에 따라 더 많은 사용자 지정 속성을 지정할 수도 있습니다.

1. 사용자 지정 프로필에서 다음 구성을 사용하십시오.

   * **multiSelect** -> true 또는 false(기본적으로 true)
   * **fileSizeLimit** -> value_in_mb(약 5)(기본적으로 2MB)
   * **buttonText** -> 팝업 창의 단추 텍스트(기본적으로 &quot;첨부&quot;)
   * **동의** -> 허용되는 파일 형식(&quot;audio/&amp;ast;, 비디오/&amp;ast;, 이미지/&amp;ast;, text/&amp;ast;, .pdf&quot; 기본적으로)

   >[!NOTE]
   >
   >Microsoft Internet Explorer 9에서 사용자는 지정된 제한보다 큰 파일을 첨부할 수 있습니다. 알려진 문제입니다.

1. 를 사용하십시오 [메타데이터 편집기](/help/forms/using/manage-form-metadata.md) HTML 5 양식에 대해 위에서 만든 사용자 지정 프로필을 선택하기 위해.
1. 사용자 지정 프로필로 양식 템플릿을 렌더링하고 첨부 파일 아이콘이 양식 도구 모음에 표시됩니다.

   >[!NOTE]
   >
   >곧바로 사용할 수 있는 양식 포털은 초안 및 첨부 파일 기능이 활성화된 사용자 지정 프로필을 제공합니다. 에 대한 자세한 정보 **초안으로 저장** 프로필 [HTML5 양식을 초안으로 저장](/help/forms/using/saving-html5-form-draft.md).

1. 첨부 아이콘 을 클릭하면 첨부 선택 대화 상자가 나타납니다. 첨부 파일을 찾아 선택하고 을(를) 클릭합니다 **첨부**.

   >[!NOTE]
   >
   >첨부 파일을 미리 보려면 첨부 파일 이름을 클릭합니다.

   >[!NOTE]
   >
   >익명 사용자는 파일 미리 보기 옵션을 사용할 수 없습니다.

## 첨부 파일 제출 형식 {#attachment-submission-format}

첨부 파일이 활성화되면 HTML5 양식이 다중 부분 데이터를 제출합니다. 다중 부분 제출 데이터에는 두 부분이 있습니다 **dataXml** 및 **첨부 파일**.

>[!NOTE]
>
>이전 버전과의 호환성을 위해, `mfAllowAttachments`옵션이 꺼져 있으면 HTML5 forms에서 다중 부분 데이터를 보내지 않습니다. 에서는 간단한 데이터 xml을 **응용 프로그램/xml** 형식 지정

mfAllowAttachments 플래그가 설정되어 있으면 [서비스 프록시 서비스 제출](/help/forms/using/service-proxy.md) 또한 dataXml 및 첨부 파일이 있는 여러 부분 데이터를 게시합니다.
