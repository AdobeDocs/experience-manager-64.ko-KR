---
title: 기존 도메인 편집 및 변환
seo-title: Editing and converting existing domains
description: 도메인 관리 페이지에서 기존 도메인의 설정을 변경하는 방법을 배웁니다. 기존 엔터프라이즈 도메인을 하이브리드 도메인으로 변환하거나 그 반대로 변환합니다.
seo-description: Learn how to change the settings for existing domains from the Domain Management page. Convert an existing enterprise domain to a hybrid domain or vice versa.
uuid: 4cc9547e-b4ec-4588-b1cf-18720f06149a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 44dec184-3ef7-4ba6-a87f-ad171d3cb188
exl-id: 07ca7715-f7b3-40e0-95bc-e05f0662ed08
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 2%

---

# 기존 도메인 편집 및 변환{#editing-and-converting-existing-domains}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

도메인 관리 페이지에서 기존 도메인에 대한 설정을 변경할 수 있습니다. 기존 엔터프라이즈 도메인을 하이브리드 도메인으로 변환할 수도 있습니다.

## 기존 도메인 편집 {#edit-an-existing-domain}

1. 관리 콘솔에서 설정 > 사용자 관리 > 도메인 관리 를 클릭합니다.
1. 편집할 도메인의 이름을 클릭합니다.
1. 도메인 이름을 변경하려면 이름 상자에서 텍스트를 변경합니다.
1. Enterprise 또는 hybrid 도메인에 대한 인증 정보를 변경하려면 페이지 하단에서 해당 인증 이름을 클릭합니다. [인증 편집] 페이지에서 필요에 따라 설정을 변경합니다. (자세한 내용은 [인증 설정](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings))
1. 엔터프라이즈 도메인의 디렉토리 정보를 변경하려면 페이지 하단에 있는 해당 디렉토리 이름을 누릅니다. [디렉토리 편집] 페이지에서 필요에 따라 설정을 변경합니다. (자세한 내용은 [디렉토리 또는 사용자 지정 SPI 추가](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis))
1. 변경을 완료하면 확인을 클릭합니다.

## 엔터프라이즈 도메인을 하이브리드 도메인으로 변환 {#convert-an-enterprise-domain-to-a-hybrid-domain}

1. 관리 콘솔에서 설정 > 사용자 관리 > 도메인 관리 를 클릭합니다.
1. 변환할 엔터프라이즈 도메인의 이름을 클릭합니다.
1. 하이브리드 도메인으로 변환 을 클릭합니다.
1. 사용자 및 그룹 데이터 및 사용자 인증과 관련된 정보를 검토하고 확인을 클릭합니다.
1. 하이브리드 도메인의 설정을 편집하고 확인을 클릭합니다.

>[!NOTE]
>
>변환하려는 엔터프라이즈 도메인에 디렉토리 설정이 없는 경우 LDAP 인증 설정이 손실됩니다.

## 하이브리드 도메인을 엔터프라이즈 도메인으로 변환 {#convert-a-hybrid-domain-to-an-enterprise-domain}

1. 관리 콘솔에서 설정 > 사용자 관리 > 도메인 관리 를 클릭합니다.
1. 변환할 하이브리드 도메인의 이름을 클릭합니다.
1. Enterprise 도메인으로 변환을 클릭합니다.
1. 사용자 및 그룹 데이터 및 사용자 인증과 관련된 정보를 검토하고 확인을 클릭합니다.
1. 디렉토리 추가 를 클릭하고 필요한 디렉토리 정보를 구성합니다. (자세한 내용은 [디렉토리 또는 사용자 지정 SPI 추가](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis))
