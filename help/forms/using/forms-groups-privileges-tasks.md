---
title: OSGi 그룹 및 권한의 AEM Forms
seo-title: AEM Forms on OSGi Groups and Privileges
description: OSGi에서 AEM Forms을 관리할 그룹에 사용자 할당
seo-description: Assign users to the groups to manage AEM Forms on OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: Admin
exl-id: a79e863e-c316-422e-a565-b0ffdeffcc00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 4%

---

# OSGi 그룹 및 권한의 AEM Forms {#aem-forms-on-osgi-groups-and-privileges}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

OSGi에서 AEM Forms을 관리할 그룹에 사용자 할당

다음을 수행할 수 있습니다 [그룹 만들기](/help/sites-administering/user-group-ac-admin.md#group-administration) 정책 및 할당 [사용자](/help/sites-administering/user-group-ac-admin.md#user-administration) 추가 콘텐츠는 AEM의 그룹에 속해 있어야 합니다. 이러한 정책은 그룹에 속하는 사용자의 권한을 제어합니다.

설치한 후 [AEM Forms 추가 기능 패키지](/help/forms/using/installing-configuring-aem-forms-osgi.md)에서는 forms-user 및 forms-power-user와 같이 이 문서에 언급된 그룹을 자동으로 할당에 사용할 수 있습니다. 다음 표에는 그룹 할당을 기반으로 사용자가 OSGi에서 AEM Forms에 대해 수행할 수 있는 작업이 나열되어 있습니다.

<table> 
 <tbody>
  <tr>
   <td>그룹</td> 
   <td>작업</td> 
  </tr>
  <tr>
   <td>forms-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>적응형 양식 만들기, 미리 보기, 게시 및 제출</li> 
     <li>대화형 커뮤니케이션 및 문서 조각 만들기, 미리 보기 및 게시</li> 
     <li>AEM 인스턴스에 자산 업로드</li> 
     <li>테마 만들기</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>적응형 양식 만들기, 미리 보기, 게시 및 제출</li> 
     <li>대화형 커뮤니케이션 및 문서 조각 만들기, 미리 보기 및 게시</li> 
     <li>코드 편집기를 사용하여 적응형 양식의 스크립트 만들기</li> 
     <li>스크립트를 포함한 자산 업로드</li> 
     <li>테마 만들기</li> 
     <li>XDP가 포함된 패키지 가져오기</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms 제출 검토자</td> 
   <td>
    <ul> 
     <li>제출 검토</li> 
     <li>제출 승인 또는 거부</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>적응형 양식 또는 대화형 커뮤니케이션 템플릿 만들기 및 미리 보기</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>양식 데이터 모델 만들기 및 수정</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-user-agent</td> 
   <td>
    <ul> 
     <li>에이전트 UI를 사용하여 서신 관리 편지 또는 대화형 커뮤니케이션에 액세스</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>받은 편지함 애플리케이션 만들기</li> 
     <li>워크플로우 모델 만들기</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>AEM 받은 편지함 애플리케이션 사용</li> 
     <li>워크플로우 인스턴스 관리</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>PDF 생성기 구성</li> 
     <li>감시 폴더 구성</li> 
     <li>워크플로우 애플리케이션 관리</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. 양식 사용자 그룹 권한이 있는 사용자는 적응형 양식에 대한 스크립트를 작성할 수 없습니다.
1. 템플릿 작성자 그룹 권한이 있는 사용자는 템플릿에 대한 스크립트를 작성할 수 없습니다.
