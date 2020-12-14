---
title: Clientlibs 추가
seo-title: Clientlibs 추가
description: ClientLibraryFolder 추가
seo-description: ClientLibraryFolder 추가
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 805e4411930749ff4b6b05ea4a8b87b4f96d72fd
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 4%

---


# Clientlibs {#add-clientlibs} 추가

## ClientLibraryFolder(clientlibs) {#add-a-clientlibraryfolder-clientlibs} 추가

사이트의 페이지를 렌더링하는 데 사용되는 JS와 CSS를 포함할 `clientlibs`라는 ClientLibraryFolder를 만듭니다.

이 클라이언트 라이브러리에 지정된 `categories`속성 값은 컨텐츠 페이지에서 이 clientlib을 직접 포함하거나 다른 clientlibs에 포함하는 데 사용되는 식별자입니다.

1. **[!UICONTROL CRXDE Lite]**&#x200B;을 사용하여 `/etc/designs` 확장

1. `an-scf-sandbox`을 마우스 오른쪽 단추로 클릭하고 `Create Node` 선택

   * 이름: `clientlibs`
   * 유형: `cq:ClientLibraryFolder`

1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다

![chlimage_1-220](assets/chlimage_1-220.png)

새 `clientlibs` 노드의 **[!UICONTROL 속성]** 탭에서 **`categories`** 속성을 입력합니다.

* 이름:**[!UICONTROL 카테고리]**
* 유형:**[!UICONTROL String]**
* 값:**[!UICONTROL apps.an-scf-sandbox]**
* **[!UICONTROL 추가]**&#x200B;를 클릭합니다
* **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

참고:&#39;apps&#39;로 카테고리 값 앞에 표시 는 &#39;소유 응용 프로그램&#39;이 /libs가 아닌 /apps 폴더에 있는 것으로 식별하기 위한 규칙입니다.  중요:자리 표시자 `js.txt` 및 `css.txt` 파일을 추가합니다. 공식적으로 cq:ClientLibraryFolder가 없는 것은 아닙니다.


1. **`/etc/designs/an-scf-sandbox/clientlibs`**&#x200B;을(를) 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL 파일 만들기...를 선택합니다.]**
1. **[!UICONTROL 이름]**&#x200B;을 입력합니다.`css.txt`

1. **[!UICONTROL 파일 만들기...를 선택합니다.]**
1. **[!UICONTROL 이름]**&#x200B;을 입력합니다.`js.txt`

1. **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

![chlimage_1-221](assets/chlimage_1-221.png)

css.txt 및 js.txt의 첫 행은 다음 파일 목록을 찾을 기본 위치를 식별합니다.

css.txt의 컨텐츠를 다음과 같이 설정합니다.

```
#base=.
 style.css
```

그런 다음 style.css라는 clientlibs 아래에 파일을 만들고 내용을 다음으로 설정합니다.

`body {`

`background-color: #b0c4de;`

`}`

## SCF Clientlibs {#embed-scf-clientlibs} 포함

`clientlibs` 노드의 **[!UICONTROL 속성]** 탭에서 다중 값 문자열 속성 **[!UICONTROL embed]**&#x200B;을 입력합니다. 이렇게 하면 SCF 구성 요소](client-customize.md#clientlibs-for-scf)에 필요한 [클라이언트측 라이브러리(clientlibs)가 포함됩니다. 이 자습서에서는 커뮤니티 구성 요소에 필요한 많은 클라이언트를 추가합니다.

**모든 페이지에 대해 다운로드한 클라이언트의 크기/속도 및 편의에 대한 고려 사항이 있기 때문에 프로덕션 사이트에 사용하기 원하는 접근 방식이** 아니거나 이에 해당될 수 있습니다.

한 페이지에 하나의 기능을 사용하는 경우에만 해당 기능의 complete clientlib을 페이지에 직접 포함할 수 있습니다. 예를 들어, &lt;% ui:includeClientLib categories=cq.social.hbs.forum&quot; %>

이 경우 모든 SCF를 포함하므로 author clientlibs인 보다 기본적인 SCF clientlibs를 선호합니다.

* 이름: **`embed`**
* 유형: **`String`**

* 클릭 **`Multi`**
* 값: **`cq.social.scf`**

   *&lt;enter> 대화 상자가 표시됩니다.*

   *각 항목&#x200B;**[뒤에]**+를 클릭하여 다음 clientlib 범주를 추가합니다.*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * **[!UICONTROL 확인]**&#x200B;을 클릭합니다

* **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

![chlimage_1-222](assets/chlimage_1-222.png)

