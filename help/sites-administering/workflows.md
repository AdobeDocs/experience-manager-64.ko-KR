---
title: 워크플로우 관리
seo-title: 워크플로우 관리
description: AEM에서 워크플로우를 관리하는 방법을 알아봅니다.
seo-description: AEM에서 워크플로우를 관리하는 방법을 알아봅니다.
uuid: d000a13c-97cb-4b1b-809e-6c3eb0d675e8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 4b09cd44-434e-4834-bc0d-c9c082a4ba5a
exl-id: e57b7a69-6e25-4066-ad7a-917969cebbe8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 2%

---

# 워크플로우 관리{#administering-workflows}

워크플로우를 통해 Adobe Experience Manager(AEM) 활동을 자동화할 수 있습니다. 워크플로우:

* 특정 순서로 실행되는 일련의 단계로 구성됩니다.

   * 각 단계에서는 개별 활동을 수행합니다.사용자 입력 대기, 페이지 활성화 또는 이메일 메시지 보내기 등의 작업을 수행할 수 있습니다.

* 저장소, 사용자 계정 및 AEM 서비스의 자산과 상호 작용할 수 있습니다.
* AEM의 모든 측면을 포함하는 복잡한 활동을 조정할 수 있습니다.

조직에서 설정한 비즈니스 프로세스는 워크플로우로 표시될 수 있습니다. 예를 들어, 웹 사이트 컨텐츠를 게시하는 프로세스에는 일반적으로 다양한 관련자의 승인 및 로그오프와 같은 단계가 포함됩니다. 이러한 프로세스는 AEM 워크플로우로 구현하고 콘텐츠 페이지 및 자산에 적용할 수 있습니다.

* [워크플로우 시작](/help/sites-administering/workflows-starting.md)
* [워크플로우 인스턴스 관리](/help/sites-administering/workflows-administering.md)
* [워크플로우에 대한 액세스 관리](/help/sites-administering/workflows-managing.md)

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* 워크플로우에 적용 및 참여:[워크플로우 작업](/help/sites-authoring/workflows.md)
>* 워크플로우 모델 만들기 및 워크플로우 기능 확장:[워크플로우 개발 및 확장](/help/sites-developing/workflows.md)
>* 중요한 서버 리소스를 사용하는 워크플로우의 성능 개선:[동시 워크플로 처리](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing)

>



## 워크플로우 모델 및 인스턴스 {#workflow-models-and-instances}

[AEM](/help/sites-developing/workflows.md#model) 의 워크플로우 모델은 비즈니스 프로세스를 나타내고 구현합니다.

* 일반적으로 페이지나 자산에서 움직여서 특정 결과를 얻습니다.
* 이러한 페이지 및/또는 자산을 워크플로우 페이로드라고 합니다.
* 워크플로우 모델은 특정 작업을 수행하는 일련의 단계로 구성됩니다.
* 워크플로우가 진행되면서 페이로드가 단계별로 전달됩니다.

워크플로우 모델이 시작(실행)되면 워크플로우 인스턴스가 생성됩니다. 고유한 워크플로우 인스턴스를 생성할 때마다 워크플로우 모델을 여러 번 시작할 수 있습니다. 각 인스턴스에 대해 워크플로우 모델이 정의하는 단계가 실행됩니다.

>[!CAUTION]
>
>수행되는 단계는 인스턴스가 생성되는 시점에 워크플로우 모델 *에 의해 정의된 단계입니다.* 자세한 내용은 [워크플로우 개발](/help/sites-developing/workflows.md#model)을 참조하십시오.

워크플로우 인스턴스는 다음 라이프사이클을 통해 진행됩니다.

1. 워크플로우 모델이 시작되고 워크플로우 인스턴스가 생성되고 실행됩니다.

   1. 모델이 시작될 때 워크플로우 인스턴스의 페이로드가 식별됩니다.
   1. 인스턴스는 생성 시 모델의 사본입니다.
   1. AEM 작성자, 관리자 또는 서비스는 워크플로우 모델을 시작할 수 있습니다.

1. 워크플로우 모델의 첫 번째 단계가 실행됩니다.
1. 단계가 완료되고 워크플로우 엔진은 모델을 사용하여 실행할 다음 단계를 결정합니다.
1. 워크플로우 모델의 후속 단계가 실행 및 완료됩니다.
1. 최종 단계가 완료되면 워크플로우 인스턴스가 완료되어 보관됩니다.

많은 유용한 워크플로우 모델에도 AEM이 제공됩니다. 또한 조직의 개발자는 비즈니스 프로세스의 특정 요구 사항에 맞게 사용자 지정 워크플로우 모델을 만들 수 있습니다.

## 워크플로우 단계 {#workflow-steps}

워크플로우 단계가 실행되면 워크플로우 인스턴스와 연결됩니다. 워크플로우 인스턴스의 기록에는 인스턴스에 대해 실행된 각 단계에 대한 정보가 포함되어 있습니다. 이 정보는 실행 중에 발생하는 문제를 조사하는 데 유용합니다.

사용자 또는 서비스는 단계 유형에 따라 워크플로우 단계를 수행합니다.

* 사용자가 단계를 수행하면 받은 편지함에 배치되는 작업 항목이 할당됩니다. 사용자는 워크플로우 인스턴스가 진행되도록 단계를 수동으로 완료할 책임이 있습니다.
* 서비스가 단계를 수행하면, 완료 시 워크플로우 인스턴스가 자동으로 다음 단계로 진행합니다.

>[!NOTE]
>
>오류가 발생하면 서비스/단계 구현에서 오류 시나리오에 대한 동작을 처리해야 합니다. 워크플로우 엔진 자체는 작업을 다시 시도한 다음 오류를 기록하고 인스턴스를 중지합니다.

## 워크플로우 상태 및 작업 {#workflow-status-and-actions}

워크플로우에는 다음 상태 중 하나가 있을 수 있습니다.

* **실행** 중:워크플로우 인스턴스가 실행 중입니다.
* **완료됨**:워크플로 인스턴스가 종료되었습니다.

* **일시 중단**:워크플로 인스턴스가 일시 중지되었습니다.
* **중단됨**:워크플로 인스턴스가 종료되었습니다.
* **부실**:워크플로 인스턴스의 진행에서는 백그라운드 작업이 실행되어야 하지만 시스템에서 작업을 찾을 수 없습니다. 이 문제는 워크플로우를 실행할 때 오류가 발생할 수 있습니다.

>[!NOTE]
>
>프로세스 단계를 실행하면 오류가 발생하면 관리자의 받은 편지함에 단계가 나타나고 워크플로우 상태는 **RUNNING**&#x200B;입니다.

현재 상태에 따라 워크플로우 인스턴스의 일반 진행에 개입해야 하는 경우 워크플로우 인스턴스 실행 작업을 수행할 수 있습니다.

* **일시 중단**:워크플로우의 실행을 일시적으로 중지합니다. 일시 중단은 예를 들어 유지 관리를 위해 워크플로우를 진행하지 않으려는 특별한 경우에 유용합니다. 일시 중단하면 워크플로우 상태가 일시 중단됨으로 변경됩니다.
* **다시 시작**:동일한 구성을 사용하여 일시 중지된 실행 시점에 일시 중지된 워크플로우를 다시 시작합니다.
* **종료**:워크플로우 실행을 종료하고 상태를 ABORTED로  **변경합니다**. 중단된 워크플로 인스턴스를 다시 시작할 수 없습니다.
