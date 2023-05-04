---
title: 티저 및 전략
seo-title: Teasers and Strategies
description: 캠페인에서는 특정한 방문자 세그먼트를 관심사에 맞는 컨텐츠로 유도하기 위한 메커니즘으로 티저를 사용하는 경우가 많습니다. 특정 캠페인에 하나 이상의 티저가 정의됩니다.
seo-description: Campaigns often use teasers as a mechanism to entice a specific segment of the visitor population through to content focused on their interests. One or more teasers are defined for a specific campaign.
uuid: 496caa14-2e91-4544-b3fc-12e0fe0da88d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 86a31407-96a4-467c-9468-da4095ca38d5
exl-id: 311ffab4-8bc9-486b-9ca5-a958f13f16f8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 7%

---

# 티저 및 전략{#teasers-and-strategies}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

캠페인에서는 특정한 방문자 세그먼트를 관심사에 맞는 컨텐츠로 유도하기 위한 메커니즘으로 티저를 사용하는 경우가 많습니다. 특정 캠페인에 하나 이상의 티저가 정의됩니다.

>[!NOTE]
>
>Teaser 구성 요소는 AEM 6.2에서 더 이상 사용되지 않습니다.

* **브랜드 페이지** 는 웹 사이트의 캠페인 섹션에 저장됩니다. 브랜드에는 개별 캠페인이 포함되어 있습니다.

* **캠페인 페이지** 는 웹 사이트의 캠페인 섹션에 저장됩니다. 각 캠페인에는 개별 페이지가 있으며, 이 페이지에 티저 정의가 있습니다. 또한 컨테이너 또는 개요 페이지는 개별 Teaser 페이지에 대한 특정 정보 및 통계를 포함합니다.

AEM 내의 Teaser는 여러 부분으로 구성됩니다.

* **티저 페이지** 는 해당 캠페인 페이지에 저장되며 특정 캠페인에서 사용할 수 있는 티저 단락의 정의를 포함합니다. 이러한 정의는 Teaser 단락을 표시할 때 사용됩니다. 컨텐츠 변형을 포함하여, 변형 및 증폭 인수를 선택하는 데 사용할 세그먼트입니다.
* 다음 **티저 구성 요소** 즉시 사용 가능하며, 컨텐츠 페이지에 특정 Teaser 단락의 인스턴스를 만들 수 있습니다. 사이드킥에서 티저 구성 요소를 드래그한 다음 티저 정의를 지정하여 티저 단락을 직접 만들 수 있습니다. **참고:** Teaser 구성 요소는 AEM 6.2에서 더 이상 사용되지 않습니다.

* **티저 단락** 컨텐츠 페이지 내에 있는 티저의 실제 인스턴스입니다. 방문자 세그먼트를 관심사에 맞는 컨텐츠로 유도합니다.
* 특정 방문자 세그먼트에 중점을 둔 캠페인 콘텐츠를 보유하는 페이지입니다. 일반적으로 티저 단락은 방문자를 이러한 페이지로 유도합니다.

## 전략 {#strategies}

페이지에 Teaser 단락을 추가할 때는 **전략**.

지정된 세그먼트가 모두 성공적으로 해결되므로 여러 Teaser를 선택할 수 있습니다. 다음 **전략** 그런 다음 표시된 티저를 선택하는 데 사용되는 추가 기준을 지정합니다.

* **Clickstream 점수**&#x200B;는 방문자의 클라이언트 컨텍스트(방문자가 각 태그가 포함된 페이지를 얼마나 자주 클릭했는지 표시)에 포함된 태그 및 관련 태그 히트를 기반으로 합니다. 티저 페이지에 정의된 태그의 조회수가 비교됩니다.
* **Random**: &quot;random selection&quot; 페이지에 생성된 무작위 인수를 사용합니다. 이 인수를 [클라이언트 컨텍스트](/help/sites-administering/client-context.md).

* **첫 번째** 로 나열된 상태로 남아 있는 문제를 해결했습니다. 순서는 캠페인 컨테이너 페이지 내의 티저 순서와 같습니다.

