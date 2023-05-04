---
title: JEE 프로세스에서 AEM Forms에 양식 데이터를 제출하도록 AEM Forms 구성
seo-title: Configuring AEM Forms to submit form data to an AEM Forms on JEE process
description: AEM Forms을 사용하면 적응형 양식을 JEE 프로세스의 AEM Forms과 통합하여 양식 데이터를 처리할 수 있습니다.
seo-description: AEM Forms allows you to integrate adaptive forms with AEM Forms on JEE processes for processing form data.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
role: Admin
exl-id: 260e405e-f59c-4aea-b83f-53ee103df94e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# JEE 프로세스에서 AEM Forms에 양식 데이터를 제출하도록 AEM Forms 구성 {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

적응형 양식은 추가적인 처리를 위해 JEE 프로세스에서 AEM Forms에 데이터 제출을 지원합니다. 이를 통해 제출된 양식에서 사용할 수 있는 데이터로 JEE 프로세스에서 AEM Forms을 트리거할 수 있습니다. AEM Forms 인스턴스가 JEE 프로세스에서 AEM Forms에 적응형 양식을 제출할 수 있도록 하려면 다음 단계를 수행하십시오.

## AEM Forms 서버 구성 {#configure-your-aem-forms-server}

AEM Forms 서버가 JEE 서버의 AEM Forms에 데이터를 제출하도록 하려면 다음 단계를 수행하십시오.

1. https://에서 AEM 웹 구성 콘솔로 이동합니다.[*호스트*]:[*포트*]/system/console/configMgr.

1. 을(를) 찾아 클릭합니다. **Adobe LiveCycle 클라이언트 SDK 구성** 구성 요소.
1. JEE 서버의 AEM Forms 구성 서버 URL, 사용자 이름 및 암호를 편집하려면 을(를) 클릭합니다.
1. 설정을 검토하고 를 클릭합니다. **저장**.

![Adobe LiveCycle 클라이언트 SDK 구성](assets/clientsdkconfiguration.jpg)

## 프로세스 필드에 데이터 매핑 {#map-data-with-process-fields}

AEM Forms이 구성되면 제출된 양식의 데이터 XML 및 첨부 파일을 JEE 프로세스의 AEM Forms 필드에 매핑합니다. 이를 위해 진행되는 작업:

1. AEM 웹 구성 콘솔에서 을(를) 클릭하여 **가이드 LiveCycle 프로세스 로케이터 및 인포커** 구성.
1. 다음 매개 변수를 지정합니다.

   * **데이터 xml 매개 변수의 이름** (필수): 제출된 데이터를 처리해야 하는 JEE 프로세스에서 AEM Forms의 XML 속성 파일을 지정합니다. 기본값은 입니다. **dataxml**.
   * **첨부 파일 매개변수 이름** (선택 사항): JEE의 AEM Forms 프로세스에서 처리해야 하는 문서 객체 목록을 지정합니다. 기본값은 입니다. **fileAttachmentsList**.

1. 설정을 검토하고 를 클릭합니다. **저장**.

![가이드 LiveCycle 프로세스 로케이터 및 인포커](assets/test3.jpg)

구성된 경우, Submit to Forms Workflow 제출 작업은 지정된 데이터 xml 매개 변수를 포함하는 JEE 서버 프로세스의 AEM Forms을 나열합니다.
