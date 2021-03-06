---
title: AEM Forms 작업 공간에서 양식 작업
seo-title: AEM Forms 작업 공간에서 양식 작업
description: 양식 세트는 그룹화되어 최종 사용자에게 단일 양식 세트로 제공되는 HTML5 양식의 컬렉션입니다. AEM Forms 작업 공간에서 양식 세트를 사용하는 방법을 알아봅니다.
seo-description: 양식 세트는 그룹화되어 최종 사용자에게 단일 양식 세트로 제공되는 HTML5 양식의 컬렉션입니다. AEM Forms 작업 공간에서 양식 세트를 사용하는 방법을 알아봅니다.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
exl-id: 4e39f6dd-b7a3-4c6c-be1f-66b9a5743352
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---

# AEM Forms 작업 공간 {#working-with-formsets-in-aem-forms-workspace}에서 양식 집합 작업

양식 세트는 그룹화되어 최종 사용자에게 단일 양식 세트로 제공되는 HTML5 양식의 컬렉션입니다. 최종 사용자가 양식 세트에 채우기를 시작하면 한 양식에서 다른 양식으로 원활하게 전환됩니다. 한 번의 클릭으로 양식 세트를 제출할 수 있습니다. 양식 세트 및 설정 방법에 대한 자세한 내용은 AEM Forms](/help/forms/using/formset-in-aem-forms.md)의 [양식 세트를 참조하십시오.

AEM Forms 작업 공간에서 양식 세트를 지원합니다. 양식 세트를 사용하면 서비스 또는 프로세스와 관련된 여러 양식을 그룹화하여 비즈니스 프로세스를 자동화하고 최종 사용자에게 제공할 수 있습니다. 이러한 시나리오에서는 사용자가 전체 세트를 하나로 채울 수 있으며 개별 양식이나 프로세스를 파일, 제출 및 추적할 필요가 없습니다.

## AEM Forms 작업 공간 앱 {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}에서 시작점에 양식 세트 첨부

1. Workbench에서 비즈니스 프로세스 워크플로우를 만듭니다. 자세한 내용은 [Workbench 도움말](https://www.adobe.com/go/learn_aemforms_workbench_63)을 참조하십시오.
1. 시작점의 프로세스 속성에서 프레젠테이션 및 데이터에서 **CRX 자산 사용**&#x200B;을 선택합니다.

   ![3-1](assets/1-1.png)

1. CRX 자산 경로 옆에 있는 ![찾아보기](assets/browse.png)(찾아보기)를 클릭합니다. 양식 자산 선택 대화 상자가 나타납니다.

   ![2개](assets/2.png)

1. **양식 세트** 탭을 클릭하고 목록에서 관련 양식 세트를 선택한 다음 **확인**&#x200B;을 클릭합니다.

1. 다른 관련 프로세스 속성을 업데이트한 후 응용 프로그램을 배포합니다.

## AEM Forms 작업 공간에서 양식 세트 사용 {#using-formset-in-nbsp-aem-forms-workspace}

양식 세트가 시작점에 연결되면 다른 시작점이 호출될 때 AEM Forms 작업 공간에서 시작점을 호출할 수 있습니다.

AEM Forms 작업 공간을 통해 양식 세트에서 지원되는 작업은 다음과 같습니다.

* 초안으로 저장
* 잠금
* 중단
* 전송
* 첨부 파일 추가
* 메모 추가
* 뒤로 또는 다음 단추를 사용하여 양식 세트의 양식 간을 이동합니다.

![3-1](assets/3-1.png)

>[!NOTE]
>
>양식 세트의 이전 양식과 다음 양식에서 이동하는 동안 성능 향상을 위해 관련 양식이 완전히 렌더링될 때까지 모든 작업 공간 단추(뒤로, 다음, 저장, 제출 및 ...(자세히))가 비활성화됩니다.
