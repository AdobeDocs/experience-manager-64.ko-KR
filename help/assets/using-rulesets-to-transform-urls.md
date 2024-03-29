---
title: 규칙 세트를 사용하여 URL 변환
description: 'Dynamic Media에서 규칙 세트를 배포하여 URL을 변환할 수 있습니다. 규칙 세트는 XML 데이터를 평가하고 특정 조건을 충족하는 경우 특정 작업을 수행하는 스크립팅 언어(예: JavaScript)로 작성된 지침 세트입니다. '
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: f0cd3a75-03ed-40a9-b336-8a782f3cfe69
feature: Rulesets
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 6%

---

# 규칙 세트를 사용하여 URL 변환 {#using-rulesets-to-transform-urls}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Dynamic Media에서 규칙 세트를 배포하여 URL을 변환할 수 있습니다. 규칙 세트는 XML 데이터를 평가하고 특정 조건을 충족하는 경우 특정 작업을 수행하는 스크립팅 언어(예: JavaScript)로 작성된 지침 세트입니다. 각 규칙은 하나 이상의 조건과 하나 이상의 작업으로 구성됩니다. 규칙은 조건에 대해 XML 데이터를 평가하고 조건이 충족되면 적절한 작업을 수행합니다. 규칙 세트의 예는 다음과 같습니다.

* MIME 유형 접미사를 추가하는 중입니다. 많은 서비스 및 웹 사이트에는 추가 등의 이미지 접미사가 필요합니다 `.jpg` 추가 URL.
* SEO(검색 엔진 최적화) 목적의 URL에 대한 폴더 경로 만들기

   자세한 내용은 [Adobe Dynamic Media Classic에서 SEO를 지원하는 방법](/help/assets/assets/s7_seo.pdf).

* SEO(검색 엔진 최적화) 목적으로 URL에 메타데이터 추가.

   자세한 내용은 [Adobe Dynamic Media Classic에서 SEO를 지원하는 방법](/help/assets/assets/s7_seo.pdf).

* 다운로드를 트리거하도록 컨텐츠 처리를 설정합니다.
* 개인화를 위해 이미지 제공 템플릿 URL을 단순화합니다. 예를 들어 `rgb{XX,YY,ZZ}` RTF에 `\redXX\greenYY\blueZZ`

* 인코딩할 특정 문자 요청(예: ) `$`, `{`, 및 `}`및 ImageServer에 디코딩할 특정 문자 예를 들어 Facebook은 특수 문자가 포함된 URL에서 잘 작동하지 않습니다.

   자세한 내용은 [URL에서 특수 문자 제거](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

Dynamic Media 컨텍스트에서 XML 기반 시스템을 사용하여 자산 정보를 관리하는 웹 사이트는 XML 파일을 Dynamic Media에 업로드할 수 있습니다. 이러한 파일 중 하나를 Dynamic Media 자산을 제공할 사전 처리 규칙 세트 파일로 지정할 수 있습니다. 이 파일은 Dynamic Media과 통합되는 시스템의 비즈니스 로직을 충족하도록 표준 URL 프로토콜 형식을 재구성합니다. 규칙 세트 정의 파일 경로로 사용할 XML 파일을 지정합니다.

>[!CAUTION]
>
>규칙 세트를 사용할 때는 주의하십시오. 웹 사이트에 Dynamic Media 컨텐츠가 표시되지 않도록 할 수 있습니다.

고유한 규칙 세트를 만드는 데 도움이 되는 샘플 규칙 세트를 사용할 수 있습니다.\
자세한 내용은 [규칙 세트 참조](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/rule-set-reference/c-rule-set-reference.html).

모든 규칙 세트 생성과 마찬가지로 xmlvalid와 같은 XML 유효성 검사기 프로그램을 사용하여 업로드하기 전에 XML 파일이 유효한지 확인하십시오.\
참조 - [규칙 세트 문제 해결](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html).

또한 라이브 프로덕션 환경에 영향을 주지 않는 스테이징 환경에서 규칙 세트를 먼저 테스트해야 합니다.\
프로덕션 환경 및 스테이징 환경에서는 일반적으로 다른 로그인이 필요합니다.

자세한 내용은 [로그인 정보를 위한 Adobe Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#sign-in-dmc-app).

<!-- * **NA staging environment** login page: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **EMEA staging environment** login page: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC staging environment** login page: [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/) -->

참조 - [규칙 세트에서 &#39;is&#39; 이미지 대신 &#39;asset&#39;를 사용](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html).

**XML 규칙 세트를 배포하려면**

1. 사용자 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#sign-in-dmc-app).

   자격 증명 및 로그인은 프로비저닝 시 Adobe이 제공했습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.

1. 다음을 수행하여 규칙 세트 파일을 업로드합니다.

   * 전역 탐색 막대에서 **[!UICONTROL 업로드]**.
   * 설정 **[!UICONTROL 업로드]** 왼쪽 위 모서리 근처에 있는 페이지에서 **[!UICONTROL 찾아보기]**.
   * 에서 **[!UICONTROL 열기]** 대화 상자에서 규칙 세트 파일(XML)로 이동합니다.
   * 파일을 선택한 다음 **[!UICONTROL 열기]**.
   * 오른쪽 **[!UICONTROL 업로드]** 페이지에서 규칙 세트 파일의 대상 폴더를 선택합니다.
   * 페이지 하단 근처에 **[!UICONTROL 업로드 후 게시]** 이(가) 선택되어 있습니다.
   * 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 업로드 제출]**.
   * 전역 탐색 막대에서 **[!UICONTROL 작업]** 업로드 작업의 상태를 확인합니다. 이 **[!UICONTROL 상태]** 열 **[!UICONTROL 작업]** 페이지에 업로드 완료 가 표시되면 다음 단계를 계속 진행합니다.

1. 페이지 상단 근처에 있는 탐색 막대에서 **[!UICONTROL 설정 > 애플리케이션 설정 > 게시 설정 > 이미지 서버]**.
1. On the **[!UICONTROL Image Server Publish]** page, under the **[!UICONTROL Catalog Management]** group, locate **[!UICONTROL Rule Set Definition File Path]**, then click **[!UICONTROL Select]**.
1. On the **[!UICONTROL Select Rule Set Definition File (XML)]** page, browse to your rule set file, then in the lower-right corner of the page, click **[!UICONTROL Select]**.
1. Setup 페이지의 오른쪽 아래 모서리에서 을 클릭합니다. **[!UICONTROL 닫기]**.
1. 이미지 서버 게시 작업을 실행합니다.

   규칙 세트 조건은 라이브 Dynamic Media 이미지 서버에 대한 요청에 적용됩니다.

   규칙 세트 파일을 변경하면 다시 업로드하고 업데이트된 규칙 세트 파일을 다시 게시할 때 변경 사항이 즉시 적용됩니다.
