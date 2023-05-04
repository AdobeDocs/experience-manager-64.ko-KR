---
title: 인증서 취소 목록 관리
seo-title: Managing certificate revocationlists
description: 인증서 해지 목록을 관리하는 방법을 알아봅니다.
seo-description: Learn how to manage certificate revocation lists.
uuid: d8c4b64c-a273-4f5d-8b71-f6ea455c0f0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9744cc2d-5e6b-4341-9270-43d479bdca04
exl-id: 45741270-2d57-4d6d-92ef-65b6c1deb448
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 5%

---

# 인증서 취소 목록 관리{#managing-certificate-revocationlists}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Trust Store Management를 사용하여 CRL(인증서 해지 목록)을 가져오기, 편집 및 삭제할 수 있습니다. Base64 및 DER 인코딩 인증서 해지 목록이 지원됩니다.

## CRL 가져오기 {#import-a-crl}

1. 관리 콘솔에서 설정 > Trust Store Management > 인증서 해지 목록을 클릭한 다음 가져오기를 클릭합니다.
1. 별칭 상자에 CRL의 식별자를 입력합니다.
1. 찾아보기 를 클릭하여 CRL을 찾은 다음 확인을 누릅니다.

## CRL 내보내기 {#export-a-crl}

1. 관리 콘솔에서 설정 > Trust Store Management > 인증서 해지 목록을 클릭합니다.
1. 내보낼 CRL의 별칭 이름을 누른 다음 내보내기를 누릅니다.
1. 지침에 따라 CRL을 내보냅니다. CRL은 Base64 인코딩에서 내보내집니다.
1. 확인을 클릭합니다.

## CRL 삭제 {#delete-a-crl}

1. 관리 콘솔에서 설정 > Trust Store Management > 인증서 해지 목록을 클릭합니다.
1. 삭제할 CRL에 대한 확인란을 선택하고 삭제를 누른 다음 확인을 누릅니다.
