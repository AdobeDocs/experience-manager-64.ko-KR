---
title: AEM DS 설정 구성
seo-title: Configuring AEM DS settings
description: 양식을 제출하기 전에 처리 서버 URL을 지정해야 합니다.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%

---

# AEM DS 설정 구성 {#configuring-aem-ds-settings}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

이 문서에서는 구성 방법을 설명합니다 **AEM DS 설정 서비스**. 이 설정은 다음과 같이 여러 시나리오에서 사용할 수 있습니다.

* 서신 관리

   * AEM Forms 워크플로우 구성
   * 양식 포털을 사용하여 초안/제출 원격 저장

* 게시 인스턴스에서 적응형 양식을 제출할 때 사례에 대한 적응형 양식에서

다음은 를 구성하는 단계입니다 **[!UICONTROL AEM DS 설정]**:

1. URL을 사용하여 게시 인스턴스에서 구성 관리자를 엽니다.

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. 에서 **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성]** 창에서 을(를) 찾아 클릭합니다. **[!UICONTROL AEM DS 설정]** 선택 사항입니다.

   ![ds_settings](assets/ds_settings.png)

1. 다음 **[!UICONTROL AEM DS 설정 서비스]** 창에는 AEM DS 구성 요소에 대한 일반 구성 설정이 표시됩니다.

   ![ds_settings_1](assets/ds_settings_1.png)

1. 각 필드에 다음 정보를 추가합니다.

   **[!UICONTROL 처리 서버 URL]**: 처리 서버는 Forms 또는 AEM 워크플로우를 트리거해야 하는 서버입니다. AEM 작성자 인스턴스의 URL 또는 다른 서버 URL(즉, http:// localhost:port/)과 같을 수 있습니다.

   **[!UICONTROL 처리 서버 사용자 이름]**: 워크플로우 사용자의 사용자 이름 [사용되는 서버 URL을 기반으로 합니다]

   **[!UICONTROL 처리 서버 암호]**: 워크플로우 사용자 암호

   >[!NOTE]
   >
   >* Forms 또는 AEM 워크플로우를 사용하는 동안 게시 서버에서 제출하기 전에 DS 설정 서비스를 구성해야 합니다. 그렇지 않으면 양식 제출이 실패합니다.

