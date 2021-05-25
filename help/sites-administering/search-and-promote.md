---
title: Adobe Search & Promote과 통합
seo-title: Adobe Search & Promote과 통합
description: 을 Adobe Search & Promote과 통합하는 방법을 알아봅니다.
seo-description: 을 Adobe Search & Promote과 통합하는 방법을 알아봅니다.
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
exl-id: 2bbcc8d0-c1c7-4901-836f-44b8a2153a46
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 1%

---

# Adobe Search &amp; Promote{#integrating-with-adobe-search-promote}과 통합

웹 사이트에서 Adobe Search &amp; Promote 서비스를 호출하려면 다음 작업을 수행하십시오.

1. 클라우드의 URL을 지정합니다.
1. Search &amp; Promote 서비스에 대한 연결을 구성합니다.
1. [!UICONTROL 사이드킥에 Search &amp; Promote 구성 요소를 추가합니다].
1. 구성 요소를 사용하여 컨텐츠를 작성합니다. ([웹 페이지에 Search &amp; Promote 기능 추가](/help/sites-authoring/search-and-promote.md)를 참조하십시오.)
1. 페이지에 배너를 추가합니다. 배너 이미지는 Search &amp; Promote 데이터에 민감합니다.
1. Search &amp; Promote 서비스가 사용할 사이트 맵을 생성합니다.

