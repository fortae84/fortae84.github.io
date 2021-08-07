<link rel="stylesheet" type="text/css" href="../style.css" />

<div align="center">
    <img src="./images/docker.png" width="200px" />
</div>

## **Docker**

- Linux Container화 기술
- 애플리케이션의 실행 환경을 구축 및 운영하기 위한 플랫폼
  - **Build**: Docker 이미지를 만드는 기능
  - **Ship**: Docker 이미지를 공유하는 기능
  - **Run**: Docker Container를 작동시키는 기능

## Docker Image 관리

- Docker Image는 Docker 레지스트리에서 공유 하거나, Hub을 통해 Image를 받고 설치

### Public Docker Registry

- Docker Hub: https://hub.docker.com
- 공식 Docker Image 외 여러 개인이 작성한 Docker Image 저장소

### Private Docker Registry

- 별도의 Private 도커 Image 저장소를 구축하여 직접 관리
- "Docker Hub"를 사용할 경우 하나의 Image만 저장 가능하며, 추가 사용시 비용 발생

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

    # 로컬PC/Server에 저장되어 있는 이미지 자체 레지스트리로 이관
    docker tag "이미지 이름":"이미지 버전" localhost:5000/"이미지 이름"

    # Image 레지스트리에 저장하기
    docker push localhost:5000/"이미지 이름"

    # Web GUI기반 Docker Registry Dashboard 제공하나 비추천
    # Docker image hyper/docker-registry-web 참조

```

### Private Docker Registry 구성 - Nexus Oss 3 활용

- Nexus 설치

  - Nexus3 소프트웨어 설치 버전을 다운 받아서 구성: https://www.sonatype.com/products/repository-oss-download

  - 공식 Docker 이미지 sonatype/nexus3 사용

  ```
    # Docker Nexus3 oss 이미지 다운로드
    docker pull sonatype/nexus3:latest

    # Docker Nexus3 oss 이미지 실행
    docker run -d -p 8081:8081  \
        --name nexus    \
        -e NEXUS_CONTEXT=nexus  \
        -v c:/some/dir/nexus-data:/nexus-data \
        sonatype/nexus3
  ```

- Nexus3 Docker Repository 구성
