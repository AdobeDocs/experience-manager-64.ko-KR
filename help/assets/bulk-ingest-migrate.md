---
title: 벌크 자산 마이그레이션용 기능 팩 18912 설치
seo-title: 벌크 자산 마이그레이션용 기능 팩 18912 설치
description: 기능 팩 18912을 사용하면 FTP를 통해 자산을 벌크하거나 Dynamic Media Classic에서 AEM의 Dynamic Media으로 자산을 마이그레이션할 수 있습니다. 이 선택적 기능 팩은 Adobe 지원에서 사용할 수 있습니다.
seo-description: 기능 팩 18912을 사용하면 FTP를 통해 자산을 벌크하거나 Dynamic Media Classic에서 AEM의 Dynamic Media으로 자산을 마이그레이션할 수 있습니다. 이 선택적 기능 팩은 Adobe 지원에서 사용할 수 있습니다.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: 구성
role: Administrator,Business Practitioner
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 4%

---

# 벌크 자산 마이그레이션용 기능 팩 18912 설치 {#installing-feature-pack}

기능 팩 18912 설치은 _선택 사항_&#x200B;입니다.

기능 팩 18912을 사용하면 FTP를 통해 AEM에서 Dynamic Media - Scene 7 모드로 직접 자산을 일괄 수집하거나, Dynamic Media Classic에서 AEM의 Dynamic Media - Scene7 모드로 자산을 마이그레이션할 수 있습니다. 기능 팩은 [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)에서 사용할 수 있습니다.

>[!NOTE]
>
>기능 팩을 사용하여 자산을 Dynamic Media Classic에서 Dynamic Media - Scene 7 모드로 직접 마이그레이션하거나 AEM Classic의 FTP 기능을 사용하여 자산을 벌크로 마이그레이션하는 것이 가능하지만, Adobe은 관련된 복잡성으로 인해 *이 아닌*&#x200B;을 추천합니다.
>
>이와 같은 마이그레이션 기능 팩은 *만 [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)을 통해 마이그레이션 프로젝트의 일부로 지원됩니다.*

이 기능 팩을 설치하려면 먼저 서비스 사용자를 만들고 해당 정보를 Adobe에 제공해야 합니다.

[Dynamic Media 구성 - Scene7 모드](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)도 참조하십시오.

**벌크 자산 마이그레이션용 기능 팩 18912을 설치하려면 다음을 수행하십시오**.

1. AEM 인스턴스에서 **[!UICONTROL 도구 > 보안 > 사용자 > 사용자 만들기]**&#x200B;로 이동합니다. 이 서비스 사용자는 `/content/dam`에 대한 읽기/쓰기 권한이 있어야 합니다.
1. **[!UICONTROL ID]** 및 **[!UICONTROL 암호]** 필드에 사용자 이름과 암호를 입력합니다.예: `FTP User` 이 이름은 자산을 만든 사용자로 타임라인에 나타납니다. 자산이 FTP에서 업로드되면 자산이 FTP 서버에 업로드되면 자산이 만들어지고 AEM으로 푸시되는 것으로 간주됩니다.
1. 기능 팩 18912에 대한 액세스를 요청하려면 [Experience Manager에 대한 엔터프라이즈 지원 Adobe](https://helpx.adobe.com/kr/contact/enterprise-support.ec.html)에 문의하십시오. 지원에 문의할 때 다음 정보가 필요할 수 있습니다.

   * 작성자 인스턴스의 서버 IP 주소(기본적으로 포트 번호는 4502)입니다.
   * 이전 단계의 AEM 서비스 사용자 이름 및 암호입니다.

1. AEM용 Adobe 엔터프라이즈 지원 은 FTP 자격 증명과 기능 팩 18912에 대한 액세스 권한을 제공합니다.

1. 기능 팩 18912을 받으면 설치합니다.

   AEM에서 소프트웨어 배포 및 패키지 사용에 대한 자세한 내용은 [패키지 사용 방법](/help/sites-administering/package-manager.md)을 참조하십시오.
