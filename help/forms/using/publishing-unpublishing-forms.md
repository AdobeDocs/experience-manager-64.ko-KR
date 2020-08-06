---
title: 양식 및 문서 게시 및 게시 취소
seo-title: 양식 및 문서 게시 및 게시 취소
description: 양식의 게시 및 게시 취소를 예약할 수 있습니다. 게시된 양식은 게시 인스턴스에서 복제됩니다.
seo-description: 양식의 게시 및 게시 취소를 예약할 수 있습니다. 게시된 양식은 게시 인스턴스에서 복제됩니다.
uuid: 4de958f8-46d0-4356-ab88-70fa3d480216
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
content-strategy: max-2018
discoiquuid: 7dd08e81-5df6-4522-9f8c-48b4bba8927b
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 0%

---


# 양식 및 문서 게시 및 게시 취소 {#publishing-and-unpublishing-forms-and-documents}

AEM Forms을 사용하면 양식을 손쉽게 작성, 게시 및 게시 취소할 수 있습니다. AEM Forms에 대한 자세한 내용은 양식 [관리 소개를 참조하십시오](/help/forms/using/introduction-managing-forms.md).

AEM Forms 서버는 다음 두 가지 인스턴스를 제공합니다. 작성 및 게시를 참조하십시오. 작성 인스턴스는 양식 자산 및 리소스를 만들고 관리하는 것입니다. 게시 인스턴스는 최종 사용자가 사용할 수 있는 자산 및 관련 리소스를 유지하는 데 사용됩니다. 작성 모드에서 XDP 및 PDF forms을 가져올 수 있습니다. 자세한 내용은 AEM Forms에서 [XDP 및 PDF 문서 가져오기를 참조하십시오](/help/forms/using/get-xdp-pdf-documents-aem.md).

## 지원되는 에셋   {#supported-assets-nbsp}

AEM Forms은 다음과 같은 유형의 자산을 지원합니다.

* 적응형 양식
* 적응형 문서
* 적응형 양식 조각
* 테마
* 양식 템플릿(XFA 양식)
* PDF forms
* 문서(일반 PDF 문서)
* 양식 세트
* 리소스(이미지, 스키마 및 스타일 시트)

처음에는 모든 자산을 작성자 인스턴스에서만 사용할 수 있습니다. 관리자나 양식 작성자는 리소스를 제외한 모든 자산을 게시할 수 있습니다.

양식을 선택하고 게시하면 관련 자산 및 리소스도 게시됩니다. 그러나 종속 자산은 게시되지 않습니다. 이러한 컨텍스트에서 관련 자산 및 리소스는 게시된 자산이 사용하거나 참조하는 자산입니다. 종속 자산은 게시된 자산을 참조하는 자산입니다.

응용 Forms은 자동으로 게시되지 않는 일부 구성, 설정 및 사용자 지정을 활용할 수 있습니다. 적응형 양식을 게시하기 전에 이러한 리소스를 게시하거나 활성화하는 것이 좋습니다.

* 편집 가능한 적응형 양식 템플릿
* Adobe Sign, Typekit, reCAPTCHA 및 양식 데이터 모델에 대한 Cloud Service 구성
* 다른 클라우드 서비스 구성은 사용자에게 관리자 권한이 있는 경우에만 활성화됩니다.
* 사용자 정의 여기에는 다음이 포함되지만 이에 국한되지 않습니다.

   * 사용자 정의 레이아웃
   * 사용자 정의 모양
   * CSS 파일 - 적응형 양식 컨테이너 속성 대화 상자에서 입력으로 취함
   * 클라이언트 라이브러리 범주 - 응용 양식 컨테이너 속성 대화 상자에서 입력으로 취함
   * 응용 양식 템플릿의 일부로 포함할 수 있는 다른 클라이언트 라이브러리
   * 디자인 패스

## 자산 상태 {#asset-states}

자산은 다음 상태를 가질 수 있습니다.

* **게시 안 됨:** 게시되지 않은 자산(게시 취소된 상태는 Forms 자산에만 적용됩니다. 통신 관리 자산에 게시 취소된 상태가 없습니다.)
* **게시됨**: 게시되어 게시 인스턴스에서 사용할 수 있는 자산
* **수정됨**: 게시한 후 수정된 자산

## 자산 게시 {#publish-an-asset}

