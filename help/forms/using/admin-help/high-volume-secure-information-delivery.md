---
title: 대용량 보안 정보 제공
seo-title: High-volume secure information delivery
description: 문서 보안은 대량 생산 환경에서 문서가 아닌 사용자에게 라이센스를 연결할 수 있도록 지원합니다.
seo-description: Document security supports the association of licenses to users, rather than to the documents in mass production environments.
uuid: 9747d283-506c-434e-9850-e50b95290cc8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b76d7d93-23a5-4c08-81f5-a56267b1556a
feature: Document Security
exl-id: 78fc7c4a-a634-4628-927a-c9622bdc13fc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 2%

---

# 대용량 보안 정보 제공 {#high-volume-secure-information-delivery}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

통신 회사에 대해 매월 고정된 청구서를 생성하는 것과 같은 대량 생산 환경에서 각 문서에 맞는 라이센스를 생성하는 것은 자원 집약적인 프로세스가 될 수 있습니다. 이러한 경우 문서 보안은 문서가 아닌 사용자에 대한 라이센스 연결을 지원합니다. 사용자에 대해 생성된 라이센스는 해당 사용자에 대해 보호되는 모든 문서에 사용됩니다.

이 접근 방식의 한 가지 이점은 문서 보안 데이터베이스 크기가 사용자 수가 아닌 문서와 함께 선형적으로 증가하지 않는다는 것입니다. 또한 사용자에 대해 라이센스를 한 번만 만들어야 하기 때문에 이러한 정책을 통해 문서를 이후 보호할 수 있습니다. 오프라인 액세스, 문서 만료 및 취소와 같은 기능이 이러한 모든 문서에 대해 지원됩니다.

문서 보안은 추상 정책도 지원합니다. 추상 정책은 문서 보안 설정 및 사용 권한과 같은 모든 정책 속성을 포함하지만 주체 목록을 포함하지 않는 정책 템플릿입니다. 관리자는 문서에 액세스해야 하는 서로 다른 주도자와 함께 추상 정책에서 원하는 개수의 정책을 만들 수 있습니다. 추상 정책에 대한 변경 사항은 추상 정책으로부터 생성된 실제 정책에 영향을 주지 않습니다.

통신 회사에 대한 월별 청구서 생성의 경우 추상 정책을 생성하고 사용자를 생성한 다음 각 사용자에 대한 고유 라이센스를 생성합니다. 라이센스는 나중에 각 사용자의 문서에 적용됩니다.

추상 정책 만들기는 문서 보안 Java SDK를 통해서만 지원됩니다. 그러나 문서 보안 웹 페이지에서 추상 정책으로 생성한 정책을 관리할 수 있습니다. 이 방법을 사용하여 작성된 정책은 문서 보안 웹 페이지에서 만든 정책과 동일합니다.

자세한 내용은 [AEM 양식을 사용한 프로그래밍](https://www.adobe.com/go/learn_aemforms_programming_63) 추가 정보.
