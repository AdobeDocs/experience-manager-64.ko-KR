---
title: 중복 감지 활성화
description: AEM에서 중복 자산을 탐지할 수 있는 방법을 알아봅니다.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 4%

---

# 중복 감지 활성화 {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets에 있는 자산을 업로드하려고 하면 중복 감지 기능이 이를 중복으로 식별합니다. 중복 감지는 기본적으로 비활성화되어 있습니다. 이 기능을 활성화하려면 다음 단계를 수행하십시오.

1. 를 엽니다. **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성]** 페이지 위치 `https://[server]:[port]/system/console/configMgr`.
1. 서블릿에 대한 구성 편집 **[!UICONTROL Day CQ DAM 자산 만들기]**.
1. 을(를) 선택합니다 **[!UICONTROL 중복 검색]** 옵션을 선택하고 클릭/탭합니다. **[!UICONTROL 저장]**.

   ![서블릿에서 중복 감지 옵션을 선택합니다](assets/chlimage_1-377.png)

이제 중복 검색 기능이에서 활성화됩니다. [!DNL Experience Manager] 자산. 사용자가 AEM에 있는 자산을 업로드하려고 하면 시스템에서 충돌이 있는지 확인하고 표시합니다. 자산은 에 저장된 SHA-1 해시를 사용하여 식별됩니다 `jcr:content/metadata/dam:sha1`- 파일 이름과 관계없이 중복 자산이 검색됩니다.

>[!MORELIKETHIS]
>
>* [기존 저장소의 중복된 자산(커뮤니티 구성원의 자습서)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

