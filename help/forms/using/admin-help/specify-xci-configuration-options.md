---
title: XCI 구성 옵션 지정
seo-title: XCI 구성 옵션 지정
description: XCI 구성 옵션을 지정하는 방법을 알아봅니다.
seo-description: XCI 구성 옵션을 지정하는 방법을 알아봅니다.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 1%

---

# XCI 구성 옵션 {#specify-xci-configuration-options} 지정

출력을 사용하면 렌더링에 사용하는 사용자 지정 XCI 파일을 지정할 수 있습니다. ([출력](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output)에 대한 파일 위치 지정 을 참조하십시오.) 기본적으로 출력 은 다음을 포함하여 XCI 파일에 지정된 옵션 중 일부를 무시합니다.

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

위에 나열된 옵션에 대한 무시를 취소하는 옵션을 선택할 수 있습니다. 이 경우 출력에서는 사용자 지정 XCI 파일에 지정된 값을 사용합니다.

1. 관리 콘솔에서 서비스 > 출력을 클릭합니다.
1. 시스템 기본 XCI 옵션 사용 확인란을 선택하거나 선택 취소합니다. 이 옵션을 선택하면 Output에서 패킷, 생성자, 생성자 및 compressObjectStream 설정에 기본값을 사용합니다. 이 옵션을 선택 취소하면 출력에서는 사용자 지정 XCI 파일에 지정된 값을 사용합니다.
1. 저장을 클릭합니다.
