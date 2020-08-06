---
title: 통신 UI 사용자 정의
seo-title: 통신 UI 사용자 정의
description: 서신 UI를 사용자 정의하는 방법을 알아봅니다.
seo-description: 서신 UI를 사용자 정의하는 방법을 알아봅니다.
uuid: 5b6eb8fd-0270-4638-bdf4-cb7015919d57
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 3efd8f5a-9f38-4d9b-88d6-d8fde6c9a644
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '1106'
ht-degree: 0%

---


# 통신 UI 사용자 정의 {#customize-create-correspondence-ui}

## 개요 {#overview}

통신 관리를 사용하면 솔루션 템플릿을 다시 브랜딩하여 브랜드 가치를 높이고 조직의 브랜드 표준을 준수할 수 있습니다. 사용자 인터페이스의 재브랜딩에는 통신 UI 만들기의 왼쪽 상단에 표시되는 조직 로고 변경이 포함됩니다.

조직의 로고로 통신 UI 만들기에서 로고를 변경할 수 있습니다.

![통신 UI 만들기의 사용자 지정 아이콘](assets/0_1_introscreenshot.png)**:** *통신 UI 만들기의 사용자 지정 아이콘*

### 서신 작성 UI에서 로고 변경 {#changing-the-logo-in-the-create-correspondence-ui}

원하는 로고 이미지를 설정하려면 다음을 수행합니다.

