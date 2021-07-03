---
title: 중복 감지 활성화
description: AEM에서 중복 자산을 탐지할 수 있는 방법을 알아봅니다.
contentOwner: AG
feature: 자산 관리,자산 보고서
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# 중복 감지 활성화 {#enabling-duplicate-detection}

Adobe Experience Manager (AEM) Assets에 있는 자산을 업로드하려고 하면 중복 감지 기능이 이를 중복으로 식별합니다. 중복 감지는 기본적으로 비활성화되어 있습니다. 이 기능을 활성화하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성]** 페이지를 `https://[server]:[port]/system/console/configMgr`에서 엽니다.
1. 서블릿 **[!UICONTROL Day CQ DAM 자산 만들기]**&#x200B;에 대한 구성을 편집합니다.
1. **[!UICONTROL 중복 검색]** 옵션을 선택하고 **[!UICONTROL 저장]**&#x200B;을 클릭/탭합니다.

   ![서블릿에서 중복 감지 옵션을 선택합니다](assets/chlimage_1-377.png)

이제 AEM Assets에서 중복 감지 기능이 활성화됩니다. 사용자가 AEM에 있는 자산을 업로드하려고 하면 시스템에서 충돌이 있는지 확인하고 표시합니다. 자산은 `jcr:content/metadata/dam:sha1`에 저장된 SHA-1 해시를 사용하여 식별됩니다. 즉, 파일 이름과 관계없이 중복 자산이 검색됩니다.

>[!MORELIKETHIS]
>
>* [기존 저장소의 중복된 자산(커뮤니티 구성원의 자습서)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

