---
title: Adobe Search & Promote과 통합
seo-title: Adobe Search & Promote과 통합
description: Adobe Search & Promote과 통합하는 방법을 살펴보십시오.
seo-description: Adobe Search & Promote과 통합하는 방법을 살펴보십시오.
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---


# Integrating with Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

웹 사이트에서 Adobe Search &amp; Promote 서비스를 호출하려면 다음 작업을 수행하십시오.

1. 클라우드 URL을 지정합니다.
1. Search &amp; Promote 서비스에 대한 연결을 구성합니다.
1. 사이드 킥에 Search &amp; Promote 구성 요소를 [!UICONTROL 추가합니다].
1. 구성 요소를 사용하여 컨텐츠를 작성합니다. 웹 페이지에 [Search &amp; Promote 기능 추가를 참조하십시오](/help/sites-authoring/search-and-promote.md).
1. 페이지에 배너를 추가합니다. 배너 이미지는 Search &amp; Promote 데이터에 민감합니다.
1. Search &amp; Promote 서비스가 사용할 사이트 맵을 생성합니다.

>[!NOTE]
>
>사용자 지정 프록시 구성과 함께 Search &amp; Promote을 사용하는 경우, AEM의 일부 기능에서 3.x API를 사용하고 일부 다른 기능은 4.x API를 사용하고 있는 것처럼 두 HTTP 클라이언트 프록시 구성을 구성해야 합니다.
>
>* 3.x는 http://localhost:4502/system/console/configMgr/com.day.commons.httpclient으로 [구성됩니다.](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x는 http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator으로 [구성됩니다.](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## Search &amp; Promote 서비스 URL 변경 {#changing-the-search-promote-service-url}

Search &amp; Promote 서비스에 대해 구성된 기본 URL입니다 `https://searchandpromote.omniture.com/px/`. 다른 서비스를 사용하려면 OSGi 콘솔을 사용하여 다른 URL을 지정합니다.

**Search &amp; Promote 서비스 URL을 변경하려면 다음을 수행하십시오**.

1. OSGi [!UICONTROL 콘솔을] 열고 구성 **[!UICONTROL 탭을]** 누릅니다. ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. Day CQ **[!UICONTROL Search &amp; Promote 구성]** 항목을 클릭합니다.
1. [ **[!UICONTROL 원격 서버 URI]** ] 텍스트 필드에 URL을 입력한 다음 **[!UICONTROL 저장을 탭합니다]**.

## Search &amp; Promote에 연결 구성 {#configuring-the-connection-to-search-promote}

웹 페이지가 서비스와 상호 작용할 수 있도록 하나 이상의 Search &amp; Promote 연결을 구성합니다. 연결하려면 Search &amp; Promote 계정의 멤버 ID와 계정 번호가 필요합니다.

**Search &amp; Promote에 대한 연결을 구성하려면 다음을 수행하십시오**.

1. 도구 **[!UICONTROL 아이콘]** > **[!UICONTROL 배포에서]** Cloud Services을 선택합니다 ****.

   Cloud Services 대시보드로 이동합니다. 로컬 시스템에서 대시보드의 URL은 다음과 같습니다.

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Cloud Services [!UICONTROL 페이지에서] Adobe Search &amp; Promote **[!UICONTROL 링크 또는]** Search &amp; Promote **[!UICONTROL 아이콘을]** 누릅니다.

1. 처음으로 Adobe Search &amp; Promote을 구성하는 경우 지금 구성 **[!UICONTROL 을]** 눌러 구성 [!UICONTROL 만들기] 패널을 엽니다.

   Search &amp; Promote에 대한 자세한 내용을 보려면 **[!UICONTROL 자세한 내용을]** 클릭하십시오.

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. 페이지 작성자가 인식할 수 있는 **[!UICONTROL 제목을]** 입력하고 고유한 **[!UICONTROL 이름을]**&#x200B;입력한 다음 **[!UICONTROL 만들기를]**&#x200B;누릅니다.

   또한 새로 만든 구성은 Cloud Services 대시보드 **[!UICONTROL Adobe 목록 항목]** 의 사용 가능한 구성 **[!UICONTROL 아래에]** 나타납니다.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 구성 요소 [!UICONTROL 편집] 대화 상자에서 필드에 다음을 추가합니다.

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
   >브라우저의 주소 표시줄에 있는 URL을 확인합니다. 다음과 유사한 모양이 되어야 합니다.
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >여기서 **XXXXXXXX는** **[!UICONTROL 멤버 id]** 에 해당하고 **[!UICONTROL spYYYYYYYY는]** 계정 번호에 해당합니다.

