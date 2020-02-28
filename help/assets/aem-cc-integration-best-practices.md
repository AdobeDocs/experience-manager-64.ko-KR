---
title: AEM 및 Creative Cloud 통합 모범 사례
description: AEM 배포를 Adobe Creative Cloud와 통합하여 에셋 전송 워크플로우를 간소화하고 효율성을 극대화하기 위한 모범 사례
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1f44950e3e0653df61289e1bd435d13829051365

---


# AEM 및 Creative Cloud 통합 모범 사례 {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets는 Adobe Creative Cloud와 통합하여 DAM 사용자가 크리에이티브 팀과 공동 작업을 할 수 있도록 해주는 디지털 에셋 관리(DAM 파섹) 솔루션으로 콘텐츠 제작 프로세스의 공동 작업을 간소화할 수 있습니다.

Adobe Creative Cloud는 크리에이티브 팀에게 디지털 에셋을 제작하는 데 도움이 되는 솔루션과 서비스의 에코시스템을 제공합니다. 여기에는 데스크탑 및 모바일 애플리케이션, 데스크탑 동기화 또는 웹 경험이 포함된 스토리지와 같은 클라우드 서비스, Adobe Stock과 같은 마켓플레이스가 포함되어 있습니다.

사용 사례를 기반으로 데스크탑과 엔터프라이즈급 DAM을 통합하는 기능과 연결된 워크플로우에 대한 모범 사례를 살펴보십시오.

>[!NOTE]
>
>AEM에서 Creative Cloud로의 폴더 공유는 더 이상 사용되지 않으며 이 안내서에서 다루지 않습니다. Adobe에서는 크리에이티브 사용자가 AEM에서 [관리되는 자산에](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) 액세스할 수 있도록 하려면 Adobe Asset Link [또는 AEM 데스크탑 앱과 같은 최신 기능을 사용하는 것이 좋습니다](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html) .

## 크리에이티브 전문가, 마케터 및 DAM 사용자의 공동 작업 요구 사항 {#collaboration-needs-of-creatives-marketers-and-dam-users}

| 요구 사항 | 사용 사례 | 관련 서피스 |
|---|---|---|
| 데스크탑에서 크리에이티브 전문가를 위한 경험 간소화 | 크리에이티브 전문가를 위한 DAM(AEM Assets)에서 에셋에 대한 액세스 권한을 간소화할 수 있고, 보다 광범위하게 데스크탑 사용자가 기본 에셋 제작 애플리케이션에서 작업할 수 있습니다. AEM에 대한 변경 사항을 검색, 사용(열기), 편집 및 저장하고 새 파일을 업로드하는 간편하고 간단한 방법이 필요합니다. | Win 또는 Mac 데스크탑Creative Cloud 앱 |
| Adobe Stock에서 바로 사용할 수 있는 고품질의 에셋 제공 | 마케터는 자산 확보 및 검색을 지원함으로써 컨텐츠 제작 프로세스를 가속화할 수 있습니다. 크리에이티브 전문가는 승인된 자산을 크리에이티브 툴에서 바로 사용합니다. | AEM Assets;Adobe Stock 마켓플레이스메타데이터 필드 |
| 조직별 에셋 배포 및 공유 | 내부 부서/지역 지사와 외부 파트너, 배포업체 및 대리점은 상위 조직이 공유하는 승인된 자산을 사용합니다. 조직은 보다 광범위하게 재사용할 수 있도록 작성된 자산을 안전하고 매끄럽게 공유하려고 합니다. | 브랜드 포털, 자산 공유 공유물 |

## 공동 작업 요구 사항을 지원하는 Adobe 솔루션 {#adobe-offerings-to-support-the-collaboration-need}

