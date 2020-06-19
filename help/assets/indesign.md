---
title: Adobe InDesign Server와 AEM Assets 통합
description: InDesign Server와 AEM Assets을 통합하는 방법을 살펴보십시오.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 1%

---


# Adobe InDesign Server와 AEM Assets 통합 {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager(AEM) 자산에서 사용하는 항목:

* 특정 처리 작업의 로드를 배포하는 프록시입니다. 프록시는 특정 작업을 수행하기 위해 프록시 작업자와 통신하는 AEM 인스턴스와 결과를 전달하는 기타 AEM 인스턴스입니다.
* 특정 작업을 정의 및 관리하는 프록시 작업자입니다.

여기에는 다양한 작업이 포함될 수 있습니다. 예를 들어 Adobe InDesign Server를 사용하여 파일을 처리할 수 있습니다.

Adobe InDesign으로 만든 AEM Assets에 파일을 완전히 업로드하려면 프록시가 사용됩니다. 이 기능은 프록시 작업자를 사용하여 Adobe InDesign Server와 통신합니다. Adobe InDesign Server에서는 [스크립트를 실행하여 메타데이터를 추출하고 AEM Assets에 대한 다양한 변환을 생성합니다](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) . 프록시 작업자는 클라우드 구성에서 InDesign Server와 AEM 인스턴스 간의 양방향 통신을 활성화합니다.

