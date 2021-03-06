---
title: Dynamic Media 구성 - Scene7 모드
description: Dynamic Media - Scene7 모드를 구성하는 방법을 알아봅니다.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: b0f0c6e4-77c8-40db-a9f4-699d1a633571
feature: Configuration,Scene7 Mode
role: Admin,User,Developer
source-git-commit: a750c5425e33c2a115aab581b71862c1d30cf166
workflow-type: tm+mt
source-wordcount: '5589'
ht-degree: 1%

---

# Dynamic Media 구성 - Scene7 모드 {#configuring-dynamic-media-scene-mode}

개발, 스테이징 및 라이브 프로덕션과 같은 다양한 환경에 대해 Adobe Experience Manager 설정을 사용하는 경우 각 환경에 대해 Dynamic Media Cloud Services을 구성해야 합니다.

## Dynamic Media 아키텍처 다이어그램 - Scene7 모드 {#architecture-diagram-of-dynamic-media-scene-mode}

다음 아키텍처 다이어그램은 Dynamic Media - Scene7 모드 작동 방식을 설명합니다.

새 아키텍처를 통해 Experience Manager은 마스터 자산을 관리하고 자산 처리 및 게시를 위해 Dynamic Media과 동기화합니다.

1. 마스터 자산이 Experience Manager에 업로드되면 Dynamic Media에 복제됩니다. 이때 Dynamic Media은 이미지의 비디오 인코딩 및 동적 변형과 같은 모든 자산 처리 및 표현물 생성을 처리합니다.
1. 표현물이 생성되면 Experience Manager이 원격 Dynamic Media 표현물에 안전하게 액세스하고 미리 볼 수 있습니다(바이너리가 Experience Manager 인스턴스로 다시 전송되지 않음).
1. 컨텐츠를 게시 및 승인할 준비가 되면, 컨텐츠를 전달 서버에 푸시하고 CDN에 컨텐츠를 캐시하도록 Dynamic Media 서비스를 트리거합니다.

![chlimage_1](assets/chlimage_1.png)

## Scene7 모드에서 Dynamic Media 활성화 {#enabling-dynamic-media-in-scene-mode}

[Dynamic Media는 기본적으로 비활성화됩니다. ](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) Dynamic Media 기능을 사용하려면 활성화해야 합니다.

>[!WARNING]
>
>Dynamic Media - Scene7 모드는 *Experience Manager 작성자 인스턴스에만 사용됩니다*. 따라서 Experience Manager 작성자 인스턴스에서 `runmode=dynamicmedia_scene7`Experience Manager 게시 인스턴스가 아닌 *을 구성합니다.*

Dynamic Media을 활성화하려면 터미널 창에 다음을 입력하여 명령줄에서 `dynamicmedia_scene7` 실행 모드를 사용하여 Experience Manager을 시작해야 합니다(사용된 예제 포트는 4502).

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## (선택 사항) Dynamic Media 사전 설정 및 구성을 6.3에서 6.4로 마이그레이션 다운타임 없음 {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Experience Manager Dynamic Media을 6.3에서 6.4로 업그레이드하는 경우(다운타임 없이 배포할 수 있는 기능이 포함됨) 다음 curl 명령을 실행하여 모든 사전 설정 및 구성을 `/etc`에서 `/conf`로 CRXDE Lite에 마이그레이션하십시오.

>[!NOTE]
>
>호환성 모드에서 Experience Manager 인스턴스를 실행하는 경우(즉, 호환성 패키지가 설치되어 있으므로) 이러한 명령을 실행할 필요가 없습니다.

사용자 지정 사전 설정 및 구성을 `/etc`에서 `/conf`(으)로 마이그레이션하려면 다음 Linux® curl 명령을 실행하십시오.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

호환성 패키지를 사용하거나 사용하지 않고 모든 업그레이드의 경우 다음 명령을 실행하여 기본 뷰어 사전 설정을 복사할 수 있습니다.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## (선택 사항) 벌크 자산 마이그레이션용 기능 팩 18912 설치 {#installing-feature-pack}

기능 팩 18912을 사용하면 FTP를 통해 자산을 벌크하거나 Dynamic Media - 하이브리드 모드 또는 Dynamic Media Classic에서 Experience Manager의 Dynamic Media - Scene7 모드로 자산을 마이그레이션할 수 있습니다. Adobe Professional Services에서 이용할 수 있습니다.

자세한 내용은 [벌크 자산 마이그레이션용 기능 팩 18912 설치](bulk-ingest-migrate.md) 를 참조하십시오.

## Dynamic Media Cloud Services 구성 {#configuring-dynamic-media-cloud-services}

Dynamic Media Cloud Services을 구성하기 전에 암호를 변경합니다. Dynamic Media 자격 증명으로 프로비저닝 이메일을 받은 후 암호를 변경하려면 [Dynamic Media Classic 데스크탑 애플리케이션에 로그인](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)해야 합니다. 프로비저닝 전자 메일에 제공된 암호는 시스템에서 생성되며 임시 암호만 사용할 수 있습니다. Dynamic Media Cloud Service이 올바른 자격 증명으로 설정되도록 암호를 업데이트하는 것이 중요합니다.

>[!NOTE]
>
>기본적으로 Cloud Services의 구성 경로는 `/content/dam`입니다. 다른 구성 경로는 Dynamic Media - Scene7 모드에서 지원하지 않습니다.

**Dynamic Media Cloud Services을 구성하려면:**

1. Experience Manager 작성자 인스턴스에서 Experience Manager 로고를 탭하여 전역 탐색 콘솔에 액세스하고 도구 아이콘을 탭한 다음, **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media 구성]**&#x200B;을 누릅니다.
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 **[!UICONTROL global]**&#x200B;을 탭하고 **[!UICONTROL 만들기]**&#x200B;를 탭합니다. [!UICONTROL global] 왼쪽에 있는 폴더 아이콘을 탭하거나 선택하지 마십시오.
1. [!UICONTROL Dynamic Media 구성 만들기] 페이지에서 제목, Dynamic Media 계정 이메일 주소 및 암호를 입력합니다. 지역을 선택합니다. 이 정보는 프로비저닝 이메일에서 Adobe이 제공합니다. 이메일을 받지 못한 경우 Adobe 고객 지원 센터에 문의하십시오.

   **[!UICONTROL Dynamic Media에 연결]**&#x200B;을 누릅니다.

   >[!NOTE]
   >
   >Dynamic Media 자격 증명으로 프로비저닝 이메일을 받은 후 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 회사 계정에 로그인하여 암호를 변경합니다. 프로비저닝 전자 메일에 제공된 암호는 시스템에서 생성되며 임시 암호만 사용할 수 있습니다. Dynamic Media Cloud Service이 올바른 자격 증명으로 설정되도록 암호를 업데이트하는 것이 중요합니다.

