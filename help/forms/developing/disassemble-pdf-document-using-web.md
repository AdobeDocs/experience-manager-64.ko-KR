---
title: 웹 서비스 API를 사용하여 PDF 문서 분리
seo-title: 웹 서비스 API를 사용하여 PDF 문서 분리
description: 'null'
seo-description: 'null'
uuid: d6283dc5-e333-49d0-abde-1d390662f4fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/programmatically_disassembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 49584fb4-8c3a-4d73-acd6-0879a67f6093
translation-type: tm+mt
source-git-commit: 529b8c6556a7179a9169ff8250af6b5dc1251ef3
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

---


# 웹 서비스 API를 사용하여 PDF 문서 분리 {#disassemble-a-pdf-document-usingthe-web-service-api}

Assembler Service API(웹 서비스)를 사용하여 PDF 문서를 분해합니다.

1. 프로젝트 파일 포함

   MTOM을 사용하는 Microsoft .NET 프로젝트를 만듭니다. 서비스 참조를 설정할 때 다음 WSDL 정의를 사용해야 합니다. `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >AEM Forms `localhost` 를 호스팅하는 서버의 IP 주소로 대체합니다.

1. PDF 어셈블러 클라이언트 만들기

   * 기본 생성자를 사용하여 `AssemblerServiceClient` 개체를 만듭니다.
   * 생성자를 사용하여 `AssemblerServiceClient.Endpoint.Address` 개체를 `System.ServiceModel.EndpointAddress` 만듭니다. WSDL을 지정하는 문자열 값을 AEM Forms 서비스에 전달합니다(예: `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). 속성을 사용할 필요는 `lc_version` 없습니다. 이 속성은 서비스 참조를 만들 때 사용됩니다.
   * 필드의 값을 `System.ServiceModel.BasicHttpBinding` 가져와 개체를 `AssemblerServiceClient.Endpoint.Binding` 만듭니다. 반환 값을 다음으로 캐스팅합니다 `BasicHttpBinding`.
   * 개체 `System.ServiceModel.BasicHttpBinding` 필드를 (으)로 `MessageEncoding` 설정합니다 `WSMessageEncoding.Mtom`. 이 값을 사용하면 MTOM이 사용됩니다.
   * 다음 작업을 수행하여 기본 HTTP 인증을 활성화합니다.

      * 필드에 AEM 양식 사용자 이름을 지정합니다 `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * 해당 암호 값을 필드에 지정합니다 `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * 필드에 상수 값 `HttpClientCredentialType.Basic` 을 지정합니다 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 필드에 상수 값 `BasicHttpSecurityMode.TransportCredentialOnly` 을 지정합니다 `BasicHttpBindingSecurity.Security.Mode`.

1. 기존 DDX 문서를 참조합니다.

   * 생성자를 사용하여 `BLOB` 개체를 만듭니다. 이 `BLOB` 개체는 DDX 문서를 저장하는 데 사용됩니다.
   * 생성자를 호출하여 `System.IO.FileStream` 개체를 만듭니다. DCX 문서의 파일 위치와 파일을 열 모드를 나타내는 문자열 값을 전달합니다.
   * 개체의 내용을 저장하는 바이트 배열을 `System.IO.FileStream` 만듭니다. 개체의 속성을 가져와 바이트 배열의 크기를 결정할 수 `System.IO.FileStream` `Length` 있습니다.
   * 개체의 메서드를 호출하고 바이트 배열, 시작 위치 및 읽을 스트림 길이를 전달하여 바이트 배열 `System.IO.FileStream` `Read` 을 스트림 데이터로 채웁니다.
   * 바이트 배열의 컨텐츠로 해당 `BLOB` `MTOM` 속성을 지정하여 개체를 채웁니다.

