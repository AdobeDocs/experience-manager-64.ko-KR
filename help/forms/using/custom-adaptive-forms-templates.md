---
title: 사용자 지정 적응형 양식 템플릿 만들기
seo-title: Creating a custom adaptive form template
description: 이 문서에서는 사용자 정의 적응형 양식 템플릿을 만드는 방법을 설명합니다.
seo-description: This article describes how to create custom adaptive form templates.
uuid: 8f8c770f-984c-48e8-978c-7cdfcd1af95b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: c6115b64-e06f-4b5e-b7f9-876553c7627f
exl-id: 83f978ca-d451-4d27-820f-3620331285cf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 1%

---

# 사용자 지정 적응형 양식 템플릿 만들기 {#creating-a-custom-adaptive-form-template}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 사전 요구 사항 {#prerequisites}

* AEM 이해 [페이지 템플릿](/help/sites-authoring/templates.md) 및 [적응형 양식 작성](https://helpx.adobe.com/aem-forms/6-1/introduction-forms-authoring.html)

* AEM 이해 [클라이언트 측 라이브러리](/help/sites-developing/clientlibs.md)

## 적응형 양식 템플릿 {#adaptive-form-template}

적응형 양식 템플릿은 적응형 양식을 만드는 데 사용되는 특정 속성 및 컨텐츠 구조를 가진 전문 AEM 페이지 템플릿입니다. 템플릿에는 사전 구성된 레이아웃, 스타일 및 기본 초기 컨텐츠 구조가 있습니다.

양식을 만들면 원래 템플릿 콘텐츠 구조에 대한 변경 내용이 양식에 반영되지 않습니다.

## 기본 적응형 양식 템플릿 {#default-adaptive-form-templates}

AEM QuickStart는 다음과 같은 적응형 양식 템플릿을 제공합니다.

* 기본: 임의의 순서로 탭을 방문할 수 있는 왼쪽 탭 레이아웃을 사용하여 다중 탭 적응형 양식을 만들 수 있습니다.
* Acrobat Sign을 사용하는 기본 기능: 탭과 마법사가 여러 개인 양식을 만들 수 있습니다. 탭-왼쪽 레이아웃을 사용하여 원하는 순서로 탭을 방문할 수 있습니다. 서명 및 확인에 Adobe Document Cloud 디자인 서비스를 사용합니다.
* 빈 템플릿: 머리글, 바닥글 및 초기 컨텐츠 없이 양식을 만들 수 있습니다. 텍스트 상자, 단추 및 이미지와 같은 구성 요소를 추가할 수 있습니다. 빈 템플릿을 사용하면 양식을 만들 수 있습니다 [AEM 사이트 페이지에 포함](/help/forms/using/embed-adaptive-form-aem-sites.md).

이러한 템플릿에는 `sling:resourceType` 해당 페이지 구성 요소로 설정된 속성입니다. 페이지 구성 요소는 적응형 양식 컨테이너를 포함하는 CQ 페이지를 렌더링하여 적응형 양식을 렌더링합니다.

다음 표는 템플릿과 페이지 구성 요소 간의 연결을 열거합니다.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>템플릿</strong></p> </td> 
   <td><p><strong>페이지 구성 요소</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/surveyTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/survey</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/simpleRegulationTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/base</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/tabRegulationTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/tabbedenrolment</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/afaddon/templates/advancedRegulationTemplate</p> </td> 
   <td><p>/libs/fd/afaddon/components/page/advanced/renderment</p> </td> 
  </tr> 
 </tbody> 
</table>

## 템플릿 편집기를 사용하여 적응형 양식 템플릿 만들기 {#creating-an-adaptive-form-template-using-template-editor}

템플릿 편집기를 사용하여 적응형 양식의 구조 및 초기 컨텐츠를 지정할 수 있습니다. 예를 들어, 모든 양식 작성자가 등록 양식에 텍스트 상자, 탐색 단추 및 제출 단추가 거의 없는 경우를 예로 들 수 있습니다. 작성자가 다른 등록 양식과 일치하는 양식을 만드는 데 사용할 수 있는 템플릿을 만들 수 있습니다. AEM 템플릿 편집기를 사용하면 다음 작업을 수행할 수 있습니다.

* 양식의 머리글 및 바닥글 구성 요소를 구조 레이어에 추가합니다
* 양식의 초기 컨텐츠를 제공합니다.
* 테마를 지정합니다.
* 제출, 재설정 및 탐색과 같은 작업을 지정합니다.

자세한 내용은 [템플릿 편집기](/help/forms/using/template-editor.md).

## CRXDE에서 적응형 양식 템플릿 만들기 {#creating-an-adaptive-form-template-from-crxde}

사용 가능한 템플릿을 사용하는 대신 템플릿을 만들어 적응형 양식을 만들 수 있습니다. 사용자 지정 템플릿은 적응형 양식 컨테이너 및 머리글 및 바닥글 등 페이지 요소를 참조하는 다양한 페이지 구성 요소를 기반으로 합니다.

웹 사이트의 기본 페이지 구성 요소를 사용하여 이러한 구성 요소를 만들 수 있습니다. 또는 기본 템플릿에서 사용하는 적응형 양식의 페이지 구성 요소를 확장할 수 있습니다.

다음 단계를 수행하여 simpleRegistrationTemplate과 같은 사용자 지정 템플릿을 만듭니다.

1. 작성 인스턴스의 CRXDE Lite으로 이동합니다.

1. /apps 디렉토리에서 애플리케이션의 폴더 구조를 만듭니다. 예를 들어 애플리케이션 이름이 mycompany인 경우 이 이름으로 폴더를 만듭니다. 일반적으로 응용 프로그램 폴더에는 구성 요소, 구성, 템플릿, src 및 설치 디렉토리가 있습니다. 이 예에서는 구성 요소, 구성 및 템플릿 폴더를 만듭니다.

1. /libs/fd/af/templates 폴더로 이동합니다.
1. 를 복사합니다. `simpleEnrollmentTemplate` 노드 아래에 있어야 합니다.
1. /apps/mycompany/templates 폴더로 이동합니다. 마우스 오른쪽 단추를 클릭하고 을 선택합니다 **[!UICONTROL 붙여넣기]**.
1. 필요한 경우 복사한 템플릿 노드의 이름을 변경합니다. 예를 들어 등록 템플릿으로 이름을 변경합니다.

1. /apps/mycompany/templates/regulation-template 위치로 이동합니다.

1. 수정 `jcr:title` 및 `jcr:description` 속성 `jcr:content` 노드 를 사용하여 복사한 템플릿과 템플릿을 구별합니다.

1. 다음 `jcr:content` 수정된 템플릿의 노드는 다음을 포함합니다 `guideContainer` 및 `guideformtitle` 구성 요소. `guideContainer` 적응형 양식을 포함하는 컨테이너입니다. 다음 `guideformtitle` 구성 요소는 응용 프로그램 이름, 설명 등을 표시합니다.

   대신 `guideformtitle`, 사용자 지정 구성 요소 또는 `parsys` 구성 요소. 예: 제거 `guideformtitle`, 사용자 지정 구성 요소 또는 `parsys` 구성 요소 노드입니다. 다음을 확인합니다. `sling:resourceType` 구성 요소의 속성은 구성 요소를 참조하며 페이지에 정의되어 있습니다 `component.jsp` 파일.

1. /apps/mycompany/templates/regulation-template/jcr:content 위치로 이동합니다.

1. 를 엽니다. **[!UICONTROL 속성]** 탭하고 값 변경 `cq:designPath` /etc/designs/mycompany에 대한 속성입니다.

1. 이제 다음을 위해 /etc/designs/mycompany 노드를 만듭니다. `cq:Page` 유형.

## 적응형 양식 페이지 구성 요소 만들기 {#create-an-adaptive-form-page-component}

사용자 지정 템플릿은 페이지 구성 요소 /libs/fd/af/components/page/base를 참조하므로 기본 템플릿과 동일한 스타일이 있습니다. 구성 요소 참조를 속성으로 찾을 수 있습니다 `sling:resourceType` /apps/mycompany/templates/regulation-template/jcr:content 노드에 정의됩니다. 기본 는 핵심 제품 구성 요소이므로 이 구성 요소를 수정하지 마십시오.

1. /apps/mycompany/templates/regulation-template/jcr:content 노드로 이동하고 속성 값을 수정합니다 `sling:resourceType` /apps/mycompany/components/page/enrolentpage
1. /libs/fd/af/components/page/base 노드를 /apps/mycompany/components/page 폴더에 복사합니다.

1. 복사된 구성 요소의 이름을 다음으로 변경합니다. `enrollmentpage`.

1. **(이미 콘텐츠 페이지가 있는 경우에만)** 기존 가 있는 경우 다음 단계(a-d)를 수행합니다 `contentpage`구성 요소를 사용하여 웹 사이트에 액세스할 수 있습니다. 기존 항목이 없는 경우 `contentpage`웹 사이트의 구성 요소를 만들려면 `resourceSuperType`OOTB 기본 페이지를 가리키는 속성입니다.

   1. 대상 `enrollmentpage` node, 속성 값 설정 `sling:resourceSuperType` 회사/구성 요소/페이지/콘텐츠 페이지로 이동합니다. 다음 `contentpage` 구성 요소는 사이트의 기본 페이지 구성 요소입니다. 다른 페이지 구성 요소가 확장할 수 있습니다. 아래의 스크립트 파일 제거 `enrollmentpage`, 제외 `head.jsp`, `content.jsp`, 및 `library.jsp`. 다음 `sling:resourceSuperType` 구성 요소: `contentpage` 이 경우 에는 이러한 스크립트가 모두 포함됩니다. 탐색 막대형 및 바닥글을 포함한 머리글은 `contentpage` 구성 요소.

   1. 파일을 엽니다. `head.jsp`.

      JSP 파일에 줄이 포함되어 있습니다 `<cq.include script="library.jsp"/>`.

      다음 `library.jsp` 파일에 가 있습니다. `guide.theme.simpleEnrollment` 적응형 양식의 스타일이 포함된 클라이언트 라이브러리입니다.

      페이지 구성 요소 `enrollmentpage` 는 독점 `head.jsp` 재정의하는 파일 `head.jsp` 파일의 `contentpage` 구성 요소.

   1. 에 모든 스크립트 포함 `head.jsp` 파일 `contentpage` 구성 요소를 `head.jsp` 파일 `enrollmentpage` 구성 요소.
   1. 에서 `content.jsp` 스크립트를 사용하면, 페이지가 렌더링될 때 포함된 다른 구성 요소에 대한 추가적인 페이지 컨텐츠 또는 참조를 추가할 수 있습니다. 예를 들어 사용자 지정 구성 요소를 추가하는 경우 `applicationformheader`JSP 파일의 구성 요소에 다음 참조를 추가해야 합니다.

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      마찬가지로, `parsys` 구성 요소를 포함할 수도 있습니다.

## 적응형 양식 클라이언트 라이브러리 만들기 {#creating-an-adaptive-form-client-library}

다음 `head.jsp` 파일의 `enrollmentpage` 새 템플릿의 구성 요소에 클라이언트 라이브러리가 포함되어 있습니다 `guide.theme.simpleEnrollment`. 기본 템플릿은 이 클라이언트 라이브러리도 사용합니다. 다음 방법 중 하나를 사용하여 새 템플릿의 스타일을 변경합니다.

* 사용자 지정 테마를 정의하고 기본 테마를 바꿉니다 `guide.theme.simpleEnrollment` 사용자 지정 테마 사용.
* /etc/designs/mycompany에서 새 클라이언트 라이브러리를 정의합니다. jsp 페이지의 기본 테마 항목 뒤에 클라이언트 라이브러리를 포함합니다. 이 클라이언트 라이브러리에 재정의된 모든 스타일과 추가 Java Script 파일을 포함하십시오.

>[!NOTE]
>
>테마는 적응형 양식을 렌더링하는 데 사용되는 페이지 구성 요소에 포함된 클라이언트 라이브러리를 나타냅니다. 클라이언트 라이브러리는 주로 적응형 양식의 모양을 제어합니다.
