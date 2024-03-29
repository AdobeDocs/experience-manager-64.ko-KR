---
title: 애플리케이션 가져오기 및 관리
seo-title: Import and manage applications
description: 애플리케이션을 가져오고 관리하는 방법을 알아봅니다.
seo-description: Learn how to import and manage applications.
uuid: 7fba6c4e-1a3e-4a4b-9201-acf2ff66a9df
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: dc53a6d0-317a-4abd-990c-455e13f8b824
exl-id: 81a48c01-8052-47b1-be39-e126c37c7f0f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---

# 애플리케이션 가져오기 및 관리{#import-and-manage-applications}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM 양식에서 *애플리케이션* 는 AEM Forms 솔루션을 구현하는 데 필요한 자산을 저장하는 컨테이너입니다. 자산의 예로는 양식 디자인, 양식 조각, 이미지, 프로세스, DDX 파일, 양식 안내서, HTML 페이지 및 SWF 파일이 있습니다. 프로젝트의 개발 단계 동안 Workbench 사용자는 Workbench의 응용 프로그램 보기에서 직접 응용 프로그램을 배포할 수 있습니다. 배포되면 이러한 응용 프로그램은 [응용 프로그램 관리] 페이지의 [응용 프로그램] 탭에 있는 관리 콘솔에 나타납니다.

애플리케이션이 완료되어 프로덕션 서버에 배포할 준비가 되면 Workbench 사용자는 애플리케이션을 *AEM forms 애플리케이션 파일* (.lca). 그런 다음 관리자는 Application Management 페이지의 Applications 탭을 사용하여 Administration Console을 사용하여 응용 프로그램 파일을 가져오고 배포합니다.

Application Management 페이지의 아카이브 탭을 사용하여 Workbench 8.x를 사용하여 생성된 LCA를 가져올 수도 있습니다.

>[!NOTE]
>
>향후 릴리스의 LCA 파일이 반드시 이전 버전과 호환되지 않는다는 알려진 문제가 있습니다. 향후 AEM Forms 릴리스(예: 미리 보기 릴리스)에서 LCA 파일을 보고 가져올 수 있지만, 지원되지 않으므로 비정상적인 동작이 발생할 수 있습니다.

애플리케이션 탭을 사용하여 워크벤치에서 생성된 애플리케이션을 가져오고 관리할 수 있습니다. 응용 프로그램 관리자는 응용 프로그램에 대한 런타임 구성을 내보낼 수도 있습니다. 런타임 구성을 내보내면 배포된 응용 프로그램을 시작하기 전에 프로덕션 환경에서 설정을 수동으로 다시 구성할 필요가 없습니다. 런타임 구성 파일에는 다음이 포함되어 있습니다.

* 서비스 구성 설정
* 풀 구성 설정
* 엔드포인트 구성 설정
* 보안 프로필

## 애플리케이션 또는 아카이브 가져오기 {#import-an-application-or-archive}

1. 관리 콘솔에서 서비스 > 응용 프로그램 및 서비스 > 응용 프로그램 관리를 클릭합니다.
1. 가져오기를 클릭합니다.
1. 찾아보기 를 클릭하고 가져올 .lca 파일을 선택하고 미리 보기를 클릭합니다. [응용 프로그램 미리 보기] 페이지에는 응용 프로그램에 대한 정보가 표시됩니다.
1. (선택 사항) 애플리케이션에 포함된 자산 목록을 보려면 자산 보기를 클릭합니다.
1. (선택 사항) 런타임에 자산을 배포하려면 가져오기가 완료되면 Deploy To Runtime을 선택합니다. 이 옵션을 선택하지 않으면 나중에 자산을 배포할 수 있습니다.
1. 가져오기를 클릭합니다. 응용 프로그램이 응용 프로그램 탭에 나타납니다.
1. 관리자 자격 증명을 사용하여 CRX 저장소에 로그인합니다.
1. 컨텐츠/dam/lcapplication으로 이동

   >[!NOTE]
   >
   >가져온 응용 프로그램은 lcapplications 노드에 표시됩니다.

