---
title: Linux/Script - Java 어플리케이션 Bash 실행 스크립트 작성
author: Fortae
date: 2021-08-17 09:32:00
categories: [DEVOPTS, Linux]
tags: [infra, linux, script]
---

- daemon.sh 파일 생성하여 아래 내용을 복사
- daemon.sh 파일에 실행 권한 부여 ex) chmod 770 daemon.sh
- 주석 "check!!" 부분 어플리케이션 환경(linux 사용자 지정, 어플리케이션 이름)에 맞게 수정
- 스크릅트 실행: "daemon.sh start" / "daemon.sh stop"

```
#!/bin/bash

HOMEPATH=$(pwd)
CURRENT_USER="$(whoami)"

# check!! JAVA HOME 설정
JAVA_HOME="/sw/sol/java/java1.8"

# check!! 고유값 APP 이름 설정
APP_NM="app_java1"

# check!! 해당 스크립트를 기동할 사용자 지정
APP_USER="root"

# check!! 기타 JAVA 추가 실행 명령어
APP_SCRIPT="-jar agent.jar"

if [ $CURRENT_USER = $APP_USER ]
then
    # ---------------------------------------------------------------------------
    # JVM argument
    # ---------------------------------------------------------------------------
    JVM_ARGS="-DappName=$APP_NM"
    JVM_ARGS="$JVM_ARGS -Djava.security.egd=file:///dev/urandom"

    # ---------------------------------------------------------------------------
    # memory argument
    # ---------------------------------------------------------------------------
    MEM_ARGS="-Xms256m -Xmx256m"

    # ---------------------------------------------------------------------------
    #
    # ---------------------------------------------------------------------------
    case $1 in
            start)
                    XPID=`pgrep -f $APP_NM`
                    if [ "$XPID" !=  "" ]
                    then
                            kill -9 $XPID
                            echo "Current pid "$XPID" killed..................."
                    fi
                    echo "Start"
                    $JAVA_HOME/bin/java $JVM_ARGS $MEM_ARGS $APP_SCRIPT &
                    ;;
            stop)
                    echo "Stop"
                    XPID=`pgrep -f $APP_NM`
                    if [ "$XPID" !=  "" ]
                    then
                            kill -9 $XPID
                            echo "Current pid $XPID killed..................."
                    fi
                    ;;
            *)
                     echo "Usage  start | stop"
                    ;;
    esac
else
        echo "invalid user"
fi
```