다음 [증폭 인수](/help/sites-administering/campaign-segmentation.md#boost-factor) 세그먼트의 선택 부분에도 영향을 줍니다. 세그먼트 정의에 추가되어 상대적인 선택 가능성을 높이거나 낮추는 가중치입니다.

다양한 선택 기준의 프로세스 및 상호 관계를 예로 들 수 있습니다(티저가 필요한 대상에게 도달하도록 하는 데 사용할 수도 있는 메서드).

다음 세그먼트가 이미 만들어지고 각각의 증폭 인수를 지정한 경우

| 세그먼트 | 증폭 인수 |
|---|---|
| S1 | 0 |
| S2 | 0 |
| S3 | 10 |
| S4 | 30 |
| S5 | 0 |
| S6 | 100 |

그리고 다음 티저 정의를 사용합니다.

<table> 
 <tbody> 
  <tr> 
   <td>캠페인</td> 
   <td>티저</td> 
   <td>지정된 세그먼트</td> 
   <td>지정된 태그 </td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T1</td> 
   <td>S1, S2</td> 
   <td>비즈니스, 마케팅</td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T2 </td> 
   <td>S1</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T3</td> 
   <td>S3, S4</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T4</td> 
   <td>S2, S5</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T5</td> 
   <td>S1, S2, S6</td> 
   <td>마케팅</td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T6</td> 
   <td>S6</td> 
   <td>상업<br /> </td> 
  </tr> 
 </tbody> 
</table>

다음과 같은 방문자에게 적용합니다.

* **S1**, **S2** 및 **S6** 해결 성공

* 태그 **마케팅** 히트 수가 3개 있음
* 태그 **비즈니스** 히트가 6개 있음

결과:

* 일치 성공 - 티저에 지정된 세그먼트가 현재 방문자에 대해 성공적으로 확인됩니까?
* 증폭 인수 - 적용 가능한 모든 세그먼트의 가장 높은 증폭 인수
* clickstream 점수 - 적용 가능한 모든 태그 조회수에 대한 누적 합계

적절한 전략을 적용하기 전에 계산됩니다.

<table> 
 <tbody> 
  <tr> 
   <td>캠페인</td> 
   <td>티저</td> 
   <td>지정된 세그먼트</td> 
   <td>태그 </td> 
   <td>일치 성공?</td> 
   <td>결과 증폭 인수</td> 
   <td>결과 클릭스트림 점수 </td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T1</td> 
   <td>S1, S2</td> 
   <td>비즈니스, 마케팅</td> 
   <td>예</td> 
   <td>0</td> 
   <td>9</td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T2 </td> 
   <td>S1</td> 
   <td><br /> </td> 
   <td>예</td> 
   <td>0</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T3</td> 
   <td>S3, S4</td> 
   <td><br /> </td> 
   <td>아니요</td> 
   <td><br /> </td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T4</td> 
   <td>S2, S5</td> 
   <td><br /> </td> 
   <td>예<br /> </td> 
   <td>0<br /> </td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T5</td> 
   <td>S1, S2, S6</td> 
   <td>마케팅</td> 
   <td>예</td> 
   <td>100</td> 
   <td>3</td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T6</td> 
   <td>S6</td> 
   <td>상업</td> 
   <td>예</td> 
   <td>100</td> 
   <td>6 </td> 
  </tr> 
 </tbody> 
</table>

이러한 값은 다음에 따라 방문자에게 표시되는 티저를 결정하는 데 사용됩니다 **전략** teaser 단락에 적용됨:

<table> 
 <tbody> 
  <tr> 
   <td>전략</td> 
   <td>결과 티저</td> 
   <td>댓글</td> 
  </tr> 
  <tr> 
   <td>처음</td> 
   <td>T5</td> 
   <td>세그먼트가 모두 해결되므로 T5 및 T6만 고려됩니다 <i>및</i> 그들은 가장 높은 증폭 인자를 가지고 있습니다. 반환된 목록은 T5, T6 순서대로 있습니다. 따라서 T5가 선택되어 표시됩니다.</td> 
  </tr> 
  <tr> 
   <td>임의</td> 
   <td>T5 또는 T6</td> 
   <td>두 티저 모두 모두 해결된 세그먼트와 동일한 증폭 인수가 있습니다. 따라서 두 티저가 동일한 비율로 표시됩니다.</td> 
  </tr> 
  <tr> 
   <td>Clickstream 점수</td> 
   <td>T6</td> 
   <td><p>방문자에 대해 T1, T4, T5 및 T6의 세그먼트가 모두 해결됩니다. T5 및 T6의 증폭 인수가 높을수록 T1 및 T4가 제외됩니다. 마지막으로 Clickstream 점수가 더 높은 T6이 선택됩니다.</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>위의 해결 방법 이후에 여러 티저를 선택할 수 있는 경우 내부 선택(임의)에서 단일 티저를 선택하여 표시합니다.
>
>예를 들어 전략이 Clickstream 점수이고 T5의 Clickstream 점수가 T6(3이 아닌 6점)과 동일한 경우 내부 선택(임의)이 두 점수 중 하나를 선택하는 데 사용됩니다.

Teaser 페이지/단락은 특정 방문자 세그먼트를 관심사에 맞는 콘텐츠로 유도하는 데 사용됩니다. 방문자가 선택할 수 있는 다양한 옵션을 표시하거나 특정 방문자 세그먼트를 기반으로 하는 하나의 티저 단락만 표시할 수 있습니다. 예를 들어, 표시되는 티저 단락은 방문자의 나이에 따라 달라질 수 있습니다.

일반적으로 Teaser 페이지는 다음 Teaser 페이지로 대체될 때까지 특정 기간 동안 지속되는 임시 작업입니다.

브랜드 및 캠페인을 만든 후 티저 경험을 만들고 설정할 수 있습니다.

## 티저에 대한 터치포인트 만들기 {#creating-a-touchpoint-for-your-teaser}

>[!NOTE]
>
>Teaser 구성 요소는 AEM 6.2에서 더 이상 사용되지 않습니다.

1. 캠페인 페이지로 이어지는 티저 단락을 배치할 컨텐츠 페이지로 이동합니다.
1. 추가 **티저** 구성 요소(에서 사용 가능) **개인화** 사이드 킥의 섹션)을 포함합니다. 처음 만들면 캠페인 경로가 아직 구성되지 않았다고 표시됩니다.

   ![chlimage_1-4](assets/chlimage_1-4.png)

