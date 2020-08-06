---
title: 초안 및 제출 구성 요소
seo-title: 초안 및 제출 구성 요소
description: 초안 및 제출 구성 요소는 초안 상태이며 이미 제출된 양식을 나열합니다. 구성 요소의 모양과 스타일을 사용자 정의할 수 있습니다.
seo-description: 초안 및 제출 구성 요소는 초안 상태이며 이미 제출된 양식을 나열합니다. 구성 요소의 모양과 스타일을 사용자 정의할 수 있습니다.
uuid: 351d6df5-0dc3-4f7a-8bdf-0f1c8dd80f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 219dd379-5bc9-40b0-bdc2-2fb347da29d8
translation-type: tm+mt
source-git-commit: 2abf448e0231eb6fcd9295f498a24e81e1ead11a
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# 초안 및 제출 구성 요소 {#drafts-and-submissions-component}

초안 및 제출 구성 요소는 초안 상태의 모든 양식과 이미 제출된 양식을 나열합니다. 구성 요소에는 초안 및 제출된 양식에 대한 별도의 섹션(탭)이 있습니다. 사용자는 자신의 초안 및 제출된 양식만 볼 수 있습니다.

## 구성 요소 구성 {#configuring-the-component}

초안 및 제출 구성 요소에는 두 개의 탭이 있습니다. 초안 및 제출.

제출 탭에 적응형 양식을 제출하려면 **제출 작업을** Forms 포털 제출 **[동작으로 설정합니다](/help/forms/using/configuring-submit-actions.md).**또는 Forms 포털 제출 옵션을 활성화합니다. 사용자가 양식을 제출할 때마다 양식이 제출 탭에 추가됩니다.

초안 기능은 기본적으로 활성화되어 있습니다. 사용자가 응용 **양식에** 대해 저장을 클릭하면 양식이 초안 탭에 추가됩니다.

초안 및 제출 구성 요소를 추가하고 구성하려면 다음 단계를 수행하십시오.

1. 초안 및 제출 **구성** 요소를 페이지의 구성 요소 브라우저에서 문서 서비스 범주 아래에 드래그합니다.
1. 구성 요소를 누른 다음 ![settings_icon](assets/settings_icon.png) 을 탭하여 구성 요소에 대한 편집 대화 상자를 엽니다.

   ![초안 및 제출 구성 요소](assets/drafts-submissions-edit.png)

1. 편집 대화 상자에서 다음 세부 사항을 지정하고 **완료를** 눌러 설정을 저장합니다.

<table>
 <tbody>
  <tr>
   <th>탭</th>
   <th>구성</th>
   <th>설명</th>
  </tr>
  <tr>
   <td>일반</td>
   <td>총 결과</td>
   <td>표시할 최대 결과 수를 지정합니다. 결과 수가 전체 결과 제한을 늘리면 구성 요소 맨 아래에 <strong>추가 </strong>링크가 나타납니다. 자세히 <strong>를 </strong>클릭하면 모든 양식이 표시됩니다. </td>
  </tr>
  <tr>
   <td> </td>
   <td>스타일 유형</td>
   <td>구성 요소의 스타일을 지정합니다. 양식 목록 <strong>에 스타일</strong>안 <strong></strong>, <strong>기본 스타일</strong> 또는사용자 지정 스타일을지정할 수 있습니다. 사용자 지정 스타일 옵션의 경우 사용자 지정 스타일 경로 <strong>필드 </strong><strong>에서 사용자 지정 CSS 파일의 경로를 지정할 수 있습니다.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>사용자 지정 스타일 경로</td>
   <td>스타일 유형 <strong>필드에서</strong> 사용자 지정 스타일 <strong>옵션을</strong> 선택한 <strong>경우 사용자</strong> 지정 스타일 경로필드를 사용하여 사용자 지정 CSS 파일의 경로를 지정합니다. </td>
  </tr>
  <tr>
   <td> </td>
   <td>표시 옵션</td>
   <td><p>표시할 탭을 지정합니다. 초안 양식, 제출된 양식 또는 둘 다를 표시하도록 선택할 수 있습니다. </p> <p><strong>참고</strong>:<em> [ <strong>표시] 옵션</strong>의 경우 [모두] 이외의 옵션을 <strong>선택하면</strong>기본 탭 <strong>필드</strong> 옵션이 사용되지않습니다.</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>기본 탭</td>
   <td>양식 포털 페이지가 로드될 때 표시할 탭을 지정합니다. 초안 Forms 탭 <strong>과 제출된 Forms 탭</strong> 중에서 선택할 수 <strong>있습니다</strong>.</td>
  </tr>
  <tr>
   <td>초안 Forms 탭 구성</td>
   <td>사용자 지정 제목</td>
   <td>초안 Forms <strong>탭의 제목을</strong> 지정합니다. 기본값은 <strong>초안 Forms입니다.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>레이아웃 템플릿</td>
   <td><p>초안 Forms 목록에 사용할 레이아웃을 지정합니다.</p> <p><strong>참고:</strong> 기본값(더 이상 사용되지 않음) 옵션을 사용하지 마십시오.<br /> </p> </td>
  </tr>
  <tr>
   <td>제출된 Forms 탭 구성</td>
   <td>사용자 지정 제목 </td>
   <td>제출된 Forms <strong>탭의 제목을 </strong>지정합니다. 기본값은 <strong>전송 Forms입니다.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>레이아웃 템플릿</td>
   <td>제출된 Forms<strong> 목록에 사용할 레이아웃을 </strong>지정합니다. </td>
  </tr>
 </tbody>
