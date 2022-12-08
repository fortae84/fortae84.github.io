---
title: Kubernetes - CKA, CKAD, CKS certification
author: Fortae
date: 2022-10-08 00:32:00 -0500
categories: [DEVOPTS, Kubernetes]
tags: [kubernetes, cka, ckad, cks]
---

### CKA 자격증
- 추천 강의
  - https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/ (UDEMY)

- 시험 유형 
  - 쿠버네티스 업그레이드
    - 쿠버네티스 버전 업그레이드는 miner version 1단계 up 예) 1.**`24`**.0 -> 1.**`25`**.0
    - 업그레이드 순서: kubeadm upgrade -> kubeadm 계획 수립 -> kubelet upgrade
    - master node 부터 worker node로 순차적으로 적용
      
    ``` bash
      # kubeadm update 수행
      apt-get update
      apt-cache madison kubeadm
      apt-get install kubeadm=1.24.0-00

      # kubeadm 업그레이드 계획 수립 및 적용
      kubeadm upgrade plan
      kubeadm upgrade apply v1.24.0-00
        
      # kubeadm worker node 업그레이드
      kubeadm upgrade node
      
      # 업그레이드 대상 schedule 차단 및 contrainer 다른 노드로 이관
      kubectl drain controlplane --ignore-daemonsets
      apt-get install kubelet=1.24.0-00 kubectl=1.24.0-00

      # kubelet 재기동
      systemctl restart kubelet

      # 업그레이드 노트 스케줄 활성화
      kubectl uncordon controlpane

    ```
  - 쿠버네티스 Cluster 구성
  - ETCD 백업 하기
  - Static pod/etcd-controlplane 내용 참조, 파일: "/etc/kubernetes/manifests/etcd.yaml"
    ``` bash
      ETCDCTL_API=3 etcdctl \
        --endpoints=https://127.0.0.1:2379 \ 
        --cacert=/etc/kubernetes/pki/etcd/ca.crt \ 
        --cert=/etc/kubernetes/pki/etcd/server.crt \ 
        --key=/etc/kubernetes/pki/etcd/server.key snapshot save /opt/etcd-backup.db
    ```

  - 트러블 슈팅
    ``` text
    - 서비스 "name", "target와 port 불일치"
    - env, configmap 불일치
    - /etc/kubernetes/manifests static pod 설정 오류
    - node kubelet 실행 오류
    ```

### CKAD 자격증
- 추천 강의: 
  - https://www.udemy.com/course/certified-kubernetes-application-developer/ (UDEMY)

### CKS 자격증


