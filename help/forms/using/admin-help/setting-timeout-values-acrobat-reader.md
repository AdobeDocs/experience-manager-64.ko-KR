---
title: Acrobat Reader DC 확장에 사용할 시간 초과 값 설정
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: Acrobat Reader DC 확장에서 사용할 시간 초과 값을 설정하는 방법을 알아봅니다.
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 3%

---

# Acrobat Reader DC 확장에 사용할 시간 초과 값 설정  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Acrobat Reader DC 확장의 많은 PDF 파일에서 작업할 경우 작업이 시간 초과와 실패를 방지하기 위해 다음 시간 초과 값이 적절히 설정되어 있는지 확인하십시오.

**문서 처리 시간 초과**

이 값은 관리 콘솔에서 설정할 수 있습니다. 설정 > 핵심 시스템 설정 > 구성 을 클릭하고 기본 문서 처리 시간 초과에 대한 값을 지정합니다.

**User Manager AEM Forms Timeout:** 이 값은 config.xml 파일을 편집하여 설정할 수 있습니다. 관리 콘솔에서 설정 > 사용자 관리 > 구성 > 구성 파일 가져오기 및 내보내기를 클릭한 다음 내보내기를 클릭합니다. 내보낸 config.xml 파일을 열고 다음 줄을 편집합니다.

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

저장 후 config.xml 파일을 다시 관리 콘솔로 가져옵니다.

**응용 프로그램 서버 세션 시간 초과:** 이 값은 애플리케이션 서버에서 설정할 수 있습니다. 자세한 내용은 애플리케이션 서버와 함께 제공된 설명서를 참조하십시오.
