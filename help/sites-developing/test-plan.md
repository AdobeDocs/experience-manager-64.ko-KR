---
title: 테스트 계획 컴파일
seo-title: 테스트 계획 컴파일
description: 개별 시험 사례가 테스트 계획에 통합됩니다
seo-description: 개별 시험 사례가 테스트 계획에 통합됩니다
uuid: 99822b02-7b75-422d-ae21-16c4af742567
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 3a8302e8-bc61-402c-a9f2-5db3dfa6dd6d
exl-id: 913e1fee-b071-4152-94c3-dd7b8900e5ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 5%

---

# 테스트 계획 컴파일{#compiling-your-test-plan}

그 후 개별 테스트 사례가 테스트 계획에 통합될 것이며, 다음과 같이 정의할 것입니다.

## 우선순위

특정 테스트가 다른 테스트보다 더 중요하므로 우선 순위를 표시하는 것이 좋습니다.

예를 들어, 특정 테스트는 Go/No-Go 결정에 영향을 줄 수 있으므로 테스트될 때마다 중간 릴리스를 통해 확인해야 합니다.

## 반복

프로젝트에서 개발 반복(사용 가능한 다중 릴리스를 포함)을 사용하는 경우 각 반복에 대한 결과를 표시해야 하거나 원할 수 있습니다. 다음을 나타내는 데 사용할 수 있습니다.

* 어떤 테스트를 반복할지 결정합니다.
* 여러 반복에서 반복되는 테스트에 대해 표시되는 결과.
* 기본 기능에 대한 우선 순위 테스트와 테스트는 정기적으로 반복됩니다.

## 테스터

이때 적절한 테스트 팀이나 특정 테스트 담당자를 할당할 수 있습니다(가용성 및/또는 경험에 따라 달라질 수 있음).

## 요약 또는 개요

보고 목적으로 테스트 결과에 대한 개요를 제공하려고 합니다.

* 이미 적용된 테스트 비율입니다.
* 성공/실패 백분율입니다.
* 우선 순위 테스트와 관련된 특정 수치입니다.
