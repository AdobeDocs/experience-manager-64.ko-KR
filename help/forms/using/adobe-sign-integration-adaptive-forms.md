---
title: Adobe Sign과 AEM Forms 통합
seo-title: Adobe Sign과 AEM Forms 통합
description: AEM Forms용 Adobe Sign 구성 방법 알아보기
seo-description: AEM Forms용 Adobe Sign 구성 방법 알아보기
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: 응용 Forms, Adobe Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# Adobe Sign과 AEM Forms 통합 {#integrate-adobe-sign-with-aem-forms}

Adobe Sign을 사용하면 적응형 양식에 전자 서명 워크플로우를 사용할 수 있습니다. 전자 서명은 법률, 영업, 급여, 인적 자원 관리 및 기타 여러 분야에 대한 문서를 처리하기 위한 워크플로우를 개선합니다.

일반적인 Adobe Sign 및 적응형 양식 시나리오에서 사용자는 적응형 양식을 **서비스**&#x200B;에 적용합니다. 예를 들어, 신용카드 신청서와 시민 혜택 양식입니다. 사용자가 애플리케이션 양식을 작성, 제출 및 서명하면 추가 작업을 위해 양식이 서비스 공급자에게 전송됩니다. 서비스 제공업체는 애플리케이션을 검토하고 Adobe Sign을 사용하여 승인된 애플리케이션을 표시합니다. 유사한 전자 서명 워크플로우를 활성화하기 위해 Adobe Sign을 AEM Forms과 통합할 수 있습니다.

AEM Forms과 함께 Adobe Sign을 사용하려면 AEM 클라우드 서비스에서 Adobe Sign을 구성하십시오:

## 전제 조건 {#prerequisites}

Adobe Sign을 AEM Forms과 통합하려면 다음 항목이 필요합니다.