1. 분해할 PDF 문서를 참조합니다.

   * 생성자를 사용하여 `BLOB` 개체를 만듭니다. 이 `BLOB` 개체는 입력 PDF 문서를 저장하는 데 사용됩니다. 이 `BLOB` 개체는 인수로 `invokeOneDocument` 전달됩니다.
   * 생성자를 호출하고 입력 PDF 문서의 파일 위치와 파일을 열 모드를 나타내는 문자열 값을 전달하여 `System.IO.FileStream` 개체를 만듭니다.
   * 개체의 내용을 저장하는 바이트 배열을 `System.IO.FileStream` 만듭니다. 개체의 속성을 가져와 바이트 배열의 크기를 결정할 수 `System.IO.FileStream` `Length` 있습니다.
   * 개체의 메서드를 호출하고 바이트 배열, 시작 위치 및 읽을 스트림 길이를 전달하여 바이트 배열 `System.IO.FileStream` `Read` 을 스트림 데이터로 채웁니다.
   * 바이트 배열의 내용에 해당 `BLOB` `MTOM` 필드를 할당하여 개체를 채웁니다.
   * 개체를 `MyMapOf_xsd_string_To_xsd_anyType` 만듭니다. 이 컬렉션 개체는 분해할 PDF를 저장하는 데 사용됩니다.
   * 개체를 `MyMapOf_xsd_string_To_xsd_anyType_Item` 만듭니다.
   * 키 이름을 나타내는 문자열 값을 `MyMapOf_xsd_string_To_xsd_anyType_Item` 개체의 `key` 필드에 할당합니다. 이 값은 DCX 문서에 지정된 PDF 소스 요소의 값과 일치해야 합니다.
   * PDF 문서를 저장하는 `BLOB` 개체를 `MyMapOf_xsd_string_To_xsd_anyType_Item` 개체 `value` 필드에 할당합니다.
   * 개체에 `MyMapOf_xsd_string_To_xsd_anyType_Item` 개체를 `MyMapOf_xsd_string_To_xsd_anyType` 추가합니다. 개체의 `MyMapOf_xsd_string_To_xsd_anyType` 메서드를 `Add` 호출하고 `MyMapOf_xsd_string_To_xsd_anyType` 개체를 전달합니다.

1. 런타임 옵션을 설정합니다.

   * 생성자를 사용하여 런타임 옵션을 저장하는 `AssemblerOptionSpec` 객체를 만듭니다.
   * 객체에 속하는 데이터 멤버에 값을 할당하여 비즈니스 요구 사항에 맞게 런타임 옵션을 `AssemblerOptionSpec` 설정합니다. 예를 들어 오류가 발생할 때 어셈블러 서비스에서 작업을 계속 처리하도록 지정하려면 개체 `false` 필드에 `AssemblerOptionSpec` `failOnError` 할당합니다.

1. PDF 문서를 분해합니다.

   개체의 `AssemblerServiceClient` 메서드를 `invokeDDX` 호출하고 다음 값을 전달합니다.

   * PDF 문서를 분해하는 DCX 문서를 나타내는 `BLOB` 개체
   * 분해할 PDF 문서가 포함된 `MyMapOf_xsd_string_To_xsd_anyType` 개체
   * 런타임 옵션을 지정하는 `AssemblerOptionSpec` 개체

   이 `invokeDDX` `AssemblerResult` 메서드는 작업 결과 및 발생한 예외를 포함하는 개체를 반환합니다.

1. 분해된 PDF 문서를 저장합니다.

   새로 만든 PDF 문서를 얻으려면 다음 작업을 수행하십시오.

   * 분해된 PDF 문서를 포함하는 `AssemblerResult` `documents` `Map` 개체인 개체의 필드에 액세스합니다.
   * 객체를 반복하여 결과 문서를 `Map` 가져옵니다. 그런 다음 해당 어레이 멤버 `value` 를 a로 캐스팅합니다 `BLOB`.
   * 개체의 속성에 액세스하여 PDF 문서를 나타내는 이진 데이터 `BLOB` 를 `MTOM` 추출합니다. PDF 파일에 기록할 수 있는 바이트 배열을 반환합니다.

**참고 항목**

[프로그래밍 방식으로 PDF 문서 분리](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

[MTOM을 사용하여 AEM Forms 호출](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
