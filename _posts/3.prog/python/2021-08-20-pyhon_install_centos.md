---
title: Python3 Centos 설치
author: Fortae
date: 2021-08-20 00:00:00 -0500
categories: [3.Programming, Python]
tags: [programming, Python, backend]
---

- yum 을 이용한 Python3 간편 설치

```bash
-- kakao centos repo 추가
vi /etc/yum.repos.d/kakao-repo

[base]
name=CentOS-$releasever - Base
baseurl=http://ftp.daumkakao.com/centos/$releasever/AppStream/$basearch/os/
gpgcheck=0
[updates]
name=CentOS-$releasever - Updates
baseurl=http://ftp.daumkakao.com/centos/$releasever/AppStream/$basearch/os/
gpgcheck=0
[extras]
name=CentOS-$releasever - Extras
baseurl=http://ftp.daumkakao.com/centos/$releasever/AppStream/$basearch/os/
gpgcheck=0

-- yum을 이용 python3 설치
yum install python3

-- 파이썬 버전 확인
python3 -V

```



- 파이썬 SDK를 받아 직접 서버에 설치 (yum이 안될경우 rpm을 직접받아 관련 패키지 설치)


```bash
-- wget이 없을 경우 yum을 이용하여 wget 설치
yum install wget

-- Python 설치할 경로에서 wget으로 파이썬 최신 버전 다운로드 
wget https://www.python.org/ftp/python/3.9.6/Python-3.9.6.tgz

-- 따운 받은 파일 압축 해제
tar xzf Python-3.9.6.tgz

-- Python 해당 폴더로 이동, compile 수행
cd Python-3.9.6
./configure --enable-optimizations

-- 오류 발생시 "configure: error: no acceptable C compiler found in $PATH" gcc 설치 및 compile 재수행
yum install gcc openssl-devel bzip2-devel libffi-devel

-- make이 없을 경우 yum을 이용하여 make 설치
yum install make

-- 설치
make altinstall

-- which가 없을 경우 yum을 이용하여 which 설치
yum install which

-- 설치된 파이썬 위치 확인 
which python3.9

-- .bashrc or .bash_profile 파이썬 환경변수 선언
alias python="/usr/local/bin/python3.9"

-- 환경변수 적용
source /root/.bashrc

-- 파이썬 버전 확인
phyhon -V

-- python3 설치 다운 폴더로 이동 압축파일 설치폴더 삭제
rm -f Python-3.9.6.tgz
rm -Rf Python-3.9.6/

```



