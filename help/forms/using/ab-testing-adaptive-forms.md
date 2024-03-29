---
title: 적응형 양식에 대한 A/B 테스트 만들기 및 관리
seo-title: Create and manage A/B test for adaptive forms
description: AEM Forms은 적응형 양식에 대한 A/B 테스트를 실행하여 고객 경험을 향상시키고 전환율을 향상시킬 수 있는 Adobe Target과 통합됩니다.
seo-description: AEM Forms integrates with Adobe Target that allows running A/B tests for adaptive forms to enhance customer experience and improve conversion rates.
uuid: c41aea04-f4d9-41b9-b1a8-df2bb710354c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: a69ff832-7955-4b10-b47f-287ac385b786
exl-id: e330a8e8-4d55-4723-921b-812cb243f420
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 3%

---

# 적응형 양식에 대한 A/B 테스트 만들기 및 관리 {#create-and-manage-a-b-test-for-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview-br}

고객이 이 기능을 제공하지 않는 경험을 통해 양식을 포기할 가능성이 높습니다. 고객에게 좌절감을 주지만 조직에 대한 지원 볼륨과 비용을 늘릴 수도 있습니다. 전환율을 높일 수 있는 올바른 고객 경험을 식별 및 제공하기 어려운 것도 중요합니다. Adobe Experience Manager Forms은 이 문제의 열쇠를 쥐고 있습니다.

AEM Forms은 Adobe Marketing Cloud 솔루션인 Adobe Target과 통합되어 있으며, 여러 디지털 채널에서 개인화되고 매력적인 고객 경험을 제공할 수 있습니다. Target의 주요 기능 중 하나는 동시 A/B 테스트를 신속하게 설정하고, 타깃팅된 사용자에게 관련 컨텐츠를 제공하고, 전환율을 높이는 경험을 식별할 수 있도록 하는 A/B 테스트입니다.

AEM Forms을 사용하면 적응형 양식에 대해 A/B 테스트를 실시간으로 설정하고 실행할 수 있습니다. 또한 기본 제공 및 사용자 지정 가능한 보고 기능을 제공하여 양식 경험의 실시간 성능을 시각화하고 사용자 참여도와 전환을 극대화하는 것을 식별합니다.

## AEM Forms에서 Target 설정 및 통합 {#set-up-and-integrate-target-in-aem-forms}

적응형 양식에 대한 A/B 테스트를 만들고 분석하기 전에 Target 서버를 설정하고 AEM Forms에 통합해야 합니다.

### Target 설정 {#set-up-target}

AEM을 Target과 통합하려면 유효한 Adobe Target 계정이 있는지 확인합니다. Adobe Target에 등록하면 클라이언트 코드가 전송됩니다. AEM을 Target과 연결하려면 클라이언트 코드, Target 계정과 연결된 이메일 및 암호가 필요합니다.

