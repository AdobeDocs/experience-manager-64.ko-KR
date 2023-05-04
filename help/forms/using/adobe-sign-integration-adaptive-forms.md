---
title: Acrobat Sign과 AEM Forms 통합
seo-title: Integrate Acrobat Sign with AEM Forms
description: AEM Forms용 Acrobat Sign 구성 방법 알아보기
seo-description: Learn how to configure Acrobat Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Acrobat Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 13%

---

# Acrobat Sign과 AEM Forms 통합 {#integrate-adobe-sign-with-aem-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Acrobat Sign을 사용하면 적응형 양식에 전자 서명 워크플로우를 사용할 수 있습니다. 전자 서명은 법무, 판매, 임금, 인적 자원 관리 등의 다양한 분야에서 문서를 처리하는 워크플로를 개선합니다.

일반적인 Acrobat Sign 및 적응형 양식 시나리오에서 사용자는 적응형 양식을 **서비스 신청**. 신용 카드 신청 양식과 시민 혜택 양식을 예로 들 수 있습니다. 사용자가 신청 양식에 정보를 입력하고 이를 제출한 뒤 서명하면, 이후의 액션이 가능하도록 양식이 서비스 제공자에게 전달됩니다. 서비스 제공업체는 애플리케이션을 검토하고 Acrobat Sign을 사용하여 승인된 애플리케이션을 표시합니다. 유사한 전자 서명 워크플로우를 활성화하기 위해 Acrobat Sign을 AEM Forms과 통합할 수 있습니다.

AEM Forms과 함께 Acrobat Sign을 사용하려면 AEM 클라우드 서비스에서 Acrobat Sign을 구성하십시오:

## 사전 요구 사항 {#prerequisites}

Acrobat Sign을 AEM Forms과 통합하려면 다음 항목이 필요합니다.

