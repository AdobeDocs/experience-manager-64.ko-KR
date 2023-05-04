---
title: 원격 끝점 구성
seo-title: Configuring Remoting endpoints
description: 원격 끝점을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---

# 원격 끝점 구성 {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

원격 끝점을 사용하면 Flex으로 빌드된 응용 프로그램이 AEM Forms에서 사용되지 않는 AEM Forms Remoting을 사용하여 서비스를 호출할 수 있습니다. 활성화된 각 서비스에 대해 원격 끝점이 자동으로 만들어집니다. 종단점과 동일한 이름을 갖는 Flex 대상이 생성되며 Flex 클라이언트는 해당 대상을 가리키는 원격 개체를 만들어 관련 서비스에서 작업을 호출할 수 있습니다.

## 원격 끝점 설정 {#remoting-endpoint-settings}

**Flex 클라이언트 인증 방법:** 호출된 서비스가 보안된 경우 서버가 클라이언트로 다시 보내는 응답 유형을 결정하고, 호출된 작업은 익명 호출을 지원하지 않으며, 클라이언트가 아무 자격 증명도 없거나 잘못된 자격 증명을 전달합니다.
