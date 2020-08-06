---
title: AEM에서의 3D 자산 업로드 및 처리 정보
seo-title: AEM에서의 3D 자산 업로드 및 처리 정보
description: 3D 자산을 업로드하고 처리하기 위한 모범 사례
seo-description: 3D 자산을 업로드하고 처리하기 위한 모범 사례
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 71%

---


# AEM에서의 3D 자산 업로드 및 처리 정보 {#about-the-uploading-and-processing-of-d-assets-in-aem}

표준 업로드 또는 동기화 메커니즘을 사용하여 3D 자산과 관련 참조된 파일을 AEM Assets로 가져오십시오.

[자산 업로드](managing-assets-touch-ui.md#uploading-assets)를 참조하십시오.

기본 3D 모델 파일을 업로드하기 전이나 동시에 참조된 모든 파일을 업로드하는 것이 좋습니다. 그러나 요구 사항은 아닙니다.

업로드가 완료되면, 자산을 보고 렌더링할 수 있도록 3D 파일이 변환되고, 추가적인 처리가 적용됩니다.

## 3D 자산 업로드에 대한 우수 사례 {#best-practices-for-uploading-d-assets}

* 일반적으로 AEM Assets 폴더 계층 구조에서 3D 컨텐츠를 업로드하는 것에 대한 제한 사항은 없습니다. 그러나 AEM 3D의 자동화된 파일 종속성 해소에는 대규모 자산 저장소를 검색하는 데 걸리는 시간을 제어하는 범위 제한이 있습니다. 따라서 3D 자산 및 연결된 파일들을 업로드할 때에는 각 파일의 합리적인 범위 내(일반적인 차상위 폴더)에서 수행하는 것이 좋습니다. 파일 종속성이 해소된 후에는 구축된 관계를 잃지 않고 저장소 내 어디에서든 3D 자산과 종속 항목을 모두 자유롭게 이동할 수 있습니다.
* 3D 컨텐츠를 업로드하려면 그 *전*&#x200B;에 3D 컨텐츠를 위한 일관된 폴더 구조를 결정하는 것이 좋습니다. 다음 팁은 선택할 수 있는 몇 가지 추천 접근 방식입니다.

   * **업로드하는 각 3D 자산에 대해 별도의 폴더를 유지 관리합니다**.

      이 폴더는 기본 3D 모델 파일과 모든 해당 종속 항목을 포함합니다. 모든 자산 및 종속 항목을 하나의 폴더에 넣어서 구현은 쉽지만 컨텐츠 검색은 쉽지 않습니다. 모델 간에 종속 항목(텍스처 맵)을 공유하는 것도 복잡해집니다.

   * **모델을 한 폴더에 보관하고 종속 항복은 동위 폴더나 하위 폴더에 보관합니다**.

      이 접근 방식은 모델 간 종속 항목 공유를 쉽게 지원합니다. 그러나 자산의 개수가 많을 경우에는 특정 종속 항목을 찾기가 어려워질 수 있습니다.

   * **모델 및 종속 항목을 위한 별도의 병렬 폴더 계층 구조**.

      Autodesk Maya와 같은 3D 작성 애플리케이션이 컨텐츠를 저장하는 방식에 대한 접근 방식을 모델링할 수 있습니다.

* 종속 자산은 연결된 3D 자산이나 종속 자산을 참조한 자산도 제거하지 않는 한 삭제하면 안 됩니다. 그러나 종속 자산을 삭제하지 않고도 3D 자산을 자유롭게 삭제할 수 있습니다. 종속성이 실수로 없어진 경우에는 종속성을 복원하도록 쉽게 종속성을 해결할 수 있습니다.

   파일 종속성 해결을 참조하십시오.

## 3D 파일을 업로드할 때의 성능 고려 사항 {#performance-considerations-when-uploading-d-files}

3D 파일을 변환 및 처리하는 데에는 일반적으로 서버에서 상당한 CPU 및 메모리 리소스가 소비됩니다. 또한 상당한 시간이 소요됩니다. 처리 시간은 종종 모델의 크기와 서버의 기능에 따라 크게 달라집니다. 예를 들어 면이 10만 개 미만인 일반적인 작은 모델은 일반적으로 1분 미만이면 볼 수 있도록 준비가 되며, 2~3분이면 완전히 처리됩니다. 반면에 면이 백만 개 이상인 큰 모델은 완전히 처리하는 데 수십 분이 걸릴 수 있습니다.

서버가 너무 많이 느려지는 방지하기 위해 전환, 처리 및 렌더링 작업은 필요에 따라 큐에 오르게 됩니다. The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. 이 상태는 현재 자산이 처리되기 전에 다른 처리 또는 렌더링 작업이 완료되어야 함을 나타냅니다.

처리 및 렌더링에 CPU 사용을 제한하는 메커니즘이 있습니다. CPU [제한](advanced-config-3d.md) 구성 방법에 대한 자세한 내용은 고급 구성 설정을 참조하십시오.

## 업로드된 3D 파일의 처리 상태 모니터링 {#monitoring-the-processing-status-of-your-uploaded-d-files}

In **[!UICONTROL Card View]** only, the processing status and progression is displayed as a progress banner on the asset&#39;s card. 업로드된 각 3D 모델은 일반적으로 다음 4-6개의 순서로 처리 단계를 수행합니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>처리 단계</strong><br /> </td> 
   <td><strong>처리 이름</strong></td> 
   <td><strong>설명</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>처리 중</td> 
   <td>기본적인 초기 처리 및 메타데이터 추출</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>형식 변환</td> 
   <td>3D 모델이 기본 형식(Autodesk® Maya® 또는 Autodesk® 3ds Max®)에서 중간 형식(FBX)으로 변환됩니다.</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>미리 보기 만들기</td> 
   <td>FBX 또는 OBJ 파일을 인제스트하고 처리합니다. 파일 종속성을 평가하고 가능한 경우 자산 참조로 확인합니다.</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>지면 그림자 만들기</td> 
   <td>선택 사항입니다. 3D 개체 아래의 지표 평면에 배경 교합 그림자 효과를 생성할 수 있습니다. 이 처리 <a href="/help/assets/advanced-config-3d.md">를</a> 활성화하거나 비활성화하려면 고급 구성 설정을 참조하십시오.</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>라이트맵 만들기</td> 
   <td>선택 사항입니다. 대화형 미리 보기의 품질을 높이고 기본 렌더러의 렌더링을 신속하게 처리할 수 있도록 해줍니다. 이 처리 <a href="/help/assets/advanced-config-3d.md">를</a> 활성화하거나 비활성화하려면 고급 구성 설정을 참조하십시오.</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>애니메이션 만들기</td> 
   <td>선택 사항입니다. 카드 보기에서 시각적 썸네일로 사용되는 간단한 애니메이션을 렌더링할 수 있도록 해줍니다. 이 처리 <a href="/help/assets/advanced-config-3d.md">를</a> 활성화하거나 비활성화하려면 고급 구성 설정을 참조하십시오.</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>처리 대기 중</td> 
   <td>다른 3D 자산에 처리 우선 순위가 있을 때 표시됩니다. 예를 들어, 이전에 업로드되었지만 처리가 아직 완료되지 않은 자산입니다.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. 모든 처리 단계가 완료될 때까지 기다릴 필요가 없습니다.

