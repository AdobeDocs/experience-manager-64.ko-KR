---
title: AEM Forms JEE 패치 설치 프로그램
description: 'null'
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 610e9a54adad3abdfecb8b2c4da67d677f75175e
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---


# AEM Forms JEE 패치 설치 프로그램 {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[지원](https://www.adobe.com/account/sign-in.supportportal.html) 센터에 문의하여 자세한 내용을 확인하거나 패치를 받으십시오.

## 패치 설치 프로그램 정보 {#about-the-patch-installer}

AEM 6.4 Forms JEE 패치 설치 프로그램에는 이 패치가 릴리스될 때까지 AEM 6.4 Forms JEE의 모든 구성 요소에 대한 모든 고정 문제가 포함됩니다. 해결된 문제의 전체 목록은 최신 [누적 수정 팩 릴리스](cfp-release-notes.md) 정보를 참조하십시오.

## 패치 설치 전제 조건 {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## 패치 설치 및 구성 {#installing-and-configuring-the-patch}

1. &lt;*AEM_forms_root*>/deploy 폴더의 백업을 수행합니다. 빠른 수정 사항을 제거하려는 경우 필요합니다.
1. 응용 프로그램 서버를 중지합니다.
1. 패치 설치 프로그램 아카이브 파일을 하드 드라이브에 추출합니다.
1. 사용 중인 운영 체제에 따라 이름이 지정된 디렉토리:

   * **Windows**&#x200B;설치 프로그램을 복사한 하드 디스크의 설치 미디어 또는 폴더에서 해당 디렉토리로 이동한 다음 
`aemforms64_cfp_install.exe` file.

      * (Windows 32비트) `Windows\Disk1\InstData\VM`
      * (Windows 64비트) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX**&#x200B;해당 디렉토리로 이동하고 명령 프롬프트에서 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   설치 과정을 안내하는 설치 마법사가 시작됩니다.

1. [소개] 패널에서 [ **[!UICONTROL 다음]을 클릭합니다]**.
1. [폴더 설치 선택] 화면에서 표시되는 기본 위치가 기존 설치에 적합한지 확인하거나 [ **[!UICONTROL 찾아보기]** ]를 클릭하여 AEM 양식이 설치된 대체 폴더를 선택한 다음 [ **[!UICONTROL 다음]을 클릭합니다]**.

1. 빠른 수정 패치 요약 정보를 읽고 **[!UICONTROL 다음을 클릭합니다]**.
1. 사전 설치 요약 정보를 읽고 **[!UICONTROL 설치를 클릭합니다]**.
1. 설치가 완료되면 **[!UICONTROL 다음]**을 클릭하여 설치된 파일에 빠른 수정 업데이트를 적용합니다.
1. [Windows만] 다음 단계 중 하나를 수행합니다.

   * 완료를 클릭하기 전에 구성 관리자 시작 옵션을 선택 취소합니다. Configuration Manager를 실행할 때 에 있는 `ConfigurationManager.bat` 파일을 사용합니다 `[aem-forms root]\configurationManager\bin`. 를 사용하면 .lax 파일에서 axis.jar 이름 이름을 수동으로 업데이트하지 않는 데 `ConfigurationManager.bat` 도움이 됩니다.
   * 완료를 클릭하기 전에 구성 관리자 시작 옵션을 선택 취소합니다. ConfigurationManager.exe **또는** ConfigurationManager_IPv6.exe **를 사용하여 구성 관리자를 실행하기 전에**&lt;AForms_Install_Dir\configurationManager\bin *디렉토리 및 update.dir을 탐색하여 다음* 의 **aem-axis 1.4.jar 파일의 jar을 탐색합니다.1.** **** following 파일의 &lt;jar로 이동합니다.

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Unix 기반 전용) 기본적으로 구성 관리자 시작 확인란이 선택되어 있습니다. 완료를 **[!UICONTROL 클릭하여]** 구성 관리자를 실행합니다.

   나중에 Configuration Manager를 실행하려면 완료를 클릭하기 전에 구성 관리자 시작 옵션을 선택 취소합니다. 나중에 디렉토리에서 해당 스크립트를 사용하여 Configuration Manager를 시작할 수 `[AEM_forms_root]/configurationManager/bin` 있습니다.

1. 응용 프로그램 서버에 따라 다음 문서 중 하나를 선택하고 [AEM 양식 *구성 및 배포] 섹션의 지침을 따릅니다* .

   * [JBoss용 AEM 양식 설치 및 배포](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [WebSphere용 AEM 양식 설치 및 배포](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [WebLogic용 AEM 양식 설치 및 배포](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. (JBoss에만 해당) 패치를 설치하고 서버를 구성한 후 JBoss 응용 프로그램 서버의 tmp 및 작업 디렉토리를 삭제합니다.

## 배포 후 구성 {#post-deployment-configurations}

### SAML 구성 {#saml-configurations}

큰 IDP 메타데이터에 대해 SAML 인증이 구성되고 문제가 발생하는 경우 패치를 설치한 후 다음을 수행합니다.

1. 응용 프로그램 서버에서 다음 시스템 속성을 설정합니다.\
   `um.saml.enable.large.xml=true`

1. 서버를 다시 시작합니다.
1. SAML 설정에 설명된 대로 기존 SAML 인증 공급자를 삭제하고 기존 도메인에 대해 다시 추가합니다.

## 영향을 받은 모듈 {#impacted-modules}

* 문서 서비스
* 문서 보안
* Foundation JEE
* PDFG 서비스

[지원 문의](https://www.adobe.com/account/sign-in.supportportal.html)