1. 가져온 응용 프로그램 중 하나를 클릭합니다.

   오른쪽의 속성 탭에는 선택한 CRX 노드의 속성이 표시됩니다.

   다음 **syncState** 속성은 AEM Forms 서버와 CRX 저장소 간의 데이터 동기화 상태를 나타냅니다. 가져오기 프로세스가 시작되면 이 상태가 0으로 설정됩니다. 이 상태는 데이터가 현재 동기화되지 않았음을 나타냅니다. 데이터가 동기화되면 상태가 1로 설정됩니다.

## 애플리케이션 배포 {#deploy-an-application}

가져온 응용 프로그램 또는 Workbench에서 가져온 Workbench 사용자를 배포할 수 있습니다.

1. 관리 콘솔에서 서비스 > 응용 프로그램 및 서비스 > 응용 프로그램 관리를 클릭합니다.
1. 배포할 애플리케이션 옆의 확인란을 선택하고 배포를 클릭합니다.
1. 표시되는 확인 대화 상자에서 확인 을 클릭합니다.

## 애플리케이션 배포 취소 {#undeploy-an-application}

런타임에서 응용 프로그램 배포를 취소할 수 있습니다.

1. 관리 콘솔에서 서비스 > 응용 프로그램 및 서비스 > 응용 프로그램 관리를 클릭합니다.
1. 배포를 취소할 애플리케이션 옆의 확인란을 선택하고 배포 취소를 클릭합니다.
1. 표시되는 확인 대화 상자에서 확인 을 클릭합니다.

## 서버에서 응용 프로그램 제거 {#remove-an-application-from-the-server}

서버에서 해당 응용 프로그램을 제거하기 전에 응용 프로그램의 배포를 취소합니다.

1. 관리 콘솔에서 서비스 > 응용 프로그램 및 서비스 > 응용 프로그램 관리를 클릭합니다.
1. 제거할 애플리케이션 옆의 확인란을 선택하고 제거를 클릭합니다.
1. 표시되는 확인 대화 상자에서 확인 을 클릭합니다.

## 응용 프로그램의 런타임 구성 가져오기 {#import-an-application-s-runtime-configuration}

응용 프로그램 관리자가 응용 프로그램에 대한 런타임 구성을 내보낸 경우 배포된 응용 프로그램으로 가져올 수 있습니다. 관리 콘솔 또는 스크립팅된 LCA 배포를 사용하여 가져올 수 있습니다.

1. 관리 콘솔에서 서비스 > 응용 프로그램 및 서비스 > 응용 프로그램 관리를 클릭합니다.
1. 응용 프로그램 이름을 클릭합니다.
1. 런타임 구성 가져오기를 클릭합니다.
1. 찾아보기 를 클릭하고 런타임 구성이 포함된 XML 파일을 선택합니다.
1. 가져오기를 클릭합니다.

## 응용 프로그램의 런타임 구성 내보내기 {#export-an-application-s-runtime-configuration}

배포된 응용 프로그램의 런타임 구성 정보를 내보낼 수 있습니다.

1. 관리 콘솔에서 서비스 > 응용 프로그램 및 서비스 > 응용 프로그램 관리를 클릭합니다.
1. 응용 프로그램 이름을 클릭합니다.
1. 런타임 구성 내보내기 를 클릭하고 생성된 구성 파일(XML)을 저장합니다.

## AEM Forms 응용 프로그램의 스크립팅된 배포 {#scripted-deployment-of-aem-forms-applications}

다음 설정을 지정하는 settings.xml 파일을 비롯하여 스크립트 배포 도구를 사용하여 응용 프로그램 파일을 배포할 수도 있습니다.

* 서비스 구성 설정
* 풀 구성 설정
* 엔드포인트 구성 설정
* 보안 프로필

스크립팅된 배포를 사용하면 배포된 애플리케이션을 시작하기 전에 프로덕션 환경에서 설정을 수동으로 다시 구성할 필요가 없습니다.

1. 명령 프롬프트에서 다음 위치로 이동합니다. *[aem forms 루트]*/sdk/misc/Foundation/ArchiveManagement
1. 자세한 지침은 ReadMe.txt 파일을 검토하십시오.
1. readme.txt 파일에 설명된 대로 scriptedDeploy.bat 및 sample-files/sample.xml 파일을 수동으로 수정합니다.
1. scriptedDeploy.bat 파일을 실행합니다. 이 작업을 수행하면 무시 설정으로 AEM Forms 보관 파일이 배포됩니다.
