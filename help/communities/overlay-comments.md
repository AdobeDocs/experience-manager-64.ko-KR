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
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# 오버레이 주석 구성 요소 {#overlay-comments-component}

기본 구성 요소를 [오버레이하는](client-customize.md#overlays) 의도는 구성 요소에 대한 모든 상대 참조에 대해 전체적으로 구성 요소의 모양이나 동작을 변경하는 것입니다. /libs 폴더에서 검색하기 전에 /apps 폴더로 확인하는 슬링의 특성에 의존합니다. 따라서 구성 요소의 경로는 /apps 폴더에 있지 않고 /libs 폴더에 있다는 점을 제외하고 기본 구성 요소의 경로와 동일합니다.

## 예 {#example}

주석 기능을 수정하면 댓글에 대한 아바타가 더 이상 표시되지 않도록 주석 헤더를 변경하여 웹 사이트의 디자인과 일치한다고 가정합니다. 아바타를 숨기는 방법은 CSS를 사용하거나, 여기에 설명된 대로, 아바타가 포함된 HTML이 클라이언트에 전송되지 않도록 앱 폴더에 header.jsp를 오버레이하는 것입니다.

주석을 오버레이하려면 다음을 수행해야 합니다.

1. [댓글 페이지](overlay-create-comments-page.md)
1. [노드 만들기](overlay-create-nodes.md)
1. [모양 변경](overlay-alter-appearance.md)

