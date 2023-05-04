---
title: AEM 문제 해결
seo-title: Troubleshooting AEM
description: AEM의 문제 해결에 대해 알아봅니다.
seo-description: Learn about troubleshooting issues with AEM.
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
exl-id: 34b509d5-4e80-4229-b155-40004856e87e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 5%

---

# AEM 문제 해결{#troubleshooting-aem}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

다음 섹션에서는 AEM을 사용할 때 발생할 수 있는 몇 가지 문제와 이러한 문제를 해결하는 방법에 대한 제안 사항을 다룹니다.

>[!NOTE]
>
>AEM에서 작성 문제를 해결하는 경우 [작성자를 위한 문제 해결.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>문제가 발생하는 경우 [알려진 문제](/help/release-notes/known-issues.md) 예(릴리스 및 서비스 팩).

## 관리자에 대한 문제 해결 시나리오 {#troubleshooting-scenarios-for-administrators}

다음 표에서는 관리자가 문제를 해결해야 할 수 있는 문제에 대한 개요를 제공합니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>역할</strong></td> 
   <td><strong>문제 </strong></td> 
  </tr> 
  <tr> 
   <td>시스템 관리자</td> 
   <td><p>Quickstart jar를 두 번 클릭해도 아무런 효과가 없거나 다른 프로그램(예: 아카이브 관리자)에서 jar 파일을 엽니다</p> </td> 
  </tr> 
  <tr> 
   <td><p>시스템 관리자</p> </td> 
   <td><p>CRX에서 실행 중인 내 애플리케이션에서 메모리 부족 오류가 발생합니다</p> </td> 
  </tr> 
  <tr> 
   <td><p>시스템 관리자</p> </td> 
   <td><p>AEM CM Quickstart를 두 번 클릭해도 AEM 시작 화면이 브라우저에 표시되지 않습니다</p> </td> 
  </tr> 
  <tr> 
   <td><p>시스템 관리자</p> <p>관리자 사용자</p> </td> 
   <td><p>스레드 덤프 만들기</p> </td> 
  </tr> 
  <tr> 
   <td><p>시스템 관리자</p> <p>관리자 사용자</p> </td> 
   <td><p>닫히지 않은 JCR 세션 확인</p> </td> 
  </tr> 
 </tbody> 
</table>

## 설치 문제 {#installation-issues}

자세한 내용은 [일반적인 설치 문제](/help/sites-deploying/troubleshooting.md#common-installation-issues) 다음 문제 해결 시나리오에 대한 자세한 내용은

* Quickstart jar를 두 번 클릭해도 아무런 효과가 없거나 JAR 파일이 다른 프로그램(예: 아카이브 관리자)과 함께 있는 경우에는 적용되지 않습니다.
* CRX에서 실행되는 응용 프로그램에서 메모리 부족 오류가 발생합니다.
* AEM Quickstart를 두 번 클릭해도 AEM 시작 화면이 브라우저에 표시되지 않습니다.

## 분석 문제 해결 방법 {#methods-for-troubleshooting-analysis}

### 스레드 덤프 만들기 {#making-a-thread-dump}

스레드 덤프는 현재 활성 상태인 모든 Java 스레드의 목록입니다. AEM이 제대로 응답하지 않으면 스레드 덤프가 교착 상태 또는 기타 문제를 식별하는 데 도움이 될 수 있습니다.

### Sling 스레드 덤퍼 사용 {#using-sling-thread-dumper}

1. 를 엽니다. **AEM 웹 콘솔**; 예를 들어 `http://localhost:4502/system/console/`.

1. 을(를) 선택합니다 **스레드**&#x200B;아래에&#x200B;**상태** 탭.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### jstack 사용(명령줄) {#using-jstack-command-line}

1. AEM Java 인스턴스의 PID(프로세스 ID)를 찾습니다.

   예를 들어 `ps -ef` 또는 `jps`.

1. 실행:

   `jstack <pid>`

1. 스레드 덤프가 표시됩니다.

>[!NOTE]
>
>를 사용하여 스레드 덤프를 로그 파일에 추가할 수 있습니다 `>>` 출력 리디렉션:
>
>`jstack <pid> >> /path/to/logfile.log`

자세한 내용은 [JVM에서 스레드 덤프를 가져오는 방법](https://helpx.adobe.com/cq/kb/TakeThreadDump.html) 자세한 내용은 설명서 를 참조하십시오

### 닫히지 않은 JCR 세션 확인 {#checking-for-unclosed-jcr-sessions}

AEM WCM용 기능을 개발하면 JCR 세션을 열 수 있습니다(데이터베이스 연결을 여는 것과 유사). 열린 세션이 종료되지 않으면 시스템에 다음과 같은 증상이 나타날 수 있습니다.

* 시스템이 느려집니다.
* 많은 CacheManager를 볼 수 있습니다. 크기 조정 로그 파일의 모든 항목 다음 숫자(size=&lt;x>)에 캐시 수가 표시되고 각 세션은 여러 캐시를 엽니다.
* 시스템이 때때로 메모리가 부족합니다(심각도에 따라 몇 시간, 일 또는 몇 주 후).

닫히지 않은 세션을 분석하고 세션을 닫지 않는 코드를 확인하려면 기술 자료 문서를 참조하십시오 [닫히지 않은 세션 분석](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html).

### Adobe Experience Manager 웹 콘솔 사용 {#using-the-adobe-experience-manager-web-console}

OSGi 번들의 상태는 가능한 문제를 조기에 나타낼 수도 있습니다.

1. 를 엽니다. **AEM 웹 콘솔**; 예를 들어 `http://localhost:4502/system/console/`.

1. 선택 **번들** 아래에 **OSGI** 탭.

1. 확인:

   * 번들 상태. 비활성 또는 충족되지 않은 경우 번들을 중지하고 다시 시작하려고 합니다. 문제가 지속되면 다른 방법을 사용하여 더 자세히 조사해야 할 수 있습니다.
   * 번들에 종속성이 있는지 여부. 이러한 세부 사항은 링크인 개별 번들 이름 을 클릭하여 확인할 수 있습니다(다음 예에는 문제가 없음).

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
