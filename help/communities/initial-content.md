---
title: 초기 샌드박스 컨텐츠
seo-title: 초기 샌드박스 컨텐츠
description: 콘텐츠 만들기
seo-description: 콘텐츠 만들기
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
exl-id: 171fd95d-51f6-468b-84ed-4a757dba868e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 7%

---

# 초기 샌드박스 컨텐츠 {#initial-sandbox-content}

이 섹션에서는 모두 [페이지 템플릿](initial-app.md#createthepagetemplate)을 사용하는 다음 페이지를 만듭니다.

* 기본 페이지의 영어 버전으로 리디렉션되는 SCF 샌드박스 사이트

   * SCF 샌드박스 - 사이트의 영어 버전에 대한 기본 페이지입니다

      * SCF 재생 - 재생할 기본 페이지의 하위 페이지입니다

이 자습서는 [언어 사본](../../help/sites-administering/tc-prep.md)을 학습하지 않지만, 루트 페이지가 HTML 헤더를 통해 사용자에 대한 기본 언어 탐지를 구현하고 해당 언어에 대한 기본 페이지로 리디렉션할 수 있도록 디자인되었습니다. 이 규칙은 페이지의 노드 이름에 두 문자로 이루어진 국가 코드를 사용하는 것입니다. 예를 들어, &quot;en&quot;은 영어로, &quot;fr&quot;은 프랑스어로 사용됩니다.

## 첫 번째 페이지 만들기 {#create-first-pages}

이제 [페이지 템플릿](initial-app.md#createthepagetemplate)이 있으므로 /content 디렉터리에 웹 사이트의 루트 페이지를 설정할 수 있습니다.

1. 표준 UI는 현재 사이트 작성에 대한 청사진을 제공합니다. 이 자습서에서는 간단한 사이트를 만들 수 있으므로 클래식 UI가 유용합니다.

   클래식 UI로 전환하려면 전역 탐색 을 선택하고 프로젝트 아이콘 오른쪽을 마우스로 가리킵니다. 표시되는 *클래식 UI로 전환* 아이콘을 선택합니다.

   ![chlimage_1-36](assets/chlimage_1-36.png)

   클래식 UI로 전환할 수 있는 기능은 관리자가 [활성화해야 합니다](../../help/sites-administering/enable-classic-ui.md).

1. [클래식 UI 시작 페이지](http://localhost:4502/welcome.html)웹 사이트&#x200B;]**를 선택합니다.**[!UICONTROL 

   ![chlimage_1-37](assets/chlimage_1-37.png)

   또는 [/siteadmin.](http://localhost:4502/siteadmin)

1. 탐색기 창에서 **[!UICONTROL 웹 사이트]**&#x200B;를 선택한 다음 도구 모음에서 **[!UICONTROL 새로 만들기 > 새 페이지]**&#x200B;를 선택합니다.

   **[!UICONTROL 페이지 만들기]** 대화 상자에서 다음을 입력합니다.

   * 제목: `SCF Sandbox Site`
   * 이름: `an-scf-sandbox`
   * **[!UICONTROL SCF 샌드박스 재생 템플릿]**&#x200B;을 선택합니다.
   * **[!UICONTROL 만들기]**&#x200B;를 클릭합니다

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. 탐색기 창에서 방금 만든 페이지 `/Websites/SCF Sandbox Site`을 선택하고 **[!UICONTROL 새로 만들기 > 새 페이지]**&#x200B;를 클릭합니다.

   * 제목: `SCF Sandbox`
   * 이름: `en`
   * **SCF 샌드박스 재생 템플릿**&#x200B;을 선택합니다.
   * **만들기**&#x200B;를 클릭합니다

1. 탐색기 창에서 방금 만든 페이지 `/Websites/SCF Sandbox Site/SCF Sandbox`을 선택하고 **[!UICONTROL 새로 만들기 > 새 페이지]**&#x200B;를 클릭합니다

   * 제목: `SCF Play`
   * 이름: `play`
   * **[!UICONTROL SCF 샌드박스 재생 템플릿]**&#x200B;을 선택합니다.
   * **[!UICONTROL 만들기]**&#x200B;를 클릭합니다

1. 웹 사이트 콘솔에 웹 사이트가 표시되는 방식입니다. 탐색기 창에서 선택한 항목의 하위 페이지가 관리할 수 있는 오른쪽 창에 표시됩니다.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   웹 사이트 도구 및 템플릿을 사용하여 만든 저장소 보기입니다.

   ![chlimage_1-40](assets/chlimage_1-40.png)

## 디자인 경로 {#add-the-design-path} 추가

도구 콘솔의 디자인 섹션을 사용하여 ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)`을 만들면 &quot; 속성이 만들어집니다.

* `cq:template="/libs/wcm/core/templates/designpage"`

가 정의되었으며, 이 값은 `currentDesign.getPath()`을 사용하여 스크립트에서 디자인 자산을 참조할 수 있는 선택 기능을 제공합니다. 예

* &lt;>


   * 이름: `cq:designPath`
   * 유형: `String`
   * 값: `/etc/designs/an-scf-sandbox`

* 녹색 `[+] Add` 을 클릭합니다

응답은 다음과 같이 표시됩니다.

![chlimage_1-41](assets/chlimage_1-41.png)

* **[!UICONTROL 모두 저장]** 클릭

[ 저축하는 데 문제가 있습니까? 다시 로그인!]

>[!NOTE]
>
>cq:designPath의 사용은 선택 사항이며, clientlibs](develop-app.md#includeclientlibsintemplate) 사용과 관련이 없습니다. 이 사용은 SCF 구성 요소가 [clientlibs](client-customize.md#clientlibs-for-scf)를 사용하여 JS 및 CSS를 관리하므로 기본적으로 필요합니다.[