1. Tap **[!UICONTROL Connect To Search&amp;Promote]**.

   연결 성공 메시지가 나타나면 **[!UICONTROL 확인을 누릅니다]**.

   연결 후 단추 텍스트가 [Search &amp; Promote에 **[!UICONTROL 다시 연결]으로 변경됩니다]**.

1. 확인을 **[!UICONTROL 누릅니다]**. 방금 만든 구성에 대해 [Search &amp; Promote 설정] 페이지가 나타납니다.

## 데이터 센터 구성 {#configuring-the-data-center}

Search &amp; Promote 계정이 아시아 또는 유럽에 있는 경우 기본 데이터 센터를 올바른 데이터 센터로 가리키도록 변경해야 합니다(기본 데이터 센터는 북미 계정).

**데이터 센터를 구성하려면 다음을 수행하십시오**.

1. 웹 콘솔 탐색( `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 서버 위치에 따라 URI를 다음 중 하나로 변경합니다.

   * 북미: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. 저장을 **[!UICONTROL 누릅니다]**.

## 사이드 킥에 Search &amp; Promote 구성 요소 추가 {#adding-search-promote-components-to-sidekick}

디자인  모드에서 **[!UICONTROL 단락]** 구성 요소를 편집하여 사이드 킥의 Search &amp; Promote 구성 요소를 [!UICONTROL 허용합니다]. (See the [Components](/help/sites-developing/components.md) documentation for more information.)

구성 요소 사용에 대한 자세한 내용은 웹 페이지에 [Search &amp; Promote 기능 추가를 참조하십시오](/help/sites-authoring/search-and-promote.md).

## 페이지에서 사용하는 Search &amp; Promote 서비스 지정 {#specifying-the-search-promote-service-that-your-pages-use}

특정 Search &amp; Promote 서비스를 사용하도록 웹 페이지를 구성합니다. Search &amp; Promote 구성 요소는 호스트 페이지의 서비스를 자동으로 사용합니다.

페이지의 Search &amp; Promote 속성을 구성하면 모든 하위 페이지가 설정을 상속합니다. 필요한 경우 상속된 설정을 무시하도록 하위 페이지를 구성할 수 있습니다.

>[!NOTE]
>
>서비스 연결이 이미 구성되어 있어야 합니다. Search &amp; Promote [에 대한 연결 구성을 참조하십시오](#configuring-the-connection-to-search-promote).

1. 페이지 **[!UICONTROL 속성]** 대화 상자를 엽니다. 예를 들어 웹 사이트 **** 페이지에서 페이지를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성을 클릭합니다]**.

1. Cloud Services **[!UICONTROL 탭을]** 클릭합니다.

1. 상위 페이지에서 클라우드 서비스 구성 상속을 비활성화하려면 상속 경로 옆에 있는 자물쇠 아이콘을 클릭합니다.

   ![샌드핀 상속 자물쇠](assets/sandpinheritpadlock.png)

1. 서비스 **[!UICONTROL 추가를]**&#x200B;클릭하고 **[!UICONTROL Adobe Search &amp; Promote]**&#x200B;를 선택한 다음 **[!UICONTROL 확인을 클릭합니다]**.

1. Search &amp; Promote 계정에 대한 연결 구성을 선택한 다음 **[!UICONTROL 확인을 클릭합니다]**.

## Product Feed {#product-feed}

Search &amp; Promote 통합을 통해 다음을 수행할 수 있습니다.

* 기본 [!UICONTROL 저장소 구조 및 상거래 플랫폼과는] 별도로 eCommerce API를 사용하십시오.
* Search &amp; Promote의 [!UICONTROL 색인 커넥터] 기능을 활용하여 제품 피드를 XML 형식으로 제공합니다.
* Search &amp; Promote의 [!UICONTROL 원격 제어] 기능을 활용하여 제품 피드의 on-demand 또는 예약된 요청을 수행할 수 있습니다.
* 클라우드 서비스 구성으로 구성된 다양한 Search &amp; Promote 계정에 대한 피드 생성

자세한 내용은 [제품 피드를 참조하십시오](/help/sites-administering/product-feed.md).
