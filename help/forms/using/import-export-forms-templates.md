---
title: AEM Forms으로 자산 가져오기 및 내보내기
seo-title: Importing and exporting assets to AEM Forms
description: 적응형 양식 및 템플릿을 가져오거나 AEM 인스턴스로 내보낼 수 있습니다. 따라서 양식을 마이그레이션하거나 시스템 간에 이동하는 데 도움이 됩니다.
seo-description: You can import and export adaptive forms and templates from and in to AEM instances. This helps in migrating forms or moving them across systems.
uuid: 9365dc02-fe2e-455a-8aa2-4c5bacb1fb74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 6fddb09a-ec60-4235-8ff4-0646f53f38f7
role: Admin
exl-id: 2f71c588-5616-440f-8e47-8d9665169b3b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2538'
ht-degree: 0%

---

# AEM Forms으로 자산 가져오기 및 내보내기 {#importing-and-exporting-assets-to-aem-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다양한 AEM Forms 인스턴스 간에 양식 및 관련 자산, 테마, 데이터 사전, 문서 조각 및 문자를 이동할 수 있습니다. 이러한 이동은 시스템을 마이그레이션하거나 스테이지 서버에서 프로덕션 서버로 양식을 이동할 때 필요합니다. AEM Forms UI를 통해 업로드하고 가져올 수 있는 자산을 내보내거나 가져오는 데 Forms UI를 사용하는 것이 좋습니다. 이러한 자산을 내보내거나 가져올 때는 AEM 패키지 관리자를 사용하지 않는 것이 좋습니다.

>[!NOTE]
>
>* AEM 6.4 Forms에서 crx-repository의 구조 및 경로가 변경되었습니다. 이전 버전에서 AEM 6.4 Forms으로 자산을 가져오는데 양식에 이전 구조에 대한 일부 종속성이 있는 경우 종속성을 수동으로 내보내야 합니다. 저장소의 구조 및 경로 변경 사항에 대한 자세한 내용은 [AEM 6.4의 저장소 구조 변경](/help/sites-deploying/repository-restructuring.md).
>


## Forms 및 문서 자산 다운로드 또는 업로드 {#download-or-upload-forms-amp-documents-assets}

AEM Forms 사용자 인터페이스를 사용하면 AEM CRX-package 또는 binary 파일로 자산을 다운로드하여 AEM 인스턴스에서 자산을 내보낼 수 있습니다. 그런 다음 다운로드한 AEM CRX-package 또는 binary 파일을 다른 AEM 인스턴스로 가져올 수 있습니다.

AEM Forms 사용자 인터페이스를 통한 내보내기 및 가져오기는 적용형 양식 템플릿 및 적용형 양식 컨텐츠 정책을 제외한 모든 자산에 대해 지원됩니다. 따라서 AEM Forms UI에서 적응형 양식을 내보낼 때 관련 적응형 양식 템플릿 및 컨텐츠 정책이 다른 관련 자산처럼 자동으로 내보내지지 않습니다.

이러한 자산 유형의 경우, AEM 패키지 관리자를 사용하여 소스 AEM 서버에 CRX 패키지를 만들고 대상 서버에 패키지를 설치해야 합니다. 패키지 만들기 및 설치에 대한 자세한 내용은 [패키지 작업](/help/sites-administering/package-manager.md).

### Forms 및 문서 자산 다운로드 {#download-forms-amp-documents-assets}

Forms 및 문서 자산을 다운로드하려면 다음을 수행하십시오.

