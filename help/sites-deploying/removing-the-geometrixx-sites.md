---
title: Geometrixx 사이트 제거
seo-title: Removing the Geometrixx Sites
description: 샘플 Geometrixx 컨텐츠를 제거하는 방법을 알아봅니다.
seo-description: Learn how to remove the sample Geometrixx content.
uuid: 07d20837-3375-4e64-bb07-3e4d10452335
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 56761a36-ce21-46e1-856f-75a7e94acae9
exl-id: 495031fb-b559-4071-abc4-93d238ce136d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# Geometrixx 사이트 제거{#removing-the-geometrixx-sites}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

AEM에는 샘플 Geometrixx 웹 사이트 세트가 포함되어 있습니다. 을 통해 이 샘플 컨텐츠를 제거할 수 있습니다. **패키지 관리자**.

개별 geometrixx 관련 패키지는 다음과 같습니다.

* `cq-geometrixx-outdoors-ugc-pkg-*<version>*.zip`
* `cq-geometrixx-pkg-*<version>*.zip`
* `cq-content-mac-*<version>*.zip`
* `cq-geometrixx-login-pkg-*<version>*.zip`
* `cq-geometrixx-users-pkg-*<version>*.zip`
* `cq-geometrixx-workflow-pkg-*<version>*.zip`
* `cq-geometrixx-outdoors-pkg-*<version>*.zip`
* `cq-geometrixx-commons-pkg-*<version>*.zip`
* `cq-geometrixx-media-pkg-*<version>*.zip`

개별 패키지를 제거하려면 **제거** 그 패키지 위에

수퍼 패키지도 있다.

* `cq-geometrixx-all-pkg-5.6.12.zip`

이 패키지에는 위의 개별 패키지가 모두 포함되어 있습니다. 모든 geometrixx 관련 컨텐츠를 한 번에 제거하려면 **제거** 이 패키지 수퍼 패키지는 제거된 상태로 이동하며 모든 개별 패키지가 패키지 관리자 보기에서 사라집니다.

이제 데모 사이트 없이 &quot;빈&quot; AEM 인스턴스가 있습니다.

>[!NOTE]
>
>업그레이드할 때 geometrixx 사이트는 자동으로 다시 설치됩니다. 이러한 샘플을 사용하지 않으려면 업그레이드 후 geometrixx 웹 사이트를 제거해야 할 수 있습니다.
