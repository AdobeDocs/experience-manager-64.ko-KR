---
title: 데이터베이스 증가 최소화 팁
seo-title: Tips for minimizing database growth
description: 장기 처리 프로세스는 AEM Forms 데이터베이스에 프로세스 데이터를 저장합니다. 몇 가지 간단한 프로세스 설계 및 제품 구성 전략을 사용하여 AEM Forms 데이터베이스의 증가를 최소화할 수 있습니다.
seo-description: Long-lived processes store process data in the AEM forms database. The growth of the AEM forms database can be minimized using a few easy process design and product configuration strategies.
uuid: 13f99d4f-848e-451e-90d9-55e202dc0bdb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 89441336-babc-4d1f-9053-d1566cd42d22
exl-id: 7b266170-c7e2-42e7-8ee0-153e1e73a901
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# 데이터베이스 증가 최소화 팁 {#tips-for-minimizing-database-growth}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

장기 처리 프로세스는 AEM Forms 데이터베이스에 프로세스 데이터를 저장합니다. 몇 가지 간단한 프로세스 설계 및 제품 구성 전략을 사용하여 AEM Forms 데이터베이스의 증가를 최소화할 수 있습니다.

## 프로세스 디자인 팁 {#process-design-tips}

가능한 한 단기 프로세스를 사용하십시오. 단기 프로세스가 데이터베이스에 프로세스 데이터를 저장하지 않습니다. 단기 프로세스를 사용할 때의 단점은 상태 및 상태가 관리 콘솔에서 추적되지 않고 프로세스 내역이 없다는 것입니다.

작업 할당 작업(사용자 서비스)과 같은 일부 서비스 작업은 장기 처리 프로세스에서 사용되어야 합니다. 이 경우 프로세스를 여러 하위 프로세스로 세그먼트화하고 가능한 경우 단기 체류자로 만들 수 있습니다. 이 전략을 사용하는 경우 단기 하위 프로세스는 문서 값과 같은 큰 데이터 항목을 처리해야 합니다.

변수를 드물게 사용합니다. 긴 기간 프로세스를 사용할 때 모든 프로세스 인스턴스에 대해 프로세스 내의 각 변수에 대해 데이터베이스에 공간이 할당됩니다. 변수를 전략적으로 사용하면 상당한 공간을 절약할 수 있다. 예를 들어 프로세스에서 이전 값이 더 이상 필요하지 않으면 변수 값을 덮어쓸 수 있습니다. 만들고 사용하지 않는 변수를 모두 삭제합니다. 프로세스의 유효성을 검사하여 사용하지 않는 변수를 찾을 수 있습니다.

간단한 변수 유형(예: 문자열 또는 int)을 사용하고 가능한 경우 복잡한 변수 유형을 사용하지 마십시오. 데이터베이스 공간은 값이 포함되지 않더라도 변수에 할당됩니다. 복잡한 변수는 일반적으로 단순 변수보다 더 많은 공간을 필요로 합니다.

## 제품 관리 팁 {#product-administration-tips}

GDS(글로벌 문서 스토리지)를 효과적으로 사용 Forms 서버의 GDS 디렉토리는 프로세스에서 AEM Forms의 일부인 서비스에 전달되는 파일을 저장하는 데 사용됩니다. 성능을 향상시키기 위해 더 작은 문서가 대신 메모리에 저장되어 데이터베이스에 유지됩니다.

관리 콘솔은 메모리에 저장되고 데이터베이스에 지속되는 문서의 최대 크기를 구성하기 위한 [기본 문서 최대 인라인 크기] 속성을 표시합니다. (자세한 내용은 [일반 AEM 양식 설정 구성](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)) 이 속성을 낮은 값으로 설정하면 대부분의 문서가 데이터베이스 대신 GDS 디렉토리에 유지됩니다. 따라서 GDS 디렉토리에 파일을 저장할 때 더 이상 필요하지 않은 파일을 보다 쉽게 삭제할 수 있습니다.
