---
title: 서신 관리 솔루션 구성
seo-title: Configuring a Correspondence Management solution
description: 작성자 인스턴스 버전 복원에 대한 작성자 인스턴스 URL을 정의하고 공개 인스턴스 활성화 관리자를 위한 게시 인스턴스 URL을 정의하는 방법을 알아봅니다.
seo-description: Learn how to define an author instance URL for the author instance version restore and define the Publish instance URL for public instance activation manager.
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
exl-id: a062957d-a526-4c4b-bbc5-0cda8ab007a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 3%

---

# 서신 관리 솔루션 구성 {#configuring-a-correspondence-management-solution}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## VersionRestoreManagerImpl에 대한 작성자 인스턴스 URL 정의 {#defining-author-instance-url-for-versionrestoremanagerimpl}

작성자 인스턴스 버전 복원용 작성자 인스턴스 URL을 정의하려면 다음 단계를 사용하십시오.

1. 이동 *https://:&lt;publishhost>:&lt;publishport>/lc/system/console/configMgr*. OSGi Management Console 사용자 자격 증명으로 로그인합니다. 기본 자격 증명은 관리자/관리자입니다.
1. 을(를) 찾아 클릭합니다. **[!UICONTROL 편집]** 아이콘 옆에 있는 를 클릭합니다. **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]** 설정
1. 에서 **[!UICONTROL VersionRestoreManager 작성자 URL]** 필드에서 VersionRestoreManager의 작성자 인스턴스의 URL을 지정합니다.

   **URL 문자열**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >로드 밸런서에서 앞에 작성자 인스턴스(클러스터됨)가 여러 개 있는 경우, 로드 밸런서에서 로드 밸런서에 대한 URL을 지정합니다 **[!UICONTROL VersionRestoreManager 작성자 URL]** 필드.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## ActivationManagerImpl(공용 인스턴스 활성화 관리자)에 대한 게시 인스턴스 URL 정의 {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

다음 단계에 따라 공용 인스턴스 활성화 관리자에 대한 게시 인스턴스 URL을 정의합니다.

1. 이동 *https://:&lt;authorhost>:&lt;authorport>/lc/system/console/configMgr*. OSGi Management Console 사용자 자격 증명으로 로그인합니다. 기본 자격 증명은 관리자/관리자입니다.
1. 을(를) 찾아 클릭합니다. **[!UICONTROL 편집]** 아이콘 옆에 있는 를 클릭합니다. **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** 설정
1. 에서 **[!UICONTROL ActivationManager 게시 URL]** 필드에서 게시 인스턴스 ActivationManager에 액세스할 URL을 지정합니다. 다음 URL을 제공할 수 있습니다.

   * **로드 밸런서 URL(권장)**: 게시 팜 앞에 로드 밸런서 역할을 하는 웹 서버가 있는 경우(클러스터되지 않은 여러 게시 인스턴스) 로드 밸런서 URL을 제공합니다.
   * **게시 인스턴스 URL**: 모든 게시 인스턴스 URL 제공. 단일 게시 인스턴스가 있거나 제한 사항으로 인해 게시 팜을 프론트하는 웹 서버에 작성자 환경에서 액세스할 수 없습니다. 지정된 게시 인스턴스가 다운된 경우 작성자 측에서 처리할 대체 메커니즘이 있습니다.
   * **URL 문자열**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

서신 관리 구성에 대한 자세한 내용은 [서신 관리 구성 속성](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).
