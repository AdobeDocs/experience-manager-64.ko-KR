---
title: 적응형 양식에서 CAPTCHA 사용
seo-title: 적응형 양식에서 CAPTCHA 사용
description: 적응형 양식에서 AEM CAPTCHA 또는 Google reCAPTCHA 서비스를 구성하는 방법을 알아봅니다.
seo-description: 적응형 양식에서 AEM CAPTCHA 또는 Google reCAPTCHA 서비스를 구성하는 방법을 알아봅니다.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
translation-type: tm+mt
source-git-commit: b9d2a5b65f7ae48a9bde5580b5ddd3e55fc68d61

---


# 적응형 양식에서 CAPTCHA 사용 {#using-captcha-in-adaptive-forms}

CAPTCHA(Computers and Human Apart)는 사람과 자동화된 프로그램 또는 보트를 구별하기 위해 온라인 거래에서 일반적으로 사용되는 프로그램입니다. Adobe Experience Manager는 도전 과제를 해결하고 사용자 응답을 평가하여 사이트와 상호 작용하는 사람 또는 보트 중 어느 것인지 판단합니다. 이는 테스트가 실패할 경우 사용자가 계속할 수 없도록 하고, 봇이 스팸이나 악의적인 용도를 게시하지 못하도록 하여 온라인 거래를 안전하게 할 수 있도록 합니다.

AEM Forms는 적응형 양식의 CAPTCHA를 지원합니다. Google의 reCAPTCHA 서비스를 사용하여 CAPTCHA를 구현할 수 있습니다.

>[!NOTE] {grayBox=&quot;true&quot;}
>
>AEM Forms는 reCaptcha v2만 지원합니다. 다른 버전은 지원되지 않습니다.
>적응형 양식의 CAPTCHA는 AEM Forms 앱의 오프라인 모드에서 지원되지 않습니다.

## Google의 ReCAPTCHA 서비스 구성 {#google-recaptcha}

양식 작성자는 Google의 reCAPTCHA 서비스를 사용하여 적응형 양식에 CAPTCHA를 구현할 수 있습니다. 사이트를 보호하는 고급 CAPTCHA 기능을 제공합니다. reCAPTCHA의 작동 방식에 대한 자세한 내용은 Google reCAPTCHA를 [참조하십시오](https://developers.google.com/recaptcha/).

![apaptcha](assets/recaptcha.png)

AEM Forms에서 reCAPTCHA 서비스를 구현하려면:

1. Google [에서 reCAPTCHA API 키 쌍을](https://www.google.com/recaptcha/admin) 받습니다. 사이트 키와 비밀이 포함되어 있습니다.
1. 클라우드 서비스의 구성 컨테이너를 만듭니다.

   1. 도구 > **[!UICONTROL 일반 > 구성 브라우저로 이동합니다]**.
   1. 클라우드 구성에 대한 글로벌 폴더를 활성화하거나 이 단계를 건너뛰려면 다음을 수행하여 클라우드 서비스 구성에 대한 다른 폴더를 만들고 구성합니다.

      1. 구성 브라우저에서 **[!UICONTROL 전역]** 폴더를 선택하고 속성을 **[!UICONTROL 누릅니다]**.
      1. 구성 속성 대화 상자에서 클라우드 구성을 **[!UICONTROL 활성화합니다]**.
      1. 저장 **[!UICONTROL 및]** 닫기를 눌러 구성을 저장하고 대화 상자를 종료합니다.
   1. 구성 브라우저에서 만들기를 **[!UICONTROL 탭합니다]**.
   1. 구성 만들기 대화 상자에서 폴더의 제목을 지정하고 클라우드 구성을 **[!UICONTROL 활성화합니다]**.
   1. 만들기를 **[!UICONTROL 탭하여]** 클라우드 서비스 구성을 사용할 수 있는 폴더를 만듭니다.


1. reCAPTCHA 파섹

   1. AEM 작성자 인스턴스에서 ![도구](assets/tools.png) > 클라우드 서비스로 **이동합니다**.
   1. reCAPTCHA **[!UICONTROL 를 누릅니다]**. 구성 페이지가 열립니다. 이전 단계에서 만든 구성 컨테이너를 선택하고 만들기를 **[!UICONTROL 누릅니다]**.
   1. reCAPTCHA 서비스의 이름, 사이트 키 및 암호 키를 지정하고 **[!UICONTROL 만들기를]** 눌러 클라우드 서비스 구성을 만듭니다.
   1. 구성 요소 편집 대화 상자에서 1단계에서 얻은 사이트 및 암호 키를 지정합니다. 설정 **[!UICONTROL 저장을]** 누른 다음 **[!UICONTROL 확인을]** 눌러 구성을 완료합니다.
   reCAPTCHA 서비스가 구성되면 적응형 양식에서 사용할 수 있습니다. 자세한 내용은 적응형 [양식에서](#using-captcha)CAPTCHA 사용을 참조하십시오.

## 적응형 양식에서 CAPTCHA 사용 {#using-captcha}

적응형 양식에서 CAPTCHA를 사용하려면

1. 편집 모드에서 응용 양식을 엽니다.

   >[!NOTE]
   >
   >응용 양식을 만들 때 선택한 구성 컨테이너에 reCAPTCHA 클라우드 서비스가 포함되어 있는지 확인합니다. 적응형 양식 속성을 편집하여 양식과 연결된 구성 컨테이너를 변경할 수도 있습니다.

1. 구성 요소 브라우저에서 Captcha **[!UICONTROL 구성 요소를]** 응용 양식으로 드래그하여 놓습니다.

   >[!NOTE]
   >
   >응용 양식에 둘 이상의 Captcha 구성 요소를 사용하는 것은 지원되지 않습니다. 또한 레이지 로딩으로 표시된 패널이나 조각에서 CAPTCHA를 사용하지 않는 것이 좋습니다.

   >[!NOTE]
   >
   >Captcha는 시간 민감하므로 약 1분 후에 만료됩니다. 따라서 적응형 양식의 제출 단추 바로 앞에 Captcha 구성 요소를 배치하는 것이 좋습니다.

1. 추가한 Captcha 구성 요소를 선택하고 ![cmppr](assets/cmppr.png) 을 눌러 해당 속성을 편집합니다.
1. CAPTCHA 위젯의 제목을 지정합니다. The default value is **Captcha**. 제목을 **[!UICONTROL 표시하지 않으려면 제목]** 숨기기를 선택합니다.
1. Captcha **[!UICONTROL 서비스]** 드롭다운에서 reCAPTCHA **[!UICONTROL 서비스를]** Google의 ReCAPTCHA 서비스에 설명된 대로 구성한 경우 [reCAPTCHA 서비스를](#google-recaptcha)활성화하도록 선택합니다. 설정 드롭다운에서 구성을 선택합니다. 또한 reCAPTCHA 위젯의 크기를 **[!UICONTROL 표준]** 또는 **[!UICONTROL 압축]** 크기로 선택합니다.

   >[!NOTE]
   >
   >기본 AEM **[!UICONTROL CAPTCHA]** 서비스가 더 이상 사용되지 않으므로 Captcha 서비스 드롭다운에서 기본값을 선택하지 마십시오.

1. 속성을 저장합니다.

reCAPTCHA 서비스는 적응형 양식에서 활성화됩니다. 양식을 미리 보고 CAPTCHA가 작동하는지 확인할 수 있습니다.
