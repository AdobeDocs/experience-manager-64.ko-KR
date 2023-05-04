---
title: 백업 및 복원 서비스 APIQ 빠른 시작
seo-title: Backup and Restore Service APIQuick Starts
description: Java API 빠른 시작을 사용하여 백업 모드로 전환하고 백업 모드를 종료하려면 백업 및 복원 서비스 API를 사용합니다.
seo-description: Use the Backup and Restore Service API to enter and leave backup mode using the Java API Quick Start.
uuid: c3992be2-ceb4-480d-9c8f-71eb0ea66dde
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 813162be-dbf5-4dc1-80ff-e37dbc25ef60
role: Developer
exl-id: b4fa018f-48a6-4991-9f80-d2d6e0b30555
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 2%

---

# 백업 및 복원 서비스 API 빠른 시작 {#backup-and-restore-service-apiquick-starts}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Java API 빠른 시작(SOAP)은 백업 및 복원 서비스 API에 사용할 수 있습니다.

[빠른 시작: Java API(SOAP)를 사용하여 백업 모드 시작](backup-restore-service-api-quick.md#quick-start-soap-mode-entering-backup-mode-using-the-java-api)

[빠른 시작: Java API(SOAP)를 사용하여 백업 모드 종료](backup-restore-service-api-quick.md#quick-start-soap-mode-leaving-backup-mode-using-the-java-api)

AEM Forms 작업은 AEM Forms 강력한 형식의 API를 사용하여 수행할 수 있으며 연결 모드는 SOAP로 설정해야 합니다.

>[!NOTE]
>
>AEM Forms으로 프로그래밍에 있는 빠른 시작은 Forms 운영 체제를 기반으로 합니다. 그러나 UNIX와 같은 다른 운영 체제를 사용하는 경우에는 Windows 관련 경로를 해당 운영 체제에서 지원하는 경로로 바꿉니다. 마찬가지로, 다른 J2EE 응용 프로그램 서버를 사용하는 경우 올바른 연결 속성을 지정해야 합니다. 자세한 내용은 [연결 속성 설정](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 빠른 시작(SOAP 모드): Java API를 사용하여 백업 모드 시작 {#quick-start-soap-mode-entering-backup-mode-using-the-java-api}

다음 Java 코드 예는 두 시간 동안 고유한 레이블이 있는 백업 모드로 전환됩니다. 백업 시간이 만료되거나 백업 모드가 명시적으로 종료되면 Forms 서버가 글로벌 문서 저장소에서 파일을 제거하도록 돌아갑니다. (자세한 내용은 [Forms 서버에서 백업 모드 시작](/help/forms/developing/preparing-aem-forms-backup.md#entering-backup-mode-on-the-forms-server))

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-backup-restore-client-sdk.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
  
 import com.adobe.idp.backup.dsc.client.BackupServiceClient; 
 import com.adobe.idp.backup.dsc.service.BackupModeEntryResult; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class BackupRestoreEnter 
 { 
     public static void main(String[] args)  
     { 
         try 
         { 
             // Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL, ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             // Create a ServiceClientFactory instance 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a BackupService client object 
             BackupServiceClient backup = new BackupServiceClient(myFactory); 
              
             // Specify a generic label, 120 minutes to perform the backup,  
             // and not to provide continous backup mode coverage (used for snapshot backups) 
             String backUpLabel = new String("Snapshot2008July01"); 
             int minsInBackupMode = 120; 
             boolean continousCoverage = false; 
              
              
             // Enter backup mode on the forms server server 
             BackupModeEntryResult backupResult = backup.enterBackupMode(backUpLabel,minsInBackupMode, continousCoverage); 
              

             // Get information from entering backup mode on the forms server. 
             if (backupResult != null) 
             {     
                 System.out.println("Start time is: " + backupResult.getStartTime()); 
                 System.out.println("Backup Current ID is: " + backupResult.getId()); 
                 System.out.println("Backup Previous ID is: " + backupResult.getPreviousReservationId()); 
                 System.out.println("Backup Label is: " + backupResult.getLabel()); 
                 System.out.println("Backup Time to complete is: " + backupResult.getReservationTimeout()); 
             } 
             else 
             { 
                 System.out.println("Could not enter backup mode."); 
             } 
                              
         } 
         catch (Exception e)  
         { 
             e.printStackTrace(); 
         } 
         return; 
     }  
 } 
 
```

## 빠른 시작(SOAP 모드): Java API를 사용하여 백업 모드 종료 {#quick-start-soap-mode-leaving-backup-mode-using-the-java-api}

다음 Java 코드 예제를 명시적으로 사용하면 Forms 서버가 백업 모드를 종료하고 글로벌 문서 저장소에서 파일 제거로 돌아갑니다. (자세한 내용은 [Forms 서버에서 백업 모드 종료](/help/forms/developing/preparing-aem-forms-backup.md#leaving-backup-mode-on-the-forms-server))

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-backup-restore-client-sdk.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
  
 import com.adobe.idp.backup.dsc.client.BackupServiceClient; 
 import com.adobe.idp.backup.dsc.service.BackupModeResult; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class BackupRestoreLeave  
 { 
      
     public static void main(String[] args) 
     { 
         try 
         { 
             //Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[host]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL, ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             // Create a ServiceClientFactory instance 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a BackupService object 
             BackupServiceClient backup = new BackupServiceClient(myFactory); 
                      
             // Leave backup mode on the forms server 
             BackupModeResult leaveBackupResult = backup.leaveBackupMode(); 
              
             //Get result information from leaving backup mode 
             if (leaveBackupResult != null) 
             { 
                 System.out.println("Backup Mode ID is : " + leaveBackupResult.getId()); 
             } 
             else 
             { 
                 System.out.println("Forms server is not in backup mode."); 
             }         
      
         } 
         catch (Exception e)  
         { 
             e.printStackTrace(); 
         } 
         return; 
     } 
 } 
 
```
