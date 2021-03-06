---
title: 모바일 장치용 페이지 작성
seo-title: 모바일 장치용 페이지 작성
description: 모바일 페이지를 작성할 때는 모바일 장치를 에뮬레이션하는 방식으로 페이지가 표시됩니다. 페이지를 작성할 때에는 몇 개의 에뮬레이터 간을 전환하여 페이지에 액세스할 때 최종 사용자에게 표시되는 내용을 확인할 수 있습니다.
seo-description: 모바일 페이지를 작성할 때는 모바일 장치를 에뮬레이션하는 방식으로 페이지가 표시됩니다. 페이지를 작성할 때에는 몇 개의 에뮬레이터 간을 전환하여 페이지에 액세스할 때 최종 사용자에게 표시되는 내용을 확인할 수 있습니다.
uuid: ca16979d-6e5f-444d-b959-ae92542039b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 430a27b5-f344-404f-8bf8-0d91b49b605e
exl-id: 26324f89-f5e2-40bc-96b4-0f3faa08bdd1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 84%

---

# 모바일 장치용 페이지 작성{#authoring-a-page-for-mobile-devices}

모바일 페이지를 작성할 때는 모바일 장치를 에뮬레이션하는 방식으로 페이지가 표시됩니다. 페이지를 작성할 때에는 몇 개의 에뮬레이터 간을 전환하여 페이지에 액세스할 때 최종 사용자에게 표시되는 내용을 확인할 수 있습니다.

장치는 페이지를 렌더링할 장치의 기능에 따라 카테고리 기능, 스마트와 터치로 그룹화됩니다. 최종 사용자가 모바일 페이지에 액세스하면 AEM이 장치를 감지하여 장치 그룹에 해당하는 표현 데이터를 전송합니다.

>[!NOTE]
>
>기존 표준 사이트를 기반으로 모바일 사이트를 만들려면 표준 사이트의 Live Copy를 만드십시오. ([다른 채널용 Live Copy 만들기](/help/sites-administering/msm-livecopy.md) 참조).
>
>AEM 개발자는 새 장치 그룹을 만들 수 있습니다. ([장치 그룹 필터 만들기를 참조하십시오.](/help/sites-developing/groupfilters.md))

다음 절차를 사용하여 모바일 페이지를 작성하십시오.

1. 브라우저에서 **Siteadmin** 콘솔로 이동합니다.
1. **웹 사이트** >> **Geometrixx 모바일 데모 사이트** > **영어** 페이지를 엽니다.****

1. 다른 에뮬레이터로 전환합니다. 다음 방법 중 하나를 사용합니다.

   * 페이지 상단의 장치 아이콘을 클릭합니다.
   * **사이드킥**&#x200B;에서 **편집** 단추를 클릭하고 드롭다운 메뉴에서 장치를 선택합니다.

1. 사이드 킥의 모바일 탭에서 **텍스트 및 이미지** 구성 요소를 페이지에 드래그합니다.
1. 구성 요소를 편집하고 텍스트를 추가합니다. **확인**&#x200B;을 클릭하여 변경 사항을 저장합니다.

페이지가 다음과 같이 표시됩니다.

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>모바일 장치에서 작성 인스턴스의 페이지를 요청하면 에뮬레이터가 비활성화됩니다. 그런 다음 터치 지원 UI를 사용하여 작성을 수행할 수 있습니다.
