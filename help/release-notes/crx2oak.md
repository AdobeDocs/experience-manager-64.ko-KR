---
title: CRX2OAK 마이그레이션 도구
seo-title: CRX2OAK 마이그레이션 도구
description: Adobe Experience Manager 6.4 CRX2OAK 마이그레이션 툴과 관련된 릴리스 노트입니다.
seo-description: Adobe Experience Manager 6.4 CRX2OAK 마이그레이션 툴과 관련된 릴리스 노트입니다.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc

---


# CRX2OAK 마이그레이션 도구 {#crx-oak-migration-tool}

## 변경 사항 및 수정 사항 목록 {#list-of-changes-and-fixes}

### 1.8.6(2018년 6월) {#june}

* OAK-7339 LoopbackBlobStore를 도입하여 MissingBlobStore에서 UnsupportedOperationException을 사용하여 모든 사이드그레이드 분류를 수정합니다.
* Oak 1.8.4 사용

### 1.8.4(2018년 4월) {#april}

* Oak 버전 1.8.2 사용
* GRANITE-18104 6.3에서 6.4로 리포 마이그레이션 오류는 더욱 의미 있어야 합니다.
* GRANITE-16571 SHA-1 교체

   * —version 옵션을 사용할 때 도구 체크섬이 이제 SHA-512입니다.

* GRANITE-17601 Embed oak-upgrade in CRX2Oak with oak-blob-cloud
* GRANITE 파섹 18553 CRX2OAK는 버전이 마이그레이션되지 않더라도 노드에 버전 속성을 남깁니다.

### 버전 1.6.8(2017년 3월) {#version-march}

* Oak 버전이 1.6.1로 업데이트되었습니다.
* CQ-61847 crx2oak-quickstart-extension과 crx2oak(마이그레이션 프로필 추가) 병합
* CQ-97488 AEM 실행 모드 홍보 및 삭제(sling.options.file을 다시 작성하여)
* GRANITE-12798/OAK-4260 Capability to side grade from Oak Segment Tar

### 버전 1.4.2(2016년 3월) {#version-march-1}

* Oak 버전을 1.4.1로 업그레이드
* OAK-3846 / GRANITE-10748 nodetype 제약 조건을 위반하는 경우 SNS 노드 이름 변경
* OAK-3910 / GRANITE-10730 버전 내역 `mix:versionable` 없이 상속된 노드 마이그레이션
* OAK-4128 / GRANITE-11757 `RepositorySidegrade` 이 루트 노드 속성을 복사하지 않음

### 버전 1.3.4(2016년 1월) {#version-january}

* Oak 버전을 1.3.16으로 업그레이드
* OAK-3844 / GRANITE-10730 버전 내역 없이 버전 가능한 노드에 대한 향상된 지원
* OAK-3846 nodetype 제약 조건을 위반하는 경우 SNS 노드의 이름을 변경합니다.

### 버전 1.3.2(2015년 12월) {#version-december}

* Oak 버전을 1.3.12로 업그레이드
* 마이그레이션 후 데이터 저장소 디렉토리를 이동해서는 안 됩니다(GRANITE-10447).
* crx2oak-quickstart-extension과 crx2oak 병합(CQ-61847)
* crx2oak가 저장소의 중복 값에 실패함(CQ-61906)
* CQ 5.x에서 마이그레이션 후 긴 AEM 시작(GRANITE-10309)
* crx2oak에서 여러 LDAP 서버 지원(GRANITE-9917)
* 최대 노드 이름 길이 확인(OAK-3111)
* 마이그레이션 소스로 S3DataSource 지원(OAK-3685)
