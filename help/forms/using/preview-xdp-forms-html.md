---
title: XDP 양식의 HTML 5 미리 보기 생성
seo-title: Generate HTML5 preview of an XDP form
description: LiveCycle 디자이너의 미리 보기 HTML 탭을 사용하여 브라우저에서 나타나는 양식을 미리 볼 수 있습니다.
seo-description: Preview HTML tab in LiveCycle Designer can be used to preview forms as they appear in a browser.
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
feature: Mobile Forms
exl-id: f855d3f9-cf3c-4883-b82b-d607250c3dae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 2%

---

# XDP 양식의 HTML 5 미리 보기 생성 {#generate-html-preview-of-an-xdp-form}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM Forms Designer에서 양식을 디자인하는 동안 양식의 PDF 렌디션을 미리 볼 수 있을 뿐만 아니라 양식의 HTML 5 렌디션을 미리 볼 수도 있습니다. 를 사용할 수 있습니다 **미리 보기 HTML** 탭을 클릭하여 브라우저에 표시되는 양식을 미리 봅니다.

## 디자이너에서 XDP 양식에 대한 HTML 미리 보기 활성화 {#html-preview-of-forms-in-forms-designer}

디자이너가 XDP 양식의 HTML 미리 보기를 생성할 수 있도록 하려면 다음 구성을 수행하십시오.

* Apache Sling 인증 서비스 구성
* 보호 모드 비활성화
* AEM Forms 서버에 대한 세부 정보 제공

### Apache Sling 인증 서비스 구성 {#configure-apache-sling-authentication-service}

1. 이동 `https://[server]:[port]/system/console/configMgr` OSGi 또는

   `https://[server]:[port]/lc/system/console/configMgr` JEE에서 실행 중인 AEM Forms에서.

1. 을(를) 찾아 클릭합니다 **Apache Sling 인증 서비스** 구성 : 편집 모드에서 열기.

1. OSGi 또는 JEE에서 AEM Forms을 실행 중인지 여부에 따라 다음을 에 추가합니다 **인증 요구 사항** 필드:

   * JEE의 AEM Forms

      * -/content/xfaforms
      * -/etc/clientlibs
   * OSGi의 AEM Forms

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >지정한 값을 Authentication Requirements 필드에 복사하여 붙여넣으면 값의 특수 문자가 손상될 수 있습니다. 대신 필드에 지정된 값을 입력합니다.

1. 사용자 이름과 암호를 지정합니다. **[!UICONTROL 익명 사용자 이름]** 및 **[!UICONTROL 익명 사용자 암호]** 필드(각각)를 반환합니다. 지정한 자격 증명은 익명 인증을 처리하고 익명 사용자에 대한 액세스를 허용하는 데 사용됩니다.
1. 클릭 **저장** 구성을 저장합니다.

### 보호 모드 비활성화 {#disable-protected-mode}

다음 [보호 모드](/help/forms/using/get-xdp-pdf-documents-aem.md) 은 기본적으로 켜져 있습니다. 프로덕션 환경에 대해 사용하도록 설정합니다. 개발 환경에서 비활성화하여 Destiner에서 HTML 5 Forms을 미리 볼 수 있습니다. 비활성화하려면 다음 단계를 수행하십시오.

1. 관리자로 AEM 웹 콘솔에 로그인합니다.

   * OSGi에서 AEM Forms의 URL은 `https://[server]:[port]/system/console/configMgr`
   * JEE에서 AEM Forms용 URL은 `https://[server]:[port]/lc/system/console/configMgr`

1. 열기 **[!UICONTROL 모바일 Forms 구성]** 참조하십시오.
1. 선택 취소 **[!UICONTROL 보호 모드]** 옵션을 선택하고 **[!UICONTROL 저장]**.

### AEM Forms 서버에 대한 세부 정보 제공 {#provide-details-of-aem-forms-server}