1. 연결에 성공하면 다음을 설정할 수도 있습니다.

   * **[!UICONTROL 회사]**  - Dynamic Media 계정의 이름입니다. 다양한 하위 브랜드, 사업부 또는 다양한 스테이징/프로덕션 환경에 대한 여러 Dynamic Media 계정이 있을 수 있습니다.
   * **[!UICONTROL 회사 루트 폴더 경로]**
   * **[!UICONTROL 자산 게시]**  -  **** 즉시 옵션은 자산이 업로드되면 시스템이 자산을 수집하여 URL/포함을 즉시 제공함을 의미합니다. 자산을 게시하는 데 필요한 사용자 개입이 없습니다. **[!UICONTROL 활성화 시]** 옵션은 URL/포함 링크가 제공되기 전에 먼저 자산을 명시적으로 게시해야 함을 의미합니다.
   * **[!UICONTROL 보안 미리 보기 서버]**  - 보안 변환 미리 보기 서버의 URL 경로를 지정할 수 있습니다. 즉, 표현물이 생성되면 Experience Manager이 원격 Dynamic Media 표현물에 안전하게 액세스하고 미리 볼 수 있습니다(바이너리가 Experience Manager 인스턴스로 다시 전송되지 않음).

      회사의 서버나 특수 서버를 사용하기 위해 특별히 마련된 경우가 아니면 기본 설정을 사용하는 것이 좋습니다.
   >[!NOTE]
   >
   >DMS7에서는 버전 관리를 지원하지 않습니다. 또한, [!UICONTROL Dynamic Media 구성 편집] 페이지의 **[!UICONTROL 자산 게시]**&#x200B;가 **[!UICONTROL 활성화 시]**&#x200B;로 설정된 경우에만 지연된 활성화가 적용되며, 처음 자산이 활성화될 때까지 지연됩니다.
   >
   >자산이 활성화되면 모든 업데이트가 즉시 S7 Delivery에 실시간으로 게시됩니다.

   ![dynamicmediaconfiguration2업데이트됨](assets/dynamicmediaconfiguration2updated.png)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.
1. Dynamic Media 컨텐츠를 게시하기 전에 안전하게 미리 보려면 Dynamic Media에 연결하려면 Experience Manager 작성자 인스턴스를 &quot;&quot;허용 목록에 추가하다해야 합니다.

   * [Dynamic Media Classic 데스크탑 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 계정에 로그인합니다. 자격 증명 및 로그인 세부 정보는 프로비저닝 시 Adobe이 제공했습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.
   * 페이지의 오른쪽 상단 근처에 있는 탐색 모음에서 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 게시 설정]** > **[!UICONTROL 이미지 서버]**&#x200B;를 누릅니다.
   * 이미지 서버 게시 페이지의 게시 컨텍스트 드롭다운 목록에서 **[!UICONTROL 테스트 이미지 제공]**&#x200B;을 선택합니다.
   * 클라이언트 주소 필터에 대해 **[!UICONTROL 추가]**&#x200B;를 누릅니다.
   * 주소를 활성화(설정)하려면 확인란을 선택합니다. Experience Manager 작성자 인스턴스(Dispatcher IP 아님)의 IP 주소를 입력합니다.
   * **[!UICONTROL 저장]**&#x200B;을 누릅니다.

이제 기본 구성을 완료했습니다. Dynamic Media - Scene7 모드를 사용할 준비가 되었습니다.

