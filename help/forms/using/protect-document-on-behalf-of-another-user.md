---
title: 다른 사용자를 대신하여 Protect 문서
seo-title: 다른 사용자를 대신하여 Protect 문서
description: 문서 편집 권한을 달성하지 않고 API를 사용하여 다른 사용자를 대신하여 문서를 보호하는 방법을 알아봅니다.
seo-description: 문서 편집 권한을 달성하지 않고 API를 사용하여 다른 사용자를 대신하여 문서를 보호하는 방법을 알아봅니다.
uuid: 76f4b30b-6d0c-4cae-98b3-334efdbf27bb
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 7cb8140d-dd62-4659-8cc7-21361bd5d3f6
feature: 문서 보안
exl-id: 76f25e65-1bc3-4801-998c-40ff533393e2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 다른 사용자 {#protect-a-document-on-behalf-of-another-user} 대신 문서를 Protect

AEM Forms Document Security Java SDK는 문서 편집 권한을 달성하지 않고도 사용자 계정이 다른 사용자를 대신하여 문서를 보호할 수 있도록 해주는 API를 제공합니다. 워크플로우 프로세스 또는 프로그래밍 방식으로 문서 서비스로 API를 사용할 수 있습니다. 새 API는 다음과 같습니다.

* **** protectDocumentProtectDocument API를 사용하여

   다른 사용자 계정. 정책을 적용하는 데 사용되는 사용자 계정의 권한은 문서를 보호하는 것으로 제한됩니다. 문서를 열고 볼 수 있는 권한은 없습니다. RMSecureDocumentResult protectDocument(Document inDoc, String documentName, String policySetName, String policyName, RMLocale 로케일, 부울 bExactMatchForNames)

* **** createLicenseCreateLicense API를 사용하여 다른 사용자 계정을 대신하여 정책에 대한 라이선스를 만듭니다. PublishLicenseDTO createLicense(String policyId, String documentName, boolean logSecureDocEvent)
* **** protectDocumentWithCoverPageProtectDocumentWithCoverPage API를 사용하여 정책을 적용하고 다른 사용자를 대신하여 문서에 표지 페이지를 추가합니다. 정책을 적용하는 데 사용되는 사용자 계정의 권한은 문서를 보호하는 것으로 제한됩니다. 문서를 열고 볼 수 있는 권한은 없습니다. RMSecureDocumentResult protectDocumentWithCoverPage(Document inDoc, String documentName, String policySetName, String policyName, Document coverDoc, 부울 bExactMatchForNames)

## API를 사용하여 다른 사용자 {#using-the-apis-to-protect-a-document-on-behalf-of-another-user} 대신 문서 보호

다음 단계를 수행하여 다른 사용자를 대신하여 문서를 보호할 수 있으며 문서를 편집할 수 있는 권한을 부여하지 않습니다.

1. 정책 세트를 만듭니다. 예를 들면 PolicySet1입니다.
1. 새로 만든 정책 세트에서 정책을 만듭니다. 예를 들어 PolicySet1의 Policy1이 있습니다.
1. 역할 Rights Management 최종 사용자를 사용하여 사용자를 만듭니다. 예: User1. 새로 만든 사용자에게 Policy1을 사용하여 보호된 문서를 볼 수 있는 권한을 제공합니다.
1. 새 역할을 만듭니다. 예: 역할1. 새로 만든 역할에 서비스 호출 권한을 제공합니다. 새로 만든 역할이 있는 사용자를 만듭니다. 예를 들어 User2.User2 또는 관리자를 사용하여 SDK 연결을 만들고 protectDocument 서비스를 호출할 수 있습니다.

   이제 다음 샘플 코드를 실행하여 문서를 보호하는 사용자에게 문서를 편집할 수 있는 권한을 제공하지 않고도 문서를 보호할 수 있습니다.

   ```java
   import java.io.File;
   import java.io.FileInputStream;
   import java.io.FileNotFoundException;
   import java.io.FileOutputStream;
   import java.io.IOException;
   import java.io.InputStream;
   import java.util.Properties;
   
   import com.adobe.edc.common.dto.PublishLicenseDTO;
   import com.adobe.edc.sdk.SDKException;
   import com.adobe.idp.Document;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
   import com.adobe.livecycle.rightsmanagement.RMSecureDocumentResult;
   import com.adobe.livecycle.rightsmanagement.client.DocumentManager;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient2;
   
   public class PublishAsProtectAPI {
   
   private static final String unprotectedFileName = "C:\\unprotected.pdf";
   private static final String protectedFileName = "C:\\protect.pdf";
   private static final String coverFileName = "C:\\CoverPage.pdf";
   private static final String POLICY_ID = "2EF66008-5E2D-1034-9B06-00000A292C18"; 
   
   public static void main(String[] args) {
   
   try {
   
   Properties connectionProps = new Properties();
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT,"http://localhost:8080");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD,"password");
   
   // Create a ServiceClientFactory instance
   ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
   testProtectDocument(factory);
   testProtectDocumentWithCoverPage(factory);
   testProtectDocumentJavaPPL(factory);
   
   } 
   catch (Exception ex) {
   ex.printStackTrace(); }
   }
   
   private static void testProtectDocument(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocument(inPDF, "test", "newPolicySet", "latest", "DefaultDom", "administrator", null, true);
   System.out.println("Total Time taken for protectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static void testProtectDocumentWithCoverPage(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   FileInputStream coverIS = new FileInputStream(coverFileName);
   Document inCoverPDF = new Document(coverIS);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocumentWithCoverPage(inPDF, "test", "newPolicySet", "latestPolicy", inCoverPDF, true);
   System.out.println("Total Time taken for Page0ProtectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static PublishLicenseDTO testProtectDocumentJavaPPL (ServiceClientFactory factory) throws SDKException, FileNotFoundException, IOException {
   // Create a RightsManagementClient object
   RightsManagementClient2 rmClient2 = new RightsManagementClient2(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient2.getDocumentManager();
   long startTime = System.currentTimeMillis();
   PublishLicenseDTO license = documentManager.createLicense(POLICY_ID, "Out.pdf", true);
   System.out.println("Create License totalTime = " + (System.currentTimeMillis() - startTime));
   startTime = System.currentTimeMillis();
   // Reference a PDF document to which a policy is applied
   InputStream inputFileStream = new FileInputStream(unprotectedFileName);
   // Apply a policy to the PDF document
   InputStream protectPDF = rmClient2.getRightsManagementEncryptionService().protectDocument(inputFileStream, license);
   // Save the policy-protected PDF document
   File myFile = new File(protectedFileName);
   // write the inputStream to a FileOutputStream
   FileOutputStream outputStream = new FileOutputStream(myFile);
   int read = 0;
   byte[] bytes = new byte[1024];
   while ((read = protectPDF.read(bytes)) != -1) {
   outputStream.write(bytes, 0, read);
   }
   System.out.println("protectPDFDocument totalTime = " + (System.currentTimeMillis() - startTime));
   outputStream.close();
   inputFileStream.close();
   System.out.println("Document Protected Successfully");
   return license;
   }
   }
   ```
