---
title: 이메일 서비스 공급자에 이메일 게시
seo-title: Publishing an Email to Email Service Providers
description: ExactTarget 및 Silverpop Engage와 같은 이메일 서비스에 뉴스레터를 게시할 수 있습니다.
seo-description: You can publish newsletters to e-mail services such as ExactTarget and Silverpop Engage.
uuid: 1a7adcfe-8e52-49f4-9a00-99ac99881225
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: b9618913-5433-4baf-9ff6-490a26860505
exl-id: 1353b302-7b8e-4c74-b3d2-8b0a3d4a0612
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 4%

---

# 이메일 서비스 공급자에 이메일 게시{#publishing-an-email-to-email-service-providers}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

ExactTarget 및 Silverpop Engage와 같은 이메일 서비스에 뉴스레터를 게시할 수 있습니다. 이 문서에서는 이러한 이메일 서비스에 뉴스레터를 게시하도록 AEM을 구성하는 방법에 대해 설명합니다.

>[!NOTE]
>
>이메일을 만들고 게시하려면 먼저 서비스 공급자를 구성해야 합니다. 자세한 내용은 [ExactTarget 구성](/help/sites-administering/exacttarget.md) 및 [Silverpop Engage 구성](/help/sites-administering/silverpop.md) 추가 정보.

전자 메일 서비스 공급자에 전자 메일을 게시하려면 다음 단계를 수행해야 합니다.

1. 이메일을 만듭니다.
1. 이메일에 이메일 서비스 구성을 적용합니다.
1. 이메일을 게시합니다.

>[!NOTE]
>
>이메일 공급자를 업데이트하거나, 플라이트 테스트를 수행하거나, 뉴스레터를 전송하는 경우, 뉴스레터가 게시 인스턴스에 먼저 게시되지 않거나, 게시 인스턴스를 사용할 수 없는 경우 이 작업이 실패합니다. 뉴스레터를 게시하고 게시 인스턴스가 작동되어 실행 중인지 확인하십시오.

## 이메일 만들기 {#creating-an-email}

이메일 서비스에 게시하려는 이메일 또는 뉴스레터는 **Geometrixx 뉴스레터** 템플릿. 를 사용할 수도 있습니다 **Geometrixx Outdoors 이메일** 템플릿. 을 기반으로 하는 이메일/뉴스레터 샘플 **Geometrixx Outdoors 이메일** 템플릿을 사용할 수 있는 위치: `https://<hostname>:<port>/cf#/content/campaigns/geometrixx-outdoors/e-mails.html`.

구성된 이메일 서비스에 게시된 새 이메일을 만들려면:

