---
title: 폴더 구조 이해
seo-title: Understanding the folder structure
description: 사용자 지정할 AEM Forms 작업 공간 소스 코드의 폴더 구조를 이해하는 방법입니다.
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---

# 폴더 구조 이해 {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms 작업 공간 구성 요소는 백본을 사용하여 MVC 아키텍처로 디자인됩니다. 각 구성 요소에는 다음에 대한 파일이 있습니다.

* 비즈니스 논리를 포함하는 모델.
* 템플릿 - 인터페이스 컨트롤이 포함된 HTML 파일입니다.
* 템플릿에 대한 컨트롤러 클래스 역할을 하는 보기.

모든 구성 요소의 자산은 아래에 설명된 폴더 구조에 배치됩니다. 자산에 액세스하려면 CRXDE Lite에 로그인하고 `/libs/ws/js/runtime/`.

**모델** 백본 모델을 포함합니다.

**보기** 백본 보기를 포함합니다.

**템플릿** 구성 요소에 대한 HTML 템플릿만 포함합니다.

**경로** 범용 경로를 포함합니다. 경로 내의 템플릿 폴더에는 HTML 코드와 구성 요소에 대한 참조가 들어 있습니다.

**서비스** REST 종단점에서 Adobe Experience Manager 서버 API를 호출하기 위한 서비스 인터페이스를 포함합니다.

**util** 여러 구성 요소에서 사용할 수 있는 일반 유틸리티를 포함합니다.
