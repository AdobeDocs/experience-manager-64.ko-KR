---
title: Touch UI 기능 상태
seo-title: Touch UI 기능 상태
description: Adobe Experience Manager 6.3 터치 UI에만 적용되는 릴리스 노트입니다.
seo-description: Adobe Experience Manager 6.3 터치 UI에만 적용되는 릴리스 노트입니다.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
translation-type: tm+mt
source-git-commit: db26dd05f6c0997eeda462f27971cbcfa6737527
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 15%

---


# Touch UI 기능 상태 {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 버전 6.4에서는 [클래식 UI가 더 이상 사용되지 않습니다](/help/release-notes/deprecated-removed-features.md). Adobe은 클래식 UI를 추가로 개선할 계획이 없으며, 사용자는 터치 지원 UI에서 사용할 수 있는 강력한 새로운 기능을 활용할 수 있습니다.

버전 6.0부터 AEM은 Adobe Marketing Cloud 및 전체 Adobe 사용자 인터페이스 가이드라인에 정렬된 &quot;터치 지원 UI&quot;(간단히 &quot;터치 UI&quot;라고도 함)라는 새로운 사용자 인터페이스를 도입했습니다. 거의 모든 기능이 이에 도달했습니다. 이는 &quot;클래식 UI&quot;라고 하는 레거시 데스크톱 기반 인터페이스를 사용하는 AEM의 표준 UI가 되었습니다.

대부분의 기능이 터치 지원 UI에 있지만 아직 완전하지 않은 기능이 있으며 향후 릴리스에 추가될 예정입니다.

다음 목록은 AEM 6.4에 구현된 기능의 현재 상태를 보여줍니다.

AEM 6.4로 업그레이드하는 고객을 위한 권장 사항은 [고객을 위한 사용자 인터페이스 Recommendations](/help/sites-deploying/ui-recommendations.md)를 참조하십시오.

>[!NOTE]
>
>이 페이지는 클래식 UI의 기능 패리티만 다룹니다.
>
>클래식 UI에 없는 터치 지원 UI에 추가되거나 고유한 기능은 나열되지 않습니다.

>[!NOTE]
>
>이 목록은 완성을 위해 노력하고 있지만 철저한 것으로 간주해서는 안 된다.

## 범례 {#legend}

* **완료**:이 기능은 터치 지원 UI에서 사용할 수 있습니다.
* **대부분**:이 기능은 대부분 터치 지원 UI에서 사용할 수 있습니다.
* **누락**:터치 활성화 UI에 이 기능이 없으면 클래식 UI를 사용하여 이 작업을 수행해야 합니다.
* **교체**:이 기능은 다르게 작동하는 새 구현으로 대체되었습니다.
* **제거됨**:이 기능은 터치 지원 UI에 더 이상 존재하지 않으며 바뀌지 않습니다.

## 기능 상태:사이트 관리자 {#feature-status-sites-admin}

클래식 UI 사이트 관리자( `/siteadmin`)의 기능과 터치가 활성화된 UI( `/sites.html`)의 상태입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>기능<br /> </strong></td> 
   <td><strong>상태<br /> </strong></td> 
   <td><strong>주석</strong></td> 
  </tr>
  <tr>
   <td>사이트 계층 탐색</td> 
   <td>완료<br /> </td> 
   <td>AEM 6.4는 <a href="/help/sites-authoring/basic-handling.md#content-tree">컨텐트 트리 보기</a>를 도입했습니다.</td> 
  </tr>
  <tr>
   <td>워크플로우 시작</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>새 페이지 만들기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>새 사이트 만들기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>새 론치 만들기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>새 livecopy <br /> 만들기 </td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>폴더 만들기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>게시 상태 표시</td> 
   <td>대부분</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>검색</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 복사/붙여넣기(복제)</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 이동</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 게시</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>복제 권한이 없는 페이지 게시</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>나중에 게시</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>트리 게시</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 게시 취소</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>복제 권한이 없는 페이지 게시 취소</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>나중에 게시 취소</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>삭제</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>잠금/잠금 해제</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>속성 보기/편집</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지에 대한 권한 설정</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>버전 내역</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>버전 복원</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>트리 복원 및 삭제된 페이지 복원</td> 
   <td>누락</td> 
   <td>클래식 UI 사용을 참조하십시오.</td> 
  </tr>
  <tr>
   <td>이전 버전과 현재 버전 간 차이 표시<br /> </td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Livecopy 작업(롤아웃)</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>언어 사본 보기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>찾기 및 바꾸기</td> 
   <td>누락된 항목<br /> </td> 
   <td>클래식 UI 사용을 참조하십시오.</td> 
  </tr>
  <tr>
   <td>알림 받은 편지함(JCR 이벤트)</td> 
   <td>누락</td> 
   <td>클래식 UI 사용을 참조하십시오. 다른 구현으로 대체됩니다.</td> 
  </tr>
  <tr>
   <td>참조</td> 
   <td>대부분</td> 
   <td>들어오는 페이지 링크 표시가 AEM 2019 릴리스에서 추가됩니다.</td> 
  </tr>
 </tbody>
