---
title: FormsService에 문서 전달
seo-title: FormsService에 문서 전달
description: 양식 디자인이 포함된 com.adobe.idp.Document 개체를 Forms 서비스에 전달합니다. Forms 서비스는 com.adobe.idp.Document 개체에 있는 양식 디자인을 렌더링합니다.
seo-description: 양식 디자인이 포함된 com.adobe.idp.Document 개체를 Forms 서비스에 전달합니다. Forms 서비스는 com.adobe.idp.Document 개체에 있는 양식 디자인을 렌더링합니다.
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
role: Developer
exl-id: fe19e9b3-d662-4df2-b372-5006b794cde8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1700'
ht-degree: 0%

---

# Forms 서비스에 문서 전달 {#passing-documents-to-the-formsservice}

AEM Forms 서비스는 사용자 정보를 수집하기 위해 클라이언트 장치(일반적으로 웹 브라우저)에 대화형 PDF forms을 렌더링합니다. 대화형 PDF 양식은 일반적으로 XDP 파일로 저장되고 디자이너에서 만들어지는 양식 디자인을 기반으로 합니다. AEM Forms부터는 양식 디자인이 포함된 `com.adobe.idp.Document` 개체를 Forms 서비스에 전달할 수 있습니다. 그런 다음 Forms 서비스는 `com.adobe.idp.Document` 개체에 있는 양식 디자인을 렌더링합니다.

`com.adobe.idp.Document` 개체를 Forms 서비스에 전달하면 다른 서비스 작업에서 `com.adobe.idp.Document` 인스턴스를 반환하는 이점이 있습니다. 즉, 다른 서비스 작업에서 `com.adobe.idp.Document` 인스턴스를 가져와 렌더링할 수 있습니다. 예를 들어, 다음 그림과 같이 XDP 파일이 `/Company Home/Form Designs`(더 이상 사용되지 않음) 노드인 컨텐츠 서비스 노드에 저장된다고 가정합니다.

컨텐츠 서비스(더 이상 사용되지 않음)에서 Loan.xdp를 프로그래밍 방식으로 검색하고(더 이상 사용되지 않음) XDP 파일을 `com.adobe.idp.Document` 개체 내에서 Forms 서비스에 전달할 수 있습니다.

