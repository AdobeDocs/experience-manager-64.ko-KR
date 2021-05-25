---
title: 'OSGi 및 AEM Forms JEE 워크플로우에서 양식 중심의 AEM 워크플로우의 작업 및 기능 '
seo-title: 'OSGi 및 AEM Forms JEE 워크플로우에서 양식 중심의 AEM 워크플로우의 작업 및 기능 '
description: AEM 받은 편지함 및 HTML 작업 영역에서 지원되는 작업의 차이점, OSGi 및 AEM Forms JEE Workflows의 양식 중심의 AEM Workflows에서 지원하는 기능의 차이점, AEM 받은 편지함 및 AEM Forms 앱 기능의 차이점에 대해 자세히 알아보십시오.
seo-description: AEM 받은 편지함 및 HTML 작업 영역에서 지원되는 작업의 차이점, OSGi 및 AEM Forms JEE Workflows의 양식 중심의 AEM Workflows에서 지원하는 기능의 차이점, AEM 받은 편지함 및 AEM Forms 앱 기능의 차이점에 대해 자세히 알아보십시오.
uuid: ce2a05fe-ba45-42ed-880e-fb1d6efc1d26
contentOwner: khsingh
topic-tags: publish
discoiquuid: 4c7ba430-25b2-4ba2-a5eb-4edaed0d599a
exl-id: 6172d936-9348-4f3f-a437-6465dd156f3b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 18%

---

# OSGi 및 AEM Forms JEE 워크플로우에서 양식 중심의 AEM 워크플로우의 작업 및 기능 {#actions-and-capabilities-of-form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

## AEM 받은 편지함 및 HTML 작업 공간 {#aem-inbox-and-html-workspace}

AEM 받은 편지함은 OSGi에서 Forms 중심의 AEM 워크플로우를 실행하고 모니터링하는 데 사용됩니다. HTML 작업 공간을 사용하면 AEM Forms JEE 워크플로우를 실행하고 모니터링할 수 있습니다. 다음 표에는 OSGi의 Forms 중심의 AEM 워크플로우를 위한 AEM 받은 편지함 및 AEM Forms JEE Workflows의 HTML 작업 공간에서 사용할 수 있는 중요한 작업이 나와 있습니다.

<table> 
 <tbody>
  <tr>
   <td>작업</td> 
   <td>AEM 받은 편지함</td> 
   <td>HTML 작업 공간</td> 
  </tr>
  <tr>
   <td>프로세스, 작업 또는 양식 응용 프로그램 시작<br /> </td> 
   <td>지원됨<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>작업 제출</td> 
   <td>지원됨<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>그룹에 작업 할당</td> 
   <td>지원됨<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>여러 경로에 제출</td> 
   <td>지원됨<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>작업 내역 및 작업 요약 추적</td> 
   <td>지원됨<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>이메일 알림</td> 
   <td>지원됨<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>작업 재지정</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>적응형 양식의 필드 수준 첨부 파일</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>달력 보기</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>작업 수준 설명</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>큐(공유 개인 큐, 큐의 클레임 작업)</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>부재 중 알림</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>여러 사용자에게 작업 할당</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
 </tbody>
</table>

## OSGi 및 AEM Forms JEE 워크플로우의 양식 중심의 AEM 워크플로우 {#form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

OSGi 및 AEM Forms JEE 워크플로우의 양식 중심의 AEM 워크플로우(JEE 프로세스 관리의 AEM Forms)에는 서로 다른 기능 세트가 있습니다. 다음 표에는 OSGi의 양식 중심의 AEM 워크플로우 및 JEE 워크플로우의 AEM Forms 기능에 사용할 수 있는 중요한 기능과 지원이 나와 있습니다.

