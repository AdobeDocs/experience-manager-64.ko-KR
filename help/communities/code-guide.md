---
title: 코딩 지침
seo-title: Coding Guidelines
description: 커뮤니티 개발자 지침, 팁 및 요령
seo-description: Communities developer guidelines, tips, and tricks
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
exl-id: 022043cd-35ed-49b1-b5b4-5cc92d29cef4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 4%

---

# 코딩 지침 {#coding-guidelines}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 지침, 팁 및 요령 {#guidelines-tips-and-tricks}

AEM Communities과 함께 작업하는 것은 비즈니스 논리, 스타일 및 페이지 컨텐츠가 서로 구별되는 템플릿 스크립팅 언어를 선택할 때 유연성에 따라 Java Server 페이지에 크게 의존하지 않게 발전했습니다.

UGC(사용자 생성 컨텐츠)를 사용할 때 보다 유연하게 작업할 수 있는 것은 SocialResourceProvider API를 통해 제공되는 유연성이며, 이를 통해 알아야 할 필요가 없습니다 [SRP](srp.md) 배포에 대해 옵션이 선택되었습니다.

다음은 AEM Communities 개발자를 위한 다양한 코딩 지침 및 우수 사례입니다.

### 코드 {#code}

* [SRP를 사용하여 UGC 액세스](accessing-ugc-with-srp.md) - JSRP(JCR)에 UGC를 저장할 때만 작동하는 애플리케이션을 작성하지 않는 방법입니다.
* [SocialUtils 리팩터링](socialutils.md) - SocialUtils를 대체하는 SRP에 대한 유틸리티 메서드입니다.
* [이름 지정 규칙](naming-conventions.md) - 사용자 지정 Java 클래스에 대한 이름 지정 규칙.

### 스크립트 {#scripts}

* [커뮤니티 구성 요소 테스트하기](sideloading.md) - 페이지가 로드된 후 구성 요소를 동적으로 추가하는 방법.
* [리치 텍스트 편집기 핵심 사항](rte.md) - 컨텐츠 게시를 위해 구성원에게 제공된 리치 텍스트 UI를 사용자 지정하는 방법.

### IDE {#ide}

* [커뮤니티에 Maven 사용](maven.md) - Communities API jar를 포함하는 방법.
* [SocialUtils 리팩터링](socialutils.md) - SocialUtils를 대체하는 SRP에 대한 유틸리티 메서드입니다.
