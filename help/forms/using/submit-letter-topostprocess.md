---
title: 편지 및 대화형 커뮤니케이션의 사후 처리
seo-title: Post Processing of Letters
description: Correspondence Management에서 편지 사후 처리를 사용하면 인쇄 및 이메일과 같은 AEM 및 Forms 게시 프로세스를 만들고 편지에 통합할 수 있습니다.
seo-description: Post Processing of Letters in Correspondence Management lets you create AEM and Forms post processes, such as print and email, and integrate them with your letters.
uuid: 4163bba9-e82b-4d3e-b1df-909855413a9e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 637342e8-fbdd-4cda-b175-56a805b3b480
feature: Correspondence Management
exl-id: d2dfdab8-815e-4378-b287-81e31c9d9333
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 1%

---

# 편지 및 대화형 커뮤니케이션의 사후 처리 {#post-processing-of-letters-and-interactive-communications}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 사후 처리 {#post-processing}

에이전트는 편지 및 대화형 커뮤니케이션에서 사후 처리 워크플로우를 연결 및 실행할 수 있습니다. 실행할 사후 프로세스는 편지 템플릿의 속성 보기에서 선택할 수 있습니다. 최종 편지를 전자 메일, 인쇄, 팩스 또는 보관하도록 사후 프로세스를 설정할 수 있습니다.

![사후 처리](assets/ppoverview.png)

게시 프로세스를 편지 또는 대화형 커뮤니케이션과 연결하려면 먼저 사후 프로세스를 설정해야 합니다. 제출된 편지에 두 가지 유형의 워크플로우를 실행할 수 있습니다.

