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
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 7%

---


# 초기 샌드박스 컨텐츠 {#initial-sandbox-content}

이 섹션에서는 모두 [페이지 템플릿](initial-app.md#createthepagetemplate)을 사용하는 다음 페이지를 만듭니다.

* 기본 페이지의 영어 버전으로 리디렉션되는 SCF 샌드박스 사이트

   * SCF 샌드박스 - 사이트의 영어 버전에 대한 기본 페이지

      * SCF 재생 - 재생할 기본 페이지의 하위 페이지

이 자습서는 [언어 사본](../../help/sites-administering/tc-prep.md)에 대한 내용은 아니지만 루트 페이지가 HTML 헤더를 통해 사용자에 대한 기본 언어를 감지하고 해당 언어에 대한 적절한 기본 페이지로 리디렉션할 수 있도록 디자인되었습니다. 이 규칙은 페이지의 노드 이름에 2자로 된 국가 코드를 사용합니다(예: 영어의 경우 &quot;en&quot;, 프랑스어의 경우 &quot;fr&quot;).

## 첫 번째 페이지 만들기 {#create-first-pages}

이제 [페이지 템플릿](initial-app.md#createthepagetemplate)이 있으므로 /content 디렉토리에 웹 사이트의 루트 페이지를 설정할 수 있습니다.

1. 표준 UI는 현재 사이트 만들기에 대한 청사진을 제공합니다. 이 자습서는 간단한 사이트를 만드는 것이므로 클래식 UI가 유용합니다.

   클래식 UI로 전환하려면 글로벌 탐색을 선택하고 프로젝트 아이콘 오른쪽에 마우스를 놓습니다. 나타나는 *클래식 UI로 전환* 아이콘을 선택합니다.

   ![chlimage_1-36](assets/chlimage_1-36.png)

   클래식 UI로 전환하는 기능은 [관리자가 활성화해야 합니다](../../help/sites-administering/enable-classic-ui.md).

1. [클래식 UI 시작 페이지](http://localhost:4502/welcome.html)에서 **[!UICONTROL 웹 사이트]**&#x200B;를 선택합니다.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   또는 [/siteadmin](http://localhost:4502/siteadmin)으로 이동하여 웹 사이트에 대한 클래식 UI에 직접 액세스합니다.

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

1. 탐색기 창에서 방금 만든 페이지 `/Websites/SCF Sandbox Site/SCF Sandbox`을 선택하고 **[!UICONTROL 새로 만들기 > 새 페이지]**&#x200B;를 클릭합니다.

   * 제목: `SCF Play`
   * 이름: `play`
   * **[!UICONTROL SCF 샌드박스 재생 템플릿]**&#x200B;을 선택합니다.
   * **[!UICONTROL 만들기]**&#x200B;를 클릭합니다

1. 이제 웹 사이트가 웹 사이트 콘솔에 표시되는 방식을 살펴봅니다. 탐색기 창에서 선택한 항목의 하위 페이지가 관리될 수 있는 오른쪽 창에 표시됩니다.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   웹 사이트 도구 및 템플릿을 사용하여 만든 항목의 저장소 보기입니다.

   ![chlimage_1-40](assets/chlimage_1-40.png)

## 디자인 경로 {#add-the-design-path} 추가

도구 콘솔의 디자인 섹션을 사용하여 ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)`이(가) 만들어지면 속성 &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

가 정의되었습니다. 이 변수는 `currentDesign.getPath()`을(를) 사용하여 스크립트에서 디자인 에셋을 참조하는 선택 사항을 제공합니다. 예

* &lt;>


   * 이름: `cq:designPath`
   * 유형: `String`
   * 값: `/etc/designs/an-scf-sandbox`

* 녹색 `[+] Add`

응답은 다음과 같이 표시됩니다.

![chlimage_1-41](assets/chlimage_1-41.png)

* **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

[ 저장하는 데 문제가 있습니까? 다시 로그인!]

>[!NOTE]
>
>cq:designPath의 사용은 선택 사항이며, SCF 구성 요소가 [clientlibs](client-customize.md#clientlibs-for-scf)을 사용하여 JS 및 CSS를 관리할 때 기본적으로 필요한 [clientlibs](develop-app.md#includeclientlibsintemplate)의 사용과는 관련이 없습니다.

