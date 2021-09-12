---
title: 조합 자산을 관리하고 하위 자산을 생성합니다.
description: InDesign, Adobe Illustrator 및 Photoshop 파일 내에서 AEM 자산에 대한 참조를 만드는 방법을 알아봅니다. 또한 페이지 뷰어 기능을 사용하여 PDF, INDD, PPT, PPTX 및 AI 파일을 포함한 여러 페이지 파일의 개별 페이지를 보는 방법을 알아봅니다.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '1408'
ht-degree: 0%

---

# 하위 자산과 조합 자산 관리 {#managing-compound-assets}

AEM(Adobe Experience Manager) 자산은 업로드된 파일에 이미 저장소에 있는 자산에 대한 참조가 포함되어 있는지 식별할 수 있습니다. 이 기능은 지원되는 파일 형식에만 사용할 수 있습니다. 업로드된 자산에 AEM 자산에 대한 참조가 있으면, 업로드된 자산과 참조된 자산 사이에 양방향 링크가 만들어집니다.

중복성을 제거하는 것 외에도, Adobe Creative Cloud 애플리케이션에서 AEM 자산을 참조하면 공동 작업이 개선되고 사용자의 효율성 및 생산성이 향상됩니다.

AEM Assets은 **양방향 참조**&#x200B;를 지원합니다. 업로드된 파일의 자산 세부 정보 페이지에서 참조된 자산을 찾을 수 있습니다. 또한 참조된 자산의 자산 세부 사항 페이지에서 AEM 자산에 대한 참조 파일을 볼 수 있습니다.

참조는 참조된 자산의 경로, 문서 ID 및 인스턴스 ID를 기반으로 해결됩니다.

## Adobe Illustrator: 자산을 참조로 추가 {#refai}

Adobe Illustrator 파일 내에서 기존 AEM 자산을 참조할 수 있습니다.