* 활성 [Acrobat Sign 개발자 계정.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* An [SSL 활성화](/help/sites-administering/ssl-by-default.md) AEM Forms 서버.
* An [Acrobat Sign API 애플리케이션](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Acrobat Sign API 애플리케이션의 자격 증명(클라이언트 ID 및 클라이언트 암호)입니다.
* 다시 구성할 때 작성자 및 게시 인스턴스 모두에서 기존 Acrobat Sign 구성을 제거합니다.
* 작성자에 대해 [동일한 암호 키](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed)를 사용하고 인스턴스를 게시합니다.

## AEM Forms을 사용하여 Acrobat Sign 구성 {#configure-adobe-sign-with-aem-forms}

사전 요구 사항이 준비되면 다음 단계를 수행하여 작성자 인스턴스에서 AEM Forms을 사용하여 Acrobat Sign을 구성합니다.

1. AEM Forms 작성자 인스턴스에서 **도구** ![망치](assets/hammer.png) > **일반** > **구성 브라우저**.
   * 자세한 내용은 [구성 브라우저 설명서](/help/sites-administering/configurations.md) 추가 정보.
1. 설정 **[!UICONTROL 구성 브라우저]** 페이지, 탭 **[!UICONTROL 만들기]**.
1. 에서 **[!UICONTROL 구성 만들기]** 대화 상자에서 다음을 지정합니다 **[!UICONTROL 제목]** 구성에 대해 **[!UICONTROL 클라우드 구성]**, 탭 **[!UICONTROL 만들기]**. 클라우드 서비스용 구성 컨테이너를 만듭니다.
1. 다음으로 이동 **도구** ![망치](assets/hammer.png) > **Cloud Services** > **Acrobat Sign** 및 위의 단계에서 만든 구성 컨테이너를 선택합니다.

   >[!NOTE]
   >
   >1-4단계를 실행하여 새 구성 컨테이너를 만들고 컨테이너에서 Acrobat Sign 구성을 만들거나 기존 를 사용할 수 있습니다 `global` 폴더 **도구** ![망치](assets/hammer.png) > **Cloud Services** > **Acrobat Sign**. 새 구성 컨테이너에서 구성을 만드는 경우 **[!UICONTROL 구성 컨테이너]** 적응형 양식을 만들 때 필드를 추가합니다.

   >[!NOTE]
   클라우드 서비스 구성 페이지의 URL이 **HTTPS**. 그렇지 않으면, [ssl 활성화](/help/sites-administering/ssl-by-default.md) AEM Forms 서버용.

1. 구성 페이지에서 **[!UICONTROL 만들기]** AEM Forms에서 Acrobat Sign 구성을 만들려면 다음을 수행하십시오.
1. 에서 **[!UICONTROL 일반]** 의 탭 **[!UICONTROL Acrobat Sign 구성 만들기]** 페이지에서, **이름** 를 사용하려면 를 탭하고 **다음**. 원하는 경우 제목을 지정하고 구성 축소판을 찾아 선택할 수 있습니다.

1. 현재 브라우저 창의 URL을 메모장에 복사합니다. AEM Forms을 사용하여 Acrobat Sign 애플리케이션을 구성해야 합니다.

1. Acrobat Sign 애플리케이션에 대한 OAuth 설정을 구성합니다.

   1. 브라우저 창을 열고 Acrobat Sign 개발자 계정에 로그인합니다.
   1. AEM Forms에 대해 구성된 애플리케이션을 선택하고 Configure OAuth for Application을 탭합니다.
   1. 에서 **리디렉션 URL** 상자에서 이전 단계에서 복사한 HTTPS URL을 추가하고 를 클릭합니다. **저장**.
   1. Acrobat Sign 애플리케이션에 대해 다음 OAuth 설정을 활성화하고 를 클릭합니다 **저장**.
   * aggregation_read
   * aggregation_write
   * aggregation_send
   * widget_write
   * workflow_read

   Acrobat Sign 애플리케이션에 대한 OAuth 설정을 구성하고 키를 가져오는 단계별 정보는 을 참조하십시오. [애플리케이션에 대한 oAuth 설정 구성](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) 개발자 설명서입니다.

   ![OAuth Config](assets/oauthconfig_new.png)

1. 로 돌아갑니다. **Acrobat Sign 구성 만들기** 페이지. 에서 **[!UICONTROL 설정]** 탭, **[!UICONTROL OAuth URL]** 필드에 다음 기본 URL이 설명되어 있습니다.

   `https://secure.na1.echosign.com/public/oauth`

   여기에서

   **na1**&#x200B;은 기본값 데이터베이스 분할을 의미합니다.

   데이터베이스 분할의 값을 수정할 수 있습니다. 데이터베이스 공유 값을 사용할 수 있도록 서버를 다시 시작합니다.

1. 을(를) 지정합니다. **클라이언트 ID** (응용 프로그램 ID라고도 함) 및 **클라이언트 암호**. 을(를) 선택합니다 **첨부 파일용 Acrobat Sign을 사용할 수도 있습니다** 적응형 양식에 첨부된 파일을 서명을 위해 전송된 해당 Acrobat Sign 문서에 첨부하는 옵션입니다.

   탭 **[!UICONTROL Acrobat Sign에 연결]**. 자격 증명을 입력하라는 메시지가 표시되면 Acrobat Sign 응용 프로그램을 만드는 동안 사용되는 계정의 사용자 이름과 암호를 입력합니다.

   탭 **[!UICONTROL 만들기]** Acrobat Sign 구성을 만들려면

1. AEM 웹 콘솔을 엽니다. URL은 `https://'[server]:[port]'/system/console/configMgr`
1. 열기 **Forms 일반 구성 서비스.**
1. 에서 **허용** 필드, **선택** 모든 사용자 - 익명 또는 로그인한 모든 사용자는 첨부 파일을 미리 보고, 양식을 확인 및 서명하고, **저장.** 작성자 인스턴스가 Acrobat Sign을 사용하도록 구성되었습니다.
1. 사용 [복제](/help/sites-deploying/replication.md) 해당 게시 인스턴스에 동일한 구성을 만들려면

이제 Acrobat Sign은 AEM Forms과 통합되어 적응형 양식에 사용할 수 있습니다. 종료 [적응형 양식에서 Acrobat Sign 서비스 사용](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)적응형 양식 속성에서 위에 만든 구성 컨테이너를 지정합니다.

## 서명 상태를 동기화하도록 Acrobat Sign 스케줄러 구성 {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

모든 서명자가 서명 프로세스를 완료한 후에만 Acrobat Sign이 활성화된 적응형 양식이 제출됩니다. 기본적으로 Acrobat Sign 스케줄러 서비스는 24시간마다 후에 (폴링) 서명자 응답을 확인하도록 예약됩니다. 해당 환경에 맞게 기본값 간격을 변경할 수 있습니다. 기본 간격을 변경하려면 다음 단계를 수행하십시오.

1. 관리자 자격 증명을 사용하여 AEM Forms 서버에 로그인하고 **도구** > **작업** > **웹 콘솔**.

   브라우저 창에서 다음 URL을 열 수도 있습니다.
   `https://[localhost]:'port'/system/console/configMgr`

1. 을(를) 찾아 엽니다. **Acrobat Sign 구성 서비스** 선택 사항입니다. 을(를) 지정합니다 [cron 식](https://en.wikipedia.org/wiki/Cron#CRON_expression) 에서 **상태 업데이트 스케줄러 표현식** 필드를 입력하고 **저장**. 예를 들어 매일 오전 00:00에 구성 서비스를 실행하려면 `0 0 0 1/1 * ? *` 에서 **상태 업데이트 스케줄러 표현식** 필드.

이제 Acrobat Sign의 동기화 상태에 대한 기본 간격이 변경되었습니다.

## 관련 문서 {#related-articles}

* [적응형 양식에서 Acrobat Sign 사용](../../forms/using/working-with-adobe-sign.md)
* [AEM Forms에서 Acrobat Sign 사용(비디오)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Acrobat Sign과 AEM Forms 통합](../../forms/using/adobe-sign-integration-adaptive-forms.md)
