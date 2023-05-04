---
title: 적응형 양식 캐시 구성
seo-title: Configure adaptive forms cache
description: 적응형 양식 캐시는 적응형 양식 및 문서용으로 특별히 설계되었습니다. 클라이언트에서 적응형 양식 또는 문서를 렌더링하는 데 필요한 시간을 줄이기 위해 적응형 양식 및 적응형 문서를 캐시합니다.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 3%

---

# 적응형 양식 캐시 구성 {#configure-adaptive-forms-cache}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

캐시는 데이터 액세스 시간을 단축하고 지연을 줄이며 입출력 속도를 향상시키는 메커니즘입니다. 적응형 양식 캐시는 사전 채워진 데이터를 저장하지 않고 적응형 양식의 HTML 콘텐츠과 JSON 구조만 저장합니다. 클라이언트에서 적응형 양식 또는 문서를 렌더링하는 데 필요한 시간을 줄이는 데 도움이 됩니다. 적응형 양식을 위해 특별히 고안되었으며 적응형 문서도 지원합니다.

>[!NOTE]
>
>적응형 양식 캐시를 사용하는 경우 AEM Dispatcher를 사용하여 적응형 양식 또는 문서의 클라이언트 라이브러리(CSS 및 JavaScript)를 캐시합니다.

>[!NOTE]
>
>사용자 지정 구성 요소를 개발하는 동안 개발에 사용되는 서버에서 적응형 양식 캐시를 사용하지 않도록 설정하십시오.

## 캐시 구성 {#configure-the-cache}

적응형 양식 캐시를 구성하려면 다음 단계를 수행하십시오.

1. 의 AEM 웹 콘솔 구성 관리자로 이동합니다. `https://[server]:[port]/system/console/configMgr`.
1. 클릭 **적응형 양식 및 대화형 통신 웹 채널 구성** 구성 값을 편집하려면 다음을 수행하십시오.
1. 구성 값 편집 대화 상자에서 AEM Forms 서버의 인스턴스가 캐싱할 수 있는 최대 양식 또는 문서 수를 **적응형 Forms 수** 필드. 기본값은 100입니다.

   >[!NOTE]
   >
   >캐시를 비활성화하려면 [적응형 Forms 수] 필드의 값을 **0**. 캐시 구성을 비활성화하거나 변경하면 캐시가 재설정되고 모든 양식 및 문서가 캐시에서 제거됩니다.

   ![적응형 양식 HTML 캐시를 위한 구성 대화 상자](assets/cache-configuration-edit.png)

1. 클릭 **저장** 구성을 저장합니다.
