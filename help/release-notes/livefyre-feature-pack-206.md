---
title: Livefyre 기능 팩 2.0.6 릴리스 노트
seo-title: Livefyre 기능 팩 2.0.6 릴리스 노트
description: Livefyre 기능 팩 2.0.6 릴리스 노트
seo-description: Livefyre 기능 팩 2.0.6 릴리스 노트
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 2%

---

# Livefyre 기능 팩 2.0.6 릴리스 노트 {#livefyre-feature-pack-release-notes}

## 릴리스 정보 {#release-information}

| 제품 | Livefyre 기능 팩 2.0.6 |
|--- |--- |
| 버전 | 2.0.6 |
| 유형 | 기능 릴리스 |
| 날짜 | 2018년 8월 31일 |
| 다운로드 URL | 관리자에게 문의하십시오 |
| 호환성 (*) | AEM 6.4 SP1, 6.4, 6.3GA 및 6.2 SP1 |
| 설명 | 이 패키지를 사용하면 Livefyre의 업계 선도적인 큐레이션 기능을 AEM 인스턴스에 통합하여 소셜 네트워크에서 몇 분 안에 사이트에 중요한 UGC(사용자 생성 컨텐츠)를 게시할 수 있습니다. |

## Livefyre 기능 팩 2.0.6 {#what-is-included-in-livefyre-feature-pack}에 포함된 제품

이 패키지는 Livefyre의 업계 선도적인 큐레이션 기능을 AEM 인스턴스와 통합하므로 소셜 네트워크에서 몇 분 안에 사이트에 중요한 UGC(사용자 생성 콘텐츠)를 게시할 수 있습니다. 이 패키지에는 다음 세 가지 구성 요소가 있습니다.

**UGC 컨텐츠를 AEM Assets에 가져오기**

* UGC 가져오기를 사용하여 Livefyre Studio에서 AEM Assets으로 Twitter 및 Instagram 사용자 생성 콘텐츠(UGC)를 가져옵니다.
* Livefyre 라이브러리에 액세스합니다.
* Livefyre Social Search를 사용하여 Twitter 및 Instagram에서 실시간으로 검색합니다.
* UGC에 대한 권한 관리

**AEM Sites 또는 Communities에 Livefyre 구성 요소 추가**

* 맵, 갤러리 및 미디어 벽을 포함한 소셜 구성 요소 세트를 사용하여 동적 및 매력적인 경험을 즉시 만들고 사용자 지정할 수 있습니다.
* AEM Sites 또는 커뮤니티에서 UGC를 게시합니다.

**AEM Commerce를 사용하여 Livefyre에 제품 카탈로그 가져오기**

* 기존 제품 카탈로그를 Livefyre에 원활하게 통합하여 사이트에서 사용자 참여와 전환을 유도하고 쇼퍼블 UGC 경험을 제공합니다.
* AEM Commerce 제품 카탈로그에서 항목을 편집 또는 삭제하고 Livefyre의 변경 사항을 자동으로 업데이트합니다.

설치에 대한 도움말은 [Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)와 통합 을 참조하십시오.

### 추가 릴리스 정보 {#additional-release-information}

instagram 비비즈니스 사용자 계정의 콘텐츠 집계에 영향을 주는 업데이트로 인해 Adobe에서는 더 이상 사용자를 대신하여 댓글을 게시하거나 작성자의 답글을 자동으로 확인할 수 없습니다. [자세한 내용을 보려면 여기를 클릭하십시오](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre 기능 팩 2.0.6은 AEM Classic UI를 지원하지 않습니다.

#### 새 기능 또는 개선 사항 {#new-feature-or-improvement}

* Livefyre에서 권한 요청 소셜 계정을 설정하기 전에 UGC를 검색하는 기능이 추가되었습니다. 권한을 요청하도록 소셜 계정을 설정하거나, 콘텐츠를 소유한 경우 권한 요청을 무시해야 합니다.
* Instagram 및 Twitter [UGC 권한 요청 워크플로우](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)가 최신 API를 준수하도록 업데이트되었습니다.
* 이제 권한 상태 및 적절한 작업이 권한 요청 화면에 표시됩니다.

#### 버그 수정 {#bug-fixes}

* AEM에서 UGC 라이브러리를 로드할 때 권한 요청에 사용된 Livefyre Studio에서 소셜 계정을 삭제하면 오류가 발생하는 문제가 해결되었습니다.
* Livefyre Studio의 자산 수가 AEM UGC 라이브러리의 자산 수와 일치하지 않는 문제가 해결되었습니다.
* 필터 옵션이 재설정된 후 필터링된 결과가 표시되는 UGC 라이브러리의 문제를 수정했습니다.
* 클릭유도문안 단추가 사용자를 잘못된 URL로 리디렉션하는 AEM Commerce 문제를 수정했습니다.
* 여러 구성 요소를 parsys 자리 표시자로 드래그 앤 드롭하면 parsys 자리 표시자가 사라지는 AEM Sites 문제를 수정했습니다.
* 권한 요청을 보낼 때 사용할 수 없는 소셜 계정인 비활성화된 social 계정을 사용하는 문제가 수정되었습니다.
* Assets에서 Sites로 UGC를 드래그 앤 드롭하면 오류가 발생하는 문제를 수정했습니다.
* 채팅 및 Liveblog 구성 요소를 Sites에 끌어다 놓아도 앱이 생성되지 않는 문제가 해결되었습니다.
* 사용자가 댓글을 달려고 할 때 댓글 앱에 오류가 발생하는 문제가 해결되었습니다.
* Livefyre Media Wall App을 사이트에 추가하면 Java Content Repository에서 추가 노드가 발생하는 문제를 해결했습니다.
* instagram UGC 검색에서 페이지 분리와 콘솔 오류가 발생하는 문제를 수정했습니다.
* instagram 사용자 아이콘이 자산에서 API 오류를 생성하는 문제를 해결했습니다.
* 미리 정의된 형식이 없는 사이트에 검토 앱이 추가되던 문제를 수정했습니다.
* Touch UI 기능 및 인라인 편집 문제를 해결했습니다.
* 특정 Instagram 이미지 자산을 가져올 때 오류가 발생하는 문제를 해결했습니다.
* AEM의 Livefyre HTTP 클라이언트가 프록시 구성을 지원하지 않는 문제를 해결했습니다.