1. AEM Forms 인스턴스에 로그인합니다.
1. Experience Manager 탭 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > 탐색 ![나침반](assets/compass.png) 아이콘> Forms > Forms 및 문서
1. Forms 자산을 선택하고 **다운로드** 아이콘.
1. 자산 다운로드에서 다음 옵션 중 하나를 선택하고 를 탭합니다 **다운로드**.

   * **CRX 패키지로 다운로드:** 옵션을 사용하여 선택한 모든 자산 및 관련 종속성을 AEM Forms 인스턴스에서 다른 인스턴스로 다운로드하고 이동합니다. 모든 자산 및 폴더를 crx 패키지로 다운로드합니다. AEM에서 작성된 양식(적응형 양식, 대화형 통신 및 적응형 양식 조각), 양식 세트, 양식 템플릿, PDF 문서 및 리소스(XSD, XFS, 이미지)를 포함한 모든 양식 자산은 AEM Forms UI에서 패키지로 다운로드할 수 있습니다.

      자산을 패키지로 다운로드하면 다운로드하도록 선택한 자산에서 사용한 자산도 다운로드되는 이점이 있습니다. 예를 들어 양식 템플릿, XSD 및 이미지를 사용하는 적응형 양식이 있는 경우 이 적응형 양식을 선택하고 패키지로 다운로드하면 다운로드한 패키지에는 양식 템플릿, XSD 및 이미지도 포함되어 있습니다. 자산과 연결된 모든 메타데이터 속성(사용자 지정 속성 포함)도 다운로드됩니다.

   * **자산을 이진 파일로 다운로드:** 양식 템플릿(XDP), PDF forms(PDF), 문서(PDF) 및 리소스(이미지, 스키마, 스타일 시트)만 다운로드하려면 옵션을 사용합니다. 외부 애플리케이션에서 이러한 자산을 편집할 수 있습니다. XSD, XDP, 이미지, PDF 및 XDP와 같은 바이너리가 있는 양식 자산을 .zip 파일로 다운로드합니다.

      적응형 양식, 대화형 통신, 적응형 양식 조각, 테마 및 양식 세트는 **자산을 이진 파일로 다운로드** 선택 사항입니다. 이러한 자산을 다운로드하려면 **CRX 패키지로 다운로드** 선택 사항입니다.
   선택한 자산이 아카이브(.zip 파일)로 다운로드됩니다.

   >[!NOTE]
   >
   >AEM 패키지와 이진 파일은 모두 보관 파일(.zip 파일)로 다운로드됩니다. 자산에 대한 템플릿은 자산과 함께 다운로드되지 않습니다. 자산 템플릿을 별도로 내보내야 합니다.

### Forms 및 문서 자산 업로드 {#upload-forms-amp-documents-assets}

Forms 및 문서 자산을 업로드하려면

