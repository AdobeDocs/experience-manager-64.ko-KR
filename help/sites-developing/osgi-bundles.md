---
title: OSGI 번들
seo-title: OSGI 번들
description: OSGi 번들 관리를 위한 팁
seo-description: OSGi 번들 관리를 위한 팁
uuid: 07af7089-a233-4e5b-928c-76ddc0af8839
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8d3374ac-51dd-4ff5-84c9-495c937ade12
exl-id: 19df20a9-7c89-4dfa-8eca-81c4a14c21ff
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 1%

---

# OSGI 번들{#osgi-bundles}

## 시맨틱 버전 관리 사용 {#use-semantic-versioning}

의미 체계 버전 번호 지정에 대한 우수 사례는 [https://semver.org/](https://semver.org/)에서 찾을 수 있습니다.

## OSGi 번들 {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}에 절대적으로 필요한 것보다 더 많은 클래스와 jar를 포함하지 마십시오

공통 라이브러리는 별도의 번들로 분리해야 합니다. 이렇게 하면 번들에서 다시 사용할 수 있습니다. OSGI 번들에서 *JAR*&#x200B;를 래핑할 때는 온라인 소스에서 이미 이 작업이 수행되었는지 확인합니다. 기존 번들 래퍼를 찾기 위한 몇 가지 일반적인 위치는 다음과 같습니다.Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse 번들 Recipes 및 SpringSource Enterprise 번들 저장소.

## 가장 필요한 번들 버전 {#depend-on-the-lowest-needed-bundle-versions}에 따라 다름

POM 파일의 컴파일 시간 종속성의 경우 는 항상 필요한 API를 표시하는 가장 필요한 버전에 따라 다릅니다. 이렇게 하면 이전 버전과의 호환성을 더 높일 수 있고 이전 릴리스에 대한 백업 수정 사항을 더 쉽게 만들 수 있습니다.

## OSGi 번들 {#export-a-minimal-set-of-packages-from-osgi-bundles}에서 최소 패키지 세트를 내보냅니다.

패키지를 내보내는 즉시 다른 사람이 사용할 수 있는 API를 만들었습니다. 가능한 한 적게 내보내고 내보내는 것이 API인지 확인합니다. 개인 메서드/클래스를 가져와서 공개하기 더 쉽습니다. 이전에 내보낸 내용을 가져와서 비공개로 만드는 것보다 더 쉽습니다.

구현은 항상 별도의 *impl* 패키지에 넣어야 합니다. 기본적으로 *maven-bundle-plugin*&#x200B;은 해당 이름에 *impl*&#x200B;이 없는 프로젝트의 모든 항목을 내보냅니다.

## 내보낸 각 패키지에 대해 항상 시맨틱 버전을 명시적으로 정의합니다. {#always-explicitly-define-a-semantic-version-for-each-package-exported}

이렇게 하면 API 소비자가 사용자와 함께 진화할 수 있습니다. 이때 항상 시맨틱 버전 관리 우수 사례를 따라야 합니다. 이렇게 하면 API 소비자가 새 버전에서 기대할 변경 사항 유형을 알 수 있습니다.

## {#include-metatype-information-where-exposed}이 노출되는 메타데이터 정보 포함

의미 있는 메타데이터 유형 정보를 지정하면 Felix 콘솔에서 서비스와 구성 요소를 쉽게 이해할 수 있습니다. SCR 주석 및 속성 목록은 다음 위치에서 찾을 수 있습니다.[https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html)
