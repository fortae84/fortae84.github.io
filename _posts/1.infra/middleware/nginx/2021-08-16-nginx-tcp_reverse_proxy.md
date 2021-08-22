---
title: Nginx - TCP/UDP Reverse Proxy 구성
author: Fortae
date: 2021-08-16 00:32:00 -0500
categories: [1.Infra, Nginx]
tags: [infra, middleware, Nginx]
---

- Nginx 1.9.0부터 ngx_stream_core_module 지원
- ngx_stream_core_module을 사용, TCP/UDP Reverse Proxy 구성 가능
- 윈도우 / Linux 모두 지원

```
- TCP/UDP Reverse Proxy 구성 nginx.conf 예시

#user  nobody;
worker_processes  auto;

error_log  logs/error.log;
error_log  logs/notice.log  notice;
error_log  logs/info.log  info;

#pid        logs/nginx.pid;

events {
    worker_connections  1024;
}

stream
{
    #로그 Format
    log_format  basic   'time: $time_local / '
                'network: client_address($remote_addr:$remote_port) >> proxy_address($server_addr:$server_port) >> server_address($upstream_addr) / '
                'protocal($protocol) status($status) / '
                'process_time: session_time($session_time) upstream_connect_time($upstream_connect_time) / '
                'request: bytes_received($bytes_received) upstream_bytes_sent($upstream_bytes_sent) / '
                'response: bytes_sent($bytes_sent) upstream_bytes_received($upstream_bytes_received) ';

    proxy_connect_timeout 20s;
    proxy_timeout 20s;


    server{

            // TCP 수신 Proxy port
        listen 12345;
        access_log      logs/service_socket.log  basic buffer=1k flush=5s;
        // TCP 송신 IP & port
            proxy_pass 127.0.0.1:9050;

    }

}
```
