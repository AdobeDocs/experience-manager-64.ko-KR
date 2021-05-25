---
title: 이름 지정 규칙
seo-title: 이름 지정 규칙
description: Java 패키지 이름의 하이픈
seo-description: Java 패키지 이름의 하이픈
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 4%

---

# 이름 지정 규칙 {#naming-conventions}

## Java 패키지 이름의 하이픈 이름 {#hyphens-in-java-package-name}

Java 클래스의 위치를 생성할 때는 패키지 이름이 저장소 폴더 위치의 이름과 일치해야 하며 경로에 있는 하이픈이 올바르게 이스케이프 처리되어야 합니다.

저장소 항목 이름에서 하이픈을 사용하는 것은 AEM 개발에서 권장되지만 Java 패키지 이름 내에서는 하이픈을 사용할 수 없습니다.

기본 CRX 플랫폼은 실제 밑줄 &#39;_&#39;과 하이픈 &#39;-&#39;을 구별할 수 있어야 합니다. 따라서 JCR에서 하이픈은 유니코드 값(u002d)으로 대체해야 하며 밑줄 &#39;_&#39;로 이스케이프해야 합니다.

예를 들어 저장소 경로가 **/apps/my-example/component/info/Info.java**&#x200B;이면 패키지 이름은 `java package apps.my_002dexample.component.info;`여야 합니다.

`_`이 `_005f`이 되도록 밑줄을 이스케이프 처리해야 합니다.
