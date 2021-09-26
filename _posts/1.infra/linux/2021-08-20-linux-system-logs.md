---
title: Linux/System- 리눅스 시스템 로그
author: Fortae
date: 2021-08-20 00:00:00
categories: [1.Infra, Linux]
tags: [infra, linux, system]
---

- 리눅스 관련 로그 저장 경로 : /var/log
- 로그 정책관련 정보는 /etc/rsyslog.conf 파일에 정의 됨.
- syslog.conf 변경후 시스템 적용 명령어: systemctl restart rsyslog

```
1. /var/log/messages: 부팅시의 메시지를 포함해 전체 시스템의 로그 저장
2. /var/log/dmesg: kernel ring buffer의 정보 로그 저장 (시스템이 시작할때 커널이 발견한 하드웨어의 정보)
3. /var/log/auth.log: 사용자 로그인이나 사용된 인증방법같은 시스템 인증 정보 로그 저장
4. /var/log/boot.log: 시스템 부팅 과정의 로그 저장
5. /var/log/daemon.log:  시스템에서 실행 중인 백그라운드 데몬들의 정보 로그 저장
6. /var/log/dpkg.log: dpkg 명령어로 패키지를 설치하고 삭제한 로그 저장(ubuntu debian계열)
7. /var/log/kern.log: 리눅스 커널 로그 (리눅스 커널 커스터마이징시 사용)
8. /var/log/lastlog: 모든 사용자의 최근 로그인 정보 저장 (확인 명령어: lastlog)
9. /var/log/maillog, /var/log/mail.log: 메일서버의 로그 저장
10. /var/log/user.log: user 레벨의 모든 로그 저장
11. /var/log/Xorg.x.log: X 윈도의 로그(GUI 원격 접속 로그) 저장
12. /var/log/alternatives.log: 여러 버전의 패키지 정보 저장 (debian 계열)
13. /var/log/btmp: 이 파일에는 로그인 시도 실패에 대한 정보 저장 (확인 명령어: last -f /var/log/btmp | more)
14. /var/log/cups: 프린터 관련 로그 정보 저장
15. /var/log/anaconda.log: 리눅스 설치 지원 프로그램인 아나콘다의 로그 정보 저장
16. /var/log/yum.log: yum으로 패키지를 설치할 로그 정보 저장
17. /var/log/cron: cron 데몬이 대한 로그 정보 저장
18. /var/log/secure: 인터넷 슈퍼 데몬 xinetd의 로그로 권한부여와 관련된 내용의 로그 정보 저장
19. /var/log/wtmp, /var/log/utmp: 로그인 관련 정보(언제, 어디서 얼마나) 저장( 확인 명령어: last -f /var/log/wtmp)
```