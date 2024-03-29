---
title: 문서 보안 서비스
seo-title: Document security offerings
description: AEM Document Security의 다양한 도구 및 기능에 대해 알아봅니다
seo-description: Learn about various tools and features of AEM Document Security
uuid: b9417ca7-ddfb-46d0-a5b7-2f39ee90b9dd
contentOwner: khsingh
geptopics: SG_AEMFORMS/categories/working_with_document_security
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8e7a8481-b8cd-4f2b-b9d2-7a8132f1d3f6
feature: Document Security
exl-id: 18ebc041-0660-4595-bc96-2039474f91fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 1%

---

# 문서 보안 서비스 {#document-security-offerings}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Forms 문서 보안을 사용하면 인증된 사용자만 문서를 사용할 수 있습니다. 문서 보안을 사용하면 지원되는 형식으로 저장한 정보를 안전하게 배포할 수 있습니다. 지원되는 파일 형식에는 Adobe Portable Document Format(PDF) 및 Microsoft Word, Excel 및 PowerPoint 파일이 포함됩니다.

정책을 사용하여 문서를 보호할 수 있습니다. 정책에 지정하는 기밀 설정은 수신자가 정책을 적용할 문서를 사용할 수 있는 방법을 결정합니다. 예를 들어 수신자가 텍스트를 인쇄하거나 복사할지, 텍스트를 편집할지, 보호된 문서에 서명 및 주석을 추가할 수 있는지를 지정할 수 있습니다.

정책은 Document Security 서버에 저장됩니다. 클라이언트 응용 프로그램을 통해 문서에 정책을 적용합니다. 문서에 정책을 적용하면 정책에 지정된 기밀 설정이 문서에 포함된 정보를 보호합니다. 정책에 의해 권한이 부여된 수신자에게 정책에 따라 보호된 문서를 배포할 수 있습니다.

다음 다이어그램은 AEM Forms Document Security의 일반적인 아키텍처를 보여 줍니다.

![문서 보안 - 권장 아키텍처](do-not-localize/document_security_architecture.png)

## 문서 보안 클라이언트 {#document-security-clients}

Document Security는 문서를 보호하고 보호된 문서를 보고 편집할 수 있는 다양한 클라이언트, 보호된 문서에서 전체 텍스트 검색을 사용할 수 있는 인덱서를 제공합니다. 클라이언트의 요구 사항과 기능을 기반으로 클라이언트를 선택할 수 있습니다.

Document Security Server는 Document Security에서 사용자 인증, 실시간 정책 관리 및 기밀 적용 등의 트랜잭션을 수행하는 중앙 구성 요소입니다. 또한 서버는 정책, 감사 레코드 및 기타 관련 정보를 위한 중앙 저장소를 제공합니다.

Document Security 서버는 웹 기반 인터페이스(웹 페이지)를 제공하여 정책을 만들고, 정책으로 보호된 문서를 관리하고, 정책으로 보호된 문서와 관련된 이벤트를 모니터링할 수 있습니다. 또한 관리자는 초대된 사용자에 대한 사용자 인증, 감사 및 메시지와 같은 글로벌 옵션을 구성하고 초대된 사용자 계정을 관리할 수 있습니다.