>[!VIDEO](https://vimeo.com/)

1. AEM Forms 인스턴스에 로그인합니다.
1. Experience Manager 탭 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > 탐색 ![나침반](assets/compass.png) 아이콘> Forms> Forms 및 문서
1. 탭 **만들기** > **파일 업로드**. 양식 업로드 또는 패키지 대화 상자가 나타납니다.
1. 대화 상자에서 가져올 패키지 또는 아카이브를 찾아 선택합니다. PDF 문서, XSD, 이미지, 스타일 시트 및 XDP 양식을 선택할 수도 있습니다. 탭 **열기**.

   대화 상자에서 업로드되는 자산의 세부 정보를 확인하고 탭합니다 **업로드**.

   기존 양식 자산을 업로드하는 경우, 자산이 업데이트됩니다.

   >[!NOTE]
   >
   >패키지를 업로드해도 기존 폴더 계층 구조가 바뀌지 않습니다. 예를 들어 한 서버에 &#39;Training&#39;이라는 적응형 양식이 있는 경우 /content/dam/formsanddocuments 위치에 있습니다. 적응형 양식을 다운로드하고 다른 서버에 양식을 업로드합니다. 두 번째 서버에도 같은 위치에 이름이 &#39;Training&#39;인 폴더가 있습니다. /content/dam/formsanddocuments. 업로드에 실패합니다.

## 테마 다운로드 또는 업로드 {#downloading-or-uploading-a-theme}

AEM Forms을 사용하면 테마를 생성, 다운로드 또는 업로드할 수 있습니다. 테마는 양식, 문서 및 문자와 같은 다른 자산과 같이 만들어집니다. 테마를 만들고 다운로드하여 별도의 인스턴스에 업로드하여 다시 사용할 수 있습니다. 주제에 대한 자세한 내용은 다음을 참조하십시오 [AEM Forms의 테마](/help/forms/using/themes.md).

### 테마 다운로드 {#downloading-a-theme}

다른 프로젝트 또는 인스턴스에서 사용할 수 있는 AEM Forms의 테마를 내보낼 수 있습니다. AEM에서 인스턴스에 업로드할 수 있는 zip 파일로 테마를 다운로드할 수 있습니다.

테마를 다운로드하려면

1. AEM Forms 인스턴스에 로그인합니다.
1. Experience Manager 탭 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > 탐색 ![나침반](assets/compass.png) 아이콘> Forms> 테마.
1. 테마를 선택하고 탭합니다 **다운로드**. 테마는 아카이브(.zip 파일)로 다운로드됩니다.

### 테마 업로드 {#uploading-a-theme}

프로젝트에서 스타일 사전 설정으로 생성된 테마를 사용할 수 있습니다. 다른 사용자가 만든 테마 패키지를 프로젝트에서 업로드하여 가져올 수 있습니다.

테마를 업로드하려면

1. Experience Manager에서 **Forms > 테마**.
1. 테마 페이지에서 **만들기 > 파일 업로드**.
1. 파일 업로드 프롬프트에서 컴퓨터에서 테마 패키지를 찾아 선택하고 **업로드**.

   업로드된 테마는 테마 페이지에서 사용할 수 있습니다.

1. AEM Forms 인스턴스에 로그인합니다.
1. Experience Manager 탭 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) 아이콘 > 탐색 ![나침반](assets/compass.png) 아이콘> Forms> 테마.
1. click **만들기** >  **파일 업로드**. 파일 업로드 프롬프트에서 컴퓨터에서 테마 패키지를 찾아 선택하고 **업로드**. 테마가 업로드됩니다.

## 서신 관리에서 자산 가져오기 및 내보내기 {#import-and-export-assets-in-correspondence-management}

데이터 사전, 문자 및 문서 조각과 같은 자산을 서신 관리의 두 가지 다른 구현 간에 공유하려면 .cmp 파일을 만들고 공유할 수 있습니다. .cmp 파일에는 하나 이상의 데이터 사전, 문자, 문서 조각 및 양식이 포함될 수 있습니다.

### 문서 조각, 문자 및/또는 데이터 사전 내보내기 {#export-document-fragments-letters-and-or-data-dictionaries}

1. 편지, 문서 조각 또는 데이터 사전 페이지에서 단일 패키지로 내보낼 자산을 탭하여 선택한 다음, [다운로드 큐]를 탭합니다. 자산을 내보낼 수 있도록 정렬되어 있습니다.
1. 필요에 따라 위의 단계를 반복하여 문자, 문서 조각 및 데이터 사전을 추가합니다.
1. 탭 **다운로드**.
1. 서신 관리에는 내보내기 목록에 자산 목록이 있는 자산 다운로드 대화 상자가 표시됩니다.

   ![내보내기](assets/export.png)

1. 내보낸 종속성을 보려면 [해결]을 누릅니다. 또는 다음 단계로 건너뜁니다. 해결을 탭하지 않더라도 종속성은 계속 내보내집니다.
1. .cmp 파일을 다운로드하려면 다음을 누릅니다 **확인**.
1. 서신 관리는 컴퓨터에 .cmp 파일을 다운로드합니다.

   .cmp 파일에는 내보낸 자산이 포함되어 있습니다. .cmp 파일을 다른 사용자와 공유할 수 있습니다. 다른 사용자는 다른 서버에 .cmp 파일을 가져와서 새 서버의 모든 자산을 가져올 수 있습니다.

