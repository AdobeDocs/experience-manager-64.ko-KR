---
title: 오버레이 주석 구성 요소
seo-title: 오버레이 주석 구성 요소
description: 오버레이 주석 구성 요소 개요
seo-description: 오버레이 주석 구성 요소 개요
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# 오버레이 주석 구성 요소 {#overlay-comments-component}

기본 구성 요소를 오버레이하는 의도는 구성 요소에 대한 모든 상대 참조에 대해 구성 요소의 모양 또는 동작을 전역 변경하는 것입니다. [](client-customize.md#overlays) /libs 폴더에서 검색하기 전에 sling의 특성을 사용하여 /apps 폴더로 확인합니다. 따라서 구성 요소의 경로는 /apps 폴더에 있지 않고 /libs 폴더에 있다는 점을 제외하고 기본 구성 요소의 경로와 동일합니다.

## 예 {#example}

주석 기능을 수정하여 웹 사이트의 디자인과 일치되도록 하거나 주석 헤더를 변경하여 더 이상 댓글에 대한 아바타가 표시되지 않도록 한다고 가정합니다. 아바타를 숨기는 솔루션은 CSS를 사용하거나, 여기에 설명된 대로 앱의 header.jsp를 오버레이하여 아바타가 포함된 HTML이 클라이언트로 전송되지 않도록 합니다.

주석을 오버레이하려면 다음을 수행해야 합니다.

1. [댓글 페이지](overlay-create-comments-page.md)
1. [노드 만들기](overlay-create-nodes.md)
1. [모양 변경](overlay-alter-appearance.md)
