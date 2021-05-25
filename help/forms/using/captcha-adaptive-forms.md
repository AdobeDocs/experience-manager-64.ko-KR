---
title: 적응형 양식에서 CAPTCHA 사용
seo-title: 적응형 양식에서 CAPTCHA 사용
description: 적응형 양식으로 AEM CAPTCHA 또는 Google reCAPTCHA 서비스를 구성하는 방법을 알아봅니다.
seo-description: 적응형 양식으로 AEM CAPTCHA 또는 Google reCAPTCHA 서비스를 구성하는 방법을 알아봅니다.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: 적응형 양식
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# 적응형 양식에서 CAPTCHA 사용 {#using-captcha-in-adaptive-forms}

CAPTCHA(컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공공 튜링 테스트)는 사람과 자동화된 프로그램 또는 보트를 구별하기 위해 온라인 트랜잭션에 자주 사용되는 프로그램입니다. 과제를 안고 사용자 응답을 평가하여 그것이 사람인지 아니면 사이트와 상호 작용하는 봇인지를 결정합니다. 따라서 테스트가 실패하면 사용자가 진행할 수 없고, 봇이 스팸 또는 악의적인 목적을 게시하지 못하도록 하여 온라인 거래를 안전하게 할 수 있습니다.

AEM Forms은 적응형 양식에서 CAPTCHA를 지원합니다. Google의 reCAPTCHA 서비스를 사용하여 CAPTCHA를 구현할 수 있습니다.

>[!NOTE]
>
>AEM Forms은 reCaptcha v2만 지원합니다. 다른 버전은 지원되지 않습니다.
>
>적응형 양식의 CAPTCHA는 AEM Forms 앱의 오프라인 모드에서 지원되지 않습니다.

## Google에서 ReCAPTCHA 서비스 구성 {#google-recaptcha}

양식 작성자는 Google의 reCAPTCHA 서비스를 사용하여 적응형 양식에 CAPTCHA를 구현할 수 있습니다. 사이트를 보호하기 위한 고급 CAPTCHA 기능을 제공합니다. reCAPTCHA 작동 방식에 대한 자세한 내용은 [Google reCAPTCHA](https://developers.google.com/recaptcha/) 를 참조하십시오.

![recaptcha](assets/recaptcha.png)

AEM Forms에서 reCAPTCHA 서비스를 구현하려면 다음을 수행하십시오.

1. Google에서 [reCAPTCHA API 키 쌍](https://www.google.com/recaptcha/admin)을 얻습니다. 사이트 키와 암호가 포함되어 있습니다.
1. 클라우드 서비스용 구성 컨테이너를 만듭니다.

   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
      * 자세한 내용은 [구성 브라우저 설명서](/help/sites-administering/configurations.md)를 참조하십시오.
   1. 클라우드 구성에 대한 글로벌 폴더를 활성화하려면 다음을 수행하십시오. 또는 이 단계를 건너뛰고 클라우드 서비스 구성에 대한 다른 폴더를 만들고 구성하려면 다음을 수행하십시오.

      1. 구성 브라우저에서 **[!UICONTROL 전역]** 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 누릅니다.
      1. 구성 속성 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 활성화합니다.
      1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 눌러 구성을 저장하고 대화 상자를 종료합니다.
   1. 구성 브라우저에서 **[!UICONTROL 만들기]**&#x200B;를 누릅니다.
   1. 구성 만들기 대화 상자에서 폴더의 제목을 지정하고 **[!UICONTROL 클라우드 구성]**&#x200B;을 활성화합니다.
   1. 클라우드 서비스 구성에 대해 활성화된 폴더를 만들려면 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.


1. reCAPTCHA에 대한 클라우드 서비스를 구성합니다.

   1. AEM 작성자 인스턴스에서 ![도구](assets/tools.png) > **Cloud Services**&#x200B;로 이동합니다.
   1. **[!UICONTROL reCAPTCHA]**&#x200B;를 누릅니다. 구성 페이지가 열립니다. 이전 단계에서 만든 구성 컨테이너를 선택하고 **[!UICONTROL 만들기]**&#x200B;를 누릅니다.
   1. reCAPTCHA 서비스의 이름, 사이트 키 및 비밀 키를 지정하고 **[!UICONTROL 만들기]**&#x200B;를 탭하여 클라우드 서비스 구성을 만듭니다.
   1. 구성 요소 편집 대화 상자에서 1단계에서 얻은 사이트 및 비밀 키를 지정합니다. **[!UICONTROL 설정 저장]**&#x200B;을 탭한 다음, **[!UICONTROL 확인]**&#x200B;을 탭하여 구성을 완료합니다.

   reCAPTCHA 서비스가 구성되면 적응형 양식에서 사용할 수 있습니다. 자세한 내용은 적응형 양식에서 CAPTCHA 사용](#using-captcha)을 참조하십시오.[

## 적응형 양식에서 CAPTCHA 사용 {#using-captcha}

적응형 양식에 CAPTCHA를 사용하려면:

1. 편집 모드에서 적응형 양식을 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 선택한 구성 컨테이너에 reCAPTCHA 클라우드 서비스가 포함되어 있는지 확인합니다. 적응형 양식 속성을 편집하여 양식과 연결된 구성 컨테이너를 변경할 수도 있습니다.

1. 구성 요소 브라우저에서 **[!UICONTROL Captcha]** 구성 요소를 적응형 양식으로 드래그합니다.

   >[!NOTE]
   >
   >적응형 양식에서 두 개 이상의 Captcha 구성 요소를 사용할 수 없습니다. 또한 지연 로딩으로 표시된 패널 또는 조각에서 CAPTCHA를 사용하지 않는 것이 좋습니다.

   >[!NOTE]
   >
   >Captcha는 시간에 민감하며 약 1분 후에 만료됩니다. 따라서 [제출] 단추 바로 앞에 Captcha 구성 요소를 적응형 양식으로 배치하는 것이 좋습니다.

1. 추가한 Captcha 구성 요소를 선택하고 ![cmppr](assets/cmppr.png)을 탭하여 해당 속성을 편집합니다.
1. CAPTCHA 위젯의 제목을 지정합니다. 기본값은 **Captcha**&#x200B;입니다. 제목을 표시하지 않으려면 **[!UICONTROL 제목 숨기기]**&#x200B;를 선택합니다.
1. **[!UICONTROL Captcha 서비스]** 드롭다운에서 **[!UICONTROL reCaptcha]** 를 선택하여 Google](#google-recaptcha)ReCAPTCHA 서비스에 설명된 대로 구성한 경우 reCAPTCHA 서비스를 활성화합니다. [ 설정 드롭다운에서 구성을 선택합니다. 또한 reCAPTCHA 위젯의 경우 크기를 **[!UICONTROL Normal]** 또는 **[!UICONTROL Compact]**&#x200B;로 선택합니다.

   >[!NOTE]
   >
   >기본 AEM CAPTCHA 서비스가 더 이상 사용되지 않으므로 Captcha 서비스 드롭다운에서 **[!UICONTROL 기본]**&#x200B;을 선택하지 마십시오.

1. 속성을 저장합니다.

reCAPTCHA 서비스는 적응형 양식에서 활성화됩니다. 양식을 미리 보고 CAPTCHA가 작동하는 것을 볼 수 있습니다.
