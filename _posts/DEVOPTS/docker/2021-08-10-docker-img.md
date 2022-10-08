---
title: Docker - Image 관리
author: Fortae
date: 2021-08-10 18:32:00 -0500
categories: [DEVOPTS, KUBERNETES, DOCKER]
tags: [docker]
---

## Docker Image 관리

- Docker Image는 Docker 레지스트리에서 공유 하거나, Hub을 통해 Image를 받고 설치

### Public Docker Registry

- Docker Hub: https://hub.docker.com
- 공식 Docker Image 외 여러 개인이 작성한 Docker Image 저장소

### Private Docker Registry

- 별도의 Private 도커 Image 저장소를 구축하여 직접 관리
- Docker Hub를 사용할 경우 하나의 Image만 저장 가능하며, 추가 사용시 비용 발생

### Private Docker Registry 구성 - Docker registry Image 활용

```
    # Docker Registry 이미지 다운로드
    docker pull registry:latest

    # Docker Registry 이미지 실행
    docker run --name local-registry \
        -d --restart=always \
        -p 5000:5000 \
        -v c:/ftdata/sol-registry:/var/lib/registry/docker/registry/v2 \
        registry:latest

    # http 통신 가능하도록 특정 /etc/docker/daemon.json 파일 변경
    {
        "insecure-registries":["localhost:5000"]
    }

    # 로컬PC/Server에 저장되어 있는 이미지 자체 레지스트리로 이관
    docker tag "이미지 이름":"이미지 버전" localhost:5000/"이미지 이름"

    # Image local 레지스트리에 저장하기
    docker push localhost:5000/"이미지 이름"

    # Web GUI기반 Docker Registry Dashboard 제공하나 비추천
    # Docker image hyper/docker-registry-web 참조

```

### Private Docker Registry 구성 - Nexus oss 3 활용

- Nexus 설치

  - Nexus3 소프트웨어 설치 버전을 다운 받아서 구성: https://www.sonatype.com/products/repository-oss-download

  - 공식 Docker 이미지 sonatype/nexus3 사용

  ```
    # Docker Nexus3 oss 이미지 다운로드
    docker pull sonatype/nexus3:latest

    # Docker Nexus3 oss 이미지 실행
    docker run -d \
        -p 8081:8081  \
        -p 5000:5000  \
        --name nexus    \
        -e NEXUS_CONTEXT=nexus  \
        -v c:/ftdata/sol-nexus-data:/nexus-data \
        sonatype/nexus3
  ```

- Nexus3 Docker Repository 구성

  1. Nexus3 oss 웹사이트 접속: http://localhost:8081/nexus
  2. Nexus3 oss 로그인
     - 기본 계정은 admin 이며 비밀번호는 컨테이너안 /nexus-data/admin.password에 저장되어 있음
     - docker exec -it nexus bin/sh | cat /nexus-data/admin.password
  3. 상단 톰니바쿼 아이콘(Server administration and configuration) 클릭 -> Repository 클릭 -> Create repository 클릭
  4. docker hosted 클릭 -> Name에 repo 이름 지정한다
  5. Repository Connectors http 체크: docker전용 http포트 지정한다
  6. Enable Docker V1 API 체크: 기본은 Docker V2버전이며 V2는 https만 지원한다.

  ```
    # http 통신 가능하도록 특정 /etc/docker/daemon.json 파일 변경
    {
        "insecure-registries":["localhost:5000"]
    }

    # 로컬PC/Server에 저장되어 있는 이미지 자체 레지스트리로 이관
    docker tag "이미지 이름":"이미지 버전" localhost:5000/"이미지 이름"

    # Image 레지스트리에 저장하기
    docker push localhost:5000/"이미지 이름"
  ```
