---
title: Adobe 분류
seo-title: Adobe Classifications
description: Adobe 분류에 대해 알아봅니다.
seo-description: Learn about Adobe Classifications.
uuid: 57fb59f4-da90-4fe7-a5b1-c3bd51159a16
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6787511a-2ce0-421a-bcfb-90d5f32ad35e
exl-id: 25e58c68-5c67-4894-9a54-1717d90d7831
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 7%

---

# Adobe 분류{#adobe-classifications}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

Adobe 분류은 분류 데이터를 로 내보냅니다 [Adobe Analytics](/help/sites-administering/adobeanalytics.md) ... 수출자는 **com.adobe.cq.scheduled.exporter.exporter**.

다음을 구성하려면 다음을 수행하십시오.

1. 을 통해 탐색 **도구, Cloudservices** 변환 후 **Adobe Analytics** 섹션을 참조하십시오.
1. 새 구성을 추가합니다. 이제 **Adobe Analytics 분류** 구성 템플릿은 **Adobe Analytics 프레임워크** 구성. 공급 a **제목** 및 **이름** 필요한 경우:

   ![aa-25](assets/aa-25.png)

1. 클릭 **만들기** 를 클릭하여 설정을 구성합니다.

   ![chlimage_1](assets/chlimage_1.png)

   속성은 다음과 같습니다.

   | **필드** | **설명** |
   |---|---|
   | 활성화됨 | 선택 **예** 분류 Adobe 설정을 활성화했습니다. |
   | 충돌 시 덮어쓰기 | 선택 **예** 데이터 충돌을 덮어쓰려면 다음을 수행합니다. 기본적으로 다음 위치로 설정되어 있습니다 **아니요**. |
   | 삭제가 처리되었습니다 | 로 설정된 경우 **예**&#x200B;를 삭제하면 처리된 노드가 내보낸 후에 삭제됩니다. 기본값은 입니다. **False**. |
   | 작업 내보내기 설명 | Adobe 분류 작업에 대한 설명을 입력합니다. |
   | 알림 전자 메일 | Adobe 분류 알림의 이메일 주소를 입력합니다. |
   | 보고서 세트 | 보고서 세트를 입력하여 가져오기 작업을 실행합니다. |
   | 데이터 세트 | 가져오기 작업을 실행할 데이터 집합 관계 ID를 입력합니다. |
   | 변환자 | 드롭다운 메뉴에서 변압기 구현을 선택합니다. |
   | 데이터 소스 | 데이터 컨테이너의 경로로 이동합니다. |
   | 일정 내보내기 | 내보내기 일정을 선택합니다. 기본값은 30분마다 있습니다. |

1. 클릭 **확인** 설정을 저장하려면 을 클릭합니다.

## 페이지 크기 수정 {#modifying-page-size}

레코드는 페이지에서 처리됩니다. 기본적으로 Adobe 분류은 페이지 크기가 1000인 페이지를 만듭니다.

페이지 크기는 Adobe 분류의 정의에 따라 최대 25000 수 있으며 Felix 콘솔에서 수정할 수 있습니다. 내보내기 중에 Adobe 분류은 동시 수정 사항을 방지하기 위해 소스 노드를 잠급니다. 내보내기 후, 오류 시 또는 세션이 닫힐 때 노드의 잠금이 해제됩니다.

페이지 크기를 변경하려면:

1. 에서 OSGI 콘솔로 이동합니다 **https://&lt;host>:&lt;port>/system/console/configMgr** 을(를) 선택합니다. **Adobe AEM 분류 내보내기**.

   ![aa-26](assets/aa-26.png)

1. 업데이트 **페이지 크기 내보내기** 필요에 따라 을(를) 클릭한 다음 **저장**.

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe 분류은 이전에 SAINT 익스포터라고 했습니다.

Exporter는 Transformer를 사용하여 내보내기 데이터를 특정 형식으로 변환할 수 있습니다. Adobe 분류의 경우 하위 인터페이스 `SAINTTransformer<String[]>` Transformer 인터페이스 구현이 제공되었습니다. 이 인터페이스는 데이터 유형을 `String[]` SAINT API에서 사용하고 선택할 수 있는 그러한 서비스를 찾기 위한 마커 인터페이스가 있어야 합니다.

기본 구현 SAINTDefaultTransformer에서 내보내기 소스의 자식 리소스는 속성 이름을 키로 하고 속성 값을 값으로 포함하는 레코드로 처리됩니다. 다음 **키** 열이 자동으로 첫 번째 열로 추가됩니다. 이 값은 노드 이름입니다. 네임스페이스가 지정된 속성(포함)은 무시됩니다.

*노드 구조:*

* id-classification `nt:unstructured`

   * 1 `nt:unstructured`

      * Product = My Product Name (String)
      * 가격 = 120.90 (문자열)
      * 크기 = M(문자열)
      * 색상 = 검정(문자열)
      * 색상^코드 = 101(문자열)

**SAINT 헤더 및 레코드:**

| **키** | **제품** | **가격** | **크기** | **컬러** | **색상^코드** |
|---|---|---|---|---|---|
| 1 | 내 제품 이름 | 120.90 | M | black | 101 |

속성은 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>속성 경로</strong></td> 
   <td><strong>설명</strong></td> 
  </tr> 
  <tr> 
   <td>변압기</td> 
   <td>SAINTTransformer 구현의 클래스 이름</td> 
  </tr> 
  <tr> 
   <td>이메일</td> 
   <td>알림 전자 메일 주소입니다.</td> 
  </tr> 
  <tr> 
   <td>보고서 세트</td> 
   <td>보고서 세트 ID로 가져오기 작업을 실행할 수 있습니다. </td> 
  </tr> 
  <tr> 
   <td>데이터 세트</td> 
   <td>가져오기 작업을 실행할 데이터 집합 관계 ID입니다. </td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>작업 설명. <br /> </td> 
  </tr> 
  <tr> 
   <td>덮어쓰기</td> 
   <td>데이터 충돌을 덮어쓸 플래그입니다. 기본값은 입니다. <strong>false</strong>.</td> 
  </tr> 
  <tr> 
   <td>체크포인트</td> 
   <td>보고서 세트에서 호환성을 확인하는 플래그입니다. 기본값은 입니다. <strong>true</strong>.</td> 
  </tr> 
  <tr> 
   <td>deleteprocessed</td> 
   <td>내보내기 후 처리된 노드를 삭제하는 플래그입니다. 기본값은 입니다. <strong>false</strong>.</td> 
  </tr> 
 </tbody> 
</table>

## Adobe 분류 내보내기 자동화 {#automating-adobe-classifications-export}

고유한 워크플로우를 만들어 새로운 가져오기가 워크플로우를 시작하여 적절하고 올바르게 구조화된 데이터를 **/var/export/** 이를 통해 분류 Adobe으로 내보낼 수 있습니다.