</table>

## 스토리지 사용자 정의 {#customizing-the-storage}

Forms 포털 제출 작업을 사용하거나 양식 포털에서 데이터 저장 옵션을 적응형 양식으로 활성화하면 양식 데이터가 AEM 저장소에 저장됩니다. 제작 환경에서는 초안 또는 제출된 양식 데이터를 AEM 저장소에 저장하지 않는 것이 좋습니다. 대신 초안 및 제출 구성 요소를 기업 데이터베이스와 같은 보안 스토리지와 통합하여 초안 및 제출된 양식 데이터를 저장해야 합니다.

Forms 포털을 통해 로컬 AEM 저장소, 원격 AEM 저장소 또는 데이터베이스에 데이터를 저장할 수 있습니다. AEM Forms을 사용하면 초안 및 제출용 사용자 데이터 저장 구현을 사용자 정의할 수 있습니다. 기본 방법을 무시하여 초안 및 제출 데이터가 원하는 저장 위치에 저장되는 방식을 지정할 수 있습니다. 예를 들어 조직에서 현재 구현된 데이터 저장소에 데이터를 저장할 수 있습니다.

Forms 포털은 로컬 및 원격 AEM Forms 게시 인스턴스의 crx-repository에 데이터를 저장하는 최신 API(서비스)를 제공합니다. 초안 및 제출 문서에 대한 스토리지 서비스 [구성에 설명된 기본 구현을 기본 기능을 대체할 수](/help/forms/using/configuring-draft-submission-storage.md) 있는 사용자 지정 구현으로 대체할 수 있습니다. 사용자 정의 구현에서 컨텐츠를 안전한 위치에 저장하기 위해 필요한 방법에 대한 자세한 내용은 초안 및 제출 데이터 서비스 [사용자](/help/forms/using/custom-draft-submission-data-services.md) 정의 및 초안 및 제출 구성 [요소에 대한 사용자 정의 스토리지를 참조하십시오.](/help/forms/using/adding-custom-storage-provider-forms.md)

AEM Forms 설명서는 초안 및 제출 구성 [요소를 데이터베이스와 통합하는 샘플을 제공합니다](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/integrate-draft-submission-database.html). 샘플 구현을 사용하여 사용자 지정 구현을 개발할 수 있습니다.

## 관련 문서

* [양식 포털 구성 요소 활성화](/help/forms/using/enabling-forms-portal-components.md)
* [양식 포털 페이지 만들기](/help/forms/using/creating-form-portal-page.md)
* [API를 사용하여 웹 페이지의 양식 목록 작성](/help/forms/using/listing-forms-webpage-using-apis.md)
* [초안 및 제출 구성 요소 사용](/help/forms/using/draft-submission-component.md)
* [초안 및 제출된 양식의 저장 사용자 정의](/help/forms/using/draft-submission-component.md)
* [초안 및 제출 구성 요소를 데이터베이스와 통합하는 샘플](/help/forms/using/integrate-draft-submission-database.md)
* [양식 포털 구성 요소에 대한 템플릿 사용자 정의](/help/forms/using/customizing-templates-forms-portal-components.md)
* [포털에서 양식 게시 소개](/help/forms/using/introduction-publishing-forms.md)