>[!NOTE]
>
>Forms 서비스에 대한 자세한 내용은 [AEM Forms에 대한 서비스 참조](https://www.adobe.com/go/learn_aemforms_services_63)를 참조하십시오.

## 단계 요약 {#summary-of-steps}

컨텐츠 서비스(더 이상 사용되지 않음)에서 가져온 문서를 Forms 서비스로 전달하려면 다음 작업을 수행하십시오.

1. 프로젝트 파일을 포함합니다.
1. Forms 및 Document Management 클라이언트 API 개체를 만듭니다.
1. Content Services에서 양식 디자인을 검색합니다(더 이상 사용되지 않음).
1. 대화형 PDF 양식을 렌더링합니다.
1. 양식 데이터 스트림으로 작업을 수행합니다.

**프로젝트 파일 포함**

개발 프로젝트에 필요한 파일을 포함하십시오. Java를 사용하여 클라이언트 응용 프로그램을 만드는 경우 필요한 JAR 파일을 포함하십시오. 웹 서비스를 사용하는 경우 프록시 파일을 포함하십시오.

**Forms 및 Document Management 클라이언트 API 개체 만들기**

Forms 서비스 API 작업을 프로그래밍 방식으로 수행하려면 먼저 Forms 클라이언트 API 개체를 만드십시오. 또한 이 워크플로우는 컨텐츠 서비스에서 XDP 파일을 검색하므로(더 이상 사용되지 않음) 문서 관리 API 개체를 만듭니다.

**컨텐츠 서비스에서 양식 디자인을 검색합니다(더 이상 사용되지 않음).**

Java 또는 웹 서비스 API를 사용하여 콘텐츠 서비스에서 XDP 파일을 검색합니다(더 이상 사용되지 않음). XDP 파일은 `com.adobe.idp.Document` 인스턴스(또는 웹 서비스를 사용하는 경우 `BLOB` 인스턴스) 내에서 반환됩니다. 그런 다음 `com.adobe.idp.Document` 인스턴스를 Forms 서비스에 전달할 수 있습니다.

**대화형 PDF 양식 렌더링**

대화형 양식을 렌더링하려면 Content Services(사용 중지)에서 반환된 `com.adobe.idp.Document` 인스턴스를 Forms 서비스에 전달합니다.

>[!NOTE]
>
>양식 디자인이 포함된 `com.adobe.idp.Document` 을 Forms 서비스에 전달할 수 있습니다. `renderPDFForm2` 및 `renderHTMLForm2` 라는 두 개의 새 메서드는 양식 디자인이 포함된 `com.adobe.idp.Document` 개체를 허용합니다.

**양식 데이터 스트림으로 작업 수행**

클라이언트 응용 프로그램 유형에 따라 양식을 클라이언트 웹 브라우저에 작성하거나 양식을 PDF 파일로 저장할 수 있습니다. 웹 기반 응용 프로그램은 일반적으로 웹 브라우저에 양식을 기록합니다. 그러나 데스크톱 응용 프로그램은 일반적으로 양식을 PDF 파일로 저장합니다.

**참고 항목**

[AEM Forms Java 라이브러리 파일 포함](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[연결 속성 설정](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms 서비스 API 빠른 시작](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Java API {#pass-documents-to-the-forms-service-using-the-java-api}를 사용하여 Forms 서비스에 문서를 전달합니다

Forms 서비스 및 컨텐츠 서비스(더 이상 사용되지 않음) API(Java)를 사용하여 컨텐츠 서비스(더 이상 사용되지 않음)에서 가져온 문서를 전달합니다.

1. 프로젝트 파일 포함

   adobe-forms-client.jar 및 adobe-contentservices-client.jar와 같은 클라이언트 JAR 파일을 Java 프로젝트의 클래스 경로에 포함합니다.

1. Forms 및 Document Management 클라이언트 API 개체 만들기

   * 연결 속성을 포함하는 `ServiceClientFactory` 개체를 만듭니다. ([연결 속성 설정](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties) 참조)
   * 생성자를 사용하여 `FormsServiceClient` 개체를 만들고 `ServiceClientFactory` 개체를 전달합니다.
   * 생성자를 사용하여 `DocumentManagementServiceClientImpl` 개체를 만들고 `ServiceClientFactory` 개체를 전달합니다.

1. 컨텐츠 서비스에서 양식 디자인을 검색합니다(더 이상 사용되지 않음).

   `DocumentManagementServiceClientImpl` 개체의 `retrieveContent` 메서드를 호출하고 다음 값을 전달합니다.

   * 컨텐츠가 추가되는 저장소를 지정하는 문자열 값입니다. 기본 저장소는 `SpacesStore`입니다. 이 값은 필수 매개 변수입니다.
   * 검색할 컨텐츠의 정규화된 경로를 지정하는 문자열 값입니다(예: `/Company Home/Form Designs/Loan.xdp`). 이 값은 필수 매개 변수입니다.
   * 버전을 지정하는 문자열 값입니다. 이 값은 선택적 매개 변수이며 빈 문자열을 전달할 수 있습니다. 이 경우 최신 버전이 검색됩니다.

   `retrieveContent` 메서드는 XDP 파일이 포함된 `CRCResult` 개체를 반환합니다. `CRCResult` 개체의 `getDocument` 메서드를 호출하여 `com.adobe.idp.Document` 인스턴스를 가져옵니다.

1. 대화형 PDF 양식 렌더링

   `FormsServiceClient` 개체의 `renderPDFForm2` 메서드를 호출하고 다음 값을 전달합니다.

   * Content Services에서 검색한 양식 디자인이 포함된 `com.adobe.idp.Document` 개체입니다(더 이상 사용되지 않음).
   * 폼과 병합할 데이터를 포함하는 `com.adobe.idp.Document` 개체입니다. 데이터를 병합하지 않으려면 빈 `com.adobe.idp.Document` 개체를 전달합니다.
   * 런타임 옵션을 저장하는 `PDFFormRenderSpec` 개체입니다. 이 값은 선택적 매개 변수이며, 런타임 옵션을 지정하지 않으려는 경우 `null`을 지정할 수 있습니다.
   * URI 값을 포함하는 `URLSpec` 개체입니다. 이 값은 선택적 매개 변수이며 `null`을 지정할 수 있습니다.
   * 첨부 파일을 저장하는 `java.util.HashMap` 개체입니다. 이 값은 선택적 매개 변수이며 양식에 파일을 첨부하지 않으려는 경우 `null`을 지정할 수 있습니다.

   `renderPDFForm` 메서드는 클라이언트 웹 브라우저에 작성해야 하는 양식 데이터 스트림을 포함하는 `FormsResult` 개체를 반환합니다.

1. 양식 데이터 스트림으로 작업 수행

   * `FormsResult` 개체 &#39;s `getOutputContent` 메서드를 호출하여 `com.adobe.idp.Document` 개체를 만듭니다.
   * `getContentType` 메서드를 호출하여 `com.adobe.idp.Document` 개체의 콘텐츠 형식을 가져옵니다.
   * `setContentType` 메서드를 호출하고 `com.adobe.idp.Document` 개체의 콘텐츠 형식을 전달하여 `javax.servlet.http.HttpServletResponse` 개체의 콘텐츠 형식을 설정합니다.
   * `javax.servlet.http.HttpServletResponse` 개체의 `getOutputStream` 메서드를 호출하여 클라이언트 웹 브라우저에 양식 데이터 스트림을 쓰는 데 사용되는 `javax.servlet.ServletOutputStream` 개체를 만듭니다.
   * `com.adobe.idp.Document` 개체의 `getInputStream` 메서드를 호출하여 `java.io.InputStream` 개체를 만듭니다.
   * 바이트 배열을 만들고 `InputStream` 개체의 `read` 메서드를 호출하여 양식 데이터 스트림으로 채웁니다. 바이트 배열을 인수로 전달합니다.
   * `javax.servlet.ServletOutputStream` 개체의 `write` 메서드를 호출하여 양식 데이터 스트림을 클라이언트 웹 브라우저로 보냅니다. 바이트 배열을 `write` 메서드에 전달합니다.

**참고 항목**

[빠른 시작(SOAP 모드):Java API를 사용하여 Forms 서비스에 문서 전달](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[AEM Forms Java 라이브러리 파일 포함](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[연결 속성 설정](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## 웹 서비스 API {#pass-documents-to-the-forms-service-using-the-web-service-api}를 사용하여 Forms 서비스에 문서를 전달합니다

Forms 서비스 및 콘텐츠 서비스(더 이상 사용되지 않음) API(웹 서비스)를 사용하여 콘텐츠 서비스에서 얻은 문서를 전달합니다.

1. 프로젝트 파일 포함

   MTOM을 사용하는 Microsoft .NET 프로젝트를 만듭니다. 이 클라이언트 응용 프로그램은 두 개의 AEM Forms 서비스를 호출하므로 두 개의 서비스 참조를 만듭니다. Forms 서비스와 연결된 서비스 참조에 대해 다음 WSDL 정의를 사용하십시오.`http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`

   문서 관리 서비스와 연결된 서비스 참조에 대해 다음 WSDL 정의를 사용하십시오.`http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`

   `BLOB` 데이터 유형은 두 서비스 참조에 공통이므로 사용할 때 `BLOB` 데이터 형식을 완전히 정규화합니다. 해당 웹 서비스 빠른 시작에서 모든 `BLOB` 인스턴스는 완전히 검증됩니다.

   >[!NOTE]
   >
   >`localhost`*를 AEM Forms을 호스팅하는 서버의 IP 주소로 바꿉니다.*

1. Forms 및 Document Management 클라이언트 API 개체 만들기

   * 기본 생성자를 사용하여 `FormsServiceClient` 개체를 만듭니다.
   * `System.ServiceModel.EndpointAddress` 생성자를 사용하여 `FormsServiceClient.Endpoint.Address` 개체를 만듭니다. WSDL을 지정하는 문자열 값을 AEM Forms 서비스에 전달합니다(예: `http://localhost:8080/soap/services/FormsService?WSDL`). `lc_version` 특성을 사용할 필요는 없습니다. 이 속성은 서비스 참조를 생성할 때 사용됩니다.)
   * `FormsServiceClient.Endpoint.Binding` 필드의 값을 가져와서 `System.ServiceModel.BasicHttpBinding` 개체를 만듭니다. 반환 값을 `BasicHttpBinding`(으)로 캐스팅합니다.
   * `System.ServiceModel.BasicHttpBinding` 개체의 `MessageEncoding` 필드를 `WSMessageEncoding.Mtom`로 설정합니다. 이 값은 MTOM이 사용되도록 합니다.
   * 다음 작업을 수행하여 기본 HTTP 인증을 활성화합니다.

      * AEM Forms 사용자 이름을 `FormsServiceClient.ClientCredentials.UserName.UserName` 필드에 지정합니다.
      * 해당 암호 값을 `FormsServiceClient.ClientCredentials.UserName.Password` 필드에 할당합니다.
      * 상수 값 `HttpClientCredentialType.Basic`을 필드 `BasicHttpBindingSecurity.Transport.ClientCredentialType`에 할당합니다.
   * 상수 값 `BasicHttpSecurityMode.TransportCredentialOnly`을 필드 `BasicHttpBindingSecurity.Security.Mode`에 할당합니다.

   >[!NOTE]
   >
   >`DocumentManagementServiceClient`* 서비스 클라이언트에 대해 이러한 단계를 반복합니다.*

1. 컨텐츠 서비스에서 양식 디자인을 검색합니다(더 이상 사용되지 않음).

   `DocumentManagementServiceClient` 개체의 `retrieveContent` 메서드를 호출하고 다음 값을 전달하여 콘텐츠를 검색합니다.

   * 컨텐츠가 추가되는 저장소를 지정하는 문자열 값입니다. 기본 저장소는 `SpacesStore`입니다. 이 값은 필수 매개 변수입니다.
   * 검색할 컨텐츠의 정규화된 경로를 지정하는 문자열 값입니다(예: `/Company Home/Form Designs/Loan.xdp`). 이 값은 필수 매개 변수입니다.
   * 버전을 지정하는 문자열 값입니다. 이 값은 선택적 매개 변수이며 빈 문자열을 전달할 수 있습니다. 이 경우 최신 버전이 검색됩니다.
   * 찾아보기 링크 값을 저장하는 문자열 출력 매개 변수입니다.
   * 컨텐츠를 저장하는 `BLOB` 출력 매개 변수입니다. 이 출력 매개 변수를 사용하여 컨텐츠를 검색할 수 있습니다.
   * 컨텐츠 속성을 저장하는 `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` 출력 매개 변수입니다.
   * `CRCResult` 출력 매개 변수입니다. 이 개체를 사용하는 대신 `BLOB` 출력 매개 변수를 사용하여 콘텐츠를 가져올 수 있습니다.

1. 대화형 PDF 양식 렌더링

   `FormsServiceClient` 개체의 `renderPDFForm2` 메서드를 호출하고 다음 값을 전달합니다.

   * Content Services에서 검색한 양식 디자인이 포함된 `BLOB` 개체입니다(더 이상 사용되지 않음).
   * 폼과 병합할 데이터를 포함하는 `BLOB` 개체입니다. 데이터를 병합하지 않으려면 빈 `BLOB` 개체를 전달합니다.
   * 런타임 옵션을 저장하는 `PDFFormRenderSpec` 개체입니다. 이 값은 선택적 매개 변수이며, 런타임 옵션을 지정하지 않으려는 경우 `null`을 지정할 수 있습니다.
   * URI 값을 포함하는 `URLSpec` 개체입니다. 이 값은 선택적 매개 변수이며 `null`을 지정할 수 있습니다.
   * 첨부 파일을 저장하는 `Map` 개체입니다. 이 값은 선택적 매개 변수이며 양식에 파일을 첨부하지 않으려는 경우 `null`을 지정할 수 있습니다.
   * 페이지 수를 저장하는 데 사용되는 긴 출력 매개 변수입니다.
   * 로케일 값을 저장하는 데 사용되는 문자열 출력 매개 변수입니다.
   * 대화형 PDF 양식 `.`을 저장하는 데 사용되는 `FormsResult` 출력 매개 변수입니다

   `renderPDFForm2` 메서드는 대화형 PDF 양식이 포함된 `FormsResult` 개체를 반환합니다.

1. 양식 데이터 스트림으로 작업 수행

   * `FormsResult` 개체의 `outputContent` 필드 값을 가져와서 양식 데이터를 포함하는 `BLOB` 개체를 만듭니다.
   * 해당 생성자를 호출하여 `System.IO.FileStream` 개체를 만듭니다. 대화형 PDF 문서의 파일 위치와 파일을 열 모드를 나타내는 문자열 값을 전달합니다.
   * `FormsResult` 개체에서 검색한 `BLOB` 개체의 콘텐츠를 저장하는 바이트 배열을 만듭니다. `BLOB` 개체의 `MTOM` 데이터 멤버의 값을 가져와서 바이트 배열을 채웁니다.
   * 해당 생성자를 호출하고 `System.IO.FileStream` 개체를 전달하여 `System.IO.BinaryWriter` 개체를 만듭니다.
   * `System.IO.BinaryWriter` 개체의 `Write` 메서드를 호출하고 바이트 배열을 전달하여 바이트 배열 내용을 PDF 파일에 씁니다.

**참고 항목**

[MTOM을 사용하여 AEM Forms 호출](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
