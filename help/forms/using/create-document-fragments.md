---
title: "자습서: 문서 조각 만들기"
seo-title: Create document fragments for Interactive Communication
description: 대화형 커뮤니케이션용 문서 조각 만들기
seo-description: Create document fragments for Interactive Communication
uuid: 215d09a6-949c-45ef-b2b0-88cd0cb4b99c
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9b78e2b-af7d-49d7-b37f-c96ec732015e
feature: Interactive Communication
exl-id: 50d93998-6393-4607-b89b-5b97aad530a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1719'
ht-degree: 2%

---

# 자습서: 문서 조각 만들기 {#tutorial-create-document-fragments}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

대화형 커뮤니케이션용 문서 조각 만들기

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

이 자습서는 [첫 번째 대화형 통신 만들기](/help/forms/using/create-your-first-interactive-communication.md) 시리즈. 전체 자습서 사용 사례를 이해하고, 수행하고, 시연하기 위해 시리즈를 시간 순서대로 따르는 것이 좋습니다.

문서 조각은 대화형 커뮤니케이션을 작성하는 데 사용되는 서신의 재사용 가능한 구성 요소입니다. 문서 조각은 다음 유형의 조각입니다.

* 텍스트 - 텍스트 자산은 하나 이상의 텍스트 단락으로 구성된 컨텐츠의 일부입니다. 단락은 정적 또는 동적일 수 있습니다.
* 목록 - 목록은 텍스트, 목록, 조건 및 이미지를 포함한 문서 조각 그룹입니다.
* 조건 - 조건을 사용하면 양식 데이터 모델에서 수신한 데이터를 기반으로 Interactive Communication에 포함되는 컨텐츠를 정의할 수 있습니다.

이 튜토리얼에서는 다음을 통해 제공된 해부학을 기반으로 여러 텍스트 문서 조각을 만드는 단계를 안내합니다. [대화형 통신 계획](/help/forms/using/planning-interactive-communications.md) 섹션을 참조하십시오. 이 자습서를 마치면 다음을 수행할 수 있습니다.

* 문서 조각 만들기
* 변수 만들기
* 규칙 만들기 및 적용

![text_document_fragments](assets/text_document_fragments.gif)

다음은 이 자습서에서 만든 문서 조각 목록입니다.

