---
title: DocConverter 서비스 Java API QuickStart(SOAP)
seo-title: DocConverter Service Java API QuickStart(SOAP)
description: DocConverter 서비스 Java API를 사용하여 PDF/A 규정을 확인하고 문서를 PDF/A 문서로 변환합니다.
seo-description: Use the DocConverter Service Java API to determine PDF/A compliance and to convert a document to a PDF/A document.
uuid: a02e13a5-4557-4c8a-a4be-e8d017127128
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: ea4b26c8-b9cf-42c2-b4da-2884336014a9
role: Developer
exl-id: 0a418016-f61a-485d-a87a-a3d48651e0d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 2%

---

# DocConverter 서비스 Java API 빠른 시작(SOAP) {#docconverter-service-java-api-quickstart-soap}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

DocConverter 서비스에서 Java API 빠른 시작(SOAP)을 사용할 수 있습니다.

[빠른 시작(SOAP 모드): Java API를 사용하여 PDF/A 준수 결정](docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[빠른 시작(SOAP 모드): Java API를 사용하여 문서를 PDF/A 문서로 변환](docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

AEM Forms 작업은 AEM Forms 강력한 형식의 API를 사용하여 수행할 수 있으며 연결 모드는 SOAP로 설정해야 합니다.

>[!NOTE]
>
>AEM Forms로 프로그래밍에 있는 빠른 시작은 JBoss Application Server 및 Microsoft Windows 운영 체제에 배포되는 Forms 서버를 기반으로 합니다. 그러나 UNIX와 같은 다른 운영 체제를 사용하는 경우에는 Windows 관련 경로를 해당 운영 체제에서 지원하는 경로로 바꿉니다. 마찬가지로, 다른 J2EE 응용 프로그램 서버를 사용하는 경우 올바른 연결 속성을 지정해야 합니다. 자세한 내용은 [연결 속성 설정](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 빠른 시작(SOAP 모드): Java API를 사용하여 문서를 PDF/A 문서로 변환 {#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api}

다음 Java 코드 예는 라는 PDF 문서를 변환합니다 *Loan.pdf* PDF 파일로 저장된 PDF/문서에 *LoanArchive.pdf*. (자세한 내용은 [문서를 PDF/A 문서로 변환](/help/forms/developing/pdf-a-documents.md#converting-documents-to-pdf-a-documents))

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-docconverter-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.docconverter.client.DocConverterServiceClient; 
 import com.adobe.livecycle.docconverter.client.PDFAConversionOptionSpec; 
 import com.adobe.livecycle.docconverter.client.PDFAConversionResult; 
  
 public class CreatePDFADocumentSOAP { 
      
     public static void main(String[] args) { 
     try{ 
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
          
         //Create a DocConverterServiceClient object 
         DocConverterServiceClient docConverter = new DocConverterServiceClient(myFactory); 
      
         //Reference a PDF document to convert to a PDF/A document  
         FileInputStream myPDF = new FileInputStream("C:\\Adobe\Loan.pdf");  
         Document inDoc = new Document(myPDF);  
          
         //Create a PDFAConversionOptionSpec object and set  
         //tracking information 
         PDFAConversionOptionSpec spec = new PDFAConversionOptionSpec(); 
         spec.setLogLevel("FINE"); 
          
         //Convert the PDF document to a PDF/A document 
         PDFAConversionResult result =  docConverter.toPDFA(inDoc,spec);      
          
         //Save the PDF/A file 
         Document pdfADoc= result.getPDFADocument(); 
         File pdfAFile = new File("C:\\Adobe\LoanArchive.pdf"); 
         pdfADoc.copyToFile(pdfAFile); 
       }catch (Exception e) { 
         e.printStackTrace(); 
     } 
      } 
 }
```

## 빠른 시작(SOAP 모드): Java API를 사용하여 PDF/A 준수 결정 {#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api}

다음 Java 코드 예는 입력 PDF 문서가 PDF/A 규격 문서인지 여부를 결정합니다. DocConverter 서비스에 전달되는 입력 PDF 문서의 이름은 다음과 같습니다 *LoanArchive.pdf*. 검증 결과는 이름이 인 XML 파일에 기록됩니다. *ValidationResults.xml*. (자세한 내용은 [프로그래밍 방식으로 PDF/규정 준수 결정](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy))

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-docconverter-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.docconverter.client.DocConverterServiceClient; 
 import com.adobe.livecycle.docconverter.client.PDFAValidationOptionSpec; 
 import com.adobe.livecycle.docconverter.client.PDFAValidationResult; 
  
 public class IsDocumentPDFASOAP { 
      
     public static void main(String[] args) { 
     try{ 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
          
         //Create a DocConverterServiceClient object 
         DocConverterServiceClient docConverter = new DocConverterServiceClient(myFactory); 
      
         //Reference a PDF document used to determine PDF/A compliancy  
         FileInputStream myPDF = new FileInputStream("C:\\Adobe\LoanArchive.pdf");  
         Document inDoc = new Document(myPDF);  
          
         //Create a PDFAValidationOptionSpec object and set  
         //run-time values 
         PDFAValidationOptionSpec spec = new PDFAValidationOptionSpec(); 
         spec.setCompliance(PDFAValidationOptionSpec.Compliance.PDFA_1B); 
         spec.setResultLevel(PDFAValidationOptionSpec.ResultLevel.DETAILED); 
         spec.setLogLevel("FINE"); 
         spec.setIgnoreUnusedResource(true); 
                  
         //Determine if the PDF document is PDF/A compliant 
         PDFAValidationResult result =  docConverter.isPDFA(inDoc,spec)    ; 
                  
         //Get the results of the operation 
         Boolean isPDFA = result.getIsPDFA(); 
          
         //Get XML data that contains validaction results 
         Document validationResults =  result.getValidationLog(); 
         File file= new File("C:\\Adobe\ValidationResults.xml"); 
         validationResults .copyToFile(file); 
      
     }catch (Exception e) { 
         e.printStackTrace(); 
     } 
      } 
 }
```
