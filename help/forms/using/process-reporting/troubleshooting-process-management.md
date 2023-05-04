---
title: 프로세스 보고 문제 해결
seo-title: Troubleshooting Process Reporting
description: JEE 프로세스 보고에서 AEM Forms의 문제 해결
seo-description: Troubleshoot issues in AEM Forms on JEE Process Reporting
page-status-flag: de-activated
uuid: 1c1cc27c-fbed-4366-bffe-e1581d269a93
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0a818d19-8804-4c69-b721-31c347c593c0
exl-id: 57ddfead-22bb-4a99-925e-11d71fc61669
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 6%

---

# 프로세스 보고 문제 해결 {#troubleshooting-process-reporting}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## Microsoft Windows 7에서 Internet Explorer 9에서 필터를 만들 때 발생하는 문제 {#issues-faced-in-creating-filters-on-internet-explorer-on-microsoft-windows}

사전 정의된 보고서에 대한 필터를 만드는 경우, 간헐적으로 다음 문제가 발생합니다 **Internet Explorer 9** 대상 **Microsoft Windows 7** 환경:

* 값 필드의 드롭다운 목록에는 값 대신 고유 식별자가 표시됩니다.
* 값 필드의 Calendar 컨트롤에는 일본어 문자가 표시됩니다.
* 조건 필드가 표시되지 않습니다.
* 값 필드의 Calendar 컨트롤이 표시되지 않습니다.

### 해결 {#resolution}

프로세스 보고에 여전히 로그인되어 있는 동안:

1. 브라우저 캐시를 지웁니다.
1. 브라우저 화면을 새로 고칩니다.
