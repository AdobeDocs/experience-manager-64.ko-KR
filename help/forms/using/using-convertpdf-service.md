---
title: ConvertPDF 서비스
seo-title: ConvertPDF Service
description: AEM Forms ConvertPDF 서비스를 사용하여 PDF 문서를 PostScript 또는 이미지 파일로 변환합니다.
seo-description: Use AEM Forms ConvertPDF service to convert PDF documents to PostScript or image files.
uuid: 7fa94c8c-485b-4a77-bcd3-ed716e3cf316
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 5ec4f0ec-a9fd-4571-9b9a-278f4622c028
exl-id: a6fe7794-3c31-4706-9e23-fe63a506b0bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 2%

---

# ConvertPDF 서비스 {#convertpdf-service}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

PDF 변환 서비스는 PDF 문서를 PostScript 또는 이미지 파일(JPEG, JPEG 2000, PNG 및 TIFF)으로 변환합니다. PDF 문서를 PostScript로 변환하는 것은 모든 PostScript 프린터에서 자동 서버 기반 인쇄에 유용합니다. PDF 문서를 지원하지 않는 컨텐츠 관리 시스템에서 문서를 아카이빙할 때 PDF 문서를 다중 페이지 TIFF 파일로 변환하는 것이 실용적입니다.

변환 PDF 서비스를 사용하여 다음을 수행할 수 있습니다.

* PDF 문서를 PostScript로 변환합니다. PostScript로 변환할 때 변환 작업을 사용하여 소스 문서와 PostScript 수준 2 또는 3으로 변환할지 여부를 지정할 수 있습니다. PostScript 파일로 변환하는 PDF 문서는 비대화형 문서여야 합니다.
* PDF 문서를 JPEG, JPEG 2000, PNG 및 TIFF 이미지 형식으로 변환합니다. 이러한 이미지 형식으로 변환할 때 변환 작업을 사용하여 소스 문서와 이미지 옵션 사양을 지정할 수 있습니다. 사양에는 이미지 변환 형식, 이미지 해상도 및 색상 변환과 같은 다양한 기본 설정이 포함되어 있습니다.

## 서비스의 속성 구성   {#properties}

를 사용할 수 있습니다 **AEMFD ConvertPDF 서비스** AEM 콘솔에서 이 서비스에 대한 속성을 구성하십시오. AEM 콘솔의 기본 URL은 `https://[host]:[port]/system/console/configMgr`.

## 서비스 사용 {#using-the-service}

ConvertPDF 서비스는 다음 두 가지 API를 제공합니다.

* **[toPS](https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toPS)**: PDF 문서를 PostScript 파일로 변환합니다.

* **[toImage](https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage)**: PDF 문서를 이미지 파일로 변환합니다. 지원되는 이미지 형식은 JPEG, JPEG2000, PNG 및 TIFF입니다.

### JSP 또는 서블릿에서 toPS API 사용 {#using-tops-api-with-a-jsp-or-servlets}

```java
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToPSOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.PSLevel,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for 
 // the flat PDF file which needs to be converted 
 // to PostScript

 Document inputPDF = new Document(documentPath);

 // options object to pass to toPS API
 ToPSOptionsSpec toPSOptions = new ToPSOptionsSpec();

 // mandatory option to pass, sets PostScript langauge
 toPSOptions.setPsLevel(PSLevel.LEVEL_3);

 // invoke toPS method to convert inputPDF to PostScript
 Document convertedPS = cpdfService.toPS(inputPDF, toPSOptions);

 // save converted PostScript file to disk
 convertedPS.copyToFile(new File("C:/temp/out.ps"));

%>
```

### JSP 또는 서블릿에 toImage API 사용 {#using-toimage-api-with-a-jsp-or-servlets}

```java
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToImageOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.ImageConvertFormat,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
 String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for 
 // the flat PDF file which needs to be converted 
 // to image

 Document inputPDF = new Document(documentPath);

 // options object to pass to toImage API
 ToImageOptionsSpec toImageOptions = new ToImageOptionsSpec();

 // mandatory option to pass, image format
 toImageOptions.setImageConvertFormat(ImageConvertFormat.JPEG);

 // invoke toImage method to convert inputPDF to Image
 List<Document> convertedImages = cpdfService.toImage(inputPDF, toImageOptions);

 // save converted image files to disk
 for(int i=0;i<convertedImages.size();i++){
     Document pageImage = convertedImages.get(i);
     pageImage.copyToFile(new File("C:/temp/out_"+(i+1)+".jpeg"));
 }

%>
```

### AEM 워크플로우에서 ConvertPDF 서비스 사용 {#using-convertpdf-service-with-aem-workflows}

워크플로우에서 ConvertPDF 서비스를 실행하는 것은 JSP/서블릿에서 실행되는 것과 비슷합니다.

유일한 차이는 JSP/Servlet에서 서비스를 실행하는 것입니다. 문서 객체는 ResourceResolverHelper 개체에서 ResourceResolver 개체의 인스턴스를 자동으로 검색합니다. 이 자동 메커니즘\
워크플로우에서 코드가 호출될 때 작동하지 않습니다. 워크플로의 경우 ResourceResolver 개체의 인스턴스를 Document 클래스 생성자에 명시적으로 전달합니다. 그런 다음 Document 객체가\
저장소에서 콘텐츠를 읽을 ResourceResolver 개체를 제공했습니다.

다음 샘플 워크플로우 프로세스는 입력 문서를 PostScript 문서로 변환합니다. 코드가 ECMAScript로 작성되고 문서가 워크플로우 페이로드로 전달됩니다.

```
/*
 * Imports 
 */
var ConvertPdfService = Packages.com.adobe.fd.cpdf.api.ConvertPdfService;
var ToPSOptionsSpec = Packages.com.adobe.fd.cpdf.api.ToPSOptionsSpec;
var PSLevel = Packages.com.adobe.fd.cpdf.api.enumeration.PSLevel;
var Document = Packages.com.adobe.aemfd.docmanager.Document;
var File = Packages.java.io.File;
var ResourceResolverFactory = Packages.org.apache.sling.api.resource.ResourceResolverFactory;

// get reference to ConvertPdfService
var cpdfService = sling.getService(ConvertPdfService);

/*
 * workflow payload and path to it
 */
var payload = graniteWorkItem.getWorkflowData().getPayload();
var payload_path = payload.toString();

/* Create resource resolver using current session 
 * this resource resolver needs to be passed to Document
 * object constructor when file is to be read from 
 * crx repository. 
 */

/* get ResourceResolverFactory service reference , used 
 * to construct resource resolver
 */
var resourceResolverFactory = sling.getService(ResourceResolverFactory);

var authInfo = {
    "user.jcr.session":graniteWorkflowSession.getSession()
};

var resourceResolver = resourceResolverFactory.getResourceResolver(authInfo);

// Create Document object from payload_path 
var inputDocument = new Document(payload_path, resourceResolver);

// options object to be passed to toPS operation
var toPSOptions = new ToPSOptionsSpec();

// Set PostScript Language Three
toPSOptions.setPsLevel(PSLevel.LEVEL_3);

// invoke toPS operation to convert inputDocument to PS
var convertedPS = cpdfService.toPS(inputDocument, toPSOptions);

// save converted PostScript file to disk
convertedPS.copyToFile(new File("C:/temp/out.ps"));
```