1. 디자이너에서 **도구** >  **옵션**.
1. 옵션 창에서 **서버 옵션** 페이지에서 다음 세부 정보를 제공하고 **확인**.

   * **서버 URL**: AEM Forms 서버 URL입니다.
   * **HTTP 포트 번호**: AEM 서버 포트입니다. 기본값은 4502입니다.
   * **HTML 미리 보기 컨텍스트:** XFA 양식을 렌더링하기 위한 프로필의 경로입니다. 디자이너의 양식을 미리 보는 데 사용되는 기본 프로필은 다음과 같습니다. 그러나 사용자 지정 프로필에 대한 경로를 지정할 수도 있습니다.

      * `/content/xfaforms/profiles/default.html` (OSGi의 AEM Forms)
      * `/lc/content/xfaforms/profiles/default.html` (JEE의 AEM Forms)
   * **Forms Manager 컨텍스트:** Forms Manager UI가 배포되는 컨텍스트 경로입니다. 기본값은 다음과 같습니다.

      * `/aem/forms` (OSGi의 AEM Forms)
      * `/lc/forms` (JEE의 AEM Forms)

   **참고:** *AEM Forms 서버가 작동 중인지 확인합니다. HTML 미리 보기는 CRX 서버에 연결하며*&#x200B;생성&#x200B;*미리 보기.*

   ![AEM Forms 디자이너 옵션 ](assets/server_options.png)

   AEM Forms 디자이너 옵션

1. HTML에서 양식을 미리 보려면 **미리 보기 HTML** 탭.

   >[!NOTE]
   >
   >HTML 미리 보기 탭을 닫으면 F4 키를 눌러 미리 보기 HTML 탭을 엽니다. 보기 메뉴에서 HTML 미리 보기 를 선택하여 미리 보기 HTML 탭을 열 수도 있습니다.

   >[!NOTE]
   >
   >HTML 미리 보기는 PDF 문서를 지원하지 않으며, HTML 미리 보기는 XDP 문서에만 해당됩니다.

## 샘플 데이터를 사용하여 양식을 미리 보려면 {#to-preview-a-form-using-sample-data}

디자이너를 사용하면 샘플 XML 데이터를 사용하여 양식을 미리 보고 테스트할 수 있습니다. 양식이 올바르게 렌더링되도록 하려면 샘플 데이터로 양식을 자주 테스트하는 것이 좋습니다.

샘플 데이터가 없는 경우 Designer에서 만들거나 직접 만들 수 있습니다. (자세한 내용은 [양식을 미리 볼 샘플 데이터를 자동으로 생성하려면](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) 및 [양식을 미리 볼 샘플 데이터를 만들려면](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2))

샘플 데이터 소스를 사용하여 양식을 테스트하면 데이터 및 필드가 매핑되고 반복 하위 양식이 예상대로 반복됩니다. 병합된 데이터를 표시할 각 개체에 적절한 공간을 제공하는 균형 잡힌 양식 레이아웃을 만들 수 있습니다.

1. 선택 **파일 > 양식 속성**.

1. 을(를) 클릭합니다. **미리 보기** 탭을 선택하고 데이터 파일 상자에 테스트 데이터 파일의 전체 경로를 입력합니다. 찾아보기 단추를 사용하여 파일로 이동할 수도 있습니다.

1. **확인**&#x200B;을 클릭합니다. 다음에 에서 양식을 미리 볼 때 **미리 보기 HTML** 탭에서 샘플 XML 파일의 데이터 값이 각 객체에 나타납니다.

## 저장소에 있는 양식 미리 보기 {#html-preview-of-forms-in-forms-manager}

AEM Forms에서 리포지토리에서 양식과 문서를 미리 볼 수 있습니다. 미리 보기는 최종 사용자가 사용할 양식의 모양과 동작 방식을 정확하게 파악하는 데 도움이 됩니다.

[**지원 문의**](https://www.adobe.com/kr/account/sign-in.supportportal.html)
