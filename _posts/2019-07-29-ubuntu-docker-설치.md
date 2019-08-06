---
layout: post
title: "ubuntu-docker-설치"
date: 2019-07-29 15:36:06
description: docker 설치 자꾸 까먹음. 
tags: 
 - ubuntu, docker
---

### 설치 (스크립트가 편함)
* script 
```{.bash}
$ curl -fsSL https://get.docker.com/ | sudo sh
```
### sudo 없이 하기
```{.bash}
# sudo usermod -aG docker $USER
# docker 재시작 해도 적용안 됨. 재부팅 이나 현재 user 로그아웃 후 하면 됨.
```

### check
```{.bash}
$ docker version
Client: Docker Engine - Community
 Version:           19.03.1
 API version:       1.40
 Go version:        go1.12.5
 Git commit:        74b1e89
 Built:             Thu Jul 25 21:21:05 2019
 OS/Arch:           linux/amd64
 Experimental:      false
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/version: dial unix /var/run/docker.sock: connect: permission denied
# 위처럼 permission 문제 나면 아직 제대로 안된것.
# 아래 처럼 에러 없이 길게 나와야 정상.
Client: Docker Engine - Community
 Version:           19.03.1
 API version:       1.40
 Go version:        go1.12.5
 Git commit:        74b1e89
 Built:             Thu Jul 25 21:21:05 2019
 OS/Arch:           linux/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          19.03.1
  API version:      1.40 (minimum version 1.12)
  Go version:       go1.12.5
  Git commit:       74b1e89
  Built:            Thu Jul 25 21:19:41 2019
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.2.6
  GitCommit:        894b81a4b802e4eb2a91d1ce216b8817763c29fb
 runc:
  Version:          1.0.0-rc8
  GitCommit:        425e105d5a03fabd737a126ad93d62a9eeede87f
 docker-init:
  Version:          0.18.0
  GitCommit:        fec3683
```

### 이거 아직 안해봄. 해봐야지
* docker에 있는 mysql 백업 후 복구
```{.bash}
# Backup
docker exec CONTAINER /usr/bin/mysqldump -u root --password=root DATABASE > backup.sql

# Restore
cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE
```

### 최근 특이한 현상을 겪어서 적어둠.
* 우분투 18.04.3 LTS 버전이었는데 버전문제인지 .. 뭔지 모르겠음.
* 맨위의 스크립트를 사용해서 설치하는데 실패함
* 실패하는 이유를 다 파악해보고 clean 후 재설치.. 별거 다해봤지만 안됨.
* 원인 파악해보니 (/var/log/syslog 를 확인 하고 알게됨) 이용할수 있는 network이 없다고 오류 나고 있음.
* 인터넷 뒤져보니 수동으로 network interface를 생성하는 방법으로 해결할수 있다고 해서 해보니까 됨.
```{.bash}
* sudo ip link add name docker0 type bridge
* sudo ip addr add dev docker0 172.17.0.1/16   # IP 대역은 docker 에서 사용하는 IP 대역을 써야함.
```
