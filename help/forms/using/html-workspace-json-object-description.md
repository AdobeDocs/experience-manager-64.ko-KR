---
title: AEM Forms 작업 공간 JSON 개체 설명
seo-title: AEM Forms workspace JSON object description
description: 사용자 지정, 확장, 수정 및 재사용을 위해 AEM Forms 작업 공간에 사용되는 JSON JavaScript 개체에 대한 개념적 정보입니다.
seo-description: Conceptual information about the JSON JavaScript objects used in LiveCycle AEM Forms workspace for customization, extension, modification, and reuse.
uuid: 91c923c8-144a-4453-ba91-6a5193f1c4c4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 61b7246d-ed28-4470-a0a2-a4aaf1a061a4
exl-id: 8c7e1ee2-0f7f-427e-aca2-d4bf523fd7f1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2145'
ht-degree: 2%

---

# AEM Forms 작업 공간 JSON 개체 설명 {#aem-forms-workspace-json-object-description}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 작업 공간에 사용되는 JSON 개체는 아래에 설명되어 있습니다.

1. 범주

   카테고리는 작업 공간의 시작 프로세스 탭에 있습니다. 이러한 카테고리는 시작점을 분류하는 데 사용됩니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>이름</td> 
   <td>F</td> 
   <td>카테고리 이름</td> 
  </tr>
  <tr>
   <td>id</td> 
   <td>F</td> 
   <td>카테고리 ID<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>설명<br type="_moz" /> </td> 
   <td>F</td> 
   <td>카테고리 설명<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>parentOid<br type="_moz" /> </td> 
   <td>F</td> 
   <td>상위 카테고리의 oid 포함<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>startPointsList<br type="_moz" /> </td> 
   <td>T</td> 
   <td>카테고리에 있는 모든 시작점 목록을 포함합니다</td> 
  </tr>
  <tr>
   <td>categoryList</td> 
   <td>T</td> 
   <td>카테고리의 직접 하위 카테고리 목록을 포함합니다<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>모든 시작점과 즐겨찾기는 클라이언트 측에 정의된 카테고리입니다. 즐겨찾기 카테고리에는 사용자가 즐겨찾기로 표시한 모든 시작점이 포함됩니다. 모든 시작점 카테고리에 모든 시작점이 포함됩니다.

1. Startpoint

   시작점은 호출될 때 작업공간에서 프로세스를 시작하는 데 사용됩니다.

   | **속성** | **클라이언트만** | **댓글** |
   |---|---|---|
   | categoryId | F | 여기에는 시작점이 속한 카테고리의 ID가 포함되어 있습니다. |
   | 설명 | F | 여기에는 시작점에 대한 설명이 포함되어 있습니다. |
   | 이름 | F | 여기에는 시작점의 이름이 포함되어 있습니다. |
   | serializedImageTicket | F | 시작점에 해당하는 이미지 티켓이 포함되어 있습니다. 이 이미지 티켓은 서버에서 시작점에 대한 이미지를 가져오기 위해 startpoint의 imageUrl 필드에 사용됩니다. |
   | serviceName | F | 여기에는 startpoint에 대한 서비스 이름이 포함되어 있습니다. |
   | startpointId | F | 여기에는 시작점의 ID가 포함되어 있습니다. |
   | isFavorite | T | 시작점이 즐겨찾기인지 여부를 나타냅니다. startpoint가 favorite else false인 경우 true입니다. |
   | isDefaultImage | T | 프로세스에 지정된 이미지가 있는지 여부를 나타냅니다. 프로세스와 연결된 이미지가 없는 경우 true이고, 그렇지 않으면 false입니다. |
   | 작업 | T | startpoint가 호출될 때 생성된 작업이 포함되어 있습니다. |
   | imageUrl | T | 여기에는 시작점에 해당하는 이미지의 URL이 포함되어 있습니다. |

