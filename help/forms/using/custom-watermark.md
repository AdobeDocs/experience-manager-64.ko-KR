---
title: 문자 PDF 미리 보기의 사용자 정의 워터마크
seo-title: 문자 PDF 미리 보기의 사용자 정의 워터마크
description: Learn how to create custom watermark in letter PDF preview.
seo-description: Learn how to create custom watermark in letter PDF preview.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 문자 PDF 미리 보기의 사용자 정의 워터마크 {#custom-watermark-in-letter-pdf-preview}

## 개요 {#overview}

[통신 UI 만들기]에서 에이전트 사용자는 전자 우편 또는 인쇄와 같이 게시 프로세스로 보내지는 메시지를 최종 모양으로 미리 봅니다.

조직에서 이 데이터의 무단 사용을 방지하기 위해 미리 보기 PDF에 워터마크를 적용할 수 있습니다. 기본 워터마크는 PDF 전체에 표시되는 &quot;PREVIEW&quot;입니다.

미리 보기 PDF에서 워터마크를 활성화하려면 의 통신 관리 **[!UICONTROL 구성에서]** 미리 보기 중 워터마크 **[!UICONTROL 적용 옵션을]** 선택합니다 `https://[server]:[port]/system/console/configMgr`.

![default-watermark](assets/default-watermark.png)

다음 단계에 따라 워터마크의 텍스트와 모양을 사용자 정의할 수 있습니다.

## 통신 UI 작성에서 PDF 미리 보기에서 워터마크 사용자 정의 {#customizewatermark-}

1. 관리자로 `https://[server]:[port]/[ContextPath]/crx/de` 이동하여 로그인합니다.
1. apps 폴더에서 libs 폴더의 **[!UICONTROL previewwatermark 폴더와 유사한 경로/구조를 가진 미리 보기 워터마크라는]** 폴더를 만듭니다.

   1. 다음 경로에서 **previewwatermark **folder를 마우스 오른쪽 단추로 클릭하고 [오버레이 노드] **를 선택합니다**.

      `/libs/fd/cm/configFiles/previewwatermark`

   1. [오버레이 노드] 대화 상자에 다음 값이 있는지 확인합니다.

      **** 경로:/libs/fd/cm/configFiles/previewwatermark

      **** 오버레이 위치:/apps/

      **** 일치 노드 유형:선택됨

      >[!NOTE]
      >
      >/libs 분기에서 변경하지 마십시오. 이 분기는 다음 작업을 수행할 때마다 변경될 수 있으므로 변경한 내용이 손실될 수 있습니다.
      >
      >* 인스턴스 업그레이드
      >* 핫픽스 적용
      >* 기능 팩 설치


   1. 확인을 **클릭한** 다음 모두 **저장을 클릭합니다**. 미리 **[!UICONTROL 보기 워터마크]** 폴더가 지정된 경로에 생성됩니다.

1. &quot;/libs/fd/cm/configFiles/previewwatermark&quot; 폴더의 dx 파일을 복사하여 &quot;/apps/fd/cm/configFiles/previewwatermark&quot; 폴더에 붙여넣고 모두 **[!UICONTROL 저장을 클릭합니다]**.
1. /apps/fd/cm/configFiles/previewwatermark/ 아래의 dx 파일에서 원하는 대로 변경합니다.

   ```
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   워터마크 모양, 텍스트 및 정렬 사용자 지정에 대한 자세한 내용은 Assembler Service 및 DCX Reference [문서에서 워터마크 및 배경 추가 및 제거를 참조하십시오](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) .

   >[!NOTE]
   >
   >ddx 파일에서 결과 및 소스에 대한 참조는 output.pdf 및 input.pdf로 변경되지 않은 상태로 유지됩니다. 파일 ddx의 이름도 변경할 수 없습니다.

1. 모두 **저장을 클릭합니다**.

