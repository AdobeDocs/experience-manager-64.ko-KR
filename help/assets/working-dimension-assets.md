---
title: Adobe Dimension 에셋 작업
seo-title: Adobe Dimension 에셋 작업
description: AEM 3D에서 Adobe Dimension 에셋을 사용한 작업
seo-description: AEM 3D에서 Adobe Dimension 에셋을 사용한 작업
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# Adobe Dimension 에셋 작업 {#working-with-adobe-dimension-assets}

AEM 3D 기능 팩은 AEM Assets, AEM Sites 및 AEM Screens의 Adobe Dimension 에셋(`.dn` 파일)을 지원합니다.

glTF 개방형 표준을 기반으로 하는 새로운 3D 뷰어는 Adobe Dimension 에셋에 대한 미리 보기 및 사이트 및 화면 보기 기능을 제공합니다.

## 클라우드 기반 전환 서비스 정보 {#about-the-cloud-based-conversion-service}

Dimension 자산이 AEM에 업로드되면 파일의 사본이 Amazon AWS에서 호스팅되는 Adobe 관리 클라우드 기반 서비스로 전달됩니다. 이 서비스는 Adobe 전용 Dimension 파일 포맷에서 개방형 표준 glTF 포맷으로 변환합니다. 변환된 3D 모델은 바이너리 glTF(`.glb`)로 패키징됩니다. AEM은 변환된 모델을 기본 Dimension 에셋과 함께 변환으로 저장합니다.

다음 두 가지 방법 중 하나를 사용하여 `.glb` 전환 형식을 구성할 수 있습니다( [지침은 AEM 3D](install-config-3d.md) 설치 및 구성 참조).

* Adobe glTF 뷰어를 사용하여 AEM Assets, AEM Sites 또는 AEM Screens에서 Dimension 에셋을 볼 때 시각적 품질을 최대화하려면 Adobe 전용 익스텐션을 포함합니다. 이렇게 하면 대부분의 타사 응용 프로그램과 호환되지 않는 변환이 만들어집니다. `.glb`
* Adobe별 익스텐션을 제외하여 타사 애플리케이션과의 `.glb` 변환과 호환됩니다. 이렇게 하면 AEM Assets, AEM Sites 또는 AEM Screens(예: IBL 조명 없음)에서 볼 때 시각적 품질을 제한하여 일반적인 타사 애플리케이션의 품질을 시뮬레이션할 수 있습니다.

Dimension/glTF 파일을 Amazon AWS로 또는 AWS에서 전송하고 AWS의 임시 저장소는 완벽하게 보호됩니다. 이러한 파일은 Amazon AWS에서 최소한의 시간 동안 지속됩니다. 일반적으로 정상적인 작업 중에는 몇 분 이내입니다.

Dimension 자산에 대한 지원을 활성화하려면 전환 서비스에 액세스하기 위해 Adobe에서 자격 증명을 구해야 합니다. See [Installing and configuring AEM 3D](install-config-3d.md).

>[!NOTE]
>
>제공된 자격 증명을 설치하고 사용하는 경우, Amazon AWS에서 호스팅되는 Adobe 관리 클라우드 기반 전환 서비스로 Adobe Dimension 3D 자산을 전송 및 처리할 것임을 이해하고 이에 동의합니다.

### AEM Assets에서 보기 {#viewing-on-aem-assets}

AEM 3D 기능 팩에는 Adobe Dimension 자산을 보는 데 사용되는 glTF 열기 표준을 기반으로 하는 새로운 뷰어가 포함되어 있습니다. 이 뷰어는 Dimension 파일 또는 압축된 glTF를 AEM Assets의 세부 사항 보기 또는 AEM Sites의 3D 구성 요소로 열면 자동으로 선택됩니다.

glTF 뷰어의 사용자 인터페이스는 다른 모든 3D 자산 유형에 사용되는 표준 3D 뷰어와 다소 다릅니다.

#### See also the following: {#see-also-the-following}

* [AEM 3D 릴리스 노트](/help/release-notes/aem3d-release-notes.md) - Dn 에셋 및 glTF 뷰어에 적용할 수 있는 제한 사항 및 제한에 대한 정보입니다.
* [Adobe Dimension 자산과 관련된 구성 요소](using-the-3d-sites-component.md) 속성에 대한 3D 사이트 구성 요소 작업
* [클라우드 기반 전환 서비스를 구성하기 위해 AEM 3D](install-config-3d.md) 설치 및 구성

