---
title: 대화형 통신 구성 속성
seo-title: 대화형 통신 구성 속성
description: Interactive Communications의 기본 구성 속성 편집
seo-description: Interactive Communications의 기본 구성 속성 편집
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: 대화형 통신
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 6%

---

# 대화형 통신 구성 속성 {#interactive-communications-configuration-properties}

Interactive Communications의 기본 구성 속성 편집

대화형 통신에는 [AEM Forms 추가 기능](/help/forms/using/installing-configuring-aem-forms-osgi.md) 패키지를 설치한 후 자동으로 구성된 속성이 포함됩니다. Interactive Communication 작성자는 **Adobe Experience Manager Web Console 구성** 페이지를 사용하여 이러한 기본 구성 속성을 편집할 수 있습니다.

다음 URL을 사용하여 **Adobe Experience Manager 웹 콘솔 구성** 페이지를 엽니다.

https://&lt;server>:&lt;port>/&lt;contextPath>/system/console/configMgr

구성 속성은 다음과 같습니다.

* [문서 조각 구성](#document-fragments-configuration)
* [서신 구성 만들기](#create-correspondence-configuration)
* [적응형 양식 및 대화형 통신 웹 채널 구성](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [적응형 양식 및 대화형 통신 웹 채널 테마 구성](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## 문서 조각 구성 {#document-fragments-configuration}

**Adobe Experience Manager 웹 콘솔 구성** 페이지에서 **문서 조각 구성**&#x200B;을 탭하여 문서 조각에 대한 구성 속성을 확인합니다.

<table> 
 <tbody> 
  <tr> 
   <td>속성</td> 
   <td>설명</td> 
   <td>기본값</td> 
   <td>허용되는 값</td> 
  </tr> 
  <tr> 
   <td>데이터 표시 형식</td> 
   <td>인쇄 및 웹 채널을 위한 대화형 커뮤니케이션을 만드는 동안 사용할 수 있는 필드, 변수 및 양식 데이터 모델 요소에 대한 로케일 별 표시 형식입니다.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR 및 ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>들여쓰기</td> 
   <td>목록 문서 조각의 텍스트에 적용된 단일 들여쓰기 단위의 폭입니다.</td> 
   <td>12.7밀리미터</td> 
   <td>번호</td> 
  </tr> 
  <tr> 
   <td>최소 너비 로마자 숫자</td> 
   <td>목록 문서 조각에서 로마자 숫자를 사용하는 경우 글머리 기호 또는 번호 필드에 적용할 최소 너비입니다. </td> 
   <td>12.7밀리미터</td> 
   <td>번호</td> 
  </tr> 
  <tr> 
   <td>최소 너비 수</td> 
   <td>목록 문서 조각에서 로마자 숫자와 별도로 번호 목록을 사용할 때 글머리 기호 또는 번호 필드에 적용할 최소 너비입니다.</td> 
   <td>8.0밀리미터</td> 
   <td>번호</td> 
  </tr> 
 </tbody> 
</table>

## 서신 구성 만들기 {#create-correspondence-configuration}

**Adobe Experience Manager Web Console 구성** 페이지에서 **서신 구성 만들기**&#x200B;를 탭하여 에이전트 UI에 대한 구성 속성을 확인합니다.

| 속성 | 설명 | 기본값 | 허용되는 값 |
|---|---|---|---|
| 편집할 해결된 컨텐츠 표시 | 에이전트 UI에서 텍스트 모듈을 편집하는 동안 해결된 컨텐츠(자리 표시자 대신 실제 값)를 표시하려면 확인란을 선택합니다. | 선택하지 않음 | 해당 사항 없음 |
| 미리 보기 중에 워터마크 적용 | 미리 보기 모드에서 대화형 통신 인쇄 채널에 워터마크를 적용하려면 확인란을 선택합니다. | 선택하지 않음 | 해당 사항 없음 |

## 적응형 양식 및 대화형 통신 웹 채널 구성 {#adaptive-form-and-interactive-communication-web-channel-configuration}

**Adobe Experience Manager 웹 콘솔 구성** 페이지에서 **적응형 양식 및 대화형 통신 웹 채널 구성**&#x200B;을 탭하여 적응형 Forms 및 대화형 통신 웹 채널에 대한 구성 속성을 봅니다. 다음 표에서는 Interactive Communications와 관련된 속성을 설명합니다.

| 속성 | 설명 | 기본값 | 허용되는 값 |
|---|---|---|---|
| 자리 표시자 표시 | 적응형 양식 및 대화형 커뮤니케이션에 포함된 필드의 자리 표시자를 표시할 수 있도록 하려면 확인란을 선택합니다. | 선택 항목 | 해당 사항 없음 |
| 최대 캐시 항목 수 | 캐시 메모리를 사용하여 검색할 수 있는 최대 적응형 양식 및 대화형 커뮤니케이션 수를 설정합니다. | 100 | 번호 |
| 파일 이름을 고유하게 만들기 | 적응형 Forms 및 대화형 커뮤니케이션에서 첨부 파일로 포함된 파일의 고유한 이름을 갖도록 확인란을 선택합니다. | 선택하지 않음 | 해당 사항 없음 |

## 적응형 양식 및 대화형 통신 웹 채널 테마 구성 {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

**Adobe Experience Manager 웹 콘솔 구성** 페이지에서 **적응형 양식 및 대화형 통신 웹 채널 테마 구성**&#x200B;을 탭하여 적응형 Forms 및 대화형 통신 웹 채널 테마에 대한 구성 속성을 봅니다.

<table> 
 <tbody> 
  <tr> 
   <td>속성</td> 
   <td>설명</td> 
   <td>기본값</td> 
   <td>허용되는 값</td> 
  </tr> 
  <tr> 
   <td>글꼴 목록 이름</td> 
   <td>응용 Forms 및 대화형 커뮤니케이션을 만드는 동안 사용할 수 있는 글꼴 목록입니다.</td> 
   <td><p>조지아</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>영향</p> <p>Palatino Linotype</p> </td> 
   <td>모든 유효한 Adobe 서버 글꼴</td> 
  </tr> 
 </tbody> 
</table>
