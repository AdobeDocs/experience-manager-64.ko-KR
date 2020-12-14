---
title: Livefyre 기능 팩 2.0.6 릴리스 정보
seo-title: Livefyre 기능 팩 2.0.6 릴리스 정보
description: Livefyre 기능 팩 2.0.6 릴리스 정보
seo-description: Livefyre 기능 팩 2.0.6 릴리스 정보
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# Livefyre 기능 팩 2.0.6 릴리스 노트 {#livefyre-feature-pack-release-notes}

## 릴리스 정보 {#release-information}

| 제품 | Livefyre 기능 팩 2.0.6 |
|--- |--- |
| 버전 | 2.0.6 |
| 유형 | 기능 릴리스 |
| 날짜 | 2018년 8월 31일 |
| 다운로드 URL | 관리자에게 문의 |
| 호환성 (*) | AEM 6.4 SP1, 6.4, 6.3 GA 및 6.2 SP1 |
| 설명 | 이 패키지를 사용하면 Livefyre의 업계 선도적인 큐레이션 기능을 AEM 인스턴스와 통합할 수 있으므로 소셜 네트워크에서 사이트로 중요한 UGC(사용자 생성 콘텐츠)를 신속하게 게시할 수 있습니다. |

## Livefyre 기능 팩 2.0.6 {#what-is-included-in-livefyre-feature-pack}에 포함된 제품

이 패키지는 Livefyre의 업계 선도적인 큐레이션 기능과 AEM 인스턴스를 통합하여 소셜 네트워크에서 사이트에 중요한 UGC(사용자 생성 콘텐츠)를 신속하게 게시할 수 있습니다. 이 패키지에는 다음과 같은 세 가지 구성 요소가 있습니다.

**AEM Assets으로 UGC 컨텐츠 가져오기**

* UGC Importer를 사용하여 Twitter 및 Instagram 사용자 생성 콘텐츠(UGC)를 Livefyre Studio에서 AEM Assets으로 가져옵니다.
* Livefyre 라이브러리에 액세스합니다.
* Livefyre 소셜 검색을 사용하여 Twitter 및 Instagram에서 실시간으로 검색
* UGC에 대한 권한 관리를 참조하십시오.

**AEM Sites 또는 커뮤니티에 Livefyre 구성 요소 추가**

* 지도, 갤러리 및 미디어 월을 비롯한 소셜 구성 요소 세트를 사용하여 다이내믹하고 매력적인 경험을 신속하게 제작하고 사용자 요구에 맞게 변경할 수 있습니다.
* AEM Sites 또는 커뮤니티에 UGC를 게시합니다.

**AEM Commerce를 사용하여 제품 카탈로그를 Livefyre로 가져오기**

* 기존 제품 카탈로그를 Livefyre에 완벽하게 통합하여 사이트에서의 사용자 참여도와 전환율을 높일 뿐만 아니라 쇼퍼블 UGC 경험을 제공할 수 있습니다.
* AEM Commerce 제품 카탈로그에서 항목을 편집하거나 삭제할 수 있고 Livefyre에서 변경 사항을 자동으로 업데이트할 수 있습니다.

설치에 대한 도움말은 [Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)와 통합을 참조하십시오.

### 추가 릴리스 정보 {#additional-release-information}

Instagram 비비즈니스 사용자 계정의 컨텐츠 집계에 영향을 주는 업데이트로 인해 더 이상 사용자를 대신하여 댓글을 게시하거나 작성자의 답글을 자동으로 확인할 수 없습니다. [자세한](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/) 내용을 보려면 여기를 클릭하십시오.

>[!NOTE]
>
>Livefyre 기능 팩 2.0.6은 AEM Classic UI를 지원하지 않습니다.

#### 새 기능 또는 개선 사항 {#new-feature-or-improvement}

* Livefyre에서 권한을 설정하기 전에 UGC를 검색하는 기능이 추가되었습니다. 권한을 요청하려면 소셜 계정을 설정해야 하며, 컨텐트를 소유하는 경우 권한 요청을 무시해야 합니다.
* 최신 API를 준수하도록 Instagram 및 Twitter [UGC 권한 요청 워크플로](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)이(가) 업데이트되었습니다.
* 이제 권한 상태 및 적절한 작업이 권한 요청 화면에 표시됩니다.

#### 버그 수정 {#bug-fixes}

* 권한 요청에 사용된 Livefyre Studio에서 소셜 계정을 삭제하면 AEM에서 UGC 라이브러리를 로드할 때 오류가 발생하는 문제가 해결되었습니다.
* Livefyre 스튜디오의 자산 수가 AEM UGC 라이브러리의 자산 수와 일치하지 않는 문제가 해결되었습니다.
* 필터 옵션이 재설정된 후 필터링된 결과가 표시되는 UGC 라이브러리의 문제를 수정했습니다.
* 클릭유도문안 단추가 사용자를 잘못된 URL로 리디렉션하는 AEM Commerce 문제를 해결했습니다.
* AEM Sites에서 여러 구성 요소를 parsys 자리 표시자로 드래그 앤 드롭하면 구성 요소가 사라지는 문제를 해결했습니다.
* 권한 요청을 보낼 때 비활성화된 소셜 계정에서 선택할 수 있었던 문제가 수정되었습니다.
* 자산에서 사이트로 UGC를 드래그하여 놓는 경우 오류가 발생하는 문제를 해결했습니다.
* 채팅 및 Liveblog 구성 요소를 사이트에 드래그 앤 드롭해도 앱이 생성되지 않는 문제가 해결되었습니다.
* 사용자가 댓글을 작성하려고 하면 댓글 앱에서 오류가 발생하는 문제가 해결되었습니다.
* 사이트에 Livefyre 미디어 담벼락 앱을 추가하면 Java 컨텐츠 저장소에서 추가 노드가 만들어지는 문제가 해결되었습니다.
* Instagram UGC 검색에서 페이지 구분과 콘솔 오류가 발생하는 문제를 수정했습니다.
* Instagram 사용자 아이콘이 자산에서 API 오류를 생성하는 문제를 수정했습니다.
* 미리 정의된 형식이 없는 사이트에 리뷰 앱이 추가되던 문제를 수정했습니다.
* 터치 UI 기능 및 인라인 편집 문제를 수정했습니다.
* 특정 Instagram 이미지 자산을 가져올 때 오류가 발생하는 문제를 수정했습니다.
* AEM의 Livefyre HTTP 클라이언트가 프록시 구성을 지원하지 않는 문제를 수정했습니다.