1. 이동 **웹 사이트** 그리고 **캠페인**. 캠페인을 선택합니다.
1. 클릭 **새로 만들기** 열다 **페이지 만들기** 창을 엽니다.
1. 제목과 이름을 입력하고 **Geometrixx 뉴스레터** 사용 가능한 템플릿 목록의 템플릿입니다.
1. **만들기**&#x200B;를 클릭합니다.
1. 만든 이메일을 엽니다.
1. 디자인 모드로 전환하여 사이드 킥에 표시할 구성 요소를 선택합니다.
1. 편집 모드로 전환한 후 컨텐츠(텍스트, 이미지, [전자 메일 도구](#adding-exacttarget-email-tools-to-your-email), [개인화 변수](#adding-text-and-personalization-tool-to-your-e-mail)등)을 전자 메일에 추가합니다.

### 이메일에 ExactTarget 이메일 도구 추가 {#adding-exacttarget-email-tools-to-your-email}

>[!NOTE]
>
>이 섹션은 ExactTarget 서비스에만 적용됩니다.

다음 **이메일 도구** exactTarget 구성 요소를 통해 이메일/뉴스레터에 이메일 기능을 더 추가할 수 있습니다.

1. ExactTarget에 게시할 이메일을 엽니다.
1. 구성 요소 추가 **ET - 이메일 도구** 사이드킥을 사용하여 페이지에 추가합니다. 구성 요소를 편집 모드에서 엽니다.

   ![chlimage_1](assets/chlimage_1.gif)

1. 에서 옵션을 선택합니다 **옵션** 메뉴:

<table> 
 <tbody> 
  <tr> 
   <td>실제 우편 주소(필수)</td> 
   <td>이 구성 요소는 이메일에 조직의 실제 우편 주소를 삽입합니다.</td> 
  </tr> 
  <tr> 
   <td>프로필 센터(필수)</td> 
   <td>프로필 센터는 가입자가 자신에 대해 보존하는 개인 정보를 입력하고 유지할 수 있는 웹 페이지입니다.</td> 
  </tr> 
  <tr> 
   <td>이메일을 웹 페이지로 보기</td> 
   <td>이 구성 요소로 사용자는 이메일을 웹 페이지로 볼 수 있습니다.</td> 
  </tr> 
  <tr> 
   <td>개인정보 처리방침</td> 
   <td>이 구성 요소는 링크를 이메일의 개인정보 처리방침에 삽입합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>가입 해제 센터</td> 
   <td>사용자가 메일링 목록에서 가입을 해지할 수 있는 옵션을 제공합니다.</td> 
  </tr> 
  <tr> 
   <td>가입 센터</td> 
   <td>가입 센터는 조직으로부터 받는 메시지를 가입자가 제어할 수 있는 웹 페이지입니다.</td> 
  </tr> 
  <tr> 
   <td>이메일 열기 횟수 추적</td> 
   <td>ExactTarget 추적 기능을 사용할 수 있도록 해주는 숨겨진 구성 요소입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>다음 **옵션** 드롭다운 메뉴는 ExactTarget 구성이 이메일에 적용되는 경우에만 채워집니다. 자세한 내용은 [이메일 설정에 이메일 서비스 구성 적용](#applying-e-mail-service-configuration-to-e-mail-settings) 추가 정보.

1. 이메일을 ExactTarget에 게시합니다.

   이메일 도구가 있는 이메일은 구성된 ExactTarget 계정에서 사용할 수 있습니다.

>[!NOTE]
>
>* 이메일 도구 내의 URL(수신된 이메일의)은 을 사용하여 이메일을 보낼 때만 실제 값으로 바뀝니다 **단순 보내기** 또는 **안내 전송** 하지만 **테스트 보내기**.
>
>* 다음 두 가지 이메일 도구가 필요합니다. **실제 우편 주소(필수)** 및 **프로필 센터(필수)**. 이메일이 ExactTarget에 게시되면 기본적으로 이 두 개의 이메일 도구가 모든 메일 하단에 추가됩니다.
>


### 이메일에 텍스트 및 개인화 도구 추가 {#adding-text-and-personalization-tool-to-your-e-mail}

을(를) 추가하여 이메일에 개인화된 필드를 추가할 수 있습니다 **텍스트 및 개인화** 구성 요소를 페이지에 추가:

1. 전자 메일 서비스에 게시할 전자 메일을 엽니다.
1. 이메일 서비스에서 개인화 필드를 활성화하려면 이메일 서비스를 구성하는 동안 프레임워크 구성을 추가하십시오. 자세한 내용은 [silverpop Engage 구성](/help/sites-administering/silverpop.md) 및 [정확한 Target 구성](/help/sites-administering/exacttarget.md) 추가 정보.
1. 구성 요소 추가 **텍스트 및 개인화** 사이드 킥에서 이 구성 요소는 뉴스레터 그룹의 일부입니다. 편집 모드에서 이 구성 요소를 엽니다.

   ![chlimage_1-110](assets/chlimage_1-110.png)

1. 드롭다운 메뉴에서 필드를 선택하고 을(를) 클릭하여 필요한 개인화된 필드를 텍스트에 추가합니다 **삽입**.
1. 클릭 **확인** 을 클릭하여 끝내십시오.

## 전자 메일 설정에 전자 메일 서비스 구성 적용 {#applying-e-mail-service-configuration-to-e-mail-settings}

뉴스레터에 이메일 서비스 구성을 적용하려면:

1. 이메일 서비스 구성을 만듭니다.
1. 이메일/뉴스레터를 엽니다.
1. 다음 중 하나를 클릭하여 이메일/뉴스레터 설정을 엽니다 **설정** 또는 **의 페이지 속성** 사이드킥이요
1. 클릭 **서비스 추가** in **Cloud Services** 탭. 서비스 목록이 표시됩니다. 필요한 구성을 선택합니다. **ExactTarget** 또는 **Silverpop** - 드롭다운 목록의 목록에서

   ![chlimage_1-5](assets/chlimage_1-5.jpeg)

1. **확인**&#x200B;을 클릭합니다.

## 이메일 서비스에 이메일 게시 {#publishing-emails-to-email-service}

다음 절차에 따라 이메일/뉴스레터를 이메일 서비스에 게시할 수 있습니다.

1. 이메일을 엽니다.
1. 이메일을 게시하기 전에 이메일에 올바른 구성을 적용했는지 확인하십시오.
1. **게시**&#x200B;를 클릭합니다. 이렇게 하면 **이메일 서비스 공급자에 뉴스레터 게시** 창을 엽니다.
1. 을 입력합니다. **뉴스레터 이름** 필드. 이메일/뉴스레터가 이 이름으로 이메일 서비스 공급자에 게시됩니다. 이메일 이름을 제공하지 않으면 AEM의 뉴스레터 페이지 이름을 사용하여 이메일이 게시됩니다.
1. **게시**&#x200B;를 클릭합니다.

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

   성공적으로 작업이 수행되면 AEM에서는 ExactTarget 또는 Silverpop Engage에서 이메일을 볼 수 있다는 것을 확인합니다.

   ExactTarget의 경우, 게시된 이메일은 **게시된 이메일 보기**. ExactTarget([https://members.exacttarget.com/](https://members.exacttarget.com/).)

>[!NOTE]
>
>이메일/뉴스레터가 이미 게시된 이메일/뉴스레터와 동일한 이름으로 게시되면 이전 이메일/뉴스레터가 교체되지 않습니다. 대신 동일한 이름으로 새 이메일/뉴스레터가 만들어집니다(하지만 두 뉴스레터의 ID는 다름).
>
>이메일/뉴스레터를 이메일 서비스 공급자에게 게시해도 이메일/뉴스레터가 AEM 게시 인스턴스에 게시됩니다.

### 게시된 이메일 업데이트 {#updating-a-published-e-mail}

다음 **업데이트** 게시 대화 상자의 단추를 사용하면 이미 이메일 서비스 공급자에 게시된 뉴스레터를 업데이트할 수 있습니다. 뉴스레터가 아직 게시되지 않았으며 **업데이트** 단추를 클릭하거나 **뉴스레터가 게시되지 않음** 메시지가 표시됩니다.

게시된 이메일을 업데이트하려면:

1. 이메일/뉴스레터를 변경한 후 다시 게시할 이메일 서비스 공급자에 이전에 게시한 이메일/뉴스레터를 엽니다.
1. **게시**&#x200B;를 클릭합니다. 다음 **이메일 서비스 공급자에 뉴스레터 게시** 창이 표시됩니다. **업데이트**&#x200B;를 클릭합니다.

   이메일/뉴스레터가 ExactTarget에서 업데이트되었는지 확인하려면, **게시된 이메일 보기**. 게시된 이메일이 ExactTarget에 표시됩니다.

   이메일/뉴스레터가 Silverpop 이메일 서비스에서 업데이트되었는지 확인하려면 Silverpop Engage 사이트를 방문하십시오.