클라이언트 코드는 Adobe Target 고객 계정을 식별하고 Adobe Target 서버를 호출할 때 URL에서 하위 도메인으로 사용됩니다. 계속하기 전에 로그온하십시오 [https://experience.adobe.com/](https://experience.adobe.com/) 액세스 권한이 있으면 [!DNL Adobe Target] 옵션 [!UICONTROL 빠른 액세스] 섹션을 참조하십시오.

### AEM Forms에서 Target 통합 {#integrate-target-in-aem-forms}

실행 중인 Target 서버를 AEM Forms과 통합하려면 다음 단계를 수행하십시오.

1. AEM 서버에서 https://&lt;*호스트 이름*>:&lt;*포트*>/libs/cq/core/content/tools/cloudservices.html
1. 에서 **Adobe Target** 섹션을 클릭합니다. **구성 표시** 그리고 **+** 아이콘을 클릭하여 새 구성을 추가합니다.

   처음으로 대상을 구성하는 경우 을(를) 클릭합니다. **지금 구성**.

1. 구성 만들기 대화 상자에서 **제목** 그리고 선택적으로 **이름** 참조하십시오.
1. **만들기**&#x200B;를 클릭합니다. 구성 요소 편집 대화 상자가 열립니다.
1. 클라이언트 코드, 이메일 및 암호와 같은 Target 계정 세부 사항을 지정합니다.
1. 선택 **Rest** 를 클릭합니다.
1. Target에 연결하려면 **Adobe Target에 연결**&#x200B;을 클릭하십시오. 정상적으로 연결되면 연결 성공이라는 메시지가 표시됩니다. 메시지에서 **확인**&#x200B;을 클릭한 다음 대화 상자에서 **확인**&#x200B;을 클릭합니다. Target 계정이 구성되었습니다.
1. 에 설명된 대로 Target 프레임워크을 만듭니다. [프레임워크 추가](/help/sites-administering/target.md).
1. https://&lt;*호스트 이름*>:&lt;*포트*>/system/console/configMgr.
1. 클릭 **AEM Forms Target 구성**.
1. 선택 **Target 프레임워크**.
1. 에서 **Target URL** 필드에서 A/B 테스트가 실행될 모든 URL을 지정합니다. 예: https://&lt;*호스트 이름*>:&lt;*포트* OSGi에서 AEM Forms 서버용 >/ 또는 https://&lt;*호스트 이름*>:&lt;*포트* JEE의 AEM Forms 서버용 >/lc/

   게시 인스턴스에 대한 Target URL을 구성하려는 경우 고객이 호스트 이름 또는 IP 주소를 사용하여 URL에 액세스할 수 있다고 가정할 경우 IP 주소와 호스트 이름을 사용하여 둘 다 Target URL로 구성해야 합니다. URL 중 하나만 구성하는 경우 다른 URL에서 오는 고객에 대해서는 A/B 테스트가 실행되지 않습니다. 클릭 **+** 여러 URL을 지정합니다.

1. **저장**&#x200B;을 클릭합니다.

Target 서버가 AEM Forms과 통합되었습니다. 이제 Adobe Target을 활용할 수 있는 전체 라이센스가 있는 경우 A/B 테스트를 활성화할 수 있습니다.

Adobe Target을 활용할 수 있는 전체 라이센스가 있는 경우 AEM Forms과 Target을 통합한 후 다음 매개 변수로 서버를 시작합니다.

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

AEM 인스턴스가 JBoss에서 실행 중인 경우, 턴키에서 서비스로 시작된 후 `jboss\bin\standalone.conf.bat` 파일에서 -Dabtesting.enabled=true 매개 변수를 추가합니다.

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

jboss 서버 외에 모든 애플리케이션 서버의 서버 시작 스크립트에서 -Dabtesting.enabled=true jvm 인수를 추가할 수 있습니다. 이제 적응형 양식에 대한 A/B 테스트를 만들고 실행할 수 있습니다.

>[!NOTE]
>
>나중에 구성된 Target URL을 업데이트하는 경우 실행 중인 A/B 테스트가 현재 URL을 가리키도록 업데이트해야 합니다. A/B 테스트 업데이트에 대한 자세한 내용은 [A/B 테스트 업데이트](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p).

## AEM 내에서 대상 만들기 {#create-audiences-within-aem}

AEM에서는 대상을 만들고 A/B 테스트에 사용할 수 있습니다. AEM 내에서 만드는 대상은 AEM Forms에서 사용할 수 있습니다. AEM 내에서 대상을 만들려면 다음 단계를 수행하십시오.

1. 작성 인스턴스에서 를 누릅니다 **Adobe Experience Manager** > **개인화** > **대상**.

1. 대상 페이지에서 **대상 만들기 > Target 대상 만들기**.
1. Adobe Target 구성 대화 상자에서 Target 구성을 선택하고 **확인**.
1. 새 대상 만들기 페이지에서 규칙을 만듭니다. 규칙을 사용하여 대상을 분류할 수 있습니다. 예를 들어 운영 체제를 기준으로 대상을 분류하려고 합니다. 대상 A는 Windows이고 대상 B는 Linux에서 가져옵니다.

   * Windows를 기준으로 대상을 분류하려면 규칙 #1에서 **OS** 속성 유형입니다. When 드롭다운에서 을 선택합니다. **Windows**.
   * Linux를 기준으로 대상을 분류하려면 규칙 #2에서 **OS** 속성 유형입니다. When 드롭다운에서 을 선택합니다. **Linux**&#x200B;를 클릭하고 **다음**.

1. 만들어진 대상자의 이름을 지정하고 **저장**.

아래 표시된 대로 양식에 대해 A/B 테스트를 구성할 때 대상을 선택할 수 있습니다.

## A/B 테스트 만들기 {#create-a-b-test}

적응형 양식에 대한 A/B 테스트를 만들려면 다음 단계를 수행하십시오.

1. 이동 **Forms 및 문서** https://&lt;*호스트 이름*>:&lt;*포트*>/aem/forms.html/content/dam/formsanddocuments.

1. 적응형 양식이 포함된 폴더로 이동합니다.
1. 을(를) 클릭합니다. **선택** 도구 모음에서 도구를 선택하고 적응형 양식을 선택합니다.
1. 클릭 **자세히** 도구 모음에서 **A/B 테스트 구성**. A/B 테스트 구성 페이지가 열립니다.

[ ](assets/ab-test-configure-1.png)

1. 을(를) 지정합니다 **활동 이름** 를 입력합니다.

1. 대상 드롭다운 목록에서 양식의 다른 경험을 제공할 대상을 선택합니다. 예, **Chrome을 사용하는 방문자**. 대상 목록은 구성된 Target 서버에서 채워집니다.

1. 에서 **경험 배포** 경험 A 및 B에 대한 필드에서 백분율로 배포를 지정하여 총 대상 간 경험 분포를 결정합니다. 예를 들어, 경험 A와 B에 대해 40, 60을 각각 지정하는 경우 경험 A는 대상자의 40%에게 제공되고, 나머지 60%에는 경험 B가 표시됩니다.
1. 클릭 **구성**. A/B 테스트 만들기를 확인하는 대화 상자가 나타납니다.
1. 클릭 **경험 B 편집** 적응형 양식을 편집 모드에서 열려면 다음을 수행하십시오. 양식을 수정하여 기본 경험 A와 다른 경험을 만듭니다. 경험 B에서 사용할 수 있는 가능한 변형은 다음과 같습니다.

   * CSS 또는 스타일링
   * 다른 패널 또는 동일한 패널의 필드 순서
   * 패널 레이아웃
   * 패널 제목
   * 필드에 대한 설명, 레이블 및 도움말 텍스트
   * 제출 흐름에 영향을 주지 않거나 중단되지 않는 스크립트
   * 유효성 검사(클라이언트와 서버 측 모두)
   * 경험 B의 테마(경험 B의 대체 테마를 선택할 수 있음)

1. Forms 및 문서 UI로 이동하고 적응형 양식을 선택하고 **자세히**, 을(를) 선택하고 을(를) 선택합니다. **A/B 테스트 시작**.

이제 A/B 테스트가 실행되고 있으며 지정된 대상이 지정된 배포를 기반으로 경험을 임의로 제공합니다.

## A/B 테스트 업데이트 {#update-a-b-test}

실행 중인 A/B 테스트의 대상 및 경험 배포를 업데이트할 수 있습니다. 방법은 다음과 같습니다.

1. Forms 및 문서 UI에서 A/B 테스트가 실행 중인 적응형 양식이 포함된 폴더로 이동합니다.
1. 적응형 양식을 선택합니다.
1. 클릭 **자세히** 그런 다음 **A/B 테스트 편집**. A/B 테스트 업데이트 페이지가 열립니다.

1. 필요에 따라 대상 및 경험 배포를 업데이트합니다.
1. **업데이트**&#x200B;를 클릭합니다.

## A/B 테스트 보고서 보기 및 분석 {#view-and-analyze-a-b-test-report}

원하는 기간 동안 A/B 테스트를 실행하도록 허용하면 보고서를 생성하고 더 나은 전환을 초래한 경험을 확인할 수 있습니다. 우승자에게 더 나은 수행 경험을 선언하거나 다른 A/B 테스트를 실행하도록 선택할 수 있습니다. 이렇게 하려면 다음 단계를 수행합니다.

1. 적응형 양식을 선택하고 **자세히**&#x200B;를 클릭한 다음 **A/B 테스트 보고서**. 보고서가 표시됩니다.

[ ](assets/ab-test-report-1.png)

1. 보고서를 분석하고 더 성과가 좋은 경험 중 하나를 승자로 선언할 데이터 포인트가 충분한지 확인합니다. 동일한 A/B 테스트를 더 오랫동안 계속하도록 선택하거나 우승자를 선언하고 A/B 테스트를 종료할 수 있습니다.
1. 우승자를 선언하고 A/B 테스트를 종료하려면 **A/B 테스트 종료** 보고 대시보드의 버튼. 두 경험 중 하나를 승자로 선언하라는 대화 상자가 표시됩니다. 우승자를 선택하고 확인을 클릭하여 A/B 테스트를 종료합니다.

   또는, 먼저 을 클릭하여 승자를 선언할 수 있습니다 **승자 선언** 버튼을 클릭합니다. 우승자를 확인하라는 메시지가 표시됩니다. 클릭 **예** A/B 테스트를 종료하려면 다음을 수행하십시오.

경험 A를 승자로 선택하면 A/B 테스트가 종료되고 앞으로 진행되는 모든 대상에는 경험 A만 제공됩니다.
