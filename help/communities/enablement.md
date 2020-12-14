---
title: 지원 기능 구성
seo-title: 지원 기능 구성
description: 커뮤니티에서 활성 기능 구성
seo-description: 커뮤니티에서 활성 기능 구성
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 5%

---


# 지원 기능 구성 중 {#configuring-enablement-features}

## 개요 {#overview}

지원 기능은 [활성 커뮤니티](overview.md#enablement-community)를 만드는 기능을 제공합니다.

* 이 기능을 사용하려면 제작 환경에서 사용할 추가 라이선스가 필요합니다.

활성 기능을 사용하려면 다음이 필요합니다.

설치:

* **SCORMSharable**
Content Object Reference Model(SCORM)은 eLearning에 대한 표준 및 사양 컬렉션입니다. SCORM은 양도 가능한 ZIP 파일로 콘텐트를 패키지하는 방법도 정의합니다.

* ****
MySQLMySQL은 비디오 진행 상태를 추적하기 위한 테이블뿐만 아니라 지원을 위한 SCORM 추적 및 보고 데이터에 주로 사용되는 관계형 데이터베이스입니다. 지원 기능 팩용 SCORM을 사용하려면 MySQL JDBC 드라이버가 필요합니다.

* ****
FFmpegFFmpeg는 오디오 및 비디오를 변환하고 스트리밍하는 솔루션으로, 설치되면  [비디오 에셋을 제대로 트랜스코딩하는 데 사용됩니다](../../help/sites-authoring/default-components-foundation.md#video). 역량 강화 커뮤니티의 경우 작성 환경에서 업로드된 리소스에 대한 메타데이터를 가져오는 데 사용되며 리소스를 나열할 때 표시할 축소판을 생성합니다.

설정:

* **커뮤니티**
관리자역량 강화 커뮤니티의 경우 
`Community Enablement Managers` 사용자 그룹에는 의 역할이 할당될 수 있으며, 이 역할에는 게시 환경의  `*Community Site* Enablement Manager`컨텐츠 만들기, 할당 및 구성원 관리가 포함될 수 있습니다.

옵션 구성:

* **Adobe**
AnalyticsAdobe Analytics과 통합은 포괄적인 보고 기능을 추가하고 Analytics에 비디오 하트비트 추가를 지원합니다.

* **Dispatcher**

## 구성 단계 {#configuration-steps}

다음은 역량 강화 커뮤니티에 필요한 단계입니다.

각 단계는 필요한 세부 정보를 제공하는 문서에 연결됩니다.

**모든 작성자/게시 인스턴스에서:**

1. **[MySQLUse 웹](deploy-communities.md#jdbc-driver-for-mysql)**
콘솔(번들)용 JDBC 드라이버 설치:http://localhost:4502/system/console/  *번들*
 설치SCORM 패키지 ** 를 설치하기 전에 설치

1. **[SCORM](deploy-communities.md#scorm-package)**
패키지 설치패키지 관리자 사용: 
*http://localhost:4502/crx/packmgr/*

**모든 서버에서:**

1. **[MySQL, MySQL Workbench 설치](mysql.md)**

1. **[MySQL](mysql.md#database-setup)**
데이터베이스 설치작성자 인스턴스에서 다운로드한 SQL 스크립트 실행
\
   MySQL Workbench 사용

**동일한 서버 호스팅 작성자 인스턴스:**

1. **[FFmpeg 설치](ffmpeg.md)**

**모든 작성자/게시 인스턴스에서:**

1. **[JDBC 연결](mysql.md#configure-jdbc-connections)**
풀 구성웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[SCORM 엔진](mysql.md#aem-communities-scormengine-service)**
서비스 구성웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[CSRF](mysql.md#adobe-granite-csrf-filter)**
필터 구성웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

**작성 인스턴스에서:**

1. (*선택 사항*) **[Analytics 서비스 구성](analytics.md)**
도구, 배포, Cloud Services 콘솔 사용: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[FFmpeg](ffmpeg.md#configure-ffmpeg-transcoding-service)**
구성Workflow/Models 콘솔 사용

1. **[터널](deploy-communities.md#tunnel-service-on-author)**
서비스 활성화웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[커뮤니티 관리자](users.md#creating-community-members)** 만들기작성 환경의 경우 클래식 UI 보안 콘솔을 사용합니다. *http://localhost:4502/*
useradmincreate user(s) with path = /home/users/community

   * 다음 그룹에 구성원을 추가합니다.

      * 커뮤니티 활성화 관리자
      * 커뮤니티 관리자

## Dispatcher {#dispatcher}

배포에는 [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)이 포함되어 있는 경우 지원 기능이 제대로 작동하려면 `clientheader`및 `filter`섹션이 수정되어야 합니다. [커뮤니티](dispatcher.md#enablement)에 대한 발송자 구성을 참조하십시오.