1. 티저 구성 요소를 편집하여 다음을 추가합니다.

   * **캠페인 경로**
개별 Teaser 페이지를 포함하는 캠페인 페이지의 경로입니다. 세그먼트는 표시되는 티저를 정확히 결정합니다.
   * **[전략](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#strategies)**
여러 세그먼트가 성공적으로 해결된 경우에 사용할 선택 방법입니다.
   ![chlimage_1-5](assets/chlimage_1-5.png)

1. 클릭 **확인** 저장 Teaser에 설정한 세그먼트와 현재 로그인한 사용자의 프로필에 따라 적절한 컨텐츠가 표시됩니다.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 티저 단락 위로 마우스를 가져가면 물음표 아이콘(구성 요소의 오른쪽 아래 모서리)이 표시됩니다. 적용된 세그먼트와 현재 해결 여부를 보려면 이 아이콘을 클릭하십시오.

   ![chlimage_1-7](assets/chlimage_1-7.png)

## Teaser 개요 {#teaser-overview}

MCM의 캠페인 보기와 여기에 연결된 티저에 대한 정보도 캠페인 페이지에 제공합니다.

1. 에서 **웹 사이트** 콘솔에서 캠페인 페이지를 엽니다. 예:

   `http://localhost:4502/content/campaigns/geometrixx-outdoors/storefront/summer.html`

   여기에는 Teaser 정의와 보기 통계의 개요가 표시됩니다.

   ![chlimage_1-8](assets/chlimage_1-8.png)