1. AEM Forms 서버에 로그인합니다.
1. 다음 중 하나를 사용하여 자산을 선택하고 게시합니다.

   1. 포인터를 자산 위로 이동하고 **[!UICONTROL 게시]** ![aem6forms_globe를 누릅니다](assets/aem6forms_globe.pngasset.png).
   1. 다음 중 하나를 수행하고 게시를 누릅니다.

      * 카드 보기에 있는 경우 **[!UICONTROL 선택]** 항목 ![을 탭하고](assets/aem6forms_check-circle.png)자산을 탭합니다. 자산이 선택됩니다.
      * 목록 보기에 있는 경우 자산의 확인란을 선택합니다. 자산이 선택됩니다.
      * 자산을 탭하여 세부 사항을 표시합니다.
      * 속성 보기를 탭하여 자산의 속성을 ![표시합니다](assets/viewproperties.png).

      >[!NOTE]
      >
      >여러 자산을 선택하지 마십시오. 여러 자산을 동시에 게시할 수 없습니다.


1. 게시 프로세스가 시작되면 관련 자산 및 리소스를 모두 나열하는 확인 대화 상자가 나타납니다. 관련 에셋이 포함된 대화 상자에서 게시를 **[!UICONTROL 누릅니다]**. 자산이 게시되고 [자산 게시 성공] 대화 상자가 나타납니다.

   >[!NOTE]
   >
   >응용 양식의 경우 관련 자산과 함께 응용 양식 페이지 이름도 표시됩니다.

   ![모든 관련 자산 및 리소스가 포함된 확인 대화 상자](assets/p4.png)

   모든 관련 자산 및 리소스가 포함된 확인 대화 상자

   >[!NOTE]
   >
   >Forms 관리자의 경우, 사용자에게 나열된 자산을 게시할 권한이 없으면 게시 작업이 비활성화됩니다. 추가 권한이 필요한 자산은 빨간색으로 표시됩니다.

   자산이 게시되면 자산의 메타데이터 속성이 게시 인스턴스에 복사되고 자산의 상태가 게시됨으로 변경됩니다. 게시된 종속 자산의 상태도 게시됨으로 변경됩니다.

   자산을 게시한 후 Forms 포털을 사용하여 웹 페이지의 모든 자산을 표시할 수 있습니다. 자세한 내용은 포털 [에 양식 게시 소개를 참조하십시오](/help/forms/using/introduction-publishing-forms.md).

## Publish all the Correspondence Management Assets {#publish-all-the-correspondence-management-assets}

AEM Forms을 사용하면 서버에 모든 통신 관리 에셋을 한 번에 게시할 수 있습니다. 게시된 자산은 모든 통신 관리 자산 및 관련 종속성을 포함합니다.

서버에 모든 통신 관리 자산을 게시하려면 다음 단계를 완료하십시오.

1. AEM Forms 서버에 로그인합니다.
1. 전역 탐색 막대에서 **Adobe Experience Manager** 를 누릅니다.
1. 도구 ![-1을](assets/tools-1.png)누른 다음 **Forms을 누릅니다**.
1. Tap **Publish Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   [모든 통신 관리 자산 게시] 페이지가 나타나고 통신 관리 자산 게시 프로세스가 시도되었을 때의 정보가 표시됩니다.

   ![publish-last-run-details](assets/publish-last-run-details.png)

1. 게시를 **누르고** 확인 메시지에서 **확인을 누릅니다**.

   배치 프로세스가 완료되면 마지막 실행 상세내역을 볼 수 있습니다. 여기에는 관리자 로그인 및 일괄 처리가 성공적으로 실행되거나 실패한 경우 등의 정보가 포함됩니다.

   >[!NOTE]
   >
   >게시 프로세스는 일단 시작되면 취소할 수 없습니다. 또한 게시 작업이 진행 중인 동안에는 자산을 만들거나, 삭제하거나, 수정하거나, 게시하거나, 모든 통신 관리 자산 내보내기 작업을 시작하지 마십시오.

## Forms 및 문서에 대한 게시 및 게시 취소 자동화 {#automate-publishing-and-unpublishing-for-forms-amp-documents}

AEM Forms을 사용하면 Forms 및 문서에 대한 자산 게시 및 게시 취소를 예약할 수 있습니다. 메타데이터 편집기에서 일정을 지정할 수 있습니다. 양식 메타데이터 관리에 대한 자세한 내용은 양식 메타데이터 [관리를 참조하십시오.](/help/forms/using/manage-form-metadata.md)

Forms 및 문서 자산을 게시 및 게시 취소하는 날짜와 시간을 예약하려면 다음 단계를 따르십시오.

1. 자산을 선택하고 속성 **[!UICONTROL 보기를 누릅니다]**. 메타데이터 속성 페이지가 열립니다.
1. 메타데이터 속성 페이지에서 **[!UICONTROL 고급을]**&#x200B;누른 다음 **[!UICONTROL 편집]**![](assets/illustratorcc_penciltool_cur_edit_2_17.png)을누릅니다.
1. [ **[!UICONTROL 시간에 게시]** ] 및 [ **[!UICONTROL 시간]** 게시] 필드에서 날짜 및 시간을 선택합니다.

   **[!UICONTROL aem6forms]** _check ![완료를 누릅니다](assets/aem6forms_check.png).

