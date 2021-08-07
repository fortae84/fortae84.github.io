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

- Docker 이미지는 Docker 레지스트리에서 공유 하거나, Hub을 통해 이미지를 받고 설치

### Public Docker Registry

- Docker Hub: https://hub.docker.com
- 공식 Docker 이미지 외 여러 개인이 작성한 Docker 이미지 저장소

### Private Docker Registry

- 별도의 Private 도커 이미지 저장소를 구축하여 직접 관리
- "Docker Hub"를 사용할 경우 하나의 이미지만 저장 가능하며, 추가 사용시 비용 발생

#### Private Docker Registry 구성 - Nexus Oss 3 활용

#### Private Docker Registry 구성 - Docker Image 활용
