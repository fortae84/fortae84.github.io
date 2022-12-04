---
title: Linux/System - Linux OS 환경 정보
author: Fortae
date: 2021-08-21 00:00:00
categories: [DEVOPTS, Linux]
tags: [infra, linux, system]
---

- Lnux OS 환경 변수 파일은 profile 또는 bashrc에 정의한다.
- 모든 OS 계정에서 공통적으로 적용되는 /etc/profile /etc/bashrc가 있으며,  개별 로그인 계정에서 사용하는 ~/.profile ~/.bashrc 이 있다.
- Linux OS 환경 변수의 우선 순위는 /etc/profile -> .profile -> .bashrc -> /etc/bashrc 이다.

- Profile
용도: 시스템 환경 변수 값을 정의 한다 (각종 Path경로, 각종 변수 선언)
```bash

```


- Bashrc
용도: 시스템 관련 함수 또는 Alias를 정의한다