| 고객의 가치 제안 | Adobe 제품 | 관련 서피스 |
|---|---|---|
| 크리에이티브 사용자는 Creative Cloud 앱을 종료하지 않고도 AEM에서 자산을 검색하고, 열어 사용하고, AEM에 변경 사항을 편집 및 업로드하고, 새 파일을 AEM에 업로드합니다. | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator 및 InDesign |
| 비즈니스 사용자는 간단하게 자산 열기 및 사용, AEM에 대한 변경 사항 편집 및 업로드, 데스크톱 환경에서 새 파일 업로드를 간소화할 수 있습니다. 일반 통합을 사용하여 Adobe가 아닌 애플리케이션을 포함하여 기본 데스크탑 애플리케이션에서 모든 에셋 유형을 열 수 있습니다. | [AEM Desktop App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) | Win 및 Mac 데스크탑용 AEM 데스크탑 앱 |
| 마케터와 비즈니스 사용자는 AEM 내에서 Adobe Stock 에셋을 검색, 미리 보기, 라이선스 및 저장 및 관리할 수 있습니다. 라이선스가 부여된 에셋과 저장된 에셋은 Adobe Stock 메타데이터를 제공하므로 관리 효율성을 높일 수 있습니다. | [Adobe Experience Manager와 Adobe Stock 통합](aem-assets-adobe-stock.md) | AEM 웹 인터페이스 |

