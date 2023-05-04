---
title: 관리 [!DNL Adobe Stock] 자산 [!DNL Adobe Experience Manager Assets].
description: 검색, 가져오기, 라이선스 및 관리 [!DNL Adobe Stock] 내 자산 [!DNL Adobe Experience Manager]. 라이선스가 있는 자산을 다른 디지털 자산으로 사용합니다.
contentOwner: AG
feature: Search,Adobe Stock
role: User,Admin
exl-id: f360abaf-a812-46ed-a160-ff569b6bec1c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 13%

---

# 사용 [!DNL Adobe Stock] 자산 [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

조직은 통합할 수 있습니다 [!DNL Adobe Stock] 엔터프라이즈 플랜 [!DNL Experience Manager Assets] 라이선스가 있는 자산이 자신의 광고 및 마케팅 프로젝트에 폭넓게 사용 가능한지 그리고 [!DNL Experience Manager].

[!DNL Adobe Stock] 서비스는 디자이너와 기업의 모든 광고 프로젝트를 위해 고품질로 큐레이팅된 로열티가 없는 수백만 장의 사진, 벡터, 일러스트레이션, 비디오, 템플릿 및 3D 자산에 대한 액세스를 제공합니다. [!DNL Experience Manager] 사용자는 신속하게 검색, 미리 보기 및 라이선스를 제공할 수 있습니다 [!DNL Adobe Stock] 에 저장된 자산 [!DNL Experience Manager], 종료되지 않고 [!DNL Experience Manager] 인터페이스.

## 사전 요구 사항 {#prerequisites}