### 모든 서신 관리 자산을 패키지로 내보내기 {#export-all-the-correspondence-management-assets-as-a-package}

이 옵션을 사용하여 모든 서신 관리 자산 및 관련 종속성을 AEM Forms 인스턴스에서 패키지로 다운로드합니다.

예를 들어 서신 관리에 이미지와 텍스트를 사용하는 문자가 있는 경우, 다운로드한 패키지에는 이미지와 해당 문자와 관련된 텍스트도 포함됩니다. 자산과 연결된 모든 메타데이터 속성(사용자 지정 속성 포함)도 다운로드됩니다. 패키지(.cmp)를 다운로드한 후에는 다음을 수행할 수 있습니다 [다른 AEM Forms 인스턴스로 패키지 가져오기](/help/forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p).

모든 서신 관리 자산 및 관련 종속성을 패키지로 다운로드하려면 다음 단계를 완료하십시오.

1. Forms 사용자로 AEM Forms 서버에 로그인합니다.
1. 탭 **Adobe Experience Manager** 를 클릭합니다.
1. 도구 탭( ![tools-1](assets/tools-1.png)). **Forms**.
1. 탭 **서신 관리 자산 내보내기**.

   ![publish-cmp-assets](assets/publish-cmp-assets.png)

   [모든 서신 관리 자산 내보내기] 페이지가 나타나고 내보내기 프로세스가 마지막으로 시도된 시간과 마지막으로 성공적으로 내보낸 패키지를 다운로드할 수 있는 링크에 대한 정보가 표시됩니다.

   ![export-last-run-details](assets/export-last-run-details.png)

1. 탭 **내보내기** 확인 메시지에서 **확인**.

   배치 프로세스가 완료되면 마지막 실행 세부 정보와 패키지를 다운로드할 링크가 업데이트됩니다. 여기에는 관리자 로그인 및 배치 또는 &quot;n이 성공적으로 또는 실패한 경우 등의 정보가 포함됩니다. 자산이 패키지로 내보내지면 내보낸 패키지 다운로드 링크가 나타납니다.

   >[!NOTE]
   >
   >모든 자산 내보내기 프로세스를 시작한 후에는 취소할 수 없습니다. 또한 모든 내보내기 작업이 진행 중이면 자산을 생성, 삭제, 수정 또는 게시하거나 모든 자산 게시 프로세스를 시작하지 마십시오.a

1. 탭하기 **내보낸 패키지 다운로드** 를 눌러 패키지 파일을 다운로드합니다.

   패키지의 자산을 서신 관리의 다른 인스턴스에 추가하려면 [AEM Forms 인스턴스로 패키지 가져오기](/help/forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p).

### 문서 조각, 편지 및/또는 데이터 사전을 서신 관리로 가져오기 {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

.cmp 파일로 내보낸 자산을 가져올 수 있습니다. .cmp 파일에는 하나 이상의 문자, 데이터 사전, 문서 조각 및 종속 자산이 있을 수 있습니다.

>[!NOTE]
>
>마이그레이션을 위해 이전 서신 관리 자산을 가져오는 동안 관리 계정을 사용하여 로그인합니다. 이전 서신 관리 자산 마이그레이션에 대한 자세한 내용은 [AEM Forms 자산 및 문서 마이그레이션](/help/forms/using/migration-utility.md).

1. 데이터 사전, 문자 또는 문서 조각 페이지에서 **만들기 > 파일 업로드** .cmp 파일을 선택합니다.
1. 서신 관리에는 가져온 자산 목록이 있는 자산 가져오기 대화 상자가 표시됩니다. 탭 **가져오기**.

   자산을 가져온 후 자산의 다음 속성이 업데이트되고 다른 속성은 동일하게 유지됩니다.

   * 작성자: 자산을 서버에 가져온 사용자의 ID를 표시합니다
   * 수정됨: 자산을 서버에 가져온 시간

   >[!NOTE]
   >
   >XDP를 업로드하려면(cmp 파일의 일부나 다른 방법)에서 forms-power-users 그룹의 일부여야 합니다. 액세스 권한이 필요하면 관리자에게 문의하십시오.

