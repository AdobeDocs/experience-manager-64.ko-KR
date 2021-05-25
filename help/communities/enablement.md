---
title: 사용 기능 구성
seo-title: 사용 기능 구성
description: 커뮤니티에서 사용 기능 구성
seo-description: 커뮤니티에서 사용 기능 구성
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Administrator
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 5%

---

# 사용 기능 구성 {#configuring-enablement-features}

## 개요 {#overview}

사용 기능은 [지원 커뮤니티를 만드는 기능을 제공합니다](overview.md#enablement-community).

* 이 기능을 사용하려면 프로덕션 환경에서 사용할 추가 라이선스가 필요합니다.

사용 기능을 사용하려면 다음 조건을 충족해야 합니다.

설치:

* ****
SCORMSharable Content Object Reference Model (SCORM)은 e-learning을 위한 표준 및 사양의 모음입니다. 또한 SCORM은 컨텐츠를 전송 가능한 ZIP 파일로 패키지하는 방법을 정의합니다.

* ****
MySQLMySQL은 주로 비디오 진행 상황을 추적하는 테이블뿐만 아니라 SCORM 추적 및 활성화를 위한 보고 데이터에 사용되는 관계형 데이터베이스입니다. 지원 기능 팩용 SCORM에는 MySQL JDBC 드라이버가 필요합니다.

* ****
FFmpegFFmpeg는 오디오 및 비디오를 변환 및 스트리밍하는 솔루션이며, 설치된 경우  [비디오 자산의 적절한 코드 변환에 사용됩니다](../../help/sites-authoring/default-components-foundation.md#video). 지원 커뮤니티의 경우 작성자 환경에서 업로드된 리소스에 대한 메타데이터를 가져오고 리소스를 나열할 때 표시할 축소판을 생성하는 데 사용됩니다.

설정:

* **커뮤니티**
관리자지원 커뮤니티의 경우 
`Community Enablement Managers` 사용자 그룹에는 게시 환경의 컨텐츠 작성, 할당  `*Community Site* Enablement Manager`및 멤버 관리를 포함하는 권한이 있는 의 역할이 할당될 수 있습니다.

구성 옵션:

* **Adobe Analytics**
와 Analytics 통합은 포괄적인 보고 기능을 추가하고 Analytics에 비디오 하트비트 추가를 지원합니다.

* **Dispatcher**

## 구성 단계 {#configuration-steps}

다음은 지원 커뮤니티에 필요한 단계입니다.

각 단계는 필요한 세부 정보를 제공하는 설명서에 연결합니다.

**모든 작성자/게시 인스턴스에서 다음을 수행합니다.**

1. **[MySQLUse 웹](deploy-communities.md#jdbc-driver-for-mysql)**
콘솔(번들)용 JDBC 드라이버 설치:SCORM  *패키지를 설치하기*
전에 http://localhost:4502/system/console/ ** bundles를 설치합니다

1. **[scorm 패키지](deploy-communities.md#scorm-package)**
설치패키지 관리자 사용: 
*http://localhost:4502/crx/packmgr/*

**모든 서버에서:**

1. **[mySQL, MySQL Workbench 설치](mysql.md)**

1. **[MySQL](mysql.md#database-setup)**
데이터베이스 설치작성자 인스턴스에서 다운로드한 SQL 스크립트 실행
\
   MySQL Workbench 사용

**작성자 인스턴스를 호스팅하는 동일한 서버:**

1. **[ffMPEG 설치](ffmpeg.md)**

**모든 작성자/게시 인스턴스에서 다음을 수행합니다.**

1. **[JDBC 연결](mysql.md#configure-jdbc-connections)**
풀 구성웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[scorm 엔진](mysql.md#aem-communities-scormengine-service)**
서비스 구성웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[csrf 필터](mysql.md#adobe-granite-csrf-filter)**
구성Web Console 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

**작성자 인스턴스:**

1. (*선택 사항*) **[Analytics 서비스 구성](analytics.md)**
도구, 배포, Cloud Services 콘솔 사용: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[ffMPEG](ffmpeg.md#configure-ffmpeg-transcoding-service)**
사용 워크플로우/모델 콘솔 구성

1. **[터널](deploy-communities.md#tunnel-service-on-author)**
서비스 활성화웹 콘솔 사용(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[커뮤니티 관리자](users.md#creating-community-members)** 만들기작성 환경의 경우 클래식 UI 보안 콘솔을 사용합니다. *http://localhost:4502/*
useradmincreate user(s) with path = /home/users/community

   * 다음 그룹에 구성원을 추가합니다.

      * 커뮤니티 지원 관리자
      * 커뮤니티 관리자

## Dispatcher {#dispatcher}

배포에 [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)이 포함되어 있는 경우 지원 기능이 제대로 작동하려면 `clientheader`및 `filter`섹션이 수정되어야 합니다. [Communities에 대한 Dispatcher 구성](dispatcher.md#enablement)을 참조하십시오.