* 활성 [Adobe Sign 개발자 계정입니다.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* [SSL이 활성화된](/help/sites-administering/ssl-by-default.md) AEM Forms 서버입니다.
* [Adobe Sign API 애플리케이션](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md)
* Adobe Sign API 애플리케이션의 자격 증명(클라이언트 ID 및 클라이언트 암호)입니다.
* 다시 구성할 때 작성자 및 게시 인스턴스 모두에서 기존 Adobe Sign 구성을 제거합니다.
* 작성자 및 게시 인스턴스에 대해 [동일한 암호화 키](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed)를 사용하십시오.

## AEM Forms {#configure-adobe-sign-with-aem-forms}으로 Adobe Sign 구성

사전 요구 사항이 준비되면 다음 단계를 수행하여 작성자 인스턴스에서 AEM Forms을 사용하여 Adobe Sign을 구성합니다.

1. AEM Forms 작성자 인스턴스에서 **도구** ![햄머](assets/hammer.png) > **일반** > **구성 브라우저**&#x200B;로 이동합니다.
   * 자세한 내용은 [구성 브라우저 설명서](/help/sites-administering/configurations.md)를 참조하십시오.
1. **[!UICONTROL 구성 브라우저]** 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.
1. **[!UICONTROL 구성 만들기]** 대화 상자에서 구성에 대해 **[!UICONTROL 제목]**&#x200B;을 지정하고, **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정하고 **[!UICONTROL 만들기]**&#x200B;를 탭합니다. 클라우드 서비스용 구성 컨테이너를 만듭니다.
1. **도구** ![햄머](assets/hammer.png) > **Cloud Services** > **Adobe Sign**&#x200B;로 이동하여 위의 단계에서 만든 구성 컨테이너를 선택합니다.

   >[!NOTE]
   >
   >1-4단계를 실행하여 새 구성 컨테이너를 만들고 컨테이너에서 Adobe Sign 구성을 만들거나 **도구** ![햄머](assets/hammer.png) > **Cloud Services** > **Adobe Sign**&#x200B;에서 기존 `global` 폴더를 사용할 수 있습니다. 새 구성 컨테이너에서 구성을 만드는 경우 적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드에 컨테이너 이름을 지정해야 합니다.

   >[!NOTE]
   클라우드 서비스 구성 페이지의 URL이 **HTTPS**&#x200B;로 시작하는지 확인합니다. 없는 경우 [AEM Forms 서버용 SSL](/help/sites-administering/ssl-by-default.md)을 활성화합니다.

1. 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 탭하여 AEM Forms에서 Adobe Sign 구성을 만듭니다.
1. **[!UICONTROL Adobe Sign 구성 만들기]** 페이지의 **[!UICONTROL 일반]** 탭에서 구성에 대해 **이름**&#x200B;을 지정하고 **다음**&#x200B;을 탭합니다. 원하는 경우 제목을 지정하고 구성 축소판을 찾아 선택할 수 있습니다.

1. 현재 브라우저 창의 URL을 메모장에 복사합니다. AEM Forms을 사용하여 Adobe Sign 애플리케이션을 구성해야 합니다.

1. Adobe Sign 애플리케이션에 대한 OAuth 설정을 구성합니다.

   1. 브라우저 창을 열고 Adobe Sign 개발자 계정에 로그인합니다.
   1. AEM Forms에 대해 구성된 애플리케이션을 선택하고 Configure OAuth for Application을 탭합니다.
   1. **리디렉션 URL** 상자에서 이전 단계에서 복사한 HTTPS URL을 추가하고 **저장**&#x200B;을 클릭합니다.
   1. Adobe Sign 응용 프로그램에 대해 다음 OAuth 설정을 활성화하고 **저장**&#x200B;을 클릭합니다.
   * aggregation_read
   * aggregation_write
   * aggregation_send
   * widget_write
   * workflow_read

   Adobe Sign 애플리케이션에 대한 OAuth 설정을 구성하고 키를 가져오는 단계별 정보는 [애플리케이션](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) 개발자 설명서에 대한 oAuth 설정 구성 을 참조하십시오.

   ![OAuth 구성](assets/oauthconfig_new.png)

1. **Adobe Sign 구성 만들기** 페이지로 돌아갑니다. **[!UICONTROL 설정]** 탭에서 **[!UICONTROL OAuth URL]** 필드에 다음 기본 URL이 표시됩니다.

   `https://secure.na1.echosign.com/public/oauth`

   위치:

   **na1** 은 기본 데이터베이스 공유 항목을 나타냅니다.

   데이터베이스 공유 값에 대한 값을 수정할 수 있습니다. 데이터베이스 공유 값을 사용할 수 있도록 서버를 다시 시작합니다.

1. **클라이언트 ID**(응용 프로그램 ID라고도 함) 및 **클라이언트 암호**&#x200B;를 지정합니다. 적응형 양식에 첨부된 파일을 서명을 위해 전송된 해당 Adobe Sign 문서에 추가하려면 **첨부 파일용 Adobe Sign 사용** 옵션을 선택합니다.

   **[!UICONTROL Adobe Sign에 연결]**&#x200B;을 누릅니다. 자격 증명을 입력하라는 메시지가 표시되면 Adobe Sign 응용 프로그램을 만드는 동안 사용되는 계정의 사용자 이름과 암호를 입력합니다.

   **[!UICONTROL 만들기]**&#x200B;를 탭하여 Adobe Sign 구성을 만듭니다.

1. AEM 웹 콘솔을 엽니다. URL은 `https://'[server]:[port]'/system/console/configMgr`입니다.
1. **Forms 일반 구성 서비스를 엽니다.**
1. **허용** 필드에서 **모든 사용자 선택** - 익명 또는 로그인한 모든 사용자는 첨부 파일을 미리 보고 양식을 확인 및 서명할 수 있으며 **저장 을 클릭합니다.** 작성자 인스턴스가 Adobe Sign을 사용하도록 구성되었습니다.
1. 해당 게시 인스턴스에 동일한 구성을 만들려면 [replication](/help/sites-deploying/replication.md)을 사용하십시오.

이제 Adobe Sign은 AEM Forms과 통합되어 적응형 양식에 사용할 수 있습니다. [적응형 양식](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)에서 Adobe Sign 서비스를 사용하려면 적응형 양식 속성에서 위에 만든 구성 컨테이너를 지정하십시오.

## 서명 상태 {#configure-adobe-sign-scheduler-to-sync-the-signing-status}를 동기화하도록 Adobe Sign 스케줄러 구성

모든 서명자가 서명 프로세스를 완료한 후에만 Adobe Sign이 활성화된 적응형 양식이 제출됩니다. 기본적으로 Adobe Sign 스케줄러 서비스는 24시간마다 후에 (폴링) 서명자 응답을 확인하도록 예약됩니다. 환경의 기본 간격을 변경할 수 있습니다. 기본 간격을 변경하려면 다음 단계를 수행하십시오.

1. 관리자 자격 증명을 사용하여 AEM Forms 서버에 로그인하고 **도구** > **작업** > **웹 콘솔**&#x200B;로 이동합니다.

   브라우저 창에서 다음 URL을 열 수도 있습니다.
   `https://[localhost]:'port'/system/console/configMgr`

1. **Adobe Sign 구성 서비스** 옵션을 찾아 엽니다. **상태 업데이트 스케줄러 표현식** 필드에 [콘 표현식](https://en.wikipedia.org/wiki/Cron#CRON_expression)을 지정하고 **저장**&#x200B;을 클릭합니다. 예를 들어, 매일 오전 00:00에 구성 서비스를 실행하려면 **상태 업데이트 스케줄러 표현식** 필드에 `0 0 0 1/1 * ? *`을 지정합니다.

이제 Adobe Sign의 동기화 상태에 대한 기본 간격이 변경되었습니다.

## 관련 문서 {#related-articles}

* [적응형 양식에서 Adobe Sign 사용](../../forms/using/working-with-adobe-sign.md)
* [AEM Forms에서 Adobe Sign 사용(비디오)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Adobe Sign과 AEM Forms 통합](../../forms/using/adobe-sign-integration-adaptive-forms.md)