<table> 
 <tbody>
  <tr>
   <td>기능</td> 
   <td>OSGi<br />의 양식 중심의 AEM 워크플로우 </td> 
   <td>AEM Forms JEE 워크플로우</td> 
  </tr>
  <tr>
   <td>적응형 양식</td> 
   <td>지원됨</td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>다른 AEM 솔루션과 통합</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>낙서 서명</td> 
   <td>지원됨</td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>사용자 지정 이메일 템플릿</td> 
   <td>지원됨</td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>작업 우선 순위 정의</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>기한 후 작업 시간 초과</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>워크플로우 내에서 루프</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>할당자를 동적으로 선택 </td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>사용자 지정 메타데이터 사용</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>전자 서명(Adobe Sign)</td> 
   <td>지원되는 <sup>[1]</sup></td> 
   <td>지원되는 <sup>[5]</sup></td> 
  </tr>
  <tr>
   <td>작업 및 양식 애플리케이션 관리</td> 
   <td>지원되는 <sup>[2]</sup><br /> </td> 
   <td>지원되는 <sup>[2]</sup></td> 
  </tr>
  <tr>
   <td>문서 서비스</td> 
   <td>지원되는 <sup>[3]</sup></td> 
   <td>지원되는 <sup>[3]</sup></td> 
  </tr>
  <tr>
   <td>완료된 작업을 적응형 양식 또는 PDF 문서로 렌더링</td> 
   <td>지원됨</td> 
   <td>지원됨 [4]</td> 
  </tr>
  <tr>
   <td>서신 관리와 통합</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>재설정 단추</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>워크플로우 단계</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>읽기 전용 적응형 양식</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>기본 저장 단추 숨기기</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>워크플로우 세부 사항 섹션을 세부적으로 제어</td> 
   <td>지원됨</td> 
   <td>지원되지 않음</td> 
  </tr>
  <tr>
   <td>HTML5 Forms, 대화형 PDF forms, 양식 세트<br /> </td> 
   <td>지원되지 않음<br /> </td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>프로세스 보고</td> 
   <td>지원되지 않음<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>디지털 서명</td> 
   <td>지원됨<br /> </td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>시작 지점 카테고리</td> 
   <td>지원되지 않음 </td> 
   <td>지원됨 </td> 
  </tr>
  <tr>
   <td>일괄 작업 승인 </td> 
   <td>지원되지 않음 </td> 
   <td>지원됨 </td> 
  </tr>
  <tr>
   <td>사용자 지정 이름으로 초안 저장</td> 
   <td>지원되지 않음 </td> 
   <td>지원됨 </td> 
  </tr>
  <tr>
   <td>기존 프로세스 데이터를 사용하여 프로세스 시작<br /> </td> 
   <td>지원되지 않음</td> 
   <td>지원됨 </td> 
  </tr>
  <tr>
   <td>시작점을 초안으로 저장</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>사용자 아바타</td> 
   <td>지원됨</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>관리자 보기</td> 
   <td>지원되지 않음</td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>검색 템플릿</td> 
   <td>지원되지 않음</td> 
   <td>지원됨<br /> </td> 
  </tr>
  <tr>
   <td>타사 애플리케이션과의 통합</td> 
   <td>지원되는 <sup>[6]</sup></td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>워크플로 응용 프로그램 또는 시작점에 대한 작업 수준 첨부 파일</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>미리 알림 이메일</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>작업 시간 제한 시 제목 변경</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>작업 위임 및 작업 클레임에 대한 전자 메일</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>워크플로우가 끝나면 이메일 보내기</td> 
   <td>지원되는 <sup>[7]</sup></td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>분리된 그룹 간 위임</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>워크플로우에서 웹 서비스 호출</td> 
   <td>지원되는 <sup>[6]</sup></td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>XSLT 변환</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>게이트웨이, 대기 없음</td> 
   <td>지원됨 </td> 
   <td>지원됨 </td> 
  </tr>
  <tr>
   <td>또는, 분할</td> 
   <td>지원되지 않음</td> 
   <td>지원됨</td> 
  </tr>
  <tr>
   <td>동적 작업 우선 순위</td> 
   <td>지원되지 않음</td> 
   <td>지원되지 않음</td> 
  </tr>
 </tbody>
</table>

