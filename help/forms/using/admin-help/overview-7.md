---
title: 양식 구성 기본 사항
seo-title: 양식 구성 기본 사항
description: 대화형 데이터 캡처 응용 프로그램을 만드는 데 도움이 되는 다양한 양식 서비스에 대해 알아봅니다.
seo-description: 대화형 데이터 캡처 응용 프로그램을 만드는 데 도움이 되는 다양한 양식 서비스에 대해 알아봅니다.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 616cd550-c3bd-4daf-887d-0470f1b08389
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# 양식 구성 기본 사항 {#basics-of-configuring-forms}

Forms 서비스를 사용하면 일반적으로 Designer에서 만든 양식의 유효성 검사, 처리, 변환 및 전달을 수행하는 대화형 데이터 캡처 클라이언트 응용 프로그램을 만들 수 있습니다. 양식 작성자는 Forms 서비스가 다양한 형식으로 렌더링하는 단일 양식 디자인을 개발할 수 있습니다.

* Adobe Reader 또는 브라우저에서 PDF로 사용
* 호환 XHTML 1.0 렌더링을 포함하여 다양한 브라우저 환경에서 HTML로 사용
* Adobe Flash Player을 지원하는 다양한 브라우저 환경에서 양식 안내서로서 사용할 수 있습니다.

Forms 서비스에 대한 자세한 내용은 [서비스 참조](https://www.adobe.com/go/learn_aemforms_services_63)를 참조하십시오.

관리 콘솔에서 Forms 페이지를 사용하여 Forms 서비스의 동작을 구성할 수 있습니다. 이러한 설정은 서비스의 모든 호출에 적용됩니다. AEM Forms SDK를 통해 전송된 모든 매개 변수는 관리 콘솔에 설정된 설정을 덮어씁니다.그러나 특정 호출에만 영향을 줍니다.

관리 콘솔에서 Forms 설정을 변경한 후 저장을 클릭합니다. 변경 사항을 적용하려면 서버를 다시 시작할 필요가 없습니다. 그러나 캐시 모드 설정을 구성할 때 Forms 서비스를 중지하고 다시 시작해야 할 수 있습니다. ( [서비스 시작 및 중지](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services)를 참조하십시오.)