이제 `/etc/designs/an-scf-sandbox/clientlibs`이(가) 저장소에 표시되는 방식입니다.

![chlimage_1-223](assets/chlimage_1-223.png)

## PlayPage 템플릿에 클라이언트 포함 {#include-clientlibs-in-playpage-template}

페이지에 `apps.an-scf-sandbox` ClientLibraryFolder 범주를 포함하지 않으면 SCF 구성 요소가 기능하거나 스타일을 지정할 수 없으며 필요한 Javascript 및 스타일이므로 사용할 수 없습니다.

예를 들어 clientlibs를 포함하지 않는 SCF 주석 구성 요소는 스타일이 지정되지 않은 것으로 나타납니다.

![chlimage_1-224](assets/chlimage_1-224.png)

apps.an-scf-sandbox clientlibs가 포함되면, SCF 주석 구성 요소가 스타일이 지정된 것으로 나타납니다.

![chlimage_1-225](assets/chlimage_1-225.png)

include 문은 `<html>` 스크립트의 `<head>` 섹션에 속합니다. 기본 **`foundation head.jsp`**&#x200B;에는 오버레이할 수 있는 스크립트가 포함되어 있습니다.**`headlibs.jsp`**.

**headlibs.jsp를 복사하고 clientlibs를 포함합니다.**

1. **[!UICONTROL CRXDE Lite]**&#x200B;을 사용하여 **`/libs/foundation/components/page/headlibs.jsp`** 선택
1. 마우스 오른쪽 단추를 클릭하고 **[!UICONTROL 복사]**&#x200B;를 선택합니다(또는 도구 모음에서 복사를 선택합니다).
1. 선택 **`/apps/an-scf-sandbox/components/playpage`**
1. 마우스 오른쪽 단추를 클릭하고 **[!UICONTROL 붙여넣기]**(또는 도구 모음에서 붙여넣기)를 선택합니다.
1. **`headlibs.jsp`**&#x200B;을 두 번 클릭하여 엽니다.
1. 파일 끝에 다음 줄을 추가합니다.

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

브라우저에서 웹 사이트를 로드하고 배경이 파랑색이 아닌지 확인합니다.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## 지금까지 작업 저장 중 {#saving-your-work-so-far}

이때, 최소 샌드박스는 존재하며, 재생하는 동안 경험이 손상되고 다시 시작하려는 경우, 서버를 끄고, crx-quickstart/ 폴더의 이름을 바꾸거나 삭제하고, 서버를 켜거나, 이 저장된 패키지를 업로드 및 설치할 수 있으며 이러한 가장 기본적인 단계를 반복하지 않아도 됩니다.

이 패키지는 [샘플 페이지 만들기](create-sample-page.md) 튜토리얼에서 바로 들어가서 재생을 시작할 때까지 기다릴 수 없는 사용자를 위한 것입니다...

패키지를 만들려면:


* **[!UICONTROL CRXDE Lite]**&#x200B;에서 [패키지 아이콘](http://localhost:4502/crx/packmgr/)을 클릭합니다.
* **[!UICONTROL 패키지 만들기]**&#x200B;를 클릭합니다.

   * 패키지 이름: `an-scf-sandbox-minimal-pkg`
   * 버전: `0.1`
   * 그룹:&lt;기본값으로 유지>
   * **[!UICONTROL 확인]**&#x200B;을 클릭합니다

* **[!UICONTROL 편집]**&#x200B;을 클릭합니다

   * **[!UICONTROL 필터]** 탭 선택

      * **[!UICONTROL 필터 추가]**&#x200B;를 클릭합니다.
      * 루트 경로:`/apps/an-scf-sandbox` 찾아보기
      * **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
      * **[!UICONTROL 필터 추가]**&#x200B;를 클릭합니다.
      * 루트 경로:`/etc/designs/an-scf-sandbox` 찾아보기
      * **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
      * **[!UICONTROL 필터 추가]**&#x200B;를 클릭합니다.
      * 루트 경로:`/content/an-scf-sandbox` 찾아보기
      * **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
   * **[!UICONTROL 저장]**&#x200B;을 클릭합니다


* **[!UICONTROL 빌드]**&#x200B;를 클릭합니다.

이제 **[!UICONTROL 다운로드]**&#x200B;를 선택하여 디스크에 저장하고 다른 곳에서 **[!UICONTROL 패키지]**&#x200B;업로드 을 선택할 수 있을 뿐만 아니라, 샌드박스를 localhost 게시 인스턴스로 푸시하여 샌드박스의 영역을 확장하려면 **[!UICONTROL 자세히 > 복제]**&#x200B;를 선택합니다.
