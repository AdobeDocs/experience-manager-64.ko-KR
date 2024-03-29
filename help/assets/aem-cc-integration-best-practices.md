---
title: Experience Manager 및 Creative Cloud 통합 우수 사례
description: 통합 우수 사례 [!DNL Experience Manager] Adobe Creative Cloud을 사용하여 자산 전송 워크플로우를 간소화하고 최대 효율성을 실현하는 배포
contentOwner: AG
feature: Collaboration,Adobe Asset Link,Desktop App
role: User,Admin
exl-id: cb9bea05-3359-4fb4-b935-59e522a5f387
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3524'
ht-degree: 16%

---

# [!DNL Experience Manager] 및 [!DNL Creative Cloud] 통합 우수 사례 {#aem-and-creative-cloud-integration-best-practices}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets는 DAM 사용자가 크리에이티브 팀과 함께 작업할 수 있도록 Adobe Creative Cloud과 통합하여 컨텐츠 작성 프로세스에서 간소화된 공동 작업을 수행할 수 있도록 해주는 DAM(디지털 자산 관리) 솔루션입니다.

Adobe Creative Cloud은 크리에이티브 팀이 디지털 자산을 만드는 데 도움이 되는 솔루션 및 서비스 에코시스템을 제공합니다. 여기에는 데스크톱 및 모바일 애플리케이션, 데스크탑 동기화 또는 웹 경험이 포함된 스토리지와 같은 클라우드 서비스, Adobe Stock과 같은 마켓플레이스 등이 포함됩니다.

사용 사례를 기반으로 데스크탑과 엔터프라이즈급 DAM 간에 어떤 통합을 선택하고 연결 워크플로우에 대한 관련 모범 사례는 무엇입니까? 를 참조하십시오.

>[!NOTE]
>
>폴더 공유 위치 [!DNL Experience Manager] Creative Cloud은 더 이상 사용되지 않으며 더 이상 이 안내서에서 다루지 않습니다. Adobe은 다음과 같은 최신 기능을 사용할 것을 권장합니다. [Adobe 자산 링크](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) 또는 [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html) 크리에이티브 사용자에게 [!DNL Experience Manager].

## 크리에이티브, 마케터 및 DAM 사용자의 공동 작업 요구 사항 {#collaboration-needs-of-creatives-marketers-and-dam-users}

| 요구 사항 | 사용 사례 | 관련 서피스 |
|---|---|---|
| 데스크탑에서 크리에이티브 환경 간소화 | DAM에서 자산에 대한 액세스 간소화([!DNL Assets])를 사용하도록 선택할 수 있습니다. 변경 사항을 검색, 사용(열기), 편집 및 저장하는 쉽고 간단한 방법이 필요합니다 [!DNL Experience Manager]새 파일을 업로드할 수도 있습니다. | Win 또는 Mac 데스크탑 앱 Creative Cloud |
| Adobe Stock에서 고품질의 즉시 사용할 수 있는 자산 제공 | 마케터는 자산 소싱 및 검색을 지원하여 컨텐츠 작성 프로세스를 가속화할 수 있습니다. 크리에이티브 전문가가 크리에이티브 도구 내에서 바로 승인된 자산을 사용합니다. | [!DNL Assets]; Adobe Stock marketplace; 메타데이터 필드 |
| 조직별 자산 분배 및 공유 | 내부 부서/지역 분기 및 외부 파트너, 배포자 및 에이전시는 상위 조직에서 공유한 승인된 자산을 사용합니다. 조직은 더 광범위한 재사용을 위해 생성된 자산을 안전하고 원활하게 공유하려고 합니다. | Brand Portal, Asset Share Commons |

## 협업 요구 사항을 지원하기 위한 Adobe 제공 {#adobe-offerings-to-support-the-collaboration-need}