</table>

## 기능 상태:페이지 편집기 {#feature-status-page-editor}

클래식 UI 페이지 편집기( `/cf#`)에 있는 기능 목록과 터치 활성화 상태( `/editor.html`)입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>기능</strong></td> 
   <td><strong>상태</strong></td> 
   <td><strong>주석</strong></td> 
  </tr>
  <tr>
   <td>웹 페이지 편집</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>모바일 웹 페이지 편집<br /> </td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>디자인 가져오기 도구<br />를 통해 가져온 내용 편집 </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>이메일 편집</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>모바일 앱 편집</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Forms 편집</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>오퍼 편집</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>워크플로우 모델 편집<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>ode:편집 및 미리 보기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>반응형 미리 보기<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>모드:디자인 편집</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>모드:Scaffolding</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>모드:Live Copy 상태<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>주석 추가</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>속성 편집<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>롤아웃 페이지</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>워크플로우 시작 및 표시</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>워크플로우 패키지 처리</td> 
   <td>대부분</td> 
   <td>터치 지원 UI에서 완벽하게 액세스할 수 있습니다. 여러 워크플로 페이로드가 여전히 클래식 UI에 표시됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>페이지 잠금/잠금 해제</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 게시 <br /> </td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 게시 취소</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 복사</td> 
   <td>제거됨<br /> </td> 
   <td>사이트 관리자를 사용하여 <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">페이지</a>를 복사합니다.<br /> </td> 
  </tr>
  <tr>
   <td>페이지 이동</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하여 <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">페이지 이동</a>.<br /> </td> 
  </tr>
  <tr>
   <td>페이지 삭제</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하여 <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">페이지 삭제</a>.<br /> </td> 
  </tr>
  <tr>
   <td>참조 표시</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하여 <a href="/help/sites-authoring/author-environment-tools.md#references">자세한 참조 목록</a>.<br /> </td> 
  </tr>
  <tr>
   <td>감사 로그</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하고 <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">활동 레일 열기</a>.<br /> </td> 
  </tr>
  <tr>
   <td>버전 만들기</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하여 <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">새 버전</a>을 만듭니다.<br /> </td> 
  </tr>
  <tr>
   <td>버전 복원</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하여 <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">버전</a>을(를) 복원합니다.</td> 
  </tr>
  <tr>
   <td>론치 전환</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하여 <a href="/help/sites-authoring/launches-promoting.md">론치</a> 간을 전환합니다.<br /> </td> 
  </tr>
  <tr>
   <td>페이지 번역</td> 
   <td>제거됨</td> 
   <td>사이트 관리자를 사용하여 번역 프로젝트<a href="/help/sites-administering/tc-manage.md">에 페이지를 추가합니다.</a><br /> </td> 
  </tr>
  <tr>
   <td>타임워프(날짜/시간 선택 및 검색 사이트 선택)<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>권한 설정</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>클라이언트 컨텍스트 UI<br /> </td> 
   <td>대체됨</td> 
   <td>앞으로 <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> UI를 사용합니다.</td> 
  </tr>
  <tr>
   <td>다양한 미디어 유형에 대한 컨텐츠 파인더<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>구성 요소 목록</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>구성 요소 복사 및 붙여넣기<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>클립보드의 구성 요소 목록</td> 
   <td>누락</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>실행 취소/다시 실행</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>컨텐츠를 구성 요소 자리 표시자로 드래그하여 놓기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>구성 요소 자동 생성<br />을 사용하여 내용을 parsys 자리 표시자로 바로 드래그하여 놓기 </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 기능 상태:텍스트, 표 및 이미지 편집기 {#feature-status-text-table-and-image-editors}

클래식 UI 텍스트, 표 및 이미지 편집기의 기능 목록과 터치 지원 UI의 상태입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>기능</strong></td> 
   <td><strong>상태 </strong></td> 
   <td><strong>주석<br /> </strong></td> 
  </tr>
  <tr>
   <td>리치 텍스트 편집기</td> 
   <td>완료</td> 
   <td>즉석, 대화 상자 및 전체 화면에서 사용할 수 있습니다.</td> 
  </tr>
  <tr>
   <td>RTE 플러그인 활성화/비활성화</td> 
   <td>완료<br /> </td> 
   <td><a href="/help/sites-authoring/templates.md">템플릿 편집기</a>를 사용하여 수행할 수 있습니다.</td> 
  </tr>
  <tr>
   <td>일반 텍스트에 RTE 사용</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:링크 및 앵커</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:문자 맵</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:복사/붙여넣기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:Microsoft Word<br />에서 붙여넣기 </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:찾기 및 바꾸기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:텍스트 형식(굵게, ...)</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:아래 위 첨자 및 위 첨자</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:양쪽 정렬</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:목록(글머리 기호/번호)</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:단락 서식</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:텍스트 스타일</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:소스 편집기(HTML 편집)<br /> </td> 
   <td>완료<br /> </td> 
   <td>대화 상자 및 전체 화면에서만 사용할 수 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:맞춤법 검사기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:표(포함된 테이블 편집기)</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:실행 취소/다시 실행<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE 플러그인:인라인 이미지 허용</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>표 편집기</td> 
   <td>완료</td> 
   <td>즉석, 대화 상자 및 전체 화면에서 사용할 수 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>이미지를 표 셀에 드래그하여 놓기<br /> </td> 
   <td>완료</td> 
   <td>인라인 사용 가능</td> 
  </tr>
  <tr>
   <td>이미지 편집기<br /> </td> 
   <td>완료</td> 
   <td>즉석, 대화 상자 및 전체 화면에서 사용할 수 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>IPE 플러그인 활성화/비활성화</td> 
   <td>완료</td> 
   <td>이제 <a href="/help/sites-authoring/templates.md">템플릿 편집기</a>에 UI가 있습니다.</td> 
  </tr>
  <tr>
   <td>IPE 플러그인:자르기</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE 플러그인:뒤집기</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE 플러그인:실행 취소/다시 실행</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE 플러그인:이미지 맵</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE 플러그인:회전</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE 플러그인:확대/축소</td> 
   <td>완료<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 기능 상태:도구 {#feature-status-tools}

클래식 UI에 있는 다양한 도구 목록과 터치 지원 UI의 상태입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>기능<br /> </strong></td> 
   <td><strong>상태<br /> </strong></td> 
   <td><strong>주석</strong></td> 
  </tr>
  <tr>
   <td>작업 관리</td> 
   <td>대체됨</td> 
   <td>6.0은 <a href="/help/sites-authoring/projects.md">프로젝트 및 작업</a>을(를) 도입했습니다.<br /> </td> 
  </tr>
  <tr>
   <td>Workflow 받은 편지함<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>페이지 템플릿 구성 워크플로(<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>누락된 항목<br /> </td> 
   <td>클래식 UI 사용을 참조하십시오.</td> 
  </tr>
  <tr>
   <td>관리자 UI 태그 지정<br /> </td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>MSM/블루프린트 제어 센터</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>블루프린트 관리자 UI</td> 
   <td>완료</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>롤아웃 구성 UI</td> 
   <td>누락</td> 
   <td>클래식 UI 사용을 참조하십시오.</td> 
  </tr>
  <tr>
   <td>사용자, 그룹 및 권한 UI<br /> </td> 
   <td>대부분 완료<br /> </td> 
   <td>고급 권한 편집의 경우 클래식 UI를 사용합니다.<br /> </td> 
  </tr>
  <tr>
   <td>버전 제거(<code>/etc/versioning/purge.html</code>)</td> 
   <td>누락</td> 
   <td>클래식 UI 사용을 참조하십시오.</td> 
  </tr>
  <tr>
   <td>외부 링크 확인 (<code>/etc/linkchecker.html</code>)</td> 
   <td>누락</td> 
   <td>클래식 UI 사용<br /> </td> 
  </tr>
  <tr>
   <td>벌크 편집기(<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>누락된 항목<br /> </td> 
   <td>클래식 UI 사용을 참조하십시오.</td> 
  </tr>
 </tbody>
</table>

