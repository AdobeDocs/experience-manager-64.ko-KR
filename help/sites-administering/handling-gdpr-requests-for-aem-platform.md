---
title: AEM Foundation에 대한 GDPR 요청 처리
seo-title: Handling GDPR Requests for the AEM Foundation
description: AEM Foundation에 대한 GDPR 요청 처리
seo-description: null
uuid: d470061c-bbcf-4d86-9ce3-6f24a764ca39
contentOwner: sarchiz
discoiquuid: 8ee843b6-8cea-45fc-be6c-99c043f075d4
exl-id: dcd67a1e-b20f-4ed4-b154-dd250cbd8320
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 58%

---

# AEM Foundation에 대한 GDPR 요청 처리{#handling-gdpr-requests-for-the-aem-foundation}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

>[!IMPORTANT]
>
>아래 섹션에서는 GDPR이 예로 사용되지만, 포함된 세부 사항은 GDPR, CCPA 등 모든 데이터 보호 및 개인 정보 보호 규정에 적용됩니다.

## AEM Foundation GDPR 지원 {#aem-foundation-gdpr-support}

AEM Foundation 수준에서 저장된 개인 데이터는 사용자 프로필입니다. 따라서 이 문서의 정보에서는 주로 사용자 프로필에 액세스하여 삭제하고 GDPR 액세스 및 삭제 요청을 각각 처리하는 방법을 다룹니다.

## 사용자 프로필에 액세스 {#accessing-a-user-profile}

### 설명서 단계 {#manual-steps}

1. 로 이동하여 사용자 관리 콘솔을 엽니다. **[!UICONTROL 설정 - 보안 - 사용자]** 또는 직접 `https://<serveraddress>:<serverport>/libs/granite/security/content/useradmin.html`

   ![useradmin2](assets/useradmin2.png)

1. 그런 다음 페이지 상단의 검색 창에서 해당 사용자의 이름을 입력하여 검색합니다.

   ![usersearch](assets/usersearch.png)

1. 마지막으로 사용자 프로필을 클릭하여 연 다음 **[!UICONTROL 세부 정보]** 탭을 선택합니다.

   ![userprofile_small](assets/userprofile_small.png)

### HTTP API {#http-api}

앞에서 언급한 바와 같이, Adobe는 용이한 자동화를 위해 사용자 데이터 액세스에 대한 API를 제공합니다. 다음은 사용할 수 있는 여러 유형의 API입니다.

**UserProperties API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Sling API**

*사용자 홈 탐색:*

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

*사용자 데이터 검색*

위 명령에서 반환된 JSON 페이로드의 홈 속성에서 노드 경로 사용:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## 사용자 비활성화 및 관련 프로필 삭제 {#disabling-a-user-and-deleting-the-associated-profiles}

### 사용자 비활성화 {#disable-user}

1. 위에서 설명한 대로 사용자 관리 콘솔을 연 다음 해당 사용자를 검색합니다.
1. 해당 사용자에 마우스를 가져다 대고 [선택] 아이콘을 클릭합니다. 해당 프로필이 회색으로 바뀌고 선택되었음이 표시됩니다.

1. 사용자를 비활성화하려면 상단 메뉴의 비활성화 버튼을 누릅니다.

   ![userdisable](assets/userdisable.png)

1. 마지막으로 작업을 확인합니다.

   ![image2018-2-6_1-40-58](assets/image2018-2-6_1-40-58.png)

   그러면 사용자 인터페이스에 프로필 카드에 잠금을 로그아웃하고 추가하여 사용자가 비활성화되었음을 나타냅니다.

   ![비활성화된 사용자](assets/disableduser.png)

### 사용자 프로필 정보 삭제 {#delete-user-profile-information}

1. CRXDE Lite에 로그인한 다음 `[!UICONTROL userId]`:

   ![image2018-2-6_1-57-11](assets/image2018-2-6_1-57-11.png)

1. 아래에 있는 사용자 노드를 엽니다. `[!UICONTROL /home/users]` 기본적으로

   ![image2018-2-6_1-58-25](assets/image2018-2-6_1-58-25.png)

1. 프로필 노드 및 모든 해당 하위 노드를 삭제합니다. AEM 버전에 따라 프로필 노드에 두 가지 형식이 있습니다.

   1. 아래의 기본 개인 프로필 `[!UICONTROL /profile]`
   1. `[!UICONTROL /profiles]`: AEM 6.4를 사용하여 만든 새 프로필의 경우.

   ![image2018-2-6_2-0-4](assets/image2018-2-6_2-0-4.png)

### HTTP API {#http-api-1}

다음 절차는 `curl` 명령줄 도구를 사용하여 **[!UICONTROL Cavery]** `userId`를 통해 사용자를 비활성화하고 기본 위치에서 사용 가능한 해당 사용자의 프로필을 삭제하는 방법에 대해 설명합니다.

* *사용자 홈 탐색*

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

* *사용자 비활성화*

위 명령에서 반환된 JSON 페이로드의 홈 속성에서 노드 경로 사용:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (GDPR in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

* *사용자 프로필 삭제*

계정 탐색 명령에서 반환된 JSON 페이로드의 홈 속성에서 노드 경로 및 알려진 맞춤형 프로필 노드 위치 사용:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