## 자산 게시 취소 {#unpublish-an-asset}

1. 게시되는 자산을 선택하고 게시 **[!UICONTROL 취소]** 를 ![누릅니다](assets/unpublish.png).
1. 다음 중 하나를 사용하여 자산을 선택하고 게시 취소합니다.

   1. 포인터를 자산 위로 이동하고 게시 **[!UICONTROL 취소]** 를 ![누릅니다](assets/unpublish.png).
   1. 다음 중 하나를 수행하고 게시 취소를 누릅니다.

      * 카드 보기에 있는 경우 **[!UICONTROL Enter Selection** ![aem6forms_check-circle](assets/aem6forms_check-circle.png)을 탭하고 자산을 탭합니다. 자산이 선택됩니다.
      * 목록 보기에 있는 경우 자산을 마우스로 가리키고 selectassetcheckmark를 ![누릅니다](assets/selectassetcheckmark.png) . 자산이 선택됩니다.
      * 자산을 탭하여 세부 사항을 표시합니다.
      * 속성 보기를 탭하여 자산의 속성을 ![표시합니다](assets/viewproperties.png).

1. 게시 취소 프로세스가 시작되면 확인 대화 상자가 나타납니다. 게시 **[!UICONTROL 취소를 누릅니다]**.

   >[!NOTE]
   >
   >선택한 자산만 게시 취소되며, 해당 하위 자산과 참조된 자산(있는 경우)은 게시 취소되지 않습니다.

## 자산 또는 문자를 이전에 게시된 버전으로 되돌리기 {#revert-an-asset-or-letter-to-the-previously-published-version}

에셋 또는 문자를 편집하고 게시할 때마다 에셋 또는 글자의 버전이 만들어집니다. 자산 또는 문자를 이전에 게시된 버전으로 되돌릴 수 있습니다. 현재 버전의 자산이나 문서에 문제가 있는 경우 이 작업을 수행해야 할 수도 있습니다.

>[!NOTE]
>
>게시된 편지에서 사용된 종속 자산이 시스템에서 삭제되는 경우 편지를 마지막으로 게시된 상태로 되돌리지 마십시오.

1. 자산을 선택하고 이전에 게시된 버전 **[!UICONTROL 으로 되돌리기를]** 탭하면 ![reverttoreviouslapublishedversion이 됩니다](assets/reverttopreviouslypublishedversion.png).
1. 자산이 되돌려지기 전에 확인 대화 상자가 나타납니다. 되돌리기를 **[!UICONTROL 누릅니다]**.

   자산이나 문자가 이전에 게시된 버전으로 롤백됩니다.

## 자산 삭제 {#delete-an-asset}

>[!NOTE]
>
>자산을 삭제하면 게시 인스턴스에서 제거됩니다. 자산을 삭제하면 기본 버전을 제외한 버전 내역도 제거됩니다.

1. 자산을 선택하고 **[!UICONTROL 삭제]** 를 ![누릅니다](assets/delete.png).

   >[!NOTE]
   >
   >삭제 옵션은 자산을 탭하여 자산 세부 사항을 표시하거나 속성 보기를 탭하여 자산의 속성을 표시하는 경우에도 사용할 ![수 있습니다](assets/viewproperties.png).

1. 자산이 삭제되기 전에 확인 대화 상자가 나타납니다. 삭제를 **[!UICONTROL 누릅니다]**.

   >[!NOTE]
   >
   >선택한 자산만 삭제되며 종속 자산도 삭제되지 않습니다. 자산의 참조를 확인하려면 ![참조를](assets/references.png) 누른 다음 자산을 선택합니다.
   >
   >삭제하려는 자산이 다른 자산의 하위 자산인 경우 삭제되지 않습니다. 이러한 자산을 삭제하려면 다른 자산에서 이 자산의 참조를 제거한 다음 다시 시도하십시오.

## 보호된 적응형 양식 {#protected-adaptive-forms}

선택한 사용자가 액세스할 양식에 대한 인증을 활성화할 수 있습니다. 양식에 대한 인증을 활성화하면 액세스 전에 로그인 화면이 표시됩니다. 권한이 있는 사용자만 양식에 액세스할 수 있습니다.

양식에 대한 인증을 활성화하려면

1. 브라우저에서 게시 인스턴스의 configMgr을 엽니다.

   URL: `https://<hostname>:<PublishPort>/system/console/configMgr`

1. Adobe Experience Manager 웹 콘솔 구성에서 **Apache Sling 인증 서비스를** 클릭하여 구성합니다.
1. 표시되는 Apache Sling 인증 서비스 대화 상자에서 **+** 단추를 사용하여 경로를 추가합니다.

   경로를 추가하면 해당 경로의 양식에 대해 인증 서비스가 활성화됩니다.