서버는 AEM Forms Document Security 추가 기능 서비스에 포함되어 있습니다. AEM Forms에 문의할 수 있습니다 [영업 팀](https://www.adobe.com/products/request-consultation/marketing-cloud.html?s_osc=70114000002JNwKAAW&amp;s_iid=70114000002JHs3AAG) 문서 보안 추가 기능을 구입하려면

### Protect 문서 {#protect-documents}

AEM Forms 문서 보안은 보안 정책을 적용하는 다양한 도구를 제공합니다. 요구 사항 및 사양에 따라 도구를 선택할 수 있습니다.

![문서 보안 제공](assets/document-security-offerings.png)

Document Security SDK, Adobe Acrobat, Document Security Extension for Microsoft Office 또는 Portable Protection Library 를 사용하여 보안 정책을 적용하고 추적할 수 있습니다.

* **문서 보안 SDK:** SDK는 기능이 풍부한 클라이언트입니다. Document Security SDK를 사용하여 문서 서버 기능에 액세스하고, 정책으로 보호된 문서를 열고, 사용자 정의 확장, 플러그인 또는 응용 프로그램을 개발할 수 있습니다. 예를 들어 확장을 개발하여 사용자 지정 파일 형식을 보호하거나 SDK를 DLP(데이터 손실 방지) 솔루션과 통합할 수 있습니다. Document Security SDK를 사용하여 개발된 확장, 애플리케이션 및 플러그인은 지정된 AEM Forms 서버에 문서를 보내고 서버에 적용되는 정책을 지정합니다. 또한 AEM Forms CSDK(Document Security Client SDK)는 PPL(Portable Protection Library)을 사용하여 보호된 문서를 보호하거나 그 반대로 보호할 수 없습니다.

   문서 보안 SDK는 Java와 C++ 모두에서 사용할 수 있습니다. Java SDK는 AEM Forms Document Security 솔루션에 포함되어 있으며, JEE에서 AEM Forms 배포에 설치됩니다. 연락하시면 됩니다 [AEM 지원 팀](https://helpx.adobe.com/kr/marketing-cloud/contact-support.html) 를 사용하여 C++ SDK를 구입할 수 있습니다. C++ SDK는 Microsoft Visual Studio 2013으로 컴파일할 수 있습니다. 방문할 수 있습니다 [문서 보안 API 설명서](https://help.adobe.com/en_US/livecycle/11.0/Services/WS92d06802c76abadb76c48dfe12dbeb3e281-7ff0.2.html) 사이트에서 SDK의 기능을 학습하고 사용할 수 있습니다.

* **Adobe Acrobat:** Adobe Acrobat을 사용하여 Microsoft Office, 웹 브라우저 또는 PDF 형식으로 인쇄를 지원하는 응용 프로그램과 같이 널리 사용되는 데스크톱 응용 프로그램을 사용하여 만든 PDF 문서에 보안 정책을 적용할 수 있습니다.

   에서 Adobe Acrobat을 구매하고 다운로드할 수 있습니다 [Adobe 웹 사이트](https://acrobat.adobe.com/us/en/free-trial-download.html). Adobe Acrobat 문서 [PDF 보안 정책 설정](https://helpx.adobe.com/acrobat/using/setting-security-policies-pdfs.html) Adobe Acrobat에서 정책 만들기 및 적용에 대한 자세한 정보를 제공합니다.

* **Microsoft Office용 문서 보안 확장**: Document Security Extension for Microsoft Office를 사용하여 Microsoft Office 프로그램 내에서 사전 정의된 정책을 Microsoft Office 파일에 적용할 수 있습니다. 이 확장을 사용하면 권한이 있는 사용자만 정책으로 보호된 Microsoft Word, Excel 및 PowerPoint 파일을 사용할 수 있습니다. 플러그인이 설치되어 있는 인증된 사용자만 정책으로 보호된 파일을 사용할 수 있습니다.

   문서 보안 확장은 Microsoft Office 플러그인으로 사용할 수 있습니다. 확장은 다음에서 다운로드할 수 있습니다. [Adobe 웹 사이트](https://helpx.adobe.com/aem-forms/aem-document-security/download-installer.html). 나중에 를 방문할 수 있습니다. [Microsoft Office용 문서 보안 확장](https://helpx.adobe.com/aem-forms/aem-document-security/aem-document-security-extension-help.html) 확장 설치, 구성 및 사용에 대한 자세한 내용은 도움말을 참조하십시오.

* **휴대용 보호 라이브러리:** PPL(Portable Protection Library)은 문서를 AEM Forms 서버에 보내지 않고 로컬로 문서를 보호합니다. 보안 자격 증명과 정책 세부 사항만 네트워크를 통해 이동합니다. 또한 PPL을 사용하면 로그인한 사용자만 정책 검색 액세스를 제한할 수 있습니다. AEM 사용자에 로그인한 사용자의 컨텍스트에서 정책을 가져올 수 있습니다.

   위와 함께 Promotable Protection Library에는 Document Security SDK의 모든 기능이 있습니다. Document Security SDK를 사용하여 문서 서버 기능에 액세스하고, 정책으로 보호된 문서를 열고, 사용자 정의 확장, 플러그인 또는 응용 프로그램을 개발할 수 있습니다. 또한 PPL(Portable Protection Library)에서는 AEM Forms CSDK(Document Security Client SDK)를 사용하여 보호된 문서를 보호하거나 그 반대로 보호할 수 없습니다.

   Portable Protection Library는 32비트 및 64비트 버전에서 Java 및 C++ 언어로 제공됩니다. OSGi에서 AEM Forms용 OSGi 번들로 사용할 수 있습니다. C++ PPL은 Microsoft Visual Studio 2013으로 컴파일할 수 있습니다. AEM Forms Document Security 추가 기능의 라이센스가 있는 경우 [AEM Forms 문서 보안](https://helpx.adobe.com/kr/marketing-cloud/contact-support.html) 지원 팀이 휴대용 보호 라이브러리를 확보합니다. 나중에 Portable Protection Library Help (라이브러리와 함께 번들로 제공)를 사용하여 Portable Protection Library를 설정하고 사용할 수 있습니다.

### 보호된 문서 보기 또는 편집 {#view-or-edit-protected-documents}

* 대상 **문서 PDF**, Adobe Acrobat DC, Acrobat Reader 및 Acrobat Reader Mobile 을 사용하여 보호된 PDF 문서를 볼 수 있습니다. 대부분의 사용자는 이미 장치에 Acrobat Reader이 설치되어 있으므로 보호된 문서를 보기 위해 추가 소프트웨어를 가져오거나 배울 필요가 없습니다. Acrobat Reader을 다운로드할 수도 있습니다. [Acrobat Reader 다운로드 웹 사이트](https://get.adobe.com/reader/).

* 대상 **Microsoft Office 문서** Microsoft Office용 Microsoft Office 및 AEM Forms 문서 보안 확장이 필요합니다. 문서 보안 확장은 Microsoft Office 플러그인으로 사용할 수 있습니다. 확장은 Adobe 웹 사이트에서 다운로드할 수 있습니다.

### 보호된 문서 색인화 {#index-protected-documents}

Microsoft Windows 전체 텍스트 검색 엔진(SharePoint Index Server) 및 Adobe Experience Manager(AEM)에서는 일반 텍스트 파일, Microsoft Office 문서 및 PDF 문서와 같이 일반적으로 사용되는 문서 형식에 대해 전체 텍스트 검색을 수행할 수 있습니다. 문서 보안 인덱서를 사용하여 전체 텍스트 검색 엔진이 보호된 PDF 문서를 검색할 수 있도록 설정할 수 있습니다.

* **iFilter 인덱서:** iFilter 인덱서를 사용하여 보호된 PDF 문서를 색인화하고 Microsoft Windows 전체 텍스트 검색 엔진(Desktop Indexing Service 및 SharePoint Indexserver)을 사용하여 보호된 PDF 문서를 검색할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [AEM SharePoint 보호된 문서용 필터](assets/sharepoint-ifilter-doc-security.pdf).

* **AEM Forms Document Security Indexer:** AEM Forms Document Security 인덱서를 사용하여 보호된 PDF 문서를 색인화하고 Adobe Experience Manager에서 보호된 PDF 문서를 검색할 수 있도록 설정할 수 있습니다. 인덱서는 AEM Forms 문서 보안 서비스의 일부입니다. JEE 설치 프로그램의 AEM Forms에 포함되어 있습니다.