1. OSGi에서 양식 중심의 AEM 워크플로우를 사용하여 이미 채워진 적응형 양식에 서명할 수 있습니다. OSGi의 양식 중심의 AEM 워크플로우는 양식 서명을 지원합니다. [양식 서명](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience) 경험은 지원되지 않습니다.

1. AEM Forms JEE 워크플로우를 실행하고 모니터링하려면 AEM Forms OSGi AEM 워크플로우 및 HTML 작업 공간을 실행하고 모니터링하려면 AEM 받은 편지함에 액세스할 수 있어야 합니다.
1. 기본 AEM Forms 문서 서비스는 OSGi의 양식 중심의 AEM 워크플로우와 JEE 워크플로우의 AEM Forms 모두에서 사용할 수 있습니다. AEM Workflow는 OSGi 및 AEM Forms JEE(Process Management) 워크플로우의 양식 중심의 AEM Workflows에 기본 문서 서비스를 사용합니다.
1. AEM Forms JEE 워크플로우는 적응형 양식만 렌더링할 수 있습니다. 적응형 양식을 PDF 문서로 렌더링하는 것을 지원하지 않습니다.
1. AEM Forms JEE Workflows에는 Adobe Sign에 대한 별도의 단계가 없습니다. AEM Forms JEE 워크플로우에 대해 Adobe Sign 활성화 적응형 양식이 필요합니다. 자세한 내용은 [Adobe Sign 설명서](/help/forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component)를 참조하십시오.
1. [양식 데이터 모델 서비스 호출](/help/forms/using/aem-forms-workflow-step-reference.md#p-invoke-form-data-model-service-step-p) 단계를 사용하여 웹 서비스 서비스를 호출하고 타사 애플리케이션에서 데이터를 게시하거나 검색할 수 있습니다.
1. [이메일 보내기](/help/forms/using/aem-forms-workflow-step-reference.md#send-email-step) 단계를 사용하여 전자 메일을 보낼 수 있습니다.

## AEM 받은 편지함과 AEM Forms 앱 기능 간의 차이점 {#differences-between-aem-inbox-and-aem-forms-app-features}

Forms 중심의 워크플로우를 시작하는 두 가지 주목할 만한 방법은 [AEM Inbox](/help/forms/using/manage-applications-inbox.md) 및 AEM Forms 앱을 사용하는 것입니다. 그러나 AEM 받은 편지함 및 AEM Forms 앱의 기능은 서로 다릅니다. AEM 받은 편지함은 [Forms 중심의 워크플로우](/help/forms/using/aem-forms-workflow.md)에서만 작동하지만 AEM Forms 앱은 Forms 중심의 워크플로우뿐만 아니라 프로세스 관리에서도 작동합니다.

다음 표에는 AEM 받은 편지함 및 AEM Forms 앱의 기능이 나와 있습니다.

<table> 
 <tbody>
  <tr>
   <td><p><strong>작업</strong></p> </td> 
   <td><p><strong>AEM 받은 편지함</strong></p> </td> 
   <td><p><strong>AEM Forms 앱</strong></p> </td> 
  </tr>
  <tr>
   <td><p>양식 애플리케이션 시작</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr>
  <tr>
   <td><p>작업 제출</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr>
  <tr>
   <td><p>작업 위임</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원되지 않음</p> </td> 
  </tr>
  <tr>
   <td><p>작업 내역 및 작업 요약 추적</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원되지 않음</p> </td> 
  </tr>
  <tr>
   <td><p>작업 수준 첨부 파일 추가</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr>
  <tr>
   <td><p>작업 수준 첨부 파일 보기</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr>
  <tr>
   <td><p>필드 수준 첨부 파일 추가</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr>
  <tr>
   <td><p>달력 보기 표시</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원되지 않음</p> </td> 
  </tr>
  <tr>
   <td><p>댓글 추가</p> </td> 
   <td><p>지원됨</p> </td> 
   <td><p>지원됨</p> </td> 
  </tr>
 </tbody>
</table>
