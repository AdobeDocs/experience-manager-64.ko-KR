---
title: 스마트 컨텐츠 서비스 교육 지침
description: 자산에 스마트 태그를 적용하도록 AI 서비스 교육
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# 스마트 컨텐츠 서비스 교육 지침 {#smart-content-service-training-guidelines}

브랜드 이미지에 효과적으로 태그를 지정할 수 있도록 하기 위해 스마트 컨텐츠 서비스를 사용하려면 교육 이미지가 특정 지침을 따라야 합니다.

## 교육 지침 {#guidelines-for-training}

최상의 결과를 얻으려면 교육 세트의 이미지는 다음 지침을 따라야 합니다.

**수량 및 크기:** 태그당  **최소 30개의 이미지**. 더 긴 면에서 최소 500픽셀입니다.

**일관성**: 태그의 이미지는 시각적으로 유사해야 합니다.

예를 들어, 이러한 모든 이미지에 시각적 유사하지 않으므로 *my-party*(교육용)로 태그를 지정하는 것은 좋지 않습니다.

![교육 지침을 보여주는 실례가 되는 이미지](assets/do-not-localize/coherence.png)

**적용 범위**: 훈련 중에는 다양한 이미지가 있어야 합니다. 그 아이디어는 [!DNL Experience Manager]이 올바른 것에 초점을 맞추도록 몇 가지 하지만 상당히 다양한 예를 제공하는 것입니다. 시각적으로 다른 이미지에 동일한 태그를 적용하는 경우 각 종류의 최소 5개의 예를 포함합니다.

예를 들어, *model-down-pose* 태그의 경우, 서비스가 태깅 중에 유사한 이미지를 더 정확하게 식별하기 위해 아래 강조 표시된 이미지와 유사한 더 많은 교육 이미지를 포함합니다.

![교육 지침을 보여주는 실례가 되는 이미지](assets/do-not-localize/coverage_1.png)

**방해/장애**: 이 서비스는 집중을 덜 하는 이미지(잘 보이는 배경, 주제와 함께 있는 개체/사람과 같은 관련이 없는 인물)에서 더 잘 훈련한다.

예를 들어 *캐주얼-신발* 태그의 경우 두 번째 이미지는 올바른 훈련 후보자가 아닙니다.

![교육 지침을 보여주는 실례가 되는 이미지](assets/do-not-localize/distraction.png)

**완결성:**  이미지가 둘 이상의 태그에 대해 자격을 부여하는 경우 교육을 위한 이미지를 포함하기 전에 적용 가능한 모든 태그를 추가하십시오. 예를 들어, *레인코트* 및 *model-side-view*&#x200B;와 같은 태그의 경우, 교육을 위해 해당 자산에 태그를 모두 추가하기 전에 해당 자산에 태그를 모두 추가합니다.

![교육 지침을 보여주는 실례가 되는 이미지](assets/do-not-localize/completeness.png)

## 제한 사항 {#limitations}

향상된 스마트 태그는 브랜드 이미지 및 해당 태그의 학습 모델을 기반으로 합니다. 이러한 모델이 태그를 식별하는 데 항상 완벽하지는 않습니다. 현재 버전의 스마트 컨텐츠 서비스에는 다음과 같은 제한 사항이 있습니다.

* 이미지의 미묘한 차이를 인식하지 못합니다. 예를 들면, 슬림한 셔츠와 일반 맞춤 셔츠입니다.
* 이미지의 작은 패턴/부분을 기반으로 태그를 식별할 수 없음 예를 들어, 티셔츠의 로고는
* 태깅은 [!DNL Experience Manager]에서 지원되는 로케일에서 지원됩니다. 언어 목록을 보려면 [Smart Content Services 릴리스 노트](/help/release-notes/smart-content-service-release-notes.md)를 참조하십시오.

스마트 태그가 있는 자산을 검색하려면(일반 또는 고급) 자산 옴니 검색(전체 텍스트 검색)을 사용합니다. 스마트 태그에 대한 별도의 검색 설명이 없습니다.

>[!NOTE]
>
>태그를 학습하고 다른 이미지에 적용할 수 있는 스마트 컨텐츠 서비스의 기능은 교육에 사용하는 이미지의 품질에 따라 달라집니다.
>
>최상의 결과를 얻으려면 Adobe에서 시각적으로 유사한 이미지를 사용하여 각 태그에 대한 서비스를 교육하는 것이 좋습니다.
