---
title: Windows 10 Player 구현
seo-title: Windows 10 Player 구현
description: 'AEM Screens Windows 10 플레이어 구성에 대해 알려면 이 페이지를 따르십시오. '
seo-description: 'AEM Screens Windows 10 플레이어 구성에 대해 알려면 이 페이지를 따르십시오. '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# Windows 10 Player 구현{#implementing-windows-player}

이 섹션에서는 AEM Screens Windows 10 플레이어 구성에 대해 설명합니다. 개발 및 테스트에 사용할 설정에 대한 구성 파일 및 사용 가능한 옵션 및 권장 사항에 대한 정보를 제공합니다.

## Windows Player 설치 {#installing-windows-player}

AEM Screens용 Windows Player를 구현하려면 AEM Screens용 Windows Player를 설치하십시오.

AEM 6. [**4 Player 다운로드&#x200B;**](https://download.macromedia.com/screens/)페이지를 참조하십시오.

### 애드혹 메서드 {#ad-hoc-method}

최신 Windows Player(*.exe*)를 설치하려면 애드혹 [**방법을 참조하십시오&#x200B;**](https://download.macromedia.com/screens/).

애플리케이션을 다운로드한 후 플레이어의 단계에 따라 임시 설치를 완료합니다.

1. 왼쪽 위 모서리를 길게 눌러 관리 패널을 엽니다.
1. 왼쪽 **작업** 메뉴에서 구성으로 이동하고 연결할 AEM 인스턴스의 위치(주소)를 입력하고 저장을 **클릭합니다**.

1. 왼쪽 **작업** 메뉴에서 등록 링크를 클릭하여 장치 등록 프로세스를 완료합니다.

### 하나의 구성으로 여러 Windows 10 플레이어 등록 {#registering-multiple-windows-players-with-one-configuration}

Windows 플레이어를 설치한 후에는 하나의 구성으로 여러 플레이어를 등록할 수 있습니다.

>[!NOTE]
>
>**Windows Player 일괄 등록**
>
>Windows 플레이어를 구현할 때 모든 단일 플레이어를 수동으로 구성할 필요는 없습니다. 대신 구성 JSON 파일을 테스트하여 배포할 준비가 된 후에 업데이트할 수 있습니다.
>
>구성은 구성 파일에 제공된 동일한 서버에 대해 모든 플레이어가 ping하는지 확인합니다. 여전히 각 플레이어를 수동으로 등록해야 합니다.

아래 절차에 따라 Windows 10 플레이어를 구성합니다.

1. Windows Player를 설치합니다.
1. 구성 파일을 ***%appdata%\com.adobe.aem.screens.player\config.json에서***&#x200B;찾습니다.
1. 아래 정보를 사용하여 JSON 구성을 업데이트한 다음 플레이어가 있는 모든 시스템에 동일한 폴더를 복사합니다.

### 정책 속성 {#policy-attributes}

다음 표에는 참조용 JSON 정책 예시 및 정책 속성이 요약되어 있습니다.

| **정책 이름** | **목적** |
|---|---|
| 서버 | AEM(Adobe Experience Manager) 서버에 대한 URL. |
| 해상도 | 장치의 해상도입니다. |
| rebootSchedule | 플레이어를 재부팅하는 일정. |
| enableAdminUI | 관리 UI를 활성화하여 사이트에서 장치를 구성합니다. 완전히 구성되고 프로덕션에서 false로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 설정이 완전히 구성되고 프로덕션에서 false로 설정되는 것이 좋습니다. |
| enableActivityUI | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시할 수 있습니다. 문제 해결을 활성화하고 완전히 구성되고 프로덕션에서 비활성화하면 됩니다. |

#### 정책 JSON 파일 예 {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

