---
title: 작업 할당 단계에서 사용자 지정 전자 메일 템플릿 사용
seo-title: 작업 할당 단계에서 사용자 지정 전자 메일 템플릿 사용
description: 'Forms 워크플로우 이메일 알림용 사용자 정의 이메일 템플릿 '
seo-description: 'Forms 워크플로우 이메일 알림용 사용자 정의 이메일 템플릿 '
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
exl-id: 5af73823-2c32-41b3-9ab8-a7ad9fd9532f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 1%

---

# 작업 할당 단계 {#use-custom-email-templates-in-an-assign-task-step}에서 사용자 지정 이메일 템플릿 사용

Forms 워크플로우 이메일 알림용 사용자 정의 이메일 템플릿

작업 할당 단계를 사용하여 작업을 생성하고 사용자 또는 그룹에 지정할 수 있습니다. 작업이 사용자 또는 그룹에 할당되면 정의된 사용자 또는 정의된 그룹의 각 구성원에게 전자 메일 알림이 전송됩니다. 일반적인 전자 메일 알림에는 할당된 작업의 링크와 작업과 관련된 정보가 포함됩니다. 다음 이미지는 이메일 알림 샘플을 표시합니다.

![기본 제공 템플릿으로 이메일 알림](do-not-localize/default-email-template.png)

모양을 사용자 지정하고 이메일 알림에서 사용자 지정 메타데이터를 사용할 수 있습니다. AEM Forms에서는 이메일 알림에 대한 기본 템플릿을 제공합니다. 기본 제공 템플릿을 사용자 지정하거나 처음부터 새 템플릿을 만들 수 있습니다.

전자 메일 알림 템플릿은 [HTML 전자 메일](https://en.wikipedia.org/wiki/HTML_email)을 기반으로 합니다. 이러한 이메일은 다양한 이메일 클라이언트와 화면 크기에 맞게 조정됩니다. 또한 전자 메일의 스타일링은 템플릿 내에 정의됩니다.

다음 이미지에는 사용자 지정된 이메일 알림이 표시됩니다.

![사용자 지정 템플릿을 사용한 이메일 알림](do-not-localize/customized-email.png)

## 기존 템플릿 {#customize-the-existing-template} 사용자 지정

곧바로 사용할 수 있는 AEM Forms에서는 이메일 알림에 대한 템플릿을 제공합니다. 템플릿은 지정된 작업의 제목 설명, 기한, 우선 순위, 워크플로 이름 및 링크를 제공합니다. 템플릿을 사용자 지정하여 모양을 변경할 수 있습니다. 템플릿을 사용자 지정하려면 다음 단계를 수행하십시오.

1. 관리자 계정으로 CRXDE에 로그인합니다.

1. /libs/fd/dashboard/templates/email로 이동합니다.

1. htmlEmailTemplate.txt 파일을 엽니다. 여기에는 기본 템플릿이 포함되어 있습니다.

1. htmlEmailTemplate.txt 파일의 컨텐츠를 사용자 정의 콘텐츠로 바꿉니다.

   전자 메일 알림 템플릿은 [HTML 전자 메일](https://en.wikipedia.org/wiki/HTML_email)입니다. 기존 html 코드를 사용자 지정 코드로 대체하여 템플릿의 모양을 변경할 수 있습니다.

1. 파일을 저장합니다. 이제 사용자 지정된 템플릿을 사용할 준비가 되었습니다.

## 전자 메일 템플릿 {#create-an-email-template} 만들기

곧바로 사용할 수 있는 AEM Forms에서는 이메일 알림에 대한 템플릿을 제공합니다. 템플릿은 지정된 작업의 제목 설명, 기한, 우선 순위, 워크플로 이름 및 링크를 제공합니다. 작업 단계 지정 을 위해 사용자 정의 이메일 템플릿(사용자 고유의 템플릿)을 추가할 수도 있습니다. 사용자 지정 이메일 템플릿을 추가하려면 다음 단계를 수행하십시오.

1. 관리자 계정으로 CRXDE에 로그인합니다.

1. /libs/fd/dashboard/templates/email로 이동합니다.

1. .txt 파일을 만듭니다. 예를 들어 EmailOnTaskAssign.txt가 있습니다.

1. 파일에 사용자 지정 HTML 코드를 추가합니다.

   전자 메일 알림 템플릿은 [HTML 전자 메일](https://en.wikipedia.org/wiki/HTML_email)입니다. 파일에 사용자 지정 HTML 코드를 추가하여 새 템플릿을 만들 수 있습니다.

1. 파일을 저장합니다. 템플릿이 작업 할당 단계에서 사용할 준비가 되었습니다.

## 작업 할당 단계 {#use-an-email-template-in-an-assign-task-step}에서 전자 메일 템플릿을 사용합니다.

기본적으로 할당 작업 단계는 기본 템플릿 htmlEmailTemplate.txt를 사용하도록 구성됩니다. 사용자 지정 템플릿을 사용하도록 선택할 수 있습니다. 템플릿을 변경하려면 다음을 수행하십시오.

1. **[!UICONTROL 작업 할당]** 단계를 엽니다.

1. **[!UICONTROL 할당자 > HTML 이메일 템플릿]**&#x200B;으로 이동합니다.

1. 새로 만든 HTML 이메일 템플릿을 선택합니다.

1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 템플릿이 변경되었습니다.

전자 메일 알림도 [메타데이터](/help/forms/using/use-metadata-in-email-notifications.md)을 사용합니다. 예를 들어 기한, 우선순위, 워크플로우 이름 등이 있습니다. [사용자 지정 메타데이터](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification)를 사용하도록 템플릿을 구성할 수도 있습니다.
