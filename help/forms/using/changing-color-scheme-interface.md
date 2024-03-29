---
title: 인터페이스의 색상 구성표 변경
seo-title: Changing the color scheme of the interface
description: AEM Forms 작업 공간 사용자 인터페이스 부분의 색상 구성표를 선택적으로 수정하는 방법입니다.
seo-description: How to modify the color scheme of AEM Forms workspace user interface portions selectively.
uuid: 32c32f7a-8271-4d2c-8a1f-ad5ab3c90b83
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 18dab82a-badf-4c32-83a2-cd5cb04cae89
exl-id: efbb9a9e-0ddf-49f2-bcb8-14cd0c6de5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---

# 인터페이스의 색상 구성표 변경 {#changing-the-color-scheme-of-the-interface}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

요구 사항에 맞게 AEM Forms 작업 공간 사용자 인터페이스 부분의 색상 구성표를 수정할 수 있습니다. 다음은 대표 색상 구성표 사용자 지정의 몇 가지 예입니다. 이 문서에서 설명한 단계 외에 다음을 참조하십시오 [AEM Forms 작업 공간 사용자 지정을 위한 일반 단계](/help/forms/using/generic-steps-html-workspace-customization.md).

## 위쪽 탐색 모음 {#top-navigation-bar}

### 배경 이미지 사용 {#using-background-image}

AEM Forms 작업 공간 상단의 탐색 모음을 업데이트하려면

1. 색상을 업데이트할 배경 이미지를 만듭니다. 파일의 이름을 newBackground.jpg로 지정합니다.
1. WebDAV 클라이언트를 사용하여 /apps/ws/images 폴더에 배경 이미지 파일을 업로드합니다.

   >[!NOTE]
   >
   >WebDAV 액세스에 대한 자세한 내용은 [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. 다음 스타일을 추가하여 /apps/ws/css/newStyle.css에서 새 배경 이미지를 참조합니다.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### CSS에서 색상 속성 사용 {#using-color-property-in-css}

1. /apps/ws/css의 newStyle.css에 다음 스타일을 추가합니다

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## 카테고리 구성 요소 {#category-component}

카테고리 구성 요소는 왼쪽 패널에 작업의 다양한 카테고리를 표시합니다. 색상을 변경하려면 배경색을 `.category` CSS 파일의 요소.

## 작업 구성 요소 {#task-component}

작업은 중간 패널에 TaskList 구성 요소라고 표시됩니다. 색상을 변경하려면 스타일시트에서 .task 선택기와 연관된 스타일을 수정합니다.
