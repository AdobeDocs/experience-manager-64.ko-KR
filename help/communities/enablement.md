---
title: 사용 기능 구성
seo-title: Configuring Enablement Features
description: 커뮤니티에서 사용 기능 구성
seo-description: Configure enablement features in Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 6%

---

# 사용 기능 구성 {#configuring-enablement-features}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

사용 기능은 다음을 만드는 기능을 제공합니다 [지원 커뮤니티](overview.md#enablement-community).

* 이 기능을 사용하려면 프로덕션 환경에서 사용할 추가 라이선스가 필요합니다.

사용 기능을 사용하려면 다음 조건을 충족해야 합니다.

설치:

* **SCORM**
SCORM(Sharable Content Object Reference Model)은 e-learning을 위한 표준 및 사양 모음입니다. 또한 SCORM은 컨텐츠를 전송 가능한 ZIP 파일로 패키지하는 방법을 정의합니다.

* **MySQL**
MySQL은 주로 SCORM 추적 및 Enablement 보고 데이터와 비디오 진행 상황을 추적하는 데 사용되는 관계형 데이터베이스입니다. 지원 기능 팩용 SCORM에는 MySQL JDBC 드라이버가 필요합니다.

* **FFmpeg**
FFmpeg는 오디오 및 비디오를 변환 및 스트리밍하는 솔루션이며, 설치된 경우 를 적절한 코드 변환에 사용합니다 [비디오 자산](../../help/sites-authoring/default-components-foundation.md#video). 지원 커뮤니티의 경우 작성자 환경에서 업로드된 리소스에 대한 메타데이터를 가져오고 리소스를 나열할 때 표시할 축소판을 생성하는 데 사용됩니다.

설정:

* **커뮤니티 관리자**
지원 커뮤니티의 경우 
`Community Enablement Managers` 사용자 그룹에는 `*Community Site* Enablement Manager`게시 환경에 컨텐츠 작성, 할당 및 멤버 관리를 포함할 수 있는 권한이 있는 사용자입니다.

구성 옵션:

* **Adobe Analytics**
Adobe Analytics과 통합하면 포괄적인 보고 기능이 추가되고 Analytics에 비디오 하트비트 추가를 지원합니다.

* **Dispatcher**

## 구성 단계 {#configuration-steps}

다음은 지원 커뮤니티에 필요한 단계입니다.

각 단계는 필요한 세부 정보를 제공하는 설명서에 연결합니다.

**모든 작성자/게시 인스턴스에서 다음을 수행합니다.**

1. **[MySQL용 JDBC 드라이버 설치](deploy-communities.md#jdbc-driver-for-mysql)**
웹 콘솔 사용(번들): 설치 *http://localhost:4502/system/console/bundles*
설치 *이전* SCORM 패키지 설치

1. **[scorm 패키지 설치](deploy-communities.md#scorm-package)**
패키지 관리자 사용: 
*http://localhost:4502/crx/packmgr/*

**모든 서버에서:**

1. **[mySQL, MySQL Workbench 설치](mysql.md)**

1. **[mySQL 데이터베이스 설치](mysql.md#database-setup)**
작성자 인스턴스에서 다운로드한 SQL 스크립트 실행
\
   MySQL Workbench 사용

**작성자 인스턴스를 호스팅하는 동일한 서버:**

1. **[ffMPEG 설치](ffmpeg.md)**

**모든 작성자/게시 인스턴스에서 다음을 수행합니다.**

1. **[JDBC 접속 풀 구성](mysql.md#configure-jdbc-connections)**
웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[scorm 엔진 서비스 구성](mysql.md#aem-communities-scormengine-service)**
웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[csrf 필터 구성](mysql.md#adobe-granite-csrf-filter)**
웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

**작성자 인스턴스:**

1. (*옵션*) **[analytics 서비스 구성](analytics.md)**
도구, 배포, Cloud Services 콘솔 사용: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[ffMPEG 구성](ffmpeg.md#configure-ffmpeg-transcoding-service)**
워크플로우/모델 콘솔 사용

1. **[터널 서비스 활성화](deploy-communities.md#tunnel-service-on-author)**
웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[커뮤니티 관리자 만들기](users.md#creating-community-members)** 작성 환경의 경우 클래식 UI 보안 콘솔을 사용합니다. *http://localhost:4502/useradmin*
경로 = /home/users/community를 사용하여 사용자 만들기

   * 다음 그룹에 구성원을 추가합니다.

      * 커뮤니티 지원 관리자
      * 커뮤니티 관리자

## Dispatcher {#dispatcher}

배포가 [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)사용 기능이 제대로 작동하려면 `clientheader`및 `filter`섹션을 수정해야 합니다. 자세한 내용은 [커뮤니티에 대한 Dispatcher 구성](dispatcher.md#enablement).