## 워크플로우 애플리케이션 내보내기 {#export-a-workflow-application}

AEM 패키지 관리자를 사용하여 워크플로우 애플리케이션을 내보낼 수 있습니다. 절차는 다음과 같습니다.

1. AEM Forms 패키지 관리자를 엽니다. 패키지 관리자의 URL은 https:// 입니다.&lt;server>:&lt;port>/crx/packmgr.
1. 클릭 **[!UICONTROL 패키지 만들기]**. 다음 **[!UICONTROL 새 패키지]** 대화 상자가 나타납니다.
1. 패키지의 이름, 버전 및 그룹을 지정합니다. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.
1. 클릭 **[!UICONTROL 편집]** 그리고 **[!UICONTROL 필터]** 탭. 클릭 **[!UICONTROL 필터 추가]**. 워크플로 응용 프로그램의 경로를 지정합니다. 예를 들면 /etc/fd/dashboard/startpoints/assessortgage와 같습니다.

   클릭 **[!UICONTROL 규칙 추가]**.

1. **[!UICONTROL 고급]** 탭을 엽니다. 선택 **[!UICONTROL 병합]** 또는 **[!UICONTROL 덮어쓰기]** ACL 처리 필드에서 참조할 수 있습니다. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 클릭 **[!UICONTROL 빌드]** 패키지를 만들려면

   패키지가 빌드되면 패키지를 다운로드하여 다른 서버로 가져올 수 있습니다. Workflow 응용 프로그램은 패키지가 업로드된 서버에 나타납니다.

   >[!NOTE]
   >
   >워크플로우 애플리케이션이 제대로 작동하려면 해당 적응형 양식 및 워크플로우 모델을 작업 애플리케이션으로 내보냅니다.

## 폴더 및 자산 구성 {#folders-and-organizing-assets}

AEM Forms 사용자 인터페이스는 폴더를 사용하여 자산을 정렬합니다. 이러한 폴더는 AEM Forms 사용자 인터페이스 내에서 만든 자산을 배치하는 데 사용됩니다. 이러한 폴더에 자산 및 문서의 이름을 바꾸고 하위 폴더를 만들고 저장할 수 있습니다. 문서와 자산을 폴더에 구성하면 쉽게 관리할 수 있도록 파일을 함께 그룹화할 수 있습니다. 폴더를 선택하고 다운로드하거나 삭제할 수 있습니다.

폴더를 만들려면 다음 단계를 완료하십시오.

### 폴더를 만듭니다 {#create-a-folder}

1. 의 AEM Forms 사용자 인터페이스에 로그인합니다. `https://<server>:<port>/aem/forms.html`.
1. 폴더를 만들 위치로 이동합니다.
1. 만들기 > 폴더를 누릅니다.
1. 다음 세부 정보를 입력합니다.

   * **제목:** 폴더의 이름 표시
   * **이름:** *(필수입니다)* 저장소에 폴더를 저장할 노드 이름

   >[!NOTE]
   >
   >기본적으로 이름 필드의 값은 제목에서 자동으로 채워집니다. 이름에는 영숫자만 사용할 수 있고 하이픈(-)과 밑줄(_) 특수 문자만 사용할 수 있습니다. 제목에 입력한 다른 특수 문자는 하이픈으로 자동 대체되며 새 이름을 확인하라는 메시지가 표시됩니다. 제안된 이름을 계속 사용하거나 추가로 편집할 수 있습니다.

