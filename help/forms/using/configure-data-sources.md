---
title: 데이터 소스 구성
seo-title: 데이터 소스 구성
description: 다양한 유형의 데이터 소스를 구성하고 활용하여 양식 데이터 모델을 만드는 방법을 살펴볼 수 있습니다.
seo-description: 다양한 유형의 데이터 소스를 구성하고 활용하여 양식 데이터 모델을 만드는 방법을 살펴볼 수 있습니다.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: 양식 데이터 모델
exl-id: a8f200ac-cf9f-47b7-9856-e62aa8b229eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 1%

---

# 데이터 소스 구성 {#configure-data-sources}

다양한 유형의 데이터 소스를 구성하고 활용하여 양식 데이터 모델을 만드는 방법을 살펴볼 수 있습니다.

![](do-not-localize/data-integeration.png)

AEM Forms 데이터 통합을 사용하면 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 기본적으로 지원되는 유형은 다음과 같습니다. 그러나 사용자 지정이 거의 없는 경우에도 다른 데이터 소스를 통합할 수 있습니다.

* 관계형 데이터베이스 - MySQL, Microsoft SQL Server, IBM DB2 및 Oracle RDBMS
* AEM 사용자 프로필
* RESTful 웹 서비스
* SOAP 기반 웹 서비스
* OData 서비스

데이터 통합은 OAuth2.0, 기본 인증 및 API 키 인증 유형을 즉시 지원하며, 웹 서비스에 액세스하기 위한 사용자 지정 인증을 구현할 수 있습니다. RESTful, SOAP 기반 및 OData 서비스가 AEM Cloud Services에 구성되어 있지만, 관계형 데이터베이스용 JDBC 및 AEM 사용자 프로필용 커넥터가 AEM 웹 콘솔에 구성되어 있습니다.

## 관계형 데이터베이스 구성 {#configure-relational-database}

AEM Web Console 구성을 사용하여 관계형 데이터베이스를 구성할 수 있습니다. 다음을 수행합니다.

1. `https://[server]:[host]/system/console/configMgr`에 있는 AEM 웹 콘솔로 이동합니다.
1. **[!UICONTROL Apache Sling 연결의 풀링된 데이터 소스]** 구성을 찾습니다. 편집 모드에서 구성을 열려면 탭합니다.
1. 구성 대화 상자에서 다음과 같이 구성할 데이터베이스에 대한 세부 정보를 지정합니다.

   * 데이터 소스의 이름
   * 데이터 소스 이름을 저장하는 데이터 소스 서비스 속성
   * JDBC 드라이버의 Java 클래스 이름
   * JDBC 연결 URI
   * JDBC 드라이버와의 연결을 설정하기 위한 사용자 이름 및 암호

   >[!NOTE]
   >
   >데이터 소스를 구성하기 전에 암호와 같은 중요한 정보를 암호화해야 합니다. 암호화하려면:
   >
   >1. 이동 `https://[server]:[port]/system/console/crypto`.
   >1. **[!UICONTROL 일반 텍스트]** 필드에서 암호화할 암호나 문자열을 지정하고 **[!UICONTROL Protect]**&#x200B;을 클릭합니다.

   >
   >암호화된 텍스트는 구성에서 지정할 수 있는 보호된 텍스트 필드에 나타납니다.

1. **[!UICONTROL Test on Look]** 또는 **[!UICONTROL Test on Return]**&#x200B;을 활성화하여 개체를 빌리거나 풀에서 반환하기 전에 검증하도록 지정합니다.
1. **[!UICONTROL 검증 쿼리]** 필드에 SQL SELECT 쿼리를 지정하여 풀에서 연결을 확인합니다. 쿼리는 하나 이상의 행을 반환해야 합니다. 데이터베이스를 기준으로 다음 중 하나를 지정합니다.

   * 선택 1(MySQL 및 MS SQL)
   * 이중(Oracle)에서 1을 선택합니다

1. **[!UICONTROL 저장]**&#x200B;을 눌러 구성을 저장합니다.

## AEM 사용자 프로필 구성 {#configure-aem-user-profile}

AEM Web Console에서 사용자 프로필 커넥터 구성을 사용하여 AEM 사용자 프로필을 구성할 수 있습니다. 다음을 수행합니다.

