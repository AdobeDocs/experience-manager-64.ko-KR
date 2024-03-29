---
title: SRP - 커뮤니티 컨텐츠 저장소
seo-title: SRP - Community Content Storage
description: AEM Communities 6.1부터 UGC(사용자 생성 컨텐츠)는 SRP(저장소 리소스 제공자)가 제공하는 단일 공통 저장소에 저장됩니다
seo-description: As of AEM Communities 6.1, user generated content (UGC) is stored in a single, common store provided by a storage resource provider (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Admin
exl-id: 4ff530ae-c676-4259-86f2-a3881843b642
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 1%

---

# SRP - 커뮤니티 컨텐츠 저장소 {#srp-community-content-storage}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 소개 {#introduction}

AEM Communities 6.1부터 UGC(사용자 생성 컨텐츠)는 SRP(저장소 리소스 제공자)가 제공하는 단일 공통 저장소에 저장됩니다. ASRP, MSRP 및 JSRP와 같이 선택할 수 있는 여러 SRP 옵션이 있습니다.

이전 릴리스와 달리 AEM 인스턴스 간에 UGC의 역방향/전달 복제가 없습니다. 대신 SRP를 사용하면 JSRP를 제외하고 모든 작성자 및 게시 인스턴스에서 CRUD(만들기, 읽기, 업데이트 및 삭제) 작업을 위해 UGC에 직접 액세스할 수 있습니다.

다음은 다음과 같습니다 [각 SRP 옵션의 특성](#characteristics-of-srp-options)- 적절한 SRP를 선택할 때 결정 프로세스에 중요한 정보입니다. [기본 배포](topologies.md).

UGC용 SRP 사용에 대한 자세한 내용은 [저장소 리소스 공급자 개요](srp.md).

>[!NOTE]
>
>SRP는 커뮤니티 콘텐츠에만 적용됩니다. 사이트 컨텐츠가 저장되는 위치에는 영향을 주지 않습니다([노드 저장소](../../help/sites-deploying/data-store-config.md))이고, AEM 인스턴스 간 사용자 등록, 사용자 프로필 및 사용자 그룹의 보안 처리에 영향을 주지 않습니다(참조 [사용자 데이터 관리](#managing-user-data)).

>[!CAUTION]
>
>AEM 6.1부터, [UGC는 복제되지 않습니다.](#ugc-never-replicated).
>
>배포에 기본값과 같은 공통 저장소가 포함되지 않은 경우 [JSRP](topologies.md#jsrp) 토폴로지, UGC는 입력된 AEM 게시 또는 작성자 인스턴스에만 표시됩니다. 토폴로지에 게시 클러스터가 포함된 경우에만 게시 인스턴스에서 UGC가 표시됩니다.

## SRP 옵션 특성 {#characteristics-of-srp-options}

[ASRP - Adobe 저장소 리소스 공급자](asrp.md)\
이 옵션을 사용하면 UGC는 Adobe에서 호스팅 및 관리하는 클라우드 서비스에서 원격으로 유지됩니다. 특정 라이센스에 대한 계정을 제공하려면 추가 라이센스가 필요하며 계정 담당자와 협력해야 합니다.

* 커뮤니티 컨텐츠를 저장하려면 Adobe이 제공하고 지원하는 관련 클라우드 서비스가 필요합니다
* 특정 지역의 데이터 센터 선택 필요(미국, EMEA, APAC)
* SRP API를 통해 UGC에 대한 모든 프로그래밍 방식 액세스 필요
* TarMK 게시 팜에 적합
* 로컬 스토리지에 투자할 의사가 없는 경우 적합

>[!NOTE]
>
>ASRP의 게시물(또는 댓글)에 첨부 파일을 업로드하는 데는 50MB의 제한이 있습니다.

[MSRP - MongoDB 저장소 리소스 공급자](msrp.md)\
이 옵션을 사용하면 UGC가 로컬 MongoDB 인스턴스에서 직접 유지됩니다.

* 커뮤니티 컨텐츠를 저장하려면 MongoDB의 사용이 허가된 로컬 설치가 필요합니다
* Apache Solr의 로컬 설치 필요
* SRP API를 통해 UGC에 대한 모든 프로그래밍 방식 액세스 필요
* 기존 TarMK 게시 팜에 적합
* MongoMK 또는 RdbMK 클러스터에 적합
* 대량의 커뮤니티 컨텐츠가 필요한 경우 적합

[DSRP - 관계형 데이터베이스 저장소 리소스 공급자](dsrp.md)\
이 옵션을 사용하면 UGC가 로컬 MySQL 데이터베이스 인스턴스에 직접 유지됩니다.

* 커뮤니티 콘텐츠를 저장하려면 MySQL의 로컬 설치 필요
* Apache Solr의 로컬 설치 필요
* SRP API를 통해 UGC에 대한 모든 프로그래밍 방식 액세스 필요
* 기존 TarMK 게시 팜에 적합
* MongoMK 또는 RdbMK 클러스터에 적합
* 대량의 커뮤니티 컨텐츠가 필요한 경우 적합

[JSRP - JCR 저장소 리소스 공급자](jsrp.md)\
기본 옵션을 사용하면 공통 저장소가 없습니다. UGC는 입력된 AEM 인스턴스와 동일한 JCR 저장소에서만 유지됩니다.

* 게시된 AEM 작성자 또는 게시 인스턴스의 JCR 저장소에 커뮤니티 콘텐츠를 저장합니다
* SRP API를 통해 UGC에 대한 모든 프로그래밍 방식 액세스 필요
* 둘 이상의 게시 인스턴스가 배포되는 경우 게시 클러스터가 필요합니다(TarMK 팜의 게시 인스턴스 간에 복제 메커니즘이 없음)
* 중재는 게시 환경에서만 수행됩니다(작성자와 게시 간에 역방향/전달 복제 메커니즘이 없음)
* 일반적으로 개발, 데모 및 교육에 가장 적합합니다

## SRP 구성 {#configuring-srp}

기본 배포를 기반으로 기본 스토리지 옵션을 지정하는 것은 [스토리지 구성 콘솔](srp-config.md).

각 옵션에 대한 구성 세부 사항은 다음을 참조하십시오.

* [ASRP - Adobe 저장소 리소스 공급자](asrp.md)
* [MSRP - MongoDB 저장소 리소스 공급자](msrp.md)
* [DSRP - 관계형 데이터베이스 저장소 리소스 공급자](dsrp.md)
* [JSRP - JCR 저장소 리소스 공급자](jsrp.md)

활성 스토리지 옵션을 선택하지 않으면 기본적으로 JSRP가 활성화됩니다.

## 추가 정보 {#additional-information}

### UGC 복제 안 함 {#ugc-never-replicated}

작성 환경에서 작성자는 페이지 컨텐츠를 만들고 게시 환경에 복제합니다. 페이지에 댓글, 검토, 포럼, 블로그 또는 QnA와 같은 대화형 AEM Communities 기능이 포함되어 있으면 게시 인스턴스에서 구성원(로그인한 사이트 방문자)의 상호 작용으로 인해 게시 환경에 입력된 사용자 생성 컨텐츠(UGC)가 발생합니다.

이전에는 이 커뮤니티 컨텐츠가 작성자 인스턴스로 역복제되고, 작성자에서 게시 인스턴스로 복제되었습니다. 역방향 및 순방향 복제를 통해 AEM 인스턴스 간의 일관성을 유지하는 것은 문제가 되었습니다.

AEM Communities 6.1부터 위에 설명된 대로 UGC용 공유 저장소를 사용하여 UGC를 복제할 필요가 없어졌습니다.

사이트 컨텐츠가 복제되는 동안 UGC는 복제되지 않습니다.

### 사용자 데이터 관리 {#managing-user-data}

커뮤니티에 대한 관심 또한 다음과 같습니다 [*사용자*, *사용자 그룹*, 및 *사용자 프로필*](users.md). 게시 환경에서 만들고 업데이트될 때 이 사용자 관련 데이터는 토폴로지가 일 때 다른 게시 인스턴스에서 사용할 수 있도록 해야 합니다 [팜 게시](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

AEM Communities 6.1부터 사용자 관련 데이터는 복제 대신 Sling 배포를 사용하여 동기화됩니다. 자세한 내용은 [사용자 동기화](sync.md).

### AEM Communities 6.2로 업그레이드 {#upgrading-to-aem-communities}

AEM Communities 6.3으로 업그레이드할 때 기존 UGC를 유지해야 하는 경우 AEM 5.6.1 또는 AEM 6.0 커뮤니티에서 Adobe 온디맨드 스토리지 또는 UGC의 온-프레미스 스토리지를 사용하는지 여부에 따라 단계를 수행해야 합니다.

자세한 내용은 [AEM Communities 6.3으로 업그레이드](upgrade.md).
