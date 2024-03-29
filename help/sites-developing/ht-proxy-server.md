---
title: 프록시 서버 도구 사용 방법
seo-title: How to use the Proxy Server Tool
description: 프록시 서버는 클라이언트와 서버 사이의 요청을 중계하는 중간 서버 역할을 합니다
seo-description: The proxy server acts as an intermediate server that relays requests between a client and a server
uuid: 30f4f46d-839e-4d23-a511-12f29b3cc8aa
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: dfbc1d2f-80c1-4564-a01c-a5028b7257d7
exl-id: 63f3a172-b551-433a-aad5-58c6bfda82bb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 2%

---

# 프록시 서버 도구 사용 방법{#how-to-use-the-proxy-server-tool}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

프록시 서버는 클라이언트와 서버 사이의 요청을 중계하는 중간 서버 역할을 합니다. 프록시 서버는 모든 클라이언트-서버 상호 작용을 추적하고 전체 TCP 통신 로그를 출력합니다. 이렇게 하면 주 서버에 액세스하지 않고도 진행 상황을 정확하게 모니터링할 수 있습니다.

AEM 설치에서 프록시 서버를 찾을 수 있습니다.

`crx-quickstart/opt/helpers/proxy-2.1.jar`

프록시 서버를 사용하여 기본 통신 프로토콜에 관계없이 모든 클라이언트-서버 상호 작용을 모니터링할 수 있습니다. 예를 들어 다음 프로토콜을 모니터링할 수 있습니다.

* 웹 페이지용 HTTP
* 보안 웹 페이지용 HTTPS
* 전자 메일 메시지의 SMTP
* 사용자 관리를 위한 LDAP

예를 들어 TCP/IP 네트워크를 통해 통신하는 두 응용 프로그램 사이에 프록시 서버를 배치할 수 있습니다. 예: 웹 브라우저 및 AEM 이를 통해 CQ 페이지를 요청할 때 발생하는 일을 정확하게 모니터링할 수 있습니다.

## 프록시 서버 도구 시작 {#starting-the-proxy-server-tool}

명령줄에서 서버를 시작합니다.

`java -jar proxy-2.1.jar <host> <remoteport> <localport> [options]`

**매개변수**

`<host>`

연결할 CRX 인스턴스의 호스트 주소입니다. 인스턴스가 로컬 컴퓨터에 있는 경우 `localhost`.

`<remoteport>`

대상 CRX 인스턴스의 호스트 포트입니다. 예를 들어 새로 설치된 AEM 설치의 기본값은 입니다 **`4502`** 새로 설치된 AEM 작성자 인스턴스의 기본값은 입니다. `4502`.

`<localport>`

프록시를 통해 CRX 인스턴스에 액세스하기 위해 연결할 로컬 시스템의 포트입니다.

**옵션**

`-q` (자동 모드)

콘솔 창에 출력을 쓰지 않습니다. 연결 속도를 저하하지 않으려는 경우 또는 출력을 파일에 기록하는 경우 사용합니다( -logfile 옵션 참조).

`-b`(이진 모드)

트래픽에서 특정 바이트 조합을 찾는 경우 이진 모드를 활성화합니다. 그런 다음 출력에 16진수와 문자 출력이 포함됩니다.

`-t` (타임스탬프 로그 항목)

각 로그 출력에 타임스탬프를 추가합니다. 타임스탬프가 초 단위이므로 단일 요청을 확인하는 데 적합하지 않을 수 있습니다. 프록시 서버를 장기간 사용하는 경우 특정 시간에 발생한 이벤트를 찾을 때 사용합니다.

`-logfile <filename>`(로그 파일에 쓰기)

클라이언트-서버 대화를 로그 파일에 씁니다. 이 매개 변수는 조용한 모드에서도 작동합니다.

**`-i <numIndentions>`**(들여쓰기 추가)

각 활성 연결은 보다 잘 읽을 수 있도록 들여씁니다. 기본값은 16개 수준입니다. 이 기능은 `proxy.jar version 1.16`.

### 로그 형식 {#log-format}

proxy-2.1.jar에서 생성한 로그 항목은 모두 다음 형식을 갖습니다.

`[timestamp (optional)] [Client|Server]-[ConnectionNumber]-[BytePosition] ->[Character Stream]`

예를 들어, 웹 페이지에 대한 요청은 다음과 같을 수 있습니다.

`C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]`

* C는 이 항목이 클라이언트에서 왔음을 의미합니다(웹 페이지에 대한 요청임)
* 0은 연결 번호입니다(연결 카운터는 0부터 시작).
* #00000 스트림의 오프셋입니다. 첫 번째 항목이므로 오프셋은 0입니다.
* `[GET <?>]` 는 HTTP 헤더(url) 중 하나의 예에서 요청의 콘텐츠입니다.

연결이 닫히면 다음 정보가 기록됩니다.

```
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

클라이언트 사이에 전달된 바이트 수를 표시합니다( `C`) 및 서버( `S`)을 클릭하여 제품에서 사용할 수 있습니다.

**로그 출력의 예**

예를 들어, 요청 시 다음 코드를 생성하는 페이지를 생각해 보십시오.

### 예 {#example}

예를 들어, 다음 저장소의 매우 간단한 html 문서를 생각해 보십시오.

`/content/test.html`

에 있는 이미지 파일과 함께

`/content/test.jpg`

의 콘텐츠 `test.html` is:

```xml
<html>
<head>
    <title>Test</title>
</head>  
<body>
    Test<br>
    <img src="test.jpg">
