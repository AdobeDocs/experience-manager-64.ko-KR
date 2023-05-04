---
title: 편지 PDF 미리 보기의 사용자 지정 워터마크
seo-title: Custom watermark in letter PDF preview
description: 편지 PDF 미리 보기에서 사용자 정의 워터마크를 만드는 방법을 알아봅니다.
seo-description: Learn how to create custom watermark in letter PDF preview.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
feature: Correspondence Management
exl-id: 8aeabd95-948d-4a54-b593-1eda8ddd731b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# 편지 PDF 미리 보기의 사용자 지정 워터마크 {#custom-watermark-in-letter-pdf-preview}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

서신 작성 UI에서 에이전트 사용자는 전자 메일이나 인쇄와 같이 사후 처리로 전송되는 최종 형태를 미리 봅니다.

조직에서 이 데이터의 무단 사용을 방지하기 위해 미리 보기 PDF에 워터마크를 지정할 수 있습니다. 기본 워터마크는 PDF 전체에 표시되는 &quot;미리 보기&quot;입니다.

미리 보기 PDF에서 워터마크를 활성화하려면 **[!UICONTROL 워터마크 적용]** 의 미리 보기 중 옵션 **[!UICONTROL 서신 관리 구성]** at `https://[server]:[port]/system/console/configMgr`.

![기본 워터마크](assets/default-watermark.png)

다음 단계를 사용하여 워터마크의 텍스트와 모양을 사용자 정의할 수 있습니다.

## 서신 UI 만들기에서 PDF 미리 보기에서 워터마크 사용자 지정 {#customizewatermark-}

1. 이동 `https://[server]:[port]/[ContextPath]/crx/de` 관리자로 로그인합니다.
1. apps 폴더에서 **[!UICONTROL 미리 보기 워터마크]** libs 폴더의 미리 보기 워터마크 폴더와 유사한 경로/구조 사용:

   1. 다음 경로에서 **previewmark **폴더를 마우스 오른쪽 단추로 클릭하고 를 선택합니다 **오버레이 노드**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. 오버레이 노드 대화 상자에 다음 값이 있는지 확인합니다.

      **경로:** /libs/fd/cm/configFiles/previewmark

      **오버레이 위치:** /apps/

      **일치 노드 유형:** 선택됨

      >[!NOTE]
      >
      >/libs 분기에서 변경하지 마십시오. 이 분기는 사용자가 변경할 때마다 변경되므로 변경한 내용이 손실될 수 있습니다.
      >
      >* 인스턴스에서 업그레이드
      >* 핫픽스 적용
      >* 기능 팩 설치


   1. 클릭 **확인** 을 클릭한 다음 **모두 저장**. 다음 **[!UICONTROL 미리 보기 워터마크]** 지정된 경로에 폴더가 만들어집니다.

1. ddx 파일을 &quot;/libs/fd/cm/configFiles/previewwatermark&quot; 폴더에서 &quot;/apps/fd/cm/configFiles/previewwatermark&quot; 폴더로 복사하여 붙여 넣은 다음 를 클릭합니다 **[!UICONTROL 모두 저장]**.
1. /apps/fd/cm/configFiles/previewwatermark/ 아래의 ddx 파일에서 원하는 대로 변경합니다.

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

   워터마크 모양, 텍스트 및 정렬 사용자 지정에 대한 자세한 내용은 [어셈블러 서비스 및 DDX 참조](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) 문서.

   >[!NOTE]
   >
   >ddx 파일에서 결과 및 소스에 대한 참조가 output.pdf 및 input.pdf에 변경되지 않은 채로 유지됩니다. 파일 ddx의 이름도 변경할 수 없습니다.

1. 클릭 **모두 저장**.
