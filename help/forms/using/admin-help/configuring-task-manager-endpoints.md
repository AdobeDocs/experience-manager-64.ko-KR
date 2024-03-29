---
title: 작업 관리자 끝점 구성
seo-title: Configuring Task Manager endpoints
description: 작업 관리자 끝점을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure Task Manager endpoints.
uuid: 07604b10-0bd7-4bce-9624-7ebac4754f56
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9c55feb9-23d8-4798-a3c5-70ec736df3ad
exl-id: 546a699e-975f-42a1-8ab5-0de4bd7f4a8f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 2%

---

# 작업 관리자 끝점 구성 {#configuring-task-manager-endpoints}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

작업 관리자 끝점을 사용하면 작업 공간 사용자가 서비스를 호출할 수 있습니다.

**작업 관리자 끝점 설정**

작업 관리자 끝점을 구성하려면 다음 설정을 사용합니다.

**이름:** (필수) 끝점을 식별합니다. 이름은 Workspace의 카드 보기에 표시됩니다. Workspace에 표시되는 이름을 자릅니다. &lt; 문자는 포함하지 마십시오. URL을 끝점의 이름으로 입력하는 경우 RFC1738에 지정된 구문 규칙을 따르는지 확인하십시오.

**설명:** 끝점에 대한 설명입니다. 작업 공간에 표시되는 설명이 잘리기 때문에 &lt; 문자를 포함하지 마십시오.

**작업 지침:** 이 워크플로우를 시작하는 사용자를 위한 지침입니다.

**프로세스 소유자:** 프로세스를 담당하는 사람의 이름입니다.

**사용자가 작업을 전달할 수 있음:** 사용자가 초기 작업을 전달할 수 있습니다.

**첨부 창 표시:** 사용자가 첨부 파일 창을 볼 수 있습니다.

**첨부 파일 추가 허용:** 사용자가 첨부 파일과 메모를 추가할 수 있습니다.

**작업이 처음 잠겼습니다.** 초기 작업을 잠급니다.

**공유 큐에 대한 ACL 추가:** 초기 작업은 공유 큐 사용자의 ACL을 사용하여 만들어집니다.

**분류:** (필수) 작업 공간에서 사용자가 양식을 볼 카테고리입니다. 목록에서 카테고리를 선택하거나 새 카테고리를 선택하여 카테고리를 추가합니다.

**작업 이름:** (필수) 종단점에 지정할 수 있는 작업 목록입니다.
