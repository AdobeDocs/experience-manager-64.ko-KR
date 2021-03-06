---
title: ' [!DNL Adobe Experience Manager]에서 디지털 자산을 다운로드합니다.'
description: ' [!DNL Adobe Experience Manager] 에서 자산을 다운로드하고 다운로드 기능을 활성화하거나 비활성화하는 방법을 알아봅니다.'
contentOwner: AG
feature: Asset Management,Asset Distribution
role: User
exl-id: bfe4d597-1080-4de5-a100-73a5175863d7
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 3%

---

# [!DNL Adobe Experience Manager]에서 자산 다운로드 {#download-assets-from-aem}

정적 및 동적 표현물을 포함한 자산을 다운로드할 수 있습니다. 또는 [!DNL Adobe Experience Manager Assets]에서 직접 자산에 대한 링크가 있는 이메일을 보낼 수 있습니다. 다운로드한 자산은 ZIP 파일에 번들로 제공됩니다. 압축 ZIP 파일의 최대 파일 크기는 내보내기 작업의 1GB입니다. 내보내기 작업당 최대 500개의 총 자산이 허용됩니다.

>[!NOTE]
>
>전자 메일의 수신자는 전자 메일 메시지의 ZIP 다운로드 링크에 액세스하려면 `dam-users` 그룹의 구성원이어야 합니다. 자산을 다운로드하려면 구성원이 자산 다운로드를 트리거하는 워크플로우를 시작할 권한이 있어야 합니다.

자산 유형 이미지 세트, 스핀 세트, 혼합 미디어 세트 및 회전 세트는 다운로드할 수 없습니다.

자산을 다운로드하려면 다음 단계를 수행하십시오.

1. AEM의 왼쪽 위 모서리에서 [!DNL Experience Manager] 로고를 탭한 다음, 왼쪽 레일에서 **[!UICONTROL 탐색]**&#x200B;을 탭합니다.
1. 탐색 페이지에서 **[!UICONTROL Assets]** > **[!UICONTROL 파일.]**&#x200B;을 탭합니다.
1. 다운로드할 자산이 들어 있는 폴더로 이동합니다.
1. 폴더를 선택하거나 폴더 내에서 하나 이상의 자산을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 다운로드.]**

   ![Experience Manager 자산에서 자산을 다운로드할 때 사용할 수 있는 옵션](/help/assets/assets/asset_download_dialog.png)

   *그림: 다운로드 대화 상자 옵션.*

1. 다운로드 대화 상자에서 원하는 다운로드 옵션을 선택합니다.

   | 내보내기 또는 다운로드 옵션 | 설명 |
   |---|---|
   | **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]** | 다운로드할 각 자산을 자산의 상위 폴더 아래에 중첩된 하위 폴더에 로컬 컴퓨터의 한 폴더로 포함하려면 이 옵션을 선택합니다. 이 옵션을 선택하지 않으면 기본적으로 폴더 계층 구조가 무시되고 모든 자산이 로컬 컴퓨터의 한 폴더로 다운로드됩니다. |
   | **[!UICONTROL 이메일]** | 사용자에게 이메일 알림이 전송됩니다. 표준 이메일 템플릿은 다음 위치에서 사용할 수 있습니다.<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> 배포 중에 사용자 지정하는 템플릿은 다음 위치에서 사용할 수 있습니다. <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>다음 위치에 임차인별 사용자 지정 템플릿을 저장할 수 있습니다.<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL 에셋]** | 이 옵션을 선택하면 변환 없이 자산을 원래 양식으로 다운로드합니다.<br>원본 자산에 하위 자산이 있는 경우 하위 자산 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 표현물]** | 표현물은 자산의 이진 표현입니다. 자산에는 업로드된 파일의 표현인 기본 표현이 있습니다. 레프리젠테이션들을 수 있어요 <br> 이 옵션을 사용하여 다운로드할 표현물을 선택할 수 있습니다. 사용할 수 있는 표현물은 선택한 자산에 따라 다릅니다. 자산에 표현물이 있는 경우 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 동적 표현물]** | 일련의 대체 표현물을 실시간으로 생성하려면 이 옵션을 선택합니다. 이 옵션을 선택하는 경우 [이미지 사전 설정](image-presets.md) 목록에서 선택하여 동적으로 만들 표현물도 선택합니다. <br>또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 반전 등의 선택적 이미지 수정자를 선택할 수 있습니다. 이 옵션은 [!DNL Dynamic Media] 이 활성화된 경우에만 사용할 수 있습니다. |

