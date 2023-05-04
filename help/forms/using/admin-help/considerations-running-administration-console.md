---
title: AdministrationConsole 실행 시 고려 사항
seo-title: Considerations when running AdministrationConsole
description: 이 문서에서는 관리 콘솔을 실행할 때 고려해야 할 몇 가지 사항을 나열합니다.
seo-description: This document lists a few points to consider when running Administration Console.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
exl-id: 991418fd-5ff8-491e-834e-2324e029e499
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 관리 콘솔을 실행할 때의 고려 사항 {#considerations-when-running-administrationconsole}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다음은 관리 콘솔을 실행할 때 고려해야 할 몇 가지 사항입니다.

* URL을 사용하여 관리 콘솔에 액세스하는 경우 `https://*[hostname]*:*[port]*/adminui`로 지정하는 호스트 이름에는 밑줄 문자를 사용할 수 없습니다. 그렇지 않으면 관리 콘솔의 일부 영역에 대한 링크가 제대로 작동하지 않을 수 있습니다.
* 일본어 OS에서 Windows 탐색기에서 관리 콘솔을 실행하는 경우 다음 문제를 해결할 수 있습니다.

   * 링크를 클릭하면 예상되는 링크 대신 로그인 페이지로 돌아갑니다.
   * 링크를 클릭하면 권한 오류가 표시됩니다.

   우수 사례는 링크가 실패하지 않도록 Mozilla Firefox와 같은 다른 브라우저에서 관리 콘솔을 실행하는 것입니다.

* 관리 콘솔에서 검색을 수행할 때 백슬래시 문자()를 사용하지 마십시오.
