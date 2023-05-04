---
title: 서신 관리에서 역할 기반 사용자 인터페이스를 게시하지 않음
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: 서신 관리에서 역할 기반 사용자 인터페이스를 게시하지 않음
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---


# 서신 관리에서 역할 기반 사용자 인터페이스를 게시하지 않음 {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에서 관리자는 다양한 사용자 그룹에 대한 역할 기반 액세스 권한을 제공할 수 있으며 다른 리소스에 대해 다양한 작업을 수행할 수 있습니다. 예를 들어, 데이터 사전을 만들거나 편집하는 기능은 특정 사용자 그룹의 사용자만 사용할 수 있고 다른 사용자는 데이터 사전을 보고 사용할 수 있습니다.

AEM 인터페이스에는 사용자의 액세스 수준에 따라 자산 유형 만들기 또는 편집 등의 옵션이 표시됩니다. 예를 들어 사용자에게 데이터 사전을 만들 수 있는 권한이 없는 경우 데이터 사전을 만드는 옵션이 UI에 표시되지 않습니다.

CRX를 통해 사용자 및 그룹 계정 모두에 대한 액세스 권한을 구성할 수 있지만 이 문서는 역할 또는 사용자 그룹 기반 액세스 권한에 대한 것입니다.

그룹, 권한, 액세스 제어 목록 및 사용자 및 그룹 관리에 대한 자세한 내용은 [사용자 관리 및 보안](/help/sites-administering/security.md).

## 권한 관리 {#managing-permissions}

1. 권한을 관리할 사용자가 관련 사용자 그룹에 추가되어 있는지 확인합니다.

   예를 들어 John Doe 사용자가 그룹에 추가됩니다 `agents` 및 `cm-creditcard`. 자세한 내용은 그룹에 사용자 또는 그룹 추가 를 참조하십시오. 자세한 내용은 [사용자 및 사용자 그룹 관리](/help/communities/users.md).

   ![]()

1. 원하는 권한을 허용하는 데 맞게 폴더를 만듭니다.

   예를 들어, 기업에 주택 담보 대출, 신용 카드 및 보험 부서가 있는 경우 다음과 같은 폴더를 생성할 수 있습니다 `HomeMortgage`, `CreditCard,`및 `Insurance` 관련 자산을 유지하고 해당 부서에만 관련된 자산의 에이전트에만 선택적으로 액세스할 수 있도록 합니다.

1. AEM WCM 보안에 액세스하려면 다음 중 하나를 수행하십시오.

   1. 시작 화면 또는 AEM의 다양한 위치에서 보안 아이콘을 클릭합니다.

   1. 로 바로 이동 `https://[server]:[port]/useradmin`. 관리자로 AEM에 로그인해야 합니다.

      ![]()
   왼쪽 트리에는 현재 시스템에 있는 모든 사용자와 그룹이 나열됩니다. 표시할 열을 선택하고 열의 내용을 정렬하며 열 헤더를 새 위치로 끌어 열 순서를 변경할 수도 있습니다.

   탭에서는 다양한 구성에 액세스할 수 있습니다.

1. 왼쪽 트리 목록에서 관련 그룹의 이름을 두 번 탭한 다음 권한 탭을 선택합니다.

   그룹 이름을 찾기 위해 제공된 공간에 그룹 이름을 입력할 수 있습니다.

1. 권한 탭에서 권한을 추가할 경로로 이동합니다. 서신 관리 폴더는 `content/apps/cm/` 폴더를 입력합니다.

   해당 경로에 대한 권한을 부여할 멤버의 멤버 열에서 확인란을 선택합니다. 사용 권한을 제거할 구성원의 확인란 선택을 취소합니다. 변경한 셀에 빨간색 삼각형이 나타납니다.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >폴더에 지정된 권한이 해당 하위 폴더에 지정된 권한을 대체합니다.

1. 저장 을 누릅니다.
1. 단계 텍스트
1. 단계 텍스트
1. 단계 텍스트

