---
title: 프로젝트 워크플로를 사용하여 작업
seo-title: Working with Project Workflows
description: 다양한 프로젝트 워크플로를 즉시 사용할 수 있습니다.
seo-description: A variety of project workflows are available out of the box.
uuid: 376922ca-e09e-4ac8-88c8-23dac2b49dbe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: projects
content-type: reference
discoiquuid: 9d2bf30c-5190-4924-82cd-bcdfde24eb39
exl-id: 9d7e9d46-9f38-44a0-9c83-4bc4fceb17c8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 46%

---

# 프로젝트 워크플로를 사용하여 작업{#working-with-project-workflows}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

즉시 사용 가능한 프로젝트 워크플로는 다음과 같습니다.

* **프로젝트 승인 워크플로** - 이 워크플로를 사용하면 사용자에게 콘텐츠를 할당하고, 검토한 다음 승인할 수 있습니다.
* **론치 요청** - 론치를 요청하는 워크플로입니다.
* **랜딩 페이지 요청** - 이 워크플로는 랜딩 페이지를 요청합니다.
* **요청 이메일** - 이메일을 요청하는 워크플로입니다.
* **제품 사진 촬영 및 제품 사진 촬영(커머스)** - 자산과 제품 매핑
* **DAM 언어 사본 작성 및 번역과 DAM 언어 사본 작성** - 에셋 및 폴더에 대한 번역된 바이너리, 메타데이터 및 태그를 생성합니다.

선택하는 프로젝트 템플릿에 따라 사용 가능한 워크플로가 달라집니다.

|  | **간단한 프로젝트** | **미디어 프로젝트** | **제품 사진 촬영 프로젝트** | **번역 프로젝트** |
|---|:-:|:-:|:-:|:-:|
| 복사 요청 |  | x |  |  |
| 제품 사진 촬영 |  | x | x |  |
| 제품 사진 촬영(커머스) |  |  | x |  |
| 프로젝트 승인 | x |  |  |  |
| 론치 요청 | x |  |  |  |
| 랜딩 페이지 요청 | x |  |  |  |
| 이메일 요청 | x |  |  |  |
| DAM 언어 사본 만들기 |  |  |  | x |
| DAM 언어 사본 만들기 및 번역 |  |  |  | x |

>[!NOTE]
>
>&amp;ast; 이들 워크플로는 프로젝트의 **워크플로** 타일에서 시작되지 않습니다. [에셋용 언어 사본 만들기](/help/sites-administering/tc-manage.md)를 참조하십시오.

워크플로 시작 및 완료 단계는 선택하는 워크플로와 상관없이 동일합니다. 단계만 변경됩니다.

[프로젝트]에서 바로 워크플로를 시작합니다([DAM 언어 사본 작성]이나 [DAM 언어 사본 작성 및 번역] 제외). 프로젝트에서 아직 처리되지 않은 작업에 대한 정보는 **작업** 타일. 완료해야 하는 작업에 대한 알림이 사용자 아이콘 옆에 표시됩니다.

AEM에서 워크플로우 작업에 대한 자세한 내용은 다음을 참조하십시오.

* [워크플로에 참여](/help/sites-authoring/workflows-participating.md)
* [페이지에 워크플로 적용](/help/sites-authoring/workflows-applying.md)
* [워크플로 구성](/help/sites-administering/workflows.md)

이 섹션에서는 프로젝트에 사용할 수 있는 워크플로에 대해 설명합니다.

## 복사 요청 워크플로우 {#request-copy-workflow}

이 워크플로우에서는 사용자의 원고를 요청한 다음 승인할 수 있습니다. 요청 복사 워크플로우를 시작하려면 다음을 수행하십시오.

1. In your Media project, select the **+** sign in the **Workflows** tile and select **Request Copy Workflow**.
1. 원고 제목과 요청하는 내용에 대한 간단한 요약을 입력합니다. 해당되는 경우 대상 단어 수, 작업 우선순위 및 기한을 입력하십시오.

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로가 시작됩니다. 작업이 **작업** 타일.

   ![chlimage_1-322](assets/chlimage_1-322.png)

## 제품 사진 촬영 워크플로우 {#product-photo-shoot-workflow}

제품 사진 촬영 워크플로우(상거래 및 상거래 제외)는 [크리에이티브 프로젝트](/help/sites-authoring/managing-product-information.md).

## 프로젝트 승인 워크플로 {#project-approval-workflow}

프로젝트 승인 워크플로에서는 사용자에게 콘텐츠를 지정하고 검토한 다음 콘텐츠를 승인합니다.

1. 단순 프로젝트에서 다음을 ****+** 로그인 **워크플로우** 타일을 선택하고 **프로젝트 승인 작업 과정**.
1. 제목을 입력하고 팀 목록에서 지정할 사용자를 선택합니다. 해당하는 경우 설명, 콘텐츠 경로, 작업 우선순위 및 기한을 입력하십시오.

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로가 시작됩니다. 작업이 **작업** 타일.

   ![chlimage_1-324](assets/chlimage_1-324.png)

## 론치 요청 워크플로 {#request-launch-workflow}

이 워크플로에서는 론치를 요청할 수 있습니다.

1. 간단한 프로젝트에서 **워크플로** 타일의 **+** 기호를 선택한 다음 **론치 요청 워크플로**&#x200B;를 선택합니다.
1. 론치의 제목을 입력하고 론치 소스 경로를 제공합니다. 해당하는 경우 설명 및 라이브 날짜를 추가할 수도 있습니다. 론치가 동작하는 방식에 따라 소스 페이지의 라이브 데이터 상속 또는 하위 페이지 제외 를 선택합니다.

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로가 시작됩니다. 워크플로는 **워크플로** 목록에 표시됩니다(**워크플로** 타일의 생략 부호(**...**)를 클릭하여 목록에 액세스).

## 랜딩 페이지 요청 워크플로우 {#request-landing-page-workflow}

이 워크플로우에서는 랜딩 페이지를 요청할 수 있습니다.

1. 단순 프로젝트에서 **+** 로그인 **워크플로우** 타일링하고 랜딩 페이지 요청 워크플로우를 선택합니다.
1. 랜딩 페이지의 제목과 상위 경로를 입력합니다. 해당하는 경우 실시간 날짜를 입력하거나 랜딩 페이지의 파일을 선택합니다.

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로가 시작됩니다. 작업이 **작업** 타일.

## 이메일 요청 워크플로우 {#request-email-workflow}

이 워크플로우를 통해 이메일을 요청할 수 있습니다. 에 표시되는 워크플로우와 동일합니다 **이메일** 타일.

1. 미디어 또는 단순 프로젝트에서 **+** 로그인 **워크플로우** 타일을 선택하고 **이메일 요청 워크플로우**.
1. 캠페인 및 템플릿 경로와 함께 이메일 제목을 입력합니다. 또한 이름, 설명 및 라이브 날짜를 제공할 수 있습니다.

   ![chlimage_1-327](assets/chlimage_1-327.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로가 시작됩니다. 작업이 **작업** 타일.

   ![chlimage_1-328](assets/chlimage_1-328.png)

## 에셋용 언어 복사 워크플로 생성(및 번역) {#create-and-translate-language-copy-workflow-for-assets}

다음 **언어 사본 만들기** 그리고 **언어 사본 작성 및 번역** 워크플로우는 [자산에 대한 언어 사본 만들기.](/help/assets/translation-projects.md)
