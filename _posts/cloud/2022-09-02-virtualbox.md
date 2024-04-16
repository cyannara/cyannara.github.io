---
title: "VIRTUALBOX"
date: 2022-09-02
categories: cloud  
tags: [virtualbox]
---

## [virtual networking](https://www.virtualbox.org/manual/ch06.html){:target="_blank"}



##virtualBox 설정
* 복사 붙여넣기 
  - 가상머신 -> 장치 -> 게스트확장 CD 이미지 삽입... (설치필요)
  - 가상머진 -> 설정 -> 일반 -> 고급 -> 클립보드공유 -> "양방향"으로 변경
  
## [ubuntu 설치](https://www.osboxes.org/ubuntu/){:target="_blank"}

- 관리자 계정
```
username: osboxes
password: osboxes.org
Root account password: osboxes.org
``` 

## [ubuntu에 도커 설치](https://docs.docker.com/engine/install/ubuntu/){:target="_blank"}
* 도커 설치
```
$ sudo apt-get update

$ sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

$ sudo mkdir -p /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

* 설치 오류
```
E: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 3854 (unatended - upgr)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
```
```
sudo killall apt apt-get  
```
만일 진행중인 프로세스가 없다라고 뜨면, 아래와 같이 하나하나씩 디렉토리를 삭제해주세요.
```
$ sudo rm /var/lib/apt/lists/lock
$ sudo rm /var/cache/apt/archives/lock
$ sudo rm /var/lib/dpkg/lock*
$ sudo dpkg --configure -a
$ sudo apt update
```

