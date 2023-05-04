---
title: 웹 서비스 API를 사용하여 DDX 문서의 유효성 검사
seo-title: Validate a DDX document using theweb service API
description: 어셈블러 서비스 API를 사용하여 DDX 문서의 유효성을 확인합니다.
seo-description: Use the Assembler Service API to validate a DDX document.
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
role: Developer
exl-id: da303186-8f36-4fc8-a2db-b38a0b200c39
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 1%

---

# 웹 서비스 API를 사용하여 DDX 문서의 유효성 검사 {#validate-a-ddx-document-using-theweb-service-api}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

어셈블러 서비스 API(웹 서비스)를 사용하여 DDX 문서의 유효성을 검사합니다.

1. 프로젝트 파일을 포함합니다.

   MTOM을 사용하는 Microsoft .NET 프로젝트를 만듭니다. 다음 WSDL 정의를 사용해야 합니다. `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >localhost를 forms 서버의 IP 주소로 바꿉니다.

1. PDF 어셈블러 클라이언트를 만듭니다.

   * 만들기 `AssemblerServiceClient` 기본 생성자를 사용하여 개체를 만듭니다.
   * 만들기 `AssemblerServiceClient.Endpoint.Address` 개체를 `System.ServiceModel.EndpointAddress` 생성자입니다. WSDL을 지정하는 문자열 값을 AEM Forms 서비스에 전달합니다(예: `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). 를 사용할 필요가 없습니다 `lc_version` 속성을 사용합니다. 이 속성은 서비스 참조를 만들 때 사용됩니다.
   * 만들기 `System.ServiceModel.BasicHttpBinding` 개체의 값을 가져와서 `AssemblerServiceClient.Endpoint.Binding` 필드. 반환 값을 다음으로 캐스팅합니다. `BasicHttpBinding`.
   * 설정 `System.ServiceModel.BasicHttpBinding` 개체 `MessageEncoding` 필드 대상 `WSMessageEncoding.Mtom`. 이 값은 MTOM이 사용되도록 합니다.
   * 다음 작업을 수행하여 기본 HTTP 인증을 활성화합니다.

      * 필드에 AEM Forms 사용자 이름을 지정합니다 `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * 필드에 해당 암호 값을 지정합니다 `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * 상수 값 할당 `HttpClientCredentialType.Basic` 아래와 같이 변경하는 것을 의미합니다 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 상수 값 할당 `BasicHttpSecurityMode.TransportCredentialOnly` 아래와 같이 변경하는 것을 의미합니다 `BasicHttpBindingSecurity.Security.Mode`.

1. 기존 DDX 문서를 참조합니다.

   * 만들기 `BLOB` 생성자를 사용하여 개체를 작성합니다. 다음 `BLOB` 객체는 DDX 문서를 저장하는 데 사용됩니다.
   * 만들기 `System.IO.FileStream` 개체의 생성자를 호출하고 DDX 문서의 파일 위치와 파일을 열 모드를 나타내는 문자열 값을 전달하여 개체를 엽니다.
   * 의 내용을 저장하는 바이트 배열을 만듭니다 `System.IO.FileStream` 개체. 를 가져와서 바이트 배열의 크기를 결정할 수 있습니다 `System.IO.FileStream` 개체 `Length` 속성을 사용합니다.
   * 를 호출하여 바이트 배열을 스트림 데이터로 채웁니다 `System.IO.FileStream` 개체 `Read` 바이트 배열, 시작 위치 및 읽을 스트림 길이를 전달하는 메서드와 전달
   * 을(를) 채우기 `BLOB` 개체를 할당하여 개체를 개체 개체 `MTOM` 바이트 배열의 내용을 포함하는 속성입니다.

1. DDX 문서의 유효성을 검사할 런타임 옵션을 설정합니다.

   * 만들기 `AssemblerOptionSpec` 생성자를 사용하여 런타임 옵션을 저장하는 개체입니다.
   * 값을 true에 지정하여 어셈블러 서비스에서 DDX 문서의 유효성을 검사하도록 지시하는 런타임 옵션을 설정합니다. `AssemblerOptionSpec` 개체 `validateOnly` 데이터 멤버.
   * 문자열 값을 로 할당하여 어셈블러 서비스가 로그 파일에 쓰는 정보의 양을 설정합니다. `AssemblerOptionSpec` 개체 `logLevel` 데이터 멤버. DDX 문서의 유효성을 확인할 때 유효성 검사 프로세스를 지원할 로그 파일에 더 많은 정보를 기록할 수 있습니다. 따라서 값을 지정할 수 있습니다 `FINE` 또는 `FINER`. 설정할 수 있는 런타임 옵션에 대한 자세한 내용은 `AssemblerOptionSpec` 클래스 참조 [AEM Forms API 참조](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. 유효성 검사를 수행합니다.

   를 호출합니다 `AssemblerServiceClient` 개체 `invokeDDX` 메서드를 사용하여 다음 값을 전달합니다.

   * A `BLOB` DDX 문서를 나타내는 객체입니다.
   * 값 `null` 대상 `Map` 일반적으로 PDF 문서를 저장하는 객체입니다.
   * An `AssemblerOptionSpec` 런타임 옵션을 지정하는 개체입니다.

   다음 `invokeDDX` 메서드 반환 `AssemblerResult` DDX 문서가 유효한지 여부를 지정하는 정보가 포함된 객체입니다.

1. 유효성 검사 결과를 로그 파일에 저장합니다.

   * 만들기 `System.IO.FileStream` 객체를 사용하여 생성자를 호출하고 로그 파일의 파일 위치와 파일을 열 모드를 나타내는 문자열 값을 전달합니다. 파일 이름 확장명이 .xml인지 확인합니다.
   * 만들기 `BLOB` 로그 정보를 저장하는 개체 `AssemblerResult` 개체 `jobLog` 데이터 멤버.
   * 의 내용을 저장하는 바이트 배열을 만듭니다 `BLOB` 개체. 의 값을 가져와서 바이트 배열을 채웁니다 `BLOB` 개체 `MTOM` 필드.
   * 만들기 `System.IO.BinaryWriter` 생성자를 호출하고 전달하여 개체를 `System.IO.FileStream` 개체.
   * 를 호출하여 PDF 파일에 바이트 배열의 내용을 씁니다. `System.IO.BinaryWriter` 개체 `Write` 메서드를 사용하여 바이트 배열을 전달합니다.

   >[!NOTE]
   >
   >DDX 문서가 올바르지 않으면 `OperationException` 가 throw됩니다. catch 문 내에서 `OperationException` 개체 `jobLog` 멤버.

**추가 참조**

[DDX 문서 확인](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[MTOM을 사용하여 AEM Forms 호출](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