1. 작업

   작업은 사용자/그룹에 할당되며 데이터로 채울 수 있는 사용자 인터페이스(양식 또는 안내서(더 이상 사용되지 않음)를 포함합니다. 사용자에게 작업이 할당되면 작성 및 제출 양식 또는 안내서가 제공됩니다.

<table> 
 <tbody>
  <tr>
   <td>속성<br /> </td> 
   <td>클라이언트만<br /> </td> 
   <td>댓글<br /> </td> 
  </tr>
  <tr>
   <td>classOfTask</td> 
   <td>F</td> 
   <td>작업이 lc8 작업인 경우 작업의 클래스가 'LC8'이고 그렇지 않으면 '표준'입니다.<br /> </td> 
  </tr>
  <tr>
   <td>completeTime<br /> </td> 
   <td>F</td> 
   <td>작업이 완료될 때 타임스탬프가 들어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>consultGroupId<br /> </td> 
   <td>F</td> 
   <td>작업 확인을 수행할 수 있는 그룹의 ID가 포함되어 있습니다. 디자인 프로세스 중에 설정됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>createTime<br /> </td> 
   <td>F</td> 
   <td>작업을 만들 때 타임스탬프가 들어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>creationId<br /> </td> 
   <td>F</td> 
   <td>작업을 만든 사용자의 ID가 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>currentAssignment<br /> </td> 
   <td>F</td> 
   <td>여기에는 현재 작업 할당에 대한 세부 정보가 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>기한<br /> </td> 
   <td>F</td> 
   <td>여기에는 작업 마감일에 도달하는 타임스탬프가 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>설명<br /> </td> 
   <td>F</td> 
   <td>작업에 대한 설명이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>displayName<br /> </td> 
   <td>F</td> 
   <td>작업의 표시 이름이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>forwardGroupId<br /> </td> 
   <td>F</td> 
   <td>작업을 전달할 수 있는 그룹의 ID가 포함되어 있습니다. 디자인 프로세스 중에 설정됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>지침<br /> </td> 
   <td>F</td> 
   <td>작업에 대한 지침이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>isLocked<br /> </td> 
   <td>F</td> 
   <td>작업이 잠긴 경우 True입니다.<br /> </td> 
  </tr>
  <tr>
   <td>isMustOpenToComplete<br /> </td> 
   <td>F</td> 
   <td>작업을 완료하기 위해 작업 양식을 열어야 하는 경우 True입니다.<br /> </td> 
  </tr>
  <tr>
   <td>isOpenFullScreen<br /> </td> 
   <td>F</td> 
   <td>true인 경우 작업을 열 때 양식이 먼저 전체 화면을 표시합니다.<br /> </td> 
  </tr>
  <tr>
   <td>isRouteSelectionRequired<br /> </td> 
   <td>F</td> 
   <td>true일 경우 작업을 완료하려면 경로를 선택해야 합니다.<br /> </td> 
  </tr>
  <tr>
   <td>isShowAttachments<br /> </td> 
   <td>F</td> 
   <td>첨부 파일이 true이면 표시됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>isStartTask<br /> </td> 
   <td>F</td> 
   <td>true이면 작업이 시작점에서 생성됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>isVisible<br /> </td> 
   <td>F</td> 
   <td>작업이 작업 공간에 표시되면 True입니다.<br /> </td> 
  </tr>
  <tr>
   <td>nextRecommendations<br /> </td> 
   <td>F</td> 
   <td>다음 미리 알림을 위한 타임스탬프.<br /> </td> 
  </tr>
  <tr>
   <td>우선 순위<br /> </td> 
   <td>F</td> 
   <td>작업의 우선 순위를 포함합니다.<br /> 1 = 가장 높은 우선순위<br /> 2 = 높은 우선순위<br /> 3 = 일반 우선순위<br /> 4 = 낮음 우선순위<br /> 5 = 최저 우선순위<br /> </td> 
  </tr>
  <tr>
   <td>processInstanceId</td> 
   <td>F</td> 
   <td>작업이 속한 프로세스 인스턴스의 ID입니다.<br /> </td> 
  </tr>
  <tr>
   <td>processInstanceStatus<br /> </td> 
   <td>F</td> 
   <td>작업의 프로세스 인스턴스 상태입니다.<br /> </td> 
  </tr>
  <tr>
   <td>recommendationCount<br /> </td> 
   <td>F</td> 
   <td>작업에 대한 미리 알림 수가 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>routeList<br /> </td> 
   <td>F</td> 
   <td>작업에 연결된 경로 목록이 포함되어 있습니다. 사용자는 경로 목록에서 경로를 선택하여 작업을 완료할 수 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>selectedRoute<br /> </td> 
   <td>F</td> 
   <td>작업이 완료될 때 선택한 경로의 이름이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>serializedImageTicket<br /> </td> 
   <td>F</td> 
   <td>작업에 해당하는 이미지 티켓이 포함되어 있습니다. 이 이미지 티켓은 서버에서 작업을 위한 이미지를 가져오기 위해 작업의 imageUrl 필드에 사용됩니다.<br /> <br /> </td> 
  </tr>
  <tr>
   <td>serviceName<br /> </td> 
   <td>F</td> 
   <td>작업에 대한 서비스 이름이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>serviceTitle<br /> </td> 
   <td>F</td> 
   <td>작업에 대한 서비스 제목이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>상태<br /> </td> 
   <td>F</td> 
   <td>1 = 생성됨(시작 지점에서 작업이 생성됨)<br /> 2 = 생성 및 저장(작업이 시작점에서 만들어지고 저장됨)<br /> 3 = 할당됨(프로세스가 시작된 후 사용자에게 작업이 할당됨)<br /> 4 = 지정 및 저장됨(작업이 할당되어 저장됨)<br /> 100 = 완료됨(작업이 완료됨)<br /> 101 = 마감 날짜(작업이 마감일에 도달했습니다.)<br /> 102 = 종료됨<br /> </td> 
  </tr>
  <tr>
   <td>stepName<br /> </td> 
   <td>F</td> 
   <td>디자인하는 동안 작업 세트의 이름이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>summaryUrl<br /> </td> 
   <td>F</td> 
   <td>작업 요약 URL이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>taskACL<br /> </td> 
   <td>F</td> 
   <td>작업의 액세스 제어 목록입니다.<br /> </td> 
  </tr>
  <tr>
   <td>taskId<br /> </td> 
   <td>F</td> 
   <td>작업의 ID입니다.<br /> </td> 
  </tr>
  <tr>
   <td>updateTime<br /> </td> 
   <td>F</td> 
   <td>작업을 마지막으로 업데이트한 타임스탬프입니다.<br /> </td> 
  </tr>
  <tr>
   <td>formUrl<br /> </td> 
   <td>T</td> 
   <td>작업에 대한 양식 URL을 포함합니다.<br /> </td> 
  </tr>
  <tr>
   <td>taskFormType<br /> </td> 
   <td>T</td> 
   <td>작업 양식 유형이 포함되어 있습니다. 이 필드를 사용하면 작업이 클라이언트에서 pdf for, swf 양식 등으로 렌더링됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>showDirectActions<br /> </td> 
   <td>T</td> 
   <td>true면 경로 작업이 작업 공간에 표시됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>showACLActions<br /> </td> 
   <td>T</td> 
   <td>true인 경우 앞으로, 참조, 공유와 같은 작업이 작업 공간에 표시됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>supportsOffline<br /> </td> 
   <td>T</td> 
   <td>true일 경우 양식을 오프라인으로 전환할 수 있습니다. pdf 양식용입니다.<br /> </td> 
  </tr>
  <tr>
   <td>supportsSave<br /> </td> 
   <td>T</td> 
   <td>true이면 사용자가 작업을 저장할 수 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>readerSubmitOptions<br /> </td> 
   <td>T</td> 
   <td>이 개체에는 pdf 양식에 전송 단추가 없는 경우 Reader를 통해 pdf 양식을 제출하는 데 사용되는 옵션이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>isDefaultImage<br /> </td> 
   <td>T</td> 
   <td>프로세스에 지정된 이미지가 있는지 여부를 나타냅니다. 프로세스와 연결된 이미지가 없는 경우 true이고, 그렇지 않으면 false입니다.<br /> </td> 
  </tr>
  <tr>
   <td>historyTaskList<br /> </td> 
   <td>T</td> 
   <td>작업 세부 사항의 기록 탭에 사용되는 작업 목록이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>isOwner<br /> </td> 
   <td>T</td> 
   <td>로그인한 사용자가 작업 소유자인 경우 True입니다.<br /> </td> 
  </tr>
  <tr>
   <td>availableCommands<br /> </td> 
   <td>T</td> 
   <td>여기에는 작업에서 수행할 수 있는 모든 작업이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>availableCommands.directCommands<br /> </td> 
   <td>T</td> 
   <td>작업에 사용할 수 있는 모든 경로 작업이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>availableCommands.taskACLCommands<br /> </td> 
   <td>T</td> 
   <td>작업에 사용할 수 있는 경우 전달, 공유 및 참조 등의 명령이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>availableCommands.otherCommands<br /> </td> 
   <td>T</td> 
   <td>여기에는 잠금, 잠금 해제, 포기, 반환, 클레임 등의 명령이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>processInstanceInfo<br /> </td> 
   <td>T</td> 
   <td>작업의 프로세스 인스턴스에 대한 정보가 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>processVariables<br /> </td> 
   <td>T<br /> </td> 
   <td>여기에는 프로세스 변수(있는 경우)의 개체 배열이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>pendingTasks<br /> </td> 
   <td>T</td> 
   <td>작업의 프로세스 인스턴스에 대해 보류 중인 작업 목록이 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>userActions<br /> </td> 
   <td>T</td> 
   <td>개체 배열입니다. 각 객체에는 경로 및 해당 확인 메시지가 있는 경우 해당 확인 메시지에 대한 세부 정보가 포함되어 있습니다.<br /> </td> 
  </tr>
  <tr>
   <td>dataUrl<br /> </td> 
   <td>T</td> 
   <td>작업 형식의 데이터에 대한 URL입니다.<br /> </td> 
  </tr>
  <tr>
   <td>externalAppConfig<br /> </td> 
   <td>T</td> 
   <td>타사 애플리케이션 양식에 대한 구성입니다.<br /> </td> 
  </tr>
  <tr>
   <td>제출<br /> </td> 
   <td>T</td> 
   <td>작업이 제출되면 True입니다.<br /> </td> 
  </tr>
  <tr>
   <td>첨부 파일<br /> </td> 
   <td>T</td> 
   <td>작업에 대한 첨부 파일 목록입니다.<br /> </td> 
  </tr>
  <tr>
   <td>할당<br /> </td> 
   <td>T</td> 
   <td>작업의 할당 목록입니다.<br /> </td> 
  </tr>
 </tbody>
</table>

1. 필터

   필터는 기본적으로 사용자 또는 그룹의 대기열입니다. 작업이 사용자/그룹에 할당되면 해당 큐에 작업이 추가됩니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>isDefault <br type="_moz" /> </td> 
   <td>F</td> 
   <td>Logged in 사용자의 기본 큐인 경우 True이고, 그렇지 않은 경우 false입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>이름<br type="_moz" /> </td> 
   <td>F</td> 
   <td>큐 소유자의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>qid</td> 
   <td>F</td> 
   <td>큐의 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>유형</td> 
   <td>F</td> 
   <td>큐의 유형이 포함되어 있습니다.<br /> 0 - 사용자 큐.<br /> 1. 공유 큐.<br /> 2. 그룹 큐.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>쿼리</td> 
   <td>T</td> 
   <td>필터와 연결된 쿼리가 포함되어 있습니다. 이 쿼리는 전체 작업 목록에서 작업을 검색하는 데 사용됩니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>작업</td> 
   <td>T</td> 
   <td>필터에 속한 모든 작업 목록이 포함되어 있습니다.<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

1. 부재 중

   부재 일정을 관리하고 부재 시 자신에게 할당된 작업의 흐름을 제어할 수 있습니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong><br type="_moz" /> </td> 
   <td><strong>클라이언트만</strong><br type="_moz" /> </td> 
   <td><strong>댓글</strong><br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>dateRanges<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 부재 일정 배열 개체를 포함합니다. 각 예약 객체에서 startDate 필드에는 예약의 시작 날짜 및 종료 날짜 필드가 포함되어 있습니다. 일정에 endDate가 null인 경우 사용자가 부재 일정 종료 날짜를 예약하지 않았음을 의미합니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>isNoPrimaryDesignate<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자가 부재 중인 경우 기본 지정이 없는 경우 True입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자가 부재 중인 경우 True입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>outOfOfficeDesignate<br type="_moz" /> </td> 
   <td>F</td> 
   <td>여기에는 사용자별로 기본 지정으로 지정된 사용자의 세부 정보가 포함되어 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processSpecificDesignates<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스 특정 부재 지정 개체들을 위한 개체 배열을 포함합니다. 각 프로세스 특정 지정 객체에서 processName은 프로세스 이름을 포함하고, 해당 프로세스에 대해 지정된 사용자가 없을 경우 isNotDesignated는 true이고, 해당 프로세스에 대해 지정된 사용자의 다른 세부 정보가 사용자에게 지정되지 않은 경우 userDesignated는 null입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>프로세스<br type="_moz" /> </td> 
   <td>T</td> 
   <td>사용자가 사용할 수 있는 모든 프로세스 목록이 포함되어 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>initialOutOfOfficeSettings<br type="_moz" /> </td> 
   <td>T</td> 
   <td>이 페이지에는 처음에 가져온 사용자의 초기 부재 중 설정이 포함되어 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>outOfOfficeSettings<br type="_moz" /> </td> 
   <td>T</td> 
   <td>수정된 부재 설정이 포함되어 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>userSearchHistory<br type="_moz" /> </td> 
   <td>T</td> 
   <td>이 파일에는 로그인한 사용자가 날짜까지 검색하는 사용자 목록이 포함되어 있습니다.<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

1. 프로세스 인스턴스

   프로세스가 작업 공간이나 워크벤치를 통해 호출되면 프로세스 인스턴스가 생성됩니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>설명<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스 인스턴스에 대한 설명<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>개시자</td> 
   <td>F</td> 
   <td>프로세스 인스턴스의 개시자의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>initiatorId</td> 
   <td>F</td> 
   <td>프로세스 인스턴스의 개시자의 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processCompleteTime<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스가 완료되면 타임스탬프를 사용합니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processInstanceId<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스 인스턴스의 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processInstanceStatus<br type="_moz" /> </td> 
   <td>F</td> 
   <td>0 = 시작됨<br /> 1 = 실행 중<br /> 2 = 완료<br /> 3 = 완료<br /> 4 = 종료됨<br /> 5 = 종료 중<br /> 6 = 일시 중단됨<br /> 7 = 일시 중단<br /> 8 = 일시 중단 해제<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processStartTime<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스가 시작될 때 타임스탬프를 사용합니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processVariables<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스 변수의 개체 배열입니다. 각 프로세스 변수 객체에는 프로세스 변수의 이름인 이름, 프로세스 변수의 값인 값 및 프로세스 변수의 유형인 유형이 포함됩니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>작업 목록<br type="_moz" /> </td> 
   <td>T</td> 
   <td>이 프로세스 인스턴스에서 생성한 작업입니다.<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

1. 프로세스 이름

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>processMajorVersion<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스의 주요 버전입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processMinorVersion<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스의 부 버전입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processTitle<br type="_moz" /> </td> 
   <td>F</td> 
   <td>프로세스의 제목입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>processInstanceList<br type="_moz" /> </td> 
   <td>T</td> 
   <td>이 프로세스에 대한 프로세스 인스턴스 목록입니다.<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

1. 작업 할당 개체

   작업 할당 객체에는 작업 지정에 대한 정보가 포함되어 있습니다. 다음은 작업의 할당 속성입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>assignmentCreateTime<br type="_moz" /> </td> 
   <td>F</td> 
   <td>이 작업 할당을 만들 때 타임스탬프를 사용합니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>assignmentType<br type="_moz" /> </td> 
   <td>F</td> 
   <td>0 = 초기 배정<br /> 1 = 전달(작업이 현재 작업 소유자에게 전달되었습니다.)<br /> 2 = 반환됨(이전 작업 소유자가 작업을 현재 작업 소유자에게 반환함)<br /> 3 = 요청됨(현재 작업 소유자가 작업을 요청했습니다.)<br /> 4 = 에스컬레이션(에스컬레이션 후 태스크의 현재 소유자에게 태스크가 지정됨)<br /> 5 = 관리자 지정됨(관리자가 현재 작업 소유자에게 작업을 할당했습니다.)<br /> 6 = 상담됨 ( 현재 작업 소유자에게 작업이 상담되었습니다.)<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>assignmentUpdateTime<br type="_moz" /> </td> 
   <td>F</td> 
   <td>이 작업 할당이 업데이트될 때 타임스탬프.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>queueId<br type="_moz" /> </td> 
   <td>F</td> 
   <td>현재 작업 소유자의 큐 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>queueOwner<br type="_moz" /> </td> 
   <td>F</td> 
   <td>현재 작업 소유자의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>queueOwnerId<br type="_moz" /> </td> 
   <td>F</td> 
   <td>현재 작업 소유자의 ID입니다.<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

1. 작업 ACL 개체

   작업 ACL 개체에는 전달, 공유, 참조 등과 같은 권한에 대한 정보가 들어 있습니다. 작업 다음은 작업의 ACL 속성입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>canAddAttachments<br type="_moz" /> </td> 
   <td>F</td> 
   <td>true일 경우 첨부 파일을 작업에 추가할 수 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>canAddNotes<br type="_moz" /> </td> 
   <td>F</td> 
   <td>true면 작업에 메모를 추가할 수 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>canClaim<br type="_moz" /> </td> 
   <td>F</td> 
   <td>true이면 작업을 요구할 수 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>canConsult<br type="_moz" /> </td> 
   <td>F</td> 
   <td>true일 경우 작업을 참조할 수 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>canForward<br type="_moz" /> </td> 
   <td>F</td> 
   <td>true이면 작업을 전달할 수 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>canShare<br type="_moz" /> </td> 
   <td>F</td> 
   <td>true면 작업을 공유할 수 있습니다.<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

1. 작업 첨부 파일

   첨부 파일을 작업에 추가할 수 있습니다. 첨부 파일 유형은 첨부 파일 및 메모일 수 있습니다. 다음은 첨부 파일의 속성입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>createDate<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일을 만들 때의 타임스탬프.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>creatorId<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일을 추가한 사용자의 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>creatorName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일을 추가한 사용자의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>설명<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일에 대한 설명입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>fileName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>id<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일의 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>lastModifiedDate<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일이 마지막으로 수정된 경우 타임스탬프.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>noteExtended<br type="_moz" /> </td> 
   <td>F</td> 
   <td>true면 확장된(긴) 메모입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>권한<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일과 연관된 권한. allowRead 필드는 읽기 권한이고 allowWrite는 쓰기 권한이며 allowDelete는 삭제 권한입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>크기<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일 크기(바이트)입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>taskId<br type="_moz" /> </td> 
   <td>F</td> 
   <td>첨부 파일이 추가된 작업의 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>유형<br type="_moz" /> </td> 
   <td>F</td> 
   <td>Type은 파일에 대한 첨부 파일이며 Type은 참고에 대한 메모입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>formattedCreationDate<br type="_moz" /> </td> 
   <td>T</td> 
   <td>사용자의 UI 설정에 따른 첨부 파일 생성 날짜가 포함되어 있습니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>formatDescription<br type="_moz" /> </td> 
   <td>T</td> 
   <td>서식 있는 첨부 설명. AEM Forms 작업 영역의 첨부 파일 설명에 있는 특수 문자를 표시하는 데 사용됩니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>formatFileName<br type="_moz" /> </td> 
   <td>T</td> 
   <td>서식 있는 첨부 파일 이름입니다. AEM Forms 작업 영역에서 첨부 파일 이름에 있는 특수 문자를 표시하는 데 사용됩니다. 이건 참고용입니다<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>

1. 사용자

   다음은 사용자 객체의 속성입니다.

<table> 
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>클라이언트만</strong></td> 
   <td><strong>댓글</strong></td> 
  </tr>
  <tr>
   <td>주소<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 주소입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>commonName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 일반 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>설명<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자에 대한 설명입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>directGroupMembership<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자 그룹 목록입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>displayName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 이름을 표시합니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>email<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 이메일 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자가 부재 중인 경우 True입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>lastName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 성입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>firstName<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>oid<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 ID입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>org<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 조직 이름입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>postalAddress<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 우편 주소입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>전화<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 연락처 번호입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>phoneNumber<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 연락처 번호입니다.<br type="_moz" /> </td> 
  </tr>
  <tr>
   <td>userid<br type="_moz" /> </td> 
   <td>F</td> 
   <td>사용자의 로그인 ID입니다.<br type="_moz" /> </td> 
  </tr>
 </tbody>
</table>
