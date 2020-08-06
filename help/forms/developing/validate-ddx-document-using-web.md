---
title: 웹 서비스 API를 사용하여 DCX 문서 유효성 검사
seo-title: 웹 서비스 API를 사용하여 DCX 문서 유효성 검사
description: 'null'
seo-description: 'null'
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
translation-type: tm+mt
source-git-commit: e3fcf1a117b13392b7e530a09198982c6160cb7b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---


# 웹 서비스 API를 사용하여 DCX 문서 유효성 검사 {#validate-a-ddx-document-using-theweb-service-api}

Assembler Service API(웹 서비스)를 사용하여 DCX 문서의 유효성을 확인합니다.

1. 프로젝트 파일 포함

   MTOM을 사용하는 Microsoft .NET 프로젝트를 만듭니다. 다음 WSDL 정의를 사용해야 합니다. `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >localhost를 양식 서버의 IP 주소로 바꿉니다.

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
   * 생성자를 호출하고 DDX 문서의 파일 위치 및 파일을 열 모드를 나타내는 문자열 값을 전달하여 `System.IO.FileStream` 개체를 만듭니다.
   * 개체의 내용을 저장하는 바이트 배열을 `System.IO.FileStream` 만듭니다. 개체의 속성을 가져와 바이트 배열의 크기를 결정할 수 `System.IO.FileStream` `Length` 있습니다.
   * 개체의 메서드를 호출하고 바이트 배열, 시작 위치 및 읽을 스트림 길이를 전달하여 바이트 배열 `System.IO.FileStream` `Read` 을 스트림 데이터로 채웁니다.
   * 바이트 배열의 컨텐츠로 해당 `BLOB` `MTOM` 속성을 지정하여 개체를 채웁니다.

1. 런타임 옵션을 설정하여 DDX 문서의 유효성을 확인합니다.

   * 생성자를 사용하여 런타임 옵션을 저장하는 `AssemblerOptionSpec` 객체를 만듭니다.
   * 개체의 데이터 멤버에 값을 true로 할당하여 어셈블러 서비스에 DDC 문서의 유효성을 확인하도록 지시하는 런타임 옵션 `AssemblerOptionSpec` 을 `validateOnly` 설정합니다.
   * 어셈블리의 데이터 멤버에 문자열 값을 할당하여 어셈블러 서비스가 로그 파일에 쓰는 정보의 양을 `AssemblerOptionSpec` 설정합니다 `logLevel` . 메서드를 사용하여 DCX 문서의 유효성을 검사할 때 유효성 검사 프로세스를 지원하는 로그 파일에 자세한 정보를 기록해야 합니다. 그 결과, 값 또는 `FINE` 을 지정할 수 있습니다 `FINER`. 설정할 수 있는 런타임 옵션에 대한 자세한 내용은 `AssemblerOptionSpec` AEM Forms API 참조에서 [클래스 참조를 참조하십시오](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. 유효성 검사를 수행합니다.

   개체의 `AssemblerServiceClient` 메서드를 `invokeDDX` 호출하고 다음 값을 전달합니다.

   * DDX 문서를 나타내는 `BLOB` 개체입니다.
   * 일반적으로 PDF 문서 `null` 를 저장하는 `Map` 개체의 값입니다.
   * 런타임 옵션을 지정하는 `AssemblerOptionSpec` 개체입니다.

   이 `invokeDDX` 메서드는 DDX 문서가 유효한지 여부를 지정하는 정보가 포함된 `AssemblerResult` 개체를 반환합니다.

1. 확인 결과를 로그 파일에 저장합니다.

   * 생성자를 호출하고 로그 파일의 파일 위치 및 파일을 열 모드를 나타내는 문자열 값을 전달하여 `System.IO.FileStream` 개체를 만듭니다. 파일 이름 확장자가 .xml인지 확인합니다.
   * 개체의 데이터 멤버 값을 가져와서 로그 정보를 저장하는 `BLOB``AssemblerResult` `jobLog` 개체를 만듭니다.
   * 개체의 내용을 저장하는 바이트 배열을 `BLOB` 만듭니다. 개체 필드의 값을 가져와 바이트 배열 `BLOB` 을 `MTOM` 채웁니다.
   * 생성자를 호출하고 개체를 전달하여 `System.IO.BinaryWriter` 개체를 `System.IO.FileStream` 만듭니다.
   * 개체의 메서드를 호출하고 바이트 배열을 전달하여 바이트 배열의 내용을 PDF 파일 `System.IO.BinaryWriter` `Write` 에 씁니다.

   >[!NOTE]
   >
   >DDX 문서가 유효하지 않으면 `OperationException` throw됩니다. catch 문 내에서 `OperationException` 개체 `jobLog` 멤버의 값을 가져올 수 있습니다.

**참고 항목**

[DCX 문서 유효성 확인](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[MTOM을 사용하여 AEM Forms 호출](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
