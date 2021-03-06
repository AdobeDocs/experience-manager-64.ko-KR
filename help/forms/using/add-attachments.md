---
title: 첨부 파일 추가
seo-title: 첨부 파일 추가
description: AEM Forms 앱에서 작업에 사진과 스크리블 메모를 주석으로 추가합니다
seo-description: AEM Forms 앱에서 작업에 사진과 스크리블 메모를 주석으로 추가합니다
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
exl-id: ad1cc63a-cf99-456b-8b83-0605fb3ac6ec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# 첨부 파일 추가 {#adding-attachments}

## AEM Forms 워크플로우 서버(JEE의 AEM Forms)과 동기화된 양식에 첨부 파일 추가 {#adding-annotations}

AEM Forms 앱을 사용하면 AEM Forms JEE 서버와 동기화된 양식에 이미지, 스크리블 메모 및 텍스트 메모를 첨부할 수 있습니다. AEM Forms Workflow 서버에서 양식을 로드하면 첨부 파일이 양식에 추가됩니다. 첨부 파일 단추 ![첨부 파일](assets/attachments-app.png)을 탭하여 양식의 모든 첨부 파일을 함께 볼 수 있습니다. 빨간색 알림은 양식의 첨부 파일 수를 지정합니다. 양식에 첨부 파일이 없으면 빨간색 알림 단추가 표시되지 않습니다. 양식에 첨부 파일이 없는 경우 첨부 파일 단추 ![첨부](assets/attch.png)를 누르면 사진 또는 스크리블을 첨부할 수 있는 옵션이 제공됩니다.

옵션은 다음과 같습니다.

* **[!UICONTROL 갤러리]**:장치에 저장된 그림에서 그림을 추가할 수 있습니다.

* **[!UICONTROL 카메라]**:사진을 찍어 양식에 추가할 수 있습니다.

* **[!UICONTROL 참고]**:스크리블 또는 텍스트 메모를 추가할 수 있습니다. ![스크리블](assets/scribble.png)을 사용하여 스크리블을 추가하고, ![키보드](assets/keyboard.png)를 사용하여 텍스트 메모를 추가합니다.

>[!NOTE]
>
>한 사용자가 추가한 첨부 파일은 다른 AEM Forms 앱 사용자에게 표시됩니다. 다른 사용자는 사용자가 추가한 첨부 파일을 삭제할 수 없습니다.


### 첨부 화면 {#the-attachments-screen}

모든 첨부 파일을 한 위치에 보려면 ![attachments-app](assets/attachments-app.png)을(를) 누릅니다. 여기에서 첨부 파일을 추가, 이름 변경 및 삭제할 수 있습니다.

![모든 첨부 파일 위치](assets/attachments-screen.png)

첨부 화면에서 **+** 단추를 사용하여 다른 그림, 스크리블 또는 텍스트를 첨부할 수 있습니다.

### 사진 추가 {#adding-a-photograph}

모바일 장치의 카메라 또는 장치에 저장된 사진을 사용하여 양식에 사진을 첨부할 수 있습니다.

1. 창 하단에 있는 첨부 파일 단추 ![첨부](assets/attch.png)를 누릅니다.
1. 표시되는 팝업에서 **[!UICONTROL Gallery]** 또는 **[!UICONTROL Camera]**&#x200B;를 누릅니다.
1. 선택한 옵션에 따라 다음을 수행합니다.

   1. **[!UICONTROL 카메라]**&#x200B;를 선택하는 경우.

      사진을 찍으세요. 그런 다음 **[!UICONTROL Use]** ![use-pic](assets/use-pic.png) 단추를 누릅니다.

      또는 **[!UICONTROL Retake]** ![Retake](assets/retake.png) 단추를 눌러 사진을 다시 가져옵니다.

   1. **[!UICONTROL Gallery]**&#x200B;를 선택하는 경우.

      장치의 이미지 브라우저가 나타납니다. 장치의 그림 브라우저에서 첨부할 그림을 누릅니다.

### 참고 {#adding-a-note} 추가

**메모** 옵션을 사용하면 자유 작성 스크리블 및 텍스트 첨부 파일을 양식에 추가할 수 있습니다.

1. 창 하단에 있는 첨부 파일 단추 ![첨부](assets/attch.png)를 누릅니다.
1. 표시되는 팝업에서 **[!UICONTROL Notes]**&#x200B;를 누릅니다.
1. 시작한 Notes 사용자 인터페이스에서 자유롭게 스크리블할 수 있습니다.

   ![스크리블 인터페이스](assets/scribble-ui.png)
   **그림:** *스크리블*

   스크리블 인터페이스에서 다음 옵션을 사용할 수 있습니다.

   * **[!UICONTROL 지우기]**:화면을 지웁니다.
   * **[!UICONTROL 완료]**:현재 스크리블을 첨부합니다.
   * **[!UICONTROL 취소]**:현재 스크리블을 삭제하고 스크리블 사용자 인터페이스를 종료합니다.
   * ![키보드](assets/keyboard.png):스크리블을 지우고 텍스트 메모를 추가할 수 있도록 합니다.

   ![AEM Forms 앱의 키보드 스크리블](assets/keyboard-inapp.png)

## AEM Forms 워크플로우 없이 AEM Forms 서버와 동기화된 양식의 첨부 파일(OSGi의 AEM Forms) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

AEM Forms OSGi 서버와 동기화된 모바일 양식에 대한 첨부 파일은 AEM Forms JEE 서버와 유사하게 작동합니다.

AEM Forms OSGi 서버에서 앱에 로드되는 적응형 양식에 양식 수준 첨부 파일은 지원되지 않습니다. 이미지나 텍스트 메모를 첨부하려면 작성 시 양식의 필드 수준 첨부 파일을 활성화합니다. 필드의 구성 요소 브라우저에서 첨부 파일 구성 요소를 드래그하여 놓습니다.

적응형 양식의 경우 레코드 문서(DoR)에서 첨부된 파일을 볼 수 있습니다. XFA가 아닌 적응형 양식에 대해서는 [기록 문서 생성](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)을 참조하십시오.
