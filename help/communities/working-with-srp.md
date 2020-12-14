---
title: SRP - 커뮤니티 컨텐츠 스토리지
seo-title: SRP - 커뮤니티 컨텐츠 스토리지
description: AEM Communities 6.1부터 사용자가 생성한 컨텐츠(UGC)는 SRP(Storage Resource Provider)에서 제공하는 단일 공용 저장소에 저장됩니다
seo-description: AEM Communities 6.1부터 사용자가 생성한 컨텐츠(UGC)는 SRP(Storage Resource Provider)에서 제공하는 단일 공용 저장소에 저장됩니다
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP - 커뮤니티 콘텐츠 저장소 {#srp-community-content-storage}

## 소개 {#introduction}

AEM Communities 6.1부터 UGC(사용자 생성 콘텐츠)는 SRP(저장소 리소스 공급자)에서 제공하는 단일 공용 저장소에 저장됩니다. ASRP, MSRP 및 JSRP와 같이 선택할 수 있는 여러 SRP 옵션이 있습니다.

이전 릴리스와 달리 AEM 인스턴스 간에 UGC의 역방향/전달 복제는 없습니다. 대신 SRP는 JSRP를 제외하고 모든 작성자 및 게시 인스턴스에서 CRUD(작성, 읽기, 업데이트 및 삭제) 작업을 만들기 위해 UGC에 직접 액세스할 수 있도록 합니다.

다음은 각 SRP 옵션](#characteristics-of-srp-options)의 [특성으로, 적절한 SRP 및 [기본 배포](topologies.md)를 선택할 때 결정 프로세스에 중요한 정보입니다.

UGC 사용에 대한 자세한 내용은 [스토리지 리소스 공급자 개요](srp.md)를 참조하십시오.

>[!NOTE]
>
>SRP는 커뮤니티 컨텐츠에만 적용됩니다. 사이트 컨텐츠가 저장되는 위치([노드 저장소](../../help/sites-deploying/data-store-config.md))에는 영향을 주지 않으며 AEM 인스턴스 간 사용자 등록, 사용자 프로필 및 사용자 그룹의 보안 처리에 영향을 주지 않습니다([사용자 데이터 관리](#managing-user-data) 참조).

>[!CAUTION]
>
>AEM 6.1부터 [UGC는 결코 복제되지 않습니다](#ugc-never-replicated).
>
>배포에 기본 [JSRP](topologies.md#jsrp) 토폴로지와 같은 공용 저장소가 포함되어 있지 않으면 UGC는 입력한 AEM 게시 또는 작성자 인스턴스에서만 표시됩니다. 토폴로지에 게시 클러스터가 포함된 경우에만 게시 인스턴스에서 UGC를 볼 수 있습니다.

## SRP 옵션 {#characteristics-of-srp-options} 특성

[ASRP - Adobe 저장소 리소스 공급자](asrp.md)\
이 옵션을 사용할 경우 UGC는 Adobe에 호스팅되고 관리되는 클라우드 서비스에서 원격으로 유지됩니다. 특정 라이선스에 대한 계정을 프로비저닝하려면 추가 라이선스가 필요하며 계정 담당자와 함께 작업해야 합니다.

* 커뮤니티 콘텐츠를 저장하려면 Adobe에서 제공 및 지원하는 관련 클라우드 서비스가 필요합니다.
* 특정 지역의 데이터 센터 선택 필요(미국, EMEA, APAC)
* SRP API를 통해 UGC에 대한 모든 프로그래머틱 액세스 필요
* TarMK 게시 팜에 적합
* 로컬 스토리지에 투자할 의사가 없는 경우 적합

>[!NOTE]
>
>ASRP의 게시물(또는 주석)에 첨부 파일을 업로드하는 데는 50MB의 제한이 있습니다.

[MSRP - MongoDB 저장소 리소스 공급자](msrp.md)\
이 옵션을 사용하면 UGC가 로컬 MongoDB 인스턴스에 직접 유지됩니다.

* 커뮤니티 콘텐츠를 저장하려면 MongoDB의 라이센스가 허용하는 로컬 설치가 필요합니다.
* Apache Solr의 로컬 설치 필요
* SRP API를 통해 UGC에 대한 모든 프로그래머틱 액세스 필요
* 기존 TarMK 게시 팜에 적합
* MongoMK 또는 RdbMK 클러스터에 적합
* 많은 양의 커뮤니티 컨텐츠가 필요할 때 적합

[DSRP - 관계형 데이터베이스 저장소 리소스 공급자](dsrp.md)\
이 옵션을 사용할 경우 UGC는 로컬 MySQL 데이터베이스 인스턴스에 직접 유지됩니다.

* 커뮤니티 콘텐츠를 저장하려면 MySQL의 로컬 설치가 필요합니다.
* Apache Solr의 로컬 설치 필요
* SRP API를 통해 UGC에 대한 모든 프로그래머틱 액세스 필요
* 기존 TarMK 게시 팜에 적합
* MongoMK 또는 RdbMK 클러스터에 적합
* 많은 양의 커뮤니티 컨텐츠가 필요할 때 적합

[JSRP - JCR 스토리지 리소스 공급자](jsrp.md)\
기본 옵션을 사용할 경우 공통 스토어가 없습니다. UGC는 입력한 AEM 인스턴스와 동일한 JCR 저장소에만 지속됩니다.

* AEM 작성자 또는 게시 인스턴스가 게시된 JCR 저장소에 커뮤니티 컨텐츠를 저장합니다.
* SRP API를 통해 UGC에 대한 모든 프로그래머틱 액세스 필요
* 둘 이상의 게시 인스턴스가 배포된 경우 게시 클러스터가 필요합니다(TarMK 팜의 게시 인스턴스 간에 복제 메커니즘이 없음).
* 중재는 게시 환경에서만 수행됩니다(작성자와 게시 사이에 역방향/전달 복제 메커니즘이 없음).
* 일반적으로 개발, 데모 및 트레이닝에 적합합니다.

## SRP {#configuring-srp} 구성

기본 배포에 따라 기본 저장소 옵션을 지정하는 것은 [스토리지 구성 콘솔](srp-config.md)을 통해 수행됩니다.

각 옵션에 대한 구성 세부 사항은 다음을 참조하십시오.

* [ASRP - Adobe 저장소 리소스 공급자](asrp.md)
* [MSRP - MongoDB 저장소 리소스 공급자](msrp.md)
* [DSRP - 관계형 데이터베이스 저장소 리소스 공급자](dsrp.md)
* [JSRP - JCR 스토리지 리소스 공급자](jsrp.md)

스토리지 옵션을 적극적으로 선택하지 않으면 기본적으로 JSRP가 활성화됩니다.

## 추가 정보 {#additional-information}

### UGC가 복제되지 않음 {#ugc-never-replicated}

작성 환경에서 작성자는 페이지 컨텐츠를 만들어 게시 환경에 복제합니다. 페이지에 주석, 검토, 포럼, 블로그 또는 QnA와 같은 대화형 AEM Communities 기능이 포함되어 있으면 게시 인스턴스에서 구성원(사이트 방문자에 로그인됨)의 상호 작용으로 인해 게시 환경에 입력된 사용자 생성 컨텐츠(UGC)가 나타납니다.

이전에는 이 커뮤니티 콘텐트가 작성자 인스턴스로, 복제된 작성자에서 게시 인스턴스로 역복제되었습니다. 역/앞으로 복제를 통해 AEM 인스턴스 간의 일관성을 유지하는 것은 문제가 있었습니다.

AEM Communities 6.1부터 위에서 설명한 바와 같이 UGC에 대한 공유 스토리지를 사용하여 UGC의 복제 필요성을 제거했습니다.

사이트 컨텐츠가 복제되는 동안 UGC는 복제되지 않습니다.

### 사용자 데이터 관리 {#managing-user-data}

커뮤니티에 대한 관심 사항은 [*사용자*, *사용자 그룹* 및 *사용자 프로필*](users.md)&#x200B;입니다. 토폴로지가 [게시 팜](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)인 경우 게시 환경에서 만들고 업데이트할 때 이 사용자 관련 데이터를 다른 게시 인스턴스에서 사용할 수 있어야 합니다.

AEM Communities 6.1부터 사용자 관련 데이터는 복제 대신 Sling 배포를 사용하여 동기화됩니다. 자세한 내용은 [사용자 동기화](sync.md)를 참조하십시오.

### AEM Communities 6.2로 업그레이드 {#upgrading-to-aem-communities}

AEM Communities 6.3으로 업그레이드할 때 기존 UGC를 보존해야 하는 경우 AEM 5.6.1 또는 AEM 6.0 커뮤니티에서 UGC의 On-Demand 스토리지 또는 On-Premise 스토리지(UGC)를 사용하는지 여부에 따라 단계를 수행해야 합니다.

자세한 내용은 [AEM Communities 6.3으로 업그레이드](upgrade.md)를 참조하십시오.