* [청구서 세부 사항](/help/forms/using/create-document-fragments.md#step-create-bill-details-text-document-fragment)
* [고객 세부 사항](/help/forms/using/create-document-fragments.md#step-create-customer-details-text-document-fragment)
* [청구서 요약](/help/forms/using/create-document-fragments.md#step-create-bill-summary-text-document-fragment)
* [비용 요약](/help/forms/using/create-document-fragments.md#step-create-summary-of-charges-text-document-fragment)

각 문서 조각에는 정적 텍스트, 양식 데이터 모델에서 수신된 데이터 및 에이전트 UI를 사용하여 입력한 데이터가 있는 필드가 포함됩니다. 이러한 모든 필드는 [대화형 통신 계획](/help/forms/using/planning-interactive-communications.md) 섹션을 참조하십시오.

이 자습서에서 문서 조각을 만드는 동안 에이전트 UI를 사용하여 데이터를 받는 필드에 대한 변수가 만들어집니다.

사용 **FDM_Create_First_IC**&#x200B;에 설명된 대로 [양식 데이터 모델 만들기](create-form-data-model-tutorial.md) 섹션을 참조하십시오.

## 1단계: BOM 상세내역 텍스트 문서 조각 생성 {#step-create-bill-details-text-document-fragment}

BOM 상세내역 문서 조각에는 다음 필드가 포함됩니다.

| 필드 | 데이터 소스 |
|---|---|
| 송장 번호 | 에이전트 UI |
| 청구 기간 | 에이전트 UI |
| 청구서 날짜 | 에이전트 UI |
| 플랜 | 양식 데이터 모델 |

다음 단계를 실행하여 에이전트 UI를 데이터 소스로 사용하는 필드에 대한 변수를 만들고 정적 텍스트를 생성하고 문서 조각에서 양식 데이터 모델 요소를 사용합니다.

1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL 문서 조각]**.

1. 선택 **만들기** > **텍스트**.
1. 다음 정보를 지정합니다.

   1. Enter 키 **bill_details_first_ic** 의 이름으로 **제목** 필드. 제목은 **이름** 필드.
   1. 선택 **양식 데이터 모델** 에서 **데이터 모델** 섹션을 참조하십시오.
   1. 선택 **FDM_Create_First_IC** 양식 데이터 모델로 사용 및 탭하기 **선택**.
   1. 탭 **다음**.

1. 을(를) 선택합니다 **변수** 왼쪽 창에서 탭을 선택하고 를 누릅니다 **만들기**.
1. 에서 **변수 만들기** 섹션:

   1. Enter 키 **송장 번호** 를 변수 이름으로 지정합니다.
   1. 선택 **문자열** 유형으로 사용할 수 있습니다.
   1. 탭 **만들기**.

   ![variable_create_string](assets/variable_create_string.png)

   4~5단계를 반복하여 다음 변수를 만듭니다.

   * 청구 기간: 문자열 유형
   * 청구 일자: 날짜 유형

   ![variables_bill_details](assets/variables_bill_details.png)

1. 오른쪽 창을 사용하여 다음 필드에 대한 정적 텍스트를 만듭니다.

   * 송장 번호
   * 청구 기간
   * 청구서 날짜
   * 플랜

   ![variable_bom_details_static_text](assets/variable_bill_details_static_text.png)

1. 커서를 **송장 번호** 필드를 선택하고 두 번 클릭합니다 **송장 번호** 변수의 **변수** 왼쪽 창에서 탭을 클릭합니다.
1. 커서를 **청구 기간** 필드를 선택하고 두 번 클릭합니다 **청구 기간** 변수를 채우는 방법을 설명합니다.
1. 커서를 **청구서 날짜** 필드를 선택하고 두 번 클릭합니다 **청구서 날짜** 변수를 채우는 방법을 설명합니다.
1. 을(를) 선택합니다 **데이터 모델 개체** 왼쪽 창에서 탭을 클릭합니다.
1. 커서를 **플랜** 필드를 선택하고 두 번 클릭합니다 **고객** > **customerplan** 속성을 사용합니다.

   ![bill_details_customerplan_fdm](assets/bill_details_customerplan_fdm.png)

1. 클릭 **저장** 청구 상세내역 텍스트 문서 조각을 생성하려면

## 2단계: 고객 세부 사항 텍스트 문서 조각 만들기 {#step-create-customer-details-text-document-fragment}

고객 세부 사항 문서 조각에는 다음 필드가 포함되어 있습니다.

| 필드 | 데이터 소스 |
|---|---|
| 고객 이름 | 양식 데이터 모델 |
| 주소 | 양식 데이터 모델 |
| 공급 장소 | 에이전트 UI |
| 상태 코드 | 에이전트 UI |
| 모바일 번호 | 양식 데이터 모델 |
| 대체 연락처 번호 | 양식 데이터 모델 |
| 관계 번호 | 양식 데이터 모델 |
| 연결 수 | 에이전트 UI |

다음 단계를 실행하여 에이전트 UI를 데이터 소스로 사용하는 필드에 대한 변수를 만들고 정적 텍스트를 생성하고 문서 조각에서 양식 데이터 모델 요소를 사용합니다.

1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL 문서 조각]**.
1. 선택 **만들기** > **텍스트**.
1. 다음 정보를 지정합니다.

   1. Enter 키 **customer_details_first_ic** 의 이름으로 **제목** 필드. 제목은 **이름** 필드.
   1. 선택 **양식 데이터 모델** 에서 **데이터 모델** 섹션을 참조하십시오.
   1. 선택 **FDM_Create_First_IC** 양식 데이터 모델로 사용 및 탭하기 **선택**.
   1. 탭 **다음**.

1. 을(를) 선택합니다 **변수** 왼쪽 창에서 탭을 선택하고 를 누릅니다 **만들기**.
1. 에서 **변수 만들기** 섹션:

   1. Enter 키 **배치 공급** 를 변수 이름으로 지정합니다.
   1. 선택 **문자열** 유형으로 사용할 수 있습니다.
   1. 탭 **만들기**.

   4~5단계를 반복하여 다음 변수를 만듭니다.

   * 상태 코드: 숫자 유형
   * 번호 연결: 숫자 유형


1. 을(를) 선택합니다 **데이터 모델 개체** 탭을 클릭하고 오른쪽 창에 커서를 놓고 **고객** > **이름** 속성을 사용합니다.
1. Enter 키를 눌러 다음 행으로 커서를 이동하고 **고객** > **주소** 속성을 사용합니다.
1. 오른쪽 창을 사용하여 다음 필드에 대한 정적 텍스트를 만듭니다.

   * 모바일 번호
   * 대체 연락처 번호
   * 공급 장소
   * 관계 번호
   * 상태 코드
   * 연결 수

   ![customer_details_static_text_fdm](assets/customer_details_static_text_fdm.png)

1. 커서를 **모바일 번호** 필드를 선택하고 두 번 클릭합니다 **고객** > **mobilenum** 속성을 사용합니다.
1. 커서를 **대체 연락처 번호** 필드를 선택하고 두 번 클릭합니다 **고객** > **alternentobilenumber** 속성을 사용합니다.
1. 커서를 **관계 번호** 필드를 선택하고 두 번 클릭합니다 **고객** > **관계 번호** 속성을 사용합니다.
1. 을(를) 선택합니다 **변수** 탭에서 **공급 장소** 필드를 선택하고 두 번 클릭합니다 **배치 공급** 변수를 채우는 방법을 설명합니다.
1. 커서를 **상태 코드** 필드를 선택하고 두 번 클릭합니다 **상태 코드** 변수를 채우는 방법을 설명합니다.
1. 커서를 **연결 수** 필드를 선택하고 두 번 클릭합니다 **Numberconnections** 변수를 채우는 방법을 설명합니다.

   ![customer_details_df2](assets/customer_details_df2.png)

1. 클릭 **저장** 고객 세부 사항 텍스트 문서 조각을 만들려면

## 3단계: 청구 요약 텍스트 문서 조각 생성 {#step-create-bill-summary-text-document-fragment}

BOM 요약 문서 조각은 다음 필드를 포함합니다.

| 필드 | 데이터 소스 |
|---|---|
| 이전 잔액 | 에이전트 UI |
| 결제 | 에이전트 UI |
| 조정 | 에이전트 UI |
| 현재 청구 기간 | 양식 데이터 모델 |
| 만기 금액 | 에이전트 UI |
| 기한 | 에이전트 UI |

다음 단계를 실행하여 에이전트 UI를 데이터 소스로 사용하는 필드에 대한 변수를 만들고 정적 텍스트를 생성하고 문서 조각에서 양식 데이터 모델 요소를 사용합니다.

1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL 문서 조각]**.
1. 선택 **만들기** > **텍스트**.
1. 다음 정보를 지정합니다.

   1. Enter 키 **bill_summary_first_ic** 의 이름으로 **제목** 필드. 제목은 **이름** 필드.
   1. 선택 **양식 데이터 모델** 에서 **데이터 모델** 섹션을 참조하십시오.
   1. 선택 **FDM_Create_First_IC** 양식 데이터 모델로 사용 및 탭하기 **선택**.
   1. 탭 **다음**.

1. 을(를) 선택합니다 **변수** 왼쪽 창에서 탭을 선택하고 를 누릅니다 **만들기**.
1. 에서 **변수 만들기** 섹션:

   1. Enter 키 **이전 잔액** 를 변수 이름으로 지정합니다.
   1. 선택 **숫자** 유형으로 사용할 수 있습니다.
   1. 탭 **만들기**.

   4~5단계를 반복하여 다음 변수를 만듭니다.

   * 결제: 숫자 유형
   * 조정: 숫자 유형
   * 금액: 숫자 유형
   * 중복: 날짜 유형


1. 오른쪽 창을 사용하여 다음 필드에 대한 정적 텍스트를 만듭니다.

   * 이전 잔액
   * 결제
   * 조정
   * 현재 청구 기간
   * 만기 금액
   * 기한
   * 만기 일자 이후의 연체료: $20

   ![bill_summary_static](assets/bill_summary_static.png)

1. 커서를 **이전 잔액** 필드를 선택하고 두 번 클릭합니다 **이전 잔액** 변수를 채우는 방법을 설명합니다.
1. 커서를 **결제** 필드를 선택하고 두 번 클릭합니다 **결제** 변수를 채우는 방법을 설명합니다.
1. 커서를 **조정** 필드를 선택하고 두 번 클릭합니다 **조정** 변수를 채우는 방법을 설명합니다.
1. 커서를 **만기 금액** 필드를 선택하고 두 번 클릭합니다 **Amountdue** 변수를 채우는 방법을 설명합니다.
1. 커서를 **기한** 필드를 선택하고 두 번 클릭합니다 **듀드** 변수를 채우는 방법을 설명합니다.
1. 을(를) 선택합니다 **데이터 모델 개체** 탭에서 **현재 청구 기간** 오른쪽 창의 필드를 두 번 클릭하고 **청구서** > **usagechards** 속성을 사용합니다.

   ![bill_summary_static_variables](assets/bill_summary_static_variables.png)

1. 클릭 **저장** 고객 세부 사항 텍스트 문서 조각을 만들려면

## 4단계: 비용 요약 작성 텍스트 문서 조각 {#step-create-summary-of-charges-text-document-fragment}

비용 문서 조각의 요약에는 다음 필드가 포함됩니다.

| 필드 | 데이터 소스 |
|---|---|
| 전화 요금 | 양식 데이터 모델 |
| 전화 회의 요금 | 양식 데이터 모델 |
| SMS 요금 | 양식 데이터 모델 |
| 모바일 인터넷 요금 | 양식 데이터 모델 |
| 국가 로밍 요금 | 양식 데이터 모델 |
| 국제 로밍 요금 | 양식 데이터 모델 |
| 부가 서비스 요금 | 양식 데이터 모델 |
| 총 요금 | 양식 데이터 모델 |
| AP 총액 | 양식 데이터 모델 |

다음 단계를 실행하여 정적 텍스트를 생성하고 문서 조각에서 양식 데이터 모델 요소를 사용합니다.

1. 선택 **[!UICONTROL Forms]** > **[!UICONTROL 문서 조각]**.
1. 선택 **만들기** > **텍스트**.
1. 다음 정보를 지정합니다.

   1. Enter 키 **summary_charts_first_ic** 의 이름으로 **제목** 필드. 이름 필드에 제목이 자동으로 채워집니다.
   1. 선택 **양식 데이터 모델** 에서 **데이터 모델** 섹션을 참조하십시오.
   1. 선택 **FDM_Create_First_IC** 양식 데이터 모델로 사용 및 탭하기 **선택**.
   1. 탭 **다음**.

1. 오른쪽 창을 사용하여 다음 필드에 대한 정적 텍스트를 만듭니다.

   * 전화 요금
   * 전화 회의 요금
   * SMS 요금
   * 모바일 인터넷 요금
   * 국가 로밍 요금
   * 국제 로밍 요금
   * 부가 서비스 요금
   * 총 요금
   * AP 총액

   ![summary_charge_static](assets/summary_charges_static.png)

1. 을(를) 선택합니다 **데이터 모델 개체** 탭.
1. 커서를 **전화 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **통화 요금** 속성을 사용합니다.
1. 커서를 **전화 회의 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **고충** 속성을 사용합니다.
1. 커서를 **SMS 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **smschars** 속성을 사용합니다.
1. 커서를 **모바일 인터넷 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **인터네트전하** 속성을 사용합니다.
1. 커서를 **국가 로밍 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **로아밍국립** 속성을 사용합니다.
1. 커서를 **국제 로밍 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **roamingintnl** 속성을 사용합니다.
1. 커서를 **부가 서비스 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **vas** 속성을 사용합니다.
1. 커서를 **총 요금** 필드를 선택하고 두 번 클릭합니다 **청구서** > **usagechards** 속성을 사용합니다.
1. 커서를 **AP 총액** 필드를 선택하고 두 번 클릭합니다 **청구서** > **usagechards** 속성을 사용합니다.

   ![summary_charts_static_fdm](assets/summary_charges_static_fdm.png)

1. 에서 텍스트를 선택합니다 **부가 서비스 요금** 행 및 탭 **규칙 만들기** 대화형 커뮤니케이션에서 행이 표시되는 조건을 만들려면:
1. 설정 **규칙 만들기** 팝업 창:

   1. 선택 **데이터 모델 및 변수** 그리고 **청구서** > **통화 요금**.
   1. 선택 **보다 작음** 를 반환합니다.
   1. 선택 **숫자** 값을 다음으로 입력합니다. **60**.

   이 조건에 따라 통화 비용 필드의 값이 60보다 작은 경우에만 부가 서비스 비용 행이 표시됩니다.

   ![create_rules_caption](assets/create_rules_caption.gif)

1. 클릭 **저장** 비용 텍스트 문서 조각의 요약을 생성하려면