| 관련 성향에 대한 가치 제안 | Adobe 제공 | 관련 서피스 |
|---|---|---|
| 크리에이티브 사용자가 [!DNL Experience Manager], 열기 및 사용 변경 내용 편집 및 업로드 [!DNL Experience Manager]및에 새 파일을 업로드합니다. [!DNL Experience Manager], Creative Cloud 앱을 종료하지 않습니다. | [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator 및 InDesign |
| 비즈니스 사용자는 자산 열기 및 사용, 변경 내용 편집 및 업로드 작업을 단순화합니다. [!DNL Experience Manager], 및에 새 파일 업로드 [!DNL Experience Manager] 데스크탑 환경에서 실행할 수 있습니다. 일반 통합을 사용하여 비Adobe을 포함하여 기본 데스크탑 애플리케이션에서 자산 유형을 엽니다. | [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] Win 및 Mac 데스크탑의 데스크탑 앱 |
| 마케터와 비즈니스 사용자는 내에서 Adobe Stock 자산을 검색, 미리 보기, 라이선스 및 저장 및 관리합니다 [!DNL Experience Manager]. 라이선스와 저장된 자산은 더 나은 거버넌스를 위해 선별된 Adobe Stock 메타데이터를 제공합니다. | [Experience Manager 및 Adobe Stock 통합](aem-assets-adobe-stock.md) | [!DNL Experience Manager] 웹 인터페이스 |

This article focuses primarily on the first two aspects of the collaboration needs. Distribution and sourcing of assets at scale is briefly mentioned as a use case. For such needs solutions, consider Adobe Brand Portal or Asset Share Commons. 과 같은 대체 솔루션 [Brand Portal](https://helpx.adobe.com/kr/experience-manager/brand-portal/user-guide.html), 다음을 기반으로 구축 가능한 솔루션 [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) 구성 요소, [링크 공유](/help/assets/link-sharing.md), 사용 [Experience Manager Assets](/help/assets/managing-assets-touch-ui.md) 구체적인 요구 사항에 따라 검토해야 합니다.

![Creative Cloud 연결 [!DNL Experience Manager]: 사용할 기능 결정](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### 사용 사례 매핑

| 사용 사례 | [!DNL Experience Manager] 데스크탑 앱 | 폴더 공유 | 기타 솔루션 |
|---|---|---|---|
| Creative 사용자와 DAM 자산의 더 작은 수(1)를 공유 | ✔✔ | ✔ |  |
| Creative 사용자와 더 많은 DAM 자산 공유(2) | ✔✔ | ✘ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [자산 공유](assets-finder-editor.md) |
| DAM에 액세스할 수 있는 사용자와 DAM 자산 공유 | ✔✔ | ✔ | [공유 링크](link-sharing.md) |
| DAM에 액세스할 수 없는 사용자와 DAM 자산 공유 | ✘ | ✔✔ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [자산 공유](assets-finder-editor.md) |
| DAM에 더 작은 자산 수/볼륨 저장 | ✔✔ | ✔ | [웹 UI 업로드](managing-assets-touch-ui.md) |
| DAM에 더 많은 자산 저장(3) | ✔✔ | ✘ | [웹 UI 업로드](managing-assets-touch-ui.md) <br> 사용자 정의 스크립트/도구 |
| 많은 수의 자산을 DAM으로 마이그레이션 | ✘ | ✘ | [마이그레이션 안내서](assets-migration-guide.md) |
| 데스크탑에서 자산을 신속하게 열기 | ✔✔ | ✘ |  |
| 데스크탑에서 자산을 신속하게 열고 변경 | ✔✔ | ✘ |  |

기호의 범례:

* ✔✔: 기본 솔루션
* ✔: 허용 가능한 솔루션
* ✘: 사용 사례에는 를 사용하지 않아야 합니다.

추가 참고 사항:

* (1) 자산 수가 적음: 예를 들어 프로젝트 또는 캠페인과 관련된 작은 자산 세트가 있습니다
* (2) 자산 규모 확대 예를 들어, 조직의 모든 승인된 자산
* (3) 사용 [!DNL Experience Manager] 데스크탑 앱 업로드 폴더 기능

자산 분배 사용 사례를 지원하려면 다른 솔루션을 고려해야 합니다.

* [Brand Portal](https://helpx.adobe.com/kr/experience-manager/brand-portal/user-guide.html) 구성 가능한 SaaS 추가 기능을 [!DNL Experience Manager] 자산을 게시할 자산입니다.
* 사용자 지정 솔루션은 [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) 코드 베이스입니다.
* [!DNL Experience Manager] [링크 공유](/help/assets/link-sharing.md) 링크를 사용하여 자산을 ad hoc으로 공유하려면 다음을 수행하십시오.
* [[!DNL Experience Manager] Assets 웹 인터페이스](/help/assets/managing-assets-touch-ui.md) 외부 당사에서 보안 [!DNL Experience Manager] 액세스 제어 설정 및 필요한 IT/네트워크 구성 조정을 통해 이러한 외부 사용자가 [!DNL Experience Manager].

## 주요 개념 및 사용 사례 {#key-concepts-and-use-cases}

### 일반 용어 목록 {#glossary-of-common-terms}

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change :** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change :** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. 이 문서에서 이 문서는 [!DNL Experience Manager Assets]구체적으로 언급되지 않은 한.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.

### 사용 시 고려 사항 [!DNL Experience Manager] 및 Creative Cloud 통합 {#considerations-when-using-aem-and-creative-cloud-integration}

* 자세한 내용은 [데스크탑 앱 모범 사례](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* 자세한 내용은 [Adobe Stock 통합](aem-assets-adobe-stock.md)
* [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)를 참조하십시오

Experience Manager 및 Creative Cloud 통합에 대한 모범 사례에 대한 간략한 요약입니다. 이 문서의 나머지 부분을 읽어 자세한 내용을 파악합니다.

* **For creative users, working in Photoshop, InDesign, or Illustrator:** Adobe Asset Link provides the best user experience, including clean handling of the Work-in-progress on assets checked out from [!DNL Experience Manager]
* **For simplifying access to assets from desktop for any generic file format or application:**[!DNL Experience Manager] use desktop app
* **Understand why and when to store assets in DAM:** Updates to be made available to the broader team in your organization
* **Mind the volume of assets shared:** If your use case is asset distribution, governance and security might be the most important aspects. Consider using tools built for doing that at scale, like Brand Portal.
* **Understand asset lifecycle:** Know how assets are handled in your organization by different teams
* **Handle frequent saves to assets with care:** Adobe Asset Link takes care of that for you with PS, AI, ID. For other applications, don&#39;t carry out work in progress tasks in mapped/shared folder unless you need all the changes in DAM

### 에서 Adobe Stock 자산에 액세스 [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[[!DNL Experience Manager] 및 Adobe Stock 통합](/help/assets/aem-assets-adobe-stock.md) 제공 [!DNL Experience Manager] Adobe Stock의 자산을 검색, 미리 보기, 라이선스 및 저장할 수 있는 기능을 가진 사용자 [!DNL Experience Manager]. 라이선스가 있고 저장된 Adobe Stock 자산이 Stock 메타데이터를 선택했으며, 이 메타데이터를 추가 필터로 검색하는 데 사용할 수 있습니다.

이 통합에 대한 몇 가지 중요한 사항:

* Adobe 스톡의 자산을에 저장할 때 [!DNL Experience Manager]를 입력하면 일반 규칙이 됩니다 [!DNL Experience Manager] 자산, 바이너리가 [!DNL Experience Manager] 저장소. Adobe Stock과 관련된 일부 메타데이터는에서 자산에 대해 저장됩니다 [!DNL Experience Manager]그렇지 않으면 수집 프로세스가 다른 파일과 동일하게 표시됩니다. 예를 들어, 스마트 태그가 활성화되어 있으면 저장 시 태그가 이러한 자산에 추가됩니다.
* 에 저장된 자산 [!DNL Experience Manager] 는 복사이며 Adobe Stock에 다시 연결된 링크가 아닙니다.

**Adobe Stock에서 로 저장된 자산 작업 [!DNL Experience Manager] Creative Cloud**. 이 통합은 Adobe 자산 링크와는 다르지만, Adobe 자산 링크는 Stock에서 저장된 이러한 자산을 그러한 방식으로 인식하고, Photoshop, Illustrator 또는 InDesign의 Asset Link 확장 UI에 이러한 자산에 대한 추가 메타데이터 및 Stock 아이콘을 표시합니다. 파일은 일반이므로 검색, 열기 등에 사용할 수 있습니다 [!DNL Experience Manager] 자산을 저장할 때 자산 [!DNL Experience Manager].
Adobe Stock에서 로 이미 라이선스가 부여된 자산에 액세스할 수 있을 뿐만 아니라 Adobe Asset Link 확장이 있는 Creative Cloud 앱에서 작업하는 크리에이티브 사용자 [!DNL Experience Manager]또한 Creative Cloud 라이브러리 패널을 사용하여 Adobe Stock 자산을 검색, 미리 보기 및 라이선스를 제공할 수도 있습니다.
라이선스가 있고 다음에 저장된 Adobe Stock의 자산 [!DNL Experience Manager] 액세스 가능한 광범위한 팀이 사용 가능 [!DNL Experience Manager] Creative Cloud 라이브러리 패널을 통해 Adobe Stock의 크리에이티브 라이센싱 자산을 자산 배포하는 반면, 크리에이티브는 Creative Cloud 계정에서만 기본적으로 사용할 수 있도록 합니다.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## DAM에 자산 저장 정보 {#about-storing-assets-in-a-dam}

크리에이티브 및 마케팅/LOB(Line of Business) 팀 간의 효율적인 워크플로우를 설계하고 최상의 지원 기능을 선택하려면 DAM에 자산이 저장되는 시기와 이유를 이해하는 것이 중요합니다.

### 자산이 DAM에 저장되는 이유 {#why-assets-are-stored-in-dam}

DAM에 자산을 저장하면 쉽게 액세스하고 이를 완료할 수 있습니다. Launch를 사용하면 파트너, 고객 등을 포함하는 조직 또는 에코시스템에서 다양한 사용자가 자산을 활용할 수 있습니다.

대부분의 조직은 다운스트림 마케팅/LOB 프로세스와 관련된 자산만 저장하도록 선택합니다(를 통해 웹 채널과 같은 채널에 게시) [!DNL Experience Manager] Adobe Experience Cloud, Advertising Cloud에서 제공하고 Analytics Cloud에서 측정하여 사용자/파트너에게 제공하는 사이트 또는 기타 채널). 또한 조직은 DAM에서 검토/승인 프로세스를 수행할 수 있는 자산을 저장합니다. 이 방법으로 DAM은 주로 자산을 활용할 가능성이 높고 유휴 자산을 저장하지 않는 자산을 저장합니다.

자산을 저장하는 것은 기술 및 리소스 활용률 고려도 받습니다. DAM은 메타데이터 추출, 버전 관리, 미리 보기/코드 변환 생성, 참조 관리, 액세스 제어 정보 추가 등 저장된 자산에 대한 추가 서비스를 제공합니다. 이러한 서비스는 추가 시간과 인프라 자원을 사용합니다.

모든 자산과 업데이트를 저장하는 것은 권장되지 않는 경우가 많습니다. 예를 들어 특정 자산에 대한 업데이트가 품질이 좋지 않고 과도한 리소스를 소비하는 경우 자산이 DAM에 저장되지 않을 수 있습니다.

### 자산이 DAM에 저장되는 경우 {#when-assets-are-stored-in-dam}

광고 팀(및 조직)은 일반적으로 자산 라이프사이클의 각 단계에서 자산을 저장하는 것에 관심이 없습니다. 예를 들어 다음과 같은 경우 자산이 저장되지 않습니다.

* 아직 확정되지 않았거나 실험 대상이 되는 자산
* 크리에이티브/내부 팀 검토 주기를 통과하지 못하는 자산
* 해당 자산과 비교하여 외부 팀에 자신들의 일을 대표할 더 나은 후보가 있습니다

일반적으로 다음 클래스 자산은 DAM에 저장됩니다.

* 특정 성숙기에 도달했고 공유할 준비가 된 자산입니다
* 크리에이티브 팀이 미리 선택한 자산
* 특정 계약이나 계약에 따라 마케팅에서 사용 또는 요청한 특정 자산 형식(예: RAW 파일에서 변환된 JPG 파일, PSD 원본에서 TIFF/이미지)

### 자산 업데이트가 DAM에 저장되면 {#when-updates-to-assets-are-stored-in-dam}

일반적으로, DAM 사용자 광범위한 세트와 관련된 자산만 DAM에 저장해야 합니다. 이렇게 하면 사용자(마케팅 및 유사한 기능)가 DAM 자산 타임라인에서 관련 버전만 볼 수 있습니다.

일반적으로 자산 라이프사이클의 주요 이정표에 관련된 변경 사항입니다. 예를 들어, 크리에이티브 팀이 제공하는 요청/검토를 기반으로 한 초기 크리에이티브 지원 자산이나 공식 업데이트는 DAM에서 저장하고 버전을 지정해야 합니다.

DAM에서 기존 자산의 변경 요청 이후 마케팅 팀이 검토하도록 업데이트되는 크리에이티브 팀의 업데이트는 관련 업데이트의 예입니다. 추가 참조나 이전 버전으로 되돌리려면 DAM에서 저장 및 버전을 지정해야 합니다.

다음은 일반적으로 관련이 없는 업데이트의 예입니다.

* 마케팅 리뷰를 준비하기 전에 업로드된 자산의 이전 버전
* 크리에이티브 팀이 자산을 준비하기로 결정하기 전에 진행 중인 작업 단계에서 자산을 자주 변경

### DAM에 대한 사용자 액세스 {#user-access-to-dam}

[!DNL Experience Manager] Assets는 [!DNL Experience Manager] 자산 배포. 일반적으로 엔터프라이즈 네트워크(방화벽) 내의 사용자는 DAM에 직접 액세스할 수 있습니다. 엔터프라이즈 네트워크 외부의 다른 사용자는 직접 액세스할 수 없습니다. 사용자 유형은 기술 관점에서 사용할 수 있는 통합을 결정합니다.

#### DAM에 직접 액세스할 수 있는 크리에이티브 사용자 {#creative-users-with-direct-access-to-dam}

일반적으로 내부 크리에이티브 팀 또는 내부 네트워크에 온보딩된 에이전시/크리에이티브 전문가가 다음을 포함하여 DAM 인스턴스에 액세스할 수 있습니다 [!DNL Experience Manager] 로그인.

이 경우 [!DNL Experience Manager] 데스크탑 앱을 사용하면 최종/승인된 자산에 쉽게 액세스할 수 있으며 DAM에 크리에이티브 자산을 저장할 수 있습니다.

#### DAM에 액세스할 수 없는 크리에이티브 사용자 {#creative-users-without-access-to-dam}

DAM 인스턴스에 직접 액세스할 수 없는 외부 에이전시 및 프리랜서는 승인된 자산에 액세스해야 하거나 DAM에 새 디자인을 추가해야 할 수 있습니다.

이러한 경우 를 활용할 수 있습니다 [!DNL Experience Manager]/Creative Cloud 통합을 통해 워크플로우를 개선할 수 있습니다. 이 필수 조건은 크리에이티브 사용자가 Adobe ID을 사용하고 스토리지 서비스를 제공하는 Creative Cloud 계정을 갖도록 하기 위한 것입니다.

다음 전략을 사용하여 최종/승인된 자산에 대한 액세스 권한을 제공합니다.

* 많은 자산에 대한 액세스를 제공하려면 사용 [[!DNL Experience Manager] Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), 또는 고객의 구현 [자산 공유](assets-finder-editor.md) on [!DNL Experience Manager] 인프라 게시

* 일부 자산에 대한 액세스 권한을 제공하려면: [!DNL Experience Manager] Adobe Creative Cloud과 폴더 공유 는 [!DNL Experience Manager] Assets Brand Portal 또는 자산 공유 를 참조하십시오. 이 통합과 관련된 특정 제한 사항이 있으며 이 문서에서 자세히 다룹니다.

### 사용 사례 {#use-cases}

다음 사용 사례에서는 DAM과 디자이너의 데스크탑 간의 다양한 워크플로우 유형을 설명합니다.

#### DAM의 자산을 사용하여 새 디자인 만들기 {#creating-new-designs-using-assets-from-dam}

다음 다이어그램은 디지털 자산 라이프사이클을 보여줍니다. 이 섹션에서는 크리에이티브 사용자와 DAM 사용자(마케터, LOB 사용자)가 기존 자산을 활용하여 더 많은 자산을 만들고 승인을 위해 보내는 방법을 설명합니다.

![chlimage_1-301](assets/chlimage_1-301.png)

자산 라이프사이클에는 다음 단계가 포함됩니다.

1. 승인된 자산을 크리에이티브 데스크탑에 공유: DAM의 최종 자산은 크리에이티브 사용자(데스크탑에서)가 사용할 수 있습니다
1. 새 디자인 만들기(크리에이티브 디지털 자산): 새 파일은 WIP(Work-in-Progress) 영역에 저장됩니다.
1. 승인된 자산을 새 디자인에 사용(배치)합니다. 크리에이티브 사용자는 Creative Cloud 앱에서 기존의 승인된 자산을 사용하여 새 자산을 생성합니다
1. WIP 갱신을 자주 저장: 크리에이티브 사용자는 빠르게 반복하여 파일을 자주 저장합니다. 이 단계에서 크리에이티브 사용자는 다른 사용자와 공동 작업할 수 있지만 자주 저장된 업데이트는 일반적으로 DAM 사용자에게 관심이 없습니다.
1. 자산이 크리에이티브 준비 상태에 도달하고 Creative Ready 폴더에 저장됩니다
1. 자산 업데이트 : DAM 사용자가 자산 업데이트 또는 새 파일을 사용할 수 있습니다
1. 자산이 프로덕션에 배치됩니다. DAM 프로세스입니다. DAM 프로세스는 조직에 따라 태깅, 승인 및 액세스 제어 변경을 구성할 수 있습니다. 이 단계에서 자산은 최종적인 것으로 간주되며 DAM을 활용하는 광범위한 팀에서 사용할 수 있습니다. 크리에이티브 사용자가 다른 자산을 만드는 데 사용할 수도 있습니다.

다음은 이 프로세스를 통해 자산을 관리하는 방법에 대한 몇 가지 일반적인 권장 사항입니다.

* WIP 파일에 Adobe Creative Cloud Assets 동기화된 폴더와 같은 전용 저장소 영역/시스템을 사용합니다. DAM 사용자와 관련이 없는 빈번한 업데이트는 내부가 아니라 전용 시스템에서 가장 잘 처리됩니다 [!DNL Experience Manager] 자산. WIP 자산은 Adobe Creative Cloud 데스크탑 응용 프로그램을 사용하여 로컬 디스크에 동기화하거나 로컬 저장소에 저장하는 등의 작업을 수행할 수 있습니다.
* DAM에 업로드되는 최종 자산 및 자산에 대해 별도의 폴더/공유를 사용합니다. 명확하게 하자면 최종 자산에는 자체 매핑/공유 폴더(&quot;최종&quot; 위 예제)가 있어야 하며 DAM에 다시 업로드하려는 자산에는 자체(&quot;Creative Ready&quot;)가 있어야 합니다

#### DAM에서 관리되는 기존 자산 변경 {#changing-existing-assets-managed-in-dam}

경우에 따라 DAM의 자산을 변경해야 할 수 있습니다. 해당 예는 다음과 같습니다.

* 에서 수행한 검토 및 승인에서 자산 변경 요청 [!DNL Experience Manager] 자산
* 기존 최종 자산에 대한 주요 업데이트
* 기존 파일에 대한 빠른 편집(특히 최종 승인되기 전)

이 경우 [!DNL Experience Manager] 데스크탑 앱에서는 이러한 작업을 수행하는 가장 쉬운 방법을 제공합니다.

![chlimage_1-302](assets/chlimage_1-302.png)

다음은 다이어그램에 표시된 이벤트 흐름입니다.

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for [!DNL Experience Manager] desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** DAM에서 데스크탑으로 자산을 공유하거나 원하는 애플리케이션(예: Adobe Photoshop 등)에서 데스크탑에서 직접 엽니다. 파일을 잠그려면 체크 아웃이 권장됩니다.
* **2:** 부분 업데이트: 파일을 편집하고 변경 사항을 저장합니다.
* 2단계의 대체 흐름

   * **A:** 주요 업데이트: 파일에 정교한 변경 세트가 필요한 경우 간헐적으로 저장하고 WIP 폴더/영역에 복사해야 합니다.
   * **B:** WIP 폴더의 파일에서 작업이 계속됩니다. 저장된 변경 사항이 DAM의 버전과 동기화되지 않습니다
   * **C:** 업데이트가 완료되면 파일이 다시 복사되거나 매핑된 폴더에 저장됩니다

* **3:** 자산 업데이트가 DAM에 반영됩니다. 자산의 잠금을 해제하려면 를 선택합니다.
* **4:** 자산이 프로덕션에 투입됩니다.

다음은 이 프로세스 전체에서 자산을 관리하는 방법에 대한 몇 가지 일반적인 권장 사항입니다.

* 매핑된 네트워크 공유에서 연 파일을 직접 저장하지 마십시오. [!DNL Experience Manager] 파일 변경 내용이 작은 경우를 제외하고 데스크탑 앱입니다.
* 파일을 추가로 변경하거나, 간헐적으로 저장하거나, 크리에이티브 팀과 공동 작업하려면 파일을 별도의 WIP 폴더에 복사합니다.

#### DAM에 벌크 업로드 {#bulk-upload-to-dam}

다음과 같은 일부 시나리오에서 많은 수의 파일을 동시에 DAM에 업로드해야 할 필요가 있을 수 있습니다.

* 사진 촬영 또는 더 큰 프로젝트의 결과 업로드
* 크리에이티브 에이전시에서 제공한 자산 업로드
* DAM 외부에서 선택 작업이 수행된 경우 더 큰 세트에서 선택한 자산 업로드

이 설명은 데스크탑 사용자 워크플로우의 일반적인 일부로 운영 방식으로(예: 매주 또는 모든 사진 촬영 등) 파일을 업로드하는 것을 의미합니다. 대규모 자산 마이그레이션은 여기에서 다루지 않습니다.

자산을 일괄적으로 업로드하려면 다음 기능을 활용할 수 있습니다.

* 큰/계층적 폴더를 업로드하려면 [!DNL Experience Manager] 데스크탑 앱으로서 [폴더 업로드](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) 기능. 계층 폴더 구조를 업로드할 수도 있습니다. 자산은 백그라운드로 업로드되므로 웹 브라우저 세션에 연결되어 있지 않습니다
* 단일 폴더에서 몇 개의 파일을 업로드하려면 데스크탑에서 웹 UI로 직접 드래그하거나 [!DNL Experience Manager] Assets 웹 UI.

>[!NOTE]
>
>비즈니스 요구 사항에 따라 사용자 정의 업로더를 사용할 수도 있습니다.

#### 데스크탑에서 직접 디지털 자산 관리 {#managing-digital-assets-directly-from-desktop}

네트워크 파일 공유를 사용하여 디지털 자산을 관리하는 경우, [!DNL Experience Manager] 데스크탑 앱은 편리한 대용으로 보여질 수 있습니다. 네트워크 파일 공유에서 전환할 때 [!DNL Experience Manager] Web UI는 네트워크 공유(검색, 컬렉션, 메타데이터, 공동 작업, 미리 보기 등)에서 가능한 것 이상으로 강력한 디지털 자산 관리 기능을 제공합니다 [!DNL Experience Manager] 데스크탑 앱에서는 서버측 DAM 저장소를 데스크탑의 작업과 연결하는 편리한 링크를 제공합니다.

사용하지 마십시오 [!DNL Experience Manager] 데스크탑 앱으로, [!DNL Experience Manager] 자산. 예를 들어 [!DNL Experience Manager] 여러 파일을 이동/복사하는 데스크탑 앱. 대신, [!DNL Experience Manager] Assets 웹 UI를 사용하여 폴더를 Finder/Explorer에서 네트워크 공유로 드래그하거나 [!DNL Experience Manager] 자산 폴더 업로드 기능.

#### 자산 마이그레이션 {#asset-migration}

기존 시스템에서 새 시스템으로 자산 마이그레이션을 계획하거나 서버에 저장된 많은 자산의 마이그레이션을 실행하려면 [마이그레이션 안내서](/help/assets/assets-migration-guide.md). [!DNL Experience Manager] 데스크탑 앱 및 [!DNL Experience Manager] Creative Cloud 통합은 이러한 마이그레이션을 지원하지 않습니다. 수집할 자산의 양이 많고 메타데이터 매핑, 변환 및 섭취 관련 추가 요구 사항으로 인해 마이그레이션은 다양한 도구와 접근 방식을 사용하여 처리해야 합니다.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/in/enterprise/admin-guide.html/in/enterprise/using/adobe-asset-link.ug.html)
>* [[!DNL Experience Manager] 데스크탑 앱 모범 사례](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [[!DNL Experience Manager] Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [[!DNL Experience Manager] 및 Adobe Stock 통합](aem-assets-adobe-stock.md)

