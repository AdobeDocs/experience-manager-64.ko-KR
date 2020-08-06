---
title: 설치 시 관리자 암호 구성
seo-title: 설치 시 관리자 암호 구성
description: AEM 설치 시 관리자 암호를 변경하는 방법을 알아봅니다.
seo-description: AEM 설치 시 관리자 암호를 변경하는 방법을 알아봅니다.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# 설치 시 관리자 암호 구성{#configure-the-admin-password-on-installation}

## 개요 {#overview}

버전 6.3부터 AEM에서는 새 인스턴스를 설치할 때 명령줄을 사용하여 관리자 암호를 설정할 수 있습니다.

이전 버전의 AEM에서는 관리자 계정의 암호와 여러 다른 콘솔의 암호를 설치 후 변경해야 했습니다.

이 기능은 AEM 인스턴스를 설치하는 동안 저장소 및 서블릿 엔진에 대한 새 관리자 암호를 설정하는 기능을 추가하므로 이후 수동으로 수행할 필요가 없습니다.

>[!CAUTION]
>
>이 기능에는 Felix Console이 포함되어 있지 않으므로 암호를 수동으로 변경해야 합니다. 자세한 내용은 관련 [보안 검사 목록 섹션을 참조하십시오](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## 어떻게 사용합니까? {#how-do-i-use-it}

이 기능은 명령줄을 통해 AEM을 설치하도록 선택한 경우 자동으로 트리거되며, 파일 시스템 탐색기에서 JAR를 두 번 클릭하는 것은 아닙니다.

명령줄에서 AEM 인스턴스 실행을 위한 일반 동기화는 다음과 같습니다.

```shell
java -jar aem6.3.jar
```

명령줄에서 인스턴스를 실행하면 설치 과정에서 관리자 암호를 변경할 수 있는 옵션이 표시됩니다.

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>관리자 암호를 변경하라는 메시지가 새 AEM 인스턴스를 설치하는 동안에만 나타납니다.

## -nointeractive 플래그 사용 {#using-the-nointeractive-flag}

속성 파일에서 암호를 지정하도록 선택할 수도 있습니다. 이 작업은 시스템 속성과 함께 `-nointeractive` 플래그를 사용하여 `-Dadmin.password.file` 수행됩니다.

다음은 예입니다.

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

파일 내의 암호에는 `passwordfile.properties` 아래 형식이 있어야 합니다.

```xml
admin.password = 12345678
```

>[!NOTE]
>
>시스템 `-nointeractive` 속성 없이 매개 변수를 간단히 사용하면 AEM에서는 `-Dadmin.password.file` 변경할 요청 없이 기본 관리자 암호를 사용하므로 이전 버전의 동작을 그대로 복제할 수 있습니다. 이 비대화형 모드는 설치 스크립트에서 명령줄을 사용하여 자동으로 설치할 때 사용할 수 있습니다.

