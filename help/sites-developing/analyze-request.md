---
title: 분석 요청 스크립트
seo-title: 분석 요청 스크립트
description: 요청 분석 스크립트는 나중에 처리할 수 있도록 읽을 수 있는 보고서를 생성하는 access.log 파일의 분석을 쉽게 하기 위해 수행됩니다
seo-description: 요청 분석 스크립트는 나중에 처리할 수 있도록 읽을 수 있는 보고서를 생성하는 access.log 파일의 분석을 쉽게 하기 위해 수행됩니다
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 7%

---

# 분석 요청 스크립트{#request-analysis-script}

## 다운로드 {#download}

이 스크립트는 나중에 처리할 수 있도록 읽을 수 있는 보고서를 생성하는 `access.log` 파일의 분석을 쉽게 하기 위해 수행됩니다.

[파일 가져오기](assets/analyse-access.sh)

## 설명 {#description}

이 스크립트는 나중에 처리할 수 있도록 읽을 수 있는 보고서를 생성하는 `access.log` 파일의 분석을 쉽게 하기 위해 수행됩니다.

이렇게 하면 시간에 따른 전체 요청 수, GET과 POST, 요청 배포 등이 생성됩니다.

출력은 Markdown 구문으로 있으므로 Markdown 뷰어와 같은 플러그인이 있는 브라우저에서 또는 pandoc와 같은 도구를 사용하여 PDF로 변환하는 것이 더 쉽습니다.

명령줄에서 제공된 사용자 지정 경로를 분석할 수 있습니다.

파일 내의 주석에서 주석을 실행하는 방법을 설명하는 가져오기:

CQ `access.log`을 분석하여 다양한 정보를 추출하고 `stdout`에 Markdown 출력을 생성합니다.

## 사용량 {#usage}

`./analyse-access.sh access.log.2013-&ast;`

명령줄에서 분석할 추가 사용자 지정 경로를 제공할 수 있습니다

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

간단한 파이핑으로 출력을 저장할 수 있습니다

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