이 문서에서는 협업의 첫 두 가지 요구 사항에 대해 집중적으로 다룹니다. 규모에 따라 자산의 배포 및 소싱이 사용 사례로 간단히 언급됩니다. 이러한 요구 사항에 대한 해결 방법은 Adobe 브랜드 포털 또는 에셋 공유 공유기를 고려하십시오. Adobe Experience Manager Assets [를 사용하여](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html)자산 공유 [구성 요소,](https://adobe-marketing-cloud.github.io/asset-share-commons/) 링크 공유 [등을 기반으로](/help/assets/link-sharing.md)구축할 수 있는 솔루션, 브랜드 포털 [등의 대체 솔루션은](/help/assets/managing-assets-touch-ui.md) 특정 요구 사항에 따라 검토해야 합니다.

![AEM용 Creative Cloud 연결:사용할 기능 결정](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with AEM Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### 활용 사례 매핑

| 사용 사례 | AEM Desktop App | 폴더 공유 | 기타 솔루션 |
|---|---|---|---|
| Creative 사용자와 더 적은 수의 DAM 에셋 공유(1) | ✔✔ | ✔ |  |
| Creative 사용자와 더 많은 DAM 에셋 공유(2) | ✔✔ | ✘ | [브랜드 포털](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) <br> [자산 공유](assets-finder-editor.md) |
| DAM에 액세스할 수 있는 사용자와 DAM 에셋 공유 | ✔✔ | ✔ | [공유 링크](link-sharing.md) |
| DAM에 액세스할 수 없는 사용자와 DAM 에셋 공유 | ✘ | ✔✔ | [브랜드 포털](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) <br> [자산 공유](assets-finder-editor.md) |
| DAM에 더 적은 양의 에셋 저장 | ✔✔ | ✔ | [웹 UI 업로드](managing-assets-touch-ui.md) |
| 더 많은 양의 에셋을 DAM에 저장(3) | ✔✔ | ✘ | [웹 UI 사용자](managing-assets-touch-ui.md) 정의 스크립트 <br> /도구 업로드 |
| DAM으로 방대한 양의 에셋 마이그레이션 | ✘ | ✘ | [마이그레이션 안내서](assets-migration-guide.md) |
| 신속하게 데스크탑에서 에셋 열기 | ✔✔ | ✘ |  |
| 데스크탑에서 신속하게 에셋 열기 및 변경 | ✔✔ | ✘ |  |

심볼의 범례는 다음과 같습니다.

* ✔✔:기본 솔루션
* ✔:허용 가능한 솔루션
* ✘:사용 사례에 사용할 수 없습니다.

추가 설명:

* (1) 자산의 소수예를 들어 프로젝트 또는 캠페인과 관련된 작은 자산 집합
* (2) 자산의 수 증가예를 들어 조직에서 승인된 모든 자산을
* (3) AEM 데스크탑 앱 업로드 폴더 기능 사용

자산 배포 사용 사례를 지원하려면 다른 솔루션을 고려해야 합니다.

* [AEM](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) 자산에 대한 구성 가능한 SaaS 추가 기능을 위한 브랜드 포털에서 자산을 게시합니다.
* 사용자 지정 솔루션은 자산 공유 [공유물 코드 베이스를 기반으로](https://adobe-marketing-cloud.github.io/asset-share-commons/) 만들어집니다.
* AEM [링크 공유를](/help/assets/link-sharing.md) 사용하여 링크를 사용하여 자산을 애드혹 공유합니다.
* [AEM Access Control 설정에 의해 보안된 외부 당사자를 위한 영역과 필요한 IT/네트워크 구성 조정을 포함한 AEM Assets 웹 인터페이스를](/help/assets/managing-assets-touch-ui.md) 통해 이러한 외부 사용자가 AEM에 액세스할 수 있습니다.

## 주요 개념 및 활용 사례 {#key-concepts-and-use-cases}

### 일반 용어 용어집 {#glossary-of-common-terms}

* **** 진행 중이거나 크리에이티브 작업 진행 중(WIP):자산 라이프사이클의 한 단계로서, 자산에서 여러 변경 사항이 발생하고 일반적으로 더 광범위한 팀과 공유할 준비가 되지 않았습니다.
* **** 크리에이티브한 에셋:마케팅 또는 LOB 팀과 공유할 수 있도록 크리에이티브 팀에서 선택/승인한 자산을 더 광범위한 팀과 공유할 준비가 되었습니다.
* **** 자산 승인:DAM에 이미 업로드된 자산에 대해 실행되는 승인 프로세스는 일반적으로 브랜드 승인, 법적 승인 등을 포함합니다.
* **** 최종 자산:모든 승인/메타데이터 태그 지정을 통해 광범위한 팀에서 사용할 수 있는 에셋 이러한 자산은 DAM에 저장되며 모든(또는 관심 있는) 사용자가 사용할 수 있게 됩니다. 마케팅 채널 또는 크리에이티브 팀에서 디자인을 제작하는 데 사용할 수 있습니다.
* **** 사소한 에셋 업데이트/변경:디지털 에셋에 대한 빠르고 간단한 변경 수정 또는 경미한 편집 요청, 에셋 검토 또는 승인(예: 위치 변경, 텍스트 크기 변경, 채도/밝기, 색상 조정 등)에 대한 응답으로 종종 수행됩니다.
* **** 주요 자산 업데이트/변경:상당한 작업이 필요하고 경우에 따라 긴 시간 동안 수행해야 하는 디지털 자산의 변경. 일반적으로 여러 변경 사항이 포함됩니다. 자산을 업데이트하는 동안 여러 번 저장해야 합니다. 주요 자산 갱신으로 인해 일반적으로 자산이 WIP 단계로 들어갑니다.
* **** DAM:디지털 자산 관리 이 문서에서는 별도로 언급되지 않는 한 AEM Experience Manager 자산과 동의어입니다.
* **** 크리에이티브 사용자:Creative Cloud 앱 및 서비스를 사용하여 디지털 에셋을 제작하는 크리에이티브 전문가 경우에 따라 크리에이티브 사용자는 Creative Cloud를 사용할 수 있지만 디지털 에셋(예: 크리에이티브 디렉터 또는 크리에이티브 팀 관리자)을 만들지 않는 크리에이티브 팀의 구성원일 수 있습니다.
* **** DAM 사용자:DAM 시스템의 일반적인 사용자입니다. 조직에 따라 DAM 사용자는 마케팅 또는 비마케팅 사용자가 될 수 있습니다(예: LOB(Line-of-Business) 사용자, 도서관, 영업 사원 등).

### AEM 및 Creative Cloud 통합 사용 시 고려 사항 {#considerations-when-using-aem-and-creative-cloud-integration}

* 데스크탑 [앱 모범 사례 보기](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Adobe [Stock 통합 보기](aem-assets-adobe-stock.md)
* Adobe [Asset Link 참조](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Adobe Experience Manager 및 Creative Cloud 통합에 대한 모범 사례를 간략하게 요약해 놓은 것입니다. 이 문서의 나머지 부분에서는 이러한 내용을 자세히 살펴볼 수 있습니다.

* **** Photoshop, InDesign 또는 Illustrator에서 작업하는 크리에이티브 사용자의 경우Adobe Asset Link는 AEM에서 체크 아웃된 자산에 대한 진행 중인 작업을 깔끔하게 처리하는 등 최상의 사용자 환경을 제공합니다
* **** 모든 일반 파일 포맷 또는 애플리케이션에 대해 데스크탑에서 에셋에 대한 액세스를 간소화하기 위한 방법:aem 데스크탑 앱 사용
* **** DAM에 자산을 저장하는 이유와 시기를 이해합니다.조직의 광범위한 팀에서 사용할 수 있는 업데이트
* **** 공유된 자산의 양을 염두에 두십시오.사용 사례가 자산 배포인 경우, 거버넌스 및 보안이 가장 중요할 수 있습니다. 브랜드 포털과 같이 규모에 맞게 제작된 툴을 사용하는 것이 좋습니다.
* **** 자산 라이프사이클 이해:다양한 팀에서 조직에서 자산을 처리하는 방법 파악
* **** 에셋에 대한 빈번한 저장 처리:Adobe Asset Link는 PS, AI, ID를 통해 자동으로 처리해 줍니다. 다른 응용 프로그램의 경우 DAM의 모든 변경 사항이 필요하지 않은 경우 매핑/공유 폴더에서 진행 중인 작업을 수행하지 마십시오

### AEM 자산에서 Adobe Stock 에셋에 액세스 {#access-to-adobe-stock-assets-from-aem-assets}

[AEM 및 Adobe Stock과의 통합을](/help/assets/aem-assets-adobe-stock.md) 통해 AEM 사용자는 Adobe Stock의 자산을 검색, 미리 보기, 라이선스 및 AEM에 저장할 수 있습니다. 라이선스가 부여된 Adobe Stock 에셋과 저장된 Adobe Stock 메타데이터가 선택되었으며 추가 필터로 에셋을 검색하는 데 사용할 수 있습니다.

이 통합에 대한 몇 가지 중요 사항:

* Adobe Stock의 에셋이 AEM에 저장되면 AEM 저장소에 바이너리가 저장되는 일반 AEM Assets가 됩니다. Adobe Stock과 관련된 일부 메타데이터는 AEM의 자산에 대해 저장됩니다. 그렇지 않으면 통합 프로세스가 다른 파일과 동일하게 보입니다. 예를 들어 스마트 태그가 활성 상태인 경우 저장 시 태그가 이러한 자산에 추가됩니다.
* AEM 파섹

**Creative Cloud에서 Adobe Stock에서 AEM으로 저장된 에셋을 사용하여 작업**. 이 통합은 Adobe Asset Link와 독립적이지만 Adobe Asset Link는 이러한 에셋을 Stock에서 이러한 방식으로 저장하고 Photoshop, Illustrator 또는 InDesign에서 Adobe Asset Link 확장 UI에 이러한 에셋에 추가 메타데이터 및 Stock 아이콘을 표시합니다. 파일은 AEM에 저장될 때 일반 AEM 자산이므로 탐색, 열기 등에 사용할 수 있습니다.
Adobe Asset Link 확장 기능이 있는 Creative Cloud 앱에서 작업 중인 크리에이티브 사용자는 이미 라이선스가 부여된 Adobe Stock에서 AEM으로 에셋을 이용할 수 있을 뿐만 아니라 Creative Cloud Libraries 패널을 사용하여 Adobe Stock 에셋을 검색하고 미리 보고 라이선스를 부여할 수도 있습니다.
라이선스가 부여되고 AEM에 저장된 Adobe Stock의 에셋은 AEM Assets 배포에 액세스하는 광범위한 팀에서 사용할 수 있는 반면 Creative Cloud Libraries 패널을 통해 Adobe Stock의 크리에이티브 라이선스 에셋은 기본적으로 Creative Cloud 계정에서만 이용할 수 있습니다.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## DAM에 에셋 저장 정보 {#about-storing-assets-in-a-dam}

크리에이티브 팀과 마케팅/LOB(Line-of-Business) 팀 간의 효율적인 워크플로우를 설계하고 최상의 지원 기능을 선택하려면 DAM에 자산이 저장되는 시기와 이유를 이해하는 것이 중요합니다.

### DAM에 에셋이 저장되는 이유 {#why-assets-are-stored-in-dam}

DAM에 에셋을 저장하면 손쉽게 액세스할 수 있고 찾을 수 있습니다. 이를 통해 파트너, 고객 등이 포함된 조직 또는 에코시스템 전반의 많은 사용자가 에셋을 활용할 수 있습니다.

대부분의 조직은 다운스트림 마케팅/LOB 프로세스와 관련이 있는 자산만 저장하도록 선택합니다(AEM Sites 또는 Adobe Experience Cloud에서 제공하는 기타 채널이나 Marketing Cloud, Advertising Cloud를 통해 웹 채널에 게시하고 Analytics Cloud에서 측정하며 사용자/파트너에게 제공하는 등). 또한 조직은 DAM에서 검토/승인 프로세스를 진행할 수 있는 자산을 저장합니다. 이렇게 하면 DAM은 주로 자산을 활용할 가능성이 높은 자산을 저장하고 유휴 자산을 저장하지 않습니다.

자산 저장은 기술 및 리소스 활용률 고려 사항도 따릅니다. DAM은 메타데이터 추출, 버전 관리, 미리 보기/트랜스코딩 생성, 참조 관리, 액세스 제어 정보 추가 등 저장된 에셋에 대한 추가 서비스를 제공합니다. 이러한 서비스는 추가 시간과 인프라 리소스를 사용합니다.

종종 모든 자산 및 업데이트를 저장하는 것은 바람직하지 않습니다. 예를 들어 특정 에셋에 대한 업데이트가 품질이 좋지 않고 과도한 리소스를 소비하는 경우 DAM에 에셋이 저장되지 않을 수 있습니다.

### DAM에 에셋이 저장되는 경우 {#when-assets-are-stored-in-dam}

크리에이티브 팀(및 조직)은 일반적으로 자산 라이프사이클의 각 단계에서 자산을 저장하는 데 관심이 없습니다. 예를 들어 다음과 같은 경우 에셋을 저장하지 않습니다.

* 아직 확정되지 않았거나 실험 대상이 되는 자산
* 크리에이티브/내부 팀 검토 주기를 통과하지 못한 에셋
* 해당 자산과 비교하여 외부 팀에 자신의 업무를 대표할 후보가 더 많다

일반적으로 다음 클래스 에셋은 DAM에 저장됩니다.

* 특정 성숙도를 달성했고 공유할 준비가 된 것으로 간주되는 자산
* 크리에이티브 팀이 미리 선택한 에셋
* 특정 계약 또는 계약에 따라 마케팅 팀에서 사용 또는 요청한 특정 에셋 포맷(예: RAW 파일에서 변환된 JPG 파일, TIFF/PSD 원본 이미지)

### 에셋 업데이트가 DAM에 저장되어 있는 경우 {#when-updates-to-assets-are-stored-in-dam}

일반적으로 DAM 사용자의 광범위한 집합과 관련된 에셋에 대한 업데이트만 DAM에 저장해야 합니다. 따라서 사용자(마케팅 및 유사 기능)가 DAM 자산 타임라인에서 관련 버전만 볼 수 있습니다.

일반적으로 자산 라이프사이클의 주요 마일스톤과 관련된 변경 사항입니다. 예를 들어 크리에이티브 팀에서 제공하는 요청/검토를 기반으로 한 초기 크리에이티브 에셋 또는 공식 업데이트를 DAM에 저장하고 버전을 지정해야 합니다.

DAM의 기존 에셋 변경 요청 후 마케팅 팀이 검토할 크리에이티브 팀의 업데이트는 관련 업데이트의 예입니다. DAM에서 저장 및 버전을 관리하여 나중에 참조하거나 이전 버전으로 되돌려야 합니다.

다음은 일반적으로 관련이 없는 업데이트의 예입니다.

* 마케팅 검토를 위해 업로드된 자산의 이전 버전
* 크리에이티브 팀이 에셋을 준비할지 결정하기 전에 진행 중인 작업 단계의 에셋을 자주 크리에이티브하게 변경

### DAM에 대한 사용자 액세스 {#user-access-to-dam}

AEM Assets는 AEM Assets 배포에 대한 액세스를 기반으로 두 가지 유형의 사용자를 지원합니다. 일반적으로 엔터프라이즈 네트워크(방화벽) 내의 사용자는 DAM에 직접 액세스할 수 있습니다. 엔터프라이즈 네트워크 외부의 다른 사용자는 직접 액세스할 수 없습니다. 사용자 유형은 기술적 관점에서 사용할 수 있는 통합을 결정합니다.

#### DAM에 직접 액세스할 수 있는 크리에이티브 사용자 {#creative-users-with-direct-access-to-dam}

일반적으로 사내 크리에이티브 팀 또는 내부 네트워크에 연결된 에이전시/크리에이티브 전문가는 AEM 로그인을 비롯한 DAM 인스턴스에 액세스할 수 있습니다.

이러한 경우 AEM 데스크탑 앱을 사용하면 최종/승인 자산에 손쉽게 액세스할 수 있고 크리에이티브한 에셋을 DAM에 저장할 수 있습니다.

#### DAM을 이용할 수 없는 크리에이티브 사용자 {#creative-users-without-access-to-dam}

DAM 인스턴스에 직접 액세스하지 않고 외부 에이전시 및 프리랜서가 승인된 자산을 액세스해야 하거나 DAM에 새로운 디자인을 추가해야 할 수 있습니다.

이러한 경우 AEM/Creative Cloud 통합을 활용하여 워크플로우를 향상시킬 수 있습니다. 이 사전 요구 사항은 크리에이티브 사용자가 Adobe ID를 가지고 있고 스토리지 서비스가 포함된 Creative Cloud 계정을 보유하기 위한 것입니다.

다음 전략을 사용하여 최종/승인된 자산에 대한 액세스를 제공합니다.

* 대량의 자산에 대한 액세스를 제공하려면AEM [Assets 브랜드 포털](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html)사용 또는 고객의 AEM 게시 [인프라에서](assets-finder-editor.md) 자산 공유구현

* 일부 자산에 대한 액세스 권한을 제공하려면Adobe Creative Cloud와 AEM 폴더 공유를 AEM Assets 브랜드 포털 또는 자산 공유 외에 사용할 수 있습니다. 이 통합에 대한 특정 제한 사항은 이 문서에서 자세히 다룹니다.

### Use Cases {#use-cases}

다음 사용 사례에서는 DAM과 디자이너의 데스크탑 간 다양한 유형의 워크플로우를 설명합니다.

#### DAM 파섹 {#creating-new-designs-using-assets-from-dam}

다음 다이어그램은 디지털 자산 라이프사이클을 보여줍니다. 이 문서에서는 크리에이티브 사용자와 DAM 사용자(마케터, LOB 사용자)가 기존 자산을 활용하여 더 많은 자산을 만들고 승인을 위해 보내는 방법을 설명합니다.

![chlimage_1-301](assets/chlimage_1-301.png)

자산 라이프사이클에는 다음 단계가 포함됩니다.

1. 승인된 자산을 크리에이티브 데스크탑에 공유:DAM 파섹
1. 새 디자인 만들기(크리에이티브 디지털 에셋):새 파일은 WIP(작업 진행 중) 영역에 저장됩니다.
1. 승인된 자산을 새 디자인에 사용(배치)합니다.크리에이티브 사용자는 Creative Cloud 앱에서 승인된 기존 에셋을 사용하여 새 에셋을 만듭니다
1. WIP 업데이트 자주 저장:크리에이티브 사용자는 신속하게 반복하고 파일을 자주 저장합니다. 이 단계에서 크리에이티브 사용자는 다른 사용자와 공동 작업을 할 수 있지만 자주 저장되는 업데이트는 일반적으로 DAM 사용자에게 관심이 없습니다.
1. 에셋이 크리에이티브 준비 상태에 도달하고 Creative Ready 폴더에 저장됩니다.
1. 자산 업데이트:DAM의 사용자가 에셋 업데이트 또는 새 파일을 사용할 수 있음
1. 자산을 프로덕션에 배치:DAM 프로세스는 조직에 따라 태그 지정, 승인 및 액세스 제어를 변경할 수 있습니다. 이 단계에서 자산은 최종본으로 간주되며 DAM을 활용하는 광범위한 팀에서 사용할 수 있습니다. 또한 크리에이티브 사용자가 다른 에셋을 만드는 데 사용할 수 있습니다.

다음은 이 프로세스를 통해 자산을 관리하는 방법에 대한 일반적인 몇 가지 권장 사항입니다.

* WIP 파일에 대해 Adobe Creative Cloud Assets 동기화된 폴더와 같은 전용 스토리지 영역/시스템을 사용합니다.DAM 사용자와 관련이 없는 빈번한 업데이트는 AEM Assets가 아닌 전용 시스템에서 가장 많이 처리됩니다. WIP 자산은 Adobe Creative Cloud 데스크탑 애플리케이션, 로컬 스토리지에 저장 등을 사용하여 로컬 디스크에 동기화할 수 있습니다.
* DAM에 업로드된 최종 자산 및 자산에 대해 별도의 폴더/공유 사용:명확히 말하자면, 최종 자산은 자체 매핑/공유 폴더(&quot;최종&quot; 예 위에 있음)가 있어야 하며, DAM에 다시 업로드될 에셋은 자체 폴더(&quot;Creative Ready&quot;)가 있어야 합니다.

#### DAM에서 관리하는 기존 에셋 변경 {#changing-existing-assets-managed-in-dam}

경우에 따라 DAM의 자산을 변경해야 할 수 있습니다. 예:

* AEM 자산에서 수행한 검토 및 승인에서 자산 변경 요청
* 기존 최종 자산에 대한 주요 업데이트
* 기존 파일에 대한 빠른 편집(특히 최종 승인 전)

이러한 경우 AEM 데스크톱 앱은 이러한 작업을 수행하는 가장 쉬운 방법을 제공합니다.

![chlimage_1-302](assets/chlimage_1-302.png)

다이어그램에 설명된 이벤트 흐름은 다음과 같습니다.

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for AEM desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **** 1:DAM에서 데스크탑으로 에셋을 공유하거나 원하는 애플리케이션(예: Adobe Photoshop 등)에서 데스크탑에서 직접 열 수 있습니다. 파일을 잠그려면 체크 아웃하는 것이 좋습니다.
* **** 2:사소한 업데이트:파일을 편집하고 변경 내용을 저장합니다.
* 2단계에 대한 대체 흐름

   * **** A:주요 업데이트:파일에 세부 변경 사항 세트가 필요한 경우 간헐적으로 저장하고 WIP 폴더/영역에 복사해야 합니다.
   * **** B:WIP 폴더의 파일에서 작업이 계속됩니다. 저장된 변경 내용이 DAM의 버전에 동기화되지 않습니다.
   * **** C:업데이트가 완료되면 파일이 다시 복사되거나 매핑된 폴더에 저장됩니다

* **** 3:자산 업데이트는 DAM에 반영됩니다. 자산을 체크 인하여 잠금을 해제합니다.
* **** 4:에셋을 프로덕션에 배치

다음은 이 프로세스 전체에서 자산을 관리하는 방법에 대한 일반적인 몇 가지 권장 사항입니다.

* AEM 데스크톱 앱에서 연 파일을 AEM 데스크톱 앱으로 매핑하는 네트워크 공유에서 직접 저장하지 않도록 합니다. 단, 파일을 변경한 내용이 작지 않습니다.
* 추가 변경, 간헐적 저장, 크리에이티브 팀과 공동 작업을 하려면 파일을 별도의 WIP 폴더에 복사합니다.

#### DAM에 일괄 업로드 {#bulk-upload-to-dam}

다음과 같은 경우 DAM에 더 많은 파일을 동시에 업로드해야 할 필요가 있을 수 있습니다.

* 사진 또는 대규모 프로젝트의 결과 업로드
* 크리에이티브 에이전시에서 제공하는 에셋 업로드
* DAM 외부에서 선택한 자산을 선택한 경우 더 큰 세트에서 선택한 자산 업로드

이 설명은 데스크탑 사용자의 워크플로우에서 정상적인 부분으로 운영 방식으로(예: 매주 또는 모든 사진 촬영 등) 파일을 업로드하는 것을 말합니다. 대규모 자산 마이그레이션은 여기에서 다루지 않습니다.

자산을 일괄 업로드하려면 다음 기능을 활용할 수 있습니다.

* 대용량/계층적 폴더를 업로드하려면 폴더 업로드 기능을 제공하는 AEM 데스크톱 앱을 [사용하십시오](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) . 계층 폴더 구조를 업로드할 수도 있습니다. 자산은 백그라운드에서 업로드되므로 웹 브라우저 세션에 연결되지 않습니다
* 단일 폴더에서 몇 개의 파일을 업로드하려면 데스크탑에서 웹 UI로 직접 드래그하거나 AEM 자산 웹 UI에서 만들기 옵션을 사용합니다.

>[!NOTE]
>
>비즈니스 요구 사항에 따라 사용자 정의 업로더를 사용할 수도 있습니다.

#### 데스크탑에서 바로 디지털 자산 관리 {#managing-digital-assets-directly-from-desktop}

네트워크 파일 공유를 사용하여 디지털 자산을 관리하는 경우, AEM 데스크탑 앱으로 매핑된 네트워크 공유를 사용하는 것만으로도 편리한 대체물이 될 수 있습니다. 네트워크 파일 공유에서 전환할 때 AEM Web UI는 네트워크 공유(검색, 컬렉션, 메타데이터, 공동 작업, 미리 보기 등)에서 가능한 것 이상으로 풍부한 디지털 자산 관리 기능을 제공하고 AEM 데스크탑 앱은 서버측 DAM 저장소를 데스크탑의 작업과 연결하는 편리한 링크를 제공합니다.

AEM 데스크톱 앱을 사용하여 AEM 자산의 네트워크 공유에서 직접 자산을 관리하지 마십시오. 예를 들어 AEM 데스크톱 앱을 사용하여 여러 파일을 이동/복사하지 마십시오. 대신 AEM 자산 웹 UI를 사용하여 폴더를 Finder/탐색기에서 네트워크 공유로 드래그하거나 AEM 자산 폴더 업로드 기능을 사용합니다.

#### 에셋 마이그레이션 {#asset-migration}

기존 시스템에서 새 시스템으로 에셋 마이그레이션을 계획 및 실행하거나 서버에 저장된 많은 양의 에셋을 마이그레이션하려면 마이그레이션 [안내서를 참조하십시오](/help/assets/assets-migration-guide.md). AEM 데스크탑 앱 및 AEM에서 Creative Cloud로의 통합은 이러한 마이그레이션을 지원하지 않습니다. 인제스트할 많은 양의 자산과 메타데이터 매핑, 변형 및 인제스트에 대한 추가 요구 사항으로 인해 마이그레이션은 다양한 툴과 접근 방식을 사용하여 처리해야 합니다.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/in/enterprise/using/adobe-asset-link.html)
>* [AEM 데스크탑 앱 우수 사례](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [AEM 및 Adobe Stock 통합](aem-assets-adobe-stock.md)

