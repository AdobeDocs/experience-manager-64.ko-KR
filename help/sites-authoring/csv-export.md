---
title: CSV로 내보내기
seo-title: CSV로 내보내기
description: 로컬 시스템에서 페이지에 대한 정보를 CSV 파일로 내보내기
seo-description: 로컬 시스템에서 페이지에 대한 정보를 CSV 파일로 내보내기
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 82%

---

# CSV로 내보내기{#export-to-csv}

**CSV 내보내기 만들기**&#x200B;를 사용하여 페이지에 대한 정보를 로컬 시스템의 CSV 파일로 내보낼 수 있습니다.

* 다운로드한 파일은 `export.csv`라고 합니다.
* 컨텐츠는 사용자가 선택한 속성에 따라 다릅니다.
* 내보내기에 대한 깊이와 함께 경로를 정의할 수 있습니다.

>[!NOTE]
>
>브라우저의 다운로드 기능 및 기본 대상이 사용됩니다.

CSV 내보내기 만들기 마법사를 사용하여 다음을 선택할 수 있습니다.

* 내보낼 속성

   * 메타데이터

      * 수정됨
      * 게시됨
   * 분석

      * 페이지 보기 수
      * 고유 방문자 수
      * 페이지 시간


* 깊이

   * 상위 경로
   * 직접 하위만
   * 하위의 추가 수준
   * 수준

결과 `export.csv` 파일은 Excel 또는 기타 호환되는 애플리케이션에서 열 수 있습니다. 예를 들면 다음과 같습니다.

![chlimage_1-58](assets/chlimage_1-58.png)

**CSV 내보내기 만들기** 옵션은 **Sites** 콘솔(목록 보기)을 탐색할 때 사용할 수 있습니다.**만들기** 드롭다운 메뉴의 옵션입니다.

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

CSV 내보내기를 만들려면:

1. **사이트** 콘솔을 열고 필요한 경우 필요한 위치로 이동합니다.
1. 도구 모음에서 **만들기** 를 선택하고 **CSV 내보내기** 를 선택하여 마법사를 엽니다.

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. 내보낼 필수 속성을 선택합니다.
1. **만들기**&#x200B;를 선택합니다.