1. CRX에서 적절한 [폴더 구조를 만듭니다](#creatingfolderstructure).
1. [CRX에서 만든 폴더에 새 로고 파일을](#uploadlogo) 업로드합니다.

1. [CRX에](#createcss) CSS를 설정하여 새 로고를 참조합니다.
1. 브라우저 내역을 지우고 통신 만들기 UI를 [새로 고칩니다](#refreshccrui).

## 필요한 폴더 구조 만들기 {#creatingfolderstructure}

사용자 지정 로고 이미지 및 스타일시트를 호스팅하기 위해 아래 설명된 대로 폴더 구조를 만듭니다. 루트 폴더 /apps가 있는 새 폴더 구조는 /libs 폴더의 구조와 유사합니다.

사용자 지정을 위해 /apps 분기에서 아래 설명된 대로 병렬 폴더 구조를 만듭니다.

/apps 분기(폴더 구조):

* 시스템 업데이트가 있을 경우 파일이 안전한지 확인합니다. 업그레이드, 기능 팩 또는 핫픽스의 경우 /libs 분기가 업데이트되고 /libs 분기에서 변경 사항을 호스팅하는 경우 해당 분기가 덮어쓰기됩니다.
* 현재 시스템/분기를 방해하지 않도록 도와줍니다. 사용자 지정 파일을 저장하기 위해 기본 위치를 사용하는 경우 이 위치를 잘못 사용할 수 있습니다.
* AEM에서 리소스를 검색할 때 리소스를 우선 순위로 활용할 수 있습니다. AEM은 /apps 분기를 먼저 검색한 다음 /libs 분기를 사용하여 리소스를 찾도록 구성되어 있습니다. 이 메커니즘은 시스템이 오버레이(및 여기에 정의된 사용자 지정)를 사용함을 의미합니다.

다음 단계에 따라 /apps 분기에서 필요한 폴더 구조를 만드십시오.

1. 관리자로 `https://[server]:[port]/[ContextPath]/crx/de` 이동합니다.
1. 앱 폴더에서 css 폴더(ccrui 폴더에 있음)와 유사한 경로/구조 `css` 로 명명된 폴더를 만듭니다.

   css 폴더를 만드는 단계:

   1. 다음 경로에서 **css** 폴더를 마우스 오른쪽 버튼으로 클릭하고 **Overlay Node를 선택합니다**. `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css`

      ![오버레이 노드](assets/1_overlaynode_css.png)

   1. [오버레이 노드] 대화 상자에 다음 값이 있는지 확인합니다.

      **경로:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css

      **오버레이 위치:** /apps/

      **일치 노드 유형:** 선택

      ![오버레이 노드 경로](assets/0_1_5ioverlaynodedialog.png)

      >[!NOTE]
      >
      >/libs 분기에서 변경하지 마십시오. 이 분기는 다음과 같이 언제든지 변경할 수 있으므로 변경 사항이 손실될 수 있습니다.
      >
      >* 인스턴스 업그레이드
      >* 핫픽스 적용
      >* 기능 팩 설치


   1. **확인**&#x200B;을 클릭합니다. css 폴더가 지정된 경로에 생성됩니다.

1. apps 폴더에서 imgs 폴더(ccrui 폴더에 있음)와 유사한 경로/구조 `imgs` 로 명명된 폴더를 만듭니다.

   1. 다음 경로에서 **imgs** 폴더를 마우스 오른쪽 버튼으로 클릭하고 **Overlay Node를 선택합니다**. `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs`
   1. [오버레이 노드] 대화 상자에 다음 값이 있는지 확인합니다.

      **경로:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs

      **오버레이 위치:** /apps/

      **일치 노드 유형:** 선택

   1. **확인**&#x200B;을 클릭합니다.

      >[!NOTE]
      >
      >/apps 폴더에 폴더 구조를 수동으로 만들 수도 있습니다.

1. 모두 **저장을** 클릭하여 서버에 변경 사항을 저장합니다.

## CRX에 새 로고 업로드 {#uploadlogo}

사용자 정의 로고 파일을 CRX에 업로드합니다. 표준 HTML 규칙은 로고의 렌더링을 제어합니다. 지원되는 이미지 파일 형식은 AEM Forms에 액세스하기 위해 사용 중인 브라우저에 따라 다릅니다. 모든 브라우저는 JPEG, GIF 및 PNG를 지원합니다. 자세한 내용은 지원되는 이미지 포맷에 대한 브라우저 관련 설명서를 참조하십시오.

* 로고 이미지의 기본 크기는 48px &amp;ast;입니다. 48px 이미지가 이 크기와 비슷하거나 48px &amp;ast;보다 큰지 확인합니다. 48px
* 로고 이미지 높이가 50px 이상인 경우, 메시지 작성 사용자 인터페이스는 헤더의 높이로 인해 이미지를 최대 높이 50px로 축소합니다. 이미지 크기를 축소하는 동안 통신 사용자 인터페이스를 만들면 이미지의 종횡비가 유지됩니다.
* 통신 사용자 인터페이스 만들기는 이미지의 크기가 작은 경우 확대되지 않으므로 로고 이미지 높이가 최소 48px이고 폭이 명확해야 합니다.

다음 단계에 따라 사용자 정의 로고 파일을 CRX에 업로드합니다.

1. 이동 `https://[server]:[port]/[contextpath]/crx/de`. 필요한 경우 관리자로 로그인합니다.
1. CRXDE에서 다음 경로의 **imgs** 폴더를 마우스 오른쪽 단추로 클릭하고 **만들기 > 파일 만들기를 선택합니다**.

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs/`

   ![imgs 폴더에 새 노드 만들기](assets/2_contentexplorernewnode.png)

1. 파일 만들기 대화 상자에서 파일 이름을 CustomLogo.png(또는 로고 파일 이름)로 입력합니다.

   ![새 노드로 CustomLogo.png](assets/3_contentexplorernewnode_customlogo.png)

1. 모두 **저장을 클릭합니다**.

   새로 만든 파일(여기 CustomLogo.png)에 jcr:content 속성이 나타납니다.

1. 폴더 구조에서 jcr:content를 클릭합니다.

   jcr:content의 속성이 나타납니다.

   ![jcrcontentproperties](assets/jcrcontentproperties.png)

1. jcr:data **속성을 두 번** 클릭합니다.

   jcr:data 편집 대화 상자가 나타납니다.

   이제 newlogo.png 폴더를 클릭하고 jcr:content(dim option)를 두 번 클릭하고 nt:resource 유형을 설정합니다. 없으면 jcr:content라는 이름의 속성을 만듭니다.

1. jcr:data 편집 대화 상자에서 **찾아보기를** 클릭하고 로고로 사용할 이미지 파일(여기 CustomLogo.png)을 선택합니다.

   지원되는 이미지 파일 형식은 AEM Forms에 액세스하기 위해 사용 중인 브라우저에 따라 다릅니다. 모든 브라우저는 JPEG, GIF 및 PNG를 지원합니다. 자세한 내용은 지원되는 이미지 포맷에 대한 브라우저 관련 설명서를 참조하십시오.

   ![사용자 정의 로고 파일 샘플](assets/geometrixx-outdoors.png)
   **그림:** *예 - 사용자 지정 로고로 사용할 CustomLogo.png*

1. 모두 **저장을 클릭합니다**.

## CSS를 만들어 로고를 UI와 통합 {#createcss}

사용자 지정 로고 이미지에는 컨텐츠 컨텍스트에서 추가 스타일 시트가 로드되어야 합니다.

로고를 렌더링할 스타일 시트를 설정하려면 다음 단계를 따르십시오.

1. 이동 `https://[server]:[port]/[contextpath]/crx/de`. 필요한 경우 관리자로 로그인합니다.
1. 다음 위치에 customcss.css라는 파일을 만듭니다(다른 파일 이름을 사용할 수 없음).

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css/`

   customcss.css 파일을 만드는 단계:

   1. css 폴더를 마우스 오른쪽 **단추로 클릭하고** 만들기 > 파일 **만들기를 선택합니다**.
   1. [새 파일] 대화 상자에서 CSS의 이름을 `customcss.css`(다른 파일 이름을 사용할 수 없음)로 지정하고 [ **확인]을 클릭합니다**.
   1. 새로 만든 css 파일에 다음 코드를 추가합니다. 콘텐트:url의 코드에서 CRXDE의 imgs 폴더에 업로드한 이미지 이름을 지정합니다.

      ```css
      .logo, .logo:after {
      content:url("../imgs/CustomLogo.png");
      }
      ```

   1. 모두 **저장을 클릭합니다**.

## 서신 작성 UI를 새로 고쳐 사용자 지정 로고를 확인합니다. {#refreshccrui}

브라우저 캐시를 지운 다음 브라우저에서 서신 UI 생성 인스턴스를 엽니다. 사용자 정의 로고가 표시됩니다.

![사용자 정의 로고를 사용하여 통신 사용자 인터페이스](assets/0_1_introscreenshot-1.png)를&#x200B;**만듭니다. 그림:** *통신 UI 만들기의 사용자 지정 아이콘*