1. 대화 상자에서 **[!UICONTROL 다운로드.]**&#x200B;를 누릅니다.

다운로드할 폴더를 선택하면 폴더 아래에 있는 전체 자산 계층 구조가 다운로드됩니다. 개별 폴더에 다운로드한 각 자산(상위 폴더 아래에 중첩된 하위 폴더의 자산 포함)을 포함하려면 **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]**&#x200B;를 선택합니다.

## 자산 다운로드 서블릿 활성화 {#enable-asset-download-servlet}

[!DNL Experience Manager]의 기본 서블릿을 사용하면 인증된 사용자가 서버와 네트워크에 과부하를 줄 수 있는 표시되는 자산의 ZIP 파일을 만들기 위해 임의로 큰 동시 다운로드 요청을 발행할 수 있습니다. 이 기능으로 인해 발생할 수 있는 DoS 위험을 완화하려면 게시 인스턴스에 대해 `AssetDownloadServlet` OSGi 구성 요소가 기본적으로 비활성화됩니다.

DAM에서 자산을 다운로드할 수 있도록 하려면 Asset Share Commons 또는 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화합니다. Adobe은 일상적인 다운로드 요구 사항에 영향을 주지 않고 허용된 다운로드 크기를 가능한 한 낮게 설정할 것을 권장합니다. 높은 값은 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드(`config.publish`)를 대상으로 하는 이름 지정 규칙이 있는 폴더를 만듭니다. `/apps/<your-app-name>/config.publish`. 실행 모드에 대한 구성 속성을 정의하려면 [실행 모드](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode)를 참조하십시오.
1. 구성 폴더에서 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 유형의 파일을 만듭니다.`nt:file`
1. `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 을(를) 다음으로 채웁니다. 다운로드에 대한 최대 크기(바이트)를 `asset.download.prezip.maxcontentsize` 값으로 설정합니다. 아래 샘플은 ZIP 다운로드의 최대 크기를 100kB를 초과하지 않도록 구성합니다.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 자산 다운로드 서블릿 비활성화 {#disable-asset-download-servlet}

Dispatcher 구성을 업데이트하여 모든 자산 다운로드 요청을 차단하여 [!DNL Experience Manager] 게시 인스턴스에서 `Asset Download Servlet`을 비활성화할 수 있습니다. OSGi 콘솔을 통해 직접 서블릿을 수동으로 비활성화할 수도 있습니다.

1. 디스패처 구성을 통해 자산 다운로드 요청을 차단하려면 `dispatcher.any` 구성을 편집하고 [필터 섹션](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-access-to-content-filter)에 규칙을 추가하십시오. `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. 게시 인스턴스에서 OSGi 구성 요소를 비활성화하려면 `http://[aem_server]:[port]/system/console/components`에서 OSGi 콘솔에 액세스하십시오. `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet`을(를) 찾고 **[!UICONTROL Disable]**&#x200B;를 클릭합니다.

>[!MORELIKETHIS]
>
>* [DRM 보호 자산을 다운로드합니다](drm.md).
>* [Win 또는 Mac 데스크탑에서 Experience Manager 데스크탑 앱을 사용하여 자산을 다운로드합니다](https://helpx.adobe.com/kr/experience-manager/desktop-app/aem-desktop-app.html).
>* [지원되는 Adobe Creative Cloud 앱](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html) 내에서 Adobe 자산 링크를 사용하여 자산을 다운로드합니다.