1. `https://[server]:[host]/system/console/configMgr`에 있는 AEM 웹 콘솔로 이동합니다.
1. **[!UICONTROL AEM Forms 데이터 통합 - 사용자 프로필 커넥터 구성]**&#x200B;을 찾고 탭하여 편집 모드에서 구성을 엽니다.
1. 사용자 프로필 커넥터 구성 대화 상자에서 사용자 프로필 속성을 추가, 제거 또는 업데이트할 수 있습니다. 지정한 속성은 양식 데이터 모델에서 사용할 수 있습니다. 사용자 프로필 속성을 지정하려면 다음 형식을 사용하십시오.

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   예:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >위의 예에서 **&amp;ast;**&#x200B;는 CRXDE 구조의 AEM 사용자 프로필에서 `profile/empLocation/` 노드 아래의 모든 노드를 나타냅니다. 즉, 양식 데이터 모델은 `profile/empLocation/` 노드 아래의 노드에 있는 `string` 유형의 `city` 속성에 액세스할 수 있습니다. 그러나 지정된 속성이 포함된 노드는 일관된 구조를 따라야 합니다.

1. **[!UICONTROL 저장]**&#x200B;을 눌러 구성을 저장합니다.

## 클라우드 서비스 구성 {#cloud-folder} 폴더 구성

>[!NOTE]
>
>RESTful, SOAP 및 OData 서비스에 대한 클라우드 서비스를 구성하려면 클라우드 서비스 폴더를 구성해야 합니다.

AEM의 모든 클라우드 서비스 구성은 AEM 저장소의 `/conf` 폴더에 통합됩니다. 기본적으로 `conf` 폴더에는 클라우드 서비스 구성을 만들 수 있는 `global` 폴더가 포함되어 있습니다. 그러나 클라우드 구성에 대해서는 수동으로 활성화해야 합니다. `conf`에서 추가 폴더를 만들어 클라우드 서비스 구성을 만들고 구성할 수도 있습니다.

클라우드 서비스 구성에 대한 폴더를 구성하려면 다음을 수행하십시오.

1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   * 자세한 내용은 [구성 브라우저 설명서](/help/sites-administering/configurations.md)를 참조하십시오.
1. 클라우드 구성에 대한 글로벌 폴더를 활성화하려면 다음을 수행하십시오. 또는 이 단계를 건너뛰고 클라우드 서비스 구성에 대한 다른 폴더를 만들고 구성하려면 다음을 수행하십시오.

   1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 `global` 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 탭합니다.
   1. **[!UICONTROL 구성 속성]** 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 활성화합니다.
   1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 눌러 구성을 저장하고 대화 상자를 종료합니다.

1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.
1. **[!UICONTROL 구성 만들기]** 대화 상자에서 폴더의 제목을 지정하고 **[!UICONTROL 클라우드 구성]**&#x200B;을 활성화합니다.
1. 클라우드 서비스 구성에 대해 활성화된 폴더를 만들려면 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.

## RESTful 웹 서비스 구성 {#configure-restful-web-services}

