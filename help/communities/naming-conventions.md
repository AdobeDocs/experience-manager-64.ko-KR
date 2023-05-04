---
title: 이름 지정 규칙
seo-title: Naming Conventions
description: Java 패키지 이름의 하이픈
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 7%

---

# 이름 지정 규칙 {#naming-conventions}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## Java 패키지 이름의 하이픈 {#hyphens-in-java-package-name}

Java 클래스의 위치를 생성할 때는 패키지 이름이 저장소 폴더 위치의 이름과 일치해야 하며 경로에 있는 하이픈이 올바르게 이스케이프 처리되어야 합니다.

저장소 항목 이름에서 하이픈을 사용하는 것은 AEM 개발에서 권장되지만 Java 패키지 이름 내에서는 하이픈을 사용할 수 없습니다.

기본 CRX 플랫폼은 실제 밑줄을 구별할 수 있어야 합니다._&#39; 및 하이픈 &#39;-&#39;입니다. 따라서 JCR에서 하이픈은 유니코드 값(u002d)으로 대체해야 하며 밑줄 &#39; 로 이스케이프해야 합니다_&#39;

예를 들어 저장소 경로가 **/apps/my-example/component/info/Info.java**&#x200B;를 지정하는 경우 패키지 이름은 `java package apps.my_002dexample.component.info;`

마찬가지로 밑줄을 이스케이프해야 하므로 `_` 다음과 같이 `_005f`.
