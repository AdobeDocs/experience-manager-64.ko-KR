---
title: 사용 리소스 만들기 및 할당
seo-title: 사용 리소스 만들기 및 할당
description: 사용 리소스 추가
seo-description: 사용 리소스 추가
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
exl-id: 9f447a54-4512-41ab-b8d3-327e751eda58
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 6%

---

# 사용 리소스 만들기 및 할당 {#create-and-assign-enablement-resources}

## 지원 리소스 {#add-an-enablement-resource} 추가

새 커뮤니티 사이트에 지원 리소스를 추가하려면:

* 작성자 인스턴스에서
   * 예: [http://localhost:4502/](http://localhost:4503/)
* 시스템 관리자로 로그인
* 전역 탐색에서 **커뮤니티 > [리소스](resources.md)**를 선택합니다.

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* 지원 리소스를 추가할 커뮤니티 사이트를 선택합니다
   * 선택 `Enablement Tutorial`
* 메뉴에서 ` Create` 을 선택합니다
* **[!UICONTROL 리소스]** 선택

![chlimage_1-201](assets/chlimage_1-201.png)

### 기본 정보 {#basic-info}

리소스에 대한 기본 정보를 입력합니다.

* **[!UICONTROL 사이트 이름]**:선택한 커뮤니티 사이트의 이름으로 설정합니다.사용 자습서
* **[!UICONTROL 리소스 이름(&amp;A);]**:스키 레슨 1
* **[!UICONTROL 태그]**:자습서:스포츠/스키
* **[!UICONTROL 카탈로그에 표시]**:설정
* **[!UICONTROL 설명]**:초보자용 눈 위에서 미끄러지듯
* **[!UICONTROL 이미지 추가]**:지정 뷰에서 멤버에 리소스를 나타내는 이미지를 추가합니다
   ![chlimage_1-202](assets/chlimage_1-202.png)
* **[!UICONTROL 다음]**&#x200B;을 선택합니다

### 컨텐트 추가 {#add-content}

여러 리소스를 선택한 것처럼 표시되지만 하나만 허용됩니다.

오른쪽 상단 모서리에서 `'+' icon` 을 선택하여 소스를 식별하여 리소스를 선택하는 프로세스를 시작합니다.

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

리소스를 업로드합니다. 비디오 리소스가 있는 경우, 비디오가 재생을 시작하기 전에 표시할 사용자 지정 이미지를 업로드하거나, 비디오에서 축소판을 생성하도록 합니다(몇 분 정도 걸릴 수 있으며, 기다릴 필요가 없음).

![chlimage_1-205](assets/chlimage_1-205.png)

* **[!UICONTROL 다음]** 선택

### 설정 {#settings}

* **[!UICONTROL 소셜]**
설정학습자가 기본 설정을 사용하여 역량 요소의 주석 달기 및 등급 지정을 경험하십시오.
* **[!UICONTROL 기한]**

   *(선택 사항)*  지정을 완료해야 하는 날짜를 선택할 수 있습니다.
* **[!UICONTROL 리소스 작성자]**

   *(선택 사항)* 비워 둡니다.
* **[!UICONTROL 리소스 연락처(&amp;A);]**

   *(필수)* 풀다운 메뉴를 사용하여 멤버를 선택합니다  `Quinn Harper`.
* **[!UICONTROL 리소스 전문가]**

   *(선택 사항)* 비워 둡니다.
   **참고**:사용자 또는 그룹이 표시되지 않으면 해당 사용자 또는 그룹이 게시  `Community Enable Members` 인스턴스에 추가되고  ** 저장되었는지 확인합니다.
   ![chlimage_1-206](assets/chlimage_1-206.png)
* **[!UICONTROL 다음]**&#x200B;을 선택합니다

### 할당 {#assignments}

* **[!UICONTROL 이]**
지원 리소스가 학습 경로에 추가되므로 AssignersLeave unset를 해제합니다. 학습자가 사용 자원이 포함된 학습 경로 및 개별 지원 자원에 지정되면, 학습자는 활성 자원에 두 번 할당됩니다.

![chlimage_1-207](assets/chlimage_1-207.png)

* **[!UICONTROL 만들기]**&#x200B;를 선택합니다

![chlimage_1-208](assets/chlimage_1-208.png)

리소스를 성공적으로 만들면 새로 만든 리소스가 선택된 리소스 콘솔로 돌아갑니다. 이 콘솔에서 학습자를 게시, 추가 및 기타 설정을 변경할 수 있습니다.

사용 리소스의 새 버전을 업로드하려면 새 리소스를 만든 다음 이전 버전에서 구성원 등록을 취소하고 새 버전에 등록하는 것이 좋습니다.

### 리소스 {#publish-the-resource} 게시

등록자가 지정된 강좌를 보려면 먼저 게시해야 합니다.

* `Publish`월드 아이콘을 선택합니다

활성화는 성공 메시지와 함께 확인됩니다.

![chlimage_1-209](assets/chlimage_1-209.png)

## 두 번째 사용 리소스 {#add-a-second-enablement-resource} 추가

위의 단계를 반복하여 학습 경로를 만들 두 번째 관련 지원 리소스를 만들고 게시합니다.

![chlimage_1-210](assets/chlimage_1-210.png)

**** 두 번째 리소스를 게시합니다.

리소스의 지원 자습서 목록으로 돌아갑니다.

*힌트:두 리소스 모두 표시되지 않으면 페이지를 새로 고칩니다.*

![chlimage_1-211](assets/chlimage_1-211.png)

## 학습 경로 {#add-a-learning-path} 추가

학습 경로는 강좌를 구성하는 지원 리소스의 논리적 그룹입니다.

* 리소스 콘솔에서 `+ Create` 을 선택합니다.
* **[!UICONTROL 학습 경로]** 선택

![chlimage_1-212](assets/chlimage_1-212.png)

**[!UICONTROL 기본 정보]** 추가:

* **[!UICONTROL 학습 경로 이름]**:스키 레슨
* **[!UICONTROL 태그]**:자습서:스키
* **[!UICONTROL 카탈로그에 표시]**:선택 안 함
* **[!UICONTROL 리소스]** 콘솔에서 학습 경로를 나타내는 이미지를 업로드합니다.

![chlimage_1-213](assets/chlimage_1-213.png)

* **[!UICONTROL 다음]**&#x200B;을 선택합니다

추가할 필수 구성 요소 학습 경로가 없으므로 다음 패널을 건너뜁니다.

* **[!UICONTROL 다음]**&#x200B;을 선택합니다

리소스 추가 패널에서

* 학습 경로에 추가할 2개의 스키 세션 리소스를 선택하려면 `+ Add Resources` 을 선택합니다

   참고:**게시된** 리소스만 선택할 수 있습니다.

>[!NOTE]
>
>학습 경로와 동일한 수준에서 사용할 수 있는 리소스만 선택할 수 있습니다. 예를 들어, 그룹에 생성된 학습 경로의 경우 그룹 수준 리소스만 사용할 수 있습니다.커뮤니티 사이트에서 생성된 학습 경로의 경우 해당 사이트의 리소스를 학습 경로에 추가할 수 있습니다.

* **[!UICONTROL 제출]**&#x200B;을 선택합니다.

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* **[!UICONTROL 다음]**&#x200B;을 선택합니다

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL 할당]**
추가풀다운 메뉴를 사용하여 
`Community Ski Class` 그룹, 구성원  `Riley Taylor` 및  `Sidney Croft.`

* **[!UICONTROL 학습 경로 연락처(&amp;A);]**

   *(필수)* 풀다운 메뉴를 사용하여 멤버를 선택합니다  `Quinn Harper`.

* **[!UICONTROL 만들기]**&#x200B;를 선택합니다

![chlimage_1-217](assets/chlimage_1-217.png)

학습 경로를 성공적으로 만들면 새로 만든 학습 경로가 선택된 리소스 콘솔로 돌아갑니다. 이 콘솔에서 학습자를 게시, 추가 및 기타 설정을 변경할 수 있습니다.

**** 학습 경로를 게시합니다.