1. **Forms Workflow:** JEE 프로세스 관리 워크플로우의 AEM Forms입니다. 설정 지침 [Forms Workflow](#formsworkflow).

1. **AEM 워크플로우:** AEM 워크플로우는 제출된 편지에 대한 사후 처리로도 사용할 수 있습니다. 설정 지침 [AEM 워크플로우](/help/forms/using/aem-forms-workflow.md).

## 양식 워크플로우 {#formsworkflow}

1. AEM에서 다음 URL을 사용하여 서버에 대한 Adobe Experience Manager 웹 콘솔 구성 을 엽니다. `https://<server>:<port>/<contextpath>/system/console/configMgr`

   ![구성 관리자](assets/2configmanager-1.png)

1. 이 페이지에서 AEM Forms 클라이언트 SDK 구성을 찾아 클릭하여 확장합니다.
1. 서버 URL에서 JEE 서버의 AEM Forms 이름과 로그인 세부 사항을 입력한 다음 를 클릭합니다 **저장**.

   ![LiveCycle 서버의 이름을 입력합니다](assets/1cofigmanager.png)

1. 사용자 이름과 암호를 지정합니다.
1. sun.util.calendar가 Deserialization Firewall Configuration에 추가되었는지 확인합니다.

   Deserialization Firewall Configuration으로 이동하고 패키지 접두사의 화이트리스트에 있는 클래스에서 sun.util.calendar를 추가합니다.

1. 이제 서버가 매핑되고 JEE의 AEM Forms의 게시물 프로세스는 AEM 사용자 인터페이스에서 문자를 만드는 동안 사용할 수 있습니다.

   ![게시물 프로세스가 나열된 편지 화면 만들기](assets/0configmanager.png)

1. 프로세스/서비스를 인증하려면 프로세스 이름을 복사하여 Adobe Experience Manager Web Console 구성 페이지 > AEM Forms Client SDK 구성으로 이동한 후 프로세스를 새 서비스로 추가합니다.

   예를 들어, 문자의 속성 페이지에 있는 드롭다운에 프로세스 이름이 Forms Workflow -> ValidCCPostProcess/SaveXML로 표시되면 서비스 이름을 로 추가합니다. `ValidCCPostProcess/SaveXML`.

1. 사후 처리를 위해 JEE 워크플로우에서 AEM Forms을 사용하려면 필요한 매개 변수 및 출력을 설정합니다. 매개 변수의 기본값은 아래에 표시되어 있습니다.

   Adobe Experience Manager 웹 콘솔 구성 페이지로 이동 > **[!UICONTROL 서신 관리 구성]** 다음 매개 변수를 설정합니다.

   1. **inPDFDoc(PDF 문서 매개 변수):** PDF 문서를 입력으로 사용합니다. 이 입력에는 렌더링된 문자가 입력으로 포함됩니다. 표시된 매개변수 이름은 구성할 수 있습니다. 서신 관리 구성에서 구성할 수 있습니다.
   1. **inXMLDoc(XML 데이터 매개 변수):** XML 문서를 입력으로 사용합니다. 이 입력에는 사용자가 입력한 데이터가 XML 형식으로 포함되어 있습니다.
   1. **inXDPDoc(XDP 문서 매개 변수):** XML 문서를 입력으로 사용합니다. 이 입력에 기본 레이아웃(XDP)이 포함되어 있습니다.
   1. **inAttachmentDocs(첨부 문서 매개 변수):** 목록 입력 매개 변수입니다. 이 입력에는 모든 첨부 파일이 입력으로 포함됩니다.
   1. **redirectURL(리디렉션 URL 출력):** 리디렉션할 URL을 나타내는 출력 유형입니다.

   양식 워크플로우에는 PDF 문서 매개 변수 또는 XML 데이터 매개 변수가 지정된 이름과 동일한 이름으로 입력되어 있어야 합니다. **[!UICONTROL 서신 관리 구성]**. 이 단계는 게시 프로세스 드롭다운에 나열된 프로세스를 위해 필요합니다.

## 게시 인스턴스의 설정 {#settings-on-the-publish-instance}

1. 로그인 `http://localhost:publishport/aem/forms`.
1. 다음으로 이동 **[!UICONTROL 문자]** 게시 인스턴스에서 사용할 수 있는 게시된 문자를 보려면 다음을 수행하십시오.
1. AEM DS 설정을 구성합니다. 자세한 내용은 [AEM DS 설정 구성](/help/forms/using/configuring-the-processing-server-url-.md).

>[!NOTE]
>
>Forms 또는 AEM 워크플로우를 사용하는 동안 게시 서버에서 제출하기 전에 DS 설정 서비스를 구성해야 합니다. 그렇지 않으면 양식 제출이 실패합니다.

## 편지 인스턴스 검색 {#letter-instances-retrieval}

LetterInstanceService에 정의된 다음 API를 사용하여 편지 인스턴스 검색 및 편지 인스턴스 삭제와 같은 저장된 편지 인스턴스를 추가로 조작할 수 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>서버 측 API</strong></td> 
   <td><strong>작업 이름</strong></td> 
   <td><strong>설명</strong></td> 
  </tr> 
  <tr> 
   <td><p>공용 LetterInstanceVO</p> <p>getLetterInstance(String letterInstanceId)</p> <p>ICCException을 던집니다. </p> </td> 
   <td>getLetterInstance</td> 
   <td>지정한 편지 인스턴스를 가져옵니다. </td> 
  </tr> 
  <tr> 
   <td>public void deleteLetterInstance(String letterInstanceId)에 ICCException이 발생합니다. </td> 
   <td>deleteLetterInstance </td> 
   <td>지정한 편지 인스턴스를 삭제했습니다. </td> 
  </tr> 
  <tr> 
   <td>List getAllLetterInstances(Query)에 ICCException이 발생합니다. </td> 
   <td>getAllLetterInstances </td> 
   <td>이 API는 입력 쿼리 매개 변수를 기반으로 문자 인스턴스를 가져옵니다. 모든 편지 인스턴스를 가져오려면 쿼리 매개 변수를 null로 전달할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>공용 부울 letterInstanceExists(String letterInstanceName)에 ICCException;이 발생합니다. </td> 
   <td>letterInstanceExists </td> 
   <td>LetterInstance가 지정된 이름으로 존재하는지 확인합니다. </td> 
  </tr> 
 </tbody> 
</table>

## 게시물 프로세스를 편지와 연결 {#associating-a-post-process-with-a-letter}

CCR 사용자 인터페이스에서 다음 단계를 완료하여 게시 프로세스를 편지와 연결합니다.

1. 편지 위로 마우스를 가져간 다음 탭하기 **속성 보기**.
1. **편집**&#x200B;을 선택합니다.
1. 기본 속성에서 게시 프로세스 드롭다운을 사용하여 편지에 연결할 사후 프로세스를 선택합니다. AEM 및 Forms 관련 게시물 프로세스가 모두 드롭다운에 나열됩니다.
1. 탭 **저장**.
1. 게시 프로세스를 사용하여 편지를 구성한 후 편지를 게시하고 선택적으로 게시 인스턴스에서 처리 URL을 AEM DS 설정 서비스에 지정합니다. 이렇게 하면 처리 인스턴스에서 사후 프로세스가 실행됩니다.

## 초안 편지 인스턴스 다시 로드  {#reloaddraft}

다음 URL을 사용하여 사용자 인터페이스에서 초안 편지 인스턴스를 다시 로드할 수 있습니다.

`https://<server>:<port>/aem/forms/`

`createcorrespondence.html?/random=$&cmLetterInstanceId=$<LetterInstanceId>`

LetterInstanceID: 제출된 편지 인스턴스의 고유 ID입니다.

초안 편지 저장에 대한 자세한 내용은 [초안 저장 및 편지 인스턴스 제출](/help/forms/using/create-correspondence.md#savingdrafts).
