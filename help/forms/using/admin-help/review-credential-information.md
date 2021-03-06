---
title: 자격 증명 사용 정보 검토
seo-title: 자격 증명 사용 정보 검토
description: 자격 증명 사용 정보를 검토하는 방법을 알아봅니다.
seo-description: 자격 증명 사용 정보를 검토하는 방법을 알아봅니다.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 자격 증명 사용 정보 검토 {#review-credential-use-information}

자격 증명에는 Acrobat Reader DC 확장 최종 사용자 웹 애플리케이션을 통해 액세스할 수 있는 용도를 설명하는 정보가 포함되어 있습니다. 이 정보를 사용하여 설치된 자격 증명 유형(평가 또는 프로덕션)과 해당 유효 날짜를 결정할 수 있습니다.

1. 웹 브라우저를 열고 다음 URL을 입력합니다.

   http://localhost:*[port]*/ReaderExtensions(여기서 *[port]*&#x200B;는 애플리케이션 서버의 포트 번호입니다.)

1. 기본 사용자 이름과 암호를 사용하여 로그인합니다.

   사용자 이름:관리자

   암호:암호

   >[!NOTE]
   >
   >기본 사용자 이름과 암호를 사용하여 로그인하려면 관리자 또는 수퍼 사용자 권한이 있어야 합니다. 다른 사용자가 Acrobat Reader DC 확장에 액세스할 수 있도록 하려면 사용자 관리에서 사용자 계정을 만들고 사용자에게 Acrobat Reader DC 확장 웹 애플리케이션 역할을 부여합니다.

1. 자격 증명 선택 목록에서 자격 증명 별칭을 선택하고 만료 날짜 및 사용 예정 통지에 포함된 정보를 검토합니다.

>[!NOTE]
>
>자격 증명의 만료 날짜는 관리 콘솔의 설정 > 신뢰 저장소 관리 > 로컬 자격 증명 페이지에서 만료 날짜도 사용할 수 있습니다.