>[!NOTE]
>
>Adobe InDesign은
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  인쇄 및/또는 디지털 배포를 위한 페이지 레이아웃을 디자인할 수 있습니다.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  이 엔진을 사용하면 InDesign에서 만든 내용을 바탕으로 프로그래밍 방식으로 자동화된 문서를 만들 수 있습니다. 이 엔진은 [ExtendScript](https://www.adobe.com/devnet/scripting.html) 엔진에 인터페이스를 제공하는 서비스로 작동합니다.\
   >  스크립트는 javascript와 유사한 ExtendScript로 작성됩니다. Indesign 스크립트에 대한 자세한 내용은 https://www.adobe.com/devnet/indesign/documentation.html#idscripting을 [참조하십시오](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>



## 추출 작동 방식 {#how-the-extraction-works}

InDesign Server를 AEM Assets과 통합하여 InDesign()으로 만든 파일을 업로드하고, 변환한 다음, 추출된 `.indd`모든 ** 미디어(예: 비디오)를 추출하여 에셋으로 저장할 수 있습니다.

>[!NOTE]
>
>이전 버전의 AEM에서 XMP 및 축소판을 추출할 수 있었지만 이제 모든 미디어를 추출할 수 있습니다.

1. AEM Assets에 `.indd` 파일을 업로드합니다.
1. 프레임워크는 SOAP(Simple Object Access Protocol)를 통해 명령 스크립트를 InDesign Server로 전송합니다.

   이 명령 스크립트는 다음을 수행합니다.

   * 파일을 `.indd` 검색합니다.
   * InDesign Server 명령 실행:

      * 구조, 텍스트 및 모든 미디어 파일이 추출됩니다.
      * PDF 및 JPG 변환이 생성됩니다.
      * HTML 및 IDML 변환이 생성됩니다.
   * 결과 파일을 AEM Assets에 다시 게시합니다.

   >[!NOTE]
   >
   >IDML은 InDesign 파일의 *모든* 것을 렌더링하는 XML 기반의 포맷입니다. 압축 압축을 사용하여 압축 패키지로 [저장됩니다](https://www.techterms.com/definition/zip) .
   >
   >자세한 내용은 [Adobe InDesign Interchange Formats INX 및 IDML을](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) 참조하십시오.

   >[!CAUTION]
   >
   >InDesign Server가 설치되지 않았거나 구성되지 않은 경우에도 AEM에 파일을 업로드할 수 `.indd` 있습니다. 그러나 생성된 변환은 `png` 제한되며, `jpeg`사용자는 `html`또는 페이지 변환을 생성할 수 `idml` 없습니다.

1. 추출 및 변환 생성 후:

   * 구조가 `cq:Page` (변환 유형)에 복제됩니다.
   * 추출된 텍스트와 파일은 AEM Assets에 저장됩니다.
   * 모든 변환은 자산 자체의 AEM Assets에 저장됩니다.

## AEM과 InDesign Server 통합 {#integrating-the-indesign-server-with-aem}

AEM Assets과 함께 사용할 수 있도록 그리고 프록시를 구성한 후 InDesign Server를 통합하려면 다음을 수행해야 합니다.

1. [InDesign Server를 설치합니다](#installing-the-indesign-server).
1. 필요한 경우 AEM Assets [워크플로우를 구성합니다](#configuring-the-aem-assets-workflow).

   기본값이 인스턴스에 적합하지 않은 경우에만 필요합니다.

1. InDesign [Server에 대한 프록시 작업자 구성을 참조하십시오](#configuring-the-proxy-worker-for-indesign-server).

### InDesign Server 설치 {#installing-the-indesign-server}

AEM에서 사용할 InDesign Server를 설치하고 시작하려면 다음을 수행하십시오.

1. Adobe InDesign Server를 다운로드하여 설치합니다.

   >[!NOTE]
   >
   >InDesign Server(CS6 이상).

1. 필요한 경우 InDesign Server 인스턴스의 구성을 사용자 정의할 수 있습니다.

1. 명령줄에서 서버를 시작합니다.

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   포트 8080에서 SOAP 플러그인 수신 대기로 서버를 시작합니다. 모든 로그 메시지와 출력은 명령 창에 직접 기록됩니다.

   >[!NOTE]
   >
   >출력 메시지를 파일에 저장하려면 리디렉션; 예를 들어, Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### AEM Assets 워크플로우 구성 {#configuring-the-aem-assets-workflow}

AEM Assets에는 InDesign을 위한 몇 가지 프로세스 단계가 **있는 미리 구성된 워크플로우 DAM Update Asset**&#x200B;이 있습니다.

* [미디어 추출](#media-extraction)
* [페이지 추출](#page-extraction)

이 워크플로우는 다양한 작성 인스턴스에서 설정에 맞게 조정할 수 있는 기본값이 있는 설정으로 설정됩니다(표준 워크플로우이므로 워크플로우 [편집에서 추가 정보를 사용할 수 있습니다](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). 기본값(SOAP 포트 포함)을 사용하는 경우 구성이 필요하지 않습니다.

설정 후 InDesign 파일을 AEM Assets(일반적인 방법 중 하나)로 업로드하면 에셋을 처리하고 다양한 변환을 준비하는 데 필요한 워크플로우가 트리거됩니다. AEM Assets에 파일을 업로드하여 구성을 테스트하여 IDS에서 만든 다른 변환이 `.indd` `<*your_asset*>.indd/Renditions`

#### 미디어 추출 {#media-extraction}

이 단계는 `.indd` 파일에서 미디어 추출을 제어합니다.

사용자 정의하려면 **[!UICONTROL 미디어 추출]** 단계의 인수 탭을 편집할 수 **[!UICONTROL 있습니다]** .

![미디어 추출 인수 및 스크립트 경로](assets/media_extraction_arguments_scripts.png)

미디어 추출 인수 및 스크립트 경로

* **ExtendScript 라이브러리**: 다른 스크립트에 필요한 간단한 http get/post 메서드 라이브러리입니다.

* **스크립트 확장**: 여기에서 다양한 스크립트 조합을 지정할 수 있습니다. InDesign Server에서 자신만의 스크립트를 실행하려면 스크립트를 다음 위치에 저장합니다 `/apps/settings/dam/indesign/scripts`.

   Indesign 스크립트에 대한 자세한 내용은 https://www.adobe.com/devnet/indesign/documentation.html#idscripting을 [참조하십시오](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>ExtendScript 라이브러리를 변경하지 마십시오. 라이브러리는 Sling과 통신하는 데 필요한 HTTP 기능을 제공합니다. 이 설정은 Adobe InDesign Server로 전송할 라이브러리를 지정합니다.

미디어 추출 워크플로우 단계에서 실행되는 `ThumbnailExport.jsx` 스크립트는 .jpg 형식으로 축소판 변환을 생성합니다. 이 변환은 AEM에 필요한 정적 변환을 생성하는 [축소판 처리] 워크플로우 단계에서 사용됩니다.

[축소판 처리] 워크플로우 단계를 구성하여 서로 다른 크기로 정적 변환을 생성할 수 있습니다. AEM Assets UI에 필요하므로 기본값을 제거하지 않아야 합니다. 마지막으로, 이미지 미리 보기 변환 삭제 워크플로우 단계에서는 .jpg 축소판 변환이 더 이상 필요하지 않으므로 제거합니다.

#### 페이지 추출 {#page-extraction}

추출된 요소에서 AEM 페이지가 만들어집니다. 추출 핸들러는 변환에서 데이터를 추출하는 데 사용됩니다(현재 HTML 또는 IDML). 그런 다음 이 데이터를 사용하여 PageBuilder를 사용하여 페이지를 만듭니다.

사용자 정의하려면 페이지 추출 단계의 **[!UICONTROL 인수]** 탭을 **편집할 수** 있습니다.

![chlimage_1-289](assets/chlimage_1-289.png)

* **페이지 추출 처리기**: 드롭다운 목록에서 사용할 핸들러를 선택합니다. 추출 핸들러는 관련 API에 의해 선택된 특정 변환에서 작동합니다 `RenditionPicker` ( `ExtractionHandler` API 참조). 기본적으로 IDML 내보내기 추출 핸들러를 사용할 수 있습니다. MediaExtract 단계에서 생성된 `IDML` 변환에서 작동합니다.

* **페이지 이름**: 결과 페이지에 지정할 이름을 지정합니다. 비워 두면 이름이 &quot;page&quot;(또는 &quot;page&quot;가 이미 있는 파생 페이지)입니다.

* **페이지 제목**: 결과 페이지에 지정할 제목을 지정합니다.

* **페이지 루트 경로**: 결과 페이지의 루트 위치에 대한 경로입니다. 비워 두면 자산의 표현물을 포함하는 노드가 사용됩니다.

* **페이지 템플릿**: 결과 페이지를 생성할 때 사용할 템플릿입니다.

* **페이지 디자인**: 결과 페이지를 생성할 때 사용할 페이지 디자인입니다.

### InDesign Server용 프록시 작업자 구성 {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>작업자는 프록시 인스턴스에 상주합니다.

1. 도구 콘솔의 왼쪽 창에서 **[!UICONTROL Cloud Service 구성을]** 확장합니다. 그런 다음 **[!UICONTROL 클라우드 프록시 구성을 확장합니다]**.

1. IDS **[!UICONTROL 작업자]** 를 두 번 클릭하여 구성을 엽니다.

1. 편집 **[!UICONTROL 을]** 클릭하여 구성 대화 상자를 열고 필요한 설정을 정의합니다.

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS 풀**: InDesign Server와 통신하는 데 사용할 SOAP 끝점입니다. 항목을 추가, 제거 및 주문할 수 있습니다.

1. **[!UICONTROL 확인]**&#x200B;을 클릭하여 저장합니다.

### Day CQ Link Externalizer 구성  {#configuring-day-cq-link-externalizer}

InDesign 서버와 AEM이 다른 호스트에서 실행되거나 두 가지 응용 프로그램이 모두 기본 포트에서 실행되지 않으면 **Day CQ Link Externalizer를** 구성하여 InDesign 서버의 호스트 이름, 포트 및 컨텐트 경로를 설정합니다.

1. URL에서 구성 관리자에 액세스합니다 `https://[AEM_server]:[port]/system/console/configMgr`.
1. 구성 **[!UICONTROL Day CQ Link Externalizer를]**&#x200B;찾아 **[!UICONTROL 편집]** 아이콘을 클릭하여 엽니다.
1. Indesign 서버의 호스트 이름과 컨텍스트 경로를 지정하고 [저장]을 **[!UICONTROL 클릭합니다]**.

   ![chlimage_1-290](assets/chlimage_1-290.png)

### InDesign Server에 대한 병렬 작업 처리 활성화 {#enabling-parallel-job-processing-for-indesign-server-s}

이제 IDS에 대한 병렬 작업 처리를 활성화할 수 있습니다.

먼저 InDesign Server에서 처리할 수 있는 최대 병렬 작업 수( `x`)를 결정해야 합니다.

* 단일 다중 프로세서 시스템에서 InDesign Server가 처리할 수 있는 최대 병렬 작업(x)은 IDS를 실행하는 프로세서 수보다 하나 작습니다.
* 여러 컴퓨터에서 ID를 실행하는 경우 사용 가능한 총 프로세서 수(예: 모든 시스템의 경우)를 계산한 다음 총 시스템 수를 빼야 합니다.

병렬 ID 작업 수를 구성하려면:

1. Felix Console의 **[!UICONTROL 구성]** 탭을 엽니다. 예를 들면 다음과 같습니다.

   `http://localhost:4502/system/console/configMgr`

1. 다음 아래에서 IDS 처리 큐를 선택합니다.

   `Apache Sling Job Queue Configuration`

1. 설정:

   * **[!UICONTROL 유형]** - `Parallel`
   * **[!UICONTROL 최대 병렬 작업]** - `<*x*>` (위에 계산됨)

1. 이러한 변경 사항을 저장합니다.
1. Adobe CS6 이상 버전에 대한 다중 세션 지원을 활성화하려면 아래 `enable.multisession.name` 확인란을 선택합니다 `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. IDS [작업자 구성에 SOAP 끝점을 추가하여 &lt; `*x*>` IDS 작업자 풀을 만듭니다](#configuring-the-proxy-worker-for-indesign-server).

   InDesign Server를 실행하는 컴퓨터가 여러 개인 경우 각 컴퓨터에 SOAP 끝점(시스템당 프로세서 수 -1)을 추가합니다.

   >[!NOTE]
   >
   >직원 풀을 사용하는 경우 차단된 IDS 작업자 목록을 활성화할 수 있습니다.
   >
   >이렇게 하려면 IDS 작업 검색을 활성화하는 구성 아래의 &quot;enable.retry.name&quot; `com.day.cq.dam.ids.impl.IDSJobProcessor.name` 확인란을 활성화합니다.
   >
   >또한 구성 아래에서 `com.day.cq.dam.ids.impl.IDSPoolImpl.name` ID를 작업 핸들러 목록에서 제외하기 전에 작업 검색의 수를 결정하는 `max.errors.to.blacklist` 매개 변수에 대해 양수 값을 설정합니다
   >
   >기본적으로 구성 가능한(`retry.interval.to.whitelist.name`) 시간(분) 후 IDS 워터의 유효성을 다시 검사해야 합니다. 작업자가 온라인에서 검색되면 차단된 목록에서 제거됩니다.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Adobe InDesign Server 10.0 이상 지원 활성화 {#enabling-support-for-indesign-server-or-higher}

InDesign Server 10.0 이상의 경우 다음 단계를 수행하여 다중 세션 지원을 활성화합니다.

1. 인스턴스에서 구성 관리자를 [!DNL Assets] 엽니다 `https://[aem_server]:[port]/system/console/configMgr`.
1. 구성을 편집합니다 `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. ids.cc.en **[!UICONTROL 사용]** 가능 옵션을 선택하고 **[!UICONTROL 저장을 클릭합니다]**.

>[!NOTE]
>
>통합 [!DNL InDesign Server] 의 경우 단일 코어 시스템에서 통합에 필요한 세션 지원 기능이 지원되지 않으므로 멀티 코어 프로세서 [!DNL Assets]를 사용하십시오.

## Experience Manager 자격 증명 구성 {#configure-aem-credentials}

Adobe InDesign 서버와의 통합을 중단하지 않고 AEM 인스턴스에서 InDesign 서버에 액세스하기 위한 기본 관리자 자격 증명(사용자 이름 및 암호)을 변경할 수 있습니다.

1. 이동 `/etc/cloudservices/proxy.html`.
1. 대화 상자에서 새 사용자 이름과 암호를 지정합니다.
1. 자격 증명을 저장합니다.
