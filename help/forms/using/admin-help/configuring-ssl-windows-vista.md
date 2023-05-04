---
title: Windows Vista에서 SSL 구성
seo-title: Configuring SSL on Windows Vista
description: Windows Vista에서 SSL을 구성하는 방법을 알아봅니다.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 4%

---

# Windows Vista에서 SSL 구성 {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Windows Vista™에서 SSL을 구성하려면 인증에 RSA 키가 있는 SSL 인증서가 필요합니다. Java 키 도구를 사용하여 인증서를 만들 수 있습니다.

>[!NOTE]
>
>Windows Vista가 DSA 키와 함께 작동하지 않습니다.

인증서 및 키 저장소를 만드는 데 필요한 모든 정보를 포함하는 단일 명령을 사용하여 키 도구를 실행할 수 있습니다.

**SSL 인증서 만들기**

1. 명령 프롬프트에서 다음 위치로 이동합니다. *[JAVA 홈]*/bin 및 다음 명령을 입력하여 인증서 및 키 저장소를 만듭니다.

   `keytool -genkey -keyalg RSA -dname "CN=`*호스트 이름* `, OU=`*그룹 이름* `, O=`*회사 이름* `,L=`*구/군/시******Name* `, S=`*주/도* `, C=`*국가 코드* `" -alias`*&quot;LC 인증서&quot;* `-keypass` `*key*`*_**암호* `-keystore`*keystorname* `.keystore`

   >[!NOTE]
   >
   >바꾸기 *[JAVA_HOME] jdk가 설치된 디렉토리로 이동하여 기울임꼴로 표시된 텍스트를 환경에 해당하는 값으로 바꿉니다.*

1. 유형 `changeit` 를 암호로 사용하십시오. 이 암호는 Java 설치의 기본값이며 시스템 관리자가 변경했을 수 있습니다.
