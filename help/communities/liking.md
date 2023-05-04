---
title: 좋아요 사용
seo-title: Using Liking
description: 연결 구성 요소 추가 및 구성
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 8%

---

# 좋아요 사용 {#using-liking}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다음 `Liking`구성 요소는 사용자가 포럼 내의 댓글과 같은 특정 컨텐츠 조각에 대한 의견을 표현할 수 있도록 해주는 유용한 도구입니다. 사용 `Liking`구성 요소, 구성원은 하트아이콘을 선택하여 긍정적인 의견을 나타냅니다.

## 페이지에 좋아요 추가 {#adding-liking-to-a-page}

을(를) 추가하려면 `Liking` 구성 요소를 페이지에 작성자 모드에서 사용하려면 구성 요소 브라우저를 사용하여 를 찾습니다

* `Communities / Liking`

사용자가 원하는 기능을 기준으로 할 위치와 같이 페이지에 드래그합니다.

필요한 정보를 보려면 [커뮤니티 구성 요소 기본 사항](basics.md).

이 [필수 클라이언트 측 라이브러리](essentials-liking.md#essentials-for-client-side) 포함된 경우, 다음과 같이 하십시오 `Liking` 구성 요소가 나타납니다.

![chlimage_1-93](assets/chlimage_1-93.png)

## 연결 구성 {#configuring-liking}

배치된 항목을 선택합니다 `Liking` 액세스하여 선택할 구성 요소 `Configure` 아이콘 편집 대화 상자를 엽니다.

![chlimage_1-94](assets/chlimage_1-94.png)

아래에 **[!UICONTROL 텍스트 및 레이블]** 탭에서 좋아요 레코드를 기록하는 데 사용되는 속성을 지정합니다.

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL 긍정적인 응답 레이블]**
(
*필수 여부*) 양수 응답에 대한 속성 이름입니다.

* **[!UICONTROL 부정적인 응답 레이블]**
(
*필수 여부*) 음수 응답의 속성 이름입니다.

* **[!UICONTROL Tally 이름]**
(
*필수 여부*) 선호 구성 요소의 이 인스턴스에 대한 내부 식별 가능한 속성 이름입니다.

## 사이트 방문자 경험 {#site-visitor-experience}

### 구성원 {#members}

회원들은 언제든지 그들의 모습을 바꿀 수 있다.

### 익명 {#anonymous}

익명 연결은 지원되지 않습니다. 사이트 방문자가 등록을 하고(구성원이 되기) 로그인해야 해당 내용에 참여할 수 있습니다.

## 추가 정보 {#additional-information}

자세한 내용은 [Essentials를 좋아하는 중](essentials-liking.md) 개발자를 위한 페이지입니다.