통합에는 다음이 필요합니다 [엔터프라이즈 Adobe Stock 플랜](https://stockenterprise.adobe.com/) 및 [!DNL Experience Manager] 6.4(서비스 팩 2 이상 배포) 대상 [!DNL Experience Manager] 6.4 서비스 팩 세부 사항 [릴리스 노트](/help/release-notes/sp-release-notes.md).

## 통합 [!DNL Experience Manager] 및 [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

간의 통신을 허용하려면 [!DNL Experience Manager] 및 [!DNL Adobe Stock]를 설정하는 경우 IMS 구성 및 [!DNL Adobe Stock] 의 구성 [!DNL Experience Manager].

>[!NOTE]
>
>전용 [!DNL Experience Manager] 관리자 및 [!DNL Admin Console] 조직의 관리자는 관리자 권한이 필요하므로 통합을 수행할 수 있습니다.

### IMS 구성 만들기 {#create-an-ims-configuration}

1. 에서 [!DNL Experience Manager] 사용자 인터페이스, 탐색 **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL Adobe IMS 구성]**. Click **[!UICONTROL Create]** and select **[!UICONTROL Cloud Solution]** > **[!UICONTROL Adobe Stock]**.
1. 기존 인증서를 재사용하거나 을 선택합니다 **[!UICONTROL 새 인증서 만들기]**.
1. **[!UICONTROL 인증서 만들기]**&#x200B;를 클릭합니다. 만든 후 공개 키를 다운로드합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다. 을(를) 종료하십시오. [!UICONTROL Adobe IMS 기술 계정 구성] 필요한 값을 곧 제공하기 위해 화면이 열립니다.
1. 액세스 [Adobe Developer 콘솔](https://console.adobe.io). 통합이 필요한 조직에 대한 관리자 권한이 계정에 있는지 확인합니다.
1. 클릭 **[!UICONTROL 새 프로젝트 만들기]** 을(를) 클릭합니다. **[!UICONTROL API 추가]**. 선택 **[!UICONTROL Adobe Stock]** 을 클릭하여 제품에서 사용할 수 있습니다. 선택 [!UICONTROL OAUTH 2.0 웹].
1. 제공 **[!UICONTROL 기본 리디렉션 URI]** 및 **[!UICONTROL 리디렉션 URI 패턴]** 값. **[!UICONTROL 구성된 API 저장]**&#x200B;을 클릭합니다. 생성된 ID와 암호를 복사합니다.
1. in [!UICONTROL Adobe IMS 기술 계정 구성] 화면에서 라는 상자에 값을 입력합니다 **[!UICONTROL 제목]**, **[!UICONTROL 인증 서버]**, **[!UICONTROL API 키]**, **[!UICONTROL 클라이언트 암호]**, 및 **[!UICONTROL 페이로드]**. 이러한 값에 대한 자세한 내용은 [JWT 인증 빠른 시작](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

<!-- TBD: Update the URL when the new URL is available. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### 만들기 [!DNL Adobe Stock] 의 구성 [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. 에서 [!DNL Experience Manager] 사용자 인터페이스, 탐색 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. 클릭 **[!UICONTROL 만들기]** 구성을 만들고 기존 IMS 구성과 연결 선택 `PROD` 환경 매개 변수로 사용됩니다.
1. in **[!UICONTROL 라이선스가 있는 자산 경로]** 필드를 비워 둡니다. 저장할 위치를 변경하지 마십시오 [!DNL Adobe Stock] 자산.
1. 필요한 모든 속성을 추가하여 만들기를 완료합니다. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.
1. 추가 [!DNL Experience Manager] 자산의 라이선스를 제공할 수 있는 사용자 또는 그룹.

>[!NOTE]
>
>여러 개가 있는 경우 [!DNL Adobe Stock] 구성, 사용자 환경 설정 패널(**[!UICONTROL AEM]** > **[!UICONTROL 사용자 아이콘]** > **[!UICONTROL 사용자 환경 설정]** > **[!UICONTROL Stock 구성]**).

## 사용 및 관리 [!DNL Adobe Stock] 자산 [!DNL Experience Manager] {#usemanage}

조직은 이 기능을 사용하여 사용자가 [!DNL Adobe Stock] 자산 [!DNL Experience Manager Assets]. 에서 [!DNL Experience Manager] 사용자 인터페이스, 사용자가 검색 가능 [!DNL Adobe Stock] 자산 및 라이선스 필수 자산

한 번 [!DNL Adobe Stock] 의 라이선스가 있는 자산 [!DNL Experience Manager]일반적인 자산처럼 사용 및 관리할 수 있습니다. in [!DNL Experience Manager]로 설정되면 사용자는 자산을 검색하고 미리 볼 수 있습니다. 자산을 복사하여 게시합니다. 자산 공유 [!DNL Brand Portal]; 를 통해 자산 액세스 및 사용 [!DNL Experience Manager] 데스크탑 앱; 기타.

![Adobe Experience Manager 작업 공간에서 Adobe Stock 자산 검색 및 결과 필터링](assets/adobe-stock-search-results-workspace.png)

*그림: 검색 대상 [!DNL Adobe Stock] 자산 및 결과의 필터링 [!DNL Experience Manager] 인터페이스.*

**A.**[!DNL Adobe Stock] Search assets similar to the assets whose ID is provided. **B.** Search assets that match your selection of shape or orientation. **C.** Search for one of more supported asset types **D.** Open or collapse the filters pane **E.** License and save the selected asset in [!DNL Experience Manager]**F.**[!DNL Experience Manager] Save the asset in with watermark **G.**[!DNL Adobe Stock] Explore assets on website that are similar to the selected asset **H.**[!DNL Adobe Stock] View the selected assets on website **I.** Number of selected assets from the search results **J.** Switch between Card view and List view

### 자산 찾기 {#find-assets}

사용자 [!DNL Experience Manager] 사용자, 두 가지 모두에서 자산을 검색할 수 있음, [!DNL Experience Manager] 및 [!DNL Adobe Stock]. 검색 위치가 다음으로 제한되지 않는 경우 [!DNL Adobe Stock], 검색 결과 [!DNL Experience Manager] 및 [!DNL Adobe Stock] 표시됩니다.

* 을 검색하려면 [!DNL Adobe Stock] 자산, **[!UICONTROL 탐색]** > **[!UICONTROL 자산]** > **[!UICONTROL Adobe Stock 검색]**.

* 에서 자산을 검색하려면 다음을 수행하십시오 [!DNL Adobe Stock] 및 [!DNL Experience Manager Assets], 검색 을 클릭합니다. ![search_icon](assets/search_icon.png).

또는 입력을 시작합니다 `Location: Adobe Stock` 검색 창에서 [!DNL Adobe Stock] 자산. [!DNL Experience Manager] 에서는 검색된 자산에 고급 필터링 기능을 제공하여 사용자가 지원되는 자산 유형, 이미지 방향 및 라이선스가 있는 상태 등의 필터를 사용하여 필요한 자산을 빠르게 작성할 수 있도록 합니다.

>[!NOTE]
>
>에서 검색된 자산 [!DNL Adobe Stock] 에 표시됩니다. [!DNL Experience Manager]. [!DNL Adobe Stock] 자산을 가져와서 [!DNL Experience Manager] 다음 중 한 사용자 이후에만 저장소 [자산을 저장합니다.](/help/assets/aem-assets-adobe-stock.md#saveassets) 또는 [자산 라이선스 및 저장](/help/assets/aem-assets-adobe-stock.md#licenseassets). 이미 저장된 자산 [!DNL Experience Manager] 쉽게 참조하고 액세스할 수 있도록 표시되고 강조 표시됩니다. 또한, [!DNL Stock] 자산은 소스를 (으)로 나타내는 몇 가지 추가 메타데이터와 함께 저장됩니다 [!DNL Stock].

![검색 결과에서 Experience Manager 및 강조 표시된 Adobe Stock 자산의 검색 필터](assets/aem-search-filters2.jpg)

*그림: 검색 필터 [!DNL Experience Manager] 및 강조 표시 [!DNL Adobe Stock] 검색 결과의 자산.*

### 필요한 자산을 저장하고 봅니다 {#saveassets}

저장할 자산을 선택합니다 [!DNL Experience Manager]. 클릭 [!UICONTROL 저장] 맨 위의 도구 모음에서 자산의 이름과 위치를 제공합니다. 라이센스가 없는 자산은 워터마크로 로컬에 저장됩니다.

다음번에 자산을 검색할 때 저장된 자산이 배지로 강조 표시되어 에서는 해당 자산을 사용할 수 있음을 나타냅니다. [!DNL Experience Manager Assets].

>[!NOTE]
>
>최근에 추가된 자산에 라이센스 배지 대신 새 배지가 표시됩니다.

### 자산 라이선스 {#licenseassets}

사용자가 라이선스를 제공할 수 있음 [!DNL Adobe Stock] 자산의 할당량을 사용하여 자산 [!DNL Adobe Stock] 엔터프라이즈 플랜. 자산 라이센스를 부여하면 워터마크 없이 저장되며 에서 검색하고 사용할 수 있습니다 [!DNL Experience Manager Assets].

![Experience Manager Assets에서 Adobe Stock 자산의 라이선스 및 저장 대화 상자](assets/aem-stock_licenseandsave.jpg)

*그림: 라이선스 및 저장 대화 상자 [!DNL Adobe Stock] 자산 [!DNL Experience Manager Assets].*

### 메타데이터 및 자산 속성에 액세스 {#access-metadata-and-asset-properties}

사용자는 [!DNL Adobe Stock] 에 저장된 자산에 대한 메타데이터 속성 [!DNL Experience Manager], 및 추가 **[!UICONTROL 라이선스 참조]** 참조하십시오. 그러나 라이선스 참조에 대한 업데이트는 다음 간에 동기화되지 않습니다 [!DNL Experience Manager] 및 [!DNL Adobe Stock] 웹 사이트입니다.

사용자는 라이선스가 있는 자산과 라이선스가 없는 자산 모두에 대한 속성을 볼 수 있습니다.

![저장된 자산의 메타데이터 및 라이선스 참조를 보고 액세스합니다](assets/metadata_properties.jpg)

*그림: 저장된 자산의 메타데이터 및 라이선스 참조를 보고 액세스합니다.*

## 알려진 제한 사항 {#known-limitations}

* **편집 이미지 경고가 표시되지 않습니다**: 이미지에 라이센스를 부여할 때 이미지가 편집 전용 인지 확인할 수 없습니다. 관리 관리자는 Admin Console에서 편집 자산에 대한 액세스를 중단할 수 있습니다.

* **잘못된 라이선스 유형이 표시됩니다.**: 잘못된 라이센스 유형이 [!DNL Experience Manager] 참조하십시오. 사용자는 [!DNL Adobe Stock] 라이센스 유형을 확인하는 웹 사이트입니다.

* **참조 필드 및 메타데이터가 동기화되지 않습니다**: 사용자가 라이센스 참조 필드를 업데이트하면 라이센스 참조 정보가 [!DNL Experience Manager] 하지만 [!DNL Adobe Stock] 웹 사이트입니다. 마찬가지로 사용자가 [!DNL Adobe Stock] 웹 사이트에서는 업데이트가 동기화되지 않습니다 [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [사용에 대한 비디오 자습서 [!DNL Adobe Stock] 자산 [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [[!DNL Adobe Stock] 엔터프라이즈 플랜 도움말](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-stock-enterprise.ug.html)
>* [[!DNL Adobe Stock] FAQ](https://helpx.adobe.com/stock/faq.html)