</body>
</html>
```

AEM 인스턴스가 `localhost:4502` 다음과 같이 프록시를 시작합니다.

`java -jar proxy.jar localhost 4502 4444 -logfile test.log`

이제 프록시를 통해 CQ/CRX 인스턴스에 액세스할 수 있습니다. `localhost:4444` 이 포트를 통한 모든 통신이 `test.log`.

이제 프록시의 출력을 보면 브라우저와 AEM 인스턴스 간의 상호 작용이 표시됩니다.

프록시를 시작할 때 다음과 같이 출력합니다.

```xml
starting proxy for localhost:4502 on port 4444
using logfile: <some-dir>/crx-quickstart/opt/helpers/test.log
```

그런 다음 브라우저를 열고 테스트 페이지에 액세스합니다.

`http://localhost:4444/content/test.html`

그리고 브라우저가 `GET` 페이지에 대한 요청:

```shell
C-0-#000000 -> [GET /content/test.html HTTP/1.1 ]
C-0-#000033 -> [Host: localhost:4444 ]
C-0-#000055 -> [Connection: keep-alive ]
C-0-#000079 -> [User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_4) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.57 Safari/536.11 ]
C-0-#000212 -> [Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 ]
C-0-#000285 -> [Accept-Encoding: gzip,deflate,sdch ]
C-0-#000321 -> [Accept-Language: en-US,en;q=0.8 ]
C-0-#000354 -> [Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3 ]
C-0-#000402 -> [Cookie: login-token=179ba6bd-e0a7-4909-a965-e11c7f2bc2fc%3a618bd8a8-fbaf-43c5-827d-c84c62248c5e_22ee860cc9036fee%3acrx.default%3b21148fb0-eb6c]
C-0-#000543 -> [-43c9-a2b9-c8d40618d8ae%3ad87a3d1a-5e9a-4d5a-bab1-0ee60ad6d8df_d0e4ddce0fcd84b6%3acrx.default%3b5cb95227-ea51-47bf-850b-68ad1dfd7297%3af3bbb6]
C-0-#000684 -> [59-7913-4285-8857-832c087bafd5_c484727d3b3665ad%3acrx.default; ys-cq-siteadmin-tree=o%3Awidth%3Dn%253A240%5EselectedPath%3Ds%253A/content ]
C-0-#000824 -> [ ]
```

AEM 인스턴스는 파일의 컨텐츠에 응답합니다 `test.html`:

```shell
S-0-#000000 -> [HTTP/1.1 200 OK ]
S-0-#000017 -> [Connection: Keep-Alive ]
S-0-#000041 -> [Server: Day-Servlet-Engine/4.1.24  ]
S-0-#000077 -> [Content-Type: text/html;charset=utf-8 ]
S-0-#000116 -> [Content-Length: 104 ]
S-0-#000137 -> [Date: Mon, 16 Jul 2012 11:23:38 GMT ]
S-0-#000174 -> [Last-Modified: Mon, 16 Jul 2012 11:19:27 GMT ]
S-0-#000220 -> [ ]
S-0-#000222 -> [<html>]
S-0-#000229 -> [<head>]
S-0-#000236 -> [    <title>Test</title>]
S-0-#000260 -> [</head> ]
S-0-#000269 -> [<body>]
S-0-#000276 -> [ Test<br>]
S-0-#000286 -> [    <img src="test.jpg">]
S-0-#000311 -> [</body>]
S-0-#000319 -> [</html>]
```

### 프록시 서버의 사용 {#uses-of-the-proxy-server}

다음 시나리오는 프록시 서버를 사용할 수 있는 몇 가지 목적을 보여 줍니다.

**쿠키 및 해당 값 확인**

다음 로그 항목 예는 프록시가 시작된 이후 열린 6번째 연결에 대해 클라이언트가 보낸 모든 쿠키 및 해당 값을 보여줍니다.

`C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]`

**헤더 및 해당 값 확인**

다음 로그 항목 예는 서버가 keep-alive 연결을 만들 수 있고 콘텐츠 길이 헤더가 올바르게 설정되었음을 보여줍니다.

```
S-7-#000017 -> [Connection: Keep-Alive ]
 ...
 S-7-#000107 -> [Content-Length: 124 ]
```

**Keep-Alive가 작동하는지 확인**

Keep-alive는 클라이언트가 서버에 대한 TCP 연결을 다시 사용하여 여러 요청을 수행할 수 있도록 해주는 HTTP의 기능입니다(페이지 코드, 그림, 스타일 시트 등). keep-alive가 없으면 클라이언트는 각 요청에 대해 새 연결을 설정해야 합니다.

keep-alive가 작동하는지 확인하려면:

* 프록시 서버를 시작합니다.
* 페이지를 요청합니다.
* keep-alive가 작동하는 경우 연결 카운터가 5~10개 연결을 넘지 않아야 합니다.
* keep-alive 가 작동하지 않을 경우 연결 카운터가 빠르게 증가합니다.

**손실된 요청 찾기**

방화벽 및 디스패처와 같은 복잡한 서버 설정에서 요청을 손실하는 경우 프록시 서버를 사용하여 요청이 손실된 위치를 확인할 수 있습니다. 방화벽의 경우:

* 방화벽 전에 프록시 시작
* 방화벽 후 다른 프록시 시작
* 이러한 속성을 사용하여 요청이 가져오는 범위를 확인할 수 있습니다.

**요청 보류**

요청이 수시로 바뀌는 경우:

* 프록시를 시작합니다.
* 타임스탬프가 있는 각 항목이 있는 파일에 액세스 로그를 기다리거나 기록합니다.
* 요청 연결이 끊어지면 열려 있는 연결 수와 문제가 발생하는 요청을 확인할 수 있습니다.