1. 정의한 제목이 있는 새 폴더가 자산 목록의 현재 위치에 표시됩니다.

   지정된 이름의 폴더가 있는 경우 오류가 발생하여 제출이 실패합니다. 마우스를 오류 위로 가져가면 오류 메시지를 볼 수 있습니다 ![aem6forms_error_alert](assets/aem6forms_error_alert.png) 이름 필드 옆에 표시되는 아이콘입니다.

   새로 만든 폴더를 탭하여 폴더 내로 이동하고 폴더 내에 자산 또는 폴더를 만들 수 있습니다. 또한 폴더를 선택하고 이 폴더를 다운로드하도록 큐에 올리거나 삭제하거나 이름을 편집할 수 있습니다.

   ![ededeletedownloadaflolder](assets/editdeletedownloadafolder.png)

### 하나 이상의 자산 또는 문자의 사본 만들기 {#create-copies-of-one-or-more-assets-or-letters}

기존 자산과 문자를 사용하여 비슷한 속성, 콘텐츠 및 상속된 자산과 문자를 신속하게 만들 수 있습니다. 데이터 사전, 문서 조각 및 문자를 복사하여 붙여넣을 수 있습니다.

다음 단계를 완료하여 자산 및 문자 사본을 만듭니다.

1. 관련 자산 또는 문자 페이지에서 하나 이상의 자산/문자를 선택합니다. UI에 복사 아이콘이 표시됩니다.
1. Tap Copy. UI에 붙여넣기 아이콘이 표시됩니다. 붙여넣기 전에 폴더 내에서 이동/탐색하도록 선택할 수도 있습니다. 서로 다른 폴더에는 동일한 이름의 자산이 포함될 수 있습니다. 폴더에 대한 자세한 내용은 [폴더 및 자산 구성](#folders-and-organizing-assets).
1. 붙여넣기 를 누릅니다. 붙여넣기 대화 상자가 나타납니다. 시스템에서는 자산/문자의 새 복사본에 이름과 제목을 자동으로 생성하지만 자산/문자의 제목 및 이름을 편집할 수 있습니다.

   자산/문자를 같은 위치에 복사하여 붙여넣는 경우 &quot;-CopyXX&quot; 접미사가 자산/문자의 기존 이름에 추가됩니다. 복사된 자산/편지에 대한 제목이 없는 경우 자동 생성된 제목 필드는 공백으로 유지됩니다.

1. 필요한 경우 자산/문자의 사본을 저장할 제목 및 이름 을 편집합니다.
1. 붙여넣기 를 누릅니다. 복사한 자산의 새 복사본이 만들어집니다.

## 검색 {#search-features}

AEM Forms UI를 통해 콘텐츠를 검색할 수 있습니다. 상단 막대를 사용하여 검색을 탭할 수 있습니다 **A** 컨텐츠를 검색하여 자산 및 문서와 같은 리소스를 찾습니다.

자산을 검색하면 AEM Forms에 사이드 패널이 표시됩니다. 탭할 수도 있습니다 ![assets-browser-content-only](assets/assets-browser-content-only.png) > 필터 **[B]** 사이드 패널을 호출하려면 사이드 패널에서 다양한 필터를 사용하여 검색 범위를 좁힐 수 있습니다. 사이드 패널에서는 검색을 저장할 수도 있습니다.

![search_topbar](assets/search_topbar.png)

**A.** 검색 **B.** 필터

![사이드 패널 - 필터](assets/search_sidepanel.png)
**그림:** *사이드 패널 - 필터*

사이드 패널에서 다음을 사용하여 검색 결과의 범위를 좁힐 수 있습니다.

* 검색 디렉터리
* 태그
* 검색 기준 예를 들어, 수정한 날짜, 게시 상태, Live Copy 상태 등이 있습니다.

사이드 패널에서는 원하는 이름으로 검색 설정을 저장할 수도 있습니다.

검색, 필터, 저장된 검색 및 사이드 패널 사용에 대한 자세한 내용 및 지침은 [검색](/help/sites-authoring/search.md).