1. [AEM 데스크탑 앱](https://helpx.adobe.com/kr/experience-manager/desktop-app/aem-desktop-app.html)을 사용하여 AEM Assets 리포지토리를 로컬 시스템의 드라이브로 마운트합니다. 마운트된 드라이브 내에서 참조할 자산의 위치로 이동합니다.
1. 마운트된 드라이브에서 Illustrator 파일로 자산을 드래그합니다.
1. Illustrator 파일을 마운트된 드라이브에 저장하거나 [업로드](managing-assets-touch-ui.md#uploading-assets)를 AEM 저장소에 저장합니다.
1. 워크플로우가 완료되면 자산의 자산 세부 사항 페이지로 이동합니다. 기존 AEM 자산에 대한 참조는 **[!UICONTROL 참조]** 열의 **[!UICONTROL 종속성]** 아래에 나열됩니다.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. **[!UICONTROL 종속성]** 아래에 나타나는 참조된 자산은 현재 자산 이외의 파일에서도 참조할 수 있습니다. 자산에 대한 참조 파일 목록을 보려면 **[!UICONTROL 종속성]** 아래의 자산을 클릭하십시오.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. 도구 모음에서 **[!UICONTROL 속성 보기]** 아이콘을 클릭합니다. 속성 페이지에서 현재 자산을 참조하는 파일 목록이 **[!UICONTROL 기본]** 탭의 **[!UICONTROL 참조]** 열 아래에 표시됩니다.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign: 자산을 참조로 추가 {#add-aem-assets-as-references-in-adobe-indesign}

InDesign 파일 내에서 AEM 자산을 참조하려면 AEM 자산을 InDesign 파일로 드래그하거나 InDesign 파일을 ZIP 파일로 내보내십시오.

참조된 자산이 AEM Assets에 이미 있습니다. [InDesign 서버](indesign.md)를 구성하여 하위 자산을 추출할 수 있습니다. InDesign 파일에 포함된 자산은 하위 자산으로 추출됩니다.

>[!NOTE]
>
>InDesign 서버가 프록시된 경우 InDesign 파일의 미리 보기가 XMP 메타데이터 내에 포함됩니다. 이 경우 축소판 추출이 명시적으로 필요하지 않습니다. 그러나 InDesign 서버가 프록시되지 않은 경우 InDesign 파일에 대해 축소판을 명시적으로 추출해야 합니다.

INDD 파일이 업로드되면 리포지토리에서 `xmpMM:InstanceID` 및 `xmpMM:DocumentID` 속성을 갖는 자산을 쿼리하여 참조를 가져옵니다.

### 자산을 끌어 참조 만들기 {#create-references-by-dragging-aem-assets}

이 절차는 [Adobe Illustrator](#refai)에서 자산을 참조로 추가합니다.

### ZIP 파일을 내보내어 자산에 대한 참조를 만듭니다 {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. [워크플로우 모델 만들기](/help/sites-developing/workflows-models.md)의 단계를 수행하여 새 워크플로우를 만듭니다.
1. Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html)의 [패키지 기능을 사용하여 문서를 내보냅니다. Adobe InDesign은 문서 및 연결된 자산을 패키지로 내보낼 수 있습니다. 이 경우 내보낸 폴더에는 InDesign 파일의 하위 자산을 포함하는 `Links` 폴더가 있습니다. `Links` 폴더가 INDD 파일과 동일한 폴더에 있습니다.
1. ZIP 파일을 만들어 AEM 리포지토리에 업로드합니다.
1. 보관 해제 워크플로우를 시작합니다.
1. 워크플로우가 완료되면 링크 폴더의 참조가 자동으로 하위 자산으로 참조됩니다. 참조된 자산 목록을 보려면 InDesign 자산의 자산 세부 사항 페이지로 이동하여 [레일](/help/sites-authoring/basic-handling.md#rail-selector)을 닫습니다.

## Adobe Photoshop: 자산을 참조로 추가 {#refps}

1. WebDav 클라이언트를 사용하여 AEM Assets을 드라이브로 마운트합니다.
1. Photoshop 파일에서 AEM 자산에 대한 참조를 만들려면 Photoshop에 연결된 기능 배치 를 사용하여 마운트된 드라이브에서 해당 자산으로 이동합니다.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Photoshop 파일에 마운트된 드라이브에 저장하거나 [업로드](managing-assets-touch-ui.md#uploading-assets)를 AEM 저장소에 저장합니다.
1. 워크플로우가 완료되면 기존 AEM 자산에 대한 참조가 자산 세부 사항 페이지에 나열됩니다.

   참조된 자산을 보려면 자산 세부 사항 페이지에서 [레일](/help/sites-authoring/basic-handling.md#rail-selector)을 닫습니다.

1. 참조된 자산에는 참조된 자산 목록도 포함되어 있습니다. 참조된 자산 목록을 보려면 자산 세부 사항 페이지로 이동하고 [레일](/help/sites-authoring/basic-handling.md#rail-selector)을 닫습니다.

>[!NOTE]
>
>조합 자산 내의 자산은 문서 ID 및 인스턴스 ID를 기반으로 참조할 수도 있습니다. 이 기능은 Adobe Illustrator 및 Adobe Photoshop 버전에서만 사용할 수 있습니다. 다른 경우, AEM 이전 버전에서 수행한 것처럼 기본 조합 자산에서 연결된 자산의 상대 경로를 기반으로 참조가 수행됩니다.

## 하위 자산 만들기 {#generate-subassets}

다중 페이지 형식(PDF 파일, AI 파일, Microsoft PowerPoint 및 Apple Keynote 파일, Adobe InDesign 파일)으로 지원되는 자산의 경우, AEM은 원본 자산의 각 개별 페이지에 해당하는 하위 자산을 생성할 수 있습니다. 이러한 하위 자산은 *상위* 자산에 연결되며 다중 페이지 보기를 용이하게 합니다. 다른 모든 목적으로 하위 자산은 AEM에서 일반적인 자산처럼 처리됩니다.

하위 자산 생성은 기본적으로 비활성화됩니다. 하위 자산 생성을 활성화하려면 다음 단계를 수행하십시오.

1. 관리자로 Experience Manager에 로그인합니다. **[!UICONTROL 도구 > 워크플로우 > 모델]**&#x200B;에 액세스합니다.
1. **[!UICONTROL DAM 자산 업데이트]** 워크플로우를 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 사이드 패널 전환]** 을 클릭하고 **[!UICONTROL 하위 자산 만들기]** 단계를 찾습니다. 워크플로우를 추가합니다. **[!UICONTROL 동기화]**&#x200B;를 클릭합니다.

하위 자산을 생성하려면 다음 중 하나를 수행합니다.

* 새 자산: [!UICONTROL DAM 자산 업데이트] 워크플로우는 AEM에 업로드되는 모든 새 자산에서 실행됩니다. 새 다중 페이지 자산에 대해 하위 자산이 자동으로 생성됩니다.
* 기존 다중 페이지 자산: 다음 단계 중 하나를 수행하여 [!UICONTROL DAM 자산 업데이트] 워크플로우를 수동으로 실행합니다.

   * 자산을 선택하고 [!UICONTROL 타임라인]을 클릭하여 왼쪽 패널을 엽니다. 또는 키보드 단축키 `alt + 3`를 사용합니다. [!UICONTROL 워크플로우 시작]을 클릭하고, [!UICONTROL DAM 자산 업데이트]를 선택하고 [!UICONTROL 시작]을 클릭한 다음 [!UICONTROL 계속]을 클릭합니다.
   * 자산을 선택하고 도구 모음에서 [!UICONTROL 만들기 > 워크플로우]를 클릭합니다. 팝업 대화 상자에서 [!UICONTROL DAM 자산 업데이트] 워크플로우를 선택하고 [!UICONTROL 시작]을 클릭한 다음 [!UICONTROL 계속]을 클릭합니다.

특히 Microsoft Word 문서에서 **[!UICONTROL DAM Parse Word 문서]** 워크플로우를 실행합니다. Microsoft Word 문서의 내용에서 `cq:Page` 구성 요소를 생성합니다. 문서에서 추출된 이미지는 `cq:Page` 구성 요소에서 참조됩니다. 이러한 이미지는 하위 자산 생성이 비활성화된 경우에도 추출됩니다.

## 하위 자산 보기 {#viewing-subassets}

하위 자산은 하위 자산이 생성되고 선택한 다중 페이지 자산에 사용할 수 있는 경우에만 표시됩니다. 생성된 하위 자산을 보려면 다중 페이지 자산을 엽니다. 페이지의 왼쪽 위 영역에서 ![왼쪽 레일 아이콘](assets/do-not-localize/aem_leftrail_contentonly.png)을 클릭하고 목록에서 **[!UICONTROL 하위 자산]**&#x200B;을 클릭합니다. 목록에서 **[!UICONTROL 하위 자산]**&#x200B;을 선택하면 또는 키보드 단축키 `alt + 5`를 사용합니다.

![다중 페이지 자산에 대한 하위 자산 보기](assets/view_subassets_simulation.gif)

## 다중 페이지 파일의 페이지 보기 {#view-pages-of-a-multi-page-file}

AEM Assets의 페이지 뷰어 기능을 사용하여 PDF, INDD, PPT, PPTX 및 AI 파일과 같은 다중 페이지 파일을 볼 수 있습니다. 다중 페이지 자산을 열고 페이지의 왼쪽 위 모서리에서 **[!UICONTROL 페이지 보기]**&#x200B;를 클릭합니다. 열리는 페이지 뷰어 에는 자산의 페이지와 각 페이지를 탐색하고 확대/축소하는 컨트롤이 표시됩니다.

![다중 페이지 자산의 페이지를 보고 확인합니다](assets/view_multipage_asset_fmr.gif)

InDesign의 경우 InDesign 서버를 사용하여 페이지를 추출할 수 있습니다. 페이지 미리 보기가 InDesign 파일을 만드는 동안 저장되는 경우 페이지 추출에 InDesign Server이 필요하지 않습니다.

다음 옵션은 도구 모음, 왼쪽 레일 및 페이지 뷰어 컨트롤에서 사용할 수 있습니다.

* **[!UICONTROL AEM]** 데스크탑 앱을 사용하여 특정 하위 자산을 열거나 표시하는 데스크톱 작업입니다. AEM 데스크탑 앱을 사용하는 경우 [데스크탑 작업 구성](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) 방법을 참조하십시오.

* **** 속성 옵션을 선택하면   특정 하위 자산의 속성 페이지가 열립니다.

* **** 주석 옵션을 사용하면 특정 하위 자산에 주석을 달 수 있습니다. 상위 자산을 열어 볼 때 별도의 하위 자산에서 사용하는 주석이 수집되어 함께 표시됩니다.

* **[!UICONTROL 페이지]** 개요 선택 사항은 모든 하위 자산을 동시에 표시합니다.

* **** 왼쪽 레일을 클릭한 후 왼쪽 레일에서 타임라인 옵션 ![에 ](assets/do-not-localize/aem_leftrail_contentonly.png) 파일의 활동 스트림이 표시됩니다.

## 우수 사례 및 제한 사항 {#best-practice-limitation-tips}

* 하위 자산 생성은 모든 Experience Manager 배포에서 매우 많은 리소스를 필요로 할 수 있습니다. 복잡한 자산을 업로드할 때 하위 자산을 생성하는 경우 DAM 자산 업데이트 워크플로우에서 단계를 추가합니다. 주문형 하위 자산을 생성하는 경우 별도의 워크플로우를 만들어 하위 자산을 생성합니다. 전용 워크플로우를 사용하면 DAM 자산 업데이트 워크플로우의 다른 단계를 건너뛰고 계산 리소스를 저장할 수 있습니다.

>[!MORELIKETHIS]
>
>* [Adobe Experience Manager 데스크탑 앱 사용](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