>[!NOTE]
>
>사용자 지정 프록시 구성에서 Search &amp; Promote을 사용하는 경우 AEM의 일부 기능이 3.x API를 사용하고 4.x API를 사용하는 것과 같은 HTTP 클라이언트 프록시 구성을 모두 구성해야 합니다.
>
>* 3.x는 [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x는 [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## Search &amp; Promote 서비스 URL {#changing-the-search-promote-service-url} 변경

Search &amp; Promote 서비스에 대해 구성된 기본 URL은 `https://searchandpromote.omniture.com/px/`입니다. 다른 서비스를 사용하려면 OSGi 콘솔을 사용하여 다른 URL을 지정하십시오.

**Search &amp; Promote 서비스 URL을 변경하려면**:

1. [!UICONTROL OSGi] 콘솔을 열고 **[!UICONTROL 구성]** 탭을 탭합니다. ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. **[!UICONTROL 일 CQ Search &amp; Promote 구성]** 항목을 클릭합니다.
1. **[!UICONTROL 원격 서버 URI]** 텍스트 필드에 URL을 입력한 다음 **[!UICONTROL 저장]**&#x200B;을 누릅니다.

## Search &amp; Promote {#configuring-the-connection-to-search-promote}에 연결 구성

웹 페이지가 서비스와 상호 작용할 수 있도록 Search &amp; Promote에 대해 하나 이상의 연결을 구성합니다. 연결하려면 Search &amp; Promote 계정의 멤버 식별과 계정 번호가 필요합니다.

**Search &amp; Promote에 대한 연결을 구성하려면**:

1. **[!UICONTROL 도구]** 아이콘 > **[!UICONTROL 배포]** Cloud Services ]**을 선택합니다.**[!UICONTROL 

   이렇게 하면 Cloud Services 대시보드로 이동합니다. 로컬 컴퓨터에서 대시보드의 URL은 다음과 같이 표시됩니다.

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. [!UICONTROL Cloud Services] 페이지에서 **[!UICONTROL Adobe Search &amp; Promote]** 링크 또는 **[!UICONTROL Search &amp; Promote]** 아이콘을 탭합니다.

1. Adobe Search &amp; Promote을 처음 구성하는 경우 **[!UICONTROL 지금 구성]**&#x200B;을 눌러 [!UICONTROL 구성 만들기] 패널을 엽니다.

   Search &amp; Promote에 대해 자세히 알아보려면 **[!UICONTROL 추가 정보]**&#x200B;를 대신 클릭하십시오.

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. 페이지 작성자가 인식할 수 있는 **[!UICONTROL 제목]**&#x200B;을 입력하고 고유한 **[!UICONTROL 이름]**&#x200B;을 입력한 다음 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.

   또한 새로 만든 구성은 **[!UICONTROL Cloud Services 대시보드]** Adobe Search &amp; Promote 목록 항목의 **[!UICONTROL 사용 가능한 구성]** 아래에 나타납니다.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. [!UICONTROL 구성 요소 편집] 대화 상자에서 다음 내용을 필드에 추가합니다.

   * **[!UICONTROL 구성원 ID]**
   * **[!UICONTROL 계정 번호]**

   >[!NOTE]
   >
   >이 정보를 직접 얻으려면 다음 항목에 로그인합니다.
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >유효한 Search&amp;Promote 자격 증명 사용(이메일/암호).
   >
   >브라우저의 주소 표시줄에 URL을 확인합니다. 다음과 유사한 모양입니다.
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >여기서 **XXXXXXXX**&#x200B;은(는) **[!UICONTROL 멤버 id]** 및 **[!UICONTROL spYYYYYYY]**&#x200B;에 해당하는 계정 번호입니다.

1. **[!UICONTROL Search &amp; Promote에 연결]**&#x200B;을 누릅니다.

   연결 성공 메시지가 나타나면 **[!UICONTROL 확인]**&#x200B;을 누릅니다.

   (연결 후 단추 텍스트가 **[!UICONTROL Search &amp; Promote]**&#x200B;에 다시 연결되도록 변경됩니다.)

1. **[!UICONTROL 확인]**&#x200B;을 누릅니다. 방금 만든 구성에 대한 Search &amp; Promote 설정 페이지가 나타납니다.

## 데이터 센터 구성 {#configuring-the-data-center}

Search &amp; Promote 계정이 아시아 또는 유럽에 있는 경우 올바른 데이터 센터를 가리키도록 기본 데이터 센터를 변경해야 합니다(기본 데이터 센터는 북미 계정의 경우).

**데이터 센터를 구성하려면**:

1. `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`의 웹 콘솔로 이동합니다.

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 서버의 위치에 따라 URI를 다음 중 하나로 변경합니다.

   * 북미:[https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA:[https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC:[https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

## 사이드 킥에 Search &amp; Promote 구성 요소 추가 {#adding-search-promote-components-to-sidekick}

[!UICONTROL 디자인] 모드에서 **[!UICONTROL par]** 구성 요소를 편집하여 [!UICONTROL 사이드킥의 Search &amp; Promote 구성 요소를 허용합니다]. (자세한 내용은 [구성 요소](/help/sites-developing/components.md) 설명서 를 참조하십시오.)

구성 요소 사용에 대한 자세한 내용은 [웹 페이지에 Search &amp; Promote 기능 추가](/help/sites-authoring/search-and-promote.md)를 참조하십시오.

## 페이지에서 {#specifying-the-search-promote-service-that-your-pages-use}을 사용하는 Search &amp; Promote 서비스 지정

웹 페이지가 특정 Search &amp; Promote 서비스를 사용하도록 구성합니다. Search &amp; Promote 구성 요소는 자동으로 호스트 페이지의 서비스를 사용합니다.

페이지에 대한 Search &amp; Promote 속성을 구성하면 모든 하위 페이지가 설정을 상속합니다. 필요한 경우 상속된 설정을 재정의하도록 하위 페이지를 구성할 수 있습니다.

>[!NOTE]
>
>서비스 연결을 이미 구성해야 합니다. [Search &amp; Promote](#configuring-the-connection-to-search-promote)에 연결 구성 을 참조하십시오.

1. **[!UICONTROL 페이지 속성]** 대화 상자를 엽니다. 예를 들어 **[!UICONTROL 웹 사이트]** 페이지에서 페이지를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.

1. **[!UICONTROL Cloud Services]** 탭을 클릭합니다.

1. 상위 페이지에서 클라우드 서비스 구성 상속을 비활성화하려면 상속 경로 옆에 있는 자물쇠 아이콘을 클릭합니다.

   ![샌드핀 상속 자물쇠](assets/sandpinheritpadlock.png)

1. **[!UICONTROL 서비스 추가]**&#x200B;를 클릭하고 **[!UICONTROL Adobe Search &amp; Promote]**&#x200B;을 선택한 다음 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

1. Search &amp; Promote 계정에 대한 연결 구성을 선택한 다음 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

## 제품 피드 {#product-feed}

Search &amp; Promote 통합을 통해 다음을 수행할 수 있습니다.

* 기본 저장소 구조 및 상거래 플랫폼과 독립적으로 [!UICONTROL eCommerce] API를 사용하십시오.
* Search &amp; Promote의 [!UICONTROL Index Connector] 기능을 활용하여 제품 피드를 XML 형식으로 제공합니다.
* Search &amp; Promote의 [!UICONTROL 원격 제어] 기능을 활용하여 제품 피드의 요청 시 또는 예약된 요청을 수행합니다.
* 클라우드 서비스 구성으로 구성된 다양한 Search &amp; Promote 계정에 대한 피드 생성.

자세한 내용은 [제품 피드](/help/sites-administering/product-feed.md)를 참조하십시오.