구성을 추가로 사용자 지정하려면 원할 경우 Dynamic Media - Scene7 모드](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode)에서 [(선택 사항) 고급 설정 구성 아래에서 작업을 선택적으로 완료할 수 있습니다.

## (선택 사항) Dynamic Media - Scene7 모드에서 고급 설정 구성 {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Dynamic Media - Scene7 모드의 구성 및 설정을 추가 사용자 지정하거나 성능을 최적화하려는 경우 다음 옵션 작업 중 하나 이상을 완료할 수 있습니다.

* [(선택 사항) Dynamic Media 설정 및 구성 - Scene7 모드 설정](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [(선택 사항) Dynamic Media - Scene7 모드 성능 조정](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [(선택 사항) 복제할 자산 필터링](#optional-filtering-assets-for-replication)

### (선택 사항) Dynamic Media 설정 및 구성 - Scene7 모드 설정</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

**dynamic_media_scene7** 실행 모드에 있는 경우 Dynamic Media Classic 사용자 인터페이스를 사용하여 Dynamic Media 설정을 변경합니다.

위의 작업 중 일부는 [Dynamic Media Classic 데스크탑 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 계정에 로그인해야 합니다.

설정 및 구성 작업은 다음과 같습니다.

* [이미지 서버에 대한 게시 설정](#publishing-setup-for-image-server)
* [응용 프로그램 일반 설정 구성](#configuring-application-general-settings)
* [색상 관리 구성](#configuring-color-management)
* [지원되는 형식에 대한 MIME 유형 편집](#editing-mime-types-for-supported-formats)
* [지원되지 않는 형식에 대한 MIME 유형 추가](#adding-mime-types-for-unsupported-formats)
* [이미지 세트 및 스핀 세트를 자동으로 생성하기 위해 일괄처리 집합 사전 설정 만들기](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### 이미지 서버에 대한 게시 설정 {#publishing-setup-for-image-server}

게시 설정 설정은 Dynamic Media에서 기본적으로 자산이 전달되는 방법을 결정합니다. 지정된 설정이 없으면 Dynamic Media은 게시 설정에 정의된 기본 설정에 따라 자산을 전달합니다. 예를 들어, 해상도 속성을 포함하지 않는 이미지 전달에 대한 요청에서 기본 개체 해상도 설정이 있는 이미지가 생성됩니다.

게시 설정을 구성하려면: Dynamic Media Classic에서 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 게시 설정]** > **[!UICONTROL 이미지 서버]**&#x200B;를 탭합니다.

이미지 서버 화면은 이미지 전달을 위한 기본 설정을 설정합니다. 각 설정에 대한 설명은 사용자 인터페이스를 참조하십시오.

* **[!UICONTROL 요청 속성]**  - 이러한 설정은 서버에서 전달할 수 있는 이미지에 제한을 적용합니다.
* **[!UICONTROL 기본 요청 속성]**  - 이 설정은 이미지의 기본 모양과 관련이 있습니다.
* **[!UICONTROL 일반 축소판 속성]**  - 이 설정은 축소판 이미지의 기본 모양과 관련이 있습니다.
* **[!UICONTROL 카탈로그 필드의 기본값]**  - 이 설정은 이미지의 해상도 및 기본 축소판 유형과 관련이 있습니다.
* **[!UICONTROL 색상 관리 속성]**  - 이 설정은 사용할 ICC 색상 프로파일을 결정합니다.
* **[!UICONTROL 호환성 속성]**  - 이 설정을 사용하면 이전 버전과의 호환성을 위해 텍스트 레이어의 이전 및 이후 단락을 버전 3.6의 단락과 동일하게 처리할 수 있습니다.
* **[!UICONTROL 로컬라이제이션 지원]**  - 이 설정을 사용하여 여러 로케일 속성을 관리할 수 있습니다. 또한 로케일 맵 문자열을 지정하여 뷰어의 다양한 도구 설명에 대해 지원할 언어를 정의할 수 있습니다. 로컬라이제이션 지원 설정에 대한 자세한 내용은 [로컬라이제이션 지원을 구현할 때의 중요 고려 사항](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#image-server)을 참조하십시오.

#### 응용 프로그램 일반 설정 구성 {#configuring-application-general-settings}

[!UICONTROL 응용 프로그램 일반 설정] 페이지를 열려면 Dynamic Media Classic 전역 탐색 모음에서 **[!UICONTROL 설정]** > **[!UICONTROL 응용 프로그램 설정]** > **[!UICONTROL 일반 설정]**&#x200B;을 탭합니다.

**[!UICONTROL 서버]**  - 계정 프로비저닝에서 Dynamic Media은 자동으로 회사에 할당된 서버를 제공합니다. 이러한 서버는 웹 사이트 및 애플리케이션에 대한 URL 문자열을 구성하는 데 사용됩니다. 이러한 URL 호출은 계정에만 적용됩니다. Experience Manager 지원에 의해 명시적으로 지시하지 않는 한 서버 이름을 변경하지 마십시오.

**[!UICONTROL 이미지 덮어쓰기]**  - Dynamic Media에서는 두 파일의 이름이 같을 수 없습니다. 각 항목의 URL ID(파일 이름에서 확장자를 뺀 경우)는 고유해야 합니다. 다음 옵션은 교체 자산을 업로드하는 방법을 지정합니다. 원본과 중복이 되는지 여부 중복 자산은 &quot;-1&quot;로 이름이 변경됩니다(예를 들어 chair.tif는 chair-1.tif로 이름이 변경됨). 이러한 옵션은 원래 폴더와 다른 폴더에 업로드된 자산이나 원래 파일 확장명(예: JPG, TIF 또는 PNG)이 다른 자산에 영향을 줍니다.

* **[!UICONTROL 현재 폴더에 덮어쓰기, 동일한 기본 이미지 이름/확장]**  - 이 옵션은 교체를 위한 가장 엄격한 규칙입니다. 교체 이미지를 원본과 동일한 폴더에 업로드하고 교체 이미지의 파일 확장명이 원본과 동일해야 합니다. 이러한 요구 사항이 충족되지 않으면 복제본이 만들어집니다.

>[!NOTE]
>
>Experience Manager과 일관성을 유지하려면 **[!UICONTROL 현재 폴더에 덮어쓰기, 동일한 기본 이미지 이름/확장]**&#x200B;을 선택합니다.

* **[!UICONTROL 모든 폴더에 덮어쓰기, 동일한 기본 자산 이름/확장]**  - 대체 이미지의 파일 확장명이 원본 이미지와 동일해야 합니다(예: 은  `chair.jpg` 을 대신하지  `chair.jpg`   `chair.tif`않음). 그러나 대체 이미지를 원본과 다른 폴더에 업로드할 수 있습니다. 업데이트된 이미지는 새 폴더에 있습니다. 파일을 원래 위치에서 더 이상 찾을 수 없습니다.
* **[!UICONTROL 확장자와 관계없이 동일한 기본 자산 이름을 가진 임의의 폴더에 덮어쓰기]**  - 이 옵션은 가장 포괄적인 대체 규칙입니다. 대체 이미지를 원본과 다른 폴더에 업로드하고, 다른 파일 확장자를 가진 파일을 업로드하고, 원래 파일을 바꿀 수 있습니다. 원본 파일이 다른 폴더에 있는 경우 대체 이미지는 업로드된 새 폴더에 있습니다.

**[!UICONTROL 기본 색상 프로필]**  -  [자세한 내용은 ](#configuring-color-management) 색상 관리 구성을 참조하십시오.

>[!NOTE]
>
>기본적으로 자산의 세부 사항 보기에서 **[!UICONTROL Viewers]**&#x200B;를 선택하면 시스템은 **[!UICONTROL 표현물]** 및 15개의 뷰어 사전 설정을 선택할 때 15개의 표현물을 표시합니다. 이 제한을 늘릴 수 있습니다. [표시](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) 또는 [표시되는 뷰어 사전 설정의 수를 늘립니다](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### 색상 관리 구성 {#configuring-color-management}

Dynamic Media 색상 관리를 통해 자산의 색상을 올바르게 지정할 수 있습니다. 색상 교정을 통해 수집된 자산은 색상 공간(RGB, CMYK, 회색)과 포함된 색상 프로파일을 유지합니다. 동적 변환을 요청하면 이미지 색상이 CMYK, RGB 또는 회색 출력을 사용하여 대상 색상 공간으로 수정됩니다. [이미지 사전 설정 구성](managing-image-presets.md)을 참조하십시오.

**이미지를 요청할 때 색상 보정을 사용하도록 기본 색상 속성을 구성하려면 다음을 수행하십시오.**

1. [Dynamic Media Classic 데스크탑 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 프로비저닝 중에 제공된 자격 증명을 사용하여 계정에 로그인합니다. **[!UICONTROL 설정]** > **[!UICONTROL 응용 프로그램 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 게시 설정]** 영역을 확장하고 **[!UICONTROL 이미지 서버]**&#x200B;를 선택합니다. 게시 인스턴스의 기본값을 설정할 때 **[!UICONTROL 게시 컨텍스트]**&#x200B;를 **[!UICONTROL 이미지 제공]**&#x200B;으로 설정합니다.
1. 변경해야 하는 속성으로 스크롤합니다. 예를 들어 **[!UICONTROL 색상 관리 속성]** 영역의 속성이 있습니다.

   다음 색상 교정 속성을 설정할 수 있습니다.

   * [!UICONTROL CMYK 기본 색상 공간]  - 기본 CMYK 색상 프로파일의 이름
   * [!UICONTROL 회색 음영 기본 색상 공간]  - 기본 회색 색상 프로필의 이름
   * [!UICONTROL RGB 기본 색상 공간]  - 기본 RGB 색상 프로필의 이름
   * [!UICONTROL 색상 변환 렌더링 의도]  - 렌더링 의도를 지정합니다. 허용되는 값은 `perceptual`, `relative` `colometric`, `saturation` 및 `absolute colometric`입니다. Adobe은 `relative` 을 기본값으로 권장합니다.

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

예를 들어 **[!UICONTROL 기본 색상 공간 RGB]**&#x200B;을 `sRGB`로 설정하고 **[!UICONTROL CMYK 기본 색상 공간]**&#x200B;을 `WebCoated`로 설정할 수 있습니다.

이렇게 하면 다음 작업이 수행됩니다.

* RGB 및 CMYK 이미지에 색상 교정을 활성화합니다.
* 색상 프로필이 없는 RGB 이미지는 `sRGB` 색상 공간에 있는 것으로 간주됩니다.
* 색상 프로파일이 없는 CMYK 이미지는 `WebCoated` 색상 공간에 있는 것으로 간주됩니다.
* RGB 출력을 반환하는 동적 표현물은 `sRGB` 색상 공간에 반환됩니다.
* CMYK 출력을 반환하는 동적 표현물은 `WebCoated` 색상 공간에 반환됩니다.

#### 지원되는 형식에 대한 MIME 유형 편집 {#editing-mime-types-for-supported-formats}

Dynamic Media에서 처리할 자산 유형을 정의하고 고급 자산 처리 매개 변수를 사용자 지정할 수 있습니다. 예를 들어 자산 처리 매개 변수를 지정하여 다음을 수행할 수 있습니다.

* Adobe PDF을 eCatalog 자산으로 변환합니다.
* 개인화를 위해 Adobe Photoshop 문서(.PSD)을 배너 템플릿 자산으로 변환합니다.
* Adobe Illustrator 파일(.AI) 또는 Adobe Photoshop Encapsulated PostScript® 파일(.EPS)을 래스터화합니다.
* [비디오 ](/help/assets/video-profiles.md) 프로필 및  [이미징 ](/help/assets/image-profiles.md) 프로필 을 사용하여 각각 비디오 및 이미지 처리를 정의할 수 있습니다.

[자산 업로드](managing-assets-touch-ui.md#uploading-assets)를 참조하십시오.

**지원되는 형식에 대한 MIME 유형을 편집하려면:**

1. Experience Manager에서 Experience Manager 로고를 탭하여 전역 탐색 콘솔에 액세스한 다음, **[!UICONTROL 도구]**(망치) 아이콘을 탭하고 **[!UICONTROL 일반]** > **[!UICONTROL CRXDE Lite]**&#x200B;로 이동합니다.
1. 왼쪽 레일에서 다음 위치로 이동합니다.

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. `mimeTypes` 폴더에서 MIME 유형을 선택합니다.
1. CRXDE Lite 페이지의 오른쪽의 아래 부분:

   * **[!UICONTROL enabled]** 필드를 두 번 클릭합니다. 기본적으로 모든 자산 MIME 유형이 활성화되어 있습니다(**[!UICONTROL true]**&#x200B;로 설정). 즉, 자산은 처리를 위해 Dynamic Media에 동기화됩니다. 이 자산 MIME 유형을 처리하지 않으려면 이 설정을 **[!UICONTROL false]**&#x200B;로 변경하십시오.
   * **[!UICONTROL jobParam]**&#x200B;을 두 번 클릭하여 연결된 텍스트 필드를 엽니다. 지정된 MIME 유형에 사용할 수 있는 허용되는 처리 매개 변수 값 목록은 [지원되는 MIME 유형](assets-formats.md#supported-mime-types)을 참조하십시오.

1. 다음 중 하나를 수행하십시오.

   * 추가 MIME 유형을 편집하려면 3-4단계를 반복합니다.
   * CRXDE Lite 페이지의 메뉴 모음에서 **[!UICONTROL 모두 저장]**&#x200B;을 누릅니다.

1. 페이지의 왼쪽 위 모서리에서 **[!UICONTROL CRXDE Lite]**&#x200B;을 눌러 Experience Manager으로 돌아갑니다.

#### 지원되지 않는 형식에 대한 사용자 지정 MIME 유형 추가 {#adding-custom-mime-types-for-unsupported-formats}

Experience Manager Assets에서 지원되지 않는 형식에 대한 사용자 지정 MIME 유형을 추가할 수 있습니다. CRXDE Lite에 추가하는 새 노드가 Experience Manager에 의해 삭제되지 않도록 하려면 **[!UICONTROL image_]** 앞에 MIME 유형을 이동하고 해당 활성화된 값이 **[!UICONTROL false]**&#x200B;로 설정됩니다.

**지원되지 않는 형식에 대한 사용자 지정 MIME 유형을 추가하려면 다음을 수행합니다.**

1. Experience Manager에서 **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**&#x200B;을 클릭합니다.

   ![웹 콘솔](assets/2019-08-02_16-13-14.png)

1. 새 브라우저 탭이 **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성]** 페이지에 열립니다.

   ![웹 콘솔 구성 Experience Manager](assets/2019-08-02_16-17-29.png)

1. 페이지에서 아래로 스크롤하여 이름 **[!UICONTROL Adobe CQ Scene7 Asset MIME 유형 서비스]**&#x200B;로 이동합니다. 이름 오른쪽의 **[!UICONTROL 구성 값 편집]** (연필 아이콘)을 누릅니다.

   ![구성 값 편집](assets/2019-08-02_16-44-56.png)

1. **[!UICONTROL Adobe CQ Scene7 Asset MIME 유형 서비스]** 페이지에서 더하기 기호 아이콘 `+`을 클릭합니다. 새 MIME 유형을 추가하기 위해 더하기 기호를 클릭하는 테이블의 위치는 매우 작습니다.

   ![더하기 기호 아이콘](assets/2019-08-02_16-27-27.png)

1. 방금 추가한 빈 텍스트 필드에 `DWG=image/vnd.dwg`을 입력합니다.

   예제 `DWG=image/vnd.dwg`는 데모용으로만 사용됩니다. 여기에 추가하는 MIME 유형은 다른 지원되지 않는 형식일 수 있습니다.

   ![MIME 유형 추가 예](assets/2019-08-02_16-36-36.png)

1. 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   이때 열려 있는 Adobe Experience Manager 웹 콘솔 구성 페이지가 있는 브라우저 탭을 닫을 수 있습니다.

1. 열려 있는 Experience Manager 콘솔이 있는 브라우저 탭으로 돌아갑니다.

1. Experience Manager에서 **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL CRXDE Lite]**&#x200B;를 클릭합니다.

   ![CRXDE Lite 페이지](assets/2019-08-02_16-55-41.png)

1. 왼쪽 레일에서 다음 위치로 이동합니다.

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. MIME 유형 `image_vnd.dwg`을(를) 트리의 `image_` 바로 위에 놓습니다.

   ![MIME 유형 드래그](assets/CRXDELite_CQDOC-14627.png)

1. 트리에서 여전히 MIME 유형 `image_vnd.dwg`이 선택된 상태에서 **[!UICONTROL 속성]** 탭의 **[!UICONTROL enabled]** 행의 **[!UICONTROL 값]** 열 헤더 아래에 있는 값을 두 번 클릭하여 **[!UICONTROL 값]** 드롭다운 목록을 엽니다.

1. 필드에 `false`을 입력합니다(또는 드롭다운 목록에서 `false` 선택).

   ![False 값](assets/2019-08-02_16_60_30.png)

1. CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.

#### 이미지 세트 및 스핀 세트를 자동으로 생성하기 위해 일괄처리 집합 사전 설정 만들기 {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

자산을 Dynamic Media에 업로드하는 동안 일괄처리 집합 사전 설정을 사용하여 이미지 세트 또는 스핀 세트 만들기를 자동화합니다.

먼저 자산을 집합으로 그룹화하는 방법에 대한 이름 지정 규칙을 정의합니다. 그런 다음, 사전 설정된 레서피에서 정의된 이름 지정 규칙과 일치하는 이미지를 사용하여 세트를 구성하는 방법을 정의하는 고유한 이름이 있는 자체 포함된 지침 세트인 배치 세트 사전 설정을 생성할 수 있습니다.

파일을 업로드하면 Dynamic Media에서 활성 사전 설정에서 정의된 명명 규칙과 일치하는 모든 파일이 있는 세트를 자동으로 만듭니다.

**기본 이름 지정 구성**

배치 집합 사전 설정 배합식에서 사용되는 기본 이름 지정 규칙을 만듭니다. 배치 세트 사전 설정 정의에서 선택한 기본 이름 지정 규칙은 회사에서 배치 세트를 생성하는 데 필요한 모든 것입니다. 사용자가 정의하는 기본 이름 지정 규칙을 사용하도록 배치 세트 사전 설정이 생성됩니다. 회사에서 정의한 기본 이름에 예외가 있는 경우 특정 컨텐츠 세트에 필요한 대체 사용자 지정 이름 지정 규칙을 사용하여 일괄처리 집합 사전 설정을 최대 많이 만들 수 있습니다.

일괄처리 집합 사전 설정 기능을 사용하는 데 기본 이름 지정 규칙을 설정할 필요는 없지만 이 규칙을 사용하여 집합에서 그룹화할 명명 규칙의 요소를 최대한 정의할 수 있습니다. 이렇게 하면 배치 세트 생성을 간소화할 수 있습니다.

대신 사용 가능한 양식 필드가 없는 **[!UICONTROL 코드 보기]**&#x200B;를 사용할 수 있습니다. 이 보기에서는 완전히 정규 표현식을 사용하여 이름 지정 규칙 정의를 만듭니다.

두 요소를 정의할 수 있습니다. **[!UICONTROL Match]** 및 **[!UICONTROL 기본 이름]**. 이러한 필드를 사용하면 이름 지정 규칙의 모든 요소를 정의하고 해당 요소가 포함된 집합의 이름을 지정하는 데 사용되는 규칙의 부분을 식별할 수 있습니다. 회사의 개별 이름 지정 규칙은 이러한 각 요소에 대해 하나 이상의 정의 라인을 사용할 수 있습니다. 고유한 정의에 많은 줄을 사용하고 고유한 요소로 그룹화합니다. 예를 들어 주 이미지, 색상 요소, 대체 보기 요소 및 견본 요소가 있습니다.

**기본 이름을 구성하려면**

1. [Dynamic Media Classic 데스크탑 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 계정에 로그인합니다.

   자격 증명 및 로그인 세부 정보는 프로비저닝 시 Adobe이 제공했습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.

1. 페이지 상단 근처에 있는 탐색 모음에서 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 배치 설정]** > **[!UICONTROL 기본 이름 지정]**&#x200B;을 누릅니다.
1. **[!UICONTROL 양식 보기]** 또는 **[!UICONTROL 코드 보기]**&#x200B;를 선택하여 각 요소에 대한 정보를 보고 입력하는 방법을 지정합니다.

   **[!UICONTROL 코드 보기]** 확인란을 선택하여 양식 선택과 함께 작성되는 정규식 값을 볼 수 있습니다. 양식 보기에서 어떤 이유로든 사용자를 제한하는 경우 이름 지정 규칙의 요소를 정의하는 데 도움이 되도록 이러한 값을 입력하거나 변경할 수 있습니다. 값을 양식 보기에서 구문 분석할 수 없는 경우 양식 필드는 비활성 상태가 됩니다.

   >[!NOTE]
   >
   >비활성화된 양식 필드는 정규 표현식이 올바른지 확인하지 않습니다. 결과 라인 뒤에 각 요소에 대해 작성하는 정규 표현식의 결과가 표시됩니다. 전체 정규 표현식은 페이지 하단에 표시됩니다.

1. 필요에 따라 각 요소를 확장하고 사용할 이름 지정 규칙을 입력합니다.
1. 필요에 따라 다음 중 하나를 수행합니다.

   * **[!UICONTROL 추가]**&#x200B;를 눌러 요소에 대한 다른 이름 지정 규칙을 추가합니다.
   * 요소에 대한 이름 지정 규칙을 삭제하려면 **[!UICONTROL 제거]**&#x200B;를 누릅니다.

1. 다음 중 하나를 수행하십시오.

   * **[!UICONTROL 다른 이름으로 저장]**&#x200B;을 탭하고 사전 설정의 이름을 입력합니다.
   * 기존 사전 설정을 편집하는 경우 **[!UICONTROL 저장]**&#x200B;을 누릅니다.

**배치 집합 사전 설정 생성**

Dynamic Media은 일괄처리 집합 사전 설정을 사용하여 뷰어에 표시할 이미지 세트(대체 이미지, 색상 옵션, 360spin)로 자산을 구성합니다. 일괄처리 집합 사전 설정은 Dynamic Media의 자산 업로드 프로세스와 함께 자동으로 실행됩니다.

일괄처리 집합 사전 설정을 생성, 편집 및 관리할 수 있습니다. 배치 세트 사전 설정 정의에는 두 가지 유형이 있습니다. 하나는 사용자가 설정한 기본 이름 지정 규칙에 대한 것이고 다른 하나는 사용자가 즉석에서 생성하는 사용자 지정 이름 지정 규칙에 대한 것입니다.

양식 필드 메서드를 사용하여 묶음 세트 사전 설정을 정의하거나 정규 표현식을 사용할 수 있는 코드 메서드를 정의할 수 있습니다. 기본 이름 지정에서와 같이, [!UICONTROL 코드 보기]를 [!UICONTROL 양식 보기]에서 정의하는 동시에 선택하고 정규 표현식을 사용하여 정의를 작성할 수 있습니다. 또는 한 보기를 선택 취소하여 단독 또는 다른 보기를 사용할 수 있습니다.

**배치 세트 사전 설정을 생성하려면**

1. [Dynamic Media Classic 데스크탑 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 계정에 로그인합니다.

   자격 증명 및 로그인 세부 정보는 프로비저닝 시 Adobe이 제공했습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.

1. 페이지 상단 근처에 있는 탐색 모음에서 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 배치 설정]** > **[!UICONTROL 배치 설정 사전 설정]**&#x200B;을 누릅니다.

   [!UICONTROL 세부 사항 페이지의 오른쪽 위 모서리에 설정된 ] 보기   양식이 기본 보기입니다.

1. 사전 설정 목록 패널에서 **[!UICONTROL 추가]**&#x200B;를 눌러 화면 오른쪽의 **[!UICONTROL 세부 정보]** 패널에서 정의 필드를 활성화합니다.
1. **[!UICONTROL 세부 정보]** 패널의 **[!UICONTROL 사전 설정 이름]** 필드에 사전 설정의 이름을 입력합니다.
1. **[!UICONTROL 일괄 처리 집합 유형]** 드롭다운 메뉴에서 사전 설정 유형을 선택합니다.
1. 다음 중 하나를 수행하십시오.

   * 이전에 **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 일괄처리 집합 사전 설정]** > **[!UICONTROL 기본 이름 지정]**&#x200B;에서 설정한 기본 이름 지정 규칙을 사용하는 경우 **[!UICONTROL 자산 이름 지정 규칙]**&#x200B;을 확장한 다음 **[!UICONTROL 파일 이름 지정]** 드롭다운 목록에서 **[!UICONTROL 기본]**&#x200B;을 탭합니다.
   * 사전 설정 **[!UICONTROL 자산 이름 지정 규칙]**&#x200B;을 설정한 다음 **[!UICONTROL 파일 이름 지정]** 드롭다운 목록에서 **[!UICONTROL 사용자 지정]**&#x200B;을 탭하여 새 이름 지정 규칙을 정의합니다.

1. [!UICONTROL 시퀀스 순서]에 대해 세트가 Dynamic Media에 그룹화된 후 이미지가 표시되는 순서를 정의합니다.

   기본적으로 자산은 영숫자 순서로 지정됩니다. 그러나 쉼표로 구분된 정규 표현식 목록을 사용하여 순서를 정의할 수 있습니다.

1. **[!UICONTROL 이름 지정]** 및 **[!UICONTROL 생성 규칙]**&#x200B;에 대해 **[!UICONTROL 자산 이름 지정 규칙]**&#x200B;에서 정의한 기본 이름에 접미사 또는 접두사를 지정합니다. 또한 Dynamic Media 폴더 구조 내에서 세트가 만들어지는 위치를 정의합니다.

   많은 수의 세트를 정의하는 경우 자산 자체가 포함된 폴더와 구분하십시오. 예를 들어, 이미지 세트 폴더를 만들고 생성된 세트를 여기에 지정합니다.

1. **[!UICONTROL 세부 정보]** 패널에서 **[!UICONTROL 저장]**&#x200B;을 탭합니다.
1. 새 사전 설정 이름 옆에 있는 **[!UICONTROL Active]**&#x200B;을 누릅니다.

   사전 설정을 활성화하면 Dynamic Media에 자산을 업로드할 때 세트 사전 설정이 적용되어 세트가 생성됩니다.

**2D 스핀 세트의 자동 생성을 위한 배치 세트 사전 설정 생성**

배치 세트 유형 **[!UICONTROL 다축 스핀 세트]**&#x200B;를 사용하여 2D 스핀 세트 생성을 자동화하는 레서피를 생성할 수 있습니다. 이미지 그룹화에서는 이미지 자산이 다차원 배열의 해당 위치에서 제대로 정렬되도록 행 및 열 정규 표현식을 사용합니다. 다축 스핀 세트에 있어야 하는 최소 또는 최대 행 또는 열 수는 없습니다.

예를 들어 `spin-2dspin`이라는 이름의 다중 축 스핀 세트를 만든다고 가정합니다. 3개의 행을 포함하는 스핀 세트 이미지 세트와 행당 12개의 이미지가 있습니다. 이미지의 이름은 다음과 같습니다.

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

이 정보를 사용하여 [!UICONTROL 배치 세트 유형] 레서피를 다음과 같이 만들 수 있습니다.

![chlimage_1-1](assets/chlimage_1-1.png)

스핀 세트의 공유 자산 이름 부분에 대한 그룹이 **[!UICONTROL 일치]** 필드에 추가됩니다(강조 표시된 대로). 행과 열이 포함된 자산 이름의 변수 부분이 각각 **[!UICONTROL Row]** 및 **[!UICONTROL Column]** 필드에 추가됩니다.

스핀 세트가 업로드되고 게시되면 **[!UICONTROL 업로드 작업 옵션]** 대화 상자의 **[!UICONTROL 일괄 세트 사전 설정]** 아래에 나열된 2D 스핀 세트 레서피의 이름을 활성화합니다.

**2D 스핀 세트의 자동 생성을 위한 배치 세트 사전 설정을 생성하려면:**

1. [Dynamic Media Classic 데스크탑 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 계정에 로그인합니다.

   자격 증명 및 로그인 세부 정보는 프로비저닝 시 Adobe이 제공했습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.

1. 페이지 상단 근처에 있는 탐색 모음에서 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 배치 설정]** > **[!UICONTROL 배치 설정 사전 설정]**&#x200B;을 누릅니다.

   [!UICONTROL 세부 사항 페이지의 오른쪽 위 모서리에 설정된 ] 보기   양식이 기본 보기입니다.

1. **[!UICONTROL 사전 설정 목록]** 패널에서 **[!UICONTROL 추가]**&#x200B;를 탭하여 화면 오른쪽의 **[!UICONTROL 세부 정보]** 패널에서 정의 필드를 활성화합니다.
1. **[!UICONTROL 세부 정보]** 패널의 [!UICONTROL 사전 설정 이름] 필드에 사전 설정의 이름을 입력합니다.
1. **[!UICONTROL 일괄 처리 집합 유형]** 드롭다운 메뉴에서 **[!UICONTROL 자산 집합]**&#x200B;을 선택합니다.
1. **[!UICONTROL 하위 유형]** 드롭다운 목록에서 **[!UICONTROL 다중 축 스핀 세트]**&#x200B;를 선택합니다.
1. **[!UICONTROL 자산 이름 지정 규칙]**&#x200B;을 확장한 다음 **[!UICONTROL 파일 이름 지정]** 드롭다운 목록에서 **[!UICONTROL 사용자 지정]**&#x200B;을 탭합니다.
1. **[!UICONTROL Match]** 및 선택적으로 **[!UICONTROL 기본 이름]** 속성을 사용하여 그룹을 구성하는 이미지 자산 이름에 대한 정규 표현식을 정의합니다.

   예를 들어 리터럴 Match 정규 표현식은 다음과 같을 수 있습니다.

   `(w+)-w+-w+`

1. **[!UICONTROL 행 열 위치]**&#x200B;를 확장한 다음 2D 스핀 세트 배열 내에서 이미지 자산의 위치에 대한 이름 형식을 정의합니다.

   파일 이름에서 행 또는 열 위치를 포함하려면 괄호를 사용합니다.

   예를 들어 행 정규 표현식의 경우 다음과 같을 수 있습니다.

   `\w+-R([0-9]+)-\w+`

   또는

   `\w+-(\d+)-\w+`

   열 정규 표현식의 경우 다음과 같을 수 있습니다.

   `\w+-\w+-C([0-9]+)`

   또는

   `\w+-\w+-C(\d+)`

   이러한 표현식은 데모용으로만 사용될 수 있습니다. 원하는 대로 정규 표현식을 만들 수 있습니다.

   >[!NOTE]
   >
   >행과 열 정규 표현식의 조합이 다차원 스핀 세트 배열 내의 자산의 위치를 결정할 수 없는 경우, 해당 자산이 세트에 추가되지 않고 오류가 기록됩니다.

1. **[!UICONTROL 이름 지정]** 및 **[!UICONTROL 생성 규칙]**&#x200B;에 대해 **[!UICONTROL 자산 이름 지정 규칙]**&#x200B;에서 정의한 기본 이름에 접미사 또는 접두사를 지정합니다.

   또한 Dynamic Media Classic 폴더 구조 내에서 스핀 세트가 만들어지는 위치를 정의합니다.

   많은 수의 세트를 정의하는 경우 자산 자체가 포함된 폴더와 구분하십시오. 예를 들어, 생성된 세트를 여기에 배치할 스핀 세트 폴더를 만듭니다.

1. **[!UICONTROL 세부 정보]** 패널에서 **[!UICONTROL 저장]**&#x200B;을 탭합니다.
1. 새 사전 설정 이름 옆에 있는 **[!UICONTROL Active]**&#x200B;을 누릅니다.

   사전 설정을 활성화하면 Dynamic Media에 자산을 업로드할 때 세트 사전 설정이 적용되어 세트가 생성됩니다.

### (선택 사항) Dynamic Media - Scene7 모드 성능 조정 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Dynamic Media - Scene7 모드가 원활하게 실행되도록 하려면 다음 동기화 성능/확장성 미세 조정 팁을 권장합니다.

* 다양한 파일 형식을 처리하기 위해 사전 정의된 작업 매개 변수 업데이트.
* 사전 정의된 Granite 워크플로우(비디오 자산) 큐 작업자 스레드를 업데이트합니다.
* 사전 정의된 Granite 임시 워크플로우(이미지 및 비비디오 자산) 큐 작업자 스레드를 업데이트합니다.
* Dynamic Media Classic 서버에 대한 최대 업로드 연결 업데이트.

#### 다양한 파일 형식 처리를 위해 사전 정의된 작업 매개 변수 업데이트

파일을 업로드할 때 처리 속도를 높이기 위해 작업 매개 변수를 조정할 수 있습니다. 예를 들어 PSD 파일을 업로드하지만 템플릿으로 처리하려는 경우가 아니라면 레이어 추출을 false(off)로 설정할 수 있습니다. 이 경우 튜닝된 작업 매개 변수는 다음과 같이 나타납니다. `process=None&createTemplate=false`

템플릿 만들기를 설정하려면 다음 매개 변수를 사용하십시오. `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`

<!-- REMOVED BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe은 PDF, PostScript® 및 PSD 파일에 다음과 같은 &quot;튜닝된&quot; 작업 매개 변수를 사용하는 것을 권장합니다.

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| 파일 유형 | 권장 작업 매개 변수 |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

이러한 매개 변수를 업데이트하려면 [MIME 유형 기반 Assets/Dynamic Media Classic 업로드 작업 매개 변수 지원](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support)의 단계를 따르십시오.

#### Granite Transient 워크플로 큐 업데이트 {#updating-the-granite-transient-workflow-queue}

Granite Transit 워크플로우 큐는 **[!UICONTROL DAM 자산 업데이트]** 워크플로우에 사용됩니다. Dynamic Media에서 이미지 수집 및 처리에 사용됩니다.

**Granite Transient 워크플로우 큐를 업데이트하려면:**

1. [https://&lt;server>/system/console/configMgr](http://localhost:4502/system/console/configMgr)로 이동하여 **[!UICONTROL 큐를 검색합니다. Granite Transient 워크플로 큐]**.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. **[!UICONTROL 최대 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   **[!UICONTROL 최대 병렬 작업]**&#x200B;을 늘려서 Dynamic Media에 파일이 많이 업로드되도록 적절히 지원할 수 있습니다. 정확한 값은 하드웨어 용량에 따라 다릅니다. 초기 마이그레이션 또는 1회 벌크 업로드와 같은 특정 시나리오에서는 큰 값을 사용할 수 있습니다. 그러나 큰 값(예: 코어 수의 2배)을 사용하면 다른 동시 활동에 부정적인 영향을 줄 수 있습니다. 따라서 특정 사용 사례를 기반으로 값을 테스트 및 조정합니다.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

#### Granite 워크플로우 큐 업데이트 {#updating-the-granite-workflow-queue}

Granite 워크플로우 큐는 비임시 워크플로우에 사용됩니다. Dynamic Media에서는 **[!UICONTROL Dynamic Media 인코딩 비디오]** 워크플로우를 사용하여 비디오를 처리하는 데 사용됩니다.

**Granite Workflow 큐를 업데이트하려면:**

1. `https://<server>/system/console/configMgr`으로 이동하여 **[!UICONTROL 큐를 검색합니다. Granite Workflow 큐]**.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. **[!UICONTROL 최대 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   기본적으로 최대 병렬 작업 수는 사용 가능한 CPU 코어 수에 따라 달라집니다. 예를 들어 4 코어 서버에서 두 개의 작업자 스레드를 할당합니다. (0.0에서 1.0 사이의 값은 비율 기반이거나 둘 이상의 숫자가 작업자 스레드 수를 할당합니다.)

   대부분의 사용 사례의 경우 0.5 기본 설정으로도 충분합니다.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

#### Scene7 업로드 연결 업데이트 {#updating-the-scene-upload-connection}

Scene7 업로드 연결 설정은 Experience Manager Assets을 Dynamic Media Classic 서버에 동기화합니다.

**Scene7 업로드 연결을 업데이트하려면:**

1. 다음으로 이동 `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. [!UICONTROL 연결 수] 필드 및/또는 [!UICONTROL 활성 작업 시간 초과] 필드에서 원하는 대로 숫자를 변경합니다.

   **[!UICONTROL 연결 수]** 설정은 Dynamic Media 업로드를 위해 허용되는 최대 HTTP 연결 수를 제어합니다. 일반적으로 10개의 연결의 사전 정의된 값으로 충분합니다.

   **[!UICONTROL 활성 작업 시간 초과]** 설정은 업로드된 Dynamic Media 자산이 게재 서버에 게시될 때까지 기다리는 시간을 결정합니다. 이 값은 기본적으로 2100초 또는 35분입니다.

   대부분의 사용 사례에서 2100으로 설정하면 충분합니다.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

### (선택 사항) 복제할 자산 필터링 {#optional-filtering-assets-for-replication}

Dynamic Media이 아닌 배포에서는 Experience Manager 작성 환경에서 모든 *자산(이미지와 비디오 모두)을 Experience Manager 게시 노드에 복제합니다.* Experience Manager 게시 서버에서도 자산을 전달하므로 이 워크플로우가 필요합니다.

그러나 Dynamic Media 배포에서는 자산이 Cloud Service 방식으로 전달되므로 동일한 자산을 Experience Manager 게시 노드에 복제할 필요가 없습니다. 이러한 &quot;하이브리드 게시&quot; 워크플로우를 통해 추가 스토리지 비용과 자산 복제 처리 시간이 늘어납니다. 사이트 페이지와 같은 다른 컨텐츠는 Experience Manager 게시 노드에서 계속 제공됩니다.

필터는 *제외* 자산이 Experience Manager 게시 노드에 복제되지 않도록 하는 방법을 제공합니다.

#### 복제에 기본 자산 필터 사용 {#using-default-asset-filters-for-replication}

이미징, 비디오 또는 둘 다에 Dynamic Media을 사용하는 경우 Adobe이 제공하는 기본 필터를 그대로 사용할 수 있습니다. 다음 필터는 기본적으로 활성화되어 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>필터</strong></td> 
   <td><strong>MIME 유형</strong></td> 
   <td><strong>표현물</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media 이미지 제공</td> 
   <td><p>필터 이미지</p> <p>필터 세트</p> <p> </p> </td> 
   <td><p><strong>image/</strong>로 시작</p> <p><strong>application/</strong>을 포함하고 <strong>set</strong>로 끝납니다.</p> </td> 
   <td>곧바로 사용할 수 있는 "필터 이미지"(대화형 이미지를 포함하여 단일 이미지 자산에 적용) 및 "필터 세트"(스핀 세트, 이미지 세트, 혼합 미디어 세트 및 회전 메뉴 세트에 적용)는 다음과 같습니다. 
    <ul> 
     <li>복제에서 원본 이미지 및 정적 이미지 표현물을 제외합니다.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media 비디오 제공</td> 
   <td>필터 비디오</td> 
   <td><strong>video/</strong>로 시작합니다.</td> 
   <td>곧바로 사용할 수 있는 "filter-video"는 
    <ul> 
     <li>원본 비디오 및 정적 축소판 그림 표현물을 복제에서 제외합니다.<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>필터는 MIME 유형에 적용되며 경로별로 지정할 수 없습니다.

#### 복제를 위한 자산 필터 사용자 지정 {#customizing-asset-filters-for-replication}

1. Experience Manager에서 Experience Manager 로고를 탭하여 전역 탐색 콘솔에 액세스하고 **[!UICONTROL 도구]** 아이콘을 탭하고 **[!UICONTROL 일반]** > **[!UICONTROL CRXDE Lite]**&#x200B;로 이동합니다.
1. 왼쪽 폴더 트리에서 `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` 로 이동하여 필터를 검토합니다.

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. 필터에 대한 MIME 유형을 정의하려면 다음과 같이 MIME 유형을 찾을 수 있습니다.

   왼쪽 레일에서 **[!UICONTROL 컨텐츠]** > **[!UICONTROL dam]** > **[!UICONTROL &lt;`locate_your_asset`]** > **[!UICONTROL jcr:content]** > **[!UICONTROL 메타데이터]** 를 확장한 다음 오른쪽의 테이블에서 **[!UICONTROL dc:format]**&#x200B;을 찾습니다.

   다음 그래픽은 dc:format 자산의 경로의 예입니다.

   ![chlimage_1-3](assets/chlimage_1-3.png)

   `Fiji Red.jpg` 자산의 `dc:format`은 `image/jpeg`입니다.

   형식에 관계없이 모든 이미지에 이 필터를 적용하려면 값을 `image/*`(으)로 설정합니다. 여기서 `*` 은 모든 형식의 모든 이미지에 적용되는 정규식입니다.

   JPEG 유형의 이미지에만 필터를 적용하려면 `image/jpeg` 값을 입력합니다.

1. 복제에서 포함하거나 제외할 변환을 정의합니다.

   복제에 대해 필터링할 수 있는 문자는 다음과 같습니다.

   <table> 
    <tbody> 
    <tr> 
    <td><strong>사용할 문자</strong></td> 
    <td><strong>복제용으로 자산을 필터링하는 방법</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>와일드카드 문자<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>복제할 자산을 포함합니다.</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>복제에서 자산을 제외합니다.</td> 
    </tr> 
    </tbody> 
   </table>

   **content/dam/&lt;`locate your asset`/jcr:content/renditions**&#x200B;로 이동합니다.

   다음 그래픽은 자산 표현물의 예입니다.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   원본만 복제하려면 `+original`을 입력합니다.