RESTful 웹 서비스는 Swagger 정의 파일에서 JSON 또는 YAML 형식의 [Swagger 사양](https://swagger.io/specification/)을 사용하여 설명합니다. AEM 클라우드 서비스에서 RESTful 웹 서비스를 구성하려면 파일 시스템에 Swagger 파일 또는 파일이 호스팅되는 URL이 있는지 확인합니다.

RESTful 서비스를 구성하려면 다음을 수행하십시오.

1. **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**&#x200B;로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 탭합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법은 [클라우드 서비스 구성을 위한 폴더 구성](/help/forms/using/configure-data-sources.md#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;데이터 소스 구성 만들기 대화 상자&#x200B;]**를 엽니다.**[!UICONTROL  구성 이름과 선택적으로 구성 제목을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL RESTful 서비스]**&#x200B;를 선택하고, 선택적으로 구성에 대한 축소판 이미지를 찾아 선택한 다음, **[!UICONTROL 다음]**&#x200B;을 누릅니다.
1. RESTful 서비스에 대해 다음 세부 정보를 지정합니다.

   * Swagger 소스 드롭다운에서 URL 또는 파일 을 선택하고 그에 따라 Swagger 정의 파일에 Swagger URL을 지정하거나 로컬 파일 시스템에서 Swagger 파일을 업로드합니다.
   * 인증 유형(없음, OAuth2.0, 기본 인증, API 키 또는 사용자 지정 인증)을 선택하여 RESTful 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 눌러 RESTful 서비스에 대한 클라우드 구성을 만듭니다.

## SOAP 웹 서비스 구성 {#configure-soap-web-services}

SOAP 기반 웹 서비스는 [WSDL(Web Services Description Language) 사양](https://www.w3.org/TR/wsdl)을 사용하여 설명합니다. AEM 클라우드 서비스에서 SOAP 기반 웹 서비스를 구성하려면 웹 서비스용 WSDL URL이 있는지 확인하고 다음을 수행하십시오.

1. **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**&#x200B;로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 탭합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법은 [클라우드 서비스 구성을 위한 폴더 구성](/help/forms/using/configure-data-sources.md#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;데이터 소스 구성 만들기 대화 상자&#x200B;]**를 엽니다.**[!UICONTROL  구성 이름과 선택적으로 구성 제목을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL SOAP 웹 서비스]**&#x200B;를 선택하고, 선택적으로 구성에 대한 축소판 이미지를 찾아 선택한 다음, **[!UICONTROL 다음]**&#x200B;을 누릅니다.
1. SOAP 웹 서비스에 대해 다음을 지정합니다.

   * 웹 서비스의 WSDL URL입니다.
   * 서비스 엔드포인트. WSDL에 언급된 서비스 끝점을 무시하려면 이 필드에 값을 지정하십시오.
   * 인증 유형(없음, OAuth2.0, 기본 인증, 사용자 지정 인증 또는 X509 토큰)을 선택하여 SOAP 서비스에 액세스하고 그에 따라 인증 세부 사항을 제공합니다.

      X509 토큰을 인증 유형으로 선택하는 경우 X509 인증서를 구성합니다. 자세한 내용은 [인증서 설정](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service)을 참조하십시오.
**[!UICONTROL 키 별칭]** 필드에서 X509 인증서에 대한 KeyStore 별칭을 지정합니다. 인증 요청이 유효한 상태로 유지될 때까지 **[!UICONTROL Time To Live]** 필드에 시간을 초 단위로 지정합니다. 선택적으로, 메시지 본문 또는 타임스탬프 헤더에 서명하거나 둘 다에 서명하도록 선택합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 탭하여 SOAP 웹 서비스에 대한 클라우드 구성을 만듭니다.

## OData 서비스 구성 {#config-odata}

OData 서비스는 서비스 루트 URL로 식별됩니다. AEM 클라우드 서비스에서 OData 서비스를 구성하려면 서비스에 대한 서비스 루트 URL이 있는지 확인하고 다음을 수행하십시오.

>[!NOTE]
>
>Microsoft Dynamics 365, 온라인 또는 온프레미스를 구성하는 단계별 안내서는 [Microsoft Dynamics OData 구성](/help/forms/using/ms-dynamics-odata-configuration.md)을 참조하십시오.

1. **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**&#x200B;로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 탭합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법은 [클라우드 서비스 구성을 위한 폴더 구성](/help/forms/using/configure-data-sources.md#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;데이터 소스 구성 만들기 대화 상자&#x200B;]**를 엽니다.**[!UICONTROL  구성 이름과 선택적으로 구성 제목을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL OData 서비스]**&#x200B;를 선택하고, 선택적으로 구성에 대한 축소판 이미지를 찾아 선택한 다음, **[!UICONTROL 다음]**&#x200B;을 누릅니다.
1. OData 서비스에 대해 다음 세부 정보를 지정합니다.

   * 구성할 OData 서비스의 서비스 루트 URL입니다.
   * 인증 유형(없음, OAuth2.0, 기본 인증 또는 사용자 지정 인증)을 선택하여 OData 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공합니다.

   >[!NOTE]
   >
   >OData 끝점을 서비스 루트로 사용하여 Microsoft Dynamics 서비스와 연결하려면 OAuth 2.0 인증 유형을 선택해야 합니다.

1. **만들기**&#x200B;를 눌러 OData 서비스에 대한 클라우드 구성을 만듭니다.

## 다음 단계 {#next-steps}

데이터 소스를 구성했습니다. 다음으로 양식 데이터 모델을 만들거나 데이터 소스 없이 양식 데이터 모델을 이미 만든 경우 방금 구성한 데이터 소스와 연결할 수 있습니다. 자세한 내용은 [양식 데이터 모델 만들기](/help/forms/using/create-form-data-models.md)를 참조하십시오.
