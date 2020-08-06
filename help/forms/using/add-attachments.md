---
title: 첨부 파일 추가
seo-title: 첨부 파일 추가
description: AEM Forms 앱에서 사진에 스크리블 메모를 주석으로 추가
seo-description: AEM Forms 앱에서 사진에 스크리블 메모를 주석으로 추가
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
translation-type: tm+mt
source-git-commit: 0ce79686522da4fb3d017068b623c76f81c6b23a
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# 첨부 파일 추가 {#adding-attachments}

## AEM Forms 워크플로우 서버와 동기화된 양식에 첨부 파일 추가(JEE의 AEM Forms) {#adding-annotations}

AEM Forms 앱을 사용하면 AEM Forms JEE 서버와 동기화된 양식에 이미지, 낙서 메모 및 텍스트 노트를 첨부할 수 있습니다. 양식을 AEM Forms Workflow 서버에서 불러오면 첨부 파일이 양식에 추가됩니다. 첨부 파일 ![첨부 파일 앱을](assets/attachments-app.png) 탭하면 양식의 모든 첨부 파일을 함께 볼 수 있습니다. 빨간색 알림은 양식의 첨부 파일 수를 지정합니다. 양식에 첨부 파일이 없으면 빨간색 알림 단추를 볼 수 없습니다. 양식에 첨부 파일이 없는 경우 첨부 버튼을 ![누르면 사진](assets/attch.png)또는 낙서를 첨부할 수 있는 옵션이 표시됩니다.

옵션은 다음과 같습니다.

* **[!UICONTROL 갤러리]**: 장치에 저장된 그림에서 사진을 추가할 수 있습니다.

* **[!UICONTROL 카메라]**: 사진을 찍어 양식에 추가할 수 있습니다.

* **[!UICONTROL 참고]**: 스크리블이나 텍스트 노트를 추가할 수 있습니다. 자유 ![를](assets/scribble.png) 사용하여 자유롭게 그리기를 추가하고 ![키보드를](assets/keyboard.png) 사용하여 텍스트 노트를 추가합니다.

>[!NOTE]
>
>한 사용자가 추가한 첨부 파일은 다른 AEM Forms 앱 사용자가 볼 수 있습니다. 다른 사용자는 사용자가 추가한 첨부 파일을 삭제할 수 없습니다.


### 첨부 파일 화면 {#the-attachments-screen}

한 곳에서 모든 첨부 파일을 보려면 ![첨부 파일 앱을 누릅니다](assets/attachments-app.png). 여기에서 첨부 파일을 추가, 이름 변경 및 삭제할 수 있습니다.

![모든 첨부 파일](assets/attachments-screen.png)

첨부 파일 화면에서 **+** 버튼을 사용하여 다른 그림, 문지르기 또는 텍스트를 첨부할 수 있습니다.

### 사진 추가 {#adding-a-photograph}

모바일 장치의 카메라 또는 디바이스에 저장된 사진을 사용하여 양식에 사진을 첨부할 수 있습니다.

1. 창 아래쪽에 있는 ![첨부](assets/attch.png) 단추를 누릅니다.
1. 표시되는 팝업에서 **[!UICONTROL 갤러리]** 또는 **[!UICONTROL 카메라]** 를 누릅니다.
1. 선택한 옵션에 따라 다음을 수행합니다.

   1. 카메라를 **[!UICONTROL 선택하는 경우]**.

      사진 찍어주세요 그런 다음 **[!UICONTROL 사용]** 사진 ![단추를](assets/use-pic.png) 누릅니다.

      또는 [다시 **[!UICONTROL 복구]** ] ![단추를](assets/retake.png) 눌러 사진을 다시 선택합니다.

   1. 갤러리를 **[!UICONTROL 선택하는 경우]**.

      장치의 이미지 브라우저가 나타납니다. 장치의 사진 브라우저에서 첨부할 그림을 누릅니다.

### 메모 추가 {#adding-a-note}

[ **메모** ] 옵션을 사용하면 양식에 자유 글리프 및 텍스트 첨부 파일을 추가할 수 있습니다.

1. 창 아래쪽에 있는 ![첨부](assets/attch.png) 단추를 누릅니다.
1. 나타나는 **[!UICONTROL 팝업에서]** 노트를 누릅니다.
1. 시작한 노트 사용자 인터페이스에서 자유롭게 문지할 수 있습니다.

   ![스크리블 인터페이스](assets/scribble-ui.png)
   **그림:** *낙서*

   자유 인터페이스에서 다음 옵션을 사용할 수 있습니다.

   * **[!UICONTROL 지우기]**: 화면을 지웁니다.
   * **[!UICONTROL 완료]**: 현재 문지판을 붙입니다.
   * **[!UICONTROL 취소]**: 현재 스크리블을 무시하고 스크리블 사용자 인터페이스를 종료합니다.
   * ![키보드](assets/keyboard.png): 스크리블을 지우고 텍스트 노트를 추가할 수 있습니다.

   ![AEM Forms 앱의 키보드 스크리블](assets/keyboard-inapp.png)

## AEM Forms 워크플로우 없이 AEM Forms 서버와 동기화된 양식의 첨부 파일(OSGi의 AEM Forms) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

AEM Forms OSGi 서버와 동기화된 모바일 양식의 첨부 파일은 AEM Forms JEE 서버와 비슷하게 작동합니다.

양식 수준 첨부 파일은 AEM Forms OSGi 서버에서 앱에 로드된 적응형 양식에 대해 지원되지 않습니다. 이미지나 텍스트 노트를 첨부하려면 작성 시 양식의 필드 레벨 첨부 파일을 활성화합니다. 필드의 구성 요소 브라우저에서 파일 첨부 구성 요소를 드래그하여 놓습니다.

적응형 양식의 경우 첨부 파일을 레코드 문서(DoR)로 볼 수 있습니다. XFA [가 아닌 적응형 양식에 대해서는 기록 문서 생성을 참조하십시오](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
