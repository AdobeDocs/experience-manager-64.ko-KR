---
title: PDF 생성기 백업 제한 사항
seo-title: PDF Generator backup limitations
description: PDF 생성기 백업 제한 사항에 대해 알아봅니다.
seo-description: Learn about PDF Generator backup limitations.
uuid: 9537ffde-4396-46d1-81ea-edcd25923ffb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 23386353-b2bf-49f1-947a-dd7587bba175
noindex: true
exl-id: d2ba9881-02b6-470b-b110-7d4609e6ab24
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 8%

---

# PDF 생성기 백업 제한 사항 {#pdf-generator-backup-limitations}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

PDF 생성기가 파일 변환에 사용하는 임시 디렉터리를 백업할 수 없습니다. 서비스가 제대로 복원되더라도 PDF 생성기가 설정된 간격으로 임시 디렉터리의 내용을 검토하고 지우므로 데이터가 손실될 수 있습니다.
