---
title: '"서신 관리:문제 해결"'
seo-title: 서신 관리 문제 해결
description: 서신 관리 문제 해결
seo-description: 서신 관리 문제 해결
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: 서신 관리
exl-id: 82a35d81-13d0-435f-875e-6fd0a6d574d5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# 서신 관리:문제 해결 {#correspondence-management-troubleshooting}

## {#errors-when-saving-a-letter} 문자를 저장할 때 오류가 발생합니다

### 문제 {#issue}

편지를 저장할 때 다음 오류 중 하나가 표시됩니다.

* 텍스트 모듈에 대한 데이터 바인딩이 없습니다.
* 다음에 필요한 속성 정보를 제공하십시오

### 이유 {#reason}

다음 중 하나로 인해 이러한 오류가 발생할 수 있습니다.

* 데이터 사전은 편지에 바인딩되어 있지만 서버에 없습니다.
* 데이터 사전은 편지에 바인딩되지만 이름에 밑줄(_)이 있습니다.

### 해결 방법 {#workaround}

편지에서 사용하는 데이터 사전이 서버에 있고 해당 이름에 밑줄(_)이 없는지 확인합니다.

## {#error-when-previewing-a-letter} 문자를 미리 보는 동안 오류가 발생했습니다.

### 문제 {#issue-1}

문자를 미리 보는 동안 &quot;편지 로드 중 오류:편지에서 이전에 게시 취소된 텍스트 자산이 게시되었더라도 &quot;XML 입력에서 자산을 가져올 수 없습니다.&quot;가 표시됩니다.

### 해결 방법 {#workaround-1}

다음 단계를 사용하여 게시 인스턴스에서 편지 캐시를 재설정한 다음 편지 보기를 다시 시도하십시오.

1. **`https://[server]:[port]/[contextPath]/system/console/configMgr`**(으)로 이동하여 관리자로 로그인합니다.
1. **서신 관리 구성**&#x200B;을 선택합니다.
1. **서신 관리 구성**&#x200B;에서 **편지 캐시 활성화**&#x200B;를 비활성화한 다음&#x200B;**저장 을 클릭합니다.**
1. **Letter Cache**&#x200B;를 활성화한 다음 **Save**&#x200B;를 클릭합니다.
1. 편지 보기를 다시 시도하십시오.
