---
title: 벌크 메타데이터 가져오기 및 내보내기
description: 이 문서에서는 메타데이터를 일괄적으로 가져오고 내보내는 방법을 설명합니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 10%

---

# 벌크 메타데이터 가져오기 및 내보내기 {#bulk-metadata-import-and-export}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager] 자산을 사용하면 CSV 파일을 사용하여 자산 메타데이터를 일괄적으로 가져올 수 있습니다. CSV 파일을 가져와서 최근에 업로드한 자산 또는 기존 자산에 대한 벌크 업데이트를 수행할 수 있습니다. 타사 시스템에서 CSV 형식으로 자산 메타데이터를 일괄적으로 수집할 수도 있습니다.

## 메타데이터 가져오기 {#import-metadata}

메타데이터 가져오기는 비동기적이며 시스템 성능에 영향을 주지 않습니다. 워크플로우 플래그를 선택하는 경우 XMP 원본에 쓰기 활동으로 인해 여러 자산에 대한 메타데이터를 동시에 업데이트할 때 리소스를 많이 사용할 수 있습니다. 다른 사용자에게 성능에 영향을 주지 않도록 서버 사용 중 그러한 가져오기를 계획합니다.

>[!NOTE]
>
>사용자 지정 네임스페이스에 메타데이터를 가져오려면 먼저 네임스페이스를 등록합니다.

메타데이터를 일괄적으로 가져오려면 다음 단계를 수행합니다.

1. 자산 사용자 인터페이스로 이동하고 탭/클릭합니다 **[!UICONTROL 만들기]** 를 클릭합니다.
1. 메뉴에서 **[!UICONTROL 메타데이터]**.
1. 설정 **[!UICONTROL 메타데이터 가져오기]** 페이지에서 탭/클릭합니다 **[!UICONTROL 파일 선택]**.  Select the CSV file with the metadata.
1. CSV 파일에 다음 매개 변수가 포함되어 있는지 확인합니다.

   | 메타데이터 가져오기 매개 변수 | 설명 |
   |:---|:---|
   | [!UICONTROL 배치 크기] | 메타데이터를 가져올 일괄 처리의 자산 수입니다. 기본값은 50입니다. 최대값은 100입니다. |
   | [!UICONTROL 필드 분리 기호] | 기본값은 입니다. `,` - 쉼표. 다른 문자를 지정할 수 있습니다. |
   | [!UICONTROL 다중 값 구분 기호] | 메타데이터 값에 대한 구분자입니다. 기본값은 입니다. `|` - 파이프. |
   | [!UICONTROL 워크플로우 실행] | 기본적으로 False입니다. 를 true 로 설정하고 기본 설정이 `DAM Metadata WriteBack Workflow` (이진 XMP 데이터에 메타데이터를 기록합니다.) 워크플로우를 활성화하면 시스템에 성능에 영향을 줍니다. |
   | [!UICONTROL 자산 경로 열 이름] | 자산이 있는 CSV 파일의 열 이름을 정의합니다. |

1. 탭/클릭 **[!UICONTROL 가져오기]** 를 클릭합니다. 메타데이터를 가져오면 알림 받은 편지함으로 알림이 전송됩니다. 자산 속성 페이지로 이동하고 메타데이터 값을 자산에 대해 올바르게 가져오는지 확인합니다.

메타데이터를 가져올 때 날짜 및 타임스탬프를 추가하려면 `YYYY-MM-DDThh:mm:ss.fff-00:00` 날짜 및 시간에 대한 형식입니다. 날짜와 시간은 `T`, `hh` 시간은 24시간 형식으로, `fff` 은 나노 초이고, `-00:00` 시간대 오프셋입니다. 예, `2020-03-26T11:26:00.000-07:00` 은 2020년 3월 26일, 11일입니다:26:00.000 오전 PST 시간

>[!CAUTION]
>
>날짜 형식이 일치하지 않는 경우 `YYYY-MM-DDThh:mm:ss.fff-00:00`인 경우 날짜 값이 설정되지 않습니다. 내보낸 메타데이터 CSV 파일의 날짜 형식은 입니다 `YYYY-MM-DDThh:mm:ss-00:00`. 이 필드를 가져오려면 다음 방법으로 나타내는 나노 초 값을 추가하여 허용 가능한 형식으로 변환하십시오 `fff`.

## 메타데이터 내보내기 {#export-metadata}

메타데이터를 일괄적으로 내보내는 사용 사례는 다음과 같습니다.

* 자산을 마이그레이션할 때 서드파티 시스템에서 메타데이터를 가져옵니다.
* 더 넓은 프로젝트 팀과 자산 메타데이터를 공유합니다.
* 메타데이터를 테스트하거나 감사하여 규정을 준수합니다.
* 별도의 현지화를 위한 메타데이터를 외부화합니다.

여러 자산에 대한 메타데이터를 CSV 형식으로 내보낼 수 있습니다. 메타데이터는 비동기식으로 내보내지므로 시스템 성능에 영향을 주지 않습니다. 메타데이터를 내보내려면, [!DNL Experience Manager] 자산 노드의 속성을 통해 트래버스합니다. `jcr:content/metadata` 및 해당 하위 노드를 캡처하고 CSV 파일로 메타데이터 속성을 내보냅니다.

여러 자산의 메타데이터를 일괄적으로 내보내려면 다음 단계를 수행합니다.

1. 메타데이터를 내보낼 자산이 들어 있는 자산 폴더를 선택합니다. 도구 모음에서 를 선택합니다 **[!UICONTROL 메타데이터 내보내기]**.

1. 에서 [!UICONTROL 메타데이터 내보내기] 대화 상자에서 CSV 파일의 이름을 지정합니다. 하위 폴더의 자산에 대한 메타데이터를 내보내려면 을 선택합니다 **[!UICONTROL 하위 폴더에 자산 포함]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. 원하는 옵션을 선택합니다. 파일 이름을 입력하고 필요한 경우 날짜를 입력합니다.
1. 에서 **[!UICONTROL 내보낼 속성]**&#x200B;를 사용하여 모든 속성을 내보내는지 아니면 특정 속성을 내보내는지를 지정합니다. 만약 **[!UICONTROL 선택적]** 내보낼 속성에서 원하는 속성을 추가합니다.

1. 도구 모음에서 탭/클릭 **[!UICONTROL 내보내기]**. 메타데이터가 내보내지는지 확인하는 메시지가 나타납니다. 메시지를 닫습니다.

1. Open the inbox notification for the export job. Select the job and click **[!UICONTROL Open]** from the toolbar. To download the CSV file with the metadata, tap/click **[!UICONTROL CSV Download]** from the toolbar. **[!UICONTROL 닫기]**&#x200B;를 클릭합니다.

   ![csv_download](assets/csv_download.png)
